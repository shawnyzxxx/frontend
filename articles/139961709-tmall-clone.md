# 第三次作业-------仿写天猫商城
## 文章信息
- 原文发布于：2024-06-25 17:37:56
- 标签：javascript、前端、html
- 原阅读量：543

## 文章导读

本文是第三次前端作业的完整记录：**仿写天猫商城**。文章不涉及后端接口与数据存储，而是纯静态页面实现，用 HTML 加 CSS 从零还原了电商站点常见的三个核心页面——首页（商品活动展示）、商品展示页（商品网格列表）和商品详情页（商品参数、价格、店铺信息与购买入口）。

**适用读者**：已经掌握 HTML 基础标签和 CSS 基本语法、想通过仿写经典电商页面来练习页面布局与样式的前端初学者。全文按页面分节，每节都给出完整代码，读者可以逐页对照天猫官网的版式，理解顶部栏、导航栏、内容区和底部栏的搭建思路，再动手敲一遍。

## 仿写目标与整体思路

本次仿写围绕「一个站点、三类页面」展开，三个页面之间保持了统一的视觉结构，方便对照与复用：

| 页面 | 对应文件 | 核心内容 | 主要布局技术 |
| --- | --- | --- | --- |
| 1. 天猫商城主页 | 仿写电商页面1---首页 | 顶部栏、频道导航、精选活动大图、底部版权信息 | `position: fixed` 固定顶栏、`inline-block` 横向排列、绝对定位内容区 |
| 2. 商品展示页 | 商品展示页面2 | 商品网格列表，展示商品图、名称、价格与销量 | CSS `grid` 网格、`float` 布局 |
| 3. 商品详情页 | 商品详情页面3 | 商品大图、价格区、规格选择表、店铺信息、购买按钮 | `grid` 网格、`float` 左右分栏 |

整体设计思路如下：

1. **统一页面骨架**：三个页面都采用「顶部栏 + 内容区 + 底部栏」的三段式结构，顶部栏使用 `position: fixed` 固定在视口顶部，`z-index` 抬高层级，保证滚动时导航始终可见。
2. **统一配色与字体**：正文默认使用灰色系（`#868282`、`#6c6c6c`），价格、重点信息用红色系（`red`、`rgb(243, 95, 9)`）强调，底部栏统一使用深灰 `#3f3e3e` 背景配浅灰 `#cbcbcb` 文字。
3. **去掉默认样式，手动控制**：统一写 `* { margin: 0 auto; }` 重置外边距，列表项用 `list-style-type: none` 去掉圆点，链接用 `text-decoration: none` 去掉下划线，避免浏览器默认样式干扰布局。
4. **页面定位精确控制**：内容区使用 `position: absolute` 配合 `top` 偏移避让固定顶部栏，页脚使用绝对定位落在页面底部。

> 说明：文中所有图片均引用天猫官方图片地址（`*.alicdn.com`），作业中仅用于视觉对照，实际项目需替换为自己的资源。

## 一、天猫商城主页

主页的目标是还原天猫首页的版式：顶部品牌 Logo 与功能入口、频道导航、精选活动大图以及底部版权信息。页面标题为「仿写电商页面1---首页」。

### 1.1 样式设计

样式部分按四个区块组织：顶部栏、导航栏、内容区、底部。

