# gRPC Go Blog
gRPC Blog example in Go

## Clone the project
```
git clone https://github.com/kirils/grpc-go-blog.git
cd grpc-go-blog
```

## Install MongoDB
```
https://www.mongodb.com/
```

## Install Go language
```
https://golang.org/doc/install
```

## Install gRPC
```
$ go get -u google.golang.org/grpc
```

## Install Protocol Buffers v3
Install the protoc compiler that is used to generate gRPC service code. The simplest way to do this is to download pre-compiled binaries for your platform(protoc-<version>-<platform>.zip) from here: https://github.com/google/protobuf/releases

Unzip this file.
Update the environment variable PATH to include the path to the protoc binary file.
Next, install the protoc plugin for Go

```
$ go get -u github.com/golang/protobuf/protoc-gen-go
```
```
$ export PATH=$PATH:$GOPATH/bin
```

## Run gRPC Blog Server
```
$ cd blog_server
$ go run server.go
```

## Run gRPC Blog Client
```
$ cd blog_client
$ go run client.go
```

## Use Evans gRPC client to make requests to server
```
https://github.com/ktr0731/evans
```

```
$ evans

evans 0.6.9

Usage: evans [options ...] [PROTO [PROTO ...]]

Positional arguments:
	PROTO			.proto files

Options:
	--edit, -e		edit config file using by $EDITOR
	--repl			start as REPL mode
	--cli			start as CLI mode
	--silent, -s		hide splash
	--host HOST		gRPC server host
	--port PORT, -p PORT	gRPC server port
	--package PACKAGE	default package
	--service SERVICE	default service
	--call CALL		call specified RPC by CLI mode
	--file FILE, -f FILE	the script file which will be executed by (used only CLI mode)
	--path PATH		proto file paths
	--header HEADER		default headers which set to each requests (example: foo=bar)
	--web			use gRPC Web protocol
	--reflection, -r	use gRPC reflection

	--help, -h		display this help and exit
	--version, -v		display version and exit
least one proto file required
```

```
$ evansevans -p 50051 -r

  ______
 |  ____|
 | |__    __   __   __ _   _ __    ___
 |  __|   \ \ / /  / _. | | '_ \  / __|
 | |____   \ V /  | (_| | | | | | \__ \
 |______|   \_/    \__,_| |_| |_| |___/

 more expressive universal gRPC client


default@127.0.0.1:50051> show pa
pa: unknown target

default@127.0.0.1:50051> show package
+---------+
| PACKAGE |
+---------+
| default |
+---------+

default@127.0.0.1:50051> show service
+-------------+------------+-------------------+--------------------+
|   SERVICE   |    RPC     |    REQUESTTYPE    |    RESPONSETYPE    |
+-------------+------------+-------------------+--------------------+
| BlogService | CreateBlog | CreateBlogRequest | CreateBlogResponse |
|             | ReadBlog   | ReadBlogRequest   | ReadBlogResponse   |
|             | UpdateBlog | UpdateBlogRequest | UpdateBlogResponse |
|             | DeleteBlog | DeleteBlogRequest | DeleteBlogResponse |
|             | ListBlog   | ListBlogRequest   | ListBlogResponse   |
+-------------+------------+-------------------+--------------------+

default@127.0.0.1:50051> service BlogService

default.BlogService@127.0.0.1:50051> call CreateBlog
blog::id (TYPE_STRING) =>
blog::author_id (TYPE_STRING) => "Kiril"
blog::title (TYPE_STRING) => "First Blog"
blog::content (TYPE_STRING) => "This is my fisrst Blog"
{
  "blog": {
    "id": "5cca003bfe6110a60bbf7f16",
    "authorId": "\"Kiril\"",
    "title": "\"First Blog\"",
    "content": "\"This is my fisrst Blog\""
  }
}

default.BlogService@127.0.0.1:50051>
```