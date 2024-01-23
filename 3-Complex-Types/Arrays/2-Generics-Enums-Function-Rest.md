# Generics, Multi-dimensional Arrays, Enums, and Function Rest Parameter Explicit Types

In TypeScript, generics enable you to create reusable, type-safe components by defining one or more type variables.

Multi-dimensional arrays can be defined using nested array types, allowing for complex data structures like matrices.

Enums are a way to group named constants, providing an easy-to-read and maintainable way to handle sets of related values.

TypeScript also supports function rest parameters, which can be given explicit types to ensure that all arguments passed in a rest parameter are of a specific type.

These features, together enhance TypeScript's flexibility and robustness, allowing developers to write more precise and maintainable code.

## Generic Type Alias

```typescript
// This is a generic type alias
type Collection<G> = {
  name: string
  quantity: number
  content: G[]
}

let bookCollection: Collection<string> = {
  name: 'Nursery Books',
  quantity: 3,
  content: ['Goodnight Moon', 'Humpty Dumpty', 'Green Eggs & Ham'],
}

let primeNumberCollection: Collection<number> = {
  name: 'First 5 Prime Numbers',
  quantity: 5,
  content: [2, 3, 5, 7, 11],
}
```

Generic types are custom user defined types that are defined with a symbol or placeholder parameter within angle brackets that can be re-used throughout the type declaration as a placeholder for an as yet to be passed in type argument.

To define a generic type alias, we use the **type** keyword, followed by the alias name and angle brackets **<...>**.

## Type for Multi-dimensional Array

```typescript
// one-dimensional arrays
let zipcodesNH: string[] = ['03255', '03050', '03087', '03063']
let zipcodesMA: string[] = ['02334', '01801']

// two-dimensional array
let zipcodes: string[][] = [zipcodesNH]

// Pushing a one-dimensional array to a two-dimensional array
zipcodes.push(zipcodesMA)
console.log(zipcodes)
// prints [["03255", "03050", "03087", "03063"], ["02334", "01801"]]
```

The type for multi-dimensional arrays can be annotated by declaring the type used throughout the array with an extra **[]** for each dimenion of the array.

## Numeric and String Enum Types

```typescript
// This is a numeric enum type
enum ClassGrade {
  Freshman = 9,
  Sophomore,
  Junior,
  Senior,
}

// This is a string enum type
enum ClassName {
  Freshman = 'FRESHMAN',
  Sophomore = 'SOPHOMORE',
  Junior = 'JUNIOR',
  Senior = 'SENIOR',
}

const studentClass: ClassName = ClassName.Junior
const studentGrade: ClassGrade = ClassGrade.Junior

console.log(`I am a ${studentClass} in ${studentGrade}th grade.`)
// Prints "I am a JUNIOR in 11th grade."
```

TypeScripts both **numeric** and **string** enum types.

Members of a numeric enum have a corresponding numeric value assigned to them, whereas string enums must have a corresponding string value assigned to them.

## String Enum Variable Assignment

```typescript
enum MaritalStatus {
  Single = 'SINGLE',
  Married = 'MARRIED',
  Separated = 'SEPARATED',
  Divorced = 'DIVORCED',
  Widowed = 'WIDOWED',
}

// Assign a string to a string enum type
let eligibility: MaritalStatus
eligibility = 'SEPARATED'
// Error: Type '"SEPARATED"' is not assignable to type 'MaritalStatus'.

eligibility = MaritalStatus.Separated // No error
```

String enum types do not allow a string to be assigned to its member, unlike numeric enum types. Doing so causes a TypeScript error.

## Function Rest Parameter Explicit Type

```typescript
const sumAllNumbers = (...numberList: number[]): number => {
  let sum = 0
  for (let i = 0; i < numberList.length; i++) {
    sum += numberList[i]
  }
  return sum
}

console.log(sumAllNumbers(100, 70, '30')) // Error: Argument of type 'string' is not assignable to parameter of type 'number'.
```

Explicitly type annotating a rest parameter of a function will alert TypeScript to check for type inconsistency between the rest parameter and the function call arguments.
