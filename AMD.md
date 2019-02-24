# AMD

异步加载模块定义(Asynchronous Module Definition，**AMD**)API规定了一种定义模块的机制，并且模块的依赖可以被异步加载。异步加载模块特别适合浏览器环境，因为浏览器中模块的加载会导致性能，可用性，调试以及跨域访问的问题。

AMD与科技公司[AMD](http://en.wikipedia.org/wiki/Advanced_Micro_Devices)以及该公司制造的处理器无关。

* [测试](https://github.com/amdjs/amdjs-tests)
* [讨论](https://groups.google.com/group/amd-implement)

# API规范

## define()函数 <a name="define"></a>

规范定义了一个单一的"difine"函数，可把它当做自由变量或全局变量使用。下面的代码是"define"函数示例:

```javascript
    define(id?, dependencies?, factory);
```

### id <a name="define-id"></a>

第一个参数id是一个字符串字面量。它指明了被定义的模块的id。这个参数是可选的，如果没有传入这个参数，模块的id应该默认是loader为给定的响应脚本加载的模块的id。当传入id时，模块的id必须是一个"顶级的"id或绝对的id（不予许传入相对id）。

#### 模块id格式化 <a name="define-id-notes"></a>

模块id可以用来标识被定义的模块，并且模块id也被用在依赖数组参数中。AMD中的模块id是[CommonJS模块标识符]的超集。可以从该页面引用：

* 模块标识符是被正斜杠分割的”词语“字符串。
* 词语必须是一个驼峰标识符，”.“或”..“。
* 模块标识符不可能包含像”.js“之类的文件的扩展名。
* 模块标识符可能是”相对的“或“顶级的”，如果第一个词语是“.”或“..”，那么模块标识符就是相对的。
* 顶级标识符从相对于模块名称的根路径解析。
* 相对标识符从相对于那些写了“require“并调用它的模块标识符的位置开始解析。

上面引用的CommonJS模块id属性通常用于JavaScript模块内。

相对模块ID解析示例：

* 如果`"a/b/c"`模块请求`"../d"`模块,这样的模块ID会被解析成`"a/b"`
* 如果`"a/b/c"`模块请求`"./e"`模块，那么模块ID会被解析成`"a/b/e"`

如果AMD的实现支持[Loader插件](https://github.com/amdjs/amdjs-api/blob/master/LoaderPlugins.md)，那么用"!"从插件的源id中分离出插件的模块id。因为插件源id可能是非常自由的格式，插件的源id可以使用大多数的字符。

### dependencies <a name="define-dependencies"></a>

dependencies是第二个参数，是一个模块id数组，这些模块id会被定义的模块引用。dependencies必须在模块工厂函数执行之前解析，并把解析的值作为参数传输传递给工厂函数，参数位置对应于依赖项数组中的索引。

依赖id可能是相对的id，并且会相对于被定义的模块进行解析。换句话说，相对id就是相对于模块id进行解析，而不是用于查找模块的id。

规范定义了有独特的解析方式的三个特殊依赖名。如果”require“，”exports“，或”module“的值出现在依赖列表中，该参数应解析为CommonJS模块规范定义的相应自由变量。

dependencies是可选的参数。如果省略，默认传入["require", "exports", "module"]。然而，如果工厂函数的元数（长度属性）小于3，那么加载器可以选择仅使用与函数的arity或length相对应的参数数量来调用工厂。

### factory <a name="define-factory"></a>