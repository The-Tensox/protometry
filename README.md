
# protometry

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/52ed0a7a050c470ababeb6e888d51878)](https://app.codacy.com/gh/The-Tensox/protometry?utm_source=github.com&utm_medium=referral&utm_content=The-Tensox/protometry&utm_campaign=Badge_Grade_Dashboard)
[![Build Status](https://img.shields.io/circleci/project/The-Tensox/protometry/master.svg)](https://circleci.com/gh/The-Tensox/protometry)

Geometry on protobuf stubs, could be also implemented in other languages.

## Installation

```bash
go get github.com/louis030195/protometry-go
# Build for gRPC
# If using gRPC go get -u github.com/golang/protobuf/protoc-gen-go
protoc -I . --go_out=plugins=grpc:. protometry.proto
# Without gRPC
# protoc -I . --go_out=. protometry.proto
```

## Usage

```go
vector := NewVector3One() // 1,1,1
log.Printf("My vector: %s", vector.Get(1)) // 1
vector.Set(0, 12.6422)

v := NewVectorN(0, 0, 0)
v.Mul(3.5) // 0,0,0
v.Add(v) // 0,0,0

a := NewBox(*NewVectorN(0, 0, 0), *NewVectorN(1, 1, 1))
b := NewBoxOfSize(*NewVectorN(2, 2, 2), 0.5)
a.Inside(*b) // False
```

## Features

### Vectors

- [x] Build vectors of N dimensions
- [x] Vector comparison (min, max, equal)
- [x] ToString
- [x] Normalization
- [x] Absolute value
- [x] Add, Sub, Mul(scalar product), Dot(vector product), Div(scalar division), Cross product, Euclidean Norm, Angle, Lerp
- [ ] Encoding

### Volumes

- [x] Box Intersections, Inside
- [ ] Other volumes (sphere, capsule, Convex ...)

## Test

```bash
go test -v github.com/The-Tensox/protometry
```
