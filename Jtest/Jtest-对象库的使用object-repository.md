

在Jtest中，我们有时候为了提高覆盖率，需要利用到对象库功能，来帮助快速创建需要的对象类型，从而执行合理的单元测试，提高覆盖率数据。

常见操作方式：

1. 右键想要创建对象的类，选择Parasoft —> Jtest —> 新建对象，从而在对象库中创建出该Class类型的对象。
2. 执行测试配置“Generate and Run Unit Tests”即可利用对象库的对象去生成测试用例和执行。
3. 或者步骤2可以变更为手动操作，在已经生成的测试用例源码文件中，手动修改测试用例代码，将对象的构造方式修改为利用对象库的方式。如下代码：  
   Interpreter testedObject = (Interpreter)Repository.getObject(getTestedClass(), "InterpreterOR");
