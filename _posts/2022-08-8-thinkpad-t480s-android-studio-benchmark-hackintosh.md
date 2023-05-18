---
title:  "Android Studio Perfomance Test on ThinkPad T480s ( Hackintosh )"
author: wakhid
date: 2022-08-8 12:32:00 -0500
categories: [Blogging, Hackintosh, Android Development, macOS]
tags: [ThinkPad, Laptop, Android Development, Hackintosh, macOS]
---


>I'm not an Android Developer. I'm doing AndroidStudioPerformanceTest just to contribute to my local ThinkPad community, because many members are asking ThinkPad models for running an Android studio.*


## My ThinkPad T480s Specifications

- **Notebook model** : ThinkPad T480s
- **OS** : macOS Monterey 12.4 ( Hackintosh )
- **Android Studio version** : Chipmunk 2021.2.1 Patch 2 9 ( Java SDK 17 )
- **CPU Model** : i5 8350U 1.70 GHz ( Max Turbo 3.6 GHz )
- **RAM** : 20 GB
- **Storage** : NVME Intel SSDPEKKF512G8L capacity 500 GB
- **Test Results**: 3M 4s, 1m 55s, 1m 46s
- **Android Studio Benchmark Repository** : [https://github.com/yozhik/AndroidStudioBenchmark](https://github.com/yozhik/AndroidStudioBenchmark)

## 1st Build - BUILD SUCCESSFUL in 3m 4s
![1st Build](https://storage.wakhid.com/img/wakhidcom_t480s_android_benchmark_1.png)

## 2nd Build - BUILD SUCCESSFUL in 1m 55s
![2nd Build](https://storage.wakhid.com/img/wakhidcom_t480s_android_benchmark_2.png)

## 3rd Build - BUILD SUCCESSFUL in 1m 46s
![3rd Build](https://storage.wakhid.com/img/wakhidcom_t480s_android_benchmark_3.png)

![3rd Build](https://storage.wakhid.com/img/wakhidcom_t480s_android_benchmark_4.png)

---

## Sepecial Notes

- Max CPU temperature was up to 95C
  ThinkPad T480s series have issues with CPU temperature, see this link.
  But, as I know was fixed in Windows OS via Lenovo driver update.
  In others OS we must use undevoltage tools like https://github.com/sicreative/VoltageShift or https://github.com/erpalma/throttled
  In my test, For better results I don't use any CPU tweaker software.

- Fan speed was up to 4285 RPM
  I think that is ThinkPad T480s maximum fan speed