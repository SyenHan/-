# 任务三：三栏式布局

####任务目标

+ 掌握HTML/CSS布局的概念
+ 掌握盒模型的概念
+ 掌握position与float的概念以及在布局时的用法

####任务描述

+ 使用 HTML 与 CSS 按照 [示例图（点击查看）](http://7xrp04.com1.z0.glb.clouddn.com/task_1_3_1.png) 实现三栏式布局。
+ 左右两栏宽度固定，中间一栏根据父元素宽度填充满，最外面的框应理解为浏览器。背景色为 #eee 区域的高度取决于三个子元素中最高的高度。

####任务注意事项

+ 尝试 position 和 float 的效果，思考它们的异同和应用场景。
+ 注意测试不同情况，尤其是极端情况下的效果。
+ 图片和文字内容请自行替换，尽可能体现团队的特色。
+ 调节浏览器宽度，固定宽度和自适应宽度的效果始终符合预期。
+ 改变中间一栏的内容长度，以确保在中间一栏较高和右边一栏较高时，父元素的高度始终为子元素中最高的高度。
+ 其他效果图中给出的标识均被正确地实现。

####参考资料

+ [MDN：position](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)：了解 CSS position 属性的基本知识
+ [MDN：float](https://developer.mozilla.org/en-US/docs/Web/CSS/float)：了解 CSS float 属性的基本知识
+ [Learn CSS Positioning in Ten Steps](http://www.barelyfitz.com/screencast/html-training/css/positioning/)：通过具体的例子熟悉 position 属性
+ [清除浮动（clearfix hack）](http://zh.learnlayout.com/clearfix.html)：清除浮动是什么，如何简单地清除浮动
+ [StackOverflow：Which method of ‘clearfix’ is best?](http://stackoverflow.com/questions/211383/which-method-of-clearfix-is-best)：清除浮动黑科技完整解读


## 
### 七种不同的三栏式布局


#### 1. 流体式布局

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.left {
	    float: left;
	    height: 200px;
	    width: 100px;
	    background-color: red;
	}
	.right {
	    width: 200px;
	    height: 200px;
	    background-color: blue;
	    float: right;
	}
	.main {
	    margin-left: 120px;
	    margin-right: 220px;
	    height: 200px;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="left"></div>
        <div class="right"></div>
        <div class="main"></div>
    </div>
</body>
</html>
```
左右模块各自向左右浮动，并设置中间模块的 margin 值使中间模块宽度自适应。  
缺点就是主要内容无法最先加载，当页面内容较多时会影响用户体验。

#### 2. BFC三栏布局

BFC 规则有这样的描述：BFC 区域，不会与浮动元素重叠。因此我们可以利用这一点来实现 3 列布局。
```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.left {
	    float: left;
	    height: 200px;
	    width: 100px;
	    margin-right: 20px;
	    background-color: red;
	}
	.right {
	    width: 200px;
	    height: 200px;
	    float: right;
	    margin-left: 20px;
	    background-color: blue;
	}	
	.main {
	    height: 200px;
	    overflow: hidden;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="left"></div>
        <div class="right"></div>
        <div class="main"></div>
    </div>
</body>
</html>
```
缺点跟方法一类似，主要内容模块无法最先加载，当页面中内容较多时会影响用户体验。因此为了解决这个问题，有了下面要介绍的布局方案双飞翼布局。

#### 3. 双飞翼布局

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        .content {
  	    float: left;
  	    width: 100%;
        }
        .main {
  	    height: 200px;
  	    margin-left: 110px;
  	    margin-right: 220px;
  	    background-color: green;
        }
	.left {
	    float: left;
	    height: 200px;
	    width: 100px;
	    margin-left: -100%;
	    background-color: red;
	}
	.right {
	    width: 200px;
	    height: 200px;
	    float: right;
	    margin-left: -200px;
	    background-color: blue;
	}	
    </style>
</head>
<body>
    <div class="content">
        <div class="main"></div>
    </div>
    <div class="left"></div>
    <div class="right"></div>
</body>
</html>
```
利用的是浮动元素 margin 负值的应用，感兴趣的同学可以上网搜搜原理。  
主体内容可以优先加载，HTML 代码结构稍微复杂点。

#### 4. 圣杯布局

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.container {
	    margin-left: 120px;
	    margin-right: 220px;
	}
	.main {
	    float: left;
	    width: 100%;
	    height: 300px;
	    background-color: red;
	}
	.left {
	    float: left;
	    width: 100px;
	    height: 300px;
	    margin-left: -100%;
	    position: relative;
	    left: -120px;
	    background-color: blue;
	}
	.right {
	    float: left;
	    width: 200px;
	    height: 300px;
	    margin-left: -200px;
	    position: relative;
	    right: -220px;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="main"></div>
        <div class="left"></div>
        <div class="right"></div>
    </div>
</body>
</html>
```
跟双飞翼布局很像，有一些细节上的区别，相对于双飞翼布局来说，HTML 结构相对简单，但是样式定义就稍微复杂，也是优先加载内容主体。

#### 5. FLEX 布局

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.container {
            display: flex;
	}
	.main {
            flex-grow: 1;
	    height: 300px;
	    background-color: red;
	}
	.left {
	    order: -1;
	    flex: 0 1 200px;
	    margin-right: 20px;
	    height: 300px;
	    background-color: blue;
	}
	.right {
	    flex: 0 1 100px;
            margin-left: 20px;
	    height: 300px;
	    background-color: green;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="main"></div>
        <div class="left"></div>
        <div class="right"></div>
    </div>
</body>
</html>
```
简单实用，未来的趋势，需要考虑浏览器的兼容性。
####参考资料
+ [一个完整的Flexbox指南](http://www.w3cplus.com/css3/a-guide-to-flexbox-new.html)
+ [CSS 伸缩盒布局模组](https://www.w3.org/html/ig/zh/css-flex-1/#flex-flow)
+ [flexbox](http://www.w3cplus.com/blog/tags/157.html)

#### 6. TABLE 布局

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
        .container {
	    display: table;
	    width: 100%;
        }
        .left, .main, .right {
	    display: table-cell;
        }
        .left {
	    width: 200px;
	    height: 300px;
	    background-color: red;
        }
        .main {
	    background-color: blue;
        }
        .right {
	    width: 100px;
	    height: 300px;
	    background-color: green;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="left"></div>
        <div class="main"></div>
        <div class="right"></div>
    </div>
</body>
</html>
```
缺点：无法设置栏间距

#### 7. 绝对定位布局

```
<!DOCTYPE html>
<html lang="en">
<head>
    <style>
	.container {
	    position: relative;
	}
	.main {
	    height: 400px;
	    margin: 0 120px;
	    background-color: green;
	}
	.left {
	    position: absolute;
	    width: 100px;
	    height: 300px;
	    left: 0;
	    top: 0;
	    background-color: red;
	}
	.right {
	    position: absolute;
	    width: 100px;
	    height: 300px;
	    background-color: blue;
            right: 0;
	    top: 0;
	}
    </style>
</head>
<body>
    <div class="container">
        <div class="main"></div>
	    <div class="left"></div>
	    <div class="right"></div>
    </div>
</body>
</html>
```
简单实用，并且主要内容可以优先加载。