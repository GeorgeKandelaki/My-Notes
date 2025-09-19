## What Is Sass?
**SASS** -> Sass is a CSS preprocessor, an extension of CSS that adds power and elegance to the basic language.

**SASS SOURCE CODE** -> **SASS COMPILER** -> **COMPILED CSS CODE**

The way SASS works, is that instead of writing a CSS file with regular CSS code, we Write SASS code in SASS files, then we run a compiler and that compiler converts the SASS code we wrote into regular CSS code. 
So we need to process our SASS code first, and that is why it is called a CSS preprocessor.

### Main SASS Features
* **Variables**: For reusable values such as colors, font-sizes, spacing, etc.
* **Nesting**: To nest selectors inside of one another, allowing us to write less code.
* **Operators**: For mathematical operations right inside of CSS.
* **Partials and Imports**: To write CSS in different files and importing them all into on single file.
* **Mixins**: To write **Reusable** Pieces of CSS Code.
* **Functions**: Similar to Mixins, with the difference that they produce a value that can than be used.
* **Extends**: To make different selectors inherit declarations that are common to all of them.
* **Control Directives**: For writing complex code using conditionals and loops.

### SASS and SCSS: Clearing Up The Confusion
**SASS Syntax** (Original SASS):
```
.navigation
	list-style: none
	float: left
	
	& li 
		display: inline-block
		margin-left: 30px
```

**SCSS Syntax** (Sassy CSS):
```SCSS
.navigation {
	list-style: none;
	float: left;
	
	& li {
		display: inline-block;
		margin-left: 30px;
	}
}
```

**SASS** (Original SASS) -> The SASS Syntax is indentation sensitive and doesn't use any curly braces and semicolons.

**SCSS** (Sassy CSS) -> SCSS preserves the way the original CSS looks like, SCSS Uses curly braces and semicolons like original CSS.