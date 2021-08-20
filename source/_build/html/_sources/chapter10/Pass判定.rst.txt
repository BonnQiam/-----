Pass判定
=========================

synthesis/floorplanning/placement level
------------------------------------------

At synthesis/floorplanning/placement level,  a lot of variables are not taken into account at this stage, it is preferred to **meet setup timing with some margin** so as to accommodate the degradation in setup timing due to those variables later in the design cycle. 

.. note::

    These variables include **clock skew** , **uncommon path in clock network** , **data nets detouring** during actual routing and **crosstalk effects**

CTS level
---------------------------

When clock tree is built, we have **actual clock skew numbers**. So, STA needs to be run to **check** if the **margins** for clock skew need to be accommodated into some more optimization (area, power or timing) due to actual clock skews and uncommon clock paths being different than the margin assumed. 

routing
---------------------

Similarly, after data routing, we can run STA with actual parasitic values and crosstalk effects, thereby signing off timing using STA by running across all possible corner scenarios.