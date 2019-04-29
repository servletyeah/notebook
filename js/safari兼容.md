
safari在使用window.getSelection() 的时候，会出现不能得到正确结果的问题
得到类似这样的结果
```
anchorNode: null
anchorOffset: 0
baseNode: null
baseOffset: 0
extentNode: null
extentOffset: 0
focusNode: null
focusOffset: 0
isCollapsed: true
rangeCount: 0
type: "None"
```

解决的方法是加如下的样式
```
[contenteditable] {
  -webkit-user-select: auto;
  user-select: all;
}
```


[方案来源](https://stackoverflow.com/questions/35281283/safari-getselection-not-working)
