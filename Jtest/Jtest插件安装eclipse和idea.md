

一. 环境信息  
OS：Redhat/Windows  
IDE:  
Eclipse 4.4.2  
IDEA 2018.1  
根据以上信息和Parasoft官方手册，推荐试用Parasoft Jtest 2021.2 。

二. Eclipse 环境Jtest插件安装  
在Jtest安装目录下中提供针对Eclipse环境的插件包，通常位置如下：  
`[JTEST_INSTALL_DIR]\jtest\integration\eclipse\jtest_plugin_2021.2.0_eclipse.zip`

1. 先将Jtest安装包解压到任意目录。
2. 在Eclipse菜单栏中选择"Help> Install New Software"。
3. 点击"Add"。
4. 点击"Archive"，然后选择"`<INSTALL_DIR>\integration\eclipse\jtest_plugin_<version>_eclipse.zip`"。
5. 选择Parasoft Jtest插件并完成安装过程。这将同时安装Parasoft插件和Parasoft Jtest插件。  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579ae72d3459.webp)
6. 在提示时重启Eclipse。

三. IDEA 环境Jtest插件安装  
在Jtest安装目录下提供了2个插件 - Parasoft通用插件和Jtest插件，必须同时安装这两个插件：

1. 在任意目录解压Jtest安装包。
2. 在IntelliJ菜单栏中选择 文件>设置，然后选择 插件。
3. 点击齿轮图标菜单，选择 从磁盘安装插件...，然后选择\integration\intellij\parasoft*plugin*\_intellij.zip，并点击确定。  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579ae9f2a7cd.webp)  
   4.点击齿轮图标菜单，选择 从磁盘安装插件...，然后选择 jtest\_plugin\_\_intellij.zip，并点击确定。  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579aed220556.webp)
4. 重启IntelliJ。

四. 许可证和引擎配置  
4.1 引擎配置  
选择Parasoft菜单==> 设置，如下图示：  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579af2a033f7.webp)  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579af9c2860e.webp)  
4.2 许可证配置  
许可证的配置分为锁定许可证和浮动许可证，如果是浮动许可证，则需要配置连接DTP，如下图示：  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b00f8ea8b.webp)  
注：需要确保DTP的8443端口可以连接。
