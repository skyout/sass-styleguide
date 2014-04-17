Grasshopper SASS Style Guide
============================

*A guide to developing robust stylesheets in SASS*

Table of Contents
-----------------
    
1. [General Principles](#general)
2. [Formatting](#formatting)
3. [Naming](#naming)
4. [Mixins](#mixins)
5. [Variables](#variables)
6. [Comments](#comments)



<a name="general">General Principles</a>
-----------

Make sure there is plenty of space around all of your selectors and comments to maintain readability. Alignment is also key to keeping a file readable, so ensure that all selectors and properties are properly indented. Any files that you will be including should be prefixed with an underscore `_` so that the easily found at the top of a folder.

**Be consistent.** If you’re editing code, take a few minutes to look at the code around you and determine its style. If they use spaces around all their arithmetic operators, you should too. If their comments have little boxes of hash marks around them, make your comments have little boxes of hash marks around them too.

The point of having style guidelines is to have a common vocabulary of coding so people can concentrate on what you’re saying rather than on how you’re saying it. If code you add to a file looks drastically different from the existing code around it, it throws readers out of their rhythm when they go to read it. Avoid this.



<a name="formatting">Formatting</a>
----------

SASS should be developed using the `SASS` indentation only style not the SCSS bracket based style. The only exception is `_fonts.scss`, due to a font stacking issue in SASS.

### Spacing and Indentation

Indentation should be **four spaces**. If using tabs in a code editor, ensure that tabs are set to four spaces. Each selector should have at least one line break above, this helps to separate selectors and ideas. Properties should immediately follow the selector without a line break, which will aide in putting context to the properties. Remove any trailing whitespaces. Trailing whitespaces are unnecessary and can complicate diffs.


```sass
// bad
h1
  padding: 0
  margin: 0
h2
  color: #846383
  margin-bottom: 20px


// good
h1
    margin: 0
    padding: 0
    
h2
    color: #846383
    margin-bottom: 20px
```

### Sorting Properties

All properties should be on their own line. Properties should be ordered alphabetically to enable easy lookup. Any includes should go at the top of the propertly list, directly below the selector. Multiple includes should also be ordered alphabetically. 



```sass
// bad
h1
    padding: 5px
    @include clear
    width: 200px
    color: #000


// good
h1
    @include clear
    color: #000
    padding: 5px
    width: 200px
```

### Chaining

When possible, if multiple methods have the same styles or very similar styles then chain them together using commas. If two selectors have very similar styles with one or two differences, then chain them together with the first selector's styles, then after set the minor changes to the second selector. 

```sass
// bad
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


// good
ol, ul
    color: #000
    line-height: 1.5
    list-style: none outside none
    padding: 0
    
ul
    color: #666
```

### Nesting

Nesting should only be used when absolutely necessary. Direct descendents also should be used sparingly due to the performance hit that comes with their use. Nesting should be four spaces, and any selectors should have a line break before them.


```sass
// bad
body
    border-top: 1px solid #000
    
    > article
        background: #ccc
        padding: 0
        
    h1
        color: #000


// good
body
    border-top: 1px solid #000
    
article
    background: #ccc
    padding: 0
    
h1
    color: #000
```
    
    
Classes, pseduo-classes, and other modifiers should nest inside their selector to maintain readability. The same rules with a line break above apply to these modifiers. Pseduo-class modifiers should go as close to their parent selector as possible. This allows developers to quick see any hover or other states without having to find them later in the file. Class modifies should also go near their selector whenever possible.  


```sass
// bad
h1.green
    color: #0085e3
        
h1:first-child
    padding-top: 0


// good
h1

    &.green
        color: #0085e3
        
    &:first-child
        padding-top: 0
        
```

Global styles for elements and very common classes should be placed near the top of the global stylesheet. This can include things like body, link, input, paragraph, and header styles. 

```sass
@charset "UTF-8"

body
    border-top: 3px solid #333

a
    color: #008fc5
    cursor: pointer
    outline: none
    text-decoration: none

input
    border: 1px solid #ccc
    
h1
    font-size: $font-size + 10
    
p
    color: #666
    line-height: 1.5
    
        
// rest of the file
```
    



### Shorthand Properties

CSS offers a variety of shorthand properties (like font) that should be used whenever possible, even in cases where only one value is explicitly set. Using shorthand properties is useful for code efficiency and understandability.


```sass
// bad
body
    font-family: Arial, Helvetica, sans-serif
    font-size: 14px
    font-style: italic
    font-weight: normal
    line-height: 1.5


// good
body
    font: normal 14px/1.5 Arial, Helvetica, sans-serif
```


### Shorthand Values

Omit unit specification after “0” values unless they are required. For color values that permit it, 3 character hexadecimal notation is shorter and more succinct. As a general rule, if a unit specification isn't required, then don't use it. 

```sass
// bad
p
    color: #000000
    padding: 0px
    line-height: 1.5em


// good
p
    color: #000
    padding: 0
    line-height: 1.5
```




### Quotation marks

Use double `"` rather than single `'` quotation marks for attribute selectors or property values. Also don’t forget to quote attribute values in selectors.

```sass
// bad
html
    background: #fff url('img/bg.png') repeat 0 0
    font-family: 'open sans', arial, sans-serif

input[type=search]
    margin-left: 1em


// good
html
  background: #fff url("img/bg.png") repeat 0 0
  font-family: "open sans", arial, sans-serif

input[type="search"]
  margin-left: 1em
```






<a name="naming">Naming</a>
------


### Case

**Use only lowercase**. This applies to selectors, properties, and property values. 

```sass
// bad
UL
    color: #EEEEEE
    line-height: 1.5
    
    &:FIRST-CHILD
        padding-top: 20px


// good
ul
    color: #000
    line-height: 1.5
    
    &:first-child
        padding-top: 20px
```




### IDs and Classes

Use meaningful or generic ID and class names. Instead of presentational or cryptic names, always use ID and class names that reflect the purpose of the element in question, or that are otherwise generic. Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change. Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as “helpers”. Using functional or generic names reduces the probability of unnecessary document or template changes.


```sass
// bad

// meaningless
#yee-1901

// presentational
.button-green, .clear


// good

// specific
.gallery, .login, .video 

// generic
.aux, .alt
```

Use ID and class names that are as short as possible but as long as necessary. Try to convey what an ID or class is about while being as brief as possible. Using ID and class names this way contributes to acceptable levels of understandability and code efficiency. Unless necessary, do not use element names in conjunction with IDs.


```sass
// bad

//too long
#navigation

// not descriptive enough
.atr


// good

#nav, .author
```

### Delimiters

Separate words in ID and class names by a hyphen. Do not concatenate words and abbreviations in selectors by any characters (including none at all) other than hyphens, in order to improve understanding and scannability.


```sass
// bad

// not readble
#videoid

// camel instead of hypen
.errorMessage


// good

#video-id, .error-message
```

<a name="imports">Imports and Charset</a>
------------------

SASS imports and charset declarations should always be at the top of each SASS file. Important are used to include variables, mixins, fonts, and other chunks of code that are reusable. 

* `@charset` declaration should always be the first thing. The default charset to be used is UTF-8.
* Variables, fonts, and then mixin declarations should then immediately follow. 
* If the file needs a reset or normalize, that should then follow next. 
* Comments should also be used to describe any other mixins that are not the standard `_variables`, `_fonts`, `_mixins`, or `_reset`
* File extenions should only be used if the extension is not the default `.sass`

```sass
// bad

// imports
@import "_mixins.sass"
@import "_fonts.scss"
@import "_variables.sass"
@import "_reset.sass"
@import "_tips.sass"

@charset "UTF-8"


// good
@charset "UTF-8"

@import "_variables"
@import "_fonts.scss"
@import "_mixins"
@import "_reset"

// global tooltip styles
@import "_tips"
```





<a name="mixins">Mixins</a>
------

Mixins are declared using the `@mixin` declaration. Mixins should be housed in a file called `_mixins.sass`. Mixins are used for code that is frequently repeated through the stylesheets, but may not necessarily correspond to a single element or class. 

* Mixins should follow camel cased formatting
* Mixins should be order alphabetically by their title for organization
* If applicable, provide default settings in the mixin.


```sass
// bad
@mixin button($color)
    background: $color
    display: block
    text-align: center


// good
@mixin button($color: $blue)
    background: $color
    display: block
    text-align: center
```

Mixins are encouraged for multiple vendor prefix properties such as box-shadow, transition, transform, gradient, etc. 

### Fonts

If outside font files are needed, then a separate font file should be created and named `_fonts.scss`. Due some syntax issues, SCSS is acceptable for declaring fonts via `@font-face`. The values assigned in the font-family should be lower case only, dashes if necessary, and then set to a variable in the `_variables.sass` files

```sass
// proxima nova light
@font-face{
    font-family: 'proxima-nova-light';
    src: url('/assets/css/fonts/ProximaNovaLight/ProximaNova-Light-webfont.eot');
    src: url('/assets/css/fonts/ProximaNovaLight/ProximaNova-Light-webfont.eot?#iefix') format('embedded-opentype'),
         url('/assets/css/fonts/ProximaNovaLight/ProximaNova-Light-webfont.woff') format('woff'),
         url('/assets/css/fonts/ProximaNovaLight/ProximaNova-Light-webfont.ttf') format('truetype'),
         url('/assets/css/fonts/ProximaNovaLight/ProximaNova-Light-webfont.svg#proxima_nova_ltlight') format('svg');
    font-weight: normal;
    font-style: normal;
}
```


<a name="variables">Variables</a>
---------


### Declaration

Variables are declared using the `$` notation. Mixins should be housed in a file called `_variables.sass`. Variables are used for common colors, fonts, and numbers used throughout the stylesheets. 

* Variables should follow dashed formatting
* Ensure that variables are not ambiguous and describe the value they hold. 
* Like Variables should be grouped together to help with context and readability.
* Comment each variable or group to document the values. 

```sass
// bad

$red: #ea5b54
$green: #98fe98
$primary: #00853e
$secondary: #008fc5
$bold: "proxima-nova-bold", sans-serif
$regular: "proxima-nova-regular", sans-serif


// good

// error and success colors
$error-red: #ea5b54
$success-green: #98fe98

// brand colors
$primary-green: #00853e
$secondary-blue: #008fc5

// fonts
$proxima-bold: "proxima-nova-bold", sans-serif
$proxima-regular: "proxima-nova-regular", sans-serif
```

### Default Values

Each project should have default variables that are associated with it. These include the following: `font-size`, `font-family`, `line-height`. These values should be set to the body in the global stylesheet. 

```sass
body
    font: normal #{$font-size}/#{$line-height} $proxima-regular
```

### Manipulation

When manipulating a sizing variable in a stylesheet, use +/- modifiers instead of a fixed value. This allows for simple global font changes in the future. 

```sass
// bad
p
    font-size: 16px
    line-height: 1.7


// good
p
    font-size: $font-size + 2
    line-height: $line-height + 0.2
```


<a name="comments">Comments</a>
--------
Well commented code is extremely important. Take time to describe components, how they work, their limitations, and the way they are constructed. Don't leave others in the team guessing as to the purpose of uncommon or non-obvious code.

Comment style should be simple and consistent within a single code base.

* Place comments on a new line directly above their subject
* Comments should have a space directly after the `//`
* Align comments with the selectors they pertain to
* Use terse comments that convey ideas
* Comment major code ideas
* Comments on every selector is unnecessary

```sass
// bad

// too far away

h1
    color: #000
    

/*
    Improper use
    of the multiline
*/

section
    padding: 0


// good

// basic comment
h1
    color: #000

// Block of comments that
// pertain to the section
// below and other things
// and maintain spacing
section
    padding: 0
```
