# OpenCV.js和教程简介

## OpenCV

**Gary Bradski**于1999年在英特尔写出来了OpenCV，并与2000年发布第一个版本。**Vadim Pisarevsky**加入了Gary Bradski来管理英特尔在俄罗斯OpenCV团队。 2005年，OpenCV被用于Stanley(史丹利，美国的工具制造商，不是中国的那个化合肥公司);赢得2005 DARPA Grand Challenge。后来，OpenCV在Gary Bradski和Vadim Pisarevsky领导下，并由Willow Garage支持继续快速的发展。现在，OpenCV已经支持了计算机视觉和机器学习相关的众多算法，并且扩展在与日俱增。

OpenCV现在已经支持了多种编程语言，例如C++、Python和Java，并且可以在不同的平台上使用，包括Windows、Linux、OS X、Android和iOS。基于CUDA和OpenCL的GPU接口也在积极开发中。OpenCV.js是OpenCV的JavaScript版本，并提供给JavaScript程序员使用。

## OpenCV.js：JavaScript程序员的OpenCV

Web是最常见的的开放计算平台。在任何符合HTML5规范标准的浏览器中，Web应用程序都可以使用HTML5视频标签来呈现在线的实时视频，通过WebRTC API捕获摄像头影像，并通过canvas API访问视频帧的每个像素。随着多媒体内容的逐渐丰富，Web开发人员需要JavaScript来实时处理的各种图像和视频影像。这包括了Web虚拟现实（WebVR）和增强现实（WebAR）。所有这些程序都要求在Web上能做到有效地实现计算密集型视觉内核。

[Emscripten](http://kripken.github.io/emscripten-site)是一个LLVM到JavaScript的编译器。它需要LLVM 字节码——可以借助clang从C / C ++生成，可以将OpenCV编译成直接在Web浏览器中执行的asm.js或WebAssembly。 Asm.js是一个高度可优化的低级JavaScript子集。 Asm.js可在JavaScript引擎中实现提前编译和优化，从而提供接近本机的执行速度。 WebAssembly是一种可移植、大小和加载时间可控的二进制格式，可以编译到Web当中运行。 WebAssembly旨在可以达到原生速度执行。 WebAssembly目前已经被W3C设计为标准。

OpenCV.js是用于Web平台的OpenCV函数的集合并与JavaScript语言融合。它可以使具有多媒体处理功能的Web应用程序受益于OpenCV中提供的各种视觉处理。 OpenCV.js利用Emscripten将OpenCV函数编译为asm.js或WebAssembly文件，并为Web应用程序提供JavaScript API以访问它们。该库的未来版本将会增加利用Web上可用的加速API，例如SIMD和多线程。

OpenCV.js最初是由California Irvine (UCI)的Parallel Architectures and Systems Group创建的，并成为英特尔公司资助的研究项目。作为Google Summer of Code 2017计划的一部分，OpenCV.js进一步被集合到OpenCV项目当中。

## OpenCV.js教程

OpenCV增加了一组新的教程，将指导您完成OpenCV.js中提供的各种功能。**本指南主要关注OpenCV 3.x版本。**(原文指向的是3.x版本，但是同样我会做到多版本的兼容翻译)

OpenCV.js教程的目的是：

> 1. 帮助OpenCV在Web开发中的移植
> 2. 帮助Web社区，开发人员和计算机视觉研究人员以交互方式访问各种基于Web的OpenCV示例，以帮助他们了解特定的视觉算法。

由于OpenCV.js能够直接在浏览器中运行，因此OpenCV.js教程网页将更加直观并具有交互性。例如，使用WebRTC API和测试JavaScript代码时将允许开发人员更改CV函数的参数，并在网页上进行实时CV编码以实时查看结果。

**⚠️：建议您先了解JavaScript和Web应用程序开发，以便更加容易的了解本指南。**

## 贡献者

下面是OpenCV.js和教程的贡献者列表。

- Sajjad Taheri (Architect of the initial version and GSoC mentor, University of California, Irvine)
- Congxiang Pan (GSoC student, Shanghai Jiao Tong University)
- Gang Song (GSoC student, Shanghai Jiao Tong University)
- Wenyao Gan (Student intern, Shanghai Jiao Tong University)
- Mohammad Reza Haghighat (Project initiator & sponsor, Intel Corporation)
- Ningxin Hu (Students' supervisor, Intel Corporation)