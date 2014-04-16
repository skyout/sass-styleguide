Grasshopper SASS Style Guide
============================

*A guide to developing stylesheets in SASS*

Table of Contents
-----------------
    
1. General Principles
1. Mixins
2. Variables



General Principles
------------------


### Consistency

**Be consistent.** If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.




Mixins
------

Mixins are declared using the `@mixin` declaration. Mixins should be housed in a file called `_mixins.sass`. Mixins are used for code that is frequently repeated through the stylesheets, but may not necessarily correspond to a single element or class. 

* Mixins should follow camel cased formatting
* Mixins should be order alphabetically by their title for organization
* If applicable, provide default settings in the mixin.

**Good**

```
@mixin button($color: $blue)
    background: $color
    display: block
    text-align: center
```

**Bad**

```
@mixin button($color)
    background: $color
    display: block
    text-align: center
```


Variables
---------

Variables are declared using the `$` notation. Mixins should be housed in a file called `_variables.sass`. Variables are used for common colors, fonts, and numbers used throughout the stylesheets. 

* Variables should follow camel cased formatting
* Ensure that variables are not ambiguous and describe the value they hold. 
* Like Variables should be grouped together to help with context and readability.
* Comment each variable or group to document the values. 

**Good**

```
// error and success colors
$errorRed: #ea5b54
$successGreen: #98fe98

// brand colors
$primaryGreen: #00853e
$secondaryBlue: #008fc5


// fonts
$proximaBold: "ProximaNovaBold", sans-serif
$promixaRegular: "ProximaNovaRegular", sans-serif
```

**Bad**
```
// colors and fonts
$red: #ea5b54
$green: #98fe98
$primary: #00853e
$secondary: #008fc5
$bold: "ProximaNovaBold", sans-serif
$regular: "ProximaNovaRegular", sans-serif
```
