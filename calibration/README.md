# Calibration matrices

Each directory contains the single canonical YAML for one sensor pair:

| Pair | File | Point transform |
| --- | --- | --- |
| COLOR camera and LiDAR | `color_lidar/calibration.yaml` | `p_color = T_color_from_lidar * p_lidar_h` |
| THERMAL camera and LiDAR | `thermal_lidar/calibration.yaml` | `p_thermal = T_thermal_from_lidar * p_lidar_h` |
| COLOR and THERMAL cameras | `color_thermal/calibration.yaml` | `p_thermal = T_thermal_from_color * p_color_h` |

`K` is the 3x3 camera-intrinsic matrix. `D` contains OpenCV radial-tangential distortion coefficients in `[k1, k2, p1, p2, k3]` order. `T_*_from_*` is a 4x4 homogeneous transform; its translation column uses the `translation_unit` stated in that file.

The folder intentionally excludes calibration input names, images, per-sample errors, rejection logs, and generated-result duplicates.
