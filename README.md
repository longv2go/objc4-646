Apple Source libobjc
------
Object-c的runtime库libobjc.dylib的源码是开源的，[Apple Opensource源](http://opensource.apple.com/source/objc4/objc4-646/)，或者 [github源](https://github.com/longv2go/objc4)。
这个工程下载下来并不能直接编译，需要很多苹果的其他头文件，[参见教程。](http://blog.csdn.net/proteas/article/details/7822065)这样编译起来比较麻烦，本repo的目的主要是提供一个patch然后下载最新的objc4源码，用git把补丁打上就能编译。

#使用方法

1. 下载objc4的源码
	```git clone https://github.com/longv2go/objc4```
2. 下载本repo的objc4-646.patch到objc4的源码目录
3. 打开命令行，进入到objc4的源码目录病执行```git apply objc4-646.patch```

这样当前的objc4就可以直接编译了，注意我只在当前的646版本上测试过。这个patch主要是添加了一些必要的头文件，放在工程中的include目录下，并且去掉了项目中的LIBC_NO_LIBCRASHREPORTERCLIENT预编译宏。


#测试调试
objc4源码里面有一个test目录，里面有很多的测试代码，你可以直接在xcode中创建个新的target然后包含这些源码，并且新建的target要连接到libobjc.A.dylib target上，这样就可以直接测试调试了。

#参考
1. [https://github.com/longv2go/nixpkg](https://github.com/longv2go/nixpkgs)
2. [https://github.com/RetVal/objc4-532.2](https://github.com/RetVal/objc4-532.2)