
---
# Forms

[Back to index](../README.md)

---
## Structure of  a Form
```html
<form>
	<!-- To create a grouping with a legend (Not required) -->
	<fieldset>
	    <legend>Legend</legend>
		...
		
	</fieldset>
	
	<!-- Submit and reset inputs -->
	<input type="submit" value="Submit">
    <input type="reset" value="Reset">
	
</form>
```
---
## Form Attributes
```html
<!-- Form name -->
<form name="name"> ... </form>

<!-- Action indicates where the data must be sent -->
<!-- Using a php code -->
<form action="/action.php"> ... </form>

<!-- Data sent by URL (Do not use for sensitive data) -->
<form action="/action.php" method="get"> ... </form>

<!-- Data sent by an HTTP post -->
<form action="/action.php" method="post"> ... </form>

<!-- Send by email -->
<form action="mailto:email" method="post" enctype="text/plain" target="_blank"> ... </form>
```
---
## Form Elements
### Input
```html
<form>
	<!-- Simple input -->
	<label for="name">First name:</label>
	<input type="text" id="name" name="name"/>

	<!-- Input with predefined options -->
	<label for="browser">Browser:</label>
	<input id="browser" name="browser" list="browsers">  
	<datalist id="browsers">  
	    <option value="Chrome">
	    <option value="Firefox">
	</datalist>
</form>
```
### Select
```html
<form>
	<label for="car">Choose your car:</label>
	
	<!-- Pannel for selecting from several options -->
	<!-- We see 2 options at once (1 by default) -->
	<!-- We allow multi-select values (Forbiden by default) -->
	<select id="car" name="car" size="2" multiple>
	
		 <!-- This is an option -->
		 <option value="volvo">Volvo</option>
		 
		 <!-- This is the default option -->
		 <option value="fiat" selected>Fiat</option>  
	</select>
</form>
```
### Text area
```html
<textarea name="message" rows="10" cols="30">  
	Write here your message.  
</textarea>
```
---
## Input types
```html
	<!-- Text input -->
	<input type="text" id="name" name="name"/>
	
	<!-- Radio buttons input -->
	<input type="radio" id="male" name="sex"/>
	<input type="radio" id="female" name="sex"/>
	
	<!-- Checkboxes input -->
	<input type="checkbox" id="dev1" name="dev1" value="PC">
	<input type="checkbox" id="dev2" name="dev2" value="Phone">
	
	<!-- Date input -->
	<input type="date" id="birth" name="birth"/>
	
	<!-- Password input -->
	<input type="password" id="pwd" name="pwd"/>
	
	<!-- Button input -->
	<input type="button" onclick="function()" value="Click Me!">
	
	<!-- Other input -->
	<input type="color" id="favcolor" name="favcolor">
	<input type="email" id="email" name="email">
	<input type="file" id="myfile" name="myfile">
	<input type="number" id="quantity" name="quantity">

	<!-- To send some data hidden to the user -->
	<input type="hidden" id="data" name="data" value="someData">
```
---
## Input Attributes

- `checked`. Pre-selected radio button or checkbox.
- `max`.  Maximum value for an input.
- `min`. Minimum value for an input.
- `maxlength`.  Maximum length for an input.
- `minlength`.  Minimum length for an input.
- `pattern`. Pattern to check the input.
	- `[]` set of characters
	- `{}` range of repetitions
	- `?` optional.
	- `*` 0 or more.
	- `+` 1 or more.
- `disabled`. Disabled input.
- `readonly`. Non-modificable input.
- `required`. Mandatory input.
- `value`. Default value.
- `novalidate`.  Non-validated input.
- `placeholder`. Adds explanatory text.

---
## Events
### General
- `onload` (with body)
- `onchange` (with form inputs)
- `onfocus` (with form inputs)
- `onblur` (with form inputs)

### Mouse & Keyboard
- `onclick`. Mouse event (usually with button or span)
- `onkeyup`. Keyboard event (with form inputs)
- `onkeydown`. Keyboard event (with form inputs)
- `onkeypress`. Keyboard event (with form inputs)