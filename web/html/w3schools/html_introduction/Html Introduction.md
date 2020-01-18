

# Html Introduction

## What is HTML?

HTML : **H**yper **T**ext **M**arkup **L**anguage

- Standard markup language for creating webpages
- describes structure of a webpage
- HTML consists of series of elements
- HTML elements tell a browser how to display content
- HTML elements are represented by tags
- Browsers do not display the HTML tags, but use them to render the content of the page

### Example

```html
<!DOCTYPE html>
<html>
    <head> 
        <title>
            My First HTML page
        </title>
    </head>
    <body>
        <h1> This is a heading </h1>
        <p> Hello world. This is a paragraph </p>
    </body>
</html>
    
```

- `<!DOCTYPE html>` : Document declaration --> Tells a browser that this document is html5
- `html` : element is the root element of html page
- `head` element contains meta information about the document
- `<title>` :element specifies a title for the document
- `<body>` : element contains the visible page content
- `<h1>` : element defines a large heading
- `<p>` : element defines a paragraph



### Html tags

```html
<opening_tag_name attributes> content </closing_tag_name>
```

- HTML tags are element names surrounded by angle brackets
- HTML tags normally come in pairs like `<p>` and `</p>` 
- 