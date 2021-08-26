Verification
===================

同样 verification 也是广义上的概念（更为准确点，应该称为 Validation ），其主要的做的是

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

- Simulation
  
  - Cycle Based
  - Event Driven

- Formal Verification
- Code Coverage （Assertion Based）
- Analog Mixed Signal Simulation

Prototyping
^^^^^^^^^^^^^^^^^
Build the system on a bread-board to test. This is called bread-boarding

Not feasible for large designs

ASICs can also be verified by using programmable devices such as FPGAs. This is called ``rapid system prototyping``

Simulation
^^^^^^^^^^^^^^^^^^

1. Making a computer model for all modules
2. Performing system level simulation
3. Observing output signals to verify
4. Testing cannot be exhaustive; only certain input patterns are checked Test vectors, test pattern generation

Formal Verification
^^^^^^^^^^^^^^^^^^^^^^^
1. the algorithm that the chip implements is re-constructed from gate level netlists
2. The Boolean expressions are verified to ensure correctness
3. No need of test vector

Testing(DFT)
-------------------


Timing Verification

----------------------

Timing Verification 是采用时序分析等方法验证设计是否满足时序收敛（timing closure），具体的时序检验工作包括：

- 反标（back-annotation）
- 时序与功耗的检验
- 时序与信号完整性的检验
- （低功耗纳米技术节点）“多模式多端角”（multi-mode multi corner， ``MMMC`` ） [#MMMC]_ 检验

.. [#MMMC] 逻辑综合用时序库做时序分析时，最为普遍的应用是三种时序库，即最佳、典型、最差时序库。由于每一种时序库都是根据相应的工艺环境（PVT）和工作条件（operating condition）而建立，通常又将时序库标定的数据称为 ``工艺角`` 。在物理实现过程中，通过实际布线后，由不同的时序工艺角会导出 ``RC工艺角`` 数据，拟将多种工艺和工作条件导出的时序工艺库（ ``工艺角`` ）和布线后的 ``RC工艺角`` 两者统称为 ``多端角``

时序  
^^^^^^^^^^^^^^^^^^^

通过 :doc:`/chapter9/index` 提取布线后寄生参数，最终转化为 `sdf` 文件，进行 post-layout gate level simulation 、 :doc:`/chapter10/index`


纳米节点下集成电路的时序分析离不开考虑电源的影响，要预先或同时考虑 :doc:`/chapter11/index`;同时需要考虑噪声对时序的影响，故要预先或同时考虑 :doc:`/chapter12/index` 的相互牵制关系

面积
^^^^^^^^^^^^^^^

拥堵
^^^^^^^^^^^^^^^

Designs are considered **congested** when the wires needed to connect design components
become greater than the space available to put the wires.

功耗
^^^^^^^^^^^^^^^^^^

信号完整性
^^^^^^^^^^^^^^^^^^

可靠性
----------------------------

Physical Verification
----------------------------