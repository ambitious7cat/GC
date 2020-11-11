# GC
## GC标记—清除算法
如同字面意思一样，GC标记—清除算法由标记阶段和清除阶段构成，标记阶段是把所有活动对象都做上标记的阶段。清除阶段是把那些没有标记的对象，也就是非活动对象回收的阶段。通过这两个阶段，
就可以令不能利用的内存空间重新得到利用。代码如下：
```
def mark_sweep():
    mark_phase()
    sweep_phase()
```