# Maven的基本操作



* ## Maven的介绍

  Maven是Apache的一款开源的项目管理工具。

  以后无论是普通javase项目还是javaee项目，我们都创建的是Maven项目。

  Maven使用项目对象模型(==POM-Project Object Model,项目对象模型==)的概念,可以通过一小段描述信息来管理项目的构建，报告和文档的软件项目管理工具。在Maven中每个项目都相当于是一个对象，对象（项目）和对象（项目）之间是有关系的。关系包含了：**依赖**、**继承**、**聚合**，实现Maven项目可以更加方便的实现导jar包、拆分项目等效果。

  Maven仓库是基于简单文件系统存储的，集中化管理Java API资源（构件）的一个服务。

  仓库中的任何一个构件(项目)都有其唯一的坐标，根据这个坐标可以定义其在仓库中的唯一存储路径。得益于 Maven 的坐标机制，任何 Maven项目使用任何一个构件Java API资源的方式都是完全相同的。
  **Maven 可以在某个位置统一存储所有的 Maven 项目共享的构件，这个统一的位置就是仓库，项目构建完毕后生成的构件也可以安装或者部署到仓库中，供其它项目使用。**
  对于Maven来说，仓库分为两类：本地仓库和远程仓库。

* ## Maven[官网](https://maven.apache.org/)下载

  ![image-20201109205206335](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084821.png)

然后点击Download，滑到下方找到Previoud Release 然后the archives 是3.0.4版本以上的，如果还要下载更老版本的就点击legacy archives  咱们主要用3..6.1版本的(听说和IDEA配合没什么毛病，最新的版本容易出毛病)

![image-20201109205304918](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084822.png)

![image-20201109205542393](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084823.png)

找到要下载的版本之后，点击进去binaries

![image-20201109205643024](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084824.png)

**下载windows版本的就行**

![image-20201109205720116](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084825.png)

* ## 配置环境变量

  * M2_HOME

  * MAVEN_HOME

  * 在系统的Path中配置MAVEN_HOME

    ![image-20201109210841023](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084826.png)

%JAVA_HOME%\bin;

C:/windows/system32/;

D:\developer_tools\Git\cmd/;

==%MAVEN_HOME%\bin;==

测试MAVEN是否配置成功

![image-20201109211611673](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084827.png)





# 配置阿里云镜像仓库

作用：加速我们的下载

1. 首先打开MAVEN安装目录的conf文件夹

   ![image-20201109211945928](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084828.png)

用Notepad++打开

![image-20201109212030608](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084829.png)

找到mirrors插入一个阿里云镜像(百度搜一下就有)

![image-20201109212110085](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084830.png)

# 本地仓库

* 在本地的仓库，本地仓库指本机的一份拷贝，用来缓存远程下载，包含你尚未发布的临时构件。

  建立本地仓库：loaclRepository

  现在安装目录下新建一个maven-repository目录

  ![image-20201109212713879](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084831.png)

  然后再去conf找到settings.xml新增一下本地仓库的设置

  ![image-20201109212923262](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084832.png)

```xml
D:\JavaJDK\apache-maven-3.6.1-bin\apache-maven-3.6.1\maven-repository
```

然后IDEA其实已经整合了maven打开settings找到

![image-20201109214507979](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084833.png)

可以看到默认的是3.6.1版本的但是我们不用这个，还是用我们自己下载的。将下载好的MAVEN目录指定到Maven home directory

接下来我们还要设置User settings file 和local  repository  如下图 

![image-20201109215054811](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084834.png)



* 对于首次安装MAVEN的用户来说咱们的 用户目录下并不存在.m2文件这是MAVEN并没有使用通过win+r输入cmd进入命令行窗口输入以下命令

* ```xm
  mvn help:system
  ```

  如果你没有该本地仓库的地址的话就会生产.m2文件(注意打开隐藏文件)





# 远程仓库

不在本机中的一切仓库，都是远程仓库：分为==中央仓库 和  本地私服仓库==
远程仓库指通过各种协议如file://和http://访问的其它类型的仓库。这些仓库可能是第三方搭建的真实的远程仓库，用来提供他们的构件下载（例如repo.maven.apache.org和uk.maven.org是Maven的中央仓库）。其它“远程”仓库可能是你的公司拥有的建立在文件或HTTP服务器上的内部仓库(不是Apache的那个中央仓库，==而是你们公司的私服，你们自己在局域网搭建的maven仓库==)，用来在开发团队间共享私有构件和管理发布的。

默认的远程仓库使用的Apache提供的中央仓库：

https://mvnrepository.com/



![image-20201110153751489](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084835.png)

![image-20201110153927248](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084836.png)

**仓库的优先级问题：**

![image-20201126111403723](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201126111410.png)

# 配置JDK

当你的idea中有多个jdk的时候，就需要指定你编译和运行的jdk：
在settings.xml中配置：

