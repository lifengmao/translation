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



