Zones
=====

Zones are used to demarcate 3D regions of space within scenes. There are various types of zones, each of which have
different behaviours when Twinsen enters or interacts with them:

- *teleport zones* transport Twinsen to a different scene when entered
- *camera zones* change the camera position and angle when entered
- *sceneric zones* define areas of the scene used for "is actor in zone?" queries in scripts
- *fragment zones* define an area of the scene's terrain that can be dynamically shown or hidden
- *bonus zones* dispense items when interacted with
- *text zones* are used to implement signs and say dialogue when interacted with
- *ladder zones* provide vertical movement
- *conveyor zones* move actors which stand within them
- *spike zones* deal damaged when entered (floor spikes, traps, etc)
- *rail zones* are used to control minecart movement

All zones are cuboid in shape.

Zone format
-----------

Zones are stored as part of the scene containing the zone:

.. code-block::
    :caption: zone data layout

    {
        i32         x0
        i32         y0
        i32         z0
        i32         x1
        i32         y1
        i32         z1
        i32         info0
        i32         info1
        i32         info2
        i32         info3
        i32         info4
        i32         info5
        i32         info6
        i32         info7
        i16         type
        i16         value
    }

- *x0*, *y0*, *z0*: first corner defining the zone cuboid
- *x1*, *y1*, *z1*: opposite corner defining the zone cuboid
- *info0..7*: zone parameters; interpretation depends on the zone type
- *type*: the type of zone
- *value*: zone parameter; interpretation depends on the zone type

=========       ====
Zone type       Name
=========       ====
0               Teleport
1               Camera
2               Sceneric
3               Fragment
4               Bonus
5               Text
6               Ladder
7               Conveyor
8               Spike
9               Rail
=========       ====

The documentation below for each of the zone types describes how the flags are interpreted, as loaded from the scene.
The LBA engine modifies some of these values at run-time in order to avoid allocating additional memory; these run-time
uses and modifications are not documented here.

Teleport zones
~~~~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Destination scene
info0                   Destination x
info1                   Destination y
info2                   Destination z
info3                   Destination angle
info4                   Zone scripting ID
info5                   Door flags: bit 0 - for exterior scenes, don't activate zone until Twinsen collides with the door
info6                   Collision flags: bit 0 - don't adjust Twinsen to fix collisions
info7                   Enable flags: bit 0 - zone is enabled
=========               ===========

Teleport zones can be enabled or disabled from script by using the SET_TELEPORT_ZONE opcode.

Camera zones
~~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   Camera x
info1                   Camera y
info2                   Camera z
info3                   Camera alpha angle
info4                   Camera beta angle
info5                   Camera gamma angle
info6                   View distance
info7                   Enable flags: bit 0 - zone is enabled
=========               ===========

Camera zones can be enabled or disabled from script by using the SET_CAMERA opcode.

Sceneric zones
~~~~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   -unused-
info1                   -unused-
info2                   -unused-
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

Sceneric zones can be used from scripts by checking whether an actor is within them by using the ZONE and ZONE_OBJ
conditions.

Fragment zones
~~~~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   Fragment number
info1                   -unused-
info2                   Enable flags: bit 0 - zone is enabled
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

Fragment zones can be enabled or disabled from script by using the SET_FRAGMENT opcode.

Bonus zones
~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   -unused-
info0                   Bonus type
info1                   Bonus quantity
info2                   -unused-
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

Bonus zones are not scriptable.

Text zones
~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Message ID
info0                   Text colour
info1                   Associated camera zone (zero for none)
info2                   Direction
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

Text zones are not scriptable.

The direction values seem appropriate for use as a bitmask but the LBA engine checks for equality, not a bit test, so
each text zone can only face a single direction. Double-sided signs would require two sign zones, one on each side.

==============          ===========
Zone direction          Description
==============          ===========
1                       Sign faces North
2                       Sign faces South
4                       Sign faces East
8                       Sign faces West
==============          ===========

Ladder zones
~~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   Enabled
info1                   -unused-
info2                   -unused-
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

Ladder zones can be enabled or disabled from script using the SET_LADDER_ZONE opcode. Their enabled state can be queried
using the LADDER condition.

Conveyor zones
~~~~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   -unused-
info1                   Enabled
info2                   Direction
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

Conveyor zones can be enabled or disabled from script using the SET_CONVEYOR_ZONE opcode.

The direction values seem appropriate for use as a bitmask but the LBA engine checks for equality, not a bit test.

==============          ===========
Zone direction          Description
==============          ===========
1                       Conveyor travels North
2                       Conveyor travels South
4                       Conveyor travels East
8                       Conveyor travels West
==============          ===========

Spike zones
~~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   -unused-
info1                   Damage
info2                   Rearm time
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========

The damage of spike zones can be controlled from script using the SET_SPIKE_ZONE opcode. Setting the damage to zero will
disable the spike zone; setting it to a non-zero value will enable it.

Rail zones
~~~~~~~~~~

=========               ===========
Parameter               Description
=========               ===========
param                   Zone scripting ID
info0                   Enabled
info1                   Switch set
info2                   -unused-
info3                   -unused-
info4                   -unused-
info5                   -unused-
info6                   -unused-
info7                   -unused-
=========               ===========
