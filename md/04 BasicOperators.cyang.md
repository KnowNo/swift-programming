基本运算符
---------------

*运算符*是一种可以检查、修改或结合数值的特殊符号或短语。例如，加法运算符可以将两个数字相加（ `let i = 1 + 2` ）。
更复杂的例子还包括逻辑与运算符 `&&`（ `if enteredDoorCode && passedRetinaScan` ）以及可以简化增量操作的运算符 `++i`。

Swift 支持大多数标准 C 运算符，并增强了避免常见编码错误的能力。赋值运算符（ `=` ）没有返回值，这可以防止误用（ `=` ）和等于符号（ `==` ）。
算数运算符（ `+` ，`*` ）会检测且禁止数值溢出，避免因处理数据不当而导致的意外结果。你可以使用 Swift 的溢出运算符来自定义溢出行为，详情请参考 [溢出运算符](AdvancedOperators.xhtml#TP40014097-CH27-XID_37)。

Swift 并不像 C 那样允许你对浮点数做余数运算。它提供了两种 C 不曾拥有的范围运算符（ `a..b` ），这样的运算符可以非常方便地表示数据范围。

本章将会详细解读 Swift 的常用运算符。[高级运算符](AdvancedOperators.xhtml) 则涵盖了 Swift 的高级运算符，它会告诉你如何定义你自己的运算符，并为你自己的类型实现标准运算符。
‌

### 专有名词

运算符包括一元、二元和三元运算符：
    
- 	*一元*运算符只能作用于单一操作数（例如 -a）。一元*前缀*运算符位于操作数头部（例如 !b），而一元*后缀*运算符位于操作数尾部（例如 i++）。

- 	*二元*运算符作用于两个操作数（例如 2 + 3），并且位于两个操作数中间。

- 	*三元*运算符作用于三个操作数。和 C 类似，Swift只有一个三元运算符，也就是三元条件运算符（a ? b : c）。

The values that operators affect are *operands*. In the expression
1 + 2 symbol is a binary operator
and its two operands are the values 1 and 2.

运算符所影响的数值叫做*操作数*。在表达式 `1 + 2` 中，`+` 就是一个二元运算符，他的两个操作数就是数值 `1` 和 `2` 。
‌

### Assignment Operator 

The *assignment operator* (a = b) initializes or updates
the value of a:

    let
    var
    a
    // a is now equal to 10

If the right side of the assignment is a tuple with multiple values, its
elements can be decomposed into multiple constants or variables at once:

    let)
    // x is equal to 1, and y is equal to 2

Unlike the assignment operator in C and Objective-C, the assignment
operator in Swift does not itself return a value. The following
statement is not valid:

    if {
        // this is not valid, because x = y does not return a value
    }

This feature prevents the assignment operator (=) from
being used by accident when the equal to operator (==) is
actually intended. By making if x = y invalid, Swift
helps you to avoid these kinds of errors in your code.

‌

### Arithmetic Operators 

Swift supports the four standard *arithmetic operators* for all number
types:

-   Addition (+)

-   Subtraction (-)

-   Multiplication (*)

-   Division (/)

    1
    5
    2
    10.0

Unlike the arithmetic operators in C and Objective-C, the Swift
arithmetic operators do not allow values to overflow by default. You can
opt in to value overflow behavior by using Swift’s overflow operators
(such as a &+ b). See [Overflow
Operators](AdvancedOperators.xhtml#TP40014097-CH27-XID_37).

The addition operator is also supported for String
concatenation:

    "hello, "
    // equals "hello, world"

Two Character
value and one String value, can be added together to make
a new String value:

    let
    let
    let
    // dogCow is equal to "🐶🐮"

See also [Concatenating Strings and
Characters](StringsAndCharacters.xhtml#TP40014097-CH7-XID_379).

‌

### Remainder Operator 

The *remainder operator* (a % b) works out how many
multiples of b and
returns the value that is left over (known as the *remainder*).

Note

The remainder operator (%) is also known as a *modulo
operator* in other languages. However, its behavior in Swift for
negative numbers means that it is, strictly speaking, a remainder rather
than a modulo operation.

Here’s how the remainder operator works. To calculate
9 % 4s will
fit inside 9:

![image: ../Art/remainderInteger\_2x.png](Art/remainderInteger_2x.png)

You can fit two 4, and the
remainder is 1 (shown in orange).

In Swift, this would be written as:

    9

To determine the answer for a % b
operator calculates the following equation and returns
remainder as its output:

a) +
remainder

where some multiplier is the largest number of multiples
of b.

Inserting 9 into this equation
yields:

9) +
1

The same method is applied when calculating the remainder for a negative
value of a:

    -9

Inserting -9 into the equation
yields:

-9) +
-1

giving a remainder value of -1.

The sign of b is ignored for negative values of
b and
a % -b always give the same answer.

‌

### Floating-Point Remainder Calculations 

Unlike the remainder operator in C and Objective-C, Swift’s remainder
operator can also operate on floating-point numbers:

    8

