# uploader.js

### Link Script
```html
<script src="/path/to/cdn/jquery.min.js"></script>
<script src="uploader/uploader.js"></script>
<link rel="stylesheet" href="uploader/uploader.css" />
```

### Html Element
```html
<button type="button" class="select-file">
    Select Files...
</button>
```

### Initialize
```js
$('.select-file').uploader({
    upload_url: 'upload.php',
    input_name: 'file'
})
```

By default the plugin will automatically start uploading after a file is selected. To enable manual file upload, set the `auto_upload` to false and setup the Save as follows:

```js
var myUploader = $('.select-file').uploader({
    upload_url: 'upload.php',
    input_name: 'file',
    auto_upload: false
})

$('.save').on('click', function() {
  myUploader.upload(function() {
    console.log("Upload success...")
  })
})
```
Limit the file size & restrict the file type by extensions.
```js
var myUploader = $('.example').uploader({
    upload_url: 'upload.php',
    input_name: 'file',
    maximum_total_files: 4, // the maximum number of files
    maximum_file_size: 50009000, //the maximum file size of every file uploaded
    minimum_file_size: 500, //the minimum file size of every file uploaded
    file_types_allowed: ['image/jpeg', 'image/png'] //mime type
})
```
Callback Function
```js
var myUploader = $('.example').uploader({
    upload_url: 'upload.php',
    input_name: 'file',
    on_error: function(err) {},
    on_before_upload: function() {},
    on_after_upload: function() {}
})
```
Default Configuration
```js
var myUploader = $('.example').uploader({
    // Uploader
    upload_url: '',
    input_name: '',
    auto_upload: true,
    maximum_total_files: null,
    minimum_file_size: null,
    maximum_file_size: null,
    file_types_allowed: null,

    // File picker
    file_picker_url: '',
    files_per_page: 24,
})
```
Create a Wordpress-style media library in the file picker popup that fetches and previews all files uploaded and stored in the server.
```js
var myUploader = $('.example').uploader({
    upload_url: 'upload.php',
    input_name: 'file',
    file_picker_url: 'files.php'
})
```