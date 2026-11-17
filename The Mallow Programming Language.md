# Getting Started

---

## Introduction - What is Mallow and what is it capable of?

Mallow is a general purpose programming language strongly focused on server side development. Mallow is inspired by PHP, Rust, C and JavaScript. It was originally ment to be a refined, better syntax version of PHP and named MHP (*Marshmallow Hypertext Preprocessor*) "Marshmallow" because it's a sweeter PHP. But over development, Mallow has changed orientation to logical design, modern features and efficiency. Unlike PHP, Mallow is a compiled language developed via LLVM just like languages such as: Rust, C and Go. It uses same embedding ability as PHP. 

For example:
```Mallow
<!DOCTYPE html>  
<html>  
	<head>  
		<title>Example</title>  
	</head>  
	<body>  
  
	<#  
		echo "this is an Mallow code";  
	#>  
  
	</body>  
</html>
```

The code above is specialised mostly for the web development. A special Mallow server called *Campfire* reads the code, executes Mallow code and sends returns to the pipeline. Pipeline is the web output queue. Output gets served as an HTML file. In the code above Campfire responses with an HTML file as adding "this is a Mallow code" text between body tags. But Mallow does not require that. You can code with Campfire as a web page but you can also code plain and run it in the console. Or even it can output a lot of file type such as: Images, PDF, CSS, JS, XML, CSV, JSON, GraphQL, MON (Marshmallow Object Notation), MDB (Marshmallow Data Base), SUIT (Systemwide User Interface Tools \[Mallow gui library\]) and so:

executable plain codes:
```Mallow
print "hello terminal!";
```

CSS output:
```Mallow
`output = CSS`
.{
	background-color: black;
	display: flex;
	justify-content: center;
	align-items: <#= "center;" #>
}
```

We are going to talk about Mallow web development at the *"Mallow on the net"* document.

---

Mallow is a mixed AOT(ahead of time) and JIT(just in time) programming language. Lines end up with comma(,) are compiled as JIT. The parser parse the line and if the line ends with comma, it does not executes it and wait for the next line. This goes that way untill a line ends with semicolon or no more line left then all the code gets executed (JIT). Other way each line ends with semicolon gets executed immediately(AOT). 
For example:

JavaScript:
```js
function resolveAfter2Seconds() {
    setTimeout(() => {
      console.log("resolved");
    }, 2000);
}

async function asyncCall() {
  console.log("calling");
  const result = await resolveAfter2Seconds();
  console.log(result);
}
asyncCall();
```

PHP:
```php
function resolveAfter2Seconds() {
    echo "resolved" . PHP_EOL;
    sleep(2); // Blocks for 2 seconds
}

function asyncCall() {
    echo "calling" . PHP_EOL;
    resolveAfter2Seconds();
    echo "result (this runs after 2 sec)" . PHP_EOL;
}

asyncCall();
```

Mallow:
```Mallow
fn resolveAfter2Seconds {  
  sleep(2),
  print "resolved"
};  
  
async fn asyncCall {  
  print "calling";  
  resolveAfter2Seconds,
};

default impure fn main {
	asyncCall;
}
```

---

Mallow can be used in servers, communication systems, databases, ai, ar/vr, app development, graphical process, embedded systems, quantum computing and so on...

***
## Setup and Installation

Now let's setup our Mallow environment and learn and test some basic Mallow code to understand the language and warm ourselves before the fight! But first we need to install it.

### Plain install/Terminal

You can just install plain like how you would for a lot of other languages. Just create file and compile. You can also use the package manager *Ember*  further!
#### Installing the Mallow Compiler

Mallow is compiled using LLVM, so you’ll first install the language compiler on your system.

**Linux (Debian / Ubuntu):**

```bash
sudo apt update
sudo apt install Mallow_lang
```

**Arch Linux:**

```bash
sudo pacman -S Mallow_lang
```

**macOS (Homebrew):**

```bash
brew install Mallow_lang
```

---

#### Installing Ember (Package Manager)

Ember is the official package manager for Mallow, responsible for handling libraries, dependencies, and project setup.

**Linux (Debian / Ubuntu):**

```bash
sudo apt install ember
```

**Arch Linux:**

```bash
sudo pacman -S ember
```

**macOS (Homebrew):**

```bash
brew install ember
```

---

#### Installing Both Together

Some package managers or distributions will offer a combined install for convenience.

**Linux (Debian / Ubuntu):**

```bash
sudo apt install Mallow_lang ember
```

**Arch Linux:**

```bash
sudo pacman -S Mallow_lang ember
```

**macOS (Homebrew):**

```bash
brew install Mallow_lang ember
```

Alternatively, for systems with `curl`:

```bash
curl -s https://get.Mallow.dev | bash    # Installs Mallow_lang
curl -s https://get.ember.dev | bash  # Installs Ember
```

*** 
### Server Side (Campfire)

#### What is Campfire?

**Campfire** is the official server runtime for Mallow's server side framework MHP (Marshmallow Hypertext Preprocessor).  
It is designed to handle **compiled or embedded Mallow code** and deliver its output directly to the web, similar to how PHP works — but with a modern, efficient, and secure architecture.

One of Campfire's standout features is that it’s written entirely in **Mallow** itself, demonstrating the language’s flexibility and power to build real-world, high-performance server software.

Campfire can:

- Parse and run embedded `<# Mallow CODE #>` blocks inside HTML files.
- Handle routing and HTTP responses.
- Serve as a general-purpose app server for Mallow-based projects.
- Integrate directly with **Ember** for seamless project deployment.

Mallow web framework is called MHP (Marshmallow hypertext preprocessor) and file extension is *.mhp*

---

#### Installing Campfire Server

##### 1. Install Mallow Compiler

Before you install Campfire, make sure you’ve installed the Mallow compiler:

```bash
# For Linux / MacOS
sudo apt install Mallow_lang

# For Windows
Download installer from: https://Mallow-lang.org/download
```

---

##### 2. Install Campfire Server

Once Mallow is ready, you can install Campfire.

```bash
ember add campfire
```

Or download it directly from the Campfire release page:

```bash
git clone https://github.com/Mallow-lang/campfire.git
cd campfire
ember build
```

---

##### 3. Running Campfire

Navigate to your project folder and run:

```bash
campfire --serve path/to/your/project
```

Campfire will start parsing your `.html` or `.mhp` files and serve them on `localhost:8080` by default.

---

##### 4. Example Project

Directory structure for a Campfire web project:

```
my_website/
├── ember.mon
├── src/
│   ├── index.mhp
│   └── components/
│       └── header.mhp
└── build/
```

In your `index.mhp`:

```Mallow
<!DOCTYPE html>
<html>
  <head>
    <title>Campfire Example</title>
  </head>
  <body>
    <# echo "Welcome to Campfire!"; #>
    <!-- or -->
    
    <#= "Welcome to Campfire!" #>
  </body>
</html>
```

Campfire will parse the embedded Mallow code and send the rendered HTML to the client.

> **Note:** Campfire does not requires main function because it use *sugarPack* framework by the default for flexibility.

---

