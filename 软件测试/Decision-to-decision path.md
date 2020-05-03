---
note:
    createdAt: 2020-04-29T12:12:39.831Z
    modifiedAt: 2020-04-29T12:54:42.377Z
    tags: []
---
# Decision-to-decision path

## Definition

<!-- TODO -->

## Principle

<!-- TODO -->

## 找法

先找一条从头到尾的路径,然后吓一条加上没用过的节点或者边(每次尽量少加)

## Example

```java
f(x,y,m)
{ W=x;
    If( m>0)
        { W++;
            K=1;
            For (i=1;i<m;i++)
             K=i*k;
           }
        Else
            { W=2*w;
                K=5;
            }
        If (y<=10)
            { X=5*y*k; }
        Else
            {X=k* 3*y+5; }
    Z=w+x Return z;
 }
```

<html>
<table>
  <tr>
    <td > <img src="Decision-to-decision%20path/2020-04-29-18-42-34.png" width=200px/> </td>
  <td >独立路径
  <br />D 1: 1,2,3,4,6,8,9,11,12
  <br />D 2: 1,2,3,4,<font color=#2486b9>5</font>,6,8,9,11,12
  <br />D 3: 1,2,<font color=#2486b9>7</font>,8,9,11,12
  <br />D 4: 1,2,7,8,9,<font color=#2486b9>10</font>,12
  <br />全部路径
  <br /><small>上半部分: 2分成2条, 右边一条, 左边到3一条分成两条, 上边共 3</small>
  <br /><small>下半部分: 8分成2条</small>
  <br /><small>共: 3x2=6条路劲</small>
  <br />D 5: 1,2,3,4,6,8,9,10,12
  <br />D 6: 1,2,3,4,5,6,8,9,10,12
  <br />
  </td>
  </tr>
</table>
</html>

测试用例

|     | x   | y   | m   | 预期w | 预期x | 预期z |
| --- | --- | --- | --- | ----- | ----- | ----- |
| D 1 |     |     |     |       |       |       |
| D 2 |     |     |     |       |       |       |
| D 3 |     |     |     |       |       |       |
| D 4 |     |     |     |       |       |       |
| D 5 |     |     |     |       |       |       |
| D 6 |     |     |     |       |       |       |




