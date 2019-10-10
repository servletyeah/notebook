# unicode  
`\uxxxx` 的方式表示unicode字符  
超过FFFF的字符，可以用大括号来表示`\u{1F680}`

# for...of 
可以支持遍历大于FFFF的字符

# JSON.stringify()
对于`\uD800` 到`\uFFFF`之间的字符，utf8规定必须配对使用，不能用一个码点。但是如果传入了单独使用的码点，就返回转义的字符串

|传统 |es6 |差异 |
|--|--|--|
|String.fromCodePoint |String.fromCodePoint() | 新版支持FFFF以上的码点|
|charCodeAt|codePointAt|可以返回四个字节表示的字符|
