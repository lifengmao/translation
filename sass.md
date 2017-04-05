SASS     原文链接：https://github.com/sass/sass

====

Sass使得CSS再一次变的有趣。Sass是CSS的一个扩展，它在CSS的基础上添加了很多东西，比如嵌套规则（nested rules）、变量（variables）、mixin、选择器的继承（selector inheritance）等。使用命令行工具或者web框架的插件，可以将Sass转换为标准格式的CSS。<br>
Sass有两种语法。最新的Sass语法（Sass3）被叫做SCSS（Sassy CSS），它是CSS语法的超集（superset）。这意味着每一个有效的CSS样式表对SCSS同样有效。SCSS使用.scss的扩展名。<br>
第二种语法被叫做缩进语法（indented syntax），或者我们可以直接叫它Sass。受Halm（一种用来描述任何XHTML网络文档的标记语言，它是干净、简单的）的简洁影响，对于那些喜欢简洁的人来说，Sass是一个更好的选择（该句意译，不准确，待改进）。Sass使用命令行的缩进来指定块，而不是用括号和分号（CSS）。尽管目前它已经不是SASS的主要语法，缩进语法仍将继续被SASS所支持。缩进语法使用的扩展名为.sass。<br>
使用方法

----

Sass可以从命令行或者被当做web框架的一部分来使用。第一步要先安装gem：<br>
```Bash
gem install sass
```
在你将一些CSS转换成Sass之后，你可以运行<br>
```bash
sass style.scss
```
来将它重新编译回CSS。如果需要获得更多的命令信息，你可以键入<br>
```bash
sass --help
```
如果要在Rails2中安装Sass，仅需要添加`config.gem "sass"`到`config/environment.rb`。在Rails3中，需要添加`gem "sass"`到你的Gemfile中。`.sass`或者`.scss`文件应该放在`public/stylesheet/sass`中，这样当需要的时候它们会自动将`public/stylesheet`中的文件编译成相应的CSS文件（Sass的模板目录是可定义的，详情见[the Sass reference](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#template_location-option)）。<br>
Sass同样可以再任何使用机架（Rack-enabled）的web框架中使用，仅需要添加<br>
```
require 'sass/plugin/rack'
use Sass::Plugin::Rack
```
到`config.ru`。然后对于所有的请求，`public/stylesheet/sass`中的Sass文件都会被编译成相应的CSS文件到`public/stylesheets`中。<br>
要程序化的使用Sass，可以参考[YARD documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#using_sass)。
格式化
----
Sass是在CSS这一基础语言上添加了力量和优雅。它允许你使用[变量](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#variables_)、[嵌套规则](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#nested_rules)、[mixin](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixins)、[内联导入](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#import)等等，这些都与CSS完全兼容。在[Compass style library](http://compass-style.org/)的帮助下，Sass有助于大型样式表保持组织良好，获得小的样式表并快速运行。<br>
Sass有两种语法，其中Scss与CSS完全兼容，另一种语法Sass是对空白敏感并且基于缩进的。要想获得更多关于这两种语法的信息，可以参考[相关文档](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#syntax)。<br>
为了运行接下来的例子并且观察产生的CSS文件，我们可以将它们放在一个叫做`test.scss`的文件中，然后运行`sass test.scss`。
###嵌套
Sass通过嵌套选择器来避免重复。这对于属性来说同样适用。
```sass
table.h1 {
	margin: 2em 0;
	td.ln {text-align: right; }
}
li {
	font: {
	family: serif;
	weight: bold;
	size: 1.2em;
	}
}
```
###变量
对所有的地方适用相同的颜色？需要对一些高度、宽度和文本尺寸进行一些数学计算？Sass支持变量、数学运算符和很多有用的函数。
```sass
$blue: #3bbfce;
$margin: 16px;

.content_navigation {
	border-color: $blue;
	color: darken($blue,10%);
}

.border {
	padding: $margin/2;
	margin: $margin/2;
	border-color: $blue;
}
```
###Mixins
相比于变量，Mixins拥有更强大的力量，它允许你重复使用整个CSS、属性或者选择的块。你甚至可以给它们参数。
```sass
@mixin table-scaffolding {
	th {
	text-align: center;
	font-weight: bold;
	}
	td,th { padding: 2px;}
}

@mixin left($dlist) {
	float: left;
	margin-left: $dlist;
}

#data {
	@include left(10px);
	@include table-scaffolding;
}
```
[Sass参考](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)中提供了完整的功能列表

可执行文件
----
Sass gem中包含了几个可执行文件，它们有助于从命令行处理Sass
###`sass`
`sass`执行文件可以将一个Sass源文件转换为CSS文件。键入`sass --help`可以获得更多的信息和选项
###`sass-convert`
该文件可以在CSS、Sass和SCSS中进行转换。当从CSS转换为Sass或者SCSS时，嵌套规则将在适当的时候被应用。键入`sass-convert --help`可以获得更多信息和选项。
###本地运行
```bash
$ cd sass
$ bundle
$ bundle exec sass ...
$ bundle exec scss ...
$ bundle exec sass-convert ...
```
作者
----
不翻译了



