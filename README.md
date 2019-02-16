#Getting started.
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

Sass versus SCSS

I've seen both from YOutube videos. It seems Sass is preffered for it's ease of use. The first video I watched displayed SCSS so I am tempted to be biased toward it.


 **the clippy tool**
bennettfeely.com/clippy
Helps create clip paths for polygons


#Nesting
See the body and #bg


Check out the `<main>` and `<span>` elements 


#Sass Functions

map-get($colors, primary); is not pretty.

make a function with @function


Using specific names for classes

#CSS Functions
Use the lighten() function to get a lighter version of a color.
lighten (color, %)


#Responsive Design

You might need to change the clippy design


#Mixins

Questions you may ask yourself: when do I have room for two columns?

Definie some screen sizes like:
`$desktop: 840px;`

include @mixins in **"rulesets"** by doing:
```@include desktop { }`

remember `line-height` brings things closer together. default value is 1. Set it at .9]


#The @s // directives
@mixin
@media
@content
@function
@extend
@include
@return


#Sass partials
Modularize the codes by using @imports on pieces of. 
The name of the documents must use an _ in order to begin. `

A partial is any file with an underscore _ preceding the name. When Sass sees these files, it will not process them into CSS files. A partial requires that it be imported into another file that will inevitability be processed into CSS in order for it to be output.

