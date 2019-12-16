# 前端进阶之路

![](https://yck-1254263422.cos.ap-shanghai.myqcloud.com/20191210220530.png)

正在写作的内容：

- TS 相关

这又是一个笔者花时间打磨的一个项目。在自己的群里经常能看到有人提问前端如何进阶？其实个人认为前端进阶的点在于两点：

- 把事情做好
- 加快大家做事情的效率

第一点需要你对于使用的技术有较深的理解，并且也有不错的知识广度。另外在编码的过程中能较好的对代码进行设计，让后人编写及维护代码起来不至于骂街。

第二点就是建立起团队的基础设施，解放大家的劳动力，减少重复工作，把更多的时间投入到编码。

那么到底学习哪些内容可以提升以上说的点呢？或者说你知道有哪些点可以提升，但是觉得它们很神秘、学习起来很困难，不知道哪里去寻找优质资料学习。

笔者想尝试解决这些问题，于是就把自己的接触到的且符合以上两点的一些拙见写出来了，希望能帮助到大家。另外此项目会由三部分组成：

- 我写的内容
- 我觉得不错的内容
- 练手 Demo

所以总的来说会是原创文章一部分，list 文章一部分，另外再加上一部分相应的练手 Demo。

需要注意一点的是：图中的大部分内容都不是光靠看文章就能学会东西的，需要自己不断地结合资料去实践。笔者更多的是告诉你这块东西核心该怎么做以及一些不错的资料，更多的内容还是需要大家结合搜索引擎以及实践去完成的。

同时你也可以关注我的公众号「[前端真好玩](https://yck-1254263422.cos.ap-shanghai.myqcloud.com/20190907232328.jpg)」，每个工作日推送优质文章。

那么废话就不多说了，上图是整个项目的学习路径大纲，每个路径还会有更详细的学习路径图。觉得有帮助的可以捧个场，有错误的也欢迎你提 issus，另外也欢迎大家的 PR。

## 大纲

- 基础建设
  - [基于 Jest 的单元测试](#基于-jest-的单元测试)
- 从零开始造轮子
  - [Webpack](#webpack)
  - [深拷贝](#深拷贝)

## 基础建设

### 基于 Jest 的单元测试

![](https://yck-1254263422.cos.ap-shanghai.myqcloud.com/20190918233147.png)

在这部分的内容中，你将学习到以下几点：

- 单元测试的作用
- 最应该对哪些模块进行单元测试
- React 和 Vue 这两大框架的单元测试学习路径
- 如何在 React 和 Vue 这两大框架中进行单元测试以及 Demo 实战

单元测试是用来测试程序中一小块功能的，比如说一个函数、一个类。它能很显著地提高项目的代码质量，降低出现 Bug 的频率，并且也利于维护代码。

但是实际情况是绝大部分开发者是不愿意做这件事情的。因为平时开发都忙不过来，哪还有时间去做这些事情。

我个人其实认为业务代码的测试应该是不强求的，毕竟需求经常在变化。如果对业务代码进行高覆盖率的测试，那么一旦需求变动就需要同步修改测试用例。这样编码的压力是双份的，很可能达不到快节奏上线的目的。

但是对于依赖的基础组件库以及公共函数是一定需要编写单元测试的。因为这些内容会被多个模块使用到，并且也不会频繁变更这些基础的功能，编写单元测试的收益相对来说高得多。就比如各种知名的开源项目的测试覆盖率往往是高于 90% 的，测试覆盖率低或者压根不写测试的开源项目一般很少直接用于项目中。

那么我们如何学习这方面的内容呢？首先无论你使用什么技术栈，都需要先选择一个测试框架。Jest 是其中一个相对来说优秀的框架，开箱即用，内部集成了断言库、Mock、快照功能等等。当然你也可以同样选择别的框架，核心内容都是一样的，无非 API 有所改变罢了。

[更多内容请看这里](./Infrastructure/test/index.md)

## 从零开始造轮子

### Webpack

![](https://yck-1254263422.cos.ap-shanghai.myqcloud.com/20191210221354.png)

在这部分的内容中，笔者将会带大家来实现一个几十行的迷你打包工具，该工具可以实现以下两个功能

- 将 ES6 转换为 ES5
- 支持在 JS 文件中 `import` CSS 文件

通过这个工具的实现，大家可以理解到打包工具的**原理**到底是什么。

[更多内容请看这里](./wheels/webpack/index.md)

### 深拷贝

JS 中有个重要的类型叫做引用类型。这种类型在使用的过程中，因为传递的值是引用，所以很容易发生一些副作用，比如：

```js
let a = { age: 1 }
let b = a
b.age = 2
```

上述代码的写法会造成 `a` 和 `b` 的属性都被修改了。大家在日常开发中肯定不想出现这种情况，所以都会用上一些手段去断开它们的引用连接。对于上述的数据结构来说，浅拷贝就能解决我们的问题。

```js
let b = { ...a }
b.age = 2
```

但是浅拷贝只能断开一层的引用，如果数据结构是多层对象的话，浅拷贝就不能解决问题了，这时候我们需要用到深拷贝。

深拷贝的做法一般分两种：

- `JSON.parse(JSON.stringify(a))`
- 递归浅拷贝

第一种做法存在一些局限，很多情况下并不能使用，因此这里就不提了；第二种做法一般是工具库中的深拷贝函数实现方式，比如 loadash 中的 `cloneDeep`。虽然这种做法能解决第一种做法的局限，但是对于庞大的数据来说性能并不好，因为需要把整个对象都遍历一遍。

那么是否可以有一种实现的做法，只有当属性修改以后才对这部分数据做深拷贝，又能解决 `JSON.parse(JSON.stringify(a))` 的局限呢。这种做法当然是存在的，唯一的点是我们如何知道用户修改了什么属性？

答案是 `Proxy`，通过拦截 `set` 和 `get` 就能达到我们想要的，当然 `Object.defineProperty()` 也可以。其实 [Immer](https://github.com/immerjs/immer) 这个库就是用了这种做法来生成不可变对象的，接下来就让我们来试着通过 `Proxy` 来实现高性能版的深拷贝。

[更多内容请看这里](./wheels/deepClone/index.md)