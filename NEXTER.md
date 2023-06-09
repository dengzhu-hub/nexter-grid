# 



项目结构

> ![image-20230526131236399](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305261312449.png)

* 布局可以用repeat(8, 1fr)

* ```css
    grid-template-rows: 80vh min-content 40vw repeat(3, min-content);
    grid-template-columns: repeat(8, 1fr);
  ```

* ![image-20230527183239922](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305271832069.png)

根据我们的项目要求对其进行修改，我们加了一列用于sidebar

```scss
 grid-template-columns: 8rem  repeat(8, minmax(min-content, 14rem));
```

然后我们需要让8columns center  the viewport，我们可以分别在左边右边加上1fr，

```scss
 grid-template-columns: 8rem 1fr repeat(8, minmax(min-content, 14rem)) 1fr;
```

![image-20230527184722110](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305271847324.png)

为了方便，现在我们使用name column

```scss
 grid-template-columns:
    [sidebar-start] 8rem [sidebar-end full-start] 1fr [center-start] repeat(
      8,
      [col-start] minmax(min-content, 14rem) [col-end]
    )
    [center-end]
    1fr [full-end];
```

现在开始进行布局

> ```scss
> .sidebar {
> background-color: #e67700;
> grid-column: sidebar-start / sidebar-end;
> grid-row: 1 / -1;
> }
> .header {
> background-color: #f0f0f0;
> }
> .realtors {
> background-color: blueviolet;
> }
> .feature {
> background-color: orangered;
> grid-column: center-start / center-end;
> }
> .story-picture {
> background-color: #087f5b;
> }
> .story-content {
> background-color: #b2b2b2;
> }
> .home {
> background-color: #3b5bdb;
> grid-column: center-start / center-end;
> }
> .gallery {
> background-color: #5f3d4c;
> grid-column: full-start / full-end;
> }
> .footer {
> background-color: #be4bdb;
> grid-column: full-start / full-end;
> }
> ```
>
> 效果：
>
> ![image-20230527191738449](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305271917639.png)
>
> ![image-20230527191757585](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305271917739.png)
>
> 完整布局
>
> ```scss
> .sidebar {
>   background-color: #e67700;
>   grid-column: sidebar-start / sidebar-end;
>   grid-row: 1 / -1;
> }
> .header {
>   background-color: #a61e4d;
>   grid-column: full-start / col-end 6;
> }
> .realtors {
>   background-color: blueviolet;
>   grid-column: col-start 7 / full-end;
> }
> .feature {
>   background-color: orangered;
>   grid-column: center-start / center-end;
> }
> 
> .story {
>   &-picture {
>     background-color: #087f5b;
>     grid-column: full-start / col-end 4;
>   }
>   &-content {
>     background-color: #b2b2b2;
>     grid-column: col-start 5 / full-end;
>   }
> }
> .home {
>   background-color: #3b5bdb;
>   grid-column: center-start / center-end;
> }
> .gallery {
>   background-color: #5f3d4c;
>   grid-column: full-start / full-end;
> }
> .footer {
>   background-color: #be4bdb;
>   grid-column: full-start / full-end;
> }
> 
> ```
>
> ![image-20230528094157728](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305280941116.png)
>
> ![image-20230528094219892](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305280942238.png)

#### grid-item

* feature

* > ```scss
  > .features {
  > display: grid;
  > //   align-items: start;
  > grid-template-columns: repeat(3, 1fr);
  > margin: 15rem 0;
  > gap: 6rem;
  > .feature {
  >  display: grid;
  >  grid-template-columns: min-content 1fr;
  >  column-gap: 2.5rem;
  >  row-gap: 1.5rem;
  >  &-icon {
  >    grid-row: 1 / span 2;
  >    fill: $color-primary;
  >    width: 4.5rem;
  >    height: 4.5rem;
  >  }
  >  &-text {
  >    font-size: 1.7rem;
  >  }
  > }
  > }
  > 
  > ```
  >
  > ![image-20230528111951874](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305281119216.png)
  >
  > 这里导致了一个问题，text和heading间距比较大，因为默认align-items: stretch;
  >
  > 我们fix 它 改为start.**注意这个知识点**
  >
  > ```scss
  > align-items: start;
  > ```
  >
  > ![image-20230528112311939](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305281123140.png)
  >
  > 现在我们对其做修改，让他response  
  >
  > ```scss
  > grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));	
  > ```
  >
  > 当视图容不下3列时候，会自动换行
  >
  > ![image-20230528113402287](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305281134453.png)
  >
  > 当视图容不下2列时，也会自动换行
  >
  > ![image-20230528113450761](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305281134913.png)
  >
  > 这就是使用auto-fit和minmax()好处
  >
  > ，即使视图最小时，我们的列都不会小于25rem
  >
  > ![image-20230528113722755](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305281137872.png)

