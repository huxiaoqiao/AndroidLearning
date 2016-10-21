### 如何在github上下载单个文件夹

> 使用SVN即可

##### 比如这个项目：[https://github.com/facebook/infer](https://github.com/facebook/infer) ,我只想down`examples/android_hello`这个文件夹怎么办？

先打开`examples/android_hello`，其URL为： https://github.com/facebook/infer/tree/master/examples/android_hello

将`/tree/master/`换成`/trunk/`.变为https://github.com/facebook/infer/trunk/examples/android_hello

然后终端输入：`svn checkout https://github.com/facebook/infer/trunk/examples/android_hello`

PS：第一次使用的话，可能会出现下面这个提示：

`R)eject, accept (t)emporarily or accept (p)ermanently?`

输入P就行了.







