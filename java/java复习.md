## 面向对象：

### 类与对象

- 类是一类事物的描述，是**抽象**的。
- 对象是一类事物的实例，是**具体**的。
- 类是对象的模板，对象是类的实体。
- 类是一组相关**属性**和**行为**的集合。

* 类的成员：**成员变量**（有默认值，不需要初始化），**成员方法**，**构造方法**(有参 ，无参)。

* 局部变量需要初始化。

* 成员方法的定义

  ```java
  public void print(){
      System.out.println("");
  }
  ```

  

- 修饰符：**public**、**protected**、**default**、**private**。

- 在创建对象的时候，至少有一个构造方法，构造方法也必须与类同名，且可以有多个构造方法。

- 构造方法不能被调用，只能在实例化的时候被调动

- 实例化一个对象

  ```java
  Student student=new student(XXXX,XXXX,XXXX); 
  ```

  ​				

- 使用对象

  ```java
  student.print();
  student.id=201831773203;
  student.setId(201831782133);
  ```

  

### 三大特性：封装、继承、多态

#### 封装

- 封装组要就是把对象的**状态**和**行为**用**字段**和**方法**定义在 一个类里面，并且**不允许**外界任意调用其内部的功能方法和更改字段值。

|  修饰符   | 类内部 | 同一个包 | 子类 | 任何地方 |
| :-------: | :----: | :------: | :--: | :------: |
|  public   |   √    |          |      |          |
|  default  |   √    |    √     |      |          |
| protected |   √    |    √     |  √   |          |
|  public   |   √    |    √     |  √   |    √     |



#### 继承

- 子类继承父类的属性和方法（非private）。
- 子类对父类方法的重写（一同两小一大）。
- 一个子类不能同时继承多个父类（接口可以），只能一代一代继承。
- 缺点：耦合性高。

- 有点：提高代码的复用性。
- 直接父类和间接父类。
- 一个类只有一个直接父类，且当类没有继承其他类时，默认的直接父类是Object类。
- 子类在实例化之前必须先调用父类的构造方法（一般是无参构造），再去调用自己的构造方法。
- super和this
  - super表示父类的引用，可以调用父类方法，可以调用父类的构造方法（放在第一句）。
  - 当子类实例化时，默认调用的是父类无参构造，可用super指定调用父类的其他构造方法。
  - this调用自己的属性和方法，也可以是构造方法（放在第一位）。
- final
  - final修饰类：这个类不能被继承，但可继承其他类。
  - final修饰方法：该方法不能被重写，但可以它可以重写他的父类方法。
  - 当一个方法被修饰为private时，该方法会隐式地指定为final方法。
  - final修饰变量：数据一旦初始化之后便不能改变。如果是引用类型的变量，则在初始化之后便不能再让其指向另一个对象。

#### 多态

- 定义：指同一个实体同时具有多种形式或者同一个接口，使用不同的实例而执行不同的操作。
- 三个必要条件：继承、重写、父类引用指向子类对象。
- 方法重载（两同一不同）：在类中有多个同名的方法，但是传的参数不同，调用的时候，可以通过传参的类型和个数来决定调用那个方法。



#### 重写与重载的区别

|  区别点  |   重载   |                     重写                     |
| :------: | :------: | :------------------------------------------: |
| 参数列表 | 必须修改 |                 一定不能修改                 |
| 返回类型 | 可以修改 |                 一定不能修改                 |
|   异常   | 可以修改 | 可以减少或删除，一定不能抛出新的或更广的异常 |
|   访问   | 可以修改 |    一定不能做更严格的限制（可以降低限制）    |



#### 引用变量类型转换

- 向上转型（子类——》父类）：自动完成

  ```java
  父类名称 父类对象=子类实例；
  ```

  

- 向下转型（父类——》子类）：强制转换

  ```java
  子类名称 子类对象=（子类名称）父类实例；
  ```

  

- 判断对象是否属于该类：对象名 instance of 类

- 对象的类型和类必须要有继承关系。



## 常用的工具类

#### String类

- A compareTo (B),返回值是参与比较的前后两个字符串的ascll码的差值。	
  - a=b，返回0；
  - a<b，返回小于0的值；
  - a>b，返回大于0的值。

- 如果两个字符串的长度不一样，前面的字符串相等，则返回字符串长度的差值。
- String concat（String str），链接括号里面字符串到前面字符串的结尾。
- boolean equals（Object o），判断两个String是不是一样，不考虑物理地址，只看值。

- Sring[] split（String regx），根据正则表达式“符号”拆分字符串。
- String substring（int beginIndex），返回索引后面的字符串。
- String trim（），返回字符串的副本，忽略前导空白和尾部空白。

#### StringBuffer与SringBuilder

- String类每次在修改的时候，其实是创建新的对象来修改。
- StringBuffer和StringBuilder就直接在原来对象上修改。
- StringBuffer类有线程安全。
- StringBuilder没有线程安全。但是他的速度快，多数情况下使用它。

| 序号 | 方法描述                                                     |
| :--: | ------------------------------------------------------------ |
|  1   | public StringBuffeer append(String s)    追加字符串          |
|  2   | public StringBuffer reverse()    反正字符串                  |
|  3   | public delete(int start,int end)     移除指定字符串          |
|  4   | public insert(int offset,int i)    将int类型转给字符串插入到指定位置 |
|  5   | public replace(int start,int end,String str)    将字符创中的某段位置用其他字符串替代 |

#### 包装类

| 基本类型 | 包装类    |
| -------- | --------- |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| boolean  | Boolean   |
| char     | Character |

- **包装类之间的转换**
  - 基本数据类型——》包装类：自动装箱。
  - 包装类——》基本数据类型：自动拆箱。
  - 基本数据类型——》String：toString()方法。
  - String——》基本数据类型：包装类.parseXXX(字符串)。
  - 包装类——》String：toString()方法。
  - String——》包装：valueOf()方法。

#### Object类

- 所有类的公共父类。

- getClass方法：返回一个对象的实际类型。

