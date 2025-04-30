# airport-webcam
A simple webcam that overlays METAR and AQI data on video feed.

## Preview of Webcam
An example image from the webcam with METAR and AQI data overlayed on the video graphic

<picture>
  <img src="Website_Example.png">
</picture>

## Overview

```mermaid
flowchart TD;
  A[Antenna] --> B[Airband Receiver];
  C[Security Camera] --> |RTSP Stream| D[RPi Server FFMPEG];
  B --> |Audio Input| C;
  E[Weather Data] --> |API/Webscrape| F[Generate Overlay Image];
  GG[PurpleAir Sensor] --> G;
  G[Air Quality Data] --> |API Call| F;
F --> |PNG overlay image| D;
D --> |SRT HEVC| H[MediaConnect Input];
H --> I[MediaLive];
K[Image Overlay Scheduler] --> I;
I --> |Generate ABR Ladder| J[MediaPackage];
I --> |RTMP Output 5Mbps| N[YouTube];
J --> |HLS ABR Ladder| L[CloudFront Distribution];
L --> M[Video.JS Player];
```
