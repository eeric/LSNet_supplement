# LSNet_supplement
Project material supplement


##安装包
matplotlib

shapely

scipy
##（1）安装mmcv, 例如cuda版本 10.0.130

pip3 install mmcv-full -f  https://download.openmmlab.com/mmcv/dist/cu101/torch1.5.0/index.html
##（2）安装mmdet

Cd /home/yq/work-test/2021/LSNet-main/code

Python3 setup.py develop
##（3）安装cocoapi

a. 先安装pip3 install cython

b. cd code/cocoapi/pycocotools

c. Python3 setup.py develop
##（4）修改

./code/mmdet/ops/conv_ws.py

第25行改成：@CONV_LAYERS.register_module(name='ConvWS', force=True)

第52行改成：@CONV_LAYERS.register_module(name='ConvAWS', force=True)

##（5）ImportError: libcudart.so.10.0: cannot open shared object file: No such file or directory
##如果遇到错误ImportError: libcudart.so.10.0: cannot open shared object file: No such file or directory
sudo ldconfig /usr/local/cuda-10.0/lib64
##（6）修改训练基本设置

路径：code/configs

'./_base_/datasets/coco_lsvr.py', #数据设置

'./_base_/schedules/schedule_1x.py',#模型设置

'./_base_/default_runtime.py' 	
##（7）训练命令

./code/tools/dist_train.sh ./code/configs/lsnet/lsnet_bbox_r50_fpn_1x_coco.py 2 --work-dir work_dir/lsnet_bbox_r50_fpn_1x_coco