- equals方法：比较两个对象的内容是否相等。不过在自定义类中若没有重写equals方法，则比较的是地址。

- toString方法：返回一个对象的字符串表现形式。

- ==：基本数据类型比较值，引用数据类型比较的是地址。

  

## 抽象、接口和内部类

#### 抽象

- 抽象类：不能实例化对象。必须被继承才能使用。

- 使用**abstract class**定义抽象。

- 使用**abstract**定义抽象方法。

- 一个类如果有抽象方法，那么该类必须是抽象类。

- 任何子类必须重写父类的抽象方法，或者声明自身为抽象类。

- 抽象类可以作为子类的模板，规范子类设计。（**模板模式**）

- 如果父类的抽象方法不想被子类重写，可以写成**final abstract**。

- 构造方法、类的静态方法不能声明为抽象方法。

  

#### 接口（interface）

- 接口中的每一个方法是隐式抽象的。（**public abstract**）
- 接口中的变量是隐式的。（**public static final**）。所以必须在接口里面就给变量赋值。
- JDK1.8以后，接口里面就可以有静态方法和方法体了。
- 接口**工厂模式**，制定标准，让别人实现。
- 接口**适配器模式**，使用一个现成的类，他的接口不完全符合你的需求，只是想过要其中的一个方法，不想覆写其他的方法。
- 接口支持多继承。

#### 接口与抽象类的区别（implement）（extends）

![Alt text](https://images2015.cnblogs.com/blog/1064302/201612/1064302-20161230090438195-1243745647.png)



#### static

- 类被加载后，static修饰的方法和变量就可以使用。

- 编写static代码块优化程序性能。

- **静态方法**中**不能**访问了类中**非静态**的方法和变量。

- **非静态方法可以**访问**静态方法**中的成员方法和变量。

- 静态变量只有一个副本，非静态变量有多个副本。

  

#### 内部类

- **成员内部类**

  - 可以无条件的访问外部类的属性和方法（包括private成员和静态成员）。

  - 成员内部类访问外部类的同名成员

    ```java
    外部类.this.成员方法\成员变量
    ```

    

  - 外部类访问成员内部类，必须先创建一个成员内部类对象。

  - 在其他的类里面想创建一个外部类里面的成员内部类对象时，先创建外部类对象。

- **局部内部类**

  - 定义在方法或作用域里的类，访问权限只在方法或作用域里面。
  - 局部内部类就像方法里面的局部变量一样，是不能有public、protected、private以及static修饰符的。

- **匿名内部类**

  - 由于没有名字，所以只能用一次。用来简化代码编写。

  - 不能是抽象类，系统在创建匿名内部类是会立即创建其对象。

  - 不能定义构造器。

  - 使用匿名内部类的前提条件：**必须继承一个父类或实现一个接口。**

    ```java
    /**
             * 1.匿名内部类，用在父类是个抽象类的情况
             * （1）Person 是一个抽象类 ，直接在实例中定义一个方法say();
             */
            Person person = new Person() {
                 
                @Override
                public void say() {
                    System.out.println("hello china!!");
                     
                }
            };
             
            person.say();
    
    
    
    /**
             * 2.匿名内部类，用在父类是个接口的情况
             * （1）InterfacePersonDemo是个接口，直接在实例中定义一个方法eat();
             */
            InterfacePersonDemo interfacePerson = new InterfacePersonDemo() {
                 
                @Override
                public void eat() {
                    System.out.println("I like eat bread!!");
                     
                }
            };
             
            interfacePerson.eat();
    
     /**
             * 3.匿名内部类，用在父类是个可以被继承的情况，父类不能使final的
             */
            Animal animal = new Animal(){
     
                @Override
                public void drink() {
                    System.out.println("drink a water!");
                     
                }
                 
                 
            };
            animal.drink();
    ```

    

- **静态内部类**

  - 静态内部类不依赖外部类，他是不能使用外部类的非静态变量和方法。

  - 静态内部类就是比成员内部类多了**Static**关键字。

    

## 集合框架

- 集合是存储对象的一种常用方式。集合长度是可变 的，自动扩充。

- 数组中可以存储任意数据类型，集合只能存储对象。

- Java API提供的集合类位于java.util包内。

  #### Collection接口

  - 是Set接口和List接口的父类。

  - Set——无序的集合。不允许重复，**HashSet**。

  - List——有序的集合。允许重复 ，**ArrayList、LinkedList**。

    ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201017170100%E9%9B%86%E5%90%88%E6%A1%86%E6%9E%B61.png)

    ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201017170122%E9%9B%86%E5%90%88%E6%A1%86%E6%9E%B62.png)

#### Iterator接口

- Iterator称为迭代器或迭代精灵。主要作用是**遍历 Collection** 集合中的元素。
- ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201017235650Iterator%E6%8E%A5%E5%8F%A31.png)

- Iterator 对于集合才能用，for 不同，只要是循环都可用。
- 因为 Collection 中有 iterator 方法，所以每一个子类集合对 象都具备迭代器。
- 集合**遍历**方式
  - 迭代遍历 ： 优先选择 Iterator 接口 。
  - foreach循环 ： 可以直接用。
  - for 循环 ： 在 （） 内实例化 Iterable 对象 ， 进行遍历。
  - 先用 toArray 方法输出成为数组 ， 再用 foreach 循环。

#### Set接口

- Collection 的子接口。
- 无序，不重复，Set 判断两个对象是否相等用 equals。
- Set接口的实现类
  - HashSet：散列存储，采用哈希技术。
  - TreeSet：有序存储，存入顺序与存储的顺序不同。

- 实现唯一性：重写hashCode( )和 equals( )方法。
- 允许存储一个null值。

#### List接口

- Collection的子接口。

- 有序、可重复。List中的元素都对应一个索引，可以通过索引来访问指定位置 的集合元素（顺序索引从 0 开始）。

