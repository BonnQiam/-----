Design Flow
===========================

Implementation
--------------------------


:doc:`/chapter4/index` -> :doc:`/chapter5/index` -> :doc:`/chapter6/index` -> :doc:`/chapter7/index` -> :doc:`/chapter8/index`

从布图规划开始，到电源规划到完成布局，每一步规划不仅仅要考虑布线的实现，还要在布局完成之后时提供好的数据环境，供时钟树综合使用

Verification
--------------------------

功能验证
----------------------

functional verification & formal verification

时序
^^^^^^^^^^^^^^^

通过 :doc:`/chapter9/index` 提取布线后寄生参数，最终转化为 `sdf` 文件，进行 post-layout gate level simulation 、 :doc:`/chapter10/index`


纳米节点下集成电路的时序分析离不开考虑电源的影响，要预先或同时考虑 :doc:`/chapter11/index`;同时需要考虑噪声对时序的影响，故要预先或同时考虑 :doc:`/chapter12/index` 的相互牵制关系

logic simulation

Optimization
-----------------------------

.. note::
    

时序优化以修复时序违例

工具链
-----------------------

.. toctree::
    :maxdepth: 3
    :caption: Contents:

    ./PrimeTime_Suite.rst
    ./Prime_Rail.rst