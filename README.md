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


Variables
---------

Variables are declared using the `$` notation. Variables are used for common colors, fonts, and numbers throughout the stylesheets. When naming these files ensure that variables are not ambiguous and describe the value they hold. Like Variables should be grouped together to help with context and readability. Make sure to comment each variable or group to document the values. 

**Good**

```
// error and success colors
$errorRed: #ea5b54
$successGreen: #98fe98

// brand colors
$primaryGreen: #00853e
$secondaryBlue: #008fc5


```

**Bad**
```
// error and brand colors
$red: #ea5b54
$green: #98fe98
$primary: #00853e
$secondary: #008fc5
```












Dillinger is a cloud-enabled HTML5 Markdown editor.

  - Type some Markdown text in the left window
  - See the HTML in the right
  - Magic

Markdown is a lightweight markup language based on the formatting conventions that people naturally use in email.  As [John Gruber] writes on the [Markdown site] [1]:

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable 
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually* written in Markdown! To get a feel for Markdown's syntax, type some text into the left window and watch the results in the right.  

Version
----

2.0

Tech
-----------

Dillinger uses a number of open source projects to work properly:

* [Ace Editor] - awesome web-based text editor
* [Marked] - a super fast port of Markdown to JavaScript
* [Twitter Bootstrap] - great UI boilerplate for modern web apps
* [node.js] - evented I/O for the backend
* [Express] - fast node.js network app framework [@tjholowaychuk]
* [keymaster.js] - awesome keyboard handler lib by [@thomasfuchs]
* [jQuery] - duh 

Installation
--------------

```sh
git clone [git-repo-url] dillinger
cd dillinger
npm i -d
mkdir -p public/files/{md,html,pdf}
```

##### Configure Plugins. Instructions in following README.md files

* plugins/dropbox/README.md
* plugins/github/README.md
* plugins/googledrive/README.md

```sh
node app
```


License
----

MIT


**Free Software, Hell Yeah!**

[john gruber]:http://daringfireball.net/
[@thomasfuchs]:http://twitter.com/thomasfuchs
[1]:http://daringfireball.net/projects/markdown/
[marked]:https://github.com/chjj/marked
[Ace Editor]:http://ace.ajax.org
[node.js]:http://nodejs.org
[Twitter Bootstrap]:http://twitter.github.com/bootstrap/
[keymaster.js]:https://github.com/madrobby/keymaster
[jQuery]:http://jquery.com
[@tjholowaychuk]:http://twitter.com/tjholowaychuk
[express]:http://expressjs.com

    
