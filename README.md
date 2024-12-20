<h1>Video Captioning using Sequence-to-Sequence LSTMs</h1>

<h2>Gaurav Prakash - 211IT022<br>Srihari Madhusudana - 211IT069<br>Vivek Prem Nair - 211IT084</h2>

Video Captioning is an encoder-decoder mode based on sequence-to-sequence learning.
It takes a video as input and generates a caption describing the event in the video. 

The importance of captioning lies in its ability to make video more accessible in numerous ways. Automated video caption generator helps searching of videos in websites better.  It can be used for clustering of videos based on their content easier.

<h2>Table of contents</h2>
<a href="#Inspiration">Inspiration</a>
<br><a href="#Dataset">Dataset</a>
<br><a href="#Setup">Setup</a>
<br><a href="#Usage">Usage</a>
<br><a href="#Model">Model</a>
<br><a href="#TrainingArchitecture">Training Architecture</a>
<br><a href="#InferenceArchitecture">Inference Architecture</a>
<br><a href="#Loss">Loss</a>
<br><a href="#Metric">Metric</a>
<br><a href="#Features">Features</a>
<br><a href="#Scripts">Scripts</a>
<br><a href="#FutureDevelopment">Future Development</a>
<br><a href="#References">References</a>

<h2 id="Inspiration">Inspiration</h2>
Previous CNN methods used fail to capture spatial and temporal dependencies that are crucial for understanding data sequences for processing that 
allows us to leverage LSTMs for the task. 

<h2 id="Dataset">Dataset</h2>
This project is built on the MSVD dataset, which can be requested from the authors at Microsoft, Inc. 
It contains 1450 training videos and 100 testing videos. We had access to a subset of the dataset on request.

<h2 id="Setup">Setup</h2>

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
 
 <h3>train.py</h3> contains the model architecture
 <h3>predict_test.py</h3> is to check for predicted results and store them in a txt file along with the time taken for each prediction
 <h3>predict_realtime.py</h3> checks the results in realtime
 <h3>model_final</h3> folder contains the trained encoder model along with the tokenizerl and decoder model weights.
 <h3>features.py</h3> extracts 80 frames evenly spread from the video and then those video frames are processed by a pre-trained VGG16 so each frame
    has 4096 dimensions. So for a video we create a numoy array of shape(80, 4096)
 <h3>config.py</h3> contains all the configurations for the model

<h2 id="Future Development">Future Development</h2>
<ul>
 <li> Adding attention blocks and pretrained embeddding like glove so that the model understands sentences better</li> 
 <li> Using other pretrained models to extract features specially ones made for understanding videos like I3D</li> 
 <li> Right now the model uses only 80 frames improvements need to be made so that it can work even for longer videos</li>
 <li> Adding a UI to the project</li>
</ul>

 <h2 id="References">References</h2>
 <ul>
  <li>[SV2T paper 2015](https://arxiv.org/abs/1505.00487)</li>
  <li>[Keras implementation](https://github.com/CryoliteZ/Video2Text)</li>
 </ul>
 
 
 
