# 实验一实验报告
# 14061106 朱化磊
## Thinking
### Thinking 1.1
    ls -l
        以长格式的形式查看当前目录下所有可见文件的详细属性，包含关于文件的7个属性，文件属性
    drwxr-xr-x，文件硬链接数或目录子目录数，所有者，所属用户组,文件大小,修改时间，文件
    名。
    mv test1.c test2.c
        将test1.c重命名为test2.c。
    cp test1.c test2.c
        若有test2.c，则将test1.c覆盖到test2.c中，若没有test2.c，则新建test2.c，将
    tes1.c的容复制到tes2.c
    cd ..
        回到上一级目录

### Thinking 1.2
    grep的使用格式为grep 参数 查找内容 文件或目录名，例如：
        grep -a 将二进制文件以text文件的方式搜寻数据
        grep -i 忽略大小写的不同
        grep -r 在目录中查找
    查找项目中所有的宏可以用grep -n -r define 项目名,-r说明后面查找的是目录，-n说明要输出
    带有define的行的行数
    在某个文件中查找函数名比如 grep -n  函数名 文件名,-n代表可以输出行数
        我认为一个很强大的功能是grep可以在文件查找中使用正则表达式，比如在test.txt中查找带
    有开头是h结尾是llo中间可以有任意多个e的时候，可以用 grep -n he*llo test.txt
grep用法参考：

* https://www.cnblogs.com/ggjucheng/archive/2013/01/13/2856896.html  
* https://blog.csdn.net/dysh1985/article/details/7571273

### Thinking 1.3
    -Werror  将警告信息当做错误处理
    -Wall 输出所有的警告信息
        程序中的警告信息也应该被注意到，有时警告可能就隐含了一些致命的漏洞，因此，用-Wall可
    以得到所有的警告信息，而-Werror又把警告当作错误处理，提醒要严肃对待警告信息，解决这
    些警告信息以免后患。

### Thinking 2.1
    1、可以使用git checkout printf.c从本地的暂存区中拉回printf.c文件。
    2、此时暂存区的printf.c文件已经删除，可以先使用git reset HEAD printf.c，从本地版本
    库拉回使暂存区焕然一新，然后就可以用git checkout printf.c恢复了。
    3、git rm Tucao.txt，可以从暂存区里删除掉

### Thinking 2.2
    1、错误。从一篇博客（http://blog.csdn.net/xqs83/article/details/7382074）上看
    到，git clone 是把远程仓库整个都clone下来，因此会克隆所有的分支，前半句对，但是所有的分
    之都会被检出，也是从一篇博客（http://www.jb51.net/LINUXjishu/349615.html）看到
    的，这里面重点讲了怎么检出单独分支。
    2、正确。根据亲身测试，git log是提交日志，git status是查看当前文件状态的指令，
    git checkout和git commit都是针对于本地的暂存区或者本地版本库的操作，因此不会涉及到
    远程版本库。
    3、错误。根据1，克隆是把所有的分支克隆下来。
    4、错误。克隆不会改变当前工作区的位置，经过亲身试验，在新建的分支test里重新克隆了一遍，
    完后所处的工作区还是在test里。

## 二、难点图示
        感觉这次实验最难的部分是print.c代码的补全部分，几百行的代码确实一下子懵逼了，但通过仔细
    地查看每个函数，以及实验的要求，最后发现也是不难的。我做这部分的过程大体如下：
    
![流程图](https://raw.githubusercontent.com/HualeiZhu/BUAA_MIPS_OS_DOC/master/liucheng.png)


## 三、体会和感想
        初次接触操作系统实验，一开始确实是懵逼的，看了一晚上的指导书也没十分明白一个.c文件到
    底是怎么执行的，总共花的时间大约是一个晚上加一整天吧，之所以又得花上一整天是因为我把一条汇
    编指令搞错了，lui误记成li，导致设置栈指针一直不成功，但我没有反编译所以一直找不到错误，最
    后是我的一个同学告诉我反编译这个做法，才查出错来。总体感觉仅仅完成要求的话不是很难，但要看
    懂所有的代码就不是一件容易的事了。
        总体来说，每一个exercise几乎都是误打误撞上的，找交叉编译器的位置是通过前面安装步骤
    的说明找到的，没有一通乱找，这点感觉还行，确定内核位置和栈的位置是根据内存布局图做的，有
    个七八成把握，但其余的都是在很不确定的情况下做对的。感觉对OS还远远没有入门，好多东西都还
    不是十分清楚，实验一如果没有指导书肯定要花不少更多的时间，以后还需要在OS上多花些功夫去理
    解，去实践。
