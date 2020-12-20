# courses
course on mongodb
# **MongoDB**

This course contains the basic and advanced idea of mongoDb. This document will contain the material for first three weeks .

You will be familiarized with basics to advanced level of MONGODB

Top of Form

Bottom of Form

MongoDB is an open-source document database and leading NoSQL database. MongoDB is written in C++. This tutorial will give you great understanding on MongoDB concepts needed to create and deploy a highly scalable and performance-oriented database.

This material is designed for Software Professionals who are willing to learn MongoDB Database in simple and easy steps. It will throw light on MongoDB concepts and after completing this tutorial you will be at an intermediate level of expertise, from where you can take yourself at higher level of expertise.

# Prerequisites:

Before proceeding with this tutorial, you should have a basic understanding of database, text editor and execution of programs, etc. Because we are going to develop high performance database, so it will be good if you have an understanding on the basic concepts of Database (RDBMS).

**OVERVIEW:**

MongoDB is a cross-platform, document oriented database that provides, high performance, high availability, and easy scalability. MongoDB works on concept of collection and document.

## Database

Database is a physical container for collections. Each database gets its own set of files on the file system. A single MongoDB server typically has multiple databases.

## Collection

Collection is a group of MongoDB documents. It is the equivalent of an RDBMS table. A collection exists within a single database. Collections do not enforce a schema. Documents within a collection can have different fields. Typically, all documents in a collection are of similar or related purpose.

## Document

A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure, and common fields in a collection&#39;s documents may hold different types of data.

The following table shows the relationship of RDBMS terminology with MongoDB.

| **RDBMS** | **MongoDB** |
| --- | --- |
| Database | Database |
| Table | Collection |
| Tuple/Row | Document |
| column | Field |
| Table Join | Embedded Documents |
| Primary Key | Primary Key (Default key \_id provided by MongoDB itself) |
| **Database Server and Client** |
| mysqld/Oracle | mongod |
| mysql/sqlplus | mongo |

## **Sample Document**

Following example shows the document structure of a blog site, which is simply a comma separated key value pair.

