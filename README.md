# SIREN_Datasets

#### Introduction
The SIREN_dataset is designed for maritime environments and includes data from sensors such as Vision, mmWave Radar, and WiFi (partially). It defines five key behaviors in this context: Observing, Steering, Walking, Sitting, and In-place Activity.


#### Download Links
Dataset: https://pan.baidu.com/s/1Fgi-XbkebpW7AfK_L4BfzA?pwd=1234 <br>
Annotation File: https://pan.baidu.com/s/1H2gnUMHPNSt5Nqt3Bde4uw?pwd=1234 

The annotation file should be named label.csv with the following format:
|    file_id   | frame_start | frame_end |       activity       |
|--------------|-------------|-----------|----------------------|          
| 202302170944 |     945     |    945    | In_situ_activities   |
| 202302170944 |     1119    |    1179   | Operating_the_rudder |
| 202302170944 |     1953    |    2013   | sit                  |
| 202302170944 |     3445    |    3445   | walk                 |
| 202302170944 |     669     |    729    | watch                |

- **file_id** Filename, corresponding to the datetime in the table below.
- **frame_start** The starting frame of an activity in the video.
- **frame_end** The ending frame of an activity in the video.
- **activity** The coarse-grained labeled activity in the video, including (In-situ Activity, Operating the Rudder, Sitting, Walking, and Observing).

#### Dataset Structure

```
|-- SYNCHRONIZATION
    |-- datetime
        - Data collection date (e.g., 2023-02-17 09:44)
        |-- RADAR 
        |   - mmWave Radar data collection
        |   |-- datetime.mat
        |   - mmWave Radar raw data (e.g., 2023-02-17 09:45:16.mat)
        |-- VIDEO
        |   - Visual sensor data collection
        |   |-- datetime
        |   |   - Timestamp of visual sensor data collection (e.g., 2023-02-17 09:44)
        |   |-- frame.pkl
        |   |   - Timestamps of each video frame
        |   |-- labels.npy
        |   |   - Activity labels detected by PySlowFast
        |   |-- rgb.avi
        |   |   - Video file
        |   |-- timestamp.npy
        |   |   - Start and end times of each activity
        |-- WiFi
        |   |-- datetime.mat
        |   |   - WiFi raw data (e.g., 2023-02-17 09:45:12.mat)
        |-- initial_sync_index.npy
        |   - Initial synchronization timestamps between visual sensor and mmWave Radar
```
