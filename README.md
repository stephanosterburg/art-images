<p align="center">
    <a href="https://www.python.org/dev/peps/"><img src="https://img.shields.io/badge/code_style-standard-brightgreen.svg" alt="Standard - Python Style Guide"></a>
</p>

<center><img src='images/GoogleArt_cropped.png'></center>

    
# Project - Art Images

At [kaggle](https://www.kaggle.com) we can find a dataset containing a collection of art images of google images, yandex images and from [The Virtual Russian Museum](http://rusmuseumvrm.ru/collections/?lang=en). The dataset has about 9000 images with five categories:
1. Drawings and Watercolors
2. Paintings
3. Sculpture
4. Graphic Art
5. Iconography (old Russian art)

### Modivation

Can we use deep learning and create a convolutional neural networks (CNN) to predict what category a given image is from.


### Code Snippet

I ended up adding several more layers, including `Dropout` layers to help to avoid over-fitting.


```python
model = Sequential([
    Conv2D(32, (3, 3), input_shape=input_shape, activation='relu'),
    MaxPooling2D(pool_size=(2, 2)),
    Dropout(0.2),

    Conv2D(32, (3, 3), activation='relu'),
    MaxPooling2D(pool_size=(2, 2)),
    Dropout(0.2),

    Conv2D(64, (3, 3), activation='relu'),
    MaxPooling2D(pool_size=(2, 2)),
    Dropout(0.2),

    Flatten(),
    Dense(128, activation='relu'),
    Dropout(0.2),
    Dense(64, activation='relu'),
    Dropout(0.2),
    Dense(5, activation='softmax')
])
```

With the simple sequential model the computational time wasn't too bad but with the given dataset, the time went up from several minutes per epochs to nearly 30 minutes per epochs.

### Cloud Service

To free up the computer I used `Gradient` from [paperspace](https://gradient.paperspace.com/). Which allows me to prototype locally (prove of concept) and compute offline.


---

License MIT © [Stephan Osterburg](https://stephanosterburg.github.io)
