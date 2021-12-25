---
title: Augmentation
created: '2021-11-08T12:15:46.248Z'
modified: '2021-11-09T10:10:15.744Z'
---

# Augmentation

https://www.kaggle.com/c/global-wheat-detection/discussion/172418
https://blog.roboflow.com/yolov4-data-augmentation/
https://www.kaggle.com/kaushal2896/data-augmentation-tutorial-basic-cutout-mixup
- cutout: done
- mixup: done

Sensing Imagery
- Basic training data augmentation methods:
  -  Rotate
  - Flip
  - Color Jitter
  - Translation
  - Shape change

- Multiple images adopted into a singe training image
  - CutMix
  - Mixup
  - Mosaic

The synthesis sample and resampling methods proposed to overcome these problems are pre-processing procedures, and are not able to balance samples automactically and dynamically

Highlight of this paper:
- Analyze the object distribution of remote sensing iamges and hightlights the problems of augmentation in object samples with a sparse distribution. `Assinged Stitch` is proposed
- `Auto target duplication` - overcome the class-imblance problem. This module is able to balance the labels of each class and focus on the poor class results by efficiently selecting objects to duplicate.

# Relative works
- Random dropout: 
- Cut Paste Learn
- Random Image cropping and patching
- Cutmix

With modre blank training samples generated, the instability of the number of objects in the training sample seriously disturbs the training process, resulting in an unsatisfactory performance.
Sparse object dataset leads to unstable training procedure

Aggregated-Mosaic
- Assigned-stich: done
- Auto-target duplication copies the objects of unsatisfactory class and thus forces the network pay more attention on this class
# Resources:

- [Gridmask data augmentation](https://github.com/dvlab-research/GridMask)
- [Mixup-Beyond Emperical Risk Minimization](https://arxiv.org/pdf/1710.09412.pdf)
- [CutMix-pytorch](https://github.com/clovaai/CutMix-PyTorch)
- [Cutmix and mixup](https://www.kaggle.com/cdeotte/cutmix-and-mixup-on-gpu-tpu)
- [Training object detection](https://patrick-llgc.github.io/Learning-Deep-Learning/paper_notes/bag_of_freebies_object_detection.html)
- [Augmentation review](https://github.com/AgaMiko/data-augmentation-review)
- [Object detection augmentation](https://arxiv.org/pdf/1906.11172.pdf)




