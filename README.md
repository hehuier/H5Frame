H5动效
交互：loading、转场、引导、反馈
视觉：主视觉、logo、字体、插画
动画：2D、3D、
1. 2D: Dom 渲染、canvas 渲染、WebGL 渲染
>[Pixi.js](http://www.pixijs.com/ "Pixi.js"):WebGL 的渲染速度都会比 Canvas快,Pixi同时支持WebGL和Canvas 2D两种渲染方式,对动画的支持不友好，需要引入动画库。[Pixi中文教程](https://github.com/Zainking/LearningPixi "Pixi中文教程")<br>
>[CreateJS](https://www.createjs.com/ "CreateJS")：TweenJS 支持动画开发、SoundJS 和 PreLoadJS 提供了音频和预下载的支持以及tweenJs（补间动画）
1. 3D
>[Three.js](https://threejs.org/ "Three.js")：倾向于视觉展示，支持WebGL和CSS3D渲染。
## CreateJS
- EaselJS：用于 Sprites、动画、向量和位图的绘制，创建 HTML5 Canvas 上的交互体验（包含多点触控）
- TweenJS：用于做动画效果，补间动画
- SoundJS：音频播放引擎
- PreloadJS：网站资源预加载
#### EaselJS：
1. API
>画图片用(Bitmap)
>画图形，比如矩形，圆形等用(Shape) 【类似于改变坐标x，y，增加阴影shadow，透明度alpha，缩小放大scaleX/scaleY都可以做到】
>画文字，用(Text)
>容器Container，容器可包含多个显示对象
1. 绘图的大致流程: 创建显示对象→设置一些参数→调用方法绘制→添加到舞台→update()
## CreateJS
- EaselJS：用于 Sprites、动画、向量和位图的绘制，创建 HTML5 Canvas 上的交互体验（包含多点触控）
- TweenJS：用于做动画效果，补间动画
- SoundJS：音频播放引擎
- PreloadJS：网站资源预加载
#### EaselJS：
1. API
>画图片用(Bitmap)
>画图形，比如矩形，圆形等用(Shape) 【类似于改变坐标x，y，增加阴影shadow，透明度alpha，缩小放大scaleX/scaleY都可以做到】
>画文字，用(Text)
>容器Container，容器可包含多个显示对象
1. 绘图的大致流程: 创建显示对象→设置一些参数→调用方法绘制→添加到舞台→update()
``` javascipt
var canvas = document.querySelector('#canvas');
var rect = new createjs.Shape();
rect.graphics.beginFill("#f00").drawRect(0, 0, 100, 100);
stage.addChild(rect);     //添加到舞台
stage.update();           //刷新舞台
``` 
