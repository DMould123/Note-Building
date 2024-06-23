# TypeScript Basics 🚀

## What is TypeScript? 🤔
TypeScript is a typed superset of JavaScript that compiles to plain JavaScript. It adds static types to the language, which can help catch errors early through type checking and improve the development experience with features like autocompletion and navigation.

## TypeScript File Structure 📁
```
// This is a TypeScript file
let message: string = "Hello, TypeScript!";
console.log(message);
```

## Type Annotations 🔍

Type annotations are used to explicitly specify types for variables, function parameters, and return types.

### Variables
```
let isDone: boolean = false;
let decimal: number = 6;
let color: string = "blue";
```
## Basic Types 📏
TypeScript provides several basic types that are commonly used in programming.

- `boolean`: Represents true/false values.
- `number`: Represents numerical values.
- `string`: Represents textual data.
- `array`: Represents a collection of values of a specific type.
- `any`: A type that can represent any value (used sparingly).
- `null`: Represents null or undefined values.
- `never`: Represents values that never occur.
- `undefined`: Represents null or undefined values.
- `enum`: Represents a collection of related values that can be numeric or string-based.
- `void`: Represents the absence of a type, commonly used as a return type for functions that do not return a value.

### Examples 📝

```
let isCompleted: boolean = true;
let count: number = 42;
let username: string = "Alice";
let numbers: number[] = [1, 2, 3];
let tuple: [string, number] = ["Hello", 10];
enum Color { Red, Green, Blue }
let color: Color = Color.Green;
let randomValue: any = "Could be anything";
let unusable: void = undefined;

```

## Interfaces and Classes 🧱

### Interfaces
Interfaces define the structure of an object.

```
interface Person {
    name: string;
    age: number;
}

let user: Person = {
    name: "John",
    age: 30
};
```

### Classes
Classes provide a way to define objects and their behavior.

```
class Greeter {
    greeting: string;

    constructor(message: string) {
        this.greeting = message;
    }

    greet() {
        return "Hello, " + this.greeting;
    }
}

let greeter = new Greeter("world");
console.log(greeter.greet());
```

## Modules 📦
### Exporting
```
export class Calculator {
    add(a: number, b: number): number {
        return a + b;
    }
}
```

### Importing
```
import { Calculator } from './Calculator';

let calc = new Calculator();
console.log(calc.add(5, 3));
```

## Generics ⚙️
Generics allow you to create reusable components that work with any type.

### Example
```
function identity<T>(arg: T): T {
    return arg;
}

let output1 = identity<string>("myString");
let output2 = identity<number>(42);
```

## TypeScript Configuration 📄
You can configure the TypeScript compiler using a tsconfig.json file. This file allows you to specify the root files and compiler options required to compile a TypeScript project.

### Example tsconfig.json 
```
{
    "compilerOptions": {
        "target": "es6",
        "module": "commonjs",
        "strict": true,
        "outDir": "./dist"
    },
    "include": ["src/**/*"]
}
```

## Conclusion 🌟
TypeScript enhances JavaScript by adding type safety, improving code quality, and providing a better development experience. With its powerful features, it is widely used in modern web development. Explore TypeScript further to unlock its full potential!
