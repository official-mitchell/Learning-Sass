<!-- ############################################################################# -->
# **Sass: Syntactically Awesome Style Sheets**
<!-- ############################################################################# -->

For yee fare wonderer who stumbles upon thi Github, this resource serves as my walkthrough learning Sass/SCSS. You make Sass files for the styles and make SCSS files for the logic structure. Focus on OOCSS for reusable structures and skins. Create a number of partials to divide the structure of your CSS.

Historically, Sass is derived from HAML's creators which sought to simplify HTML syntax. Sass 3 was released at beta in 2010.

The SCSS syntax was built from the ground up and can do anything Sass can do. SCSS can import Sass files and vice versa. Sass whitespace syntax and the SCSS syntax cannot live in the same file. That is it's only limitation to full conversion.

I just got here from completing CSS basic and intermediate, learning the first half of the CSS framework bootstrap. My next step is to learn Gulp and Sass libraries as well as improve my JS skills for jQuery, although I feel there are better modern alternatives.


To Get started
- If you weren't using the Live Scss compiler you'd go into terminal: and type  `sass input.css output.css`
- To "watch" instead of "manually build" you'd: `sass --watch input.scss output.scss`
- I'm using live sass compiler and live server in VS Code.
- You'll want to use the Dart 1.0 version of Sass that you install with Homebrew not the Ruby version (which is having work stopped in March 2019)


**Ongoing Questions**
- what is a CSS reset? Why use _reset.scss



