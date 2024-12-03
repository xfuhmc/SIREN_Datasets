# VIMMFI_Datasets

#### 介绍
船舶环境下的驾驶员行为感知数据集，涉及VISION、WiFi、mmWave Radar、IMU等sensor
包括各种数据的处理函数、代码等
python版本为3.8，请运行pip install -r requirements.txt进行环境配置

#### 数据集下载地址
数据集：https://pan.baidu.com/s/1Fgi-XbkebpW7AfK_L4BfzA?pwd=1234 <br>
标注文件：https://pan.baidu.com/s/1H2gnUMHPNSt5Nqt3Bde4uw?pwd=1234 

标注文件应为label.csv，格式如下:
|    file_id   | frame_start | frame_end |       activity       |
|--------------|-------------|-----------|----------------------|          
| 202302170944 |     945     |    945    | In_situ_activities   |
| 202302170944 |     1119    |    1179   | Operating_the_rudder |
| 202302170944 |     1953    |    2013   | sit                  |
| 202302170944 |     3445    |    3445   | walk                 |
| 202302170944 |     669     |    729    | watch                |

- **file_id** 文件名，等同于下表中的datetime。
- **frame_start** 视频帧中一个行为的起始帧。
- **frame_end** 视频帧中一个行为的起始帧。
- **activity** 视频帧中一个行为的粗粒度标定结果，包括（原地活动、操舵、坐着、行走、瞭望）。

根据标注文件对Vision、mmWave Radar、WiFi、IMU等的切分代码请参照segmenttation.py文件，处理教程见vision_and_mmWave_process_tutorial.py以及vision_and_wifi_process_tutorial.py

#### 数据集格式如下

```
|-- SYNCHRONIZATION
    |-- datetime
        - 该次数据采集的日期 (e.g., 2023-02-17 09:44)
        |-- RADAR 
        |   - 毫米波雷达数据采集
        |   |-- datetime.mat
        |   - 毫米波雷达 raw data (e.g., 2023-02-17 09:45:16.mat)
        |-- VIDEO
        |   - 视觉传感器数据采集
        |   |-- datetime
        |   |   - 视觉传感器数据采集的时间 (e.g., 2023-02-17 09:44)
        |   |-- frame.pkl
        |   |   - 视频数据每一帧的时间戳
        |   |-- labels.npy
        |   |   - 由 PySlowFast 初始检测的行为标签
        |   |-- rgb.avi
        |   |   - 视频
        |   |-- timestamp.npy
        |   |   - 每个行为的开始时间和结束时间
        |-- WiFi
        |   |-- datetime.mat
        |   |   - WiFi raw data (e.g., 2023-02-17 09:45:12.mat)
        |-- initial_sync_index.npy
        |   - 视觉传感器和毫米波雷达初步同步的时间戳
```
