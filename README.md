# 移动端尺寸和单位
* 移动端尺寸
------
* 苹果常用尺寸

  * 苹果的尺寸比较固定，主要分为以下几种：
    * iphone4 ,4s       `640*960` xhdpi\[2倍\]
  
    * iphone5 ,5s ,5c   `640*1136` xhdpi\[2倍\]
  
    * iphone 6          `750*1334` xhdpi\[2倍\]
  
    * iphone 6+         `1242*2208`xxhdpi\[3倍\]<br>
    
    * （iphon7以及7+的分辨率跟6一模一样，ppi也是326和401）

* 安卓常用尺寸

  * 安卓尺寸碎片化比较严重，80×800, 480×854,540×960, 720×1280, 1080×1920什么样的分辨率都有，就目前的市场状况而言常用的尺寸有：
  
    * `480*800 `    hdpi\[1.5倍\]
  
    * `720*1280`    xhdpi\[2倍\]
  
    * `1080*1920`   xxhdpi\[3倍\]

* 逻辑像素与实际像素
  
  * 上面所列出的尺寸大多数都是实际像素，而在工作中常用的是逻辑像素，逻辑像素＝实际像素／倍率
  
  * 总结来说，移动端尺寸要比pc端复杂，主要是在倍率，但也因为倍率，把所有大大小小的屏幕拉回同一水平线。
  
  * 在css中我们常写的尺寸主要有320,360,375,414<br>

* 移动端单位
----------
* px
  
  * 移动端页面的绝对单位还是px, px保证固定大小。

* rem
  
  * rem（font size of the root element）是指相对于根元素的字体大小的单位。简单的来说它就是一个相对单位。我们可以通过改变根元素字体的大小从而改变页面上所有元素的大小。
 
  * 针对不同分辨率，设置不同的根元素font-size的值，可以使页面的排版始终按照等比例进行缩放，布局不会出现混乱
  
  * 可以通过js去动态计算font-size的值，但是也可以针对几款主流设备的分辨率使用media query来划分
  
  ```
    .one {
            width: 2rem;
            background: pink;
        }
        .two {
            width: 4rem;
            background: #000;
        }
        .three {
            width: 1.5rem;
            background: pink;
        }
    @media screen and (min-width: 320px) {
       html {
           font-size: 42.5px;
       }
   }
    @media screen and (min-width: 360px) {
        html {
            font-size: 48px;
        }
    }
    @media screen and (min-width: 375px) {
        html {
            font-size: 50px;
        }
    }
    @media screen and (min-width: 400px) {
        html {
            font-size: 55px;
        }
    }
```
* em
    
  * em也是一种相对单位
    
  * 有一个比较普遍的误解，认为em单位是相对于父元素的字体大小。 事实上，根据 W3标准 ，它们是相对于使用em单位的元素的字体大小。父元素的字体大小可以影响em值，但这种情况的发生，纯粹是因为继承。
    
  * 当em单位设置到根元素时，一般以浏览器本身默认的大小为基础，所以一般em单位都设置给特定的某个元素
    
  * em单位实际用的不多，就不多介绍啦
  
* %
    
  * %是目前布局中很常用的一种单位。主要是参照父级的值来进行设置。在不同分辨率下，使用同一套页面
  
  * css中可以使用百分比的一些属性
   定位：top,right,bottom,left <br>
   盒模型：height,width,margin,padding <br>
   背景：background-position,background-size <br>
   文本：text-indent <br>
   字体：font-size <br>
  
  * 当父级的高度设置成百分比时，子级无法用百分比继承父级的高度

* vm vh
  
  * vm vh 这两个单位是指视区宽度与高度的百分值，100vm=视区的宽度，100vh=视区的高度
  * 兼容性
  ![](http://image.zhangxinxu.com/image/blog/201608/2016-08-08_215718.png)
  * 在目前的网页设计中，最主流的方式是通过上述根据根元素的font-size的大小，具体模块在使用rem单位，但是这种方法基本只会在临界点的时候突然发生变化，不够流畅
  * 
  ```
  html {
    /* iPhone6的375px尺寸作为16px基准，600px正好18px大小 */
    font-size: calc(100% + 2 * (100vw - 375px) / 225);
}
@media screen and (min-width: 600px) {
    html {
        /* 600px-1000px每100像素宽字体增加1px(18px-22px) */
        font-size: calc(112.5% + 4 * (100vw - 600px) / 400);
    }
}
@media screen and (min-width: 1000px) {
    html {
        /* 1000px往后是每100像素0.5px增加 */
        font-size: calc(137.5% + 5 * (100vw - 1000px) / 1000);
    }
}
  ```

  
