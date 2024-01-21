# TypeScript Functions

TypeScript enhances function handling by allowing developers to specify parameter and return types explicitly, promoting code clarity and type safety. 

It supports various function expressions, declarations, and arrow functions, all with type inference capabilities. 

- Explicit parameter and return type declarations
- Support for function expressions, declarations, and arrow functions
- Function overloads for handling multiple argument types
- Optional parameters and default parameter values for flexibility
- Enhanced code clarity and type safety

## Explicit Return Types

In TypeScript we can explicitly define function return types by adding type annotations (: with the type) after a function's signature and closing paranthesis.

```typescript
function trueOrFalse(value: boolean): number {
  if (value) {
    return 35;
  }

  return 'Hello Adam'; 
  // Typescript Error: Type 'string' is not assignable to type 'boolean'.
}
```

## Default Parameters

Where we define a default value for a function parameter, TypeScript will infer that type to be the same as the default type.

```typescript
function exponentiation(power = 1) {
  console.log(4 ** power);
}

exponentiation(); // Prints: 4

exponentiation(4); // Prints: 256

exponentiation(true); 
// Error: Argument of type 'true' is not assignable to parameter of type 'number | undefined'.
```

## Void Return Type

If a function does not return a value e.g. it produces only a side effect, such as logging to the console, then you can specify the **void** return type.


```typescript
function myName(): void { 
    console.log('Adam Turner')
} 
```

## Inferring Return Types

By looking at the types of the values in the return statement and the evaluated type returned, TypeScript infers the return type of the function.

```typescript
function trueOrFalse(age: number) {
  return age > 30 ? 'true' : 'false';
}

const myAnswer : boolean = trueOrFalse(); 
// Type 'string' is not assignable to type 'boolean'
```

## Parameter Type Annotations

Function parameters can be type annotated, just like variables.

```typescript
function heyNoun(noun: string) {
  console.log(`Hey, ${noun}!`);
}

greet('World'); // Prints: Hey, World  

greet(2020); 
// Argument of type 'number' is not assignable to parameter of type 'string'.
```