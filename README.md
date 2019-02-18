<!-- ############################################################################# -->
# **Sass: Syntactically Awesome Style Sheets**
<!-- ############################################################################# -->

This Github has both a Sass and an Scss file.

Historically, Sass is derived from HAML's creators which sought to simplify HTML syntax. Sass 3 was released at beta in 2010.

The SCSS syntax was built from the ground up and can do anything Sass can do. SCSS can import Sass files and vice versa. Sass whitespace syntax and the SCSS syntax cannot live in the same file. That is it's only limitation to cooperatibilty.

# Sources

 1. [Sass in the real World](https://anotheruiguy.gitbooks.io/sassintherealworld_book-i/index.html)
 2. [Sass Documentation](https://sass-lang.com/guide)
 3. [OOCSS](https://www.youtube.com/watch?v=SqfhZk0eIdE)


<!-- ############################################################################# -->
# Sass versus SCSS
<!-- ############################################################################# -->

**1.**

|  |   Advantage    |   Disadvantage  |
|   ---    |   ---  |   ---   |
|   Sass            |   less characters |   CSS conversion required |
|   SCSS            |   no conversion required  |   Curly brackets and semi colons |


I've seen both from Youtube videos. It seems Sass is preffered for it's ease of use. The first video I watched displayed SCSS so I am tempted to be biased toward it. But SCSS is technically "newer".


SCSS seems advantageous for newcomers just because it's more familiar. Sass seems like something you get to later on because the syntax makes more sense naturally.

Leveraging the fact that .sass files can live harmoniously with .scss files, some developers have adopted a workflow of, using SCSS for all logic (mixins, extends and functions) and then using Sass for the CSS styling. Sass relies on less key strokes and quick tabs for writing code and it is easier to change selectors with identation versus refining by moving around curly brackets.

Using curly brackets are believed to assist in a developer's ability  to see logical code groupings.

**2.**
Note: CSS writing styles include `expanded`, `nested`, and `compact`

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

Good example of compact classes legacy CSS
 ```.block div { border: 1px solid black; }
.block div ul { width: 100%; float: left; }
.block div ul li { float: left; width: 100%; background: orange; }
.block div ul li p { font-weight: bold; line-height: 1.5em; }
 ```





 

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


Mixins require dashes - or underscores _


# The @s // directives

| Directive | Does |
| --- | --- |
| `@mixin` | enables you to import parameters to a pre-built CSS function for easy modularity |
| `@media` | ??? |
| `@content` | ??? |
| `@function` | define a function |
| `@extend` | import another prebuilt file into the next file. USeful for switching around contents of SCSS and Sass files. |
| `@include` | ??? |
| `@return` | ??? |

# Sass Partials

**Partials, Manifests, and Globbing**

Modularize the codes by using @imports on pieces of. 
The name of the documents must use an _ in order to begin. `

A partial is any file with an underscore _ preceding the name. When Sass sees these files, it will not process them into CSS files. A partial requires that it be imported into another file that will inevitability be processed into CSS in order for it to be output.

It is ideal to break your cod e into smaller chunks called partials. Globbing and manifests are partials techniques.

If you had `main.sass` // this *manifest file* would output to the css. It would pull from _reset.sass and _variables.scss partials.


You could have a core manifest Sass stylesheet and then two other device manifest files.
- `application.sass`
- `mobile.sass`
- `tablet.sass`

Use `@import` directive to load the partials within a single document when you're outputing to CSS from the core manifest. Order matters.

Therefore import all "logical Sass" first. Load the 1. global variables 2. functions then 3. mixins

**Globbing**

Assemble files alphabetically.
It might only be available in Rails.
It seems kinda extra as it will break functionality if not loaded correctly.
It only does away with sub-directory partials, and it may not be worth it.


**Architecture**

// 1.
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

//2. 
Furthermore use additional manifests within sub directories. For example a `stylesheets/_mixins/`

stylesheets/
|-- application.sass        // Sass manifest file
|
|-- _reset.sass             // Partials
|-- _variables.scss                 |
|-- _functions.scss                 |
|-- _base.sass                      |
|-- _layout.sass                    |
|-- _module.sass                    |
|-- _state.sass                     |
|-- _theme.sass             // Partials
|
|-- _mixins/                // Directory
|  |-- _manifest.scss
|  |-- _grid_calc.scss
|  |-- _arrow_tooltip.scss

Above, a single mixins file was divided into three files within a subdirectory, particularly _manifest.scss


 **Question: why make some files the .sass and others the .scss?**
 
 Answered above. Sass is for style SCSS is for logic.
 
 # Rules to live by
 
 The Object Oriented CSS (OOCSS) CSS semantic concepts are considered a foundation for Sass. Reduce bloat. Reduce dependence of the !important tag. Create global styles.
 
- **Separation of structure and skin.**
    - Define repeating visual patterns as reusable skins. `background-color`
    - Define repeating invisible patterns as reusable structures. `border-radius`, `padding`
    
    Define original object with structures. Define visual patterns in resulting classes.

- **Separation of container and content.**
    - objects shoud look the same wherever. Don't have location-dependent styles.
    - try to have reusable styles. Don't make a class that is too broad that it can't be reused.
    - you can do this by separating fonts by different use cases.

*idk what this is but it sounds smart*
1. Take Repeating Patterns --> `#container h2` `#footer h2`
2. Create CSS objects --> `.container` `body`
3. Make Polymorphic objects --> `.container > head` `.container > .content` 

**this is better**
 1. Modules with states: `.btn`, `.btn-primary`, `.btn-disabled`
 2. Uses classes versus IDs versus Element Selectors.
 3. Naming Conventions for classes: Semantic `.content`, `.news__title` (classes based on individual use cases) vs Presentational `.grid__col-9`, `btn--small` (classes based on sizes)
 
 
 Naming:
 - object `.media`
 - parent-child relationships `.media__image`, `.media__body`
 - modifers and states `.media--inline`, `.media--collapsed`, `.media--img-right`
 
 
 
 
 # Sass code libraries
 
 
 
 
 # Random Notes
 
  ----------
 **formating tables**

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

 ----------
 **comments** 
 
 put comments at a fixed indent from each line instead of overtop a line. You'd not want wrap on tho... but short comments would look best see this
 
  ```.block {                /* .block opening bracket */
    div {                 /* div opening bracket */
      border: 1px solid black;
      ul {                /* ul opening bracket */
        width: 100%;
        float: left;
        li {              /* li opening bracket */
          float: left;
          width: 100%;
          background: orange;
          p {             /* p opening bracket */
            font-weight: bold;
            line-height: 1.5em;
          }               /* p closing bracket */
        }                 /* li closing bracket */
      }                   /* ul closing bracket */
    }                     /* div closing bracket */
  }                       /* .block closing bracket */
  ```
  
   ----------

camelCase versus PascalCase
