### [CIFAR-10 - Object Recognition in Images](https://www.kaggle.com/c/cifar-10)

CIFAR-10  is an established computer-vision dataset used for object recognition. It is a subset of the 80 million tiny images dataset and consists of 60,000 32x32 color images containing one of 10 object classes, with 6000 images per class. It was collected by Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton.

The main idea of this project is to experiment different CNN models and find the "best".
By using pre-trained ImageNet models, we can save a lot of times. Because we believe model trained on ImageNet are like "veterans" who are very good at classifying images. What we need to do is just fine-tuning by using a small learning rate.  
The models used in this projects are resnet-18, resnet-152, inception-v3, vgg-16.  
Techniques can be used are weight decay(same as regularizations on linear regression),  mixed-up([mix two training samples as one](https://courses.d2l.ai/berkeley-stat-157/slides/3_21/16-Detection.pdf)), learning-rate decay(decreasing learning rate as epoch increases). If possible, we can use multi-gpu training.