# go实现lua的编译
#### 参考链接:[450 行代码自制编程语言](https://zhuanlan.zhihu.com/p/341405385)

### chapter1
- EBNF 示例
  ```
    SourceCharacter ::=  #x0009 | #x000A | #x000D | [#x0020-#xFFFF] 
    Name            ::= [_A-Za-z][_0-9A-Za-z]*
    StringCharacter ::= SourceCharacter - '"'
    String          ::= '"' '"' Ignored | '"' StringCharacter '"' Ignored
    Variable        ::= "$" Name Ignored
    Assignment      ::= Variable Ignored "=" Ignored String Ignored
    Print           ::= "print" "(" Ignored Variable Ignored ")" Ignored
    Statement       ::= Print | Assignment
    SourceCode      ::= Statement+ 
  ```

### chapter2
- 词法分析器:将源代码解析到EBNF中的token