{

\_id:ObjectId(7df78ad8902c)

title:&#39;MongoDB Overview&#39;,

description:&#39;MongoDB is no sql database&#39;,

by `cognizance&#39;,

tags:[&#39;mongodb&#39;,&#39;database&#39;,&#39;NoSQL&#39;],

likes:100,

comments:[

{

user:&#39;user1&#39;,

message:&#39;My first comment&#39;,

dateCreated:newDate(2011,1,20,2,15),

like:0

},

{

user:&#39;user2&#39;,

message:&#39;My second comments&#39;,

dateCreated:newDate(2011,1,25,7,45),

like:5

}

]

}

**\_id**  is a 12 bytes hexadecimal number which assures the uniqueness of every document. You can provide \_id while inserting the document. If you don&#39;t provide then MongoDB provides a unique id for every document. These 12 bytes first 4 bytes for the current timestamp, next 3 bytes for machine id, next 2 bytes for process id of MongoDB server and remaining 3 bytes are simple incremental VALUE.

Any relational database has a typical schema design that shows number of tables and the relationship between these tables. While in MongoDB, there is no concept of relationship.

## Advantages of MongoDB over RDBMS

- **Schema less**  − MongoDB is a document database in which one collection holds different documents. Number of fields, content and size of the document can differ from one document to another.
- Structure of a single object is clear.
- No complex joins.
- Deep query-ability. MongoDB supports dynamic queries on documents using a document-based query language that&#39;s nearly as powerful as SQL.
- Tuning.
- **Ease of scale-out**  − MongoDB is easy to scale.
- Conversion/mapping of application objects to database objects not needed.
- Uses internal memory for storing the (windowed) working set, enabling faster access of data.

## Why Use MongoDB?

- **Document Oriented Storage**  − Data is stored in the form of JSON style documents.
- Index on any attribute
- Replication and high availability
- Auto-Sharding
- Rich queries
- Fast in-place updates
- Professional support by MongoDB

## Where to Use MongoDB?

- Big Data
- Content Management and Delivery
- Mobile and Social Infrastructure
- User Data Management
- Data Hub

## Data Model Design

MongoDB provides two types of data models: — Embedded data model and Normalized data model. Based on the requirement, you can use either of the models while preparing your document.

### _ **Embedded Data Model** _

In this model, you can have (embed) all the related data in a single document, it is also known as de-normalized data model.

For example, assume we are getting the details of employees in three different documents namely, Personal\_details, Contact and, Address, you can embed all the three documents in a single one as shown below −

{

\_id:,

Emp\_ID:&quot;10025AE336&quot;

Personal\_details:{

First\_Name:&quot;Radhika&quot;,

Last\_Name:&quot;Sharma&quot;,

Date\_Of\_Birth:&quot;1995-09-26&quot;

},

Contact:{

e-mail:&quot;radhika\_sharma.123@gmail.com&quot;,

phone:&quot;9900990099&quot;

},

Address:{

city:&quot;Hyderabad&quot;,

Area:&quot;Madapur&quot;,

State:&quot;Telangana&quot;

}

}

### **Normalized Data Model**

In this model, you can refer the sub documents in the original document, using references. For example, you can re-write the above document in the normalized model as:

**Employee:**

{

\_id:\&lt;ObjectId101\&gt;,

Emp\_ID:&quot;10025AE336&quot;

}

**Personal\_details:**

{

\_id:\&lt;ObjectId102\&gt;,

empDocID:&quot; ObjectId101&quot;,

First\_Name:&quot;Radhika&quot;,

Last\_Name:&quot;Sharma&quot;,

Date\_Of\_Birth:&quot;1995-09-26&quot;

}

**Contact:**

{

\_id:\&lt;ObjectId103\&gt;,

empDocID:&quot; ObjectId101&quot;,

e-mail:&quot;radhika\_sharma.123@gmail.com&quot;,

phone:&quot;9848022338&quot;

}

**Address:**

{

\_id:\&lt;ObjectId104\&gt;,

empDocID:&quot; ObjectId101&quot;,

city:&quot;Hyderabad&quot;,

Area:&quot;Madapur&quot;,

State:&quot;Telangana&quot;

}

## Considerations while designing Schema in MongoDB

- Design your schema according to user requirements.
- Combine objects into one document if you will use them together. Otherwise separate them (but make sure there should not be need of joins).
- Duplicate the data (but limited) because disk space is cheap as compare to compute time.
- Do joins while write, not on read.
- Optimize your schema for most frequent use cases.
- Do complex aggregation in the schema.

## Example

Suppose a client needs a database design for his blog/website and see the differences between RDBMS and MongoDB schema design. Website has the following requirements.

- Every post has the unique title, description and url.
- Every post can have one or more tags.
- Every post has the name of its publisher and total number of likes.
- Every post has comments given by users along with their name, message, data-time and likes.
- On each post, there can be zero or more comments.

In RDBMS schema, design for above requirements will have minimum three tables.

![](RackMultipart20201220-4-1b32190_html_16e54bca2310c3cc.png)

While in MongoDB schema, design will have one collection post and the following structure −

{

\_id: POST\_ID

title: TITLE\_OF\_POST,

description: POST\_DESCRIPTION,

by: POST\_BY,

url: URL\_OF\_POST,

tags:[TAG1, TAG2, TAG3],

likes: TOTAL\_LIKES,

comments:[

{

user:&#39;COMMENT\_BY&#39;,

message: TEXT,

dateCreated: DATE\_TIME,

like: LIKES

},

{

user:&#39;COMMENT\_BY&#39;,

message: TEXT,

dateCreated: DATE\_TIME,

like: LIKES

}

]

}

So while showing the data, in RDBMS you need to join three tables and in MongoDB, data will be shown from one collection only.

## _The use Command:_

MongoDB  **use DATABASE\_NAME**  is used to create database. The command will create a new database if it doesn&#39;t exist, otherwise it will return the existing database.

### Syntax

Basic syntax of  **use DATABASE**  statement is as follows −

use DATABASE\_NAME

### **Example**

If you want to use a database with name  **\&lt;mydb\&gt;** , then  **use DATABASE**  statement would be as follows −

\&gt;use mydb

switched to db mydb

To check your currently selected database, use the command  **db**

\&gt;db

mydb

If you want to check your databases list, use the command  **show dbs**.

\&gt;show dbs

local 0.78125GB

test 0.23012GB

Your created database (mydb) is not present in list. To display database, you need to insert at least one document into it.

\&gt;db.movie.insert({&quot;name&quot;:&quot;cognizance&quot;})

\&gt;show dbs

local0.78125GB

mydb 0.23012GB

test 0.23012GB

In MongoDB default database is test. If you didn&#39;t create any database, then collections will be stored in test database.

## The dropDatabase() Method:

MongoDB **db.dropDatabase()** command is used to drop a existing database.

### **Syntax**

Basic syntax of **dropDatabase()** command is as follows −

db.dropDatabase()

This will delete the selected database. If you have not selected any database, then it will delete default &#39;test&#39; database.

### Example

First, check the list of available databases by using the command,  **show dbs**.

\&gt;show dbs

local0.78125GB

mydb 0.23012GB

test 0.23012GB

\&gt;

If you want to delete new database  **\&lt;mydb\&gt;** , then **dropDatabase()** command would be as follows −

\&gt;use mydb

switched to db mydb

\&gt;db.dropDatabase()

\&gt;{&quot;dropped&quot;:&quot;mydb&quot;,&quot;ok&quot;:1}

\&gt;

Now check list of databases.

\&gt;show dbs

local0.78125GB

test 0.23012GB

\&gt;

##

## ThecreateCollection() Method:

MongoDB **db.createCollection(name, options)** is used to create collection.

### **Syntax**

Basic syntax of **createCollection()** command is as follows −

db.createCollection(name, options)

In the command,  **name**  is name of collection to be created.  **Options**  is a document and is used to specify configuration of collection.

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| Name | String | Name of the collection to be created |
| Options | Document | (Optional) Specify options about memory size and indexing |

Options parameter is optional, so you need to specify only the name of the collection. Following is the list of options you can use −

| **Field** | **Type** | **Description** |
| --- | --- | --- |
| capped | Boolean | (Optional) If true, enables a capped collection. Capped collection is a fixed size collection that automatically overwrites its oldest entries when it reaches its maximum size.  **If you specify true, you need to specify size parameter also.** |
| autoIndexId | Boolean | (Optional) If true, automatically create index on \_id field.s Default value is false. |
| size | number | (Optional) Specifies a maximum size in bytes for a capped collection.  **If capped is true, then you need to specify this field also.** |
| max | number | (Optional) Specifies the maximum number of documents allowed in the capped collection. |

While inserting the document, MongoDB first checks size field of capped collection, then it checks max field.

### **Examples**

Basic syntax of **createCollection()** method without options is as follows −

\&gt;use test

switched to db test

\&gt;db.createCollection(&quot;mycollection&quot;)

{&quot;ok&quot;:1}

\&gt;

You can check the created collection by using the command  **show collections**.

\&gt;show collections

mycollection

system.indexes

The following example shows the syntax of **createCollection()** method with few important options −

\&gt; db.createCollection(&quot;mycol&quot;,{ capped :true, autoIndexID :true, size :6142800, max :10000}){

&quot;ok&quot;:0,

&quot;errmsg&quot;:&quot;BSON field &#39;create.autoIndexID&#39; is an unknown field.&quot;,

&quot;code&quot;:40415,

&quot;codeName&quot;:&quot;Location40415&quot;

}

\&gt;

In MongoDB, you don&#39;t need to create collection. MongoDB creates collection automatically, when you insert some document.

\&gt;db.cognizance.insert({&quot;name&quot;:&quot;cognizance&quot;}),

WriteResult({&quot;nInserted&quot;:1})

\&gt;show collections

mycol

mycollection

system.indexes

cognizance

\&gt;

##

## The drop() Method:

MongoDB&#39;s **db.collection.drop()** is used to drop a collection from the database.

### **Syntax**

Basic syntax of **drop()** command is as follows −

db.COLLECTION\_NAME.drop()

###

### **Example**

First, check the available collections into your database  **mydb**.

\&gt;use mydb

switched to db mydb

\&gt;show collections

mycol

mycollection

system.indexes

cognizance

\&gt;

Now drop the collection with the name  **mycollection**.

\&gt;db.mycollection.drop()

true

\&gt;

Again check the list of collections into database.

\&gt;show collections

mycol

system.indexes

cognizance

\&gt;

drop() method will return true, if the selected collection is dropped successfully, otherwise it will return false.

**DATATYPES:**

MongoDB supports many datatypes. Some of them are −

- **String**  − This is the most commonly used datatype to store the data. String in MongoDB must be UTF-8 valid.
- **Integer**  − This type is used to store a numerical value. Integer can be 32 bit or 64 bit depending upon your server.
- **Boolean**  − This type is used to store a boolean (true/ false) value.
- **Double**  − This type is used to store floating point values.
- **Min/ Max keys**  − This type is used to compare a value against the lowest and highest BSON elements.
- **Arrays**  − This type is used to store arrays or list or multiple values into one key.
- **Timestamp**  − ctimestamp. This can be handy for recording when a document has been modified or added.
- **Object**  − This datatype is used for embedded documents.
- **Null**  − This type is used to store a Null value.
- **Symbol**  − This datatype is used identically to a string; however, it&#39;s generally reserved for languages that use a specific symbol type.
- **Date ** − This datatype is used to store the current date or time in UNIX time format. You can specify your own date time by creating object of Date and passing day, month, year into it.
- **Object ID**  − This datatype is used to store the document&#39;s ID.
- **Binary data**  − This datatype is used to store binary data.
- **Code**  − This datatype is used to store JavaScript code into the document.
- **Regular expression**  − This datatype is used to store regular expression.

##

## **The insert() Method:**

To insert data into MongoDB collection, you need to use MongoDB&#39;s **insert()** or **save()** method.

### **Syntax**

The basic syntax of **insert()** command is as follows −

\&gt;db.COLLECTION\_NAME.insert(document)

### **Example**

\&gt; db.users.insert({

... \_id :ObjectId(&quot;507f191e810c19729de860ea&quot;),

... title:&quot;MongoDB Overview&quot;,

... description:&quot;MongoDB is no sql database&quot;,

...by:&quot;Cognizance&quot;,

... tags:[&#39;mongodb&#39;,&#39;database&#39;,&#39;NoSQL&#39;],

... likes:100

...})

WriteResult({&quot;nInserted&quot;:1})

\&gt;

Here  **mycol**  is our collection name, as created in the previous chapter. If the collection doesn&#39;t exist in the database, then MongoDB will create this collection and then insert a document into it.

In the inserted document, if we don&#39;t specify the \_id parameter, then MongoDB assigns a unique ObjectId for this document.

\_id is 12 bytes hexadecimal number unique for every document in a collection. 12 bytes are divided as follows −

\_id: ObjectId(4 bytes timestamp, 3 bytes machine id, 2 bytes process id, 3 bytes incrementer)

You can also pass an array of documents into the insert() method as shown below:.

\&gt; db.createCollection(&quot;post&quot;)

\&gt; db.post.insert([

{

title:&quot;MongoDB Overview&quot;,

description:&quot;MongoDB is no SQL database&quot;,

by:&quot;cognizance&quot;,

url:&quot;http://www.tutorialspoint.com&quot;,

tags:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],

likes:100

},

{

title:&quot;NoSQL Database&quot;,

description:&quot;NoSQL database doesn&#39;t have tables&quot;,

by:&quot;cognizance&quot;,

url:&quot;http://www.tutorialspoint.com&quot;,

tags:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],

likes:20,

comments:[

{

user:&quot;user1&quot;,

message:&quot;My first comment&quot;,

dateCreated:newDate(2013,11,10,2,35),

like:0

}

]

}

])

BulkWriteResult({

&quot;writeErrors&quot;:[],

&quot;writeConcernErrors&quot;:[],

&quot;nInserted&quot;:2,

&quot;nUpserted&quot;:0,

&quot;nMatched&quot;:0,

&quot;nModified&quot;:0,

&quot;nRemoved&quot;:0,

&quot;upserted&quot;:[]

})

\&gt;

To insert the document you can use **db.post.save(document)** also. If you don&#39;t specify  **\_id**  in the document then **save()** method will work same as **insert()** method. If you specify \_id then it will replace whole data of document containing \_id as specified in save() method.

## **The insertOne() method:**

If you need to insert only one document into a collection you can use this method.

### **Syntax**

The basic syntax of insert() command is as follows −

\&gt;db.COLLECTION\_NAME.insertOne(document)

### **Example**

Following example creates a new collection named empDetails and inserts a document using the insertOne() method.

\&gt; db.createCollection(&quot;empDetails&quot;)

{&quot;ok&quot;:1}

\&gt; db.empDetails.insertOne(

{

First\_Name:&quot;Radhika&quot;,

Last\_Name:&quot;Sharma&quot;,

Date\_Of\_Birth:&quot;1995-09-26&quot;,

e\_mail:&quot;radhika\_sharma.123@gmail.com&quot;,

phone:&quot;9848022338&quot;

})

{

&quot;acknowledged&quot;:true,

&quot;insertedId&quot;:ObjectId(&quot;5dd62b4070fb13eec3963bea&quot;)

}

\&gt;

##

## **The insertMany() method**

You can insert multiple documents using the insertMany() method. To this method you need to pass an array of documents.

### **Example**

Following example inserts three different documents into the empDetails collection using the insertMany() method.

\&gt; db.empDetails.insertMany(

[

{

First\_Name:&quot;Radhika&quot;,

Last\_Name:&quot;Sharma&quot;,

Date\_Of\_Birth:&quot;1995-09-26&quot;,

e\_mail:&quot;radhika\_sharma.123@gmail.com&quot;,

phone:&quot;9000012345&quot;

},

{

First\_Name:&quot;Rachel&quot;,

Last\_Name:&quot;Christopher&quot;,

Date\_Of\_Birth:&quot;1990-02-16&quot;,

e\_mail:&quot;Rachel\_Christopher.123@gmail.com&quot;,

phone:&quot;9000054321&quot;

},

{

First\_Name:&quot;Fathima&quot;,

Last\_Name:&quot;Sheik&quot;,

Date\_Of\_Birth:&quot;1990-02-16&quot;,

e\_mail:&quot;Fathima\_Sheik.123@gmail.com&quot;,

phone:&quot;9000054321&quot;

}

]

)

{

&quot;acknowledged&quot;:true,

&quot;insertedIds&quot;:[

ObjectId(&quot;5dd631f270fb13eec3963bed&quot;),

ObjectId(&quot;5dd631f270fb13eec3963bee&quot;),

ObjectId(&quot;5dd631f270fb13eec3963bef&quot;)

]

}

\&gt;

## **The find() Method**

To query data from MongoDB collection, you need to use MongoDB&#39;s **find()** method.

### **Syntax**

The basic syntax of **find()** method is as follows −

\&gt;db.COLLECTION\_NAME.find()

**find()** method will display all the documents in a non-structured way.

### **Example**

Assume we have created a collection named mycol as −

\&gt;use sampleDB

switched to db sampleDB

\&gt; db.createCollection(&quot;mycol&quot;)

{&quot;ok&quot;:1}

\&gt;

And inserted 3 documents in it using the insert() method as shown below −

\&gt; db.mycol.insert([

{

title:&quot;MongoDB Overview&quot;,

description:&quot;MongoDB is no SQL database&quot;,

by:&quot;cognizance&quot;,

tags:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],

likes:100

},

{

title:&quot;NoSQL Database&quot;,

description:&quot;NoSQL database doesn&#39;t have tables&quot;,

by:&quot;cognizance&quot;,

tags:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],

likes:20,

comments:[

{

user:&quot;user1&quot;,

message:&quot;My first comment&quot;,

dateCreated:newDate(2013,11,10,2,35),

like:0

}

]

}

])

Following method retrieves all the documents in the collection −

\&gt; db.mycol.find()

{&quot;\_id&quot;:ObjectId(&quot;5dd4e2cc0821d3b44607534c&quot;),&quot;title&quot;:&quot;MongoDB Overview&quot;,&quot;description&quot;:&quot;MongoDB is no SQL database&quot;,&quot;by&quot;:&quot;cognizance&quot;,&quot;url&quot;:&quot;http://www.tutorialspoint.com&quot;,&quot;tags&quot;:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],&quot;likes&quot;:100}

{&quot;\_id&quot;:ObjectId(&quot;5dd4e2cc0821d3b44607534d&quot;),&quot;title&quot;:&quot;NoSQL Database&quot;,&quot;description&quot;:&quot;NoSQL database doesn&#39;t have tables&quot;,&quot;by&quot;:&quot;cognizance&quot;,&quot;tags&quot;:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],&quot;likes&quot;:20,&quot;comments&quot;:[{&quot;user&quot;:&quot;user1&quot;,&quot;message&quot;:&quot;My first comment&quot;,&quot;dateCreated&quot;:ISODate(&quot;2013-12-09T21:05:00Z&quot;),&quot;like&quot;:0}]}

\&gt;

##

## **The pretty() Method**

To display the results in a formatted way, you can use pretty() method.

### **Syntax**

\&gt;db.COLLECTION\_NAME.find().pretty()

### **Example**

Following example retrieves all the documents from the collection named mycol and arranges them in an easy-to-read format.

\&gt; db.mycol.find().pretty()

{

&quot;\_id&quot;:ObjectId(&quot;5dd4e2cc0821d3b44607534c&quot;),

&quot;title&quot;:&quot;MongoDB Overview&quot;,

&quot;description&quot;:&quot;MongoDB is no SQL database&quot;,

&quot;by&quot;:&quot;cognizance&quot;,

&quot;tags&quot;:[

&quot;mongodb&quot;,

&quot;database&quot;,

&quot;NoSQL&quot;

],

&quot;likes&quot;:100

}

{

&quot;\_id&quot;:ObjectId(&quot;5dd4e2cc0821d3b44607534d&quot;),

&quot;title&quot;:&quot;NoSQL Database&quot;,

&quot;description&quot;:&quot;NoSQL database doesn&#39;t have tables&quot;,

&quot;by&quot;:&quot;cognizance&quot;,

&quot;tags&quot;:[

&quot;mongodb&quot;,

&quot;database&quot;,

&quot;NoSQL&quot;

],

&quot;likes&quot;:20,

&quot;comments&quot;:[

{

&quot;user&quot;:&quot;user1&quot;,

&quot;message&quot;:&quot;My first comment&quot;,

&quot;dateCreated&quot;:ISODate(&quot;2013-12-09T21:05:00Z&quot;),

&quot;like&quot;:0

}

]

}

##

## **The findOne() method**

Apart from the find() method, there is **findOne()** method, that returns only one document.

### **Syntax**

\&gt;db.COLLECTIONNAME.findOne()

### **Example**

Following example retrieves the document with title MongoDB Overview.

\&gt; db.mycol.findOne({title:&quot;MongoDB Overview&quot;})

{

&quot;\_id&quot;:ObjectId(&quot;5dd6542170fb13eec3963bf0&quot;),

&quot;title&quot;:&quot;MongoDB Overview&quot;,

&quot;description&quot;:&quot;MongoDB is no SQL database&quot;,

&quot;by&quot;:&quot;cognizance&quot;,

&quot;url&quot;:&quot;http://www.tutorialspoint.com&quot;,

&quot;tags&quot;:[

&quot;mongodb&quot;,

&quot;database&quot;,

&quot;NoSQL&quot;

],

&quot;likes&quot;:100

}

##

## **RDBMS Where Clause Equivalents in MongoDB**

To query the document on the basis of some condition, you can use following operations.

| **Operation** | **Syntax** | **Example** | **RDBMS Equivalent** |
| --- | --- | --- | --- |
| Equality | {\&lt;key\&gt;:{$eg;\&lt;value\&gt;}} | db.mycol.find({&quot;by&quot;:&quot;cognizance&quot;}).pretty() | where by = &#39;cognizance&#39; |
| Less Than | {\&lt;key\&gt;:{$lt:\&lt;value\&gt;}} | db.mycol.find({&quot;likes&quot;:{$lt:50}}).pretty() | where likes \&lt; 50 |
| Less Than Equals | {\&lt;key\&gt;:{$lte:\&lt;value\&gt;}} | db.mycol.find({&quot;likes&quot;:{$lte:50}}).pretty() | where likes \&lt;= 50 |
| Greater Than | {\&lt;key\&gt;:{$gt:\&lt;value\&gt;}} | db.mycol.find({&quot;likes&quot;:{$gt:50}}).pretty() | where likes \&gt; 50 |
| Greater Than Equals | {\&lt;key\&gt;:{$gte:\&lt;value\&gt;}} | db.mycol.find({&quot;likes&quot;:{$gte:50}}).pretty() | where likes \&gt;= 50 |
| Not Equals | {\&lt;key\&gt;:{$ne:\&lt;value\&gt;}} | db.mycol.find({&quot;likes&quot;:{$ne:50}}).pretty() | where likes != 50 |
| Values in an array | {\&lt;key\&gt;:{$in:[\&lt;value1\&gt;, \&lt;value2\&gt;,……\&lt;valueN\&gt;]}} | db.mycol.find({&quot;name&quot;:{$in:[&quot;Raj&quot;, &quot;Ram&quot;, &quot;Raghu&quot;]}}).pretty() | Where name matches any of the value in :[&quot;Raj&quot;, &quot;Ram&quot;, &quot;Raghu&quot;] |
| Values not in an array | {\&lt;key\&gt;:{$nin:\&lt;value\&gt;}} | db.mycol.find({&quot;name&quot;:{$nin:[&quot;Ramu&quot;, &quot;Raghav&quot;]}}).pretty() | Where name values is not in the array :[&quot;Ramu&quot;, &quot;Raghav&quot;] or, doesn&#39;t exist at all |

##

## **AND :**

### **Syntax**

To query documents based on the AND condition, you need to use $and keyword. Following is the basic syntax of AND −

\&gt;db.mycol.find({ $and: [{\&lt;key1\&gt;:\&lt;value1\&gt;}, { \&lt;key2\&gt;:\&lt;value2\&gt;}] })

### **Example**

Following example will show all the tutorials written by &#39;cognizance&#39; and whose title is &#39;MongoDB Overview&#39;.

\&gt; db.mycol.find({$and:[{&quot;by&quot;:&quot;cognizance&quot;},{&quot;title&quot;:&quot;MongoDB Overview&quot;}]}).pretty()

{

&quot;\_id&quot;:ObjectId(&quot;5dd4e2cc0821d3b44607534c&quot;),

&quot;title&quot;:&quot;MongoDB Overview&quot;,

&quot;description&quot;:&quot;MongoDB is no SQL database&quot;,

&quot;by&quot;:&quot;cognizance&quot;,

&quot;tags&quot;:[

&quot;mongodb&quot;,

&quot;database&quot;,

&quot;NoSQL&quot;

],

&quot;likes&quot;:100

}

\&gt;

For the above given example, equivalent where clause will be  **&#39; where by = &#39;cognizance&#39; AND title = &#39;MongoDB Overview&#39; &#39;**. You can pass any number of key, value pairs in find clause.

## **OR in MongoDB**

### **Syntax**

To query documents based on the OR condition, you need to use  **$or**  keyword. Following is the basic syntax of  **OR**  −

\&gt;db.mycol.find(

{

$or: [

{key1: value1}, {key2:value2}

]

}

).pretty()

### **Example**

Following example will show all the tutorials written by &#39;cognizance&#39; or whose title is &#39;MongoDB Overview&#39;.

\&gt;db.mycol.find({$or:[{&quot;by&quot;:&quot;cognizance&quot;},{&quot;title&quot;:&quot;MongoDB Overview&quot;}]}).pretty()

{

&quot;\_id&quot;:ObjectId(7df78ad8902c),

&quot;title&quot;:&quot;MongoDB Overview&quot;,

&quot;description&quot;:&quot;MongoDB is no sql database&quot;,

&quot;by&quot;:&quot;cognizance&quot;

&quot;tags&quot;:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],

&quot;likes&quot;:&quot;100&quot;

}

\&gt;

##

## **Using AND and OR Together:**

### **Example**

The following example will show the documents that have likes greater than 10 and whose title is either &#39;MongoDB Overview&#39; or by is &#39;cognizance&#39;. Equivalent SQL where clause is **&#39;where likes\&gt;10 AND (by = &#39;cognizance&#39; OR title = &#39;MongoDB Overview&#39;)&#39;**

\&gt;db.mycol.find({&quot;likes&quot;:{$gt:10}, $or:[{&quot;by&quot;:&quot;cognizance&quot;},

{&quot;title&quot;:&quot;MongoDB Overview&quot;}]}).pretty()

{

&quot;\_id&quot;:ObjectId(7df78ad8902c),

&quot;title&quot;:&quot;MongoDB Overview&quot;,

&quot;description&quot;:&quot;MongoDB is no sql database&quot;,

&quot;by&quot;:&quot;cognizance&quot;,

&quot;tags&quot;:[&quot;mongodb&quot;,&quot;database&quot;,&quot;NoSQL&quot;],

&quot;likes&quot;:&quot;100&quot;

}

\&gt;

##

## **NOR :**

###

### **Syntax**

To query documents based on the NOT condition, you need to use $not keyword. Following is the basic syntax of  **NOT**  −

\&gt;db.COLLECTION\_NAME.find(

{

$not: [

{key1: value1}, {key2:value2}

]

}

)

### **Example**

Assume we have inserted 3 documents in the collection  **empDetails**  as shown below −

db.empDetails.insertMany(

[

{

First\_Name:&quot;Radhika&quot;,

Last\_Name:&quot;Sharma&quot;,

Age:&quot;26&quot;,

e\_mail:&quot;radhika\_sharma.123@gmail.com&quot;,

phone:&quot;9000012345&quot;

},

{

First\_Name:&quot;Rachel&quot;,

Last\_Name:&quot;Christopher&quot;,

Age:&quot;27&quot;,

e\_mail:&quot;Rachel\_Christopher.123@gmail.com&quot;,

phone:&quot;9000054321&quot;

},

{

First\_Name:&quot;Fathima&quot;,

Last\_Name:&quot;Sheik&quot;,

Age:&quot;24&quot;,

e\_mail:&quot;Fathima\_Sheik.123@gmail.com&quot;,

phone:&quot;9000054321&quot;

}

]

)

Following example will retrieve the document(s) whose first name is not &quot;Radhika&quot; and last name is not &quot;Christopher&quot;

\&gt; db.empDetails.find(

{

$nor:[

40

{&quot;First\_Name&quot;:&quot;Radhika&quot;},

{&quot;Last\_Name&quot;:&quot;Christopher&quot;}

]

}

).pretty()

{

&quot;\_id&quot;:ObjectId(&quot;5dd631f270fb13eec3963bef&quot;),

&quot;First\_Name&quot;:&quot;Fathima&quot;,

&quot;Last\_Name&quot;:&quot;Sheik&quot;,

&quot;Age&quot;:&quot;24&quot;,

&quot;e\_mail&quot;:&quot;Fathima\_Sheik.123@gmail.com&quot;,

&quot;phone&quot;:&quot;9000054321&quot;

}

##

## **NOT in MongoDB**

### **Syntax**

To query documents based on the NOT condition, you need to use $not keyword following is the basic syntax of  **NOT**  −

\&gt;db.COLLECTION\_NAME.find(

{

$NOT: [

{key1: value1}, {key2:value2}

]

}

).pretty()

### **Example**

Following example will retrieve the document(s) whose age is not greater than 25

\&gt; db.empDetails.find({&quot;Age&quot;:{ $not:{ $gt:&quot;25&quot;}}})

{

&quot;\_id&quot;:ObjectId(&quot;5dd6636870fb13eec3963bf7&quot;),

&quot;First\_Name&quot;:&quot;Fathima&quot;,

&quot;Last\_Name&quot;:&quot;Sheik&quot;,

&quot;Age&quot;:&quot;24&quot;,

&quot;e\_mail&quot;:&quot;Fathima\_Sheik.123@gmail.com&quot;,

&quot;phone&quot;:&quot;9000054321&quot;

}

MongoDB&#39;s **update()** and **save()** methods are used to update document into a collection. The update() method updates the values in the existing document while the save() method replaces the existing document with the document passed in save() method.

## **MongoDB Update() Method**

The update() method updates the values in the existing document.

### **Syntax**

The basic syntax of **update()** method is as follows −

\&gt;db.COLLECTION\_NAME.update(SELECTION\_CRITERIA, UPDATED\_DATA)

### **Example**

Consider the mycol collection has the following data.

{&quot;\_id&quot;:ObjectId(5983548781331adf45ec5),&quot;title&quot;:&quot;MongoDB Overview&quot;}

{&quot;\_id&quot;:ObjectId(5983548781331adf45ec6),&quot;title&quot;:&quot;NoSQL Overview&quot;}

{&quot;\_id&quot;:ObjectId(5983548781331adf45ec7),&quot;title&quot;:&quot;mongo db&quot;}

Following example will set the new title &#39;New MongoDB Tutorial&#39; of the documents whose title is &#39;MongoDB Overview&#39;.

\&gt;db.mycol.update({&#39;title&#39;:&#39;MongoDB Overview&#39;},{$set:{&#39;title&#39;:&#39;New MongoDB Tutorial&#39;}})

WriteResult({&quot;nMatched&quot;:1,&quot;nUpserted&quot;:0,&quot;nModified&quot;:1})

\&gt;db.mycol.find()

{&quot;\_id&quot;:ObjectId(5983548781331adf45ec5),&quot;title&quot;:&quot;New MongoDB Tutorial&quot;}

{&quot;\_id&quot;:ObjectId(5983548781331adf45ec6),&quot;title&quot;:&quot;NoSQL Overview&quot;}

{&quot;\_id&quot;:ObjectId(5983548781331adf45ec7),}

\&gt;

By default, MongoDB will update only a single document. To update multiple documents, you need to set a parameter &#39;multi&#39; to true.

\&gt;db.mycol.update({&#39;title&#39;:&#39;MongoDB Overview&#39;},

{$set:{&#39;title&#39;:&#39;New MongoDB Tutorial&#39;}},{multi:true})

##

## **MongoDB Save() Method**

The **save()** method replaces the existing document with the new document passed in the save() method.

### **Syntax**

The basic syntax of MongoDB **save()** method is shown below −

\&gt;db.COLLECTION\_NAME.save({\_id:ObjectId(),NEW\_DATA})

### **Example**

Following example will replace the document with the \_id &#39;5983548781331adf45ec5&#39;.

\&gt;db.mycol.save(

{

&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860ea&quot;),

}

)

WriteResult({

&quot;nMatched&quot;:0,

&quot;nUpserted&quot;:1,

&quot;nModified&quot;:0,

&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860ea&quot;)

})

\&gt;db.mycol.find()

{&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860e6&quot;),

&quot;by&quot;:&quot;cognizance&quot;}

{&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860e6&quot;),&quot;title&quot;:&quot;NoSQL Overview&quot;}

{&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860e6&quot;),&quot;title&quot;:&quot;cognizance&quot;} \&gt;

##

## **MongoDB findOneAndUpdate() method**

The **findOneAndUpdate()** method updates the values in the existing document.

### **Syntax**

The basic syntax of **findOneAndUpdate()** method is as follows −

\&gt;db.COLLECTION\_NAME.findOneAndUpdate(SELECTIOIN\_CRITERIA, UPDATED\_DATA)

### **Example**

Assume we have created a collection named empDetails and inserted three documents in it as shown below −

\&gt; db.empDetails.insertMany(

[

{

First\_Name:&quot;Radhika&quot;,

Last\_Name:&quot;Sharma&quot;,

Age:&quot;26&quot;,

e\_mail:&quot;radhika\_sharma.123@gmail.com&quot;,

phone:&quot;9000012345&quot;

},

{

First\_Name:&quot;Rachel&quot;,

Last\_Name:&quot;Christopher&quot;,

Age:&quot;27&quot;,

e\_mail:&quot;Rachel\_Christopher.123@gmail.com&quot;,

phone:&quot;9000054321&quot;

},

{

First\_Name:&quot;Fathima&quot;,

Last\_Name:&quot;Sheik&quot;,

Age:&quot;24&quot;,

e\_mail:&quot;Fathima\_Sheik.123@gmail.com&quot;,

phone:&quot;9000054321&quot;

}

]

)

Following example updates the age and email values of the document with name &#39;Radhika&#39;.

\&gt; db.empDetails.findOneAndUpdate(

{First\_Name:&#39;Radhika&#39;},

{ $set:{Age:&#39;30&#39;,e\_mail:&#39;radhika\_newemail@gmail.com&#39;}}

)

{

&quot;\_id&quot;:ObjectId(&quot;5dd6636870fb13eec3963bf5&quot;),

&quot;First\_Name&quot;:&quot;Radhika&quot;,

&quot;Last\_Name&quot;:&quot;Sharma&quot;,

&quot;Age&quot;:&quot;30&quot;,

&quot;e\_mail&quot;:&quot;radhika\_newemail@gmail.com&quot;,

&quot;phone&quot;:&quot;9000012345&quot;

}

##

## **MongoDB updateOne() method**

This methods updates a single document which matches the given filter.

### **Syntax**

The basic syntax of updateOne() method is as follows −

\&gt;db.COLLECTION\_NAME.updateOne(\&lt;filter\&gt;,\&lt;update\&gt;)

### **Example**

\&gt; db.empDetails.updateOne(

{First\_Name:&#39;Radhika&#39;},

{ $set:{Age:&#39;30&#39;,e\_mail:&#39;radhika\_newemail@gmail.com&#39;}}

)

{&quot;acknowledged&quot;:true,&quot;matchedCount&quot;:1,&quot;modifiedCount&quot;:0}

\&gt;

## **MongoDB updateMany() method:**

The updateMany() method updates all the documents that matches the given filter.

### **Syntax**

The basic syntax of updateMany() method is as follows −

\&gt;db.COLLECTION\_NAME.update(\&lt;filter\&gt;,\&lt;update\&gt;)

### **Example**

\&gt; db.empDetails.updateMany(

{Age:{ $gt:&quot;25&quot;}},

{ $set:{Age:&#39;00&#39;}}

)

{&quot;acknowledged&quot;:true,&quot;matchedCount&quot;:2,&quot;modifiedCount&quot;:2}

You can see the updated values if you retrieve the contents of the document using the find method as shown below −

\&gt; db.empDetails.find()

{&quot;\_id&quot;:ObjectId(&quot;5dd6636870fb13eec3963bf5&quot;),&quot;First\_Name&quot;:&quot;Radhika&quot;,&quot;Last\_Name&quot;:&quot;Sharma&quot;,&quot;Age&quot;:&quot;00&quot;,&quot;e\_mail&quot;:&quot;radhika\_newemail@gmail.com&quot;,&quot;phone&quot;:&quot;9000012345&quot;}

{&quot;\_id&quot;:ObjectId(&quot;5dd6636870fb13eec3963bf6&quot;),&quot;First\_Name&quot;:&quot;Rachel&quot;,&quot;Last\_Name&quot;:&quot;Christopher&quot;,&quot;Age&quot;:&quot;00&quot;,&quot;e\_mail&quot;:&quot;Rachel\_Christopher.123@gmail.com&quot;,&quot;phone&quot;:&quot;9000054321&quot;}

{&quot;\_id&quot;:ObjectId(&quot;5dd6636870fb13eec3963bf7&quot;),&quot;First\_Name&quot;:&quot;Fathima&quot;,&quot;Last\_Name&quot;:&quot;Sheik&quot;,&quot;Age&quot;:&quot;24&quot;,&quot;e\_mail&quot;:&quot;Fathima\_Sheik.123@gmail.com&quot;,&quot;phone&quot;:&quot;9000054321&quot;}

\&gt;

## **The remove() Method**

MongoDB&#39;s **remove()** method is used to remove a document from the collection. remove() method accepts two parameters. One is deletion criteria and second is justOne flag.

- **deletion criteria**  − (Optional) deletion criteria according to documents will be removed.
- **justOne**  − (Optional) if set to true or 1, then remove only one document.

### **Syntax**

Basic syntax of **remove()** method is as follows −

\&gt;db.COLLECTION\_NAME.remove(DELLETION\_CRITTERIA)

### **Example**

Consider the mycol collection has the following data.

{\_id :ObjectId(&quot;507f191e810c19729de860e1&quot;), title:&quot;MongoDB Overview&quot;},

{\_id :ObjectId(&quot;507f191e810c19729de860e2&quot;), title:&quot;NoSQL Overview&quot;},

{\_id :ObjectId(&quot;507f191e810c19729de860e3&quot;), title:&quot;cognicance&quot;}

Following example will remove all the documents whose title is &#39;MongoDB Overview&#39;.

\&gt;db.mycol.remove({&#39;title&#39;:&#39;MongoDB Overview&#39;})

WriteResult({&quot;nRemoved&quot;:1})

\&gt; db.mycol.find()

{&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860e2&quot;),&quot;title&quot;:&quot;NoSQL Overview&quot;}

{&quot;\_id&quot;:ObjectId(&quot;507f191e810c19729de860e3&quot;)}

## **Remove Only One**

If there are multiple records and you want to delete only the first record, then set  **justOne**  parameter in **remove()** method.

\&gt;db.COLLECTION\_NAME.remove(DELETION\_CRITERIA,1)

##

## **Remove All Documents**

If you don&#39;t specify deletion criteria, then MongoDB will delete whole documents from the collection.  **This is equivalent of SQL&#39;s truncate command.**

\&gt; db.mycol.remove({})

WriteResult({&quot;nRemoved&quot;:2})

\&gt; db.mycol.find()

\&gt;

In MongoDB, projection means selecting only the necessary data rather than selecting whole of the data of a document. If a document has 5 fields and you need to show only 3, then select only 3 fields from them.

The find() Method

MongoDB&#39;s **find()** method, explained in [MongoDB Query Document](https://www.tutorialspoint.com/mongodb/mongodb_query_document.htm) accepts second optional parameter that is list of fields that you want to retrieve. In MongoDB, when you execute **find()** method, then it displays all fields of a document. To limit this, you need to set a list of fields with value 1 or 0. 1 is used to show the field while 0 is used to hide the fields.

Syntax

The basic syntax of **find()** method with projection is as follows −

\&gt;db.COLLECTION\_NAME.find({},{KEY:1})

Example

Consider the collection mycol has the following data −

{\_id :ObjectId(&quot;507f191e810c19729de860e1&quot;), title:&quot;MongoDB Overview&quot;},

{\_id :ObjectId(&quot;507f191e810c19729de860e2&quot;), title:&quot;NoSQL Overview&quot;},

{\_id :ObjectId(&quot;507f191e810c19729de860e3&quot;), title:&quot;cognicance&quot;}

Following example will display the title of the document while querying the document.

\&gt;db.mycol.find({},{&quot;title&quot;:1,\_id:0})

{&quot;title&quot;:&quot;MongoDB Overview&quot;}

{&quot;title&quot;:&quot;NoSQL Overview&quot;}

{&quot;title&quot;:&quot;cognicance&quot;}

\&gt;

Please note  **\_id**  field is always displayed while executing **find()** method, if you don&#39;t want this field, then you need to set it as 0.

## **The Limit() Method**

To limit the records in MongoDB, you need to use **limit()** method. The method accepts one number type argument, which is the number of documents that you want to be displayed.

### **Syntax**

The basic syntax of **limit()** method is as follows −

\&gt;db.COLLECTION\_NAME.find().limit(NUMBER)

### **Example**

Consider the collection myycol has the following data.

{\_id :ObjectId(&quot;507f191e810c19729de860e1&quot;), title:&quot;MongoDB Overview&quot;},

{\_id :ObjectId(&quot;507f191e810c19729de860e2&quot;), title:&quot;NoSQL Overview&quot;},

{\_id :ObjectId(&quot;507f191e810c19729de860e3&quot;), title:&quot;cognizance&quot;}

Following example will display only two documents while querying the document.

\&gt;db.mycol.find({},{&quot;title&quot;:1,\_id:0}).limit(2)

{&quot;title&quot;:&quot;MongoDB Overview&quot;}

{&quot;title&quot;:&quot;NoSQL Overview&quot;}

\&gt;

If you don&#39;t specify the number argument in **limit()** method then it will display all documents from the collection.

## **MongoDB Skip() Method**

Apart from limit() method, there is one more method **skip()** which also accepts number type argument and is used to skip the number of documents.

### **Syntax**

The basic syntax of **skip()** method is as follows −

\&gt;db.COLLECTION\_NAME.find().limit(NUMBER).skip(NUMBER)

### **Example**

Following example will display only the second document.

\&gt;db.mycol.find({},{&quot;title&quot;:1,\_id:0}).limit(1).skip(1)

{&quot;title&quot;:&quot;NoSQL Overview&quot;}

\&gt;

Please note, the default value in **skip()** method is 0.

## **The sort() Method**

To sort documents in MongoDB, you need to use **sort()** method. The method accepts a document containing a list of fields along with their sorting order. To specify sorting order 1 and -1 are used. 1 is used for ascending order while -1 is used for descending order.

### **Syntax**

The basic syntax of **sort()** method is as follows −

\&gt;db.COLLECTION\_NAME.find().sort({KEY:1})

### **Example**

Consider the collection myycol has the following data.

{\_id :ObjectId(&quot;507f191e810c19729de860e1&quot;), title:&quot;MongoDB Overview&quot;}

{\_id :ObjectId(&quot;507f191e810c19729de860e2&quot;), title:&quot;NoSQL Overview&quot;}

{\_id :ObjectId(&quot;507f191e810c19729de860e3&quot;), title:&quot;sorting&quot;}

Following example will display the documents sorted by title in the descending order.

\&gt;db.mycol.find({},{&quot;title&quot;:1,\_id:0}).sort({&quot;title&quot;:-1})

{&quot;title&quot;:&quot;cognizance mongodb&quot;}

{&quot;title&quot;:&quot;NoSQL Overview&quot;}

{&quot;title&quot;:&quot;MongoDB Overview&quot;}

\&gt;

Please note, if you don&#39;t specify the sorting preference, then **sort()** method will display the documents in ascending order.

Indexes support the efficient resolution of queries. Without indexes, MongoDB must scan every document of a collection to select those documents that match the query statement. This scan is highly inefficient and require MongoDB to process a large volume of data.

Indexes are special data structures, that store a small portion of the data set in an easy-to-traverse form. The index stores the value of a specific field or set of fields, ordered by the value of the field as specified in the index.

##

## **The createIndex() Method**

To create an index, you need to use createIndex() method of MongoDB.

### **Syntax**

The basic syntax of **createIndex()** method is as follows().

\&gt;db.COLLECTION\_NAME.createIndex({KEY:1})

Here key is the name of the field on which you want to create index and 1 is for ascending order. To create index in descending order you need to use -1.

### **Example**

\&gt;db.mycol.createIndex({&quot;title&quot;:1})

{

&quot;createdCollectionAutomatically&quot;:false,

&quot;numIndexesBefore&quot;:1,

&quot;numIndexesAfter&quot;:2,

&quot;ok&quot;:1

}

\&gt;

In **createIndex()** method you can pass multiple fields, to create index on multiple fields.

\&gt;db.mycol.createIndex({&quot;title&quot;:1,&quot;description&quot;:-1})

\&gt;

This method also accepts list of options (which are optional). Following is the list −

| **Parameter** | **Type** | **Description** |
| --- | --- | --- |
| background | Boolean | Builds the index in the background so that building an index does not block other database activities. Specify true to build in the background. The default value is  **false**. |
| unique | Boolean | Creates a unique index so that the collection will not accept insertion of documents where the index key or keys match an existing value in the index. Specify true to create a unique index. The default value is  **false**. |
| name | string | The name of the index. If unspecified, MongoDB generates an index name by concatenating the names of the indexed fields and the sort order. |
| sparse | Boolean | If true, the index only references documents with the specified field. These indexes use less space but behave differently in some situations (particularly sorts). The default value is  **false**. |
| expireAfterSeconds | integer | Specifies a value, in seconds, as a TTL to control how long MongoDB retains documents in this collection. |
| weights | document | The weight is a number ranging from 1 to 99,999 and denotes the significance of the field relative to the other indexed fields in terms of the score. |
| default\_language | string | For a text index, the language that determines the list of stop words and the rules for the stemmer and tokenizer. The default value is  **English**. |
| language\_override | string | For a text index, specify the name of the field in the document that contains, the language to override the default language. The default value is language. |

##

## **The dropIndex() method**

You can drop a particular index using the dropIndex() method of MongoDB.

### **Syntax**

The basic syntax of DropIndex() method is as follows().

\&gt;db.COLLECTION\_NAME.dropIndex({KEY:1})

Here key is the name of the file on which you want to create index and 1 is for ascending order. To create index in descending order you need to use -1.

### **Example**

\&gt; db.mycol.dropIndex({&quot;title&quot;:1})

{

&quot;ok&quot;:0,

&quot;errmsg&quot;:&quot;can&#39;t find index with key: { title: 1.0 }&quot;,

&quot;code&quot;:27,

&quot;codeName&quot;:&quot;IndexNotFound&quot;

}

##

## **The dropIndexes() method**

This method deletes multiple (specified) indexes on a collection.

### **Syntax**

The basic syntax of DropIndexes() method is as follows() −

\&gt;db.COLLECTION\_NAME.dropIndexes()

### **Example**

Assume we have created 2 indexes in the named mycol collection as shown below −

\&gt; db.mycol.createIndex({&quot;title&quot;:1,&quot;description&quot;:-1})

Following example removes the above created indexes of mycol −

\&gt;db.mycol.dropIndexes({&quot;title&quot;:1,&quot;description&quot;:-1})

{&quot;nIndexesWas&quot;:2,&quot;ok&quot;:1}

\&gt;

##

## **The getIndexes() method**

This method returns the description of all the indexes int the collection.

### **Syntax**

Following is the basic syntax od the getIndexes() method −

db.COLLECTION\_NAME.getIndexes()

### **Example**

Assume we have created 2 indexes in the named mycol collection as shown below −

\&gt; db.mycol.createIndex({&quot;title&quot;:1,&quot;description&quot;:-1})

Following example retrieves all the indexes in the collection mycol −

\&gt; db.mycol.getIndexes()

[

{

&quot;v&quot;:2,

&quot;key&quot;:{

&quot;\_id&quot;:1

},

&quot;name&quot;:&quot;\_id\_&quot;,

&quot;ns&quot;:&quot;test.mycol&quot;

},

{

&quot;v&quot;:2,

&quot;key&quot;:{

&quot;title&quot;:1,

&quot;description&quot;:-1

},

&quot;name&quot;:&quot;title\_1\_description\_-1&quot;,

&quot;ns&quot;:&quot;test.mycol&quot;

}

]

\&gt;

Aggregations operations process data records and return computed results. Aggregation operations group values from multiple documents together, and can perform a variety of operations on the grouped data to return a single result. In SQL count(\*) and with group by is an equivalent of MongoDB aggregation.

##

## **The aggregate() Method**

For the aggregation in MongoDB, you should use **aggregate()** method.

### **Syntax**

Basic syntax of **aggregate()** method is as follows −

\&gt;db.COLLECTION\_NAME.aggregate(AGGREGATE\_OPERATION)

### **Example**

In the collection you have the following data −

{

\_id:ObjectId(7df78ad8902c)

title:&#39;MongoDB Overview&#39;,

description:&#39;MongoDB is no sql database&#39;,

by\_user:&#39;cognizance&#39;,

tags:[&#39;mongodb&#39;,&#39;database&#39;,&#39;NoSQL&#39;],

likes:100

},

{

\_id:ObjectId(7df78ad8902d)

title:&#39;NoSQL Overview&#39;,

description:&#39;No sql database is very fast&#39;,

by\_user:&#39;cognizance&#39;,

tags:[&#39;mongodb&#39;,&#39;database&#39;,&#39;NoSQL&#39;],

likes:10

},

{

\_id:ObjectId(7df78ad8902e)

title:&#39;Neo4j Overview&#39;,

description:&#39;Neo4j is no sql database&#39;,

by\_user:&#39;Neo4j&#39;,

url:&#39;http://www.neo4j.com&#39;,

tags:[&#39;neo4j&#39;,&#39;database&#39;,&#39;NoSQL&#39;],

likes:750

},

Now from the above collection, if you want to display a list stating how many tutorials are written by each user, then you will use the following **aggregate()** method −

\&gt; db.mycol.aggregate([{$group :{\_id :&quot;$by\_user&quot;, num\_tutorial :{$sum :1}}}])

{&quot;\_id&quot;:&quot;cognizance&quot;,&quot;num\_tutorial&quot;:2}

{&quot;\_id&quot;:&quot;Neo4j&quot;,&quot;num\_tutorial&quot;:1}

\&gt;

Sql equivalent query for the above use case will be **select by\_user, count(\*) from mycol group by by\_user**.

In the above example, we have grouped documents by field  **by\_user**  and on each occurrence of by user previous value of sum is incremented. Following is a list of available aggregation expressions.

| **Expression** | **Description** | **Example** |
| --- | --- | --- |
| $sum | Sums up the defined value from all documents in the collection. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, num\_tutorial : {$sum : &quot;$likes&quot;}}}]) |
| $avg | Calculates the average of all given values from all documents in the collection. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, num\_tutorial : {$avg : &quot;$likes&quot;}}}]) |
| $min | Gets the minimum of the corresponding values from all documents in the collection. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, num\_tutorial : {$min : &quot;$likes&quot;}}}]) |
| $max | Gets the maximum of the corresponding values from all documents in the collection. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, num\_tutorial : {$max : &quot;$likes&quot;}}}]) |
| $push | Inserts the value to an array in the resulting document. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, url : {$push: &quot;$url&quot;}}}]) |
| $addToSet | Inserts the value to an array in the resulting document but does not create duplicates. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, url : {$addToSet : &quot;$url&quot;}}}]) |
| $first | Gets the first document from the source documents according to the grouping. Typically this makes only sense together with some previously applied &quot;$sort&quot;-stage. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, first\_url : {$first : &quot;$url&quot;}}}]) |
| $last | Gets the last document from the source documents according to the grouping. Typically this makes only sense together with some previously applied &quot;$sort&quot;-stage. | db.mycol.aggregate([{$group : {\_id : &quot;$by\_user&quot;, last\_url : {$last : &quot;$url&quot;}}}]) |

##

## **Pipeline Concept**

In UNIX command, shell pipeline means the possibility to execute an operation on some input and use the output as the input for the next command and so on. MongoDB also supports same concept in aggregation framework. There is a set of possible stages and each of those is taken as a set of documents as an input and produces a resulting set of documents (or the final resulting JSON document at the end of the pipeline). This can then in turn be used for the next stage and so on.

Following are the possible stages in aggregation framework −

- **$project**  − Used to select some specific fields from a collection.
- **$match**  − This is a filtering operation and thus this can reduce the amount of documents that are given as input to the next stage.
- **$group**  − This does the actual aggregation as discussed above.
- **$sort**  − Sorts the documents.
- **$skip**  − With this, it is possible to skip forward in the list of documents for a given amount of documents.
- **$limit**  − This limits the amount of documents to look at, by the given number starting from the current positions.
- **$unwind**  − This is used to unwind document that are using arrays. When using an array, the data is kind of pre-joined and this operation will be undone with this to have individual documents again. Thus with this stage we will increase the amount of documents for the next stage.

**REPLICATION:**

Replication is the process of synchronizing data across multiple servers. Replication provides redundancy and increases data availability with multiple copies of data on different database servers. Replication protects a database from the loss of a single server. Replication also allows you to recover from hardware failure and service interruptions. With additional copies of the data, you can dedicate one to disaster recovery, reporting, or backup.

##

## **Why Replication?**

- To keep your data safe
- High (24\*7) availability of data
- Disaster recovery
- No downtime for maintenance (like backups, index rebuilds, compaction)
- Read scaling (extra copies to read from)
- Replica set is transparent to the application

##

## **How Replication Works in MongoDB**

MongoDB achieves replication by the use of replica set. A replica set is a group of  **mongod**  instances that host the same data set. In a replica, one node is primary node that receives all write operations. All other instances, such as secondaries, apply operations from the primary so that they have the same data set. Replica set can have only one primary node.

- Replica set is a group of two or more nodes (generally minimum 3 nodes are required).
- In a replica set, one node is primary node and remaining nodes are secondary.
- All data replicates from primary to secondary node.
- At the time of automatic failover or maintenance, election establishes for primary and a new primary node is elected.
- After the recovery of failed node, it again join the replica set and works as a secondary node.

A typical diagram of MongoDB replication is shown in which client application always interact with the primary node and the primary node then replicates the data to the secondary nodes.

![](RackMultipart20201220-4-1b32190_html_2df45b00bd17aeba.png)

## **Replica Set Features**

- A cluster of N nodes
- Any one node can be primary
- All write operations go to primary
- Automatic failover
- Automatic recovery
- Consensus election of primary

## **Set Up a Replica Set**

In this tutorial, we will convert standalone MongoDB instance to a replica set. To convert to replica set, following are the steps −

- Shutdown already running MongoDB server.
-
- Start the MongoDB server by specifying -- replSet option. Following is the basic syntax of --replSet −

mongod --port &quot;PORT&quot; --dbpath &quot;YOUR\_DB\_DATA\_PATH&quot; --replSet &quot;REPLICA\_SET\_INSTANCE\_NAME&quot;

### **Example**

mongod --port 27017--dbpath &quot;D:\set up\mongodb\data&quot;--replSet rs0

- It will start a mongod instance with the name rs0, on port 27017.
- Now start the command prompt and connect to this mongod instance.
- In Mongo client, issue the command **rs.initiate()** to initiate a new replica set.
- To check the replica set configuration, issue the command **rs.conf()**. To check the status of replica set issue the command **rs.status()**.

##

## **Add Members to Replica Set**

To add members to replica set, start mongod instances on multiple machines. Now start a mongo client and issue a command **rs.add()**.

### **Syntax**

The basic syntax of **rs.add()** command is as follows −

\&gt;rs.add(HOST\_NAME:PORT)

### **Example**

Suppose your mongod instance name is  **mongod1.net**  and it is running on port  **27017**. To add this instance to replica set, issue the command **rs.add()** in Mongo client.

\&gt;rs.add(&quot;mongod1.net:27017&quot;)

\&gt;

You can add mongod instance to replica set only when you are connected to primary node. To check whether you are connected to primary or not, issue the command **db.isMaster()** in mongo client.

**SHRADING:**

Sharding is the process of storing data records across multiple machines and it is MongoDB&#39;s approach to meeting the demands of data growth. As the size of the data increases, a single machine may not be sufficient to store the data nor provide an acceptable read and write throughput. Sharding solves the problem with horizontal scaling. With sharding, you add more machines to support data growth and the demands of read and write operations.

##

##

## **Why Sharding?**

- In replication, all writes go to master node
- Latency sensitive queries still go to master
- Single replica set has limitation of 12 nodes
- Memory can&#39;t be large enough when active dataset is big
- Local disk is not big enough
- Vertical scaling is too expensive

##

## **Sharding in MongoDB**

The following diagram shows the Sharding in MongoDB using sharded cluster.

![](RackMultipart20201220-4-1b32190_html_a5f62a9a1d138a2.png)

In the following diagram, there are three main components −

- **Shards**  − Shards are used to store data. They provide high availability and data consistency. In production environment, each shard is a separate replica set.
- **Config Servers**  − Config servers store the cluster&#39;s metadata. This data contains a mapping of the cluster&#39;s data set to the shards. The query router uses this metadata to target operations to specific shards. In production environment, sharded clusters have exactly 3 config servers.
- **Query Routers**  − Query routers are basically mongo instances, interface with client applications and direct operations to the appropriate shard. The query router processes and targets the operations to shards and then returns results to the clients. A sharded cluster can contain more than one query router to divide the client request load. A client sends requests to one query router. Generally, a sharded cluster have many query routers.

we will see how to create a backup in MongoDB.

## **Dump MongoDB Data:**

- To create backup of database in MongoDB, you should use  **mongodump**  command. This command will dump the entire data of your server into the dump directory. There are many options available by which you can limit the amount of data or create backup of your remote server.
-
### **Syntax**
- The basic syntax of  **mongodump**  command is as follows −
- \&gt;mongodump
-
### **Example**
- Start your mongod server. Assuming that your mongod server is running on the localhost and port 27017, open a command prompt and go to the bin directory of your mongodb instance and type the command  **mongodump**
- Consider the mycol collection has the following data.
- \&gt;mongodump
- The command will connect to the server running at  **127.0.0.1**  and port  **27017**  and back all data of the server to directory  **/bin/dump/**. Following is the output of the command −

![](RackMultipart20201220-4-1b32190_html_8da33706d144ae4f.png)

- Following is a list of available options that can be used with the  **mongodump**  command.

| **Syntax** | **Description** | **Example** |
| --- | --- | --- |
| mongodump --host HOST\_NAME --port PORT\_NUMBER | This commmand will backup all databases of specified mongod instance. | mongodump --host tutorialspoint.com --port 27017 |
| mongodump --dbpath DB\_PATH --out BACKUP\_DIRECTORY | This command will backup only specified database at specified path. | mongodump --dbpath /data/db/ --out /data/backup/ |
| mongodump --collection COLLECTION --db DB\_NAME | This command will backup only specified collection of specified database. | mongodump --collection mycol --db test |

##

## **Restore data**

- To restore backup data MongoDB&#39;s  **mongorestore**  command is used. This command restores all of the data from the backup directory.
-
### **Syntax**
- The basic syntax of  **mongorestore**  command is −
- \&gt;mongorestore
- Following is the output of the command −

![](RackMultipart20201220-4-1b32190_html_8eb76d555d7f620f.png)

**DEPLOYMENT:**

When you are preparing a MongoDB deployment, you should try to understand how your application is going to hold up in production. It&#39;s a good idea to develop a consistent, repeatable approach to managing your deployment environment so that you can minimize any surprises once you&#39;re in production.

The best approach incorporates prototyping your set up, conducting load testing, monitoring key metrics, and using that information to scale your set up. The key part of the approach is to proactively monitor your entire system - this will help you understand how your production system will hold up before deploying, and determine where you will need to add capacity. Having insight into potential spikes in your memory usage, for example, could help put out a write-lock fire before it starts.

To monitor your deployment, MongoDB provides some of the following commands −

mongostat

This command checks the status of all running mongod instances and return counters of database operations. These counters include inserts, queries, updates, deletes, and cursors. Command also shows when you&#39;re hitting page faults, and showcase your lock percentage. This means that you&#39;re running low on memory, hitting write capacity or have some performance issue.

To run the command, start your mongod instance. In another command prompt, go to  **bin**  directory of your mongodb installation and type  **mongostat**.

D:\set up\mongodb\bin\&gt;mongostat

Following is the output of the command

![](RackMultipart20201220-4-1b32190_html_fde8ec0a89679c84.png)

![](RackMultipart20201220-4-1b32190_html_37f0d307d5f81665.jpg)

**mongotop**

This command tracks and reports the read and write activity of MongoDB instance on a collection basis. By default,  **mongotop**  returns information in each second, which you can change it accordingly. You should check that this read and write activity matches your application intention, and you&#39;re not firing too many writes to the database at a time, reading too frequently from a disk, or are exceeding your working set size.

To run the command, start your mongod instance. In another command prompt, go to  **bin**  directory of your mongodb installation and type  **mongotop**.

D:\set up\mongodb\bin\&gt;mongotop

Following is the output of the command −

![](RackMultipart20201220-4-1b32190_html_e49c3545942422cb.png) ![](RackMultipart20201220-4-1b32190_html_25309ffef28a9720.jpg)

To change  **mongotop**  command to return information less frequently, specify a specific number after the mongotop command.

D:\set up\mongodb\bin\&gt;mongotop 30

The above example will return values every 30 seconds.

Apart from the MongoDB tools, 10gen provides a free, hosted monitoring service, MongoDB Management Service (MMS), that provides a dashboard and gives you a view of the metrics from your entire cluster.
