Grasshopper SASS Style Guide
============================

*A guide to developing stylesheets in SASS*

Table of Contents
-----------------
    
1. Mixins
2. Variables





Mixins
------

Mixins are declared using the `@mixin` declaration. Mixins are used for code that is frequently repeated through the stylesheets, but may not necessarily correspond to a single element or class. 

* Mixins should be housed in a file called `_mixins.sass`.
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
