## Sass/Less and Preprocessing

### CSS Preprocessing tools

#### CSS Preprocessing

preprocessors are programs that offer the variables missing in CSS. They were created to organize CSS via neseted definitions and maintain.

They take code that you have written in the preprocessed language and converts into simple CSS code. 

Two popular CSS preprocessors are SASS (Syntactically Awesome Stylesheets) and Less (Leaner CSS). Newer syntax of SASS known as SCSS (Sassy CSS)

##### Variables

Containers that store the information you will reference and manipulate.
Examples of variables : color, width, font-size, font-family, and borders.
``` SCSS
// Variable example in SCSS
$primary-background-color: #666666;
```

##### Nesting
If website's CSS is structured properly then may need to use many class or ID selectors. 
Instead you can apply nesting. Specify properties to selectors within other selectors. 
``` SCSS
// Nesting Example in SCSS
.button {
    .span {
        font-weight: bold;
    }
    &:hover {
        background: $primary-background-color;
    }
}
```

##### Mixins
Allows you to define common properties once, and then reuse them throughout the rest of your CSS.  
Example: Using Mixin to write cross-browser background gradients or CSS arrows.
```SCSS
// Mixin Example in SCSS
@mixin title ($color, $size) {
    color: $color;
    cont-size: $size;
}

// Add Mixin SCSS Example
.title-page {
    @include title(gray, 2.5rem);
}
```

#### Sass/SCSS and Less

Sass uses CSS-compatible, indented syntax to provide customized, well-formatted output. 
``` Sass
// Sass
    * Indentation rather than brackets to indicate nesting of selectors
    * New lines rather than semi-colons to separate properties
    * .Sass extension

$text-color: #333333;
body 
    color: $text-color
```
``` SCSS
/* SCSS
    * Extension of CSS, hence every valid CSS is a valid SCSS file with same meaning.
    * .SCSS extension 
*/

$text-color: #333333;
body {
    color: $text-color;
}
```

##### Working with Sass/SCSS files : 
Uisng CLI :  
1. Install ruby  
2. `gem install sass` to install Sass

**Basic Sass Commands**  
1. To check Sass version : `sass -v`
2. Compile a `.scss` file into `.css` file : `sass input.scss output.css`
3. `sass --watch input.scss:output.css`, watch a .scss file for changes then create
4. `sass-convert style.sass style.scss`
5. `sass-convert style.scss style.sass`

##### Less
Less is written in JavaScript so it runs inside NodeJs, in the browser, and inside Rhino. 

**Syntax differences from Sass**  
``` Less
// Less Variable
@link-color: blue;

// Less Mixin for rounding borders
.round-borders (@radius) {
    border-radius: @radius;
}

// Add the round-borders mixin with Less
.box { round-border(0.54rem); }
```

**Using Less** : `npm install -g Less`  
**Less Compiler**
Need to setup a compiler. 

```Less
// Sample Less code
@color-base: #2d5e8b;
.class1 {
    background-color: @color-base;
    .class2 {
        background-color: #fff;
        color: @color-base;
    }
}

// Which gets converted by compiler to 
.class1 {
    background-color: #2d5e8b;
}
.class1 .class2 {
    background-color: #fff;
    color: #2d5e8b;
}
```

#### Getting Started with Sass/SCSS

**Usage Methods**
We can use task runners like `Gulp` or `Grunt` to manage or Sass or Less files. 
Installation from Node : `npm install node-sass`

**Tool Applications**
Usign GUI
* CodeKit : https://www.incident57.com/codekit
* Compass.app : http://compass.kkbox.com/
* GhostLab : https://www.vanamco.com/ghostLab/
* Hammer : http://riothq.com/hammer.html
* Koala : http://www.koala-app.com/ 
* LiveReload : http://livereload.com/
* Prepros : https://prepros.io/
* Scout : https://mhs.github.io/scout-app/

**File and Folder Structure**  
Directory where your Sass/SCSS files live is called the input folder. Your processed CSS files are saved to the output folder. A typical pattern : 
```
myproject
|   index.html
|___css
|      main_style.css
|___scss
    |   main_style.scss
    |   _mixins.scss
    |   _colors.scss
```

#### Sass Features in Depth

To try it out : https://www.sassmeister.com/

**Ampersand**
```SCSS
// SCSS
/* Prepending & in a nested Sass selector, that selector becomes
   attached to the parent selector, instead of being nested below it
 */
.parent {
    &:before {...}
}
```
```CSS
/* CSS */
.parent:before {...}
```
**Combinatorial Explosion**
```SCSS
/*SCSS*/
p {
    + p {
        margin-top: 16px;
    }
}

/*CSS*/
p + p {
    margin-top: 16px;
}
```

**Extend/Inheritance**
```SCSS
// Container Rules
.container {
    max-width: 1024px;
    padding: 0 15px;
    margin : 0 auto;
}

// Container 2 Rules
.container-2 {
    @extend .container;
    padding: 0 45px;
}
```
**Import**  
**Nesting**  
**Mixin**  
**Operations**  
**Parent Reference/Pseudo Class**  
**Parent Selector**  
**Partial**  
**Placeholder Selector**  
**Root Directive**  