In this example, 8 equals
3, so the
remainder operator returns a Double value of
0.5.

![image: ../Art/remainderFloat\_2x.png](Art/remainderFloat_2x.png)

‌

### Increment and Decrement Operators 

Like C, Swift provides an *increment operator* (++) and a
*decrement operator* (--) as a shortcut to increase or
decrease the value of a numeric variable by 1. You can
use these operators with variables of any integer or floating-point
type.

    var
    ++i

Each time you call ++i is
increased by 1 is
shorthand for saying i = i + 1. Likewise,
--i can be used as shorthand for
i = i - 1.

The ++ symbols can be used as
prefix operators or as postfix operators. ++i and
i++ are both valid ways to increase the value of
i and
i-- are both valid ways to decrease the value of
i.

Note that these operators modify i and also return a
value. If you only want to increment or decrement the value stored in
i, you can ignore the returned value. However, if you
*do* use the returned value, it will be different based on whether you
used the prefix or postfix version of the operator, according to the
following rules:

-   If the operator is written *before* the variable, it increments the
    variable *before* returning its value.

-   If the operator is written *after* the variable, it increments the
    variable *after* returning its value.

For example:

    var
    let
    // a and b are now both equal to 1
    let++
    // a is now equal to 2, but c has been set to the pre-increment value of 1

In the example above, let b = ++a increments
a *before* returning its value. This is why both
a are equal to to the new value of
1.

However, let c = a++ *after*
returning its value. This means that c gets the old value
of 1 is then updated to equal
2.

Unless you need the specific behavior of i++, it is
recommended that you use ++i in
all cases, because they have the typical expected behavior of modifying
i and returning the result.

‌

### Unary Minus Operator 

The sign of a numeric value can be toggled using a prefixed
-, known as the *unary minus operator*:

    let
    let
    // minusThree equals -3
    let
    // plusThree equals 3, or "minus minus three"

The unary minus operator (-) is prepended directly before
the value it operates on, without any white space.

‌

### Unary Plus Operator 

The *unary plus operator* (+) simply returns the value it
operates on, without any change:

    let
    let
    // alsoMinusSix equals -6

Although the unary plus operator doesn’t actually do anything, you can
use it to provide symmetry in your code for positive numbers when also
using the unary minus operator for negative numbers.

‌

### Compound Assignment Operators 

Like C, Swift provides *compound assignment operators* that combine
assignment (=) with another operation. One example is the
*addition assignment operator* (+=):

    var
    a
    // a is now equal to 3

The expression a += 2 is shorthand for
a = a + 2. Effectively, the addition and the assignment
are combined into one operator that performs both tasks at the same
time.

Note

The compound assignment operators do not return a value. You cannot
write let b = a += 2, for example. This behavior is
different from the increment and decrement operators mentioned above.

A complete list of compound assignment operators can be found in
[Expressions](Expressions.xhtml).

‌

### Comparison Operators 

Swift supports all standard C *comparison operators*:

-   Equal to (a == b)

-   Not equal to (a != b)

-   Greater than (a > b)

-   Less than (a < b)

-   Greater than or equal to (a >= b)

-   Less than or equal to (a <= b)

Note

Swift also provides two *identity operators* (=== and
!==), which you use to test whether two object references
both refer to the same object instance. For more information, see
[Classes and Structures](ClassesAndStructures.xhtml).

Each of the comparison operators returns a Bool value to
indicate whether or not the statement is true:

    1
    2
    // true, because 2 is not equal to 1
    2
    // true, because 2 is greater than 1
    1
    1
    // true, because 1 is greater than or equal to 1
    2
    // false, because 2 is not less than or equal to 1

Comparison operators are often used in conditional statements, such as
the if statement:

    let
    if {
        println)
    } else {
        println)
    }
    // prints "hello, world", because name is indeed equal to "world"

For more on the if statement, see [Control
Flow](ControlFlow.xhtml).

‌

### Ternary Conditional Operator 

The *ternary conditional operator* is a special operator with three
parts, which takes the form question ? answer1 : answer2.
It is a shortcut for evaluating one of two expressions based on whether
question is
true, it evaluates answer1 and returns its value;
otherwise, it evaluates answer2 and returns its value.

The ternary conditional operator is shorthand for the code below:

    if {
        answer1
    } else {
        answer2
    }

Here’s an example, which calculates the pixel height for a table row.
The row height should be 50 pixels taller than the content height if the
row has a header, and 20 pixels taller if the row doesn’t have a header:

    let
    let
    let +
    (hasHeader)
    // rowHeight is equal to 90

The preceding example is shorthand for the code below:

    let
    let
    var
    if {
        rowHeight
    } else {
        rowHeight
    }
    // rowHeight is equal to 90

The first example’s use of the ternary conditional operator means that
rowHeight can be set to the correct value on a single
line of code. This is more concise than the second example, and removes
the need for rowHeight to be a variable, because its
value does not need to be modified within an if
statement.

