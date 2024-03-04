---
title: JavaScript Mastering Object Manipulation & References in JavaScript (Code Examples)
date: 2021-03-12
draft: false
description: the code examples provided, which can significantly improve learning outcomes for beginners who benefit from visual reinforcement. Highlighting the "Practical Approach" further positions the content as a valuable learning tool.
image: "/images/javascript_objects.png"
imageBig: "/images/javascript_strings.webp"
categories: ["javascript"]
authors: ["superuser"]
avatar: "/images/avatar.webp"
---

JavaScript, objects reign supreme as the foundation for data modeling. They empower you to represent complex information within your code, breathing life into applications that interact with real-world entities. This comprehensive guide, enriched with code examples, equips you to confidently create, access, modify, and delete properties within your objects, laying the groundwork for exceptional JavaScript development.

## Objects: Building the Blocks

Imagine a treasure chest overflowing with knowledge. Objects in JavaScript embody this concept, serving as structured collections of key-value pairs. These key-value pairs function like labeled compartments within the chest, where each key (a unique string identifier) acts as a label and the corresponding value represents the actual data you want to store.

Here's an example of an object representing a book:

```JavaScript
let book = {
title: "Become a frondtend developer",
author: "front-end developer",
genre: "web technolodgy",
yearPublished: 1979
};
```

In this instance, `title`, `author`, `genre`, and `yearPublished` are the object's properties, each holding a specific piece of information about the book.

### 1. Accessing the Treasure: Retrieving Data from Objects

Once you've meticulously crafted your object, it's time to unlock its secrets and extract the valuable data it holds. JavaScript offers a convenient mechanism known as dot notation to achieve this:

```JavaScript
objectName.propertyName
```

Replace `objectName` with the name of your object (e.g., `book`) and `propertyName` with the specific property you wish to access (e.g., `title`).

```JavaScript
let bookTitle = book.title;
console.log(bookTitle); // Outputs "TBecome a frondtend developer"
```

Here, we've retrieved the value associated with the `title` property of the `book` object and stored it in the `bookTitle` variable.

### 2. Adding New Treasures: Modifying Objects

As your program evolves, you might require additional information within your objects. JavaScript empowers you to seamlessly add new properties using the same dot notation employed for retrieval. Simply follow this structure:

```JavaScript
objectName.newPropertyName = value;
```

**Let's enhance our book object by incorporating a pageCount property:**

```JavaScript
book.pageCount = 224;
console.log(book); // The book object will now include a "pageCount" property with the value 224.
```

**Alternative Access Method:** Square Bracket Notation
While dot notation reigns supreme in most scenarios, there are times when square **bracket notation** becomes necessary. This syntax proves particularly useful when dealing with property names containing spaces or special characters. Here's the structure:

```JavaScript
objectName["propertyName"] = value;
```

Ensure to enclose the `propertyName` within quotation marks when using this approach.

For instance, to add a property named `favoriteQuote`(with a space) to the `book` object:

```JavaScript
book["favoriteQuote"] = "Don't panic.";
console.log(book); // The book object will now include a "favoriteQuote" property.
```

### 3. Removing Unwanted Items: Deleting Properties

The `delete` keyword empowers you to eliminate properties from your objects, fostering cleaner and more streamlined data structures. The syntax is straightforward:

```JavaScript
delete objectName.propertyName;
```

**Remember** that the `delete` operation returns `true`if the property deletion is successful, and `false` otherwise.

Imagine you no longer require the `yearPublished` information for the book. Here's how to **remove** it:

```JavaScript
delete book.yearPublished;
console.log(book); // The book object will no longer include the "yearPublished" property.
```

## Understanding References:

Obsject references can be tricky for JavaScript beginners.In this concept with code examples and demonstrates how to create true object copies.

### Object References in JavaScript

Imagine your computer's memory as a filing cabinet.
**Objects** reside in drawers, and variables hold references (labels) pointing to those drawers.
Multiple variables can reference the same object.
**Assignment** vs. **Copying**

```JavaScript
const animal = { species: "canis familiaris", genus: "corvus" };
let animal2 = animal; // Assignment, not copying!

animal2.genus = "ursus";
console.log(animal.genus); // Also "ursus", as they reference the same object
```

### 1. Object.assign()

`Object.assign()`built-in function constructs a new object and copies properties from one object to another.

```JavaScript
const trueCopy = Object.assign({}, animal);
trueCopy.genus = "felis";
console.log(animal.genus); // Still "ursus" (original unaffected)
```

### 2. Spread Operator (...)

**(ES6+)** unpacks object properties into a new object.

```JavaScript
const trueCopy = { ...animal };
trueCopy.genus = "felis";
console.log(animal.genus); // Still "ursus" (original unaffected)
```

### 3. JSON Parse Trick

This approach entails transforming the object into a JSON string and subsequently parsing it back into a new object using `JSON.parse()`.

```JavaScript
const jsonString = JSON.stringify(animal);
const trueCopy = JSON.parse(jsonString);

console.log(trueCopy); // { species: "canis familiaris", genus: "ursus" }
console.log(animal); // { species: "canis familiaris
```

By understanding object references and using these techniques, you can effectively manage object data in your JavaScript applications.
