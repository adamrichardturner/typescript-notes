# Type Narrowing

Type narrowing in TypeScript refers to the process of refining variable types to more specific types than the ones initially declared.

TypeScript allows for type narrowing through various constructs such as type guards, type assertions, and control flow analysis.

For example, using if checks, typeof operators, or user-defined type guards, developers can narrow types from a broader category (like string | number) to a more specific type (string or number).

This process helps in catching errors at compile time, making the code more predictable and robust by ensuring that the operations performed on variables are type-appropriate.

## Union Type Narrowing

Since a variable of a union type can assume one of several different types, you can help TypeScript infer the correct variable type using type narrowing.

To narrow a variable to a specific type, implement a type guard.

Use the typeof operator with the variable name and compare it with the type you expect for the variable.

```typescript
const choices: [string, string] = ["NO", "YES"]
const processAnswer = (answer: number | boolean) => {
  if (typeof answer === "number") {
    console.log(choices[answer])
  } else if (typeof answer === "boolean") {
    if (answer) {
      console.log(choices[1])
    } else {
      console.log(choices[0])
    }
  }
}
processAnswer(true) // Prints "YES"
processAnswer(0) // Prints "NO"
```

## Type Guard

A TypeScript type guard is a conditional statement that evaluates the type of a variable.

It can be implemented with the typeof operator followed by the variable name and compare it with the type you expect for the variable.

```typescript
// A type guard implemented with the typeof operator
if (typeof age === "number") {
  age.toFixed()
}
```

## Type Guard: Accepted Types

The typeof operator may be used to implement a TypeScript type guard to evaluate the type of a variable including number, string and boolean.

## Type Guard with in operator

If a variable is a union type, TypeScript offers another form of type guard using the in operator to check if the variable has a particular property.

```typescript
/*
In this example, 'swim' in pet uses the 'in' operator to check if the property .swim is present on pet. TypeScript recognizes this as a type guard and can successfully type narrow this function parameter.
*/
function move(pet: Fish | Bird) {
  if ("swim" in pet) {
    return pet.swim()
  }
  return pet.fly()
}
```

## Type Guard with `if-else` Statement

If a variable is of a union type, TypeScript can narrow the type of a variable using a type guard.

A type guard can be implemented as a conditional expression in an if statement.

If an else statement accompanies the if statement, TypeScript will infer that the else block serves as the type guard for the remaining member type(s) of the union.

```typescript
function roughAge(age: number | string) {
  if (typeof age === "number") {
    // In this block, age is known to be a number
    console.log(Math.round(age))
  } else {
    // In this block, age is known to be a string
    console.log(age.split(".")[0])
  }
}
roughAge("3.5") // Prints "3"
roughAge(3.5) // Prints 4
```

## Type Guard: `if` Statement Return

If a variable is of a union type, TypeScript can narrow the type of a variable using a type guard.

A type guard can be implemented as a conditional expression in an if statement.

If the if block contains a return statement and is not followed by an else block, TypeScript will infer the rest of the code block outside the if statement block as a type guard for the remaining member type(s) of the union.

```typescript
function formatAge(age: number | string) {
  if (typeof age === "number") {
    return age.toFixed() // age must be a number
  }
  return age // age must not be a number
}
console.log(formatAge(3.5)) // Prints "4"
console.log(formatAge("3.5")) // Prints "3.5"
```
