# Vue

B站Vue学习: BV1hDMFzoE8S

## 1. 为什么选择Vue框架

## 2. Vue是什么

Vue（发音为 Nju:/，类似 view）是一款用于构建用户界面的JavaScript 框架。它基于标准 HTML、CSS 和Javascript 构建，并提供了一套声明式的、组件化的编程模型，帮助你高效地开发用户界面。无论是简单还是复杂的界面，Vue 都可以胜任

>官方文档: https://cn.vuejs.org/

### 渐进式框架

Vue 是一个框架，也是一个生态。其功能覆盖了大部分前端开发常见的需求。但web 世界是十分多样化的，不同的开发者在Web上构建的东西可能在形式和规模上会有很大的不同。考虑到这一点，Vue 的设计非常注重灵活性和“可以被逐步集成”这个特点。根据你的需求场景，你可以用不同的方式使用Vue：

- ﻿﻿无需构建步骤，渐进式增强静态的 HTML
- ﻿﻿在任何页面中作为Web Components 嵌入
- ﻿﻿单页应用（SPA）
- ﻿﻿全栈/服务端渲染（SSR）
- Jamstack / 静态站点生成（SSG）
- 开发桌面端、移动端、WebGL，甚至是命令行终端中的界面

## 3. Vue版本

目前，在开发中，Vue有两个大版本可以选择 `vue2` 和 `vue3`，老项目一般都是 `vue2` 的，而新项目一般都选择

我们本套课程讲解版本为 `vue3`，因为 `Vue3` 涵盖了 `vue2` 的知识体系，当然 `vue3` 也增加了很多新特性

### Vue API风格

Vue 的组件可以按两种不同的风格书写：选项式 API 和组合式 API

大部分的核心概念在这两种风格之间都是通用的。熟悉了一种风格以后，你也能够很快地理解另一种风格

### 选项式 API （Options API）

使用选项式 API，我们可以用包含多个选项的对象来描述组件的逻辑，例如 data、methods 和 mounted。选项所定义的属性都会暴露在函数内部的 this 上，它会指向当前的组件实例

