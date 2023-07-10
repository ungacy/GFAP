# GFAP

## 一、界面及对应的linux命令
### GO/KEGG/pfam：
#### annotate命令1：
```
python GFAP-linux.py 
-qp/qn 用户的输入文件或内容 
-aws 用户选择的内容 
-go/kegg/pfam (这里是一个多选，根据用户选择，这里也会是-go -kegg -pfam) 
-am (fast 或者sensitive或者不设置该选项) 
-e 用户设置的值(Evalue可设可不设) 
-ap 用户设置的值(match-percentage可设可不设) 
-only_ID (可设可不设) 
-o 保存的文件夹（如果前面的是一个多选，这里会同时产生多个结果文件，所以应该是一个文件夹的路径，然后将这个文件夹中的所有结果都发送给用户，发送完成后删除文件）
```

#### annotate命令2：
```
python GFAP-linux.py 
-qp/qn 用户的输入文件或内容 
-awd 用户选择的内容 
-go/kegg/pfam (这里是一个多选，根据用户选择，这里也会是-go -kegg -pfam) 
-am (fast 或者sensitive或者不设置该选项) 
-e 用户设置的值(Evalue可设可不设) 
-ap 用户设置的值(match-percentage可设可不设) 
-only_ID (可设可不设) 
-o 保存的文件夹（如果前面的是一个多选，这里会同时产生多个结果文件，所以应该是一个文件夹的路径，然后将这个文件夹中的所有结果都发送给用户，发送完成后删除文件）
```

### miRNA-lncRNA：
```
python GFAP-linux.py 
-na 
-nt (根据用户选择分miRNA或者lncRNA) 
-qn 用户输入文件 
-o 结果文件的保存路径，完成后发送给用户（可考虑发送完成后删除，以下不赘述）。
```
1. 命令行中-na是什么意思
2. Evalue的命令在哪？此处可能缺少-e表示

### gene families：
#### show members of a single family命令
```
python GFAP-linux.py 
-sf //single family
-qp (输入文件) 
-mn/mp (这里需要检测mp处是否有文件放入，如果有文件放入则该处的参数是mp并加输入文件，如果没有，则是mn并加用户选择的内容) 
-o (结果文件的保存路径，处理方法同前)
```

#### show genes containing domains of families命令
```
python GFAP-linux.py 
-mf // domains of families
-atf/agf (筛选转录因子/非转录因子家族) 
-qp (输入文件) 
-o (结果文件的保存路径)
```

### statistics：
```
python GFAP-linux.py 
-ds //draw statistics
-ar (输入文件) 
-cut_value (有默认值，用户可设可不设,以下相同) 
-gn (有默认值，用户可设可不设) 
-drawtypes (接值) 
-colormodel (接值) 
-color (接值)
-singlecolor 
-st (接值) 
-go/-kegg/pfam 
-o (会将结果保存到：./draw/)

```
1. Draw type的值：命令行输入时为bar chart

这个功能执行完成后，会保存在结果会保存在服务器上（地址和名字是./draw/ draw_detail.svg），需要在这个界面的下方提供一个框，用于展示这个结果（如何将图片传给页面需要陶老师来解决）。网页版这里，按钮6和7做一个合并。展示结果，同时也向邮箱发送一份结果。注意，-pfam对应的那个按钮显示的不对，应该显示为pfam
### pathway：
```
python GFAP-linux.py 
-dn 
-ar (输入文件) 
-cut_value (有默认值，用户可设可不设,以下相同) 
-gn (有默认值，用户可设可不设) 
-pvalue (有默认值，用户可设可不设) 
-colormodel (接值) 
-aws (接值) 
-st (接值) 
-gca (接值) 
-go/kegg/pfam 
-o (会将结果保存到：./draw/)
```
1. -dn无UI
2. -gca是不是图片中的-go_category？如果是，最终命令行里输入的应该是哪个？请统一

### translation：
```
python GFAP-linux.py 
-t 
-qn (输入文件) 
-o (结果文件的保存路径，同前)
```

### RNA2DNA：
```
python GFAP-linux.py 
-rd 
-qn (输入文件) 
-o (结果文件的保存路径，同前)
```

### extraction：
#### extraction命令
```
python GFAP-linux.py 
-ex 
-ar (输入文件) 
-ID (ID或者ID文件) 
-exfid/exgid (选其一) 
-o (结果文件的保存路径，同上)
```
#### merge annotation results
```
python GFAP-linux.py 
-mr 
-qn (输入文件) 
-rp (需要将之前的结果放入一个空文件夹并在此输入该文件夹的位置，注意移动文件的过程中不要更改文件名字) 
-o (结果文件的保存路径，同上)
```

2个上传文件

### conversion：
```
python GFAP-linux.py 
-cf 
-gf (输入文件) 
-gid (基因ID在结果文件中的index，接收的是一个整数) 
-fid (go/pfam/kegg在结果文件中的index，接收的是一个整数) 
-pvalue (pvalue在结果文件中的index，接收的是一个整数) 
-o (结果文件的保存路径，对结果的处理同上)
```