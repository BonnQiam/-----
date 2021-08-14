Floorplanning
==============================

.. toctree::
    :maxdepth: 2
    :caption: Contents:

    ./概述.rst
    ./布局IO单元.rst
    ./确定芯片面积.rst
    ./布局Macro.rst
    ./布局Block.rst
    ./电源规划.rst
    ./时钟规划.rst
    ./Floorplanning的评估.rst

.. warning::
    **To do** ：fly lines、布局障碍、电源规划、时钟规划、Floorplanning 评估

.. note::
    在正式开始 Floorplanning 之前，还有两项预备工作，分别是 
    
    （1）  `Connecting Power and Ground Ports` ：create logical connections between power
    and ground pins on standard cells and macros and the power and ground nets in the design
    
    （2） 产生设计中原本不存在但是物理实现必要的单元 `Adding Power, Ground, and Corner Cells`：Physical-only cells for power, ground, and corner placement might not be part of the
    synthesized netlist and must be added to design.


与布局（Placement）、布线（Routing）的关系
------------------------------------------

Marco、I/O pad cell 、Block 的布放在结果上属于布局，但是其又在布局规划阶段完成，由于其占据的面积（空间）很大，只有 Marco、I/O pad cell 的布放完成后，电源规划才有意义