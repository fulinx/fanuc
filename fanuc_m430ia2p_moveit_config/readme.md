# fanuc_m430ia2p_moveit_config

## Overview

This package is part of the [ROS-Industrial][] program. See the main [fanuc][]
page on the ROS wiki for more information on usage.

## Known issues

### Incorrect acceleration limits

The true acceleration limits for the manipulator supported by this package are
currently unknown. Because of this, this package is configured to use the
default MoveIt acceleration limits of 1/5th max joint velocity.

See also [fanuc/issue 49][] on the `fanuc` issue tracker.

### Poor planning performance

Some users have reported poor planning performance (abnormally long planning
times, strange paths) when using the default (ie: LBKPIECE1) planner
configuration in combination with certain robot models. At least the Universal
Robot models and some KUKA LWR4 variants are known to trigger this behaviour in
MoveIt / OMPL (see [ur/issue 193][] on the `universal_robot` repository).

This issue has not been observed with or reported for any of the MoveIt
configurations in the `fanuc` or `fanuc_experimental` repositories, but is
included here in case users run into it.

A possible work-around is to plan using the `RRTConnect` planner, and / or to
set `planning attempts` to 1.



[ROS-Industrial]: http://wiki.ros.org/Industrial
[fanuc]: http://wiki.ros.org/fanuc
[fanuc/issue 49]: https://github.com/ros-industrial/fanuc/issues/49
[ur/issue 193]: https://github.com/ros-industrial/universal_robot/issues/193
