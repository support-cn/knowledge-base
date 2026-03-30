

Jtest支持使用数据源进行单元测试，本文以Jtest示例项目JtestExample为例，讲解Jtest如何利用数据源来改变测试用例的输入和输出。

注：本文中使用的Jtest版本为Jtest9.6独立版，操作系统为windows7 64位。

1. 对Jtest Example项目生成测试用例。
2. 在PackageExplorer视图中选择任一具有输入值的测试用例，右键选择>>Jtest>>提取参数化测试用例，看到如下图所示界面：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579aad9ce0ae.webp)

在下一步中选择生成数据源包括：仅原来的测试用例值，并选择对应的数据源文件格式，这里以Excel为例，如下图所示：  
![file](https://img.parasoftchina.cn/wb/2023/12/13/6579aae303c4f.webp)

3. 点击完成，可看到测试用例的结构发生了变化，使用数据源的测试用例单独列出，而原来的测试用例在DefaultTestSuite中。  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579aaecc03cf.webp)  
   并且在测试用例所在的包中生成了对应的Excel数据源文件CustomerTest.xls打开Excel文件，内容如下：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579aaf76a1de.webp)
4. 查看对应的测试用例，内容如下图：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579aafd5a056.webp)  
   可以看出，在原来的CustomerTest.java文件中增加了一个子类，用于测试Customer方法，在这个子类中首先从数据源获取对应的输入参数，即Excel表格中的\_name和\_zip列。然后用获取到的参数作为输入值对Customer()方法进行测试，同时在测试方法中断言Customer对象的name和zip的值分别与Excel表格中\_outcome0和\_outcome1的值相等。
5. 运行该测试用例，结果如下：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579ab05c384f.webp)  
   在Excel表格中添加一行输入并保存，如下图所示：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579ab0e6da49.webp)  
   再次运行测试用例，结果如下图：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579ab1647695.webp)  
   由于Excel表格中第二行的\_name和\_zip的值与\_outcome0和\_outcome1的值均不相等，执行数据源第二行输入值时断言失败。
6. 如果想要使用已有的数据源进行测试，则只需保持文件名和Excel表格内容格式与生成的模板一致，替换生成的模板即可。
