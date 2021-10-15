<!--
 Copyright 2017 Sony Corporation.

 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
-->

# NNabla C Runtime

This is a runtime library for inference Neural Network created by [Neural Network Libraries](https://github.com/sony/nnabla).


[Neural Network Libraries](https://github.com/sony/nnabla) and [Neural Network Console](https://dl.sony.com) can output DNN training result as [NNP](https://nnabla.readthedocs.io/en/latest/format.html) file.

[File Format Converter](https://nnabla.readthedocs.io/en/latest/python/file_format_converter/file_format_converter.html) can convert NNP file into `NNB` file interpreted by [Runtime](https://github.com/sony/nnabla-c-runtime/tree/master/src/runtime) or `C Source Code` to call [Functions](https://github.com/sony/nnabla-c-runtime/tree/master/src/runtime).

This library has the following features.

- It is almost **independent from external libraries** and is written in **Pure C** (C99).
  - *almost* mean it depends C standard math library.
- It has been developed with priority over **readability** rather than performance, making it ideal for learning and porting.
- It adopts an **extensible architecture**, and you can use the function you implemented yourself as necessary for applications that need performance.
- Provides [CLI utility](https://github.com/sony/nnabla-c-runtime/tree/master/src/nnablart) that can infer NNB file and dump NNB to confirm network I/O or function list.

## Relative documents


- [Build](doc/BUILD.md)

For Linux

The following is required as prerequisite:
 cmake
 git
 C compiler

For example, on Ubuntu you can install these dependencies with the following command.

$ `sudo apt install build-essential cmake git`

Then, you can build nnabla-c-runtime with following command.

```
$ git clone https://github.com/sony/nnabla-c-runtime.git
$ cd nnabla-c-runtime
$ mkdir build
$ cd build
$ cmake ..
$ cmake --build .

```
After compilation is successfully finished, you can exececute `nnablart.exe` as following:

```
$ ./src/nnablart/nnablart version
C Runtime Version [1.2.0.dev1_c1]
NNB Version [3]
NNB Revision [API_LEVEL_6]
```


For Windows

The following is required as prerequisite:

cmake installed and in your PATH
git installed and in your PATH
Visual C++ compiler available.

The easiest way to install is to use Chocolatey.
Once you set up Chocolatey,

`> choco install cmake git choco visualstudio2019-workload-vctools`

It can be installed with the above command only.
Then,

Open `Visual C++ 2019 x64 Native Build Tools Command Prompt` from windows menu.
```
> git clone https://github.com/sony/nnabla-c-runtime.git
> cd nnabla-c-runtime
> mkdir build
> cd build
> cmake ..
> cmake --build . --config Release
```

After compilation is finished successfully, You can exececute `nnablart.exe`

`>src\nnablart\Release\nnablart.exe version`

> C Runtime Version [1.2.0.dev1_c1]
> NNB Version [3]
> NNB Revision [API_LEVEL_6]

 -[Usage]
 
 `./nnablart infer bin_class.nnb input.bin output_1` in Linux
 `./nnablart.exe infer bin_class.nnb input.bin output_1` in Win
