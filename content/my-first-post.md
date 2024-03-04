---
title: 'Unlocking the Power of CRUD Operations: Create, Update[Operators], Delete, and Read Explained 🌱'
date: Dec 10 2024
draft: false
description : "Dive into the art of CRUD operations in our guide. From creating and updating to deleting and reading data, master essential techniques for optimal database management. Perfect for developers seeking efficiency and precision in data manipulation"
image: "/images/mongoDb.webp"
imageBig: "/images/1b.webp"
categories : ["MongoDB","DataBase",]
authors : ["superuser"]
avatar : "/images/avatar.webp"
---

Creating documents in MongoDB is a fundamental part of the database's functionality. Let's explore the various ways to add data:
Welcome to the world of MongoDB, where we'll unravel the magic behind CRUD operations - Create, Read, Update, and Delete. Let's dive in and make MongoDB a breeze for beginners! 🚀

##  Create - Bringing Data to Life
Creating records in MongoDB is a piece of cake. You can use insert or its modern counterparts:

```javascript

// Single record
db.people.insertOne({ name: 'Tom', age: 28 });

// Multiple records
db.people.insertMany([
  { name: 'Tom', age: 28 },
  { name: 'John', age: 25 },
  { name: 'Kathy', age: 23 }
]);
```
> ⚠️ Note: insert is being phased out; prefer insertOne and insertMany for newer versions.

## Read - Unveiling the Data
Fetching data is where the real excitement begins. Whether finding one or many, MongoDB has your back:

```javascript
// Find all with a specific name
db.people.find({ name: 'Tom' });

// Find the first one
db.people.findOne({ name: 'Tom' });

// Specify fields to return (exclude _id, include age)
db.people.find({ name: 'Tom' }, { _id: 0, age: 1 });

// Find sub-records like 'address.country'
db.people.find({ 'address.country': 'US' });

```
> 🌈 Pro Tip: Don't forget the .pretty() method for a clean, readable JSON result.
## Delete - Bidding Farewell
Deleting documents is a breeze, whether one or many:

```javascript

// Delete all matching documents
db.people.deleteMany({ name: 'Tom' });

// Delete one matching document
db.people.deleteOne({ name: 'Tom' });

```
> 🗑️ Caution: Use with care; no one likes accidentally deleting all their data!
>
## Update - The Shape-Shifting Wizardry
Updating in MongoDB is versatile, from updating entire documents to specific fields:

```javascript


// Update entire object
db.people.updateOne({ name: 'Tom' }, { age: 29, name: 'Tom' });

// Update a single field (e.g., age)
db.people.update({ name: 'Tom' }, { $set: { age: 29 } });

// Update multiple documents at once
db.people.update({ name: 'Tom' }, { $set: { age: 29 } }, { multi: true });
```
> 🚀 MongoDB 3.2+ Feature: updateOne and updateMany for more granular control.

## Update of Embedded Documents
Dive into the fascinating realm of updating embedded documents in MongoDB. Let's decode the secrets behind the positional operator $:

### Update an Element in Array
Consider the schema : **{name: 'Tom', age: 28, marks: [50, 60, 70]}**.

Update Tom's marks to 55 where marks are 50:

```javascript

db.people.update({ name: "Tom", marks: 50 }, { "$set": { "marks.$": 55 } })
```
### Update Nested Object in Array
Now, let's venture into more complex arrays:
```javascript
{name: 'Tom', age: 28, marks: [
  {subject: "English", marks: 90},
  {subject: "Maths", marks: 100},
  {subject: "Computes", marks: 20}
]}
```
Update Tom's **English** marks to **85:**
```javascript
db.people.update(
  { name: "Tom", "marks.subject": "English" },
  { "$set": {"marks.$.marks": 85} }
)
```
**Explanation**: Identify the position with {name: "Tom", "marks.subject": "English"}, and use $ to update in that position.

### Update Values in an Array
Consider the collection 'students':
```javascript
{ "_id": 1, "grades": [80, 85, 90] }
{ "_id": 2, "grades": [88, 90, 92] }
{ "_id": 3, "grades": [85, 100, 90] }
```
Update 80 to 82 in the grades array in the first document:
```javascript
db.students.update(
  { _id: 1, grades: 80 },
  { $set: { "grades.$": 82 } }
)
  ```
### More Update Operators
MongoDB unleashes a plethora of operators for versatile updates:

#### $push - Adding to Arrays
```javascript
db.people.update({ name: 'Tom' }, { $push: { nicknames: 'Tommy' } })
```
This adds 'Tommy' to the nicknames array in Tom's document.

#### $pull - Removing from Arrays
```javascript

db.people.update({ name: 'Tom' }, { $pull: { nicknames: 'Tommy' } })
```
This removes 'Tommy' from the nicknames array in Tom's document.

#### $pop - Removing First or Last Value
```javascript

db.people.update({ name: 'Tom' }, { $pop: { siblings: -1 } })
// Removes the first value from the siblings array

db.people.update({ name: 'Tom' }, { $pop: { siblings: 1 } })
// Removes the last value from the siblings array
```
### "multi" Parameter for Bulk Updates

When updating multiple documents, set the multi option to true:
```javascript
db.mycol.update(
  { 'title': 'MongoDB Overview' },
  { $set: { 'title': 'New MongoDB Tutorial' } },
  { multi: true }
)
```
Unleash the power of MongoDB updates, and watch your data evolve! 🚀✨

Ready to embark on your MongoDB journey? CRUD operations are your trusty companions. Stay tuned for more MongoDB marvels! 🌍🚀