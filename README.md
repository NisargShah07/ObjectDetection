# ObjectDetection
This is the Deep Learning Model for the Object Detection process.<br/>
This Model is combination of ResNet101V2 and DenseNet201.<br/>
Both these pre-trained models are used for feature extraction. Here I am using Imagenet weights.<br/>
The code is easy to implement. First block imports all the necessary libraries.<br/>
<b>import numpy as np<br/>
import tensorflow<br/>
import tensorflow.keras as keras</b><br/>
The second block loads the CIFER10 dataset.<br/>
<b>(x_train, y_train), (x_test, y_test) = keras.datasets.cifar10.load_data()</b><br/>
Third block downloads both ResNet1001V2 and DenseNet201 pre-trained models.<br/>
<b>model1=keras.applications.ResNet101V2(include_top=False,input_shape=(32,32,3))<br/>
flat1=keras.layers.Flatten()(model1.layers[-1].output)<br/>
model2=keras.applications.DenseNet201(include_top=False,input_shape=(32,32,3))<br/>
flat2=keras.layers.Flatten()(model2.layers[-1].output)</b><br/>
The fifth block generates the custom model combining those two pre-trained models.<br/>
<b>def model_vgg19():<br/>
  concatLayer=keras.layers.Concatenate(axis=1)([flat1,flat2])<br/>
  layer1=keras.layers.Dense(units=256,activation='relu')(concatLayer)<br/>
  layer4=keras.layers.Dense(units=128,activation='relu')(layer1)<br/>
  layer7=keras.layers.Dense(units=10,activation='softmax')(layer4)<br/>
  model=keras.Model(inputs=[model1.inputs,model2.inputs],outputs=layer7)<br/>
  return model</b><br/>
I am getting a testing accuracy of around 80%.
