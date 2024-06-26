https://github.com/FrankKai/FrankKai.github.io/issues/229

https://github.com/sisterAn/blog/issues/87

arr.sort()是数组 (Array) 的一个内置方法，它用于对数组的元素进行排序。在没有提供比较函数（参数）的情况下，它会将数组元素转化为字符串，并按照字符的 Unicode 编码顺序进行排序。

使用 arr.sort()进行排序的基本格式如下：

```js
arr.sort()
```

不过，在许多情况下原生的排序并不能满足需求，你可能想进行数值排序、字母顺序排序，甚至按照自定义规则进行排序。这个时候你就可以提供一个比较函数作为参数给 sort()方法。这个比较函数应该接收两个参数，通常被称为 a 和 b，表示待比较的两个元素。

这个函数返回值的含义如下：

- 如果函数返回的值小于 0，那么 a 会排在 b 之前。
- 如果函数返回的值大于 0，那么 b 会排在 a 之前。
- 如果函数返回的值等于 0，那么 a 和 b 的位置不变。

例如，一个对于数字的简单比较函数可以写成：

```js
arr.sort(function (a, b) {
  return a - b
})
```

在这个函数里，如果 a < b，那么函数就会返回一个负数，所以 a 会排在 b 之前，从而实现了升序排序。
