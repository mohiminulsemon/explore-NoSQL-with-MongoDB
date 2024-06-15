# explore-NoSQL-with-MongoDB
# Explore MongoDB Queries

## Introduction:
MongoDB is a flexible, scalable, and powerful document-oriented database system widely used for data storage and retrieval.

## Installation Instructions:

1. **MongoDB Compass:** Download and install from [here](https://www.mongodb.com/try/download/compass).
2. **NoSQL Booster:** Download and install from [here](https://www.nosqlbooster.com/downloads).

## Basic Methods for Data Manipulation:

### Inserting Data:

Use `insert()` and `insertOne()` methods to insert data into MongoDB collections.

### Retrieving Data:

Operators like `$eq`, `$neq`, `$gt`, `$lt`, `$gte`, `$lte` are used for data retrieval.

### Operators for Data Retrieval:

- `$in` and `$nin`: Match values in or not in a specified list.
- `$and` and `$or`: Combine multiple conditions or find documents matching at least one condition.
- `$exists`, `$type`, `$size`: Check for field existence, data type, and array size.
- `$all` and `$elemMatch`: Match documents containing all specified elements or elements meeting specific criteria.
- `$set`, `$addToSet`, `$push`: Update field value, add elements to an array, or push elements to an array.
- `$unset`, `$pop`, `$pull`, `$pullAll`: Remove field, last array element, specific array elements, or all occurrences of specified values.

### Updating Data:

Use `updateOne()` or `updateMany()` methods to update documents in MongoDB collections.

### Deleting Data:

Use `deleteOne()` or `deleteMany()` methods to delete documents from MongoDB databases.

---



<details>
<summary>
Install MongoDB Compass & No SQL Booster ( Windows) and how to create database
</summary>
<br >

**Installing MongoDB Compass:**

1. Visit the MongoDB Compass download page: https://www.mongodb.com/try/download/compass
2. Click on the "Download for Windows" button.
3. Once the download is complete, double-click the downloaded file to start the installation process.
4. Follow the on-screen instructions to complete the installation. MongoDB Compass will be installed on your system.

**Installing NoSQL Booster:**

1. Visit the NoSQL Booster download page: https://www.nosqlbooster.com/downloads
2. Click on the "Download for Windows" button.
3. Once the download is complete, double-click the downloaded file to start the installation process.
4. Follow the on-screen instructions to complete the installation. NoSQL Booster will be installed on your system.

**Creating a Database and Collection:**

1. Open MongoDB Compass.
2. Click on the "Connect" button to connect to your MongoDB server. If you don't have a server set up, you can create a local server by clicking on "New Connection" and choosing "localhost" as the hostname.
3. Once connected, click on the "Create Database" button.
4. Enter a name for your database and click "Create Database".
5. With the database selected, click on the "Create Collection" button.
6. Enter a name for your collection and click "Create Collection".

</details> 

<details> 
<summary>  
What are the basic methods for inserting data into a MongoDB collection?

</summary> 
 <br>


The basic methods for inserting data into a MongoDB collection are using the insert() and insertOne() methods. 

1- ডাটা insert ->findOne-> finDMany 

2- Field Filtering কিভাবে করতে হয় db.test.find({gender:"Female"}).project({name:1})

  
 </details>


<details>
<summary>
What operators can we use for data retrieval in MongoDB?

</summary>
<br > 

We can use operators like $eq, $neq, $gt, $lt, $gte, $lte for data retrieval in MongoDB.

MongoDB ডেটা পাওয়ার জন্য অপারেটর হলো $eq, $neq, $gt, $lt, $gte, $lte ইত্যাদি।

```js 
db.test.find({age: {$gte: 30}})
db.collection.find({ age: { $eq: 30 } }); 
```
</details> 

<details>
<summary>
What do $in and $nin operators do?




</summary>
<br > 
The $in operator is used to find values matching any in a specified list, while the $nin operator is used to find values not matching any in a specified list

$in এবং $nin অপারেটর কি কাজ করে?

$in অপারেটর ব্যবহার করে একটি ফিল্ডের মানগুলির মধ্যে নির্দিষ্ট মানগুলির মধ্যে সনাক্ত করা হয়, যেমন [1, 2, 3]। $nin অপারেটর ব্যবহার করে একটি ফিল্ডের মানগুলির মধ্যে নির্দিষ্ট মানগুলির মধ্যে যার কোনো ম্যাচ নেই সেগুলি সনাক্ত করা হয়। 

```js
db.collection.find({ status: { $in: ["active", "pending"] } });

db.collection.find({ status: "active", category: "electronics" });

db.collection.find({ status: { $nin: ["completed", "cancelled"] } });



db.test.find({age: {$gte: 18, $lt:30 }},{age:1}).sort({ age:1 }) // Implicit And Condition
```

</details> 

<details>
<summary>
How do we use the $and and $or operators?




</summary>
<br > 
The $and operator combines multiple conditions, while the $or operator finds documents matching at least one condition.


$and এবং $or অপারেটর কিভাবে ব্যবহার করা হয়?$and অপারেটর ব্যবহার করে একই সময়ে একাধিক শর্ত যোগান করা যায়, যেমন {$and: [{field1: value1}, {field2: value2}]}। $or অপারেটর ব্যবহার করে একটি ফিল্ডের মানগুলির মধ্যে কোনো একটি ম্যাচ করতে পারে,

```js 

যেমন {$or: [{field1: value1}, {field2: value2}]}।

// db.test.find({age: {$ne: 15, $lte:30}}) 

// explicit operator 
db.test.find({ 

  $and: [

  {age: {$ne: 10}}, 

  {age: {$lte: 30}}


  ] }).project({age:1}).sort({ age:1 })


db.test.find({"skills.name": {$in: ["JAVASCRIPT", "PYTHON"]} }).project({ interests:1, skills:1}).sort({ interests: 1 }) 
```
</details> 

<details>
<summary>
What do $exists, $type, and $size operators do?



</summary>
<br > 
$exists অপারেটর ব্যবহার করে একটি ফিল্ড বা কোনো নির্দিষ্ট ফিল্ডের মান অস্তিত্বের তথ্য দেখা যায়। $type অপারেটর ব্যবহার করে ফিল্ডের ডেটা টাইপ চেক করা যায়। $size অপারেটর ব্যবহার করে একটি অ্যারের সাইজ চেক করা যায়।

The $exists operator checks for the existence of a field, $type checks the data type of a field, and $size checks the size of an array.
</details> 

<details>  
<summary>
What Do $All And $ElemMatch Operators Do? 

</summary>
<br >

The $all operator matches documents where an array contains all the specified elements, while the $elemMatch operator matches documents where an array element meets specified criteria. 

$all এবং $elemMatch অপারেটর কি কাজ করে? 

$all অপারেটর ব্যবহার করে একটি অ্যারের সকল মানের মধ্যে নির্দিষ্ট মানগুলির ম্যাচ করতে হয়। $elemMatch অপারেটর ব্যবহার করে অ্যারের একটি অংশের মান নির্দিষ্ট শর্ত সনাক্ত করা যায়।
</details> 

<details>
<summary>
What Do $Set, $AddToSet, And $Push Operators Do?

</summary>
<br >
$set, $addToSet, $push অপারেটর কি কাজ করে?

$set অপারেটর ব্যবহার করে বিদ্যমান ফিল্ডের মান আপডেট করা যায়। $addToSet অপারেটর ব্যবহার করে অ্যারের নতুন উপাদান যোগ করা যায়, তবে ইত্যাদি মূলত ইউনিক উপাদান যোগ করা হয়। $push অপারেটর ব্যবহার করে অ্যারের উপাদান যোগ করা যায়।



The $set operator updates the value of a field, $addToSet adds elements to an array if they are not already present, and $push adds elements to an array regardless of uniqueness.


```js 

db.test.updateOne(

  { _id: ObjectId("663cef3a2ce741159a405ac0") },

  {

    $push: {

      interests: { $each: ["Cook","driving"]}

    }})
```

</details> 


<details>
<summary>
What do $unset, $pop, $pull, and $pullAll operators do?
</summary>
<br >

The $unset operator removes a field, $pop removes the last element of an array, $pull removes elements that match a condition from an array, and $pullAll removes all occurrences of specified values from an array. 

$unset, $pop, $pull, $pullAll অপারেটর কি কাজ করে?
$unset অপারেটর ব্যবহার করে নির্দিষ্ট ফিল্ডের মান অপসারণ করা যায়। $pop অপারেটর ব্যবহার করে অ্যারের শেষের উপাদান অপসারণ করা যায়। $pull অপারেটর ব্যবহার করে নির্দিষ্ট মানগুলির সাথে ম্যাচিং অ্যারের উপাদান অপসারণ করা যায়। $pullAll অপারেটর ব্যবহার করে সম্পূর্ণ অ্যারে অপসারণ করা যায়। 

```js 

db.test.updateOne(

  { _id: ObjectId("663cef3a2ce741159a405ac0") },

  {

    $push: {

      interests: { $each: ["Cook","driving"]}

    }})

```
</details> 
 

<details> 
<summary>
set অপারেটরের বিষয়ে আরও কিছু বলুন।
</summary>
<br >
 
set অপারেটর ব্যবহার করে বিদ্যমান ফিল্ডের মান আপডেট করা যায়, এটি মূলত একটি ফিল্ডের মান পরিবর্তনের জন্য ব্যবহার করা হয়।


```js 
db.collection.updateOne({ name: "John" }, { $unset: { age: "" } });

//  update in array 
db.collection.updateOne(
  { "_id": 1, "items.name": "banana" },
  { "$set": { "items.$.quantity": 15 } }
);


```
</details> 





<details>
<summary>
কিভাবে MongoDB ডেটাবেস থেকে ডকুমেন্ট মুছে ফেলা যায়?
</summary>
<br >


MongoDB ডেটাবেস থেকে ডকুমেন্ট মুছে ফেলতে আমরা deleteMany() বা deleteOne() মেথড ব্যবহার করতে পারি। 

```js 
db.collection.deleteOne({ name: "John" });

```
</details> 

---------




## MongoDB Queries Cheat Sheet

<table>
  <thead>
    <tr>
      <th>Operation</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Find documents</td>
      <td><code>find()</code></td>
      <td><code>db.collection.find({ age: 30 })</code></td>
    </tr>
    <tr>
      <td>Find one document</td>
      <td><code>findOne()</code></td>
      <td><code>db.collection.findOne({ email: "example@example.com" })</code></td>
    </tr>
    <tr>
      <td>Insert a document</td>
      <td><code>insertOne()</code></td>
      <td><code>db.collection.insertOne({ name: "John", age: 25 })</code></td>
    </tr>
    <tr>
      <td>Insert multiple documents</td>
      <td><code>insertMany()</code></td>
      <td><code>db.collection.insertMany([{ name: "Alice", email: "alice@example.com" }, { name: "Bob", email: "bob@example.com" }])</code></td>
    </tr>
    <tr>
      <td>Update a document</td>
      <td><code>updateOne()</code></td>
      <td><code>db.collection.updateOne({ name: "John" }, { $set: { age: 30 } })</code></td>
    </tr>
    <tr>
      <td>Update multiple documents</td>
      <td><code>updateMany()</code></td>
      <td><code>db.collection.updateMany({ age: { $lt: 18 } }, { $set: { status: "minor" } })</code></td>
    </tr>
    <tr>
      <td>Replace a document</td>
      <td><code>replaceOne()</code></td>
      <td><code>db.collection.replaceOne({ field_name: value_name }, { new_document })</code></td>
    </tr>
    <tr>
      <td>Delete a document</td>
      <td><code>deleteOne()</code></td>
      <td><code>db.collection.deleteOne({ name: "John" })</code></td>
    </tr>
    <tr>
      <td>Delete multiple documents</td>
      <td><code>deleteMany()</code></td>
      <td><code>db.collection.deleteMany({ status: "inactive" })</code></td>
    </tr>
    <tr>
      <td>Count documents</td>
      <td><code>countDocuments()</code></td>
      <td><code>db.collection.countDocuments({ age: { $gte: 18 } })</code></td>
    </tr>
    <tr>
      <td>Aggregate documents</td>
      <td><code>aggregate()</code></td>
      <td><code>db.collection.aggregate([{ $match: { age: { $gte: 18 } } }, { $group: { _id: "$age", count: { $sum: 1 } } }])</code></td>
    </tr>
  </tbody>
</table>

----


# MongoDB aggregation stages

**1. $Match and $Project:**
   

<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$match</td>
    <td> <code> { $match: { age: { $gte: 18 } } }  </code> </td>
      <td>Selects documents with age greater than or equal to 18.</td>
    </tr>
    <tr>
      <td>$project</td>
      <td> <code> { $project: { _id: 0, name: 1 } }</code> </td>
      <td>Projects only the 'name' field excluding '_id'.</td>
    </tr>
  </tbody>
</table>


**2. $AddFields, $Out, and $Merge:**
   

<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$addFields</td>
      <td> <code>  { $addFields: { fullName: { $concat: ["$firstName", " ", "$lastName"] } } }</code></td>
      <td>Creates a new field 'fullName' by concatenating 'firstName' and 'lastName'.</td>
    </tr>
    <tr>
      <td>$out</td>
      <td><code>{ $out: "new_collection" }  </code> </td>
      <td>Writes the result of the aggregation pipeline to a new collection.</td>
    </tr>
  </tbody>
</table>


**3. $Group, $Sum, and $Push:**
   

<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$group</td>
      <td> <code>{ $group: { _id: "$category", total: { $sum: "$quantity" } } } </code></td>
      <td>Groups documents by 'category' and calculates total quantity for each category.</td>
    </tr>
    <tr>
      <td>$sum</td>
      <td> <code> { $sum: "$amount" } </code></td>
      <td>Calculates the sum of values in a field across all documents.</td>
    </tr>
  </tbody>
</table>


**4. $Group and $Project:**
   

<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$group</td>
      <td><code> { $group: { _id: "$category", avgPrice: { $avg: "$price" } } } </code>  </td>
      <td>Groups documents by 'category' and calculates average price for each category.</td>
    </tr>
    <tr>
      <td>$project</td>
      <td> <code> </code> { $project: { category: 1, avgPrice: 1 } }</td>
      <td>Projects 'category' and 'avgPrice' fields.</td>
    </tr>
  </tbody>
</table>


**5. $Group with $Unwind:**
   

<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$group</td>
      <td><code> { $group: { _id: "$category", items: { $push: "$name" } } }</code> </td>
      <td>Groups documents by 'category' and creates an array of 'name' field values for each category.</td>
    </tr>
    <tr>
      <td>$unwind</td>
      <td><code>{ $unwind: "$items" } </code> </td>
      <td>Deconstructs the 'items' array created by $group stage.</td>
    </tr>
  </tbody>
</table>

**6. $Bucket, $Sort, and $Limit:**
   

<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$bucket</td>
      <td><code>{ $bucket: { groupBy: "$price", boundaries: [0, 100, 200], default: "Other" } } </code> </td>
      <td>Buckets documents based on 'price' field values.</td>
    </tr>
    <tr>
      <td>$sort</td>
      <td><code> { $sort: { price: -1 } }</code> </td>
      <td>Sorts documents by 'price' field in descending order.</td>
    </tr>
    <tr>
      <td>$limit</td>
      <td><code> { $limit: 5 }</code> </td>
      <td>Limits the number of documents in the output to 5.</td>
    </tr>
  </tbody>
</table>

**7. $Facet, Multiple Pipeline:**
   
<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$facet</td>
      <td><code> { $facet: { categoryCount: [ { $group: { _id: "$category", count: { $sum: 1 } } } ] } }</code> </td>
      <td>Allows multiple pipelines to be executed within a single stage.</td>
    </tr>
  </tbody>
</table>

**8. $Lookup Stage, Embedding Vs Referencing:**
   
<table>
  <thead>
    <tr>
      <th>Stage</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$lookup</td>
      <td><code> { $lookup: { from: "orders", localField: "productId", foreignField: "_id", as: "orderDetails" } } </code></td>
      <td>Performs a left outer join to another collection.</td>
    </tr>
  </tbody>
</table>

**9.  Indexing, COLLSCAN Vs IXSCAN:**
   
<table>
  <thead>
    <tr>
      <th>Topic</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Indexing</td>
      <td><code>db.collection.createIndex({ field: 1 }) </code> </td>
      <td>Creates an ascending index on the 'field'.</td>
    </tr>
  </tbody>
</table>

**10. Compound Index and Text Index:**
   

<table>
  <thead>
    <tr>
      <th>Topic</th>
      <th>Method</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Compound Index</td>
      <td><code>db.collection.createIndex({ field1: 1, field2: -1 }) </code> </td>
      <td>Creates a compound index on 'field1' (ascending) and 'field2' (descending).</td>
    </tr>
    <tr>
      <td>Text Index</td>
      <td><code>db.collection.createIndex({ "$**": "text" }) </code> </td>
      <td>Creates a text index on all string fields in the collection.</td>
    </tr>
  </tbody>
</table>
