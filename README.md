# MiniProject D7041E










# Image colorization by caffemodel

The way we used the caffemodel was by first converting an image to black and white increasing it's saturation before starting the colorization. Later we will compare this to not doing any preprosessing of the original black and white image to see if it helped. One caveat to our comparison is that even if one pixel has an increased in R + 1 from the original it will still count as a much as if it were R + 100.

