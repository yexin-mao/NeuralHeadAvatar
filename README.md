# NeuralHeadAvator

This is the official PyTorch implementation of the final project of COMP8536.

## 1. Datasets
Please follow the instructions in [Video-preprocessing](https://github.com/AliaksandrSiarohin/video-preprocessing) to download and preprocess the datasets. In this project, we only use the VoxCelab dataset.

## 2. Training

To train the netowrk, run
```shell script
CUDA_VISIBLE_DEVICES=0,1,2,3 python train.py --exp_path <EXP_PATH> --exp_name <EXP_NAME>
```
You should adjust the device numbers in `CUDA_VISIBLE_DEVICES`. Tensorboard log and checkpoints will be saved in `<EXP_PATH>/<EXP_NAME>/log` and `<EXP_PATH>/<EXP_NAME>/chekcpoints` respectively.

To continue from a checkpoint, run
```shell script
CUDA_VISIBLE_DEVICES=0,1,2,3 python train.py --exp_path <EXP_PATH> --exp_name <EXP_NAME> --resume_ckpt <CHECKPOINT_PATH>
```
The path of the checkpoint should be provided in `<CHECKPOINT_PATH>`

## 3. Evaluation
To obtain L_1 and LPIPS results, put checkpoints under `./checkpoints` and run
```shell script
CUDA_VISIBLE_DEVICES=0 python evaluation.py --dataset <DATASET> --save_path <SAVE_PATH>
```
Generated videos will be save under `<SAVE_PATH>`.

## 4. Demo
Download pre-trained checkpoints from [here](https://drive.google.com/drive/folders/1N4QcnqUQwKUZivFV-YeBuPyH4pGJHooc?usp=sharing) and put models under `./checkpoints`. We have provided several demo source images and driving videos in `./data`. 
To obtain demos, you could run following commands, generated results will be saved under `./res`.
```shell script
CUDA_VISIBLE_DEVICES=0 python run_demo.py --source_path <SOURCE_PATH> --driving_path <DRIVING_PATH>
```
`<SOURCE_PATH>`  is the source image, `<DRIVING_PATH>`  is the driving video

For example 
```shell script
CUDA_VISIBLE_DEVICES=0 python run_demo.py --source_path ./data/vox/macron.png --driving_path ./data/vox/driving1.mp4
```

## Acknowledgement
Part of the code is adapted from [LIA](https://github.com/wyhsirius/LIA). We thank authors for their contribution to the community.
