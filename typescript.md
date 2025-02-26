# Typescript

🤩 A "superset" of JavaScript. 

#### 📈 Definitions
- Reduce development errors
- TS doesn't run in the browser, it needs to be compiled. After compilation, it will generate a JavaScript file

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
/* Array */
let name = 'John Snow';
// This will generate an error
name = 124;

```
