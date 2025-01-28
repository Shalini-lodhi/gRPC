# gRPC
## 1. What is gRPC?
- `gRPC` (Google Remote Procedure Call) is a framework for building APIs. It helps different systems communicate with each other, even if they're written in different languages.
- Instead of sending HTTP requests, it uses a faster and more efficient system called Protocol Buffers (`Protobuf`).

## 2. Why Use gRPC?
- **Efficiency**: Faster than REST because it uses binary data (Pro`tobuf) instead of JSON.
- **Streaming**: Supports sending multiple pieces of data back and forth in one connection.
- **Cross-Language**: Works with many programming languages.
- **Strong Typing**: Protobuf ensures data structure is correct.
---

# Protocol Buffers
[Official Documentation](https://protobuf.dev/overview/#:~:text=Protocol%20buffers%20are%20ideal%20for,gRPC%29%20and%20for%20data%20storage.)

`Protocol Buffers` are a language-neutral, platform-neutral extensible mechanism for serializing structured data.
- A way to define structured data (like JSON but faster).

### 1. How it works:
  - Define your data structure in a `.proto` file.
  - Generate Java code using the Protobuf compiler.
  - Use the generated code in your application.


### 2. How Protocol Buffer used?
- Client and Server:
  - The *client* calls a method (like a function).
  - The *server* executes the method and sends a response.
- Steps:
  1. Define the service in a `.proto` file.
  2. Generate Java code from the `.proto` file.
  3. Implement the server logic.
  4. Create a client to call the server.

### 3. Streaming in gRPC
1. **Unary RPC**: Client sends one request, gets one response (like above example).
2. **Server Streaming**: Server sends multiple responses for one request.
3. **Client Streaming**: Client sends multiple requests, server sends one response.
4. **Bidirectional Streaming**: Both client and server send multiple messages.

### 4. Advantages of using protocol buffers

-   Compact data storage
-   Fast parsing
-   Availability in many programming languages
-   Optimized functionality through automatically-generated classes

![](https://protobuf.dev/images/protocol-buffers-concepts.png)

--- 

# Evaluation of Data
### 1. **Comma Separated Values (CSV)**
A plain text file that stores data by delimiting data entries with commas.
ex.

![image](https://user-images.githubusercontent.com/55933789/227850090-a7c53dca-81a7-4ad9-9a2d-cea89a76c81e.png)



|Advantage | Disadvantage|
|--|--|
|1. Easy to parse|1. The data type of element has to be interfered and is not a guarantee|
|2.Easy to read|2. Parsing become tricky when data contains commas|
|3.Easy to make sense of|2.Column names may or may not be there.|
---
## 2. **Relational Tables Definitions**
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
---
## 3. **JSON (JavaScript Object Notation)**
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
---
## 4. **Protocol Buffers**
Protocol Buffers is defines by `.proto` text file. Can be easily read and understood by human.

```
// polyline.proto
syntax = "proto3";

package example;

service Greeter {
    rpc SayHello (HelloRequest) returns (HelloReply);
}

message HelloRequest {
    string name = 1;
}

message HelloReply {
    string message = 1;
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


