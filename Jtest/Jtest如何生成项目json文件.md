

在新版Jtest10.3.1中对命令行工具jtestcli进行了改进。对于常规项目只需要指定data参数，即可进行测试。其他选项保持默认，默认的参数选项我们可以在jtestcli.properties文件中查看。  
Jtest10.3.1中的data参数，是用来指定一个json文件，json文件格式及内容如下所示：  
![](https://img.parasoftchina.cn/wb/2023/12/15/657bfe552b6d0.webp)  
这个json文件的作用类似于之前版本的workspace，它指定了测试项目的相关信息。并且是Jtest自动生成的，下面介绍如何在Eclipse环境下自动生成项目的json文件。  
在Eclipse环境中使用Jtest10.3.1对项目进行测试，调高控制台信息。查看控制台输出，可以看到，Jtest在运行测试之前，首先执行了类似如下的命令：

```
[Jtest] Command line: jtestcli -settings 
D:\Workspace\Jtest10.3.1workspace\.metadata\.plugins\com.parasoft.xtest.common.eclipse\jtest\run.20170104-101337\jtest.settings.properties
```

进入对应的jtest.settings.properties文件所在目录，可以看到，同级目录下也有一个jtest.data.json文件，使用这个文件即可进行命令行测试。
