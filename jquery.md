[TOC]

# jQuery
---

## jQuery 教程


- jquery参考手册

[jQuery API 手册](https://www.runoob.com/manual/jquery/)

- jQuery安装
    * 从 [jquery.com](https://jquery.com/download/) 下载 jQuery 库
    * 从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery

- 引入jQuery

    * 下载后直接在``` <script> ```标签引用它
        ```javascript
        <head>
            <script src="jquery-1.10.2.min.js"></script>
        </head>
        ```
    * 不希望下载并存放 jQuery，那么也可以通过 CDN（内容分发网络） 引用它
    ```js
        <!-- Staticfile CDN: -->
        <head>
            <script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js">
            </script>
        </head>
        <!-- 百度 CDN: -->
        <head>
            <script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
            </script>
        </head>
        <!-- 又拍云 CDN: -->
        <head>
            <script src="https://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.2.min.js">
            </script>
        </head>
        <!-- 新浪 CDN: -->
        <head>
            <script src="https://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js">
            </script>
        </head>
        <!-- Microsoft CDN: -->
        <head>
            <script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-1.9.0.min.js"></script>
        </head>
        <!-- Google CDN:  不大推荐使用Google CDN来获取版本，因为Google产品在中国很不稳定。 -->
        <head>
            <script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-1.9.0.min.js"></script>
        </head>
    ```
- jQuery 使用版本
   我们可以在浏览器的 Console 窗口中使用 $.fn.jquery 命令查看当前 jQuery 使用的版本：
   ![jQuery查看版本图片](./image/jQuery查看版本.jpg)
- jQuery语法
    jQuery 入口函数:
    ```js
        $(document).ready(function(){
            // 开始写 jQuery 代码...
        });  
    ```
    简洁写法：
    ```js
        $(function(){
            // 开始写 jQuery 代码...
        });
    ```
    JavaScript 入口函数:
    ```js
        window.onload = function () {
            // 执行代码
        }
    ```
    jQuery 入口函数与 JavaScript 入口函数的区别：
    * jQuery 的入口函数是在 html 所有标签(DOM)都加载之后，就会去执行。
    * JavaScript 的 window.onload 事件是等到所有内容，包括外部图片之类的文件加载完后，才会执行。
    ![load和ready区别](./image/load和ready区别.jpeg)
- jQuery选择器
    * 元素选择器
        jQuery 元素选择器基于元素名选取元素。
        在页面中选取所有 ```<p>``` 元素:
        ```js
            $("p")
        ```
        实例
        用户点击按钮后，所有 ```<p>``` 元素都隐藏
        ```js
            $(document).ready(function(){
                $("button").click(function(){
                    $("p").hide();
                });
            });
        ```
    * id选择器
        jQuery #id 选择器通过HTML元素的id属性选取指定的元素。
        页面中元素的id应该是唯一的，所以您要在页面中选取唯一的元素需要通过#id选择器
        通过id选取元素语法如下：
        ```js
            $("#test")
        ```
        当用户点击按钮后，有 id="test" 属性的元素将被隐藏：
        ```js
            $(document).ready(function(){
                $("button").click(function(){
                    $("#test").hide();
                });
            });
        ```
    * .class类选择器
        jQuery 类选择器可以通过指定的 class 查找元素
        语法如下：
        ```js
            $(".test")
        ```
        用户点击按钮后所有带有 class="test" 属性的元素都隐藏：
        ```js
            $(document).ready(function(){
                $("button").click(function(){
                    $(".test").hide();
                });
            });
        ```
        ```js
            $("#id", ".class")  复合选择器
            $(div p span)       层级选择器 //div下的p元素中的span元素
            $(div>p)            父子选择器 //div下的所有p元素
            $(div+p)            相邻元素选择器 //div后面的p元素(仅一个p)
            $(div~p)            兄弟选择器  //div后面的所有p元素(同级别)
            $(.p:last)          类选择器 加 过滤选择器  第一个和最后一个（first 或者 last）
            $("#mytable td:odd")      层级选择 加 过滤选择器 奇偶（odd 或者 even）
            $("div p:eq(2)")    索引选择器 div下的第三个p元素（索引是从0开始）
            $("a[href='www.baidu.com']")  属性选择器
            $("p:contains(test)")        // 内容过滤选择器，包含text内容的p元素
            $(":emtyp")        //内容过滤选择器，所有空标签（不包含子标签和内容的标签）parent 相反
            $(":hidden")       //所有隐藏元素 visible 
            $("input:enabled") //选取所有启用的表单元素
            $(":disabled")     //所有不可用的元素
            $("input:checked") //获取所有选中的复选框单选按钮等
            $("select option:selected") //获取选中的选项元素
        ```
- jQuery事件
| 鼠标事件   | 键盘事件 | 表单事件 | 文档/窗口事件 |
|:-----------|:---------|:---------|:--------------|
| click      | keypress | submit   | load          |
| dblclick   | keydown  | change   | resize        |
| mouseenter | keyup    | focus    | scroll        |
| mouseleave |          | blur     | unload        |
| hover      |          |          |               |
    jQuery事件方法语法：
    在 jQuery 中，大多数 DOM 事件都有一个等效的 jQuery 方法。
    页面中指定一个点击事件：
    ```js
        $("p").click();
    ```
    下一步是定义什么时间触发事件。您可以通过一个事件函数实现：
    ```js
        $("p").click(function(){
            // 动作触发后执行的代码!!
        });
    ```
    ### 常用的jQuery事件方法
    * $(document).ready()
    $(document).ready() 方法允许我们在文档完全加载完后执行函数。该事件方法在 jQuery 语法 章节中已经提到过。
    * click()

        click() 方法是当按钮点击事件被触发时会调用一个函数。

        该函数在用户点击 HTML 元素时执行。

        在下面的实例中，当点击事件在某个 ```<p>``` 元素上触发时，隐藏当前的``` <p>``` 元素：
        ```js
            $("p").click(function(){
                $(this).hide();
            });
        ```
    * mouseenter()

        当鼠标指针穿过元素时，会发生 mouseenter 事件。

        mouseenter() 方法触发 mouseenter 事件，或规定当发生 mouseenter 事件时运行的函数：
        ```js
            $("#p1").mouseenter(function(){
                alert('您的鼠标移到了 id="p1" 的元素上!');
            });
        ```
    * mousedown()

        当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown 事件。
        mousedown() 方法触发 mousedown 事件，或规定当发生 mousedown 事件时运行的函数：
        ```js
            $("#p1").mousedown(function(){
                alert("鼠标在该段落上按下！");
            });
        ```
    * focus()
    
        当元素获得焦点时，发生 focus 事件。
        当通过鼠标点击选中元素或通过 tab 键定位到元素时，该元素就会获得焦点。
        focus() 方法触发 focus 事件，或规定当发生 focus 事件时运行的函数：
        ```js
            $("input").focus(function(){
                $(this).css("background-color","#cccccc");
            });
        ```
    * blur()

        当元素失去焦点时，发生 blur 事件。
        blur() 方法触发 blur 事件，或规定当发生 blur 事件时运行的函数：
        ```js
            $("input").blur(function(){
                $(this).css("background-color","#ffffff");
            });

        ```
        #### keypress,keydown,keyup的区别：
        + keydown: 在键盘上按下某键时发生，一直按着则会不断触发（opera浏览器除外）, 它返回的是键盘代码;
        + keypress：在键盘上按下一个按键，并产生一个字符时发生, 返回ASCII码。注意: shift、alt、ctrl等键按下并不会产生字符，所以监听无效 ,换句话说, 只有按下能在屏幕上输出字符的按键时keypress事件才会触发。若一直按着某按键则会不断触发。
        + keyup：用户松开某一个按键时触发, 与keydown相对, 返回键盘代码.
        > 常用用法举例
        
        案例1：获取按键代码或者字符的ASCII码
        ```js
            $(window).keydown( function(event){
                //获取事件对象，里面包含各种有用的信息。
                console.log(event);
                //console.log(event.which);
                // 通过event.which可以拿到按键代码.  如果是keypress事件中,则拿到ASCII码.
            } );
        ```
        案例2：传递数据给事件处理函数
        ```js
           jQueryObject.keypress( [[ data ,]  handler ] ); 
        ```
        +  data: 通过event.data传递给事件处理函数的任意数据;
        + handler: 指定的事件处理函数;
        ```js
            // 只允许按下的字母键生效, 65~90是所有大写字母的键盘代码范围.
            var validKeys = { start: 65, end: 90  };
            $("#keys").keypress( validKeys, function(event){
                var keys = event.data;  //拿到validKeys对象.
                return event.which >= keys.start && event.which <= keys.end;
            } );

            <!-- 分割线------------------------------- -->

            $(window).keypress(function(event){
            //event.which是获取ASCII码，前面的函数是将ASCII码转换成字符，空格键和Enter键输出均为空白。
            console.log(String.fromCharCode(event.which));
            //从event对象中key属性获取字符，但是Enter键的key值为"Enter"，空白键还是空白" "。
            console.log(event.key);
        });
        ```
        window.onload = function(){} 用于整个网页（包括图片等）加载完毕后执行方法内代码块。

        $(document).ready(function(){}) 用于 DOM 结构加载完毕后就可以执行方法内代码块，由此得出，onload 是在 ready 后执行。

    


## jQuery效果
### jQuery隐藏/显示
#### jQuery hide() 和 show()
```js
$("#hide").click(function(){
  $("p").hide();
});
 
$("#show").click(function(){
  $("p").show();
});
```
语法：
```js
$(selector).hide(speed,callback);

$(selector).show(speed,callback);   

```
可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

下面的例子演示了带有 speed 参数的 hide() 方法：
```js
$("button").click(function(){
  $("p").hide(1000);
});
```
下面的例子演示了带有 speed 参数的 hide() 方法，并使用回调函数：
```js
$(document).ready(function(){
  $(".hidebtn").click(function(){
    $("div").hide(1000,"linear",function(){
      alert("Hide() 方法已完成!");
    });
  });
});
```
第二个参数是一个字符串，表示过渡使用哪种缓动函数。（译者注：jQuery自身提供"linear" 和 "swing"，其他可以使用相关的插件）。

#### jQuery toggle()
通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。

显示被隐藏的元素，并隐藏已显示的元素：
```js
$("button").click(function(){
  $("p").toggle();
});
```
语法：
```js
$(selector).toggle(speed,callback);
```
可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

#### 笔记
对于可选的callback参数，以下

1 $(select)选中的元素个数为n个，则callback函数会执行n次；

2 callback函数名后加括号，会立刻先执行此函数，且只会调用一次，而不是等到显示/隐藏完成后才执行，如果不加括号，会等到元素显示或隐藏后调用函数，并且调用多次；

3 callback既可以是函数名，也可以是匿名函数

```js
$(document).ready(function(){
  $(".hidebtn").click(function(){
    $("div").hide(1000, "linear", add());
      // 只需要记住 有括号就先执行括号里面的,就跟我们数学基础运算一样
  });
});
    
function  add() {
    alert("Hide() 方法已完成!");
}

//add()加上括号 add是执行函数,直接执行
//若是 add 那么则可以理解为把add当作参数,由click函数调用add函数

<!-- 分割线------------------------------- -->

// 加上 () 的时候，div还没有隐藏就会先执行函数内的代码了。
$(document).ready(function(){
  $(".hidebtn").click(function(){
    // popalert 不加括号() 
    $("div").hide(1000,"linear",popalert)
  });
});
function popalert(){
  alert("Hide() 方法已完成!"); 
}
```

### jQuery淡入淡出
#### jQuery fadeIn() 方法
jQuery fadnIn() 用于淡入已隐藏的元素

语法：
```js
$(selector).fideIn(speed,callback);
```
可选的speed参数规定效果的时长。他可以取以下值："slow"、"fast"或毫秒。

可选的callback参数是fading完成后所执行的函数名称。

下面的例子演示了带有不同参数的fadeIn()方法：

```js
$("button").click(function(){
  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeIn(3000);
});
```

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js">
</script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("#div1").fadeIn();
    $("#div2").fadeIn("slow");
    $("#div3").fadeIn(3000);
  });
});
</script>
</head>

