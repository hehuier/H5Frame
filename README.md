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
## Preloadjs
``` javascipt
var loader, drawCanvans;
var prevLoad = function(){
  var imgUrls = [{
    {id:"bg", src:assetsPath + "images/bg.jpg"},
    {id:"logo", src:assetsPath + "images/logo.png"},
  }]
  loader = new createjs.LoadQueue(false);
  loader.addEventListener("progress", handleProgress);
  loader.addEventListener("complete", handleComplete);
  loader.loadManifest(imgUrls);
	function handleProgress (evt) {
		var num = Math.floor(evt.progress*100);
		$('.loading .num').html(num+'%');
	}
	function handleComplete (evt) {
	  // num 设置成100%
    drawCanvans = new DrawCanvans();
	}	  
}
``` 
#### EaselJS：
1. API
>画图片用(Bitmap)
>画图形，比如矩形，圆形等用(Shape) 【类似于改变坐标x，y，增加阴影shadow，透明度alpha，缩小放大scaleX/scaleY都可以做到】
>画文字，用(Text)
>容器Container，容器可包含多个显示对象
1. 绘图的大致流程: 创建显示对象→设置一些参数→调用方法绘制→添加到舞台→update()
``` javascipt
function DrawCanvans(){
  var canvas, stage, _logo, _area1, _area2, _area3;
  this.init = function(){
    w = $(window).width();
    h = $(window).height();
    var scale = w / _W;
    var canvas_width = parseInt(_W * scale);
    var canvas_height = parseInt(_H * scale);
    
    canvas = document.getElementById("mapCanvas");
    $("#canvas").css({"width": canvas_width + "px", "height": canvas_height + "px"});
    stage = new createjs.Stage(canvas);
    createjs.Ticker.setFPS(30);    //舞台帧率控制
    createjs.Ticker.addEventListener("tick", stage);   //舞台更新
    createjs.Touch.enable(stage);  // 支持touch
    
    _logo = new createjs.Bitmap(loader.getResult("logo"));
	  _logo.x = 246;
	  _logo.y = 85;
	  _logo.alpha = 0;   
    
     stage.addChild(_logo);
  }
  this.init();
}
``` 

#### TweenJs：
``` javascipt
  createjs.Tween.get(_area1).to({x:214, y: 735, scale: 1}, 800, createjs.Ease.quintInOut).call(function(){});
  createjs.Tween.get(_area2).wait(100).to({x:474, y: 746, scale: 1}, 600, createjs.Ease.quintInOut).call(function(){});
  ``` 
#### TweenJs：
``` javascipt
  createjs.Tween.get(_area1).to({x:214, y: 735, scale: 1}, 800, createjs.Ease.quintInOut).call(function(){});
  createjs.Tween.get(_area2).wait(100).to({x:474, y: 746, scale: 1}, 600, createjs.Ease.quintInOut).call(function(){});
  ``` 
1. 连续变化
	Ease时间变化函数 Linear/IN/OUT/INOUT
![](http://www.xdnote.com/images/tween-easing.png)
2. 离散型变化
`
 createjs.Tween.get(_area1).to({x: [ 1, 2, 3, 4, 5]}, 800,createjs.Ease.quintInOut).call(function(){});
// 设置后会根据值的数量(5个值时) ，分别时间经过 0%, 25%, 50%, 75%, 100% 时返回。
`
  数量过渡默认使用的是 TWEEN.Interpolation.Linear, 也可以使用 interpolation 方法做为时间变换的参数，除了 TWEEN.Interpolation.Linear 之外，还支持 TWEEN.Interpolation.Bezier, TWEEN.Interpolation.CatmullRom
3. 自定义过渡函数

`function stepEasing(k) {
	return Math.floor(k * 10) / 10;
}
tween.easing(stepEasing);`


