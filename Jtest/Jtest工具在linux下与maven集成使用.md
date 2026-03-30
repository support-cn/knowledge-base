

1. 项目添加maven-parasoft-plugin  
   在项目的pom.xml添加下列内容，如(根据实际情况修改)：

   ```
   <dependency>
     <groupId>Parasoft</groupId>
     <artifactId>jtest</artifactId>
     <version>9.5.0/version> 
   </dependency>
   ```

   以及

   ```
   <plugin>
             <groupId>Parasoft</groupId>
             <artifactId>maven-parasoft-plugin</artifactId>
             <version>3.0</version>
             <configuration>
                 <config>builtin://Static Analysis</config>
       <report>C:\Users\Administrator\Desktop\reportnew</report>  <localsettings>E:\ProgramFiles\Parasoft\Jtest\workspace95\localsettings.txt</localsettings>
             </configuration>
             <executions>
                 <execution>
                    <phase>test</phase>
                     <goals>
                         <goal>eclipse</goal>
                         <goal>jtest</goal>
                     </goals>
                 </execution>
             </executions>
         </plugin>
   ```

   如果是团队的测试配置，则使用`<config>team://ABCD Config</config>`  
   如果需要指定包含(或过滤)某些文件，则使用：

   ```
   <resources>
       <include>log4j/src/main/java</include>
   </resources>
   ```
2. 用Maven编译项目  
   `mvn compile`
3. 项目转换为Eclipse项目  
   由于被测项目在Linux执行，可能开始不是Eclipse项目，需要先转化为Eclipse项目，才能用Jtest分析(不然可能找不到资源)：  
   `mvn eclipse:eclipse`
4. 修改.classpath文件  
   由于转换之后，可能.classpath文件使用的M2\_REPO变量，而该变量在系统中没有添加，在执行测试的时候，会存在找不到依赖jia包，修改方法为：  
   1) M2\_REPO修改为绝对路径，如将M2\_REPO修改为`/home/niscmsadm/appache-maven-3.0.4/repository`  
   2) var改为lib,即 `kind="var"` 改为 `kind="lib"`
5. 测试执行  
   Cd到被测项目下，执行：`mvn parasoft:jtest`
6. Eclipse的样式在Linux下使用  
   该内容与Jtest的样式规则相关，如：FORMAT.IND、FORMAT.OSPL、FORMAT.SAC、FORMAT.SAOP、FORMAT.SC等  
   1) 自定义的一个样式Code\_Style\_Format.xml；  
   2) 样式添加到Eclipse中  
   在windows的eclipse下-》窗口-》首选项-》Java-》Code Style-》Formatter，导入自定义的样式，如下图所示：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b3b7b37d3.webp)  
   3) 启用的样式配置项目指定设置  
   在windows的eclipse下-》窗口-》首选项-》Java-》Code Style-》Formatter下，选择Configure Project Specific Settings…，如下图所示：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b41116a0b.webp)  
   选择一个项目，并确定：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b481633fb.webp)  
   Active Profile选择自定义的样式(如Eclipse [cms])，勾选”Enable project specific settings”，如下图所示：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b4bc25056.webp)  
   项目.settings目录下org.eclipse.jdt.core.prefs文件将会被修改，如下图所示：  
   ![file](https://img.parasoftchina.cn/wb/2023/12/13/6579b5408ef1c.webp)  
   4) 将Linux下对应项目org.eclipse.jdt.core.prefs文件替换  
   将org.eclipse.jdt.core.prefs文件拷贝到Linux被测项目的.settings目录下，并覆盖替换，这样将会使windows下Eclipse的样式起作用。  
   重新执 `mvn parasoft:jtest`
