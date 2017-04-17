

Vue 

官方解释：
Vue.js（读音 /vjuː/，类似于 view） 是一套构建用户界面的渐进式框架。与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。
Vue 的核心库只关注视图层，它不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与单文件组件和 Vue 生态系统支持的库结合使用时，
Vue 也完全能够为复杂的单页应用程序提供驱动。

个人理解：
Vue 是当今流行的三大 mv*框架之一 比较于其它重量级框架它有轻量而又高效的特点。而且它是渐进式框架，可以和各种组件友好配合使用来达到自底向上增量开发的效果。
生态圈繁荣，各种vue相关插件层出不穷，可谓前途一片光明。

因为效率较高，体积较小，且上手容易，学习成本低，所以选择使用vue是一个非常不错的选择。



使用vue的方式有两种

1、传统的html 头引入vue.js （不推荐使用）

2、使用vue-cli 搭建vue+webpack的现代自动化前端开发方式

1)）、Vue+webpack是官方推荐的组合 使用webpack 可以配合诸多loader来实现各种功能加快开发。
除此之外 vue的相关插件，相关ui框架 都是基于webpack来开发的，可以说没有webpack 就很难使用上vue的渐进式开发


Webpack 是当下最热门的前端资源模块化管理和打包工具，它能把各种资源，例如JS（含JSX）、coffee、样式（含less/sass）、图片等都作为模块来使用和处理。
我们可以直接使用 require(XXX) 的形式来引入各模块，即使它们可能需要经过编译（比如JSX和sass），但我们无须在上面花费太多心思，因为 webpack 有着各种健全的加载器（loader）在默默处理这些事情。


生成项目
Vue-cli是vue提供的一个脚手架工具 可以根据一个模板来生成项目。通常使用webpack模板。以下是相关技术栈：

2）使用vue-cli 意味着要使用node+npm的开发环境。
1）Node是基于v8引擎实现的 一个js开发环境，在其中可以用到很多http和io等接口。     node官网：https://nodejs.org/en/
3）npm是一个包管理工具 非常强大好用 配合node 的commonjs模块使用可以快速安装并管理所需依赖


2、.vue 单文件组件的开发方式 配合webpack的vue-loader 来使用（vue-cli已配置好）
1）.vue单文件组件是包含template、script、style、三种标签的一个文件 使用vue-loader来处理这种文件
2）vue-loader是webpack的一个loader专门处理.vue文件
3）可使用vue-component-generator 插件 来生成vue组件  同样是使用单文件组件方式，但额外生成html js css 文件引入到.vue中 方便管理。
https://github.com/NetanelBasal/vue-generate-component





3、Vue-cli  webpack中vue-loader已经帮我们配置好的功能
1）ES2015  在script标签中可以使用 es6语法，vue-loader会使用babel-loader来将其转换为es5

2）Css预处理器集成  在style标签中 通过指定lang属性 如lang=”sass” 来使用css预编译器语法，vue-loader会使用相关loader来将其编译成css 不需要额外配置。

3）postcss 后处理器，vue-cli已经配置好postcss-loader 来 使用postcss，且使用了autoprefixer插件。在style标签中编写的css 会自动添加相应的前缀，大大加快开发效率。而且还会把相关图片等url 转成base64行内图片，再也不用使用css精灵图了。

4）热重载"不是当你修改文件的时候简单重新加载页面。启用热重载后，当你修改 .vue 文件时，所有该组件的实例会被替换，并且不需要刷新页面。它甚至保持应用程序和修改组件的当前状态！当你调整模版或者修改样式时，这极大的提高了开发体验。


5）、css作用域！ Css模块 解决样式命名重复问题
https://github.com/vuejs/vue-loader/blob/master/docs/zh-cn/features/css-modules.md
https://github.com/vuejs/vue-loader/blob/master/docs/zh-cn/features/scoped-css.md

4、可选，在用vue-cli时 可以选择是否使用ESLint，ESLint是一个语法检测工具,用来避免低级错误和统一代码的风格。ESLint被设计为完全可配置的。

5、vue-cli帮我们搭建了一个简单的服务器dev-server.js文件中 使用了node的一个框架express 搭建了一个简单的服务器 




生成好项目后可选用的相关技术

1、vue-router ，当需要创建单页应用时 可使用前端路由vue-router，这是vue官方推荐使用的路由 官网：
https://router.vuejs.org/zh-cn/
2、Vuex ，当vue组件间需要通讯时（非父子组件） 可使用vuex 状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。官网：
https://vuex.vuejs.org/zh-cn/intro.html
3、 vue-resource ，与服务端交互时（ajax请求等）使用的插件，jquery 有$.ajax  vue-resource 有$.http。官网 ：https://github.com/pagekit/vue-resource
4、vue-validator ，vue编写的表单验证插件  https://github.com/kazupon/vue-validator

5、Vue 相关UI库  移动端：vux  mint UI       PC端 ：element   iview

6、使用这些库相当简单 大多数都是 在webpack的入口 main.js 使用require 引入相关模块 然后 Vue.use ，配合各自的API使用。


mock数据
1、当前后端同时开发时，难免会遇到前端静态页面写好 而后端接口还未完成的情况。 所以为了不阻塞前端的开发，前端需要自己模拟数据。
2、使用express 来搭建一个简单的服务器 来响应前端请求 并且使用mock.js返回模拟数据。 使用express的路由功能来搭建一个后端路由 并且使用mockjs的 mock方法随机生成数据。 
3、http://www.expressjs.com.cn/guide/routing.html
4、http://mockjs.com/
5、利用vue-cli 为我们创建的 dev-server中 搭建服务器

测试
1、手动测试功能

2、Karma 自动化测试。。 学习成本很大。
http://www.jianshu.com/p/a515fbbdd1b2      









 






