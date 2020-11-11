# GC
## GC标记—清除算法
如同字面意思一样，GC标记—清除算法由标记阶段和清除阶段构成，标记阶段是把所有`活动对象`都做上标记的阶段。清除阶段是把那些没有标记的对象，也就是非活动对象回收的阶段。通过这两个阶段，
就可以令不能利用的内存空间重新得到利用。代码如下：
```
def mark_sweep():
    mark_phase()
    sweep_phase()
```
### 标记阶段
在标记阶段，为堆里所有活动对象打上标记，首先标记通过根直接引用的对象，然后递归地标记通过指针数组能访问到的对象。
```
def mark_phase():
    for element in root:
        mark(element)
def mark(obj):
    if obj.mark == False:
        obj.mark == True
        for child in children(obj):
            mark(child)
```
标记完所有活动对象后，标记阶段就结束了，标记所花费的时间与‘活动对象总数’成正比，用一句话概括：标记阶段是‘遍历对象并标记’的处理过程。
### 清除阶段
在清除阶段，遍历整个堆，回收没有打上标记的对象。
```
def sweep_phase():
    sweeping = $heap_start
    while sweeping < $heap_end:
        if sweeping.mark == True:
            sweeping.mark = False
        else:
            sweeping.next = $free_list
            $free_list = sweeping
        sweeping += sweeping.size 
```
