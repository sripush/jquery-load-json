# Introduction #

JQuery loadJSON plugin enables you to load JavaScript objectinto the HTML form. Depending on the type of the form element, plugin will populate value of the form. You can see how the form is populated int the [Live example](http://jquery-load-json.googlecode.com/svn/trunk/edit.html?ID=17) page.

## Form template ##
Blank form that will be used for editing data should be defined. Form elements must have name attributes that will be used for matching with !JAvaScript objects. Example of the form template that can be used is shown in the example below:
```
<form name="form_simple" action="details.html" method="get">

    <input type="hidden" name="ID" />

	<label for="Name">Name</label>
	<input name="Name"  type="text" />

	<label for="Address">Address</label>
	<textarea name="Address" rows="5" cols="20"></textarea>

	<label for="Country">Country</label>
	<select name="Country" multiple="multiple">
		<option value="">-</option>
		<option value="UK">United Kingdom</option>
		<option value="SRB">Serbia</option>
		<option value="USA">United States of America</option>
		<option value="FRA">France</option>  
	</select>

	<label for="IsFeatured">Is Featured</label>
	<input name="IsFeatured" type="checkbox" value="true"/>

	<label for="Town">Town</label>
	<select name="Town">
		<option value="" selected="selected">-</option>
		<option value="London">London City</option>
		<option value="Liverpool">Liverpool City</option>
		<option value="Lothian">Lothian City</option>
		<option value="Newcastle">Newcastle City</option>
		<option value="Buckinghamshire">Buckinghamshire City</option>
		<option value="Essex">Essex City</option>  
	</select>

	<label for="Contact">Contact</label>
		<input name="Contact" type="radio" value="Email"/> Email
		<input name="Contact" type="radio" value="Phone" /> Phone
		<input name="Contact" type="radio" value="Post" /> Post

    <input type="submit" value="Save" class="submit-button" />
</form>
```
In this form are placed various form elements that will be bound with properties ID, Name, Address, IsFeatured, Country, Town, and Contact from the JavaScript object that will be used as a data source for the form.

## Data source ##
JavaScript object object that will be used as a data source must have properties that match the names in the form elements. Example of the JavaScript object that can be used with the form shown in the previous example is shown in the following listing:
```
data = {
            "ID":17,
            "Name":"Emkay Entertainments",
            "Address":"Nobel House, Regent Centre",
            "Town":"Lothian",
            "Contact":"Phone",
            "IsFeatured": true
        } 
```
Once this object is bound with the form, the form elements will be populated with values from the JavaScript object. You can see how the form is populated int the [Live example](http://jquery-load-json.googlecode.com/svn/trunk/edit.html?ID=17) page.

## Populating form element ##

Form is populated with JSON object using the following JavaScript call:
```
    $('form').loadJSON(data);
```

This call matches object properties with the form elements by name and depending on the type of the form element populates value. Following rules are used while the form elements are populated:

### Text, hidden and select element ###
When plugin matches hidden fields, simple text boxes, and sigle selection list, it takes value from the matched JavaScript property and place it as a value of element.
### Check boxes ###
When plugin matches check box element wth property it expect that in property is placed boolean value true or false. Depending on this value check box will be either checked or unchecked.
### Radio buttons ###
When plugin matches property of the object with radio buttons it wil find radio button with value that is same as the value of the property in JavaScript object. This radio button will be selected.
### Multiple selection lists ###
When plugin matches property with multiple selection list element, it expect that property is array of values that should be selected in the list. Plugin selects all values in the multi selection list that exist in the property of the JavaScript object.
### Text area ###
When plugin matches text area form element with a JavaScript property it takes value of property and place it as a content of text box.