# Syntax And Types

## Predefined Identifiers

### Constants

true false iota nil

### Types

bool int uint byte rune string float32 float64 etc...

### Functions

make len cap new append copy etc...


## Operators & Delimiters

< > - + = != etc 

See this [ref](https://go.dev/ref/spec#Operators_and_punctuation).


# Declaring variables

## Long declaration
```go
var i int
var i int = 1 // immediate initialization, rarely used

```

## Short declarations
```go 
i := 1
i := int64(1) // do not desire go to infer the type
```

## Zero values

> All builtin types have zero value 

```go
func main() {
	var a int
	var b string
	var c float64
	var d bool

	fmt.Printf("var a %T = %d\n", a, a)
	fmt.Printf("var b %T = %q\n", b, b)
	fmt.Printf("var c %T = %f\n", c, c)
	fmt.Printf("var d %T = %t\n\n", d, d)
}

/* output
var a int = 0
var b string = ""
var c float64 = 0.000000
var d bool = false
*/
```

## Nil value 

It is the default value for many common types

- maps
- slices
- functions
- channels
- interfaces
- errors


## Naming Rules

- Names must be one word
- Letters, numbers and underscore
- Cannot start with a number
- Are case sensitive
- Avoid using similar variable names of different case
- If first letter is uppercase, it will be exported, i.e. accessed from outside the package

## Naming Style

- Use short variable names, terse
- Given userName vs user, it is idiomatic to use user
- The smaller the scope of a variable, the smaller the variable name
- MixedCaps or mixedCaps is used instead of underscore
- It also important to agree on a naming style by the team!

```go
names := []string{"Mary", "John", "Bob", "Anna"}
for i, n := range names {
	fmt.Printf("index: %d = %q\n", i, n)
}
```

## Multiple assignment

Go allows you to assign several values to several variables on the same line

```go 
j, k, l := "gopher", 2.05, 15
fmt.Println(j)
fmt.Println(k)
fmt.Println(l)

/*
	output:
	gopher
	2.05
	15
*/
```
> Make sure not to compromise readability just to reduce line of codes

## Statistically typed

Go is statistically typed language. This means that each statement is checked at compile time. It also means that data type is bound to the variable, whereas dynamically typed languages the data type is bound to the value.

```go
var pi float64 = 3.14
var week int = 7
```
As opposed to other dynamic languages, e.g. PHP:
``` php
$s = "gopher";        // $s is a string
$s = 123;             // $s is now an integer
```

# Numeric Types

Go has two types of numeric types:

1. Architecture independent: regards of the architecture we compile for, we will always have the same number of bytes
2. Implementation specific: the size can vary based on the architecture the program built for

```go
// Go has the following architecture-independent numeric types

uint8       unsigned  8-bit integers (0 to 255)
uint16      unsigned 16-bit integers (0 to 65535)
uint32      unsigned 32-bit integers (0 to 4294967295)
uint64      unsigned 64-bit integers (0 to 18446744073709551615)
int8        signed  8-bit integers (-128 to 127)
int16       signed 16-bit integers (-32768 to 32767)
int32       signed 32-bit integers (-2147483648 to 2147483647)
int64       signed 64-bit integers (-9223372036854775808 to 9223372036854775807)
float32     IEEE-754 32-bit floating-point numbers (+- 1O-45 -> +- 3.4 * 1038 )
float64     IEEE-754 64-bit floating-point numbers (+- 5 * 10-324 -> 1.7 * 10308 )
complex64   complex numbers with float32 real and imaginary parts
complex128  complex numbers with float64 real and imaginary parts
byte        alias for uint8
rune        alias for int32

// In addition, Go has the following implementation specific types:
uint     either 32 or 64 bits
int      same size as uint
uintptr  an unsigned integer large enough to store the uninterpreted bits of a pointer value
```

## Picking the correct Numeric type

