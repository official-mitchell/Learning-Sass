# **Sass: Syntactically Awesome Style Sheets**

Historically, Sass is derived from HAML's creators which sought to simplify HTML syntax. Sass 3 was released at beta in 2010.

The SCSS syntax was built from the ground up and can do anything Sass can do. SCSS can import Sass files and vice versa. Sass whitespace syntax and the SCSS syntax cannot live in the same file. That is it's only limitation to cooperatibilty.

# Sass versus SCSS

|  |   Advantage    |   Disadvantage  |
|   ---    |   ---  |   ---   |
|   Sass            |   less characters |   CSS conversion required |
|   SCSS            |   no conversion required  |   Curly brackets and semi colons |


I've seen both from Youtube videos. It seems Sass is preffered for it's ease of use. The first video I watched displayed SCSS so I am tempted to be biased toward it. But SCSS is technically "newer".


 ```// note: this table didn't work
| **Side by Side Look**                                                            |
|   ----------      |   Advantage               |   Disadvantage                   |
|   ----------      |   ----------              |   ----------                     |
|   Sass            |   less characters         |   CSS conversion required        |
|   SCSS            |   no conversion required  |   Curly brackets and semi colons |
 ```



 




```
| Command | Description |
| --- | --- |
| git status | List all new or modified files |
| git diff | Show file differences that haven't been staged |
```



SCSS seems advantageous for newcomers just because it's more familiar. Sass seems like something you get to later on because the syntax makes more sense naturally.

// Note: CSS writing styles include `expanded`, `nested`, and `compact`

``` 
// Expanded
header {
  width: $header-width;
  height: $header-height;
}

// Nested
header .nav {
  text-decoration: none;
  background: $background-color;
  color: $text-color;
  border-radius: $default-radius $default-radius 0 0; }

// Compact
header .nav p { font-weight: bold; }
```





# Sources

 1. [Sass in the real World](https://anotheruiguy.gitbooks.io/sassintherealworld_book-i/index.html)
 2. [Sass Documentation](https://sass-lang.com/guide)
 3. 
 

# Getting started.
Got here from completing CSS basic and intermediate, CSS framework bootstrap (1/2).
Next steps: Gulp.


If you weren't using the Live Scss compiler you'd go into terminal
       ` sass input.css output.css`

To "watch" instead of "manually build" you'd
    `sass --watch input.scss output.scss`


```You can start off with a $ colors: ( 
    to have multiple colors in here
        `primary: ######,`
        `accent: ######,`
)
```




 **the clippy tool**
bennettfeely.com/clippy
Helps create clip paths for polygons


# Nesting
See the body and #bg


Check out the `<main>` and `<span>` elements 


# Sass Functions

map-get($colors, primary); is not pretty.

make a function with @function


Using specific names for classes

# CSS Functions
Use the lighten() function to get a lighter version of a color.
lighten (color, %)


# Responsive Design

You might need to change the clippy design


# Mixins

Questions you may ask yourself: when do I have room for two columns?

Definie some screen sizes like:
`$desktop: 840px;`

include @mixins in **"rulesets"** by doing:
```@include desktop { }`

remember `line-height` brings things closer together. default value is 1. Set it at .9]


# The @s // directives
@mixin
@media
@content
@function
@extend
@include
@return


# Sass Partials
Modularize the codes by using @imports on pieces of. 
The name of the documents must use an _ in order to begin. `

A partial is any file with an underscore _ preceding the name. When Sass sees these files, it will not process them into CSS files. A partial requires that it be imported into another file that will inevitability be processed into CSS in order for it to be output.

**Architecture**
Say within:

*assets/css/*

you had the following...
- _reset.sass
- _variables.scss
- _functions.scss
- _mixins.scss
- _base.sass 
- _layout.sass
- _module.sass
- _state.sass
- _theme.sass  

 **Question: why make some files the .sass and others the .scss?**