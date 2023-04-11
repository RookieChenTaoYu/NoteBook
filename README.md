# NoteBook
the NoteBook for my study

21.12.28.19:51
# Sec 1
## Sec 1.1
The *quick* brown fox jumps over the **lazy** dog.
aa ('sss') dsfs

math to see [this](https://www.jianshu.com/p/a0aa94ef8ab2)

这是一个上标<sup>上标内容</sup>,这是一个下标<sub>下标内容</sub>

用math更好：$i_{13}$

H$_{2}$O$_{O}$

# java
## sokcet
**'\r'** Bring the cursor(光标) to the beginning of the line 
**'\n'** Move the cursor down one space

function and object:
---
    substring()//The method returns a substring of the string.
    socket.getInputStream()//get the network connection input and return an InputStream instance(实例) at the same time.
    InputStream class:Is a byte-oriented(面向字节) stream abstract(抽象) class
    InputStreamReader class:Is a bridge from byte stream to character stream
    BufferedReader class:It provides a universal(通用) buffering method for text reading, and provides a very practical(实用) readLine, which reads a text line, reads text from the character input stream, and buffers each character, thereby providing efficient reading of characters, arrays and lines.
    BufferedOutputStream class:Byte buffered output stream(字节缓冲输出流)
    String.getBytes(String decode):Returns the byte array(字节数组) representation(表示) of a string by the decod, if there is no parameter(参数), the default encoding is used.
    FileInputStream class: FileInputStream is called a file byte input stream, which means to read file data in the form of bytes, such as reading pictures and videos, etc.
---
example:
---
    //Get the input stream from the Socket object
    InputStream is=socket.getInputStream();
    InputStreamReader isr=new InputStreamReader(is);
    BufferedReader br=new BufferedReader(isr);
                                
    String line=br.readLine();//use readLine to get a string
    String[] lineArr=line.split(" ");
    System.out.println(lineArr[1]);

    //the line lavue: "GET /C://temp/a.html HTTP/1.1"
    .split(" "):Split the string based on matching the given regular expression.(正则表达式)

    //get file path
    String filename=lineArr[1].substring(1);
    FileInputStream fis=new FileInputStream(filename);
    BufferedInputStream bis=new BufferedInputStream(fis);
    byte [] data=new byte[1024];
    int length=0;

    //Return HTTP response header information
    bos.write("HTTP/1.1 200 OK \r\n".getBytes());
    bos.write("content-type: text/html;charset=utf-8 \r\n".getBytes());
    bos.write("\r\n".getBytes());
    while((length=bis.read(data))!=-1){
    bos.write(data,0,length);
    }
---

# DBMS

## 关系数据语言

[集合运算](file:///C:/NOTE/material/1.01集合运算.pdf)

[集合运算](file:///C:/NOTE/material/1.02投影和选择运算.pdf)

[集合运算](file:///C:/NOTE/material/1.03连接运算.pdf)

[集合运算](file:///C:/NOTE/material/1.04除法运算.pdf)

## SQL

### exampl表：

/*S表添加数据*/
INSERT INTO S VALUES('S1','精益',20,'天津');
INSERT INTO S VALUES('S2','盛锡',10,'北京');
INSERT INTO S VALUES('S3','东方红',30,'北京');
INSERT INTO S VALUES('S4','丰泰盛',20,'天津');
INSERT INTO S VALUES('S5','为民',30,'上海');

SELECT * FROM S;

/*P表添加数据*/
INSERT INTO P VALUES('P1','螺母','红',12);
INSERT INTO P VALUES('P2','螺栓','绿',17);
INSERT INTO P VALUES('P3','螺丝刀','蓝',14);
INSERT INTO P VALUES('P4','螺丝刀','红',14);
INSERT INTO P VALUES('P5','凸轮','蓝',40);
INSERT INTO P VALUES('P6','齿轮','红',30);

SELECT * FROM P;
/*J表添加数据*/
INSERT INTO J VALUES('J1','三建','北京');
INSERT INTO J VALUES('J2','一汽','长春');
INSERT INTO J VALUES('J3','弹簧厂','天津');
INSERT INTO J VALUES('J4','造船厂','天津');
INSERT INTO J VALUES('J5','机车厂','唐山');
INSERT INTO J VALUES('J6','无线电厂','常州');
INSERT INTO J VALUES('J7','半导体厂','南京');
SSSSSS
SELECT * FROM J;
/*SPJ表添加数据*/

INSERT INTO SPJ VALUES('S1', 'P1', 'J1',200);
INSERT INTO SPJ VALUES('S1', 'P1', 'J3',100);
INSERT INTO SPJ VALUES('S1', 'P1', 'J4',700);
INSERT INTO SPJ VALUES('S1', 'P2', 'J4',700);
INSERT INTO SPJ VALUES('S1', 'P2', 'J2',100);
INSERT INTO SPJ VALUES('S2', 'P3', 'J1',400);
INSERT INTO SPJ VALUES('S2', 'P3', 'J2',200);
INSERT INTO SPJ VALUES('S2', 'P3', 'J4',500);
INSERT INTO SPJ VALUES('S2', 'P3', 'J5',400);
INSERT INTO SPJ VALUES('S2', 'P5', 'J1',400);
INSERT INTO SPJ VALUES('S2', 'P5', 'J2',100);
INSERT INTO SPJ VALUES('S3', 'P1', 'J1',200);
INSERT INTO SPJ VALUES('S3', 'P3', 'J1',200);
INSERT INTO SPJ VALUES('S4', 'P5', 'J1',100);
INSERT INTO SPJ VALUES('S4', 'P6', 'J3',300);
INSERT INTO SPJ VALUES('S4', 'P6', 'J4',200);
INSERT INTO SPJ VALUES('S5', 'P2', 'J4',100);
INSERT INTO SPJ VALUES('S5', 'P3', 'J1',200);
INSERT INTO SPJ VALUES('S5', 'P6', 'J2',200);
INSERT INTO SPJ VALUES('S5', 'P6', 'J4',500);
INSERT INTO SPJ VALUES('S1', 'P2', 'J4',700);


/*建立一个学生表Student*/
CREATE TABLE Student
(Sno CHAR(9) PRIMARY KEY,
 Sname CHAR(20) UNIQUE,
 Ssex char(2),
 Sage SMALLINT,
 Sdept CHAR(20)
 );
/*建立一个课程表 Course*/
 CREATE TABLE Course
 (Cno CHAR(4) PRIMARY KEY,
  Cname CHAR(40) NOT NULL,
	Cpno CHAR(4),
	Ccredit SMALLINT
	);
	
/*建立学生选课表SC*/
	CREATE TABLE SC
	(Sno CHAR(9),
	 Cno char(4),
	 Grade SMALLINT,
	 PRIMARY KEY(Sno,Cno),
	 FOREIGN key(Sno) REFERENCES Student(Sno),
	 FOREIGN key(Cno) REFERENCES Course(Cno)
	 );

/*插入语句*/
INSERT INTO student VALUES('201215121','李勇','男',20,'CS');
INSERT INTO student VALUES('201215122','刘晨','女',19,'CS');
INSERT INTO student VALUES('201215125','张立','男',19,'IS');
INSERT INTO student VALUES('201215123','王敏','女',18,'MA');


INSERT INTO course VALUES('1','数据库','5',4);
INSERT INTO course VALUES('2','数学',' ',2);
INSERT INTO course VALUES('3','信息系统','1',4);
INSERT INTO course VALUES('4','操作系统','6',3);
INSERT INTO course VALUES('5','数据结构','7',4);
INSERT INTO course VALUES('6','数据处理','',2);
INSERT INTO course VALUES('7','PASCAL语言','6',4);
INSERT INTO course VALUES('8','DB_Design','1',3);
INSERT INTO course VALUES('9','DB_DataDesign','8',4);

INSERT INTO sc VALUES('201215121','1',92);
INSERT INTO sc VALUES('201215121','2',85);
INSERT INTO sc VALUES('201215121','3',88);
INSERT INTO sc VALUES('201215122','2',90);
INSERT INTO sc VALUES('201215122','3',80);


- **create view：**
>创建基于单表的视图：
>
> create view v_1(id,type,birth)
> as select id,type,2021-age from users;
>
>创建基于多表的视图：
>
>create view tmp2(a,b) as select users.user_name,query.godate from users,query; 

- **delete：**
> delete from v_users where id=14;
- **update：**
> update v_query set godate=20211031 where des='tianjing' and origin='beijing';
- **insert**
>insert into sc(sid,score) values ('1','98'),('2','90');
- **使用聚集函数：**
> select max(ticprice) as 最高分 from ticket;

> select sno,avg(grade)  from SC group by sno having

group by 的使用：
聚集的时候必须有在查询寻能够比较或者能够加在一起的属性
如果没有的话就不能使用group by ，所以利用group by的时候最好使用自然连接natural join

- 自然连接：

有两种自然连接方式：

1.select * from spj natural join p;此时只有一个pno

2.select * from spj,p where spj.pno=p.pno;但此时，两个表的pno都保留了在上面，相当于全部连接后在筛选符合条件的

连接后求使用聚合函数：
select pname,sum(QTY) from spj,p where spj.pno=p.pno group by (p.pno(or spj.pno));

由于pname和QTY没有二义性所以前面不需要加上表名
### **带有EXISTS谓词的子查询**

由EXISTS引出的子查询，其目标列表达式通常都用*，因为EXISTS的子查询只返回真值假值，给出列名无实际意义。

- 例一：查询所有选修了1号课程的学生姓名。

此查询涉及的表student和SC表。可以在student中*依次选取每个元组数据的Sno值*，**用此值去检查SC表**。若SC表中村在这样的元组，其Sno值等于此student.sno值并且Cno=1，则取此student.sname送入结果表：

SELECT Sname
FROM Student
WHERE EXISTS(
SELECT *
FROM SC
WHERE Sno=Student.Sno AND Cno='1'
);

### 使用**not exists**的关于至少的查询：

注意：
**not exist**返回false：假如子查询有真值则立马返回false

但是想要**not exist**返回true，则子查询需要遍历所有假值才能返回true

通过这个特性我们就可以利用**not exist**来查询至少了：



> 注意这给得加上distinct不然的话会有重复的学号出现在结果表中

用两个*not exist*：


一共有三张表：
![Alt text](./picture/1.png)

如果想让第一张表的*某一元组*的查询的结果为true则必须让第二张表的**所有**查询的真值都为false

那么要让第二张表的查询结果为false那么**只需**在第三张表中有一个真值为true即可

则根据上述原则就可以写出sql语句如下：

---
    SELECT DISTINCT Sno
    FROM SC SCX
    WHERE NOT EXISTS(
    SELECT * FROM SC SCY
    WHERE SCY.Sno='201215122' AND NOT EXISTS(
    SELECT * FROM SC SCZ
    WHERE SCZ.Sno = SCX.Sno AND SCZ.Cno = SCY.Cno
    )
    );
---
### 触发器

    CREATE TRIGGER trigger_name 
    trigger_time trigger_event ON tb_name 
    FOR EACH ROW 
    trigger_stmt

    trigger_name：触发器的名称
    tirgger_time：触发时机，为BEFORE或者AFTER
    trigger_event：触发事件，为INSERT、DELETE或者UPDATE
    tb_name：表示建立触发器的表明，就是在哪张表上建立触发器
    trigger_stmt：触发器的程序体，可以是一条SQL语句或者是用BEGIN和END包含的多条语句
    所以可以说MySQL创建以下六种触发器：



```sql
CREATE TABLE `logs` (
  `Id` int(11) NOT NULL AUTO_INCREMENT,
  `log` varchar(255),
  PRIMARY KEY (`Id`)
);
```

```sql
DELIMITER $
CREATE TRIGGER user_log AFTER INSERT ON users FOR EACH ROW
BEGIN
DECLARE s1 VARCHAR(40)character set utf8;
DECLARE s2 VARCHAR(20) character set utf8;#后面发现中文字符编码出现乱码，这里设置字符集
SET s2 = " is created";
SET s1 = CONCAT(NEW.name,s2);     #函数CONCAT可以将字符串连接
INSERT INTO logs(log) values(s1);
END $
DELIMITER ;
```


#### 创建有多个执行语句的触发器
    CREATE TRIGGER 触发器名 BEFORE|AFTER 触发事件
    ON 表名 FOR EACH ROW
    BEGIN
        执行语句列表
    END
tips：一般情况下，mysql默认是以 ; 作为结束执行语句，与触发器中需要的分行起冲突

为解决此问题可用DELIMITER，如：DELIMITER ||，可以将结束符号变成||

当触发器创建完成后，可以用DELIMITER ;来将结束符号变成;

    CREATE TABLE `logs` (
    `Id` int(11) NOT NULL AUTO_INCREMENT,
    `log` varchar(255) DEFAULT NULL COMMENT '日志说明',
    PRIMARY KEY (`Id`)
    )

    mysql> DELIMITER ||
    mysql> CREATE TRIGGER demo BEFORE DELETE
        -> ON users FOR EACH ROW
        -> BEGIN
        -> INSERT INTO logs VALUES(NOW());
        -> INSERT INTO logs VALUES(NOW());
        -> END
        -> ||
    Query OK, 0 rows affected (0.06 sec)

    mysql> DELIMITER ;


### 存储过程

#### 删除存储过程

    drop procedure CountProc;

#### 查询

```sql
    DELIMITER ||

    CREATE PROCEDURE `select_procedure` ()
    BEGIN
        select * from users;
    END||

    DELIMITER ;
```

#### 插入

```sql
    DELIMITER ||

    CREATE PROCEDURE `select_procedure` ()
    BEGIN
        select * from users;
    END||

    DELIMITER ;
```

#### 删除

```sql
delimiter ||

    CREATE PROCEDURE `delete_user`(IN u_name INT)
    BEGIN
        DELETE FROM users
        WHERE user_name = u_name;
    END||

delimiter ;
```

#### 更新

```sql
delimiter ||

CREATE PROCEDURE `change_user_pwd`(IN u_name CHAR(15),IN u_pwd char(15))
BEGIN
        update users
        set user_pwd = u_pwd
        WHERE user_name = u_name;
END

delimiter ;
```

### JDBC调用触发器
```js
Connection conn = null; // 数据库连接对象
	CallableStatement clbStmt = null; // CallableStatement对象
	ResultSet res = null; // 结果集对象
	try
	{
		// 获取数据库连接
		conn = getConnection();
 
		// 创建CallableStatement对象
		clbStmt = conn.prepareCall("{CALL proc_search_user(?,?,?,?)}");
 
		// 设置输入参数
        // 第一个参数代表是第几个参数，第二个参数为参数值
		clbStmt.setInt(1, 3); // 查询第3页数据,
		clbStmt.setInt(2, 10); // 每页10条数据
 
		// 注册输出参数
		clbStmt.registerOutParameter(3, Types.INTEGER);
		clbStmt.registerOutParameter(4, Types.INTEGER);
 
		// 执行调用存储过程，并获取结果集
		res = clbStmt.executeQuery();
 
		// 循环遍历结果集
		while (res.next())
		{
			// 获取列值
			int id = res.getInt("id");
			String name = res.getString("name");
			Timestamp createTime = res.getTimestamp("create_time");
 
			// 输出列值
			System.out.println("编号：" + id + "  姓名：" + name + "  创建时间：" + createTime);
		}
 
		// 获取输出参数值
		int totalCount = clbStmt.getInt(3);
		int totalPage = clbStmt.getInt(4);
		System.out.println("数据总数：" + totalCount + " 总页数：" + totalPage);
 
	} catch (SQLException sqle)
	{
		sqle.printStackTrace();
	} finally
	{
		// 关闭数据库操作对象
		closeOperate(res, clbStmt, conn);
	}

```




- **where and having difference：**
> 1\.WHERE子句作用于基本表或视图，从中选择满足条件的元组
>
> 2\.GROUP BY对WHERE的结果进行分组
>
> 3\.HAVING子句作用于组，从中选择满足条件的组，即对分组数据进一步筛选。
>
> 4\.HAVING子句中可以使用聚集函数，而WHERE子句中不能。
> 
> 举例: 
> 
> select sno,avg(grade) from SC group by sno having avg(grade)>80;
- create user:
> CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
- delete user:
> Delete FROM user Where User='username';
- query user:
> SELECT User, Host FROM mysql.user;

- grant:
> grant select,update,insert on users to 'user1'@'localhost';
>
> show grants for 'user1'@'localhost';

## 关系数据库理论

R的候选键可以通过画函数依赖图来确定：如第三范式：

![Alt text](./picture/2.png)

BCNF:
![Alt text](./picture/3.png)

范式的关系：
![Alt text](./picture/4.png)


## 第七章: 数据库设计

数据库系统生存期的七个阶段

1.规划阶段 
2.需求分析阶段 
3.概念设计阶段
4.逻辑设计阶段
5.物理设计阶段
6.实现阶段
7.运行维护阶段

### 1.规划阶段 

...
### 2.需求分析阶段

1.结构化分析方法。

2.数据流程图（DFD）
![Alt text](./picture/5.png)
3.数据字典
![Alt text](./picture/6.png)
### 3.概念设计阶段

ER模型：

全局概念模型合成：局部概念模型的合并：

命名冲突: 名字的异义

属性冲突: 属性值的类型, 取值类型, 取值单位

结构冲突: 某局部图为属性，在另一局部图中为实体
### 4.逻辑设计阶段

***将概念模型转化为关系模型，是指将实体型和联系分别转化为关系模式！***

实体型转化为关系模式：
![Alt text](./picture/7.png)

联系转化为关系模式

1:1
![Alt text](./picture/8.png)

1:N   可以说是学生决定(蕴含)系：学号->系
![Alt text](./picture/9.png)

M:N
![Alt text](./picture/10.png)


### 5.物理设计阶段

物理结构设计定义:
![Alt text](./picture/11.png)
### 6.实现阶段
### 7.运行维护阶段

## 加密算法：
1.1 MD5

1.2 SHA系列

# Internet

## TCP
receiver controls sender, so sender won’t overflow receiver’s buffer by transmitting too much, too fast(接收端控制发送端，因此发送端不会因传输过多、过快而溢出接收端的缓冲区)

## 数据平面和控制平面

```asm
DSEG SEGMENT
    A DB 0AH
DSEG ENDS

CODE SEGMENT
    ASSUME CS:CODE,DS:DSEG
START:  
        MOV AX,DSEG
        MOV DS,AX   ;将数据段送到DS

        MOV DX, 283H    ;设置8255控制字
        MOV AL, 90H
        OUT DX,AL       ;设置ABC端口都为方式0，输出模式
        
        ;写中断屏蔽字OCW1
        ;开主片中断(两个)
        IN AL,21H
        AND AL,11110011B;写OCW1开中断主片IR2与IR3
        OUT 21H,AL      ;
        ;开从片中断(1个)
        IN AL,0A1H
        AND AL,11111011B     ;写OCW1开中断从片只开IR2
        OUT 0A1H,AL     ;不管IR3是开是关，先开一下中断防止IR3一开始是关的
        

        ;主片中断向量表填写
        CLI             ;关中断
        CLD             ;设定让DI递增的方向
        MOV AX, 0       ;中断服务程序对应的入口地址0000:DI
        MOV ES, AX      ;ES:DI配对使用,配合STOSW缩短程序尺寸,减少关中断时间
        MOV DI, 4*0BH   ;中断向量指针->DI
        MOV AX,OFFSET INT_X ;中断服务程序的偏移地址->AX
        STOSW           ;AX->ES:[DI][DI+1]中,然后DI+2
        MOV AX,SEG INT_X;中断服务程序的段基址->AX
        STOSW           ;AX->ES:[DI+2][DI+3]
        STI             ;开中断

        ;从片中断向量表填写
        CLI             ;关中断
        CLD             ;设定让DI递增的方向
        MOV AX, 0       ;中断服务程序对应的入口地址0000:DI
        MOV ES, AX      ;ES:DI配对使用,配合STOSW缩短程序尺寸,减少关中断时间
        MOV DI, 4*72H   ;中断向量指针->DI,从片将在72H处进行填写
        MOV AX,OFFSET INT_Y ;中断服务程序的偏移地址->AX
        STOSW           ;AX->ES:[DI][DI+1]中,然后DI+2
        MOV AX,SEG INT_Y;中断服务程序的段基址->AX
        STOSW           ;AX->ES:[DI+2][DI+3]
        STI             ;开中断

        ;8255的PC6复位为0作为中断源，每执行一次中断都得置位为0
        ;主程序
        MOV BL,00H      ;初始化设置BL开始为灭的状态为0
        MOV BH,00H      ;初始化设置BH开始为灭的状态为0
        MOV DX,283H
        MOV AL, 00000000B
        OUT DX,AL 
        MOV DX,283H
        MOV AL, 00000010B
        OUT DX,AL
L1:     MOV CL,A        ;从内存中取出计数的变量
        CMP CL,0        ;比较CL比0大还是小,是否应该循环或退出
        JA L1           ;比0大所以应该循环执行否则退出


;中断子程序1
INT_X PROC FAR
        PUSH AX
        CMP BL,00H      ;作为FLAG一样的标志，比较此时的灯是亮还是灭
        JZ L2           ;BL为0代表此时的灯是熄灭的，则跳转，否则为亮

        ;灯为亮的状态，所以把灯熄灭
        MOV DX,283H     ;把PC0作为开关灯的输出，置位1让灯亮
        MOV AL,00H      ;'000'代表PC0, '1'代表置位为1
        OUT DX,AL       ;灯灭
        MOV BL,00H      ;转换状态为灭
        JMP EXIT1        ;只要灯改变了当前状态就退出中断服务程序

        ;灯为灭的状态，所以把灯点亮
L2:     MOV DX,283H     ;要让PC0为1，让灯亮
        MOV AL,01H      ;'000'代表PC0, '0'代表置位为0
        OUT DX,AL       ;灯亮
        MOV BL,01H      ;让BL为1表示灯亮

EXIT1:  MOV CL,A        ;从内存中取出计数的变量
        DEC CL          ;自减
        MOV A,CL        ;将更改后的值存入变量中
        MOV AL,63H      ;中断程序结束用20H来结束
        OUT 20H,AL      ;写20H
        POP AX          ;恢复现场
        IRET            ;返回
INT_X ENDP

;中断子程序2
INT_Y PROC FAR
        PUSH AX
        CMP BH,00H      ;作为FLAG一样的标志，比较此时的灯是亮还是灭
        JZ L3           ;BL为0代表此时的灯是熄灭的，则跳转，否则为亮

        ;灯为亮的状态，所以把灯熄灭
        MOV DX,283H     ;把PC0作为开关灯的输出，置位1让灯亮
        MOV AL,02H      ;'001'代表PC0, '1'代表置位为1
        OUT DX,AL       ;灯灭
        MOV BH,00H      ;转换状态为灭
        JMP EXIT2        ;只要灯改变了当前状态就退出中断服务程序

        ;灯为灭的状态，所以把灯点亮
L3:     MOV DX,283H     ;要让PC0为1，让灯亮
        MOV AL,03H      ;'000'代表PC0, '0'代表置位为0
        OUT DX,AL       ;灯亮
        MOV BH,01H      ;让BL为1表示灯亮

EXIT2:  MOV CL,A        ;从内存中取出计数的变量
        DEC CL          ;自减
        MOV A,CL        ;将更改后的值存入变量中
        MOV AL,62H      ;中断程序结束用20H来结束
        OUT 20H,AL      ;写20H
        MOV DX,0A0H      ;中断程序结束用20H来结束
        MOV AL,62H
        OUT DX,AL
        POP AX          ;恢复现场
        IRET            ;返回
INT_Y ENDP

CODE ENDS
END START
```

# Assemble

## 8255

DSEG SEGMENT
      PORTA EQU 280H     ;A端口
      PORTB EQU 281H     ;B端口
      PORT_ORDER EQU 283H     ;命令端口
DSEG ENDS
CSEG SEGMENT
ASSUME CS:CSEG,DS:DSEG
START:
      MOV AX,DSEG
      MOV DS,AX   ;将数据段送到DS

      MOV DX,PORT_ORDER
      MOV AL,90H  ;1001 0000 初始化命令：A端口0方式输入，B端口0方式输出
      OUT DX,AL   ;写入命令端口

      MOV DX,PORTA
      IN AL,DX    ;将开关状态从A端口输入到AL

LIGHT:
      MOV DX,PORTB;使灯亮起
      OUT DX,AL   ;将当前流水状态从B端口输出则LED灯亮

      MOV BX,0FFFFH;使用循环来做视觉延迟
DELAY:DEC BX
      JNZ DELAY	   
      MOV BX,0FFFFH
DELAY1:DEC BX
      JNZ DELAY1
      MOV BX,0FFFFH
DELAY2:DEC BX
      JNZ DELAY2
      MOV BX,0FFFFH
DELAY3:DEC BX
      JNZ DELAY3
      MOV BX,0FFFFH
DELAY4:DEC BX
      JNZ DELAY4
      MOV BX,0FFFFH
DELAY5:DEC BX
      JNZ DELAY5
      MOV BX,0FFFFH
DELAY6:DEC BX
      JNZ DELAY6

      ROR AL,01H ;右移一个灯再将次输出。
      JMP LIGHT;

CSEG ENDS
END START


# 高性能 high performance compute HPC







## 1.compiler directives


什么是pragma?
    #pragma指令的作用是：**用于指定计算机或操作系统特定的编译器功能**  和 C++ 的每个实现均支持某些对其主机或操作系统唯一的功能。 例如，某些程序必须对将数据放入的内存区域进行准确的控制或控制某些函数接收参数的方式。 在保留与 C 和 C++ 语言的总体兼容性的同时，#pragma 指令使每个编译器均能够提供特定于计算机和操作系统的功能。
    根据定义，#pragma指令是计算机或操作系统特定的，**并且通常对于每个编译器而言都有所不同。** (MPICC) #pragma指令可用于条件语句以提供新的预处理器功能，或为编译器提供实现所定义的信息。

    #pragma  token-string
token-string 是一系列字符，这些字符提供了特定的编译器指令和参数（如果有）。 数字符号"#" 必须是位于包含#pragma指令行上的第一个非空白字符；空白字符可以分隔数字符号和词“pragma”。 在 #pragma 之后，编译转换器可分析为预处理标记的所有文本。 #pragma 的参数受宏展开的约束，如果编译器发现它无法识别的杂注，则它会发出警告并继续编译。

OpenMP directives for C/C++ are specified with the **#pragma omp preprocessing directive**

    #pragma omp parallel
    #pragma omp for
    #pragma omp parallel for
    #pragma omp barrier

## 2.runtime library

1.指「程序运行的时候」，即程序生命周期中的一个阶段。例句：「Rust 比 C 更容易将错误发现在编译时而非运行时。」 
2.指「运行时库」，即 glibc 这类原生语言的标准库。例句：「C 程序的 malloc 函数实现需要由运行时提供。」
3.指「运行时系统」，即某门语言的宿主环境。例句：「Node.js 是一个 JavaScript 的运行时。」

a header file named 

    omp.h
external functions

    omp_set_num_threads()
    omp_get_num_threads()
    omp_get_max_threads()
    omp_get_thread_num()
    omp_get_num_procs()
    omp_get_wtime()
    ...


## 3.enviroment variables

OMP_NUM_THREADS
sets the number of threads to use during execution



+-

    program -> process

    base language.
    library
    build in variables

    omp:
    hardware platform:
    共享式存储,单机,多核
    mpi:
    机群,Lan
    cpu + cuda

    paralla: independent
    communication, not close

## openmp


    #pragma omp parallel

    {

    每个线程都会执行大括号里的代码

    }


### 1.parallel Construct 
It creates a team of threads.
A set of implicit tasks is generated, one per thread, 
The code for each task is defined by the code inside the parallel construct.

    #pragma omp parallel [clause[ [, ]clause] ...]
    structured-block

test1.cpp--parallel Construct:
```cpp
#include <stdio.h>
#include <omp.h>
int main()
{
    int id,numb;
    omp_set_num_threads(3);
    #pragma omp parallel private(id,numb) 
    {
        id = omp_get_thread_num();
        numb = omp_get_num_threads();
        printf("I am thread %d out of %d \n", id, numb);
    }
}
```

![Alt text](./picture/12.png)


### 2.Worksharing construct

The work inside the construct is divided among the members of the team, and executed cooperatively instead of being executed by every thread.

    #pragma omp for [clause[[,] clause] ... ]
    for-loops

Example--worksharing construct
```cpp
#include <stdio.h>
#include <omp.h>
int main()
{
    omp_set_num_threads(3);
    //parallel construct
    #pragma omp parallel//create parallel threads
    {  
        printf("The number of threads: %d seen by thread %d \n",omp_get_thread_num() ,omp_get_num_threads());
        //Worksharing construct
        #pragma omp for// sharing blow work to each threads
        for( int i = 1; i <= 5; ++i ){
            printf("No. %d iteration by thread %d\n",i,omp_get_thread_num() );
        }
    }
    return 0;
}
```


#### 带有for的制导指令：

for制导语句是将for循环分配给各个线程执行，这里要求数据不存在依赖。

 使用形式为：

- 一、

        #pragma omp parallel for//见test3.c，使用更为普遍,这个后面不能加大括号
         for()

- 二、

        #pragma omp parallel//使用较少,见test2.c

        {//注意：大括号必须要另起一行

         #pragma omp for

          for()

        }

注意：第二种形式中并行块里面不要再出现parallel制导指令，比如写成这样就不可以：


        #pragma omp parallel

        {

         #pragma omp parallel for

          for()

        }


第一种形式作用域只是紧跟着的那个for循环，而第二种形式在整个并行块中可以出现多个for制导指令。

![Alt text](./picture/13.png)

工作共享结构

构造内部的工作在团队成员之间分配，并协同执行，*而不是由每个线程执行。*


### 3.Combined Parallel Worksharing Constructs

    #pragma omp parallel for [clause[[,] clause] ...] 
    for-loop

test3.c:
```cpp
#include <stdio.h> 
#include <omp.h>
int main() 
{ 
    //Combined Parallel Worksharing Constructs
    //Creating parallel threads and sharing below works
    #pragma omp parallel for 
    for(int i = 0; i < 10; ++i) { 
    printf(" No. %d iteration by thread %d\n",i,omp_get_thread_num());
    } 
    return 0; 
}
```
![Alt text](./picture/14.png)

### Combined Parallel Section Constructs

    #pragma omp parallel sections [clause[[,] clause] ...] new-line { 
        [#pragma omp section new-line] 
        structured-block 
        [#pragma omp section new-line ]
        structured-block 
    }

test4.c:
```cpp
#include <stdio.h> 
#include <omp.h>
int main() 
{ 
    #pragma omp parallel sections
    {
        #pragma omp section
        for (int i = 0; i < 5; ++i) 
            printf("section i : iteration %d by thread no. %d\n",   i, omp_get_thread_num());
        #pragma omp section
        for (int j = 0; j < 5; ++j) 
            printf("section j : iteration %d by thread no. %d\n", j, omp_get_thread_num());
    } 
    return 0;
} 
```
![Alt text](./picture/15.png)

If don't set threads(example: omp_set_num_threads(3)) then the default threads is your computer's maximum threads.


### specifies an explicit barrier at the point at which the construct appears

    #pragma omp barrier


test5.c:
```c++
#include <stdio.h> 
#include <omp.h>
int main() 
{ 
    omp_set_num_threads(3);
    #pragma omp parallel 
    { 
        for (int i = 0; i < 10; ++i)
            printf("loop i : iteration %d by thread no. %d\n", i,omp_get_thread_num() );
        
        #pragma omp barrier 
        
        for (int j = 0; j < 10; ++j)  
            printf("loop  j : iteration %d by thread no. %d\n", j,omp_get_thread_num() );

    } 
    return 0; 
} 
```

结果：

    loop i : iteration 0 by thread no. 1
    loop i : iteration 1 by thread no. 1
    loop i : iteration 2 by thread no. 1
    loop i : iteration 3 by thread no. 1
    loop i : iteration 4 by thread no. 1
    loop i : iteration 5 by thread no. 1
    loop i : iteration 6 by thread no. 1
    loop i : iteration 7 by thread no. 1
    loop i : iteration 8 by thread no. 1
    loop i : iteration 9 by thread no. 1
    loop i : iteration 0 by thread no. 2
    loop i : iteration 1 by thread no. 2
    loop i : iteration 2 by thread no. 2
    loop i : iteration 3 by thread no. 2
    loop i : iteration 4 by thread no. 2
    loop i : iteration 5 by thread no. 2
    loop i : iteration 6 by thread no. 2
    loop i : iteration 7 by thread no. 2
    loop i : iteration 8 by thread no. 2
    loop i : iteration 9 by thread no. 2
    loop i : iteration 0 by thread no. 0
    loop i : iteration 1 by thread no. 0
    loop i : iteration 2 by thread no. 0
    loop i : iteration 3 by thread no. 0
    loop i : iteration 4 by thread no. 0
    loop i : iteration 5 by thread no. 0
    loop i : iteration 6 by thread no. 0
    loop i : iteration 7 by thread no. 0
    loop i : iteration 8 by thread no. 0
    loop i : iteration 9 by thread no. 0
    loop  j : iteration 0 by thread no. 2
    loop  j : iteration 1 by thread no. 2
    loop  j : iteration 2 by thread no. 2
    loop  j : iteration 3 by thread no. 2
    loop  j : iteration 4 by thread no. 2
    loop  j : iteration 5 by thread no. 2
    loop  j : iteration 6 by thread no. 2
    loop  j : iteration 7 by thread no. 2
    loop  j : iteration 8 by thread no. 2
    loop  j : iteration 9 by thread no. 2
    loop  j : iteration 0 by thread no. 0
    loop  j : iteration 1 by thread no. 0
    loop  j : iteration 0 by thread no. 1
    loop  j : iteration 1 by thread no. 1
    loop  j : iteration 2 by thread no. 1
    loop  j : iteration 3 by thread no. 1
    loop  j : iteration 4 by thread no. 1
    loop  j : iteration 5 by thread no. 1
    loop  j : iteration 6 by thread no. 1
    loop  j : iteration 7 by thread no. 1
    loop  j : iteration 8 by thread no. 1
    loop  j : iteration 9 by thread no. 1
    loop  j : iteration 2 by thread no. 0
    loop  j : iteration 3 by thread no. 0
    loop  j : iteration 4 by thread no. 0
    loop  j : iteration 5 by thread no. 0
    loop  j : iteration 6 by thread no. 0
    loop  j : iteration 7 by thread no. 0
    loop  j : iteration 8 by thread no. 0
    loop  j : iteration 9 by thread no. 0

事件同步之barrier（同步路障）

if don't have #pragma omp barrier:

```c++
#include <stdio.h> 
#include <omp.h>
int main() 
{ 
    omp_set_num_threads(3);
    #pragma omp parallel 
    { 
        for (int i = 0; i < 10; ++i)
            printf("loop i : iteration %d by thread no. %d\n", i,omp_get_thread_num() );
        
        //#pragma omp barrier 
        
        for (int j = 0; j < 10; ++j)  
            printf("loop  j : iteration %d by thread no. %d\n", j,omp_get_thread_num() );

    } 
    return 0; 
} 
```

resulte:

    loop i : iteration 0 by thread no. 0
    loop i : iteration 1 by thread no. 0
    loop i : iteration 2 by thread no. 0
    loop i : iteration 3 by thread no. 0
    loop i : iteration 4 by thread no. 0
    loop i : iteration 5 by thread no. 0
    loop i : iteration 6 by thread no. 0
    loop i : iteration 7 by thread no. 0
    loop i : iteration 8 by thread no. 0
    loop i : iteration 9 by thread no. 0
    loop  j : iteration 0 by thread no. 0
    loop  j : iteration 1 by thread no. 0
    loop  j : iteration 2 by thread no. 0
    loop  j : iteration 3 by thread no. 0
    loop i : iteration 0 by thread no. 2
    loop i : iteration 1 by thread no. 2
    loop i : iteration 2 by thread no. 2
    loop i : iteration 3 by thread no. 2
    loop i : iteration 4 by thread no. 2
    loop i : iteration 5 by thread no. 2
    loop i : iteration 6 by thread no. 2
    loop i : iteration 7 by thread no. 2
    loop i : iteration 8 by thread no. 2
    loop i : iteration 9 by thread no. 2
    loop  j : iteration 0 by thread no. 2
    loop  j : iteration 1 by thread no. 2
    loop  j : iteration 2 by thread no. 2
    loop  j : iteration 3 by thread no. 2
    loop  j : iteration 4 by thread no. 2
    loop  j : iteration 5 by thread no. 2
    loop  j : iteration 6 by thread no. 2
    loop  j : iteration 7 by thread no. 2
    loop  j : iteration 8 by thread no. 2
    loop  j : iteration 9 by thread no. 2
    loop  j : iteration 4 by thread no. 0
    loop  j : iteration 5 by thread no. 0
    loop  j : iteration 6 by thread no. 0
    loop  j : iteration 7 by thread no. 0
    loop  j : iteration 8 by thread no. 0
    loop  j : iteration 9 by thread no. 0
    loop i : iteration 0 by thread no. 1
    loop i : iteration 1 by thread no. 1
    loop i : iteration 2 by thread no. 1
    loop i : iteration 3 by thread no. 1
    loop i : iteration 4 by thread no. 1
    loop i : iteration 5 by thread no. 1
    loop i : iteration 6 by thread no. 1
    loop i : iteration 7 by thread no. 1
    loop i : iteration 8 by thread no. 1
    loop i : iteration 9 by thread no. 1
    loop  j : iteration 0 by thread no. 1
    loop  j : iteration 1 by thread no. 1
    loop  j : iteration 2 by thread no. 1
    loop  j : iteration 3 by thread no. 1
    loop  j : iteration 4 by thread no. 1
    loop  j : iteration 5 by thread no. 1
    loop  j : iteration 6 by thread no. 1
    loop  j : iteration 7 by thread no. 1
    loop  j : iteration 8 by thread no. 1
    loop  j : iteration 9 by thread no. 1


barrier是OpenMP中线程同步的一种方法，在多线程代码块中插入barrier，则先完成计算任务的线程到达此处会等待，直到最后一个线程也完成了计算任务。***barrier相当于设置了一个线程的集合点，所有线程都到达之后才能继续往下执行。***

参考[this](https://blog.csdn.net/dcrmg/article/details/53888952)

### Critical vs atomic

critical可以用于任意只需要一个线程执行的地方，atomic只用于内存读写。critical对性能影响非常大。

***atomic 是说load/store是原子的，计算不是critical是整个section是原子的如果section里面的load和store不是对同一个变量，那么用atomic就可以并行而critical则是串行的***

在多线程编程中必须考虑到不同的线程对同一个变量进行读写访问引起的数据竞争问题。***如果线程间没有互斥机制，则不同线程对同一变量的访问顺序是不确定的，有可能导致错误的执行结果***。

OpenMP中有两种不同类型的线程同步机制，一种是互斥机制，一种是事件同步机制。



互斥锁机制的设计思路是**对一块共享的存储空间进行保护**，***保证任何时候最多只能有一个线程对这块存储空间进行访问，从而保证数据的完整性***。这块存储空间称为“临界区”。可以通过critical、atomic等制导指令以及API中的互斥函数来实现。





互斥锁之critical定义临界区


使用critical定义临界区的格式如下：

#pragma omp critical {需要被保护的代码块}

atomic.c:

```c++
#include <stdio.h> 
#include <omp.h>
int main() 
{ 
    int x = 0;

    omp_set_num_threads(4);
    #pragma omp parallel shared(x)
    { 
        #pragma omp atomic
        x++;
    }
    printf("x = %d\n",x);
    return 0; 
} 
```

critiacal.c:

```c++
#include <stdio.h>
#include <omp.h>
using namespace std;
int main() 
{ 
    int x = 0;
    omp_set_num_threads(4);
    #pragma omp parallel shared(x)
    { 
        #pragma omp critical
        x++;
    }
    printf("x = %d\n",x);
 return 0; 
} 
```

atomic是原子级只对一条语句有用，而critical对下面的大括号中整个section都有用

如果没有这两个***互斥机制***那么结果很有可能会出错比如输出3，6这样的错误结果，而正确结果是12(总线程为12的电脑上执行)

```c++
#include <stdio.h>
#include <omp.h>
using namespace std;
int main() 
{ 
    int x = 0;
    omp_set_num_threads(12);
    #pragma omp parallel shared(x)
    { 
        //#pragma omp critical
        //#pragma omp atomic
        x++;
    }
    printf("x = %d\n",x);
 return 0; 
} 
```
result:

    11



```c++
#include <stdio.h> 
#include <omp.h>
int main() {
    int i = 0, sum1 = 0, sum2 = 0, sum3 = 0, sum = 0;
    #pragma omp parallel sections //num_threads(3)
    {
        #pragma omp section
        #pragma omp critical
        for (i = 0; i < 5000; i++){
            sum1 = sum1 + i;
        }
        #pragma omp section
        #pragma omp critical
        for (i = 5000; i < 7000; i++){
            sum2 = sum2 + i;
        }
        #pragma omp section
        #pragma omp critical
        for (i = 7000; i < 10000; i++){
            sum3 = sum3 + i;
        }
    }
    sum = sum1 + sum2 + sum3;
    printf("%d\n", sum);
    return 0;
}
```
49995000

if don't have ***#pragma omp critical*** then the result will be wrong

a section use a critical

### Variable and reduction

    #pragma omp parallel for [clause[[,] clause] ...] 
    for-loop
Private(list):private(x,i,id)
Shared(list): 
Reduction(operator:list):reduction(+:sum)

pi.cpp
```c++
#include <stdio.h> 
#include <omp.h>
static long num_steps = 1000000000;
#define NUM_THREADS 4
int main(void){
    int i,id;
    double x,pi,sum=0;
    double step = 1.0 / (double)num_steps;
    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel for private(x) reduction(+:sum)
    for(i = 1;i <= num_steps;i++){
        x = (i - 0.5) * step;
        sum = sum + 4.0 / (1.0 + x * x);
    }

    pi = sum * step;
    printf("pi = %lf\n",pi);
    return 0; 
}
```

pi.cpp
```c++
#include <stdio.h> 
#include <omp.h>
static long num_steps = 1000000000;
#define NUM_THREADS 4
int main() 
{ 
    int i,id;
    double x,pi,sum=0;
    double step = 1.0 / (double)num_steps;
    omp_set_num_threads(NUM_THREADS);
    #pragma omp parallel private(x, i, id) reduction(+:sum)
    { 
        id = omp_get_thread_num();
        for(i = id + 1;i <= num_steps;i = i + NUM_THREADS){
            x = (i - 0.5) * step;
            sum = sum + 4.0 / (1.0 + x * x);
        }
    }
    pi = sum * step;
    printf("pi = %lf\n",pi);
    return 0; 
} 
```


```c++
#include <stdio.h>
#include <omp.h>
#include <time.h>
float array[5000][5000];

int main()
{
    int i,j;
    clock_t start1, finish1,start2, finish2;
    double duretime;

    printf("traverse in row\n");
    start1=clock();
    for (i=0;i<5000;i++)
        for (j=0;j<5000;j++)
            array[i][j]=(i+j)*2;
    finish1=clock();
    duretime=(double)(finish1-start1)/CLOCKS_PER_SEC;
    printf("time:%f\n",duretime);
    printf("traverse in collumn\n");
    start2=clock();
    for (j=0;j<5000;j++)
        for (i=0;i<5000;i++)
            array[i][j]=(i+j)*2;
    finish2=clock();
    duretime=(double)(finish2-start2)/CLOCKS_PER_SEC;
    printf("time: %f\n",duretime);
    return 0;
}

```

result:

    traverse in row
    time:0.111140
    traverse in collumn
    time: 0.170046

### OpenMP编程模型

由三个组件组成
- 编译器指令
- 运行库
- 环境变量

指定编译器应如何处理其输入,
C/C++ 的 OpenMP 指令使用 ***#pragma omp*** 预处理指令指定:


omp表示这个指令是OpenMP的指令，事实上所有OpenMP的指令都带有omp关键字，用于指定特定的编译功能

    #pragma omp parallel
    #pragma omp for
    #pragma omp parallel for
    #pragma omp barrier

**内存共享模型**：OpenMP是专为多处理器/核，共享内存机器所设计的。底层架构可以是UMA和NUMA。即(Uniform Memory Access和Non-Uniform Memory Access)

### 基于线程的并行性

OpenMP仅通过线程来完成并行
一个线程的运行是可由操作系统调用的最小处理单
线程们存在于单个进程的资源中，没有了这个进程，线程也不存在了
通常，线程数与机器的处理器/核数相匹配，然而，实际使用取决与应用程序



### #pragma
在所有的预处理指令中，#pragma 指令可能是最复杂的了，它的作用是设定编译器的状态或者是指示编译器完成一些特定的动作。#pragma指令对每个编译器给出了一个方法,在保持与C和C++语言完全兼容的情况下,给出主机或操作系统专有的特征。依据定义,编译指示是机器或操作系统专有的,且对于每个编译器都是不同的。
其格式一般为: #pragma Para
其中para 为参数，下面来看一些常用的参数。

\#pragma指令的作用是：***用于指定计算机或操作系统特定的编译器功能***。C 和 C++ 的每个实现均支持某些对其主机或操作系统唯一的功能。 例如，某些程序必须对将数据放入的内存区域进行准确的控制或控制某些函数接收参数的方式。 在保留与 C 和 C++ 语言的总体兼容性的同时，#pragma 指令使每个编译器均能够提供特定于计算机和操作系统的功能。

根据定义，#pragma指令是计算机或操作系统特定的，并且通常对于每个编译器而言都有所不同。 #pragma指令可用于条件语句以提供新的预处理器功能，或为编译器提供实现所定义的信息。

## MPI programming

[相关网址1](https://jcf94.com/2015/11/03/2015-11-03-mpi/) 
[MPICH2](https://jingyan.baidu.com/article/6d704a1354d7b528db51ca82.html)
[MPICH2](https://blog.csdn.net/cjsh_123456/article/details/80285887)
[相关网址2](https://blog.csdn.net/weixin_44048823/article/details/90046956?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522163659054516780261985200%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=163659054516780261985200&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-90046956.first_rank_v2_pc_rank_v29&utm_term=MPI%E6%95%99%E7%A8%8B&spm=1018.2226.3001.4187)



MPI Introduction

MPI-Message Passing Interface (消息传递接口)

MPI is a standard

The standard defines the syntax(词法) and semantics(语义) of a core of library routines useful to message-passing programs inC, C++, and Fortran.

该标准定义了对 C、C++ 和 Fortran 中的消息传递程序有用的库例程核心的语法（词法）和语义（字节）。

Implementations of MPI Specification :
MPI规范的实现

MPICH (Argonne)
MSMPI (Microsoft)
OpenMPI


任何一个MPI程序在调用MPI函数之前，首先调用的是初始化函数MPI_INIT.  
建立MPI的执行环境
when this is called, the MPI enviroment will be created.It means it will create n(in the arguments) processes in the communicator.And then parallel excute tasks.

    int MPI_Init(int *argc, char ***argv)
    Input Parameters:
    *argc - Pointer to the number of arguments
    ***argv - Pointer to the argument vector
有无参数均可


### NUMA

非统一内存访问（NUMA）是一种用于多处理器的电脑内存体设计，内存访问时间取决于处理器的内存位置。 在NUMA下，处理器访问它自己的本地存储器的速度比非本地存储器（存储器的地方到另一个处理器之间共享的处理器或存储器）快一些。

numa是一种关于多个cpu如何访问内存的架构模型，现在的cpu基本都是numa架构，linux内核2.5开始支持numa。

numa架构简单点儿说就是，一个物理cpu（一般包含多个逻辑cpu或者说多个核心）构成一个node，这个node不仅包括cpu，还包括一组内存插槽**也就是说一个物理cpu以及一块内存构成了一个node**每个cpu可以访问自己node下的内存，也可以访问其他node的内存，但是访问速度是不一样的，自己node下的更快。numactl --hardware命令可以查看node状况。

#### 集群运算

我们可以把NUMA看作集群运算的一个紧密耦合的形式。虚拟内存对集群结构的页式调度技术的加入更是使得NUMA可以完全由软件实现。基于软件的NUMA在节点间的延迟仍然比基于硬件的NUMA大几个数量级。

#### 进程(Process)

>一个 MPI 并行程序由一组运行在相同或不同计算机 /计算节点上的进程或线程构成。为统一起见，我们将 MPI 程序中一个独立参与通信的个体称为一个进程。

#### 进程组：

>一个 MPI程序的全部进程集合的一个有序子集。进程组中每个进程都被赋予一个在改组中唯一的序号（rank），用于在该组中标识该进程。序号范围从 0 到 n－1。

#### 通信器（communicator）:

>有时也译成通信子，是完成进程间通信的基本环境，它描述了一组可以互相通信的进程以及它们之间的联接关系等信息。MPI所有通信必须在某个通信器中进行。通信器分域内通信器（intracommunicator）和域间通信器（intercommunicator）两类，前者用于同一进程中进程间的通信，后者则用于分属不同进程的进程间的通信。

>MPI 系统在一个 MPI 程序运行时会自动创建两个通信器：一个称为 MPI_COMM_WORLD，它包含 MPI 程序中所有进程，另一个称为MPI_COMM_SELF，它指单个进程自己所构成的通信器。

> **MPI_COMM_WORLD** 是一个通信器，包含 MPI 程序中所有进程 一个通信器代表一组进程组
### 序号（rank）：

>即进程的标识，是用来在一个进程组或一个通信器中标识一个进程。MPI 的进程由进程组/序号或通信器/序号唯一确定。

### 消息（message）：

>MPI 程序中在进程间传递的数据。它由通信器、源地址、目的地址、消息标签和数据构成。

### 通信（communication）：

MPI_Comm_size(MPI_COMM_WORLD, &size);//获得进程数
MPI_Comm_rank(MPI_COMM_WORLD, &rank);//获得进程号
MPI_Get_processor_name(name, &namelength);//获得计算机名

int MPI_Send(
		void* msg_buf_p,
		int msg_size,
		MPI_Datatype msg_type,
		int dest,		
		int tag,
		MPI_Comm communicator
		);

参数意义：buf为消息的地址，count是内容的数量，datatype为消息内容的数据类型，goal为目标进程编号，tag为消息的标志，comm为通信域。

原型为int MPI_Recv(void \*buf, int count, MPI_Datatype datatype, int source, int tag, MPI_Comm comm，MPI_Status\*status)

参数意义：buf为储存消息的地址，count是接收的数量，datatype是消息内容的数据类型，source为接收来源的进程编号，tag是消息的标志，comm是通信域,status是接收状态

MPI_Status status;//是一个结构体，返回状态
其中status.MPI_SOURCE为来源进程号

>通信是指在进程之间进行消息的收发、同步等操作。
---
    MPI_Send(buf,counter,datatype,dest,tag,comm)
    buf：发送缓冲区的起始地址，可以是数组或结构指针；例如字符串str[]首地址str
    count：非负整数，发送的数据个数；
    datatype：发送数据的数据类型；
    dest：整型，目的的进程号；
    tag：整型，消息标志；
    comm：MPI进程组所在的通信域
    含义:向通信域中的dest进程发送数据，数据存放在buf中，类型是datatype，个数是count，这个消息的标志是tag，用以和本进程向同一目的进程发送的其它消息区别开来。
---

### 非阻塞通信
---
    int MPI_Isend(void* buf, int count, MPI_Datatype datatype, int dest, int tag,MPI_Comm comm, MPI_Request *request)
    /*
    IN buf 发送缓冲区的起始地址(可选数据类型)
    IN count 发送数据的个数(整型)
    IN datatype 发送数据的数据类型(句柄)
    IN dest 目的进程号(整型)
    IN tag 消息标志(整型)
    IN comm 通信域(句柄)
    OUT request 返回的非阻塞通信对象(句柄)
    */
    int MPI_Irecv(void* buf, int count, MPI_Datatype datatype, int source, int tag,MPI_Comm comm, MPI_Request *request)
    /*
    OUT buf 接收缓冲区的起始地址(可选数据类型)
    IN count 接收数据的最大个数(整型)
    IN datatype 每个数据的数据类型(句柄)
    IN source 源进程标识(整型)
    IN tag 消息标志(整型)
    IN comm 通信域(句柄)
    OUT request 非阻塞通信对象(句柄)
    */
---

#### MPI_WAIT

当进行到MPI_WAIT函数时会被阻塞
*MPI_WAIT以非阻塞通信对象为参数,一直等到与该非阻塞通信对象相应的非阻塞通信完成后才返回,同时释放该阻塞通信对象*

---
    int MPI_Wait(MPI_Request *request, MPI_Status *status)
    /*
    INOUT request 非阻塞通信对象 (句柄)
    OUT status 返回的状态 (状态类型)
    */
    int MPI_Test(MPI_Request*request, int *flag, MPI_Status *status)
    /*
    INOUT request 非阻塞通信对象(句柄)
    OUT flag 操作是否完成标志(逻辑型)
    OUT status 返回的状态 (状态类型)
    */
---

### MPI广播与归约


### 广播


    MPI_Bcast(void* buffer, int count, MPI_Datatype datatype, int root, MPI_Comm comm)
    buffer：通信消息缓存的起始地址
    count：数据个数
    datatype：数据类型
    root：根进程的标识号
    信息源进程标识号
    comm：通信域

### 归约

全局规约函数MPI_Reduce：
将所有的发送信息进行同一个操作。

    MPI_Reduce(void* sendbuf, void* recvbuf, int count, MPI_Datatype, MPI_Op op, int root, MPI_Comm comm)
    sendbuf：发送消息缓存的起始地址
    recvbuf：接收消息缓存的起始地址
    count：发送缓存中的数据个数
    op：归约操作符
    root：根进程序列号
    comm：通信域

一个广播发生的时候，一个进程会把同样一份数据传递给一个 communicator 里的所有其他进程。根节点调用 MPI_Bcast 函数的时候，data 变量里的值会被发送到其他的节点上.***当其他的节点调用 MPI_Bcast 的时候，data 变量会被赋值成从根节点接受到的数据。*** 实现使用了一个树形广播算法来获得比较好的网络利用率。



#### bcast_and_reduce_pi.cpp
```c++
#include <mpi.h>
#include <stdio.h>
#define N 1000000000
int main(int argc, char* argv[])
{
    int myid, numprocs, i, n;
    double mypi, pi, h, sum, x;
    double start, end;
    n = N;
    MPI_Init(NULL, NULL);
    start = MPI_Wtime();
    //numprocs为总的进程数量。
    MPI_Comm_size(MPI_COMM_WORLD, &numprocs);
    MPI_Comm_rank(MPI_COMM_WORLD, &myid);
    
    //广播，将n这个消息广播到各个进程
    MPI_Bcast(&n, 1, MPI_INT, 0, MPI_COMM_WORLD);
    h = 1.0 / N;
    sum = 0.0;
    //每个进程只需要执行N/numprocs次，减少了进程的工作量
    for (i = myid + 1; i <= N; i += numprocs) {
        x = h * ((double)i - 0.5);
        sum += (4.0 / (1.0 + x * x));
    }
    mypi = h * sum;
    //归约，对每个进程进行一个加的操作
    MPI_Reduce(&mypi, &pi, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);
    if (myid == 0)
    {
        end = MPI_Wtime();
        printf("pi is %.16lf\n", pi);
        printf("time is %lf\n", end - start);
        fflush(stdout);
    }
    MPI_Finalize();
}

```

#### mpi with openmp compute pi
```C++
    #include <stdio.h>
    #include <mpi.h>
    #include <omp.h>
    #include <math.h>
    #define NUM_THREADS 2
    long int n = 1000000000;
    int main(int argc, char* argv[])
    {
        double start, end;
        int my_rank, numprocs;
        long int i, my_n, my_first_i, my_last_i;
        double my_pi = 0.0, pi, h, x;
        MPI_Init(&argc, &argv);
        MPI_Comm_size(MPI_COMM_WORLD, &numprocs);
        MPI_Comm_rank(MPI_COMM_WORLD, &my_rank);
        start = MPI_Wtime();
        h = 1.0 / n;
        my_n = n / numprocs;//每个进程的步长
        my_first_i = my_rank * my_n;
        my_last_i = my_first_i + my_n;
        omp_set_num_threads(NUM_THREADS);
        //用omp并行循环计算
        #pragma omp parallel for reduction(+:my_pi) private(x,i)
        for (i = my_first_i; i < my_last_i; i++)
        {
            x = (i + 0.5) * h;
            my_pi = my_pi + 4.0 / (1.0 + x * x);
        }
        MPI_Reduce(&my_pi, &pi, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);
        if (my_rank == 0)
        {
            end = MPI_Wtime();
            printf("Approximation of pi:%15.13f\n", pi * h);
            printf("time %lf", end - start);
        }
        MPI_Finalize();
        return 0;
    }
    // mpicc demo2.c -o demo2 -fopenmp
    // mpirun ./demo2 -up 6
```









### MPI与OMP的区别：

OpenMP:线程级（并行粒度）；共享存储；隐式（数据分配方式）；可扩展性差；

MPI：进程级；分布式存储；显式；可扩展性好。

对于同一个进程的多个线程来说，由于它们只是独占自己的栈内存，堆内存是共享的，因此数据交换十分地容易，直接通过共享变量就可以进行交换，编程模型非常简单易用，并且对于操作系统来说，线程的上下文切换成本也比进程低很多。然而另一方面，由于线程不能脱离进程独立存在，而一个进程不能存在于多台机器上，所以OpenMP只适用于拥有多个CPU核心的单台电脑。并且多线程编程存在临界区（Critical Section），需要你自己去加锁，解决Race Condition问题，否则的话很容易导致不可预知的后果。

而MPI则是多进程的并发编程模型，相当于你自己调用fork——每一个进程的内存地址空间都是独立的，它们彼此之间几乎什么都不共享，只能通过进程间通信（IPC）来交换彼此的数据，因此编程难度明显要大很多。MPI有一个非常显著的优点，那就是对于一个分布式系统来说，进程是可以在分布式系统的每一台电脑之间转移的，因此对于拥有多台电脑的分布式系统来说，其并发性要明显好于OpenMP。

1、MPI（MPI是一个标准，有不同的具体实现，比如MPICH等）是多主机联网协作进行并行计算的工具，当然也可以用于单主机上多核/多CPU的并行计算，不过效率低。它能协调多台主机间的并行计算，因此并行规模上的可伸缩性很强，能在从个人电脑到世界TOP10的超级计算机上使用。缺点是使用进程间通信的方式协调并行计算，这导致并行效率较低、内存开销大、不直观、编程麻烦。

OpenMP是针对单主机上多核/多CPU并行计算而设计的工具，换句话说，OpenMP更适合单台计算机共享内存结构上的并行计算。由于使用线程间共享内存的方式协调并行计算，它在多核/多CPU结构上的效率很高、内存开销小、编程语句简洁直观，因此编程容易、编译器实现也容易（现在最新版的C、C++、Fortran编译器基本上都内置OpenMP支持）。不过OpenMP最大的缺点是只能在单台主机上工作，不能用于多台主机间的并行计算！

如果要多主机联网使用OpenMP（比如在超级计算机上），那必须有额外的工具帮助，比如 MPI + OpenMP 混合编程。或者是将多主机虚拟成一个共享内存环境（Intel有这样的平台），但这么做效率还不如混合编程，唯一的好处是编程人员可以不必额外学习MPI编程

### 计时

double start = MPI_Wtime();

double end = MPI_Wtime();

MPI_Barrier(MPI_COMM_WORLD);

这个函数用于阻塞通信，直到所有的进程都调用了次函数才将进行下一步

#### 1.MPI enviroment management

```c++
#include <stdio.h>
#include <mpi.h>
int main()
{
    int size, rank, namelength;
    char name[MPI_MAX_PROCESSOR_NAME];
    MPI_Init(NULL, NULL);
    MPI_Comm_size(MPI_COMM_WORLD, &size);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Get_processor_name(name, &namelength);
    printf("size=%d rank=%d name=%s len=%d \n", size, rank, name, namelength);
    fflush(stdout);
    MPI_Finalize();
    return 0;
}
```

#### 2.MPI收发消息：
```c++
#include <stdio.h>
#include <mpi.h>
int main()
{
    MPI_Status status;
    char string[] = "xxxxx";
    int myid;
    MPI_Init(NULL, NULL);
    MPI_Comm_rank(MPI_COMM_WORLD, &myid);
    if (myid == 2)
        MPI_Send("HELLO", 5, MPI_CHAR, 7, 1234, MPI_COMM_WORLD);
    if (myid == 7) {
        MPI_Recv(string, 5, MPI_CHAR, 2, MPI_ANY_TAG, MPI_COMM_WORLD, &status);
        printf("Got %s from P%d, tag %d\n", string, status.MPI_SOURCE, status.MPI_TAG);
        //status.MPI_SOURCE:source process
        //
        fflush(stdout);
    }
    MPI_Finalize();
}
```


#### 3.MPI非阻塞收发消息
```c++
#include <mpi.h>
#include <stdio.h>
int main(int argc, char* argv[])
{
    int numtasks, rank, dest, source, tag = 1234;
    char inmsg[] = "xxxxx", outmsg[] = "HELLO";
    MPI_Status stats[2];
    MPI_Request reqs[2];
    MPI_Init(NULL, NULL);
    MPI_Comm_size(MPI_COMM_WORLD, &numtasks);
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    if (rank == 0) {
        dest = 1;
        MPI_Isend(&outmsg, 5, MPI_CHAR, dest, tag, MPI_COMM_WORLD, &reqs[0]);
        printf("Task %d: Send %s while inmsg=%s \n", rank, outmsg, inmsg);
        fflush(stdout);
        MPI_Wait(&reqs[0], &stats[0]);
        printf("Task %d: send %s while inmsg=%s reqs[0]= %d \n", rank, outmsg, inmsg, reqs[0]);
        fflush(stdout);
    }
    else if (rank == 1) {
        source = 0;
        MPI_Irecv(&inmsg, 5, MPI_CHAR, source, tag, MPI_COMM_WORLD, &reqs[1]);
        printf("Task %d: Received %s \n", rank, inmsg);
        fflush(stdout);
        MPI_Wait(&reqs[1], &stats[1]);
        printf("Task %d: Received %s reqs[1]=%d\n", rank, inmsg, reqs[1]);
        fflush(stdout);
    }
    MPI_Finalize();
    return 0;
}
```

#### 4.利用MPI广播与规约计算pi
```c++
#include <mpi.h>
#include <stdio.h>
#define N 1000000000
int main(int argc, char* argv[])
{
    int myid, numprocs, i, n;
    double mypi, pi, h, sum, x;
    double start, end;
    n = N;
    MPI_Init(NULL, NULL);
    start = MPI_Wtime();
    //numprocs为总的进程数量。
    MPI_Comm_size(MPI_COMM_WORLD, &numprocs);
    MPI_Comm_rank(MPI_COMM_WORLD, &myid);
    //广播，将n这个消息广播到各个进程
    MPI_Bcast(&n, 1, MPI_INT, 0, MPI_COMM_WORLD);
    h = 1.0 / N;
    sum = 0.0;
    //每个进程只需要执行N/numprocs次，减少了进程的工作量
    for (i = myid + 1; i <= N; i += numprocs) {
        x = h * ((double)i - 0.5);
        sum += (4.0 / (1.0 + x * x));
    }
    mypi = h * sum;
    //归约，对每个进程进行一个加的操作
    MPI_Reduce(&mypi, &pi, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);
    if (myid == 0)
    {
        end = MPI_Wtime();
        printf("pi is %.16lf\n", pi);
        printf("time is %lf", end - start);
        fflush(stdout);
    }
    MPI_Finalize();
}    
```


### MPI与OMP求解pi

对pi的求解过程中

```c++
#include <stdio.h>
#include <mpi.h>
#include <omp.h>
#include <math.h>
#define NUM_THREADS 2
long int n = 1000000000;
int main(int argc, char* argv[])
{
    double start, end;
    int my_rank, numprocs;
    long int i, my_n, my_first_i, my_last_i;
    double my_pi = 0.0, pi, h, x;
    MPI_Init(&argc, &argv);
    MPI_Comm_size(MPI_COMM_WORLD, &numprocs);
    MPI_Comm_rank(MPI_COMM_WORLD, &my_rank);
    start = MPI_Wtime();
    h = 1.0 / n;
    my_n = n / numprocs;
    my_first_i = my_rank * my_n;
    my_last_i = my_first_i + my_n;
    omp_set_num_threads(NUM_THREADS);
    #pragma omp parallel for reduction(+:my_pi) private(x,i)
    for (i = my_first_i; i < my_last_i; i++)
    {
        x = (i + 0.5) * h;
        my_pi = my_pi + 4.0 / (1.0 + x * x);
    }
    MPI_Reduce(&my_pi, &pi, 1, MPI_DOUBLE, MPI_SUM, 0, MPI_COMM_WORLD);
    if (my_rank == 0)
    {
        end = MPI_Wtime();
        printf("Approximation of pi:%15.13f\n", pi * h);
        printf("time %lf\n", end - start);
    }
    MPI_Finalize();
    return 0;
}
```


#### 建立目录。

    [root@localhost ~]#mkdir cangls
    [root@localhost ~]#ls
    anaconda-ks.cfg cangls install.log install.log.syslog
#### 使用 -p 选项递归建立目录。 
    [root@localhost ~]# mkdir lm/movie/jp/cangls
    mkdir:无法创建目录"lm/movie/jp/cangls":没有那个文件或目录
    [root@localhost ~]# mkdir -p lm/movie/jp/cangls
    [root@localhost ~]# ls
    anaconda-ks.cfg cangls install.log install.log.syslog lm
    [root@localhost ~]# ls lm/
    movie
    #这里只查看一级子目录，其实后续的jp目录、cangls目录都已经建立

## CUDA

thread：一个CUDA的并行程序会被以许多个threads来执行。

block：数个threads会被群组成一个block，同一个block中的threads可以同步，也可以通过shared memory通信。

grid：多个blocks则会再构成grid。

warp：GPU执行程序时的调度单位，目前cuda的warp的大小为32，同在一个warp的线程，以不同数据资源执行相同的指令,这就是所谓 SIMT。(SM)

SP:最基本的处理单元，streaming processor，也称为CUDA core。最后具体的指令和任务都是在SP上处理的。GPU进行并行计算，也就是很多个SP同时做处理。

SM：**多个SP加上其他的一些资源组成一个streaming multiprocessor**.也叫GPU大核，其他资源如：warp scheduler，register，shared memory等。SM可以看做GPU的心脏（对比CPU核心），register和shared memory是SM的稀缺资源。CUDA将这些资源分配给所有驻留在SM中的threads。因此，这些有限的资源就使每个SM中active warps有非常严格的限制，也就限制了并行能力。

GPU中每个sm都设计成支持数以百计的线程并行执行，并且每个GPU都包含了很多的SM，所以GPU支持成百上千的线程并行执行。当一个kernel启动后，thread会被分配到这些SM中执行。大量的thread可能会被分配到不同的SM，同一个block中的threads必然在同一个SM中并行（SIMT）执行。每个thread拥有它自己的程序计数器和状态寄存器，并且用该线程自己的数据执行指令，这就是所谓的Single Instruction Multiple Thread。

一个SP可以执行一个thread，但是实际上并不是所有的thread能够在同一时刻执行。Nvidia把32个threads组成一个warp，warp是调度和运行的基本单元。warp中所有threads并行的执行相同的指令***一个warp需要占用一个SM运行，多个warps需要轮流进入SM***由SM的硬件warp scheduler负责调度。目前每个warp包含32个threads（Nvidia保留修改数量的权利）。所以，一个GPU上resident thread最多只有 SM * warp个。

在给出CUDA的编程实例之前，这里先对CUDA编程模型中的一些概念及基础知识做个简单介绍。CUDA编程模型是一个异构模型，需要CPU和GPU协同工作。在CUDA中，host和device是两个重要的概念，我们用host指代CPU及其内存，而用device指代GPU及其内存。CUDA程序中既包含host程序，又包含device程序，它们分别在CPU和GPU上运行。同时，host与device之间可以进行通信，这样它们之间可以进行数据拷贝。典型的CUDA程序的执行流程如下：

1.分配host内存，并进行数据初始化；

2.分配device内存，并从host将数据拷贝到device上；

3.调用CUDA的核函数在device上完成指定的运算；

4.将device上的运算结果拷贝到host上；

5.释放device和host上分配的内存。


上面流程中最重要的一个过程是调用CUDA的核函数来执行并行计算，kernel是CUDA中一个重要的概念，**kernel是在device上线程中并行执行的函数**，核函数用**__global__**符号声明，在调用时需要用<<<grid, block>>>来指定kernel要执行的线程数量，在CUDA中，每一个线程都要执行核函数，并且每个线程会分配一个唯一的线程号thread ID，这个ID值可以通过核函数的内置变量threadIdx来获得。

由于GPU实际上是异构模型，所以需要区分host和device上的代码，在CUDA中是通过函数类型限定词开区别host和device上的函数，主要的三个函数类型**限定词**如下：

__global__：在device上执行，从host中调用（一些特定的GPU也可以从device上调用），返回类型必须是void，**不支持可变参数参数，不能成为类成员函数。**注意用__global__定义的kernel是异步的，这意味着host不会等待kernel执行完就执行下一步。

__device__：在device上执行，单仅可以从device中调用，不可以和__global__同时用。

__host__：在host上执行，仅可以从host上调用，一般省略不写，不可以和__global__同时用，但可和__device__，此时函数会在device和host都编译。

要深刻理解kernel，必须要对kernel的线程层次结构有一个清晰的认识。首先GPU上很多并行化的轻量级线程。kernel在device上执行时实际上是启动很多线程，**一个kernel所启动的所有线程称为一个网格（grid）**，同一个网格上的线程共享相同的全局内存空间，grid是线程结构的第一层次，而网格又可以分为很多线程块（block），一个线程块里面包含很多线程，这是**第二个层次**。线程两层组织结构如下图所示，这是一个gird和block均为2-dim的线程组织。grid和block都是定义为dim3类型的变量，dim3可以看成是**包含三个无符号整数（x，y，z）成员的结构体变量**，在定义时，缺省值初始化为1。因此grid和block可以灵活地定义为1-dim，2-dim以及3-dim结构，对于图中结构（主要水平方向为x轴），定义的grid和block如下所示，kernel在调用时也必须通过执行配置<<<grid, block>>>来指定kernel所使用的线程数及结构。

    dim3 grid(3, 2);
    dim3 block(5, 3);
    kernel_fun<<< grid, block >>>(prams...);

所以，一个线程需要两个内置的坐标变量（blockIdx，threadIdx）来唯一标识，它们都是dim3类型变量，其中blockIdx指明线程所在grid中的位置，而threaIdx指明线程所在block中的位置，如图中的Thread (1,1)满足：

    threadIdx.x = 1
    threadIdx.y = 1
    blockIdx.x = 1
    blockIdx.y = 1

一个线程块上的线程是放在同一个流式多处理器（SM)上的，但是单个SM的资源有限，这导致线程块中的线程数是有限制的，现代GPUs的线程块可支持的线程数可达1024个。有时候，我们要知道一个线程在blcok中的全局ID，此时就必须还要知道block的组织结构，这是通过线程的内置变量blockDim来获得。它获取线程块各个维度的大小。对于一个2-dim的block [公式] ，线程 [公式] 的ID值为 [公式] ，如果是3-dim的block [公式] ，线程 [公式] 的ID值为 [公式] 。另外线程还有内置变量gridDim，用于获得网格块各个维度的大小。

kernel的这种线程组织结构天然适合vector,matrix等运算，如我们将利用上图2-dim结构实现两个矩阵的加法，每个线程负责处理每个位置的两个元素相加，代码如下所示。线程块大小为(16, 16)，然后将N*N大小的矩阵均分为不同的线程块来执行加法运算。
```c++
// Kernel定义
__global__ void MatAdd(float A[N][N], float B[N][N], float C[N][N]) 
{ 
    int i = blockIdx.x * blockDim.x + threadIdx.x; 
    int j = blockIdx.y * blockDim.y + threadIdx.y; 
    if (i < N && j < N) 
        C[i][j] = A[i][j] + B[i][j]; 
}
int main() 
{ 
    ...
    // Kernel 线程配置
    dim3 threadsPerBlock(16, 16); 
    dim3 numBlocks(N / threadsPerBlock.x, N / threadsPerBlock.y);
    // kernel调用
    MatAdd<<<numBlocks, threadsPerBlock>>>(A, B, C); 
    ...
}
```
一个线程块上的线程是放在同一个流式多处理器（SM)上的，但是单个SM的资源有限，这导致线程块中的线程数是有限制的，现代GPUs的线程块可支持的线程数可达1024个。

要知道一个线程再block中的全局ID，此时就必须还要知道block的组织结构，这是通过线程的内置变量blockDim来获得。他获取线程块各个维度的大小。对于一个2-dim的block(Dx,Dy),线程(x,y)的ID值为(x+y\*Dx),如果是3-dim的block(Dx,Dy,Dz),线程(x,y,z)的ID值为(x+y\*Dx+z\*Dy\*Dx)另外线程还有内置变量gridDim,用于获得网格块各个维度的大小

kernel的这种线程组织结构天然适合vector,matrix等运算，如我们将利用上图2-dim结构实现两个矩阵的加法，每个线程负责处理每个位置的两个元素相加，代码如下所示。线程块大小为(16, 16)，然后将N*N大小的矩阵均分为不同的线程块来执行加法运算。

pi.cu:
```c++
// cudaPi.cpp : Defines the entry point for the console application.
//

//#include "stdafx.h"
#include <stdio.h>
#include <cuda.h>
#include <math.h>
#define NUM_THREAD 1024
#define NUM_BLOCK 1

__global__ void cal_pi(double *sum, long long nbin, float step, long long nthreads, long long nblocks) {

	long long i;
	float x;
	long long idx = blockIdx.x*blockDim.x+threadIdx.x; 

	for (i=idx; i< nbin; i+=nthreads*nblocks) {
		x = (i+0.5)*step;
		sum[idx] = sum[idx]+4.0/(1.+x*x);
	}

}

int main(int argc, char* argv[])
{
    long long tid;
    double pi = 0;
    long long num_steps = 100000000;
   
    float step = 1./(float)num_steps;
    long long size = NUM_THREAD*NUM_BLOCK*sizeof(double);
    clock_t before, after;
    double *sumHost, *sumDev;
    sumHost = (double *)malloc(size);
    cudaMalloc((void **)&sumDev, size);
    // Initialize array in device to 0
    cudaMemset(sumDev, 0, size);
    before = clock();
    // Do calculation on device
    printf("Before Compute \n\n");
    dim3 numBlocks(NUM_BLOCK,1,1);
    dim3 threadsPerBlock(NUM_THREAD,1,1);
    cal_pi <<<numBlocks, threadsPerBlock>>> (sumDev, (int)num_steps, step, NUM_THREAD, NUM_BLOCK); // call CUDA kernel

    printf("After Compute \n\n");
    // Retrieve result from device and store it in host array
    cudaMemcpy(sumHost, sumDev, size, cudaMemcpyDeviceToHost);
    printf("After Copy \n\n");
    for(tid=0; tid<NUM_THREAD*NUM_BLOCK; tid++){
        pi = pi+sumHost[tid];
    }
    pi = pi*step;
    after = clock();
    printf("The value of PI is %15.12f\n",pi);
    printf("The time to calculate PI was %f seconds\n",((float)(after - before)/1000.0));
    free(sumHost); 
    cudaFree(sumDev);
    return 0;
}
```


### openCL:

    Platform (平台)：主机加上OpenCL框架管理下的若干设备构成了这个平台，通过这个平台，应用程序可以与设备共享资源并在设备上执行kernel。实际使用中基本上一个厂商对应一个Platform，比如Intel, AMD都是这样。
    Device（设备）：官方的解释是计算单元（Compute Units）的集合。举例来说，GPU是典型的device。Intel和AMD的多核CPU也提供OpenCL接口，所以也可以作为Device。
    Context（上下文）：OpenCL的Platform上共享和使用资源的环境，包括kernel、device、memory objects、command queue等。使用中一般一个Platform对应一个Context。
    Program：OpenCL程序，由kernel函数、其他函数和声明等组成。
    Kernel（核函数）：可以从主机端调用，运行在设备端的函数。
    Memory Object（内存对象）：在主机和设备之间传递数据的对象，一般映射到OpenCL程序中的global memory。有两种具体的类型：Buffer Object（缓存对象）和Image Object（图像对象）。
    Command Queue（指令队列）：在指定设备上管理多个指令（Command）。队列里指令执行可以顺序也可以乱序。一个设备可以对应多个指令队列。
    NDRange：主机端运行设备端kernel函数的主要接口。实际上还有其他的，NDRange是非常常见的，用于分组运算，以后具体用到的时候就知道区别了。


1.Query platforms//In the PC, generally there is only one host and one device.Unless there is a server.

so in the PC, num_entries always be 1.

主机加上OpenCL框架管理下的若干设备构成了这个平台，通过这个平台，应用程序可以与设备共享资源并在设备上执行kernel。平台通过cl_plantform来展现，可以使用下面的代码来初始化平台：

```c++
cl_int clGetPlatformIDs(cl_unit num_entries,
                        cl_platform_id *platforms,
                        cl_uint *num_platforms)
```
    (1,&platform,NULL)
    Return value: CL_SUCCESS or error code
    Num_entries: the number of cl_platform_id entries that can be added to platforms
    Platforms: returns a list of OpenCL platforms found. The cl_platform_id values returned.
    Num_platforms: returns the number of OpenCL platforms available.

2.Query devices
```c++
cl_int clGetDeviceIDs(cl_platform_id platforms,
                      cldevice_type device_type,
                      cl_unit num_entries,
                      cl_device_id *devices,
                      cl_uint *num_devices)
```

    (platform, CL_DEVICE_TYPE_GPU,1, &device_id, NULL)
    CL_DEVICE_TYPE_CPU/CL_DEVICE_TYPE_GPU
    Num_entries: the number of cl_device entries that can be added to devices
    Devices returns a list of OpenCL devices found
    Num_devices: returns the number of OpenCL devices available that match device_type. NULL if ignored.

3.Contexts 

定义了整个OpenCL化境，包括OpenCL kernel、设备、内存管理、命令队列等。上下文使用cl_context来表现。使用以下代码初始化：

```c++
// Returs the context

cl_context clCreateContext (const cl_context_properties*properties,
                            cl_uint num_devices,
                            const cl_device_id *devices, // Pointer to the devices object
                            void (*pfn_notify)(const char *errinfo, 
                                            const void *private_info, 
                                            size_t cb, 
                                            void *user_data), // (don't worry about this)
                            void *user_data, // (don't worry about this)
                            cl_int *errcode_ret) // error code result
```

    (0,1,&device_id,NULL,NULL,&err)
    Properties:specifies the platform to use
    Pfn_notify: A callback function registered by the application
    User_data: passed as the user_data argument when pfn_notify is called
    errcode_ret: returns an appropriate error code

4.Command queues

就像它的名字一样，他是一个存储需要在设备上执行的OpenCL指令的队列。“指令队列建立在一个上下文中的指定设备上。多个指令队列允许应用程序在不需要同步的情况下执行多条无关联的指令。”

```c++
cl_command_queue clCreateCommandQueue (cl_context context,
                                       cl_device_id device,
                                       cl_command_queue_properties properties, // Bitwise with the properties
                                       cl_int *errcode_ret) // error code result
```

    (context, device_id, 0,&err)
    command-queue properties: specifies a list of properties for the command-queue 

5.Creating program objects

OpenCL Program由kernel函数、其他函数和声明组成。它通过cl_program表示。当创建一个program时，你必须指定它是由哪些文件组成的，然后编译它。
```c++
// Returns the OpenCL program
cl_program clCreateProgramWithSource (cl_context context,
                                      cl_uint count, // number of files
                                      const char **strings, // array of strings, each one is a file
                                      const size_t *lengths, // array specifying the file lengths
                                      cl_int *errcode_ret) // error code to be returned

```

    (context,1, &kernelSource, NULL, &err)
    strings is an array of count pointers that make up the source code
    All strings in the strings argument are considered if lengths is NULL

6.Building program executables

```c++
cl_int clBuildProgram (cl_program program,
                       cl_uint num_devices,
                       const cl_device_id *device_list,
                       const char *options, // Compiler options, see the specifications for more details
                       void (*pfn_notify)(cl_program, void *user_data),
                       void *user_data)
```

    (program,0,NULL,NULL,NULL,NULL)
    If device_list is a NULL value, the program executable is built for all devices associated with program.


7.Kernel

A kernel is identified by the __kernel qualifier


8.Creating kernel objects

我们需要“提取”program的入口点。使用cl_kernel：
```c++
cl_kernel clCreateKernel (cl_program program, // The program where the kernel is
                          const char *kernel_name, // The name of the kernel, i.e. the name of the kernel function as it's declared in the code
                          cl_int *errcode_ret)
```

    (program, "vecAdd", &err)
    A program object
    a function name in the program declared with the __kernel qualifier
    Return an Error code


9.Setting kernel arguments

一旦我们的kernel建立好，我们就可以运行它。
首先，我们必须设置kernel的参数：

kernel的每个参数都需要调用一次这个函数。

```c++
cl_int clSetKernelArg (cl_kernel kernel, // Which kernel
                       cl_uint arg_index, // Which argument
                       size_t arg_size, // Size of the next argument (not of the value pointed by it!)
                       const void *arg_value) // Value
```

    (kernel, 0, sizeof(cl_mem), &d_a)
    Kernel: a valid kernel object
    Arg_index: the argument index, that go from 0
    Arg_size: the size of the argument value
    Arg_value: a pointer to data

10.Executing kernels

```c++
cl_int  clEnqueueNDRangeKernel (cl_command_queue command_queue, 
                                cl_kernel kernel, 
                                cl_uint  work_dim,    // Choose if we are using 1D, 2D or 3D work-items and work-groups
                                const size_t *global_work_offset,
                                const size_t *global_work_size,   // The total number of work-items (must have work_dim dimensions)
                                const size_t *local_work_size,     // The number of work-items per work-group (must have work_dim dimensions)
                                cl_uint num_events_in_wait_list, 
                                const cl_event *event_wait_list, 
                                cl_event *event)
```

    (queue, kernel, 1, NULL, &globalSize, &localSize,0, NULL, NULL)
    Work_dim is the number of dimensions used to specify the global work-items and work-items in the work-group.


11.Creating buffer object

在设备上分配内存，我们需要使用cl_mem类型，像下面这样：
```c++
// Returns the cl_mem object referencing the memory allocated on the device
cl_mem clCreateBuffer (cl_context context, // The context where the memory will be allocated
                       cl_mem_flags flags,
                       size_t size, // The size in bytes
                       void *host_ptr,
                       cl_int *errcode_ret)
```

    d_a = clCreateBuffer(context, CL_MEM_READ_ONLY, bytes, NULL, NULL);

12.Writing buffer object
从主机内存写入缓冲区对象。
```c++
cl_int clEnqueueWriteBuffer(cl_command_queue command_queue,
							cl_mem buffer,
							cl_bool blocking_write,
							size_t offset,
							size_t cb,
							const void *ptr,
							cl_uint num_events_in_wait_list,
							const cl_event *event_wait_list,
							cl_event *event) 
```

    clEnqueueWriteBuffer(queue, d_a, CL_TRUE, 0,bytes, h_a, 0, NULL, NULL)

13.Synchroniztion
```c++
clFinish(cl_command_queue command_queue)
```

    clFinish(queue)
    Returns CL_SUCCESS if the function call was executed successfully
    Blocks until all previously queued OpenCL commands in command_queue are issued to the associated device and have completed.

1.Allocates memory for host buffers and initializes them.
2.Gets platform and device information.
3.Sets up the platform.
4.Gets the devices list and chooses the type of device you want to run on.
5.Creates an OpenCL context for the device.
6.Creates a command queue.
7.Creates memory buffers on the device for each vector.
8.Copies the Buffer A and B to the device.
9.Creates a program from the kernel source.
10.Builds the program and creates the OpenCL kernel.
11.Sets the arguments of the kernel.
12.Executes the OpenCL kernel on the device.
13.Reads back the memory from the device to the host buffer. This step is optional, you may want to keep the data resident in the device for further processing.
14.Cleans up and waits for all the commands to complete.
15.Finally releases all OpenCL allocated objects and host buffers.


vactor.c
```c++
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <CL/opencl.h>
 
// OpenCL kernel. Each work item takes care of one element of c
const char *kernelSource =                                       "\n" \
"#pragma OPENCL EXTENSION cl_khr_fp64 : enable                    \n" \
"__kernel void vecAdd(  __global double *a,                       \n" \
"                       __global double *b,                       \n" \
"                       __global double *c,                       \n" \
"                       const unsigned int n)                    \n" \
"{                                                               \n" \
"    //Get our global thread ID                                  \n" \
"    int id = get_global_id(0);                                  \n" \
"                                                                \n" \
"    //Make sure we do not go out of bounds                      \n" \
"    if (id < n)                                                 \n" \
"        c[id] = a[id] + b[id];                                  \n" \
"}                                                               \n" \
                                                                "\n" ;
 
int main( int argc, char* argv[] )
{
	 int i=0;
	 size_t globalSize, localSize;
	 cl_int err;
	 double sum = 0;

    // Length of vectors
    // unsigned int n = 100000;
    int n = 100000;
    // Host input vectors
    double *h_a;
    double *h_b;
    // Host output vector
    double *h_c;
 
    // Device input buffers
    cl_mem d_a;
    cl_mem d_b;
    // Device output buffer
    cl_mem d_c;
 
    cl_platform_id platform;          // OpenCL platform
    cl_device_id device_id;           // device ID
    cl_context context;               // context
    cl_command_queue queue;           // command queue
    cl_program program;               // program
    cl_kernel kernel;                 // kernel
 
    // Size, in bytes, of each vector
    size_t bytes = n*sizeof(double);
 
    // Allocate memory for each vector on host
    h_a = (double*)malloc(bytes);
    h_b = (double*)malloc(bytes);
    h_c = (double*)malloc(bytes);
 
    // Initialize vectors on host
    //sin 是用的一般的角度计算的,而 sinf 是用弧度作单位计算的
    for(  i = 0; i < n; i++ ){
        h_a[i] = sinf(i)*sinf(i);
        h_b[i] = cosf(i)*cosf(i);
    }
 
   // size_t globalSize, localSize;
	
    //cl_int err;
 
    // Number of work items in each local work group
    localSize = 64;
 
    // Number of total work items - localSize must be devisor
    globalSize = ceil(n/(float)localSize)*localSize;
 
    // Bind to platform
    err = clGetPlatformIDs(1, &platform, NULL);
 
    // Get ID for the device
    err = clGetDeviceIDs(platform, CL_DEVICE_TYPE_GPU, 1, &device_id, NULL);
 
    // Create a context  
    context = clCreateContext(0, 1, &device_id, NULL, NULL, &err);
 
    // Create a command queue 
    queue = clCreateCommandQueue(context, device_id, 0, &err);
 
    // Create the compute program from the source buffer
    program = clCreateProgramWithSource(context, 1,
                            (const char **) & kernelSource, NULL, &err);
 
    // Build the program executable 
    clBuildProgram(program, 0, NULL, NULL, NULL, NULL);
 
    // Create the compute kernel in the program we wish to run
    kernel = clCreateKernel(program, "vecAdd", &err);
 
    // Create the input and output arrays in device memory for our calculation
    d_a = clCreateBuffer(context, CL_MEM_READ_ONLY, bytes, NULL, NULL);
    d_b = clCreateBuffer(context, CL_MEM_READ_ONLY, bytes, NULL, NULL);
    d_c = clCreateBuffer(context, CL_MEM_WRITE_ONLY, bytes, NULL, NULL);
 
    // Write our data set into the input array in device memory
    err = clEnqueueWriteBuffer(queue, d_a, CL_TRUE, 0,
                                   bytes, h_a, 0, NULL, NULL);
    err |= clEnqueueWriteBuffer(queue, d_b, CL_TRUE, 0,
                                   bytes, h_b, 0, NULL, NULL);
 
    // Set the arguments to our compute kernel
    err  = clSetKernelArg(kernel, 0, sizeof(cl_mem), &d_a);
    err |= clSetKernelArg(kernel, 1, sizeof(cl_mem), &d_b);
    err |= clSetKernelArg(kernel, 2, sizeof(cl_mem), &d_c);
    err |= clSetKernelArg(kernel, 3, sizeof(unsigned int), &n);
 
    // Execute the kernel over the entire range of the data set  
    //localSize = 64;
    //globalSize = ceil(n/(float)localSize)*localSize;
    err = clEnqueueNDRangeKernel(queue, kernel, 1, NULL, &globalSize, &localSize,
                                                              0, NULL, NULL);
 
    // Wait for the command queue to get serviced before reading back results
    clFinish(queue);
 
    // Read the results from the device
    clEnqueueReadBuffer(queue, d_c, CL_TRUE, 0,
                                bytes, h_c, 0, NULL, NULL );
 
    //Sum up vector c and print result divided by n, this should equal 1 within error
    //double sum = 0;
    for(i=0; i<n; i++)
        sum += h_c[i];
    printf("final result: %f\n", sum/n);
 
    // release OpenCL resources
    clReleaseMemObject(d_a);
    clReleaseMemObject(d_b);
    clReleaseMemObject(d_c);
    clReleaseProgram(program);
    clReleaseKernel(kernel);
    clReleaseCommandQueue(queue);
    clReleaseContext(context);
 
    //release host memory
    free(h_a);
    free(h_b);
    free(h_c);
 
    return 0;
}

```

openCLpi.c:
```c++
                                                                
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <CL/opencl.h>


// OpenCL kernel. many workGroups compute n iterations
#define KERNEL(...) #__VA_ARGS__
const char * kernelSource =  KERNEL(
 __kernel void Pi(__global float *workGroupBuffer, // 0..NumWorkGroups-1 
 				 __local float *insideWorkGroup,  // 0..workGroupSize-1 
 				 const uint n,        // Total iterations 
 				 const uint chunk)        // Chunk size 
 { 
 	const uint lid = get_local_id(0); 
 	const uint gid = get_global_id(0); 

 	const float step = (1.0/(float)n); 
 	float partial_sum = 0.0; 
  
 	// Each work-item computes chunk iterations 
 	for(uint i=gid*chunk; i<(gid*chunk)+chunk; i++) { 
 		float x = step * ((float) i - 0.5); 
 		partial_sum += 4.0 / (1.0 + x * x); 
 	} 
  
 	// Each work-item stores its partial sum in the workgroup array 
 	insideWorkGroup[lid] = partial_sum; 
  
 	// Synchronize all threads within the workgroup 
 	barrier(CLK_LOCAL_MEM_FENCE); 
  
 	float local_pi = 0; 
  
 	// Only work-item 0 of each workgroup perform the reduction 
 	// of that workgroup 
 	if(lid == 0) { 
 		const uint length = lid + get_local_size(0); 
 		for (uint i = lid; i<length; i++) { 
 			local_pi += insideWorkGroup[i]; 
 		} 
 		// It store the workgroup sum 
 		// Final reduction, between block, is done out by CPU 
 		workGroupBuffer[get_group_id(0)] = local_pi; 
 	} 
 } 

); 

int main( int argc, char* argv[] )
{
	 int i=0;
	 float pi;
	 float *pi_partial;
	 size_t maxWorkGroupSize;
	 cl_int err;
	 cl_mem memObjects;
	 int niter, chunks, workGroups;
	 size_t globalWorkSize;
	 size_t localWorkSize;

 
    cl_platform_id platform;        // OpenCL platform
    cl_device_id device_id;           // device ID
    cl_context context;               // context
    cl_command_queue queue;           // command queue
    cl_program program;               // program
    cl_kernel kernel;                 // kernel
 	
	niter = 262144;
	chunks=64;
 
  
    err = clGetPlatformIDs(1, &platform, NULL);
 
    // Get ID for the device
    err = clGetDeviceIDs(platform, CL_DEVICE_TYPE_GPU, 1, &device_id, NULL);
	clGetDeviceInfo(device_id, CL_DEVICE_MAX_WORK_GROUP_SIZE, sizeof(size_t),
             			&maxWorkGroupSize, NULL);
	
	workGroups = ceil((float)(niter/maxWorkGroupSize/chunks));
   
	pi_partial = (float*)malloc(sizeof(float)*workGroups);   
        	
	// Create a context  
    context = clCreateContext(0, 1, &device_id, NULL, NULL, &err);
 
    // Create a command queue 
    queue = clCreateCommandQueue(context, device_id, 0, &err);

    // Create the compute program from the source buffer
	
    program = clCreateProgramWithSource(context, 1,
                          &kernelSource, NULL, &err);
    // Build the program executable 
    err = clBuildProgram(program, 0, NULL, NULL, NULL, NULL);
	localWorkSize =  maxWorkGroupSize;//1
	globalWorkSize = niter / chunks;
	
    // Create the compute kernel in the program we wish to run
    kernel = clCreateKernel(program, "Pi", &err);

    // Create the input and output arrays in device memory for our calculation
    memObjects = clCreateBuffer(context, CL_MEM_READ_WRITE,
	   sizeof(float)*workGroups, NULL, &err); 
    
     err |= clSetKernelArg(kernel, 0, sizeof(cl_mem), &memObjects);
	 err  = clSetKernelArg(kernel, 1, sizeof(float)*maxWorkGroupSize, NULL);
     err |= clSetKernelArg(kernel, 2, sizeof(unsigned int), &niter);
     err |= clSetKernelArg(kernel, 3, sizeof(unsigned int), &chunks);

	err = clEnqueueNDRangeKernel(queue, kernel, 1, NULL, &globalWorkSize, &localWorkSize,
                                                              0, NULL, NULL);
    clFinish(queue);
    err = clEnqueueReadBuffer(queue, memObjects, CL_TRUE, 0,
            			sizeof(float)*workGroups, pi_partial, 0, NULL, NULL);
   	pi=0;
 
	for(i=0; i<workGroups; i++) {
       pi += pi_partial[i];
    }
    pi *= (1.0/(float)niter);
	printf("final result: %f\n", pi);

    // release OpenCL resources
    clReleaseMemObject(memObjects);
    clReleaseProgram(program);
    clReleaseKernel(kernel);
    clReleaseCommandQueue(queue);
    clReleaseContext(context);
 
    //release host memory
    free(pi_partial);
  
    return 0;
}
```










# algorithm
## 贪心算法
### 活动选择策略证明
fn = 活动截止时间

令S = {1, 2, 3,..., n}是活动集且f<sub>1</sub><=f<sub>2</sub><=....f<sub>n</sub>

1.归纳基础：k = 1,证明**存在最优解**包含活动1，

任取最优解A，A中活动按截止时间递增排列，如果A的第一个活动为j，j!=1
用1替换A的活动j得到解A'，即A' = (A - {j})并{1},
由于f1<=fj，A'也是最优解，且含有1,f1<=fj

2.假设命题k为真，证明对k+1也为真

证：算法执行到第k步选择了活动i1=1，i2....ik,根据归纳假设存在最优解A包含i1=1,
i2,....ik,A中剩下活动选自集合S'

S' = {i|i属于S,si>=fk}
A = {i1=1,i2,....ik,} U B

B是S'的最优解，(若不然，S’的最优解为B*)

将S'看成子问题,根据归纳基础，存在S'的最优解B'有S'中的第一个活动i<sub>k+1</sub>,且|B'|=|B|,于是

{i1,i2,...,ik} U B' = {i1,i2...,ik,ik+1} U (B' - {ik+1})也是最优解

### 合并果子
【题目】
题目描述：

在一个果园里，多多已经将所有的果子打了下来，而且按果子的不同种类分成了不同的堆。多多决定把所有的果子合成一堆。

每一次合并，多多可以把两堆果子合并到一起，消耗的体力等于两堆果子的重量之和。可以看出，所有的果子经过n－1次合并之后，就只剩下一堆了。多多在合并果子时总共消耗的体力等于每次合并所耗体力之和。

因为还要花大力气把这些果子搬回家，所以多多在合并果子时要尽可能地节省体力。假定已知每个果子重量都为1，并且已知果子的种类数和每种果子的数目，你的任务是设计出合并的次序方案，使多多耗费的体力最少，并输出这个最小的体力耗费值。

例如有三种果子，数目依次为1，2，9。可以先将 1、2堆合并，新堆数目为3，耗费体力为3。接着，将新堆与原先的第三堆合并，又得到新的堆，数目为12，耗费体力为12。所以多多总共耗费体力为3+12=15。可以证明15为最小的体力耗费值。

输入格式：

输入文件包括两行，第一行是一个整数 n (1 ≤ n ≤ 10000)，表示果子的种类数。第二行包含 n 个整数，用空格分隔，第 i 个整数ai（1 ≤ ai ≤ 20000）是第 i 种果子的数目。

输出格式：

输出文件包括一行，这一行只包含一个整数，也就是最小的体力耗费值。输入数据保证这个值小于。

样例数据：

输入
3
1 2 9

输出
15
```cpp
#include<queue>
#include<cstdio>
#include<cstring>
#include<algorithm>
#define N 10005
using namespace std;
priority_queue<int>q;//优先
int main()
{
	int n,i,x,t,ans=0;
	scanf("%d",&n);
	for(i=1;i<=n;++i)
	{
		scanf("%d",&x);
		q.push(-x);
	}
	while(--n)
	{
		t=0;
		t-=q.top();q.pop();
		t-=q.top();q.pop();
		ans+=t;
		q.push(-t);
	}
	printf("%d",ans);
	return 0;
}
```

### 最小差距

题目描述

给定一些不同的一位数字，你可以从这些数字中选择若干个，并将它们按一定顺序排列，组成一个整数，把剩下的数字按一定顺序排列，组成另一个整数。组成的整数不能以0开头（除非这个整数只有1位）。

例如，给定6个数字，0,1,2,4,6,7，你可以用它们组成一对数10和2467，当然，还可以组成其他的很多对数，比如210和764，204和176。这些对数中两个数差的绝对值最小的是204和176，为28。

给定N个不同的0~9之间的数字，请你求出用这些数字组成的每对数中，差的绝对值最小的一对（或多对）数的绝对值是多少？

输入数据

第一行包括一个数 T （T≤1000），为测试数据的组数。

每组数据包括两行，第一行为一个数 N （2≤N≤10），表示数字的个数。下面一行为 N 个不同的一位数字。

输出数据

T行，每行一个数，表示第 i 个数据的答案。即最小的差的绝对值。

```c++
#include<iostream>
#include<algorithm>
#include<cstring>
#include<cmath>
#define INF 0x3f3f3f3f
using namespace std;
int a[15]; 
int visited[15];
 
int func1(int n){
	if(a[1]==0){
		int temp=a[1];
		a[1]=a[2];
		a[2]=temp;
	}
	int s1 = 0, s2 = 0;
	for(int i=1; i<=n/2+1; i++)
		s1 = s1*10 + a[i];
	for(int i=n; i>n/2+1; i--)
		s2 = s2*10 + a[i];
	return s1-s2;
}
 
int func2(int n){
	int ans = INF;
	for(int i=2; i<=n; i++){
		if(a[i-1]){
			memset(visited, 0, sizeof(visited));
			int s1=a[i], s2=a[i-1];
			visited[i]=1;
			visited[i-1]=1;
			int left=1, right=n;
			for(int j=1; j<=(n-2)/2; j++){//每一轮选出两个数字 
				while(visited[left]) left++;
				while(visited[right]) right--;
				visited[left]=1;
				visited[right]=1;
				s1 = s1*10 + a[left];
				s2 = s2*10 + a[right];
			}
			ans = min(ans, s1-s2);
		}
	}
	return ans;
}
 
int main(){
	int t;
	cin>>t;
	
	while(t--){
		int n, ans;
		cin>>n;
		memset(a, 0, sizeof(a));
		for(int i=1; i<=n; i++)
			cin>>a[i];
			
		sort(a+1, a+n+1);
		if(n==2){
			ans = a[2]-a[1];
		}else if(n%2==1){
			ans = func1(n);
		}else{
			ans = func2(n);
		}
		cout<<ans<<endl;
	} 
	return 0;
} 

```
### 上帝的爱好


    题目描述
    我们知道，词都是按照词牌来填的，上帝为了考验小杉，只给了他四种词牌，但只要压韵就算符合词牌。
    小杉已经想好了N个意境优美的句子，每个句子都有一个韵脚。
    符合要求的词的句式应当有如下四种" XXYY" ，" XYXY" ，" XYYX" ，" XXXX" ，其中X或Y表示韵脚。
    现在小杉想知道，从他想的N个句子之中，最多能按顺序挑选出几首符合条件的词。
    并且词的句子间不能交错，比如你选了1 4 6 8做为一首诗，那么7你就不能再选了。

    输入数据
    每组测试数据的
    第一行有一个数 N (N≤4000)。
    第二行有N个不超10^{3}的正整数，第i个整数表示第i个句子的韵脚，整数相同表示韵脚相同。
    30% 的数据 N≤100

    输出数据
    对每组测试数据输出一行，仅有一个数字，表示小杉最多能挑出几首词来。

    样例输入
    12
    1 2 4 2 3 1 2 2 1 1 2 2
    样例输出
    2
    样例说明
    样例最多可以挑出两首词，一种方案如下：
    1 2 4 6/9 10 11 12
```c++

#include<iostream>
using namespace std;
int a[4005];
 
int main(){
	int n;
	cin>>n;
	
	for(int i=1; i<=n; i++)
		cin>>a[i];
	
	int pairs=0, ans=0, start=1;	
	for(int i=1; i<=n; i++){
		for(int j=start; j<i; j++){
			if(a[j]==a[i]){
				pairs += 1;
				a[i]=0;//表示已经和别人成对 
				a[j]=0;
				break;
			}
		}
		if(pairs==2){//找到两对相同韵脚的句子 
			pairs=0;
			ans += 1; 
			start=i+1; //避免与后一首诗交叉 
		}
	}
	cout<<ans<<endl;
	return 0; 
}
```

### 贪心 任务调度问题


    一个单位时间任务是恰好需要一个单位时间完成的任务。给定一个单位时间任务的有限集S。关于S 的一个时间表用于描述S 中单位时间任务的执行次序。时间表中第1 个任务从时间0 开始执行直至时间1 结束，第2 个任务从时间1 开始执行至时间2 结束，…，第n个任务从时间n-1 开始执行直至时间n结束。具有截止时间和误时惩罚的单位时间任务时间表问题可描述如下：
    (1) n 个单位时间任务的集合S={1,2,…,n}（n≤500）；
    (2) 任务i的截止时间d[i],1≤i≤n,1≤d[i]≤n，即要求任务i在时间d[i]之前结束；
    (3) 任务i 的误时惩罚1≤w[i]<1000,1≤i≤n,即任务i 未在时间d[i]之前结束将招致w[i]的惩罚；若按时完成则无惩罚。

    任务时间表问题要求确定S 的一个时间表（最优时间表）使得总误时惩罚达到最小。

    题解：根据罚时的长短进行排序，将罚时时间长的放在前面。开一个数组作为时间槽，记录每个单位时间是否有任务安排。若截止日期相同，根据时间长短判断哪个优先，尽量将任务安排在截至时间完成，否则放在放在前一天，以此类推。若在截至时间前都有任务安排，则舍去，增加到罚时中。

    输入数据
    第一行是正整数n表示任务数。接下来的2行中，每行有n个正整数，分别表示各任务的截止时间和误时惩罚
    输出数据
    将计算出的最小总误时惩罚输出
    样例输入
    7
    4 2 4 3 1 4 6
    70 60 50 40 30 20 10
    样例输出
    50

```c++
#include <iostream>
#include <stdio.h>
#define maxn 555
int d[maxn];
int w[maxn];
bool done[maxn];
using namespace std;
int main()
{
	int n,i,j,t;
	int sum=0;
	scanf("%d",&n);
	for(i=0;i<n;i++)
	{
		scanf("%d",&d[i]);
	}
	for(i=0;i<n;i++)
	{
		scanf("%d",&w[i]);
	}
/*按照时间进行排序，截止时间也随罚时排序*/
    for(i=0;i<n-1;i++)
	{
		for(j=0;j<n-1-i;j++)
		{
			if(w[j]<w[j+1])
			{
				t=w[j];
				w[j]=w[j+1];
				w[j+1]=t;
 
				t=d[j];
				d[j]=d[j+1];
				d[j+1]=t;
			}
		}
	}
/*done[]为时间槽，表示已有任务安排，j表示第几个单位时间*/
    for(i=0;i<n;i++)
	{
		for(j=d[i]; j;j--)
		{
			if(done[j]==0)
			{
				done[j]=1;
				break;
			}
 
		}
/*若都有安排，则将其加入总罚时时间sum*/
        if(j==0)
		{
			 sum+=w[i];
		}
	}
	printf("%d",sum);
	return 0;
}
``` 

### sqy 的锡纸烫

前不久 sqy 老师花了大价钱，去做了一个帅气的锡纸烫。有着商业眼光的 sqy 一下子发现了大商机，于是他自己开了一家美容美发店。

sqy 找了刚刚做完纹理烫的大预言家 cbj 预测了未来，发现每个顾客都只在白天来美发店，并且第一次来店里的时候都会充一次价值 $x_i$ 的卡，然后从<strong>第二天</strong>开始，每天白天都会来这里打理头发，而 sqy 仅收取成本价 $1$ 元钱来吸引顾客，直到把卡掏空为止，这个顾客就再也不会回来。

黑心商人 sqy 找大预言家要来了每个顾客的充卡时间和充值金额，他准备在某一天<strong>晚上</strong>跑路，他想知道自己最多能卷走多少钱。

输入数据

第一行包括一个整数 $n (1\le n\leq10^5)$ 表示有 $n$ 个顾客。
接下来共 $n$ 行，每$i+1$行包括两个整数 $x_i, y_i$ 表示第 $x_i$ 天一个顾客来充值了 $y_i$ 元 $(1\leq x_i\leq10^6, 0\leq y_i\leq2^{31}-1)$。

输出数据

输出一行包括一个整数 $ans$，表示 sqy 最多能卷走多少钱。

样例输入

    5
    1 5
    2 5 
    3 5
    4 5
    5 5

样例输出

    15

样例说明

在第五天的时候，第一个人消费4元还剩1元，第二个人消费3元还剩2元，第三个人消费2元还剩3元，第四个人消费1元还剩4元，第五个人还没有开始消费就被卷钱跑路了。

```c++
# include <iostream>
# include <cstdio>
# include <algorithm>
using namespace std;
long long ans = 0;
long long a[1000010], b[1000100];
int main(void)
{
	for (int i = 0; i < 1000010; i++) a[i] = b[i] = 0;
	long long n;
	scanf("%lld", &n);
	for (long long i = 1, x, y; i <= n; i++)
	{
		scanf("%lld%lld", &x, &y);

        //表示第x天收到的钱数
		a[x] += y;
        
        //表示从你第x天拿了一个顾客的钱那么x+1天就需要减钱给顾客
		b[x + 1]--;

        //r只是为了防止数组越界(b[r])
		long long r = min((long long)1000010, x + y + 1);

        //从x+y+1天开始，顾客就不再来了，你就无需再减钱给顾客
		b[r]++;
	}
	long long cha = 0;//这个代表当天需要减少的钱数
	long long tmp = 0;//记录当天的收益
    //
	for (int i = 1; i <= 1000000; i++)
	{
		cha += b[i];
		tmp += a[i];
		tmp += cha;
		ans = max(ans, tmp);
	}
	printf("%lld\n", ans);
	return 0;
}

```

# Internet
## Transport layer
信道利用率：
$$\frac{L/R}{RTT + L/R}$$

选择重传协议：SR protocol

最大报文段长度（MSS）用于在TCP连接建立时，收发双方协商通信时每一个报文段所能承载的最大数据长度（不包括文段头）

Consider transferring an enormous file of L bytes from Host A to Host B. Assume an MSS of 1,460 bytes.
对于TCP报文段来说，ack和sqe的增加是看增加了多少个字节的比如MSS有

一个字段是4个字节表示他有32个bit即32位，但是$2^{32}$位而它表示的可以储存的文件大小(即数据)$\approx$ 

---
    Consider transferring an enormous file of L bytes from Host A to Host B. Assume an MSS of 1,460 bytes.

    a.	What is the maximum value of L such that TCP sequence numbers are not exhausted? 
    Recall that the TCP sequence number fields has 4 bytes.

    b.	For the L you obtain in (a), find how long it takes to transmit the file. 
    Assume that a total of 66 bytes of transport, network, and data-link header are added to each segment before the 
    resulting packet is sent our over a 100 Mbps link. 
    Ignore flow control and congestion control so A can pump out the segments back to back and continuously.
    
    这道题主要是要把报文段有多少分组给算出来，这样的话用66*分组个数加上总的2^32bit
    就是总
---

因为分组序号在0和1之间交替，因此rdt3.0有时被称为比特交替协议（alternating－bit protocol）(停等协议)

# 机器学习

## 监督学习与非监督学习
有无预期输出是监督学习（supervised learning）与非监督学习（unsupervised learning）的区别。

监督学习（supervised learning）的任务是学习一个模型，使模型能够对任意给定的输入，对其相应的输出做出一个好的预测。
即：利用训练数据集学习一个模型，再用模型对测试样本集进行预测。

分类问题（离散）与回归问题（连续）等都是监督学习。

非监督学习（unsupervised learning）为直接对数据进行建模。没有给定事先标记过的训练范例，
所用的数据没有属性或标签这一概念。事先不知道输入数据对应的输出结果是什么。

如聚类算法：

针对数据集，自动找出数据中的结构，从而把数据分成不同的簇。

例如：谷歌新闻利用聚类算法把不同的主题放在一起。

## Precision，Recall，F1score，Accuracy的理解

## 交叉验证

分为训练集，验证集，测试集。
而把训练集和验证集打包在一块。
在训练集中

## 线性回归


[见此](https://blog.csdn.net/u014380165/article/details/77493978)

## 神经网络
M-P神经元模型：未知参数：权重weights与偏置项biases


### 感知机：
由两层神经元组成通过w1，w1和阈值，可以实现逻辑与或非

单层感知机对异或的感知能力较差，学习能力有限，只能解决线性可分问题

多层感知机：
### 多层前馈神经网络：
BP学习算法：对误差进行基于梯度下降法

## numpy基础：

### axis：
axis = 1为按行，axis = 0为按列


## 支持向量机 SVM

惩罚系数C

C过小，对超出ε管道的样本数据惩罚就小，训练误差变大；C过大，学习精度相应提高，但模型的泛化能力变差。

## 报错

Expected 2D array, got 1D array instead
```python
from sklearn.linear_model import LinearRegression
model1 = LinearRegression()
features1 =data.columns.tolist()#将data的列(属性)转化为list
target = ['Ir']
print(features1)
features1.remove('Ir')
print(features1)
x = data[features1]
y = data[target]
  
model1.fit(features1,features1)
```
这样写是错误的，fit里面要写的是data[features1]和data[target]所以会报错，
data[features1]是二维的矩阵，而feature1是1维的list

## pycharm主题
https://segmentfault.com/a/1190000020433630?utm_source=tag-newest

luanch: ./pycharm.sh 

# GitHub

## 下载代码
git clone 链接地址

[git教程](https://www.jianshu.com/p/c70ca3a02087)

## github镜像：
https://github.com.cnpmjs.org/
https://hub.fastgit.org/
https://github.wuyanzheshui.workers.dev/


# 计算机视觉基础

## 作业

### 目标检测之IoU、precision、recall、AP、mAP详解

[详解](https://www.pianshen.com/article/8644822005/)

# python 使用
## 查看python的安装路径：

    pip list
## anaconda 使用

    conda create --name env_name python=3.6

1)查看安装了哪些包

    conda list

2)查看当前存在哪些虚拟环境

    conda env list 
    conda info -e

激活或者切换虚拟环境

    **Linux:  source activate env_nam**
    Windows: activate env_name
6.关闭虚拟环境(即从当前环境退出返回使用PATH环境中的默认python版本)

    deactivate env_name
    或者`activate root`切回root环境
    Linux下：source deactivate 

5.对虚拟环境中安装额外的包

    conda install -n env_name [package]

7.删除虚拟环境

    conda remove -n your_env_name --all


## conda 还原初始源

conda config --remove-key channels

conda config --show 来分别查看自己电脑和服务器的channel


vim ~/.condarc 来分别查看自己电脑和服务器的channel


copy to ~/.condarc

    channels:
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/simpleitk
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    - defaults
    show_channel_urls: true
    default_channels:
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
    - http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
    custom_channels:
    conda-forge: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    msys2: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    bioconda: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    menpo: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    pytorch: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    pytorch-lts: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
    simpleitk: http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud



## qinhua

https ==> http  *useful*

conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2 
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/simpleitk


## zhongkeda
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
conda config --add channels http://mirrors.ustc.edu.cn/anaconda/cloud/pytorch/


conda config --remove channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/



https://repo.anaconda.com/pkgs/main/linux-64
https://repo.anaconda.com/pkgs/main/noarch
https://repo.anaconda.com/pkgs/free/linux-64
https://repo.anaconda.com/pkgs/free/noarch
https://repo.anaconda.com/pkgs/r/linux-64
https://repo.anaconda.com/pkgs/r/noarch
https://repo.anaconda.com/pkgs/pro/linux-64
https://repo.anaconda.com/pkgs/pro/noarch


## 激活 anaconda 环境
 source activate
## 退出 anaconda 环境
 source deactivate

作图

```python
    plt.figure(figsize = (12, 8))
    xi = np.array(X)
    ytesting = np.array(Ytesting)
    ytraining = np.array(Ytraining)
    plt.plot(xi,ytraining,'-',color = 'red',label = 'training')
    plt.plot(xi,ytesting,'-',color = 'blue',label = 'testing')
    plt.xlabel("depth")
    plt.ylabel("MAE")
    plt.xticks(xi[::1])
```
## 卷积

先卷积，再激活，再池化

### P@K

nm_20: 0.8721428571428573
nm_40: 0.8332142857142858
nm_60: 0.7969047619047618
tyht_20: 0.8323076923076921
tyht_40: 0.7696153846153847
tyht_60: 0.708205128205128
tsg_20: 0.8008064516129035
tsg_40: 0.7318548387096772
tsg_60: 0.6647849462365593
sjz_20: 0.9769841269841271
sjz_40: 0.9638888888888888
sjz_60: 0.9505291005291007
sy_20: 0.6884615384615385
sy_40: 0.5831730769230771
sy_60: 0.5096153846153846

Process finished with exit code 0


## 贝叶斯

# 实现一个高斯朴素贝叶斯分类器

## 符号

给定训练集 $T$

$$T = \{(x_1, y_1), (x_2, y_2), ···, (x_N, y_N)\}$$

其中，$x$ 为样本的特征，$y$ 是该样本对应的标记，下标表示对应的是第几个样本，上标表示第几个特征。训练集 $T$ 内一共 $\vert T \vert = N$ 个样本。

假设我们的任务是处理 $K$ 类分类任务，记类标记分别为 $c_1, c_2, ..., c_k$ 。

## 目标

我们的目标是对样本进行分类，这里我们用概率的方法，求 $P(Y = c_k \mid X = x), \ k = 1, 2, ..., K$ 中最大的那个概率对应的 $k$ 是哪个，也就是，给定样本 $x$ ，模型认为它是哪个类别的概率最大。

## 原理

由贝叶斯公式：

$$
\begin{aligned}
    P(Y = c_k \mid X = x) &= \frac{P(Y = c_k, X = x)}{P(X = x)} \\
                  &= \frac{P(X = x \mid Y = c_k)P(Y = c_k)}{\sum_kP(X = x \mid Y = c_k)P(Y = c_k)} \\
\end{aligned}
$$

这里，我们要求 $K$ 个概率中最大的那个，而这 $K$ 个概率的分母都相同，我们可以忽略分母部分，比较分子部分的大小，也就是比较 **先验概率** $P(Y = c_k)$ 和 **似然** $P(X = x \mid Y = c_k)$ 的乘积。

通过先验概率分布

$$
P(Y = c_k), \ k = 1, 2, ..., K
$$

和条件概率分布

$$
P(X = x \mid Y = c_k) = P(X^{(1)} = x^{(1)}, ···, X^{(n)} = x^{(n)} \mid Y = c_k), \ k = 1, 2, ..., K
$$

我们就可以得到联合概率分布 $P(X = x, Y = c_k)$ 。

### 1. 先验概率 $P(Y = c_k)$ ：

先验概率的求解很简单，只要统计训练集中类别 $k$ 出现的概率即可。

$$
P(Y = c_k) = \frac{\mathrm{number} \ \mathrm{of}\ c_k}{N}
$$

### 2. 似然 $P(X = x \mid Y = c_k)$ ：

求解这个条件概率比较复杂，**这里我们要假设特征之间相互独立**，可得

$$P(X = x \mid Y = c_k) = \prod^n_{j=1}P(X^{(j)}=x^{(j)} \mid Y = c_k)$$

其中， $x^{(j)}$ 表示样本 $x$ 的第 $j$ 个特征。

这样，复杂的条件概率就转换为了多个特征条件概率的乘积。

### 3. 特征 $j$ 的条件概率 $P(X^{(j)}=x^{(j)} \mid Y = c_k)$ ：

因为我们处理的特征都是连续型特征，一般我们假设这些特征服从正态分布。

当 $Y = c_k$ 时，$X^{(j)} = a_{jl}$ 的概率可由下面的公式计算得到：

$$
P(X^{(j)} = a_{jl} \mid Y = c_k) = \frac{1}{\sqrt{2 \pi \sigma^2_{c_k,j}}} \exp{\bigg( - \frac{(a_{jl} - \mu_{c_k,j})^2}{2 \sigma^2_{c_k,j}} \bigg)}
$$

这里 $\mu_{c_k,j}$ 和 $\sigma^2_{c_k,j}$ 分别表示当 $Y = c_k$ 时，第 $j$ 个特征的均值和方差，**这个均值和方差都是通过训练集的样本计算出来的**。

因为正态分布只需要两个参数（均值和方差）就可以确定，对于特征 $j$ 我们要估计 $K$ 个类别的均值和方差，所以特征 $j$ 的参数共有 $2K$个。

## 综上

朴素贝叶斯分类器可以表示为：

$$
y = \mathop{\arg\max}_{c_k} P(Y = c_k) \prod_j P(X^{(j)} = x^{(j)} \mid Y = c_k)
$$

## 实现
实现的时候会遇到数值问题，在上面的条件概率连乘中，如果有几个概率值很小，它们的连乘就会导致下溢，解决方案就是将其改写为连加的形式。

首先，我们的目标是：

$$
y = \mathop{\arg\max}_{c_k} P(Y = c_k) \prod_j P(X^{(j)} = x^{(j)} \mid Y = c_k)
$$

比较这 $K$ 个数值的大小，然后取最大的那个数对应的 $k$。

为了解决可能出现的下溢问题，我们对上面的式子取对数，因为是对 $K$ 项都取对数，不会改变单调性，所以取对数是不影响它们之间的大小关系的。

那目标就变成了：

$$
\begin{aligned}
y &= \mathop{\arg\max}_{c_k} \big[ \log^{ \ P(Y = c_k) \prod_j P(X^{(j)} = x^{(j)} \mid Y = c_k)} \big] \\
&= \mathop{\arg\max}_{c_k} \big[ \log^{ \ P(y = c_k)} + \sum_j \log^{ \ P(X^{(j)} = x^{(j)} \mid Y = c_k)} \big]
\end{aligned}
$$

在求条件概率的时候，也进行变换：

$$\begin{aligned}
\log^{ \ P(X^{(j)} = x^{(j)} \mid Y = c_k)} &= \log^{ \ \bigg[\frac{1}{\sqrt{2 \pi \sigma^2_{c_k,j}}} \exp{\bigg(- \frac{(a_{jl} - \mu_{c_k,j})^2}{2 \sigma^2_{c_k,j}}\bigg)}\bigg]}\\
&= \log^{ \frac{1}{\sqrt{2 \pi \sigma^2_{c_k,j}}} } + \log^{ \exp{\bigg(- \frac{(a_{jl} - \mu_{c_k,j})^2}{2 \sigma^2_{c_k,j}}\bigg)} }\\
&= - \frac{1}{2} \log^{2 \pi \sigma^2_{c_k,j}} - \frac{1}{2} \frac{(a_{jl} - \mu_{c_k,j})^2}{\sigma^2_{c_k,j}}
\end{aligned}
$$

所以，高斯朴素贝叶斯就可以变形为：

$$
y = \mathop{\arg\max}_{c_k} \bigg[ \log^{ \ P(y = c_k)} + \sum_j \big( - \frac{1}{2} \log^{2 \pi \sigma^2_{c_k,j}} - \frac{1}{2} \frac{(a_{jl} - \mu_{c_k,j})^2}{\sigma^2_{c_k,j}} \big) \bigg]
$$

上式就是我们需要求的，我们要求出 $K$ 个值，然后求最大的那个对应的 $k$。

## 实现代码：
``` python
class myGaussianNB:
    '''
    处理连续特征的高斯朴素贝叶斯
    '''
    def __init__(self):
        '''
        初始化四个字典
        self.label_mapping     类标记 与 下标(int)
        self.probability_of_y  类标记 与 先验概率(float)
        self.mean              类标记 与 均值(np.ndarray)
        self.var               类标记 与 方差(np.ndarray)
        '''
        self.label_mapping = dict()
        self.probability_of_y = dict()
        self.mean = dict()
        self.var = dict()
        
    def _clear(self):
        '''
        为了防止一个实例反复的调用fit方法，我们需要每次调用fit前，将之前学习到的参数删除掉
        '''
        self.label_mapping.clear()
        self.probability_of_y.clear()
        self.mean.clear()
        self.var.clear()
    
    def fit(self, trainX, trainY):
        '''
        这里，我们要根据trainY内的类标记，针对每类，计算这类的先验概率，以及这类训练样本每个特征的均值和方差

        Parameters
        ----------
            trainX: np.ndarray, 训练样本的特征, 维度：(样本数, 特征数)
        
            trainY: np.ndarray, 训练样本的标记, 维度：(样本数, )
        '''
        
        # 先调用_clear
        self._clear()
        
        # 获取类标记
        labels = np.unique(trainY)
        
        # 添加类标记与下标的映射关系
        self.label_mapping = {label: index for index, label in enumerate(labels)}
        
        # 遍历每个类
        for label in labels:
            
            # 取出为label这类的所有训练样本，存为 x
            x = trainX[trainY == label, :]
            
            # 计算先验概率，用 x 的样本个数除以训练样本总个数，存储到 self.probability_of_y 中，键为 label，值为先验概率
            # YOUR CODE HERE 
            self.probability_of_y[label] = x.shape[0]/trainX.shape[0]
            
            # 对 x 的每列求均值，使用 keepdims = True 保持维度，存储到 self.mean 中，键为 label，值为每列的均值组成的一个二维 np.ndarray
            # YOUR CODE HERE
            self.mean[label] = x.mean(axis = 0,keepdims = True)
            
            # 这句话是debug用的，如果不满足下面的条件，会直接跳出
            assert self.mean[label].shape == (1, trainX.shape[1])
            
            # 对 x 的每列求方差，使用 keepdims = True 保持维度，存储到 self.var 中，键为 label，值为每列的方差组成的一个二维 np.ndarray
            # YOUR CODE HERE
            self.var[label] = x.var(axis = 0,keepdims = True)
            
            # debug
            assert self.var[label].shape == (1, trainX.shape[1])
            
            # 平滑，因为方差在公式的分母部分，我们要加一个很小的数，防止除以0
            self.var[label] += 1e-9 * np.var(trainX, axis = 0).max()
        
    def predict(self, testX):
        '''
        给定测试样本，预测测试样本的类标记，这里我们要实现化简后的公式

        Parameters
        ----------
            testX: np.ndarray, 测试的特征, 维度：(测试样本数, 特征数)
    
        Returns
        ----------
            prediction: np.ndarray, 预测结果, 维度：(测试样本数, )
        '''
        
        # 初始化一个空矩阵 results，存储每个样本属于每个类的概率，维度是 (测试样本数，类别数)，每行表示一个样本，每列表示一个特征
        results = np.empty((testX.shape[0], len(self.probability_of_y)))
        
        # 初始化一个列表 labels，按 self.label_mapping 的映射关系存储所有的标记，一会儿会在下面的循环内部完成存储
        labels = [0] * len(self.probability_of_y)
        
        # 遍历当前的类，label为类标记，index为下标，我们将每个样本预测出来的这个 label 的概率，存到 results 中的第 index 列
        for label, index in self.label_mapping.items():
            
            # 先验概率存为 py
            py = self.probability_of_y[label]
            
            # 使用变换后的公式，计算所有特征的条件概率之和，存为sum_of_conditional_probability
            # YOUR CODE HERE
            sum_of_conditional_probability =  np.zeros(len(testX),)
            for i in range(len(testX)):
                var1 = self.var[label]
                mean1 = self.mean[label]
                sum_of_conditional_probability[i] += (-0.5) * np.log(2*np.pi*var1).sum()
                sum_of_conditional_probability[i] += (-0.5) * (np.power(testX[i]-mean1,2)/var1).sum()

            
            # debug
            assert sum_of_conditional_probability.shape == (len(testX), )
            
            # 使用变换后的公式，将 条件概率 与 log先验概率 相加，存为result，维度应该是 (测试样本数, )
            # YOUR CODE HERE
            result = sum_of_conditional_probability+np.log(py)
            
            # debug
            assert result.shape == (len(testX), )
            
            # 将所有测试样本属于当前这类的概率，存入到results中
            results[:, index] = result
            
            # 将当前的label，按index顺序放入到labels中
            labels[index] = label
        
        # 将labels转换为np.ndarray
        np_labels = np.array(labels)
        
        # 循环结束后，就计算出了给定测试样本，当前样本属于这类的概率的近似值，存放在了results中，每行对应一个样本，每列对应一个特征
        # 我们要求每行的最大值对应的下标，也就是求每个样本，概率值最大的那个下标是什么，结果存入max_prob_index中
        # YOUR CODE HERE
        max_prob_index = np.argmax(results,axis=1)
        
        # debug
        assert max_prob_index.shape == (len(testX), )
        
        # 现在得到了每个样本最大概率对应的下标，我们需要把这个下标变成 np_labels 中的标记
        # 使用上面小技巧中的第五点求解
        # YOUR CODE HERE
        prediction = np_labels[max_prob_index]
        
        # debug
        assert prediction.shape == (len(testX), )
        
        # 返回预测结果
        return prediction

```

## 在linux环境下编译运行OpenCV程序的两种方法OpenCV compile

### 第一种方法：Command Line（使用命令行参数的方法）

gcc Test.c -o Test `pkg-config --cflags --libs opencv`

### cvtColor() function

opencv提供了cvtColor()函数，用于在图像中不同的色彩空间进行转换，用于后续处理。在使用cvtColor之前首先需要了解下基本的图像色彩模式，色彩模式决定了打印或显示的图片颜色。


void cv::cvtColor(	InputArray src,
                    OutputArray dst,
                    int code,
                    int dstCn = 0 )


## linux cuda nvcc

nvcc -std=c++11 -o test test.cu

nvcc -o test test.cu

### cudaMemcpy

```c++
cudaMemcpy(d_in, src.data, memsize, cudaMemcpyHostToDevice);
```

主机到设备：cudaMemcpy(d_A,h_A,nBytes,cudaMemcpyHostToDevice)

设备到主机：cudaMemcpy(h_A,d_A,nBytes,cudaMemcpyDeviceToHost)


cudaMemcpy用于在主机（Host）和设备（Device）之间往返的传递数据

版本	                Python 版本	编译器	构建工具	cuDNN	          CUDA
tensorflow_gpu-1.15.0	2.7、3.3-3.7	GCC 7.3.1	Bazel 0.26.1	7.4	10.0

## GCC version

### 查看系统已装gcc

ls /usr/bin/gcc*

### 查看当前系统使用gcc

gcc -v

设置优先级

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 30
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 40
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 50

sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 30
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-6 40
sudo update-alternatives --install /usr/bin/g++ gc++/usr/bin/g++-5 50

或者（--slave后面加入g++是当切换gcc版本时也同时切换g++）（推荐）

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 70 --slave /usr/bin/g++ g++ /usr/bin/g++-7

接着查看

sudo update-alternatives --config gcc

## zip

解压命令unzip常用方法汇总：

1、把文件解压到当前目录下

unzip pythontab.com.zip
2、如果要把文件解压到指定的目录下，需要用到-d参数。

unzip -d ./tmp/ pythontab.com.zip

3、解压的时候，有时候不想覆盖已经存在的文件，那么可以加上-n参数

unzip -n pythontab.com.zip

unzip -n -d ./tmp/ pythontab.com.zip

4、只看一下zip压缩包中包含哪些文件，不进行解压缩

unzip -l pythontab.com.zip

5、查看显示的文件列表还包含压缩比率

unzip -v pythontab.com.zip

6、检查zip文件是否损坏

unzip -t pythontab.com.zip

7、将压缩文件pythontab.com.zip在指定目录tmp下解压缩，如果已有相同的文件存在，要求unzip命令覆盖原先的文件

unzip -o pythontab.com.zip -d ./tmp

### python: range()

range(start, stop, step)

start: 计数从 start 开始。默认是从 0 开始。例如range（5）等价于range（0， 5）;

stop: 计数到 stop 结束，但不包括 stop。例如：range（0， 5） 是[0, 1, 2, 3, 4]没有5

step：步长，默认为1。例如：range（0， 5） 等价于 range(0, 5, 1)

    >>> range(0, 30, 5)  # 步长为 5
    [0, 5, 10, 15, 20, 25]


## ubuntu command / linux command 

1、创建一个目录

    $ sudo mkdir <目录名>
 
2、删除一个非空目录下的一切

    $ sudo rm -rf <目录名>
 
3、将文件file1，更改文件名为file2。

    $ sudo mv file1 file2
 
4、将文件file1，移动到目录dir1下，文件名仍为file1。

    $ sudo mv file1 dir1
 
5、若目录 dir2 存在，则将目录 dir1，及其所有文件和子目录，移到目录 dir2 下，新目录名称为 dir1。若目录 dir2 不存在，则将dir1，及其所有文件和子目录，更改为目录 dir2。

    $ sudo mv dir1 dir2

6.rar command

    rar a -r k-means cluster

7.rm

-r 就是向下递归，不管有多少级目录，一并删除

rm -f /var/log/httpd/access.log //file

rm -rf /var/log/httpd/access    //folder

8.mkdir 命令的基本格式为：

    [root@localhost ~]# mkdir [-mp] 目录名
    -m 选项用于手动配置所创建目录的权限，而不再使用默认权限。
    -p 选项递归创建所有目录，以创建 /home/test/demo 为例，在默认情况下，你需要一层一层的创建各个目录，而使用 -p 选项，则系统会自动帮你创建 /home、/home/test 以及 /home/test/demo。


### linux 下编译运行MPI
如果是C程序，使用如下命令进行编译：

> mpicc test.c -o test

如果是C++程序，使用如下命令进行编译：

> mpicxx test.cpp -o test

编译完成后，使用如下命令运行

> mpirun -np 4 ./test

### win10 下编译运行MPI

> mpiexec -np n test.exe

### linux
> mpiexec -n 4 ./out

### linux mpi与omp一起编译运行：

// mpicc demo2.c -o demo2 -fopenmp
// mpirun ./demo2 -up 6


## linux kunpen920 connect

ssh student37@172.31.46.191

ssh student73@172.31.46.192

**logout**

## ssh function

### 1、从服务器上下载文件

scp username@servername:/path/filename /var/www/local_dir

### 2、上传本地文件到服务器
scp /path/filename username@servername:/path   

# SSH 免密登录

## 1.在 *student73@172.31.46.192* 机器上生成公钥/私钥对

ssh-keygen -t rsa

根据提示，回车即可，提示输入密码时回车即表示空密码。在用户根目录下生成.ssh文件夹，里面包括id_rsa（私钥）和id_rsa.pub（公钥）。

## 2.将 *student73@172.31.46.192*(A) 机器的id_rsa.pub复制到 *student37@172.31.46.191*(B) 机器下

scp ~/.ssh/id_rsa.pub student37@172.31.46.191:~/.ssh/node2_id_rsa.pub       //避免名字重复加上对应节点的前缀，节点2就加node2

scp ~/.ssh/id_rsa.pub student37@172.31.46.191:~/.ssh/node2_id_rsa.pub

这一步还需要输入 *student37@172.31.46.191* 机器的密码。

## 3.在B机器上将A机器的id_rsa.pub添加到B机器的.ssh/authorized_keys，并将authorized_keys的权限改成600

cat /home/student37/.ssh/nd_rsa.pub >> /home/student37/.ssh/authorized_keys

chmod 600 ~/.ssh/authorized_keys

### 3、从服务器下载整个目录
scp -r username@servername:/var/www/remote_dir/（远程目录） /var/www/local_dir（本地目录）

例如:scp -r student37@172.31.46.191:/var/www/test /var/www/

### 4、上传目录到服务器
scp -r local_dir username@servername:remote_dir
例如：scp -r test student37@172.31.46.191:./

把当前目录下的test目录上传到服务器的/var/www/ 目录

### 3.2 - L-layer Neural Network

The initialization for a deeper L-layer neural network is more complicated because there are many more weight matrices and bias vectors. When completing the `initialize_parameters_deep`, you should make sure that your dimensions match between each layer. Recall that $n^{[l]}$ is the number of units in layer $l$. Thus for example if the size of our input $X$ is $(12288, 209)$ (with $m=209$ examples) then:




<tr>
    <td>  </td> 
    <td> **Shape of W** </td> 
    <td> **Shape of b**  </td> 
    <td> **Activation** </td>
    <td> **Shape of Activation** </td> 
<tr>

<tr>
    <td> **Layer 1** </td> 
    <td> $(n^{[1]},12288)$ </td> 
    <td> $(n^{[1]},1)$ </td> 
    <td> $Z^{[1]} = W^{[1]}  X + b^{[1]} $ </td> 
    
    <td> $(n^{[1]},209)$ </td> 
<tr>

<tr>
    <td> **Layer 2** </td> 
    <td> $(n^{[2]}, n^{[1]})$  </td> 
    <td> $(n^{[2]},1)$ </td> 
    <td>$Z^{[2]} = W^{[2]} A^{[1]} + b^{[2]}$ </td> 
    <td> $(n^{[2]}, 209)$ </td> 
<tr>

    <tr>
    <td> $\vdots$ </td> 
    <td> $\vdots$  </td> 
    <td> $\vdots$  </td> 
    <td> $\vdots$</td> 
    <td> $\vdots$  </td> 
<tr>

<tr>
    <td> **Layer L-1** </td> 
    <td> $(n^{[L-1]}, n^{[L-2]})$ </td> 
    <td> $(n^{[L-1]}, 1)$  </td> 
    <td>$Z^{[L-1]} =  W^{[L-1]} A^{[L-2]} + b^{[L-1]}$ </td> 
    <td> $(n^{[L-1]}, 209)$ </td> 
<tr>


<tr>
    <td> **Layer L** </td> 
    <td> $(n^{[L]}, n^{[L-1]})$ </td> 
    <td> $(n^{[L]}, 1)$ </td>
    <td> $Z^{[L]} =  W^{[L]} A^{[L-1]} + b^{[L]}$</td>
    <td> $(n^{[L]}, 209)$  </td> 
<tr>



Remember that when we compute $W X + b$ in python, it carries out broadcasting. For example, if: 

$$ W = \begin{bmatrix}
    j  & k  & l\\
    m  & n & o \\
    p  & q & r 
\end{bmatrix}\;\;\; X = \begin{bmatrix}
    a  & b  & c\\
    d  & e & f \\
    g  & h & i 
\end{bmatrix} \;\;\; b =\begin{bmatrix}
    s  \\
    t  \\
    u
\end{bmatrix}\tag{2}$$

Then $WX + b$ will be:

$$ WX + b = \begin{bmatrix}
    (ja + kd + lg) + s  & (jb + ke + lh) + s  & (jc + kf + li)+ s\\
    (ma + nd + og) + t & (mb + ne + oh) + t & (mc + nf + oi) + t\\
    (pa + qd + rg) + u & (pb + qe + rh) + u & (pc + qf + ri)+ u
\end{bmatrix}\tag{3}  $$




复试，上机：
```c++
#include<vector>
#include<map>
//容器写法：
container<type> variable    //这里 ‘container<type>’ 整个也是一个type，是递归定义的
//容器的迭代器：顺序遍历
container<type>::iterator iter;     //声明一个迭代器
for(iter = variable.begain();iter != variable.end();iter++)
    *iter   //如果是map则用iter->first与iter->second分别表示map的key和value。
//逆序遍历：
container<type>::reverse_iterator iter;
for(iter = variable.rbegain();iter != variable.rend();iter++)
    *iter   //如果是map则用iter->first与iter->second分别表示map的key和value。
//***特别注意***:
//如果中途容器中添加或删除了东西的话，迭代器将会失效！！！因为他是动态分配的 


//map容器举例：
map<char, int> char2int;
char2int.clear();       //清空map
char2int['a'] = 2;      //添加元素
char2int.count('a')     //判断是否有key为'a'的元素，如果有则返回1否则返回0
iter = char2int.find(key);   //find()方法是返回一个迭代器，如果没有找到这个key则返回char2int.end();
if(char2int.find(key) != char2int.end())
    cout<<iter->first<<iter->second<<endl;    //输出这个迭代器指向的key和value

//vector容器举例：
vector<int> vec(10, 0);   //一维
vector<vector<type> > vec(len1, vector<type>(len2, value));     //二维vector
vector<int> vec(10, 0);
vector<int>::iterator iter;     //声明一个迭代器
vec.push_back(10);      //向量尾部增加一个元素
//特别注意迭代器复制之后无效，只有在语句内赋值才有效！！！
vec.insert(vec.begin(), 9);  //迭代器的前一个位置增加一个元素
vec.pop_back();         //删除vector中最后一个元素
for(iter = vec.begin();iter!=vec.end();iter++)
    cout<<*iter<<endl;
vec.size();     //返回vec元素个数
reverse(vec.begin(),vec.end()) 逆置容器


//string类举例(不是容器)
string s1 = "ab123";
string s2 = "ab25656";
s1[0];//取值  不能像python一样切片
s1.substr(起始位置,长度);//c++取子串
s1.size();
//字符串直接用大于小于号比较大小,默认字典序(数字小于字母)
cout<< s1<s2 << endl;

//queue容器举例 'queue与stack没有迭代器'
//queue想要遍历只能通过遍历每一个元素并且边遍历(遍历即使用que.front()方法)边删除
queue<int> que;     //创建一个队列
que.empty();        //判断是否为空，空则返回1，否则返回0
while(!que.empty()) que.pop();   //que清空,没有clear函数
que.push(1);        //在队尾处入队一个元素
que.pop();          //在队首处出队
que.front();        //返回队首的引用，'明白C++的引用的用法吗？'
que.back();         //返回队尾的引用。
que.size();

//priority_queue容器举例 '这个容器的头文件同样是<queue>'优先队列本质上是堆比如大根堆或者小根堆
//类型的写法为： 'priority_queue<Type, Container, Functional>' 如果只填type其他两个缺省则默认container为vector，functional为大根堆模式
//默认模式遵循'First in，Largest out' 即先进者不一定先出，而是优先级最高的先出队
priority_queue<int> big2small;      //优先队列，相当于自动排序的队列，默认从大到小
priority_queue<int, vector<int>, greater<int> > small2big;     //小根堆
priority_queue<int, vector<int>, less<int> > big2small2;       //跟第一个一样，大根堆
//除了front和top的不同 其余和queue一样
big2small.push(5);// 头 5 尾
big2small.push(8);// 头 8 5 尾
big2small.push(4);// 头 8 5 4 尾
big2small.top();//读头 注意queue是front, 返回8
big2small.pop();//头 5 4 尾

//stack容器举例
stack<int> st;
st.empty();     //判断栈是否为空，空则返回1
st.push();      //入栈一个元素
st.pop();       //出栈一个元素
st.top();       //返回栈顶，类型是C++的引用
st.size();      //返回元素个数

//set(集合)容器举例
set<int>s;      //集合,保证元素不重复
s.clear();      //清空
s.insert(1);    //插入1
s.insert(1);    //无效插入 但是不报错
s.erase(1);     //删除指定元素 没有pop
s.count(1);     //查询是否有元素

//其他函数用法

//内置二分查找，**前提是有序的情况下**，lower_bound返回指向第一个值不小于val的位置，也就是返回第一个大于等于val值的位置(通过二分查找)
//即返回一个迭代器，注意迭代器不能直接cout，只能用 'iter1 - vec.begin()' 这种形式输出iter1的下标
//注意，虽然这里是二分查找，但是可以用 if(*iter == value)来判断是否存在这个元素
sort(vec.begin(),vec.end());
lower_bound(vec.begin(),vec.end(), value)

min(a,b) max(a,b) swap(a,b) //分别是求最小值最大值和交换两个元素的位置

//关于输入的统一格式
//C++的输入：
while(cin >> a >> b){
    statement;
}


//c输入
while(2 == scanf("%d%d",&a, &b)){
    statement;
}


//整行输入:
//c:
scanf("%s");
//c++:这里的getline是string头文件中的getline，所以s应定义为string类
getline(cin, s);

//介绍一个stringstream类型
#include<sstream>
#include<string>
string str_a = "2.34523e3";     //这个是2.34523 * 10 ^ 3
double double_a;
stringstream ss1, ss2;      //特别注意每个ss只能用一次，不可重复使用ss1与ss2
ss1 << str_a;        //注意这两个运算式子只能是stringstream类的放在前面，如同cin与cout，不能让ss在"<<" or ">>"的右边出现
ss1 >> double_a;     
cout<<double_a<<endl;
double_a += 30;
ss2 << double_a;
ss2 >> str_a;
cout <<str_a<<endl; 






```

# dp动态规划：
## 数组中最大连续子序列和：
```c++

//解释：让dp[i]表示以第i个元素为结尾的子数组的最大连续子序列和，
//则状态转移方程可写为：dp[i] = max(a[i - 1],dp[i] + a[i - 1]);
//base case 为'dp[0] = 0'即空集合中的元素和为0.
for(int i = 1;i <= len;i++){
    dp[i] = max(a[i - 1],dp[i] + a[i - 1]);
}
//别忘了最后要把最大连续子序列给跳出来:
int max = -99999;
for(int i = 1;i <= len;i++){
    max = max(max, dp[i]);
}
```

sort函数：

```c++
//有一个node类型的数组node arr[100]，想对它进行排序：先按a值升序排列，如果a值相同，再按b值降序排列，如果b还相同，就按c降序排列。就可以写一个比较函数：
bool cmp(node x,node y){    
    if(x.a != y.a) return x.a < y.a;    
    if(x.b != y.b) return x.b > y.b;    
    return x.c > y.c;
}
//如果是对一个二维数组：先按a值升序排列，如果a值相同，再按b值降序排列，如果b还相同，就按c降序排列:
bool cmp(int** a,int** b){    
    if((*a)[0] != (*b)[0]) return (*a)[0] < (*b)[0];    
    if((*a)[1] != (*b)[1]) return (*a)[1] > (*b)[1];
    return (*a)[2] > (*b)[2];
}
int main(void){
    sort(a,a+100,cmp);
    return 0;
}

```
# 算法笔记
```c++
//格式化输入输出： 'double -> %lf', 'long long -> %lld'
//三种实用的输出格式: '%md -> 不足m位的int变量以m位进行右对齐输出，高位用空格补齐，超过m位则原样输出'
//'%0md -> 同%md只不过用0补齐不用空格'
//'%.mf -> 让浮点数保留m位小数输出
//round函数:在math.h里面的四舍五入函数
char c1 = getchar();    //接受单个字符存储到一个char型变量中
getchar();              //接受单个字符，但是不存储
putchar(c1);            //输出一个字符
putchar('c');           //输出一个字符
//常用的<math.h>里的函数：
fabs(double x)      //取绝对值
floor(double x)     //向左取整
ceil(double x)      //向右取整
pow(double x, double y)     //x ^ y
sqrt(double x)      //对x开算数平方根
log(double x)       //即ln(x)，如果是以a为底，以b为真数则要用换底公式ln(b) / ln (b)
sin(), cos(), tan(), asin(), acos(), atan() 


```




# leetcode总结
动态规划系列:  
## 子序列类型
回文系列：让i，j分别指向本字符串的不同字符，且i < j，选定base case为dp[i][i]即dp矩阵的对角线位置。从dp矩阵的右下角开始遍历，即i = len - 1, j = i + 1  
两个字符串的编辑距离系列：让i, j分别指向两个字符串的其中一个字符，选定base case 为i = 0 or j = 0，即为dp矩阵的第一行和第一列。(注意这里的dp矩阵的行数和列数分别为len1 + 1, len2 + 1。因为i和j从字符串的第'-1'下标开始，而不是'0'下标，但是这里要注意第i个字符对应的是s[i - 1])
递增数组，最大子数组系列：让i表示以i结尾的子序列数组的dp状态。这样通过前i - 1个dp状态后可以知道当前dp[i]的状态
## 背包类型  
0-1背包系列：让dp[i][W]代表前i个物品内，在背包容量为W时最多能装下的value，那么dp[i][W] = max(dp[i - 1][W - Wi] + value[i], dp[i - 1][W]) (其中W - Wi >= 0 && W <= W_max)  
子集背包问题：关键和0-1背包类似，即用条件判断语句和状态选择方程构造出***选择或不选***这个行为。让dp[i][j]表示前i个物品内是否可以恰好凑出j这个数字。最后的ret为dp[i][sum / 2]注意边界条件。注意可以利用状态转移方程来检验一下边界情况和条件判断，因为i - 1，j - num[i]很有可能越界。
完全背包系列: 状态转移方程不一样了，数学推导就不写了，dp[i][j] = max(dp[i - 1][j], dp[j - wi] + vi). 由于零钱兑换2问题是问组合数，所以改写状态转移方程为dp[i][j] = dp[i - 1][j] + dp[j - wi] + vi  
## 状态机问题

# 在写代码的时候的需要注意的问题：
```
1. 拼写string.length();
2. string类中第i个元素为string[i - 1]不是string[i]
3. 注意dp[][]的i, j遍历位置和范围，起始位置别出错，i, j不要越界数组范围
4. s1, s2, len1, len2, i, j要搞清楚搭配，不要弄混了在各个字符串中的搭配
5. 特别要注意**有时候**设置dp数组时，第i个元素对应的是dp[i]但是在string或者array可能对应的元素是string[i - 1], array[i - 1].
6. 对于DFS算法来说现在积累有三种写法：bool, int, void: 分别对应判断是否可行、递归分解子问题(类似DP或者分治)、回溯求解路径
7. 现在草稿纸上打好框架，别一上来就用计算机
8. 经过测试发现，10^9，500^3的时间复杂度可以接受，1000000^2(二维数组)的复杂度不可以接受，4000^2(二维数组)的空间复杂度可以接受，1000000(一维)的空间复杂度可以接受
```

# 数学问题，模拟问题系列：要敏锐的分析出什么是数学题，什么是算法题
1. 在求阶乘0的个数问题，可以转化为更一般的形式：时间复杂度为logn或者为nlogn级别：即***求一个数n!中能分解出多少个x的因子***方法如下：  
logn级别：先求出数从1 -> n中有多少可分接出x的数字，再求出从1 -> n中有多少可以分解出x^2的数字...然后将这些数字依次相加则为最终答案当x^i > n时将跳出循环  
nlogn级别：从1 -> n中求出可以分解出x因子的个数t，再从1 -> t依次计算i*x能分解出多少个x,然后依次相加即可  

# 二分查找
1. 寻找某个数：用左闭右闭的方法即[left, right].此时循环的条件为left <= right, 因为如果条件为 '<' 的话就会漏掉[left, left]这一种情况.此时right为数组最后一个数的下标，跳出条件为left = right + 1.  
```c++
int binarySearch(int[] nums, int target) {
    int left = 0; 
    int right = nums.length - 1; // 注意

    while(left <= right) {
        int mid = left + right / 2;
        if(nums[mid] == target)
            return mid; 
        else if (nums[mid] < target)
            left = mid + 1; // 注意
        else if (nums[mid] > target)
            right = mid - 1; // 注意
    }
    return -1;
}
int binary_get(int A[], int left, int right, int val){
    //A 必须严格递增
    //right = A's length - 1
    //left = 0
    //区间为[left, right]
    while(left < right){
        int mid = (left + right) / 2;
        if(A[mid] == val) return mid;
        else if(A[mid] < val) left = mid + 1;   //往右边区间搜索
        else if(A[mid] > val) right = mid - 1;  //往左边区间搜索
    }
    return -1;
}
```
2. lower_bound:寻找某个数的左侧边界，如果这个数不存在于这个数组中则***返回他如果存在的话***可能存在的位置：注意此时right为数组最后一个数的下标 + 1, 因为此时是左闭右开的区间，跳出条件为left == right， 可能返回数组最后一个数字的下标 + 1，即数组长度
```c++
int lower_bound(int A[],int left,int right,int x){
    int mid;
    while(left < right){
        mid = (left + right)/2;
        if(A[mid] >= x) right = mid;    //当找到了x时继续缩小范围
        else if(A[mid] < x) left = mid + 1;
    }
    return left;
}
```
3. upper_bound:可能返回-1
```c++
int upper_bound(int A[],int left,int right,int x){
    while (left < right) {
        int mid = (left + right) / 2;
        if (A[mid] > x) right = mid;
        else if (A[mid] <= x) left = mid + 1;
    }
    return left - 1; // 注意
}
```
机器学习：

transformer: Sequence2sequence
Sequence to sequence model:
Encoder:

pre-train model:
通过self-supervise learning预训练出来一个模型，是一个上游任务
出来的模型可以通过fine-tune来作用于下游任务。

毕设  
# Paper: Deep Clustering for Unsupervised Learning of Visual Features  

1) preliminary: It uses a standard AlexNet architecture. It consists of five convolutional layers with 96, 256, 384, 384 and 256 filters; and of three fully connected layers. It removes the Local Response Normalization layers and use batch normalization. cost function is the multinomial logistic loss. This cost function is minimized using mini-batch stochastic gradient descent and backpropagation to compute the gradient.  
2) clustering the output of the convnet and use the subsequent cluster assignments as “pseudo-labels” to optimize Eq. (1). This deep clustering (DeepCluster) approach iteratively learns the features and groups them.
![Alt text](./picture/16.png)  

# Paper: A Simple Framework for Contrastive Learning of Visual Representations
This paper presents SimCLR: a simple framework for contrastive learning of visual representations.  
profile:
Inspired by recent contrastive learning algorithms (see Section 7 for an overview), SimCLR learns representations by maximizing agreement between differently augmented views of the same data example via a contrastive loss in the latent space. As illustrated in Figure 2, this framework comprises the following four major components.  
1)***A stochastic data augmentation module*** that transforms any given data example randomly resulting in two correlated views of the same example, denoted ˜xi and ˜xj , which we consider as a positive pair.  
2)***A neural network base encoder f(·)*** that extracts representation vectors from augmented data examples. Our framework allows various choices of the network architecture without any constraints.  
3)We opt for simplicity and adopt the commonly used ***ResNet*** to obtain hi = f(˜xi) = ResNet(˜xi) where hi ∈ R d is the output after the average pooling layer.
4)***A small neural network projection head g(·)*** that maps representations to the space where contrastive loss is applied. We use a MLP with one hidden layer to obtain zi = g(hi) = W(2)σ(W(1)hi) where σ is a ReLU nonlinearity. As shown in section 4, we find it beneficial to define the contrastive loss on zi’s rather than hi’s.  
![Alt text](./picture/17.png)  
LOSS function:  
sim(x, y) is cosine similarity  
![Alt text](./picture/18.png)  

## *Loss Functions and Batch Size*
We find that, when the number of training epochs is small (e.g. 100 epochs), larger batch sizes have a significant advantage over the smaller ones.  
in contrastive learning, larger batch sizes provide more negative examples, facilitating convergence (i.e. taking fewer epochs and steps for a given accuracy).  


A nonlinear projection head improves the representation quality of the layer before it 'g(.)'

# Paper: Unsupervised Learning of Visual Features by Contrasting Cluster Assignments

Chen et al. [9] show that the memory bank can be entirely replaced with the elements from the same batch if the batch is large enough. In contrast to this line of works, we avoid comparing every pair of images by mapping the image features to a set of trainable prototype vectors.

We propose a multi-crop strategy where we use two standard resolution crops and sample V additional low resolution crops that cover only small parts of the image. Using low resolution images ensures only a small increase in the compute cost.



# Paper: Unsupervised Deep Feature Transfer for Low Resolution Image Classification:
Three modules:  
Feature extraction, unsupervised deep feature transfer, and Classification  
***Feature extraction***： use the resnet-101 pre-trained on ILSVRC20121 as the backbone convenet to extract the features from high and low resolution images.  
***Unsupervised deep feature transfer***:  The k-means takes a high resolution feature as input, in our case the feature fθ(xi) extracted from the convenet, and clusters them into k distinct groups based on a geometric criterion. Then, the pseudo-label of low resolution features are assigned by finding its nearest neighbor to the k centroids of high resolution features. Finally, the parameter of the feature transfer network is updated by optimizing Eq. (1) with mini-batch stochastic gradient descent.The feature transfer network is a two-layer fully connected network.  
***Classification***: The final step is to train a commonly used classifier such as Support Vector Machine (SVM) using the transferred low resolution features. In testing, given only the low resolution images, first, our algorithm extracts the features. Then feeds them to the learned feature transfer network to obtain the transferred low resolution features.Finally, we run SVM to get the classification results directly  
***evaluation***: 

# Paper: Deep Degradation Prior for Low-quality Image Classification  
***Use t-SNE find***:  
1)features from clear images are clustered together regardless which dataset they come from. It is the same for the foggy case; 2) there is a large gap between the clear features and foggy ones.  
***In this end***:  
propose a feature de-drifting module (FDM) to learn the mapping relationship between deep representations of low- and high- quality images, and leverage it as a deep degradation prior (DDP) for low-quality image classification.  
***FDM***:
the learned weights in FDM serve as the learned DDP to map the degraded features to the clear ones  
Steps:
***train phase***:  
First: use a pre-trained model to extract the low-level features of both degraded and clear images, for example, “conv2 2” in VGG16, and the first layer in AlexNet, respectively. This part of network is fixed during the training phase and is called Shallow Pretrained Layers (SPL) in this paper.  
Then: propose a novel feature de-drifting module (FDM) to accomplish the feature reconstruction. Taking the hazy image as an example, it is concatenated with the DF from SPL together and fed into FDM. Leveraging the residual learning idea, the output feature from FDM is fused with the original DF by an element-wise sum. The resulting enhanced feature (EF) is compared with its paired CF to calculate the MSE loss and the error is back-propagated to FDM to update its parameters.
***test phase***:  
Insert the trained FDM into an existing classification network, i.e., between its SPL and subsequent deep pre-trained layers (DPL), as shown in Figure 3 (b).


# 刷题笔记
## 动态规划

### 连续数组：
```
给定一个二进制数组 nums , 找到含有相同数量的 0 和 1 的最长连续子数组，并返回该子数组的长度。
示例 1:

输入: nums = [0,1]
输出: 2
说明: [0, 1] 是具有相同数量 0 和 1 的最长连续子数组。

示例 2:

输入: nums = [0,1,0]
输出: 2
说明: [0, 1] (或 [1, 0]) 是具有相同数量0和1的最长连续子数组。


解法1：O(n)
可以用前缀和记录数组中 0 和 1 的数量的差值，如果某一时刻前缀和的值已经出现过，则说明这两个位置之间 0 和 1 的数量相等，记录下它们之间的长度，最终返回长度最长的。  
具体实现步骤如下：  
将数组中的 0 替换为 -1，这样在后面的计算中，连续的 0 和 1 的数量之差就可以用前缀和的方式来表示了。  
用哈希表记录每个前缀和第一次出现的位置。  
遍历数组，计算前缀和，如果当前前缀和的值已经在哈希表中出现过，则说明这两个位置之间 0 和 1 的数量相等，记录下它们之间的长度。  
最终返回长度最长的值即可。  

解法2：O(n^2)
这个解法即用dp[i][j]表示从下标i到下标j的子数组和，可以用状态压缩压缩空间复杂度。同样将0看作为-1，当子数组和为0时找到一个符合条件的数组。<这个解法的代码就不写了>
```

```c++
class Solution {
public:
    int findMaxLength(vector<int>& nums) {
        int max_len = 0;
        unordered_map<int, int> mp;
        int counter = 0;//counter作为前缀和，每次将counter记录在哈希表中，
        mp[counter] = -1;
        for(int i = 0;i < nums.size();i++){
            if(nums[i]) counter++;
            else counter--;
            if(mp.count(counter)){//当遇到相同的前缀和时，只会记录每个前缀和第一次出现的位置，因为这时的前缀和的下标是最小的，可以得到最大的长度
                int preindex = mp[counter];
                max_len = max(max_len, i - preindex);
            }
            else mp[counter] = i;
        }
        return max_len;
    }
};

```
### 和等于 k 的最长子数组长度：
```
给定一个数组 nums 和一个目标值 k，找到和等于 k 的最长子数组长度。如果不存在任意一个符合要求的子数组，则返回 0。

示例 1:

输入: nums = [1, -1, 5, -2, 3], k = 3

输出: 4

解释: 子数组 [1, -1, 5, -2] 和等于 3，且长度最长。

示例 2:

输入: nums = [-2, -1, 2, 1], k = 1

输出: 2

解释: 子数组 [-1, 2] 和等于 1，且长度最长。

解法1：O(n)
这道题可以使用前缀和和哈希表来解决。先来看一下前缀和的概念：对于一个数组 nums，我们可以用 prefix[i] 表示 nums[0:i] 的和。那么 nums[i:j] 的和就可以表示为 prefix[j]-prefix[i-1]。接下来，我们遍历数组 nums，并计算出前缀和数组 prefix。在遍历的同时，我们用一个哈希表来记录出现过的前缀和以及它们第一次出现的下标。当我们到达下标 i 时，我们首先计算出前缀和 sum，然后查找是否存在一个之前的前缀和 sum-k，如果存在，说明从之前的下标到当前下标 i 的这段子数组的和为 k，更新最长子数组长度。注意，当 sum 等于 k 时，要特殊处理一下，因为题目要求的是最长子数组长度，所以我们需要记录所有 sum 等于 k 的下标，找到它们中最大的下标之差即可。

解法2：O(n^2)
这个解法即用dp[i][j]表示从下标i到下标j的子数组和，可以用状态压缩压缩空间复杂度。当子数组和为k时找到一个符合条件的数组。<这个解法的代码就不写了>
```
```c++
#include <unordered_map>
#include <vector>

using namespace std;

int maxSubArrayLen(vector<int>& nums, int k) {
    unordered_map<int, int> mp;
    mp[0] = -1; // 初始化，保证当 sum 等于 k 时能够正确更新 maxLen
    int prefix = 0, maxLen = 0;
    for (int i = 0; i < nums.size(); i++) {
        prefix += nums[i];
        if (mp.count(prefix - k)) { // 如果存在 sum-k，更新 maxLen
            int pre_index = mp[prefix - k];
            maxLen = max(maxLen, i - pre_index);
        }
        if (!m.count(prefix)) { // 如果不存在 sum，添加到哈希表
            mp[prefix] = i;
        }
    }
    return maxLen;
}

```

# [NOIP2000 提高组] 方格取数

## 题目描述

设有 $N \times N$ 的方格图 $(N \le 9)$，我们将其中的某些方格中填入正整数，而其他的方格中则放入数字 $0$。如下图所示（见样例）:

```plain
A
 0  0  0  0  0  0  0  0
 0  0 13  0  0  6  0  0
 0  0  0  0  7  0  0  0
 0  0  0 14  0  0  0  0
 0 21  0  0  0  4  0  0
 0  0 15  0  0  0  0  0
 0 14  0  0  0  0  0  0
 0  0  0  0  0  0  0  0
                         B
```
某人从图的左上角的 $A$ 点出发，可以向下行走，也可以向右走，直到到达右下角的 $B$ 点。在走过的路上，他可以取走方格中的数（取走后的方格中将变为数字 $0$）。  
此人从 $A$ 点到 $B$ 点共走两次，试找出 $2$ 条这样的路径，使得取得的数之和为最大。

## 输入格式

输入的第一行为一个整数 $N$（表示 $N \times N$ 的方格图），接下来的每行有三个整数，前两个表示位置，第三个数为该位置上所放的数。一行单独的 $0$ 表示输入结束。

## 输出格式

只需输出一个整数，表示 $2$ 条路径上取得的最大的和。

## 样例 #1

### 样例输入 #1

```
8
2 3 13
2 6  6
3 5  7
4 4 14
5 2 21
5 6  4
6 3 15
7 2 14
0 0  0
```

### 样例输出 #1

```
67
```

```c++
//这里用四维dp写出，即让dp[i][j][k][l]代表从起点第一次走到i, j;第二次走到k, l 这两个点时获得的最大的和
//那么dp的状态转移方程为：dp[i][j][k][l] = max({dp[i - 1][j][k - 1][l], dp[i - 1][j][k][l - 1], dp[i][j - 1][k - 1][l], dp[i][j - 1][k][l - 1]}) + mp[i][j] + mp[k][l];
//注意如果两次都经过同样一个地方的话那么要去重：if(i == k && j == l) dp[i][j][k][l] -= mp[k][l];
#include<iostream>
#include<algorithm>
#include<string.h>

using namespace std;

int mp[11][11];
int dp[11][11][11][11];
int main(void){
    memset(mp, 0, sizeof(mp)); 
    memset(dp, 0, sizeof(dp)); 
    int n;
    cin>>n;
    int a, b, c;
    while(cin>>a>>b>>c && a){
        mp[a][b] = c;
    }
    for(int i = 1;i <= n;i++){
        for(int j = 1;j <= n;j++){
            for(int k = 1;k <= n;k++){
                for(int l = 1;l <= n;l++){
                    dp[i][j][k][l] = max({dp[i - 1][j][k - 1][l], dp[i - 1][j][k][l - 1], dp[i][j - 1][k - 1][l], dp[i][j - 1][k][l - 1]}) + mp[i][j] + mp[k][l];
                    if(i == k && j == l) dp[i][j][k][l] -= mp[k][l];
                }
            }
        }
    }
    cout<<dp[n][n][n][n];
    return 0;
    
}
```


# [NOIP2000 普及组] 计算器的改良

## 题目背景

NCL 是一家专门从事计算器改良与升级的实验室，最近该实验室收到了某公司所委托的一个任务：需要在该公司某型号的计算器上加上解一元一次方程的功能。实验室将这个任务交给了一个刚进入的新手 ZL 先生。

## 题目描述

为了很好的完成这个任务，ZL 先生首先研究了一些一元一次方程的实例：

- $4+3x=8$。
- $6a-5+1=2-2a$。
- $-5+12y=0$。

ZL 先生被主管告之，在计算器上键入的一个一元一次方程中，只包含整数、小写字母及 `+`、`-`、`=` 这三个数学符号（当然，符号“`-`”既可作减号，也可作负号）。方程中并没有括号，也没有除号，方程中的字母表示未知数。

你可假设对键入的方程的正确性的判断是由另一个程序员在做，或者说可认为键入的一元一次方程均为合法的，且有唯一实数解。

## 输入格式

一个一元一次方程。

## 输出格式

解方程的结果（精确至小数点后三位）。

## 样例 #1

### 样例输入 #1

```
6a-5+1=2-2a
```

### 样例输出 #1

```
a=0.750
```

这里模拟太难了，建议先留着不看：
```c++
#include <iostream>
#include <cstdio>
using namespace std;
char c,a;//c用来读入,a是未知数名
int f=1,now=1,k,b,x;//f初始化为正，now初始为左，k、b、x意义如上
bool r;//用来判是否有数字读入
int main()
{
	while(cin>>c)//各种处理上面已经解释的很清楚了……（吧）
	{
		if(c=='-') {b+=now*f*x;x=0;f=-1;r=0;}
		if(c=='+') {b+=now*f*x;x=0;f=1;r=0;}
		if(c=='=') {b+=now*f*x;x=0;f=1;now=-1;r=0;}
		if(c>='a'&&c<='z')
		{
			if(r)
			{
				k+=now*f*x;x=0;
			}
			else k+=now*f;
			a=c;r=0;
		}
		if(c>='0'&&c<='9') {x=x*10+c-'0';r=1;}
	}
	b+=now*f*x;//加上最后一项常数（若最后一项是未知数则会加0）
    double ans=double(-b*1.0/k);
	if(ans==-0.0) ans=0;//特判，将-0.0改为0
	printf("%c=%.3lf",a,ans);//保留三位小数输出
	return 0;
}
```


## 括号生成：
数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。

示例 1：

输入：n = 3
输出：["((()))","(()())","(())()","()(())","()()()"]
示例 2：

输入：n = 1
输出：["()"]

```c++
class Solution {
public:
    string t;
    vector<string> res;
    int len;
    void DFS(int left_num, int right_num, int index){
        if(index > len * 2){
            res.push_back(t);
            return;
        }
        if(left_num < len){
            t = t + "(";
            DFS(left_num + 1, right_num, index + 1);
            t = t.substr(0, t.size() - 1);
        }
        if(right_num < left_num){
            t = t + ")";
            DFS(left_num, right_num + 1, index + 1);
            t = t.substr(0, t.size() - 1);
        }
    }
    vector<string> generateParenthesis(int n) {
        len = n;
        DFS(0, 0, 1);
        return res;
    }
};
```

交错字符串：
给定三个字符串 s1、s2、s3，请你帮忙验证 s3 是否是由 s1 和 s2 交错 组成的。

两个字符串 s 和 t 交错 的定义与过程如下，其中每个字符串都会被分割成若干非空子字符***串***：

s = s1 + s2 + ... + sn
t = t1 + t2 + ... + tm
|n - m| <= 1
交错 是 s1 + t1 + s2 + t2 + s3 + t3 + ... 或者 t1 + s1 + t2 + s2 + t3 + s3 + ...
注意：a + b 意味着字符串 a 和 b 连接。

解答：
```c++
//特别注意这里状态方程的定义：dp[i][j]指的是s1的前i个字符，s2的前j个字符是否能交错拼凑出s3的前i + j个字符
//那么此时的边界情况就可以由这个来定义了，一定注意边界情况。那么dp[0][0]一定是1，因为前0，0个字符一定能拼出s3的前0个字符
//但是对于i，0和0，j来说就不一样了，这里可以自己单独判断，或者直接用dp合起来来判断。
class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
        int len1 = s1.size(), len2 = s2.size(), len3 = s3.size();
        bool dp[len1 + 1][len2 + 1];
        memset(dp, 0, sizeof(dp));
        if(len1 + len2 != len3) return 0;
        dp[0][0] = 1;
        for(int i = 0;i <= len1;i++){
            for(int j = 0;j <= len2;j++){
                if(i > 0)
                dp[i][j] |= dp[i - 1][j] & (s1[i - 1] == s3[i + j - 1]);
                if(j > 0)
                dp[i][j] |= dp[i][j - 1] & (s2[j - 1] == s3[i + j - 1]);
            }
        }
        return dp[len1][len2];
    }
};
```

### 三角形最小路径和：
给定一个三角形 triangle ，找出自顶向下的最小路径和。

每一步只能移动到下一行中相邻的结点上。相邻的结点 在这里指的是 下标 与 上一层结点下标 相同或者等于 上一层结点下标 + 1 的两个结点。也就是说，如果正位于当前行的下标 i ，那么下一步可以移动到下一行的下标 i 或 i + 1 。

```c++
//这里就必须特别注意边界条件，所以我的建议分三种情况写，必须把每种情况分的明明白白，代码写的清清楚楚：
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        int len = triangle.size();
        int dp[len + 1][len + 1];
        memset(dp, 0, sizeof(dp));
        dp[1][1] = triangle[0][0];
        for(int i = 2;i <= len;i++){
            for(int j = 1;j <= i;j++){
                if(j - 1 >= 1 && j <= i - 1)
                    dp[i][j] = min(dp[i - 1][j - 1], dp[i - 1][j]) + triangle[i - 1][j - 1];
                else if(j - 1 < 1) 
                    dp[i][j] = dp[i - 1][j] + triangle[i - 1][j - 1];
                else if(j > i - 1) 
                    dp[i][j] = dp[i - 1][j - 1] + triangle[i - 1][j - 1];
            }
        }
        int ans = 0x3f3f3f3f;
        for(int j = 1;j <= len;j++){
            ans = min(ans, dp[len][j]);
        }
        return ans;
    }
};


```


### 分割回文串
区间DFS加动态规划：
(先用dp将i -> j的字串给直接用dp[i][j]来表示是否为回文串)然后用类似于区间分割的方法：即设1 -> i已经分割为了回文串，则只需继续分割i + 1 -> len这部分区间即可

```c++
#include<iostream> 
#include<cstring> 
#include<string.h> 
#include<vector>
using namespace std; 
int len;
int res;
vector<string> t;
string str;
bool dp[20][20];
void DFS(int i){
    if(i > len){
        res++;
        return;
    }
    for(int k = i;k <= len;k++){
        if(dp[i][k] == 1){
            t.push_back(str.substr(i - 1, k - i + 1));
            DFS(k + 1);
            t.pop_back();
        }
    }
}
int main(void){
    string s;
    cin>>s;
    len = s.size();
    str = s;
    memset(dp, 0, sizeof(dp));
    //注意这两个for循环已经是固定格式了，计算[i][i] 与 [i][i + 1]这两个边界
    for(int i = 1;i <= len;i++)
        dp[i][i] = 1;
    for(int i = 1;i <= len - 1;i++)
        if(s[i - 1] == s[i])
            dp[i][i + 1] = 1;

    
    for(int i = len - 2;i >= 1;i--){
        for(int j = i + 2;j <= len;j++){
            if(s[i - 1] == s[j - 1]) dp[i][j] |= dp[i + 1][j - 1];
            else dp[i][j] = 0;
        }
    }
    DFS(1);
    cout<<res;
    return 0;
}

```

### 乘积最大子数组：
这里最讨厌的点就是复杂的分类，但是实际情况是不需要这么复杂的讨论前i - 1个连续乘积的正负性，直接用max，和min一概而论来减轻复杂的程度：
```c++
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int len = nums.size();
        int dp[len + 1][2];
        memset(dp, 0, sizeof(dp));
        dp[1][0] = dp[1][1] = nums[0];
        for(int i = 2;i <= len;i++){
            dp[i][0] = max({dp[i - 1][0] * nums[i - 1], nums[i - 1], dp[i - 1][1] * nums[i - 1]});
            dp[i][1] = min({dp[i - 1][1] * nums[i - 1], nums[i - 1], dp[i - 1][0] * nums[i - 1]});
        }
        int ans = -0x3f3f3f3f;
        for(int i = 1;i <= len;i++){
            ans = max(ans, dp[i][0]);
        }
        return ans;
    }
};
```

```c++
class Solution {
public:
    int miceAndCheese(vector<int>& reward1, vector<int>& reward2, int k) {
        int len = reward1.size();
        int dp[len + 1][k];
        memset(dp, 0, sizeof(dp));

        for(int i = 1;i <= len;i++){
            for(int j = 1;j <= k;j++){
                dp[i][k] = max(dp[i - 1][k] + reward2[i - 1], dp[i - 1][k - 1] + reward1[i - 1]);
            }
        }



        return dp[len];

    }
};
```


# 刷题总结：
## 动态规划题：
### 子串，子数组等连续的子序列问题：
最坏用双指针来做一个O(n^3)的写法，i从左到右，j从右到i，或从i到右
一般可以找到O(n^2)的动态规划，即从i -> j之间用动态规划
但是最好的解法一般是O(n)
举例：
最大子数组和；最长0，1相同的子数组；乘积最大子数组；

### 双字符串dp问题：
编辑距离，交错字符串(特别注意dp定义与边界处理)，

## DFS问题：
### 求解的个数问题(在一般的I/O类型)和把具体解返回(力扣类型)
分割回文串；







## 图算法题：

SPFA算法
```c++
#include <iostream>
#include <queue>
#include <vector>
#include <cstring>
using namespace std;
const int INF = 0x3f3f3f3f;
const int MAXV = 110;
struct Node{
    int v, dis;
};
vector<Node> Adj[MAXV];
int n, m, d[MAXV], num[MAXV];
bool inq[MAXV];
bool SPFA(int s){
    memset(d, 0x3f, sizeof(d));
    memset(num, 0, sizeof(num));
    memset(inq, 0, sizeof(inq));

    queue<int> Q;
    Q.push(s);
    inq[s] = 1;
    num[s]++;
    d[s] = 0;

    while(!Q.empty()){

        int u = Q.front();
        Q.pop();
        inq[u] = 0;

        for(int j = 0;j < Adj[u].size();j++){
            int v = Adj[u][j].v;
            int dis = Adj[u][j].dis;
            if(d[u] + dis < d[v]){
                d[v] = d[u] + dis;
                if(!inq[v]){
                    Q.push(v);
                    inq[v] = 1;
                    num[v]++;

                    if(num[v] >= n){
                        return 0;
                    }
                }
            }
        }
    }
    return 1;
}
int main(void){
    cin>>n>>m; 
    int u, v, w;
    
    for(int i = 0;i < m;i++){
        cin>>u>>v>>w;
        Node tmp1, tmp2;
        tmp1.v = v;
        tmp1.dis = w;
        Adj[u].push_back(tmp1);
        //特别注意这里的输入，即当图为无向图时必须在邻接表和邻接矩阵中赋值两次！！
        tmp2.v = u; 
        tmp2.dis = w;
        Adj[v].push_back(tmp2);
        //cout<<u<<endl;
        //cout<<Adj[u][0].v<< ' ' <<Adj[u][0].dis<<endl;
    }
    bool flag = SPFA(1);
    cout<<d[n];
}

```

prim算法
```c++
#include <iostream>
#include <cstring>
using namespace std;
const int INF = 0x3f3f3f3f;
const int MAXV = 110;
int n, G[MAXV][MAXV];
int  d[MAXV];
bool vis[MAXV];
int prim(void){//默认从0号节点开始
    memset(vis, 0, sizeof(vis));
    memset(d, 0x3f, sizeof(d));
    d[0] = 0;
    int ans = 0;
    for(int i = 0;i < n;i++){
        int u = -1, MIN = INF;
        for(int j = 0;j < n;j++){
            if(!vis[j] && d[j] < MIN){
                u = j;
                MIN = d[j];
            }
        }
        if(u == -1) return -1;
        vis[u] = 1;
        ans += d[u];
        for(int v = 0;v < n;v++){
            if(!vis[v] && G[u][v] != INF && G[u][v] < d[v]){
                d[v] = G[u][v];
            }
        }
    }
    return ans;
}
int main(void){
    memset(G, 0, sizeof(G));

}
```
```c++
//拓扑排序代码，特别注意这里的代码所用的队列必须没有inq的，因为inq多次则
//将使得num > n，即会使得拓扑排序失败，如果
#include <iostream>
#include <cstring> 
#include <vector>
#include <queue>
using namespace std;
const int INF = 0x3f3f3f3f;
const int MAXV = 110;
struct Node{
    int v, dis;
};
vector<Node> Adj[MAXV];
int n, m, inDegree[MAXV];
vector<int> SortTable;
bool topologicalSort(){
    SortTable.clear();
    int num = 0;
    queue<int> Q;
    for(int i = 0;i < n;i++){
        if(inDegree[i] == 0){
            Q.push(i);
        }
    }
    while(!Q.empty()){
        int u = Q.front();
        SortTable.push_back(u);
        Q.pop();
        for(int i = 0;i < Adj[u].size();i++){
            int v = Adj[u][i].v;
            inDegree[v]--;
            if(inDegree[v] == 0){
                Q.push(v);
            }
        }
        Adj[u].clear();
        num++;
    }
    if(num == n) return 1;
    else return 0;
}
int main(){
    cin >> n >> m;
    memset(inDegree, 0, sizeof(inDegree)); // 将每个节点的入度初始化为0
    //特别注意这里的输入输出处理，在输入时可以直接将inDegree来进行处理
    for(int i = 0; i < m; i++){
        int u, v, dis;
        cin >> u >> v >> dis;
        Adj[u].push_back(Node{v, dis}); // 将边加入邻接表
        inDegree[v]++; // 将终点的入度加1
    }
}
```
邻接矩阵实现：
```c++
#include <iostream>
#include <cstring>
#include <queue>
using namespace std;

const int MAXN = 110;
const int INF = 0x3f3f3f3f;

int n, m;
int G[MAXN][MAXN];
int inDegree[MAXN];
vector<int> topoTable;

bool topologicalSort(){
    topoTable.clear();
    int num = 0;
    queue<int> Q;
    for(int i = 0; i < n; i++){
        if(inDegree[i] == 0){
            Q.push(i);
        }
    }
    while(!Q.empty()){
        int u = Q.front();
        Q.pop();
        topoTable.push_back(u);
        for(int v = 0; v < n; v++){
            if(G[u][v] != INF && v != u){ // 如果u到v有边
                inDegree[v]--;
                if(inDegree[v] == 0){
                    Q.push(v);
                }
            }
        }
        num++;
    }
    if(num == n) return true;
    else return false;
}

int main(){
    cin >> n >> m;
    memset(G, INF, sizeof(G)); // 初始化邻接矩阵为INF
    memset(inDegree, 0, sizeof(inDegree)); // 将每个节点的入度初始化为0
    for(int i = 0; i < m; i++){
        int u, v;
        cin >> u >> v;
        G[u][v] = 1; // 将边加入邻接矩阵
        inDegree[v]++; // 将终点的入度加1
    }
    if(topologicalSort()){ // 如果可以拓扑排序
        cout << "Yes" << endl;
    }
    else{
        cout << "No" << endl;
    }
    return 0;
}


```
有向图求最长、最短路算法，利用拓扑排序+动态规划
```

```





```c++ 素数筛查法
//Tips:当用打表时可以用vector来作为表，逐渐加上
#include<iostream>
#include<cstring>
#include<vector>
using namespace std;

const int maxn = 10010;
bool notPrime[maxn];
vector<int> PrimeTable;

int main(void){
    int n;
    cin>>n;
    memset(notPrime, 0, sizeof(notPrime));//先让所有的数都为素数
    for(int i = 2;i <= n;i++){
        if(!notPrime[i]){//如果是素数则将后面的不是素数的数全部筛除
            PrimeTable.push_back(i);
            for(int j = i + i;j <= n;j += i){
                notPrime[j] = 1;
            }
        }
    }
}

```

## 求解最长路径
```
#include<iostream>

```


## 自己写的SPFA有问题:
```c++ 
#include <vector>
#include <iostream>
#include <cstring>
#include <queue>
using namespace std;
const int INF = 0x3f3f3f3f;
const int MAXV = 110;
struct Node{
    int v, dis;
};
vector<Node> Adj[MAXV];
int n, num[MAXV], d[MAXV];
bool inq[MAXV];

bool SPFA(int s){
    memset(num, 0, sizeof(num));
    memset(inq, 0, sizeof(inq));
    memset(d, 0x3f, sizeif(d));
    queue<int> Q;
    Q.push(s);
    d[s] = 0;
    inq[s] = 1;
    num[s]++;
    while(!Q.empty()){
        int u = Q.front();
        Q.pop();
        inq[u] = 0;
        for(int j = 0;j < Adj[u].size();j++){
            int v = Adj[u][j].v;
            if(!inq[v] && d[u] + Adj[u][j].dis < d[v]){//这里有问题：并不需要判断他是否在队列，而是可以直接松弛，在需要入队的时候再判断是否已经在队列中，松弛是必须松弛的，但是不一定要入队。
                inq[v] = 1;
                Q.push(v);
                d[v] = d[u] + Adj[u][j].dis;
                num[v]++;
                if(num[v] >= n) {
                    return 0;
                }
            }
        }
    }
    return 1;
}

```

图算法求最长，最短路径心得：
最短路径：  
无向图可以用dijsktra, SPFA
有向无环图可以用拓扑排序+动态规划或者SPFA边权取反来做
注意：
当求最长路径时必须保证没有正环，求最短路径时必须保证没有负环
