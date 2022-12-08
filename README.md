# MiniProject D7041E






In this project we have created two models capable of restoring color to grayscale images using neural nets. The accuracy of the models was tested with various preprocessing steps such as color saturization in order to see what effect, positive or negative, these had on the results. By doing this we hope to show two ways of implementing grayscale to color models with neural net and how these are affected by preprocessing. The accuracy of the results is measured by summarizing the amount of pixels containing a differing rgb value compared to the original picture divided by the total amount of pixels in the image.



# Image colorization by caffemodel

The way we used the caffemodel was by first converting an image to black and white increasing it's saturation before starting the colorization. Later we will compare this to not doing any preprosessing of the original black and white image to see if it helped. One caveat to our comparison is that even if one pixel has an increased in R + 1 from the original it will still count as a much as if it were R + 100.

