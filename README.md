# MiniProject D7041E

In this project we have used two models capable of restoring color to grayscale images using neural nets. The accuracy of the models was tested with various preprocessing steps such as color saturization in order to see what effect, positive or negative, these had on the results. By doing this we hope to show two ways of implementing grayscale to color models with neural net and how these are affected by preprocessing. The accuracy of the results is measured by summarizing the amount of pixels containing a differing rgb value compared to the original picture divided by the total amount of pixels in the image.



# Setup
In order to run our code you need to install a few libries. Most of the libraries we used is bellow but something might be missing.
`pip install keras tensorflow numpy cv2 pillow jupyter scikit-image` To add we used python 3 and the latest version of tensorflow and wrote everything with visual studio code.

### Simple and Advanced model
These are very simple to run. Simply download the zip, open it in whatever jupiter ide then install the nessesary libraries.

### Caffemodel / Advanced pre-trained model
To setup the caffemodel start by downloading the repository and the weights from: https://drive.google.com/drive/folders/1FaDajjtAsntF_Sw5gqF0WyakviA5l8-a and 
put the files into `Caffemodel\Model`. Find an image you like and add it into the `colored` folder inside `Caffemodel\images`, then just run the program. 



# The Models
Each black and white image consists of 1 layer where each pixel has a value between 0-255 reprecenting the brightness / black to white scale. Colored images consist of three layers, R`Red` G`Green` B`Blue` with each layer having a value between 0-255 for each pixel. But just using the 1 value for each 3 layers will not nessesarily result in a correct RGB value. Neural networks works in creating relations between a input value to an output value. The neural network needs to find features that can link the grid of grayscale values to three grids for RGB. This is how the 2 models that we wrote work.

### Simple model
This model is a neural net that trains on only one image thus it only becomes good to restore the same image back from black and white to colorized. This has very litte practical use but it is a good entryway to understand the advanced model.

### Advanced model
Caffeemodel is a deep learning framework and we use already created weights for our testing. The colorizing is fairly good although the size of the weight file is only 126MB so we don't expect anything increadibly accurate.

### Caffemodel / Advanced pre-trained model

The way we used the caffemodel was by first converting an image to black and white increasing it's saturation before starting the colorization. Later we will compare this to not doing any preprosessing of the original black and white image to see if it helped. One caveat to our comparison is that even if one pixel has an increased in R + 1 from the original it will still count as a much as if it were R + 100, the accuracy is based othe formula `(r+g+b)/('dimensions of picture' * 3)`. The effectivness of the saturation is a bit modest and sometimes decreases the accuracy. To really increase it's accuary we need to train the weights of the models we used.
The codebase is based of geeksforgeeks code https://www.geeksforgeeks.org/black-and-white-image-colorization-with-opencv-and-deep-learning/ we modified it aswell and added some functionality and made it streamlined for us.

# Results

### Simple model
As mentioned earlier, this model is only good at restoring the same image. Trying any other results in a mess :P
![image](https://user-images.githubusercontent.com/61740233/207275768-096ab527-b976-41b8-a91e-5ecf4960f06b.png)
As we see with this img the model is trained on the woman and can manage to restore her to colorized but whenever we try to color another image it doesn't give any good results. We tryed applying our preprocessing steps to get better results but nothing worked. The model is just to "dumb" and needs to be trained more.


### Advanced model
The program did a fairly good job, the main issues we saw were some inaccuracy in shading the colors(T1-T3) and sometimes the backgrounds had innacurate colors(T2). 

![image](https://user-images.githubusercontent.com/60612841/207373258-902bda39-4fe4-4746-a315-2584db6d88c1.png)

![image](https://user-images.githubusercontent.com/60612841/207372486-7b3cb7a9-9ac0-4f04-b7d4-6197a8a7b66e.png)

![image](https://user-images.githubusercontent.com/60612841/207372980-c5cd05d2-ddfc-4cb5-81ac-b31e453a0e63.png)




### Caffemodel / Advanced pre-trained model
Here are some of the outpus for the caffemodel, the left picture is the original picture and the right is the colorized.

#### Saturated T1
![Screenshot 2022-12-13 121106](https://user-images.githubusercontent.com/120106208/207303043-14d3f8b4-5fcb-4589-83c5-084bc53e6d65.png)
`R: 420678  G: 1015762  B: 791926`
As we can see the green value is quite high since the tree in the picture is not as green and more brown colored.
Accuracy:`0.585`
#### Not Saturated T1
![Screenshot 2022-12-13 121045](https://user-images.githubusercontent.com/120106208/207302957-615ac633-6ca6-4e68-a79c-29028006b905.png)
`R: 420759  G: 1015784  B: 791858`
Accuracy:`0.585`, the difference between the two is around `-9.129E-6`(Not satureted - saturated)
#### Saturated T2

![Screenshot 2022-12-13 121836](https://user-images.githubusercontent.com/120106208/207304257-22edaeb4-0d9c-4bfe-bb91-7483c5b89c0d.png)
`R: 1215525  G: 116878  B: 703572`
This picture has been reshaped since it's resolution was larger than my montior, but the comparison was made by the original sized images  the blue is quite significant higher since the hills in the background are actually blue rather than green.
Accuracy:`0.452`

#### Not Saturated T2
![Screenshot 2022-12-13 121932](https://user-images.githubusercontent.com/120106208/207304389-dad1697b-7f9a-42d9-96f2-3ad795a6d0d6.png)
`R: 1214169  G: 119143  B: 703305`
Accuracy:`0.453`, the difference between the two is around `1.43E-6`


#### Saturated T3
![Screenshot 2022-12-09 161151](https://user-images.githubusercontent.com/120106208/206735776-d5c6e35b-9c78-4f3c-8e02-dab9cc25038e.png)
`R: 539146  G: 598922  B: 1024964`
The high blue value is due to the really dark blue on the left hand side of the picture. Accuracy:`0.637`

#### Not Saturated T3
![Screenshot 2022-12-09 161312](https://user-images.githubusercontent.com/120106208/206735892-bdfcd25a-92d1-44c0-b7ae-d2313139c748.png)
`R: 539267  G: 598991  B: 1024935`
Accuracy:`0.637`, the difference between the two is around `-4.74E-5`

# Evaluation
## Caffemodel / Advanced pre-trained model
The Caffemodel is a bit innacruate in it's shading of colors and the preprossesing method we used to increase it's saturation does not always better the accuracy. But as forementioned it's hard to develop a method to evaluate colorization accuracy.

# Final words
To train a good model it takes large datasets with a lot of different features. According to our research to train a ok model with verry few features it's normal that it needs to train for 1 day. To get a good model that can find a lot of different features this time takes even longer. Thus it's a good thing that there exists these pre-trained models avalible.

