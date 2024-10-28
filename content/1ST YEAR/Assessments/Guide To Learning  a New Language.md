---
tags:
  - How_to_Learn_a_New_Language
---
# INTRODUCTION

In this guide, we will discuss the main concepts of programming as they relate to TypeScript. On reading this, it is useful to note that much of what is discussed here is also applicable to JavaScript as the languages share a common syntax. While an existing familiarity with JavaScript will ease the transition to TypeScript, this guide is written under the assumption that the reader has no prior JavaScript knowledge and will therefore aim to cover each topic as comprehensively as possible.

The decision to formulate a guide for TypeScript as opposed to JavaScript is based upon best practices in programming. Though JavaScript is arguably more flexible due to being a dynamically typed language, the adoption of a strongly typed alternative such as TypeScript aids a more robust approach. By informing the compiler of the expected type, runtime errors are significantly reduced thus increasing the speed and efficiency of the development process. Ultimately, TypeScript and JavaScript are in most regards, the same language, with TypeScript adding strongly typed functionality on top of the existing JavaScript language. It should therefore be noted that plain JavaScript can be used in a TypeScript file, however, the same cannot be said for the converse case.

# TYPES

Variables in TypeScript, like in any other language, are categorised into a particular type with each type falling in to one of two categories: Primitive and Composite. Primitive types are essentially any type of variable which is not composed of other types such as Boolean, Number, or String. Conversely, composite types are built from multiple instances of primitive types. In TypeScript, such composite types are: Array, Tuple, Object, and Enum. In addition, TypeScript also offers a number of "special types" which can be used, however these are generally used in very specialist circumstances or to allow the flexibility of a variable to take on any type while maintaining the statically typed syntax.

#### Static vs Dynamic Typing

