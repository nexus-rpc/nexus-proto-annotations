# nexus-proto-annotations

Protobuf annotations for Nexus services and operations.

## Install

### With buf

Add a dependency to your `buf.yaml` file:

```
deps:
  - buf.build/nexus-rpc/nexusannotations
```

### Unmanaged

Copy the `nexusannotations` directory from this repository and include it as one of the sources to `protoc`.

## Usage

### Service

#### (nexusannotations.v1.service).name

`string`

Defines the Nexus Service name. Defaults to the proto Service full name.

**Example:**

```protobuf
syntax = "proto3";

package example.v1;

import "nexusannotations/v1/options.proto";

service ExampleService {
  option (nexusannotations.v1.service).name = "example.v1.Example";
}
```

#### (nexusannotations.v1.service).tags

`repeated string`

Tags a Nexus Service. Used by code generators for Service inclusion and exclusion.

**Example:**

```protobuf
syntax = "proto3";

package example.v1;

import "nexusannotations/v1/options.proto";

service ExampleService {
  option (nexusannotations.v1.service).tags = "tag1";
  option (nexusannotations.v1.service).tags = "tag2";
}
```

### Method

#### (nexusannotations.v1.operation).name

`string`

Defines the Nexus Operation name. Defaults to the proto Method name.

**Example:**

```protobuf
syntax = "proto3";

package example.v1;

import "nexusannotations/v1/options.proto";

service ExampleService {
  rpc Foo(FooInput) returns (FooResponse) {
	option (nexusannotations.v1.operation).name = "foo";
  }
}
```

#### (nexusannotations.v1.operation).tags

`repeated string`

Tags a Nexus Service. Used by code generators for Operation inclusion and exclusion.

**Example:**

```protobuf
syntax = "proto3";

package example.v1;

import "nexusannotations/v1/options.proto";

service ExampleService {
  rpc Foo(FooInput) returns (FooResponse) {
	option (nexusannotations.v1.operation).tags = "tag1";
	option (nexusannotations.v1.operation).tags = "tag2";
  }
}
```

## Contribute

### Generate Go files

Any change in the proto definitions must be reflected in the associated Go package and commited. Run the following command on change:

`buf generate`


### Push to the buf registy

`buf push`
