

Jtest Examples中有个示例项目叫做Example.initialze的类，其中的Guestbook.java待测文件中可以考虑修改对应的测试类中Setup方法来提高测试覆盖率。

```
Guestbook object = new Guestbook();
object.dataInitialize();
jtest.Repository.putTemporary("name", object);
```

这里的巧妙在于Jtest提供了一个特别的方法设定属性：jtest.Repository.putTemporary("name", object); ，利用该方法可以替换掉后面各测试方法中的TestedObject对象，从而使得Setup中的对象能够生效，进而批量替换后面测试方法中的自动生成的测试类对象。  
自动生成的测试用例：

```
@Test
public void testDisplay0() throws Throwable {
Guestbook testedObject = new Guestbook(); //会被Setup方法中的object替换 
          String result = testedObject.display();
          assertEquals(null, result); // jtest_unverified

          // No exception thrown
          // jtest_unverified
}
```
