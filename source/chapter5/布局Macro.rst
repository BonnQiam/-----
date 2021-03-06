布局Macro
=========================

若采用展平式物理设计方案，则设计中仅仅由 Macro 和标准单元构成；若采用层次化物理设计方案，则经过 Partitioning 后，顶层设计主要由 Macro、sub-system级别的 Block 构成

在 Floorplan 阶段，对于前者主要是考虑 Macro 的放置，后者则是要考虑 Macro、Block 的放置

.. note::
    Before staring of Floorplan, it is better to have **basic design understanding** , data flow of the design, integration guidelines of any special analog hard IPs in the design. And for block/partition level designs understanding the placement & IO interactions of the block in Full chip will help in coming up with good floorplan.

Macro / Block 的放置显著依赖于设计者的经验，摆放它们时要考虑面积、互连线长等传统问题，还需要考虑Macro / Block 的摆放对于 Place 的影响


(Macro) Floorplan Techniques
----------------------------------

.. figure:: ./floorplantechniques.png

*   Abutted floorplan : Channel less placement of blocks.
*   Non-Abutted / Channeled floorplan  : Channel based placement of blocks.
*   Mix / Narrow-Channel floorplan : partially abutted with some channels.


Macro 放置原则：边缘摆放
-------------------------------

边缘摆放的出发动机主要来源于下面两点：
    1. 从目前芯片设计的趋势来看，芯片中除了计算单元外就是随机存储单元RAM、只读存储单元ROM等。这些存储单元占据的芯片面积在有些设计中甚至超过百分之五十
   
       1. 对于存储单元来说，存在数据端口和存储端口，并且周围需要有一些可测性电路。这使得这些单元引线众多且功耗巨大
       2. 将它们*贴边放置*，不仅有利于这些单元的供电，而且防止这些单元过多的引脚对其他单元的布线造成影响。

    2. 标准单元在布局时，按照Row所划定的高度一排一排的摆放
   
       1. 既有利于算法的设计，又有利于工业制造。
       2. 在给各个器件供电时，可以使用横向的电源线将处于同一高度的器件连接在一起统一供电
    
    3. 将标准单元都摆放在芯片区域的中心，而大的Macro摆放在四周，就可以使标准单元方便的只用一条电源线连接在一起，而不会被高度不统一的Macro打断。对电源网格的设计提供了巨大便利 

Macro的摆放原则基本如下，可以参照下面这张图

.. figure:: ./test.png

1）Macro 尽量摆放在靠近相应输入输出口（IO pad cell）的位置

一般来说对于大型的Macro，他们不仅仅需要与芯片内部的其他Macro或者标准单元进行数据交换，还需要与芯片外部的器件进行通信。

比如，锁相环单元需要接收外部晶振信号，存储单元需要接收外部地址等。这种数据交换就是靠 IO pad cell 进行的，因此摆放在离相应的数据端口附近，有利于减少互联线长度，减少线上延迟，并节约布线资源。

2）大的Macro摆放尽量贴近版图的边缘和角落，这样有利于空间的利用，要尽量留出一个连续且尽量接近圆形/方形的Core区域来摆放标准单元。

3）Macro与Macro之间要留有一定空隙，给予布线资源。

特别是在Macro的间隙有端口的时候更是如此，设计者可以通过相邻Marco边界上端口的多少来决定留有多大的间隙比较合适，这样才不至于出现Pin Access的问题

4）合理设置Macro摆放的角度。在考量Macro摆放的角度时，不仅仅考虑空间摆放的因素，还要根据端口的连接关系与互连Macro的位置来决定。

如前面原理图中存储Macro的端口方向朝向中央，因为中间的标准单元需要与存储Macro进行数据交换，存在互连关系。在实际设计时，不仅要根据端口与标准单元之间的连接关系，还要考虑Macro与Macro之间的互连关系进行综合判断。


手工对宏单元进行摆放后，需要将他们设置为dont_touch属性，以防止在布局阶段软件对它进行移动。命令为：

.. code-block:: console
    :linenos:
    
    set_dont_touch_placement[all_macro_cells]

Halo
--------------------------------
    
在使用EDA软件的Floorplan设计时，同样可以给 Macro加上 **晕环** （ `halo` ）来控制 Macro 与 Macro 之间的距离 —— 设置不允许摆放标准单元晕道的目的是为了能够提供专用的布线空间
    
    .. figure:: ./halo.jpg
    
.. note::
        在ICC中这被称为 `Keepout Margin`，有 `hard` 、 `soft` 之分:
        
        (1)hard区域不允许任何Cell放置在该区域
        (2)soft则在coarse place的时候不允许任何Cell放入其内，但是在optimization以及legalization的时候是允许Cell放入其内的，也就是只允许Buffer加入其中
        
        Keepout Margin与Placement Blockage不同，它并不是独立存在的，而是依附于Macro周围，可随Macro移动的。所以它是专门用来控制Macro和其他单元之间距离的一种功能。
    
在基于标准单元的设计中，标准单元在布局（place）阶段完成了整个芯片内部的摆放，由于标准单元占据了底层金属的绝大多数布线轨道，当芯片局部出现拥塞时，布线晕道就能够提供更多底层的布线通道