---
title: "Understanding TypeScript 🔵 Basics: A Beginner's Guide 🚀"
date: 2021-03-12
draft: false
description : "A Comprehensive Guide to Functions, Variables, and Operations for Your TypeScript🔵 short guide."
image: "/images/ts.webp"
imageBig: "/images/typescript.webp"
categories : ["TypeScript",
"javascript",
"WebDevelopment",
]
authors : ["rohit patel"]
avatar : "/images/avatar.webp"
---

**TypeScript**, a superset of *JavaScript*, enhances code quality through static typing. Let's explore the essentials with emojis to make it even more fun!

## Installing TypeScript 🌐
To get started, install TypeScript globally using npm:

```bash
$ npm install -g typescript
$ tsc -v
```

## Setting Up tsconfig.json ⚙️
Create a tsconfig.json file to configure your TypeScript project:

```bash
$ tsc --init
```

Set the rootDir and outDir:

```typescript
{
  "compilerOptions": {
    // Other options...
    "rootDir": "./src",
    "outDir": "./public"
  }
  // Other configurations...
}
```
## Compiling TypeScript 🛠️
Compile a specific file or watch for changes:

```bash
$ tsc index.ts
$ tsc index.ts -w
```

Compile into a specified output file:

```bash
$ tsc index.ts --outfile out/script.js
```
Compile all files in the rootDir:
```bash
$ tsc -w
```

## Strict Mode 🚫
Enable strict mode for better error detection:

```bash
{
  "compilerOptions": {
    // Other options...
    "strict": true
  }
  // Other configurations...
}
```

## Primitive Types 🔄
Seven primitive types: string, number, bigint, boolean, undefined, null, and symbol. Explicitly annotate types:

```typescript
let firstName: string = 'superuser';
```

## Union Types 🤝
Variables with more than one type:

```typescript
let age: number | string;
age = 26;
age = "26";
```

## Dynamic Types 🌐
The any type for dynamic typing:
```typescript
let dynamicAge: any = 100;
dynamicAge = true;
```

## Literal Types 🎯
Specific strings or numbers:
```typescript
let direction: 'UP' | 'DOWN';
direction = 'UP';
```
## Objects 🧑‍💼
Objects with correct properties and value types:
```typescript
let person: {
    name: string;
    isProgrammer: boolean;
};

person = {
    name: 'Superuser',
    isProgrammer: true
};
```
## Arrays 📚
Define the type of data an array can contain:
```javascript

let id: number[] = [];
id.push(1);
// id.push("2"); // Error
```
## Tuples 🍇
Strict arrays with fixed size and known data types:

```typescript
let options: [string, number];
options = ['UP', 10];
  ```
## Functions 🎉
Define argument and return types:
```typescript

function circle(diameter: number): string {
    return 'Circumference = ' + Math.PI * diameter;
}
```
### For arrow functions:
```typescript

const circle = (diameter: number): string =>
    'Circumference = ' + Math.PI * diameter;

```
If declaring without defining:
```typescript


let sayHi: (name: string) => void;

sayHi = (name: string) =>
    console.log('Hi ' + name);

sayHi('Superuser'); // Hi Superuser
```
## Type Aliases 📝
Reduce code duplication:
```typescript

type StringOrNum = string | number;
let id: StringOrNum = 24;

```
## Interfaces 🎭
Describe objects with interfaces:

```typescript
interface Person {
    name: string;
    isProgrammer: boolean;
}

let person1: Person = {
    name: 'sudo',
    isProgrammer: false
};
```
For functions in interfaces:


```typescript
interface Speech {
    sayHi(name: string): string;
    sayBye(name: string): string;
}
let speech: Speech = {
    sayHi: function (name: string) {
        return 'Hi ' + name;
    },
    sayBye: function (name: string) { return 'Bye ' + name; }
};
```
## Extending Interfaces 🚀
Extend interfaces to create new ones:

```typescript
interface Animal {
    name: string;
}

interface Dog extends Animal {
    breed: string;
}
```
## DOM and Type Casting 🏰
Use the non-null operator (!) when TypeScript lacks access to the DOM:
```typescript
const form = document.getElementById('signup-form') as HTMLFormElement;
```
## Generics 🧬
Ensure type safety with unknown argument and return types:

```typescript
interface HasLength {
    length: number;
const logLength = <T extends HasLength>(a: T) => {
    console.log(a.length);
};
logLength('Hello'); // 5
logLength<number[]>([1, 2, 3]); // 3
```
## Enums 🏷️
Create sets of related values:

```typescript
enum ResourceType {
    BOOK,
    FILE,
    FILM,
}

ResourceType.BOOK; // 0
ResourceType.FILE; // 1
```
## Narrowing ⚡
Narrow down variable types for precision:

```typescript
let age = getUserAge();
// age // string | number

if (typeof age === 'string') {
    // age; // string
}
```
This guide covers the essentials of **TypeScript** for beginners. Dive deeper into advanced features and best practices to elevate your coding experience. Happy coding! 🚀👩‍💻