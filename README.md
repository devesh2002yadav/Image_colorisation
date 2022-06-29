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
