布局I/O单元
======================

It is critical to functional operation of an ASIC design to insure:

- the pads have adequate power and ground connections
- the pads are placed properly

目的：eliminate electromigration and current-switching noise related problems.

.. warning::
    设置 I/O Pad Cell 约束

以 ICC 为例，在 initializing the floorplan 之前，首先为 I/O pad cells 设置约束：

.. code-block:: console
    :linenos:

    $ set_pad_physical_constraints

约束内容为指定 the pad cell ordering, orientation, placement side, offset from die edge, and pad-to-pad spacing for each I/O pad 

.. figure:: ./pad约束.png

.. note::
    上述工作即为设置管脚约束的 ``tdf`` 文件了，它指定了每个 IO cell 在整个芯片中的位置和排列顺序 —— 对于 Chip level 的设计而言，该文件主要用来定义设计中所有 IO 以及 IO Corner 的位置（上下左右的方位以及排列顺序，也可以定义具体的坐标）

    如果是 Block Level的设计而言，因为设计中没有IO cell，所以可以读入pin顺序和位置的 ``tdf`` 文件 —— 对于Block level的设计而言，它用来指定所有pin的位置和所用的metal的层次。

之后在执行

.. code-block:: console
    :linenos:

    $ initialize_floorplan

在读入管脚约束文件（ ``.tdf`` 文件）后，可以创建Floorplan得到芯片大概的物理形状和尺寸，在这一步执行完毕之后，IO pad cell 或者 pin 就会按照前面的约束进行摆放。

P.S. The ``initialize_floorplan`` command places constrained pads first. Any unconstrained pads are placed next, using any available pad location. The tool does not place unconstrained pads between consecutively ordered constrained pads

.. figure:: ./pad_placement.png