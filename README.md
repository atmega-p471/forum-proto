# Forum Proto Definitions

This module contains gRPC protocol buffer definitions for the forum microservices project.

## Overview

This module defines the communication contracts between:
- **auth-service** - Authentication and authorization
- **forum-service** - Forum messages and topics

## Structure

```
proto/
├── auth/
│   ├── auth.proto      # Auth service definitions
│   ├── auth.pb.go      # Generated Go code
│   └── auth_grpc.pb.go # Generated gRPC Go code
└── forum/
    ├── forum.proto      # Forum service definitions  
    ├── forum.pb.go      # Generated Go code
    └── forum_grpc.pb.go # Generated gRPC Go code
```

## Services

### Auth Service
- `AuthService.Register` - User registration
- `AuthService.Login` - User authentication  
- `AuthService.ValidateToken` - JWT token validation
- `AuthService.GetUserInfo` - Get user details

### Forum Service  
- `ForumService.CreateMessage` - Create new message
- `ForumService.GetMessages` - Retrieve messages
- `ForumService.UpdateMessage` - Update existing message
- `ForumService.DeleteMessage` - Delete message

## Usage

### As Go Module

```bash
go get github.com/YOUR_USERNAME/forum-proto
```

```go
import (
    authpb "github.com/YOUR_USERNAME/forum-proto/auth"
    forumpb "github.com/YOUR_USERNAME/forum-proto/forum"
)
```

### Regenerating Proto Files

Install protoc and Go plugins:
```bash
# Install protoc compiler
# Windows: Download from https://github.com/protocolbuffers/protobuf/releases
# Linux: sudo apt install protobuf-compiler
# macOS: brew install protobuf

# Install Go plugins
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

Generate code:
```bash
# From auth/ directory
protoc --go_out=. --go-grpc_out=. auth.proto

# From forum/ directory  
protoc --go_out=. --go-grpc_out=. forum.proto
```

## Requirements

- Go 1.20+
- protoc compiler
- protoc-gen-go plugin
- protoc-gen-go-grpc plugin

## License

MIT 