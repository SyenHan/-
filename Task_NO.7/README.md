# 任务七：实现常见的技术产品官网的页面架构及样式布局

####任务目的

+ 通过实现一个常见的技术产品官网，加深对于HTML，CSS的实战能力
+ 学习掌握如何在没有标注的情况下实现设计稿到页面的精确转变

####任务描述

+ 通过HTML及CSS实现设计稿 [设计稿PSD文件（点击下载）](http://7xrp04.com1.z0.glb.clouddn.com/task_1_7_1.psd)，效果如 [效果图（点击打开）](http://7xrp04.com1.z0.glb.clouddn.com/task_1_7_2.jpg)
+ 设计稿是有一定宽度的，这个宽度为页面的最小宽度，也就是说，当浏览器窗口宽度小于设计稿宽度时，允许出现横向滚动条，页面内容宽度保持不变，但是当浏览器窗口宽度大于设计稿宽度时，页面部分内容的宽度应该保持和浏览器窗口宽度一致，具体哪些部分题目不做具体指明，看看大家的判断如何。

####任务注意事项

+ 只需要完成HTML，CSS代码编写，不需要写JavaScript
+ 设计稿中的图片、文案均可自行设定
+ 在Chrome中完美实现与设计稿的各项字体、布局、内外边距等样式
+ 有能力的同学可以尝试跨浏览器的兼容性
+ 有能力的同学可以在实现一遍后尝试用less, sass或者stylus等再实现一次

####在线学习参考资料

+ [MDN HTML入门](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Introduction)
+ [MDN CSS入门教程](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Getting_started)
+ [百度面试题--盒子凸起一个角效果实现的讨论](http://blog.csdn.net/u014267351/article/details/48374373)



####箭头实现
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>css制作空心的上下左右的箭头</title>
    <style type="text/css">
        *{
            padding:0;
            margin:0;
        }
        .box{
            width:100px;
            height:500px;
            margin:0 auto;
            border:1px solid red;
            background:white;
        }
        .arrow-box{
            width:30px;
            height:30px;
            margin:20px auto;
            position:relative;
        }
        /*右箭头*/
        .right{
            width:20px;
            height:20px;
            position:absolute;
            left:0;
            top:0;
            border:1px solid blue;
        }
        .right-arrow1,.right-arrow2{
            width:0;
            height:0;
            display:block;
            position:absolute;
            left:0;
            top:0;
            border-top:10px transparent dashed;
            border-right:10px transparent dashed;
            border-bottom:10px transparent dashed;
            border-left:10px white solid;
            overflow:hidden;
        }
        .right-arrow1{
            left:1px;/*重要*/
            border-left:10px blue solid;
        }
        .right-arrow2{
            border-left:10px white solid;
        }
        /*左箭头*/
        .left{
            width:20px;
            height:20px;
            position:absolute;
            left:0;
            top:0;
            z-index: 2;/*兼容ie8-*/
            border:1px solid blue;
        }
        .left-arrow1,.left-arrow2{
            width:0;
            height:0;
            display:block;
            position:absolute;
            left:0;
            top:0;
            z-index:5;/*兼容ie8-*/
            border-top:10px transparent dashed;
            border-left:10px transparent dashed;
            border-bottom:10px transparent dashed;
            border-right:10px white solid;
            overflow:hidden;
        }
        .left-arrow1{
            border-right:10px blue solid;
        }
        .left-arrow2{
            left:1px;/*重要*/
            border-right:10px white solid;
        }
        /*上箭头*/
        .top{
            width:20px;
            height:20px;
            position:absolute;
            left:0;
            top:0;
            z-index: 2;/*兼容ie8-*/
            border:1px solid blue;
        }
        .top-arrow1,.top-arrow2{
            width:0;
            height:0;
            display:block;
            position:absolute;
            left:0;
            top:0;
            z-index: 5;/*兼容ie8-*/
            border-top:10px transparent dashed;
            border-left:10px transparent dashed;
            border-right:10px transparent dashed;
            border-bottom:10px white solid;
            overflow:hidden;
        }
        .top-arrow1{
            border-bottom:10px blue solid;
        }
        .top-arrow2{
            top:1px;/*重要*/
            border-bottom:10px white solid;
        }
        /*下箭头*/
        .bottom{
            width:20px;
            height:20px;
            position:absolute;
            left:0;
            top:0;
            z-index: 2;/*兼容ie8-*/
            border:1px solid blue;
        }
        .bottom-arrow1,.bottom-arrow2{
            width:0;
            height:0;
            display:block;
            position:absolute;
            left:0;
            top:0;
            z-index: 5;/*兼容ie8-*/
            border-bottom:10px transparent dashed;
            border-left:10px transparent dashed;
            border-right:10px transparent dashed;
            border-top:10px white solid;
            overflow:hidden;
        }
        .bottom-arrow1{
            top:1px;/*重要*/
            border-top:10px blue solid;
        }
        .bottom-arrow2{
            border-top:10px white solid;
        }
    </style>

<body>
<div class="box">
    <p> 右箭头</p>
    <div class="arrow-right arrow-box">
        <b class="right"><i class="right-arrow1"></i><i class="right-arrow2"></i></b>
    </div>
    <p> 左箭头</p>
    <div class="arrow-left arrow-box" >
        <b class="left"><i class="left-arrow1"></i><i class="left-arrow2"></i></b>
    </div>
    <p> 上箭头</p>
    <div class="arrow-top arrow-box" >
        <b class="top"><i class="top-arrow1"></i><i class="top-arrow2"></i></b>
    </div>
    <p> 下箭头</p>
    <div class="arrow-bottom arrow-box" >
        <b class="bottom"><i class="bottom-arrow1"></i><i class="bottom-arrow2"></i></b>
    </div>
</div>
</body>
</html>
```
```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title></title>
<style type="text/css">
.arrow {
width: 20px;
height: 4px;
margin: 0 auto 7px;
border-left: 4px solid transparent;
border-right: 4px solid transparent;
border-bottom: 4px solid #343c99;
transform: rotate(45deg);
transform-origin: left;
}.arrow:after {
content: '';
display: block;
width: 100%;
height: 100%;
border-left: 4px solid transparent;
border-right: 4px solid transparent;
border-top: 4px solid #343c99;
position: absolute;
right: -10px;
top: -14px;
transform: rotate(90deg);
transform-origin: bottom;
}
</style>
</head>
<body>
<div></div>
</body>
</html>
```
第二种写法相对于比较简单

```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title></title>
<style type="text/css">
/*简单*/
.wb_arrow{
border-right: 2px solid #343c99;
border-top: 2px solid #343c99;
height: 10px;
width: 10px;
margin:50px auto 0;
transform: rotate(deg);
-webkit-transform: rotate(0deg);
/*不加这两个属性三角会比上一个略丑, 大家可以试一下*/
border-left: 2px solid transparent;
border-bottom: 2px solid transparent;
}
</style>
</head>
<body>
<div></div>
</body>
</html>
```

```
.test {
    position: relative;
    width: 120px;
    height: 40px;
    border: 1px solid #d2d2d2;
    border-radius: 3px;
}
.test:after {
    position: absolute;
    right: 15px;
    top: 18px;
    width: 0;
    height: 0;
    content: "";
    border-width: 6px 6px 0 6px;
    border-style: solid;
    border-color: #fff transparent;
    -webkit-transition: all .25s;
       -moz-transition: all .25s;
        -ms-transition: all .25s;
         -o-transition: all .25s;
            transition: all .25s;
}

.test:before {
    position: absolute;
    right: 13px;
    top: 18px;
    width: 0;
    height: 0;
    content: "";
    border-width: 8px 8px 0 8px;
    border-style: solid;
    border-color: #d36969 transparent;
    -webkit-transition: transform .25s;
       -moz-transition: transform .25s;
        -ms-transition: transform .25s;
         -o-transition: transform .25s;
            transition: transform .25s;
}
.test.active:after{       
    top: 20px;
    -webkit-transform: rotate(180deg);
       -moz-transform: rotate(180deg);
        -ms-transform: rotate(180deg);
         -o-transform: rotate(180deg);
            transform: rotate(180deg); 
}
.test.active:before{
    -webkit-transform: rotate(180deg);
       -moz-transform: rotate(180deg);
        -ms-transform: rotate(180deg);
         -o-transform: rotate(180deg);
            transform: rotate(180deg);        
}
```

####照片旁白色三角
```
.triangle {
	width: 2px;
    height: auto;
    position: relative;
	/*三角只出现在右侧，采用div翻转的方式*/
    -moz-transform: rotate(180deg);
	-webkit-transform: rotate(180deg);
	-o-transform: rotate(180deg);
	-ms-transform: rotate(180deg);
	transform: rotate(180deg);
}
.triangle:before{
	content: "";
  	position: absolute;
  	top: 280px;
  	width: 0px;
  	height: 0px;
  	border: 20px solid transparent;
  	border-left-color: #fff;
}
```
####select下拉列表样式
```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>ADVANCED CSS3 STYLING OF SELECT ELEMENT (DROP-DOWN)</title>
        <style type="text/css">
 
            /* SELECT W/IMAGE */
            select#selectTravelCity
            {
               width                    : 14em;
               height                   : 3.2em;
               padding                  : 0.2em 0.4em 0.2em 0.4em;
               vertical-align           : middle;
               border                   : 1px solid #e9e9e9;
               -moz-border-radius       : 0.2em;
               -webkit-border-radius    : 0.2em;
               border-radius            : 0.2em;
               box-shadow               : inset 0 0 3px #a0a0a0;
               -webkit-appearance       : none;
               -moz-appearance          : none;
               appearance               : none;
               /* sample image from the webinfocentral.com */
               background               : url(http://webinfocentral.com/Images/favicon.ico) 95% / 10% no-repeat #fdfdfd;
               font-family              : Arial,  Calibri, Tahoma, Verdana;
               font-size                : 1.1em;
               color                    : #000099;
               cursor                   : pointer;
            }
            select#selectTravelCity  option
            {
                font-size               : 1em;
                padding                 : 0.2em 0.4em 0.2em 0.4em;
            }
            select#selectTravelCity  option[selected]{ font-weight:bold}
            select#selectTravelCity  option:nth-child(even) { background-color:#f5f5f5; }
            select#selectTravelCity:hover
            {
                color                   : #101010;
                border                  : 1px solid #cdcdcd;
            }    
            select#selectTravelCity:focus {box-shadow: 0 0 2px 1px #404040;}
 
            /*SELECT W/DOWN-ARROW*/
            select#selectPointOfInterest
            {
               width                    : 185pt;
               height                   : 40pt;
               line-height              : 40pt;
               padding-right            : 20pt;
               text-indent              : 4pt;
               text-align               : left;
               vertical-align           : middle;
               box-shadow               : inset 0 0 3px #606060;
               border                   : 1px solid #acacac;
               -moz-border-radius       : 6px;
               -webkit-border-radius    : 6px;
               border-radius            : 6px;
               -webkit-appearance       : none;
               -moz-appearance          : none;
               appearance               : none;
               font-family              : Arial,  Calibri, Tahoma, Verdana;
               font-size                : 18pt;
               font-weight              : 500;
               color                    : #000099;
               cursor                   : pointer;
               outline                  : none;
            }
            select#selectPointOfInterest option
            {
                padding             : 4px 10px 4px 10px;
                font-size           : 11pt;
                font-weight         : normal;
            }
            select#selectPointOfInterest option[selected]{ font-weight:bold}
            select#selectPointOfInterest option:nth-child(even) { background-color:#f5f5f5; }
            select#selectPointOfInterest:hover {font-weight: 700;}
            select#selectPointOfInterest:focus {box-shadow: inset 0 0 5px #000099; font-weight: 600;}
 
            /*LABEL FOR SELECT*/
            label#lblSelect{ position: relative; display: inline-block;}
            /*DOWNWARD ARROW (25bc)*/
            label#lblSelect::after
            {
                content                 : "\25bc";
                position                : absolute;
                top                     : 0;
                right                   : 0;
                bottom                  : 0;
                width                   : 20pt;
                line-height             : 40pt;
                vertical-align          : middle;
                text-align              : center;
                background              : #000099;
                color                   : #fefefe;
               -moz-border-radius       : 0 6px 6px 0;
               -webkit-border-radius    : 0 6px 6px 0;
                border-radius           : 0 6px 6px 0;
                pointer-events          : none;
            }
        </style>
    </head>
 
    <body>
        <br />
        <select id="selectTravelCity" title="Select Travel Destination">
            <option>New York City</option>
            <option>Washington DC</option>
            <option>Los Angeles</option>
            <option>Chicago</option>
            <option>Houston</option>
            <option>Philadelphia</option>
            <option>Phoenix</option>
            <option>San Antonio</option>
            <option>San Diego</option>
            <option>Dallas</option>
            <option>San Jose</option>
            <option>Austin</option>
        </select>
        <br />
        <br />
 
        <label id="lblSelect">
            <select id="selectPointOfInterest" title="Select points of interest nearby">
                <option>caffe</option>
                <option>food beverage</option>
                <option>restaurant</option>
                <option>shopping</option>
                <option>taxi limo</option>
                <option>theatre</option>
                <option>museum</option>
                <option>computers</option>
            </select>
        </label>
</body>
</html>
```