# Java - fundamentals

Variables, Primitive data types, Arithmetic operators, Type conversion

## Variables:

Java -> strongly typed
// int dataValue;
// datavValue = 100;
// int myInfo = 200;

- value can be modified

## Naming conventions:

1.  letters, numbers, \$, \_

- convention -> letter and numbers

2.  first character is not a number

- always letter

3.  Camel case - Primitive Data Types

- built into the language

4. categories of primitive types

- Integer
- Floating point
- Character
- Boolean

## Integer types:

- byte - 8 bits
- short - 16 bits
- int - 32 bits
- long - 64 bits - 0L

## Floating Point types:

- IEE 754 floating point standard
- containing a fractional portion

- float - 32bits - 0.0f
- 65 bits - 0.0 or 0.0d

## Character and Boolean types:

- stores a single Unicode character
- single quotes
- unicode code points '\u00DA' (4 digit hex value)

- true/false values

## Java primitive types are stored by-value

Basic math operators:
add, substract, multiply, divide, modulus

## Prefix/Postfix operators:

-- ++

## Compound assignment operators:

- applies result of right side to left side
  +=, -=, \*=, /=, %=

## Operator precedence:

postfix -> prefix -> multiplicative -> additive
same precedence -> left to right

## Type conversion:

- implicit type conversion (performed automatically by the compiler)
  // int iVal = 50;
  // long lVal = iVal;
- widening conversions are automatic
- mixed integer sizes:
  - user largest integer in equation
- mixed floating point sizes:
  - uses double
- mixed integer and floating point:

  - uses largest floating point in equation

- explicit type conversion (cast operator)
  // long lVal = 50;
  // int iVal = (int) lVal;
- can perform widening and narrowing
- floating point to integer drops fraction
- integer to floating point can lose precision

## Conditional Logic, Looping, Arrays

## Conditions:

- relational operators - >, >=, <=, <, ==, !=
- conditional assignments - result = condition ? true : false
- the if statement
  if(condition)
  true;
  else if(condition2)
  true
  else
  false;
- logical operators -> &, | , ^ (exclusive or (XOR)), !
- conditional logical operators -> &&, ||
  && only executes right-side if left-side is true
  || only executes right-side if left-side is false

## Block statements:

```java
int v1 = 10, v2 = 4, diff;
if(v1 > v2) {
diff = v1 - v2
}

```

## Loops

- while loop
- do-while loop
- for

//
while(condition)
statement;

do
statement;
while(condition);

for(initialize; condition; update)
statement

## Arrays:

- provides an ordered collection of elements
  float[] theVals = new float[3];
  float[] theVals = {10.0f, 20.0f, 30.0f}
  theVals[0] = 10.0f;
  theVals[1] = 20.0f;
  theVals[2] = 30.0f;

```java
float sum = 0.0f;

for(int i = 0; i < theVals.length; i++){
sum += theVals[i]l
}

```

For-each loop:

for(lopp-variable-declaration:array){
statement;
}

```java
float[] theVals = {10.0f, 20.0f, 30.0f}
float sum = 0.0f;

for(float currentVal: theVals){
sum += currentVal;
}

Switch:
(only primitive types supported are char and integers)
switch(test-value){
case value-1:
statements
case value-2:
statement
default:
statement
}

```

```java
int iVal = 10;
switch(iVal % 2){
case 0:
System.out.print("is even")
break;
case 1:
System.out.print("is odd")
break;
default:
System.out.print(zjebało")
break;
}

```

```

```
