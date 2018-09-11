# DCGAN256
DCGAN on 256x256 pictures 

(*) This repo is a modification of manicman1999/GAN256

(*) The full credit of the basic model structure design goes to manicman1999/GAN256

This GAN was based on GAN256 by Matthew Mann as his implementation allowed input and output of pictures of 256x256 resolution. Normally, GANs trained at a personal scale only works well at much lower resolutions (32x32 or 64x64), and may not transfer to datasets other than Mnist. 

## Modifications

A couple of modifications were made to the model architecture for better results. With reference from GANs articles and research (https://medium.com/@utk.is.here/keep-calm-and-train-a-gan-pitfalls-and-tips-on-training-generative-adversarial-networks-edd529764aa9, https://arxiv.org/pdf/1606.03498.pdf), the following changes were made:

1. Larger Kernel and more filters
The kernel size of layers 2 and 3 in the generator was increased by 1. As larger kernels cover more area it should capture more information. 

2. Flip labels (Generated=True, Real=False)
Helps with gradient flow.

3. Instance noise added to stabilize training
A Gaussian Noise layer was added at the top of the Discriminator, with the idea being to prevent the Discriminator from being too good too early, which will prevent the Generator from learning and possibly converging. 

## Input

For female blouses, the images were scraped using Scrapy from the Amazon website, and filters were used to select only 4-/5-star products. 

For heels, the images were taken from the UT Zappos50K dataset (http://vision.cs.utexas.edu/projects/finegrained/utzap50k/). They are all catalog images collected from Zappos.com.

All the images were resized and background-filled to 256x256 resolution before input into the model for training.

## Results



