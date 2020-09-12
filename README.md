# Crowdsampling the Plenoptic Function 

## Introduction
This repository is a PyTorch implementation of the paper:

**Crowdsampling The Plenoptic Function**. 
[[Project Website]](https://research.cs.cornell.edu/crowdplenoptic/) [[Paper]](https://arxiv.org/pdf/2007.15194.pdf) [[Video]](https://www.youtube.com/watch?v=MAVFKWX8LYo)

[Zhengqi Li](https://www.cs.cornell.edu/~zl548/),
[Wenqi Xian](https://www.cs.cornell.edu/~wenqixian/),
[Abe Davis](http://www.abedavis.com/),
[Noah Snavely](https://www.cs.cornell.edu/~snavely/)

(ECCV 2020 Oral)

## Dataset
Download and unzip data from the links below: 

* [[Effiel Tower]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0000.zip)
* [[Top of the Rock]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0011.zip)
* [[Sacre Coeur]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0013.zip)
* [[Lincoln Memorial]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0021.zip)
* [[Pantheon]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0023.zip)
* [[Trevi Fountain]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0036.zip)
* [[Piazza Navona]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/0057.zip)
* [[Mount Rushmore]](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/1589.zip)

Read more about the dataset in [Readme file](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/README.txt).

## Dependency
The code is tested with Pytorch >= 1.2, the depdenency library includes PIL, opencv, skimage, json, scipy.

## Pretrained Model
Download and unzip pretrained models from [link](https://research.cs.cornell.edu/megadepth/dataset/CrowdSampling/pretrain_models.zip).

To use the pretrained model, put the folders under the project root directory.

### Test the pretrained model:
To run the evaluation, change variable "root" and "data_dir" in script evaluation.py to code directory and data directory respectively. The released code is not highly optimized, so you have to use 4 GPUs with > 11GB memory to run the evaluation. 

| Dataset| Name  | Max depth  | FOV | 
|--------|----------|-------|--------|
| Trevi Fountain | trevi  | 4 |  70 |
| The Pantheon | pantheon | 25 |  65 |
| Top of the Rock | rock  | 75 |  70 |
| Sacre Coeur | coeur | 20 |  65 |
| Piazza Navona | navona  | 25 |  70 |

Follow the commands below:
```bash
   # Usage
   # python evaluation.py --dataset <name> --max_depth <max depth> --ref_fov <fov> --warp_src_img 1
   
   python evaluation.py --dataset trevi --max_depth 4 --ref_fov 70 --warp_src_img 1
```
### Demo of novel view synthesis:
```bash
   # Usage
   # python evaluation.py --dataset <name> --max_depth <max depth> --ref_fov <fov> --warp_src_img 1 --where_add adain --img_a_name xxx --img_b_name xxx --img_c_name xxx
 
   python wander.py --dataset trevi --max_depth 4 --ref_fov 70 --warp_src_img 1  --where_add adain --img_a_name 5094768508_fa56e355bd.jpg  -
-img_b_name 34558526690_e5ba5b3b9d.jpg --img_c_name 34558526690_e5ba5b3b9d.jpg
```
where img_a_name is image name associated with center target viewpoint, img_b_name=img_c_name is the image whose apperance we would like to condition on.

### Demo of novel view synthesis:
```bash
   # Usage
   # python wander.py --dataset <name> --max_depth <max depth> --ref_fov <fov> --warp_src_img 1 --where_add adain --img_a_name xxx --img_b_name xxx --img_c_name xxx
 
   python wander.py --dataset trevi --max_depth 4 --ref_fov 70 --warp_src_img 1  --where_add adain --img_a_name 5094768508_fa56e355bd.jpg  -
-img_b_name 34558526690_e5ba5b3b9d.jpg --img_c_name 34558526690_e5ba5b3b9d.jpg
```
where img_a_name is image name associated with center target viewpoint, img_b_name=img_c_name is the image whose apperance we would like to condition on. The results will be saved in folder demo_wander_trevi.


## Cite
Please cite our work if you find it useful:
```bash
@inproceedings{Li2020,
Author = {Zhengqi Li and Wenqi Xian and Abe Davis and Noah Snavely},
Title = {Crowdsampling the Plenoptic Function},
Year = {2020},
booktitle = {Proc. European Conference on Computer Vision (ECCV)},
}
```