```css
*{
    margin: 0 auto;
}

div,span{
    /* border: 1px solid red; */
    color: #868282;
}

li{
    display: inline-block;
    list-style-type:none;
}

/* 1.顶部栏 */
.top{
    height: 110px;
    width: 1980px;
    position:fixed;
    top: 0px;
    background: white;
    z-index: 1;
}

.top > div{
    margin: 0px 10px;
    height: 105px;
    border-bottom: 5px solid rgb(255, 0, 0);
    position: relative;
}

.top-print{
    position: absolute;
    top:15px;
}

.top-text{
    position: absolute;
    top:40px;
    left: 170px;
}

.top-text a,.navigation-text a,.container3 a{
    text-decoration: none;
}

/* 2.导航栏 */
.box3{
    width: 800px;
    height: 50px;
    margin: 100px;
    position: relative;
    border-style: solid;
    text-align: center;
    line-height: 50px;
    border-radius: 15px;
    font-size: 25px;
}
.span2:hover{
    background-color: cyan;
}
.span2{
    display: inline-block;
    color: rgb(200, 12, 12);
    height: 400px;
    width: 120px;
    margin: 50px;
}

/* 3.内容 */
.container{
    width: 1700px;
    position: absolute;
    top: 145px;
    margin: 100px;
}

.container1{
    height: 30px;
    padding: 10px;
    border-bottom: 1px solid #6c6c6c;
}

.container1 > div{
    color: black;
    display: inline-block;
    font-size: 20px;
}

.container2{
    position: absolute;
    left: 200px;
}

.container3{
    position: absolute;
    right: 330px;
}

.box{
    width: auto;
    height: auto;
    margin-top: 20px;
    position: relative;
}

.box > div{
    top: 145px;
    /* border: 1px solid black; */
    width: auto;
}

.box1{
    margin-left: 200px;
}

.box2{
    margin-left:178px;
}

.box2 > div{
    display: inline-block;
    margin:  20px 21px;
}

/* 4.底部 */
.foot{
    height: 200px;
    width: 100%;
    margin: 100px;
    position: absolute;
    top: 800px;
    background: #3f3e3e;
}

.foot1,.foot2,.foot3,.foot4 {
    margin-top: 15px;
    text-align: center;
}

.foot span{
    color: #cbcbcb;
}
```

样式要点：

- 顶部栏 `.top` 宽 `1980px`、高 `110px`，使用 `position: fixed` 固定，`z-index: 1` 保证其浮于内容之上；内部用 `.top-print` 放 Logo、`.top-text` 放功能链接。
- 导航栏 `.box3` 使用 `border-radius: 15px` 做圆角，频道项 `.span2` 为 `inline-block`，鼠标悬停时背景变青色。
- 内容区 `.container` 使用 `position: absolute` 且 `top: 145px`，正好避让固定顶部栏；`.container1` 用下边框分隔标题栏，`.container2` 放标题、`.container3` 放「更多」链接。
- 底部 `.foot` 绝对定位到 `top: 800px`，内部四行分别放置版权、资质、备案与热线信息。

### 1.2 页面结构

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>仿写电商页面1---首页</title>
    <style>
        /* 样式同 1.1 节，此处省略 */
    </style>
