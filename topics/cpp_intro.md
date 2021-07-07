
# C++ Introduction

Tutorial: https://www.tutorialspoint.com/cplusplus/index.htm

Advantages:
* Close to hardware, so better performance, control, and versatility.
* Good to learn about OOP
* Used my many
* Teaches you other important concepts



Applications of C++
* Application software development
* programming language development
* Scientific computing
* Games
* Embedded Systems

C++ is a statically typed, compiled, general-purpose, case-sensitive, free-form programming language that supports procedural, object-oriented, and generic programming.

A programming language is said to use static typing when type checking is performed during compile-time as opposed to run-time


C++ fully supports object-oriented programming, including the four pillars of object-oriented development −

    Encapsulation
    Data hiding
    Inheritance
    Polymorphism

ANSI stnadard is what compilers follow so they all act the same

.cpp (default), .cp, and .c are all normal file extensions




    Object − Objects have states and behaviors. Example: A dog has states - color, name, breed as well as behaviors - wagging, barking, eating. An object is an instance of a class.

    Class − A class can be defined as a template/blueprint that describes the behaviors/states that object of its type support.

    Methods − A method is basically a behavior. A class can contain many methods. It is in methods where the logics are written, data is manipulated and all the actions are executed.

    Instance Variables − Each object has its unique set of instance variables. An object's state is created by the values assigned to these instance variables.





    # Hello World

    main.cpp
    ```c++
    #include <iostream>
    using namespace std;

    // main() is where program execution begins.
    int main() {
       cout << "Hello World"; // prints Hello World
       return 0;
    }
    ```





        The C++ language defines several headers, which contain information that is either necessary or useful to your program. For this program, the header <iostream> is needed.

        The line using namespace std; tells the compiler to use the std namespace. Namespaces are a relatively recent addition to C++.

        The next line '// main() is where program execution begins.' is a single-line comment available in C++. Single-line comments begin with // and stop at the end of the line.

        The line int main() is the main function where program execution begins.

        The next line cout << "Hello World"; causes the message "Hello World" to be displayed on the screen.

        The next line return 0; terminates main( )function and causes it to return the value 0 to the calling process.




        Type 'g++ hello.cpp' and press enter to compile your code. If there are no errors in your code the command prompt will take you to the next line and would generate a.out executable file.

        g++ -o TARGETFILE SOURCEFILE
        g++ -o hello.exe test.cpp

        Now, type './a.out' to run your program.


semi colon ; is statement terminator

block is code enclosed by brackets

newlines dont actually matter, semi colon does


A C++ identifier is a name used to identify a variable, function, class, module, or any other user-defined item. An identifier starts with a letter A to Z or a to z or an underscore (_) followed by zero or more letters, underscores, and digits (0 to 9).

C++ does not allow punctuation characters such as @, $, and % within identifiers. C++ is a case-sensitive programming language. Thus, Manpower and manpower are two different identifiers in C++.



reserved words

asm 	else 	new 	this
auto 	enum 	operator 	throw
bool 	explicit 	private 	true
break 	export 	protected 	try
case 	extern 	public 	typedef
catch 	false 	register 	typeid
char 	float 	reinterpret_cast 	typename
class 	for 	return 	union
const 	friend 	short 	unsigned
const_cast 	goto 	signed 	using
continue 	if 	sizeof 	virtual
default 	inline 	static 	void
delete 	int 	static_cast 	volatile
do 	long 	struct 	wchar_t
double 	mutable 	switch 	while
dynamic_cast 	namespace 	template 	 


A few characters have an alternative representation, called a trigraph sequence. A trigraph is a three-character sequence that represents a single character and the sequence always starts with two question marks.


Trigraph 	Replacement
??= 	#
??/ 	\
??' 	^
??( 	[
??) 	]
??! 	|
??< 	{
??> 	}
??- 	~


```
/* This is a comment */

/* C++ comments can also
   * span multiple lines
*/
```

# Data types
Boolean 	bool
Character 	char
Integer 	int
Floating point 	float
Double floating point 	double
Valueless 	void
Wide character 	wchar_t



typedef type newname;

enum enum-name { list of names } var-list;

enum color { red, green, blue } c;
c = blue;

enum color { red, green = 5, blue };

Here, blue will have a value of 6 because each name will be one greater than the one that precedes it.



int    i, j, k;
char   c, ch;
float  f, salary;
double d;

The line int i, j, k; both declares and defines the variables i, j and k; which instructs the compiler to create variables named i, j and k of type int.

Variables can be initialized (assigned an initial value) in their declaration. The initializer consists of an equal sign followed by a constant expression as follows −
```
int var = 6;
```

use extern keyword to declare a variable at any place


Try the following example where a variable has been declared at the top, but it has been defined inside the main function −
Live Demo

// function declaration
int func();
int main() {
   // function call
   int i = func();
}

// function definition
int func() {
   return 0;
}




    lvalue − Expressions that refer to a memory location is called "lvalue" expression. An lvalue may appear as either the left-hand or right-hand side of an assignment.

    rvalue − The term rvalue refers to a data value that is stored at some address in memory. An rvalue is an expression that cannot have a value assigned to it which means an rvalue may appear on the right- but not left-hand side of an assignment.
