# what-i-learned-weeks-9-and-10

## `Callback Functions`

A callback is a function passed as an argument to another function.  This technique allows a function to call another function.  A callback function can run after another function has finished.  

JavaScript functions are executed in the sequence they are called.  Not in the sequence they are defined.  

### `How to create a Callback`

In the following example I will console.log a message, but after a 3 second delay.  

```javascript
const message = () => {  
    console.log("This message is shown after 3 seconds");
}
 
setTimeout(message, 3000);
```

There is a built-in method in JavaScript called "setTimeout", which calls a function or evaluates an expression after a given period of time( in milliseconds).  

-------

## `Readline() Module`

Readline Module in Node.js allows the reading of input stream line by line. This module wraps up the process standard output and process standard input objects. Readline module makes it easier for input and reading the output given by the user. To use this module, create a new JavaScript file and write the following code at the starting of the application – 

```javascript
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
})
```

Here, the `createInterface() `method takes two arguments. The first argument will be for the standard input and the second one will be for reading the standard output. 

```javascript
rl.question('What is your age? ', (input) => {
    console.log('Your age is: ' + input);
});

```
Here, `rl.question()` method is used for asking questions from the user and reading their reply (output). The first parameter is used to ask the question and the second parameter is a callback function which will take the output from the user as the parameter and return it on the console. 
The output for the above code will be – 

```javascript
What is your age? 25
Your age is: 25
```
Here, the problem is it will not exit the application and it will keep asking for the inputs. To resolve this issue, rl.close() method is used. This method will close the interface. To use it in the application, write the following –

```javascript
rl.question('What is your age? ', (input) => {
    console.log('Your age is: ' + input);
    rl.close();
});
```
----------
## `JSON - what is it?? -`

`JSON` is a text-based data format following JavaScript object syntax. Even though it closely resembles JavaScript object literal syntax, it can be used independently from JavaScript, and many programming environments feature the ability to read (parse) and generate JSON.

### `Uses of JSON`

* Storing data

* Configuring and verifying data

* Generating data structures from user input

* Transferring data from server to client, client to server, and server to server. 

* Web services and API's use JSON format to provide public data. 

* It can be used with modern programming languages.  
-----------
### `JSON Format`

JSON format is derived from JavaScript object syntax, but it is entirely text-based.  It is a key-value data format that is typically rendered in curly braces. 

When working with a `.json` file, it will look like the following:
```javascript
{
  "first_name"  :  "Patrick",
  "last_name"   :  "Navarre",
  "online"      :  true
}
```
If you have a JSON object in a .js file, you'll likely see it set to a variable:
```javascript
let patrick = {
  "first_name"  :  "Patrick",
  "last_name"   :  "Navarre",
  "online"      :  true
}
```

Or you also may see JSON as a string rather than an object within the context of a JavaScript program file or script.  In this case, you may also see it all on one line:
```javascript
let patrick = '{"first_name" : "Patrick", "last_name" : "Navarre", "location" : "somewhere"}';
```
----------
## `fs.writeFile()`
Syntax: 
```javascript
fs.writeFile( file, data, options, callback )
```

* file: it is a string, Buffer, URL or file description integer that de-notes the path of the file where it has to be written.  Using a file descriptor will make it behave similar to fs.write() method. 
* data: it is string, Buffer, TypedArray or DataView that will be written to the file.
* options: it is a string or object that can be used to specify optional parameters that will affect the output.  It has three optional parameters:
    * encoding: it is a string value that specifies the encoding of the file.  The default value is 'utf8'. 
    * mode: it is an integer value that specifies the file mode.  The default value is Oo666.
    * flag: it is a string value that specifies the flag used while writing to the file.  The default value is 'w'. 
* callback: it is the function that would be called when the method is executed. 
    * err: it is an error that would be thrown if the operation fails.

```javascript
// Node.js program to demonstrate the 
// fs.writeFile() method 
  
// Import the filesystem module 
const fs = require('fs'); 
  
let data = "This is a file containing a collection of books."; 
  
fs.writeFile("books.txt", data, (err) => { 
  if (err) 
    console.log(err); 
  else { 
    console.log("File written successfully\n"); 
    console.log("The written has the following contents:"); 
    console.log(fs.readFileSync("books.txt", "utf8")); 
  } 
}); 
```
### Output:
```
File written successfully

The written has the following contents:
This is a file containing a collection of books.
```