</head>
<body>
    <!-- 1.顶部栏 -->
    <div class="top">
        <div clsass="top1">
            <div class="top-print"><img src="https://img.alicdn.com/imgextra/i2/O1CN01a69z6z1hJklCkBqOU_!!6000000004257-2-tps-174-106.png" width="180px" height="63px"></div>
            <ul class="top-text">
                <li><a href=""><span1>首页|</span1></a></li>
                <li><a href=""><span1>天猫商家入驻|</span1></a></li>
                <li><a href=""><span1>热点资讯|</span1></a></li>
                <li><a href=""><span1>社会招聘|</span1></a></li>
                <li><a href=""><span1>校园招聘|</span1></a></li>
                <li><a href=""><span1>招采平台|</span1></a></li>
                <li><a href=""><span1>帮助中心|</span1></a></li>
                <li><a href=""><span1>举报平台|</span1></a></li>
                <li><a href=""><span1>分享赚钱|</span1></a></li>
                <li><a href=""><span1>物流查询</span1></a></li>
            </ul>
        </div>
    </div>

    <!-- 2.导航栏 -->
    <div class="box3">
        <span2><b>天猫会员&nbsp;&nbsp;&nbsp;&nbsp;</b></span2>
        <span2><b>喵养生&nbsp;&nbsp;&nbsp;&nbsp;</b></span2>
        <span2><b>医药馆&nbsp;&nbsp;&nbsp;&nbsp;</b></span2>
        <span2><b>苏宁易购&nbsp;&nbsp;&nbsp;&nbsp;</b></span2>
        <span2><b>天猫内容&nbsp;&nbsp;&nbsp;&nbsp;</b></span2>
    </div>

    <!-- 3.内容 -->
    <div class="container">
        <div class="container1">
            <div class="container2">精选活动</div>
            <div class="container3"><a href=""><span3>更多&gt;</span3></a></div>
        </div>
        <div class="box">
            <div class="box1"><a href="">
                <img src="https://gw.alicdn.com/imgextra/i3/O1CN01Am8Sra21Zaice06ax_!!6000000006999-2-tps-1130-500.png_570x10000.jpg_.webp" width="560spx" height="280px">
            </a></div>
            <div class="box2">
                <div><a href=""><img src="https://gw.alicdn.com/tfs/TB1xwW3eiLaK1RjSZFxXXamPFXa-502-380.jpg_290x10000Q75.jpg_.webp" width="256px" height="200px">
                </a></div>
                <div><a href=""><img src="https://gw.alicdn.com/tps/TB1Lw9SLVXXXXajaXXXXXXXXXXX-1130-500.jpg_570x10000Q75.jpg_.webp" width="256px" height="200px">
                </a></div>
            </div>
        </div>
    </div>

    <!-- 4.底部 -->
    <div class="foot">
        <div class="foot1">
            <span4>
                Copyright 2015-2024  tianmao.com 版权所有
                (增值电信业务经营许可证: 沪B2-20170215)
            </span4>
        </div>
        <div class="foot2">
            <span4>
                互联网药品信息服务资格证书：（沪）-经营性-2024-0019 | 网络文化经营许可证：沪网文 [2022] 3418-243 号 |
                药品网络交易服务第三方平台备案: (沪) 网药平台备字〔2023〕第000006-001号
            </span4>
        </div>
        <div class="foot3">
            <div></div>
            <span4>沪公网安备 31010502000392号</span4>
            <span4>（沪）网械平台备字[2018]第00003号</span4>
            <span4>沪ICP备15010535号-13 | 营业执照</span4>
        </div>
        <div class="foot4">
            <span4>全国旅游服务热线：12301</span4>
        </div>
    </div>
</body>
</html>
```

> 提示：原文顶部栏的 `<div clsass="top1">` 是笔误，标准属性应为 `class`，实际编写时应写作 `<div class="top1">`。

## 二、商品展示页

商品展示页用于陈列多个商品，标题为「商品展示页面2」。页面采用 CSS Grid 实现商品网格，每个商品包含图片、名称、现价、划线原价与销量。

### 2.1 样式设计

```css
*{
    margin: 0 auto;
}

div,span{
    /* border: 1px solid red; */
    color: #6c6c6c;
}

li{
    display: inline-block;
    list-style-type:none;
}

/* 1.顶部栏 */
.top{
    height: 110px;
    width: 1980px;

    position:fixed;
    top: 0px;
    background: white;
    z-index: 1;
}

.top > div{
    margin: 0px 10px;
    height: 105px;
    /* border: 1px solid black; */
    position: relative;
}

.top-print{
    position: absolute;
    top:15px;
}

.top-text{
    position: absolute;
    top:40px;
    left: 170px;
}

.top-text a,.navigation-text a{
    text-decoration: none;
}

/* 2.导航栏 */
.navigation{
    margin-top: 110px;
    height: 30px;
    width: 100%;
    background: red;
    position: fixed;
    opacity: 1;
    z-index: 1;
}

.navigation-text > ul{
    width: 200px;
    margin-left: 0px;
    color: rgb(255, 255, 255);
    /* border: 1px solid black; */
    position: relative;
    top: 5px;
}

.navigation-text  a:hover{
    background: rgb(2, 2, 43);
}

.navigation-text span{
    color: white;
}

/* 3.内容 */
.container{
    height: 2000px;
    width: 100%;

    position: absolute;
    top: 145px;
}

.box{
    float: left;
    position: relative;
    margin-left: 50px;
    display: grid;

    grid-template-columns:repeat(4,2fr);
    grid-template-rows: repeat(4,2fr);

    grid-gap: 10px;
}

.box > div{
    /* border: 1px solid black; */
    width: 266px;
}

.box img{
    margin: 10px 33px;
}

.box-text{
    padding: 15px;
    color: #5d574d;
}

.box-price1{
    color: rgb(243, 95, 9);
    margin-left: 20px;
    font-size: 22px;
}