As previously touched on in the introductory section, TypeScript is a strongly typed language (as opposed to it's dynamically typed counterpart: JavaScript). In general, programming languages fall into one of two categories: Statically typed, and Dynamically typed. The difference between these lies fundamentally in where the type checking occurs. As TypeScript is a statically typed language, type checking occurs at the time of compilation as opposed to runtime, as it the case with dynamically typed languages. However, since TypeScript is an extension of JavaScript which in itself is a dynamically typed language, code written in TypeScript is actually checked twice. First TypeScript's compiler will check the code against declared types to ensure compliance, then the code will be further checked in runtime as plain JavaScript.

#### Type Declaration

In TypeScript, the type of a variable or return type of a function is declared at the same time as the variable or function declaration. In the case of variables, multiple types can be declared at once by using a 'union type' if the programmer wishes for more flexibility without resorting to use of the 'any' type. Such declarations can be done as illustrated below:

```
let stringVar : string = "Hola Amigo"
let unionVar : string | number = 5
```

In the latter example above, the variable 'unionVar' can be assigned to either a string or a number as it has been declared using a union type. The first variable declared, however, can only be a string and will result in an error if attempting to assign a non-string value.

In the case of function declarations, types are declared for the functions return type itself as well as the arguments which the function takes, as shown below:

```
function newFunction(name: string, age: number) : string {
...
return "my name is: " + name + " and I am " + String(age)
}
```

In this example, the function takes two arguments of different types and returns a string, all of which is declared explicitly in the function declaration. However, TypeScript provides some flexibility when it comes to the return type in that it can infer the return type directly from the return statement itself. Declaring a functions return type is therefore optional but perhaps good practice to ensure that functions are defined as expected.
#### Type Conversion

As TypeScript is a strongly typed language, most type conversions a programmer will come across are in the form of explicit casting using either the 'as' keyword or wrapping the variable in brackets with the new type. 

```
let numVar : number = 5
let stringVar : string = "five"

stringVar = numVar as string
console.log(stringVar) // 5

stringVar = String(numVar)
console.log(stringVar) // "5"
```

These allow for converting the type only if the new type supports the value to be cast, however it should be noted that usage of the 'as' keyword does not actually change the value, but rather implements an allowance for  usage of values outside of the declared type. This can be seen in the above example where assigning  a number value to string type variable is made possible using the as keyword, however the value prints as a number rather than a string, as is the case when casting using 'String(...)'. Interrogation of these two methods will similarly reveal that despite the variable being initialised with a declared 'string' type, assigning a number value using 'as' returns "number" following usage of the 'typeof' operator, whereas casting using 'String(...)' returns a type of 'string'.

One interesting note on the topic of casting using the type name method is that this is actually done using object types as opposed to primitive type operations. In TypeScript, primitive types have a corresponding object type (differentiated by use of a capital letter) which allow for certain functionality such as casting to the respective type, as shown above. 

# VARIABLES

#### Declaration

In TypeScript there are three ways to declare a variable: var, let, and const. While const defines a variable which is constant and cannot therefore be further changed, var and let both define non-constant variables. The difference between var and let comes down to scope, with var having a much wider, function level scope than let's block level scope.

In general, this means that in most cases, it is wiser to opt for 'let' in order to safe guard against undesired value changes. However, cases do arise where a wider scope is necessary, thus necessitating the use of 'var' in the variable declaration. Below shows an example of how variables initialised using var can be seen outside of the for loop, whereas initialising the counter variable with 'let' narrows the scope.

```

for (var i = 0; i < 5; i++) {

}

console.log("outside i loop: " + i) // 5

for (let j = 0; j < 5; j++) {

}

console.log("outside j loop: " + j) // Error


```

#### Primitive Types

TypeScript's main primitive types are Boolean, Number, and String - all of which are commonly observed in many other programming languages and therefore should be familiar to all but the most novice of developers.

Boolean variables can take the value of either "true" or "false" and are declared explicitly using "boolean" as shown below:

```
let boolVar: boolean = true;
```

Similarly, number type variables are declared explicitly using "number". While the number type is the most commonly used numerical data type, it is worth noting that its usage is limited to a 64-bit size therefore larger numerical values may necessitate the use of "bigint". However, the number type is able to take a range of formats such as floating point, binary, octal, and hexadecimal values, the bigInt type can only take whole number values. While it's considered best practice to use the smallest type size possible, the limitations of the bigInt type should be taken into account when making later changes as converting from bigInt to number may result in reduced numerical accuracy. In addition, when multiple numerical values are used in a single operation, they must both be of the same type, therefore the decision regarding where to use number or bigInt may lie with the required size of the largest value used rather than the size of each individual value itself. Below shows an example of how number and bigInt types can and cannot be used as well as how to circumvent the restriction on using both types in the same operation:

```
let numOne: number = 50
let numTwo: bigint = 100n //

console.log(numOne + numTwo) // Error
console.log(numOne + Number(numTwo)) // 150
```

Regarding casting from bigInt to Number, it should be noted that this option is only possible if the value to be cast is within the limits of values able to be stored by a Number type variable.

It should be noted that TypeScript is versatile with regards to types and not only contains "null" and "unknown" primitive types, but also allows for declarations of any, void, or never types. Admittedly, the latter two types are most commonly seen in function return types as opposed to variable type declarations. Nonetheless, provision for usage of the 'unknown' and 'any' types are particularly useful on occasions where extra flexibility is needed than is generally allowed for within the strongly typed syntax.

A safer alternative to using the 'any' type is to use a union type. This involves declaring the type as a selection of types, such that the compiler will allow a value which conforms. to any one of those listed. This allows the compiler to run the strictest type checking possible while still maintaining some flexibility.

```
let numOrString : number | string = "five" // initialise to string
numOrString = 5 // set to number
```

#### Composite Types

In TypeScript, composite types are all considered objects therefore, while functionality exists to implement data structures such as Arrays and Tuples, TypeScript itself considers them objects and thus will return such when enquiring via the "typeof" operator.

```
let stringArray : string[] = ["This is a string", "This is another string"]

console.log(typeof(stringArray)) // "object"
```

Nonetheless, the functionality exists to use common composite data types seen in other languages such as Arrays, Tuples, Enums, and Dictionaries. As seen above, these can be declared in a similar manner to that of their primitive counterparts, i.e. 

```
let stringArray : string[]......(etc)
let numArray: number[]......(etc)
```

defines arrays containing string and number types, respectively. Tuples can similarly be declared, with the caveat that the type of each member of the tuple is declared separately and therefore allows for more flexibility in its declaration while maintaining the strongly-typed characteristics of TypeScript.

```
let stringTuple : [string, string, string]
let mixedTuple : [number, string, boolean]
```

As illustrated in the above examples, declaring the type of a variable in TypeScript involves declaring the primitive type of each component part of a composite type. In other words, a variable cannot be declared as as having an "array" type, but rather an array of strings, numbers, etc. This allows the compiler to determine if, for example, the correct *type* of array is being passed, thus making for a more robust type checking process.

Since the composite types in TypeScript are all specific implementations of the Object type, it is possible to also set the type as a user defined object. This allows the the compiler to incorporate object-specific functions to the type checking process.

```
let honda : Car = newCar()

function doShopping(transport: car | bus) {
	transport.goTo("Sainsbury's")
}

```

# STATEMENTS

Statements in TypeScript are written in much the same way as most other languages with single line statements terminating in an optional semi-colon and multi-line statements encompassed in curly brackets. TypeScript's optional inclusion of the semi-colon to terminate lines allows the programmer to make the decision to do so based on their own preference and style. It may be worth noting, however, that there are a few fringe cases where a semi-colon is needed. As a rule, the semi-colons should be omitted unless the line begins with one of the following characters:
```
(
[
`
```

In such cases, the semi-colon can be placed at the start of the line to prevent the otherwise resulting error.

While much on the topic of specific types of statements is covered within other relevant sections of this guide, the following serves as an overview of more general concepts.

#### Assignment and Declaration

Assignment of values can be done either during or after declaration of a variable using the '=' operator. This can involve assigning either a value or a function, both of which involve the same syntax as shown below:
```
let y : string = "New String"
y = "Another new string"

let x : number;
x = 13

let z : number = generateNum()
```

In terms of assigning functions to variables, the above examples is just one option for doing so when the function has previously been defined. Other options exist for assignment of new functions as shown below:

```
let assignedFn: () => number = function() : number {

return 13

}

  

let fnVar = function() : number {

return 13

}
```

In the above statements, the important thing to note is the "function()" part of the statement - this cannot be changed to a custom name and stands merely to inform that what follows is a function as opposed to a static value. This option can also be used in conjunction with parameters for the function, including setting their type as shown below:

```
let newFn = function(name: string, age: number) : string {
	return "My name is " + name + " and I am " + age
}
```

It's important to note that despite the functions in the above examples appearing to be assigned to a variable, this process is essentially an alternative way of declaring a function with a particular scope. In practice, this means that calling the function must be done in the regular way, inclusive of the brackets after the function name as below:

```
newFn()
```

#### Jump Statements

The main jump statements used in TypeScript are: return, break, and continue. Usage of these statements is as simple as typing the word with the one caveat being that return statements may be followed by a value to be returned for non-void functions.

```
if (x > 5) {
	break
}

if (x < 2) {
	continue
}

if (x < 5) {
	return true
}
```

As is normally the case common to many other languages, break statements will break out of the current block completely, continue will break out of the current iteration of a loop, and return will stop the running of a function (potentially passing a value back to the call point).

#### Operations

Operations can be performed in TypeScript on various data types. TypeScript has the capability to perform all basic mathematical operations and comparisons in the usual way as shown below:

```
a + b // addition
a - b // subtraction
a * b // multiplication
a / b // division
a % b // modulus
a++ // increment a by 1
a-- // decrement a by 1

a > b // returns true if a is larger
a < b // returns true if a is smaller
a >= b // returns true if a is larger or equal to b
a <= b // returns true if a is smaller or equal to b
a == b // returns true if a and b are equal in value
a != b // returns true if a and b are not equal
```

many of these above operations can be used in combination with assignments to simultaneously perform an operation and assign the resulting value to an existing variable:

```
let a : number = 1
a += 2 // 2
a -= 1 // 1
a *= 2 // 2
a /= 2 // 1
```

In addition, the + operator can be used to concatenate strings as follows:

```
let firstString = "Hello "
let secondString = "World!"

let bigString = firstString + secondString // "Hello World!"

bigString += " How are you?"
```

TypeScript also supports use of logical operations and does so following syntax common to many other languages:

```
true && false // AND operator
true || false // OR operator
!false // NOT operator
```

The NOT operator illustrated above can be used twice in succession to convert values or strings to boolean. This will return true for any non-empty string (even "false") or non-zero value as shown below:

```
!!"false" // returns true
!!-5 // returns true
!!0 // returns false
!!undefined // returns false
```

Although less commonly used, bitwise operations can also be performed in TypeScript:
```
x & y // bitwise AND
x | y // bitwise OR
x ^ y // bitwise XOR
~x // bitwise NOT

x >> 1 // bitwise right shift
x << 1 // bitwise left shift
x >>> 1 // bitwise right shift with trailing zeros
```



# BLOCKS

Like many programming languages (and unlike languages such as Python) TypeScript groups code into blocks by use of curly brackets as opposed to indentation or white space. The main types of blocks are functions, classes, and control blocks; Here we will deal mainly with functions as the other types will be be covered in later sections.

Commonly, blocks are nested within other blocks and therefore one class, for example, can contain multiple functions and control blocks within it. This ability to nest blocks allows TypeScript to incorporate the same level of flexibility and complexity as seen in many other languages therefore making TypeScript a powerful and versatile choice for a wide range of needs.

#### Functions

Functions can be declared in multiple ways within TypeScript, all of which are encased within curly brackets to denote the block of code which belongs within the function. The most straightforward way to declare a function is with the 'function' keyword:

```
function newFn() {
	...
}

function fnWithParams(name: string) {
	...
}
```

In the above examples, the function is declared without stating the return type as TypeScript is able to infer this from the return statement within the function, if included. However, it may be preference to explicitly declare the return type, in which case the following option for declaration may be used:

```
function aFn() : void {
	...
}

function newFn(fn: () => void) {
	...
}
```

This explicitly tells TypeScript that the function should either have an empty return statement or no return statement at all. The 'void' can easily be replaced for any other type such as string or number to denote a function which should return with the stated type.

As can be easily noted from latter example above, the syntax can be quite long, therefore TypeScript allows for declaration of a custom type which can be later used as shorthand:

```
type stringFn = (s: string) => string
function newFn(fn: stringFn) {
	...
}
```

This allows method signatures to be set and reused multiple times to reduce code repetition and increase readability.

As demonstrated in the previous section, functions can be assigned using let, var, and const in much the same way as a variable  thus allowing extra control over the scope of the function:
```
let assignedFn: () => number = function() : number {

return 13

}  

let fnVar = function() : number {

return 13

}

let newFn = function(name: string, age: number) : string {
	return "My name is " + name + " and I am " + age
}
```

Additionally, TypeScript allows functions to be defined with optional parameters by either using a question mark after the parameter name or assigning the parameter to a default value as below:
```
function newFn(age?: number) {
	...
}

function anotherFn(age = 21) {
	...
}
```

Both of these examples enable the function to be called with or without passing arguments, however the latter example is usually preferred as it safeguards against attempting to use an argument which is undefined. In cases where it may be necessary to use optional arguments, TypeScript allows function overloading whereby multiple method signatures are declared followed by one function definition with optional parameters. Below is an example to demonstrate this implementation:

```
function greetUser(name: string) : string
function greetUser(title: string, fName: string, sName: string) : string
function greetUser(nameOrTitle: string, name?: string, sName?: string) : string {
	if (name != undefined && sName != undefined) {
		return "Hello " nameOrTitle + " " + name + " " + sName
	} else {
		return "Hello " + nameOrTitle;
	}
}
```

Such overloading as shown above allows the method to be called with or without parameters much like when using optional parameters. Choosing to implement function overloads, however, allows a parameters usage to change depending on how many parameters are passed. The above example illustrates this by using the first argument as either a name or a title depending on whether or not other arguments are passed when the function is called.

Another flexibility TypeScript allows in terms of declaring functions is the ability to set a correlation between the input type and the return type. This is particularly useful when dealing with arrays which must be declared using the type of the component values. In functions dealing with array operations, it may not be preferable to write separate functions for different types of array, therefore TypeScript allows for use of 'generic functions' whereby the output type is set to the same as the input type as shown below:

```
function sortArray<Type>(inputArray: Type[]) : Type {
	...
	return sortedArray
}
```

In the above example, the use of the word "Type" can be replaced with another term such as Input, Output, Names, Ages, or whatever is most fitting to the usage. Multiple generic types can be used, for example, when passing another function as an argument, the outputs can be set as the same type, while allowing the flexibility to also pass an array of any type:

```
function newFn<firstType, secondType>(inputArray: firstType[], fn: (arg: firstType) => secondType) : secondType[] {
	...
}
```

This therefore allows a great deal of flexibility in writing functions, while maintaining the benefits of TypeScript's strict type checking.
# CONTROL

In addition to the aforementioned jump statements to control the flow of the programme, iteration and conditions can also be used in TypeScript, as is common in many other languages. These both use fairly standard syntax which programmers coming from other languages should find to be easily understood and readable.

### Conditionals

To instantiate conditional if-else logic within TypeScript, the condition to check (in the case of if or else if) is encapsulated in regular brackets, followed by the block wrapped in curly brackets which will execute if the condition is met. Below shows an example of all three of these used together, however it's perfectly possible to use only if, if and else, or if and else if.

```
if (condition) {
	console.log("first condition met")
} else if (otherCondition) {
	console.log("second condition met)
} else {
	console.log("neither condition met")
}
```

In the above example, the conditions passed to if and else if must evaluate to a boolean. This can be done either by passing a boolean value directly, or by evaluating to boolean within the brackets, for example:

```
if (randomNum > 6) {
	console.log("greater than six!")
}
```

It's worth noting that there exists alternative shorthand notation for if and if-else conditionals which may be preferred by some over the more verbose examples above as shown below:

```
condition && runFunction() // shorthand IF

condition ? runIfTrue() : runIfFalse() // shorthand IF-ELSE
```

The latter example above can also be used in variable declaration to declare a variables value based on another condition, for example:

```
let newVar : string = condition ? 'met' : 'not met'
```

In circumstances where more than two or three cases need to be handled, a switch statement can be used as per the following syntax:

```
switch (numericVar) {
	case 1:
		console.log("first case")
		break;
	case 2:
		console.log("second case")
		break;
	case 3:
		console.log("third case")
		break;
	default:
		console.log("default case")
}
```

In the above example, the numeric variable and subsequent numbers for each case can be replaced with any condition to check along with its corresponding values for each case, for example a switch statement using a string could be implemented as follows:

```
switch (stringVar) {
	case "yes":
		console.log("first case")
		break;
	case "maybe":
		console.log("second case")
		break;
	case "probably":
		console.log("third case")
		break;
	default:
		console.log("default case")
}
```

One important thing to bear in mind, as is is common for switch statement usage, is the use of the break statement to prevent fall-through. Omitting the break will lead to all cases below the triggered case also triggered. When used inside a function, the break can, however, be replaced with a return statement if necessary.

### Definite Iteration

The basic structure of a for loop in TypeScript is as follows:

```
for (let i = 0; i < n; i++) {
	console.log(i)
}
```

This example will run the loop for *n* number of times, incrementing i at the end of each loop. The most important point to note with the syntax above is to ensure usage of the semi-colon between each statement of the loop condition. As is usually the case, for loops can easily be nested inside other loops by placing them inside the curly brackets denoting the block.

Alternate syntax exists when writing for loops to iterate over an enumerable object such as an array by using the for...in format as shown below:

```
for (const i in arrayOfThings) {
	console.log(arrayOfThings[i])
}
```

This will take an already defined array and print element. The important points in this syntax besides anything already covered in previous sections is only the use of 'in'. In practice, the 'i' written above can be substituted to any string as per programmers preference for readability, while the 'arrayOfNumbers' must be some already declared enumerable object.

When using for...in, it should be kept in mind that altering the object to be iterated over is highly discouraged as it may result in unexpected behaviour. Adding to the object, for example, will not increase the number of iterations as the additional value will not be included in the loop. Similarly, removing items from the object will not decrease the number of iterations, but instead return an undefined value if attempting to access the deleted index.

An alternative solution to using for...in when preferring to access the values directly rather than the index is to use for...of syntax as shown below:

```
for (const num of arrayOfThings) {
	console.log(num)
}
```

In this circumstance, the constant declared inside the loop condition refers to the value itself rather than the index. Ultimately, however, both for...in and for...of are very similar ways of iterating over an object, therefore much of the decision regarding which to use comes down to preference and style

### Indefinite Iteration

Indefinite iteration in TypeScript is handled by using either while or do...while loops. These options are almost identical, with the only caveat being that do...while loops will always run at least once regardless of whether the while condition is met or not.

Below illustrated the syntax for a basic while loop:

```
while (condition) {
	condole.log("inside loop")
}
```

This will only execute the console log inside the curly brackets if the condition is met. However, it is preferable to ensure inclusion of a return or break statement to prevent the possibility of executing an infinite loop.

When necessary to run a block at least once regardless of the condition, do...while loops may be better suited - the syntax is as follows:

```
do {
	console.log("doing something")
} while (condition)
```

This will run the console log statement and then check the condition. If the condition is true, it will again execute the do block until the condition returns false. Using break statements inside the do block here will work exactly the same as they would for regular while loops meaning the condition will not be checked again.

# DATA STRUCTURES

TypeScript utilises many options for both mutable and immutable data structures - all of which are implemented under the object type discussed in the previous section regarding types. Here, the common data structures of dictionaries, arrays, and tuples will be covered along with some built in objects and how to define custom objects as well as file handling.

### Dictionaries

In order to utilise the typing functionality of TypeScript in a dictionary, index signatures must be used to declare the types of both the key and value:

```
let dictExample : {[key: string] : string} = {
	name: 'Bob'
}
```

In this example, the key (usefully named 'key' here, but can be named anything the developer prefers) as well as the value are both set to the string type. Notably, in both JavaScript and TypeScript numeric keys are converted to a string, therefore regardless of setting the keys type to string as shown above, using a number is still tolerated due to this conversion process.

```
let dictNumbers : {[key: string] : string} = {
1: 'One'
}
```

However, this still presents a problem when accessing the value if wishing to use dot notation. 

```
dictNumbers.1 // Error
dictNumbers[1] // Returns 'One'
dictNumbers ['1'] // Also returns 'One' due to conversion
```

Additionally, due to conversion of numeric keys to strings, it's not possible to setup a dictionary to have both keys '1' and 1 for example. Those wishing to retain a numeric key's number type or use two keys of the same number (one being number type and the other string type) should instead consider using a Map:

```
let mapExample = new Map<number, string>
mapExample.set(5, 'five')
mapExample.get(5) // returns 'five'

let secondMap = new Map<number | string, string>
secondMap.set(1, 'one')
secondMap.set('1', 'first')

secondMap.get(1) // returns 'one'
secondMap.get('1') // returns 'first'
```

As can be seen from the above example, using  Map allows differentiation between numeric and string keys and therefore retains the numeric typing. It's also worth pointing out that since numbers are not converted to strings, it may be necessary to either declare a union type (as shown in the second example above) or ensure the number is input as a string (wrapped in inverted commas) when using a combination of numeric and string keys for a Map.

### Arrays

As seen in the examples featured in the section covering variables, arrays are declared using the primitive type contained within:

```
let myArray : string[],
let newArray : number[] = [1, 2, 3]
```

In certain situations it may be necessary to declare an array with a union type, in which case the below syntax can be used *only* if the values contained within are all of the same type.

```
let unionArray : string[] | number[]
let newUnionArr : string[] | number[] = ['one', 'two', 'three']
```

In this example, the array can contain values which are of either string or number type  and reassigned later to contain values of the other type in the declaration. However, the values must all be of the same type, otherwise the built-in Array object and its respective notation should be used instead.

```
let comboArray : Array<number | string>
let secondArray : Array<number | string> = [1, 'two', 3]
```

In any case, since arrays are a mutable data type they can be amended after declaration with ease, for example:

```
comboArray.push('four') // Appends 'four' to end of array
comboArray.unshift('zero') // Appends 'zero' to start of array

comboArray = comboArray.concat(secondArray) // Appends 'secondArray' to end of 'comboArray'

comboArray.slice(1, 4) // Returns array items starting from index 1 until (but not including) index 4

comboArray.pop() // Removes last element of array
comboArray.shift() // Removes first element of array
```

The above is by no means an exhaustive list as many other operations exist for arrays, but instead is intended to illustrate the flexibility associated with arrays in terms of mutability. It should be noted that many operations which take an argument have a set default value to be used when called without arguments; The 'join' operation, for example, will default to comma separation:

```
let newArray : number[] = [1, 2, 3]
console.log(newArray.join()) // Returns "1, 2, 3"
console.log(newArray.join(' & ')) // Returns "1 & 2 & 3"
```

One additional operation worth covering is the sort function which allows for arrays to be easily sorted:

```
newArray.sort() // Returns sorted array
```

The sorted array returned here will be in alphabetical order, regardless of if the array is typed as containing only numbers, therefore this may not be appropriate to use when requiring numerical sorting as shown below:

```
let numArray : number[] = [1, 2, 12, 3, 5, 21]
numArray.sort() // Returns: [1, 12, 2, 21, 3, 5]
```

When using the sort operation, it is worth bearing in mind that this will mutate the array, therefore consideration should be given as to whether a deep copy should be made. In this case, the array's values can be spread into the copy array as follows:

```
let copyArray : number[] = [...numArray]
```

An alternative to the above which may be suitable to some situations is to make the array read only, however care should still be taken as reassignment is still possible even with read only arrays:

```
let staticArray : readonly number[] = [1, 2, 3]

let anotherArray : readonly number[]
anotherArray = [3, 4, 5]

anotherArray = [5, 6, 7, 8]

```

This will, however, prevent usage of many operations such as sort, push, pop, etc. Therefore, while not entirely immutable, read only arrays do give some degree of protection against mutation.

### Tuples

Often times it may be more appropriate to use a Tuple rather than an Array, particularly when wanting to use an array featuring multiple types of value. While in many other languages Tuples are entirely immutable, in TypeScript this is not the case. Tuples in TypeScript are immutable only in terms of value type, but only for the indexes declared, therefore new values can be pushed to the end of the tuple regardless of type

```
let newTuple : [boolean, string, number]
newTuple = [true, 'this is a tuple', 5]

let anotherTuple : [number, string, number] = [1, 'two', 3]
anotherTuple.push(4)
anotherTuple.push(true)

```

It may therefore make more sense to declare tuples as read only, which can be achieved in the same way as is done for arrays:

```
let fixedTuple : readonly [boolean, string, number]
fixedTuple = [false, 'hello', 13]

let secondTuple : readonly [string, number, boolean] = ['good morning', 4, true]
```

However, as with read only arrays, read only tuples can be reassigned as the 'readonly' only prevents mutating operations from being performed on it.

While there may appear to be little difference between tuples and arrays in TypeScript, tuples ensure that not only are the values input in the correct order (at least as far as typing is concerned), but that the minimum number of values are always given. This latter point means that, while non-'readonly' tuples can take more values than declared, they cannot take less, for example:

```
let myTuple : [number, string, boolean]
myTuple = [2024, 'glasgow', true] // Allowed
myTuple = [100, 'edinburgh'] // Not allowed! Too few values
```

### Enums

When dealing with a fixed list of options, it may be preferable to implement an enum rather than an array or tuple. Enums provide a way of declaring an immutable list of values and therefore provides a degree of safety such that non-listed values cannot be passed.

The syntax for enums is very straightforward:

```
enum language {
	english,
	german,
	french,
	spanish,
	klingon
}
```

Enums will evaluate to a number, therefore attempting to print the enum value will result in the index being output as opposed to the string. By default, the enums are indexed starting at 0, however this can be overridden in the declaration as follows:

```
enum language {
	english = 1,
	german,
	french,
	spanish,
	klingon
}
```

The above example will set the first index to 1 instead of 0 and increment by one for each subsequent value. It is possible, however, to implement non-sequential or even non-numerical indexes which allows the enums to be used in a wider range of circumstances. This is achieved in much the same manner as the above example:

```
enum language {
	enligh = 'EN',
	german = 'DE',
	french = 'FR',
	spansih = 'ES',
	klingon = 'KL'
}
```

This example sets each value to a string which can later be printed or passed to another variable or method call as required. One important thing to bear in mind is that under the hood, enums are still evaluating to a number, therefore while it's possible to set each value to the return value of a function, the return value in this case must be of the number type.

```
enum myEnum {
	potatoes = price(), // Allowed (returning number)
	cabbage = brand() // Now allowed (returning string)
}
```


### Objects

For those wishing to utilise the benefits of object oriented programming while using TypeScript, defining custom objects is a fairly straightforward process. These objects can then be used in place of types when wishing to declare an input as being an instance of a certain object, for example.

Classes in TypeScript must always contain a constructor method, but otherwise are incredibly flexible

```
class Actor {
	name : string
	role : string

	constructor(n : string, r : string) {
		this.name = n
		this.role = r
	}
}

let baftaWinner : Actor = new Actor('David Tennant', 'The Doctor')
```

As expected with objects, custom methods can be added to the class and then called later on any instance of the class

```
class Actor {
	name : string
	role : string

	constructor(n : string, r : string) {
		this.name = n
		this.role = r
	}

	win() {
		console.log("Yass!")
	}
}

let baftaWinner : Actor = new Actor('David Tennant', 'The Doctor')
baftaWinner.win() // Prints 'yass' to console
```

In the case of getters and setters, however, TypeScript has specific keywords for declaring these(aptly named 'get' and 'set', respectively), however it should be noted that access to any properties of the class always required use of 'this', as illustrated below:

```
class Actor {
	name : string
	role : string

	constructor(n : string, r : string) {
		this.name = n
		this.role = r
	}

	get getName() : string {
		return this.name
	}

	set setName(n : string) {
		this.name = n
	}
}
```

The option to use these keywords falls entirely to preference as they can equally be declared using the same syntax as for any other method. The difference therefore lies in how they are called. The following example shows the regular syntax for calling methods:

```
baftaWinner.setName('Brad Pitt')
baftaWinner.getName()
```

Whereas the following syntax must be used for calling getters and setters declared using the get and set keywords:

```
baftaWinner.setName = 'Brad Pitt'
baftaWinner.getName
```

When defining a class' methods, consideration should be given to the syntax regarding overloading as this follows a slightly different pattern than seen in some other languages such as Java. In TypeScript, it is not possible to declare two methods with the same name therefore overloading must be achieved via optional arguments and provision of logic within the method, for example:

```
win(award? : string) {

award === undefined ? console.log("Yass") : console.log("Thanks for the " + award)

}
```

Subclasses can also be declared using the 'extends' keyword, however the superclass must be called within the constructor prior to using 'this', for example:

```
class Actor extends Person {
	role : string
	
	constructor(n : string, a : number, r : string) {
		super()
		this.name = n
		this.age = a
		this.role = r
	}
}
```

### File Handling

While file handling text documents is possible using TypeScript, it does rely upon Node modules, therefore should any difficulties be encountered when following this section, it's worth double checking that node is configured correctly.

#### Reading

When reading text files, there are two slightly different options with regards to syntax. Either option can be chosen and is largely a matter of preference:

```
import * as file from 'fs'

let stuff = file.readFileSync('stuff.txt', 'utf8')

console.log("stuff)  
  

const fileTwo = require('fs')

let things = fileTwo.readFileSync('things.txt', 'utf8')

console.log(things)
```

Both of these approaches shown above will result in the entire contents of the file being printed to the console. This output can be manipulated, for example, by using the split operator to convert the file from one (potentially very long) string into an array of strings as shown below:

```
things.split(', ')
```

This will split the contents of the file into multiple strings based on comma separation, however the argument can be changed to suit needs. Commonly, files containing a list of words or phrases would be split up by new line as shown below:

```
let stuffList = stuff.split('\n')
```

It may be preferable in some cases to read only one line at a time, in which case a more complicated approach is needed. In this instance, it's required to read the file asynchronously, therefore 'await' must be used, however often Node will throw an error when attempting to use await at the top level. For the sake of ensuring each code example in this guide functions as expected regardless of context, the asynchronous operations have been wrapped in an asynchronous function so as to avoid any error regarding top-level await calls:

```
const file = require('fs/promises')

async function reader() {
	const stuff = await file.open('data.txt')

	for await(const line of stuff.readLines()) {
		console.log(line)
	}
}
  

reader()
```

The above example will print each line to the console individually, however it can be manipulated depending on need to perform individual operations on each line.

These examples assume the file being read is a text file, yet it is far more common to see JSON used within a TypeScript project as it provides a set format compatible with both JavaScript and TypeScript which can then be imported and used directly. Reading from JSON files is therefore far more straightforward:

```
import data from 'data.json'
```

In this example, the contents of the JSON file is stored within the 'data' variable for later use. When importing from a JSON file, the contents are automatically parsed and stored appropriately as opposed to storing as a string, therefore entire objects and configurations can be loaded in directly without having to split and manipulate text documents manually.

Alternatively, JSON data can be read asynchronously by implementing Node's promises module. As before, this may need to be encased in an asynchronous function as below:

```
import * as file from 'fs/promises';  

async function loadJson() {
	const loadedFile = await file.readFile('nominees.json', 'utf-8')
	const fileJson = JSON.parse(loadedFile)
}  

loadJson()
```

It should be noted here that the inclusion of the encoding type is required, unlike in previous examples where it can be safely omitted. Otherwise, the asynchronous version follows a similar pattern to its synchronous counterpart and should therefore be fairly straightforward to implement.
#### Writing

Writing to text files follows an incredibly similar syntax to that used for reading, differing mainly in that the text to be written must be passed as an argument to the writing function:

```
import * as file from 'fs'

let addText : string = 'Good Morning!'
file.writeFileSync('stuff.txt', addText)

```

The above function will overwrite the entire text file with the string passed into the writing function's arguments. In cases where it's more appropriate to append rather than overwrite, the final line in the above example should be replaced with the following:

```
file.appendFileSync('stuff.txt', addText)
```

Of course, commonly it is preferred to store data in the JSON format, in which case the object should be first converted to JSON before writing to the file:

```
let baftaNominee : Person = {
	name: 'David Tennant'
	role: 'The Doctor'
}

let nomineeJson = JSON.stringify(baftaNominee)
file.writeFileSync('nominees.json', nomineeJson)
```

As before, this will overwrite the entire file but replacing the write function with the appending counterpart will prevent data loss:

```
file.appendFileSync('nominees.json', nomineeJson)
```

As seen before in previous examples, Node's promises module implements the ability to perform file operations asynchronously. It may therefore be preferable to incorporate this when writing to files, particularly when the data is quite large - lest the developer risk holding up the execution of the rest of the programme while waiting on the writing operation. As this again requires use of 'await', it may be necessary to wrap it in an asynchronous function call to prevent throwing an error at compilation:

```
import * as file from 'fs/promises';  

async function writeJson() {

	const newNominee: Person = {	
		name: 'David Tennant',	
		role: 'The Doctor',	
	};
	
	const nomineeJson = JSON.stringify(newNominee);	
	await file.writeFile('nominees.json', nomineeJson);

}  

writeJson()
```


# ERROR HANDLING

Errors in TypeScript are implemented using the built-in error object which stores the name and error message associated with various types of error. While numerous errors are already accounted for within TypeScript itself, the option is available to developers to create their own error classes in cases where this may be more preferable or informative

### Catching Errors

Errors in TypeScript can be caught by using a try-catch block. The program will first run the code contained within the try block and, should an error present, run the contents of the catch block.

```
try {
	...
} catch (error) {
	console.log(error.message)
}
```

While in many cases it may suffice to simply print the message property associated with the error, it's good practice to narrow down the error within the catch block in order to provide context for debugging when the error is thrown. Narrowing down the error makes use of TypeScript's error object by checking if the error is an instance of a particular error class, for example:
```
try {
	...
} catch (error) {
	if (error instanceof TypeError) {
		...
	} else if (error instanceof SyntaxError) {
		...
	}
}
```

This allows the error to be handled differently depending on which error is thrown, and therefore allow the programme to reroute accordingly. For improved debugging, however, it may be worth also printing the stack trace, however this should be done after checking the stack property exists, otherwise this itself will throw an error:

```
catch (error) {
	if ('stack' in error) {
		console.log(error.stack)
	}
}
```

Additionally, the try-catch block can be extended to include a 'finally' clause which will run regardless of whether an error is thrown:
```
try {
	...
} catch (error) {
	...
} finally {
	...
}
```

### Throwing Errors

While it may in many cases be enough to simply implement a try-catch block, some cases may involve an error which won't be caught in the catch block or require the error to be passed up the stack. In either of these circumstances, the error can be thrown using the 'throw' keyword as follows:

```
throw (error)
throw new Error("Error 418: I'm a teapot!")
```

The second line of the above example also allows errors to be thrown outside of a try-catch block, which may be preferred in more simple cases or necessary in circumstances where the error would not be caught in the catch block.

### Custom Errors

Custom errors can be defined by implementing a class which extends the Error class as shown:

```
class teapotError extends Error {
	code : number

	constructor() {
	super()	
	this.name = 'TeapotError'	
	this.code = 418	
	this.message = "I'm a Teapot!"	
	}
}
```

The custom error can then be used in the same manner as built in errors by creating an instance as follows:

```
let error : Error = new teapotError()
console.log(error.message)
throw error
```

This therefore allows for a high degree of flexibility with regard to error handling as custom errors can implement custom methods, for example, one may wish to include a default method for handling a particular error.

# CONCLUSION

As hopefully has been made clear in this guide, learning the syntax of TypeScript should prove relatively painless, particularly to those already familiar with another language. Much of the syntax used follows already established precedents in the programming world and therefore provides an excellent choice for those wishing to use a language which is both highly readable and highly accessible. Additionally, as much of the syntax is based upon or identical to pure JavaScript, there are numerous resources online for learning or reference regardless of experience or skill level.

Such basis on JavaScript allows developers wishing to incorporate the benefits of a strongly typed language into an existing JavaScript codebase seamlessly. Any individual wishing to migrate is therefore free to do so without a lengthy refactoring process or time spent retraining.

All in all, this makes TypeScript a strong contender for those looking for a robust and flexible language to use, particularly for those involved in web based development. Ideally, having completed their way through this guide, any developer wishing to adopt the TypeScript language into their own development work will find themselves in a good position to do so.

