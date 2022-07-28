# StyleGAN2_Pytorch
This project is a reimplementation from official NV_Lab stylegan2[(link)](https://github.com/NVlabs/stylegan2) & [this](https://github.com/rosinality/stylegan2-pytorch) repo.


## Data Preprocessing
I only use the first 130K images(NG: 42610, OK: 87390) from `_train_map.txt` for training GAN. In data preprocessing stage, I resize images to 160x160 then center crop to 128x128 and normalize the pixel value into [-1, 1] along the spatial dimension.

## Model
Stylgan2(Condtional GAN architecture). I use embedding table to lookup label and concat it with latent vector in mapping network of StyleGAN2. In Discriminator, I use label information to only output prediction for that class.

## Training 
The training behavior is quite like the official Stylegan2. I traing this model for 300K iteration with initial learning rate `0.002`, batch size 16, Non-saturating loss with path length regularization for Generator, logistic loss and r1 regularization for Discriminator, and Style mixing regularization. For training configuration file, please refer to `StyleGAN2_Pytorch/experiments/itri-noaug.yml`

## FID
The best FIDs in this training are 87.5 and 48.7 for NG and OK, respectively. For FID in whole training, please refer to `fid.txt`