```html
 <script>
	export default ｛
		data {
			eturn {
      	count: 0
    	｝
  	},
		methods: {
			increment () {
				this.count++
			｝
  	},
  	mouted(){
    	console.log('The initial count is ${this.count}.')
  	}
	}
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

### 组合式 API （Composition API

通过组合式 API，我们可以使用导入的 API函数来描述组件逻辑。

```html
<script setup>
	import { ref, onMounted } from 'vue'
	const count = ref(0)
	function increment {
		count. value++
	｝
	onMounted( => {
		console.log（ The initial count is $｛count.value｝. ）
	｝）
</script>

<template>
	<button @click="increment">Count is: {{ count }}</button>
</template>
```

### 该选哪一个？

两种 API 风格都能够覆盖大部分的应用场景。它们只是同一个底层系统所提供的两套不同的接口。实际上，选项式 API 是在组合式 API的基础上实现的！关于 Vue 的基础概念和知识在它们之间都是通用的。

### 在生产项目中

- ﻿﻿当你不需要使用构建工具，或者打算主要在低复杂度的场景中使用 Vue，例如渐进增强的应用场景，推荐采用选项式 API
- ﻿﻿当你打算用 Vue 构建完整的单页应用，推荐采用组合式API + 单文件组件

## 4. Vue开发前的准备

> 熟悉命令行
>
> Node.js 15.0或更高

```bash
>node -v
v18.17.1
```

### 创建Vue项目

```bash
npm init vue@latest
```

选择语盖

这一指令将会安装并执行 `create-we`，它是 Vue 官方的项目脚手架工具。你将会看到一些诸如 Typescript 和测试支持之类的可选功能提示

```bash
# 不要存在大写
Project name: … <your-project-name>

Add Typescript? ... No / Yes

# 和React相关的
Add JSX Support? ... No / Yes

Add Vue Router for Single Page Application development? ... No / Yes

Add Pinia for state management? ... No / Yes

Add Vitest for Unit testing? ... No / Yes

Add Cypress for both Unit and End-to-End testing? ... No / Yes

Add ESLint for code quality? ... No / Yes

Add Prettier for code formatting? ... No / Yes

Scaffolding project in ./<your-project-name>…
Done.
```

如果不确定是否要开启其个功能你可以直接按下回在键选择Nol在项目被创建后通过以下步骤安装依赖并启动开发服务器

```bash
cd <your-project-name> 
npm install 
npm run dev
```

### 开发环境

推荐的IDE 配置是 `Vsual Sudlo Code` + ` Volar` 扩展

### 实时效果反馈

1.创建Vue项目的命令是什么？：

npm init vue@latest

## 5. Vue项目的目录结构

```bash
.vscode --- Vscode工具的配置文件
node_modules ーーー vue项目的运行依赖文件 npm install安装
public ーーー 资源文件夹（浏览器图标）
src --- 源码文件夹(编码文件夹)
.gitignore --- git忽略文件
index.html ーーー 入口HTML文件
package.json ーーー 信息描述文件
README.md ーーー 注释文件
vite.config.js --- vue配置文件
```

## 6. 模板语法

Vue 使用一种基于 HTML的模板语法，使我们能够声明式地将其组件实例的数据绑定到呈现的DOM上。所有的 Vue 模板都是语法层面合法的 HTML，可以被符合规范的浏览器和 HTML 解析器解析。

### 文本插值

最基本的数据绑定形式是文本插值，它使用的是“Mustache”语法（即双大括号）：

```html
<template>
	<p>{{ msg }}</p>
</template>

<script>
	export default {
		data(){
			return{
				msg："神奇的魔法"
			}
		}
	}
</script>
```

### 使用JavaScript 表达式

每个绑定仅支持单一表达式，也就是一段能够被求值的JavaScript代码。一个简单的判断方法是是否可以合法地写在 return 后面

```html
<template>
	<p>{{ number + 1 }}<p>
  <p>｛｛ ok ？'YES'：'NO'｝｝</p>
  <p>{{ message.split('').reverse().join('') 3}</p>
</template>

<script>
	export default {
		data (){
			return{
				number:10，
				ok: true,
				message： "大家好"
			}
		｝
 	}
</script>
```

### 原始HTML
双大括号将会将数据插值为纯文本，而不是 HTML。若想插入 HTML，你需要使用 vhtml 指令

```html
<template>
	<p>纯文本：｛｛ rawHtml ｝｝</p>
	<p>##: <span v-html="rawhtml"></span></p>
</template>

<script>
	export default {
		data(){
			return{
				rawHtml："<a href='https://itbaizhan.com'>百战程序员</a>"
			}
		｝
	}
</script>
```

### 实时效果反馈

1.下列那个语句可以作为模板语法中的语句：c

A {vara = 1 }}

B ff if (ok) {return message } }}

C { message split("). reverse() join (") }}

D fif (ok) else 0 }}

## 7. 属性绑定

双大括号不能在 HTML attributes 中使用。想要响应式地绑定一个 attribute，应该使用 `v-bind` 指令

```html
<template>
	<div v-bind:id="dynamicID" v-bind:class-"dynamicClass">AppID</div>
</template>

<script>
	export default {
		data(){
			return{
				dynamicId:"appid",
        dynamicClass:"appclass"
			}
		｝
	｝
</script>
```

`v-bind` 指令指示 Vue 将元素的id attribute 与组件的 aynamiold 属性保持一致。如果绑定的值是 null或者undefined，那么该 attribute 将会从渲染的元素上移除

### 简写

因为 `v-bind` 非常常用，我们提供了特定的简写语法

```html
<div :id="dynamicId" :class="dynamicclass"></div>
```

### 布尔型 Attribute

布尔型 attribute 依据true / false 值来决定 attribute 是否应该存在于该元素上，disabled 就是最常见的例子之一

```vue
<template>
	<button :disabled="isButtonDisabled">Button</button>
</template>

<script>
	export default {
		data(){
    	return{
        isButtonDisabled: true
			}
		}
  }
</script>
```

### 动态绑定多个值
如果你有像这样的一个包含多个 attribute 的Javascript 对象

```vue
<template>
	<div v-bind="objectofAttrs">百战程序员</div>
</template>

<script>
	export default {
		data(){
      return {
				objectofAttrs: {
					id: 'container',
					class: 'wrapper'
				}
      }
 		}
	}
</script>
```

## 8. 条件渲染

在 vue 中，提供了条件渲染，这类似于 Javascript 中的条件语句

- `v-if`
- `v-else`
- `v-else-if`
- `v-show`
- `v-if`

`v-if` 指令用于条件性地渲染一块内容。这块内容只会在指令的表达式返回真值时才被渲染

```vue
<template>
	<div v-if="flag">你能看见我么</div>
</template>

<script>
	export default {
		data() {
      return {
        flag:true
      }
    }
  }
</script>
```

`v-else`

你也可以使用 `v-else` 为 `v-if` 添加一个"else 区块”

```vue
<template>
	<div v-if="flag">你能看见我么</div>
	<div v-else>那你还是看看我吧</div>
</template>

<script>
	export default {
		data(){
      return {
				flag: false
      }
    ｝
	}
</script>
```

`v-else-if`

顾名思义，`v-else-if` 提供的是相应于 `v-if` 的“else if 区块”。它可以连续多次重复使用

```vue
<template>
	<div v-if="type === 'A'">A</div>
	<div v-else-if="type === 'B'">B</div>
	<div v-else-if="type === 'c'">C</div>
	<div v-else>Not A/B/C</div>
</template>

<script>
	export default {
		data () {
			return {
				type: "D"
      }
    }
  }
</script>
```

`v-show`

另一个可以用来按条件显示一个元素的指令是vshow。其用法基本一样

```vue
<template>
	<div v-show="flag">你能看见我么</div>
</template>

<script>
	export default {
		data() {
			return {
				flag: true
			}
		}
	｝
</script>
```

`v-if` VS `v-show`

`v-if` 是“真实的“按条件渲染，因为它确保了在切换时，条件区块内的事件监听器和子组件都会被销毁与重建。

`v-if` 也是惰性的：如果在初次渲染时条件值为false，则不会做任何事。条件区块只有当条件首次变为 true 时才被渲染。

相比之下，`v-show` 简单许多，元素无论初始条件如何，始终会被渲染，只有CSS `display` 属性会被切换。

总的来说，`v-if` 有更高的切换开销，而`v-show` 有更高的初始渲染开销。因此，如果需要频繁切换，则使用`v-show` 较好；如果在运行时绑定条件很少改变，则`v-if` 会更合适

## 9. 列表渲染

我们可以使用 `v-for` 指令基于一个数组来渲染一个列表。`v-for` 指令的值需要使用 `item in items` 形式的特殊语法，其中 `items` 是源数据的数组，而 `item` 是迭代项的别名

```html
<template> 
<div><p v-for="item in names">{{ item }}</p></div>
</template>

<script>
export default {
	data() {
		return {
			names：［"百战程序员"，“尚学堂"，"IT"］
		｝
	｝
}
</script>
```

### 复杂数据

大多数情况，我们渲染的数据源来源于网络请求，也就是 JSON 格式

```html
<template>
	< div v-for="item in result">
		<p>{{ item.title }}</p>
		<img :src="item.avator" alt="'">
	</div>
</template>

<script>
export default {
	data() {
		return {
			result: [{
				"id": 2261677,
				"title":"鄂尔多斯| 感受一座城市的璀璨夜景 感受一座城市，除了白日里的车水马龙，喧嚣繁华之",
        					"avator":"https://pic.qyer.com/avatar/002/25/77/30/200？V=1560226451",
      },
			{
				"id":2261566,
        "title":"成都这家洞穴暗黑风咖啡厅酷毙了！！早c晚A走起色☕️成都天气这么热🔥咖啡人必"，
				"avator":"https://pic.qyer.com/avatar/011/07/08/69/200?V=1572185180",
      },
			{
				"id": 2261662，
				"title":"【川西新龙-措卡湖】措卡湖，意为“乱石丛中的黑色海水”，神秘小众 原汁原味。深"，
				"avator":"https://pic.qyer.com/avatar/009/88/48/58/200?v=1507386782",
      },
			]
		｝
	｝
}
</script>
```

`v-for` 也支持使用可选的第二个参数表示当前项的位置索引

```html
<template>
  <div>
  	<p v-for=" (item, index) in names">{{ index }}:{{ item 33</p>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				names:["百战程序员", "尚学堂", "IT"]
      }
		｝
}
</script>
```

你也可以使用 `of` 作分隔符来替代 `in` ，这更接近Javascript 的迭代器语法

```html
<div v-for="item of items"></div>
```

`v-for` 与对象

你也可以使用 `v-for` 来遍历一个对象的所有属性

```html
<template>
	<div>
    <p v-for="(value, key, index) in userInfo">
      {{ index }}-{{ key }}-{{ index }}
    </p>
  </div>
</template>

<script>
	export default {
		data() {
			return {
				userInto: {
					name: "iwen",
					age: 20
        }
			}
  	}
	}
</script>
```

## 10. 通过key管理状态

Vue 默认按照“就地更新”的策略来更新通过 `v-for` 渲染的元素列表。当数据项的顺序改变时，Vue 不会随之移动 DOM 元素的顺序，而是就地更新每个元素，确保它们在原本指定的索引位置上渲染。

为了给 Vue 一个提示，以便它可以跟踪每个节点的标识，从而重用和重新排序现有的元素，你需要为每个元素对应的块提供一个唯一的 `key` attribute:

```html
<template>
	<div>
    <p v-for="(item, index) in names" :key="index">{{ item }}</p>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				names:["百战程序员", "尚学堂", "IT"]
      }
		}
	｝
</script>
```

>温馨提示
>
>key 在这里是一个通过 v-bind 绑定的特殊 attribute
>
>推荐在任何可行的时候为 for 提供一个 key attributekey 绑定的值期望是一个基础类型的值，例如字符串或 number 类型

### key的来源

请不要使用 index 作为 key 的值，我们要确保每一条数据的唯一索引不会发生变化

## 11. 事件处理

我们可以使用 `v-on` 指令（简写为 `@`）来监听 DOM 事件，并在事件触发时执行对应的Javascript。用法：`v-on:click="methodName"` 或者  `@click="handler"`

事件处理器的值可以是

1. 内联事件处理器：事件被触发时执行的内联JavaScript 语句（与 `onclick` 类似）
2. 方法事件处理器: 一个指向组件上定义的方法的属性名或是路径

### 内联事件处理器

内联事件处理器通常用于简单场景

```html
<template>
	<button @click="count++">Add 1</button>
	<p>Count is: {{ count }}</p>
</template>

<script>
	export default {
		data(){
    	return {
				count: 0
    	}
		}
	｝
</script>
```

### 方法事件处理器

```html
<template>
	<button @click="addCount">Add</button>
	<p>Count is: {{ count }}</p>
</template>

<script>
	export default {
		data() {
			return {
				count: 0
            }
        },
    //所有的方法/函数
		methods: {
			addCount(){
				this.count+=1
            }
        }
    }
</script>    
```

## 12. 事件参数

事件参数可以获取 `event` 对象和通过事件传递数据

### 获取 `event` 对象

```html
<template>
	<button @click="addCount">Add</button>
	<p>Count is: {{ count }}</p>
</template>

<script>
	export default{
		data() {
			return {
				count: 0
            }
        },
		methods: {
			addCount(e) {
        // Vue中的event对象就是原生js对象
				e.target.innerHTML = "Add" + this.count;
				this.count++
            }
        }
    }
</script>
```

### 传递参数

```html 
<template>
    <h3>事件传参</h3>
    <p @click="getNameHandler(item, $event)" v-for="(item,index) of names" :key="index">{{ item }}</p>
</template>

<script>
    export default {
        data(){
            return{
                names: ["iwen","ime", "frank"]
            }
        },
        methods: {
            getNameHandler (name, e) {
                console.log(name)
                console.log(e)
            }
        }
    }
</script>
```

## 13. 事件修饰符

在处理事件时调用 `event.preventDefault()` 或`event.stopPropagation()`是很常见的。尽管我们可以直接在方法内调用，但如果方法能更专注于数据逻辑而不用去处理 DOM 事件的细节会更好

为解决这一问题，Vue 为 `v-on` 提供了事件修饰符，常用有以下几个：

1. stop
2. prevent
3. once
4. ﻿enter

>  具体参考
>
> 地址: https://cn.vuejs.org/guide/essentials/event-handling.html#event-modifiers 

### 阻止默认事件

```html
<template>
	<div>
		<a @click.prevent="clickHandle" href="https://www.itbaizhan.com">战程序员</a>
	</div>
</template>

<script>
	export default {
		data(){
			return{
            }
        },
        methods:{
            clickHandle(e) {
              	// 阻止默认对象
                console.log("点击了");
            }
        }
    }
</script>
```

### 阻止事件冒泡

```html
<template>
    <div @click="clickDiv">
        <p @click.stop="clickP">测试冒泡</p>
    </div>
</template>

<script>
    export default {
        data(){
            return{}
        },
        methods: {
            clickDiv() {
                console.log("div");
            },
            clickP() {
                console.log ("p");
            }
        }
    }
</script>
```

## 14. 数组变化侦测

Vue 能够侦听响应式数组的变更方法，并在它们被调用时触发相关的更新。这些变更方法包括：

1. `pop()`
2. `shift()`
3. `unshift()`
4. `splice()`
5. `sort()`
6. `reverse()`

```html
<template>
    <h3>数组变化侦听</h3>
    <button @click="addLisktHandle">添加数据</button>
    <ul>
        <li v-for="(item, index) in names" :key="index">{{ item }}</li>
    </ul>
</template>

<script>
    export default{
        data() {
            return {
                names: ["iwen","ime", "frank"]
            }
        },
        methods:{
            addLisktHandle() {
                // 会引起UI变化
                this.names.push("sakura")
            }
        }
    }
</script>
```

### 替换一个数组

变更方法，顾名思义，就是会对调用它们的原数组进行变更。相对地，也有一些不可变（immutable）方法，例如 `flter()` 、 `concat()` 和`slice()`，这些都不会更改原数组，而总是返回一个新数组。当遇到的是非变更方法时，我们需要将旧的数组替换为新的

```html
<template>
    <h3>数组变化侦听</h3>
    <button @click="addLisktHandle">添加数据</button>
    <ul>
        <li v-for="(item, index) in names" :key="index">{{ item }}</li>
    </ul>
</template>

<script>
    export default{
        data() {
            return {
                names: ["iwen","ime", "frank"]
            }
        },
        methods:{
            addLisktHandle() {
                // 不会引起UI自动更新 
                this.names.concat(["sakura"])
            }
        }
    }
</script>
```

## 15. 计算属性

模板中的表达式虽然方便，但也只能用来做简单的操作。如果在模板中写太多逻辑，会让模板变得臃肿，难以维护。因此我们推荐使用计算属性来描述依赖响应式状态的复杂逻辑

```html
<template>
    <h3>{{ itbaizhan.name  }}</h3>
    <p>{{ itbaizhanContent }}</p>

</template>

<script>
    export default{
        data() {
            return {
                itbaizhan:{
                    name: "百战程序员",
                    content: ["前端", "Java", "Python"]
                }
            }
        },
        // 计算属性
        computed:{
            itbaizhanContent(){
                return this.itbaizhan.content.length > 0 ? 'Yes' : 'No'
            }
        }
    }
</script>
```

### 计算属性缓存 vs方法

你可能注意到我们在表达式中像这样调用一个函数也会获得和计算属性相同的结果

```html
<template>
    <h3>{{ itbaizhan.name  }}</h3>
    <p>{{ getReadBook() }}</p>

</template>

<script>
    export default{
        data() {
            return {
                itbaizhan:{
                    name: "百战程序员",
                    content: ["前端", "Java", "Python"]
                }
            }
        },
        methods:{
            getReadBook(){
                return this.itbaizhan.content.length > 0 ? 'Yes' : 'No'
            }
        }
    }
</script>
```

> 重点区别：
>
> 计算属性：计算属性值会基于其响应式依赖被缓存。一个计算属性仅会在其响应式依赖更新时才重新计算方法：方法调用总是会在重渲染发生时再次执行函数

## 16. Class绑定

数据绑定的一个常见需求场景是操纵元素的CSS `class` 列表，因为 oass 是 attribute，我们可以和其他attribute 一样使用 `v-bind` 将它们和动态的字符串绑定。但是，在处理比较复杂的绑定时，通过拼接生成字符串是麻烦且易出错的。因此，Vue 专门为 `class` 的 `v-bind` 用法提供了特殊的功能增强。除了字符串外，表达式的值也可以是对象或数组

### 绑定对象

```html
<template>
    <p :class="{ 'active':isActive, 'text-danger':hasError }">Class样式绑定</p>
</template>

<script>
    export default{
        data() {
            return {
                isActive: true,
                hasError: false
            }
        }
    }
</script>

<style>
    .active {
        
        font-size: 30px;
    }
    .text-danger {
        color: red;
    }
</style>
```

### 多个对象绑定

```html
<template>
    <p :class="classObject">class样式绑定2</p>
</template>

<script>
    export default{
        data() {
            return {
                classObject:{
                    'active':true,
                    'text-danger':true
                }
            }
        }
    }
</script>

<style>
    .active {
        
        font-size: 30px;
    }
    .text-danger {
        color: red;
    }
</style>
```

### 绑定数组

```html
<template>
    <p :class="[arrActive, arrHasError]">class样式绑定3</p>
</template>

<script>
    export default{
        data() {
            return {
                arrActive:"active",
                arrHasError:"text-danger"
            }
        }
    }
</script>

<style>
    .active {
        
        font-size: 30px;
    }
    .text-danger {
        color: red;
    }
</style>
```

如果你也想在数组中有条件地渲染某个 class，你可以使用三元表达式：

```html
<template>
	< div :class="[isActive ? 'active' : '']" > isActive</div>
</template>

<script>
	export default {
		data() {
			return {
				isActive: true
      }
		}
  }
</script>
```

### 数组和对象

```html
<template>
	<div :class="[{ 'active':isActive }, hasError]">class样式绑定</div>
</template>

<script>
	export default {
		data {
			return {
				isActive: true,
				hasError:"text-danger"
  		}
		}
	}
</script>
```

>温馨提示: 数组和对象嵌套过程中，只能是数组嵌套对象，不能反其道而行

## 17. Style绑定

数据绑定的一个常见需求场景是操纵元素的CSS style列表，因为 `style` 是 attribute，我们可以和其他 attribute 一样使用 `v-bind` 将它们和动态的字符串绑定。但是，在处理比较复杂的绑定时，通过拼接生成字符串是麻烦且易出错的。因此，Vue 专门为 `style` 的 `v-bind` 用法提供了特殊的功能增强。除了字符串外，表达式的值也可以是对象或数组

### 绑定对象

```html
<template>
    <p :style="{color:activeColor, fontSize:fontSize + 'px' }">style样式绑定1</p>

</template>

<script>
    export default{
        data() {
            return {
                activeColor: "green",
                fontSize:30
            }
        }
    }
</script>
```

多个

```html
<template>
    <p :style="styleObject">style样式绑定1</p>
</template>

<script>
    export default{
        data() {
            return {
                styleObject: {
                  color:'red',
                  fontSize:'30px'
                }
            }
        }
    }
</script>
```

### 绑定数组

我们还可以给：`style` 绑定一个包含多个样式对象的数组

```html
<template>
	<div :style=" [basestyles]">style#</div>
</template>

<script>
	export default {
		data() {
			return {
				basestyles: {
					color: "green",
					fontSize:"30px"
        }
      }
		}
  }
</script>
```

## 18. 侦听器

我们可以使用 `watch` 选项在每次响应式属性发生变化时触发一个函数

```html
<template>
    <h3>监听器</h3>
    <p>{{ message }}</p>
    <button @click="updateHandle">修改事件</button>

</template>

<script>
    export default{
        data() {
            return {
                message:"Hello"
            }
        },
        methods:{
            updateHandle() {
                this.message = "World";
            }
        },
        // 一个监听对象
        watch:{
            // 函数名要与data中的对象同名
            // newValue: 改变后的数据
            // oldValue: 改变前的数据
            message(newValue, oldValue) {
                // 数据发生变化,自动执行的函数
                console.log(newValue, oldValue)
            }
        }
    }
</script>
```

## 19. 表单输入绑定

在前端处理表单时，我们常常需要将表单输入框的内容同步给JavaScript 中相应的变量。手动连接值绑定和更改事件监听器可能会很麻烦，`v-model` 指令帮我们简化了这一步骤

```html
<template>
    <h3>表单输入绑定</h3>
    <form>
        <input type="text" v-model="message">
        <p>{{ message }}</p>
    </form>

</template>

<script>
    export default{
        data() {
            return {
                message:""
            }
        }
    }
</script>
```

### 复选框

```html
<template>
    <h3>表单输入绑定</h3>
    <form>
        <input type="checkbox" id="checkbox" v-model="checked">
        <label for="checkbox">{{ checked }}</label>
    </form>
</template>

<script>
    export default{
        data() {
            return {
                checked:false
            }
        }
    }
</script>
```

### 修饰符

`v-model` 也提供了修饰符: `.lazy` 、`.number` 、`.trim`

`.lazy`

默认情况下，`v-model` 会在每次 `input` 事件后更新数据。你可以添加 `lazy` 修饰符来改为在每次 `change` 事件后更新数据

```html
<template>
	<input type="text" v-model.lazy="message">
	<p>{{ message }}</p>
</template>
<script>
	export default {
		data() {
			return {
				message:""
			}
		}
  }
</script>
```

## 20. 模板引用

虽然 Vue 的声明性渲染模型为你抽象了大部分对DOM 的直接操作，但在某些情况下，我们仍然需要直接访问底层 DOM元素。要实现这一点，我们可以使用特殊的 `ref` attribute

挂载结束后引用都会被暴露在 `this.$refs` 之上

```html
<template>
    <h3>模板引用</h3>
    <div ref="container" class="container">{{ content }}</div>
    <input type="text" ref="username">
    <button @click="getElementHandle">获取元素</button>
</template>

<script>
/*
    内容改变: {{ 模板语法 }}
    属性改变: v-bind: 指令
    事件: v-on:click

    如果没有特殊需求不要操作DOM
*/
    export default{
        data() {
            return {
                content:"内容"
            }
        },
        methods:{
            getElementHandle() {
                // innerHTML: 原生JS属性
                console.log(this.$refs.container.innerHTML = "哈哈哈" );
                console.log(this.$refs.username.value)
            }
        }
    }
</script>
```

## 21. 组件组成

组件最大的优势就是可复用性

当使用构建步骤时，我们一般会将 Vue 组件定义在一个单独的 `.vue` 文件中，这被叫做单文件组件（简称SFC）

### 组件组成结构

```html
<template>
	<div>承载标签</div>
</template>

<script>
	export default {}
</script>

<style>
</style>
```

### 组件引用

```html
<template>
  <myComponent/>
</template>

<script>
  // 第一步, 引入组件
  import myComponent from './components/myComponent.vue';
  // 第二步, 注入组件
  export default{
    components:{
      myComponent
    }
  }
</script>
```

```html
<script setup>
  import myComponent from './components/myComponent.vue';
</script>

<template>
  <myComponent/>
</template>
```

## 22. 组件嵌套关系

![截屏2025-06-20 17.11.25](/Users/nancyxie/Library/Application Support/typora-user-images/截屏2025-06-20 17.11.25.png)

组件允许我们将 UI 划分为独立的、可重用的部分，并且可以对每个部分进行单独的思考。在实际应用中，组件常常被组织成层层嵌套的树状结构

这和我们嵌套 HTML 元素的方式类似，Vue 实现了自己的组件模型，使我们可以在每个组件内封装自定义内容与逻辑

### 创建组件以及引用关系

### Header

```html
<template>
    <h3>Header</h3>
</template>

<style>
    h3 {
        width: 100%;
        height: 100px;
        border: 5px solid #999;
        text-align: center;
        line-height: 100px;
        box-sizing: border-box;
    }
</style>
```

### Main

```html
<template>
    <div class="aside">
        <h3>Aside</h3>
        <Item />
        <Item />
        <Item />
    </div>
</template>

<script>
import Item from "./Item.vue"
    export default {
        components: {
            Item
        }
    }
</script>

<style scoped>
    .aside  {
        float: right;
        width: 30%;
        height: 600px;
        border: 5px solid #999;
        box-sizing: border-box;
        border-left: 0;
        border-top: 0;
    }
</style>
```

### Aside

```html
<template>
    <div class="aside">
        <h3>Aside</h3>
        <Item />
        <Item />
        <Item />
    </div>
</template>

<script>
import Item from "./Item.vue"
    export default {
        components: {
            Item
        }
    }
</script>

<style scoped>
    .aside  {
        float: right;
        width: 30%;
        height: 600px;
        border: 5px solid #999;
        box-sizing: border-box;
        border-left: 0;
        border-top: 0;
    }
</style>
```

### Article

```html
<template>
    <h3>Article</h3>
</template>

<style scoped>
    h3 {
        width: 80%;
        margin: 0 auto; 
        text-align: center;
        line-height: 100px; 
        box-sizing: border-box; 
        margin-top: 50px; 
        background: #999;
    }
</style>
```

### Item

```html
<template>
    <h3>Item</h3>
</template>

<style scoped>
    h3 {
    width: 80%;
    margin: 0 auto;
    text-align: center;
    line-height: 100px;
    box-sizing: border-box;
    margin-top: 10px;
    background:#999;
    }
</style>
```

## 23. 组件注册方式

一个 Vue 组件在使用前需要先被“注册”，这样Vue 才能在渲染模板时找到其对应的实现。组件注册有两种方式：全局注册和局部注册

### 全局注册

在main.js中修改

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import Header from './pages/Header.vue'

const app=createApp(App)

// 在这个中间写
app.component("Header", Header)

app.mount('#app')
```

App.vue

```html
<script setup>
// import Header from './pages/Header.vue';
import Main from './pages/Main.vue';
import Aside from './pages/Aside.vue';
</script>

<template>
  <Header/>
  <Main/>
  <Aside/>
</template>
```

### 局部注册

全局注册虽然很方便，但有以下几个问题：

1. 全局注册，但并没有被使用的组件无法在生产打包时被自动移除（也叫"tree-shaking”）。如果你全局注册了一个组件，即使它并没有被实际使用，它仍然会出现在打包后的JS 文件中

2. 全局注册在大型项目中使项目的依赖关系变得不那么明确。在父组件中使用子组件时，不太容易定位子组件的实现。和使用过多的全局变量一样，这可能会影响应用长期的可维护性

局部注册需要使用 `components` 选项

```html
<template>
  <GlobalComponent />
</template>

<script>
	import Globalcomponent from "./components/GlobalComponent.vue"
	export default {
		components: {
			GlobalComponent
		｝
	｝
</script>
```

## 24. 组件传递数据_props

组件与组件之间不是完全独立的，而是有交集的，那就是组件与组件之间是可以传递数据的传递数据的解决方案就是 `props`

Parent.vue

```html
<template>
    <h3>Parent</h3>
    <Child title="Parent数据" demo="测试"/>
</template>

<script>
import Child from './Child.vue';

export default {
    data() {
        return {

        }
    },
    components:{
        Child
    }
}
</script>
```

Child.vue

```html
<template>
    <h3>Child</h3>
    <p>{{ title }}</p>
    <p>{{ demo }}</p>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props:["title", "demo"]
}
</script>
```

### 动态数据传递

```html
<template>
    <h3>Parent</h3>
    <Child title="Parent数据" demo="测试"/>
    <Child :title="message"/>
</template>

<script>
import Child from './Child.vue';

export default {
    data() {
        return {
            message:"Parent数据!"
        }
    },
    components:{
        Child
    }
}
</script>
```

> 注意事项:
>
> props: 传递数据只能父传子

## 25. 组件传递多种数据迷型

通过 `props` 传递数据，不仅可以传递字符串类型的数据，还可以是其他类型，例如：数字、对象、数组等但实际上任何类型的值都可以作为 props 的值被传递

## 26. 组件传递Props效验

Vue 组件可以更细致地声明对传入的 props 的校验要求

ComponentA.vue

```html
<template>
    <h3>ComponentA</h3>
    <ComponentB :title="title"/>
</template>

<script>
import ComponentB from './ComponentB.vue';

export default {
    data() {
        return {
            title:"标题"
        }
    },
    components:{
        ComponentB
    }
}
</script>
```

ComponentB.vue

```html
<template>
    <h3>ComponentB</h3>
</template>

<script>
export default {
    data() {
        return {
        }
    },
    props:{
        title:{
            type:String
        }
    }
}
</script>
```

### default和require

ComponentA.vue

```html
<template>
    <h3>ComponentA</h3>
    <ComponentB :title="title" :age="age"/>
</template>

<script>
import ComponentB from './ComponentB.vue';

export default {
    data() {
        return {
            title:"标题",
            age:20,
            names:["iwen", "ime"]
        }
    },
    components:{
        ComponentB
    }
}
</script>
```

```html
<template>
    <h3>ComponentB</h3>
    <p>{{ title }}</p>
    <p>{{ age }}</p>
    <p>{{ names }}</p>
</template>

<script>
export default {
    data() {
        return {
        }
    },
    props:{
        title:{
            type:[String, Number, Object],
          	require:true
        },
        age:{
            type:Number,
            default:0
        },
        names:{
            type:Array,
            default() {
                return["空"]
            }
        }
        // 数字和字符串可以直接default,但其数组和对象必须通过工厂函数返回默认值
    }
}
</script>
```

## 27. 组件事件

在组件的模板表达式中，可以直接使用 `$emit` 方法触发自定义事件

触发自定义事件的目的是组件之间传递数据

ComponentEvent.vue

```html
<template>
    <h3>组件事件</h3>
    <ComponentChild @someEvent="getHandle"/>
    <p>{{ message }}</p>
</template>

<script>
import ComponentChild from './ComponentChild.vue';

export default {
    data() {
        return {
            message:""
        }
    },
    components: {
        ComponentChild
    },
    methods:{
        getHandle(data) {
            console.log("触发了", data);
            this.message = data;
        }
    }
    
}
</script>
```

ComponentChild.vue

```html
<template>
    <h3>ComponentChild</h3>
    <button @click="clickEventHandle">传递按钮</button>
</template>

<script>
export default {
    methods: {
        clickEventHandle() {
            // 自定义事件
            this.$emit("someEvent", "Child")
        }
    }
}
</script>
```

> 温馨提示:
>
> 父传子: props
>
> 子传父: 自定义事件`this.$emit`

## 28. 组件事件配合v-model使用

如果是用户输入，我们希望在获取数据的同时发送数据配合 `v-model` 来使用

SearchComponent.vue

```html
<template>
    <h3>SearchComponent</h3>
    搜索: <input type="text" v-model="search">
</template>

<script>
export default {
    data() {
        return {
            search:""
        }
    },
    // 侦听器
    watch:{
        search(newValue, oldValue) {
            this.$emit("searchEvent", newValue)
        }
    }
}
</script>
```

Main.vue

```html
<template>
    <h3>Main</h3>
    <p>搜索内容为: {{ search }}</p>
    <SearchComponent @searchEvent="getSearch"/>
    
</template>

<script>
import SearchComponent from './SearchComponent.vue';

export default {
    data() {
        return{
            search:""
        }
    },
    components:{
        SearchComponent
    },
    methods: {
        getSearch(data){
            this.search=data;
            console.log("发送")
        }
    }
}
</script>
```

## 29. 组件数据传递

我们之前讲解过了组件之间的数据传递，`props` 和 自定义事件 两种方式:

1. `props`：父传子

2. 自定义事件：子传父

出了上述的方案 `props` 也可以实现子传父

ComponentC.vue

```html
<template>
    <h3>ComponentC</h3>
    <ComponentD title="标题" :onEvent="dataFn"/>
    <p>父元素: {{ message }}</p>
</template>

<script>
import ComponentD from './ComponentD.vue';

export default {
    data() {
        return {
            message:""
        }
    },
    components:{
        ComponentD
    },
    methods: {
        dataFn(data) {
            this.message = data
            console.log(data);
        }
    }
}
</script>
```

ComponentD.vue

```html
<template>
    <h3>ComponentD</h3>
    <p>{{ title }}</p>
    <p>{{ onEvent('传递数据') }}</p>
</template>

<script>
export default {
    data() {
        return {
            search:""
        }
    },
    props:{
        title:String,
        onEvent:Function
    }
}
</script>
```









