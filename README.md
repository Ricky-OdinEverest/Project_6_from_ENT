# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 6: Wake Word Classification Model 

---
## Problem Statement
A local startup has reached out to me to create a wakeword model prototype for their upcoming choose your own adventure mobile game. I must design a model capable of accurately identifying a specific keyword from a variety of other words and environmental noise. To accomplish this , I will use both publicly available audio data and the audio data that I generate myself.

I will test the accuracy of the model using a validation and test dataset, including the audio data that I generate myself. In addition, I will use confusion matrices to identify any common misclassifications that the model may make, which will help me to optimize the algorithm further.


---

## Table of Contents

1. [Data Preparation](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/preprocess_step1.ipynb) : Read and combine data from soures. Group data for EDA and Modeling.

2. [Data Preparation 2](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/preprocess_step1.ipynb) create a recorder function to make audio files of my own voice in both high and in quality

3. [Data Preparation 3](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/preprocess_step1.ipynb) create a function to modify audio to create more targets for wake word

4. [EDA](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/EDA_FOR_AUDIO_some_cleaning.ipynb) :  Explore data and ensure it's all useable

5. [Models](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/RNN_CNN_for_audiodata.ipynb) :Further data preprocessing. Instantiate and evaluate CNN and RNN models


---
## Data

The data is a combination of speech data from Mozilla Common Voice as well as Environemtal sounds from UrbanSound8k

#
### Datasets
|Dataset|Description|
|---|---|
|[Urban Sound 8k](https://urbansounddataset.weebly.com/urbansound8k.html)| Fold1 was used for the project
[Common Voice](https://commonvoice.mozilla.org/en) | Random samples were pulled from the Common Voice Delta Segment 12.0
[My own voice] I produced over 500 samples using | differnt devices, software, and python editing tools.



---
## EDA

During the exploratory data analysis (EDA) phase, I checked if the audio samples were loud enough to be heard clearly. Unfortunately, some of the data didn't meet the required volume level and couldn't be used in the analysis. However, I did include some of the lower quality audio data to account for potential issues with the microphone or background noise. My aim was to use enough data to create an accurate wakeword model while ensuring that the quality of the data was sufficient.
The first image below shows the frequncy ranges for the data. I did not discrimate based on frequency but I did end up uniformly sampling all data at 1600HZ in order to lower compute time and create less noise


![HZ](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/p6img/download%20(14).png)
![DB](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/p6img/download%20(15).png)
---

## Model Evaluation 

At first, I developed a set of models that performed well in terms of accuracy during testing, but failed to produce the desired results during inference. Specifically, I encountered an issue where the initial model could only recognize variations of my voice, and struggled to classify anything else I said as not being the wake word. This meant that the model was not effective in identifying other spoken words that were not the wake word.

To fix this I decided to augment the negative dataset with 200 random spoken words of my own voice. This helped to improve the classification of other spoken words, while still maintaining high levels of accuracy during testing and validation. By doing so, the model was able to better differentiate between spoken words that were the wake word and those that were not. Overall, this adjustment proved to be a successful solution to the issue and resulted in improved performance during inference.

![Best Final Model](https://git.generalassemb.ly/ricky-odineverest/Project_6/blob/main/p6img/download%20(26).png)

---
## Conclusions
While the current models I created work for the given data, they need more work before they are suitable for general consumers. One issue is that the negative dataset needs to be expanded to make the model more accurate at recognizing non-wake words. To achieve this, I suggest including a wider variety of audio samples.

Another approach that could help improve the accuracy and robustness of the model is to use AI-generated samples from sources like 11 labs. These could provide a more extensive and diverse set of samples to improve the model's performance. 

---
## Further Study
To create a wakeword model that can recognize any wake word, it could be helpful to include a pretrained language model. This would allow the model to recognize various wake words and the context in which they are spoken, which could improve the model's ability to identify different word patterns and variations. By integrating a pretrained language model, we can make the wakeword model more adaptable and comprehensive.

---
## Software Requirements

For this project, I imported pandas, os, librosa, random, numpy, matplotlib.pyplot, python_speech_features, shutil, scipy.io, tqdm, wave, soundfile, seaborn, IPython.display, pyrubberband, tensorflow.keras, json, seaborn, sklearn.metrics, pyaudio, struct, sounddevice, time
