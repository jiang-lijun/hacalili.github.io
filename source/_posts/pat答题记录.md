---
title: pat答题记录
date: 2021-11-28 13:32:12
tags:

---

# pat答题记录

#### 1046 划拳 (15 分)
```
-*- coding: gbk -*-
n = input()
jiahe = 0
yihe = 0
for i in range(int(n)):
    jiahan, jiahua, yihan, yihua = map(int,input().split())
    if jiahan + yihan == jiahua and jiahan + yihan != yihua:
        yihe += 1
    elif jiahan + yihan == yihua and jiahan + yihan != jiahua:
        jiahe += 1
    elif jiahan + yihan == jiahua and jiahan + yihan == yihua:
        continue
print(jiahe,yihe)
```

输出：
1 2

<!-- more -->

#### 1018 锤子剪刀布 (20 分)

```
n = int(input())
ping = 0
jiay = 0
yiy = 0
maxjiass = ""
maxjia = 0
maxyiss = ""
maxyi = 0
cntjiay = [0, 0, 0]
cntyiy = [0, 0, 0]
biao=["B", "C", "J"]
for i in range(int(n)):
    jia, yi = input().split()
    if jia == "C":
        if yi == "C":
            ping += 1
        elif yi == "B":
            yiy += 1
            cntyiy[0] += 1
        elif yi == "J":
            jiay += 1
            cntjiay[1] += 1
    if jia == "B":
        if yi == "C":
            jiay += 1
            cntjiay[0] += 1
        elif yi == "B":
            ping += 1
        elif yi == "J":
            yiy += 1
            cntyiy[2] += 1
    if jia == "J":
        if yi == "C":
            yiy += 1
            cntyiy[1] += 1
        elif yi == "B":
            jiay += 1
            cntjiay[2] += 1
        elif yi == "J":
            ping += 1
print(jiay, ping, yiy)
print(yiy, ping, jiay)
print(biao[cntjiay.index(max(cntjiay))],biao[cntyiy.index(max(cntyiy))])
```
输出:
5 3 2
2 3 5
B B

#### 1041 考试座位号 (15 分)
```
n=int(input())
list=dict()
for i in range(n):
    zkzh,sjzh,kszh=map(str,input().split())
    list[sjzh]=[zkzh,sjzh,kszh]
m=int(input())
dcx=map(str,input().split())#待查询
for i in dcx:
    res=list[i]
    print(res[0],res[2])
```
输出：
3310120150912002 2
3310120150912119 1

#### 1004 成绩排名 (20 分)
```
n=int(input())
lists=dict()
max=0
min=101
for i in range(n):
    xm,xh,cj=map(str,input().split())
    lists[cj]=[xm,xh,cj]
for i in lists:
    if int(i)>max:
        max=int(i)
        maxxx=lists[str(max)]
    if int(i)<min:
        min=int(i)
        minxx=lists[str(min)]
print(maxxx[0],maxxx[1])
print(minxx[0],minxx[1])
```
输入：
3
Joe Math990112 89
Mike CS991301 100
Mary EE990830 95
输出：
Mike CS991301
Joe Math990112

#### 1028 人口普查 (20 分)超时
```
n=int(input())
lists=[]
max="1814/09/06"
min="2014/09/06"
for i in range(n):
    xm,srs=map(str,input().split())
    if srs<"1814/09/06" or srs>"2014/09/06":
        continue
    else:
        info = []
        info.append(xm)
        for j in srs.split("/"):
            info.append(j)
        lists.append(info)
lists=sorted(lists,key=lambda x:(x[1],x[2],x[3]),reverse=False)
if len(lists)==0:
    print(0)
else:
    print(str(len(lists))+" "+lists[0][0]+" "+lists[-1][0])
```
输入：
5
John 2001/05/12
Tom 1814/09/06
Ann 2121/01/30
James 1814/09/05
Steve 1967/11/20
输出：
3 Tom John

#### 1027 打印沙漏 (20 分)
```
a,b,d=map(int,input().split())
result=[]
sum=a+b
if sum!=0:
    while sum!=0:
        data=sum%d
        result.insert(0,str(data))
        sum=sum//d
    print(''.join(result))
else:
    print(0)
```
输入：
123 456 8
输出：
1103