#### story



![IMG_1386](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305281139431.PNG)

#### home

同样的我们继续用grid来设计home-card

```html
        <div class="home">
          <img
            src="./img/house-6.jpeg"
            alt="beautiful house"
            class="home-img"
          />
          <svg class="home-like">
            <use xlink:href="./img/sprite.svg#icon-heart"></use>
          </svg>
          <h5 class="home-name">安逸的大别墅</h5>
          <div class="home-location">
            <svg>
              <use xlink:href="./img/sprite.svg#icon-location-pin"></use>
            </svg>
            <p>香港</p>
          </div>
          <div class="home-rooms">
            <svg>
              <use xlink:href="./img/sprite.svg#icon-user"></use>
            </svg>
            <p>7 rooms</p>
          </div>
          <div class="home-area">
            <svg>
              <use xlink:href="./img/sprite.svg#icon-flattr"></use>
            </svg>
            <p>900 m <sup>2</sup></p>
          </div>
          <div class="home-price">
            <svg>
              <use xlink:href="./img/sprite.svg#icon-credit"></use>
            </svg>
            <p>￥22,222,000</p>
          </div>
          <button class="btn home-btn">联系realtor</button>
        </div>
```

首先对html进行布局

然后我们对其进行format

```scss
.homes {
  // background-color: #3b5bdb;
  grid-column: center-start / center-end; //采用的还是name 命名法，著名的8列
     grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
    //auto 让我们的页面可以不使用media query，从而实现自适应。非常不错这个属性，还有minmax
    
}
//对每个home进行设计
.home {
  background-color: $color-gray--light-1;
  display: grid;
  grid-template-columns: repeat(2, 1fr);   //我们还是不采用具体值，按照比例设计，这样更加响应
  row-gap: 5rem;
    
      &-img {
    width: 100%;  // 让图片占满空间
    grid-row: 1 / 2;
    grid-column: 1 / -1;  //通过grid 方式进行布局
    z-index: 1;
  }
    
      &-name {
    grid-row: 1 / 2;
    grid-column: 1 / -1;
    z-index: 3;
    width: 80%;
    justify-self: center;  //让这个元素 在grid中是居中的
    align-self: end;      //让他的假交叉轴是位于最下面的
    transform: translateY(50%);  //这里让他向下转换，50%就相当于自身元素一半，居中 
    font-size: 1.6rem;
    background-color: $color-secondary;
    padding: 1.2rem;
    text-align: center;
    font-family: $font-dispaly;
    font-weight: 400;
    color: #fff;
  }


```

![image-20230531144022390](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305311440512.png)

添加

```scss
transform: translateY(50%);
```

![image-20230531144206521](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305311442562.png)

制作右上角爱心

```scss
  &-like {
    grid-column: 2 / 3;   //依旧是采取grid方式
    grid-row: 1 / 2;    //
    width: 2.5rem;
    height: 2.5rem;
    fill: orangered;
    justify-self: end;     // 让他水平方向靠最后
    margin: 1rem;
    z-index: 2;
  }
```

![image-20230531144509119](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305311445213.png)

```scss
  &-location,
  &-rooms,
  &-area,
  &-price {
    margin-left: 2rem;
    font-size: 1.5rem;
    display: flex;   //利用flex实现icon和文字side by side
    gap: 1.2rem;
    align-items: center; 
    svg {
      width: 2rem;
      height: 2rem;
      fill: $color-primary;
    }
```

flex布局非常适合这种小的布局，所以我们这里用到

![image-20230531144704269](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305311447319.png) 

btn就很好布局了，因为我们grid使用的是两列，直接让他占据两列就可以了

```scss
&-btn {
    grid-column: 1/ -1;
  
  }
//其余就是在format它了，跟以前一样
```

可见cssgrid是非常方便的

#### gallery

object-fit, object-position, background-size, background-position

