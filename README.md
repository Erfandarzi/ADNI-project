# Pytorch-GAN
A clean and readable Pytorch implementation of a GAN to be tested on ADNI dataset

## Prerequisites
Code is intended to work with ```Python 3.6.x```, it hasn't been tested with previous versions

### [PyTorch & torchvision](http://pytorch.org/)
Follow the instructions in [pytorch.org](http://pytorch.org) for your current setup

### [Visdom](https://github.com/facebookresearch/visdom)
To plot loss graphs and draw images in a nice web browser view
```
pip3 install visdom
```

## Training
### 1. Setup the dataset
First, you will need to download and setup a dataset. The easiest way is to use one of the already existing datasets on UC Berkeley's repository:
```
./download_dataset <dataset_name>
```

You can build your own dataset by setting up the following directory structure:

    .
    ├── datasets                   
    |   ├── <dataset_name>         # i.e. brucewayne2batman
    |   |   ├── train              # Training
    |   |   |   ├── A              # Contains domain A images (i.e. Bruce Wayne)
    |   |   |   └── B              # Contains domain B images (i.e. Batman)
    |   |   └── test               # Testing
    |   |   |   ├── A              # Contains domain A images (i.e. Bruce Wayne)
    |   |   |   └── B              # Contains domain B images (i.e. Batman)
    
### 2. Train!
```
./train --dataroot datasets/<dataset_name>/ --cuda
```
This command will start a training session using the images under the *dataroot/train* directory with default hyperparameters. 


## Testing
```
./test --dataroot datasets/<dataset_name>/ --cuda
```
This command will take the images under the *dataroot/test* directory, run them through the generators and save the output under the *output/A* and *output/B* directories. As with train, some parameters like the weights to load, can be tweaked, see ```./test --help``` for more information.
