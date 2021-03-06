# WorkTasks

本人常用用户名密码集合：

```java
h5售房手机端：
    我的用户名/密码
	13545035011/123456
    
公司自己的仓库：
    http://ys.hztujing.com:9901/
    我的用户名/密码：zangziwei/123456
        

    
    
    
    
    
    
    
    
    
```







## uni-app

### 1、开发环境节点端口配置

- 官方文档里面明明有说明，但是就是没有写端口的配置，就很离谱。。。
- ![image-20220520112704991](Typora_images/workTasks/image-20220520112704991.png)

### 2、vscode快捷注释失效

- 按ctrl + /发现注释失效了。
- 使用ctrl + shift + p 打开命令搜索窗口，然后搜索注释，把快捷键改一下就行了。

### 3、导航栏配置在微信端和钉钉端失效的问题

- 官方文档上说就是页面的导航栏的配置可以由pages.json页面中的节点进行配置的，然后捏我就去配置了

![image-20220520151059260](Typora_images/workTasks/image-20220520151059260.png)

在这个h5的页面端显示的时候是没有任何问题的，但是打包后在微信端和钉钉端的编译就出现了问题，这些导航栏的配置根本显示不出来。。。结果还是得用page-mate写：

![image-20220520151339285](Typora_images/workTasks/image-20220520151339285.png)

这样写打包成微信端和小程序端就可以正常显示了。

- **<font color='purple'>文档上说了好像有三个端，一个web h5，一个是APP端，还有一个小程序端，上面的pages节点中的配置很多可以实现很多的样式，这些配置在h5端和APP端都可以比较好的使用，但是在小程序段就无能为力了，给爷看乐了🤣</font>**

### 4、头部组件开发

**<font color='red'>有两个问题没有解决：1个是头部导航栏的那个高度问题，我不知道怎么把高度调整高一点，文档里面没有相关的属性的配置的，然后还有一点就是那个钉钉小程序的那个头部的title无法居中的问题，明明我也设置了居中在h5端和微信端都是没有问题的，但是钉钉小程序就是无法居中，初步认为是钉钉内置的样式特效导致的</font>**

#### part1：导航栏高度问题？

![image-20220520161158377](Typora_images/workTasks/image-20220520161158377.png)

##### 解决：https://uniapp.dcloud.net.cn/collocation/pages.html#style

![image-20220523224446892](Typora_images/workTasks/image-20220523224446892.png)

#### part2：钉钉标题居中问题

![image-20220520161349976](Typora_images/workTasks/image-20220520161349976.png)

##### 解决：

#### part3：组件内容显示不出来

**<font color='red'>我封装了头部的组件，然后在h5调试的时候都显示不出来，就很离谱。。。然后我又封装了一个测试的content的组件，放在index页面上，结果也是没有显示出来。。。？</font>**

![image-20220520170012172](Typora_images/workTasks/image-20220520170012172.png)



- 这里我还特意使用Import导入组件，但是就是显示不出来。

![image-20220520170137036](Typora_images/workTasks/image-20220520170137036.png)



##### 解决：组件导入时大写

![image-20220520172513996](Typora_images/workTasks/image-20220520172513996.png)

- **<font color='purple'>组件在封装的时候最好都先大写，符合vue2的组件开发要求。然后别忘记在pages.json中进行页面的配置，就算不进行路由也是得先配置的。</font>**

- **<font color='red'>pages.json页面配置注意点：</font>**

  ![image-20220521123253804](Typora_images/workTasks/image-20220521123253804.png)



### 5、uni-app开发注意

#### 5.1、根元素唯一

![image-20220521144046985](Typora_images/workTasks/image-20220521144046985.png)

**<font color='purple'>在\<template>模板中根元素必须唯一，虽然在公司电脑上写两个根元素没有问题？这个我也搞不清楚是什么问题，有可能是版本问题，不过为了规范性和兼容性考虑，请遵守这个准则！</font>**

#### 5.2、*组件导入的坑

