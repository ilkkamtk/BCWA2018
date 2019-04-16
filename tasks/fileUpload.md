# File Upload

## Start
1. Load and extract this repo as a ZIP https://github.com/ilkkamtk/BCW3

## 1. It's 90's again

* Modify task_a.html
  * Complete the form to upload an image to your Express server
  * Study [multer](https://github.com/expressjs/multer) to find out how to receive files with express
  * Study [using cors in express cors](https://medium.com/@alexishevia/using-cors-in-express-cac7e29b005b) to find out how to handle cross domain requests
  * Study [attributes of input element](https://www.w3schools.com/tags/tag_input.asp) and find a suitable attribute to select only images 


## 2. Modern version

* Use fetch API to upload the file
* Example:
```javascript
    // select input element where type is file
    const input = document.querySelector('input[type="file"]');
    // make FormData -object
    const data = new FormData();
    // add file to FormData -object.
    // Note that 'files' is an FileList object. This means that you can upload multiple files. 
    data.append('fileToUpload', input.files[0]);
    // make an object for settings
    const settings = {
            method: 'POST',
            // credentials: 'same-origin', // this might be needed for some servers
            body: data
        };
    // initiate fetch. In this example the server responds with text.
    // Response could also be json. Then you would use response.json()
    fetch('url_to_server', settings).then((response) => {
        return response.json();
    }).then((json) => {
        console.log(json);
    });
```
* [FormData](https://developer.mozilla.org/en-US/docs/Web/API/FormData)
* Modify task_b.html and main_b.js
* More help in the comments of main_b.js

## 3. Adding to database (optional)
* Add uploaded files to database
   * Add new input-element to main_b.js for adding a title for the uploaded file (image)
   * In your express server create a middleware to save the filename and title to database after upload
   
