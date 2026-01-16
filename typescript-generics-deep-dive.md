---
title: Making Sense of TypeScript Generics
anchor: TypeScript generics as type variables (not annotations)
tags: [typescript, generics, types, programming]
description: Artem Zakharchenko's guide to understanding generics as type variables
source_url: https://kettanaito.com/blog/making-sense-of-typescript-generics
---

## Key Insight

Generics aren't type annotations - they're **type variables** that get assigned when you call the function.

```typescript
function print<MessageType>(msg: MessageType): MessageType {}
//        ↑ stores the type     ↑ uses the stored type as return
```

## How Type Inference Works

- Pass `"hello"` → TypeScript infers `MessageType = 'hello'` (literal type, not just `string`)
- Pass `42` → Infers `MessageType = 42`
- Return type matches whatever you passed in

## Constraints

Use `extends` to limit accepted types:

```typescript
function print<T extends string | number>(msg: T): T {}
```

## Conditional Types

Different behavior based on the generic's value:

```typescript
T extends string ? T : void  // Return T if string, void otherwise
```

## The Mental Model Shift

Once you see generics as "variables for types" instead of annotations, everything clicks.

## Complementary Resource

- [Una Kravets on TypeScript Generics](https://bsky.app/profile/una.im/post/3mckobpozms2z)
