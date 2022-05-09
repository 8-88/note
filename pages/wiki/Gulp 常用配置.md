​

#### 特点：（ 与 grunt 比较 ）

* 由于基于流（ stream ）的形式，所以无需要太多 `io` 操作。
* 异步执行。
* 并没有使用类似 `grunt` 配置文件的写法，而是代码，所以更贴近 `node style` 。
* 由于使用了 代码的写法，所以，更加灵活。

#### 与 grunt 的区别：

![diff](http://i.imgur.com/WDGusMK.png)

#### 常用命令：

* `gulp.task(name[, deps], fn)` - 执行任务。
  * `name` - 定义的名称。
  * `deps` - 依赖。定义后，所依赖的内容（一般也是 task ），先执行，执行完毕后，才进行当前 task 。
  * `fn` - 当前 task 具体执行的操作。

    > gulp 是基于 异步 处理的方式，所以要进行同步处理，需要如下三种情况：

    * 增加 `return`
    * 增加 `promise`
    * 增加 `callback`

* `gulp.watch(glob[, opts, cb])` - 监控文件，然后用于某些处理。
  * `glob` - 符合 `glob` 规范的 字符串 或者 数组。
  * `tasks` - 监控的对象。  
  * `cb` - 每次变动后，执行的 callback 。
    * `event.type` - 文件变化的类型，包括： `add` `changed` `deleted` 。
    * `event.path` - 改变的文件路径（ 包括文件名 ）。

* `gulp.src(globs[, options])` - 需要进行匹配的文件，符合 `glob` 语法规范。
  * `glob` - 符合 `glob` 规范的 字符串 或者 数组。
  * `options.base` - 比较重要的参数，如果指定了路径，如`aaa` 写入文件时将以此目录为根目录。

* `gulp.dest(path[, options])` - 输出的路径。
  * `paths` - 字符串 或者 函数（需要返回值），输出路径，也需要符合 `glob` 规范。

#### 常用包：

* `gulp-util` -  一些常用的基础包，如：输出带颜色的 print 等。
* `gulp-notify` -  提示。
* `gulp-plumber` -  当发生 error 的时候，gulp 会退出，加入后，可以防止 gulp 进程由于错误导致的意外退出，并且也能捕获到 error ，结合 `gulp-notify` 提供更友好的出错处理界面显示。
* `gulp-jshint` - javascript 语法检查器。
* `gulp-jshint` - 格式化 `gulp-jshint` 检验后的结果。（  `jshint.reporter( require('jshint-stylish'))`  ）
* `gulp-stylus` -  编译 并 处理 stylus 。
* `gulp-csslint` - css 语法检查器。
* `gulp-watch` -  监控 文件 的变化。
* `gulp-clean` - 删除文件夹。
* `gulp-htmlmin` -  html 压缩。
* `gulp-uglify` -  javascript 压缩。
* `gulp-minify-css` -  css 压缩。
* `run-sequence` - 让 gulp task 具有顺序执行的能力。
* `browser-sync` - 浏览器同步测试。

#### 其它包：

* `gulp-if` - 用于 判断条件，符合条件后，才能继续执行。
* `gulp-imagemin` - 用于图片压缩。
* `gulp-autoprefixer` - 给 css 添加浏览器前缀。
* `gulp-git` - 顾名思义，针对 git 各种操作的 gulp 封装。
* `gulp-usemin` - 替换。
* `gulp-inject` - 类似 `gulp-usemin` 。
* `gulp-version-tag` - 自动添加 版本号 。
* `gulp-bump` -  类似 `gulp-version-tag` ，用作 版本升级 时添加版本号。
* `gulp-replace` - 字符串替换。
* `gulp-rename` - 重命名，一般用于何必压缩后（ 配合 `jshint` `uglify` ）的文件。
* `gulp-concat` - 合并文件。
* `gulp-filter` - 过滤/筛选 stream 中的文件。
* `gulp-sourcemaps` - 生成 source map 文件。
* `gulp-header` - 在文件头添加 header 。
* `gulp-footer` - 类似 `gulp-header` ，只是在文件尾部添加。
* `gulp-load-plugins` - 省略 `require('gulp-xxx')` 直接使用 `$.xxx` 。
* `gulp-rev` - 添加 md5 ， 多用于 发布。
* `gulp-rev-outdated ` - 类似 `gulp-rev` ，增加了，每次发布时，可以删除老版本 的功能。
* `gulp-changed` -  只允许改变的文件通过 stream ，多用于 图片的压缩。
* `gulp-cached` - 类似 `gulp-changed` ，通过缓存的形式，未修改的文件不放到管道中，多用于增量编译。
* `gulp-remember` - 通常与 `gulp-cached` 配合。
* `gulp-newer` - 只将新文件加入到 stream 中。
* `gulp-bytediff` - 统计文件大小变化，多用于压缩文件后 size 变化的显示。
* `gulp-print` - 打印通过 stream 的全部文件名。
* `gulp-flatten` - 去掉 stream 中获取的文件路径，只保留文件名。
* `merge-stream` - 合并重复性工作，比如：`gulp.src` 和 `gulp.dest` 的参数不同，但它们都流程都相同，这时可以使用。
* `gulp-accord` - 集合了多种语言的的预处理器，包括： stylus, less, sass 等。
* `gulp-connect` - 比 `browser-sync` 轻量级的 服务器。
* `gulp-open` - 用浏览器打开某些指定的文件、URL等，一般与 `gulp-connect` 配合使用。

#### 典型的例子：

* <https://gist.github.com/Kenshin/116c5ceb5aefec407880>

#### 参考：

* <https://github.com/gulpjs/vinyl>
* <https://kejyuntw.gitbooks.io/gulp-learning-notes/content/>
* <http://www.gulpjs.com.cn/docs/recipes/bump-version-and-create-git-tag/>
* <http://colobu.com/2014/11/17/gulp-plugins-introduction/>
* <http://www.tuicool.com/articles/AzqA3uE>
* <http://www.gulpjs.com.cn/docs/recipes/incremental-builds-with-concatenate/>
* <http://pinkyjie.com/2015/08/02/commonly-used-gulp-plugins-part-1/>
* <http://pinkyjie.com/2015/08/12/commonly-used-gulp-plugins-part-2/>