```xml
<profile>
                <!-- settings.xml中的id不能随便起的 -->
                <!-- 告诉maven我们用jdk1.8 -->
                <id>jdk-1.8</id>
                <!-- 开启JDK的使用 -->
                <activation>
                                <activeByDefault>true</activeByDefault>
                                <jdk>1.8</jdk>
                </activation>
                <properties>
                        <!-- 配置编译器信息 -->
                        <maven.compiler.source>1.8</maven.compiler.source>
                        <maven.compiler.target>1.8</maven.compiler.target>
                        <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
                </properties>
    </profile>
```

配置的前提是你的idea中要有1.8的jdk



# Maven工程类型

【1】POM工程
**POM工程是逻辑工程。**用在父级工程或聚合工程中。用来做jar包的版本控制。

【2】JAR工程
将会打包成jar，用作jar包使用。即常见的本地工程 ---> Java Project。

【3】WAR工程
将会打包成war，发布在服务器上的工程。



# 在IDEA中创建Maven工程

![image-20201110155223317](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084837.png)

![image-20201110155253829](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084838.png)

给工程取个名字点击Finish就行了



![image-20201110155407585](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084839.png)

## Maven的项目结构

❀src/main/java  
**这个目录下储存java源代码**

❀src/main/resources 
**储存主要的资源文件。比如xml配置文件和properties文件**

❀src/test/java 
**储存测试用的类，比如JUNIT的测试一般就放在这个目录下面**
**因为测试类本身实际是不属于项目的，所以放在任何一个包下都显得很尴尬，所以maven专门创建了一个测试包**
**用于存放测试的类**

❀src/test/resources (这个默认生成的没有，可以自己新建一个)
**可以自己创建，你储存测试环境用的资源文件**

❀src 
**包含了项目所有的源代码和资源文件，以及其他项目相关的文件。**

❀target (右侧点击Maven,然后再点击install就会生成)
**编译后内容放置的文件夹**  

❀pom.xml 
**是Maven的基础配置文件。配置项目和项目之间关系，包括配置依赖关系等等**

```java
--MavenDemo 项目名
  --.idea 项目的配置，自动生成的，无需关注。
  --src
    -- main 实际开发内容
         --java 写包和java代码，此文件默认只编译.java文件
         --resource 所有配置文件。最终编译把配置文件放入到classpath中。
    -- test  测试时使用，自己写测试类或junit工具等
        --java 储存测试用的类
  pom.xml 整个maven项目所有配置内容。
```

![image-20201110155822192](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084840.png)

![image-20201110155942313](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084841.png)

接着就会出现target

![image-20201110161038306](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084842.png)

当前项目的jar包会出现在项目所在目录下与此同时Maven的本地仓库还有一份

![image-20201110161204029](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084843.png)

# POM模式和Maven工程关系

Maven工具基于POM（==Project Object Model，项目对象模型==）模式实现的。在Maven中每个项目都相当于是一个对象，对象（项目）和对象（项目）之间是有关系的。关系包含了：依赖、继承、聚合，实现Maven项目可以更加方便的实现导jar包、拆分项目等效果。

## 依赖

### 特性_依赖的传递性

传递性依赖是Maven2.0的新特性。假设你的项目依赖于一个库，而这个库又依赖于其他库。你不必自己去找出所有这些依赖，你只需要加上你直接依赖的库，==Maven会隐式的把这些库间接依赖的库也加入到你的项目中==。这个特性是靠解析从远程仓库中获取的依赖库的项目文件实现的。一般的，这些项目的所有依赖都会加入到项目中，或者从父项目继承，或者通过传递性依赖。

![image-20201110161812458](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084844.png)

创建A项目后，选择IDEA最右侧Maven面板lifecycle，双击install后就会把项目安装到本地仓库中，其他项目就可以通过坐标引用此项目。

**案例：**

项目1：MavenDemo项目依赖了Mybatis的内容：

![image-20201110163849153](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084845.png)

**注意：请将项目1打包为jar包---》重新打包**

再创建项目2：让项目2依赖项目1：

![image-20201110171800034](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084846.png)

**从上面可以证明：项目2依赖项目1，项目1依赖Mybatis工程，--》传递性---》项目2可以直接使用Mybatis工程**

**注意：在这里发现了一个问题   就是我新建MavenDemo2的时候Maven设置那里还是原来的配置必须要设置和MavenDemo一样的配置才能够实现依赖传递的功能，要不然mybatis的包导入不进来**

![image-20201110172028649](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084847.png)

### 原则_依赖的两个原则

【1】==第一原则：最短路径优先原则==
“最短路径优先”意味着项目依赖关系树中路径最短的版本会被使用。

   例如，假设A、B、C之间的依赖关系是A->B->C->D(2.0)  和A->E->(D1.0)，那么D(1.0)会被使用，因为A通过E到D的路径更短。

【2】==第二原则：最先声明原则==

