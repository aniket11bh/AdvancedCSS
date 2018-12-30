## CSS Modules and High Fidelity Designs

### What is Modular CSS ?

In Context of CSS, Modular CSS describes a consistent apporach for creating CSS that is broken down into smaller parts. 

There are similiar approaches where what we are referring to as Modules are also sometimes called Components, Objects, or Web Parts. CSS modules are crafted based on a set of guidelines to create a collection of re-usable building blocks.

#### Modular CSS is : 
* A guideline based approach for breaking down pages into generic usable CSS code.
* Based on classes and consistent naming conventions.
* Easy to read and maintain by teams.

#### CSS Modules are : 
* Generic, self-contained, and reusable.
* Modifiable, combinable, and scalable.
* Can contain or be contained by other modules but stay independent.

#### Some common modules : 
.nav, .search, .logo, .breadcrumbs, .title, .icon, .media-object, .list, .frame, .slider, .card etc.  
.nav may represent the elements on the page that form the navigational menu.

``` CSS
/* Module "does not" look like  */
/* because by modular css guidelines, the button should be independent and not coupled to .content-area */
/* We want .btn to have same visual appearance no matter where it is located */
.content-area .btn {
    // style rules
}

/* Button module, how does it look like */
.btn {
    padding: .5em 1em;
    text-decoration: none;
    border: 1px gray solid;
    display: inline-block; //help anchors and other inline elements
}
```

``` html
<!-- using basic button module from above -->
<div class="btn"> Button Text </div>
<a class="btn"> Button Text </a>
<button class="btn"> Button Text </button>
```
```CSS
/* To create variation we need for .content-area, we can create sub-module */
/* Button Sub module */
.btn-content {
    background: blue;
    color: white;
}
```

```html
<!-- Both class applied -->
<button class="btn btn-content"> Button </button>
```
#### Basic Guiding Principals:

* Turn visual design into it’s underrating layout structure.
* Breakdown page sections into smaller parts that can act on their own.
* Organize your code so it is consistent.
* Make code that allows for change and growth.
* Create code that is reusable and efficient.


### General Modular guidelines : 

* **OOCSS** : object oriented CSS (http://oocss.org)
* **SMACSS** : Scalable and Modular Architecture for CSS (https://smacss.com/)
    * Base
    * Layout: Divides web page into sections. They hold one or more modules together.
    * Module: They sit inside layout components, and can sit within other modules as well
    * State: Defines how modules/layouts will look in a particular state (hidden, expanded, active, inactive) like bigger, smaller, in different views etc.
    * Theme: Act similiarly to state rules, describe how modules/layout might appear.
* **BEM** : Block, Element, Modifier (http://getbem.com) Uses the word block instead of moudle
* **DRY** : Don't Repeat Yourself CSS. Different than above three because it modifies a module in CSS not with a modifier class in the HTML. 
``` CSS
/* DRY Blue background */
/* In this, you don't add the class .background-blue in the HTML, use comma separted classes that you want to add to that rule base */
.background-blue,
.header-primary,
.footer-primary {
    background: blue;
}
```
#### Example of Modules using Icon Fonts :
Since icon fonts are vector and resolution independent, they are versatile and easy to read on various devices.

A populate set of icon fonts is Font Awesome (http://fontawesome.io/) essentially a font face together with CSS rules.  
Adding them follows modular pattern. They use `class .fa` as its base icon style, other icon sets might use the `class .icon`

``` html
<i class="fa"></i>

<!-- In Font Awesome, there is not a default icon, so need to modify this icon with the type of icon to display -->

<i class="fa fa-thumbs-up"></i>
<i class="fa fa-thumbs-up fa-4x"></i> <!-- Making it 4 times bigger -->
<i class="fa fa-thumbs-up fa-4x fa-spin"></i> <!--Animate it -->
<button class="btn"><i class="fa fa-thumbs-up"></i> Like </button> <!-- Nested modules -->
<button class="btn btn-primary"><i class="fa fa-thumbs-up"></i> Like </button> <!-- Mdifier for .btn to add more style rules-->
```

### Advanced Positioning with CSS

#### Layout and Advanced positioning for Modules

It's always helpful to separate layout and positioning from the module. As modules are reused througout the web site they often have different external/internal layouts. And often get more complicated when we start using media queries. 

##### Abstracting layout : 
We don't want mix the layout or position rules with a module itself. Therefore need to create a new layout or position module. Grid system is great example of layout module by using .container, .row, .col we have abstracted the layout and allowed a place for any module we want inside. 

``` CSS
/* The logo in the header is on the left side of the screen and right in the footer */
.logo {
    display: inline-block;
    font-family: georgia;
    float: left;
}

/* But in this attempt, always floating the logo to the left we introduce a rule that the logo in the footer have to override. So instead pull the layout rule from the module and create layout modules instead  */
Remove float left from .logo
.pull-left {
    float:left;
}
.pull-right {
    float:right;
}
```

```html
<header>
    <div class="pull-left">
        <div class="logo">Logo </div>
    </div>
</header>
```

##### Abstracting Position : 
Relative positioned modules are essentially static untill a property is applied. By using top, left, right, and bottom you can move the module relatively to where it was first rendered by the browser.  
By adding `top: -30px;` it will move the module up by 30px, other modules and elements in the flow will not be changed by the shift of the relative module. 

Absolute positioned module will offset itself from the edge of a surrouding container which is positioned either relative or absolute itself. When a module is absolute it acts like a layer and does not affect any other module in the visual flow, this is just like a relative module. Use the z-index property to stack absolute modules on top of other relative and absolute modules.

```html
<!-- Model HTML for simple popup modal -->
<!-- In the header of the modal, we need a title and a close button -->

<div class=“model”>
    <div class=“modal-header”>
        <h5 class=“modal-header__title”>Hello World</h5>
        <div class=“modal-header__btn-wrap”>
            <button class="btn"><i class=“fa fa-close“></i> close</button>
        </div>
    </div>

    <div class=“modal-body”>…</div>
    <div class=“modal-footer”>…</div>

</div>

<!-- By using div with the class .modal-header__btn-wrap, we have a place to abstract the positioning rules to. This avoids using .modal-header > .btn to position the close button-->
```
```CSS
/* Position Close button wrapper */
.modal-header__btn-wrap {
    position: absolute;
    top: 0.75rem;
    right: 0.75rem;
}
.modal-header {
    position: relative; // This is the container for modal-header__btn-wrap
}
/* Now, we can swap the close button for a different button without breaking the design or needing to position the new button */
```

### Build the Base Button Module

### Build Mobile Header, logo and navigation

#### Base Button CSS Module
Design mobile first, add the basic button style settings to button module. 
Refer to http://pxtoem.com/ to convert font sizes from style guide into web friendly units.

CSS Transitions at : https://www.w3schools.com/css/css3_transitions.asp

#### Create and Style Header Wrapper 

#### Create and Style Navigation for Extra Small Devices

### Build the Hero Section and Background Image

#### Create Hero and Hero Primary modules
#### Create and Style the Hero Text Content
#### Create Hero Background Image Module

### Build a Media Object that includes an Icon Font

#### Create an HTML template for Media Objects
#### Add Font Awesome icon Font
#### Style your Media Object



