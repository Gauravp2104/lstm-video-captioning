# Video-Captioning

Video Captioning is an encoder decoder mode based on sequence to sequence learning.
It takes a video as input and generates a caption describing the event in the video. 

The importance of captioning lies in its ability to make video more accessible in numerous ways. 
Automated video caption generator helps searching of videos in websites better. 
It can be used for clustering of videos based on their content easier.
This is a brief overview of my project. To understand the project in details check out my medium <a href="https://medium.com/analytics-vidhya/video-captioning-with-keras-511984a2cfff">post</a>. I also did a <a href="https://youtu.be/DJEnkhKPbxA">live session</a> on this you can check that as well.

## Table of contents
* <a href="#Inspiration">Inspiration</a>
* <a href="#Dataset">Dataset</a>
* <a href="#Setup">Setup</a>
* <a href="#Usage">Usage</a>
* <a href="#Model">Model</a>
  * <a href="#TrainingArchitecture">Training Architecture</a>
  * <a href="#InferenceArchitecture">Inference Architecture</a>
  * <a href="#Loss">Loss</a>
  * <a href="#Metric">Metric</a>
* <a href="#Features">Features</a>
* <a href="#Scripts">Scripts</a>
* <a href="#FutureDevelopment">Future Development</a>
* <a href="#References">References</a>

<h2 id="Inspiration">Inspiration</h2>
Previous CNN methods used fail to capture spatial and temporal dependencies that are crucial for data

<h2 id="Dataset">Dataset</h2>
This project is build on the MSVD dataset, which can be requested from the authors at Microsoft, Inc. 
It contains 1450 training videos and 100 testing videos. We had access to a subset of the dataset.

<h2 id="Setup">Setup</h2>
Clone the repository : <code>git clone https://github.com/Shreyz-max/Video-Captioning.git</code>

Video Caption Generator: <code>cd Video-Captioning</code>

Create environment: <code>conda create -n video_caption python=3.7</code>

Activate environment: <code>conda activate video_caption</code>

Install requirements: <code>pip install -r requirements.txt</code>

<h2 id="Usage">Usage</h2>
To use the models that have already been trained

For faster results extract the features of the video and save it in feat folder of the testing_data.

To convert into features run the extract_features.py file as <code>python extract_features.py</code>

Run train.py for local training of the LSTM inference model. 

<h2 id="Model">Model</h2>

<h3 id="TrainingArchitecture">Training Architecture</h3>

<p align = "center"><img align = "center" src = "images/model_train.png" /></p>

<h3 id="InferenceArchitecture">Inference Architecture</h3>

<h3 id="EncoderModel">Encoder Model</h3>
<p align = "center"><img align = "center" src = "images/model_inference_encoder.png" /></p>

<h3 id="DecoderModel">Decoder Model</h3>
<p align = "center"><img align = "center" src = "images/model_inference_decoder.png" /></p>

<h3 id="Loss">Loss</h3>
This is the graph of epochs vs loss. The loss used is categorical crossentropy.
<p align = "center"><img align = "center" src = "images/loss.png" /></p>

<h3 id="Metric">Metric</h3>
This is the graph of epochs vs metric. The metric used is accuracy.
<p align = "center"><img align = "center" src = "images/accuracy.png" /></p>

<h2 id="Features">Features</h2>
<ul>
 <li> Realtime implementation</li>
 <li> Training models using LSTMs for potentially applying videos of varying lengths</li>
 <li> Beam search</li>
 </ul>


 <h2 id="Scripts">Scripts</h2>
 
 * **train.py** contains the model architecture
 * **predict_test.py** is to check for predicted results and store them in a txt file along with the time taken for each prediction
 * **predict_realtime.py** checks the results in realtime
 * **model_final** folder contains the trained encoder model along with the tokenizerl and decoder model weights.
 * **features.py** extracts 80 frames evenly spread from the video and then those video frames are processed by a pre-trained VGG16 so each frame
    has 4096 dimensions. So for a video we create a numoy array of shape(80, 4096)
    config.py contains all the configurations i am using
 * **Video_Captioning.ipynb** is the notebook i used for training and building this project.

<h2 id="Future Development">Future Development</h2>
<ul>
 <li> Adding attention blocks and pretrained embeddding like glove so that the model understands sentences better</li> 
 <li> Using other pretrained models to extract features specially ones made for understanding videos like I3D</li> 
 <li> Right now the model uses only 80 frames improvements need to be made so that it can work even for longer videos</li>
 <li> Adding a UI to the project</li>
</ul>

 <h2 id="References">References</h2>
 
 [SV2T paper 2015](https://arxiv.org/abs/1505.00487)
 
 [Keras implementation](https://github.com/CryoliteZ/Video2Text)
#   l s t m _ v i d e o _ c a p t i o n i n g  
 