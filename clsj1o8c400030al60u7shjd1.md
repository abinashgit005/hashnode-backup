---
title: "Linux commands : awk, sed, grep, expect"
datePublished: Mon Feb 12 2024 14:43:38 GMT+0000 (Coordinated Universal Time)
cuid: clsj1o8c400030al60u7shjd1
slug: linux-commands-awk-sed-grep-expect
tags: awk, linux-for-beginners, linux-basics, awk-commands

---

## **awk:**

awk command treats the spaces as a delimiter for fields by default.

```bash
awk 'command' <file-name>
awk '{print}' awkcommand.txt
awk '{print $1}' awkcommand.txt # it will show the first field
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707737341714/091f5fa3-d1ac-4e80-87fb-75fc0e249e34.png align="center")

here we put $1 to get the first field of each line.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707737390162/c9d2ce54-cd07-4c71-8b8e-88076a4f2f94.png align="center")

remember $0 represents the field type so it will print the whole file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707737695895/e9dadc08-667f-4298-87b1-d7a04980fa46.png align="center")

we also can select multiple fields like : $1,$3

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707737825052/b4ea9f83-e4fc-43ca-b43c-15fd0433177d.png align="center")

similarly,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707747689518/e0a6b1d2-843c-41e7-9582-227c1ea7644e.png align="center")

```bash
echo "here is an example of awk command" | awk '{print $6,$7}'
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707747756790/8e29f175-bb03-410c-b4b9-1703afbdc107.png align="center")

```bash
awk '{print $NF}' awkcommand.txt
```

$NF stands for number of fields. Here it will print the last field in the file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707748013308/503cc684-ea7b-4c2d-8dc2-a3ed87bff7d7.png align="center")

sometimes the delimiter is not a space " ", At that moment we can define what delimiter we want to use  
for example our /etc/passwd file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707748247529/53a2cdce-e393-4f3a-b54b-4711467d1512.png align="center")

Here we can see the : can be delimiter. We can define the delimiter like **\-F ':'**

```bash
awk -F':' '{print $6}' /etc/passwd
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707748764046/c1d17c16-fb5e-4c89-ad50-d6dabf2cc686.png align="center")

**How can i search a word in a file using awk ?**

```bash
awk '/john/{print $0}' sample2.txt
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713009305024/c23550f5-9025-48f6-b387-8df64c4088a4.png align="center")

**How can you print the line number at the beginning of each line ?**

```bash
awk '{print NR, $0}' sample2.txt # NR denotes the number of rows
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713011624587/0cd78624-a3a5-48a3-9c77-9f0fff2ec0f2.png align="center")

How to print a specific line from the text file ?

```bash
awk 'NR==5 {print $0}' sample2.txt
awk 'NR==5 {print NR, $0}' sample2.txt #here NR prints the line number also
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713017405283/e99911a3-7a33-4449-a22f-ccc84e3fc747.png align="center")