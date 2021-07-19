---
title: "Piece-wise Functions on NumPy"
date: 2021-07-15
---


As part of my internship, I needed to implement the following piece-wise function (FILL).

This can be done on numpy through something like this:

```python
def upperfn(time,a,beta,t0,t1,tfall,trise):
    val = (a*(1 - beta*(time-t0)/(t1-t0)))/(1+np.exp(-(time-t0)/trise))
    return val
def lowerfn(time,a,beta,t0,t1,tfall,trise):
    val = (a*(1-beta)*np.exp(-(time-t1)/tfall))/(1+np.exp(-(time-t0)/trise))
    return val
def alercev1(time,a,beta,t0,gamma,tfall,trise):
    t1 = t0 + gamma
    val = np.piecewise(time, [time < t1, time >= t1], [lambda time: upperfn(time,a,beta,t0,t1,tfall,trise), lambda time: lowerfn(time,a,beta,t0,t1,tfall,trise)])
    return val
```
