# MiniProject D7041E

In this project we have used two models capable of restoring color to grayscale images using neural nets. The accuracy of the models was tested with various preprocessing steps such as color saturization in order to see what effect, positive or negative, these had on the results. By doing this we hope to show two ways of implementing grayscale to color models with neural net and how these are affected by preprocessing. The accuracy of the results is measured by summarizing the amount of pixels containing a differing rgb value compared to the original picture divided by the total amount of pixels in the image.



# Setup
In order to run our code you need to install a few libries. Most of the libraries we used is bellow but something might be missing.
`pip install keras tensorflow numpy cv2 pillow jupyter scikit-image` To add we used python 3 and the latest version of tensorflow and wrote everything with visual studio code.

### Simple and Advanced model
These are verry simple to run. Simply download the zip, open it in whatever jupiter ide then install the nessesary libraries.

### Caffemodel / Advanced pre-trained model
To setup the caffemodel start by downloading the repository and the weights from: https://drive.google.com/drive/folders/1FaDajjtAsntF_Sw5gqF0WyakviA5l8-a and 
put the files into `Caffemodel\Model`. Find an image you want to colorize and add it into the `colored` folder inside `Caffemodel\images`, then just run the program.



# The Models
Each black and white image consists of 1 layer where each pixel has a value between 0-255 reprecenting the brightness / black to white scale. Colored images consist of three layers, R`Red` G`Green` B`Blue` with each layer having a value between 0-255 for each pixel. But just using the 1 value for each 3 layers will not nessesarily result in a correct RGB value. Neural networks works in creating relations between a input value to an output value. The neural network needs to find features that can link the grid of grayscale values to three grids for RGB. This is how the 2 models that we wrote work.

### Simple model
This model is a neural net that trains on only one image thus it only becomes good to restore the same image back from black and white to colorized. This has verry litte practical use but it is a good entryway to understand the advanced model.

### Advanced model
`TODO`

### Caffemodel / Advanced pre-trained model

The way we used the caffemodel was by first converting an image to black and white increasing it's saturation before starting the colorization. Later we will compare this to not doing any preprosessing of the original black and white image to see if it helped. One caveat to our comparison is that even if one pixel has an increased in R + 1 from the original it will still count as a much as if it were R + 100. The effectivness of the saturation is a bit modest since to really increase it's accuary we need to change the weights of the models we used.
The codebase is based from geeksforgeeks code https://www.geeksforgeeks.org/black-and-white-image-colorization-with-opencv-and-deep-learning/ we modified it aswell and added some functionality and made it streamlined for us.

# Results

### Simple model
As mentioned earlier, this model is only good at restoring the same image. Trying any other results in a mess :P
![image](https://user-images.githubusercontent.com/61740233/207275768-096ab527-b976-41b8-a91e-5ecf4960f06b.png)
As we see with this img the model is trained on the woman and can manage to restore her to colorized but whenever we try to color another image it doesn't give any good results. We tryed applying our preprocessing steps to get better results but nothing worked. The model is just to "dumb" and needs to be trained more.


### Advanced model
`TODO`

### Caffemodel / Advanced pre-trained model
Here are some of the outpus for the caffemodel, the left picture is the original picture and the right is the colorized.

#### Saturated
![Screenshot 2022-12-09 153121](https://user-images.githubusercontent.com/120106208/206734686-515ff36d-d5f3-4e80-aeb9-6435751818eb.png)
`R: 125074  G: 188954  B: 57200`
As we can see the green value is quite high since the tree in the picture is not as green and more brown colored.

#### Not Saturated
![Screenshot 2022-12-09 153316](https://user-images.githubusercontent.com/120106208/206734479-155a0191-37b1-42bd-8175-25ffedf32984.png)
`R: 116567  G: 200574  B: 60275`

#### Saturated
![Screenshot 2022-12-09 155519](https://user-images.githubusercontent.com/120106208/206735127-b67ad3ce-3976-4ddb-8a58-e577bb139f54.png)
`R: 1246894  G: 126337  B: 717091`
This picture has been reshaped since it's resolution was larger than my montior, but the comparison was made by the original sized images  the blue is quite significant higher since the hills in the background are actually blue rather than green.

#### Not Saturated
![Screenshot 2022-12-09 155159](https://user-images.githubusercontent.com/120106208/206735663-85e3df11-f6ce-43c4-942e-8344bbf6f1fd.png)
`R: 1246195  G: 127364  B: 716987`

#### Saturated
![Screenshot 2022-12-09 161151](https://user-images.githubusercontent.com/120106208/206735776-d5c6e35b-9c78-4f3c-8e02-dab9cc25038e.png)
`R: 539146  G: 598922  B: 1024964`
The high blue value is due to the really dark blue on the left hand side of the picture.

#### Not Saturated
![Screenshot 2022-12-09 161312](https://user-images.githubusercontent.com/120106208/206735892-bdfcd25a-92d1-44c0-b7ae-d2313139c748.png)
`R: 539267  G: 598991  B: 1024935`

# Evaluation
`TODO: Evaluate`

# Final words
To train a good model it takes large datasets with a lot of different features. According to our research to train a ok model with verry few features it's normal that it needs to train for 1 day. To get a good model that can find a lot of different features this time takes even longer. Thus it's a good thing that there exists these pre-trained models avalible.

