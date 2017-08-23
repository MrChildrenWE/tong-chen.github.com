---
title: Cytoscape视频教程
author: ct
layout: post
categories:
  - Cytoscape
tags:
  - Cytoscape
  - Bioinfo
---

Cytoscape已成为网络图绘制的核心工具，基因表达调控网络、蛋白互作网络、miRNA-gene调节关系、分析流程、组织架构等任何与网络、结构、层级有关系的事情都可以用Cytoscape来绘制。前期的教程中有[Cytoscape的基本使用](http://mp.weixin.qq.com/s/ZSoW7-qWs3BuSB7bkDnfmA)，[早期录制的Cytoscape视频教程, 含安装和基本使用](http://mp.weixin.qq.com/s/Q30mdC26UqffBcbtFxpnXg)等。

从上次录制视频，到现在Cytoscape也有了不少更新，个人对Cytoscape的体会也有了进步，更主要的是不少人反应之前的视频不够清晰，或实名或匿名 (匿名的都没回复)的联系我要清晰版。实际我也没有，不知道为啥传上去就不清晰了，这次录制了全屏版，希望效果能好些。

本次三个视频，截图不同的角度。

### 基本操作

利用一个简单的组织构建图展示Cytoscape的基本使用，导入网络、导入节点属性，更改点的形状、颜色，在点上插入图片、绘制饼图、柱状图、加入颜色条纹，点的手动对齐、横向分布等。

网络文件和节点属性文件都是正常矩阵格式，若有中文需使用UTF-8编码；若非EXCEL文件，不能有xls后缀。

{::nomarkdown}
<embed src="https://imgcache.qq.com/tencentvideo_v1/playerv3/TPout.swf?max_age=86400&v=20161117&vid=z0541oby69q&auto=0" allowFullScreen="true" quality="high" width="480" height="400" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>
{:/nomarkdown}


### miRNA-mRNA调控网络

Cytoscape可用于绘制基因共表达网络，这儿选取miRNA-gene调控网络 (含miRNA-gene表达相关性数据)做为例子，涉及到根据表达变化倍数对每个点进行着色、根据表达相关性对线进行着色、miRNA和靶基因采用不同的形状表示、微调获得合适的展示图形、结果导出PDF格式、导出图例等。

{::nomarkdown}
<embed src="https://imgcache.qq.com/tencentvideo_v1/playerv3/TPout.swf?max_age=86400&v=20161117&vid=z0541oby69q&auto=0" allowFullScreen="true" quality="high" width="480" height="400" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>
{:/nomarkdown}

### 不同的布局的调试和修改

网络绘制根据网络图的大小、展示的用意可以选择合适的布局。Cytoscape提供了多种布局算法，具体见[http://manual.cytoscape.org/en/stable/Navigation_and_Layout.html](http://manual.cytoscape.org/en/stable/Navigation_and_Layout.html)。

下面列出几种示例

#### Attribute Circle Layout

属性环展示方式所有的节点都在环上，适用于点比较少的时候。环上点的顺序可以根据某一列来调整。

![](http://blog.genesino.com/images/cytoscape/attribute_circle_layout.png)

#### Group Attributes Layout

先按某一列的值对点进行分组，每个分组的点成为一个独立的环。在区分上下调基因时，可以按这个来分类，看不同类的基因的调控关系。


![](http://blog.genesino.com/images/cytoscape/group_by_attribute_layout.png)

#### Prefuse Force Directed Layout

通常也可以获得比较好的结果，相连的点邻接，其它点较远。同时可以根据某一列设置边的强度作为连线的长度。

![](http://blog.genesino.com/images/cytoscape/force_layout.png)

#### Compound Spring Embedder Layout

复杂网络适用这个，尤其是连线特别多时。

![](http://blog.genesino.com/images/cytoscape/cose_layout.png)

#### Edge-weighted Spring-Embedded Layout

所有的边视为连接2个节点的弹簧。每一个弹簧有一个松弛状态下的期望长度 (resting length)和压缩强度。算法会迭代所有的弹簧，并进行仿真模拟获得每个弹簧的最佳长度。是比较常用的一种，其获得结果也是一个环，但对空间的利用比下面两种要好。

![](http://blog.genesino.com/images/cytoscape/spring.png)

#### yFiles Organic Layout

也是一种Spring-embeded的算法，可以展示网络图的聚类结构。

![](http://blog.genesino.com/images/cytoscape/yOrganic.png)


{::nomarkdown}
<embed src="https://imgcache.qq.com/tencentvideo_v1/playerv3/TPout.swf?max_age=86400&v=20161117&vid=w05410fbsys&auto=0" allowFullScreen="true" quality="high" width="480" height="400" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>
{:/nomarkdown}



## 参考

1. [Cytoscape的基本使用](http://mp.weixin.qq.com/s/ZSoW7-qWs3BuSB7bkDnfmA)
2. [早期录制的Cytoscape视频教程, 含安装和基本使用](http://mp.weixin.qq.com/s/Q30mdC26UqffBcbtFxpnXg)
3. [http://blog.genesino.com/2012/04/cytoscape-basic-usage/](http://blog.genesino.com/2012/04/cytoscape-basic-usage/)
4. [http://manual.cytoscape.org/en/stable/Navigation_and_Layout.html](http://manual.cytoscape.org/en/stable/Navigation_and_Layout.html)

