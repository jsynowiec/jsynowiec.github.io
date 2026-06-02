---
title: "You Might Not Need an Enum: Why Const Assertions Are the Better Default in TypeScript"
date: 2026-06-02 10:39:11 +0200
categories: ["Software Engineering", "Guides"]
description: Why as const beats enums for most TypeScript use cases. Covers Zod integration, the satisfies operator, and keeping a single source of truth.
tags: ["TypeScript", "Patterns", "Zod", "Deep Dive"]
---

I was recently reviewing a few PRs and saw a mix of string literal unions and enums used for what was essentially a config lookup. The values were duplicated between the types and Zod schema, and some type assertions were clearly there just to satisfy the compiler. When I suggested using the `as const` pattern instead, the author — a senior engineer — had never seen it. That surprised me.

When we want to document intent and create a set of distinct, named constraints, we usually use one of three patterns:
- literal union type,
- enum,
- and const assertion.


Each has its upsides, caveats, associated risks, and runtime costs. As usual, there is no one-size-fits-all approach here. However, arguably, the const assertion is what you should default to unless you have specific reasons not to use it.

## Literal Union

I'm sure you've used or seen plenty of [literal](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#literal-types) [union](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types) types in TypeScript, especially using string literals. This type restricts the variable to only the few defined options.

```ts
type LogLevel = "debug" | "info" | "warn" | "error";
```

Plain and simple, right? But there are caveats: **you can't access the values at runtime**.

If you want to add runtime validation when reading a file config or environment variables, you need to duplicate the values. If you later add the `"critical"` literal to the union, you must remember to update the schema too, or you will get a runtime failure. There is no connection between the type and the runtime validation.

```ts
type LogLevel = "debug" | "info" | "warn" | "error";
// Separate Zod schema
const logLevelSchema = z.enum(["debug", "info", "warn", "error"]);
```

## Enumerated Data Type

The commonly used alternative is the enumerated data type. The enumerator names are usually identifiers that behave as constants. There are some small differences at runtime between numeric, string, and mixed enums. I am not going to cover those, but I strongly suggest you read the TypeScript [documentation](https://www.typescriptlang.org/docs/handbook/enums.html).

```ts
enum LogLevelEnum {
  DEBUG = "debug",
  INFO  = "info",
  WARN  = "warn",
  ERROR = "error",
}

// Optional type alias if you want to hide the enum itself
// `${LogLevelEnum}` resolves to the literal union:
// "debug" | "info" | "warn" | "error"
export type LogLevel = `${LogLevelEnum}`;
```

You can then perform runtime extraction or iterate without duplicating the values.

```ts
enum LogLevelEnum {
  DEBUG = "debug",
  INFO  = "info",
  WARN  = "warn",
  ERROR = "error",
}

// Caveat: type-link is severed because TypeScript can't connect
// string back to the Enum type
const logLevelSchema = z.enum(
  Object.values(LogLevelEnum) as [string, ...string[]]
);
```

The runtime cost of using enums this way is higher than the other two patterns. It adds a JavaScript object and the `Object.values()` call. It's a tradeoff for removing value duplication and enabling runtime access.

The important limitation here is that this way of extracting enum values for Zod only works cleanly for string enums. For numeric enums, `Object.values()` returns both the numeric values and reverse-mapped keys (e.g., `[0, 1, "DEBUG", "INFO"]`), while for mixed enums, it's worse.

## Const Assertion

The modern preferred pattern is TypeScript's **const assertion** syntax, sometimes called a "string literal union via const assertion".

Const assertions were introduced in [TypeScript 3.4](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-4.html) and are a valuable tool for creating idiomatic, explicit, and type-safe code. Unfortunately, this syntax is still not widely known and is underused. Also, I haven't seen it used much in AI-generated code. The current SOTA models still seem to default to string literal union types and duplicate values. But, if I explicitly steer the model to use const assertions, it usually admits it's a better choice than a literal union or an enum.

In TypeScript, `const` declarations and `const` assertions serve different purposes. The `const` declaration creates a named constant variable, while `const` assertion creates literal types.

You can use the `as const` assertion with arrays and objects, in addition to primitives. The assertion is limited to **literal values** and cannot be applied to variables, function returns, or non-literal expressions.

```ts
const LOG_LEVEL = ["debug", "info", "warn", "error"] as const;
type LogLevel = (typeof LOG_LEVEL)[number];
```

`as const` narrows the array type from `string[]` to a **readonly tuple** of literal types. Then `typeof` captures that readonly tuple, and `[number]` indexes into it to extract a union of its literal values.

If you want to add runtime validation using a Zod schema, you can use the tuple directly, forming a strong type-schema link. The `LOG_LEVEL` becomes a single source of truth, and the tuple has negligible runtime cost.

```ts
// No duplication, no runtime extraction
const logLevelSchema = z.enum(LOG_LEVEL);
```

And because the tuple is already a runtime source, you can iterate over it directly.

```ts
LOG_LEVEL.forEach((v) => { ... });
```

Now, when you need to add a `"critical"` level, you can do it in a single place and everything expands together with no risk or drift.

The const assertion is more expressive. It gives you the type **and** a runtime artifact derived from the same source. You trade slightly cryptic syntax and a minimal runtime cost (paid once) for better ergonomics and a single source of truth.

> *"This is the way."*
>
> \- philosophy of Mandalorians

Also, this pattern enables a few handy use cases that weren't straightforward with the literal union or enum data type. Here are some examples I often use:

#### 1. Validate Against a Type

You can use the Zod schema, as shown earlier, but you can also directly check if the tuple has a specific value.

```ts
LOG_LEVEL.includes('info'); // true
```

#### 2. Derive Related Types

You can define derived types, for example:

```ts
type LogLevelMap = Record<typeof LOG_LEVEL[number], string>
```

#### 3. Ensure an Object Matches a Record While Keeping the Literal Types

Using `as const` on a `Record` makes the structure deeply readonly. However, to avoid losing literal type information, do not explicitly annotate the variable as `Record<K, V>`. Instead, use the `satisfies` keyword (TypeScript 4.9+) to validate the shape.

This is a great use case when you need a lookup table or configuration map where:

- **Keys are known and fixed** at compile time (e.g., specific status codes, event names, or feature flags)
- **Values must be strictly typed** but you also want to preserve their literal values for type narrowing.
- You want the compiler to error if a key is missing or if an extra, invalid key is added.

A classic use case is mapping specific error codes to user-friendly messages or retry logic. You want to ensure every defined error code has a corresponding message, and you want to use the specific message strings elsewhere in your code with full type safety.


```ts
// 1. Define the set of allowed keys (error codes)
type ErrorCode = "INVALID_INPUT" | "UNAUTHORIZED";

// 2. Define the shape of the value
interface ErrorConfig {
  message: string;
  retryable: boolean;
  httpStatus: number;
}

// 3. Create the Record using 'satisfies' and 'as const'
const errorMap = {
  INVALID_INPUT: {
    message: "Check your input.",
    retryable: false,
    httpStatus: 400,
  },
  UNAUTHORIZED: {
    message: "Login required.",
    retryable: false,
    httpStatus: 401,
  },
} as const satisfies Record<ErrorCode, ErrorConfig>;
```

### How The Indexed Access Works

The `[number]` index can be counterintuitive at first. The `[number]` syntax is used because arrays and tuples in TypeScript are technically objects with numeric keys.

1. **Arrays are Objects**: In TypeScript's type system, an array like `["A", "B"]` is treated similarly to an object `{ 0: "A", 1: "B" }`.
2. **Indexed Access**: The syntax `T[K]` looks up the type of property `K` on type `T`.
3. **The number Key**: By using `number` as the index, you aren't accessing a specific item (like index 0). Instead, you are accessing the **numeric index signature** of the array.

Without the `[number]`, `typeof` would just be the array structure itself, not the individual element types.

## Const Type Parameters

TypeScript 5.0 introduced [const type parameters](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-5-0.html#const-type-parameters), which let you write `function getLevels<const T>(arr: T[])` and have the compiler infer a readonly tuple instead of a widened array type without `as const` at the call site.

This is relevant here because if you find yourself writing wrapper functions that consume const-asserted arrays, a const type parameter can make the API cleaner.

It does not replace `as const` for most use cases, but if you are building internal utilities around this pattern, it is worth knowing about.

## When Would You Still Use Enums

I am not arguing that enums or string literal unions are obsolete. They still solve problems that const assertions do not. While I now default to using the const assertion patterns most of the time, there are still some cases when I would reach for an enum.

The rule of thumb is to start with `as const` and reach for an enum only when a specific need surfaces in the design.

### Declaration Merging

You cannot merge a const-asserted tuple with anything. Enums support declaration merging, which is genuinely useful when you are extending a type defined by a library or splitting a large set of constants across multiple files.

### Reverse Mapping

Numeric enums in TypeScript create a bidirectional mapping at runtime. `SomeEnum[0]` gives you `"DEBUG"`. For debugging serialized numeric values this is occasionally useful in a way that a plain tuple is not.

### Team/Tooling Friction

If a codegen, a backend API schema, or a protobuf definition generator emits TypeScript types, it will almost certainly emit enums. There is no point in fighting the tooling to convert everything to `as const`. Be pragmatic with the rest of your stack and team.

### Nominal Typing

Two unrelated const-asserted tuples that happen to contain the same values will be interchangeable. An enum produces a nominally distinct type. That distinction matters in larger codebases where accidental interchange is a real risk.