- List集合实现类：

  - ArrayList（线程不安全）。线性顺序存储，的大小是可以动态改变，便于查找。

    ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018001714List%E6%8E%A5%E5%8F%A31.png)

  - LinkedList。链表集合，有利于增删改，非常方便的实现我 们数据结构中的常见的Stack(栈)、queue(队列)等。

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018002711LinkedList1.png)

#### Map接口

- 映射关系，Map存储的是键/值对这样以成对的对象组， 一组 是 key, 一组是 value。
- Map 里的 key不允许重复，通过 key 总能找到唯一的 value 与之对应。
- Map 里的 key 集存储方式和对应的 Set 集合中的元素存储 方式一致。
- HashMap允许将null作为一个entry的key或者value。
- Map接口有两个实现：
  - HashMap — key/value对是按照Hash算法存储的。
  - TreeMap — key/value对是排序(按key排序)存储的。

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018003536map%E6%8E%A5%E5%8F%A31.png)

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018003548map%E6%8E%A5%E5%8F%A32.png)

#### Map.Entry

- Entry 是 Map 接口里面的一个内部接口.常用于打印map。
- 该接口用于封装 key- value,有 3 个方法:
  - Object getKey();返回 Entry 里包含的 key 值。
  - – Object getValue();返回 Entry 里包含的 value 值。
  - Object setValue(Object value):设置 Entry 里包含的value 值,并返回新设置的 value 值。

#### 集合类的选择

- Set内存放的元素不允许重复，List存放的元素有一定的顺序。
- Map的应用主要在利用键/值对进行快速查询。
- ArrayList和LinkedList的区别在于随机查询性能上ArrayList要好，但LinkedList的中间元素的插入与删除性能好。
- HashSet和TreeSet的区别在于集合内元素是否排序。



## 异常、泛型

#### 异常

- 在Java中，异常是一个类，产生异常就是创建异常对象并抛 出了个异常对象。

- Java处理异常的方式是**中断处理**。

- **异常体系**：**Throwable**，是Java语言中所有错误或异常的超类。

  - Error：通常指 JVM 出现重大问题如：运行的类不存在或者 内存溢出等。需要修改源代码才能执行。
  - Exception：在运行时运行出现的一些情况，可以通过 try,catch,finally 处理。

- **异常处理两种方式**

  - 捕获异常 ：try catch 直接处理可能出现的异常，虽抛出异常，但是程序能正常执行。

    ```java
    /**
    
    第一种
    
    **/
    try{
     //可能出异常的代码
    } catch(异常类 对象){
     //处理该异常类型的语句
    }
    [finally] {
    //一定会执行的代码
    //catch 块使用 System.exit(1);除外
    }
    
    
    /**
    
    第二种
    
    **/
    public 返回值类型 方法名(参数列表...)throws
    异常类 A,异常类 B... {
    }
    ```

    

  - 声明异常 ：throws让虚拟机去处理，中断处理。

#### 异常的分类

- (编译时异常)：代码在编译时（写代码时）出现的异常。
- RuntimeException(运行时异常)：代码运行过程中出现的问题。

#### throws & throw

- throws 用于在方法上声明该方法**可能**会出现的**异常类型**。
- throw 用于抛出具体**异常类的对象**。
- throws 与 与 throw 的区别 ：
  - thorws 用在方法上，后面跟异常类名,可以是多个异常类。
  - throw 用在方法内，后面跟异常对象,只能是一个。

- 常见的异常
  - ArithmeticException 算术异常，比如1除0。
  - ArrayIndexOutOfBoundsException数组下标越界异常。
  - NullPointerException空指针异常，比如获取null的哈希 码 .hashCode()。
  - ClassCastException类型转换异常。
  - 检查异常，比如加载驱动。

#### 泛型

- 泛型是一种未知的数据类型。

- 泛型也可看成是一种变量，可以接收任意数据类型。

- 创建集合对象时，使用泛型与不使用泛型的差别:

  - 使用泛型：
    - 避免了类型转换，存储的是何种类型，取出也是何种。
    - 把运行时异常转化成编译时异常。

  - 不使用泛型：
    - 可以存储任意类型，但是不安全，容易引发异常。

####  泛型类

- 格式：修饰符 class 类名**<泛型变量>**{ }

#### 泛型方法

- 修饰符 **<泛型变量>** 返回值类型 方法名（参数）{ }
- 在方法调用的时候确定泛型的数据类型。

#### 泛型接口

- 方式1：定义接口的实现类，实现接口的时候，在接口的实现类指定接口的泛型。
- 方式2：接口使用何种泛型，实现类就使用何种泛型。

#### 泛型的通配符

- 不知道使用何种数据类型来接收的时候，可使用泛型的通配符**？**。

- 此时只能接收数据，不能往集合中存储数据。



## 文件与流

#### File类

-  Java中的对文件的管理，通过java.io包中的File类实现。

-  java.io.File类代表硬盘上的一个文件或者文件夹。
-  包含创建、删除、文件等操作。

#### File类的构造方法

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018012529File1.png)

#### File类的相关方法

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018012545File2.png)

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018012555File3.png)

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018012607File4.png)



#### 递归

- 在使用递归时，必须有一个明确的递归结束条件，称为递归出口。比如：输出指定目录中的全部文件的路径。



#### 流

- Java 的 IO 是实现输入和输出的基础。
- 程序需要数据 --> 读进来 --> 输入。
- 程序保存数据 --> 写出去 --> 输出。

#### 流的层次结构图

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018013636%E6%B5%81%E7%9A%84%E5%B1%82%E6%AC%A1%E7%BB%93%E6%9E%84%E5%9B%BE1.png)

![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018013817%E6%B5%81%E7%9A%84%E5%B1%82%E6%AC%A1%E7%BB%93%E6%9E%84%E5%9B%BE2.png)

#### 流的分类

- ① 按 **流动方向**的不同可以分为 **输入流和输出流** ；
- ② 按 **处理数据的单位**不同分为 **字节流和字符流** ；
- ③ 按 **功能的不同**可分为 **节点流和处理流** ；
  - 节点流 ： **直接操作目标设备** ， 例如 ： 磁盘或一块内存区 域 。
  - 处理流 ： 通过**操作节点流,** 从而间接完成输入或输出功能 的流 。 处理流是的存在是建立在一个已经存在的输入流或 输出流的基础之上的。

