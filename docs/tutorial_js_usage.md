# 初入OpenCV.js

## 步骤 

在本章教程中，您将学习到如何在网页中引入并开始使用`opencv.js`。

### 创建一个Web页面

首先，让我们创建一个能够上传图像的简单网页。

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Hello OpenCV.js</title>
</head>
<body>
<h2>Hello OpenCV.js</h2>
<div>
  <div class="inputoutput">
    <img id="imageSrc" alt="No Image" />
    <div class="caption">imageSrc <input type="file" id="fileInput" name="file" /></div>
  </div>
</div>
<script type="text/javascript">
let imgElement = document.getElementById("imageSrc")
let inputElement = document.getElementById("fileInput");
inputElement.addEventListener("change", (e) => {
  imgElement.src = URL.createObjectURL(e.target.files[0]);
}, false);
</script>
</body>
</html>
```

如果要运行这个网页，请复制上面的内容并将其保存到本地index.html文件，并使用Web浏览器将其打开。(由于可能要运行某些特殊的数据操作，建议使用web服务打开，而非直接打开这个文件)

### 引入OpenCV.js

添加一个script标签，并引入OpenCV.js文件。

比如就像这样的引入：

```html
<script src="opencv.js" type="text/javascript"></script>
```

如果你想使用异步的方式进行加载，你可以使用`async`属性，并在OpenCV.js准备就绪的使用使用onload来回调。

比如这个例子：

```html
<script async src="opencv.js" onload="onOpenCvReady();" type="text/javascript"></script>
```



### Use OpenCV.js

Once `opencv.js` is ready, you can access OpenCV objects and functions through `cv` object.

For example, you can create a [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html) from an image by [cv.imread](https://docs.opencv.org/4.0.1/d4/da8/group__imgcodecs.html#ga288b8b3da0892bd651fce07b3bbd3a56).

- Note

  Because image loading is asynchronous, you need to put [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html) creation inside the `onload` callback.

imgElement.onload = function() {

  let mat = cv.imread(imgElement);

}

Many OpenCV functions can be used to process [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html). You can refer to other tutorials, such as [Image Processing](https://docs.opencv.org/4.0.1/d2/df0/tutorial_js_table_of_contents_imgproc.html), for details.

In this tutorial, we just show a [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html) on screen. To show a [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html), you need a canvas element.

<canvas id="outputCanvas"></canvas>

You can use [cv.imshow](https://docs.opencv.org/4.0.1/d7/dfc/group__highgui.html#ga453d42fe4cb60e5723281a89973ee563) to show [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html) on the canvas. 

cv.imshow(mat, "outputCanvas");

Putting all of the steps together, the final index.html is shown below.

<!DOCTYPE html>

<html>

<head>

<meta charset="utf-8">

<title>Hello OpenCV.js</title>

</head>

<body>

<h2>Hello OpenCV.js</h2>

<p id="status">OpenCV.js is loading...</p>

<div>

  <div class="inputoutput">

​    <img id="imageSrc" alt="No Image" />

    <div class="caption">imageSrc <input type="file" id="fileInput" name="file" /></div>

  </div>

  <div class="inputoutput">

​    <canvas id="canvasOutput" ></canvas>

    <div class="caption">canvasOutput</div>

  </div>

</div>

<script type="text/javascript">

let imgElement = document.getElementById('imageSrc');

let inputElement = document.getElementById('fileInput');

inputElement.addEventListener('change', (e) => {

  imgElement.src = URL.createObjectURL(e.target.files[0]);

}, false);



imgElement.onload = function() {

  let mat = cv.imread(imgElement);

  cv.imshow('canvasOutput', mat);

  mat.delete();

};



function onOpenCvReady() {

  document.getElementById('status').innerHTML = 'OpenCV.js is ready.';

}

</script>

<script async src="opencv.js" onload="onOpenCvReady();" type="text/javascript"></script>

</body>

</html>

- Note

  You have to call delete method of [cv.Mat](https://docs.opencv.org/4.0.1/d3/d63/classcv_1_1Mat.html) to free memory allocated in Emscripten's heap. Please refer to [Memory management of Emscripten](https://kripken.github.io/emscripten-site/docs/porting/connecting_cpp_and_javascript/embind.html#memory-management) for details.

## Try it