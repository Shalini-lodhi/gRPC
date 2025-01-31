# gRPC Demo

### 1. Set up
**Add Dependencies (Maven)**
Add the following dependencies in `pom.xml`

### Step 2: Define the gRPC Service (hello.proto)
This defines a gRPC service called `Greeter` with a single method `SayHello`, which takes a `HelloRequest` and returns a `HelloReply`.

### Step 3: Generate Java Code from `.proto`
Use the `protoc` compiler to generate the Java classes:
```sh
protoc --java_out=src/main/java --grpc-java_out=src/main/java -I=src/main/proto src/main/proto/main.proto
```
This generates Java files inside `com/example/hello/` (for service and message types).