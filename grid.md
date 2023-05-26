# Grid

* CSS Grid Layout（又名“Grid”或“CSS Grid”）是一种基于二维网格的布局系统，与过去的任何 Web 布局系统相比，它完全改变了我们设计用户界面的方式。 CSS 一直被用来布局我们的网页，但它从来没有做得很好。首先，我们使用了表格，然后是浮动、定位和内联块，但所有这些方法本质上都是 hack，遗漏了很多重要的功能（例如垂直居中）。 Flexbox 也是一个非常棒的布局工具，但它的单向流有不同的用例——它们实际上可以很好地协同工作！ Grid 是第一个专门为解决布局问题而创建的 CSS 模块，自从我们制作网站以来，我们一直在努力解决这些问题。
* Grid Container（网格容器）：通过将元素的`display`属性设置为`grid`或`inline-grid`，将其标记为网格容器。它包含了网格项和网格线。
* Grid Item（网格项）：网格容器的直接子元素成为网格项，它们是布局的基本单位。
* Grid Lines（网格线）：网格中的水平和垂直线，用于定义网格单元格和网格区域的边界。
* Grid Track（网格轨道）：两个相邻网格线之间的空间被称为网格轨道，可以是行轨道或列轨道。
* Grid Cell（网格单元格）：由相邻的水平和垂直网格线所围成的区域，表示一个网格单元格。
* Grid Area（网格区域）：由一个或多个网格单元格组成的矩形区域，用于布局和定位网格项。
* Grid Template（网格模板）：通过`grid-template-rows`和`grid-template-columns`属性，定义网格容器的行和列结构。
* Grid Gap（网格间距）：网格单元格之间的间距，可以使用`grid-row-gap`和`grid-column-gap`属性来设置。
* Grid Placement（网格定位）：通过`grid-row`、`grid-column`和相关属性，指定网格项在网格中的位置。
* Grid Line Names（网格线名称）：通过`grid-template-rows`和`grid-template-columns`属性，为网格线指定名称，以便在布局中引用。
* Grid Auto Placement（自动网格定位）：用于定义网格项在网格容器中的自动放置方式，可以使用`grid-auto-flow`属性来控制。
* Grid Auto Sizing（自动网格尺寸）：通过`grid-auto-rows`和`grid-auto-columns`属性，定义在自动放置过程中生成的网格单元格的大小。
* ![IMG_1383](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305221509227.PNG)

![IMG_1384](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305221511262.PNG)



`Flexbox`和`CSS Grid`是用于创建响应式和灵活的布局的两种不同的CSS布局技术。

1. **Flexbox**（弹性布局）：
   - Flexbox是一种单一维度（一维）的布局模型，用于创建灵活的、自适应的布局。
   - 它主要用于处理一维布局需求，如行或列布局。
   - 使用`display: flex`属性将容器元素设置为Flex容器，其中容器的直接子元素成为Flex项。
   - Flexbox提供了一组属性来控制Flex项的布局，如`flex-direction`、`justify-content`、`align-items`等。
   - Flexbox适用于构建简单的布局、导航栏、水平或垂直居中的元素等。
2. **CSS Grid**（网格布局）：
   - CSS Grid是一个二维的布局模型，用于创建复杂的网格结构。
   - 它允许你在行和列上创建网格，并控制网格中各个单元格的大小和位置。
   - 使用`display: grid`属性将容器元素设置为Grid容器，然后定义行和列的结构。
   - CSS Grid提供了一组属性来控制单元格的布局，如`grid-template-rows`、`grid-template-columns`、`grid-gap`等。
   - CSS Grid适用于构建复杂的网格布局、响应式布局、项目排列、网格对齐等。

* fr

* > ```css
  > fr"是一种单位，表示网格轨道（grid track）的一部分。它用于指定网格列或网格行的大小。
  > 
  > "fr"是"fraction"的缩写，意思是"分数"。当使用"fr"单位时，它会将可用空间按比例分配给网格轨道。
  > grid-template-columns: 1fr 2fr 1fr;
  > ```
  >
  
* implict grids 

  >    ```css
  >  grid-auto-rows: 80px;
  >   grid-auto-flow: row dense; 
  >    ```

​	当你定义的的 grid-template-rows: repeat(2, 100px);不够时，如果元素多了，他会自动开辟空间，但是你可以指定长度： grid-auto-rows: 80px;

![image-20230524110258500](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305242003575.png)

* grid-auto-flow: row dense; 指定排列方向

![image-20230524110340911](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305242003867.png)

* grid-auto-flow: column

![image-20230524110530246](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305242001166.png)

* Aligning track

  > ```css
  >   grid-template-columns: repeat(2, 200px);
  >         grid-template-rows: repeat(2, 100px);
  >         height: 1000px;
  >         align-items: start;
  >         justify-content: space-evenly;
  >         align-content: center;
  > ```
  >
  > ![image-20230524111740642](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305242001334.png)
  >
  > 有时候我们想把这个空缺补上
  >
  > ![image-20230524113253528](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305241950284.png)
  >
  > 我们只需要
  >
  > ```css
  >   grid-auto-flow: row dense ;
  > ```
  >
  > ![image-20230524113340292](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305241408473.png)



* min-content, max-content,minmax() function

* > 使用`max-content`可以使网格布局更加灵活，能够根据内容自动调整网格项的尺寸，以适应不同的情况。使用`max-content`时需要注意内容的大小和布局的约束条件
  >
  > ![image-20230524195341207](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305241953257.png)
  >
  > `min-content`是CSS Grid布局中的一个关键字，用于指定网格项（grid item）在该网格轨道（grid track）上的最小尺寸应为其内容所需的最小尺寸
  >
  > ![image-20230524200405427](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305242004462.png)
  >
  > minmax()
  >
  > ```css
  >   width: 90%;
  >         grid-template-rows: repeat(2, minmax(150px, min-content));
  >         grid-template-columns: minmax(200px, 300px) repeat(3, 1fr);
  > ```
  >
  > ![image-20230525153221117](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251532329.png)
  >
  > 当我不断减少视口宽度时，我的第一列也是不会少于200px的。
  >
  > ![image-20230525153410150](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251534338.png)
  
* use auto fill and auto fit 因为width: 1000px;

* > ```css
  > grid-template-rows: repeat(2, minmax(150px, min-content));
  >    grid-template-columns: repeat(auto-fill, 100px);
  > ```
  >
  > ![image-20230525155807136](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251558298.png)
  >
  > ```css
  > grid-template-columns: repeat(auto-fit, 100px);
  > ```
  >
  > ![image-20230525160055149](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251600288.png)
  >
  > ```css
  > grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  > ```
  >
  > ![image-20230525163421795](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251634930.png)
  >
  > 响应式布局，随着我的视口宽度来自适应内容的大小和排列  **1列**
  >
  > ![image-20230525164218568](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251642604.png)
  >
  > **2列**
  >
  > ![image-20230525164414301](https://makeforpicgo.oss-cn-chengdu.aliyuncs.com/study/202305251644345.png)

## nexter

