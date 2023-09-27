## React Native环境配置与快速打包

#### 问题描述

相信大家都知道HBuilder编辑器软件吧，它有个功能就是可以将自己写的移动端项目打包成App项目，但是它是将我们自己写的代码提交到HBuilder的服务器端，很多大企业是不会将自己的源代码提交到别的服务器来打包的，所以就有必要自己来配置打包环境并且打包代码了。


### 安装最新版本的java jdk
1. 修改环境变量，新增`JAVA_HOME`的系统环境变量，值为`C:\Program Files (x86)\Java\jdk1.8.0_112`，也就是安装JDK的根目录
2. 修改系统环境变量`Path`，在`Path`之后新增`%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;`
3. 新建**系统环境变量**`CLASSPATH`，值为`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`
4. 保存所有的系统环境变量，同时退出系统环境变量配置窗口，然后运行cmd命令行工具，输入`javac`，如果能出现javac的命令选项，就表示配置成功！

### 安装Node.js环境
注意：需要安装最新的长期稳定版本，不要实验版本；安装完毕之后的node.js会自动配置到全局系统环境变量中
安装完毕后，可以输入`node -v`查看node版本号；

### 安装C++环境
大多数情况下操作系统自带C\++环境，不需要手动安装C\++环境；
如果运行报错，则需要手动安装visual studio中的C\++环境；

### 安装Git环境
Git安装完毕后，会自动配置到系统环境变量中；
可以通过运行`git --version`来检查是否正确安装和配置了Git的环境变量；

### 安装Python环境
1. 注意：安装Python时候，只能**安装2.×的版本**，注意勾选安装界面上的`Add Python to path`，这样才能自动将Python安装到系统环境变量中；
2. 安装完毕之后，可以在命令行中运行`python`，检查是否成功安装了python。

### 配置安卓环境
1. 安装`installer_r24.3.4-windows.exe`，最好手动选择安装到C盘下的android目录
2. 打开安装根目录，将`android-25`、`android-23`(react-native必须依赖这个)解压后，放到`platforms`文件夹下
3. 解压`platform-tools`，放到`platform-tools`文件夹下
4. 【这一步直接忽略即可！】**tools文件夹不解压覆盖也行；**~~解压`tools`，放到安装根目录中~~
5. 解压`build-tools_r23.0.1-windows.zip(react-native必须依赖这个)`、`build-tools_r23.0.2-windows.zip(weex必须依赖这个)`和`build-tools_r23.0.3-windows.zip`，并将解压出来的文件夹，分别改名为版本号`23.0.1`、`23.0.2`和`23.0.3`；在安装目录中新建文件夹`build-tools`，并将改名为版本号之后的文件夹，放到新创建出来的`build-tools`文件夹下
6. 在安装根目录中，新建`extras`文件夹，在`extras`文件夹下新建`android`文件夹；解压`m2responsitory`文件夹和`support`文件夹，放到新建的`extras -> android`文件夹下
7. 配置安装环境变量：在系统环境变量中新建`ANDROID_HOME`，值为android SDK Manager的安装路径`C:\Users\user\AppData\Local\Android\android-sdk`，紧接着，在Path中新增`;%ANDROID_HOME%\tools;%ANDROID_HOME%\platform-tools;`

## [ReactNative快速打包](http://reactnative.cn/docs/0.42/getting-started.html)
1. 安装完node后建议**设置npm镜像**以加速后面的过程（或使用科学上网工具）。注意：**不要使用cnpm！**cnpm安装的模块路径比较奇怪，packager不能正常识别！
 > npm config set registry https://registry.npm.taobao.org --global<br/>
 > npm config set disturl https://npm.taobao.org/dist --global

2. Yarn、React Native的命令行工具（react-native-cli）
 + Yarn是Facebook提供的替代npm的工具，可以加速node模块的下载。React Native的命令行工具用于执行创建、初始化、更新项目、运行打包服务（packager）等任务。
 	> npm install -g yarn react-native-cli

 + 安装完yarn后同理也要设置镜像源：
     > yarn config set registry https://registry.npm.taobao.org --global<br/>
     > yarn config set disturl https://npm.taobao.org/dist --global

3. 运行`react-native init myProject`创建React-Native项目

 + 我在创建项目的时候有报错，报错如下：
 ![](https://i.imgur.com/3GsA6il.png)
 ##### 这里出现类似错误的解决方案：将上面第一步和第二步重新运行一遍即可解决问题

4. 运行`cd AwesomeProject`切换到项目根目录中，运行`adb devices`来确保有设备连接到了电脑上
5. 运行`react-native run-android`打包编译安卓项目，并部署到模拟器或开发机中
6. 运行上一条命令之前，要确保有设备连接到了电脑上，可以运行`adb devices`查看当前接入的设备列表，`adb connect 127.0.0.1:62001`(62001是夜神模拟器的默认端口)

》 到这步如果有报错时：

参考这篇文章： [http://www.open-open.com/lib/view/open1477469117948.html](http://www.open-open.com/lib/view/open1477469117948.html)

来自：[http://blog.csdn.net/coder_nice/article/details/52933187](http://blog.csdn.net/coder_nice/article/details/52933187)

安装包下载地址：[https://github.com/Goorln/react-native-packages.git](https://github.com/Goorln/react-native-packages.git)
	
