# Introduction #

JQuery loadJSON plugin enables you to load JSON object into the HTML code. In this page are show examples how the plain HTML template can be used.

## Loading JSON object properties into the standard HTML elements ##

The simplest case of template is plain HTML elements such as SPAN, P, DIV, LI, H1, H2, etc. When plugin finds a HTML element that matches property of the JSON object used as a data source, value of the property is placed as a content of the tag. If the following HTML code is used as a template:

```
    <h1 id="Title"></h1>
    <span id="Address"></span>
    <p id="Description"></p>
```
And if following JSON object is loaded to the template:

```
   data = { "Title": "This is a title",
            "Address": "Regent Street",
            "Description": "Lorem ipsum dolor sit amet" }
```

Values of the properties of the JSON object called Title, Address, and Description will be placed as a content of these elements. Resulting HTML that will be generated is shown below:
```
    <h1 id="Title">This is a title</h1>
    <span id="Address">Regent Street</span>
    <p id="Description">Lorem ipsum dolor sit amet</p>
```


## Loading JSON object properties into the image tag ##

HTML image tag do not uses content - only important attributes of IMG tag are src that defines where image is placed, and alt attribute that is shown when image cannot be loaded from the loaction placed in the src attribute. Exampe of the image tag that can be used as a template is shown below:
```
    <img id="Logo" src="" alt="" />
```
Values of the properties that can be placed into the IMG tag are shown below:
```
    data1 = { "Logo": "/images/logo.jpeg$This is an alt tag text"}
    data2 = { "Logo": "/images/logo.jpeg"}
```
When the first object is loaded into the image tag, "/images/logo.jpeg" is placed as a src attribute, and "This is an alt tag text" is placed as an alt attribute of the image. Dollar ($) is used as a separator for src and alt values. Resulting HTML is shown in the following listing:
```
    <img id="Logo" src="/images/logo.jpeg" alt="This is an alt tag text" />
```
When the second object is loaded into the image tag, "/images/logo.jpeg" is placed as a src attribute, and "logo" is placed as an alt attribute of the image. If an alt tag is not placed in the JSON object name of the image is used as an alt tag. HTML that wil be generated is shown below:
```
    <img id="Logo" src="/images/logo.jpeg" alt="logo" />
```

## Loading JSON object properties into the link tag ##

Link tag has a href property that represents URL where user will be redirected when he clicks on the link. Example of the blank link that can be used for populating with JSON object is shown below:
```
    <a href="" id="Link">Google</a>
```
Property that matches link tag by id will be placed as a href attribute of the tag. Example of object that has property 'Link' that can be loaded into the link is shown below:
```
    data = { "Link": "http://www.google.com"}
```
If link with id Link is placed in the HTML code '<a href=''>Google</a>' value of the Link property will be placed into the href attribute. Resulting HTML is shown below:

```
    <a href="http://www.google.com" id="Link">Google</a>
```

Note that text that will be shown in the link ("Google" in the example) will not be modified, because property from the JSON object is placed into the href attribute and not in the element content. If text of the link should be dinamically loaded, HTML element with id should be placed instead of the hardcoded text as shown in the example below:

```
    <a href="" id="Link"><span id="LinkText"></span></a>
```
If this HTML is bound to the following JSON object:
```
    data = { "Link": "http://www.google.com",
             "LinkText": "Google site" }
```
Link property will be set as a href attribute of A tag, and LinkText property will be placed as a content of the SPAN tag and shown to the user. Resulting HTML code that will be generated in this case is shown below:
```
    <a href="http://www.google.com" id="Link"><span id="LinkText">Google site</span></a>
```