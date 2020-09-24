v8delphiwrapper is a Delphi wrapper for V8 JavaScript Engine

##Build v8dll.dll v8delphiwrapper depends on node.js. see building node.js after successfully building node.js, use the *.lib files in directory node-vX.X.X-src\build\Release\lib to build the v8delphiwrapper dll code

https://github.com/zolagiggszhou/v8delphiwrapper.git

1. Node version maybe is 4.4.0, because this version is close to the development time of the original project and can be compiled normally after testing
https://nodejs.org/dist/v4.4.0/
node-v4.4.0. tar.gz

2. Visual studio 2015 (V140) platform Toolset

3. Make sure your node can be compiled and generated normally node.exe File, because compiling V8 dll.dll You need to use the V8 library file generated by node
node-v4.4.0\build\Release\lib
V8_ base_ 0.lib
V8_ base_ 1.lib
V8_ base_ 2.lib
V8_ base_ 3.lib
V8_ libbase.lib
V8_ libplatform.lib
V8_ nosnapshot.lib
V8_ snapshot.lib

4. Add node-v4.4.0\build\Release\lib to the Library Directory of VS （librarypath）

5. Add node-v4.4.0\deps\v8 及 node-v4.4.0\deps\v8\include to the include directory of VS (includepath)

6. Compile project to DLL (ndll.dll)

7. rename V8dll.dll



(the original author only deals with the V8 engine, but not the entire nodejs. There is no such function as setTimeout, Nodejs4.4.0 is a single thread, which uses its own UV event callback mechanism. If nodejs is simply compiled to DLL, it will cause program blocking. It is necessary to use multithreading, modify nodejs source code, control UV signal, trigger by UV callback, and modify related exception handling, etc.)

===========================================================================================================================
1.node版本为4.4.0  因为这个版本接近原项目的开发时间，测试过可以正常编译 
https://nodejs.org/dist/v4.4.0/
node-v4.4.0.tar.gz

2.Visual Studio 2015 (v140) 平台工具集 

3.确定你的node能够正常编译产生node.exe文件，因为编译v8dll.dll需要使用node产生的V8库文件
node-v4.4.0\build\Release\lib
v8_base_0.lib
v8_base_1.lib
v8_base_2.lib
v8_base_3.lib
v8_libbase.lib
v8_libplatform.lib
v8_nosnapshot.lib
v8_snapshot.lib

4.把node-v4.4.0\build\Release\lib加到vs的库目录中  LibraryPath

5.把node-v4.4.0\deps\v8 及 node-v4.4.0\deps\v8\include 添加到包含目录中 IncludePath

6.编译DLL,重命名v8dll.dll

(原作者仅V8处理了V8引擎，没有处理整个nodejs，像setTimeout这样的功能是没有的， nodejs4.4.0是一个单线程，它使用了自己的uv事件回调机制，如果简单地编译nodejs到DLL使用，会造成程序阻塞，必须使用多线程，及修改nodejs的源码，对uv信号进行控制，使用uv的回调触发，以及需要修改相关的异常处理等)