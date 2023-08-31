# HTML Smuggling

## Summary
HTML Smuggling has been around for a while, but it has seen an uptick in its usage lately with malware like Qakbot utilizing it. 
## What is it?
HTML Smuggling is an evasive payload delivery method that helps an attacker smuggle payload past content filters and firewalls by hiding malicious payloads inside of seemingly benign HTML files. This is possible by using JavaScript blobs and the HTML5 download attribute used with the anchor tag.
## What are anchor tags?
The anchor tag <a> defines a hyperlink that can be used to link one page to another resource like the script, other HTML page or downloadable files. When <a> is used with the “download” attribute, it can be used to provide links to a downloadable file. 
## What is a Javascript Blob?
JavaScript blobs are objects that are a collection of bytes that contain data stored in a file. Blob data is stored in the user’s memory. This collection of bytes can be used in the same places where an actual file would have been used. In other words, blobs can be used to construct file-like objects on the client that can be passed to JavaScript APIs that expect URLs.
Blobs are very useful for storing binary data because their content can be easily read as an ArrayBuffer. Blobs can be stored in the memory or on disk by the web browser, and they can represent truly massive bits of data that are too large to fit in the main memory unless first separated into smaller pieces with the slice () method.
The syntax for creating a JavaScript blob may be defined as:
```
new Blob("blobParts, options");
```
- Blobparts: It is an array of Blob, BufferSource, and string values.
- Options: It is an optional object.
- Type: It is a Blob type, generally MIME-type like image.png.

An example would be:
```
<!DOCTYPE html>  
<html>  
<head>  
    <meta charset="utf-8">  
    <title>JavaScript Blob</title>  
</head>  
<body>  
    <p id="main"></p>  
    <script>  
var abc = new Blob(["Wassup Playa"],   
{type : "text/plain"});  
var def = new FileReader();  
def.addEventListener("loadend", function(e) {  
document.getElementById("main").innerHTML  
     = e.srcElement.result;  
});  
def.readAsText(abc);  
</script>  
</body>  
</html>  
```
Let’s break this down:

1.	We start our HTML document with the tag HTML
2.	This is followed by <head> to indicate a header, where you can store things like meta tags as well as a title
3.	<title> is what will show at the top of the tab
4.	<body> starts the body of the HTML file
5.	<p> is to indicate a parameter. In this case we are specifying ‘main’ as an id element. Later in the HTML we will be referencing this ID. 
6.	<script> indicates that what comes next is Javascript
7.	var abc = new Blob(["Wassup Playa"],   {type : "text/plain"});  We can see this follows the Javascript Blob syntax I mentioned earlier. The text here, Wassup Playa, is what we will want shown on the page, thus it is the data element, in this case being a string value. Then its followed by the MIME type of text/plain. All of this is being assigned to the variable abc, so that whenever abc is used, it really means this Blob that has the string value of Wassup Playa
8.	Next we see a variable assigning FileReader. The FileReader object lets web applications asynchronously read the contents of files (or raw data buffers) stored on the user's computer, using File or Blob objects to specify the file or data to read. This is assigned to the variable def. https://developer.mozilla.org/en-US/docs/Web/API/FileReader 
9.	It is using the FileReader component of addEventListener, which sets up a function that will be called whenever the specified event is delivered to the target. It has the syntax of addEventListener(type, listener) So in our code, the type is FileReader’s loadend event https://developer.mozilla.org/en-US/docs/Web/API/FileReader/loadend_event The loadend event is fired when a file read has completed, successfully or not. Next part is function(e). Function is the function to run when the event occurs, which in this case is the loadend event. 
10.	Next it looks through the document table and gets the element named ‘main’, which we defined earlier in the start of our paragraph. innerHTML sets or returns the HTML content (inner HTML) of an element. In the case of our code, it is setting or changing the value that was in the element with the id of ‘main’ to e.srcElement.result
11.	Next, we see the readAsText portion. This starts reading the contents of the specified Blob, once finished, the result attribute contains the contents of the file as a text string. The Blob is referenced by its variable abc.
12.	The rest of the code just closes out the rest of the HTML document


