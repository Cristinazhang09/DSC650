---
title: Assignment 1
subtitle: Computer performance, reliability, and scalability calculation
author: Jingru Zhang
---

## 1.2 

#### a. Data Sizes

| Data Item                                  | Size per Item | 
|--------------------------------------------|--------------:|
| 128 character message.                     | 128 Bytes     |
| 1024x768 PNG image                         | 1 MB          |
| 1024x768 RAW image                         | 7.5 MB        | 
| HD (1080p) HEVC Video (15 minutes)         | 36 MB         |
| HD (1080p) Uncompressed Video (15 minutes) | 36,000 MB     |
| 4K UHD HEVC Video (15 minutes)             | 228 MB        |
| 4k UHD Uncompressed Video (15 minutes)     | 228,000 MB    |
| Human Genome (Uncompressed)                | 1.5 GB        |

1. A character is 8 bits(1 byte), thus, 128 character message is 128 Bytes.
2. The totle number of pixels is 1024\*768=786,432 pixels. If use RGB, each pixel in the image needs 3 bytes in memory, one for the Red channel, one for the Green channel, and one for the Blue channel.So the total file size 786,432\*3=2,359,296 bytes= 2,359296/1024/1024=2.25MB. PNG is compressed, if use a typical compression ratio is 2, then the size is about 1 MB
3. Assume raw image has a depth of 10, then it is 1024 * 768 * 10/1024/1024 = 7.5MB
4. Using 30 fps and 8 bit depth, I have 15 miniutes = 15* 60 s= 900 s, HEVC is known to have a common compression ratio of 1000, so a 15 minutes HEVC video is, 900\*30\*1290\*1080\*8/8/1000/1024/1024, which is roughly 36 MB.
5. If uncompressed, the size will be 1000 times more than the number in 4, which makes it 36,000 MB.
6. For 4k, the size of 15 mins HEVC video will be: 900\*30\*4096\*2160\*8/8/1000/1024/1024, which is about 228 MB.
7. If uncompressed, the size is about 1000 times larger, which is about 228,000 MB.
8. 6\*10^9 base pairs/diploid genome x 1 byte/4 base pairs = 1.5GB

#### b. Scaling

|                                           | Size     | # HD | 
|-------------------------------------------|---------:|-----:|
| Daily Twitter Tweets (Uncompressed)       | 64 GB    |  1   |
| Daily Twitter Tweets (Snappy Compressed)  | 43 GB    |  1   |
| Daily Instagram Photos                    | 375 TB   | 38   |
| Daily YouTube Videos                      | 104 TB   | 11   |
| Yearly Twitter Tweets (Uncompressed)      | 23 TB    |  3   |
| Yearly Twitter Tweets (Snappy Compressed) | 15 TB    |  2   |
| Yearly Instagram Photos                   | 136875 TB|13688 |
| Yearly YouTube Videos                     | 37960 TB | 3796 |

1. About 500 million tweets are sent per day, the umcompressed daily storage needed is 500 million\*128 bytes, which is about 64,000,000,000 bytes, which is about 64 GB.
2. Snappy compression has a 1.5-1.7x ratio for plain text, if use 1.5, then the storage for compressed data is about 43 GB.
3. The storage size is 0.75 * 500000000 * 1MB = 375000000 MB, which is about 375 TB.
4. The daily video is 500 hours * 60 * 24 = 720000 hours = 720000 * 60 minutes, which is 720000 * 4 per 15 minutes length. So the storage is about 720000 * 4 * 36 MB = 103680000 MB, which is about 104 TB.
5. 64 GB * 365 = 23360 GB, which is about 23 TB.
6. 43 GB * 365 = 15695 GB, which is about 15 TB.
7. 375 TB * 365 = 136875 TB.
8. 104 TB * 365 = 37960 TB.

#### c. Reliability
|                                    | # HD | # Failures |
|------------------------------------|-----:|-----------:|
| Twitter Tweets (Uncompressed)      | 3    |      <1    |
| Twitter Tweets (Snappy Compressed) | 2    |      <1    |
| Instagram Photos                   | 13688|     122    |
| YouTube Videos                     | 3796 |      34    |

Note, the failure rate  used is 0.89%. The number of failures is calculated through #Failures =  #HD * Failure_Rate

#### d. Latency

|                           | One Way Latency      |
|---------------------------|---------------------:|
| Los Angeles to Amsterdam  | 30 ms                |
| Low Earth Orbit Satellite | 40 ms                |
| Geostationary Satellite   | 600 ms               |
| Earth to the Moon         | 1281 ms              |
| Earth to Mars             | 3 minutes            | 

1. The distance between LA and Amsterdam is 8937 km, and the speed of light is about 300000 km/s, so the time si about 8937 * 1000/300000 = 29.79 ms, which is about 30 ms.
2. The Loe Eath Orbit, Geostationary Satellite data are collected from https://www.omniaccess.com/leo/#:~:text=The%20GEO%20latency%20is%20of,and%20an%20essential%20part%20if.
3. The distance between earth and moon is 384,400 km, the speed of light is 300,000 km/s, so t = 384400/300000 * 1000 = 1281.3 ms
4. The distance between earth and Mars is about 54.6 million kilometers, so the time needed is about 54600000/300000 s = 182 s = 3 minutes