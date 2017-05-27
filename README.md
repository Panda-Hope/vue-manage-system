# manage-system #
基于Vue.js 2.x系列 + Element UI 的后台管理系统解决方案。[线上地址](http://work.omwteam.com/)

[English document](https://github.com/lin-xin/manage-system/blob/master/README_EN.md)

## 前言 ##
之前在公司用了Vue + Element组件库做了个后台管理系统，基本很多组件可以直接引用组件库的，但是也有一些需求无法满足。像图片裁剪上传、富文本编辑器、图表等这些在后台管理系统中很常见的功能，就需要引用其他的组件才能完成。从寻找组件，到使用组件的过程中，遇到了很多问题，也积累了宝贵的经验。所以我就把开发这个后台管理系统的经验，总结成这个后台管理系统解决方案。

该方案作为一套多功能的后台框架模板，适用于绝大部分的后台管理系统（Web Management System）开发。基于vue.js,使用vue-cli脚手架快速生成项目目录，引用Element UI组件库，方便开发快速简洁好看的组件。分离颜色样式，支持手动切换主题色，而且很方便使用自定义主题色。

## 功能 ##
- [x] Element UI
- [x] 登录/注销
- [x] 表格
- [x] 表单
- [x] 图表 :bar_chart:
- [x] 富文本编辑器
- [x] markdown编辑器
- [x] 图片拖拽/裁剪上传
- [x] 支持切换主题色 :sparkles:
- [x] 列表拖拽排序


## 目录结构介绍 ##

	|-- build                            // webpack配置文件
	|-- config                           // 项目打包路径
	|-- src                              // 源码目录
    |   |-- api                          // QQ音乐Api分析文件
    |       |-- index.js                 
    |   |-- assets                       // 图片资源文件
	|   |-- components                   // 组件
	|       |-- fallback.vue             // 公用后退组件
	|       |-- header.vue           	 // 重写Mini-Ui头部组件，来实现更多效果
	|       |-- index.vue                // 首页界面
    |       |-- list.vue                 // 公用歌曲列表组件
    |       |-- lyrics.vue               // 歌词组件
    |       |-- play-fixed.vue           // 底部固定歌曲播放组件
    |       |-- playing.vue              // 歌曲播放页面
    |       |-- radio.vue                // 电台界面
    |       |-- ranklist.vue             // 歌曲排行榜界面
    |       |-- recommend.vue            // 推荐歌曲界面
    |       |-- search.vue               // 搜索界面
    |       |-- singer.vue               // 歌手界面
    |       |-- singerlist.vue           // 歌手列表界面
    |       |-- slider.vue               // 歌词滑动组件
    |       |-- special.vue              // 特殊界面用于使用Iframe包含封面等QQ音乐原生界面
    |       |-- toplist.vue              // QQ音乐巅峰榜界面
    |   |-- mixin                        // 全局mixin方法
    |       |-- index.js          
    |   |-- router                       // Vue 路由
    |       |-- index.js
    |   |-- sass                         // css文件夹，采用Sass进行预编译
    |       |-- packages                 // Mint-Ui文件夹，覆盖Mint-Ui原有样式
    |            |-- cell.scss
    |            |-- header.scss
    |            |-- index.scss
    |            |-- navbar.scss
    |            |-- search.scss
    |       |-- themes                   // APP主题CSS，未来将增加主题切换功能
    |           |-- index.scss
    |       |-- transition               // 全局公用Transition, Animation
    |            |-- index.scss
    |       |-- dimension.scss           // 阿里SUI, Rem屏幕适应变化css(暂未使用)
    |       |-- index.scss               // Sass 入口文件
    |       |-- mixins.scss              // Sass 公用全局Mixin
    |       |-- normalize.scss           // Normalize.css
    |       |-- page.scss                // 页面布局css
    |       |-- scaffold.scss            // scaffold css 设置基本全局样式
    |       |-- util.scss                // 公用全局Sass组件
    |       |-- var.scss                 // 全局Sass变量，这里使用sass-resources-loader向全局注入Sass变量
    |   |-- store                        // Vuex Store文件，APP核心所在
    |       |-- index.js       
    |   |-- util                         // 全局公用函数
    |       |-- index.js                 
	|   |-- App.vue                      // App入口文件
    |   |-- filter.js                    // 注册全局Vue filter
	|   |-- main.js                      // 程序入口文件，加载Vuex,Vue-router等插件
    |   |-- mintUi.js                    // Mint-Ui配置文件
    |   |-- test                         // 测试目录，暂未使用
	|-- .babelrc                         // ES6语法编译配置
	|-- .editorconfig                    // 代码编写规格
	|-- .eslintignore                    // Eslint 忽略的文件
    |-- .eslintrc.js                     // EsLint 配置 暂未使用 
    |-- .gitignore                       // git ingnore
    |-- .postcssrc.js                    // post css 配置文件
	|-- README.md                        // README
	|-- index.html                       // 入口html文件
	|-- package.json                     // 项目及工具的依赖配置文件


## 安装步骤 ##

	git clone https://github.com/lin-xin/manage-system.git		// 把模板下载到本地
	cd manage-system											// 进入模板目录
	npm install													// 安装项目依赖，等待安装完成之后

## 本地开发 ##

	// 开启服务器，浏览器访问 http://localhost:8080
	npm run dev

## 构建生产 ##

	// 执行构建命令，生成的dist文件夹放在服务器下即可访问
	npm run build

## 组件使用说明与演示 ##

### element-ui ###
一套基于vue.js2.0的桌面组件库。访问地址：[element](http://element.eleme.io/#/zh-CN/component/layout)

### vue-datasource ###
一个用于动态创建表格的vue.js服务端组件。访问地址：[vue-datasource](https://github.com/coderdiaz/vue-datasource)

```JavaScript
<template>
	<div>
		<datasource language="en" :table-data="information.data"
	        :columns="columns"
	        :pagination="information.pagination"
	        :actions="actions"
	        v-on:change="changePage"
	        v-on:searching="onSearch"></datasource>
	</div>
</template>

<script>
	import Datasource from 'vue-datasource';					// 导入quillEditor组件
    export default {
        data: function(){
            return {
                information: {
	                pagination: {...},						// 页码配置
	                data: [...]
	            },
	            columns: [...],								// 列名配置
	            actions: [...]								// 功能配置
            }
        },
        components: {
            Datasource										// 声明组件Datasource
        },
	    methods: {
	        changePage(values) {...},
	        onSearch(searchQuery) {...}
	    }
	}
</script>
```


### Vue-Quill-Editor ###
基于Quill、适用于Vue2的富文本编辑器。访问地址：[vue-quill-editor](https://github.com/surmon-china/vue-quill-editor)

```JavaScript
<template>
	<div>
		<quill-editor ref="myTextEditor" v-model="content" :config="editorOption"></quill-editor>
	</div>
</template>

<script>
	import { quillEditor } from 'vue-quill-editor';			// 导入quillEditor组件
    export default {
        data: function(){
            return {
                content: '',								// 编辑器的内容
                editorOption: {								// 编辑器的配置
                    // something config
                }
            }
        },
        components: {
            quillEditor										// 声明组件quillEditor
        }
	}
</script>
```

### Vue-SimpleMDE ###
Vue.js的Markdown Editor组件。访问地址：[Vue-SimpleMDE](https://github.com/F-loat/vue-simplemde)

```JavaScript
<template>
    <div>
        <markdown-editor v-model="content" :configs="configs" ref="markdownEditor"></markdown-editor>
    </div>
</template>

<script>
    import { markdownEditor } from 'vue-simplemde';			// 导入markdownEditor组件
    export default {
        data: function(){
            return {
                content:'',									// markdown编辑器内容
                configs: {									// markdown编辑器配置参数
                    status: false,							// 禁用底部状态栏
                    initialValue: 'Hello BBK',				// 设置初始值
                    renderingConfig: {
                        codeSyntaxHighlighting: true,		// 开启代码高亮
                        highlightingTheme: 'atom-one-light' // 自定义代码高亮主题
                    }
                }
            }
        },
        components: {
            markdownEditor									// 声明组件markdownEditor
        }
    }
</script>
```

### Vue-Core-Image-Upload ###
一款轻量级的vue上传插件，支持裁剪。访问地址：[Vue-Core-Image-Upload](https://github.com/Vanthink-UED/vue-core-image-upload)

```JavaScript

<template>
    <div>
		<img :src="src">									// 用于显示上传的图片
        <vue-core-image-upload :class="['pure-button','pure-button-primary','js-btn-crop']"
           :crop="true"										// 是否裁剪
           text="上传图片"
           url=""											// 上传路径
           extensions="png,gif,jpeg,jpg"					// 限制文件类型
           @:imageuploaded="imageuploaded">					// 监听图片上传完成事件
		</vue-core-image-upload>
    </div>
</template>

<script>
    import VueCoreImageUpload  from 'vue-core-image-upload';	// 导入VueCoreImageUpload组件
    export default {
        data: function(){
            return {
                src:'../img/1.jpg'							// 默认显示图片地址
            }
        },
        components: {
            VueCoreImageUpload								// 声明组件VueCoreImageUpload
        },
        methods:{
            imageuploaded(res) {							// 定义上传完成执行的方法
                console.log(res)
            }
        }
    }
</script>

```

### vue-echarts-v3 ###
基于vue2和eCharts.js3的图表组件。访问地址：[vue-echarts-v3](https://github.com/xlsdg/vue-echarts-v3)

```JavaScript
<template>
    <div>
        <IEcharts :option="bar"></IEcharts>
    </div>
</template>
	
<script>
    import IEcharts from 'vue-echarts-v3';					// 导入IEcharts组件
    export default {
        data: function(){
            return {
                bar: {
			        title: {
			          text: '柱状图'							// 图标标题文本
			        },
			        tooltip: {},	
			        xAxis: {								// 横坐标
			          data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
			        },
			        yAxis: {},								// 纵坐标
			        series: [{
			          name: '销量',
			          type: 'bar',							// 图标类型
			          data: [5, 20, 36, 10, 10, 20]
			        }]
			   	}
            }
        },
        components: {
            IEcharts								// 声明组件VueCoreImageUpload
        }
    }
</script>
```

## 其他注意事项 ##
### 一、如果我不想用到上面的某些组件呢，那我怎么在模板中删除掉不影响到其他功能呢？ ###

举个栗子，我不想用 vue-datasource 这个组件，那我需要分四步走。

第一步：删除该组件的路由，在目录 src/router/index.js 中，找到引入改组件的路由，删除下面这段代码。

```JavaScript
{
    path: '/vuetable',
    component: resolve => require(['../components/page/VueTable.vue'], resolve)     // vue-datasource组件
},
```

第二步：删除引入该组件的文件。在目录 src/components/page/ 删除 VueTable.vue 文件。

第三步：删除该页面的入口。在目录 src/components/common/Sidebar.vue 中，找到该入口，删除下面这段代码。
	
```HTML
<el-menu-item index="vuetable">Vue表格组件</el-menu-item>
```

第四步：卸载该组件。执行以下命令：
	
	npm un vue-datasource -S

完成。

### 二、如何切换主题色呢？ ###

第一步：打开 src/main.js 文件，找到引入 element 样式的地方，换成浅绿色主题。

```javascript
import 'element-ui/lib/theme-default/index.css';    // 默认主题
// import '../static/css/theme-green/index.css';       // 浅绿色主题
```

第二步：打开 src/App.vue 文件，找到 style 标签引入样式的地方，切换成浅绿色主题。

```javascript
@import "../static/css/main.css";
@import "../static/css/color-dark.css";     /*深色主题*/
/*@import "../static/css/theme-green/color-green.css";   !*浅绿色主题*!*/
```

第三步：打开 src/components/common/Sidebar.vue 文件，找到 el-menu 标签，把 theme="dark" 去掉即可。

## 项目截图 ##
### 默认皮肤 ###

![Image text](https://github.com/lin-xin/manage-system/raw/master/screenshots/wms1.png)

### 浅绿色皮肤 ###

![Image text](https://github.com/lin-xin/manage-system/raw/master/screenshots/wms2.png)
