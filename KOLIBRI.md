![Kolibri Logo](logo.png)

# Kolibri Programming Language

## Description

**Kolibri** is a multiparadigm programming language that merges features from various languages for easy and powerful coding. Highly optimized through the use of C++ for intermediate compilation, it also allows for direct memory management. Memory control is strictly governed by a revolutionary system of "dictatorship pointers." 

Kolibri aims to support procedural, functional, and object-oriented programming paradigms. It automatically infers variable types, simplifying syntax and eliminating issues like `nullptr` and uninitialized variables. Kolibri's syntax is designed for maximal brevity and readability.

---

## Disclaimer

**ALPHA VERSION 0.1**: The current version lacks the majority of planned future functionalities like Classes, Realms, Lambdas, Standard Functions, etc. The compiler also has significant issues. To report bugs or to contribute to the project, please email us at [latestback@gmail.com](mailto:latestback@gmail.com).

## Program Structure

### Main File: `.lbo`

The cornerstone of a Kolibri program is a `.lbo` (LittleBird Object) file. This file serves as the entry point and reference point for the entire application. All the executable `.lb` files are located relative to this `.lbo` file within the `source` folder.

#### File Structure in `.lbo`

- **Main File**: Points to the primary `.lb` file
- **Secondary Files**: Points to other `.lb` files (optional, multiple allowed)
- **lib**: Points to libraries (optional, multiple allowed)

```text
main.lb
second.lb
lib
C:\LB\lib.lbc
```

### Executable Files: `.lb`

Executable files with `.lb` extension contain the actual code and are associated with the main `.lbo` file.

#### Built-in Main Function

The main `.lb` file has an embedded `Main(args:[string])` function. It serves as the entry point for program execution. The function persists until a namespace, date, or class is defined.

**Example: Recursive Main Function**

```c#
if args[0]::long == 0 || args[0]::long == 1: => 1;
=> Main([(args[0]::long - 1)::string]);
```

### Libraries: `.lbc`

Kolibri libraries use the `.lbc` (LittleBird Compiled) extension and can be specified in the `.lbo` file under the `Lib` section.

### Running the program

To compile and run the program:

1. Click the PCM on `.lbo`
2. Select the item `Properties`
3. Opposite `Application` click on `Change...`
4. Change to the compiler `Kolibri` (if not in standard programs, then select manually)
5. Run it

The executable file is compiled in the folder with `.lbo`

## Creating Variables and Immutability

In programming, a variable is essentially a storage box for data. You can think of it as a container where you put things (values) that you might need later. Kolibri streamlines the process of creating variables through its syntax.

### Variable Declaration

In Kolibri, a variable is declared using the syntax `name = expression;`. The name can begin with an underscore (`_`), followed by English letters, and numbers (not as the first character). The compiler determines the variable's type by analyzing the expression.

**Example**: 
```c#
count = 10;
```

If a variable with the same name already exists, the syntax `name = expression;` will not create a new variable but change its value instead.

**Example**:
```c#
count = 20;  // Now, count is 20, not 10
```

If the type of the new expression does not match the existing variable's type, an error will occur rather than a type change.

**Example**:
```c#
count = "ten";  // This will throw an error
```

### Immutability

There are scenarios where you want a variable to remain unchanged during its lifetime. Note that this is different from a constant; it's more like a compiler-level block on reassignment.

To declare an immutable variable, use the syntax `=name = expression;`.

**Example**:

```c#
=answerToTheUltimateQuestionOfLifeTheUniverseAndEverything = 42; // This variable cannot be changed
```

## Data Types and Literals

Data types define the nature and type of data that can be stored in a variable. Literals are constant values used for representing these types within expressions. Below is a comprehensive table of data types available in Kolibri, their literals, and storage sizes.

| Data Type | Literals          | Size    | Description          |
|-----------|-------------------|---------|----------------------|
| `bool`    | `true` \| `false` | 1 byte  | Logical type         |
| `byte`    | `34b`             | 1 byte  | Integer type         |
| `short`   | `54s`             | 2 bytes | Integer type         |
| `int`     | `42i`             | 4 bytes | Integer type         |
| `long`    | `64`              | 8 bytes | Integer type         |
| `extra`   | `42e`             | 16 bytes| Integer type         |
| `float`   | `43f` \| `.1f` \| `1.1f` | 4 bytes | Floating-point type |
| `double`  | `.1` \| `1.1`     | 8 bytes | Floating-point type  |
| `quad`    | `43q` \| `.1q` \| `1.1q`  | 16 bytes| Floating-point type |
| `string`  | `"Hello, World!"` | 2 bytes per char | Unicode string type |

