## 虚拟Dom

1 提出

​		声明式代码的更新性能消耗=找出差异性的性能消耗+直接修改的性能消耗。因此如果能找出最小化的差异性就可以让声明式代码无限接近命令式代码。但是虚拟DOM的性能理论上不可能比原生JS操作DOM更高。

2 渲染器

```
render(vnode,container) // 将container作为挂载点，递归渲染子节点
```

3 虚拟dom过程

```
1 判断vnode类型，如果不同则先卸载再挂载。
2 patch(n1,n2,container) //不仅可以用来打补丁，也可以进行挂载
3 解决事件冒泡， 屏蔽所有绑定时间晚于事件触发时间的事件处理函数的执行
4 
```

**简单diff：**

diff 算法的目的是根据 key 复用 dom 节点，通过移动节点而不是创建新节点来减少 dom 操作。

对于每个新的 vnode，在旧的 vnode 中根据 key 查找一下，如果没查找到，那就新增 dom 节点，如果查找到了，那就可以复用。

复用的话要不要移动要判断下下标，如果下标在 lastIndex 之后，就不需要移动，因为本来就在后面，反之就需要移动。

最后，把旧的 vnode 中在新 vnode 中没有的节点从 dom 树中删除。

**双端diff：**

双端 diff 是头尾指针向中间移动的同时，对比头头、尾尾、头尾、尾头是否可以复用，如果可以的话就移动对应的 dom 节点。

如果头尾没找到可复用节点就遍历旧的 vnode 数组来查找，然后移动对应下标的节点到头部。

最后还剩下旧的 vnode 就批量删除，剩下新的 vnode 就批量新增。

**快速diff：**

预处理部分，首先会对它进行全等比较：`if (TEXT1 === TEXT2) return`，如果全等旧没有必要进入核心的diff步骤了。除了全等比较，还会对他们进行前缀于后缀的比较。一眼就能看到这两段文本的头部和尾部分别有一段相同的内容。进行增删

然后需要构造一个数组 source，它的长度等于新的一组子节点在经过预处理之后剩余未处理节点的数量，并且source中每个元素的初始值都是-1。

判断是否需要移动定义一个变量 moved 代表当前节点是否需要移动，pos 代表遍历就得子节点得过程中遇到得最大索引值。**如果在遍历过程中遇到得索引值呈现递增趋势，则说明不需要移动；否则需要移动。**

卸载多余节点：添加一个数量表示 patched，表示已经更新过的节点数量。已经更新过的节点数量应该小于等于新的一组子节点中需要更新的节点数量，如果它超过了新的一组子节点中需要更新的节点数量，则说明有多余的节点，应该将它卸载。

如何移动元素*利用最长递增子序列用来得出不需要移动的节点片段* 然后进行重新编号之前，最长递增子序列对应的是 新节点在旧节点列表中的为止。而编号之后，最长递增子序列对应的是 具体的节点

https://juejin.cn/post/7142726009249333261#heading-8