‘r’：读

‘w’：写

‘a’：追加

‘r+’ == r+w（可读可写，文件若不存在就报错(IOError)）

‘w+’ == w+r（可读可写，文件若不存在就创建）

‘a+’ ==a+r（可追加可写，文件若不存在就创建）

/找到字符串con中的所有中文
''.join(re.compile('[^\u4e00-\u9fa5]').split(con))

--遍历某个dir文件夹下的所有文件并输出文件名和所在路径
for root,dirs,files in os.walk(dir):
     for file in files:
         print(os.path.join(root,file))



   #求交集的两种方式
    retA = [i for i in listA if i in listB]
    retB = list(set(listA).intersection(set(listB)))
    #求并集
    retC = list(set(listA).union(set(listB)))
    #求差集，在B中但不在A中
    retD = list(set(listB).difference(set(listA)))
 