## Standard Input and Output

Interacting with the console is a fundamental part of programming, and Kolibri provides several built-in methods for both input and output. Here are the core I/O functions:

### Output Methods

- **`console.Write(a:string)`**: Prints the string `a` to the console inline, without adding a new line at the end.

- **`console.WriteLine(a:string)`**: Prints the string `a` to the console and adds a new line at the end, pushing the cursor to the next line.

### Input Methods

- **`console.Read()`**: Reads input from the console until a space or newline character is encountered. The captured input is returned as a string.

- **`console.Read(a:string)`**: Prints the string `a` to the console first, then reads the subsequent input until a space or newline character is encountered. The captured input is returned as a string.

By using these methods, you can create interactive programs that can both display information to the user and capture user input for further processing.

## Standard Kolibri operations

### Operator Table

| Operator | Description          | Unary Right | Unary Left | Binary | Integers | Floats | String | Logical |
|----------|----------------------|-------------|------------|--------|----------|--------|--------|---------|
| +        | Addition             | No          | Yes        | Yes    | Yes      | Yes    | Yes    | No      |
| -        | Subtraction/Negation | No          | Yes        | Yes    | Yes      | Yes    | No     | No      |
| *        | Multiplication       | No          | No         | Yes    | Yes      | Yes    | No     | No      |
| /        | Division             | No          | No         | Yes    | Yes      | Yes    | No     | No      |
| %        | Modulus              | No          | No         | Yes    | Yes      | No     | No     | No      |
| ++       | Increment            | Yes         | Yes        | No     | Yes      | No     | No     | No      |
| --       | Decrement            | Yes         | Yes        | No     | Yes      | No     | No     | No      |
| !        | Logical NOT/Bitwise NOT | No       | Yes        | No     | No       | No     | No     | Yes     |
| &&       | Logical AND          | No          | No         | Yes    | No       | No     | No     | Yes     |
| \|\|     | Logical OR           | No          | No         | Yes    | No       | No     | No     | Yes     |
| ==       | Equal                | No          | No         | Yes    | Yes      | Yes    | Yes    | Yes     |
| !=       | Not Equal            | No          | No         | Yes    | Yes      | Yes    | Yes    | Yes     |
| <        | Less Than            | No          | No         | Yes    | Yes      | Yes    | No     | No      |
| >        | Greater Than         | No          | No         | Yes    | Yes      | Yes    | No     | No      |
| <=       | Less or Equal        | No          | No         | Yes    | Yes      | Yes    | No     | No      |
| >=       | Greater or Equal     | No          | No         | Yes    | Yes      | Yes    | No     | No      |
| <<       | Left Shift           | No          | No         | Yes    | Yes      | No     | No     | No      |
| >>       | Right Shift          | No          | No         | Yes    | Yes      | No     | No     | No      |
| &        | Bitwise AND          | No          | No         | Yes    | Yes      | No     | No     | No      |
| ^        | Bitwise XOR          | No          | No         | Yes    | Yes      | No     | No     | No      |
| \|       | Bitwise OR           | No          | No         | Yes    | Yes      | No     | No     | No      |

### Operator Precedence Table
| Precedence Level | Operators            | Type        |
|------------------|----------------------|-------------|
| 1.               | `++`, `--`           | Unary Left  |
| 2.               | `++`, `--`           | Unary Right |
| 3.               | `!`, `+`, `-`        | Unary Left  |
| 4.               | `*`, `/`, `%`        | Binary      |
| 5.               | `+`, `-`             | Binary      |
| 6.               | `<<`, `>>`           | Binary      |
| 7.               | `<`, `>`, `<=`, `>=` | Binary      |
| 8.               | `==`, `!=`           | Binary      |
| 9.               | `&`                  | Binary      |
| 10.              | `^`                  | Binary      |
| 11.              | `\|`                 | Binary      |
| 12.              | `&&`                 | Binary      |
| 13.              | `\|\|`               | Binary      |

