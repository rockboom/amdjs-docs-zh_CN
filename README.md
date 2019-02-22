这个仓库包含AMD的API规范以及一些和AMD密切相关的API。

* [AMD](https://github.com/amdjs/amdjs-api/blob/master/AMD.md)：异步模块定义（Asynchronous Module Definition），主要用来引用和定义模块化的JS代码。
* [require](https://github.com/amdjs/amdjs-api/blob/master/require.md)：require()函数的API，允许动态加载，异步加载模块，并且会把一些基于模块ID的字符串解析成文件路径。
* [Loader 插件](https://github.com/amdjs/amdjs-api/blob/master/LoaderPlugins.md)：通过允许加载那些不是传统JavaScript依赖的资源，Loader插件可以实现对AMD的扩展。
* [Common-Config](https://github.com/amdjs/amdjs-api/blob/master/CommonConfig.md)：可选的公共配置。如果一个loader支持那些在配置值中指定的的功能，则应使用这些配置结构以便更容易与其他loader互相操作。

如果你正在实现一个AMD loader，[实现amd规范的列表](https://groups.google.com/group/amd-implement)用来讨论那些不适用的较小项目，这些项目可以通过问题票根（issue tickets）追踪到。

维基百科上的一些文档不是实际的API，但是里面的信息与AMD使用的特别相似。

* [jQuery-and-AMD](https://github.com/amdjs/amdjs-api/wiki/jQuery-and-AMD)：描述了jQuery 1.7+的版本支持AMD模块注册，不过只有define.amd.jQuery 设置为true时才能使用。

文档和AMD文档相似并且是用其他库实现的。

* [AMD Forks](https://github.com/amdjs/amdjs-api/wiki/AMD-Forks)：已经内置AMD注册的库的分叉列表。

此项目的[wiki](https://github.com/amdjs/amdjs-api/wiki)还包含此仓库中信息的副本。 这些页面是出于历史原因/链接而保留的，但此回购的内容被视为权威来源。

---

<p xmlns:dct="http://purl.org/dc/terms/" xmlns:vcard="http://www.w3.org/2001/vcard-rdf/3.0#">
  <a rel="license"
     href="http://creativecommons.org/publicdomain/zero/1.0/">
    <img src="http://i.creativecommons.org/p/zero/1.0/88x31.png" style="border-style: none;" alt="CC0" />
  </a>
  <br />
  To the extent possible under law,
  <a rel="dct:publisher"
     href="https://github.com/amdjs">
    <span property="dct:title">the amdjs organization</span></a>
  has waived all copyright and related or neighboring rights to
  <span property="dct:title">AMD specifications</span>.
This work is published from:
<span property="vcard:Country" datatype="dct:ISO3166"
      content="US" about="https://github.com/amdjs">
  United States</span>.
</p>