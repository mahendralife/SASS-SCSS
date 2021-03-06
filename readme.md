# How to step a project with SCSS 
<b>Follow below steps</b>
<ul>
<li> Create project directory (eg mkdir project_name)</li>
<li> Navigate to project folder (eg. cd poject_name)</li>
</ul>

# Install sass on local machine
npm install -g sass

<b>Generate SCSS to css file</b>
The below commond always watch your SCSS file if any changes are made by SCSS file 
CSS file will automatically updated,  run the below   

sass --watch base.scss ./output/output.css
<ul>
<li>base.scss : main file of SCSS which is import all scss file</li>
<li>output.css : this is css file include all css code that you write on scss file</li>
<li>--watch : commond always LISTEN changes for SCSS file</li>
<li>Referencing Parent Selectors: & </li>
</ul>

```
a {
  font-weight: bold;
  text-decoration: none;
  &:hover { text-decoration: underline; }
  body.firefox & { font-weight: normal; }
}
```
# Nested Properties 
```
  .alert {
    color: black; 
    .alert-success {
      border: 1px solid; 
    }
  }
 ```
# SASS Directive
# @import 
If you have a SCSS or Sass file that you want to import but don't want to compile to a CSS file, you can add an underscore to the beginning of the filename. This will tell Sass not to compile it to a normal CSS file. You can then import these files without using the underscore.
```
  #main {
    @import "example"; 
  }
```
import all selector from the file example
# @extend
#The @extend directive avoids these problems by telling Sass that one selector should inherit the styles of another selector
```
  .error {
    border: 1px #f00;
    background-color: #fdd;
    }
  .seriousError {
    @extend .error;
    @extend .success;
    border-width: 3px;
  }
```
we can used multiple @extend with single block
% Operators
```
  #context a%extreme {
    color: blue;
    font-weight: bold;
    font-size: 2em;
  }

  .notice {
    @extend %extreme;
  }
```

# @media
  @media queries can also be nested within one another. The queries will then be combined using the and operator
  ```
  @media screen {
    .sidebar {
      @media (orientation: landscape) {
        width: 500px;
      }
    }
```
  # @at-root
  The @at-root directive causes one or more rules to be emitted at the root of the document, rather than being nested beneath their parent selectors. It can either be used with a single inline selector:
  ```
  @media print {
    .page {
      width: 8in;
      @at-root (without: media) {
        color: red;
      }
    }
  }
```
  @at-root (without: media supports)

  # @debug 
  The @debug directive prints the value of a SassScript expression to the standard error output stream. It's useful for debugging Sass files that have complicated SassScript going on. 

  # @warn
  Print the text on console
  The @warn directive prints the value of a SassScript expression to the standard error output stream. It's useful for libraries that need to warn users of deprecations or recovering 

  # @error
  The @error directive throws the value of a SassScript expression as a fatal error, including a nice stack trace. It's useful for validating arguments to mixins and functions.
  There is currently no way to catch errors.

-------------------------------------------------------------------
# Control Directives & Expressions
Control directives are an advanced feature, and are uncommon in day-to-day styling. They exist mainly for use in mixins, particularly those that are part of libraries like Compass, and so require substantial flexibility.

<ul>
  <li>if()</li>
  <li>@for()</li>
  <li>@each()</li>
  <li>@while()</li>
</ul>

# @if
```
  $list: 'style-1';

  .pageX {
      @if $list == 'style-1' {
      @extend %equal-heights;
      }
  }
```

# @For
```
  $color : (1,2,3);

  @for $i from 0 to length($color) {
      .color-#{$i} {
          @include setBgColor('red');
      }
  }
```

# @each
```
  $colors : ('red', 'green');
  
  @each $color in $colors{
  @warn $color;
      .color-#{$color} {
          @include setBgColor($color);
      }
  }
```
# @while
```
  $colors : ('red', 'green');
  $counter : 0;
  @while $counter < length($color)-1{
  $counter: $counter+1;
  @warn 'asdas'+ length($color);
  .color-#{$counter} {
          @include setBgColor('red');
      }
  }
```