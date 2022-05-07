# Flower-Classification-on-TPU
This Kaggle competition is about classifying 104 types of flowers based on their images drawn from five different public datasets.

<img width="405" alt="image" src="https://user-images.githubusercontent.com/76504592/167242928-ca2d7122-645d-44f7-a3eb-d35807d7de03.png">


## Tensor Processing Unit(TPU)
TPUs are powerful hardware accelerators specialized in deep learning tasks. They were developed (and first used) by Google to process large image databases, such as extracting all the text from Street View. This competition is designed for you to give TPUs a try.
More information on TPU : https://www.kaggle.com/docs/tpu

<img width="299" alt="image" src="https://user-images.githubusercontent.com/76504592/167243066-baaa7533-4358-4518-a6b8-efbf50157908.png">


## Data Description :
This competition provides its files in TFRecord format. The TFRecord format is a container format frequently used in Tensorflow to group and share data files for optimal training performace. Each file contains the id, label (the class of the sample, for training data) and img (the actual pixels in array form) information for many images.

* 12753 training images
* 3712 validation images
* 7382 unlabeled test images

## Approach to get 95% Accuracy [Kaggle Code](https://www.kaggle.com/code/shivanisinghal/flower-classification-on-tpu/data) -

Use the [getting started notebook.](https://www.kaggle.com/code/mgornergoogle/getting-started-with-100-flowers-on-tpu/notebook)

### 1. Use Transfer learning with fine tuning 
I have used [EfficientNet](https://paperswithcode.com/method/efficientnet) here. 
First, freeze the weights of the pretrained network and trian only the added layers.

<img width="587" alt="image" src="https://user-images.githubusercontent.com/76504592/167243463-d8db84f5-5293-4c72-a155-b35d5363e7d3.png">

Second, fine tune the whole network.

<img width="494" alt="image" src="https://user-images.githubusercontent.com/76504592/167243583-2a0f6fa5-8a48-4440-95ce-c528c58e7723.png">

##### Model details 

<img width="590" alt="image" src="https://user-images.githubusercontent.com/76504592/167243622-7e850d9b-9256-4660-9741-095727eec4b3.png">

### 2. Use Learning Rate scheduling for fine tuning -

High initial learning rates can make loss explode. It is usually better linearly to increase learning rate from very small value over the first ~5000 iterations. Moreover, if we increase the batch size by N, also scale the initial learning rate by [N. Goyal et al, Accurate, Large Minibatch SGD: Training ImageNet in 1 Hour.](https://arxiv.org/pdf/1706.02677.pdf)

<img width="338" alt="image" src="https://user-images.githubusercontent.com/76504592/167243855-0dfff9e7-8464-4ca9-a5fb-41e6f7f976bf.png">

<img width="371" alt="image" src="https://user-images.githubusercontent.com/76504592/167243873-3816672e-fa68-4968-a653-b4048360ad5c.png">

## Results -

Confusion Matrix plot :

![output](https://user-images.githubusercontent.com/76504592/167244103-e260706a-270f-4a31-bf43-ba67ff895fea.png)

Model Loss and Accuracy plot:

![output1](https://user-images.githubusercontent.com/76504592/167244219-b44cd04c-7e19-4f50-bebc-97ca82e5f105.png)

## Next Steps :

* Use simple Ensemble of DenseNet201 and EfficientNetB7
* Use data augmentation
* Use label smoothing to have better generalization