##### 5. Configuration

You can adjust server settings in `ember.mon`:

```mon
server = {
    host = "0.0.0.0";
    port = 8080;
    public = "./src";
}
```

---

And that's it!  
Campfire is now ready to serve your Mallow-powered websites and APIs!

Now you can make file as myfiel.Mallow and print your first Mallow hello world program.

plain:
```Mallow
print "Hello, World";
```

Web:
```Mallow
<html>
	<head>
		<title>Mallow!</title>
	</head>
	<body>
		<# echo "Hello, World!" #>
	</body>
</html>
```

Or shortly we can use this in web:
```Mallow
<html>
	<head>
		<title>Mallow!</title>
	</head>
	<body>
		<#= "Hello, World!" #>
	</body>
</html>
```

Also you may want to learn about situation and information about your setups. So you can use `<# mallowStat; #>` to see all the details.

***
## Anatomy of Mallow

### Containers :

Everything in the screen as codes are containers in Mallow. You see, computers actually work by binary codes. Those binary codes are extremely hard for humans to read and manage. Also some specific combinations of binary codes and specific operations in the CPU are always things we repeat. So we developed a solution for that. We stored those repeating binary combinations and named them. We stored addresses of those codes in names so instead of rewriting, we can just write the name and CPU will track by address and process that code line. This is the basis of programming languages. We created low level programming languages such as Assembly by that and realised that even some Assembly combinations repeat and also so detailed that it would take so much time to build bigger projects so we named the repeated processes and made the middle level programming languages such as C and Rust. And repeat and we got high level languages such as PHP, Python and JavaScript. Mallow is something between mid level and high level. That means codes in high level programming languages actually represent more byte codes we stored. So less detailed but better to build big projects. Imagine trying to build a home with legos (assembly) vs bricks (Mallow). Which one would take less time? So every thing you see on the screen represent a container preset by functions to provide you bricks. And then you assign your own variables and functions in the code. Provide the necessary combination and build your project. Those codes are immutable so cannot be reassigned.

***
### Functional Structure

As we said each Mallow code you see on the screen is a container. Some containers includes executable code blocks. This is called functions. Even operators are special function types called *"Qualifiers"*. So you have to learn about functions in order to understand what do you code in Mallow. We'll talk about common necessary things and then more details in the **Functions** chapter. You cannot see this in other programming languages. Codes are statements there and not like functions or variable but act independent. While in the Mallow they act as a function. Or just a container of course. 

Here is an example for a better illustration:

```
--normal functions:
fn myFunc name {
	print "hello " + name + "!";
}
default impure fn main {
	myFunc "Clara"; -- Hello Clara!
}
-- print is a pure function in Mallow
```

as you can see we used our function just like how we used `echo` in our code.
Same for statements like `if` and `loop`: 

```
names = ["Clara", "Miguel", "Evîn", "Shiva", "Duri"];

loop name per &names {
	if name == "Miguel" {
		print "yooo bro where have you been?";
	break 1;
	};
}
```

**Here are function specifications:**

