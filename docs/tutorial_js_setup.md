# 编译 OpenCV.js

## 安装 Emscripten

[Emscripten](https://github.com/kripken/emscripten)是一个可以将C/C++编译成叫做asm.js的javaScript变体的编译器。因为OpenCV是基于C/C++开发的，所以我们将使用Emscripten来编译生成OpenCV.js。

首先，我们需要准备好Emscripten，参考[这篇介绍](https://kripken.github.io/emscripten-site/docs/getting_started/downloads.html)。

For example: 

```shell
$ ./emsdk update
$ ./emsdk install latest
$ ./emsdk activate latest
```

> Note
>
> To compile to [WebAssembly](http://webassembly.org/), you need to install and activate [Binaryen](https://github.com/WebAssembly/binaryen) with the `emsdk` command. Please refer to [Developer's Guide](http://webassembly.org/getting-started/developers-guide/) for more details.

After install, ensure the `EMSCRIPTEN` environment is setup correctly.

For example: 

```shell
$ source ./emsdk_env.sh
$ echo ${EMSCRIPTEN}
```

## Obtaining OpenCV Source Code 

You can use the latest stable OpenCV version or you can grab the latest snapshot from our [Git repository](https://github.com/opencv/opencv.git).

### Obtaining the Latest Stable OpenCV Version

- Go to our [releases page](http://opencv.org/releases.html).
- Download the source archive and unpack it.

### Obtaining the Cutting-edge OpenCV from the Git Repository

Launch Git client and clone [OpenCV repository](http://github.com/opencv/opencv).

For example: 

```shell
$ git clone https://github.com/opencv/opencv.git
```

>  Note
>
> It requires `git` installed in your development environment.

## Building OpenCV.js from Source 

1. To build `opencv.js`, execute python script `<opencv_src_dir>/platforms/js/build_js.py <build_dir>`.

   For example, to build in `build_js` directory: 

   ```shell
   $ cd opencv
   $ python ./platforms/js/build_js.py build_js
   ```

   >  Note
   >
   > It requires `python` and `cmake` installed in your development environment.

2. The build script builds asm.js version by default. To build WebAssembly version, append `--build_wasm` switch.

   For example, to build wasm version in `build_wasm` directory: 

   ```shell
   $ python ./platforms/js/build_js.py build_wasm --build_wasm
   ```

3. [optional] To build documents, append `--build_doc` option.

   For example: 

   ```shell
   $ python ./platforms/js/build_js.py build_js --build_doc
   ```

   >  Note
   >
   > It requires `doxygen` installed in your development environment.

4. [optional] To build tests, append `--build_test` option.

   For example: 

   ```shell
   $ python ./platforms/js/build_js.py build_js --build_test
   ```

   To run tests, launch a local web server in <build_dir>/bin folder. For example, node http-server which serves on `localhost:8080`.

   Navigate the web browser to `http://localhost:8080/tests.html`, which runs the unit tests automatically.

   You can also run tests using Node.js.

   For example: 

   ```shell
   $ cd bin
   $ npm install
   $ node tests.js
   ```

   >  Note
   >
   > It requires `node` installed in your development environment.