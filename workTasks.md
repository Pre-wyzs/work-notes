# WorkTasks

## uni-app

### 1、开发环境节点端口配置

- 官方文档里面明明有说明，但是就是没有写端口的配置，就很离谱。。。
- ![image-20220520112704991](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520112704991.png)

### 2、vscode快捷注释失效

- 按ctrl + /发现注释失效了。
- 使用ctrl + shift + p 打开命令搜索窗口，然后搜索注释，把快捷键改一下就行了。

### 3、导航栏配置在微信端和钉钉端失效的问题

- 官方文档上说就是页面的导航栏的配置可以由pages.json页面中的节点进行配置的，然后捏我就去配置了

![image-20220520151059260](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520151059260.png)

在这个h5的页面端显示的时候是没有任何问题的，但是打包后在微信端和钉钉端的编译就出现了问题，这些导航栏的配置根本显示不出来。。。结果还是得用page-mate写：

![image-20220520151339285](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520151339285.png)

这样写打包成微信端和小程序端就可以正常显示了。

- **<font color='purple'>文档上说了好像有三个端，一个web h5，一个是APP端，还有一个小程序端，上面的pages节点中的配置很多可以实现很多的样式，这些配置在h5端和APP端都可以比较好的使用，但是在小程序段就无能为力了，给爷看乐了🤣</font>**

### 4、头部组件开发

**<font color='red'>有两个问题没有解决：1个是头部导航栏的那个高度问题，我不知道怎么把高度调整高一点，文档里面没有相关的属性的配置的，然后还有一点就是那个钉钉小程序的那个头部的title无法居中的问题，明明我也设置了居中在h5端和微信端都是没有问题的，但是钉钉小程序就是无法居中，初步认为是钉钉内置的样式特效导致的</font>**

#### part1：导航栏高度问题？

![image-20220520161158377](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520161158377.png)

#### part2：钉钉标题居中问题

![image-20220520161349976](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520161349976.png)

#### part3：组件内容显示不出来

**<font color='red'>我封装了头部的组件，然后在h5调试的时候都显示不出来，就很离谱。。。然后我又封装了一个测试的content的组件，放在index页面上，结果也是没有显示出来。。。？</font>**

![image-20220520170012172](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520170012172.png)



- 这里我还特意使用Import导入组件，但是就是显示不出来。

![image-20220520170137036](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520170137036.png)



- **<font color='red'>解决：组件导入的时候要进行大写。。。</font>**

![image-20220520172513996](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520172513996.png)

- **<font color='purple'>组件在封装的时候最好都先大写，符合vue2的组件开发要求。然后别忘记在pages.json中进行页面的配置，就算不进行路由也是得先配置的。</font>**

- pages.json页面配置注意点：

  ![image-20220520173849102](C:\Users\win10\Desktop\我的任务\workTasks.assets\image-20220520173849102.png)



















