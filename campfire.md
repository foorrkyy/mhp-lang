# Campfire Server

## What is Campfire?

**Campfire** is the official server runtime for MHP (Marshmallow Hypertext Preprocessor).  
It is designed to handle **compiled or embedded MHP code** and deliver its output directly to the web, similar to how PHP works — but with a modern, efficient, and secure architecture.

One of Campfire's standout features is that it’s written entirely in **MHP** itself, demonstrating the language’s flexibility and power to build real-world, high-performance server software.

Campfire can:

- Parse and run embedded `<# MHP CODE #>` blocks inside HTML files.
- Handle routing and HTTP responses.
- Serve as a general-purpose app server for MHP-based projects.
- Integrate directly with **Ember** for seamless project deployment.

---

## Installing Campfire Server

### 1. Install MHP Compiler

Before you install Campfire, make sure you’ve installed the MHP compiler:

```bash
# For Linux / MacOS
sudo apt install mhp_lang

# For Windows
Download installer from: https://mhp-lang.org/download
```

---

### 2. Install Campfire Server

Once MHP is ready, you can install Campfire.

```bash
ember add campfire
```

Or download it directly from the Campfire release page:

```bash
git clone https://github.com/mhp-lang/campfire.git
cd campfire
ember build
```

---

### 3. Running Campfire

Navigate to your project folder and run:

```bash
campfire --serve path/to/your/project
```

Campfire will start parsing your `.html` or `.mhp` files and serve them on `localhost:8080` by default.

---

### 4. Example Project

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

```mhp
<!DOCTYPE html>
<html>
  <head>
    <title>Campfire Example</title>
  </head>
  <body>
    <# echo "Welcome to Campfire!"; #>
  </body>
</html>
```

Campfire will parse the embedded MHP code and send the rendered HTML to the client.

---

### 5. Configuration

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
Campfire is now ready to serve your MHP-powered websites and APIs!

Now you can make file as myfiel.mhp and print your first mhp hello world program.

plain:
```mhp
print "Hello, World";
```

Will send WebAssembly code to the browser to print it in the web browser console.

Web:
```mhp
<html>
	<head>
		<title>MHP!</title>
	</head>
	<body>
		<# echo "Hello, World!" #>
	</body>
</html>
```

Or shortly we can use this in web:
```mhp
<html>
	<head>
		<title>MHP!</title>
	</head>
	<body>
		<#= "Hello, World!" #>
	</body>
</html>
```

Also you may want to learn about situation and information about your setups. So you can use `<# mhpStat; #>` to see all the details.

# MHP web tag

On the CLI you can just code in the .mhp file. You don't need any main function or scope. And use `print` to write things. You can even just use the mhp compiler: `mhp {print "Hello, World!"}`. But for the web we use the *Campfire* server and we write either plain or with HTML tags and use `echo`. But to make the server differentiate MHP and HTML we need to code within MHP tags. The server will create an output HTML file (we can change that output file format too if we want ofc. We will mention in the next parts) by ignoring HTML parts, making them remain same (if not interfered by MHP). But when it sees special MHP tags it runs the code inside and send the output after finished. 

To code it, create an myFile.mhp file, and edit it: 
```html
<html>
	<head>
		<title>MHP Web!</title>
	</head>
	<body>
		<#
			echo "Hello, Web!";
		 #>
	</body>
</html>
```
open terminal in the folder you created the file in it, and run `campfire --serve path/to/your/project/myFile.mhp`.

as you can see MHP tags are different from HTML tags. And this allows **Campfire** to detect it. If it does not detect it, it will ignore and show static like html content:

```html 
<html>
	<head>
		<title>MHP Web!</title>
	</head>
	<body>
			echo "Hello, Web!";
		 #>
	</body> <!--This will show echo "Hello, Web!; #>" in the page--> 
</html>
```

**There is only one MHP tag:** `<# your code in here #>`. And that's it.

But there is also a shorthand PHP style echo tag: `<#= "Hello, Web!" #>`

## Behaviours of MHP tag

MHP tags are just for distinguishing between MHP code and HTML code. **They don't divide the main scope,** **They don't have any scope.** All the MHP codes in the same file still behave united. 

So we don't have to worry about scopes but we can also do PHP style cool tricks: 
**Code:**
```mhp
<html>
	<head>
		<title>MHP Web!</title>
	</head>
	<body>
<# 
	loop(i = 0, i <= 5, i += 1) {
#>
			<div class="card">
				<span class="header">
				</span>
				<div class="body">
				</div>
			</div>
<#
}
#>
	</body> 
</html>
```

**Output:**

```html
<html>
	<head>
		<title>MHP Web!</title>
	</head>
	<body>
		<div class="card">
			<span class="header">
			</span>
			<div class="body">
			</div>
		</div>
		<div class="card">
			<span class="header">
			</span>
			<div class="body">
			</div>
		</div>
		<div class="card">
			<span class="header">
			</span>
			<div class="body">
			</div>
		</div>
		<div class="card">
			<span class="header">
			</span>
			<div class="body">
			</div>
		</div>
		<div class="card">
			<span class="header">
			</span>
			<div class="body">
			</div>
		</div>
	</body> 
</html>
```

# Print

It takes one parameter. Any singular type like `str`, `int`, `float` and so, but not arrays (`[]`) or lists (`()`).  

`print "Hello, Console!"`

you'll need a loop for arrays and lists:
```mhp
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

# Echo

It sends the input to the pipeline. Everything is shown in the web page, in the exact place `echo` written. Pipeline is static so `echo` gets one parameter but you can pass array and lists. Because it's gonna show it as it is in the HTML:

```mhp
<# echo ["Peter", "Lois", "Chris", "Meg"]; #>
```
will print: "Peter Lois Chris Meg"

Or shortly:

`<#= "Yaba daba duuu!!!!!!" #>`

`echo` won't work in the CLI and give error:
`Error: Echo is not defined`

Because `echo` is defined by the *Campfire* server. It does not exist in the MHP compiler by default. Same as tags.

# Super global containers (Campfire only)

There are pre assigned variables by the *Campfire* server includes containers of  information. They are PHP styled. Here is the list of them:

* GET
* POST
* PUT
* DELETE
* SERVER
* FILES
* COOKIE
* SESSION
* REQUEST
* ENV

## GET

`GET` container includes URL parameters of a GET request. 

For example:
`http://mywebsite.com?name=John`
we get the name value by:
```mhp
<#
echo "Welcome, " + GET.name + "!"
#>
```

*"Welcome, John!"* 

## POST

same as `GET` but parameters are sent in the request header instead of url. So it's more secure.




