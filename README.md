# ar_track_alvar

See [ROS wiki](http://wiki.ros.org/ar_track_alvar) for the users document.

To run the tracking using a RealSense camera, we need:

## Usage Instructions
- Install the RealSense ROS packages for your ROS distribution. For ROS Noetic, these are:
  - `ros-noetic-realsense2-camera`
  - `ros-noetic-rgbd-launch`
  - `ros-noetic-realsense2-description`
- Connect Intel RealSense camera. Verify that you're able to see depth & RGB camera outputs using the `realsense-viewer` program.
- Attach printed AR tags (of known dimensions) to the object you want to detect.
- Clone this package to a ROS workspace
- Launch realsense camera node (change device_type value to suit your camera):
```sh
roslaunch realsense2_camera rs_rgbd.launch device_type:=d435 enable_depth:=true
```
- Run this package:
```sh
roslaunch ar_track_alvar realsense_depth_track_indiv.launch
```
- Visualize marker using Rviz: Launch rviz > Add frame > Add point cloud > Tf
- Verify published pose by running `rostopic echo /ar_pose_marker`
