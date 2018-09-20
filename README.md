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

For heels, the images were taken from the [UT Zappos50K dataset](http://vision.cs.utexas.edu/projects/finegrained/utzap50k/). They are all catalog images collected from Zappos.com.

All the images were resized and background-filled to 256x256 resolution before input into the model for training.

## Usage
Read the code first in the Jupyter Notebook, and create an images folders to store your image dataset (with the names renamed to 5-digit numbers starting from 0, images resized to 256x256). Then just run it and let the community know what you came up with!

## Results
Using 10,000 images of women's blouses with 4/5-star ratings scraped from Amazon:
![Amazon Clothes Epoch 1-300](https://github.com/t0nberryking/DCGAN256/blob/master/Example%20Results/Amazon%20Clothes%20GANs%20epoch%201-300.gif)

213th Iteration:
![213th Iteration](https://github.com/t0nberryking/DCGAN256/blob/master/Example%20Results/i213.png)

300th Iteration:
![300th Iteration](https://github.com/t0nberryking/DCGAN256/blob/master/Example%20Results/i300.png)

Using 5,700 images of Zippo's Heels from the [UT Zappos50K dataset](http://vision.cs.utexas.edu/projects/finegrained/utzap50k/):

![Zippo Heels Epoch 1-165](https://github.com/t0nberryking/DCGAN256/blob/master/Example%20Results/Zippo%20Heels%20GANs%20epoch%201-165.gif)

149th Iteration:
![149th Iteration](https://github.com/t0nberryking/DCGAN256/blob/master/Example%20Results/i149.png)

158th Iteration
![158th Iteration](https://github.com/t0nberryking/DCGAN256/blob/master/Example%20Results/i149.png)

## Discussion
Using a DCGANs, we were able to input 256x256 images and train the Generative Adversarial Network to generate random novel images. Depending on the input, it can be useful to generate such images in order to inspire designers to create new designs. As in the case of the Amazon clothes, we can restrict the input of the images to popular items so that the generated images will mainly incorporate popular colours and designs. Further research and tweaking is needed to tailor different GANs to suit different purposes and outputs since as we can see, the current DCGAN architecture seems to work better for shoes rather than clothes as it is easier to generate more abstract designs than frabic-like images. 

## References
https://github.com/manicman1999/GAN256

https://medium.com/@utk.is.here/keep-calm-and-train-a-gan-pitfalls-and-tips-on-training-generative-adversarial-networks-edd529764aa9

Generative adversarial nets [[arXiv]](https://arxiv.org/abs/1406.2661)

Improved Techniques for Training GANs [[arXiv]](https://arxiv.org/abs/1606.03498)

Improved Training of Wasserstein GANs [[arXiv]](https://arxiv.org/abs/1704.00028)


