# Regular Expression



# Bash

-n 會讓 message 不換行，判斷 $? 最近一次的結束狀態，再顯示 OK 或 Failed。
```
echo -n "Process $file now ... "
myprog $file > /dev/null
if [ $? -eq 0 ]; then
  echo "OK"
else
  echo "Failed"
fi
```
合併加總 /bin 與 /sbin 的檔案數
```
$ (ls /bin; ls /sbin) | wc -l
```
在 [ 和 ] 要留有空格，用 -f 判斷是否為檔案，用 -e 判斷是否存在。
```
$ cat myscript
#!/bin/bash
if [ -f /etc/passwd ]; then
  echo "/etc/passwd is a file"
fi
```
利用 if [ "$name" = "mystring" ]; then 來處理 [: =: unary operator expected 問題，用 -x 來除錯。

sed 可以用來編輯檔案內容。
```
$ sed -e 's//Johnny/' -e 's///' elasticsearch.yml
```
