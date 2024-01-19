# Types in TypeScript

## Type Inference

Type inference ensures the expected type of a variable matches the data type bound to the variable when first declared.

If we assign a string to a mutable variable and try to re-assign it to a number, TypeScript will log a complaint that the new value cannot be assigned because it is expecting the initial data type.

```typescript
let name = 'Adam';

first = 1988; // Type 'number' is not assignable to type 'string'
```

## Any

If no initial value is assigned to a variable, TypeScript considers it to be of type **any**. A variable of this type can be reassigned to any data type without error.

```typescript
let name;
first = 'Adam';
first = 1988;
```

The above will not produce any errors or warnings, and the variable can be used without type safety throughout the program.

## Primitive Types

A primitive data type in JavaScript is a basic data type that represents a single immutable value, such as numbers, strings, booleans, null, and undefined. 

They are not objects and do not have methods or properties.

All primitive or built-in data types in JavaScript are present in TypeScript.

```typescript
// Number (numeric data type)
const age = 35; 

// String (textual data type)
const name = "Adam"; 

// Boolean (true or false)
const isStudent = false; 

// Undefined (represents the absence of a value)
let city; 

// Null (represents the intentional absence of any object value)
const car = null; 

// Symbol (unique and immutable values, often used as object keys)
const uniqueSymbol = Symbol("description"); 

// BigInt (used for very large integers)
const bigIntValue = 1234567890123456789012345678901234567890n; 
```

## Shape of an Object

TypeScript is aware of the **shape of an object** - what properties it does or does not contain. TypeScript logs errors and suggestions if we try to access properties that don't exist on the object.

```typescript
let firstName = 'muriel!';

console.log(firstName.toUppercase()); 

// error: Property 'toUppercase' does not exist on type 'string'. Did you mean 'toUpperCase'?
```

