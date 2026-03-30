
待测方法代码：

其中存在多次的readLine操作，如果希望每次readLine得到的结果不同，则需要考虑在桩中进行计数返回不同结果的方式。

```
public void write_file() throws IOException{
BufferedReader brd = new BufferedReader(new InputStreamReader(System.in));
fileName = brd.readLine();
System.out.println("please input a file name:");
System.out.println("please input the data you want to write into a file:");
try {
wrd = new BufferedWriter(new FileWriter(fileName));
} catch (IOException e) {
e.printStackTrace();
}
while((buff = brd.readLine())!=null){
wrd.write(buff);
// buff = brd.readLine();
}
wrd.close();
brd.close();
}
```

构造方法中声明并初始化:

```
public class BufferPracticeTest extends PackageTestCase {
protected static jtest.StubIterationCounter _stubs_iteration = null;
/**
 * Constructor for test class.
 *
 * @author Parasoft Jtest 9.6
 */
public BufferPracticeTest() {
/*
 * This constructor should not be modified. Any initialization code
 * should be placed in the setUp() method instead.
 */
}
```

Setup初始化方法中进行\_stubs\_iteration实例化：

```
public void setUp() throws Exception {
/*
 * Add any necessary initialization code here (e.g., open a socket).
 * Call Repository.putTemporary() to provide initialized instances of
 * objects to be used when testing.
 */
super.setUp();
// jtest.Repository.putTemporary("name", object);
_stubs_iteration = new jtest.StubIterationCounter();
}
```

具体的桩方法中进行Switch判断计数并设定不同的return值：

```
public java.lang.Object stubsWrite_file1(Member method, Object _this, Object[] args) throws Throwable {
Class[] argument_types;
if (Stubs.matches(method, BufferedReader.class)) {
argument_types = new Class[] { Reader.class };
if (Stubs.matches(method, argument_types)) {
return (BufferedReader) Stubs.makeStubObject(BufferedReader.class);
}
     argument_types = new Class[] {};
     String file_name = "C:\\Users\\kwang\\Desktop\\test.txt";
     if (Stubs.matches(method, "readLine", argument_types)) {
          int index = _stubs_iteration.getIterationCount("java.io.BufferedReader.readLine()");
     switch (index) {
case 1:
return file_name;
case 2:
return "我是真的不知道最近大家是怎么了，老是聒噪不安和吵架，希望一切尽快恢复平静！\n";
case 3:
return null;
default:
return Stubs.NO_STUB_GENERATED;
}
}
```