#### 抽象流

- 所有流都继承于以下四种抽象流类型的某一种： （ 抽象流 ）

  |        |    字节流    | 字符流 |
  | :----: | :----------: | :----: |
  | 输入流 | Inputstream  | Reader |
  | 输出流 | Outputstream | Writer |

  

- java.io包中有两大继承体系

  - 以byte处理为主的Stream类，他们的命名方式是XXXStream。
  - 以字符处理为主的Reader /Writer类，他们的命名方式 XXXReader或XXXWriter。

#### 字节流

- 传输的数据单位是字节，也意味着字节流能够处理任何一 种文件。

- **InputStream**

- ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018015345%E5%AD%97%E8%8A%82%E8%BE%93%E5%85%A5%E6%B5%81InputStream1.png)

- **OutputStream**

  ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018015357%E5%AD%97%E8%8A%82%E8%BE%93%E5%87%BA%E6%B5%811.png)





#### 字符流

- **Reader**

  ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018015345%E5%AD%97%E8%8A%82%E8%BE%93%E5%85%A5%E6%B5%81InputStream1.png)

- **Writer**

  ![Alt text](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018015357%E5%AD%97%E8%8A%82%E8%BE%93%E5%87%BA%E6%B5%811.png)

#### 字节流与字符流

- 一般来说处理字符或字符串时使用字符流，处理字节或二进制对 象时使用字节流。
- **字符流必须关闭资源**，因为它中间有缓冲区！而**字节流不需要**！ 但是一般都会（最后）关闭资源。
- Java 中的字符是 Unicode 编码,是双字节的,1 个字符 等于 2 个字节;
- 字节流 ：程序 → 文件。
- 字符流 ：程序 → 缓冲区 （ 内存中） ） → 文件。
- 在输出的时候， **OutputStream 类即使最后没有关闭内容也 可以输出**。 但是**如果是 Writer的话 ， 则如果不关闭 ，最后 一条内容是无法输出的** ， 因为所有的内容都是保存在了缓冲 区之中 ， 每当调用了 close() 方法就意味着清空缓冲区了 。 那么可以证明字符流确实使用了缓冲区 。
- 如果现在字符流即使不关闭也可以完成输出的话，则必须强制 性清空缓冲区。
- 两者相比 ， 肯定使用字节流更加的方便 ， 而且在程序中像 图片 、MP3 等都是采用字节的方式的保存 ， 那么肯定字节 流会比字符流使用的更广泛 。
- 如 果要是想操作中文的话 ， 字符 流肯定是最好使的（ 字节流的话,可能会出现乱码 （一个汉字 分成了两份）)。



#### 操作流的步骤

```java
A. 使用 File 类找到一个文件对象,  得到 IO 操作的源或目标.
B. 通过字节流或字符流的子类创建对象 ,( 得到 IO 操作的通
道).
C. 进行读或写的操作,(IO 操作) .
D. 关闭输入/ 输出 ,( 打完收工, , 注意节约资源, 关掉) ).
```

- 由于流的操作属于资源操作，所以在操作的最后一定要关闭以 释放资源 。

#### 节点流与处理流的使用

- 在java.io包中，**字节继承体**系有**三种**节点类，而**字符继承体** 系有**四种**节点类

  ![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018021133%E5%9C%A8java.io1.png)

- 字节流方法

  ![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018021538%E8%8A%82%E7%82%B9%E6%B5%81%E7%9A%84%E6%96%B9%E6%B3%95.png)

- **Reader类**中没有available方法，取而代之的是”**ready**”方 法，这个方法会去检查Reader对象是否已经准备好输入数据 了，如果是返回true，反之返回false。



#### 处理流

![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018022411%E5%A4%84%E7%90%86%E6%B5%811.png)

####  文件过滤器

- java.io.FilenameFilter
- File 类里有方法： String[] list(FilenameFilter filter) 返回一个 字符串数组，这些字符串指定此抽象路径名表示满足指定过滤器的 文件和目录。
- FilenameFilter(文件过滤器)该接口里包含 accept(File dir,String name)方法，该方法依次对指定File 的所有子目录，子文件夹进行 迭代。
  - dir - 被找到的文件所在的目录。
  - name - 文件的名称。

- 当且仅当该名称应该包含在文件列表中时返回 true；否则返回 false。



#### 	内存流

- 操作内存流的时候（从内存读取出来，注意一定要把 真正的 数据用toByteArray 或者toCharArray将数据读出来 ）。
- 之前的文件操作流是以文件的输入输出为主的 ， 当输出的位 置变成了内存 ， 那么就称为内存操作流 。 此时 要 使用内存 流完成内存的输入和输出操作 。
- 如果程序运行过程中要产生一些临时文件 ， 可采用虚拟文件 方式实现 ；直接操作磁盘的文件很耗性能, 使用内存流可以提 升性能;jdk 里提供了内存流可实现类似于 内存虚拟文件的功能。
  - ByteArrayInputStream ： 将内容写到内存中 CharArrayReader。
  - ByteArrayOutputStream ： 将内存中的数据写出 CharArrayWriter。

#### 打印流

- PrintWriter PrintStream。
- 打印流有非常好的打印功能，可以打印任何的数据类型。如， 整数，小数，字符串等。
- PrintWriter 和 和 PrintStream 都属于输出流 ， 分别针对 字符和字节 。
- PrintWriter 和 PrintStream 重载的 print()和 println()用 于多种数据类型的输出。
- print() 里的参数不能为空 ；println() 可以。
- PrintWriter 和 PrintStream 输出操作不抛出异常。
- PrintStream 调用 println 方法有自动 flush 功能。

#### 缓冲流

![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018023346%E7%BC%93%E5%86%B2%E6%B5%811.png)

![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018023549%E7%BC%93%E5%86%B2%E6%B5%812.png)

#### 合并流

