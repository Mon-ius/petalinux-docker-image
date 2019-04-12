# petalinux-docker-image

Quick start petalinux SDK environment for development of Zynq system.

Docker Hub Page: [monius/petalinux](https://hub.docker.com/r/monius/petalinux)

Attention: Current petalinux version is <span style="color:red"> *2018.3* </span>.

## Usage

- ` docker run -it monius/petalinux:latest` (defualt: ubuntu16.x)
- ` docker run -it monius/petalinux:ubuntu16.x` 
- ` docker run -it monius/petalinux:ubuntu18.x` 
- ` docker run -it monius/petalinux:debian9.x` 

## Tags

- monius/petalinux:ubuntu16 (Test passed)
- monius/petalinux:ubuntu18 (Test passed)
- monius/petalinux:debian9  (Installed passed, test failed)

## Tips

- Large files in git : `git lfs install`
- To exit QEMU : press Ctrl+A together, release and then press X.


## MIT License

Copyright (c) 2019 Monius

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
