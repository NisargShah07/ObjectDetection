# ObjectDetection
This is the Deep Learning Model for the Object Detection process.<br/>
This Model is combination of ResNet101V2 and DenseNet201.<br/>
Both these pre-trained models are used for feature extraction. Here I am using Imagenet weights.<br/>
The code is easy to implement. First block imports all the necessary libraries.<br/>
The second block loads the CIFER10 dataset.<br/>
Third block downloads both ResNet1001V2 and DenseNet201 pre-trained models.<br/>
The fifth block generates the custom model combining those two pre-trained models.<br/>
I am getting a testing accuracy of around 80%.
