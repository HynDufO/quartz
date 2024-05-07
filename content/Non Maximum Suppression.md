---
aliases:
  - NMS
---
- [Tìm hiểu và triển khai thuật toán Non Maximum Suppression](https://viblo.asia/p/tim-hieu-va-trien-khai-thuat-toan-non-maximum-suppression-bJzKmr66Z9N)

Basically, the network detects a bunch of boxes but there are many boxes that represents the same thing, so we want to remove all the redundant boxes.
![[Pasted image 20240507052946.png]]
After using NMS:
![[Pasted image 20240507053007.png]]
## Intersection Over Union (IoU)
![[Pasted image 20240507053030.png]]
## Algorithms
- Step 1: Select box S with the highest confidence score from set P, remove that box from set P, and add that box to the keep set.
- Step 2: Calculate the Intersection over Union (IOU) between the box S selected in step 1 and all other boxes remaining in set P. If any box in P has an IOU with box S being considered greater than the IOU threshold, remove that box from P.
- Step 3: Repeat step 1 until set P has no more boxes.