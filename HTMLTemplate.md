# Introduction #

Jquery loadJSON plugin can be used to define template that will be used to generate list of elements. In this plugin is placed a simple template engine that uses plain HTML as a template source and generate HTML output based on the template item and array of objects that are used as data source.

## Definition of template ##

Template item that will be used for generatin output doesnot require any specific syntax or language. Only thing that is required is to define HTML template with elements that have id, class or rel attributes that will be used as a placeholders for actual values taken from the JavaScript objects. Example of such kind template is shown below:
```
<ul>
    <li> 
       <a href="details.html" class="ID">
            <span class="Name"></span>
       </a>
       <span class="Address"></span>
    </li>
</ul>
```
In this template is defined one list where ID, Name, and Address properties of the JavaScript objects will be placed.

## JavaScript DataSource ##

Data source for this template is JavaScript object array represented in JSON notation. This array should have objects that have properties that match HTML element in template. Example of array that can be bound to the bound to the template shown in the example above is shown in the following listing:
```
data =
[
    {
	"ID": 17,
        "Name": "Emkay Entertainments",
        "Address": "Nobel House, Regent Centre"
    },
    {
        "ID": 18,
        "Name": "The Empire",
        "Address": "Milton Keynes Leisure Plaza"
    },
    {
        "ID": 19,
        "Name": "Asadul Ltd",
        "Address": "Hophouse"
    }
]
```
Each of the objects in the array have ID, Name, and Address fields that will be bound to the elements in the template.

## Generating output ##

Binding JSON array 'data' with template is done on the client-side using the following JavaScript code:
```
    $('li').loadJSON(data);
```
In this code is defined that the template placed in the LI tag should be loaded with JavaScript array in 'data' variable. As a result of this call, LI element will be populated with each of the object in the array and replicated three times (because there are a three elements in the array). Resulting HTML is shown below:

```
<ul>
    <li> 
       <a href="details.html?ID=17" class="ID">
            <span class="Name">Emkay Entertainment</span>
       </a>
       <span class="Address">Nobel House, Regent Centre</span>
    </li>
    <li> 
       <a href="details.html?ID=18" class="ID">
            <span class="Name">The Empire</span>
       </a>
       <span class="Address">Milton Keynes Leisure Plaza</span>
    </li>
    <li> 
       <a href="details.html?ID=19" class="ID">
            <span class="Name">Asadul Ltd</span>
       </a>
       <span class="Address">Hophouse</span>
    </li>
</ul>
```

Detailed rules how HTML elements are populated with JavaScript objects can be found in the [LoadingHTMLElements](LoadingHTMLElements.md) page.