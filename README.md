# Vessl.ai PytorchFI Example

## About
Performs neuron single bit flip in DNNs using [PytorchFI](https://github.com/pytorchfi/pytorchfi).    
This code runs on [vessl.ai](https://vessl.ai/) platform.

## Requirements
Pytorch >= 1.7.0

## How to run in vessl.ai
1. Log in to `vessl.ai`.
2. Create `New project`.
3. Create `New experiment`.
4. Make sure that your `Docker image` has at least pytorch 1.7.0
5. (Optional) You can upload tar.gz file of CIFAR-10 or CIFAR-100 dataset to `/input`.
6. Enter `Start command` and `Hyperparameters`.

## Start command
```
pip install bitstring && git clone https://github.com/WaiNaat/vessl-ai-pytorchfi-example.git && mv vessl-ai-pytorchfi-example/code/* ~ && git clone https://github.com/WaiNaat/pytorchfi.git && python main.py
```

You can add arguments at `python main.py`.    
Available ones are    
1. `--input-path [PATH]`: input dataset directory. Default `/input`.
2. `--output-path [PATH]`: result saving directory. Default `/output`.
3. `--detailed-log`: saves detailed log (binary before/after fault injection) of single bit flip. Check detailed log at `sample-output`.

## Hyperparameters
| Key | Default value | Description | Example |
|:---:|:-----:|:-----------:|:--------|
|model_name|`vgg19_bn`|Model names at [chenyaofo/pytorch-cifar-models](https://github.com/chenyaofo/pytorch-cifar-models) or at [torchvision.models](https://pytorch.org/vision/stable/models.html) if dataset is imagenet|`vgg11_bn`|     
|dataset|`cifar10`|`cifar10` or `cifar100` or `imagenet`|`cifar100`|
|seed|`-1`|Seed value. Uses current time value if given seed is negative integer.|`1234`|
|batch_size|`256`|Batch size.||
|img_size|`32`|Input image size.||
|channels|`3`|Input image channel size.||
|bit_flip_pos|`-1`|Specific bit position to flip. Chooses random position if value is negative. Usually Pytorch models use float32, so the value should be in `range(0, 32)`|`3`|
|layer_type|`all`|`all` or module names in `torch.nn` separated by single comma `,`|`Conv2d,Linear,Identity`|
|layer_num|`all`|`all` or list of nonnegative integers of layer numbers to append fault injection, separated by single comma|`0,2,4,8,10`|

You don't have to add hyperparameters if you want to use default.

## Citations
[PytorchFI](https://github.com/pytorchfi/pytorchfi)

[chenyaofo/pytorch-cifar-models](https://github.com/chenyaofo/pytorch-cifar-models)

[vessl.ai](https://vessl.ai/)