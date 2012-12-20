---
layout: post
title: "Test embeded python"
date: 2012-12-18 15:26
comments: true
categories: 
 - python
 - note
---

### Test how to embedded python
* example using python tutor
* link

```    
http://www.pythontutor.com/visualize.html#code=class+Test%3A%0A++++def+__init__(self,+a,+b)%3A%0A++++++++self.name+%3D+str(a)%0A++++++++self.inner+%3D+str(b)%0A%0Av+%3D+%5BTest('1',+'a'),+Test('2',+'c')%5D%0Ab+%3D+v%5B%3A%5D%0A%0Aprint('value+in+v')%0Afor+i,+t+in+enumerate(v)%3A%0A++++print(str(i)%2B'th+item%3A',+t.name,+t.inner)%0Aprint('change+1st+value+in+v')%0Av%5B0%5D.name+%3D+'changed'%0Aprint('value+in+b')%0Afor+i,+t+in+enumerate(b)%3A%0A++++print(str(i)%2B'th+item%3A',+t.name,+t.inner)&mode=display&cumulative=false&py=3&curInstr=26)
```

<!-- more -->
<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=x+%3D+%5B1,+2,+3%5D%0Ay+%3D+%5B4,+5,+6%5D%0Az+%3D+y%0Ay+%3D+x%0Ax+%3D+z%0A%0Ax+%3D+%5B1,+2,+3%5D+%23+a+different+%5B1,+2,+3%5D+list!%0Ay+%3D+x%0Ax.append(4)%0Ay.append(5)%0Az+%3D+%5B1,+2,+3,+4,+5%5D+%23+a+different+list!%0Ax.append(6)%0Ay.append(7)%0Ay+%3D+%22hello%22%0A%0A%0Adef+foo(lst)%3A%0A++++lst.append(%22hello%22)%0A++++bar(lst)%0A%0Adef+bar(myLst)%3A%0A++++print(myLst)%0A%0Afoo(x)%0Afoo(z)&cumulative=false&py=3&curInstr=27"> </iframe>

<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=class+Test%3A%0A++++def+__init__(self,+a,+b)%3A%0A++++++++self.name+%3D+str(a)%0A++++++++self.inner+%3D+str(b)%0A%0Av+%3D+%5BTest('1',+'a'),+Test('2',+'c')%5D%0Ab+%3D+v%5B%3A%5D%0A%0Aprint('value+in+v')%0Afor+i,+t+in+enumerate(v)%3A%0A++++print(str(i)%2B'th+item%3A',+t.name,+t.inner)%0Aprint('change+1st+value+in+v')%0Av%5B0%5D.name+%3D+'changed'%0Aprint('value+in+b')%0Afor+i,+t+in+enumerate(b)%3A%0A++++print(str(i)%2B'th+item%3A',+t.name,+t.inner)&cumulative=false&py=3&curInstr=26"> </iframe>