Verification
===================

同样 verification 也是广义上的概念，其主要的做的是

- Simulate circuits (typically Spice or derivatives)
 
  - Validate design across multiple operating environments

- Measure circuit parameters

  - Evaluate analytical equations based on simulated values

- Verify assumptions

  - For example: check transistors are operating correctly

- Goal: explore limitations of the circuit

  - Figure out where and how the circuit breaks

功能验证
-------------------

functional verification & formal verification

时序
-------------------

通过 :doc:`/chapter9/index` 提取布线后寄生参数，最终转化为 `sdf` 文件，进行 post-layout gate level simulation 、 :doc:`/chapter10/index`


纳米节点下集成电路的时序分析离不开考虑电源的影响，要预先或同时考虑 :doc:`/chapter11/index`;同时需要考虑噪声对时序的影响，故要预先或同时考虑 :doc:`/chapter12/index` 的相互牵制关系

logic simulation

面积
-------------------

拥堵
-------------------

Designs are considered **congested** when the wires needed to connect design components
become greater than the space available to put the wires.

功耗
-------------------

信号完整性
-------------------

可靠性
-------------------