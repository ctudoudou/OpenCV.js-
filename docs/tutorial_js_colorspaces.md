# Changing Colorspaces

## Goal

- In this tutorial, you will learn how to convert images from one color-space to another, like RGB ↔ Gray, RGB ↔ HSV etc.
- You will learn following functions : **cv.cvtColor()**, **cv.inRange()** etc.

## cvtColor

There are more than 150 color-space conversion methods available in OpenCV. But we will look into the most widely used one: RGB ↔ Gray.

We use the function: **cv.cvtColor (src, dst, code, dstCn = 0)**

### Parameters

src		input image.

dst		output image of the same size and depth as src

code	color space conversion code(see **cv.ColorConversionCodes**).

dstCnn	umber of channels in the destination image; if the parameter is 0, the number of the channels is derived automatically from src and code.

For RGB → Gray conversion we use the code cv.COLOR_RGBA2GRAY.

## Try it

pass

## inRange

Checks if array elements lie between the elements of two other arrays.

We use the function: **cv.inRange (src, lowerb, upperb, dst)**

- Parameters

  srcfirst input image.lowerbinclusive lower boundary Mat of the same size as src.upperbinclusive upper boundary Mat of the same size as src.dstoutput image of the same size as src and cv.CV_8U type.

## Try it

pass

