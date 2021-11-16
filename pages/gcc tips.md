### gcc指定字符编码
	- `-finput-charset`用来指定输入文件的的字符编码。
	- `-fexec-charset`指定了系统字符串所使用的格式。
	- `-fexec-charset=GBK` ` -finput-charset=UTF-8`就是源文件是UTF-8格式，输出的exe文件是GBK格式。
	- 示例：`gcc -c test.c -o test.o -fexec-charset=GBK -finput-charset=UTF-8`
-