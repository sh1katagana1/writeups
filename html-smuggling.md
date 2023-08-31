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

