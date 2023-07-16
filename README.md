# xai-saliency-maps

If you are looking to get more insight into your image neural network, like I was, here are 2 good ways you can do it. Both methods approach this problem, with the idea of saliency of a picture.

## Table of Contents
  * [What are Saliency Maps?](#what-are-saliency-maps)
  * [Setup](#setup)
    + [Saliency](#Saliency)
    + [Occlusion](#Occlusion)

## What are Saliency Maps?

Oxford definition: Prominence, The quality of being particularly noticeable or important.

In our case, our goal is to score saliency for each pixel-value in the image.

First introduced in Zeiler and Fergus, “Visualizing and Understanding Convolutional Networks”, ECCV 2014, this technique brought the idea of occluding part of an image, to identify how “important” was that segment to the prediction of our model.

## Setup

1. `git clone https://github.com/gordicaleksa/pytorch-gans`
2. Open Anaconda console and navigate into project directory `cd path_to_repo`
3. Run `conda env create` from project directory (this will create a brand new conda environment).
4. Run `activate pytorch-gans` (for running scripts from your console or set the interpreter in your IDE)

That's it! It should work out-of-the-box executing environment.yml file which deals with dependencies.

-----

PyTorch package will pull some version of CUDA with it, but it is highly recommended that you install system-wide CUDA beforehand, mostly because of GPU drivers. I also recommend using Miniconda installer as a way to get conda on your system. 

Follow through points 1 and 2 of [this setup](https://github.com/Petlja/PSIML/blob/master/docs/MachineSetup.md) and use the most up-to-date versions of Miniconda and CUDA/cuDNN.

## Saliency

First introduced in Simonyan, Vedaldi, and Zisserman, “Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps”, ICLR Workshop 2014, this approach introduced a technique that will generate an image map which maximizes the output score.

### We can use Tensorflow GradientTape():

1. Getting the model loss function, and preparing our data.
2. Predicting with the model and calculating the loss, and using automatic differantiation.
3. Calculate the loss gradient with respect to the original image.

## Occlusion

1. Adding an occlusion map in the original picture.
2. Calculating the amount of error that is added in the prediction.
3. Attributing the error to the occluded pixels.

### Usage

For training just check out [vanilla GAN](#training) (just make sure to use `train_dcgan.py` instead). <br/>
The only difference is that this script will download [pre-processed CelebA dataset](https://s3.amazonaws.com/video.udacity-data.com/topher/2018/November/5be7eb6f_processed-celeba-small/processed-celeba-small.zip) instead of MNIST.


## Acknowledgements

I found these repos useful (while developing this one):
* [gans](https://github.com/diegoalejogm/gans) (PyTorch & TensorFlow)
* [PyTorch-GAN](https://github.com/eriklindernoren/PyTorch-GAN) (PyTorch)

## Citation

If you find this code useful for your research, please cite the following:

```
@misc{Kotani2023TensorflowSaliencyMaps,
  author = {Gabriel Kotani},
  title = {xai-saliency-maps},
  year = {2023},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/Gab314/xai-saliency-maps}},
}
```

## Connect with me

* Follow me on [LinkedIn](https://www.linkedin.com/in/gabriel-kotani/)
* Follow me on [Medium](https://medium.com/@gabriel.o.k) :books: :heart: