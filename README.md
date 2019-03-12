# Tron Node Protocol

This npm package contains the compiled to node.js tron protocol gRPC API code.  
The code was compiled from https://github.com/tronprotocol/protocol

## Introduction

Tron protocol offers two ways to communicate with nodes : http and gRPC API.  
The gRPC API is specified with google protobuf, which is a mechanism for serializing structured data and an Interface Description Language.  
Google Protobuf code can be compiled to different languages - C++, Java, Node.js, etc.  
This package is a compiled to Node.js google protobuf code.

## Steps to compile the code :

###### Download the latest version of the protocol

```
git clone https://github.com/tronprotocol/protocol.git && cd protocol/
```

###### Install google apis required for the compilation process

```
./install-googleapis.sh
```

###### Create a folder which will contain the artifacts from the compilation

```
mkdir node-protocol/
``` 

###### Install grpc compilation tools

```
npm i -g grpc-tools
```

###### Run the compilation command for protocol/api/ files (artifacts are in node-protocol/api -> api_pb.js and api_grpc_pb.js)

```
protoc --js_out=import_style=commonjs,binary:node-protocol/ --grpc_out=node-protocol/ --plugin=protoc-gen-grpc=\`which grpc_tools_node_protoc_plugin` api/api.proto
```
###### Run the compilation command for protocol/core/ files (artifacts are in node-protocol/core)

```
protoc --js_out=import_style=commonjs,binary:node-protocol/ core/*
```