- 需要两个源文件，一个输出的目标文件。
- SequenceInputStream：将两个文件的内容合并成一个文件。
- 该类提供的方法：
  - SequenceInputStream(InputStream s1, InputStream s2) ：根据两个字节输入流对象来创建合并流对象。

- 备注：谁放在前面，谁就先打印出来





## 多线程编程

#### 进程与线程

- **进程**：指一个内存中运行的应用程序。**一个进程**中可以有**多个线程**，每个进程都有自己独立的一块内存空间。
  -  进程有独立的进程空间，进程中的数据存放空间（堆空间和栈 空间）是独立的。

- **线程**：指进程中的一个执行任务(控制单元)，一个进程中可以运行多个线程,多个线程可共享数据。
  - 线程的堆空间是共享的，栈空间是独立的，线程消耗的资源也 比进程小，相互之间可以影响的。
- 多线程存在一个特性： 随机性。虽然同时运行，但是每一次结果都不一致。
  - 随机性造成的原因 ：CPU 在瞬间不断切换去处理各个线程而 导致的 。可以理解成多个线程在抢 cpu 资源。



#### 创建线程的方式

- 方式1

  ```java
  ① 继承 Thread 类（方式1）
  – 子类覆写父类中的 run 方法，将线程运行的代码存放在
  run 中。
  – 建立子类对象的同时线程也被创建。
  – 通过调用 start 方法开启线程。
  ```

  

- 方式2

  ```java
  ② 实现 Runnable 接口（方式2）
  – 子类覆盖接口中的 run 方法。
  – 通过 Thread 类创建线程，并将实现了 Runnable 接口的
  子类对象作为参数传递给 Thread类的构造函数。
  – Thread 类对象调用 start 方法开启线程。
  – 可使用匿名内部类来写
  ```

#### 两种创建线程方式的比较

```java
① A extends Thread（继承类）：
– 简单
– 不能再继承其他类了(Java 单继承)
– 同份资源不共享
② A implements Runnable（实现接口）:(推荐)
– 多个线程共享一个目标资源，适合多线程处理同一份资源。
– 该类还可以继承其他类，也可以实现其他接口。
总结：为了避免单继承的局限性 建议使用第二种方式
```

#### 线程的生命周期

```java
① 新建状态:创建一个线程对象，该线程对象就处于新建状态。
它保持这个状态直到程序 start() 这个线程。
    
② 就绪状态:当线程对象调用了start()方法之后，该线程就进入
就绪状态，并等待JVM里线程调度器的调度。
    
③ 运行状态:如果就绪状态的线程获取 CPU 资源，就可以执行 r
un()，此时线程便处于运行状态。处于运行状态的线程最为复
杂，它可以变为阻塞状态、就绪状态和死亡状态。
    
④ 阻塞状态:如果一个线程执行了sleep（睡眠）、suspend（挂
起）等方法，失去所占用资源之后，该线程就从运行状态进入
阻塞状态。在睡眠时间已到或获得设备资源后可以重新进入就
绪状态。可以分为三种：
– 等待阻塞：运行状态中的线程执行 wait() 方法，使线程进
入到等待阻塞状态。
– 同步阻塞：线程在获取 synchronized 同步锁失败(因为同
步锁被其他线程占用)。
– 其他阻塞：通过调用线程的 sleep() 或 join() 发出了 I/O
请求时，线程就会进入到阻塞状态。当sleep() 状态超时，
 join() 等待线程终止或超时，或者 I/O 处理完毕，线程重
新转入就绪状态。
    
⑤ 死亡状态:一个运行状态的线程完成任务或者其他终止条件发
生时，该线程就切换到终止状态。
```

#### 线程方法

![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018031025%E7%BA%BF%E7%A8%8B%E6%96%B9%E6%B3%951.png)

![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018031037%E7%BA%BF%E7%A8%8B%E6%96%B9%E6%B3%952.png)

#### 线程的优先级

- ① 每个线程都有优先级，优先级的高低只和线程获得执行机会的 次数多少有关。并非线程优先级越高的就一定先执行，哪个线 程的先运行取决于 CPU 的调度。
- ② Thread类的三个常量，表示常用的线程优先级：
  - Thread.MIN_PRIORITY //1
  - Thread.NORM_PRIORITY // 5（默认）
  - Thread.MAX_PRIORITY // 10

![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018031105%E7%BA%BF%E7%A8%8B%E7%9A%84%E4%BC%98%E5%85%88%E7%BA%A71.png)





#### 线程的中断

- ① 自动终止 （推荐）：
  - 开启多线程运行 ， 运行代码通常是循环结构 。 只要控制住循环 ， 就可以让 run 方法结束 ， 也就是线程结束 。

- 手动终止 
  - stop( ) —— 已过时，基本不用 。
  - interrupt( ) —— 粗暴的终止方式。

#### 线程的控制

#### ![](https://images.cnblogs.com/cnblogs_com/songcubi/1865416/o_201018031116%E7%BA%BF%E7%A8%8B%E7%9A%84%E6%8E%A7%E5%88%B61.png)

#### 线程安全

- ① 方式1：同步代码块

  - 通过代码块中的锁对象，可以是任意对象。

  - 但是必须保证多个线程使用的锁对象是同一个。

  - 锁对象作用：把同步代码块锁住，只让一个线程在同步代 码块中执行。

    ```java
    格式：synchronized(锁对象){
     可能会出现线程安全问题的代码
     （访问了共享数据的代码）
    }
    ```

    

- ② 方式2：同步方法

  ```java
  修饰符 synchronized 返回值 方法名（参数列表）{
   可能会出现线程安全问题的代码
   （访问了共享数据的代码）
  }
  ```

  - • 把访问了共享数据的代码抽取出来，放在一个方法中.
  - 在方法上添加synchronized修饰符.

- ② 方式2：静态方法的同步

  ```java
  修饰符 static synchronized 返回值类型 方法名（参数列表）
  {
   可能会出现线程安全问题的代码
   （访问了共享数据的代码）
  }
  ```

  - static不能和this连用.
  - 静态方法的默认同步锁是当前方法所在类的.class

