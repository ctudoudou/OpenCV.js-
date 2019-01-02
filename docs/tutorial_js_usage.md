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



### 使用OpenCV.js

当`opencv.js`加载完成之后，你就可以使用`cv`来调用OpenCV的类和函数。

比如，你可以使用`cv.imread`将读取图片并将其创建为一个`cv.Mat`类型的数据。

注意：因为图片是异步加载的，你需要将图片的处理函数放到`onload`回调函数中。

```javascript
imgElement.onload = function() {
  let mat = cv.imread(imgElement);
}
```

很多OpenCV函数都可以直接处理`cv.Mat`。你可以查看其他的教程，例如图像处理。

本章教程中，我们只讲述如何在屏幕上显示`cv.Mat`。当然，我们首先要准备好一个`canvas`元素。

在本教程中，我們只在屏幕上顯示cv.Mat。 要顯示cv.Mat，您需要一個canvas元素。

```html
<canvas id="outputCanvas"></canvas>
```

你可以使用`cv.imshow`在画布上显示`cv.Mat`数据。

```javascript
cv.imshow(mat, "outputCanvas");
```
完整的代码如下：

```html
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
    <img id="imageSrc" alt="No Image" />
    <div class="caption">imageSrc <input type="file" id="fileInput" name="file" /></div>
  </div>
  <div class="inputoutput">
    <canvas id="canvasOutput" ></canvas>
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
```
注意：你需要调用delete方法来释放内存，因为Emscripten堆中的内存不会自动释放。请参照[Emscripten的內存管理](https://kripken.github.io/emscripten-site/docs/porting/connecting_cpp_and_javascript/embind.html#memory-management)。
