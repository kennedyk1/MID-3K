# MID-3K (Multimodal ISR Dataset with 3000 images)

[https://github.com/kennedyk1/MID-3K](https://github.com/kennedyk1/MID-3K)


This dataset, collected by the [ISR (Institute of Systems and Robotics)](https://www.isr.uc.pt/) Team, is a new multi-sensory dataset that was organized, calibrated, curated, and annotated. The sensory data was collected using ROS and a Jackal Clearpath mobile robot (see Fig. 1), operating in two indoor environments: three floors of the [DEEC](https://www.uc.pt/fctuc/deec/) building and two floors of [DEI](https://www.uc.pt/fctuc/dei/) building at the [University of Coimbra](https://www.uc.pt/), Polo 2, Portugal.

This main repository provides information about the Dataset, which consists of 3,083 scenes, each containing 4 images from different modalities (RGB, thermal, depth, and intensity). The images are organized by modality into separate repositories, with the links listed below:

- [MID-3K RGB Modality](https://github.com/kennedyk1/MID-3K-rgb): Contains RGB images.
- [MID-3K Thermal Modality](https://github.com/kennedyk1/MID-3K-thermal): Contains thermal images.
- [MID-3K Depth Modality](https://github.com/kennedyk1/MID-3K-depth): Contains depth images data captured by LiDAR.
- [MID-3K Intensity Modality](https://github.com/kennedyk1/MID-3K-intensity): Contains intensity images data captured by LiDAR.

You can clone any of these modalities to your local environment using the `git clone` command. Simply open the terminal and follow these steps:

   ```bash
   git clone https://github.com/kennedyk1/MID-3K-rgb
   git clone https://github.com/kennedyk1/MID-3K-thermal
   git clone https://github.com/kennedyk1/MID-3K-depth
   git clone https://github.com/kennedyk1/MID-3K-intensity
   ```
This dataset includes a [metainfo.csv](https://github.com/kennedyk1/MID-3K/raw/main/metainfo.csv) file that provides detailed information about each image, including the collection date and time, department, floor, and the number of thermal and RGB annotations. This file can be useful for splitting the dataset into training, validation, and test sets for CNN training, allowing for organized and efficient dataset management.


<table>
<tr>
<td align="center">
<img src="img_files/jackal.png" alt="Jackal Clearpath"/>
</td>
</tr>
<tr><td><em>Fig. 1: Sensors on mobile robot, Clearpath Jackal model: (RGB) Ximea MQ013CG-E2, (Thermal) Flir Boson 640 LWIR, and (LiDAR) Ouster OS1-64-U.</em></td></tr>
</table>

<table>
<tr>
<td align="center">
<img src="img_files/calib.png" alt="Sensors Calibration"/>
</td>
</tr>
<tr><td><em>Fig. 2: Sample images used for sensors calibration. The composite image shows the <i>RGB</i> (left) and <i>thermal</i> (center) images, and the projection of 3D-LiDAR points over the RGB image (right). The first two images are used for sensor calibrations, while the last one is used to verify if the LiDAR-camera calibration is properly aligned.</em></td></tr>
</table>


The dataset consists of 3083 selected frames, containing RGB, thermal, depth-map and intensity-map images  (last two generated from LiDAR) totaling 12332 image files (see Fig. 2). The sensors have been calibrated, but a small temporal misalignment is present due to hardware limitations.

<table>
    <tr>
        <td><img src="img_files/r.png" alt="RGB Modality"/></td>
        <td><img src="img_files/t.png" alt="Thermal Modality"/></td>
        <td><img src="img_files/d.png" alt="Depth Modality"/></td>
        <td><img src="img_files/i.png" alt="Intensity Modality"/></td>
    </tr>
    <tr>
        <td colspan="4" align="center"><em>Fig. 2: Dataset frame-examples composed of RGB, Thermal, Depth-Map and Intensity-Map modalities.</em></td>
    </tr>
</table>

The depth and intensity images representation was generated from the `projected` LiDAR point clouds using a modified bilateral filter. In particular, each LiDAR point cloud is projected on the RGB image-plane, considering the Camera-LiDAR calibration matrix, and then a sliding-window based weighing function, dependent on the range dispersion, is used to interpolate the points inside the mask therefore generating a dense representation.

<table>
  <tr>
    <th></th>
    <th>RGB</th>
    <th>Thermal</th>
    <th>Depth</th>
    <th>Intensity</th>
  </tr>
  <tr>
    <td>Model</td>
    <td align="center"><em>Ximea MQ013CG-E2</em></td>
    <td align="center"><em>FLIR BOSON 640 LWIR</em></td>
    <td align="center"><em>OUSTER OS1-64-U</em></td>
    <td align="center"><em>OUSTER OS1-64-U</em></td>
  </tr>
  <tr>
    <td>Type</td>
    <td align="center"><em>Colour Camera</em></td>
    <td align="center"><em>Thermal Camera</em></td>
    <td align="center"><em>LiDAR</em></td>
    <td align="center"><em>LiDAR</em></td>
  </tr>
  <tr>
    <td>Spec.</td>
    <td align="center"><em>1280x1024 pixels, 1.3 MP</em></td>
    <td align="center"><em>640x512 pixels</em></td>
    <td align="center"><em>Vert. Res.: 64 channels<BR>Hor. Res.: 2048 points</em></td>
    <td align="center"><em>Vert. Res.: 64 channels<BR>Hor. Res.: 2048 points</em></td>
  </tr>
  <tr>
    <td>Image Type</td>
    <td align="center"><em>.png</em></td>
    <td align="center"><em>.png</em></td>
    <td align="center"><em>.png</em></td>
    <td align="center"><em>.png</em></td>
  </tr>
  <tr>
    <td>Total Images</td>
    <td align="center"><em>3,083</em></td>
    <td align="center"><em>3,083</em></td>
    <td align="center"><em>3,083</em></td>
    <td align="center"><em>3,083</em></td>
  </tr>
  <tr>
    <td>Total Files Annotations</td>
    <td align="center"><em>3,083 txt files</em></td>
    <td align="center"><em>3,083 txt files</em></td>
    <td align="center"><em>3,083 txt files</em></td>
    <td align="center"><em>3,083 txt files</em></td>
  </tr>
  <tr>
    <td>Total Annotations (people)</td>
    <td align="center"><em>10,824</em></td>
    <td align="center"><em>10,881</em></td>
    <td align="center"><em>10,824¹</em></td>
    <td align="center"><em>10,824¹</em></td>
  </tr>
  <tr>
    <td>Dataset Size</td>
    <td align="center"><em>~1.3 GB</em></td>
    <td align="center"><em>~1.3 GB</em></td>
    <td align="center"><em>~977 MB</em></td>
    <td align="center"><em>~1.7 GB</em></td>
  </tr>
  <tr>
    <td>Images Resolution</td>
    <td align="center"><em>640x512</em></td>
    <td align="center"><em>640x512</em></td>
    <td align="center"><em>640x512</em></td>
    <td align="center"><em>640x512</em></td>
  </tr>
  <tr>
    <td>Annotation Format</td>
    <td align="center"><em>YOLO xywhn²</em></td>
    <td align="center"><em>YOLO xywhn²</em></td>
    <td align="center"><em>YOLO xywhn²</em></td>
    <td align="center"><em>YOLO xywhn²</em></td>
  </tr>
  <tr>
    <td colspan="5" align="center"><em>¹ The labels from the RGB modality were used because the LiDAR was calibrated with the RGB camera.<BR>² YOLO normalized xywh format <b>class x_center y_center width height</b></em></td>
  </tr>
</table>


<table style="text-align: center;">
  <thead>
    <tr><td colspan="7" align="center"><b>Daily Distribution of Images in the Dataset</b></td></tr>
    <tr align="center">
      <td><b>Day</b></td>
      <td><b>Date</b></td>
      <td><b>Images</b></td>
      <td><b>Thermal Annotations</b></td>
      <td><b>RGB Annotations</b></td>
      <td><b>Folder</b></td>
    </tr>
  </thead>
  <tbody>
    <tr align="center">
      <td>#1</td>
      <td>29-Apr</td>
      <td>368 (11.9%)</td>
      <td>1368 (12.6%)</td>
      <td>1404 (13.0%)</td>
      <td><b>Test</b></td>
    </tr>
    <tr align="center">
      <td>#2</td>
      <td>07-May</td>
      <td>332 (10.8%)</td>
      <td>1075 (9.9%)</td>
      <td>1072 (9.9%)</td>
      <td><b>Train</b></td>
    </tr>
    <tr align="center">
      <td>#3</td>
      <td>08-May</td>
      <td>337 (10.9%)</td>
      <td>1658 (15.2%)</td>
      <td>1651 (15.3%)</td>
      <td><b>Test</b></td>
    </tr>
    <tr align="center">
      <td>#4</td>
      <td>09-May</td>
      <td>1333 (43.2%)</td>
      <td>4199 (38.6%)</td>
      <td>4125 (38.1%)</td>
      <td><b>Train</b></td>
    </tr>
    <tr align="center">
      <td>#5</td>
      <td>16-May</td>
      <td>713 (23.1%)</td>
      <td>2581 (23.7%)</td>
      <td>2572 (23.8%)</td>
      <td><b>Train</b></td>
    </tr>
    <tr align="center">
      <td><b>-</b></td>
      <td><b>-</b></td>
      <td><b>3083</b></td>
      <td><b>10881</b></td>
      <td><b>10824</b></td>
       <td><b></b></td>
    </tr>
  </tbody>
</table>

## Visit our datasets through the links below.
- MID-1K - [Multimodal ISR Dataset with 1100 images](https://kennedyk1.github.io/MID-1K/) (*RGB, thermal and depth*)
- MID-3K - [Multimodal ISR Dataset with 3000 images](https://kennedyk1.github.io/MID-3K/) (*RGB, thermal, depth and intensity*)


## References

- Sousa, E., Mota, K. O., Gomes, I. P., Garrote, L., Wolf, D. F., & Premebida, C. (2023, September). **Late-Fusion Multimodal Human Detection Based on RGB and Thermal Images for Robotic Perception**. In *2023 European Conference on Mobile Robots (ECMR)* (pp. 1-6).
- Kennedy O. S. Mota, Luís Garrote, Cristiano Premebida. **Multimodal Human Detection using RGB, Thermal and LiDAR modalities for Robotic Perception**. *In 2024 IEEE 20th International Conference on Automation Science and Engineering (CASE), Bari, Italy.* [Preview Document](https://github.com/kennedyk1/MID-3K/blob/main/Multimodal%20Human%20Detection%20Using%20YOLO%20and%20Representation%20Learning%20for%20Robot%20Perception.pdf)
