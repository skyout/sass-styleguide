Grasshopper SASS Style Guide
============================

*A guide to developing stylesheets in SASS*

Table of Contents
-----------------
    
1. Consistency
2. Formatting
2. Mixins
3. Variables



Consistency
-----------

### Consistency

**Be consistent.** If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.

Formatting
----------

SASS should be developed using the `SASS` indentation only style not the `SCSS` bracket based style. 



Imports and Charset
------------------

SASS imports and charset declarations should always be at the top of each SASS file. Important are used to include variables, mixins, fonts, and other chunks of code that are reusable. 

* `@charset` declaration should always be the first thing. The default charset to be used is UTF-8.
* Variables, fonts, and then mixin declarations should then immediately follow. 
* If the file needs a reset or normalize, that should then follow next. 
* Comments should also be used to describe any other mixins that are not the standard `_variables`, `_fonts`, `_mixins`, or `_reset`
* File extenions should only be used if the extension is not the default `.sass`

**Good**
```
@charset "UTF-8"

@import "_variables"
@import "_fonts.scss"
@import "_mixins"
@import "_reset"

// global tooltip styles
@import "_tips"
```

**Bad**
```
// imports
@import "_mixins.sass"
@import "_fonts.scss"
@import "_variables.sass"
@import "_reset.sass"
@import "_tips.sass"

@charset "UTF-8"
```



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
