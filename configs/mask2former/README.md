# Mask2Former

> [Masked-attention Mask Transformer for Universal Image Segmentation](http://arxiv.org/abs/2112.01527)

<!-- [ALGORITHM] -->

## Abstract

Image segmentation is about grouping pixels with different semantics, e.g., category or instance membership, where each choice of semantics defines a task. While only the semantics of each task differ, current research focuses on designing specialized architectures for each task. We present Masked-attention Mask Transformer (Mask2Former), a new architecture capable of addressing any image segmentation task (panoptic, instance or semantic). Its key components include masked attention, which extracts localized features by constraining cross-attention within predicted mask regions. In addition to reducing the research effort by at least three times, it outperforms the best specialized architectures by a significant margin on four popular datasets. Most notably, Mask2Former sets a new state-of-the-art for panoptic segmentation (57.8 PQ on COCO), instance segmentation (50.1 AP on COCO) and semantic segmentation (57.7 mIoU on ADE20K).

<div align=center>
<img src="https://camo.githubusercontent.com/455d3116845b1d580b1f8a8542334b9752fdf39364deee2951cdd231524c7725/68747470733a2f2f626f77656e63303232312e6769746875622e696f2f696d616765732f6d61736b666f726d657276325f7465617365722e706e67" height="300"/>
</div>

## Introduction

Mask2Former requires COCO and [COCO-panoptic](http://images.cocodataset.org/annotations/panoptic_annotations_trainval2017.zip) dataset for training and evaluation. You need to download and extract it in the COCO dataset path.
The directory should be like this.

```none
rsidetection
├── rsidet
├── tools
├── configs
├── data
│   ├── coco
│   │   ├── annotations
|   |   |   ├── instances_train2017.json
|   |   |   ├── instances_val2017.json
│   │   │   ├── panoptic_train2017.json
│   │   │   ├── panoptic_train2017
│   │   │   ├── panoptic_val2017.json
│   │   │   ├── panoptic_val2017
│   │   ├── train2017
│   │   ├── val2017
│   │   ├── test2017
```

## Results and Models

### Panoptic segmentation

| Backbone |  style  |   Pretrain   | Lr schd | Mem (GB) | Inf time (fps) |  PQ  | box mAP | mask mAP |                                                                         Config                                                                         |                                                                                                                                                                                                                             Download                                                                                                                                                                                                                             |
| :------: | :-----: | :----------: | :-----: | :------: | :------------: | :--: | :-----: | :------: | :----------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|   R-50   | pytorch | ImageNet-1K  |   50e   |   13.9   |       -        | 51.9 |  44.8   |   41.9   |            [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_r50_lsj_8x2_50e_coco-panoptic.py)            |                                             [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r50_lsj_8x2_50e_coco-panoptic/mask2former_r50_lsj_8x2_50e_coco-panoptic_20220326_224516-11a44721.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r50_lsj_8x2_50e_coco-panoptic/mask2former_r50_lsj_8x2_50e_coco-panoptic_20220326_224516.log.json)                                             |
|  R-101   | pytorch | ImageNet-1K  |   50e   |   16.1   |       -        | 52.4 |  45.3   |   42.4   |           [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_r101_lsj_8x2_50e_coco-panoptic.py)            |                                           [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r101_lsj_8x2_50e_coco-panoptic/mask2former_r101_lsj_8x2_50e_coco-panoptic_20220329_225104-c54e64c9.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r101_lsj_8x2_50e_coco-panoptic/mask2former_r101_lsj_8x2_50e_coco-panoptic_20220329_225104.log.json)                                           |
|  Swin-T  |    -    | ImageNet-1K  |   50e   |   15.9   |       -        | 53.4 |  46.3   |   43.4   |     [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco-panoptic.py)      |                   [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco-panoptic/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco-panoptic_20220326_224553-fc567107.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco-panoptic/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco-panoptic_20220326_224553.log.json)                   |
|  Swin-S  |    -    | ImageNet-1K  |   50e   |   19.1   |       -        | 54.5 |  47.8   |   44.5   |     [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco-panoptic.py)      |                   [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco-panoptic/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco-panoptic_20220329_225200-c7b94355.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco-panoptic/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco-panoptic_20220329_225200.log.json)                   |
|  Swin-B  |    -    | ImageNet-1K  |   50e   |   26.0   |       -        | 55.1 |  48.2   |   44.9   |     [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-b-p4-w12-384_lsj_8x2_50e_coco-panoptic.py)     |                 [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-b-p4-w12-384_lsj_8x2_50e_coco-panoptic/mask2former_swin-b-p4-w12-384_lsj_8x2_50e_coco-panoptic_20220331_002244-c149a9e9.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-b-p4-w12-384_lsj_8x2_50e_coco-panoptic/mask2former_swin-b-p4-w12-384_lsj_8x2_50e_coco-panoptic_20220331_002244.log.json)                 |
|  Swin-B  |    -    | ImageNet-21K |   50e   |   25.8   |       -        | 56.3 |  50.0   |   46.3   |  [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-b-p4-w12-384-in21k_lsj_8x2_50e_coco-panoptic.py)  |     [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-b-p4-w12-384-in21k_lsj_8x2_50e_coco-panoptic/mask2former_swin-b-p4-w12-384-in21k_lsj_8x2_50e_coco-panoptic_20220329_230021-3bb8b482.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-b-p4-w12-384-in21k_lsj_8x2_50e_coco-panoptic/mask2former_swin-b-p4-w12-384-in21k_lsj_8x2_50e_coco-panoptic_20220329_230021.log.json)     |
|  Swin-L  |    -    | ImageNet-21K |  100e   |   21.1   |       -        | 57.6 |  52.2   |   48.5   | [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-l-p4-w12-384-in21k_lsj_16x1_100e_coco-panoptic.py) | [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-l-p4-w12-384-in21k_lsj_16x1_100e_coco-panoptic/mask2former_swin-l-p4-w12-384-in21k_lsj_16x1_100e_coco-panoptic_20220407_104949-d4919c44.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-l-p4-w12-384-in21k_lsj_16x1_100e_coco-panoptic/mask2former_swin-l-p4-w12-384-in21k_lsj_16x1_100e_coco-panoptic_20220407_104949.log.json) |

### Instance segmentation

| Backbone | style   | Pretrain    | Lr schd | Mem (GB) | Inf time (fps) | box mAP | mask mAP | Config                                                                                                                               | Download                                                                                                                                                                                                                                                                                                                                                                                 |
| -------- | ------- | ----------- | ------- | -------- | -------------- | ------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R-50     | pytorch | ImageNet-1K | 50e     | 13.7     | -              | 45.7    | 42.9     | [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_r50_lsj_8x2_50e_coco.py)              | [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r50_lsj_8x2_50e_coco/mask2former_r50_lsj_8x2_50e_coco_20220506_191028-8e96e88b.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r50_lsj_8x2_50e_coco/mask2former_r50_lsj_8x2_50e_coco_20220506_191028.log.json)                                                     |
| R-101    | pytorch | ImageNet-1K | 50e     | 15.5     | -              | 46.7    | 44.0     | [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_r101_lsj_8x2_50e_coco.py)             | [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r101_lsj_8x2_50e_coco/mask2former_r101_lsj_8x2_50e_coco_20220426_100250-c50b6fa6.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_r101_lsj_8x2_50e_coco/mask2former_r101_lsj_8x2_50e_coco_20220426_100250.log.json)                                                 |
| Swin-T   | -       | ImageNet-1K | 50e     | 15.3     | -              | 47.7    | 44.7     | [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco.py) | [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco_20220508_091649-4a943037.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco/mask2former_swin-t-p4-w7-224_lsj_8x2_50e_coco_20220508_091649.log.json) |
| Swin-S   | -       | ImageNet-1K | 50e     | 18.8     | -              | 49.3    | 46.1     | [config](https://github.com/open-mmlab/rsidetection/blob/master/configs/mask2former/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco.py) | [model](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco_20220504_001756-743b7d99.pth) \| [log](https://download.openmmlab.com/rsidetection/v2.0/mask2former/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco/mask2former_swin-s-p4-w7-224_lsj_8x2_50e_coco_20220504_001756.log.json) |

Note: We have trained the instance segmentation models many times (see more details in [PR 7571](https://github.com/open-mmlab/rsidetection/pull/7571)). The results of the trained models are relatively stable (+- 0.2), and have a certain gap (about 0.2 AP) in comparison with the results in the [paper](http://arxiv.org/abs/2112.01527). However, the performance of the model trained with the official code is unstable and may also be slightly lower than the reported results as mentioned in the [issue](https://github.com/facebookresearch/Mask2Former/issues/46).

## Citation

```latex
@article{cheng2021mask2former,
  title={Masked-attention Mask Transformer for Universal Image Segmentation},
  author={Bowen Cheng and Ishan Misra and Alexander G. Schwing and Alexander Kirillov and Rohit Girdhar},
  journal={arXiv},
  year={2021}
}
```
