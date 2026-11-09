# Type Narrowing in TypeScript

## Introduction
Type narrowing is the process of refining a broad type, such as a union, into a more specific one inside a block of code. It lets TypeScript know exactly what you can safely do with a value at each point.

## Using typeof
The `typeof` operator is best for primitive types.

```ts
function format(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase(); // value is string here
  }
  return value.toFixed(2);      // value is number here
}
```

## Using instanceof
The `instanceof` operator narrows values to a specific class.

```ts
function showError(error: Error | string): string {
  if (error instanceof Error) {
    return error.message;
  }
  return error;
}
```

## Using the in Operator
The `in` operator checks whether a property exists, which helps with object unions.

```ts
interface Dog { bark(): void }
interface Cat { meow(): void }

function speak(pet: Dog | Cat): void {
  if ("bark" in pet) {
    pet.bark();
  } else {
    pet.meow();
  }
}
```

## Conclusion
Type narrowing removes the need for unsafe type assertions. Use `typeof` for primitives, `instanceof` for classes and `in` for object shapes, and your code will be both safer and easier to read.