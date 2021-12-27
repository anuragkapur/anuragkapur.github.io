Installing glfw - tutorial uses Visual Studio IDE but I want to either work from the CLI or use CLion.
Build via clion, I'm not sure if the libraries are actually being built. I need to understand the basics of CMake first.

https://cmake.org/cmake/help/latest/guide/tutorial/index.html
https://www.glfw.org/docs/latest/compile_guide.html#compile_compile

cmake -S . -B glfw-build
cd glfw-build
make && make install

https://github.com/tuyasa/ClionOpenGLSetUp <- this project builds fine on my machine
https://www.programmersought.com/article/85305491112/ <- looks promising