.box-price2{
    color: #cbcbcb;
    font-size: 16px;
    text-decoration: line-through;
}

.box-price3{
    color: #cbcbcb;
    font-size: 16px;
    margin-top: 5px;
    float: right;
}

/* 4.底部 */
.foot{
    height: 200px;
    width: 100%;
    position: absolute;
    top: 2000px;
    background: #3f3e3e;
}

.foot1,.foot2,.foot3,.foot4 {
    margin-top: 15px;
    text-align: center;
}

.foot span{
    color: #cbcbcb;
}
```

样式要点：

- 导航栏 `.navigation` 为红色 `fixed` 条，`margin-top: 110px` 正好让内容下移，避免被固定顶部栏遮挡。
- 商品容器 `.box` 使用 `display: grid`，列与行都定义为 `repeat(4, 2fr)`，`grid-gap: 10px` 控制商品间距，实现四列四行的商品矩阵。
- 价格用三个类区分：`.box-price1` 是醒目的橙红色现价，`.box-price2` 用 `text-decoration: line-through` 画删除线表示原价，`.box-price3` 靠右显示销量。

### 2.2 页面结构

商品卡片在原文中重复出现 8 次，每张卡片结构一致，示例如下：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>商品展示页面2</title>
    <style>
        /* 样式同 2.1 节，此处省略 */
    </style>
</head>
<body>
    <!-- 1.顶部栏 -->
    <div class="top">
        <div clsass="top1">
            <div class="top-print"><img src="https://gw.alicdn.com/imgextra/i1/O1CN01obvh6l1iRpMLSol1z_!!6000000004410-2-tps-214-68.png_110x10000.jpg_.webp" width="180px" height="63px"></div>
            <ul class="top-text">
                <li><a href=""><span>首页|</span></a></li>
                <li><a href=""><span>天猫商家入驻|</span></a></li>
                <li><a href=""><span>热点资讯|</span></a></li>
                <li><a href=""><span>社会招聘|</span></a></li>
                <li><a href=""><span>校园招聘|</span></a></li>
                <li><a href=""><span>招采平台|</span></a></li>
                <li><a href=""><span>帮助中心|</span></a></li>
                <li><a href=""><span>举报平台|</span></a></li>
                <li><a href=""><span>分享赚钱|</span></a></li>
                <li><a href=""><span>物流查询</span></a></li>
            </ul>
        </div>
    </div>

    <!-- 2.导航栏 -->
    <div class="navigation">
        <div class="navigation-text">
            <ul>
                <li><a href=""><span>限时特价&nbsp;&nbsp;</span></a></li>
                <li><a href=""><span>好物推荐&nbsp;&nbsp;</span></a></li>
                <li><a href=""><span>正品保障&nbsp;&nbsp;</span></li>
            </ul>
        </div>
    </div>

    <!-- 3.内容 -->
    <div class="container">
        <div class="box">
            <!-- 以下卡片结构重复，此处展示一张，其余同构 -->
            <div>
                <img src="https://gw.alicdn.com/bao/uploaded/i3/6000000007361/O1CN01ox32td24FOPDkofGu_!!6000000007361-0-sm.jpg_220x10000Q75.jpg_.webp">
                <div class="box-text">小恐龙儿童睡衣冬季加厚款男童珊瑚绒男孩三层夹棉冬款加绒家居服 1件装</div>
                <div>
                    <span class="box-price1">￥190</span>
                    <span class="box-price2">￥288</span>
                    <span class="box-price3">已售3.8w+</span>
                </div>
            </div>
            <!-- 其余 7 张卡片结构与上面完全一致 -->
        </div>
    </div>

    <!-- 4.底部 -->
    <div class="foot">
        <div class="foot1">
            <span>
                Copyright 2015-2024  tianmao.com 版权所有
                (增值电信业务经营许可证: 沪B2-20170215)
            </span>
        </div>
        <div class="foot2">
            <span>
                互联网药品信息服务资格证书：（沪）-经营性-2024-0019 | 网络文化经营许可证：沪网文 [2022] 3418-243 号 |
                药品网络交易服务第三方平台备案: (沪) 网药平台备字〔2023〕第000006-001号
            </span>
        </div>
        <div class="foot3">
            <div></div>
            <span>沪公网安备 31010502000392号</span>
            <span>（沪）网械平台备字[2018]第00003号</span>
            <span>沪ICP备15010535号-13 | 营业执照</span>
        </div>
        <div class="foot4">
            <span>全国旅游服务热线：12301</span>
        </div>
    </div>
</body>
</html>
```

