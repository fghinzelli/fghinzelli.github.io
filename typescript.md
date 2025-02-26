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
##### Primitive types
```typescript
let myNumber: number;
let myString: string;
let myBoolean: boolean;
```
##### More complex types
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


```
