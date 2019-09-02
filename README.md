[![license](https://img.shields.io/github/license/RediSearch/redisearch-go.svg)](https://github.com/filipecosta90/redisai-go)
[![CircleCI](https://circleci.com/gh/filipecosta90/redisai-go/tree/master.svg?style=svg)](https://circleci.com/gh/filipecosta90/redisai-go/tree/master)
[![GitHub issues](https://img.shields.io/github/release/filipecosta90/redisai-go.svg)](https://github.com/filipecosta90/redisai-go/releases/latest)
[![Codecov](https://codecov.io/gh/filipecosta90/redisai-go/branch/master/graph/badge.svg)](https://codecov.io/gh/filipecosta90/redisai-go)
[![Go Report Card](https://goreportcard.com/badge/github.com/filipecosta90/redisai-go)](https://goreportcard.com/report/github.com/filipecosta90/redisai-go)
[![GoDoc](https://godoc.org/github.com/filipecosta90/redisai-go?status.svg)](https://godoc.org/github.com/filipecosta90/redisai-go)

# RedisAI Go Client

Go client for [RedisAI](http://redisai.io), based on redigo.

# Installing 

```sh
go get github.com/filipecosta90/redisai-go/redisai
```

# Usage Example

```go
package main

import (
    "fmt"
    "github.com/filipecosta90/redisai-go/redisai"
    "log"
)

func ExampleClient() {

	// Create a client. 
	client := redisai.Connect("redis://localhost:6379", nil )

	// Set a tensor
	// AI.TENSORSET foo FLOAT 2 2 VALUES 1 2 3 4
	client.TensorSet( "foo" , TypeFloat, []int{2,2}, []float32{1.1,2.2,3.3,4.4} )
	
	// Get a tensor content as a slice of values
    // dt DataType, shape []int, data interface{}, err error
    _, _, fooTensorValues, err := client.TensorGetValues( "foo" )

	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(fooTensorValues)
	// Output: [ 1 2 3 4 ]
}
```