> 注意：原文中 8 张商品卡片的图片地址、商品名称、价格与销量完全一致，属于复制粘贴的占位效果；真正使用时，每张卡片应替换为不同商品图、名称与价格。

## 三、商品详情页

商品详情页是三个页面中信息最完整的一屏，标题为「商品详情页面3」。页面采用左右分栏：左侧约 40% 放商品主图与店铺信息，右侧约 60% 放商品标题、价格、配送、规格选择与购买按钮。

### 3.1 样式设计

```css
*{
    margin: 0 auto;
}

div,span{
    /* border: 1px solid red; */
    color: #6c6c6c;
}

li{
    display: inline-block;
    list-style-type:none;
}

/* 1.顶部栏 */
.top{
    height: 110px;
    width: 1980px;

    border-bottom: 3px solid red;

    position:fixed;
    top: 0px;
    background: white;
    z-index: 1;
}

.top > div{
    margin: 0px 10px;
    height: 105px;
    /* border: 1px solid black; */
    position: relative;
}

.top-print{
    position: absolute;
    top:15px;
}

.top-text{
    position: absolute;
    top:40px;
    left: 170px;
}

.top-text a,.navigation-text a{
    text-decoration: none;
}

/* 2.内容 */
.navigation1,.navigation2{
    margin-top: 130px;

    /* border: 1px solid red; */
    height: 800px;

    float: left;
}
/* 左侧40%内容部分 */
.navigation1{
    width: 38%;
    margin-right: 20px;
}

.navigation1 > img{
    position: relative;
    top: 20px;
    left: 100px;
}

.box{
    margin-top: 50px;
    /* border:1px red solid; */
    display: grid;
    grid-template-columns: repeat(2,1fr);
    grid-template-rows: repeat(2,1fr);

    margin-left: 100px;
}

.box1 {
    width: 200px;
    height: 30px;

    grid-column: 1/4;
    margin-left: 0px;

    color: black;
    font-size: 20px;
    font-weight: bolder;
}

.box2,.div3{
    margin: 10px 0px;
    width: 350px;
    height: 50px;
}

.box2 > span{
    position: relative;
    bottom: 20px;
    left: 10px;

    font-size: 20px;
    color: black;
    font-weight: bolder;
}

.box3{
    position: relative;
    text-align: center;
    top:  20px;
    left: 0px;
    font-size: 25px;
    color: rgb(145, 135, 135);
    font-weight: bolder;
}

/* 右侧60%内容部分 */
.navigation2{
    width: 60%;
}

.navigation2 > div{
    width: 800px;
    height: 140px;
    /* border: 1px solid black; */
    margin: 20px 0px;
}

.navigation21{
    text-align: center;
    background-color: #f4f4f4;
}

.price > div{
    /* border: 1px solid black; */
    float: left;

    margin-top: 0px;
}

.price1,.price3,.price5,.price7,.price9{
    width: 19%;
    height: 35px;

    font-size: 16px;
    text-align: end;
    color: #b2adad;
}

.price2,.price4,.price6,.price8,.price10{
    width: 200px;
    height: 35px;
    margin-left: 10px;
    color: #6c6c6c;
}

.price2{
    color: red;
    font-size: 24px;
    font-weight: bolder;
}

.price4{
    color: #cbcbcb;
}

.price8{
    color: darkorange;
}

.price10{
    color: crimson;
}

.cell{
    height: 150px;
    width: 800px;

    margin-top:10px;
    /* border:1px red solid; */
    display: grid;
    grid-template-columns: 11% 11% 26% 26% 26%;
    grid-template-rows: 50% 50%;
}

.cell > div{
    margin: 10px 50px;
}

.cell2,.cell7{
    color: red;
    width: 50px;
    text-align: center;
    border: 1px solid black;
}

.cell3,.cell4,.cell8,.cell9,.cell10{
    width: 200px;
    color: #000;
    text-align: center;
    border: 1px solid rgb(202, 199, 199);
}

.shop{
    position: relative;
    text-align: center;
    top: 10px;
}

.shop > div{
    width: 128px;
    height: 40px;

    margin: 0px 20px;
    border:1px red solid;

    float: left;

    position: relative;
    top: 130px;
}

.shop1{
    line-height: 35px;
    text-align: center;
    font-size: 25px;
    color: white;
    background-color: rgb(243, 101, 7);
}

.shop2{
    line-height: 35px;
    text-align: center;
    font-size: 25px;
    color: rgb(253, 252, 249);
    background-color: #f4ba0d;
    margin-left: 50px;
}

/* 3.底部 */
.foot{
    height: 200px;
    width: 100%;

    position: absolute;
    top: 1000px;

    background: #3f3e3e;
}

.foot1,.foot2,.foot3,.foot4 {
    margin-top: 15px;
    text-align: center;
}

.foot span{
    color: #cbcbcb;
}
```

