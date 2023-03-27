# gRPC
General Purpose Remote Procedure Call

## Protocol Buffers
#### Evaluation of Data
 1. **Comma Separated Values (CSV)**
A plain text file that stores data by delimiting data entries with commas.
ex.

![image](https://user-images.githubusercontent.com/55933789/227850090-a7c53dca-81a7-4ad9-9a2d-cea89a76c81e.png)



|Advantage | Disadvantage|
|--|--|
|1. Easy to parse|1. The data type of element has to be interfered and is not a guarantee|
|2.Easy to read|2. Parsing become tricky when data contains commas|
|3.Easy to make sense of|2.Column names may or may not be there.|

2. **Relational Tables Definitions**
A relational database is *a type of database that stores and provides access to data points that are related to one another*. Relational databases are based on the relational model, an intuitive, straightforward way of representing data in tables.
ex. `CREATE TABLE distributors(
did integer PRIMARY KEY,
name VARCHAR(40)
);`

![image](https://user-images.githubusercontent.com/55933789/227850205-d75e56a3-e4e9-4b61-a96d-39dba56caca1.png)


|Advantages|Disadvantage|
|--|--|
|1. Data is fully types|1. Data gas to be flat|
|2.Data fits in a table|2. Data is stored in database, and data definition will be different for each database|

3. **JSON (JavaScript Object Notation)**
Json format can be shared across the network. An [open standard](https://en.wikipedia.org/wiki/Open_standard "Open standard")  [file format](https://en.wikipedia.org/wiki/File_format "File format") and [data interchange](https://en.wikipedia.org/wiki/Electronic_data_interchange "Electronic data interchange") format that uses [human-readable](https://en.wikipedia.org/wiki/Human-readable_medium "Human-readable medium") text to store and transmit data objects consisting of [attribute–value pairs](https://en.wikipedia.org/wiki/Attribute%E2%80%93value_pair "Attribute–value pair") and [arrays](https://en.wikipedia.org/wiki/Array_data_type "Array data type") (or other [serializable](https://en.wikipedia.org/wiki/Serialization "Serialization") values).

ex. 

    { "menu":
	    {
		    "id": "file",
		    "value": "File",
		    "popup": {
		    "menuitem": [
      {"value": "New", "onclick": "CreateNewDoc()"},
      {"value": "Open", "onclick": "OpenDoc()"},
      {"value": "Close", "onclick": "CloseDoc()"}
			    ]	
		     }
		 }
	 }
   
   ![image](https://user-images.githubusercontent.com/55933789/227850277-f7abff62-2dda-400f-a57a-432a92cb15ad.png)


|Advantages|Disadvantage|
|--|--|
|1. Data can take any form(arrays, nested elements)|1. Data has no schema enforcing|
|2. Widely accepted format on the web|2. Objects can be quite big in size because of repeated key.|
|3. can be pretty much any language||
|4. can be easily shared over a network|

4. **Protocol Buffers**
Protocol Buffers is defines by `.proto` text file. Can be easily read and understood by human.

```
// polyline.proto
syntax = "proto2";

message Point {
  required int32 x = 1;
  required int32 y = 2;
  optional string label = 3;
}

message Line {
  required Point start = 1;
  required Point end = 2;
  optional string label = 3;
}

message Polyline {
  repeated Point point = 1;
  optional string label = 2;
}
```

|Advantages|Disadvantage|
|--|--|
|- Data is fully typed|- Protobuf support for some language migh be lacking(but the main ones is fine)|
|- Data is compressed automatically (less CPU usage)|- Can't "open" the serialized data with a text editor(because it's compressed and serialized)|
|- Schema (defined using `.proto` file) is needed to generate code and read the data||
|- Documentation can be embedded in the schema|
|- Data can be read across any language (C#, Java, Go, Python, etc..)|
|Schema can evolve over time, in a safe manner(**Schema Evolution**)|
|3-10x smaller, 20-100x faster than XML|
|Code is generated for you automatically|


