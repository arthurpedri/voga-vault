## Video Downloader project
### Useful py lib
[lib for getting urls](https://docs.python.org/3/library/urllib.request.html#module-urllib.request)

### Extension example in github
[github extension example](https://github.com/DoctorLai/VideoDownloadHelper/tree/master)

### Maybe streaming with a clean player instead of downloading
### ChatGPT Prompt
Creating a video downloader extension for Vivaldi involves a mix of JavaScript, HTML, and potentially other web technologies. Here's a simplified guide to help you get started:

**1. Understand the Basics:**
   Familiarize yourself with HTML, JavaScript, and the basics of browser extensions. You should understand how to manipulate the DOM (Document Object Model) of web pages and how to make network requests.

**2. Set Up Your Development Environment:**
   Install a code editor (like Visual Studio Code) and Vivaldi browser. You'll use the browser for testing your extension.

**3. Create a New Extension:**
   In Vivaldi, extensions can be created using HTML, CSS, and JavaScript. Here's a basic structure:

   ```plaintext
   my-extension/
   ├── manifest.json
   ├── popup.html
   ├── popup.js
   └── icon.png
   ```

**4. Define `manifest.json`:**
   This is the configuration file for your extension. It defines properties like the extension's name, permissions, icons, and scripts. Here's a minimal example:

   ```json
   {
     "manifest_version": 2,
     "name": "My Video Downloader",
     "version": "1.0",
     "permissions": [
       "activeTab",
       "storage"
     ],
     "browser_action": {
       "default_popup": "popup.html",
       "default_icon": {
         "16": "icon.png",
         "48": "icon.png",
         "128": "icon.png"
       }
     }
   }
   ```

**5. Create `popup.html`:**
   This is the popup window that opens when the user clicks on the extension icon. It can have a button to trigger the download.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
     <title>Video Downloader</title>
     <script src="popup.js"></script>
   </head>
   <body>
     <button id="downloadButton">Download Video</button>
   </body>
   </html>
   ```

**6. Write `popup.js`:**
   This script will handle the logic of capturing the video URL and initiating the download.

   ```js
   document.addEventListener("DOMContentLoaded", function() {
     const downloadButton = document.getElementById("downloadButton");

     downloadButton.addEventListener("click", function() {
       chrome.tabs.query({ active: true, currentWindow: true }, function(tabs) {
         const activeTab = tabs[0];
         const videoUrl = activeTab.url;

         // Write logic here to extract the video URL and trigger download
       });
     });
   });
   ```

**7. Add Content Scripts (if needed):**
   Content scripts allow you to interact with the web page's DOM. You might need these to identify video elements and extract their URLs.

**8. Test Your Extension:**
   Load your extension into Vivaldi for testing. Go to `vivaldi://extensions/`, enable "Developer mode", and click "Load unpacked". Select the directory containing your extension files.

**9. Implement Video Download Logic:**
   You'll need to implement the logic to identify video URLs on the page, choose the desired format, and initiate the download. This could involve using libraries or APIs for video manipulation.

**10. Refine and Publish:**
   Test thoroughly and refine your extension's functionality. Once it's working well, you can consider publishing it on the Chrome Web Store, as Vivaldi supports Chrome extensions.

Remember, this is a simplified outline. Developing a full-fledged video downloader extension requires a deeper understanding of JavaScript, web technologies, and browser extension development. Make sure to check the documentation and resources for Vivaldi extension development to understand the specifics and best practices.

## Detecting and retrieving
Detecting and retrieving embedded videos from a web page using JavaScript involves identifying video elements in the HTML structure and extracting relevant information such as the video URL, source, or attributes. Here's a general approach:

**1. Identifying Video Elements:**
Use JavaScript to identify video elements within the webpage's DOM. Video elements are typically represented using the `<video>` tag.

```javascript
const videoElements = document.querySelectorAll("video");
```

**2. Extracting Video Information:**
Once you have the list of video elements, you can loop through them and extract relevant information such as the video source URL and attributes.

```javascript
videoElements.forEach(videoElement => {
    const videoSource = videoElement.src; // Retrieve the video source URL
    const videoType = videoElement.type; // Retrieve the video MIME type
    // You can also retrieve other attributes like width, height, poster, etc.
    
    // Do something with the video information
    console.log("Video Source:", videoSource);
    console.log("Video Type:", videoType);
});
```

**3. Handling Embedded Videos:**
Embedded videos could be hosted within iframes. In this case, you would need to traverse the iframe's content to identify and extract video elements.

```javascript
const iframeElements = document.querySelectorAll("iframe");

iframeElements.forEach(iframeElement => {
    const iframeDocument = iframeElement.contentDocument || iframeElement.contentWindow.document;
    const videoElementsInIframe = iframeDocument.querySelectorAll("video");

    videoElementsInIframe.forEach(videoElement => {
        // Extract and process video information within the iframe
    });
});
```

**4. Additional Checks:**
Not all `<video>` elements necessarily have a `src` attribute directly. Some might load video content dynamically through JavaScript or use multiple sources with different formats and resolutions. You might need to explore the DOM further to handle these scenarios.

**5. Video Hosting Services:**
If you are particularly interested in extracting videos from known video hosting services like YouTube or Vimeo, these platforms often expose APIs that provide video information in a structured manner. This could be a more reliable approach than parsing the DOM for embedded videos.

Remember that accessing and manipulating the content of other websites might have legal and ethical implications, so make sure to check the website's terms of use and respect their policies when scraping or interacting with their content.