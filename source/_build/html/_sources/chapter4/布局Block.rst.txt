布局Block
==================

若采用展平式物理设计方案，则设计中仅仅由 Macro 和标准单元构成；若采用层次化物理设计方案，则经过 Partitioning 后，顶层设计主要由 Macro、sub-system级别的 Block 构成

在 Floorplan 阶段，对于前者主要是考虑 Macro 的放置，后者则是要考虑 Macro、Block 的放置

.. note::
    在层次化设计中，对于对于各个预计分割的区域之间也需要进行布线通道的定义。布线通道的宽度需要考虑模块布局的拓扑约束，诸如：

- 子模块到子模块的界限
- 子模块之间的距离、顺序、排列
- 子模块之间的表面比率、网络权重、子模块隔离区

该部分请参考 Placement 部分

布局障碍
-----------------

**blockages** :
    are specific location where placing of cells are blocked, acts like guidelines for placement of std cells.  

blockages will not be guiding the tool to place the std cells at some particular area, but it won't allow the tool to place the std cell in the blocked area

.. note::
    在 Placement、Routing 阶段都存在 Blockage，均有如下分类
    
    1）Hard Blockages
    
    2）Soft Blockages
    
    3）Partial Blockages    

+------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
|       分类       |              特征               |                                                                          目的                                                                           |
+==================+=================================+=========================================================================================================================================================+
| Hard Blockage    | Complete Standard Cell Blockage | （1）avoid routing congestion at macro corners（2）Restrict std cells to certain regions in the design（3）control power rail generation at macro cells |
+------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
| Soft Blockage    | Non-Buffering Blockage          | only buffers can be placed and std cells cannot be placed                                                                                               |
+------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
| Partial Blockage | Partial Standard Cell Blockage  | （1）used to avoid congestion（2）can Block Standard Cells as per the required percentage value                                                         |
+------------------+---------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