### Type Conversion

In Kolibri, type compatibility is strict; operations work only between variables of the same type. This often necessitates type conversions. Kolibri features a specific syntax for this: `variable::type`. 

#### Example

```kolibri
i = 4;  // long
console.Write(i::string);
```

#### Information about Standard Type Conversions:

- **From Floating-Point to Integer**: Truncates the numbers after the decimal point.
- **To Bool**: Will be `true` if the value is 1 or "true".
- **To a Smaller Type**: Conversion might lose data, no guarantee of accuracy.
- **Bool to Others**: Converts to 1 or "true" if `true`, and 0 or "false" if `false`.
- **Universal**: Any standard type can be converted to any other standard type.

## If-Else Statements

For newcomers, an `if-else` statement is like a road with a fork. It helps the program decide which way to go based on whether a certain condition is met. So if the condition is true, the program will go one way (`if`), and if not, it will go another (`else`).

### Syntax 

1. **Single Statement**: If you're using it for a single statement, you write the `if` keyword, the condition, and then a colon. After that, you write the statement that gets executed if the condition is true. **Note**: With `else`, you don't use a colon.
    ```c#
    if some_condition: do_this();
    else do_that();
    ```
  
2. **Block of Statements**: If you have multiple statements to execute, you use curly braces to group them. 
    ```c#
    if some_condition {
        do_this();
        do_this_too();
    } else {
        do_that();
        and_that();
    }
    ```

#### Examples

- **Simple If-Else**

    ```c#
    if x == 1: console.Write("x is 1");
    else console.Write("x is not 1");
    ```
  
- **If-Else with Multiple Conditions (Else If)**

    ```c#
    if x < 0 {
        console.Write("x is negative");
    } else if x > 0 {
        console.Write("x is positive");
    } else {
        console.Write("x is zero");
    }
    ```

    or

    ```c#
    if x < 0: console.Write("x is negative");
    else if x > 0: console.Write("x is positive");
    else console.Write("x is zero");
    ```
  
## Loops and Control Structures in Kolibri

Kolibri introduces a fresh approach to looping and conditional statements. Let's delve into each of them, focusing on the unique `from` loop and its versatility.

### The `from` Loop

The `from` loop in Kolibri is incredibly flexible, capable of handling a variety of conditions and steps. 

#### Syntax

```c#
i from <start> [to|until] <end> [step <step_size>] [do <action>]
```

#### Algorithm

Initialize `i` to `<start>`.

For `<end>` of type `i`: 

> If `until` is used, loop until `i` is less than `<end>`. If `to` is used, loop until `i` is less than or equal to `<end>`.

For `<end>` of type `bool`: 

> If `until` is used, the loop is executed as long as `<end>` is true. If `to` is used, it loop is executed as long as `<end>` is false.

Apply `<step_size>` increment to `i` after each iteration if specified.

If `do <action>` is present, execute `<action>` on `i` during each loop iteration.

#### Examples

```c#
i from 0 to 10 // Iterates from 0 to 10, inclusive
i from 0 until 10 step 2 // Iterates from 0 to 9 with steps of 2
i from 0 to i > 4 // Iterates until i > 4 is false
i from 0 until i < 4 // Iterates until i < 4 is true
i from 0 to 10 do i.Do() // Executes i.Do() for each iteration from 0 to 10
```

### While Loop

A `while` loop in Kolibri runs the same block of code as long as a given condition is true.

**Syntax**:

```c#
while <condition>:
    // Single statement
```
or
```c#
while <condition> {
    // Multiple statements
}
```

**Example**:
```c#
i = 0;
while i < 10 {
    console.Write(i);
    i++;
}
```

### While Until Loop

The `while until` loop is a variation that also runs as long as its condition is true. 

**Syntax**:

```c#
while until <condition>:
    // code
```

**Example**:

```c#
i = 0;
while until i == 10
{
    console.Write(i);
    i++;
}
```

### While To Loop

The `while to` loop runs until the condition becomes true. It's useful when you want the loop to execute at least once.

**Syntax**:

```c#
while to <condition>:
    // code
```

**Example**:

```c#
i = 0;
while to i > 10:
    console.Write(++i);
```

### From Block

The `from` block serves as a conditional branching mechanism. It can compare a variable against multiple possible values and execute corresponding blocks of code.

