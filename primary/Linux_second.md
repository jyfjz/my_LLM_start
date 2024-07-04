### 搭建JavaEE环境

* 安装步骤
  * mkdir /opt/jdk
  * 通过xftp7上传到 /opt/jdk下
  * cd /opt/jdk
  * 解压 tar -zxvf jdk-8u261-linux-x64.tar.gz
  * mkdir /usr/local/java
  * mv /opt/jdk/jdk1.8.0_261 /usr/local/java
  * 配置环境变量的配置文件 vim /etc/profile
  * export JAVA_HOME=/usr/local/java/jdk1.8.0_381
  * export PATH=$JAVA_HOME/bin:$PATH
  * source /etc/profile （让文件生效）
  * 测试是否成功

### tomcat的安装

。。

### Shell编程入门

* Shell是命令行解释器，它为用户提供了一个向Linux内核发送请求以便运行程序的界面系统级程序，用户可以用Shell来启动，挂起，停止甚至是编写一些程序。

* ~~~shell
  #!/bin/bash
  脚本需要有可执行权限：chmod u+x 脚本名
  ./脚本名 运行
  或者使用sh来运行脚本
  sh 脚本名
  ~~~

* Shell的变量

  * ~~~shell
    系统变量：$HOME,$PWD,$SHELL,$USER等等
    自定义变量
    set指令可以查看全部系统变量
    ~~~

  * unset可以销毁变量

  * 将命令的返回值赋给变量

    * A=\`date\`，运行反引号里面的命令，并把结果返回给变量A
    * A=$(date) 等价于反引号
  
* 设置环境变量

  * ~~~shell
    export 变量名=变量值 	# 将Shell变量输出为环境变量/全局变量
    source 配置文件		# 让修改后的配置信息立即生效
    echo $变量名		# 查询环境变量的值
    ~~~

  * ~~~shell
    # 在 /etc/profile文件中定义TOMCAT_HOME环境变量
    export TOMCAT_HOME=/opt/tomcat
    source /etc/profile
    # 查看环境变量TOMOCAT_HOME的值
    echo $TOMCAT_HOME
    # 在另一个Shell文件程序中使用TOMOCAT_HOME
    # hello.sh文件内
    echo $TOMCAT_HOME
    ~~~

  * ~~~shell
    :<<!
    内容
    !	# 多行注释
    ~~~

* 位置参数变量

  * $n n为数字，$1~$9代表1到9个参数，10个参数以上，需要用大括号括起来，${10}

  * $* 代表命令行中所有的参数，$*把所有的参数看成一个整体

  * $@ 代表命令行中所有的参数，$@把每个参数区分对待

  * $# 代表命令行中所有参数的个数

  * 编写一个shell脚本 position.sh，在脚本中获得命令行当中的信息

    * ~~~shell
      #!/bin/bash
      echo "前三个参数：$0 $1 $2"
      echo "所有的参数：$*"
      echo "$@"
      echo "参数的个数：$#"
      ~~~

* 预定义变量

  * shell预先定义好的变量，可以在Shell脚本中使用

  * ~~~shell
    #!/bin/bash
    echo "当前执行的进程id=$$"	# $$当前运行的进程id
    /root/shcode/myshell.sh &
    echo "最后一个后台方式运行的进程id=$!"
    echo "执行的结果为$?"
    ~~~

* 运算符

  * $[运算式]	$((运算式)) 	expr m + n（运算符之间需要有空格）

    * 如果要把expr的运算结果赋给别的值，需要使用\`\`括起来
    * expr的乘法前需要加 \

  * ~~~shell
    #!/bin/bash
    result=$(((2+3)*4))
    echo "result_1=$result"
    result=$[(2+3)*4]
    echo "result_2=$result"
    tmp=`expr (2 + 3)`
    result=`expr $tmp \* 4`
    echo "result_3=$result"
    tmp=$[$1+$2]
    echo "tmp=$tmp"
    ~~~

* 条件判断

  * ~~~shell
    [ codition ](注意condition前后需要有空格)
    1）= 字符串比较
    2）两个整数的比较
    -lt 徐爱天涯
    -le 小于等于
    -eq 等于
    -gt 大于
    -ge 大于等于
    -ne 不等于
    3）按照文件权限进行判断
    -r 读权限
    -w 写权限
    -x 执行权限
    4）按照文件类型进行判断
    -f 文件存在并且是一个常规的文件
    -e 文件存在
    -d 文件存在并且是一个目录
    ~~~

  * ~~~shell
    # "ok"是否等于"ok" 字符串比较用=
    # 23是否大于等于22，使用-ge
    # 判断/root/shcode/aaa.txt目录里的文件是否存在 使用-f
    #!/bin/bash
    :<<!
    这是一个多行注释
    多行
    !
    if [ "ok" = "ok2"  ]
    then
            echo "equal"
    fi
    
    if [ 23 -ge 22 ]
    then
            echo "大于"
    else
            echo "小于等于"
    fi
    
    if [ -f /root/shcode/aaa.txt ]
    then
            echo "exist"
    else
            echo "no exist"
    fi
    
    if [  ]
    then
            echo "为真"
    else
            echo "为假"
    fi
    ~~~

* 流程控制

  * if - elif - else -fi

  * ~~~shell
    #!/bin/bash
    case $1 in
    "1")
    echo "周一"
    ;;
    "2")
    echo "周二"
    ;;
    *)
    echo "周天"
    ;;
    esac
    ~~~

* for循环

  * ~~~shell
    for 变量 in 值1 值2 ...
    do
    程序/代码
    done
    
    for (( 初始值;循环控制条件;变量变化 ))
    do
    程序代码
    done
    ~~~

* while循环

  * ~~~shell
    while [ 条件判断式子]
    do
    循环
    done
    ~~~

* read读取控制台输入

  * ~~~shell
    read(选项)(参数)
    选项:
    	-p:指定读取值时的提示符；
    	-t：指定读取值时等待的时间，如果没有在指定时间内输入，则不等待
    参数
    	变量：指定读取值的变量名
    	
    ~~~

* 函数

  * shell变成有系统函数和自定义函数

  * ~~~shell
    basename：返回完整路径最后/的部分，常用于获取文件名
    basename /home/aaa/test.txt 
    返回test.txt
    dirname：返回完整路径最后/的前面的部分，常用于返回路径部分
    dirname /home/aaa/test.txt 
    返回/home/aaa
    ~~~

  * ~~~shell
    [ function ] funcname[()]
    {
    	Action;
    	[return int;]
    }
    调用方法：funcname [值]
    案例
    function getSum(){
    	SUM=$[$n1+$n2]
    	echo "和是=$SUM"
    }
    
    read -p "输入两个数n1，n2" n1 n2
    getSum $n1 $n2
    ~~~

* Shell编程综合案例

  * ~~~shell
    /usr/sbin/mysql_db_backup.sh
    #!/bin/bash
    BACKUP=/data/backup/db
    DATETIME=$(date +%Y-%m-%d_%H:%M:%S)
    echo $DATETIME
    HOST=localhost
    DB_USER=root
    DB_PW=hspedu100
    DATABASE=hspedu
    
    [ ! -d "${BACKUP}/${DATETIME}" ] && mkdir -p "${BACKUP}/${DATETIME}"
    
    mysqldump -u${DB_USER} -p${DB_PW} --host=${HOST} -q -R --databases ${DATABASE} | gzip > ${BACKUP}/${DATETIME}/$DATETIME.sql.gz
    
    cd ${BACKUP}
    tar -zcvf $DATETIME.tar.gz ${DARETIME}
    
    rm -rf ${BACKUP}/${DATETIME}
    
    # 这句不懂
    find ${BACKUP} -atime + 10 -name ".tar.gz" -exec rm -rf {} \;
    echo "备份数据库hspedu 成功~"
    ~~~

  * crontab -e

    * 30 2 * * *  /usr/sbin/mysql_db_backup.sh

