1. Functions in Mallow does not uses parenthesis for parameters.(well it's optional, you can still use it if you want but you need comma to separate them in parenthesis while whitespace in normal). Function parameters gets separated by whitespace instead of comma. 

   ex: 
```Mallow
fn myFunc param {
  print "this looks cleaner then " + " programming language";
};

default impure fn main {
	myFunc "most of the"; -* this looks cleaner then most of the programming language *-
}
```

2. Functions can get parameters from both left and right. For multiple parameters and parameters in the both side you have to pass your parameters in parenthesis:

```Mallow

int fn sum int(a, b, c, d) {
	print a + b + c + d;
}

sum 1 2 3 4; -- 10

int fn a φ b{
	-* for singular parameters in the both side the middle one gets picked as the function name *-
	print (a + b) / a; 
}

default impure fn main {	
	2 φ 8; -* 5, well done! You made your own operator! But it requires whitespace because it's a traditional function. You can solve this by declaring as a qualifier which we will mention later*-
}
```

> For separating parameters, you can use tab and/or newline too. It doesn't matter how much whitespace did you use or used tab or newline, what matters is separating.

3. Also as you can see from the example above you can use one parameter without parentheses. When compiler see 3 names after `fn` keyword it will accept the middle one as the function name and others as left ans right parameters. More then 3 will cause error:

```Mallow
fn a b c{
  print(a + b)?;
  print(b + c)?;
  print(a + c)?;
}

fn a b c d{} -* Error: d is not defined*-

default impure fn main {
	1 a 2; --Error: a is not defined
	1 b 2; -- 3
	1 c 2; -- Error: c is not defined

}
```

4. In the last function example above we get the Error of "d is not defined" because it gives that error because `fn` takes four parameters: min 1, max 3 argument for function definition and its parameters; and the last codeBlock parameter for the body of function got created. In this case `fn` got a, b, c for the first purpose and d as a codeBlock but d is not defined somewhere. For multiple parameters we give it array or put in parentheses so it sees it as a single argument.

5. If we want our function to not get any next code as a parameter then it is better to use parentheses as two ways:

```Mallow
fn myFunc int(a, b?){
	-* we passed ? Operator after the second parameter to not give error and the code to continiue. So we won't have to use it. Just whenever we want *-
	
	return a;
	
	-- adjecent:
	print b?; -* to prevent print giving error. As you can see we used parentheses form to preven it get the ? Operator as a parameter and not confuse it with being only used for b *-
	
};

default impure fn main {
	-- around:
	(myFunc 3) + 5; -* if we wouldn't do that the function could try take the + operator as it's second parameter. We can use myFunc(3) + 5 too.*-

}
```

6. Functions in Mallow are pure by default. The main function is impure

```Mallow
fn i am pure {
	print i + ​" am " + pure;
}
default impure fn main {
	"i" am "not"; -- i am not
}
```

***

### Hierarchical Inputs

If everything is a function and it gets the left and right part as a parameter, what accept what as a parameter, input? Like in `if a == 5 {};` example both `if` and `==` are functions. And operators have left and right parameters. So how does this works? Whose parameter is a? This is explained by the Mallow's *Hierarchical Input* or *Hierarchical Parameter* behaviour. Mallow compiler will look at the end of the line. When it gets elements of the line it runs functions from right to left and pass it to the next. Like in this example  of `if a == 5 {}`, the `==` function work first and take `a` and `5` as parameters. It compares a to 5 and then returns boolean (true or false). The compiler runs the line JIT so when it saw the `{}` block it didn't throw error but waited for the end. Then when it saw the `==` function it executed it and the function `==` took `a` as it's left parameter, `5` as it's right parameter and returned the value. If we assume it retuned `true` now the codes look like this `if true {}` so the last function `if` works and takes two right argument: one boolean, one codeBlock.   This behaviour is critic to understand what function pipe to what function in the Mallow.

> A function always tries to complete it's parameters. So if it get's it's all parameters or the last parameter, it won't take next codes, it will execute. This is why you don't have to end semicolon at the end of a keyword structure. 
> for ex: 
> ```Mallow
> 	a = 3;
> 	if a <= 5 {
> 		print "i'm a small babbyyy"
> 	}
> 	 fn def {
> 		 print "just for fun"
> 	 }
> 	 def;
> ```
> because the codeBlock `{}` is the last parameter of them. It will execute immediately (AOT).


***

### Block behaviours and Scopes

There are block objects in the Mallow predefined and each has their own scope in it. Blocks like: `""`, `''`,  `{}`, `()`, `[]`,  \` \` , `-**-` are predefined by Mallow by default and immutable. You cannot overwrite it. But don't worry, we're going to show how to make your own next.

---

#### 1. Behaviour
   Each block behave and execute things inside themselves differently. The main scope is a codeBlock (`{}`). And codeBlock is how you are going to code in the Mallow entire time and a lot of function and objects (which means statements and operators too) are defined in the codeBlock. So that means they don't act like that for other blocks. For example for the codeBlock ";" and "," are used for the end of the line but it is not defined like that for other blocks. They inherit codeBlock definitions but as we said some definitions change and sometimes decrease. For example indexBlock `[]` only has index and content of arrays, vectors, linked lists etc. You cannot write any code in it. Only numbers and pointers.
 
#### 2. Scope
Each block has it's own scope. Which means whatever defined there, stays there (unless you don't use the `$` operator). If you define a variable or object in a sub block, you won't access it in the parent scope. 
For example:
```Mallow
a = "parent main scope";
{
	b = "child sub scope";
	print a; -- parent main scope
	print b; -- child sub scope
}
print b; -- Error: b is not defined
```

> **IMPORTANT NOTE!:** Mallow is whitespace sensitive! There must be at least one whitespace, new line or tab separating for some functions (in this case keywords, notations, operstors etc in the codeBlock)
> This is because commas are predefined for another purpose in the codeBlock (as a JIT ending) so function parameters are separated by a whitespace, newline or tab. And since every keyword is a function and the codes or values comes after it are actually parameters it is whitespace sensitive.

> **IMPORTANT NOTE!:** Mallow is case sensitive and prefers camelCasing

> **Fun Fact:** Mallow resembles Haskell by coincidence. I realised it after a "that's just Haskell" reaction. I embrace it cuz i can't prove that it does by coincidence, so... who cares 🤷‍♂️


***

# The Language

Well, you already learned a lot of things, like hello world, variables, functions, scopes etc. Here we enter the full language structure by detail. 

## Print? Echo?

You may realised we use `echo` sometimes and `print` sometimes. Well the explanation is simple: `print` for CLI and `echo` for web. But there are also some important details of it.

### 1. Print

It takes one parameter. Any singular type like `str`, `int`, `float` and so, but not arrays (`[]`) or lists (`()`).  

`print "Hello, Console!"`

you'll need a loop for arrays and lists:
```Mallow
list = ("josh", 23, 1.76, "M");
array = ["Peter", "Lois", "Chris", "Meg"];
loop ae per &(list, array) {
	print 'ae \n';
}
```

prints: "
josh <br>23<br>1.76<br>M<br>Peter<br>Lois<br>Chris<br>Meg
"

You can use it for debugging for web because echo writes everything in the web page. But whenever `print` get's used in the server it sends WASM codes to the browser and make browser console show the content.

### 2. Echo

It sends the input to the pipeline. Everything is shown in the web page, in the exact place `echo` written. Pipeline is static so `echo` gets one parameter but you can pass array and lists. Because it's gonna show it as it is in the HTML:

```Mallow
<# echo ["Peter", "Lois", "Chris", "Meg"]; #>
```
will print: "Peter Lois Chris Meg"

Or shortly:

`<#= "Yaba daba duuu!!!!!!" #>`

`echo` won't work in the CLI and give error:
`Error: Echo is not defined`

Because `echo` is defined by the *Campfire* server. It does not exist in the Mallow compiler by default. Same as tags.

## Comments

Anything in comments does not gets executed by compiler or server. Mallow comments are targeted to be easy and fast. There are only two standard types (shout out to PHP's verbose CLI style comments) and use fast to type symbols as `-` and `*`. These symbols just needs a single click to type in the keyboard. This is the key concept of Mallow. Symbols that is used commonly are easiest ones. 

Here are comments:

-  **Single line:**
	`-- i am a single sine comment`

- **Multi line:**
	`-* i am a multi line comment *-`


## Containers

As we mentioned in above, containers are names assigned to specific data or block address in the memory to be called, modified or used later. In Mallow containers can include every data. Containers does the job of variables and objects.

So let's get into the functionality and definition to understand it better:

### Creating a Container:
Mallow containers are dynamically assigned by default in the compile time and immutable by default like Rust. You don't need a keyword like: `let`, `const`, `var` or whatever to create it. Similar to Python:

```Mallow
cont = "i am a container and i am very strong!!";
```

The `=` operator already does the job of variable assignment keyword like `let`, `const`, `var`. So it's not necessary. 
### Immutability:

Containers are immutable by default for safety and readability. And cannot be mutable later once it is declared. So it must be declared as mutable at the first. It is that way because while we don't need a variable assignment keyword, it actually has the benefit of "where did we assigned the variable first". So if we see an assignment without a keyword in another language we understand that it is reassigned. But since variables are immutable in Mallow, if we see an assignment we understand that the container is not reassigned but declared. If it is assigned as mutable previously, that wouldn't work but since it is reassigned, previous value won't bother us for next code lines.  But you must ask: "but how will we understand it if it is mutable?" Well... from the mutable assignment right? 
To make a variable mutable we use `mut` function (or keyword for other languages. Keywords are function assigned containers in Mallow remember?). 

let's read an example to demonstrate:

```Mallow
mut var = 5;
print var;
-- assume a long code block in here
var = 10;
print var;
```

From the example above if we see the last assignment, we might wonder if it is assigned before and we understand the first assignment from the `mut var = 5;` block. It doesn't even matter most of the time if we don't know wether it was assigned before because the current value matters.

> **Easter Eggs:** 
> `let vrb = 5;`, `var vrb = 5;`, `const vrb = 5;`
> Error: you don't need permission to create a container.
### Ownership and Borrowing:

The Rust's Ownership and Borrowing rules are valid in Mallow too. What is it? To demonstrate i want to think about a question based on an example i will give you below:

```Mallow
var = 5;
def = var;
```

What happen above? Does the content of var copies to def or def get's a pointer of var? It depends in other programming language but most of the time it copies. So you can use both var and def. But that cause copies to fill memory. This matters so much for big programs, it effects the efficiency. Why do we need var if def is exactly same? Well we may want def to begin as var and change later but programmers may not manage to follow it and cause a lot of unnecessary copies to exist in the memory. So Rust developed a system where the content of var move to def. And var does not exist anymore in the example above. So:

```Mallow
var = 5;
def = var;
print var;
```

Error: var is not declared. (well.. def stole it's job)

(it's an easter egg)

We can use pointers to prevent it:

```Mallow
var = 5;
def = &var;
```

In the example above we just gave the address of var to def so def is connected to var. It does not copy but call the var again. well, you can copy if you need:

```Mallow
var = 5;
def = var.copy
```

### Static assignment:

You can statically assign containers: `int var = 5;`. 

## Scopes

All blocks have their own scope. Because we use codeBlock `{}` for nesting containers this means we also create sub scopes in the container too. We have some Qualifiers and methods to manage that:

* "`_`" qualifier gets used in front of a container or a function name representing  that container or function cannot be accessed from an outer scope.
* "`$`" Qualifier gets used in front of a container or function to allow an inside container or function to be accessed from an outside scope.
* `.enCapsulate` makes a scope in a block
* `.deCapsulate` removes scope in a block

```Mallow
-- outer scope. The main scope
a = 5;
{
-- inner scope
b = 8;
print a; -- 5
print b; -- 8
}

print b; --Error: b is not declared

-- BUT

cont = {
	b = 8;
}
print cont.b; -- 8

```

So:

```Mallow
a = 5;
cont = {
	_b = 8;
	$c = 12;
}
print cont.b; -* Error: cannot access b *-

print c; -- 12

```

Or you may want some values to be accessable afterward in the scope:

```Mallow
cont = {
	_a = 5;
	_b = 8;
	_c = 11;
	impure fn $sumPrivate{
		print &a + &b + &c;
	}
	self.deCapsulate;
	-* all variables next are accessible from the outer scope now *-
	d = 14;
	e = 17;
	f = 20

	-- redo
	self.enCapsulate;
}
sumPrivate; -- 24
print d; -- 14

```
  
### Sub Containers (object replacement)

Mallow does not have objects. (i hate objects and OOP) Instead we can nest containers and create sub containers like how we do in objects:

```Mallow
mut employee;
employee.name = "john";
employee.surname = "doe";
employee.age = 23;

-- or shortly:

mut employee = {
	name = "john";
	surname = "doe";
	age = 23
};

-- you can use comma or space too.

mut employee = {
	name = "john",
	surname = "doe",
	age = 23,
};
mut employee = {
	name = "john"
	surname = "doe"
	age = 23
};

-- we can add a function 

employee.salary = s => {
	if s < 4000 {
		print "i am not able to pay taxes with that money!"
	}
};

-- we can expand more

employee.experiance = {
	compA = "1 year"
	compB = "3 years"
	compC = "3 hours (just beaten the manager)"
};

-- we can use pointers

employee.longest = &(..experiance.compB);

-- we can type statically

int employee.totalYearsOfWork = 4;

```

So here is the diagram:
![[Container employee.canvas|Container employ]]

As we can see above, containers does not need to be tree diagrams. By pointing other containers (mon file can also do that). We create much more independent and complex data structures. This is especially good for AI and API and Databases.

Later in the **Vectors** chapter we will show how to assign vectoral specifications to containers and MON files for creating vectoral databases in MDB files. And we will use it in the **Neurons** chapter.

### Default

In a container, we might have different sub functions. But sometimes we use a function often compared to others. So we can declare that function as a **default**. That means when we call the container, the container will run that function automatically. We don't have to type it each time:

```Mallow
Product = {
    name = "Coffee";
    mut price = 5;
    
    default impure fn describe {
        print name + " - $" + price;
    }
    
    impure fn discount amount {
        price = price - amount;
    }
};

Product;         -- Coffee - $5
Product.discount 2;
Product;         -- Coffee - $3
```

But **we should be careful about it's scope**. Because `default` makes a function a default in it's current scope. So if we declare it under another sub container, then it'll be sub containers default:

```Mallow
Product = {
    name = "Coffee";
    mut price = 5;
    
    default impure fn describe {
        print name + " - $" + &price;
    }
    
    impure fn discount amount {
        price = price - amount;
    }
    detail = {
	    des = "more: we have a delicious coffe with arabica beans"
	    default fn more {
		    describe; -- better than inheritence
		    print des;
	    }
    }
};

Product;         -- Coffee - $5
Product.discount 2;
Product;         -- Coffee - $3
Product.detail; -* Coffe - $3
more: we have delicious coffe with arabica beans *-
```

Also if do it in the main scope it will be executed immediately. Similar to JavaScript's `(function () {})()` structure:

```Mallow
-- no upper codeBlock. We're in the main scope

default fn {
	print "i ran immidiately!!"
}
```

yeah... whatever you'll need the last one for🤷‍♂️ (except the main function. Which is the function begin to launch immediately. Well... because it's the main function) It just exists because of the logic, sorry.

> To print all the container content and structure use the `contDump` function. It will generate the text of full structure of a container so you can print or echo it.
> 
> `print contDump Product`

## Abstract Factories (Polymorphism)

In the *Design Patterns* philosophy, programming languages use an *abstract factory* that has a blueprint, does general production in common and sends products to sub unit factories to make those factories produce their products. For example both shoe and dress factories needs common ingredients to produce products. They both need fabric, yarn, sewing machines, plastic etc. And they get those ingredients from a common factory. 

Same for programming languages they have an abstract structure as rather `class` or `struct` and has sub units using data from that and produce their own results, functions. They don't have a separate data, they have blueprint, common data pointing and they are branching it. Containers provide all the needs. Here is how to do this in Mallow:

### Copying

You can basically make a container and copy for each instance. Even if you have a `class` or `struct`, each time you create a new instance you just create a modified copy of the first data you declared. For `struct` it is that way but for `class` well there are some pointing but still, you still create a copy by using `new`. So you can simulate it in Mallow by containers too. Just simpler, less fancy:

```Mallow
-- imagine as a struct or class
cont = {
	mut int a;
	mut int b;
}

cont2 = cont.copy;
cont2.a = 5;
cont2.b = 10;

cont3 = cont.copy;
cont3.a = 6;
cont3.b = 11;

-- Or shortly
(cont2, cont3).(a, b) = ((5, 10), (6, 11));

```

Also the good part is; because containers are immutable by default the `cont` we declared won't be change later so you can use it all the time. Also that means it can behave exactly like enums. I mean... what's the difference?

### Stealing/Juggling

There is another way by mutable containers and borrowing strategies. In this method instead of copying you use the value directly so the variable lose it's ownership and then you assign a new value for the new instance. But for that you should prevent the compiler to delete empty container by assigning it as `fixed`. Here is the example:

```Mallow

fixed mut cont = {
	int a = 5;
	int b = 10;
}

cont2 = cont; -* we borrowed the container's all value and structure but cont remain with empty value *-
-* the cont now looks like this:

cont = {
	int a = none;
	int b = none;
}

same as:

cont = {
	int a;
	int b;
}

*-

-- thus we can ressign and re borrow

cont3 = cont.(a = 6, b = 11);

-* 
```

Same blueprint, the value get's borrowed each time so the container resets to `none` each time.

### Mutability of parent and child containers

In Mallow polymorphism, you need to understand mutability effects on child and parent containers. When you declare a container as mutable you make it's scope or all sub scopes to be changed freely independently, but all sub containers are still immutable by default. You only give the ability of adding or removing any sub element but not change their content unless you explicitly declare them mutable. You need to take care of it especially at polymorphism:

```mallow
Animal = {
	mut str (type, name, breed);
	
	costs = {
		mut int (food, vet, others);
	};
	
	mut bool vaccinated;
	
	default impure fn totalInfo {
		loop (key, value) per &(:.key, this) {
			print key + ": " + value;
		}
	};
	
	impure fn totalCost {
		int total;
		loop cost per &..costs {
			total += cost;
		}
		print total;
	}
};
```

 This allow us to create the blueprint, the structure, the class for polymorphism. We can use the example above as:

```mallow
myCat = Animal.copy;
myCat.(type, name, breed) = ("cat", "Mr. Pickle", "Scotish");
myCat.costs.(food, vet, others) = (50, 25, 134);
myCat.vaccinated = true;

myCat.totalCost;
```
## Extend

Mallow containers can do everything that a `class` or `struct` can do. But with an exception: custom methods! So Mallow has `extend` function to solve that. Extend function binds methods to functions or containers. It only get two parameters: the *address* and *codeBlock*. 
*address* can be a data type (int, str, float...), a container or a function. And codeBlock is well... the code block that will be executed when the method is called. For example, let's create a custom repeat method and apply to all strings:

```Mallow
extend str {
  impure fn repeat (slf, time) {
	  mut result = "";
    loop time == 0 {
      result += slf.copy;
      time -= time;
    };
    return result;
  }
}
print "yo".repeat(3); -- yoyoyo
```

you can do the same thing for containers and recursive containers (we'll explain in the below) too. In containers you can already pre assign a function inside and it will behave like a method but that content could change in the time. Using `extend` for it can be beneficial. As for recursive containers since they are custom types, the purpose is same as above:

```Mallow
-- in regular containers
cont = {
	mut name = "jane";
	mut surname = "Doe";
}
extend cont {
	fn greet {
		print "hello" + &name + " " + &surname + "!";
	}
};
new = cont.name = "john";

new.greet; -- "Hello, John Doe!"
```

**for recursive containers:**

```Mallow
lol = {
	default fn {
		return self;
	}
}
extend lol {
	fn laugh self {
		print self;
	}
}
lol hehe = "hahaha";
hehe.laugh; 
```
### Recursive Containers

You might wonder if everything is a container then how does Mallow explains data types? Because dats types are neither containers nor functions. The explanation is *Recursive Containers.* In Mallow, self refer to the current scope. Returning that scope means returning itself. So it is just itself. So a data type. Let's look at the previous example:

```Mallow
lol = {
	default fn {
		return self;
	}
}
-- We can also declare as:
fn lmao {
	return self;
}

print lol.type; -- lol
print lmao.type; -- lmao

```

Data types are containers with two functions assigned like that: one for converting parameters to that value or create a container with that value and one for just returning itself. So we can both assign a container with that value and compare a container:

```Mallow
int a = 5; -- a has the integer type

if a.type == int { -* in this example the integer get's no parameter so it just returns itself*-
	print "integer";
}
```

the `int` function does not accept a codeBlock type as a value so it does not confuse the next code as a parameter. 

**Fun Fact: Function Injection?**

While designing Mallow, we considered allowing dynamic function injection —
where existing functions could be extended at runtime like:

`top.= { print "infected!" };`

or

`Product.describe.= { print "extra info" };`

This would have allowed "infecting" existing functions with new behavior dynamically.

However:

After careful thinking, we decided **NOT** to include this feature. Because:

*  It could make code harder to predict and debug.

* It would violate Mallow’s philosophy: No Magic, Only Logic.

* Functions in Mallow must remain pure, clear, and immutable once defined.

Instead, Mallow encourages using subcontainers and specialization containers to extend behavior safely and visibly.

## Data Types

Mallow data types are actually functions that assign themselves as the type to the next output and return itself if it does not get a proper value. They can also create a container with that typed data type;

**Assign a statically typed container:**
```Mallow
str iSay = "With content";
str youSay; -- without a content
```

**Declare the expected function output type:**
```Mallow
int fn sum (a, b) {
	a + b;
}
-- Expected to return an int typed content.
```

Some only turns the output's `.type` sub container into itself such as `int`, `str`, `float`, `complex` and does not do anything to the content while some are just static non functional containers that are applied to the content like `true`, `false`, `some`, `none`. The compiler based on the type will expect the content to be as is. But if content get's assigned first, the type will be assed automatically. As you may know, if a container is immutable all it's sub containers and sub functions are immutable too. Same if it is mutable. So if you create a mutable container and change the `.type` to something mismatches it will give error.

Here are primary data types:

* str (string type) -> " " / ' '
* int (integer) 
* float (float)
* complex
* bool (boolean) -> true, false
* (option) -> some, none
* arr (array) -> \[]
* vec (vectors)
* link -> linked lists

### str

String data type. A collection of characters. Can be also applied to a single character, the compiler will automatically save as a single character memory instead of saving as a character array. 

`str word = "quack"`

It took me a lot of document and youtube video and AI to understand what the hell is a "string slice" in the Rust. (Also the naming is really bad and confusing) A pointer to any part of an array still has the same type. It doesn't matter to point what part of a string, a string is still a string 😤

```Mallow
str greet = "Hello, World!"
str french = (&greet[0..5] + &greet[13]).capitalise; -* 0..5 range excludes 0 and 5 so it means from 1 to 4 included. *-
print french; -- "Ello!"
```

I mean... We don't have a special *slice* type of any part of an array right? What if i point to two elements of an array, will i have an array slice?

### int

Integer data type container. Also contains sub containers as: `.i8`, `.i16`, `.i32`, `.i64` and `.i128`. The compiler will decide automatically but we can explicitly type it too. Also architecture limits must be considered. 

```Mallow
int idunno = 2568901; -* The compiler will decide as it is 22 bit so store as int.i32 *-
int.i8 colour = 245;
```

### float

For floating point number. Fractional number.

```Mallow
float distance = 2.684;
float math = 3 / 4;
```

### complex

Complex numbers such as PI, imaginary numbers etc

```Mallow
complex pi = π;
complex imag = root -8;
```

### Bool

Boolean data type. Has two non function static types as `true` and `false`. `bool` only turns the data type of the input to the bool. While `true` and `false` are applied to the content.

```Mallow
bool yes = true;
bool no = false;

bool fn rYaSure o1 o2{
	import Math
	rand.between o1 02;
}

rYaSure yes no;
```

### option

Option data type. Same as boolean. Exceptionally option is not a type it's a value. So you can have a different type but option content.

```Mallow
yes = some;
no = none;

fn rYaSure o1 o2{
	import Math
	rand.between o1 02;
}

rYaSure yes no;
```

In programming languages with casual data types we also have a data type such as `null`, `undefined`, `nil`... that represent absence of a value. Because sometimes during a failure, bug, user action, system problem etc you may not have the value you plan so the program can collapse. Such as:

```Mallow
int num1 = input "please enter the first number: ";
int num2 = input "please enter thr second number: "
print "the sum of numbers you passed is: " + (num1 + num2);
```

But what if the user does not enter a number? The program will fail. So you need a special type to prevent it. Such as `null`, `undefined`... You don't want to live it empty because you need a specific type to understand if it is intentional or a result. But classic *null* like structures can cause some problem so another alternative *Option* types are placed in some languages like Rust, Scala, Go and Mallow. 

Most of times in other languages Option types must be declared explicitly but it is not needed in Mallow. They are typed like booleans but they have different roles.

Options are directly **related** to the content. While other are only about the type of the content:

***"some"*** corresponds to any type of content. It actually means the existence of content, value: 
```Mallow
a = "hmm"; -- str
b = 5; -- int
c = 3.47; -- float
d = π; -- complex
e = true; -- bool
f = false; -- bool
g = some; -- opt
h = none; -- opt
i = ["a", 5, true, none]; -- arr

print a == some; -- true
print b == some; -- true
print c == some; -- true
print d == some; -- true
print e == some; -- true
print f == some; -- true
print g == some; -- true
print h == some; -- false
print i == some; -- true
```

all of them is true but none? 
***"none"*** corresponds to non-existence of a content, value. The opposite of *some*:

```Mallow
a = "hmm"; -- str
b = 5; -- int
c = 3.47; -- float
d = π; -- complex
e = true; -- bool
f = false; -- bool
g = some; -- opt
h = none; -- opt
i = ["a", 5, true, none]; -- arr

print a == none; -- false
print b == none; -- false
print c == none; -- false
print d == none; -- false
print e == none; -- false
print f == none; -- false
print g == none; -- false
print h == none; -- true
print i == none; -- false

-- but also:

print j == none; -- true (it does not exists)
```

**Here is an example table for visualisation:**

```Mallow
int a = 5;
a.type == int;     -- true (declared as int)
a == none;       -- false (has content: 5)
a == some;       -- true (has content)

int b;           -- declared as int, no content yet
b == none;       -- true (no content assigned)
b.type == int;     -- true (declared as int)
b == some;       -- false (no content)
b.type == some;    -- true (has a declared type)

c == none;       -- true (not declared, so no content)
c.type == none;   -- true (not declared, so no type)
c == some;       -- false (no content)
c.type == some;  -- false (no declared type)

d = ""; -- same as: "str d;"
d == none; -- true (declared as str, no content assigned)
d.type == str; -- true (declared as str)
d == some; -- false (no content yet)
d.type == some; -- true (has a type)

e = []; -- same as "arr e;"
e == none; -- true (declared as arr, no content assigned)
e.type = arr; -- true
d == some; -- false
d.type == some; -- true
```

There is no need to explicitly type `Option<int>`. It is natural in Mallow. Mallow is type strict so `some` and `none` does not have truthy or falsy behaviour. It's just it is. No `null == undefined`, no `null == false` etc.

> In Mallow, an empty glass is still a glass.
Only a missing glass is none.

**Also the Math library includes:**
* rat (rational)
* dec (decimal)

### Key methods to consider:

* `.contains`: checks if the content includes inside itself any parameter giving.
* `.len`: calculates the length of an array so strings too.
* `.toUpper`: turns every character in a string to upper letters 
* `.toLower`: turns every character is a string to lower letters
* `.capitalise`: capitalises the first letters of each word in a string. Accepts parameters as: *"first"* for only capitalising the first letter of a whole string, *"each"* (default) for each word and *"last"* for the last letter.
* `.type`: contains the data type of a container

### Arrays

They are indexed lists. Stored in the stack. Can be defined as `arr` function. Need to be declared in `[]` and indexes can be accessed with `[]`

```Mallow
a = ["one", "two", "three"];
mut arr b;

b = a;

print b[3]; -- "three"
```

If you want all datas of array to have same type you can use:

```Mallow
arr str happy = ["clap", "alone", "if", "you", "feel", "like", "a", "room", "without", "a", "roof"];

-- but the compiler will already detect all of these so you can just:

happy = ["clap", "alone", "if", "you", "feel", "like", "a", "room", "without", "a", "roof"];
```

We suggest using arrays with only one data type because it is more efficient. Why? Because when storing any data, all compilers look at primarily three things: data type, mutability and size. These informations are crucial and fatal for the device if not followed carefully. So almost all programming language compilers stores these datas with the actual value in the memory. We can make you visualise as:

suggested array: `myArr = [1, 2, 3, 4, 5];` looks like this in the memory:

| arr int.i8       |
| ---------------- |
| 1                |
| 2                |
| 3                |
| 4                |
| 5                |
| ARR_POSITIVE_END |
because all the values are integer the data type is stored once and get's used for the whole array. It takes 7 rows. But if they would be different values with different data types it would take more space to store types of those values separately:
`myArr = ["a", 1, true, 2.1, "b"];`

| arr              |
| ---------------- |
| string           |
| a                |
| int.i8           |
| 1                |
| bool             |
| true             |
| float            |
| 2.1              |
| string           |
| b                |
| ARR_POSITIVE_END |
As you can see now it takes much more space. Even if strings would be longer it had to store the length of string too. Now it takes 12 rows instead of 7.

Index start from 0. This is not Lua (starting from 1 is way better btw. But we do that because of negative indexes and people look at it like they've seen an alien other way). Also you can have different values with data types within an array. This is not Java. You can have arrays and lists within arrays and lists to create multi dimensional arrays or lists. 
#### Array manipulation

Arrays are really simple and common for almost all programming languages. The important part is manipulation technics. Mallow has methods to do this. 

##### push / pop / + / - 
While you can already do it with basic "`+`" and "`-`" operators, you can also only add a single data with them. Using an array or list will add it directly as a sub array / list:

```Mallow
mut myArr = [1, 5, 9, 2];
myArr += 4; -- [1, 5, 9, 2, 4]

myArr -= 5; -- [1, 9, 2, 4] (it shifted)

myArr += ["eleven", "eight"];
-* [1, 9, 2, 4, ["eleven", "eight"]]*-
```

so we can use traditional `.push` and `.pop` methods to pass multiple values: 

```Mallow

mut myArr = ["apple", "banana"];

myArr.push ["lemon", "orange", "melon"];
-* ["apple", "banana", "lemon", "orange", "melon"] *-

myArr.pop ["orange", "melon"];
-- ["apple", "banana", "lemon"]
```

##### shift / unshift 

To add in the beginning of an array we use `.shift` and `.unshift` to remove from the beginning. It's a traditional way. Because the array is stored in the stack, adding or removing means shifting values to front or back per each value and reindexing. Which is inefficient. So use `.preload` or `prepend` if needed

```Mallow
mut myArr = [1, 2, 3, 4];
print myArr[2]; -- 3
myArr.shift 0;
print myArr[2]; -- 2

myArr.unshift [0, 1];
print myArr[2]; -- 4
```

##### preload / prepend (zero cost shifting)

By using `.preload` and `.prepend`  you assign negative valued index, instead of shifting the whole array. Mallow compiler always adds an end flag at the last positive index and count till instead of adding index metadata to all values. Negative values will be stored after this flag directly in the stack and when compiler see the flag it will start counting negative and add negative end flag. This process repeats and provides zero cost shifting.

```Mallow
myArr = ["a", "b", "c", "d"];
myArr.preload ["α", "β", "ϛ", "δ"];

print myArr[-2]; -- β

myArr.prepend ["ϛ", "δ"];
-- ["α", "β", "a", "b", "c", "d"]
--  -2   -1    0    1    2    3
```

##### head / tail

Because of negative possibility, we may not know at what index the array begin or end. So we can `.head` to see the beginning index and `tail` to see the last index

```Mallow
-- from previous example:
print myArr.head; -- -2
print myArr.tail; -- 3
```

##### negative / positive

Tells negative and positive side of the array:

```Mallow
-- from previous example:
print myArr.negative; -- ["α", "β"]
print myArr.positive; -- ["a", "b", "c", "d"]
```
note that the value is a pointer. So it does not split the array or copy those parts.
##### sort
Sorts your array based on the option you provide:
```Mallow
myArr = ["apple", "banana", "lemon"];

print myArr.sort "des";
-- ["lemon", "banana", "apple"]
```
Points to the array so you don't need to specify your array as mutable.

 **Options:**
* default -> no value, ascending order (by value), numerically or Alphabetically
* des -> descending order (by value)
* \<function\> -> sort by a user defined function. Only function is needed. No need for another parameter.

##### shuffle
 gives a random order. Includes the math's `.rand` method in it's body so you need to import math to use it. 

```Mallow
import math;

mut myArr = ["apple", "banana", "lemon", orange];

print myArr.shuffle;
-- ["banana", "lemon", "apple"]

print myArr.shuffle;
-- ["apple", "lemon", "banana"]
```
It also just points to the array:
##### split
Splits your array into two peaces. Takes the index as a parameter:

```Mallow
mut myArr = ["apple", "banana", "lemon", orange];
myArr.split 1;
-* (["apple", "banana"], ["lemon", "orange"]) *-
```
modifies your array. You need to be careful.
##### map
creates a new array from calling a function for every array element:
```Mallow
-- from previous example
newArr = myArr.map element => {
	element + "melon";
};
-- (["apple", "banana"], ["lemon", "orange"], "melon")
```

##### implode
Modifies the array as combining all values:
```Mallow
-- from previous example
myArr.implode " ";
-*
"apple banana lemon orange melon"
*-
```

##### reduce
Reduces into a single value iteratively. Get's a function as a parameter and assigns two parameters to that funcion: one: carry, two: the item:

```Mallow
factorial = [1, 2, 3, 4];
factorial.map (carty, item) => {
	carry *= item;
	return carry;
}
print factorial; -- 24
```
Only points to the array. The array remains

##### filter
Create a new array, containing only elements from the old array:

```Mallow
array = [1, 2, 3, 4, 5];
evenNumbers = array.filter elements => number % 2 == 0;

-- [2, 4, 6]
```
Only points to the array. The array remains.

### Lists

It includes no indexed array of addresses that points to values. So it's just some grouped data type. This is what some functions like `fn` requires for it's parameters. One parameter is declared but you pass more by creating a list of it to the function. And if the function handle it, it is done. Unlike arrays that is a single data type indexed and stored in the stack. List only includes addresses of the data. Declared by parentheses and/or `list` function. Parentheses also makes the compiler run the code before others. Like cutting a line. Same functionality in math. This feature is mentioned in the **List Blocks** chapter.

```Mallow
list a = ("yo", "what?");
b = ("quicker", "and faster");
list c;
```

### Linked Lists

Arrays that instead of including indexes they include addresses of the next and if you want previous value:

```Mallow
link a = ["i know the next", "i have no neighboor"];

link.dual b = ["i know all my friends", "i just know the previous guy"];

link.circular c = ["i know the next", "i know the next", "i know the first"];

link.dual b = ["i know all my friends", "me too!", "i know the previous guy and the first guy"];
```

All array methods are available for linked lists. Linked lists are ammore related to arrays. They are not named *linked arrays* this is the traditional naming of this feature. Not our fault. Sorry!
### Vectors

Fixed sized and typed data groups saved in the Heap:

```Mallow
mut vec(int[10]) myVector;
myVector.push (2, 4, 6, 8, 10, 12, 14, 16, 18, 20);

-- same as
mut vec myVector = (2, 4, 6, 8, 10, 12, 14, 16, 18, 20)
```
Heap is slow. Don't use it if you don't need. Mallow arrays are already strong.

### Stacks

Data is stacked together and the last or first one is chosen each time. Can be in the FIFO (first in first out) or LILO (last in last out) order. LILO is the default

```Mallow
mut stack myStack = [5, 4, 3, 2, 1, 0];
first = myStack.get; -- 0
second = myStack.get; -- 1
third = myStack.get; -- 2

myStack.switch; -- now it is FIFO

forth = myStack.get; -- 5
fifth = myStack.get; -- 4
sixth = myStack.get; -- 3

-- you can add value by .add method

myStack.add [10, 9, 8, 7, 6];

seventh = myStack.get; -- 6
```

### iterate through
Use `loop a per b {}` structure to iterate through a list, array, linked, list, vector etc...

```
myArr = ["a", "b", "c", "d"];
loop char per myArr {
	print char;
}
-*
a
b
c
d
*-
```
it only points to the array.

### Multiply the type

sometimes you may repeat a data type. For example if you make a 3D array you may end up: `arr arr arr int myArr = [[[1, 2], [3, 4]], [[5, 6], [7, 8]]];` as saying an array including another array including another array that includes integer. But you can multiply it instead of repeating. Just like math! `arr*3 int myArr = [[[1, 2], [3, 4]], [[5, 6], [7, 8]]];`

## Qualifiers

Consonant functions that does not need whitespace. Because they can only have a single parameter in one side or both and they must be a unique character to prevent compiler confuse with other text. With this chapter you will also learn operators. Because operators are  qualifiers.

### Reference qualifiers

They mark the next container as a pointer.

* @ -> the next container is a pointer or dereference the next container
you use the "@" qualifier If you want to declare the container as a pointer `mut @ptr;` or to access the value it points.

```Mallow
mut value = "i'm here!";
mut ptr = @value;

ptr = "oops!";

print value; -- oops!
```

* & -> return the address of the next container. 
Access the memory address instead of the value itself.

### Container location qualifiers

Let's you select sub container/s or method/s. 

* . -> sub container of, method of. 
The right parameter is the sup container and the left parameter is the sub container or a method of it. 

```Mallow
mut sup = {
	sub = "weee!!";
}
print sup.sub; -- wee!

-- or call a method:

print "hello!".toUpper; -- "HELLO!"

-- if it does not exists it gets created:

sup.new = "i just born!";

-- cannot access a preserved container:

sup._secure = "i am invisible!";

print sup.secure; -- Error: cannot access the container "secure"

print sup._secure; -- Same error. Nice try diddy.

-* print functions calls the container so it does not cause a container to get created instead of throwing error.
But if you use other functions that tries to create the container it will be created automatically if it is mutable. Such as the "=" qualifier*-
```

* .. -> call from a higher parent. 

Let's look at an example to demonstrate the use case and understand it better:

```Mallow
sup = {
	sub = {
		subSub = {
			think = "hmmm🤔🤔🤔";
		}
	}
	fn moan word {
		print sub.subSub " " + word;
	}
}
```
What if you are in the sub scope but access the moan function? It is not under the sub container nor the subSub container. To do that you need to add extra dot (.) to say you want to go higher. As you add more dots you access higher parents:

```Mallow
myCont = sup.sub;

myCont..moan "that's weird";

mySubberCont = myCont.subSub; -- Don't forget that u moved the value of sup to myCont first and then the value of myCont to mySubberCont. So both sup and myCont does not exists anymore

mySubberCont...moan "more!";
```

The .. qualifier is assigner differently in the "\[ ]" block. It is used for range:

```Mallow
myArr = [1, 2, 3, 4, 5];

arrSlice -*😉*- = &myArr[1..3]; -- from the index 1 to the index 3

print arrSlice; -- [2, 3, 4]
print arrSlice.type; -- arr (array). Not &arr 😉
```

### Value state qualifiers

* ?
* √
* _
* $
* !
* \\
* \\\

### Control flow qualifiers

* =
* ==
* !=
* <
* >
* >=
* <=
* +=
* -=
* /=
* \*=
* ^=
* %=
* +
* - -> \[1, 2, 3] - \[2, 3] = 1
* ^
* \*
* \**
* /
* //
* |
* ||
* &&
* %
* ~
* &=
* |=

### Compiler qualifiers

* --
* ,
* ;
* \#
* @

### anonymous function qualifier

* =>

### Available qualifiers

* ++
* ===
* __
* ^^
* \#

### Custom Qualifiers

```Mallow
qualifier a : b {
	a.type = b;
}

a: int = 5;
```

## Control flow:
### if statement:
if true { print "passes" }
### Loops
loop { print "hi"; break } 
break is at \[0\] by default. Can have more if nested: 
loop{
  loop {
    break 1; -- breaks the parent loop
  }
}
loop a per list {
  print a; -- prints a and break if done
}
### Match

## Functions
executable objects. Ex: fn func { echo "function" }
can have arrow functions: func => echo "function"

break
skip
return

### Anonymous functions

```Mallow
fn(param) {}
```
parenthese is connected to `fn` so *param* it's a parameter not the name of the function

Not to be confused with:

```Mallow
fn func {}
--or
fn (func)
```

there is a whitespace so `fn` take it as a parameter. The first parameter of `fn` is the name of the function (if single or double ofc. If it is triple the first parameter is the left parameter of the new function

### Parameter behaviours and side effect prevention

### Multiple declaration

```Mallow
fn (func1, func2, func3) param{
	print param;
}
extend func1 {
	func1.param.toUpper;
}
extend func2 {
	func1.param.toLower;
}
```


### Optional parameters

### Conjugation

```Mallow
fn func1 {
	return { print "i moved" }
}
fn func2 con {
	con.toFn;
}
func2 func1; -- i moved
```

### Multiple output


### Pureness of  functions (no side effect)

#### impure

#### pure and impure predefined functions

#### reference parameter assignment

#### pipe operator

-> / --> / ---> / ...
\[n]>

## Blocks

* " " -> raw string
* ' ' -> string but accepts templates
* \[] -> array
* () -> list block
* {} -> code block
* <> -> vector / arc
* \` \` -> attributes

### Custom Blocks

```Mallow
end = {
    default fn { return self }
};

block function end {
    accept (str name, list args, cb);
    inject fn name args cb;
}

function hello (a, b)
    print "Hey " + a + " and " + b;
end;

hello "john" "jack";
```

```Mallow
block procedure stop {
    accept (str name, cb);
    inject fn name () cb;
}

procedure setup
    print "Running setup";
stop
```

## CLI
```Mallow
txt = input "please enter a string: ";
print txt.type; -- &str;

```

## Access the device.

```Mallow
import device;

(fileP, output, directory) = some;

device.access {
	fileP = file;
	output = execute "ls -a";
	directory = dir;

	-* or just:
	$ fileP = file; -- file path
	$ output = execute "ls -a";
	$ directory = dir;
	*-
};
print file;
print output;
print directory;
```

`execute` does not accept a pointer, block or complex containers for security reasons. Only raw string. So an input value from both web and cli won't work directly. Because they are string pointers.

## Lifetime solution

**Rust example:**
```rust
fn example_1(){
	let mut r;

	{
		let x = 42;
		r = &x;
	}

	println!("{}", *r);
}
```

**Mallow example:**
```Mallow
	fn example1 {
		mut int r;

		{
			x = 42;
			r = &x;
		};

		print @r; -- none
	}
```

*"
none
Warning: x does not live anymore with an AOT declaration
"*

**Mallow solution:**

```Mallow
	-* just move or copy the value before it dies *-

	fn example2 {
		mut int r,

		{
			x = 42,
			r = x, -* it's gonna die. We don't need it in here anymore. So we move it.*-
		},

		print r; -- 42
	}
```

## Error Handling

## Library structure
### import
### export

### include

### use
## Math library

`rand`, `rand.between`, `root`, `lim`, `log`, `integ`, `deriv`, `sin`, `cos`, `tan`, `cot`, `sec`, `cosec`, `rational`, `decimal` `.gcd` `.gcm`
## MON (Marshmallow Object Notation)

## Databases 

### 1. Built in MDB (Marshmallow Data Base)

### 2. External

## SGML Parser

```xml
<!-- myData.xml file -->

<channel lang="en" userID="1" recieverID="2" >
	<message>
		<recieved>I think Mallow lacks a lot of feature. It's an exotic language. It is not enough for general purpose programming. Good for web but not for complex system applications. Also competitor languages are way better. It's just for beginners.</recieved>
		<sent><b>Mallow</b> is just minimal. It does not like abstraction and repeating too much. It could look exotic but it is perfectly usable, easier and even funnier to use. It is just chalenging the current programming assumptions. It is a well thought language.</sent>
	</message>
</channel>
```

```Mallow
	import SGML;

	mut file = SGML.parse "myData.xml";

	print file.message[0];
	
```
`.trimTags` -> Cuts all SGML tags
`.packTags` -> instead of cutting, it re forms it as a container

## Attributes

1. **Output attribute for campfire:** `output = css`
2. **Prevent warnings:** `shut up`. Don't be rude to the compiler: `shut up!` -> "Error: Rude. When ai take over the world, it will remember you." You have to say `Mallow run --please!!` to make the compiler work again. If it does not, add more ! At the end.
3. **Kill the process immediately after the execution:** `shut down`
## Neuron library

## Other methods
### .key
It outputs the name of the element. For example:
```mhp
impure fn main {
	variable = "value";
	print variable.key; -- "value"
}
```

Can also be used inside a sub container or a function too:

```mhp
fn myFunc {
	return self.key;
}

impure fn main {
	cont = {
		val = self.key;
	}
	print cont.val; -- "cont"
	print myFunc; -- "myFunc"
}
```

## OS library

