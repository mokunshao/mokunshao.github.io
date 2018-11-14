---
title: export, export default, import
---

可以 export 多个表达式，其对应的 import 要给变量名加上花括号，而且变量名一致。

只能 export default 一次，第二次会报错，其对应的 import 的变量名可以随便取，而且无需加上花括号。

直接 import 文件名不会导入任何变量。通常 import 要搭配 from 使用。

export 变量名的时候要加上花括号，而 export default 不需要。