# Hitachi-ASR

## Contributors
- Aniket Kumar
- Agnibha Sinha

##About
The goals of the this Project are as follows:
- "Identify numeric keywords in continuous speech"
- "Locate keywords in timeframes or in post-processed transcripts"
Both these tasks are tackled in the following 2 methods.

##Methods

###Pre-Processing using Speech Yolo

**Data**
- The data needed to train in the model is a labelled 1 sec audio clip of a keyword.
- Each Keyword Directory has multiple .wav and .wrd files representing audio clips and
a text file with [start end keyword] tuple as in the files.

**Feature Extraction:**
- Extract preliminary features using Soundfile, a two-dimensional (frames x channels)
NumPy array is returned.
- Take Short Term Fourier Transform of the audio with windo-size=0.02, window-
stride=0.01.
- We convert the output matrix into magnitude and phase using magphase function
of librosa library.
- We take log of 1 + the output matrix to avoid errors popping in for features values
which are almost equal to 1 using numpy library of python.
- Conversion into a standard 160x100 NumPy array takes place which is used as data for our 
model after normalization.

**Model**
- The CNN multi-layer model has 16 Convoluted Layers with 2 Fully Connected layers with 5 Pooling layers, 
each Convoluted Layer Normalises and applies ReLU before going to the next layer.
- The model is based on dividing the last connected into 3 parts c, b, k which represent container, box, 
and keyword and can be set as per the users after which a probability of keyword existing in each box is 
calculated using the loss function and greatest probability above a threshold is returned.

###Post-Processing using Soundex

**Data**
-first_point
-second_point

**Algorithm**
-first_point
-second_point

## References
- [Basics of ASR](http://www.cs.columbia.edu/~julia/courses/CS6998-2019/%5B09%5D%20Automatic%20Speech%20Recognition.pdf)

- [Aradilla, Guillermo and Ajmera, Jitendra. (2007). Detection and
Recognition of Number Sequences in Spoken Utterances.](https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.367.7514&rep=rep1&type=pdf)

- [Speech YOLO paper](https://arxiv.org/pdf/1904.07704.pdf)