- **组件可以按照经典的vue2.x的import模式进行导入也可以采用最新的easycome导入方式，[easycome导入](https://uniapp.dcloud.net.cn/collocation/pages.html#easycom)，注意如果按照[vue2.x组件命名标准](https://cn.vuejs.org/v2/style-guide/#%E5%9F%BA%E7%A1%80%E7%BB%84%E4%BB%B6%E5%90%8D%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)进行导入，不然很有可能有莫名奇妙的报错的。。。**

  - **<font color='purple'>建议给组件命名时，使用`xxx-xxx-...`的形式，这种形式既符合组件命名规范，又符合easycome的导入方式</font>**

  如图：

  ![image-20220521153020886](Typora_images/workTasks/image-20220521153020886.png)

  - **<font color='red'>如果使用大写的驼峰组件命名方式，easycome就不支持了。。。如图：</font>**

  ![image-20220521153428296](Typora_images/workTasks/image-20220521153428296.png)

  - 然后就报错了。。。

  ![image-20220521153518792](Typora_images/workTasks/image-20220521153518792.png)

#### 5.3、小程序打包的坑

打包错误：

![image-20220521163111567](Typora_images/workTasks/image-20220521163111567.png)

- **因为是文件名的关系，在小程序端进行打包，项目的文件名中不能包含-的，所以还是改成import导入吧，想想<font color='blue'>如果坚持用easycome导入，又要满足打包小程序不报错，那只能文件名和组件名相同并且小写，然后使用的时候大写，不然不可能了。</font>**

#### 5.4、本地图片显示的坑

**本来想在轮播图中显示图片的，然后使用img标签，不过发现在打包微信的时候图片的缩放不对，然后打包钉钉的时候发现图片显示不出来。。。没能解决这个问题；之后采用了背景图片的技术方案、用div然后样式设置如下：**

```css
.swiper-img{
	width:100%;
	height: 100%;
	/* background-image: url('~@/static/img1.jpg');  */
	/* background-repeat: no-repeat; */
	/* background-position: center; */
	background-size:100% 100%;  /**背景图片的大小 */
}

```

![image-20220522222032378](Typora_images/workTasks/image-20220522222032378.png)

- **然后dom的代码大概是这个样子的（源码删了），绑定style动态变量，然后就可以用v-for了，然后就是url这里使用es6的模板字符串，然后在打包微信的时候又出现问题了。。。就是图片的缩放不对了。然后把style中的background改成backgroundImage就正确了，我也不懂为什么，总之就是感觉很乱。然后打包钉钉还是失败了！**

**<font color='purple'>方向调整：使用上面的技术方案结果小问题一大堆，不知道从何解决起，还是自己一点一点试出来的，然后就想用uni-app官网提供的cover-view参考它的写法应该不会有太多问题了吧，结果钉钉小程序还是有问题，不懂。</font>**

![image-20220522223113049](Typora_images/workTasks/image-20220522223113049.png)

item项：

![image-20220522223138029](Typora_images/workTasks/image-20220522223138029.png)



- 这样写的话在微信小程序上没有问题的，都很正常，但是钉钉就是显示不出来。。。

![image-20220522223411460](Typora_images/workTasks/image-20220522223411460.png)

小结：

1. 使用本地图片的时候不要用相对路径和@开头的绝对路径，那个就算参照官方文档上的~@打包后还是显示不出来的。。。就是用/static的绝对路径就行了。
2. 不考虑使用base64的编码格式，因为它太长了，打包体积都大了太多。
3. 参考了各种的manifset中的小程序打包的设置都不能解决钉钉图片显示不出来的问题，不懂了。
4. 解决这个问题主要以下三个方向：1cover-img标签深入，2小程序打包配置文件，3看看钉钉的官方文档怎么说的吧。

### 6、uniapp-先后

- **<font color='purple'>看了一下uni-app的视频教程，发现原来底部的tabbar可以直接通过pages.json中的文件进行配置好的，这就是一个很重要的先后顺序的问题了，就是先有pages.json中的配置文件，然后再有那些个uni-app封装好的组件的。所以先搞定配置文件然后再搞定内置组件会比较好。</font>**

##### bug:【提示组件不存在】

- 通过pages.json的tabbar节点配置好底部的导航栏之后，然后运行报如下的错误：

![image-20220523220023034](Typora_images/workTasks/image-20220523220023034.png)

**<font color='purple'>解决：之前在index.vue组件中使用了YhTabbar组件，然后删掉该组件的时候忘记把使用给删了，删除掉就好了。</font>**



##### bug:【底部tabbar图片显示不出来】

![image-20220523221626576](Typora_images/workTasks/image-20220523221626576.png)



**<font color='purple'>解决：图片名字写错了。。。</font>**



**打包编译的结果：就是tabbar能对微信小程序有又很好的适配性，但是钉钉小程序就很死相了，不仅图片显示不出来，而且底部的tabbar也是显示不出来的，给爷整🤮🤡了。**



## 北向房销维护

### 1、prototype原型

最好的教程：https://www.bilibili.com/video/BV1gE411f7Fu?p=19&spm_id_from=333.851.header_right.history_list.click

- 在项目中就是使用Vue.prototype属性注册的全局getDicts方法，所以有必要去学习一下js prototype这个东西的。

#### 1.1、作用

功能：返回对象类型原型的引用

用法：Class.prototype  //注意这里是类名，不是对象！

#### 1.2、原理图

![image-20220525063958369](Typora_images/workTasks/image-20220525063958369.png)

- 其实就是一个道理，就是**<font color='purple'>没有的属性/方法到原型对象里面找</font>**，Person类中，如果没有age属性，你实例化一个person对象，然后用person.age是获取不到的对吧，如果你使用了Person.prototype.age = 30;相当于在Person原型对象中添加了一个age属性，值是30；这时候person对象就会根据指向原型对象的[[prototype]]指针来到原型对象中找找有没有这个属性，有了，用person.age时它的值就是30了。
- 还有一个比较容易混淆的，person.age = 20;注意这个是一个赋值语句，就是说在**<font color='purple'>Person类中动态添加一个age的属性</font>**，值为20；同时是不会改变原型对象中的age值的。

### 2、vue2.x代理配置



### 3、无

- 就是我发现北向房销对**<font color='purple'>请求的封装</font>**做的很好，就是一个组件对应一个js文件，这个js文件中封装好了该组件的所有请求，然后导入axios的原始封装，这种结构很好。【可以解决智慧工地中请求封装的问题】

- **<font color='purple'>函数封装导出 + 添加函数到Vue原型对象</font>**；就是像函数封装好之后导出，再用import导入的封装模式是非常常用的，然后就是添加函数给原型对象，然后Vue对象就有了全局的方法，这种设计思想应该主要是用于全局对象和全局方法而言的

- **<font color='purple'>快速定位目标组件</font>**：就是给你看一下跑起来的项目，快速定位到组件的位置。uniapp看pages.json，vue可以看路由。

- 拉取+启动项目的基础步骤**：1、先git clone下来项目；<font color='red'>2、进入到项目目标文件夹；3、npm install 下载依赖；</font>4、然后npm run dev/serve**
  - 这个很基础东西我还是要记录一下，这个是一切的基础，对吧，而我经常把2,3两步搞错，这就很麻烦了！以后不要记错了！

**<font color='blue'>然后再研究一下项目的目录结构，看看他们是怎么安排的。</font>**

### 4、bug【stylelint样式检查错误】

就是启动的时候报错了。。。

![image-20220525183237032](Typora_images/workTasks/image-20220525183237032.png)





- 凯哥说这个是stylelint导致样式语法错误，不知道为什么。

**<font color='green'>解决：这个的报错主要是因为stylelint的样式检查问题，因为我写的是rgb(21，45， 76， 70%);而rgb中是没有第四个参数的，所以就会自动转成rgb(21 45 76 /70%);的格式，然后就会报没有获取到argument $green的错误了；<font color='red'>首先得先换成rgba的然后再使用stylelint的自动修复功能取消对这一行的检查就行了。</font></font>**

如图所示：

![image-20220526101329982](Typora_images/workTasks/image-20220526101329982.png)





### 5、Typora图片路径设置

![image-20220527101552711](Typora_images/workTasks/image-20220527101552711.png)



### 6、pnpm简介

- 简介：**<font color='red'>pnpm就是高性能的npm，比原先的npm和yarn具有更高的性能，并且下载的包只有一份，不会有副本，节约磁盘空间。</font>**

- 参考：https://blog.csdn.net/weixin_43106777/article/details/121745882

### 7、router配置

#### 7.1、路径参数正则匹配

路由参数匹配官方文档：https://router.vuejs.org/zh/guide/essentials/route-matching-syntax.html#%E5%9C%A8%E5%8F%82%E6%95%B0%E4%B8%AD%E8%87%AA%E5%AE%9A%E4%B9%89%E6%AD%A3%E5%88%99

![image-20220529194733903](Typora_images/workTasks/image-20220529194733903.png)

- **()括起来的就是配置传进来的path参数可有可无。匹配正则表达式，具体看官方文档就知道了。**















## h5-housing-sales bug修复和维护

### 1、bug【内容显示不全的问题】

![image-20220530150720444](Typora_images/workTasks/image-20220530150720444.png)

**<font color='red'>原因：因为下面的那个输入框的大小限制为最大是100了，所以会连带上面的最大输入1000失效的，我也不知道是为什么，只要把100改成1000就好了。</font>**

![image-20220530151616429](Typora_images/workTasks/image-20220530151616429.png)





























## echarts高级使用

目标样式：

![image-20220530093820391](Typora_images/workTasks/image-20220530093820391.png)



### 1、颜色透明的设置方法

```js
        /** 蓝色透明圆的设置 */
        {
          type: 'pie',
          selectedMode :false,
          radius: ['50%'],
          center: ['50%', '50%'],
          hoverAnimation: false,
          //*设置不响应鼠标浮动事件
          silent: true,
          //数据可以为空
          data: [{name:'',value:100}],
          label: {
            //不要显示文本提示
            show: false,
          },
          itemStyle: {
            //@1这里为什么不显示呢？因为这个设置的意思是饼状图中的每一项进行样式设置
            //所以如果 data: []这样写的话，那么不是一项数据都没有了吗，所以颜色设置不起作用了捏。
            color: 'rgba(102,198,255,0.3)',
            borderColor: '#3871FE',
            borderWidth: 3,
            borderType: 'dashed'
          },
        },
```

- **<font color='red'>看看itemStyle的color节点，就是用rgba然后再使用‘’把它变成一个字符串就行了。</font>**

### 2、bug【饼状图颜色改变不了】

**<font color='purple'>bug描述，就是当options.color中设置了全局的颜色之后，然后在一个pie数据对象中设置 itemStyle.color就没有用了，后来才意识到，就是itemStyle是专门为data中的每一个item项目设置的，所以如果data:[] 这样写的话，就没有item项了，所以itemStyle.color就没有用了。</font>**

![image-20220527102228953](Typora_images/workTasks/image-20220527102228953.png)





## 其它

## 封装组件

### 1、bug【eslint报错】

![image-20220531111032499](Typora_images/workTasks/image-20220531111032499.png)



- **<font color='red'>解决，mthods不是tm的一个对象吗？？？？我自己把这个都写错了。。。服了，这个就太过于离谱了。</font>**



## 技术累积

**本周：**

- **首先是那个图片分块组件的编写，以及封装，尝试了使用flex布局和html2Canvas，以及使用原生dom进行操作->css**
- **然后是要看一下为什么 大运河中的em我使用不了？？**
- **<font color='red'>然后是滑块的scroll的样式的编写。去查询总结一下</font>**
- **然后是那个js日期的调用，把date的使用给总结一下**



- **<font color='purple'>js中两个！的意义和用法，第一个!可以将变量强制转成bool类型，第二个变量可以把类型转成具体的bool值。。。</font>**

***\*学会配置一个新的项目运行环境。。。\****







# 大运河H5

遇事多问为什么，为什么是反者道之动的最好应用了。

## 路由方面：

路由的文件夹结构：
![image-20220623095005515](Typora_images/workTasks/image-20220623095005515.png)

- 在modules这个模块文件夹中，有homeTabbar.js和tabbar.js两个路由配置文件，这两个文件的写法无一例外都是这样的：写好配置数组，然后导出配置数组。

![image-20220623095223736](Typora_images/workTasks/image-20220623095223736.png)



这个目前不知道是干啥用的，tabbar.js下面的路由是应用页面底部的四个大的路由，homeTabbar.js就是主页面那八个选项和其子页面，不过，alleventjudgment到目前为止我没有点到它的页面里。

![image-20220623100653874](Typora_images/workTasks/image-20220623100653874.png)



```js
const files = require.context('./modules', false, /\.js/);
const routes = [];

routes.push({
  path: '/',
  redirect: '/home'
});

files.keys().map(file => {
  const route = files(file).default;
  routes.push(...route);
});

// 404页面需要放到最末尾,先行注册404界面,否则无法指向404界面会报错
const errorPage = [
  {
    path: '/404',
    name: 'page404',
    hidden: true,
    component: () => import('@/views/404'),
    meta: { title: '404' }
  },
  {
    path: '/login',
    name: 'Login',
    component: () => import('@/views/login'),
    meta: { title: '登录', description: '登录' }
  },
  {
    path: '/notLogin',
    component: () => import('@/views/notLogin')
  },
  // 群众爆料的路由
  {
    path: '/breakNews',
    name: 'BreakNews',
    component: () => import('@/views/breakNews/BreakNews.vue'),
    meta: { title: '群众爆料', description: '群众爆料' }
  },
  // 群众爆料的文保点选择页面
  {
    path: '/breakNewsWenbao',
    name: 'BreakNewsWenbao',
    component: () => import('@/views/breakNews/BreakNewsWenbao.vue'),
    meta: { title: '文保点位', description: '文保点位' }
  },

  // 指向页面错误跳转到404
  { path: '*', redirect: '/404', hidden: true }
];
routes.push(...errorPage);
// 路由入口文件
export default routes;
```

- 这个就是routes.js路由中的全部内容，

这段代码是什么意思？

```js
const files = require.context('./modules', false, /\.js/);
```



**require.context(directory,useSubdirectories,regExp)**

**directory:表示检索的目录**
**useSubdirectories：表示是否检索子文件夹**
**regExp:匹配文件的正则表达式,一般是文件名**
**例如 require.context("@/views/components",false,/.vue$/)**

**<font color='red'>所以我们知道这里的意思就是在当前的modules文件夹下匹配所有的.js文件，然后不用在子文件中检索，然后导出到files常量，我们打印一下这个files.keys()，然后就会出现下面的结果：</font>**

![image-20220623103547275](Typora_images/workTasks/image-20220623103547275.png)

这就说明files.key()就是文件们的路径数组。那一定会有一个疑问就是什么是files(file)呢，打印出来看看：

![image-20220623104208576](Typora_images/workTasks/image-20220623104208576.png)

**<font color='red'>这下就明了了，files(file).default就是当初export default Tabber的数组。为什么他要用require.context然后使用循环的方式来进行导入呢?相比于Import一次性只能导出，一个文件（当然在一个文件里可以导出很多的export ），使用require.context可以一次性导入多个文件，然后多个文件就比较好进行拆分了。</font>**





## 向后台提交数据submit

Promise对象：

```js
var p = new Promise((resolve, reject) => {
    //做一些异步操作
    setTimeout(function(){
        console.log('执行完成');
        resolve('随便什么数据');
    }, 2000);
});
```

- 回调函数中的resolve，和reject函数其实都只是设置了Promise对象的状态而已。



submit函数：

```js
    // 提交
    async handleSubmit() {
      if (+this.checkRadio === 1) {
        const { bumpPointId, problemRemark } = this.form;
        const imgList = this.$refs.uploadFile.imgFileList;
        const wentiList = this.checkQuestion;
        if (!bumpPointId) {
          TipsPop({
            message: '文保点位未选择',
            type: 'fail'
          });
          return;
        }

        if (!(problemRemark || wentiList.length > 0)) {
          TipsPop({
            message: '问题未选择或描述',
            type: 'fail'
          });
          return;
        }
        if (imgList.length === 0) {
          TipsPop({
            message: '图片未上传',
            type: 'fail'
          });
          return;
        }
      }
      if (this.form.type === '0' && !this.form.remark) {
        TipsPop({
          message: '代巡检人未填',
          type: 'fail'
        });
        return;
      }

      // 先判断是否有点位，再进行ToastLoading提交加载提示
      const pos = await getLocalPosition();
      if (!pos) {
        return;
      }

      const { Success, Fail } = ToastLoading({
        text: '提交中',
        success: '新增巡检成功',
        fail: '新增巡检失败'
      });
      if (this.isLoad) {
        return;
      }
      this.isLoad = true;


      const form = { ...this.form, lon: pos.longitude, lat: pos.latitude };
      form.files = [
        ...this.$refs.uploadFile.imgFileList,
        ...this.$refs.uploadFile.videoFileList,
        ...this.$refs.audioFile.audioList
      ];
      form.problemList = this.checkQuestion.join(';');
      form.problemExist = this.checkRadio;
      const fileViews = this.fileViewList.map((item, index, arr) => {
        return {
          fileUrl: item.fileUrl.replaceAll(process.env.VUE_APP_BASE_API, ''),
          fileUrlOrig: item.fileUrlOrig.replaceAll(
            process.env.VUE_APP_BASE_API,
            ''
          ),
          remark: item.remark,
          type: item.type
        };
      });
      form.files = [...form.files, ...fileViews];

      postPollingReport(form).then(response => {
        console.log('提交的表单', form);
        if (response.code === 200) {
          setTimeout(() => {
            Success(() => {
              this.isLoad = false;
              this.resetForm();
              this.$router.go(-1);
            });
          }, 1000 * 1);
        } else {
          Fail(response.msg);
        }
        this.isLoad = false;
      });
    },
```

- 首先这个提交是一个异步函数，为的就是能获取post之后的response状态，看看是否提交成功了。
- 然后是+this.checkRadio，这个变量前面的+是什么意思？？

```js
// null：返回 0
console.info(+null) // => 0
// undefined：返回 NaN
console.info(+undefined) // => NaN
// 获取当前的时间戳，相当于`new Date().getTime()`
console.info(+new Date())
// 布尔型转换为整型：true 返回 1，false 返回 0
console.info(+true) // => 1
console.info(+false) // => 0
// 空字符串：返回0
console.info(+'') // => 0
// 忽略前面的 0
console.info(+'010') // => 10
// 16进制转换成 10进制
console.info(+'0x3E8') // => 1000
// 科学计数法自动解析
console.info(+'1e3') // => 1000
console.info(+'1e-3') // => 0.001
// 无法解析的格式：返回 null
console.info(+'1,000') // => NaN
```

可问题在于this.checkRadio是一个number类型的数据啊，this.checkRadio和+this.checkRadio都是0，这段代码没有什么太大的意义.



```js
      if (+this.checkRadio === 1) {
        const { bumpPointId, problemRemark } = this.form;
        const imgList = this.$refs.uploadFile.imgFileList;
        const wentiList = this.checkQuestion;
        if (!bumpPointId) {
          TipsPop({
            message: '文保点位未选择',
            type: 'fail'
          });
          return;
        }

        if (!(problemRemark || wentiList.length > 0)) {
          TipsPop({
            message: '问题未选择或描述',
            type: 'fail'
          });
          return;
        }
        if (imgList.length === 0) {
          TipsPop({
            message: '图片未上传',
            type: 'fail'
          });
          return;
        }
      }
```

- 这段代码是校验是否巡检存在问题的，如果有问题this.checkRadio就是1。这个bumpPointId的获取是什么时候的事情呢？函数的执行时机主要有以下三个：钩子函数、事件（@click、@change、@confirm。。。）、其它函数的调用。





![image-20220623164034344](Typora_images/workTasks/image-20220623164034344.png)



- **<font color='#ff4000'>这个activated函数好像是，vue3 keep-alive的钩子函数，它的作用和用法我们还不得而知</font>**



```js
        if (!(problemRemark || wentiList.length > 0)) {
          TipsPop({
            message: '问题未选择或描述',
            type: 'fail'
          });
          return;
        }
```

- 这个判断的写法还是挺有意思的，对于两个中只要有一个就可以通过就行的 校验，!（... || ... || ...）总体取反

- 你想想，这里写成下面这样行不行

```js
        if (!problemRemark || !wentiList.length > 0) {
          TipsPop({
            message: '问题未选择或描述',
            type: 'fail'
          });
          return;
        }
```

==如果这样写的，只有两个都选中了，校验才不会触发，否则校验还是会触发的！==





 ```js
   const { Success, Fail } = ToastLoading({
 
     text: '提交中',
 
     success: '新增巡检成功',
 
     fail: '新增巡检失败'
 
    });
 
 ```

- 这个是提交中的加载框框，ToastLoading的具体实现看一下：

```js
export const ToastLoading = (obj = {}) => {
  const { text = '加载中...', success = '加载完成', fail = '加载失败' } = obj;
  Toast.loading({
    message: text,
    forbidClick: true,
    duration: 0
  });
  // 成功具备回调函数
  const Success = fn => {
    Toast.clear();
    Toast.success({
      message: success,
      forbidClick: true,
      duration: 1000,
      onClose: () => {
        fn && fn();
      }
    });
  };
  // 失败具备动态文本
  const Fail = str => {
    Toast.clear();
    Toast.fail({
      message: str || fail,
      forbidClick: true
    });
  };
  return {
    Success,
    Fail
  };
};

```

- 首先是obj = {}，这个是默认参数的用法。
- 然后是Toast这个是vant的组件，在这里做了一层封装。

- 总体来说，这个ToastLoading是一个函数，这个函数在执行的时候，就会调用Toast.loaing展示提交中的加载框框，封装Toast.success加载成功函数和Toast.fail失败函数的时候，用了两个函数，一个是Success封装函数，还有一个是Fail封装函数，这两个封装函数是提供给外部调用使用的，可见一个函数的功能可以有很多，既可以执行具体的过程，也可以定义新的封装函数并且返回给外部供外部的函数进行调用。这两个函数都先，调用clear先清除Toast.loading的窗口，然后再调用Toast.success函数和Toast.fail函数，在success函数当中，可以传递一个回调函数，就是在loading成功的时候进行一下后续的处理操作。【比如提交成功之后，进行表单的重置，然后返回到上一个提交之前的页面等等，我们可以看一下这里进行的操作。】

![image-20220623182224976](Typora_images/workTasks/image-20220623182224976.png)



- 这个timeout的设置的时间决定了Toast.loading框能存在多长的时间，因为，Success()函数一旦执行的话，才会把Toast.loading的窗口关闭掉的。
- 然后就是isLoad这个校验的作用：，如图：

![image-20220623183114932](Typora_images/workTasks/image-20220623183114932.png)

**<font color='red'>之前我一直不明白为什么，这里需要这个isLoad的校验，这个是因为，有这样一种情况，就是在提交中的时候，加载框不是会停留1s钟吗，如果这个时候再去点击提交的话，就会再次进行提交，这个是很不好的。。。</font>**



## 文保选择页面

![image-20220625082422470](Typora_images/workTasks/image-20220625082422470.png)



**<font color='red'>想一想这个页面有哪一些功能点，首先刚进入页面你就要从后台拿到所有的数据，然后渲染到页面上，这是其一，然后你要能通过选择区域、镇街道、片区来重新向后台发起数据请求获取到筛选过后的内容，这是其二，其三还要注意到上方输入框的搜索功能，最后还要满足只能选中一项，然后点击确认后能够返回到上一个页面。</font>**



该组件的初始化代码：

```js
  created() {
    getPointArea().then(res => {
      this.inspectionTypeList.push(...res.data);
    });

    getPointStreet().then(res => {
      this.distributeTypeList.push(...res.data);
    });

    getPointGrid().then(res => {
      this.gridTypeList.push(...res.data);
    });

    this.resetScroll();
    console.log(this.getList(1, true));
  }
```

==上面三个部分是先获取所有的区域，街道以及片区，可以供我们选择。==



























