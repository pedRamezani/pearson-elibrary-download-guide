# Pearson eLibrary Download Guide
This guide demonstrates how to download full books from [Pearson eLibrary](https://elibrary.pearson.de/).

## Method 1 - Developer Console - Debugger tab

**LAST CHECKED: December 1st, 2024**

1. Connect to a VPN / Login with your institution with access to the eLibrary
2. Find a Book you can access and want to download. 
3. Press the read button to open the PDF viewer
4. Press <kbd>F12</kbd> to open the Developer Console
   + could be something else for your browser
   + This guide will assume, that you are using Firefox
5. Switch to the Debugger tab
6. Activate XHR breakpoints
7. Reload the page
8. Step forward until the PDF URL appears (see picture)
9. Open the URL in a new browser page
10. Enjoy your eBook!

### Debugger tab with catched URL
![Developer console with loaded PDF URL](https://github.com/user-attachments/assets/190154cf-6de4-42b6-bcd9-d44a82b5d334)

## Method 2 - Developer Console - Network tab

**LAST CHECKED: March 25th, 2025**

1-4. Follow steps from first method<br/>
5. Switch to Network tab<br/>
6. Reload the page<br/>
7. Copy the URL requesting the subdocument /content/pdf-for-viewer[...]<br/>
8. In a new tab open https://elibrary.pearson.de + /content/pdf-for-viewer[...]<br/>
9. Freedom!

### Network tab with URL (copy red, ignore blue)
![Network tab with URL](https://github.com/user-attachments/assets/4bb31d1b-1421-4b1c-921e-8d574e87cd8b)

---
## Alternative Download Method
You can also try this approach for downloading the PDF URL. This might be useful for converting this guide into a script.

```js
response = await fetch("URL", {
  credentials: "same-origin"
})

blob = await response.blob() 

blobURL = URL.createObjectURL(blob)
```

Then you will have to attach the `blobURL` to a `<a>`-Element and download the PDF.
