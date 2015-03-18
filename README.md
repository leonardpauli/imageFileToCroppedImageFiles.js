# imageFileToCroppedImageFiles.js
Basically, image file to cropped image files, client side, javascript.

We use it to resize an image to multiple versions (small, medium, large) before uploading it to an external store-only server.
The image is chosen through a file input, and uploaded as a file, hence the need to convert it from and to a file.

The crop function will scale aspect fill the image to the desired size. If the image is too small, it will cut it (while keeping center at center) to match the destination proportions.

##Example:

```javascript
$("#inp").change(function(){
  var sizes = [{w:400,h:400},{w:120,h:120},{w:60,h:60}];
  imageFileToCroppedImageFiles(file, sizes, function (files) {
    var files = {original:file,default:files[0],medium:files[1],small:files[2]};
  }
});
```

##Functions:

```javascript
aspectContainImageCrop(image, size, isPng) -> Image
imageFileToCroppedImageFiles(file, sizes, callback) callback(files)

getImageFromSrc(src, callback) callback(image)
getImageFromFile(file, callback) callback(image)

dataURItoBlob(dataURI) -> Blob
```

##More

Original creator: Leonard Pauli,
Date: 18/3-2015,
License: MIT