<body>
<p>以下实例演示了 fadeIn() 使用了不同参数的效果。</p>
<button>点击淡入 div 元素。</button>
<br><br>
<div id="div1" style="width:80px;height:80px;display:none;background-color:red;"></div><br>
<div id="div2" style="width:80px;height:80px;display:none;background-color:green;"></div><br>
<div id="div3" style="width:80px;height:80px;display:none;background-color:blue;"></div>

</body>
</html>
```

#### jQuery fadeOut()方法

jQuery fadeOut()方法用于淡出可见元素

语法：

```js
$(selector).fadeIn(speed,callback);
```

可选的speed参数规定效果时长，他可以取以下值："slow"、"fast"或毫秒。

可选的callback参数是fading完成后所执行的函数名称。

下面的例子演示了带有不同参数的fadeIn()方法：
```js
$("button").click(function(){
  $("#div1").fadeIn();
  $("#div2").fadeIn("slow");
  $("#div3").fadeIn(3000);
});
```
#### jQuery fadeToggle()方法
jQuery fadeToggle() 方法可以在fadeIn()和fadeOut() 方法中进行切换。

如果元素已淡出，则fadeToggle()会向元素添加淡入效果。

如果元素已淡入，则fadeToggle()会向元素添加淡出效果

语法：
```
$(selector).fadeToggle(speed,callback);
```
可选的speed参数规定效果时长，他可以取以下值："slow"、"fast"或毫秒。

可选的callback参数是fading完成后所执行的函数名称。

下面的例子演示了带有不同参数的fadeToggle()方法：
```js
$("button").click(function(){
  $("#div1").fadeToggle();
  $("#div2").fadeToggle("slow");
  $("#div3").fadeToggle(3000);
});
```
#### jQuery fadeTo()方法
jQuery fadeTo()方法允许渐变为给定的不透明度（值介于0与1之间）

语法：
```
$(selector).fadeTo(speed,opacity,callback);
```
必需的speed参数规定效果的时长。他可以取以下值:"slow"、"fast"或毫秒。

fadeTo()方法中必需的opacity参数将淡入淡出效果设置为给定的不透明度（值介于0与1）之间。

可选的callback参数是该函数完成执行后所执行的函数名称。

下面的例子演示了带有不同参数的fadeTo()方法：
```js
$("button").click(function(){
  $("#div1").fadeTo("slow",0.15);
  $("#div2").fadeTo("slow",0.4);
  $("#div3").fadeTo("slow",0.7);
});
```
#### 笔记

1 注意大小写，fadeIn()   fadeOut()   fadeToggle()   fadeTo()  大小写不能变。

### jQuery 滑动

jQuery 滑动方法可使元素上下滑动

#### 实例

[jQuery slideDown()](https://www.runoob.com/try/try.php?filename=tryjquery_slide_down)
演示 jQuery slideDown() 方法。

[jQuery slideUp()](https://www.runoob.com/try/try.php?filename=tryjquery_slide_up)
演示 jQuery slideUp() 方法。

[jQuery slideToggle()](https://www.runoob.com/try/try.php?filename=tryjquery_slide_toggle)
演示 jQuery slideToggle() 方法。

#### jQuery 滑动方法

通过 jQuery，您可以在元素上创建滑动效果。

jQuery 拥有以下滑动方法：

- slideDown()
- slideUp()
- slideToggle()

##### jQuery slideDown() 方法

jQuery slideDown() 方法用于向下滑动元素

**语法：**

```
$(selector).slideDown(speed,callback);
```

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。

下面的例子演示了 slideDown() 方法：

**实例：**

```js

$("#flip").click(function(){
  $("#panel").slideDown();
});

```

[点击尝试一下？](https://www.runoob.com/try/try.php?filename=tryjquery_slide_down)

##### jQuery slideToggle() 方法

jQuery slideUp() 方法用于向上滑动元素。

**语法：**

```
$(selector).slideUp(speed,callback);
```

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。

下面的例子演示了 slideUp() 方法：

**实例：**

```js

$("#flip").click(function(){
  $("#panel").slideUp();
});

```

[点击尝试一下？](https://www.runoob.com/try/try.php?filename=tryjquery_slide_up)

##### jQuery slideToggle()方法

jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

如果元素向下滑动，则 slideToggle() 可向上滑动它们。

如果元素向上滑动，则 slideToggle() 可向下滑动它们。

**语法：**

```
$(selector).slideToggle(speed,callback);
```

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。

下面的例子演示了 slideToggle() 方法：

**实例：**

```js

$("#flip").click(function(){
  $("#panel").slideToggle();
});

```

[点击尝试一下？](https://www.runoob.com/try/try.php?filename=tryjquery_slide_toggle)

### jQuery 动画

jQuery animate() 方法允许您创建自定义的动画。

#### jQuery 动画 - animate() 方法

jQuery animate() 方法用于创建自定义动画。

**语法：**

```
$(selector).animate({params},speed,callback);
```

必需的 params 参数定义形成动画的 CSS 属性。

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是动画完成后所执行的函数名称。

下面的例子演示 animate() 方法的简单应用。它把 <div> 元素往右边移动了 250 像素：

**实例：**

```js

