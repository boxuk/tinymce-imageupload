TinyMCE - ImageUpload
=====================

## What this does ##

This gives a very basic file upload form to a user which allows them to upload an image.

After the image has been uploaded, the dialog closes and an image is placed into the area.

## Requirements ##

This was written for TinyMCE version 4.0b1 (2013-04-11)

It utilises the iFrame Post Form plugin, which can be found here:

http://sourceforge.net/projects/iframepostform/files/

## Setup ##

Your TinyMCE init() method should contain the following value:

```javascript
tinymce.init({
    ...
    imageupload_url: '/my/uploader/path', // PHP (or other server side script)
    // imageupload_rel: 'http://cdn.somewhere.com/media/tinymce-plugin/imageupload', // use if not installed in plugin folder.
    plugins: 'imageupload', // and your other plugins
    toolbar1: 'imageupload' // and your others
    ...
});
```

## Recognised Responses ##

It handles a couple responses, which are:

#### Success ####
```javascript
{"error":false,"path":"http:\/\/www.mydomain.com\/myimage.jpg"}
```

#### Errors ####

An invalid image error message is produced by returning this:
```javascript
{"error":"filetype"}
```


An unknown error message is produced with this:
```javascript
{"error":"unknown"}
```

## Known Issues ##

The jquery.iframe-post-form.js script commonly available fails to parse a JSON response in Chrome. This is mainly because chrome wraps the returned text in a 'pre' tag. Its a simple one line fix to the script, .html() is changed .text(). You can get the fixed script here - https://github.com/worldspawn/jquery.iframe-post-form