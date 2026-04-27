# cat file.txt | grep "python" | grep -v "javaScript"

**cat** file.txt 将 file.txt 的内容输出到终端

**|** 是管道符，意思是将前一个命令的输出作为后一个命令的输入

**grep** “python” 筛选出包含python的行

**-v** 表示取反匹配

grep -v 就是排除