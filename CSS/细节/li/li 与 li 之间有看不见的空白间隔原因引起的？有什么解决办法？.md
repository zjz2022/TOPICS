## li 与 li 之间有看不见的空白间隔原因引起的？有什么解决办法？

行框的排列会受到中间空白（回车空格）等的影响，因为空格也属于字符,这些空白也会被应用样式，占据空间，所以会有间隔，把字符大小设为0，就没有空格了

**解决方法：**

1. 可以将li代码全部写在一排
2. 浮动li中float：left
3. 在ul中用font-size：0（谷歌不支持）；
4. 可以将 ul{letter-spacing: -4px;};li{letter-spacing: normal;}

https://www.cnblogs.com/anpu/p/16330154.html