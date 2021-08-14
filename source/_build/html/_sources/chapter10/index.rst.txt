静态时序分析
========================


.. toctree::
    :maxdepth: 3
    :caption: Contents:

    ./静态时序分析的基本原理.rst
    ./延时模型.rst
    ./统计静态时序分析.rst


静态时序分析贯穿于设计过程中的各个阶段，从RTL :doc:`/chapter4/index` 到 :doc:`/chapter6/index` 、:doc:`/chapter7/index` 、 :doc:`/chapter8/index` ，对各个阶段的物理实现方案进行评估的一大侧重点就是使用静态时序分析工具进行时序分析，检查其是是否满足设计的约束条件

其基本过程是根据时序约束文件，使用多种 PVT 条件（诸如最佳、典型、最差）分析不同的时序路径类型和时钟定义，检查关键时序 setup、hold 以及其他约束是否实现或违例

.. warning::
    纳米节点下集成电路的时序分析离不开考虑电源的影响，要预先或同时考虑 :doc:`/chapter11/index`;同时需要考虑噪声对时序的影响，故要预先或同时考虑 :doc:`/chapter12/index` 的相互牵制关系
