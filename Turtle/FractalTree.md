# 使用Python中的turtle库绘制分形树 #

在基本的递归绘制分形树基础上，添加了以下变化：
- 使用随机数，让分形树更接近自然形态
- 调整画笔粗细，达到子树枝比主干纤细的效果
- 添加了树叶

https://github.com/WillowLiu66/CGPractise/blob/master/Turtle/MyTurtleTree.png

代码如下：

```python

import turtle
from random import random, randint

def drawFractalTree(n,length):
    turtle.pendown()
    turtle.pensize(n / 3)
    turtle.forward(length)
    if n > 0:
        b = random() * 15 + 10 # 右分支偏转角度
        c = random() * 15 + 10 # 左分支偏转角度
        d = length * (random() * 0.25 + 0.7) # 下一个分支的长度
        turtle.right(b)#右转一定角度
        drawFractalTree(n-1,d)#画右分支
        turtle.left(b+c)#左转一定角度
        drawFractalTree(n-1,d)#画左分支
        turtle.right(c)#转回原角度

     else:
        turtle.right(90) 
        turtle.circle(3)#画树叶
        turtle.left(90)

    turtle.penup()
    turtle.backward(length)

turtle.tracer(1000, 0)  # 每1000个动作刷新一次画面
turtle.penup()
turtle.right(-90)#将海龟起始移动方向调整为从下到上
turtle.backward(300)#将海龟起点调整到画面靠下位置
drawFractalTree(12,100)#递归7层
turtle.exitonclick()      
```



