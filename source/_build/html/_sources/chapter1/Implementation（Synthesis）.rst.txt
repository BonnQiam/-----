Implementation（Synthesis）
=============================

此处的 synthesis 是广义上的概念，其主要有如下几个工作

- Make assumptions and local sub-goals

  - For example: transistor saturation

- Select circuit topology

  - For example: operational amplifier (single-stage, multi-stage, etc.)
  
- Formulate analytical equations to guide design decisions

  - For example: bandwidth, gain

- Size devices

  - Satisfy performance envelope

.. figure:: ./逻辑综合_物理综合.png

:doc:`/chapter4/index` -> :doc:`/chapter5/index` -> :doc:`/chapter6/index` -> :doc:`/chapter7/index` -> :doc:`/chapter8/index`

物理综合
-------------------

.. note::
    ``物理综合`` 的概念 —— Physical synthesis is the process that produces layout of logic circuit

    Physical synthesis not only places and routes the cells of a circuit but also **optimizes** the cell as required by the designer，例如针对 Area、Interconnect length、Power density、Clock distribution 进行优化

``物理综合`` 包括 Floorplanning、Placement、Routing —— 从布图规划开始，到电源规划到完成布局，每一步规划不仅仅要考虑布线的实现，还要在布局完成之后时提供好的数据环境，供时钟树综合使用