# Sources

 1. [Sass in the real World. 100% the best resource](https://anotheruiguy.gitbooks.io/sassintherealworld_book-i/index.html)
 2. [Sass Documentation](https://sass-lang.com/guide)
 3. [OOCSS](https://www.youtube.com/watch?v=SqfhZk0eIdE)
 4. [Comparison artcle from 2011](http://thesassway.com/editorial/sass-vs-scss-which-syntax-is-better#reason_1_scss_is_more_expressive)
 5. [Ruby Sass will cease to be developed](https://css-tricks.com/ruby-sass-to-be-put-to-pasture-on-march-26-2019/)

Also:
- [CSS Selectors Review](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)


<!-- ############################################################################# -->
# Sass versus SCSS
<!-- ############################################################################# -->

 ----------
 **1.**
 

|  |   Advantage    |   Disadvantage  |
|   ---    |   ---  |   ---   |
|   Sass            |   less characters |   CSS conversion required |
|   SCSS            |   no conversion required  |   Curly brackets and semi colons |


I've seen both from Youtube videos. It seems Sass is preffered for it's ease of use. The first video I watched displayed SCSS so I am tempted to be biased toward it. But SCSS is technically "newer".


SCSS seems advantageous for newcomers just because it's more familiar. Sass seems like something you get to later on because the syntax makes more sense naturally.

Leveraging the fact that .sass files can live harmoniously with .scss files, some developers have adopted a workflow of, using SCSS for all logic (mixins, extends and functions) and then using Sass for the CSS styling. Sass relies on less key strokes and quick tabs for writing code and it is easier to change selectors with identation versus refining by moving around curly brackets.

Using curly brackets are believed to assist in a developer's ability  to see logical code groupings.

 ----------
 
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

# Language


 ----------
 
**Nesting**
See the body and #bg


Check out the `<main>` and `<span>` elements 



 ----------
**Sass Functions**

map-get($colors, primary); is not pretty.

make a function with @function


Using specific names for classes



 ----------
**Imports**

import _reset.scss into base.scss
```
// _reset.scss

html,
body,
ul,
ol {
  margin:  0;
  padding: 0;
}
```
notice that you can import just "reset" not "_reset"
```
// base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

 ----------
 
**Extending**

You can create placeholders. Use `%` signs like in `%name-here` to create CSS that can be generated upon it's extension. `%message-shared` is generated due to its extension in placeholder classes like mesage, success, error, and warning.

SCSS
```
/* This CSS will print because %message-shared is extended. */
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

// This CSS won't print because %equal-heights is never extended.
%equal-heights {
  display: flex;
  flex-wrap: wrap;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}

.error {
  @extend %message-shared;
  border-color: red;
}

.warning {
  @extend %message-shared;
  border-color: yellow;
}
```

CSS
```
/* This CSS will print because %message-shared is extended. */
.message, .success, .error, .warning {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```

The CSS receives a makeover as a few classes share the same qualities but adjust throughout the page.


 ----------
 
**Operators**

Use like `+, -, *, /, and %` for calculating widths and heights. For example:

SCSS
```
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```

CSS output results in "main" width's as 62.5% and complementary's width as 31.25%.







# CSS Functions
Use the lighten() function to get a lighter version of a color.
lighten (color, %)


# Responsive Design

You might need to change the clippy design



 ----------

**Mixins**

You'll probably use SCSS to describe these premade groupings of CSS declarations for reuse.

- Questions you may ask yourself: when do I have room for two columns?
- Define some screen sizes like:
    - `$desktop: 840px;`
- include @mixins in **"rulesets"** by doing:
    - ```@include desktop { }`


remember `line-height` brings things closer together. default value is 1. Set it at .9]


*Mixins require dashes - or underscores _* **not sure on this...**

SCSS
```
@mixin transform($property) {
  -webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}

.box { @include transform(rotate(30deg)); }
```

leads to CSS
```
.box {
  -webkit-transform: rotate(30deg);
  -ms-transform: rotate(30deg);
  transform: rotate(30deg);
}
```

This example enables multiple transformations (in webkit ms and normal) with the `rotate(30deg)` property.








**The @s "Directives"**

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

``` 
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
```

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
 
 
 # CSS Objects with OOCSS

| "A CSS object consists of four things: HTML, which can be one or more nodes of the DOM, CSS declarations about the style of those nodes all of which begin with the class name of the wrapper node Components like background images and sprites required for display, and JavaScript behaviors, listeners, or methods associated with the object."
 
 
 **Example 1**
 
 ```
 /* The font-family, which is usually applied on the entire site, is applied at the body. */
body {
  font-family: Verdana, Arial, sans-serif;
}

/* The <h2> element has CSS rules that will be applied anywhere the element is used. */
h2 {
  font-size: 2em;
  line-height: 1em;
}

/* The new semantic class .section-header reduces the font-size and increases margin-left and margin-right. This new selector can be applied anywhere, including the footer, which will override the <h2> base element rules. */
.section-header {
  font-size: 1.5em;
  margin: 0.25em 0.5em;
  color: #CFC35D;
}
 ```
 
 `body` takes `font-family`, types like `h2` take CSS rules applied across the whole page, semantic classes adjust for each section to override type base element rules. 
 
  ----------
  
 
 
 **Example 2**
 
 ```
 a {
  color: blue;
}

.footer-link {
  color: #ccc;
}
 ```
 
 Allow default styles from type selectors and create styles to override and apply needed changes.
 Type selectors by default should be reusable. Style semantically for specific case-by-case use.
 
 
 **Example 3: Non-Bootstrap Spacing classes for Reuse**
 
 ```
 /**
 * Spacing classes
 * Should be used to modify the default
 * spacing between objects (not between nodes of the same
 * object)
 * Please use judiciously. You want to be
 * using defaults most of the time, these are
 * exceptions!
 * <type><location><size>
 */
/* spacing helpers
p,m = padding,margin
a,t,r,b,l,h,v = all,top,right,bottom,left,
horizontal,vertical
s,m,l,n = small(5px),medium(10px),large(20px),none(0px)
*/
.ptn,.pvn,.pan{padding-top:0px !important}
.pts,.pvs,.pas{padding-top:5px !important}
.ptm,.pvm,.pam{padding-top:10px !important}
.ptl,.pvl,.pal{padding-top:20px !important}
.prn,.phn,.pan{padding-right:0px !important}
.prs,.phs,.pas{padding-right:5px !important}
.prm,.phm,.pam{padding-right:10px !important}
.prl,.phl,.pal{padding-right:20px !important}
.pbn,.pvn,.pan{padding-bottom:0px !important}
.pbs,.pvs,.pas{padding-bottom:5px !important}
.pbm,.pvm,.pam{padding-bottom:10px !important}
.pbl,.pvl,.pal{padding-bottom:20px !important}
.pln,.phn,.pan{padding-left:0px !important}
.pls,.phs,.pas{padding-left:5px !important}
.plm,.phm,.pam{padding-left:10px !important}
.pll,.phl,.pal{padding-left:20px !important}
.mtn,.mvn,.man{margin-top:0px !important}
.mts,.mvs,.mas{margin-top:5px !important}
.mtm,.mvm,.mam{margin-top:10px !important}
.mtl,.mvl,.mal{margin-top:20px !important}
.mrn,.mhn,.man{margin-right:0px !important}
.mrs,.mhs,.mas{margin-right:5px !important}
.mrm,.mhm,.mam{margin-right:10px !important}
.mrl,.mhl,.mal{margin-right:20px !important}
.mbn,.mvn,.man{margin-bottom:0px !important}
.mbs,.mvs,.mas{margin-bottom:5px !important}
.mbm,.mvm,.mam{margin-bottom:10px !important}
.mbl,.mvl,.mal{margin-bottom:20px !important}
.mln,.mhn,.man{margin-left:0px !important}
.mls,.mhs,.mas{margin-left:5px !important}
.mlm,.mhm,.mam{margin-left:10px !important}
.mll,.mhl,.mal{margin-left:20px !important}
.mra,.mha{margin-right:auto !important}
.mla,.mha{margin-left:auto !important}
 ```
 
`padding-top-small`
 
 ----------
 
**Example 4: Default container class in tandem with child selectors**

```
.container {
  background: transparent;
  padding: 5px;
  box-sizing: border-box;
  width: 100%;
  height: auto;
  overflow: auto;
}
```

Use a default `.container` class.

Use 


 
 
 # Sass code libraries
 
 
 
 
 
 # Live Example
 
 1) Colors
 ```
You can start off with a $ colors: ( 
    to have multiple colors in here
        `primary: ######,`
        `accent: ######,`
)
```


2) Clippy tool
 **the clippy tool**
bennettfeely.com/clippy
Helps create clip paths for polygons

 
 
 
 
  ----------
  
 
 
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


**Selectors Reminders**

`A > B` is selecting a child selector. This is popular with things like:
- `ul > li` for unordered list elements
- `container > h1` header1 fonts inside of containers...

`.container card` is a descendant selector.

**Psuedo-classes**
State information selection `
