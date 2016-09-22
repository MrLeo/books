```css
.flex-cont{
  /*定义为flexbox的“父元素”*/
  display: -webkit-box;
  display: -webkit-flex;
  display: flex;
  /*子元素沿主轴对齐方式居中*/
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  justify-content: center;
  /*子元素沿侧轴对齐方式垂直居中*/
  -webkit-box-align: center;
  -webkit-align-items: center;
  align-items: center;
  /*指定主轴的伸缩流方向是纵向的*/
  -webkit-box-orient:vertical;
  -webkit-box-direction: normal;
  -webkit-flex-direction: column;
  flex-direction: column;
}
.flex-item{
  /*不要给flexbox里的子元素设置“margin:auto”的属性，在部分安卓机下，它会导致该元素的宽度撑开到100%占位*/
  /*在旧版的规范中，使用比例伸缩布局时，子元素的内容长短不同会导致无法“等分”，这个时候，我们需要给子元素设置一个“width:0%”来解决问题*/
  width: 0%;
  /*给“子元素”赋予自由伸缩的能力*/
  -webkit-box-flex: 1;
  -webkit-flex: 1;
  flex:1;
}
```


>这里假设flex容器为 .box ，子元素为 .item 。

1. 定义容器为flex布局
    ```css
    .box{
        display: -webkit-flex; /*webkit*/
        display: flex;
    }
    
    /*行内flex*/
    .box{
        display: -webkit-inline-flex; /*webkit*/
        display:inline-flex;
    }
    ```

2. 容器样式
    ```css
    .box{
        flex-direction: row | row-reverse | column | column-reverse;
        /*主轴方向：左到右（默认） | 右到左 | 上到下 | 下到上*/
        
        flex-wrap: nowrap | wrap | wrap-reverse;
        /*换行：不换行（默认） | 换行 | 换行并第一行在下方*/
        
        flex-flow: <flex-direction> || <flex-wrap>;
        /*主轴方向和换行简写*/
        
        justify-content: flex-start | flex-end | center | space-between | space-around;
        /*主轴对齐方式：左对齐（默认） | 右对齐 | 居中对齐 | 两端对齐 | 平均分布*/
        
        align-items: flex-start | flex-end | center | baseline | stretch;
        /*交叉轴对齐方式：顶部对齐（默认） | 底部对齐 | 居中对齐 | 上下对齐并铺满 | 文本基线对齐*/
        
        align-content: flex-start | flex-end | center | space-between | space-around | stretch;
        /*多主轴对齐：顶部对齐（默认） | 底部对齐 | 居中对齐 | 上下对齐并铺满 | 上下平均分布*/
    }
    ```

3. 子元素样式
    ```css
    .item{
        order: <integer>;
        /*排序：数值越小，越排前，默认为0*/
        
        flex-grow: <number>; /* default 0 */
        /*放大：默认0（即如果有剩余空间也不放大，值为1则放大，2是1的双倍大小，以此类推）*/
        
        flex-shrink: <number>; /* default 1 */
        /*缩小：默认1（如果空间不足则会缩小，值为0不缩小）*/
        
        flex-basis: <length> | auto; /* default auto */
        /*固定大小：默认为0，可以设置px值，也可以设置百分比大小*/
        
        flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
        /*flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto，*/
        
        align-self: auto | flex-start | flex-end | center | baseline | stretch;
        /*单独对齐方式：自动（默认） | 顶部对齐 | 底部对齐 | 居中对齐 | 上下对齐并铺满 | 文本基线对齐*/
    }
    ```