- ③ 方式3：Lock锁

  - Java.util.concurrent.locks.Lock接口，该接口提供了比 使用synchronized方法和语句更广泛的锁定操作.
  - Lock接口中的方法： **Void lock( )获取锁** 、 **Void unlock( )释放锁**。
  - 实现类：java.util.concurrent.locks.ReentrantLock。
  - 使用步骤：
    - 在成员位置创建一个ReentrantLock对象 。
    - 在可能会出现安全问题的代码前调用Lock接口中的方法 lock（）获取锁 。
    - 在可能会出现安全问题的代码后调用Lock接口中的方法 unlock（）释放锁。

#### 线程通信

- ① wait():让当前线程放弃监视器进入等待，直到其他线程调用 同一个监视器并调用 notify()或notifyAll()为止。
- ② notify():唤醒在同一对象监听器中调用 wait 方法的第一个线程。
- ③ notifyAll():唤醒在同一对象监听器中调用 wait 方法的所有线程。

#### Daemon

- ① 后台线程：处于后台运行，任务是为其他线程提供服务。也称为 “守护线程”或“精灵线程”。 
- ② JVM 的垃圾回收就是典型的后台线程。 
- ③ 特点：若所有的前台线程都死亡，后台线程自动死亡。 
- ④ 设置后台线程：Thread 对象 setDaemon(true); 
- ⑤ setDaemon(true)必须在 start()调用前。否则出现 IllegalThreadStateException 异常； 
- ⑥ 前台线程创建的线程默认是前台线程; 
- ⑦ 判断是否是后台线程：使用 Thread 对象的 isDaemon()方法； 
- ⑧ 并且当且仅当创建线程是后台线程时，新线程才是后台线程。



## 网络编程

- 客户端(Client)，服务器(Server)。

- TCP与UDP：

  - UDP: 
    - – 将数据源和目的地封装到数据包中，不需要建立连接 
    - – 每个数据包的大小限制在 **64k** 以内 
    - – 因**无连接** ，是**不可靠协议** 
    - – 不需要建立连接

  - TCP: 
    - – 建立连接 ， 形成传输数据的通道 
    - – 在连接中进行大量数据的传输 
    - – 通过**三次握手**完成连接 、 是可靠协议 
    - – 必须建立连接

- 网络编程三要素：①协议，②IP地址，③端口号

  - ①协议：

    - TCP：传输控制协议 (Transmission Control Protocol)。

    - 三次握手：TCP协议中，在发送数据的准备阶段，客户端与服务 器之间的三次交互，以保证连接的可靠。

      第1次握手：客户端向服务器端发出连接请求，等待服务器确认。

      第2次握手：服务器端向客户端回送一个响应，通知客户端收到了连接请求。

      第3次握手：客户端再次向服务器端发送确认信息，确认连接。

    - 完成三次握手，连接建立后，客户端和服务器就可以开始进行 数据传输了。由于这种面向连接的特性，TCP协议可以保证传 输数据的安全，所以应用十分广泛，例如下载文件、浏览网页 等。



#### 基于TCP的Socket编程

