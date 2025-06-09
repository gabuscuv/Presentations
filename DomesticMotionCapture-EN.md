---
marp: true
transition: fade
description: hi
author: Gaby Bustillo del Cuvillo
paginate: true
---

# Domestic Motion Capture (Remastered)

Gaby Bustillo del Cuvillo
Original Date: 2023/12/15

---

## History of Domestic Tracking

- Kinect 360 OpenNI (+MMD Community) - 2010
  - [Video](https://www.youtube.com/watch?v=JQvLt7DQhaI)
- VTubers Hits (Kizuna Ai) - 2016
- Virtual Streamers Boom (Hololive) - 2019

<!-- Yagoo - Hololive CEO - In the ViveX Program
(Using a Vive Tracker as Head Tracking) -->

---

## Types of Motion Capture
<!-- Vive Trackers Image -->
- 6DoF Based
  - Pros:  The most precise, reliables,
  - Cons: Most Expensive Ones, most of them has occlusion issues
  <!-- Tundra Trackers Image -->
- IMU Based
  - Uses accelerometers, gyroscopes, and sometimes magnetometers with a AI/Guesses Algorithms
    - Pros: It’s Cheaper, It easier to set up, It doesn’t have Visual Occlusion Issues.
    - Cons: It’s based on Guesses, And It can Fail
- Visual Computation Based
  - Pros: The Cheapest one or Home-made
  - Cons: Unreliable for long term, Limited capabilities.

---

## 2. 6DoF Examples
<!-- HTC Vive Wands as feet Tracker-->
- Any VR Controller
Pros: Cheap, Because You already Have it
(Or you can buy some second-hand controller or upgrade your old ones If you have a lighthouse ecosystem)
<!-- FBT video of using Quest 2 Cameras with Quest 2 Controllers-->
- Any VR Controller
Pros: Cheap, Because You already Have it
(Or you can buy some second-hand controller or upgrade your old ones If you have a lighthouse ecosystem)
<!-- FBT video of using Quest 2 Cameras with Quest 2 Controllers-->
- Lighthouse dedicated devices (Vive Trackers / Tundra Trackers)
  - Pros: Probably The most advanced IMU Solutions
  - Cons: The Initial Setup is Expensive if you don’t own a Vive/Index Headset
<!-- Vive Tracker 3.0 Photo -->
- Vive Trackers Ultimate
  - Pro: It’s cheaper (At least brand new)  than a Lighthouse Setup for No-Vive/Index/lighthouse System, It is not necessary have a fixed place to use it.
 <!-- Tundra Trackers Photo -->
- Cons: It’s not OpenXR/PC Compatible at launch and the recovery of missing tracking is funky

---

## 2. 3DoF Examples

- Mocopi (Sony) - $500
  - Pros: Continuous/worldwide production,
  - Cons: It only works with Mobile Phones (You need rerouting) (but It exists projects like Moslime), Quite slow/laggy for Realtime Uses (like VR Social)
- SlimeVR - $235 (+ Customs)
  - Pros: Probably The most advanced IMU Solutions and Cheaper, (And OpenSource!)
  - Cons: PreOrder Only,
- owoTrackVR (SlimeVR Clone)
  - Pros: Free! (Use Your Android-Based Phone)
  - Cons: Do you have 3 lightweight phones? And a way of strap it?, Yeah, You have these kind of issues.

- HaitoraX
  - Pros: You only need charge a battery, uuuuh
  - Cons: Maybe to much wires?

---

## 2. Visual Computation Examples

- Mocap4All
  - Pros: You need a bunch of Cameras
  - Cons: Uses Machine Learning, So It could be a Miss or Hit
- Amethyst - ~50$  (A Used Kinect)
  - Pros: It’s cheap and reliable
  - Cons:
- April Tags - Free ?
  - Pros: Cheap
  - Cons: It’s unreliable

---

## Table

| | | | | | | | | | |
|--------------------|-----------------------|-----------------|-----------------------|----------------|-----------------------------|------------------|------------------------|-------------------------|------------------|
| Developer            | HTC                     | HTC               | Tundra                  | SlimeVR          | Shiftall                      | Sony               | Akiya Research Institute | Ju1ce, DIY                | K2VR Team          |
| Form factor          | 3x 75 g trackers        | 3x 94g trackers   | 3x 50 g trackers        | 5x 50 g trackers | 5 trackers connected by wires | 6x 8g trackers     | Various Cameras          | QR codes & central camera | Central camera     |
| Battery Life         | 7.5 h                   | 7h                | 7 h                     | 15 h             | 10 h                          | 10 h               | ∞                        | ∞                         | ∞                  |
| Tracking             | 6DoF                    | 6DoF (Inside Out) | 6DoF                    | IMU              | IMU                           | IMU                | Visual                   | Visual                    | Visual             |
| Prone to occlusion   | Yes                     | No?               | Yes                     | No               | No                            | No                 | Yes                      | Yes                       | Yes                |
| Coverage             | 360°                    | 360°              | 360°                    | 360°             | 360°                          | 360°               | 360° \*                  | 360° ²                    | 180°               |
| Precision            | < 1 mm                  | TBD (<1mm)        | < 1 mm                  | 1-10 cm ¹        | 1-10 cm ¹                     | 1-20 cm            | 1-10 cm                  | < 1 cm                    | 1-10 cm            |
| Latency              | ~15 ms                  | 15 ms             | ~15 ms                  | ~15 ms           | \>15 ms                       | 50+ ms             | 30+ ms                   | 30+ ms                    | ~20 ms             |
| Update rate          | 90-144 Hz               | Unknown (90Hz)    | 90-144 Hz               | 100 Hz           | 50-100 Hz                     | 50 Hz              | Cameras framerate        | Camera framerate          | 30 Hz              |
| Range                | 10 m                    | 10 m / Wi-Fi C.   | 10 m                    | Wi-Fi coverage   | Bluetooth coverage            | Bluetooth coverage |                          | 2-3 m                     | 2-4 m              |
| Connectivity         | 2.4Ghz (SteamVR)        | 2.4Ghz \| Wi-Fi   | 2.4Ghz (SteamVR)        | Wi-Fi            | Bluetooth                     | Bluetooth \| Wi-Fi |                          | Visual                    | Visual             |
| Can track any object | Yes                     | Yes?              | Yes                     | No               | No                            | No                 |                          | Yes                       | No                 |
| Open Source          | No                      | No                | No                      | SW + HW          | No                            | No                 |                          | SW + HW                   | SW                 |
| Price                | $390 + ~$400 Lighthouse | $600              | $360 + ~$400 Lighthouse | $195             | $270                          | $449               |                          | Printer & camera          | ~$30 (used Kinect) |

---

## On the Software-Side

---

## It’s quite weird

There are a bunch of protocols, From VR API like to OpenVR/OpenXR to OSC/VMCP, proprietary file formats like Mocopi BVH Format,
With different degree of support between devices and protocols.
Unreal Engine only support Vive Tracker natively as Camera/Mesh Points
And Unity support humanoid tracking (As far, I can understand)
There are a lot of Workflows, So I will talk my own workflow

---

## Virtual Motion Capture - sh_akira

- Uses SteamVR API as a base
- Supports External OSC and Exports OSC via VMCP (This last one requires a Patreon Build, $2 minimum)
- Supports Mocopi (With own UDP Protocol and OSC mode)
- Support for Vive Lip Tracking
- Support Vive Pro/Focus Eye Tracking & Tobii Eyetracker
- It has Export Plugins for Unity (VMC4U) and Unreal Engine (EVMC4UE)
- It’s Open Source

---

## VMC Interconnectivity
<!-- VMC Software Supported Image -->

---

## OSC or VMCP (1)
<!-- It shows a diagram of VMC Pipeline Architecture -->

---

## OSC or VMCP (2)

<!-- It shows a diagram of VMC Network Architecture -->

---

### Also, Did you know OSC stands for

## Open Sound Control?

Yeah, Somehow the  Japanese body tracking community uses Sound-related messaging protocol. (And Fair Enough, It should be similar to MIDI Messages)
(It’s probably because Low-latency but don’t ask me)

---

## 2. FaceTracking
<!-- Vive FaceTracker -->
- Use Vive FaceTracker + some HMD With Eye Tracking support
  - Cons: Probably Expensive
- Use LiveLink Face
  - Pros: It’s Free, It uses ARKit so, It can use FaceId.
  - Cons: You need a iOS Devices and use Unreal Engine
- iFacialMocap (Using ARKit )
  - Pros: It Uses already VMC Protocol
- Camera Android Tracking (Like MeowFace)
  - Pros: It Uses already VMC Protocol

---

## HandTracking

- OpenGloves
  - Pros: It’s Open Source
  - Cons: It’s a DIY Product, It doesn’t exists a commercial product
- Quest 3/2 Hand Tracking
  - Pros: Already included If you Have a Quest 2
  - Cons: You need a iOS Devices and use Unreal Engine
- Valve index Controller (Knuckles)
  - Ideal if you have already a lighthouse setup.
- LeapMotion (Probably dead)

## Ragdolls

## My workflow

<!-- Images of Oculus Rift S, Oculus Touch, Knuckles, OpenVR Space Calibrator, 3 Vive Trackers + Tundra Dongle, , ueOSC, VMC4UE, VRM Format, VRM4U, Unreal Animation Retargeting and Unreal Recorder -->

---

## Results

---

## Results 2 (Quite Old Build/Record)

---

## Closing
