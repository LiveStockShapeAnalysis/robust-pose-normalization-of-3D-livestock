## 2D/3D fusion-based robust pose normalization of 3D livestock from multiple RGB-D cameras
Created by <a href="http://pclcn.org" target="_blank">Jie Lu</a>, <a href="http://clst.cau.edu.cn/art/2018/8/8/art_31197_580629.html" target="_blank">Hao Guo</a> from China Agricultural University.

### New place for all the code and data.
Since it's difficult to upload large files in github. So We move all the code and data to here. This git repository will be updated anymore. Please go to this new site.

https://gitee.com/guohaolys/robust-pose-normalization-of-3D-livestock
### Introduction
A 2D/3D fusion-based robust livestock pose normalization method for 3D point clouds captured from multiple RGB-D cameras, is proposed.
This method fuse the information of 2D images and 3D data to improve the robustness of computing process. Specifically, by introducing the state-of-the-art 2D object detection technology, both procedure of forward estimation and segmentation for livestock are optimized.
Extensive experiments on the multiple RGB-D data of livestock show that our proposed method is far more robust and practical. The proposed algorithm serves as the pose normalization procedure in an automatic body measurement system which can be used for health monitoring, weighing and so on.
Furthermore, our approach can handle different livestock species, providing satisfied input data for other algorithms, such as animal behavior analysis, skeleton extraction.

### Installation
Before execute the code, please install some python package:
Matplotlib and tensorflow-gpu==1.13.2 and keras==2.1.5 and numpy==1.18.2 and pillow==7.1.2 and so on.


### Usage
To normalize one point clouds sample:

1.Open “predict.py” 

2.Change 'pcdfilename' to your filename

```
from yolo import YOLO
from PIL import Image
import os
import matplotlib.pyplot as plt
import sys
pcdfilename='65.pcd'  //Change the 65.pcd to the 3d file of yours
main12='all_in_one.exe '+pcdfilename+' -create_image'
a=os.system(main12)
...
```

3. Run “predict.py”

![screenshot for select a viewpoint](./fig/select%20viewpoint.jpg)


4. When “predict.py” is running, .pcd file will be open in new window, and select a viewpoint to generate the ‘1.png’ and ‘matrix.txt’ which will be used in next step. you should make sure that ‘1.png’ has the target region that you need, which will help the model to predict the target regions.

5. After step3, the everything we need to do is done. The file named “result.pcd” will appear in the folder. Then open result.pcd you could see the result of pose normalization for the input pcd file.

![screenshot for result of pose normalization](./fig/normalized%20visual.jpg)



6. The details of the `database`. The following is the content of the folder of database:

|Folder name|File properties|Details|
|---|---|---|
|img|2D data|this folder contains the image which is used to train and test|
|img/cow_rgb|RGB image(cattle) | this folder contains 909 RGB images|
|img/cow_rgb_anno|the annotation for RGB image(cattle)  | this folder contains 909 `xml`|
|img/cow_single|single virtual image(cattle) | this folder contains 924 single virtual images|
|img/cow_single_anno|the annotation for single virtual image(cattle)  | this folder contains 924 `xml`|
|img/cow_triple|triple virtual image(cattle) | this folder contains 309 triple virtual images|
|img/cow_triple_anno|the annotation for triple virtual image(cattle)  | this folder contains 309 `xml`|
|img/pig_rgb|RGB image(pig) | this folder contains 1095 RGB images|
|img/pig_rgb_anno|the annotation for RGB image(pig)  | this folder contains 1095 `xml`|
|img/pig_single|single virtual image(pig) | this folder contains 39 single virtual images|
|img/pig_single_anno|the annotation for single virtual image(pig)  | this folder contains 39 `xml`|
|img/pig_double|double virtual image(pig) | this folder contains 1224 double virtual images|
|img/pig_double_anno|the annotation for double virtual image(pig)  | this folder contains 1224 `xml`|
|img/test|the images are used to test|this folder contains the 20 percent of all above images|
|img/train|the images are used to train|this folder contains the 80 percent of all above images|
|ply_pcd|3D data|this folder contains the pcd file or ply file|
|ply_pcd/cow_triple|pcd file for pig|this folder contains 439 pcd file |
|ply_pcd/pig_double|ply file for cattle|this folder contains 103 ply file|
