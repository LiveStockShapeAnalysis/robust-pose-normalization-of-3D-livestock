## 2D/3D fusion-based robust pose normalization of 3D livestock from multiple RGB-D cameras
Created by <a href="http://pclcn.org" target="_blank">Jie Lu</a>, <a href="http://clst.cau.edu.cn/art/2018/8/8/art_31197_580629.html" target="_blank">Hao Guo</a> from China Agricultural University.

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




