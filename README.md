# psr
psr-0和psr-4的区别

## 背景
psr-0和psr-4的区别到底是什么,在百度上找了很多介绍区别的,但都是从官网翻译过来的,并没有说出真正的区别是什么,今天花了很多时间,努力看了官方文档,把生肉变成了熟肉,终于可以一句话总结区别了

## psr-0和psr-4的区别
二者的最大区别是对下划线的定义，然而psr-4对下划线的定义没有任何特殊的意义，而psr-0在代码中对下划线的定义是把下划线转化为目录分割符。
- psr0官方文档的原文

```Each _ character in the CLASS NAME is converted to a DIRECTORY_SEPARATOR. The _ character has no special meaning in the``` 
- 实例
\namespace\package\Class_Name => /path/to/project/lib/vendor/namespace/package/Class/Name.php
\namespace\package_name\Class_Name => /path/to/project/lib/vendor/namespace/package_name/Class/Name.php

- psr4官方文档的原文

```Underscores have no special meaning in any portion of the fully qualified class name.```

- 实例

\namespace\package_name\Class_Name => /path/to/project/lib/vendor/namespace/package_name/Class_Name.php

## 共同点

- 可以说psr-4几乎完全继承了psr-0的规则(下划线除外), 例如命名空间的组成规则

## 踩到的坑

- psr-0官方文档说命名空间组成的时候是
```\<Vendor Name>\(<Namespace>\)*<Class Name>```
- psr-4官方文档说命名空间组成的时候是
```\<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>```
- 组成的第一部分是不一样的 (vendor name vs namespacebame), 不用纠结,可以理解成一样的 

## 参考地址:

- https://www.php-fig.org/psr/psr-4/#2-specification
- https://www.php-fig.org/psr/psr-0/#mandatory
