# xai-saliency-maps

This repo contains PyTorch implementation of various GAN architectures. <br/>
It's aimed at making it **easy for beginners** to start playing and learning about GANs. <br/>

All of the repos I found do obscure things like setting bias in some network layer to `False` without explaining <br/>
why certain design decisions were made. This repo makes **every design decision transparent.**

## Table of Contents
  * [What are Saliency Maps?](#what-are-saliency-maps)
  * [Setup](#setup)
    + [Saliency](#Saliency)
    + [Occlusion](#Occlusion)

## What are Saliency Maps?

GANs were originally proposed by Ian Goodfellow et al. in a seminal paper called [Generative Adversarial Nets](https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf).

GANs are a framework where 2 models (usually neural networks), called generator (G) and discriminator (D), play a **minimax game** against each other.
The generator is trying to **learn the distribution of real data** and is the network which we're usually interested in.
During the game the goal of the generator is to trick the discriminator into "thinking" that the data it generates is real.
The goal of the discriminator, on the other hand, is to correctly discriminate between the generated (fake) images and real images coming from some dataset (e.g. MNIST).

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

Important note: you don't need to train the GANs to use this project I've checked-in pre-trained models. <br/>
You can just use the `generate_imagery.py` script to play with the models.

## Occlusion

Vanilla GAN is my implementation of the [original GAN paper (Goodfellow et al.)](https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf) with certain modifications mostly in the model architecture,
like the usage of LeakyReLU and 1D batch normalization (it didn't even exist back then) instead of the maxout activation and dropout.

### Usage

For training just check out [vanilla GAN](#training) (just make sure to use `train_dcgan.py` instead). <br/>
The only difference is that this script will download [pre-processed CelebA dataset](https://s3.amazonaws.com/video.udacity-data.com/topher/2018/November/5be7eb6f_processed-celeba-small/processed-celeba-small.zip) instead of MNIST.

#### Generating imagery

Again just use the `generate_imagery.py` script.

You have 3 options you can set the `generation_mode` to:
* `GenerationMode.SINGLE_IMAGE` <- generate a single face image
* `GenerationMode.INTERPOLATION` <- pick 2 face images you like and script will interpolate between them
* `GenerationMode.VECTOR_ARITHMETIC` <- pick 9 images and script will do vector arithmetic

GenerationMode.VECTOR_ARITHMETIC will give you an **interactive matplotlib plot** to pick 9 images.

Note: make sure to set `--model_name` to either `DCGAN_000000.pth` (pre-trained and checked-in) or your own model.

## Acknowledgements

I found these repos useful (while developing this one):
* [gans](https://github.com/diegoalejogm/gans) (PyTorch & TensorFlow)
* [PyTorch-GAN](https://github.com/eriklindernoren/PyTorch-GAN) (PyTorch)

## Citation

If you find this code useful for your research, please cite the following:

```
@misc{Gordić2020PyTorchGANs,
  author = {Gordić, Aleksa},
  title = {pytorch-gans},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/gordicaleksa/pytorch-gans}},
}
```

## Connect with me

If you'd love to have some more AI-related content in your life :nerd_face:, consider:
* Subscribing to my YouTube channel [The AI Epiphany](https://www.youtube.com/c/TheAiEpiphany) :bell:
* Follow me on [LinkedIn](https://www.linkedin.com/in/aleksagordic/) and [Twitter](https://twitter.com/gordic_aleksa) :bulb:
* Follow me on [Medium](https://gordicaleksa.medium.com/) :books: :heart: