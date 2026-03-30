# Jtest 10.1.2 静态分析与 gradle 的集成

说明：  
本文以Jtest 10.2.1 为例，向大家展示 Jtest 静态分析是如何集成到构建过程的。  
涉及的技术与工具：  
Jtest 10.1.2 gradle 2.2.1

步骤：

1. 运行gradle构建Jtest 10.1.2 的内建项目demo。
2. 在 build.gradle 中添加 parasoft jtest plugin支持。
3. 执行静态分析。  
   步骤1：

安装好gradle，设置好环境变量Path，以方便启动gradle。如： C:\gradle-2.2.1\bin。 在命令行输入gradle -version，提示下图消息，表示配置成功。  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b0d81748a.webp)  
安装好Jtest10.1.2，在安装目录中找内建的项目demo，如： D:\parasoftEngine\jtest\examples\demo。 在命令下cd到该目录，输入gradle compileJava -Djtest.home=d:\parasoftEngine\jtest，提示构建成功则该步骤配置完成。  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b10a8f078.webp)  
步骤2：

略。gradle的具体配置可参考以下文件：

```
D:\parasoftEngine\jtest\examples\demo\build.gradle 
D:\parasoftEngine\jtest\examples\demo\settings.gradle 
D:\parasoftEngine\jtest\integration\gradle\init.gradle
D:\parasoftEngine\jtest\integration\gradle\jtest.gradle。
```

步骤3：

在命令下cd到目录 D:\parasoftEngine\jtest\examples\demo。 输入 `gradle jtest -Djtest.home=d:\parasoftEngine\jtest。`  
提示：  
可以通过修改build.gradle文件中的Jtest部分来指定其它Jtest参数，如：  
文件： D:\parasoftEngine\jtest\examples\demo\build.gradle。  
脚本内容：

```
jtest {
   // enforcing choosen configuration // config = "builtin://Demo Configuration"
    settings = "demo.properties"
    exclude = "path:**/tests/**"
}
```

配置正确可看到如下图所示信息。  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b1e3451db.webp)  
同时在目录 D:\parasoftEngine\jtest\examples\demo 下，可以找到生成文件清单及子目录：

```
build\jtest\jtest.data.json 
build\jtest\.jtest 
build\report\report.html。
```
