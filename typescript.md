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
##### 1️⃣ Primitive types 
```typescript
let myNumber: number;
let myString: string;
let myBoolean: boolean;
```
##### 2️⃣ More complex types
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

##### 3️⃣ Type inference
If a variable is instatiated without a type definition, typescript will infer the type and generate an error if something doesn't respect the type after the instantiation.
```typescript
let name = 'John Snow';
// This will generate an error, because name should be a string
name = 124;
```

##### 4️⃣ Union types
```typescript
let varStringOrNull: string | null = 'John Snow';
// This will not generate an error
name = null;
```

##### 5️⃣ Type Aliases
```typescript
type Person = {
  name: string,
  age: number
}
let firstPerson: Person
```

##### 6️⃣ Function types
```typescript
// Declaring the type is not necessary because it's inferred
function add(a: number, b:number): number {
  return a + b;
}
```

##### 7️⃣ Generics
function prepend<T>(theList: T, item: T) {
  return [item, ...theList];
}
// New number list
let newNumberList = prepend([2, 3, 4, 5], 1);
// New string list
let newStringList = prepend(['b', 'c', 'd'], 'a');

##### 8️⃣ Classes
class Student {
  
  // firstName: string
  // lastName: string
  // age: number
  // private courses: string[]

  // with this method, its not necessary declare the attributes
  constructor(
    public firstName: string, 
    public lastName: string, 
    public age: number,
    private courses: string[]
  )

  // methods
  enrol(courseName: string) {
    this.courses.push(courseName);
  }

  listCourses() {
    return this.courses.slice();
  }
}

##### 9️⃣ Interfaces



