# apprentice
## 1. DOM XSS in document.write sink using source location.search
document.write向html写内容。search属性是一个可读可写的字符串，可设置或返回当前URL的查询部分，即问号?之后的部分。
![lab](img/D1.png)
输入框的内容会放入img标签中
![try](img/S1.png)
将img标签闭合,输入"><script>alert(1)</script>，XSS触发。
## 2.DOM XSS in innerHTML sink using source location.search
不执行插入的<script>标签。故输入其他标签触发js代码
```<img src='' onerror="alert(1)">```
img标签当资源加载失败或无法使用时，触发onerror。
## 3.DOM XSS in jQuery anchor href attribute sink using location.search source
herf可以链接到URL，也可以加载脚本（比如 href="javascript:alert('1');"）
![lab](img/Q3.png)
提示点击back回到上一页
![s3](img/S3.png)
back按钮的herf会获取renturnpath中的值。如果将returnpath该改成我们要执行获取cookie的js代码```javascript:alert(doucment.cookie)```，则也会被传进herf属性，又由于href属性是可以加载脚本的，所以会执行这个js代码。从而达到获取cookie的效果。
## 4.Reflected XSS into attribute with angle brackets HTML-encoded
![T4](img/T4.png)
可以看到value中<、/这些都被编码
输入代码创建鼠标移动事件，注意把前后的双引号闭合 ```"onmouseover="alert(/xss/)```
![S4](img/S4.png)
## 5.Reflected XSS into a JavaScript string with angle brackets HTML encoded
![Q5](img/Q5.png)
在搜索栏中搜索，注意以下script代码
![T5](img/T5.png)
闭合前后的单引号，并且构造成一个完整js语句';alert(1);'，触发XSS弹窗。

# Practitioner
