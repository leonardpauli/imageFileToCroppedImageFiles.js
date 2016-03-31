# imageFileToCroppedImageFiles.js
Turns an original image file into multiple cropped/scaled ones - client side.

We use it to resize an image to multiple versions (small, medium, large) before uploading it to an external store-only server.
The image is chosen through a file input, and uploaded as a file, hence the need to convert it from and to a file.

1. The crop function will scale aspect fill (css `background-size: cover;` style) the image to the desired size.
2. If the image is too small, it will cut it (while keeping center at center) to match the destination proportions.
3. If the image contains transparancy, or the *fillModeContain* flag is set, it will scale aspect to contain instead (css `background-size: contain;` style).


## Example:

```javascript
$("#input").change(function(){
  var sizes = [{ w:400, h:400 },{ w:120, h:120 },{ w:60, h:60 }];
  imageFileToCroppedImageFiles(file, sizes, function (files) {
    var allFiles = { original:file, default:files[0], medium:files[1], small:files[2] };
    // All files ready
  }
});
```


## Functions:

```javascript
aspectContainImageCrop(image, size[, fillModeContain])    						-> Image
imageFileToCroppedImageFiles(file, sizes, callback, fillModeContain) 	-> callback(files)

getImageFromSrc(src, callback) 	                          						-> callback(image)
getImageFromFile(file, callback)                          						-> callback(image)

dataURItoBlob(dataURI)                                    						-> Blob
```

(Where fillModeContain is eigther null (auto, contain if transparent bg), true (force contain), false (force cover))


---

Feel free to contribute, and to open issues/requests.

Original creator: Leonard Pauli,  
Date: 18/3-2015,  
License: MIT  
