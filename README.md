Grasshopper SASS Style Guide
============================

*A guide to developing extensible stylesheets in SASS*

Table of Contents
-----------------
    
1. General Principles
2. Formatting
3. Mixins
4. Variables



General Principles
-----------

### Consistency

**Be consistent.** If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.

General Formatting
----------

SASS should be developed using the `SASS` indentation only style not the SCSS bracket based style. 

### Spacing and Indentation

Indentation should be **four spaces**, if using tabs ensure that the tab settings is set to four spaces. Each selector should have at least one line break above. Properties should immediately follow the selector without a line break.

**Good**
```
h1
    margin: 0
    padding: 0
    
    
h2
    color: #846383
    margin-bottom: 20px
```

**Bad**
```
h1

  padding: 0
  margin: 0
h2

  color: #846383
  margin-bottom: 20px
```


### Sorting Properties

All properties should be ordered alphabetically to enable easy lookup. Any includes should go at the top of the propertly list, directly below the selector. Multiple includes should also be ordered alphabetically. 

**Good**
```
h1
    @include clear
    color: #000
    padding: 5px
    width: 200px
```

**Bad**
```
h1
    padding: 5px
    @include clear
    width: 200px
    color: #000
```


### Nesting

Nesting should only be used when absolutely necessary. Direct descendents also should be used sparingly due to the performance hit that comes with their use. Nesting should be four spaces, and any selectors should have a line break before them.

**Good**
```
body
    border-top: 1px solid #000
    
// main wrapper
article
    background: #ccc
    padding: 0
    
// main header style
h1
    color: #000
```

**Bad**
```
body
    border-top: 1px solid #000
    
    // main wrapper
    > article
        background: #ccc
        padding: 0
        
    // main header style
    h1
        color: #000
```
    
    
Classes, IDs, pseduo-classes, and other modifiers should nest inside their selector to maintain readability. The same rules with a line break above apply to these modifiers. 

**Good**
```
h1

    &.green
        color: #0085e3
        
    &:first-child
        padding-top: 0
        
```

**Bad**
```
    h1.green
        color: #0085e3
        
    h1:first-child
        padding-top: 0
```

### Chaining

When possible, if multiple methods have the same styles or very similar styles then chain them together using commas. If two selectors have very similar styles with one or two differences, then chain them together with the first selector's styles, then after set the minor changes to the second selector. 


**Good**
```
ol, ul
    color: #000
    line-height: 1.5
    list-style: none outside none
    padding: 0
    
ul
    color: #666
```

**Bad**
```
ol
    color: #000
    line-height: 1.5
    list-style: none outside none
    padding: 0

ul
    color: #666
    line-height: 1.5
    list-style: none outside none
    padding: 0
```
    

    
    

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
