# Obstacle detection on head mounted wearable for the vision impaired dataset
 *Peijie Xu, Andy Song, Ke Wang*
 
 *RMIT University, Melbourne, Australia* 

Here we present a novel benchmark dataset with the associated challenge, that is to detect obstacles based on head-mounted sensors and lightweight wearable devices to assist Blind and Visually Impaired individuals (BVIs) navigate in indoor environments.  The challenge encompasses three objectives: (1) as accurately as possible to detect the obstacles on the pathway that likely lead to a collision; (2) as durably as possible on a given amount of battery power for the detection algorithm or model to run; (3) as reliably as possible to compensate natural head turns so nearby objects would not trigger false alarms.  The data provided in the benchmark are collected from the following head mounted sensors: (i) nine low-cost ultrasonic sensors; (ii) one high-end ultrasonic sensor with a larger detection range but higher power consumption; (iii) a 9-Degrees of Freedom (DOF) Inertial Measurement Unit (IMU).  The resulting dataset consists of more than 188,000 unique sequences obtained from multiple subjects walking in three different indoor scenarios.  This benchmark is to facilitate and encourage accurate yet fast obstacle detection solutions that can really benefit BVIs.  

---

*This study is under the ethics approval of the RMIT University College Human Ethics Advisory Network (Approval number: 25031). The study was conducted in accordance with the principles outlined in the Declaration of Helsinki, which ensures the protection of participants' rights and well-being in research studies involving human subjects.*

---

**1. Hardware setting**

|Property        | Characteristics        | Description                                              |
|----------------|------------------------|----------------------------------------------------------|
|                |                        | - 1.5GHz ARM Cortex-A72 CPU                              |
|Raspberry Pi 4B |Onboard processing      | - Quad-core CPU                                          |
|                |                        | - Linux Kernel 5.10 LTS                                  |
|----------------|------------------------|----------------------------------------------------------|
|HC-SR04         |Operating Range         | 2 cm – 400 cm                                            |
|ultrasonic      |Accuracy                | ± 3 mm                                                   |
|sensor          |Effective Angle         | 15°                                                      |
|----------------|------------------------|----------------------------------------------------------|
|MaxSonar-EZ1    |Operating Range         | 30 cm – 500 cm                                           |
|ultrasonic      |Accuracy                | ± 1 %                                                    |
|sensor          |Features                | Real-time automatic calibration                          |
|                |                        |(voltage, humidity, ambient noise)                        |
|----------------|------------------------|----------------------------------------------------------|
|                |Acceleration            | Three axes of acceleration in m/s^2                      |
|BNO085          |Angular Velocity        | Three axes of rotation speed in rad/s                    |
|9-DOF IMU       |Magnetic Field Strength | Three axes of magnetic field sensing in micro Tesla (uT) |
|                |Rotation                | Four point quaternion output                             |

 **2. Obstacle setting**
 
 - A 15-meter-long corridor: One side of the corridor features a clean wall, while the other side is furnished with long sofas.
 - An ’L’-shaped laboratory: includes clean walls on one side, while the opposite side is occupied by long rows of tables.
 - A regular rectangular office setting: with additional conventional benches, cupboards, and cabinets.
 
 ![Figure 1](https://github.com/Dataset4BVI/Benchmark/assets/136880140/d0de569a-59eb-4d84-8099-58cd668cdd60)

To introduce variability and diversity, and to simulate real-world scenarios, different variables are introduced during the walk. This includes walking while maintaining different head orientations, such as facing forward, facing toward the right, or facing toward the left and making head turns. This also includes walking at different speeds, e.g. 0.5 m/s, 0.75 m/s, and 1 m/s.
 
 
 **3. Sensory dataset**

The sensory data are the raw data which are accompanied by timestamps, indicating the time at which each entry is created.
Each entry contains two timestamps, one is the raw system time, and one is the converted time in the format of (HH: MM: SS). Each entry contains 20 sensory readings, including nine distance readings in centimetres from the ultrasonic sensors, one distance reading also in cm from the additional ultrasonic sensor, and 10 readings from the IMU. The 10 attributes are three axes of linear acceleration, three axes of gravitational acceleration, and four attributes derived from quaternion calculations


|raw system time|converted time|accel_x|accel_y|accel_z|gyro_x|gyro_y|gyro_z|quat_i|quat_j|quat_k|quat_real|distance|top1|top2|top3|top4|btm1|btm2|btm3|btm4|btm5|
|---------------|--------------|-------|-------|-------|------|------|------|------|------|------|---------|--------|----|----|----|----|----|----|----|----|----|


**4. Processed and labelled dataset**

All timestamped data entries are verified to ensure synchronisation. Redundant or duplicated data samples are removed. The data process resulted in a total of 188,565 valid data entries. Another important part of this dataset is the labelling, either ‘0’ or ‘1’ to indicate the presence or absence of obstacles.

|accel_x|accel_y|accel_z|gyro_x|gyro_y|gyro_z|quat_i|quat_j|quat_k|quat_real|max_ez1|top1|top2|top3|top4|btm1|btm2|btm3|btm4|btm5|label|
|-------|-------|-------|------|------|------|------|------|------|---------|-------|----|----|----|----|----|----|----|----|----|-----|
 

 