**`object-fit`** [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 属性指定[可替换元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced_element)（例如：[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 或 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/video)）的内容应该如何适应到其使用高度和宽度确定的框。

## [尝试一下](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-fit#尝试一下)

<iframe class="interactive is-default-height" height="200" src="https://interactive-examples.mdn.mozilla.net/pages/css/object-fit.html" title="MDN Web Docs Interactive Example" loading="lazy" data-readystate="complete" style="box-sizing: border-box; border: none; max-width: 100%; width: 765.719px; background-color: var(--background-secondary); border-radius: var(--elem-radius); color: var(--text-primary); height: 375px; margin: 1rem 0px; padding: 0px;"></iframe>

[CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 属性 **`object-position`** 规定了[可替换元素](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced_element)的内容，在这里我们称其为对象（即 **`object-position`** 中的 **`object`**）在其内容框中的位置。可替换元素的内容框中未被对象所覆盖的部分，则会显示该元素的背景。

你还可以使用 [`object-fit`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-fit) 属性来改变可替换元素的对象的内在的大小（即它看上去的大小）的调整方式，借助拉伸与缩放等使对象更好地适应元素的内容框。

## [尝试一下](https://developer.mozilla.org/zh-CN/docs/Web/CSS/object-position#尝试一下)

<iframe class="interactive is-default-height" height="200" src="https://interactive-examples.mdn.mozilla.net/pages/css/object-position.html" title="MDN Web Docs Interactive Example" loading="lazy" data-readystate="complete" style="box-sizing: border-box; border: none; max-width: 100%; width: 765.719px; background-color: var(--background-secondary); border-radius: var(--elem-radius); color: var(--text-primary); height: 375px; margin: 1rem 0px; padding: 0px;"></iframe>

* 布局
* ```scss
    &-img {
      width: 100%;
      object-fit: cover;
    }
  ```
* ![image-20230531191809088](C:\Users\jackdeng\AppData\Roaming\Typora\typora-user-images\image-20230531191809088.png)

虽然我们设置了object-fit: cover;但是他还是不会起作用，图片还是占据了其他item，因为没有设置高度。

```scss
  &-img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
}
```

现在我们让他只在网格线里面了，这个属性是真的好。

```scss
 &-item {
    &--1 {
      grid-column: 1 / span 2;
      grid-row: 1 / span 2;
    }
    &--2 {
      grid-column: 3 / span 3;
      grid-row: 1 / span 3;
    }
    &--3 {
      grid-row: span 2;
      grid-column: span 1;
    }
    &--4 {
      grid-row: span 2;
      grid-column: span 2;
    }
```

然后就这样布局，很简单，非常方便。

![image-20230601105840425](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202306011058372.png)

吧视口宽度缩小

![image-20230601105944169](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202306011059261.png)

我们发现他的高度还是没怎么变，宽度却在随着视口减下

因为设置了

```scss
  grid-template-rows: repeat(7, 5vw);
```

#### sidebar

实现一个

![image-20230603163324082](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202306031633247.png)

我们可以用::before,::after as grid items

```scss
.btn-nav {
  border: 0;
  border-radius: 0;
  background-color: #fff;
  height: 2px;
  width: 4.5rem;
  margin-top: 4rem;
  &::before,
  &::after {
    content: "";
    background-color: #fff;
    height: 2px;
    width: 4.5rem;
    display: block;
  }
  &::before {
    transform: translateY(-1.5rem);
  }
  &::after {
    transform: translateY(1.5rem);
  }
```

#### header

这一次我们定义rows

```scss
  grid-template-rows: 1fr min-content 6rem 1fr;
```

实现这种效果，我们依然使用grid和伪类

![image-20230603163650333](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202306031636428.png)

```scss
    color: $color-gray--light-2;
    text-transform: capitalize;
    display: grid;
    grid-template-columns: 1fr max-content 1fr;
    align-items: center;
    column-gap: 1.2rem;
    font-size: 1.4rem;
    &::before,
    &::after {
      content: "";
      height: 1.2px;
      background-color: currentColor;
      display: block;
    }

//注意我们这里使用了currentColor
```

logos

```scss
  &-seenon--logos {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    column-gap: 2rem;
    justify-items: center;
    img {
      height: 2.5rem;
      filter: brightness(70%);
      // display: block;
    }
  }
```

效果

![image-20230603164116975](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202306031641288.png)