$("button").click(function(){
  $("div").animate({left:'250px'});
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_animation1)

> **提示**  默认情况下，所有 HTML 元素都有一个静态位置，且无法移动。
            如需对位置进行操作，要记得首先把元素的 CSS position 属性设置为 relative、fixed 或 absolute

#### jQuery animate() - 操作多个属性

请注意，生成动画的过程中可同时使用多个属性：

**实例：**

```js

$("button").click(function(){
  $("div").animate({
    left:'250px',
    opacity:'0.5',
    height:'150px',
    width:'150px'
  });
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_animation1_multicss)

>  **可以用 animate() 方法来操作所有 CSS 属性吗？**
>> 是的，几乎可以！不过，需要记住一件重要的事情：当使用 animate() 时，必须使用 Camel 标记法书写所有的属性名，比如，必须使用 paddingLeft 而不是 padding-left，使用 marginRight 而不是 margin-right，等等。
同时，色彩动画并不包含在核心 jQuery 库中。
如果需要生成颜色动画，您需要从 [jquery.com](https://jquery.com/download/) 下载 [颜色动画](https://plugins.jquery.com/color/) 插件。

#### jQuery animate() - 使用相对值

也可以定义相对值（该值相对于元素的当前值）。需要在值的前面加上 += 或 -=：

**实例：**

```js

$("button").click(function(){
  $("div").animate({
    left:'250px',
    height:'+=150px',
    width:'+=150px'
  });
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_animation1_relative)

#### jQuery animate() - 使用预定义的值

可以把属性的动画值设置为 "show"、"hide" 或 "toggle"：

**实例：**

```js

$("button").click(function(){
  $("div").animate({
    height:'toggle'
  });
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_animation1_toggle)

#### jQuery animate() - 使用队列功能

默认地，jQuery 提供针对动画的队列功能。

这意味着如果您在彼此之后编写多个 animate() 调用，jQuery 会创建包含这些方法调用的"内部"队列。然后逐一运行这些 animate 调用。

**实例1：**

```js

$("button").click(function(){
  var div=$("div");
  div.animate({height:'300px',opacity:'0.4'},"slow");
  div.animate({width:'300px',opacity:'0.8'},"slow");
  div.animate({height:'100px',opacity:'0.4'},"slow");
  div.animate({width:'100px',opacity:'0.8'},"slow");
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_animation)

下面的例子把 `<div>` 元素往右边移动了 100 像素，然后增加文本的字号：

**实例2：**

```js

$("button").click(function(){
  var div=$("div");
  div.animate({left:'100px'},"slow");
  div.animate({fontSize:'3em'},"slow");
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_animation2)




## jQuery  HTML

### jQuery捕获

#### jQuery - 获取内容和属性

> jQuery 拥有可操作HTML元素和属性的强大方法。

#### jQuery DOM操作

jQuery中非常重要的部分，就是操作DOM的能力。
jQuery提供一系列与DOM相关的方法，这使访问和操作元素和属性变得很容易。

> DOM = Document Object Model (文档对象模型)
>> DOM定义访问HTML和XML文档的标准：
  "W3C文档对象模型独立于平台和语言的界面，允许程序和脚本动态访问和更新文档的内容、结构以及样式。"

#### 获得内容 - text()、 html() 以及 val()

三个简单实用的用于DOM操作的jQuery 方法

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括HTML标记）
- val() - 设置或返回表单字段的值

下面的例子演示如何通过jQuery text() 和 html() 方法来获得内容：

**实例**

```js

$("#btn1").click(function(){
  alert("Text: " + $("#test").text());
});
$("#btn2").click(function(){
  alert("HTML: " + $("#test").html());
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_html_get)

下面的例子演示如何通过 jQuery val() 方法获得输入字段的值：

**实例**

```js

$("#btn1").click(function(){
  alert("值为: " + $("#test").val());
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_val_get)

#### 笔记

attr 和 prop 的区别介绍：

对于 HTML 元素本身就带有的固有属性，在处理时，使用 prop 方法。

对于 HTML 元素我们自己自定义的 DOM 属性，在处理时，使用 attr 方法。

**实例 1：**

```js
<a href="https://www.runoob.com" target="_self" class="btn">菜鸟教程</a>
```

这个例子里 ```<a>``` 元素的 DOM 属性有: href、target 和 class，这些属性就是 ```<a> ```元素本身就带有的属性，也是 W3C 标准里就包含有这几个属性，或者说在 IDE 里能够智能提示出的属性，这些就叫做固有属性。处理这些属性时，建议使用 prop 方法。

```js
<a href="#" id="link1" action="delete" rel="nofollow">删除</a>
```

这个例子里 ```<a>``` 元素的 DOM 属性有: href、id 和 action，很明显，前两个是固有属性，而后面一个 action 属性是我们自己自定义上去的，```<a>``` 元素本身是没有这个属性的。这种就是自定义的 DOM 属性。处理这些属性时，建议使用 attr 方法。

prop()函数的结果:

      1.如果有相应的属性，返回指定属性值。

      2.如果没有相应的属性，返回值是空字符串。

attr()函数的结果:

      1.如果有相应的属性，返回指定属性值。

      2.如果没有相应的属性，返回值是 undefined。

对于HTML元素本身就带有的固有属性，在处理时，使用prop方法。

对于HTML元素我们自己自定义的DOM属性，在处理时，使用 attr 方法。

具有 true 和 false 两个属性的属性，如 checked, selected 或者 disabled 使用prop()

### jQuery设置

#### jQuery - 设置内容和属性

#### 设置内容 - text()、 html()以及 val()

使用上一小节中三个相同的方法来设置内容：

- text() - 设置或返回所选元素的文本内容
- html() - 设置或返回所选元素的内容（包括HTML标记）
- val() - 设置或返回表单字段的值

下面的例子演示如何通过 text()、html() 以及 val() 方法来设置内容：

**实例**

```js

$("#btn1").click(function(){
    $("#test1").text("Hello world!");
});
$("#btn2").click(function(){
    $("#test2").html("<b>Hello world!</b>");
});
$("#btn3").click(function(){
    $("#test3").val("RUNOOB");
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_html_set)

#### text()、 html()以及 val()的回调函数

上面的三个 jQuery 方法：text()、html() 以及 val()，同样拥有回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

下面的例子演示带有回调函数的 text() 和 html()：

**实例**

```js

$("#btn1").click(function(){
    $("#test1").text(function(i,origText){
        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")"; 
    });
});
 
$("#btn2").click(function(){
    $("#test2").html(function(i,origText){
        return "旧 html: " + origText + " 新 html: Hello <b>world!</b> (index: " + i + ")"; 
    });
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_html_callback)

#### 设置属性 - attr()

jQuery attr() 方法也用于设置/改变属性值。

下面的例子演示如何改变（设置）链接中 href 属性的值：

**实例**

```js

$("button").click(function(){
  $("#runoob").attr("href","http://www.runoob.com/jquery");
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_attr_set)

attr() 方法也允许您同时设置多个属性。

下面的例子演示如何同时设置 href 和 title 属性：

**实例**

```js

$("button").click(function(){
    $("#runoob").attr({
        "href" : "http://www.runoob.com/jquery",
        "title" : "jQuery 教程"
    });
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_attr_set2)

#### attr()的回调函数

jQuery 方法 attr()，也提供回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

下面的例子演示带有回调函数的 attr() 方法：

**实例**

```js

$("button").click(function(){
  $("#runoob").attr("href", function(i,origValue){
    return origValue + "/jquery"; 
  });
});

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_dom_attr_callback)

### jQuery - 添加元素

#### 添加新的 HTML 内容

添加新内容的四个 jQuery 方法

- append() - 在被选元素的结尾插入内容
- prepend() - 在被选元素的开头插入内容
- after() - 在被选元素之后插入内容
- before() - 在被选元素之前插入内容

#### jQuery append() 方法

jQuery append() 方法在被选元素的结尾插入内容（仍然在该元素的内部）。

**实例**

```js
$("p").append("追加文本");
```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_html_append)

#### jQuery prepend() 方法

jQuery prepend() 方法在被选元素的开头插入内容。

**实例**

```js
$("p").prepend("在开头追加文本");
```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_html_prepend)

#### 通过 append() 和 prepend() 方法添加若干新元素

在上面的例子中，我们只在被选元素的开头/结尾插入文本/HTML。

不过，append() 和 prepend() 方法能够通过参数接收无限数量的新元素。可以通过 jQuery 来生成文本/HTML（就像上面的例子那样），或者通过 JavaScript 代码和 DOM 元素。

在下面的例子中，我们创建若干个新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 append() 方法把这些新元素追加到文本中（对 prepend() 同样有效）：

**实例**

```js

function appendText(){
    var txt1="<p>文本-1。</p>";              // 使用 HTML 标签创建文本
    var txt2=$("<p></p>").text("文本-2。");  // 使用 jQuery 创建文本
    var txt3=document.createElement("p");
    txt3.innerHTML="文本-3。";               // 使用 DOM 创建文本 text with DOM
    $("body").append(txt1,txt2,txt3);        // 追加新元素
}

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_html_append2)

#### jQuery after() 和 before() 方法

jQuery after() 方法在被选元素之后插入内容。

jQuery before() 方法在被选元素之前插入内容。

**实例**
```js

$("img").after("在后面添加文本");
 
$("img").before("在前面添加文本");

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_html_after)

#### 通过 after() 和 before() 方法添加若干新元素

after() 和 before() 方法能够通过参数接收无限数量的新元素。可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建新元素。

在下面的例子中，我们创建若干新元素。这些元素可以通过 text/HTML、jQuery 或者 JavaScript/DOM 来创建。然后我们通过 after() 方法把这些新元素插到文本中（对 before() 同样有效）：

**实例**

```js

function afterText()
{
    var txt1="<b>I </b>";                    // 使用 HTML 创建元素
    var txt2=$("<i></i>").text("love ");     // 使用 jQuery 创建元素
    var txt3=document.createElement("big");  // 使用 DOM 创建元素
    txt3.innerHTML="jQuery!";
    $("img").after(txt1,txt2,txt3);          // 在图片后添加文本
}

```

**备注**
参数也可以是array，数组的形式

```js

function afterText(){
    var txt1="<b>I </b>";                    // 使用 HTML 创建元素
    var txt2=$("<i></i>").text("love ");     // 使用 jQuery 创建元素
    var txt3=document.createElement("big");  // 使用 DOM 创建元素
    txt3.innerHTML="jQuery!";
    $("img").after([txt1,txt2,txt3]);          // 在图片后添加文本
}

```

[尝试一下>>](https://www.runoob.com/try/try.php?filename=tryjquery_html_after2)

#### 笔记

那有木有考虑过append/prepend和after/before有什么区别呢？

**append**

```js

<p>
  <span class="s1">s1</span>
</p>
<script>
$("p").append('<span class="s2">s2</span>');
</script>

```
结果是这样的:
```js

<p>
  <span class="s1">s1</span>
  <span class="s2">s2</span>
</p>

```

**after**

```js

<p>
  <span class="s1">s1</span>
</p>
<script>
$("p").after('<span class="s2">s2</span>');
</script>

```
结果是这样的
```js

<p>
  <span class="s1">s1</span>
</p>
<span class="s2">s2</span>

```

**总结：**

append/prepend 是在选择元素内部嵌入。

after/before 是在元素外面追加。

### jQuery删除元素





## jQuery  遍历

## jQuery  Ajax

## jQuery  其他

## jQuery  实例

## jQuery参考手册

### jQuery选择器

| 选择器                     | 实例                           | 选取                                                                                         |
|:---------------------------|:-------------------------------|:---------------------------------------------------------------------------------------------|
| *                          | $("*")                         | 所有元素                                                                                     |
| #id                        | $("#lastname")                 | id="lastname" 的元素                                                                         |
| .class                     | $(".intro")                    | class="intro" 的所有元素                                                                     |
| .class,.class              | $(".intro,.demo")              | class 为 "intro" 或 "demo" 的所有元素                                                        |
| element                    | $("p")                         | 所有 ```<p>``` 元素                                                                          |
| el1,el2,el3                | $("h1,div,p")                  | 所有 ```<h1>```、```<div>``` 和``` <p>``` 元素                                                |
|                            |                                |                                                                                              |
| :first                     | $("p:first")                   | 第一个 ```<p>``` 元素                                                                        |
| :last                      | $("p:last")                    | 最后一个 ```<p>``` 元素                                                                      |
| :even                      | $("tr:even")                   | 所有偶数``` <tr>``` 元素，索引值从 0 开始，第一个元素是偶数 (0)，第二个元素是奇数 (1)，以此类推。 |
| :odd                       | $("tr:odd")                    | 所有奇数 ```<tr>``` 元素，索引值从 0 开始，第一个元素是偶数 (0)，第二个元素是奇数 (1)，以此类推。 |
|                            |                                |                                                                                              |
| :first-child               | $("p:first-child")             | 属于其父元素的第一个子元素的所有 ```<p>``` 元素                                              |
| :first-of-type             | $("p:first-of-type")           | 属于其父元素的第一个 ```<p>``` 元素的所有 ```<p>``` 元素                                     |
| :last-child                | $("p:last-child")              | 属于其父元素的最后一个子元素的所有 ```<p>``` 元素                                            |
| :last-of-type              | $("p:last-of-type")            | 属于其父元素的最后一个 ```<p>``` 元素的所有 ```<p>``` 元素                                   |
| :nth-child(n)              | $("p:nth-child(2)")            | 属于其父元素的第二个子元素的所有 ```<p>``` 元素                                              |
| :nth-last-child(n)         | $("p:nth-last-child(2)")       | 属于其父元素的第二个子元素的所有 ```<p>``` 元素，从最后一个子元素开始计数                     |
| :nth-of-type(n)            | $("p:nth-of-type(2)")          | 属于其父元素的第二个 <p> 元素的所有 <p> 元素                                                 |
| :nth-last-of-type(n)       | $("p:nth-last-of-type(2)")     | 属于其父元素的第二个 ```<p>``` 元素的所有 ```<p>``` 元素，从最后一个子元素开始计数            |
| :only-child                | $("p:only-child")              | 属于其父元素的唯一子元素的所有 ```<p>``` 元素                                                |
| :only-of-type              | $("p:only-of-type")            | 属于其父元素的特定类型的唯一子元素的所有 ```<p>``` 元素                                      |
|                            |                                |                                                                                              |
| parent > child             | $("div > p")                   | ```<div>``` 元素的直接子元素的所有 ```<p>``` 元素                                            |
| parent descendant          | $("div p")                     | ```<div>``` 元素的后代的所有 ```<p>``` 元素                                                  |
| element + next             | $("div + p")                   | 每个 ```<div>``` 元素相邻的下一个 ```<p>``` 元素                                             |
| element ~ siblings         | $("div ~ p")                   | ```<div>``` 元素同级的所有 ```<p>``` 元素                                                    |
|                            |                                |                                                                                              |
| :eq(index)                 | $("ul li:eq(3)")               | 列表中的第四个元素（index 值从 0 开始）                                                        |
| :gt(no)                    | $("ul li:gt(3)")               | 列举 index 大于 3 的元素                                                                     |
| :lt(no)                    | $("ul li:lt(3)")               | 列举 index 小于 3 的元素                                                                     |
| :not(selector)             | $("input:not(:empty)")         | 所有不为空的输入元素                                                                         |
|                            |                                |                                                                                              |
| :header                    | $(":header")                   | 所有标题元素 ```<h1>```, ```<h2>``` ...                                                      |
| :animated                  | $(":animated")                 | 所有动画元素                                                                                 |
| :focus                     | $(":focus")                    | 当前具有焦点的元素                                                                           |
| :contains(text)            | $(":contains('Hello')")        | 所有包含文本 "Hello" 的元素                                                                  |
| :has(selector)             | $("div:has(p)")                | 所有包含有 ```<p>``` 元素在其内的 ```<div>``` 元素                                           |
| :empty                     | $(":empty")                    | 所有空元素                                                                                   |
| :parent                    | $(":parent")                   | 匹配所有含有子元素或者文本的父元素。                                                          |
| :hidden                    | $("p:hidden")                  | 所有隐藏的 ```<p>``` 元素                                                                    |
| :visible                   | $("table:visible")             | 所有可见的表格                                                                               |
| :root                      | $(":root")                     | 文档的根元素                                                                                 |
| :lang(language)            | $("p:lang(de)")                | 所有 lang 属性值为 "de" 的 ```<p>``` 元素                                                    |
|                            |                                |                                                                                              |
| [attribute]                | $("[href]")                    | 所有带有 href 属性的元素                                                                     |
| [attribute=value]          | $("[href='default.htm']")      | 所有带有 href 属性且值等于 "default.htm" 的元素                                              |
| [attribute!=value]         | $("[href!='default.htm']")     | 所有带有 href 属性且值不等于 "default.htm" 的元素                                            |
| [attribute$=value]         | \$("[href$='.jpg']")           | 所有带有 href 属性且值以 ".jpg" 结尾的元素                                                   |
| [attribute\|=value]        | $("[title\|='Tomorrow']")      | 所有带有 title 属性且值等于 'Tomorrow' 或者以 'Tomorrow' 后跟连接符作为开头的字符串          |
| [attribute^=value]         | $("[title^='Tom']")            | 所有带有 title 属性且值以 "Tom" 开头的元素                                                   |
| [attribute~=value]         | $("[title~='hello']")          | 所有带有 title 属性且值包含单词 "hello" 的元素                                               |
| [attribute*=value]         | $("[title*='hello']")          | 所有带有 title 属性且值包含字符串 "hello" 的元素                                             |
| [name=value][name2=value2] | \$( "input[id][name$='man']" ) | 带有 id 属性，并且 name 属性以 man 结尾的输入框                                               |
| :input                     | $(":input")                    | 所有 input 元素                                                                              |
| :text                      | $(":text")                     | 所有带有 type="text" 的 input 元素                                                           |
| :password                  | $(":password")                 | 所有带有 type="password" 的 input 元素                                                       |
| :radio                     | $(":radio")                    | 所有带有 type="radio" 的 input 元素                                                          |
| :checkbox                  | $(":checkbox")                 | 所有带有 type="checkbox" 的 input 元素                                                       |
| :submit                    | $(":submit")                   | 所有带有 type="submit" 的 input 元素                                                         |
| :reset                     | $(":reset")                    | 所有带有 type="reset" 的 input 元素                                                          |
| :button                    | $(":button")                   | 所有带有 type="button" 的 input 元素                                                         |
| :image                     | $(":image")                    | 所有带有 type="image" 的 input 元素                                                          |
| :file                      | $(":file")                     | 所有带有 type="file" 的 input 元素                                                           |
| :enabled                   | $(":enabled")                  | 所有启用的元素                                                                               |
| :disabled                  | $(":disabled")                 | 所有禁用的元素                                                                               |
| :selected                  | $(":selected")                 | 所有选定的下拉列表元素                                                                       |
| :checked                   | $(":checked")                  | 所有选中的复选框选项                                                                         |
| .selector                  | $(selector).selector           | ==在jQuery 1.7中已经不被赞成使用==返回传给jQuery()的原始选择器                               |
| :target                    | $( "p:target" )                | 选择器将选中ID和URI中一个格式化的标识符相匹配的`<p>`元素                                     |

#### 笔记

1. 基本选择器

    ```js
    $("#id")            //ID选择器
    $("div")            //元素选择器
    $(".classname")     //类选择器
    $(".classname,.classname1,#id1")     //组合选择器
    ```

2. 层次选择器

    ```js
    $("#id>.classname ")    //子元素选择器
    $("#id .classname ")    //后代元素选择器
    $("#id + .classname ")    //紧邻下一个元素选择器
    $("#id ~ .classname ")    //兄弟元素选择器
    ```

3. 过滤选择器（重点）
    ```js
    $("li:first")    //第一个li
    $("li:last")     //最后一个li
    $("li:even")     //挑选下标为偶数的li
    $("li:odd")      //挑选下标为奇数的li
    $("li:eq(4)")    //下标等于 4 的li(第五个 li 元素)
    $("li:gt(2)")    //下标大于 2 的li
    $("li:lt(2)")    //下标小于 2 的li
    $("li:not(#runoob)") //挑选除 id="runoob" 以外的所有li
    ```

    3.2. 内容过滤选择器

    ```js
    $("div:contains('Runob')")    // 包含 Runob文本的元素
    $("td:empty")                 //不包含子元素或者文本的空元素
    $("div:has(selector)")        //含有选择器所匹配的元素
    $("td:parent")                //含有子元素或者文本的元素
    ```

    3.3. 可见性过滤选择器

    ```js
    $("li:hidden")       //匹配所有不可见元素，或type为hidden的元素
    $("li:visible")      //匹配所有可见元素
    ```

    3.4. 属性过滤选择器

    ```js
    $("div[id]")        //所有含有 id 属性的 div 元素
    $("div[id='123']")        // id属性值为123的div 元素
    $("div[id!='123']")        // id属性值不等于123的div 元素
    $("div[id^='qq']")        // id属性值以qq开头的div 元素
    $("div[id$='zz']")        // id属性值以zz结尾的div 元素
    $("div[id*='bb']")        // id属性值包含bb的div 元素
    $("input[id][name$='man']") //多属性选过滤，同时满足两个属性的条件的元素
    ```

    3.5. 状态过滤选择器

    ```js
    $("input:enabled")    // 匹配可用的 input
    $("input:disabled")   // 匹配不可用的 input
    $("input:checked")    // 匹配选中的 input
    $("option:selected")  // 匹配选中的 option
    ```
4. 表单选择器 
    ```js
    $(":input")      //匹配所有 input, textarea, select 和 button 元素
    $(":text")       //所有的单行文本框，$(":text") 等价于$("[type=text]")，推荐使用$("input:text")效率更高，下同
    $(":password")   //所有密码框
    $(":radio")      //所有单选按钮
    $(":checkbox")   //所有复选框
    $(":submit")     //所有提交按钮
    $(":reset")      //所有重置按钮
    $(":button")     //所有button按钮
    $(":file")       //所有文件域
    ```

### jQuery事件方法

事件方法触发器或添加一个函数到被选元素的事件处理程序。

下面的表格列出了所有用于处理事件的 jQuery 方法

| 方法                                  | 描述                                                                      |
|---------------------------------------|-------------------------------------------------------------------------|
| bind()                                | 向元素添加事件处理程序                                                    |
| blur()                                | 添加/触发失去焦点事件                                                     |
| change()                              | 添加/触发 change 事件                                                     |
| click()                               | 添加/触发 click （单击）事件                                                |
| dblclick()                            | 添加/触发 double click （双击）事件                                         |
| delegate()                            | 向匹配元素的当前或未来的子元素添加处理程序                                |
| die()                                 | ==在版本 1.9 中被移除。== 移除所有通过 live() 方法添加的事件处理程序       |
| error()                               | ==在版本 1.8 中被废弃。== 添加/触发 error 事件                             |
| event.currentTarget                   | 在事件冒泡阶段内的当前 DOM 元素                                           |
| event.data                            | 包含当前执行的处理程序被绑定时传递到事件方法的可选数据                    |
| event.delegateTarget                  | 返回当前调用的 jQuery 事件处理程序所添加的元素                            |
| event.isDefaultPrevented()            | 返回指定的 event 对象上是否调用了 event.preventDefault()                  |
| event.isImmediatePropagationStopped() | 返回指定的 event 对象上是否调用了 event.stopImmediatePropagation()        |
| event.isPropagationStopped()          | 返回指定的 event 对象上是否调用了 event.stopPropagation()                 |
| event.namespace                       | 返回当事件被触发时指定的命名空间                                          |
| event.pageX                           | 返回相对于文档左边缘的鼠标位置                                            |
| event.pageY                           | 返回相对于文档上边缘的鼠标位置                                            |
| event.preventDefault()                | 阻止事件的默认行为                                                        |
| event.relatedTarget                   | 返回当鼠标移动时哪个元素进入或退出                                        |
| event.result                          | 包含由被指定事件触发的事件处理程序返回的最后一个值                        |
| event.stopImmediatePropagation()      | 阻止其他事件处理程序被调用                                                |
| event.stopPropagation()               | 阻止事件向上冒泡到 DOM 树，阻止任何父处理程序被事件通知                    |
| event.target                          | 返回哪个 DOM 元素触发事件                                                 |
| event.timeStamp                       | 返回从 1970 年 1 月 1 日到事件被触发时的毫秒数                            |
| event.type                            | 返回哪种事件类型被触发                                                    |
| event.which                           | 返回指定事件上哪个键盘键或鼠标按钮被按下                                  |
| event.metaKey                         | 事件触发时 META 键是否被按下                                              |
| focus()                               | 添加/触发 focus 事件                                                      |
| focusin()                             | 添加事件处理程序到 focusin 事件                                           |
| focusout()                            | 添加事件处理程序到 focusout 事件                                          |
| hover()                               | 添加两个事件处理程序到 hover 事件                                         |
| keydown()                             | 添加/触发 keydown 事件                                                    |
| keypress()                            | 添加/触发 keypress 事件                                                   |
| keyup()                               | 添加/触发 keyup 事件                                                      |
| live()                                | ==在版本 1.9 中被移除。== 添加一个或多个事件处理程序到当前或未来的被选元素 |
| load()                                | ==在版本 1.8 中被废弃。== 添加一个事件处理程序到 load 事件                 |
| mousedown()                           | 添加/触发 mousedown 事件                                                  |
| mouseenter()                          | 添加/触发 mouseenter 事件                                                 |
| mouseleave()                          | 添加/触发 mouseleave 事件                                                 |
| mousemove()                           | 添加/触发 mousemove 事件                                                  |
| mouseout()                            | 添加/触发 mouseout 事件                                                   |
| mouseover()                           | 添加/触发 mouseover 事件                                                  |
| mouseup()                             | 添加/触发 mouseup 事件                                                    |
| off()                                 | 移除通过 on() 方法添加的事件处理程序                                      |
| on()                                  | 向元素添加事件处理程序                                                    |
| one()                                 | 向被选元素添加一个或多个事件处理程序。该处理程序只能被每个元素触发一次     |
| $.proxy()                             | 接受一个已有的函数，并返回一个带特定上下文的新的函数                       |
| ready()                               | 规定当 DOM 完全加载时要执行的函数                                         |
| resize()                              | 添加/触发 resize 事件                                                     |
| scroll()                              | 添加/触发 scroll 事件                                                     |
| select()                              | 添加/触发 select 事件                                                     |
| submit()                              | 添加/触发 submit 事件                                                     |
| toggle()                              | ==在版本 1.9 中被移除。== 添加 click 事件之间要切换的两个或多个函数        |
| trigger()                             | 触发绑定到被选元素的所有事件                                              |
| triggerHandler()                      | 触发绑定到被选元素的指定事件上的所有函数                                  |
| unbind()                              | 从被选元素上移除添加的事件处理程序                                        |
| undelegate()                          | 从现在或未来的被选元素上移除事件处理程序                                  |
| unload()                              | ==在版本 1.8 中被废弃。== 添加事件处理程序到 unload 事件                   |
| contextmenu()                         | 添加事件处理程序到 contextmenu 事件                                       |
| $.holdReady()                         | 用于暂停或恢复.ready() 事件的执行                                         |

#### 笔记
对于由 jQuery 动态生成的元素，如用 jQuery 给元素添加 class，或者直接添加一对 p 标签，不能直接绑定常用的事件，如 click。因为这些元素属于动态生成，除非采用 noclick 内联的形式。那么解决办法是使用 live 和 on 事件方法。

注意，jquery 1.7.2 之后的版本不建议使用 live。
例如：
```js
$(".box ").click(function(){});
```
类名为 box 的元素是由 jquery 动态生成，以上写法将会无效，那么可以改为如下：
```js
$(".box ").live('click', function(){});
```
或者
```js
$(".box ").on('click', function(){});
```
另外 click, blur, keyup, change等方法，都可以这样解决。

### jQuery效果方法

下面的表格列出了所有用于创建动画效果的 jQuery 方法。

| 方法          | 描述                                       |
|:--------------|:-----------------------------------------|
| animate()     | 对被选元素应用“自定义”的动画               |
| clearQueue()  | 对被选元素移除所有排队函数（仍未运行的）     |
| delay()       | 对被选元素的所有排队函数（仍未运行）设置延迟 |
| dequeue()     | 移除下一个排队函数，然后执行函数            |
| fadeln()      | 逐渐改变被选元素的不透明度，从隐藏到可见    |
| dadeOut()     | 逐渐改变被选元素的不透明度，从可见到隐藏    |
| fadeTo()      | 把被选元素逐渐改变至给定的不透明度         |
| fadeToggle()  | 在fadeIn()和fadeOut()方法之间进行切换      |
| finish()      | 对被选元素停止、移除并完成所有排队动画      |
| hide()        | 隐藏被选元素                               |
| queue()       | 显示被选元素的排队函数                     |
| show()        | 显示被选元素                               |
| slideDown()   | 通过调整高度来滑动显示被选元素             |
| slideToogle() | slideUp()和slideDown()方法之间的切换       |
| slideUp()     | 通过调整高度来滑动隐藏被选元素             |
| stop()        | 停止被选元素上当前正在运行的动画           |
| toggle()      | hide()和show()方法之间的切换               |

### jQueryHTML/CSS方法

下面的表格列出了所有用于处理 HTML 和 CSS 的 jQuery 方法。

下面的方法适用于 HTML 和 XML 文档。除了：html() 方法。

| 方法               | 描述                                              |
|--------------------|-------------------------------------------------|
| addClass()         | 向被选元素添加一个或多个类名                      |
| after()            | 在被选元素后插入内容                              |
| append()           | 在被选元素的结尾插入内容                          |
| appendTo()         | 在被选元素的结尾插入HTML元素                      |
| attr()             | 设置或返回被选元素的属性/值                       |
| before()           | 在被选元素前插入内容                              |
| clone()            | 生成被选元素的副本                                |
| css()              | 为被选元素设置或返回一个或多个样式属性            |
| detach()           | 移除被选元素（保留数据和事件）                      |
| empty()            | 从被选元素移除所有子节点和内容                    |
| hasClass()         | 检查被选元素是否包含指定的class名称               |
| height()           | 设置或返回被选元素的高度                          |
| html()             | 设置或返回被选元素的内容                          |
| innerHeight()      | 返回元素的高度（包含padding，不包含border）          |
| innerWidth()       | 返回元素的宽度（包含padding，不包含border）          |
| insertAfter()      | 在被选元素后插入HTML元素                          |
| insertBefore()     | 在被选元素前插入HTML元素                          |
| offset()           | 设置或返回被选元素的偏移坐标（相对于文档）          |
| offsetParent()     | 返回第一个定位的祖先元素                          |
| outerHeight()      | 返回元素的高度（包含padding和border）               |
| outerWidth()       | 返回元素的宽度（包含padding和border）               |
| position()         | 返回元素的位置（相对于父元素）                      |
| prepend()          | 在被选元素的开头插入内容                          |
| prependTo()        | 在被选元素的开头插入HTML元素                      |
| prop()             | 设置或返回被选元素的属性/值                       |
| remove()           | 移除被选元素（包含数据和事件）                      |
| removeAttr()       | 从被选元素移除一个或多个属性                      |
| removeClass()      | 从被选元素移除一个或多个类                        |
| removeProp()       | 移除通过prop()方法设置的属性                      |
| replaceAll()       | 把被选元素替换为新的HTML元素                      |
| replaceWith()      | 把被选元素替换为新的内容                          |
| scrollLeft()       | 设置或返回被选元素的水平滚动条位置                |
| scrollTop()        | 设置或返回被选元素的垂直滚动条位置                |
| text()             | 设置或返回被选元素的文本内容                      |
| toggleClass()      | 在被选元素中添加/移除一个或多个类之间切换         |
| unwrap()           | 移除被选元素的父元素                              |
| val()              | 设置或返回被选元素的属性值（针对表单元素）          |
| width()            | 设置或返回被选元素的宽度                          |
| wrap()             | 在每个被选元素的周围用HTML元素包裹起来            |
| wrapAll()          | 在所有被选元素的周围用HTML元素包裹起来            |
| wrapInner()        | 在每个被选元素的周围用HTML元素包裹起来            |
| $.escapeSelector() | 转义CSS选择器中有特殊意义的字符或字符串           |
| $.cssHooks         | 提供了一种方法通过定义函数来获取和设置特定的CSS值 |

### jQuery遍历方法

| 方法           | 描述                                                                           |
|----------------|------------------------------------------------------------------------------|
| add()          | 把元素添加到匹配元素的集合中                                                   |
| addBack()      | 把之前的元素集添加到当前集合中                                                 |
| andSelf()      | ==在版本1.8中被废弃。== addBack()的别名                                         |
| children()     | 返回被选元素的所有直接子元素                                                   |
| closest()      | 返回被选元素的第一个祖先元素                                                   |
| contents()     | 返回被选元素的所有直接子元素（包含文本和注释节点）                               |
| each()         | 为每个匹配元素执行函数                                                         |
| end()          | 结束当前链中最近的一次筛选操作，并把匹配元素集合返回到前一次的状态              |
| eq()           | 返回带有被选元素的指定索引号元素                                               |
| filter()       | 把匹配元素集合缩减为匹配选择器或匹配函数返回值得新元素                         |
| find()         | 返回被选元素的后代元素                                                         |
| first()        | 返回被选元素的第一个元素                                                       |
| has()          | 返回拥有一个或多个元素在其内的所有元素                                         |
| is()           | 根据选择器/元素/jQuery对象检查匹配元素集合，如果存在至少一个匹配元素，则返回true |
| last()         | 返回被选元素的最后一个元素                                                     |
| map()          | 把当前匹配集合中的每个元素传递给函数，产生包含返回值的新jQuery对象              |
| next()         | 返回被选元素的后一个同级元素                                                   |
| nextAll()      | 返回被选元素之后的所有同级元素                                                 |
| not()          | 从匹配元素集合中移除元素                                                       |
| offsetParent() | 返回第一个定位的父元素                                                         |
| parent()       | 返回被选元素的直接父元素                                                       |
| parents()      | 返回被选元素的所有祖先元素                                                     |
| parentsUntil() | 返回介于两个给定参数之间的所有祖先元素                                         |
| prev()         | 返回被选元素的前一个同级元素                                                   |
| prevAll()      | 返回被选元素之前的所有同级元素                                                 |
| prevUntil()    | 返回介于两个给定参数之间的每个元素之前的所有同级元素                           |
| sublings()     | 返回被选元素的所有同级元素                                                     |
| slice()        | 把匹配元素集合缩减为指定范围的子集                                             |

### jQueryAJAX方法

AJAX 是一种与服务器交换数据的技术，可以在不重新载入整个页面的情况下更新网页的一部分。

下面的表格列出了所有的 jQuery AJAX 方法：

| 方法              | 描述                                                                      |
|-------------------|-------------------------------------------------------------------------|
| $.ajax()          | 执行异步AJAX请求                                                          |
| $.ajaxPrefilter() | 在每个请求发送之前且被$.AJAX()处理之前，处理自定义Ajax选项或修改已存在选项 |
| $.ajaxSetup()     | 为将来的AJAX请求设置默认值                                                |
| $.ajaxTransport() | 创建处理Ajax数据实际传送的对象                                            |
| $.get()           | 使用AJAX的HTTP GET 请求从服务器加载数据                                   |
| $.getJSON()       | 使用HTTP GET 请求从服务器加载JSON编码的数据                               |
| $.getScript()     | 使用AJAX的HTTP GET 请求从服务器加载并执行Javascript                       |
| $.param()         | 创建数组或对象的序列化表示形式（可用于AJAX请求的URL查询字符串）             |
| $.post()          | 使用AJAX的HTTP POST 请求从服务器加载数据                                  |
| ajaxComplete()    | 规定AJAX请求完成时运行的函数                                              |
| ajaxError()       | 规定AJAX请求失败时运行的函数                                              |
| ajaxSend()        | 规定AJAX请求发送之前运行的函数                                            |
| ajaxStart()       | 规定第一个 AJAX 请求开始时运行的函数                                      |
| ajaxStop()        | 规定所有的 AJAX 请求完成时运行的函数                                      |
| ajaxSuccess()     | 规定 AJAX 请求成功完成时运行的函数                                        |
| load()            | 从服务器加载数据，并把返回的数据放置到指定的元素中                         |
| serialize()       | 编码表单元素集为字符串以便提交                                            |
| serializeArray()  | 编码表单元素集为 names 和 values 的数组                                   |


### jQuery杂项方法

| 方法           | 描述                                                                      |
|----------------|-------------------------------------------------------------------------|
| data()         | 向被选元素附加数据，或者从被选元素获取数据                                 |
| each()         | 为每个匹配元素执行函数                                                    |
| get()          | 获取由选择器指定的 DOM 元素                                               |
| index()        | 从匹配元素中搜索给定元素                                                  |
| $.noConflict() | 释放变量 $ 的 jQuery 控制权                                               |
| $.param()      | 创建数组或对象的序列化表示形式（可在生成 AJAX 请求时用于 URL 查询字符串中） |
| removeData()   | 移除之前存放的数据                                                        |
| size()         | ==在版本 1.8 中被废弃。== 返回被 jQuery 选择器匹配的 DOM 元素的数量        |
| toArray()      | 以数组的形式检索所有包含在 jQuery 集合中的所有 DOM 元素                   |
| pushStack()    | 将一个DOM元素集合加入到jQuery栈                                           |
| $.when()       | 提供一种方法来执行一个或多个对象的回调函数                                |


### jQuery属性

| 方法               | 描述                                                             |
|--------------------|----------------------------------------------------------------|
| context            | ==在版本 1.10 中被废弃。== 包含被传递到 jQuery 的原始上下文       |
| jquery             | 包含 jQuery 的版本号                                             |
| jQuery.fx.interval | 改变以毫秒计的动画运行速率                                       |
| jQuery.fx.off      | 对所有动画进行全局禁用或启用                                     |
| jQuery.support     | 包含表示不同浏览器特性或漏洞的属性集（主要用于 jQuery 的内部使用） |
| length             | 包含 jQuery 对象中元素的数目                                     |
| jQuery.cssNumber   | 包含所有可以不使用单位的CSS属性的对象                            |


## jQuery插件

### jQuery Validate

jQuery Validate 插件为表单提供了强大的验证功能，让客户端表单验证变得更简单，同时提供了大量的定制选项，满足应用程序各种需求。该插件捆绑了一套有用的验证方法，包括 URL 和电子邮件验证，同时提供了一个用来编写用户自定义方法的 API。所有的捆绑方法默认使用英语作为错误信息，且已翻译成其他 37 种语言。

该插件是由 Jörn Zaefferer 编写和维护的，他是 jQuery 团队的一名成员，是 jQuery UI 团队的主要开发人员，是 QUnit 的维护人员。该插件在 2006 年 jQuery 早期的时候就已经开始出现，并一直更新至今。目前版本是 1.14.0。

访问 [jQuery Validate 官网](https://jqueryvalidation.org/) ，下载最新版的 jQuery Validate 插件。
目前1.14.0 版本下载地址：http://static.runoob.com/download/jquery-validation-1.14.0.zip

#### 导入 js 库（使用菜鸟教程提供的CDN）

```js
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/lib/jquery.js"></script>
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/dist/jquery.validate.min.js"></script>
```

#### 默认校验规则

| 序号 | 规则               | 描述                                                                           |
|------|--------------------|------------------------------------------------------------------------------|
| 1    | required:true      | 必须输入的字段                                                                 |
| 2    | remote:"check.php" | 使用ajax方法调用check.php验证输入值                                            |
| 3    | email:true         | 必须输入正确格式的电子邮件                                                     |
| 4    | url:true           | 必须输入正确格式的网址                                                         |
| 5    | date:true          | 必须输入正确格式的日期。（日期校验ie6出错，慎用）                                  |
| 6    | dateISO:true       | 必须输入正确格式的日期（ISO），例如：2009-06-23,1998/01/22。只验证格式，不验证有效性 |
| 7    | number:true        | 必须输入合法的数字（负数，小数）                                                  |
| 8    | digits:true        | 必须输入整数                                                                   |
| 9    | creditcard:        | 必须输入合法的信用卡号                                                         |
| 10   | equalTo:"#field"   | 输入值必须和#field相同                                                         |
| 11   | accept:            | 输入拥有合法后缀名的字符串（上传文件的后缀）                                     |
| 12   | maxlength:5        | 输入长度最多是5的字符串（汉字算一个字符）                                        |
| 13   | minlength:10       | 输入长度最小是10的字符串（汉字算一个字符）                                       |
| 14   | rangelength:[5,10] | 输入长度必须介于5和10之间的字符串（汉字算一个字符）                              |
| 15   | range:[5,10]       | 输入值必须介于5和10之间                                                        |
| 16   | max:5              | 输入值不能大于5                                                                |
| 17   | min:10             | 输入值不能小于10                                                               |

#### 默认提示

```
messages: {
    required: "This field is required.",
    remote: "Please fix this field.",
    email: "Please enter a valid email address.",
    url: "Please enter a valid URL.",
    date: "Please enter a valid date.",
    dateISO: "Please enter a valid date ( ISO ).",
    number: "Please enter a valid number.",
    digits: "Please enter only digits.",
    creditcard: "Please enter a valid credit card number.",
    equalTo: "Please enter the same value again.",
    maxlength: $.validator.format( "Please enter no more than {0} characters." ),
    minlength: $.validator.format( "Please enter at least {0} characters." ),
    rangelength: $.validator.format( "Please enter a value between {0} and {1} characters long." ),
    range: $.validator.format( "Please enter a value between {0} and {1}." ),
    max: $.validator.format( "Please enter a value less than or equal to {0}." ),
    min: $.validator.format( "Please enter a value greater than or equal to {0}." )
}

```

jQuery Validate提供了中文信息提示包，位于下载包的 dist/localization/messages_zh.js，内容如下：

```js
(function( factory ) {
    if ( typeof define === "function" && define.amd ) {
        define( ["jquery", "../jquery.validate"], factory );
    } else {
        factory( jQuery );
    }
}(function( $ ) {

/*
 * Translated default messages for the jQuery validation plugin.
 * Locale: ZH (Chinese, 中文 (Zhōngwén), 汉语, 漢語)
 */
$.extend($.validator.messages, {
    required: "这是必填字段",
    remote: "请修正此字段",
    email: "请输入有效的电子邮件地址",
    url: "请输入有效的网址",
    date: "请输入有效的日期",
    dateISO: "请输入有效的日期 (YYYY-MM-DD)",
    number: "请输入有效的数字",
    digits: "只能输入数字",
    creditcard: "请输入有效的信用卡号码",
    equalTo: "你的输入不相同",
    extension: "请输入有效的后缀",
    maxlength: $.validator.format("最多可以输入 {0} 个字符"),
    minlength: $.validator.format("最少要输入 {0} 个字符"),
    rangelength: $.validator.format("请输入长度在 {0} 到 {1} 之间的字符串"),
    range: $.validator.format("请输入范围在 {0} 到 {1} 之间的数值"),
    max: $.validator.format("请输入不大于 {0} 的数值"),
    min: $.validator.format("请输入不小于 {0} 的数值")
});

}));
```

也可以将该本地化信息文件 dist/localization/messages_zh.js 引入到页面：

#### 使用方式

1、将校验规则写到控件中

```html
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/lib/jquery.js"></script>
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/dist/jquery.validate.min.js"></script>
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/dist/localization/messages_zh.js"></script>
<script>
$.validator.setDefaults({
    submitHandler: function() {
      alert("提交事件!");
    }
});
$().ready(function() {
    $("#commentForm").validate();
});
</script>

<form class="cmxform" id="commentForm" method="get" action="">
  <fieldset>
    <legend>输入您的名字，邮箱，URL，备注。</legend>
    <p>
      <label for="cname">Name (必需, 最小两个字母)</label>
      <input id="cname" name="name" minlength="2" type="text" required>
    </p>
    <p>
      <label for="cemail">E-Mail (必需)</label>
      <input id="cemail" type="email" name="email" required>
    </p>
    <p>
      <label for="curl">URL (可选)</label>
      <input id="curl" type="url" name="url">
    </p>
    <p>
      <label for="ccomment">备注 (必需)</label>
      <textarea id="ccomment" name="comment" required></textarea>
    </p>
    <p>
      <input class="submit" type="submit" value="Submit">
    </p>
  </fieldset>
</form>
```

[不如点击尝试一下？](https://www.runoob.com/try/try.php?filename=jquery_validate_demo)

2、将校验规则写到js代码中

```js
$().ready(function() {
// 在键盘按下并释放及提交后验证提交表单
  $("#signupForm").validate({
    rules: {
      firstname: "required",
      lastname: "required",
      username: {
        required: true,
        minlength: 2
      },
      password: {
        required: true,
        minlength: 5
      },
      confirm_password: {
        required: true,
        minlength: 5,
        equalTo: "#password"
      },
      email: {
        required: true,
        email: true
      },
      topic: {
        required: "#newsletter:checked",
        minlength: 2
      },
      agree: "required"
    },
    messages: {
      firstname: "请输入您的名字",
      lastname: "请输入您的姓氏",
      username: {
        required: "请输入用户名",
        minlength: "用户名必需由两个字符组成"
      },
      password: {
        required: "请输入密码",
        minlength: "密码长度不能小于 5 个字符"
      },
      confirm_password: {
        required: "请输入密码",
        minlength: "密码长度不能小于 5 个字符",
        equalTo: "两次密码输入不一致"
      },
      email: "请输入一个正确的邮箱",
      agree: "请接受我们的声明",
      topic: "请选择两个主题"
     }
    })
});
```

```html
<form class="cmxform" id="signupForm" method="get" action="">
  <fieldset>
    <legend>验证完整的表单</legend>
    <p>
      <label for="firstname">名字</label>
      <input id="firstname" name="firstname" type="text">
    </p>
    <p>
      <label for="lastname">姓氏</label>
      <input id="lastname" name="lastname" type="text">
    </p>
    <p>
      <label for="username">用户名</label>
      <input id="username" name="username" type="text">
    </p>
    <p>
      <label for="password">密码</label>
      <input id="password" name="password" type="password">
    </p>
    <p>
      <label for="confirm_password">验证密码</label>
      <input id="confirm_password" name="confirm_password" type="password">
    </p>
    <p>
      <label for="email">Email</label>
      <input id="email" name="email" type="email">
    </p>
    <p>
      <label for="agree">请同意我们的声明</label>
      <input type="checkbox" class="checkbox" id="agree" name="agree">
    </p>
    <p>
      <label for="newsletter">我乐意接收新信息</label>
      <input type="checkbox" class="checkbox" id="newsletter" name="newsletter">
    </p>
    <fieldset id="newsletter_topics">
      <legend>主题 (至少选择两个) - 注意：如果没有勾选“我乐意接收新信息”以下选项会隐藏，但我们这里作为演示让它可见</legend>
      <label for="topic_marketflash">
        <input type="checkbox" id="topic_marketflash" value="marketflash" name="topic">Marketflash
      </label>
      <label for="topic_fuzz">
        <input type="checkbox" id="topic_fuzz" value="fuzz" name="topic">Latest fuzz
      </label>
      <label for="topic_digester">
        <input type="checkbox" id="topic_digester" value="digester" name="topic">Mailing list digester
      </label>
      <label for="topic" class="error">Please select at least two topics you'd like to receive.</label>
    </fieldset>
    <p>
      <input class="submit" type="submit" value="提交">
    </p>
  </fieldset>
</form>
```

[不如点击尝试一下？](https://www.runoob.com/try/try.php?filename=jquery_validate_demo1)

required: true 值是必须的。
required: "#aa:checked" 表达式的值为真，则需要验证。
required: function(){} 返回为真，表示需要验证。

后边两种常用于，表单中需要同时填或不填的元素。

#### 常用方法及注意问题

1、用其他方法替代默认的SUBMIT

```js
$().ready(function() {
 $("#signupForm").validate({
        submitHandler:function(form){
            alert("提交事件!");   
            form.submit();
        }    
    });
});
```

使用ajax方式

```js
$(".selector").validate({     
 submitHandler: function(form) 
   {      
      $(form).ajaxSubmit();     
   }  
 }) 
```

可以设置validate的默认值，写法如下：

```js
$.validator.setDefaults({
  submitHandler: function(form) { alert("提交事件!");form.submit(); }
});
```

如果想提交表单, 需要使用 form.submit()，而不要使用 $(form).submit()。

2、debug，只验证不提交表单

如果这个参数为true，那么表单不会提交，只进行检查，调试时十分方便。

```js
$().ready(function() {
 $("#signupForm").validate({
        debug:true
    });
});
```

如果一个页面中有多个表单都想设置成为debug，则使用

```js
$.validator.setDefaults({
   debug: true
})
```

3、ignore：忽略某些元素不验证

```js
ignore: ".ignore"
```

4、更改错误信息显示的位置

```js
errorPlacement：Callback
```

指明错误放置的位置，默认情况是：error.appendTo(element.parent());即把错误信息放在验证的元素后面。

```js
errorPlacement: function(error, element) {  
    error.appendTo(element.parent());  
}
```

实例

```html
<p>将错误信息放在 label 元素后并使用 span 元素包裹它</p>

<form method="get" class="cmxform" id="form1" action="">
  <fieldset>
    <legend>Login Form</legend>
    <p>
      <label for="user">Username</label>
      <input id="user" name="user" required minlength="3">
    </p>
    <p>
      <label for="password">Password</label>
      <input id="password" type="password" maxlength="12" name="password" required minlength="5">
    </p>
    <p>
      <input class="submit" type="submit" value="Login">
    </p>
  </fieldset>
</form>
```

[不打算尝试一下？](https://www.runoob.com/try/try.php?filename=jquery_validate_demo2)

代码的作用是：一般情况下把错误信息显示在 `<td class="status"></td>` 中，如果是 radio 则显示在 `<td></td>` 中，如果是 checkbox 则显示在内容的后面。

| 参数                | 类型     | 描述                                                                                                                                    | 默认值  |
|---------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------|---------|
| errorClass          | String   | 指定错误提示的class类名，可以自定义错误提示的样式                                                                                        | "error" |
| errorElment         | String   | 用什么标签标记错误，默认是label，可以改成em。                                                                                              | "label" |
| errorContainer      | Selector | 显示或者隐藏验证信息，可以自动实现有有错误信息出现时把容器属性变为显示，无错误时隐藏，用处不大。 errorContainer:"#messageBox1,#messageBox2" |         |
| errorLabelContainer | Selector | 把错误信息统一放在一个容器里面                                                                                                          |         |
| wrapper             | String   | 用什么标签再把上边的errorElement包起来                                                                                                  |         |


一般这三个属性同时使用，实现爱一个容器内显示所有错误提示的功能，并且没有信息时自动隐藏。

```js
errorContainer: "div.error",
errorLabelContainer: $("#signupForm div.error"),
wrapper: "li"
```

5、更改错误信息显示的样式

设置错误提示的样式，可以增加图标显示，在该系统中已经建立了一个validation.css，专门用于维护校验文件的样式。

```css
input.error { border: 1px solid red; }
label.error {
  background:url("./demo/images/unchecked.gif") no-repeat 0px 0px;

  padding-left: 16px;

  padding-bottom: 2px;

  font-weight: bold;

  color: #EA5200;
}
label.checked {
  background:url("./demo/images/checked.gif") no-repeat 0px 0px;
}
```

6、每个字段验证通过执行函数

```js
success：String,Callback
```

要验证的元素通过验证后的动作，如果跟一个字符串，会当作一个css类，也可跟一个函数。

```js

success: function(label) {
    // set &nbsp; as text for IE
    label.html("&nbsp;").addClass("checked");
    //label.addClass("valid").text("Ok!")
}

```

添加"valid"到验证元素，在CSS中定义的样式`<style>label.valid{}</style>`.

```js

success: "valid"

```

7、验证的触发方式修改

下面的虽然是boolean型的，但建议除非要改为false，否则别乱添加。
| 触发方式     | 类型    | 描述                                                                               | 默认值 |
|--------------|---------|----------------------------------------------------------------------------------|--------|
| onsubmit     | Boolean | 提交时验证，设置为false就用其他方法去验证。                                          | true   |
| onfocusout   | Boolean | 失去焦点时验证（不包括复选框/单选按钮）。                                             | true   |
| onkeyup      | Boolean | 在keyup时验证。                                                                     | true   |
| onclick      | Boolean | 在点击复选框和单选按钮时验证。                                                      | true   |
| focusInvalid | Boolean | 提交表单后，未通过验证的表单（第一个或提交之前获得焦点的未通过验证的表单）            | true   |
| focusCleanup | Boolean | 如果是true那么当未通过验证的元素获得焦点时，移除错误提示。避免和 focusInvalid 一起用 | false  |

```js

// 重置表单
$().ready(function() {
 var validator = $("#signupForm").validate({
        submitHandler:function(form){
            alert("submitted");   
            form.submit();
        }    
    });
    $("#reset").click(function() {
        validator.resetForm();
    });

});

```

8、异步验证

```js

remote：URL

```

使用ajax方式进行验证，默认会提交当前验证的值到远程地址，如果需要提交其他的值，可以使用data选项。

```js

remote: "check-email.php"

```

```js

remote: {
    url: "check-email.php",     //后台处理程序
    type: "post",               //数据发送方式
    dataType: "json",           //接受数据格式   
    data: {                     //要传递的数据
        username: function() {
            return $("#username").val();
        }
    }
}

```
远程地址只能输出"true"或"false",不能有其他输出。

9、添加自定义校验

```js

addMethod：name, method, message

```

自定义验证方法

```js

// 中文字两个字节
jQuery.validator.addMethod("byteRangeLength", function(value, element, param) {
    var length = value.length;
    for(var i = 0; i < value.length; i++){
        if(value.charCodeAt(i) > 127){
            length++;
        }
    }
  return this.optional(element) || ( length >= param[0] && length <= param[1] );   
}, $.validator.format("请确保输入的值在{0}-{1}个字节之间(一个中文字算2个字节)"));

// 邮政编码验证   
jQuery.validator.addMethod("isZipCode", function(value, element) {   
    var tel = /^[0-9]{6}$/;
    return this.optional(element) || (tel.test(value));
}, "请正确填写您的邮政编码");

```

**注意：** 要在 additional-methods.js 文件中添加或者在 jquery.validate.js 文件中添加。建议一般写在 additional-methods.js 文件中。
**注意：** 在messages_cn.js 文件中添加： isZipCode:"只能包括中文字、英文字母、数字和下划线"。调用钱要添加对 additional-methods.js 文件的引用。

10、radio 和 checkbox、select 的验证

radio 的 required 表示必须选中一个。

```html

<input  type="radio" id="gender_male" value="m" name="gender" required />
<input  type="radio" id="gender_female" value="f" name="gender"/>

```

checkbox 的 required 表示必须选中。

```html

<input type="checkbox" class="checkbox" id="agree" name="agree" required />

```

checkbox 的 minlength 表示必须选中的最小个数， maxlength 表示最大的选中个数， rangelength:[2,3] 表示选中个数区间。

```html

<input type="checkbox" class="checkbox" id="spam_email" value="email" name="spam[]" required minlength="2" />
<input type="checkbox" class="checkbox" id="spam_phone" value="phone" name="spam[]" />
<input type="checkbox" class="checkbox" id="spam_mail" value="mail" name="spam[]" />

```

select 的 required 表示选中的 value 不能为空。

```html

<select id="jungle" name="jungle" title="Please select something!" required>
    <option value=""></option>
    <option value="1">Buga</option>
    <option value="2">Baga</option>
    <option value="3">Oi</option>
</select>

```

select 的 minlength 表示选中的最小个数（可多选的select）， maxlength 表示最大的选中个数， rangelength:[2,3] 表示选中个数区间。

```html

<select id="fruit" name="fruit" title="Please select at least two fruits" class="{required:true, minlength:2}" multiple="multiple">
    <option value="b">Banana</option>
    <option value="a">Apple</option>
    <option value="p">Peach</option>
    <option value="t">Turtle</option>
</select>

```

#### jQuery.validate 中文 API

| 名称                                          | 返回类型        | 描述                     |
|-----------------------------------------------|-----------------|--------------------------|
| validate(options)                             | Validator       | 验证所选的form           |
| valid()                                       | Boolean         | 检查是否验证通过         |
| rules()                                       | Options         | 返回元素的验证规则       |
| rules("add", rules)                           | Options         | 增加验证规则             |
| rules("remove", rules)                        | Options         | 删除验证规则             |
| removeAttrs(attributes)                       | Options         | 删除特殊属性并且返回它们 |
| **自定义选择器**                              |                 |                          |
| :blank                                        | Validator       | 没有值的筛选器           |
| :filled                                       | Array\<Element> | 有值的筛选器             |
| :unchecked                                    | Array\<Element> | 没选择的元素筛选器       |
| **实用工具**                                  |                 |                          |
| jQuery.format(template,argument,argumentN...) | String          | 用参数代替模板中的{n}    |

##### Validator

validator 方法返回一个 Validator 对象。 Validator 对象有很多方法可以用来引发检验程序或者改变 form 的内容，下面列出几个常用的方法。

| 名称                             | 返回类型  | 描述                                                                                    |
|----------------------------------|-----------|-----------------------------------------------------------------------------------------|
| form()                           | Boolean   | 验证form返回成功还是失败                                                                |
| element(element)                 | Boolean   | 验证单个元素是成功还是失败                                                              |
| restForm()                       | undefined | 把前面验证的 form 恢复到验证前原来的状态                                                |
| showErrors(errors)               | undefined | 显示特定的错误信息                                                                      |
| **Validator 函数**               |           |                                                                                         |
| setDefaults(defaults)            | undefined | 改变默认的设置                                                                          |
| addMethod(name, method, message) | undefined | 添加一个新的验证方法。必须包括一个独一无二的名字，一个 javascript 的方法和一个默认的信息。 |
| addClassRules(name, rules)       | undefined | 增加组合验证类型，在一个类里面用多种验证方法是比较有用                                   |
| addClassRules(rules)             | undefined | 增加组合验证类型，在一个类里面用多种验证方法时比较有用。这个是同时加多个验证方法          |

##### 内置验证方式

| 名称                            | 返回类型 | 描述                                                          |
|---------------------------------|----------|-------------------------------------------------------------|
| required()                      | Boolean  | 必填验证元素                                                  |
| required(dependency-expression) | Boolean  | 必填元素依赖于表达式的结果                                    |
| required(dependency-callback)   | Boolean  | 必填元素依赖于回调函数的结果                                  |
| remote(url)                     | Boolean  | 请求远程校验。url通常是一个远程调用方法                        |
| minlength(length)               | Boolean  | 设置最小长度                                                  |
| maxlength(length)               | Boolean  | 设置最大长度                                                  |
| rangelength(range)              | Boolean  | 设置一个长度范围[min, max]                                    |
| min(value)                      | Boolean  | 设置最小值                                                    |
| max(value)                      | Boolean  | 设置最大值                                                    |
| email()                         | Boolean  | 验证电子邮箱格式                                              |
| range(range)                    | Boolean  | 设置值的范围                                                  |
| url()                           | Boolean  | 验证 URL 格式                                                 |
| date()                          | Boolean  | 验证日期格式（类型30/30/2008的格式，不验证日期准确性只验证格式） |
| dateISO()                       | Boolean  | 验证 ISO 类型的日期格式                                       |
| dateDE()                        | Boolean  | 验证德式的日期格式（29.0.1994 或 1.1.2006）                     |
| number()                        | Boolean  | 验证十进制数字（包括小数的）                                    |
| digits()                        | Boolean  | 验证整数                                                      |
| creditcard()                    | Boolean  | 验证信用卡号                                                  |
| accept(extension)               | Boolean  | 验证相同后缀名的字符串                                        |
| equalTo(other)                  | Boolean  | 验证两个输入框的内容是否相同                                  |
| phoneUS()                       | Boolean  | 验证美式的电话号码                                            |

##### validate () 的可选项

**debug：进行调试模式（表单不提交）**

```js

$(".selector").validate
({
    debug:true
})

```

**把调试设置为默认**

```js

$.validator.setDefaults({
    debug:true
})

```

**submitHandler：通过验证后运行的函数，里面要加上表单提交的函数，否则表单不会提交**

```js

$(".selector").validate({
    submitHandler:function(form) {
        $(form).ajaxSubmit();
    }
})

```

**ignore：对某些元素不进行验证**

```js

$("#myform").validate({
    ignore:".ignore"
})

```

**rules：自定义规则，key:value 的形式，key 是要验证的元素，value 可以是字符串或对象**

```js

$(".selector").validate({
    rules:{
        name:"required",
        email:{
            required:true,
            email:true
        }
    }
})

```

**messages：自定义的提示信息，key:value 的形式，key 是要验证的元素，value 可以是字符串或函数**

```js

$(".selector").validate({
    rules:{
        name:"required",
        email:{
            required:true,
            email:true
        }
    },
    messages:{
        name:"Name不能为空",
        email:{       
            required:"E-mail不能为空",
            email:"E-mail地址不正确"
        }
    }
})

```

**groups：对一组元素的验证，用一个错误提示，用errorPlacement 控制把出错信息放在哪里**

```js

$("#myform").validate({
    groups:{
        username:"fnamelname"
    },
    errorPlacement:function(error,element) {
        if (element.attr("name") == "fname" || element.attr("name") == "lname")   
            error.insertAfter("#lastname");
        else    
            error.insertAfter(element);
    },
   debug:true
})

```

**onsubmit：类型Boolean，默认 true，指定是否提交时验证**

```js

$(".selector").validate({  
    onsubmit:false
}

```

**onfocusout：类型 Boolean，默认 true，指定是否在获取焦点时验证**

```js

$(".selector").validate({   
    onfocusout:false
})

```

**onkeyup：类型 Boolean，默认 true，指定是否在敲击键盘时验证**

```js

$(".selector").validate({
   onkeyup:false
})

```

**onclick：类型 Boolean，默认 true,指定是否在鼠标点击时验证（一般验证checkbox、radiobox）**

```js

$(".selector").validate({
   onclick:false
})

```

**focusInvalid：类型 Boolean，默认 true。提交表单后，未通过验证的表单（第一个或提交之前获得焦点的未通过验证的表单）会获得焦点。**

```js

$(".selector").validate({
   focusInvalid:false
}) 

```

**focusCleanup：类型 Boolean，默认 false。当未通过验证的元素获得焦点时，移除错误提示（避免和 focusInvalid 一起使用**

```js

$(".selector").validate({
   focusCleanup:true
})

```

**errorClass：类型 String，默认 "error"。指定错误提示的 class 类名，可以自定义错误提示的样式**

```js

$(".selector").validate({ 
    errorClass:"invalid"
})

```

**errorElement：类型 String，默认 "label"。指定使用什么标签标记错误。**

```js

$(".selector").validate({
   errorElement:"em"
})

```

**wrapper：类型 String，指定用什么标签再把上边的 errorElment 包起来**

```js

$(".selector").validate({
   wrapper:"li"
})

```

**errorLabelContainer：类型 Selector，把错误信息统一放在一个容器里面**

```js

$("#myform").validate({   
    errorLabelContainer:"#messageBox",
    wrapper:"li",
    submitHandler:function() { 
        alert("Submitted!") 
    }
})

```

**showErrors：跟一个函数，可以显示总共有多少个未通过验证的元素**

```js

$(".selector").validate({  
    showErrors:function(errorMap,errorList) {
        $("#summary").html("Your form contains " + this.numberOfInvalids() + " errors,see details below.");
        this.defaultShowErrors();
    }
})

```

**errorPlacemet：跟一个函数，可以自定义错误放到哪里。**

```js

$("#myform").validate({  
    errorPlacement:function(error,element) {  
        error.appendTo(element.parent("td").next("td"));
   },
   debug:true
})

```

**success：要验证的元素通过验证后的动作，如果跟一个字符串，会当作一个 css 类，也可跟一个函数。**

```js

$("#myform").validate({        
    success:"valid",
        submitHandler:function() { 
            alert("Submitted!") 
        }
})

```

**hightlight：可以给未通过验证的元素加效果、闪烁等**


##### addMethod(name, method, message)方法

参数 name 是添加的方法的名字。

参数 method 是一个函数，接收三个参数(value, element, param)

value 是元素的值，element 是元素本身，param 是参数。

我们可以用 addMethod 来添加除内置的 Validtion 方法之外的验证方法。比如有一个字段，只能输入一个字母，范围是 a-f，写法如下：

```js

$.validator.addMethod("af",function(value,element,params){  
    if(value.length>1){
        return false;
    }
    if(value>=params[0] && value<=params[1]){
        return true;
    }else{
        return false;
    }
},"必须是一个字母,且a-f");

```

如果有个表单字段的 name="username"，则在 rules 中写：

```js

username:{
   af:["a","f"]
}

```

addMethod 的第一个参数，是添加的验证方法的名字，这时是af。
addMethod 的第三个参数，是自定义的错误提示，这里的提示为：“必须是一个字母，且 a-f”。
addMethod 的第二个参数，是一个函数，这个比较重要，决定了用这个验证方法时的写法。
如果只有一个参数，直接写，比如af:"a"，那么a就是这个唯一的参数，如果多个参数，则写在[]里，用逗号分开。

##### meta String 方式

```js

$("#myform").validate({

   meta:"validate",

   submitHandler:function() { 
alert("Submitted!") }

})

```

```html

<script type="text/javascript" 
src="js/jquery.metadata.js"></script>

<script type="text/javascript" 
src="js/jquery.validate.js"></script>

<form id="myform">

  <input type="text" 
name="email" class="{validate:{ required:true,email:true }}" />

  <input type="submit" 
value="Submit" />

</form>

```

#### 实例演示

##### 虚构的实例

- [错误的消息容器](https://www.runoob.com/try/try.php?filename=jquery-plugin-errorcontainer)

- [自定义消息作为元素数据](https://www.runoob.com/try/try.php?filename=jquery-plugin-custom-messages-data)

- [radio（单选按钮）、checkbox（多选按钮）和 select（下拉框）](https://www.runoob.com/try/try.php?filename=jquery-plugin-radio-checkbox-select)

- [与表单（Form）插件的交互（AJAX 提交）](https://www.runoob.com/try/try.php?filename=jquery-plugin-ajaxSubmit-integration)

- [自定义方法和消息显示](https://www.runoob.com/try/try.php?filename=jquery-plugin-custom-methods)

- [动态表单](https://www.runoob.com/try/try.php?filename=jquery-plugin-dynamic-totals)

- [使用jQuery UI Themeroller 定义表单样式](https://www.runoob.com/try/try.php?filename=jquery-plugin-themerollered)

- [TinyMCE - 一个轻量级的基于浏览器的所见即所得编辑器](https://www.runoob.com/try/try.php?filename=jquery-plugin-tinymce)

- [文件输入框](https://www.runoob.com/try/try.php?filename=jquery-plugin-file-input)

- [jQuery Mobile 表单验证](https://www.runoob.com/try/try-cdnjs.php?filename=jquery-plugin-jquerymobile)  **PS：** 可能打开会较慢，如不显示可尝试点击已打开网页左上角的源代码按钮

##### 现实世界的实例

- [Milk 注册表单](https://www.runoob.com/try/try.php?filename=jquery-plugin-milk)

- [Marketo 注册表单](https://www.runoob.com/try/try.php?filename=jquery-plugin-marketo-step1)

- [房屋买卖折叠面板表单](https://www.runoob.com/try/try.php?filename=jquery-plugin-multipart)  **PS：** 可能打开较慢，如不显示可尝试点击一打开网页的点击运行按钮

- [远程 CAPTCHA(验证码)验证](https://www.runoob.com/try/try.php?filename=jquery-plugin-captcha)

##### 实例下载

- [点击下载](http://static.runoob.com/download/jquery-validation-1.14.0.zip)

- [官方实例](http://static.runoob.com/assets/jquery-validation-1.14.0/demo/index.html)


### jQuery Cookie

#### jQuery Cookie 插件

jQuery 可以通过 jquery.cookie.js 插件来操作 Cookie。

官方地址：http://plugins.jquery.com/cookie/
Github 地址：https://github.com/carhartl/jquery-cookie
使用 jquery.cookie.js 之前需要先引入 jQuery：

```html

<script src="/path/to/jquery.min.js"></script>
<script src="/path/to/jquery.cookie.js"></script>

```

也可以使用第三方资源库引入这两个文件：

```html

<script src="https://cdn.staticfile.org/jquery/3.4.0/jquery.min.js"></script>
<script src="https://cdn.staticfile.org/jquery-cookie/1.4.1/jquery.cookie.min.js"></script>

```

#### 使用方法

**创建 cookie：**

```js

$.cookie('name', 'value');

```

如果未指定过期时间，则会在关闭浏览器或过期。
**创建 cookie，并设置 7 天后过期：**

```js

$.cookie('name', 'value', { expires: 7 });

```

创建 cookie，并设置 cookie 的有效路径，路径为网站的根目录：

```js

$.cookie('name', 'value', { expires: 7, path: '/' });

```

**注：** 在默认情况下，只有设置 cookie 的网页才能读取该 cookie。如果想让一个页面读取另一个页面设 置的cookie，必须设置 cookie 的路径。cookie 的路径用于设置能够读取 cookie 的顶级目录。将这 个路径设置为网站的根目录，可以让所有网页都能互相读取 cookie （一般不要这样设置，防止出现冲突）
**读取 cookie：**

```js

$.cookie('name'); // => "value"
$.cookie('nothing'); // => undefined

```

**读取所有的 cookie 信息：**

```js

$.cookie(); // => { "name": "value" }

```

**删除cookie：**

```js

// cookie 删除成功返回 true，否则返回 false
$.removeCookie('name'); // => true
$.removeCookie('nothing'); // => false 
 
// 写入使用了 path时，读取也需要使用相同的属性 (path, domain) 
$.cookie('name', 'value', { path: '/' });
 
// 以下代码【删除失败】
$.removeCookie('name'); // => false
// 以下代码【删除成功】
$.removeCookie('name', { path: '/' }); // => true

```

**注意：** 删除 cookie 时，必须传递用于设置 cookie 的完全相同的路径，域及安全选项。
**实例**

```js

$(document).ready(function(){
  $.cookie('name', 'runoob');  // 创建 cookie
  name = $.cookie('name');     // 读取 cookie
  $("#test").text(name);
  $.cookie('name2', 'runoob2', { expires: 7, path: '/' });
  name2 = $.cookie('name2');
  $("#test2").text(name2);
});

```

[为什么不点击尝试一下呢](https://www.runoob.com/try/try.php?filename=tryjquery_cookie)

执行完后，我们可以在浏览器中查看 Cookie 信息，如下图所示：

![jQuery-Cookie](./image/jQuery-Cookie.jpg "jQuery-Cookie")

#### 参数说明

- **raw**

    默认值：false
    默认情况下，读取和写入 cookie 的时候自动进行编码和解码（使用 encodeURIComponent 编码，decodeURIComponent 解码）。要关闭这个功能设置 raw:true 即可：

    ```js

    $.cookie.raw = true;

    ```

- **json**

    设置 cookie 的数据使用 json 存储和读取，这时就不需要使用 JSON.stringify 和 JSON.parse 了。

    ```js

    $.cookie.json = true;

    ```

- **expires**

    ```js

    expires: 365

    ```

    定义 cookie 的有效时间，值可以是一个数字（从创建 cookie 时算起，以天为单位）或一个 Date 对象。如果省略，那么创建的 cookie 是会话 cookie，将在用户退出浏览器时被删除。

- **path**

    ```js

    path: '/'

    ```

    默认情况：只有设置 cookie 的网页才能读取该 cookie。

    定义 cookie 的有效路径。默认情况下， 该参数的值为创建 cookie 的网页所在路径（标准浏览器的行为）。

    如果你想在整个网站中访问这个 cookie 需要这样设置有效路径：path: '/'。如果你想删除一个定义了有效路径的 cookie，你需要在调用函数时包含这个路径:
    
    ```js

    $.cookie('the_cookie', null,{ path: '/' });

    ```

- **domain**

    ```js

    domain: 'example.com'

    ```

    默认值：创建 cookie 的网页所拥有的域名。

- **secure**

    ```js

    secure: true

    ```

    默认值：false。如果为 true，cookie 的传输需要使用安全协议（HTTPS）。









| 描述                           | 代码                                            |
|--------------------------------|-------------------------------------------------|
| debug：进行调试模式（表单不提交） | ``` $(".selector").validate ({ debug:true })``` |
|                                |                                                 |
|                                |                                                 |
|                                |                                                 |
|                                |                                                 |


|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |






