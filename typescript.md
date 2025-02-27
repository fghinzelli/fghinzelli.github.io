# Typescript

🤩 A "superset" of JavaScript. 

#### 📈 Definitions
- Reduce development errors
- TS doesn't run in the browser, it needs to be compiled. After compilation, it will generate a JavaScript file
- Whenever possible, use type inference (It's not necessary to declare the type)
- Define **types** reduce code duplication

#### 💥 Instalation
```shell
npm install typescript
# Create a tscofig.json file
npx tsc --init
```
#### 🚀 Run 
```
npx tsc <file_name.ts>
```
#### 📓 Sintax
##### 1. Primitive types
```typescript
let myNumber: number;
let myString: string;
let myBoolean: boolean;
```
##### 2. More complex types
```typescript
/* Array */
let myArray: number[];
myArray = [1, 2, 3, 4];

/* Object */
let person: {
  name: string,
  age: number
}
person = {
  name: 'John',
  age: 12
}

/* Object with array */
let people: {
  name: string
  age: number
}[];

##### 3. Type inference
If a variable is instatiated without a type definition, typescript will infer the type and generate an error if something doesn't respect the type after the instantiation.
```typescript
let name = 'John Snow';
// This will generate an error, because name should be a string
name = 124;
```

##### 4. Union types
```typescript
let varStringOrNull: string | null = 'John Snow';
// This will not generate an error
name = null;
```

##### 5. Type Aliases
```typescript
type Person = {
  name: string,
  age: number
}
let firstPerson: Person
```

##### 6. Function types
```typescript
// Declaring the type is not necessary because it's inferred
function add(a: number, b:number): number {
  return a + b;
}
```

##### 7. Generics
##### 8. Classes
##### 9. Interfaces



