## 行内元素的水平居中
要实现行内元素（`<span>`、`<a>`等）的水平居中，只需把行内元素包裹在块级父层元素（`<div>`、`<li>`、`<p>`等）中，并且在父层元素CSS设置如下：
```css
#container{
    text-align:center;
}
```
适用于文字，链接，及其inline或者inline-block、inline-table和inline-flex。

## 块状元素的水平居中 
要实现块状元素（display:block）的水平居中，我们只需要将它的左右外边距margin-left和margin-right设置为auto，即可实现块状元素的居中，要水平居中的块状元素CSS设置如下：
```css
#center{
    margin:0 auto;
}
```

## 多个块状元素的水平居中
要实现多个水平排列的块状元素的水平居中，传统的方法是将要水平排列的块状元素设为display:inline-block，然后在父级元素上设置text-align:center，达到与上面的行内元素的水平居中一样的效果
```css
#container{
    text-align:center;
}
#center{
    display:inline-block;
}
```

## 使用flexbox实现多个块状元素的水平居中
在使用之前，首先介绍一下[flexbox](https://github.com/dsying/flex-demo)
### 学会使用flexbox
利用flexbox实现多块状元素的水平居中，只需要将父级容器的Css设置如下：
```css
#container {
    display: flex;
    justify-content:center;
}
```

## 已知高度宽度元素的水平垂直居中    
### 法一 绝对定位与负边距实现
利用绝对定位，将元素的top和left属性都设为50%，再利用margin边距，将元素回拉它本身高宽的一半，实现垂直居中。核心CSS代码如下：
```css
#container{
    position:relative;
}
#center{
    width:100px;
    height:100px;
    position:absolute;
    top:50%;
    left:50%;
    margin:-50px 0 0 -50px;
}
```
### 法二 绝对定位与margin
这种方法也是利用绝对定位与margin，但是无需知道被垂直居中元素的高和宽。核心代码如下：
```css
#container{
    position:relative;
}
#center{
    position:absolute;
    margin:auto;
    top:0;
    bottom:0;
    left:0;
    right:0;
}
```
### 法三 绝对定位和calc计算属性
注意与方法一的区别
核心CSS代码如下：
```css
#container{
    position:relative;
}
#center{
    width:100px;
    height:100px;
    position:absolute;
    top:calc(50% - 50px);
    left:calc(50% - 50px);
    /*margin:-50px 0 0 -50px;*/
}
```


## 未知高度和宽度元素的水平垂直居中 
### 法一.  当要被居中的元素是inline或者inline-block元素
当要被居中的元素是inline或者inline-block的时候，可以巧妙的将父级容器设置为display:table-cell，配合text-align:center和vertical-align:middle即可以实现水平垂直居中。

核心代码如下：
```css
#container{
    display:table-cell;
    text-align:center;
    vertical-align:middle;
}
#center{
 
}
```

### 法二. Css3显威力
利用Css3的transform，可以轻松的在未知元素的高宽的情况下实现元素的垂直居中。
```css
#container{
    position:relative;
}
 
#center{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

### 法三. flex布局轻松解决
使用flex布局，无需绝对定位等改变布局的操作，可以轻松实现元素的水平垂直居中。

核心代码如下：
```css
#container{
    display:flex;
    justify-content:center;
    align-items: center;
}
 
#center{
 
}
```