**Syntax**:

```c#
from i 
{ 
    value1{}, 
    value2{} 
}
```

### From Loop

The `from` loop works similarly to a 'foreach' loop, running a block of code for each element in a collection.

**Syntax**:

```c#
i from j:
    console.WriteLine(i::string);
```

## Arrays in Kolibri

### What is an Array?

An array is like a list or a collection of variables that share the same name and type. Instead of declaring multiple variables to store related information, you can just create an array. It's like having a bunch of mailboxes under the same address, each with its own unique number. You can put something in a specific mailbox or take it out, just by knowing its number. 

### Declaring Arrays

In Kolibri, creating an array is a piece of cake. You've got three main ways to do it:

1. `variableName:[type; size];` 
   - This creates an empty array of a specific type and size. 
2. `variableName:[initialValue; size];` 
   - This creates an array with a set initial value for all elements.
3. `variableName = [value1, value2, value3];`
   - This initializes the array right away with specific values.

### Accessing Array Data

To get to the stuff in your 'mailboxes', you use the index, starting from zero.

```c#
arrayName[index]
```

### Getting the Size of the Array

If you ever need to know how many 'mailboxes' you've got, use:

```c#
arrayName.Len
```

### Looping Through an Array

Good news, you can use that nifty `from` loop with arrays too.

```c#
i from j:
    console.WriteLine(i::string)
```

### Multidimensional Arrays

Yeah, you can even have arrays of arrays, like a big ol' grid of mailboxes. You've got two types:

1. Jagged Array:
    ```c#
    value:[[type]; size]
    ```
2. Rectangular Array:
    ```c#
    value:[[type; sizeB]; sizeA]
    ```

## Functions in Kolibri

### What is a Function?

Think of a function as a mini-program inside your main program. It's like a magical box that takes something, does its magic, and sometimes gives something back. You can use this magic box again and again, anywhere in your program. It's a way to avoid repeating the same code over and over. 

### Creating Functions in Kolibri

In Kolibri, making a function is no big deal. You've got various syntax options for defining one:

1. **Typed Parameters**
    ```c#
    FunctionName(param1:type1, param2:type2)
    ```
2. **Default Values**
    ```c#
    FunctionName(param1 = expression1, param2 = expression2)
    ```
3. **Template-like (Type-less)**
    ```c#
    FunctionName(param1, param2)
    ```
    This one acts like a template, meaning you can pass any type and the function will adapt.
  
4. **Mixed Bag**
    ```c#
    FunctionName(param1:type1, param2 = expression2)
    ```
    Parameters with an expression must always come at the end.

### Function Body

Your function can have a single-line body:

```c#
Add(a, b) console.Write((a+b)::string);
```

Or a multi-line block:

```c#
Add(a, b) {
    console.Write((a+b)::string);
    console.Write("\n");
}
```

### Return Values

Your function can also return a value using the `=>` symbol:

```c#
Add(a, b) => a+b;
```

### Calling Functions

To use your function, you just call it by its name and provide the necessary 'ingredients':

```c#
FunctionName(expression1, expression2, expression3);
```

## Pointers and Their Control System in Kolibri

### What are Pointers?

Imagine you have a box somewhere in your room. Instead of going to the box every time you need something from it, you can use a "map" that directly points to this box. This map is what we call a "pointer" in programming. It points to the location in memory where your data (the box) is stored.

### Naming (Dereferencing) and Pointing To (Referencing)

- **Naming or Dereferencing (`<pointer>`)** means you're looking inside the box. You're getting the actual data the pointer is pointing to.
  
- **Pointing To or Referencing (`>variable<`)** is creating that map to your box. You're getting the location of your data in memory.

### Syntax

1. **Creating a Pointer**
    ```c#
    pointer = >variable<;
    ```

2. **Dereferencing a Pointer**
    ```c#
    <pointer>
    ```
   
### Rules

1. **Null Pointers**: In Kolibri, you can't have a pointer that doesn't point to anything. It must always have a destination.
  
2. **Pointer to Pointer**: Kolibri says "Hell no!" You can't have pointers pointing to other pointers, unless you're working with dynamic arrays (covered later).

### Examples

```c#
a = 7;
b = >a<;
c = >b<; // This will throw an error
```

## Kolibri's Revolutionary Pointer Control System - Dictatorship Model

### The Basics

It dictates which pointer gets the right to rule and change the variable it's pointing at. It's all about control and accountability, making sure you're not playing fast and loose with your memory locations.

### Terms

- **Owner**: The original keeper of the data.
- **Usurped**: Original owner but with read-only access.
- **Dictator**: The one who snatches the write-access from the original owner.
- **Overthrown**: A former dictator without write-access.
- **Henchman**: A secondary pointer with read-only access.

### Examples

**Single Dictator**

```kolibri
a = 7; // owner
b = >a<; // `a` is usurped, `b` is the dictator pointer to a
```

**Overthrowing a Dictator**

```kolibri
c = >b<; // `b` is overthrown now, `c` is the dictator to `a`
```

**Multiple Henchmen**

```kolibri
=d = >c<; // `d` is a henchman to `a`, `c` is the dictator to `a` now
```

### Conditional Context

```kolibri
a = 7;
b = >a<;
if a == 5 {
    c = b; // `b` is now read-only, `c` rules
} // c is destroyed, `b` rules again
```

### Returning Pointers from Functions

```kolibri
a = 1;
b = >a<;
if a == 0: c = Boo(); // b is overthrown by c
else Boo(b); // b remains dictator

Boo() {
    a = 7;
    => >a<;
}
```

### Restrictions

You can't overthrow or return foreign dictators inside a function:

```kolibri
Boo(a:<long>) b = a; // Error: cannot overthrow foreign
Boo(a:<long>) => a; // Error: cannot return foreign
```

### Dynamic Ownership

```kolibri
a = 1;
b = 2;
c = >a<; // c is dictator for a ownership
c = >b<; // c is dictator for b ownership, a is back to being the owner
```

## Data Containers in Kolibri

### What Are Data Containers?

Data containers, or custom data types, are like mini-databases for storing multiple data elements in one block. They allow you to group various fields and methods that operate on those fields. It’s like making a super-variable with its own sub-variables and functionalities. Ideal for newbies who don't want to get lost in a sea of variables.

### Syntax for Creating Data Containers

You define a data container using the `data` keyword. Here's the basic syntax:

```rust
data Name:
  field1:type;
  field2:type;
  MethodName(params) {}
```

### Initializing Data in Code

You initialize a data variable in one of two ways:

1. Specifying the fields explicitly:  
  ```rust
  var:DataType(field1:expr1, field2:expr2);
  ```
  
2. Implicit initialization using positional arguments:  
  ```rust
  var:DataType(expr1, expr2);
  ```

### Accessing Methods

You access a method within the data container like this:

```rust
variable.MethodName(params);
```

### Real-world Example

Let's create a `Person` data container with a `greet` method.

```rust
Vitalii:Person("Vitalii", 18);
Vitalii.greet();  // Output: "Hello, my name is Vitalii and I'm 18 years old."

data Person:
  name:string;
  age:int;
  Greet() 
    console.Write("Hello, my name is " + name + " and I'm " + (age)::string + " years old.");
```

### Dependent Fields

You can make one field dependent on another during initialization. Here's an example using a `Square` data container:

```rust
a:Square(1);
console.Write(a.y::string);  // Output: "1"

data Square:
  x:int;
  y = x;
```

### Dictatorship in Data Containers

#### How It Works

In Kolibri, the dictatorship concept also applies to data containers but with a little twist. Unlike regular dictators declared in the code context, the mutability (or immutability) of a dictator within a data container is determined at the time of the data object's creation and remains fixed.

#### Wrong Example

In the following example, we cannot make `c` a dictator for `a.value` because `a` is immutable within the data context:

```kolibri
b = 7;
a:Data(value: >b<);
c = a.value;  // Error: can't overthrow `a` because `a` is protected by data

data Data:
  value:<long>;
```

#### Correct Example

Here, `a.value` is mutable (denoted by the `=` before the field definition), and it can act as a henchman for `b`. Then `c` can also become a henchman for `b`.

```kolibri
b = 7;
a:Data(value: >b<);  // Correct: b is the owner, a.value is a henchman
c = a.value;  // Correct: b is the owner, a.value is a henchman, c is also a henchman

data Data:
  =value:<long>;
```

#### Resource Management

This mechanism aids in proper resource management. If a data container that holds a dictator is destroyed, the dictator is also destroyed automatically. This can help prevent resource leaks and make your code more efficient.

## Dynamic Arrays in Kolibri

### What Are They?

Dynamic arrays in Kolibri are essentially pointers to contiguous blocks of memory that can be resized during runtime. Yep, you heard me right, it's basically a glorified pointer but with some extra functionalities and sugar to make it easier to work with.

### Initialization

You can initialize a dynamic array in multiple ways:

- By specifying the type and size: `var:<type; size>;`
- By specifying an initial value and size: `var:<initVal; size>;`
- By directly assigning values: `var = <exp1, exp2, exp3>;`

### Accessing Data and Finding Length

You can access elements of the array using zero-based indexing: `array[index]`.

To get the length of the array, you use `array.Len`.

### Looping through an Array

You can loop through an array using constructs like:

```kolibri
i from j:
    console.WriteLine(i::string);
```

### Pointers but Not Really

Even though dynamic arrays are essentially pointers, you can't dereference them like you might expect. It's designed this way for type safety and readability, I guess.

### Multidimensional Arrays

You can have jagged arrays with this syntax: `value:<<type>; size>;`. If you want to have rectangular arrays, you can do so with `value:<<type; sizeB>; sizeA>;`.

### Dynamic Arrays vs. Regular Arrays

- The dictatorship concept applies to dynamic arrays. You can have owners, henchmen, and dictators for your dynamic array.
- When you pass a dynamic array to a function, it goes as a pointer; regular arrays are passed by value.
- Regular arrays in Kolibri have more functions and can be dynamically resized.

### C++ Analogy

For those of you who're familiar with C++, a dynamic array in Kolibri is like a raw dynamic array in C++, and the regular array is more like a `vector`.

## Functions as Pointers in Kolibri

### Introduction

In many languages, functions are often treated as "first-class citizens." What this means is that they can be assigned to variables, passed around, returned from other functions, and so on. Kolibri follows the same philosophy but adds its own twist to it. Here, you can store pointers to functions in specific types.

### Syntax

To define the type of a function pointer, you use the following syntax:

```
param1:param2:returnType
```

To assign a function pointer, you use the function name without the parentheses:

```
function
```

### Limitations

Once you've got a function pointer, you can only invoke the function through it. You can't change the function or dereference the pointer. Here's an example:

```c++
Boo(Add, 5, 6);
Boo(op:long:long:long, a:long, b:long) console.Write(op(a, b)::string);
Add(a:long, b:long) => a + b;
```

### Void Types

If the function doesn't take any parameters or doesn't return anything, you use `void`. Like so:

```c++
Boo(Do);
Boo(f:void:void) f();
Do() console.Write("Hello, World!");
```

### Templates

When working with function templates, you need to specify the types using angle brackets `<>`. For instance:

```c++
Boo(Add<long, long>, 5, 6);
Boo(op:long:long:long, a:long, b:long) console.Write(op(a, b)::string);
Add(a, b) => a + b;
```

## Namespaces in Kolibri

### Introduction

Namespaces are a critical feature in many programming languages, helping to organize code, manage scope, and prevent naming collisions. In Kolibri, the `space` keyword is used to define a namespace. It offers you the ability to keep related functionalities together under a single umbrella, facilitating cleaner and more maintainable code.

### Syntax

Declaring a namespace in Kolibri is straightforward:

```kolibri
space name:
```

To call a function within a namespace:

```kolibri
spaceName.FunctionName();
```

If you use the `use` keyword to import a namespace, then you can call the function directly:

```kolibri
use:spaceName;
FunctionName();
```

### Nested Namespaces

Namespaces can be nested using the `.` notation. For example:

```kolibri
space name1.name2:
Foo();
```

If you use `use:name1;`, you can call the nested function like this:

```kolibri
name2.Foo();
```

But you can't call it directly as `Foo()`.

### Functions within Namespaces

To define a function within a namespace without explicitly writing out the whole space block, you can use the following syntax:

```kolibri
spaceName.Boo(){}
```

For instance:

```kolibri
use:test;
Hello();
test.Hello() console.Write("Hello, World!");
```

This is equivalent to:

```kolibri
use:test;
Hello();
space test:
Hello() console.Write("Hello, World!");
```