样式要点：

- 左右分栏通过 `.navigation1`（宽 `38%`）与 `.navigation2`（宽 `60%`）配合 `float: left` 实现，`.navigation1` 设置 `margin-right: 20px` 留出间距。
- 左侧店铺信息块 `.box` 使用两行两列网格，`.box1` 通过 `grid-column: 1/4` 横跨整行，作为「店铺信息」标题。
- 价格区 `.price` 内部全部 `float: left`，标签（`.price1` 等）右对齐、内容（`.price2` 等）左对齐，形成「标签—值」的横向排列；现价 `.price2` 用大号红色加粗突出。
- 规格选择表 `.cell` 使用 `grid-template-columns: 11% 11% 26% 26% 26%`，两行两列布局，第一行是「款式 / 参考身高」的标签与全部选项，第二行是各规格选项。
- 购买按钮 `.shop` 中 `.shop1` 为橙红色「立刻购买」、`.shop2` 为黄色「加入购物车」，按钮通过 `top: 130px` 定位到合适位置。

### 3.2 页面结构

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>商品详情页面3</title>
    <style>
        /* 样式同 3.1 节，此处省略 */
    </style>
</head>
<body>
    <!-- 1.顶部栏 -->
    <div class="top">
        <div clsass="top1">
            <div class="top-print"><img src="https://img.alicdn.com/imgextra/i4/O1CN01Im2DQT1EtMnaEEhtI_!!6000000000409-2-tps-174-106.png" width="180px" height="100px"></div>
            <ul class="top-text">
                <li><a href=""><span>首页|</span></a></li>
                <li><a href=""><span>天猫商家入驻|</span></a></li>
                <li><a href=""><span>热点资讯|</span></a></li>
                <li><a href=""><span>社会招聘|</span></a></li>
                <li><a href=""><span>校园招聘|</span></a></li>
                <li><a href=""><span>招采平台|</span></a></li>
                <li><a href=""><span>帮助中心|</span></a></li>
                <li><a href=""><span>举报平台|</span></a></li>
                <li><a href=""><span>分享赚钱|</span></a></li>
                <li><a href=""><span>物流查询</span></a></li>
            </ul>
        </div>
    </div>

    <!-- 2.内容 -->
    <div class="navigation">
        <!-- 左侧40%内容部分 -->
        <div class="navigation1">
            <img src="https://gw.alicdn.com/imgextra/i3/6000000007361/O1CN01ox32td24FOPDkofGu_!!6000000007361-0-sm.jpg_Q75.jpg_.webp" width="450px" height="460px">
            <div class="box">
                <div class="box1">店铺信息</div>
                <div class="box2">
                    <img src="../作业图片/作业图片一/商店图标.jpg" alt="">
                     <span>小熊传说&gt&gt;</span>
                </div>
                <div class="box3">联系客服</div>
            </div>
        </div>

        <!-- 右侧60%内容部分 -->
        <div class="navigation2">
            <h3>小恐龙儿童睡衣冬季加厚款男童珊瑚绒男孩三层夹棉冬款加绒家居服 1件装</h3>
            <div class="navigation21">
               <div class="price">
                <div class="price1">特价</div>
                <div class="price2">￥198</div>
                <div class="price3">配送</div>
                <div class="price4">出发地&nbsp;---&nbsp;收货地</div>
                <div class="price5">特价规则</div>
                <div class="price6">2件 9折&nbsp;|&nbsp;&gt;2件 8.7折</div>
                <div class="price7">专享服务</div>
                <div class="price8">全店2件起批 破损包退，极速退款，30天放心退，上门取退，假一赔十，7天无理由退换</div>
                <div class="price9">已售</div>
                <div class="price10">3.8w+</div>
               </div>
            </div>
            <div class="navigation22">
                <div class="cell">
                    <div class="cell1">款式：</div>
                    <div class="cell2">全部</div>
                    <div class="cell3">迷你小恐龙</div>
                    <div class="cell4">帅气卡通超人</div>
                    <div class="cell5"></div>
                    <div class="cell6">参考身高：</div>
                    <div class="cell7">全部</div>
                    <div class="cell8">100cm（适合身高90cm~100cm）</div>
                    <div class="cell9">110cm（适合身高100cm~100cm）</div>
                    <div class="cell10">120cm（适合身高110cm~120cm）</div>
                </div>
            </div>
            <div class="shop">
                <div class="shop1">立刻购买</div>
                <div class="shop2">加入购物车</div>
            </div>
        </div>
    </div>

    <!-- 3.底部 -->
    <div class="foot">
        <div class="foot1">
            <span>
                Copyright 2015-2024  tianmao.com 版权所有
                (增值电信业务经营许可证: 沪B2-20170215)
            </span>
        </div>
        <div class="foot2">
            <span>
                互联网药品信息服务资格证书：（沪）-经营性-2024-0019 | 网络文化经营许可证：沪网文 [2022] 3418-243 号 |
                药品网络交易服务第三方平台备案: (沪) 网药平台备字〔2023〕第000006-001号
            </span>
        </div>
        <div class="foot3">
            <div></div>
            <span>沪公网安备 31010502000392号</span>
            <span>（沪）网械平台备字[2018]第00003号</span>
            <span>沪ICP备15010535号-13 | 营业执照</span>
        </div>
        <div class="foot4">
            <span>全国旅游服务热线：12301</span>
        </div>
    </div>
