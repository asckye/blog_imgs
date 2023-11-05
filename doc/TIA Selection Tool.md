## 一、TIA Selection Tool使用入门
TIA Selection Tool 是一款西门子工业自动化产品的选型工具，用户可以使用该工具进行配置选型并生成订货清单。本文以S7-300 PLC为例，简要介绍其使用方法。

## 二、TIA Selection Tool 提供在线和离线两种版本供用户选择
离线版本下载：https://mall.industry.siemens.com/spicecad/api/CS/thirdParty/tia-selection-tool/download/tia-selection-tool.zip

在线版本：https：//mall.industry.siemens.com/tst/#/Start

本文基于TIA Selection Tool 离线版本：2016.3.2.34383创建

#### 1. 打开TIA Selection Tool，选择新建设备，并选择控制器。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/10.png)
![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/20.png)
##### 2.选择SIMATIC S7-300。
![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/30.png)
#### 3. 选择好CPU后会自动跳转至配置页面，该页面有4个选项卡：特殊产品属性、组态、限值、工程组态软件。

   1. 在特殊产品属性选项卡中可以设置是标准模块还是故障安全模块、环境要求、控制柜要求等等。本例中选择默认设置如图：
![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/40.png)

   2. 在组态选项卡中进行组态，已经自动放好一个导轨（默认为160mm规格的导轨，其规格会随着模块数量的增减自动适应），在右侧的目录中可以选择相应模块拖到导轨机架上。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/50.png)

      本例中依次组态PS307 5A，CPU 315-2PN/DP，数字量输入模块 16DI，数字量输出模块16 DO，模拟量输入模块 8AI和模拟量输出模块 4AO。

      当拖拽CPU时会弹出选择附件窗口（下拉列表中的附件已经过自动筛选，都可用于该模块），根据程序容量选择MMC卡，本例中选择4MB的存储卡。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/60.png)

      当拖拽IO模块时也会弹出选择附件窗口，如图所示，IO模块的附件有三种选择：
      - 全模块化系统布线：包括前连接器、端子模块及之间的连接电缆，安装方便,可大幅度减少用户柜内配线工作量
      - 柔性连接系统：前连接器配好接线，用户自己提供接线端子，可减少用户柜内配线工作量
     -   前连接器: 仅有前连接器，柜内端子及配线由用户完成
    本例中选择前连接器，螺钉型。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/70.png)

        组态完成后如图所示，可以调整某个模块的附件，如想把CPU的MMC卡换成8M，可在插槽列表中选中CPU，点击右侧按钮更改即可。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/80.png)

  3. 在限制选项卡中，可以看到当前的模块尺寸、地址空间占用、电流消耗等信息。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/90.png)

        点击右侧的“+”可以展开查看详细信息，以电流为例：![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/100.png)
#### 4. 组态完成后可以导出订货清单。![enter image description here](https://cdn.jsdelivr.net/gh/asckye/blog_imgs@main/soft/TIA_Selection_Tool/110.png)