依赖路径长度是一样的的时候，第一原则不能解决所有问题，比如这样的依赖关系：A–>B–>Y(1.0)，A–>C–>Y(2.0)，Y(1.0)和Y(2.0)的依赖路径长度是一样的，都为2。那么到底谁会被解析使用呢？在maven2.0.8及之前的版本中，这是不确定的，但是maven2.0.9开始，为了尽可能避免构建的不确定性，maven定义了依赖调解的第二原则：第一声明者优先。==在依赖路径长度相等的前提下，在POM中依赖声明的顺序决定了谁会被解析使用。顺序最靠前的那个依赖优胜。==

### 排除依赖

exclusions： 用来排除传递性依赖 其中可配置多个exclusion标签，每个exclusion标签里面对应的有groupId, artifactId, version三项基本元素。注意：不用写版本号。

比如：A--->B--->C (Mybatis.jar) 排除C中的Mybatis.jar    

![image-20201110172153273](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084848.png)

### 依赖范围

***依赖范围就决定了你依赖的坐标 在什么情况下有效，什么情况下无效：***

==1.❀compile==
	这是默认范围。如果没有指定，就会使用该依赖范围。表示该依赖在编译和运行时都生效。**使用scope标签来设置依赖范围**

![image-20201110172559677](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084849.png)

==2.❀provided==
	已提供依赖范围。使用此依赖范围的Maven依赖。典型的例子是servlet-api，编译和测试项目的时候需要该依赖，但在运行项目的时候，由于容器已经提供，就不需要Maven重复地引入一遍(如：servlet-api)

==3.❀runtime==
	**runtime范围表明编译时不需要生效，而只在运行时生效。典型的例子是JDBC驱动实现，**项目主代码的编译只需要JDK提供的JDBC接口，只有在执行测试或者运行项目的时候才需要实现上述接口的具体JDBC驱动。

==4.❀system==
	系统范围与provided类似，不过你必须显式指定一个本地系统路径的JAR，此类依赖应该一直有效，Maven也不会去仓库中寻找它。但是，使用system范围依赖时必须通过systemPath元素显式地指定依赖文件的路径。

==5.❀test==
	test范围表明使用此依赖范围的依赖，只在编译测试代码和运行测试的时候需要，==应用的正常运行不需要此类依赖。典型的例子就是JUnit==，它只有在编译测试代码及运行测试的时候才需要。Junit的jar包就在测试阶段用就行了，你导出项目的时候没有必要把junit的东西到处去了就，所在在junit坐标下加入scope-test

==6.❀Import==
	import范围只适用于pom文件中的<dependencyManagement>部分。表明指定的POM必须使用<dependencyManagement>部分的依赖。
注意：import只能用在dependencyManagement的scope里。



定义一个父工程--》POM工程：只是建立了一个管理依赖的 并不会导入Mybatis

![image-20201110174046650](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084850.png)

注意：工程1要打成自己的jar包

定义一个子工程：

![image-20201110174452990](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084851.png)

**如果父工程中加入 <scope>import</scope>  相当于强制的指定了版本号：**

![image-20201110174542609](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084852.png)

## 继承

【1】继承关系：
如果A工程继承B工程，则代表A工程默认依赖B工程依赖的所有资源，且可以应用B工程中定义的所有资源信息。

被继承的工程（B工程）只能是POM工程。注意：在父项目中放在**dependencyManagement**中的内容时不被子项目继承，不可以直接使用。

放在**dependencyManagement**中的内容主要目的是进行版本管理。里面的内容在子项目中依赖时坐标只需要填写**group id**和**artifact id**即可。（注意：如果子项目不希望使用父项目的版本，可以明确配置version）。

 父工程是一个POM工程：

![image-20201110174845490](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084853.png)

创建子工程：

![image-20201126114750889](https://gitee.com/studylihai/pic-repository/raw/master/%5Cimg/20201126114750.png)

==**本质上：POM文件的继承 ，而不是项目之间的继承关系。**==

## 聚合

​	当我们开发的工程拥有2个以上模块的时候，每个模块都是一个独立的功能集合。比如某大学系统中拥有搜索平台，学习平台，考试平台等。开发的时候每个平台都可以独立编译，测试，运行。这个时候我们就需要一个聚合工程。

在创建聚合工程的过程中，总的工程必须是一个POM工程<packing>pom</packing>（Maven Project）（聚合项目必须是一个pom类型的项目，jar项目war项目是没有办法做聚合工程的），各子模块可以是任意类型模块（Maven Module）。

前提：继承。

聚合包含了继承的特性。

聚合时多个项目的本质还是一个项目。这些项目被一个大的父项目包含。且这时父项目类型为pom类型。同时在父项目的pom.xml中出现**modules**表示包含的所有子模块。

总项目：一般总项目：POM项目



![image-20201110181827549](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084854.png)

具体模块：

![image-20201110181902399](https://gitee.com/studylihai/pic-repository/raw/master/img/20201115084855.png)