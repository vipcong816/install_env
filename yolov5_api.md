# 1.下载
https://github.com/ultralytics/yolov5


# 2.数据可能下载很慢，可以手动下载，放到相应位置
https://developer.aliyun.com/article/797577




# 3.图像标注工具
labelimg工具
xml转yolo标签工具
https://github.com/bjornstenger/xml2yolo

火焰测试数据，如果使用要改成coco对应形式
https://github.com/ntsmoura/FireNET-YoloV5?tab=readme-ov-file

```
# Train/val/test sets as 1) dir: path/to/imgs, 2) file: path/to/imgs.txt, or 3) list: [path/to/imgs1, path/to/imgs2, ..]
path: ../fire # dataset root dir
train: train.txt # train images (relative to 'path') 118287 images
val: val.txt # val images (relative to 'path') 5000 images
test: # 20288 of 40670 images, submit to https://competitions.codalab.org/competitions/20794

# Classes
names:
  0: fire
``` 

# 4.训练
火焰数据训练，epochs大些loss能降下来，检测可以检测出来

python train.py --data fire.yaml --epochs 100 --weights yolov5s.pt --cfg yolov5n.yaml  --batch-size 32


# 5.检测
--view-img可以窗口实时展现检测
runs/train/exp7/weights/best.pt 是训练好的模型

python detect.py --weights runs/train/exp7/weights/best.pt --source c53f664d8509def876481982ba7f9fc0.mp4 --view-img


# 6.windows可能遇到的问题

OSError: [WinError 126] 找不到指定的模块。 Error loading "D:\anaconda3\envs\yolo\lib\site-packages\torch\lib\fbgemm.dll" or one of its dependencies.

1、先下载文件libomp140.dll

下载地址
文件大小：315.5 K|
https://mysecreat.lanzoue.com/iQAhN27bnsqd
2、把文件解压后的libomp140.x86_64.dll文件复制到C://windows/system32文件夹内即可




NotImplementedError: cannot instantiate ‘PosixPath‘ on your system报错解决


在代码detect.py的最前面加上

import pathlib
temp = pathlib.PosixPath
pathlib.PosixPath = pathlib.WindowsPath


如果是Linux上报错
import pathlib
pathlib.WindowsPath = pathlib.PosixPath
