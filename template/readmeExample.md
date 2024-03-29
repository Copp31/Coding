# :computer: Project for functions and testing interface 
> In this project, you will find a repository for script functions and a testing interface.

### Table of Contents
1. [Introduction](#introduction)
2. [Script functions](#script-function)
    1. [Folder location](#folder-location)
    2. [Script files configuration](#configuration)
    2. [How to use this repository](#repository)

3. [Test with the command-line interface (CLI)](#testing-CLI)
    1. [Technologies](#technologies)
    2. [CLI](#cli)

4. [Write a test](#test)
    1. [Step 1 : variable name](#variable)
    2. [Step 2 : test construction](#write)    
    3. [Step 3 : runClassTests()](#runtest)  
    4. [Empty template](#template)  

 <hr />
 <br>
### Introduction <a name="introduction"></a>
<br>
The purpose of this project is to be able to easily **share script functions** used in client projects. 

For developers, it's also possible to test all the functions or a specific one when you launch **run.js** from the command-line interface.
You will see the results of each test in the terminal. 

Each test needs to be written following a precise pattern and configuration.
<br>
 <hr />
<br>
## :memo: Script functions <a name="script-function"></a>
### Folder location <a name="folder-location"></a>

All the script files are listed under folders named by function type (autofill, autohide, search, dev).

```
scripts / autofill
        / autohide 
        / search
```

<br>

### Script file configuration <a name="configuration"></a>

- Script files use the extension .txt
- Each script has its own .txt file
- Title of each .txt file needs to start with a **capital letter**
- Each script begins with a summary :

```
// This script return a clear summary of items when you have the item's name and quantity.

let array = [];

[...]
```
<br>

### :star: How to use this repository <a name="repository"></a>

You will be lucky to find the script you are looking for exactly. You will probably need to change at least the docData's name to fit yours. 

The main idea of ​​this script repository is to create a library where you can get inspired and see more possibilities for your project. Some functions can be used as a starting template to help you write functions. 

We want to facilitate sharing information, so we will undoubtedly add more script functions over time. 

Take a look at all the scripts! :dizzy:

<br>
<hr/>

> The following section is for developers
<br>

## :chart_with_upwards_trend: Test with the command-line interface <a name="testing-CLI"></a>

Each script can be tested while running run.js. 

- Be sure that your .txt and .js files are both in the **mirror folder** of each other.
- It is essential to use the **same name** for these two files.

```
scripts / autofill
            /test.txt
        / autohide 
        / search

tests   / autofill
            /test.js
        / autohide 
        / search
```

**Important**: The .js file will be written following the EayTest.js model in the tests/dev folder.

<br>

### Technologies <a name="technologies"></a>
This project is created with : 

* Node version : 16.15.0
* NPM version : 8.5.5
* JavaScript : ES2020 

<br>

### Command-line interface <a name="cli"></a>

To run the testing interface, you need to install [Node](https://nodejs.org/en/download/) on your computer.

To launch tests, you have to run **run.js** from the **FWfunctions folder**.


```
$ node run.js 
```

You should see this in your terminal : 

```
--------------- testing interface ---------------

1. Run all tests from all functions
2. Run all tests from one specific function
3. Exit test module


What do you want to test (1, 2, 3)? 
```

If you want to run all tests from one specific function, you will be asked the function type (autofill, autohide, search, dev) and the function name:

```
Write Function Type : dev
Write function name : EasyName
```
<br>

:point_right: *Trick: if you don't know the exact **type** and **name** of the function you want to test, start with option 1. You will find the information that you need.*
<br>
<hr />
<br>

## :pencil2: Write a test <a name="test"></a>

*If you write a test, it's essential to follow the scripts/dev/EasyTest.js model.*

<br>

#### :one: Step 1 : variable name <a name="variable"></a>

The **name** of the .js test needs to be the same as the **name** of the .txt script.<br>
It is also the name of your class, so it needs to start with a **capital letter**.

The function **type** needs to be the same name as the folder's name. 
It's essential because the path is related to it.

ClassNameString and type are both strings.

```
let type = "dev";
let classNameString = "EasyTest";
let scriptPath = `./scripts/${type}/${classNameString}.txt`; 

class EasyTest {
  constructor(type, classNameString, scriptPath) {
```

As you can see, each function has its class. In this class, you can find all tests for a single script. 

<br>

#### :two: Step 2: Test construction <a name="write"></a>

The test follows the arrange, act, assert pattern. 

```
  testNombreEntier(scriptPath, detail) {
    // arrange
    const docData = { test1: "2", test2: "3" };
    // act
    tstf.transformScriptToFunction(scriptPath, docData, detail);
    // assert
    af.assertFunction(tstf.result[0], 5);
  }
```

- The title of each test needs to **start with "test"**, be clear, and be as precise as possible.
- You need to **add the docData** depending on the information required in the script. 
- The **wanted result** needs to be written in the second argument of assertFunction(). 

In the previous example, our docData is { test1: "2", test2: "3" } and we want to assert if the result is 5. 

<br>

#### :three: Step 3 : runClassTests() <a name="runtest"></a>

Finally, it's essential to change the name of the class in rct.runClassTests() with the class name:
```
rct.runClassTests(EasyTest, type, classNameString, scriptPath, detail);
```

That's it! You should be able to run your test with **run.js**! :rainbow:

<br>

### :round_pushpin: Empty template <a name="template"></a>

Here's an empty template to begin writing your test:

```
const tstf = require("../../utils/transformScriptToFunction.js");
const af = require("../../utils/assertFunction.js");
const rct = require("../../utils/run/runClassTests.js");
let detail = process.argv[2];

let type = "XXXtype";
let classNameString = "XXXclassName";
let scriptPath = `./scripts/${type}/${classNameString}.txt`;

class XXXclassName {
  constructor(type, classNameString, scriptPath) {
    this.type = type;
    this.classNameString = classNameString;
    this.scriptPath = scriptPath;
  }

  testXXX(scriptPath, detail) {
    // arrange
    const docData = {XXXDOCDATA};
    // act
    tstf.transformScriptToFunction(scriptPath, docData, detail);
    // assert
    af.assertFunction(tstf.result[0], XXXwantedResult);
  }
}

rct.runClassTests(EasyTest, type, classNameString, scriptPath, detail);

exports.XXXclassName = XXXclassName;

```

<br>

### :construction: Project status <a name="statut"></a>
This project is in progress 
