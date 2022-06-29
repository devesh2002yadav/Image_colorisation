# Image_colorisation
Hello Everyone! I have made this project of image colorisation using Conditional GANs
There is a amazing use case of Deep learning, that we will be using here i.e. Colorization of black and white images.  We will be deploying this project in Google Colab notebook using PyTorch library and with some knowledge of Deep learning, Nueral networks, generative adversarial network(GANs) .



**Problem overview -**

We would try to colorise the images provided as black and white into their sought ‘real’ colours. 



**Understanding Basics –** 

**1)	RGB Colour Scheme -** when we load an image, we get a 3-rank array(height, width, colour) with the last axis containing the colour data for the image. The colour data is represented in the RGB scheme, which means there would be 3 numbers(ranging from 0 to 255) assigned to each pixel of image representing the extent of colours red, green and blue in it. You can see example through the below image. 


![RGB-image-and-its-three-components](https://user-images.githubusercontent.com/77203935/176382601-8e47ef1c-8897-4b39-bcb5-9f77a092af09.png)



**2)	LAB color scheme –** In L*a*b scheme also, we have 3 numbers, where ‘l’ represents extent of lightness in photo, **a** represents the extent of green-red color in photo and **b** tells about how much of blue-yellow is there in photo. Below examples helps in understanding the concept.


![lab eg main img](https://user-images.githubusercontent.com/77203935/176383422-8fbb19d9-8b1a-4610-a5cb-d23ffe7e187c.jpg)
![lab eg img](https://user-images.githubusercontent.com/77203935/176383454-1dd744e3-8ad9-4222-ab97-a7ad3c581e36.jpg)



**3)**	We would use L*a*b color scheme, so does most of people for image colorization, because we would provide the Lightness channel image (which is already grayscale) and we have predict only two numbers of ***a** and ***b** channel which is easier than using rgb color scheme and predicting 3 numbers.


![rgb vs lab image](https://user-images.githubusercontent.com/77203935/176385057-3522fc85-d623-4ee6-a879-a46c8f5a1354.png)



**Visualisation of RBG vs L*a*b -**


![rgb vs lab img](https://user-images.githubusercontent.com/77203935/176385089-29ac40ea-9906-4dee-8632-5d09523a03fa.jpg)




**Example of RGB and L*a*b scheme through a picture-**

![image proj rgb main](https://user-images.githubusercontent.com/77203935/176385666-77f9dd3f-7870-4293-9e7a-364c27fe5087.jpeg)


![image proj lab main](https://user-images.githubusercontent.com/77203935/176385148-1aedff41-90db-48a2-9503-2c2e066705f9.jpeg)




**Approach to solve the problem –**

There are ways to solve this, people have used classification and regression for this purpose but they have their pros and cons . We will be using Image to image translation using Conditional Adversarial networks. In this we would have two losses, 1) L1 Loss – regression loss and 2) GAN Loss. 



**What actually GAN is ? –**

Generative Adversarial Networks, or GANs are an approach to generative modeling using deep learning techniques, such as convolutional neural networks.

GANs are a way of training a generative model by framing the problem as a supervised learning problem with two sub-models: the generator model that we train to generate new examples, and the discriminator model that tries to classify examples as either real (from the domain) or fake (generated).

![image](https://user-images.githubusercontent.com/77203935/176389127-26880f54-9232-4e9d-8552-64b6caa56edf.png)


In our project, the generator model will take a grayscale image (1ightness channel  image) and produce a 2-channel image, a channel for a and another for b.  The discriminator, will take these two produced channels and concatenate them with the input grayscale image and will decide whether this new 3-channel image is fake or real using binary classification. For this we will be providing some real images that are not generated by generator to train the discriminator. 

Considering x as the grayscale image,  y as the 2-channel output we want from the generator (it can also represent the 2 color channels of a real image) and z as the input noise for the generator. Also, G is the generator model and D is the discriminator. Then the loss for our conditional GAN will look like this – 

![Cond GAN loss img](https://user-images.githubusercontent.com/77203935/176386580-79d7709e-10a1-4c7c-89b0-ab09474fec5d.png)

We will combine this loss function with L1 Loss ( which is known as mean absolute error) –

![l1 loss fgxn](https://user-images.githubusercontent.com/77203935/176387528-142f0861-0a4e-43e8-aa10-8d2ed6100a95.jpeg)



So  this was about basic theory, You can read more about GANs in the paper link I have provided here. So now lets jump to the code. I have implemented it in the Google Colab notebook , but you can also use Jupyter notebook for this. 


**Resources -**


Paper about details of GANs - 

https://machinelearningmastery.com/what-are-generative-adversarial-networks-gans/

Paper about Image-to-Image Translation with Conditional Adversarial Networks - 

https://arxiv.org/abs/1611.07004

Getting started with Google colab -

https://towardsdatascience.com/getting-started-with-google-colab-f2fff97f594c