The ternary conditional operator provides an efficient shorthand for
deciding which of two expressions to consider. Use the ternary
conditional operator with care, however. Its conciseness can lead to
hard-to-read code if overused. Avoid combining multiple instances of the
ternary conditional operator into one compound statement.

‌

### Range Operators 

Swift includes two *range operators*, which are shortcuts for expressing
a range of values.

‌

### Closed Range Operator 

The *closed range operator* (a...b) defines a range that
runs from a, and includes the values
a.

The closed range operator is useful when iterating over a range in which
you want all of the values to be used, such as with a
for loop:

    for {
        println
    \* 5)
    }
    // 1 times 5 is 5
    // 2 times 5 is 10
    // 3 times 5 is 15
    // 4 times 5 is 20
    // 5 times 5 is 25

For more on for loops, see [Control
Flow](ControlFlow.xhtml).

‌

### Half-Closed Range Operator 

The *half-closed range operator* (a..b) defines a range
that runs from a, but does not
include b. It is said to be *half-closed* because it
contains its first value, but not its final value.

Half-closed ranges are particularly useful when you work with zero-based
lists such as arrays, where it is useful to count up to (but not
including) the length of the list:

    let,
    "Brian"]
    let
    for {
        println +
    1)
    }
    // Person 1 is called Anna
    // Person 2 is called Alex
    // Person 3 is called Brian
    // Person 4 is called Jack

Note that the array contains four items, but 0..count
only counts as far as 3 (the index of the last item in
the array), because it is a half-closed range. For more on arrays, see
[Arrays](CollectionTypes.xhtml#TP40014097-CH8-XID_135).

‌

### Logical Operators 

*Logical operators* modify or combine the Boolean logic values
true. Swift supports the three
standard logical operators found in C-based languages:

-   Logical NOT (!a)

-   Logical AND (a && b)

-   Logical OR (a || b)

‌

### Logical NOT Operator 

The *logical NOT operator* (!a) inverts a Boolean value
so that true, and
false.

The logical NOT operator is a prefix operator, and appears immediately
before the value it operates on, without any white space. It can be read
as “not a”, as seen in the following example:

    let
    if {
        println)
    }
    // prints "ACCESS DENIED"

The phrase if !allowedEntry can be read as “if not
allowed entry.” The subsequent line is only executed if “not allowed
entry” is true; that is, if allowedEntry is
false.

As in this example, careful choice of Boolean constant and variable
names can help to keep code readable and concise, while avoiding double
negatives or confusing logic statements.

‌

### Logical AND Operator 

The *logical AND operator* (a && b) creates logical
expressions where both values must be true for the
overall expression to also be true.

If either value is false, the overall expression will
also be false. In fact, if the *first* value is
false, the second value won’t even be evaluated, because
it can’t possibly make the overall expression equate to
true. This is known as *short-circuit evaluation*.

This example considers two Bool values and only allows
access if both values are true:

    let
    let
    if
    {
        println)
    } else {
        println)
    }
    // prints "ACCESS DENIED"

‌

### Logical OR Operator 

The *logical OR operator* (a || b) is an infix operator
made from two adjacent pipe characters. You use it to create logical
expressions in which only *one* of the two values has to be
true for the overall expression to be
true.

Like the Logical AND operator above, the Logical OR operator uses
short-circuit evaluation to consider its expressions. If the left side
of a Logical OR expression is true, the right side is not
evaluated, because it cannot change the outcome of the overall
expression.

In the example below, the first Bool value
(hasDoorKey, but the second
value (knowsOverridePassword.
Because one value is true, the overall expression also
evaluates to true, and access is allowed:

    let
    let
    if
    {
        println)
    } else {
        println)
    }
    // prints "Welcome!"

‌

### Combining Logical Operators 

You can combine multiple logical operators to create longer compound
expressions:

    if
    || hasDoorKey {
        println)
    } else {
        println)
    }
    // prints "Welcome!"

This example uses multiple &&
operators to create a longer compound expression. However, the
&& operators still operate on only
two values, so this is actually three smaller expressions chained
together. It can be read as:

If we’ve entered the correct door code and passed the retina scan; or if
we have a valid door key; or if we know the emergency override password,
then allow access.

Based on the values of enteredDoorCode,
passedRetinaScan, the
first two mini-expressions are false. However, the
emergency override password is known, so the overall compound expression
still evaluates to true.

‌

### Explicit Parentheses 

It is sometimes useful to include parentheses when they are not strictly
needed, to make the intention of a complex expression easier to read. In
the door access example above, it is useful to add parentheses around
the first part of the compound expression to make its intent explicit:

    if &&
    passedRetinaScan ||
    knowsOverridePassword {
        println)
    } else {
        println)
    }
    // prints "Welcome!"

The parentheses make it clear that the first two values are considered
as part of a separate possible state in the overall logic. The output of
the compound expression doesn’t change, but the overall intention is
clearer to the reader. Readability is always preferred over brevity; use
parentheses where they help to make your intentions clear.
