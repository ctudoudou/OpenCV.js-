# Arithmetic Operations on Images

## Goal

- Learn several arithmetic operations on images like addition, subtraction, bitwise operations etc.
- You will learn these functions : **cv.add()**, **cv.subtract()** etc.

## Image Addition

You can add two images by OpenCV function, [cv.add()](https://docs.opencv.org/4.0.1/d2/de8/group__core__array.html#ga10ac1bfb180e2cfda1701d06c24fdbd6). res = img1 + img2. Both images should be of same depth and type.

For example, consider below sample:

```javascript
let src1 = cv.imread("canvasInput1");
let src2 = cv.imread("canvasInput2");
let dst = new cv.Mat();
let mask = new cv.Mat();
let dtype = -1;
cv.add(src1, src2, dst, mask, dtype);
src1.delete(); src2.delete(); dst.delete(); mask.delete();
```

## Image Subtraction

You can subtract two images by OpenCV function, [cv.subtract()](https://docs.opencv.org/4.0.1/d2/de8/group__core__array.html#gaa0f00d98b4b5edeaeb7b8333b2de353b). res = img1 - img2. Both images should be of same depth and type.

For example, consider below sample:

```javascript
let src1 = cv.imread("canvasInput1");
let src2 = cv.imread("canvasInput2");
let dst = new cv.Mat();
let mask = new cv.Mat();
let dtype = -1;
cv.subtract(src1, src2, dst, mask, dtype);
src1.delete(); src2.delete(); dst.delete(); mask.delete();
```

## Bitwise Operations

This includes bitwise AND, OR, NOT and XOR operations. They will be highly useful while extracting any part of the image, defining and working with non-rectangular ROI etc. Below we will see an example on how to change a particular region of an image.

I want to put OpenCV logo above an image. If I add two images, it will change color. If I blend it, I get an transparent effect. But I want it to be opaque. If it was a rectangular region, I could use ROI as we did in last chapter. But OpenCV logo is a not a rectangular shape. So you can do it with bitwise operations.

## Try it

pass