![](https://img2018.cnblogs.com/blog/1592754/201904/1592754-20190429142109609-1802071046.png)



#### 客户端方法

| Socket(String host, int port)  | 构造方法，服务器Ip地址和端口 号，可以找到指定（服务器）设 备上的指定进程 |
| ------------------------------ | ------------------------------------------------------------ |
| OutputStream getOutputStream() | 返回此套接字的输出流。                                       |
| InputStream getInputStream()   | 返回此套接字的输入流                                         |
| void close()                   | 关闭此套接字                                                 |
| void shutdownOutput()          | 禁用此套接字的输出流。                                       |

#### 客户端实现步骤

| 1    | 创建一个客户端对象Socket,构造方法绑定服务器的IP地址和 端口号 |
| ---- | ------------------------------------------------------------ |
| 2    | 使用Socket对象中的方法getOutputStream()获取网络字 节输出流OutputStream对象 |
| 3    | 使用网络字节输出流OutputStream对象中的方法write,给 服务器发送数据 |
| 4    | 使用Socket对象中的方法getInputStream()获取网络字节 输入流InputStream对象 |
| 5    | 使用网络字节输入流InputStream对象中的方法read,读取服 务器回写的数据 |
| 6    | 释放资源(Socket)                                             |

#### 客户端注意事项

| 1    | 套接字:包含了IP地址和端口号的网络单位                        |
| ---- | ------------------------------------------------------------ |
| 2    | 客户端和服务器端进行交互,必须使用Socket中提供的网络流, 不能使用自己创建的流对象 |
| 3    | ---当我们创建客户端对象Socket的时候,就会去请求服务器 和服务器经过3次握手建立连接通路 ---这时如果服务器没有启动,那么就会抛出异常 ConnectException: Connection refused: connect --- 如果服务器已经启动,那么就可以进行交互了 |

#### 服务端方法

| ServerSocket(int port) | 创建绑定到特定端口的服务器套接字。                           |
| ---------------------- | ------------------------------------------------------------ |
| Socket accept()        | 侦听并接受到此套接字的连接 （获取到请求的客户端对象 Socket） |

#### 服务端的实现步骤

| 1    | 创建服务器ServerSocket对象和系统要指定的端口号               |
| ---- | ------------------------------------------------------------ |
| 2    | 使用ServerSocket对象中的方法accept,获取到请求的客户 端对象Socket |
| 3    | 使用Socket对象中的方法getInputStream()获取网络字节 输入流InputStream对象 |
| 4    | 使用网络字节输入流InputStream对象中的方法read,读取 客户端发送的数据 |
| 5    | 使用Socket对象中的方法getOutputStream()获取网络字 节输出流OutputStream对象 |
| 6    | 使用网络字节输出流OutputStream对象中的方法write,给 客户端回写数据 |
| 7    | 释放资源(Socket,ServerSocket)                                |



## JDBC

- ① JDBC(Java Database Connectivity)是一个 独立于特定数 据库管理系统、通用的SQL 数据库存取和操作的公共接口 （一组API），定义了用来访问数据库的标准Java类库， （java.sql,javax.sql）使用这个类库可以以一种标准的方法、 方便地访问数据库资源
- ② JDBC接口（API）包括两个层次： – 面向应用的API：Java API，抽象接口，供应用程序开发 人员使用（连接数据库，执行SQL语句，获得结果）。 – 面向数据库的API：Java Driver API，供开发商开发数据 库驱动程序用。

#### JDBC API

- JDBC API 是一系列的接口，它使得应用程序能够进行数据库 联接，执行SQL语句，并且得到返回结果。

#### Driver接口

- ① java.sql.Driver 接口是所有 JDBC 驱动程序需要实现的接口。 这个接口是提供给数据库厂商使用的，不同数据库厂商提供不 同的实现 。
- ② 在程序中不需要直接去访问实现了 Driver 接口的类，而是由 驱动程序管理器类(java.sql.DriverManager)去调用这些 Driver实现 – Oracle的驱动：oracle.jdbc.driver.OracleDriver – mySql的驱动： com.mysql.jdbc.Driver。

#### 加载与注册 JDBC 驱动

- 方式一：加载 JDBC 驱动需调用 Class 类的静态方法 forName()，向其传递要加载的 JDBC 驱动的类名 。
  - Class.forName(“com.mysql.jdbc.Driver”);

- 方式二：DriverManager 类是驱动程序管理器类，负责管理 驱动程序 。
  - DriverManager.registerDriver(com.mysql.jdbc.Driver);

#### 建立连接(Connection)

- ① 可以调用 DriverManager 类的 getConnection() 方法建立 到数据库的连接 。
- ② User,password可以用“属性名=属性值”方式告诉数据库。
- ③ JDBC URL 用于标识一个被注册的驱动程序，驱动程序管理 器通过这个 URL 选择正确的驱动程序，从而建立到数据库的 连接。 
- ④ JDBC URL ： jdbc: 子协议: 子名称 子协议：数据库驱动程序 子名称：主机名(对应服务端的ip地址)，端口号，数据库名。

#### 几种常用数据库的JDBC URL

![](https://images2017.cnblogs.com/blog/731387/201709/731387-20170904180337429-429131820.png)

```java
1、对于 Oracle 数据库连接，采用如下形式： 
jdbc:oracle:thin:@localhost:1521:sid


2、对于 SQLServer 数据库连接，采用如下形式：
jdbc:microsoft:sqlserver//localhost:1433; DatabaseName=sid


3、对于 MYSQL 数据库连接，采用如下形式： 
jdbc:mysql://localhost:3306/sid
```

#### 访问数据库

- ① 数据库连接被用于向数据库服务器发送命令和 SQL 语句，在 连接建立后，需要对数据库进行访问，执行 sql 语句 。
- ② 在 java.sql 包中有 3 个接口分别定义了对数据库的调用的不同方式： 
  - Statement  
  - reparedStatement 
  - CallableStatement

#### SQL 注入攻击

- ① SQL 注入是利用某些系统没有对用户输入的数据进行充分的 检查，而在用户输入数据中注入非法的 SQL 语句段或命令从 而利用系统的 SQL 引擎完成恶意行为的做法。 
- ② 对于 Java 而言，要防范 SQL 注入，只要用 **PreparedStatement**(从Statement扩展而来) 取代 Statement 就可以了。

#### PreparedStatement

- ① 可以通过调用 Connection 对象的 preparedStatement() 方法获取PreparedStatement 对象 
- ② PreparedStatement 接口是 Statement 的子接口，它表示 一条预编译过的SQL 语句 
- ③ PreparedStatement 对象所代表的 SQL 语句中的参数用问 号(?)来表示，调用 PreparedStatement 对象的 setXxx() 方法来设置这些参数. setXxx() 方法有两个参数，第一个参数 是要设置的 SQL 语句中的参数的**索引(从 1 开始)**，第二个是 设置的 SQL 语句中的参数的值

#### 连接数据库、操作表的步骤

- ① 注册驱动 (只做一次) 
- ② 建立连接(Connection)
-  ③ 创建执行SQL的语句(Statement)
-  ④ 执行语句
-  ⑤ 处理执行结果(ResultSet)
-  ⑥ 释放资源

#### 释放资源

- ① 释放ResultSet, Statement,Connection。 
- ② 数据库连接（Connection）是非常稀有的资源，用完后必须 马上释放，如果Connection不能及时正确的关闭将导致系统 宕机。Connection的使用原则是 **尽量晚创建，尽量早的释放**。

#### ResultSet

- ① 通过调用 PreparedStatement 对象的 excuteQuery() 方法创建该对象。 
- ② ResultSet 对象以逻辑表格的形式封装了执行数据库操作的结果集，ResultSet 接口由数据库厂商实现 。
- ③ ResultSet 对象维护了一个指向当前数据行的游标，初始的时 候，游标在第一行之前，可以通过ResultSet 对象的 next() 方法移动到下一行 – ResultSet 接口的常用方法：
  - boolean next() 
  - getString()

- ① ResultSet: 结果集. 封装了使用 JDBC 进行查询的结果，返 回的实际上就是一张数据表. 有一个指针指向数据表的第一条 记录的前面 
- ② 可以调用 next() 方法检测下一行是否有效. 若有效该方法返 回 true, 且指针下移. 相当于Iterator 对象的 hasNext() 和 next() 方法的结合体 
- ③ 当指针指向一行时, 可以通过调用 getXxx(int index) 或 getXxx(int columnName) 获取每一列的值 – 例如: getInt(1), getString("name") 
- ④ ResultSet 也需要进行关闭

#### JDBC事务处理

- ① 当一个连接对象被创建时，默认情况下是自动提交事务：每次 执行一个SQL 语句时，如果执行成功，就会向数据库自动提交，而不能回滚 。
- ② 为了让多个 SQL 语句作为一个事务执行：
- - 调用 Connection 对象的 setAutoCommit(false); 以取 消自动提交事务 。
  - 在所有的 SQL 语句都成功执行后，调用 commit(); 方法 提交事务。
  -  在出现异常时，调用 rollback(); 方法回滚事务 
  - 若此时 Connection 没有被关闭, 则需要恢复其自动提交状态

#### 数据库事务

- 事务的ACID(acid)属性 。
- 原子性（Atomicity） 。
- 原子性是指事务是一个不可分割的工作单位，事务中的操作要 么都发生，要么都不发生。 
- 一致性（Consistency）。 
- 事务必须使数据库从一个一致性状态变换到另外一个一致性状 态。 
- 隔离性（Isolation） 。
- 事务的隔离性是指一个事务的执行不能被其他事务干扰，即一 个事务内部的操作及使用的数据对并发的其他事务是隔离的， 并发执行的各个事务之间不能互相干扰。 
- 持久性（Durability）。
- 持久性是指一个事务一旦被提交，它对数据库中数据的改变就 是永久性的，接下来的其他操作和数据库故障不应该对其有任何影响。



- ① 以第一个 DML 语句的执行作为开始
- ② 以下面的其中之一作为结束: 
  - – COMMIT 或 或 ROLLBACK 语句 
  - – DDL 或 DCL 语句（自动提交） 
  - – 用户会话正常结束 
  - – 系统异常终了

- ① DDL: 数据定义语言(用来定义数据库结构): create table; alter table; drop table; create index; drop index 。
- ② DCL: 数据控制语言(用来控制数据库的访问)：grant; revoke; commit;rollback; lock; 
- ③ DML: 数据操纵语言(用来查询与更新记录): insert; update; delete

#### 数据库连接池（connection pool ）

- ① 数据库连接池的 基本思想就是为数据库连接建立一个“缓冲 池”。预先在缓冲池中放入一定数量的连接，当需要建立数据 库连接时，只需从“缓冲池”中取出一个，使用完毕之后再放 回去。 
- ② 数据库连接池负责分配、管理和释放数据库连接，它 允许应 用程序重复使用一个现有的数据库连接，而不是重新建立一个。

#### 两种开源的数据库连接

- ① JDBC 的数据库连接池使用 javax.sql.DataSource 来表示， DataSource只是一个接口，该接口通常由服务器(Weblogic, WebSphere, Tomcat)提供实现，也有一些开源组织提供实 现：
  -  – DBCP 数据库连接池 
  - – C3P0 数据库连接池
-  ② DataSource 通常被称为数据源，它包含连接池和连接池管 理两个部分，习惯上也经常把 DataSource 称为连接池 
- ③ DataSource 用来取代DriverManager 来获取Connection ， 获取速度快，同时可以大幅度提高数据库访问速度。





## Java原生动态代理

## DAO 

```java
package com.clive.dao;
public interface UserDao {
public void save();
}
```

## DAO 实现类

```java
package com.clive.dao.impl;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Repository;
import com.clive.dao.UserDao;
@Repository
public class UserDaoImpl implements UserDao{
public void save() {
System.out.println("把用户保存到数据库");
}
}
```

## Service

```java
package com.clive.service;
public interface UserService {
public void addUser();
}
```

## Service 实现类

```java
package com.clive.service.impl;
import javax.annotation.PostConstruct;
import javax.annotation.PreDestroy;
import javax.annotation.Resource;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;
import org.springframework.stereotype.Service;
import com.clive.dao.UserDao;
import com.clive.dao.impl.UserDaoImpl;
import com.clive.service.UserService;
@Service
public class UserServiceImpl implements UserService {
private UserDao userDao = new UserDaoImpl();
public void addUser() {
//开启日志
userDao.save();
//提交日志
}
}
```

## 配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xmlns:context="http://www.springframework.org/schema/context"
 xsi:schemaLocation="http://www.springframework.org/schema/beans
 http://www.springframework.org/schema/beans/spring-beans.xsd
 http://www.springframework.org/schema/context
http://www.springframework.org/schema/context/spring-context.xsd">

 <context:component-scan
base-package="com.clive"></context:component-scan>
</beans>
```

## 动态代理

```java
package com.clive.test;
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;
import org.junit.Test;
import org.springframework.context.ApplicationContext;
import
org.springframework.context.support.ClassPathXmlApplicationContext;
import com.clive.dao.BookDao;
import com.clive.service.UserService;
import com.clive.service.impl.UserServiceImpl;
public class MyTest {
@Test
public void proxyDemo(){
//Proxy.newProxyInstance 生成一个动态代理对象
final UserService userService = new UserServiceImpl();
/**
* 通过 Proxy.newProxyInstance 方法传入三个参数吧 UserService 变成一个
动态代理对象
* 三个参数分别是 需要动态代理对象的类加载器，需要动态代理对象的接口
* InvocationHandler 动态代理的具体实现
* 当 UserService 变成一个动态代理对象以后， 这个动态代理对象调用 他本
身的 addUser()方法的时候
* 实际上是去执行 invoke 方法里面的代码
* method.invoke(userService); 通过反射 的代码===
* System.out.println("开启日志");
* userService.addUser();
* System.out.println("提交日志");
* return 代表的是 这个方法是否有返回值 返回什么东西
* java 的动态代理分为两种 jdk cglib
*
*/
UserService proxyUserService =
(UserService) Proxy.newProxyInstance(
userService.getClass().getClassLoader(),
userService.getClass().getInterfaces(), new
InvocationHandler() {
/*
第一个参数 object 一般是指代理类，method 是被代理的方法，args 为该方法的参数数组
*/
public Object invoke(Object proxy, Method method,
Object[] args)throws Throwable {
System.out.println("开启日志");
 //通过反射得到
method.invoke(userService);
System.out.println("提交日志");
return null;
}
});
//proxyUserService他还是UserService的addUser方法但是他是动态代理对
象的方法
proxyUserService.addUser();
}
}
```