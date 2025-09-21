# alterego_msgs

This package contains the custom messages and services used by AlterEGO.

## ROS2 Migration

The package has been migrated from ROS1 (catkin + `message_generation`) to ROS2 (ament + `rosidl`).

Key changes:
* Uses `ament_cmake` and `rosidl_default_generators`.
* `CMakeLists.txt` now calls `rosidl_generate_interfaces` with message/service files.
* Added missing `MarkerInfo.msg` to the build list and `geometry_msgs` dependency.
* Removed ROS1-only dependencies (`actionlib_msgs`) since no actions are currently defined. Re-add if you introduce action interfaces.

### Build

From the root of your ROS2 workspace:
```bash
colcon build --packages-select alterego_msgs
source install/setup.bash
```

### Usage

Add to another package's `package.xml`:
```xml
<depend>alterego_msgs</depend>
```
And in its `CMakeLists.txt`:
```cmake
find_package(alterego_msgs REQUIRED)
```

Then include headers (C++) or import in Python:
```python
from alterego_msgs.msg import EgoArms
from alterego_msgs.srv import NavService
```

---
BSD-3-Clause License.
