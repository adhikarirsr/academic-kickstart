+++
# Date this page was created.
date = 2019-01-19

# Project title.
title = "Cracking Captcha using Deep Learning"

# Project summary to display on homepage.
summary = ""

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning",]`
tags = ["machine-learning", "deep-learning", "captcha","python","mathematica", "julia"]
categories = ["Resources"] # still works in v3.1?

# Optional external URL for project (replaces project detail page).
external_link = ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references
#   `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides = ""

# Links (optional).
url_pdf = ""
url_slides = ""
url_video = ""
url_code = ""

# Custom links (optional).
# Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
#url_custom = [{icon_pack = "fab", icon="twitter", name="Follow", url = "https://twitter.com/janani137"}, {icon_pack = "fab", icon="twitter", name="Follow R-Ladies East Lansing", url = "https://twitter.com/RLadiesELansing"}]
url_custom = []
# Does the project detail page use math formatting?
math = true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
[image]
  # Caption (optional)
  caption = ""

  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = "Smart"

  # Show image only in page previews?
  preview_only = false

+++
## Research
As an academician, we have been mostly exploring theoretical aspects of machine learning. This project grew out of our need to get our hands dirty. So, the idea is to explore deep learning by figuring out how to crack captcha. We will play with different DNN models. Here, the idea is not to come up with an original method but shamefully use previously tested models. Hopefully, while doing so we learn how to code up the model in different platforms and develop a work flow for machine learning projects.

## Tools

For scientific computing, we have have been using $\textit{Mathematica}$. So, firstly we will $\textit{Mathematica}$’s inbuilt Neural Network functions and tools.

We have used $\textit{Python}$ for data generation. We would also like to use $\textit{Python}$’s ML packages like: $\textit{PyTroch, Keras, Fastai}$.

Lastly, we would like to use $\textit{Julia}$’s ML packages like: $\textit{Flux, KNet}$.


## Procedure
* Using the following python code to create 50,000 Captcha:

```python
import random
import numpy as np
import string
from captcha.image import ImageCaptcha

image = ImageCaptcha()
clist = list(string.ascii_uppercase+string.digits)
random.shuffle(clist)

labels = []
for j in range(50000):
    randstr = ''
    for i in range(4):
        randstr = randstr + random.choice(clist)
    labels.append(randstr)
    data = image.generate(randstr)
    image.write(randstr, '~/Desktop/Neural_nets/data_10/'+randstr+'.png')

with open('~/Desktop/Neural_nets/data_10/'+'labels.txt','w') as f:
  for labs in labels:
      f.write('%s\n' %labs)
```

* We are in a process of writing and training a model like: VGG16