</body>
</html>
```

## 四、作业小结

综合三个页面，本次仿写天猫商城主要练习了以下 CSS 布局能力：

| 布局能力 | 所在页面 | 关键代码 |
| --- | --- | --- |
| 固定顶部导航 | 三个页面 | `position: fixed` + `top: 0px` + `z-index: 1` |
| 横向列表排列 | 主页顶部栏、展示页导航 | `display: inline-block` + `list-style-type: none` |
| 绝对定位内容区 | 三个页面内容区、底部栏 | `position: absolute` + `top` 偏移 |
| 商品网格 | 商品展示页、详情页 | `display: grid` + `grid-template-columns` / `grid-template-rows` + `grid-gap` |
| 左右分栏 | 商品详情页 | 百分比宽度 + `float: left` |
| 价格与标签强调 | 展示页、详情页 | 红色系配色 + `font-weight: bolder` + `text-decoration: line-through` |

几点结论：

> 1. **固定定位是电商页面的常见做法**：顶部栏与红色导航条都使用 `position: fixed` 并抬高 `z-index`，保证用户滚动浏览时导航始终可用，内容区则用绝对定位避让。
> 2. **Grid 是商品列表最直观的布局方式**：商品展示页用 `repeat(4, 2fr)` 定义四列网格，商品详情页的规格表用自定义百分比列宽，两者都避免了繁琐的浮动计算。
> 3. **重复结构可以复制后替换**：商品卡片、页脚信息在原文中都是重复结构，实际开发中应抽取为可复用的模板，再替换各自的图片、文案与价格。
> 4. **注意原文中的笔误**：三个页面的顶部栏都写成了 `clsass="top1"`，标准写法应为 `class="top1"`，动手复现时需修正，否则样式不会生效。
