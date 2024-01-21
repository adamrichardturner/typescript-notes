# Array Types

TypeScript arrays are typed collections of elements, with two main ways to define them: by appending [] to the element type:

```typescript
string[]
```

or by using generic syntax:

```typescript
Array<T>
```

These type definitions ensure type safety, preventing the addition of incompatible elements.

TypeScript also introduces **tuples**, which are fixed-length arrays where each element can have a distinct type.

Tuples are useful for representing a fixed set of related values with potentially different types.

These features enhance code maintainability and reduce runtime errors by enforcing stricter type checks.

### TypeScript Arrays:

- **Typed Elements:** Arrays in TypeScript enforce elements to be of a specific type.
- **Type Safety:** Prevents the addition of incompatible element types.
- **Flexible Length:** The array can grow or shrink in size, maintaining the same element type.

### TypeScript Tuples:

- **Fixed Length:** Tuples have a predetermined number of elements.
- **Heterogeneous Types:** Each element in a tuple can be of a different type.
- **Order Matters:** The type of each element is fixed based on its position.
- **Readability:** Useful for representing a set of related, but differently-typed, values.
- **Strict Assignment:** Adding or removing elements from a tuple is more restricted than in arrays.

## TypeScript Tuple Type Length and Order

Tuples are declared with a fixed number of elements which cannot be assigned a different number of elements or length of tuple.

Order is important: tuples maintain a strict ordering of member elements.

The type for each element is enforced and an error will be generated if these condtions are not met.

```typescript
// Incompatible types
let employee: [string, number] = ['Manager', null]
// Error: Type 'null' is not assignable to type 'number'.

// Assigned values do not match fixed length of types in tuple
let grade: [string, number, boolean] = ['TypeScript', 85, true, 'beginner']
/*
Error: Type '[string, number, true, string]'
is not assignable to type '[string, number, boolean]'.
Source has 4 element(s) but target allows only 3.
*/
```

## Rest Parameter Any Array Type

Rest parameters are implicitly assigned an array type of **any[]** by TypeScript

```typescript
const sumAllNumbers = (...numberList): number => {
  // Error: Rest parameter 'numberList' implicitly has an 'any[]' type.
  let sum = 0
  for (let i = 0; i < numberList.length; i++) {
    sum += numberList[i]
  }
  return sum
}

// Notice third argument is a string
console.log(sumAllNumbers(100, 70, '30'))
// Prints a string "17030 instead of a number 200
```

## Tuple Syntax

When annotating a tuple, we add a colon followed by square brackets containing a list of comma separated types.

```typescript
// This is a tuple
let profile: [string, number, boolean, number] = ['Kobe', 39, true, 150000]

profile[2] = 'false' // Error: Type 'string' is not assignable to type 'boolean'.
profile[3] = null // Error: Type 'null' is not assignable to type 'number'.
```

## Generic Type for One Dimensional Arrays

We can annotate a one-dimensional array as a generic type

```typescript
Array<T>
```

Here is an example using a generic type:

```typescript
// zipcodes is an array of strings
let zipcodes: Array<string> = ['03255', '02134', '08002', '03063']

// Pushing a number to zipcodes will generate an error
// Error: Argument of type 'number' is not assignable to parameter of type 'string'.
zipcodes.push(90210)
```

## Tuple Type Spread Syntax

Spread syntax can be used as an argument in a function call where the function has parameter types that match the types of the tuple elements.

```typescript
function modulo(dividend: number, divisor: number): number {
  return dividend % divisor
}

const numbers: [number, number] = [6, 4]

// Call modulo() with a tuple
console.log(modulo(numbers))
// Error: Expected 2 arguments, but got 1.
// Prints NaN

// Call modulo() with spread syntax
console.log(modulo(...numbers))
// No error, prints 2
```
