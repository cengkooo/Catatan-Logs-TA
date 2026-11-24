Scientific Reports
https://doi.org/10.1038/s41598-025-29200-1
Article in Press
Feature centric based deep learning approach 
for music mood recognition with HuBERT 
transformer model
Received: 7 May 2025
Accepted: 14 November 2025
Cite this article as: Sun Y. Feature 
centric based deep learning approach 
for music mood recognition with 
HuBERT transformer model. Sci Rep 
(2025). https://doi.org/10.1038/
s41598-025-29200-1
Yaoyu Sun
We are providing an unedited version of this manuscript to give early access to its 
findings. Before final publication, the manuscript will undergo further editing. Please 
note there may be errors present which affect the content, and all legal disclaimers 
apply.
If this paper is publishing under a Transparent Peer Review model then Peer 
Review reports will publish with the final article.
ARTICLE IN PRESS
© The Author(s) 2025. Open Access This article is licensed under a Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International 
License, which permits any non-commercial use, sharing, distribution and reproduction in any medium or format, as long as you give appropriate credit 
to the original author(s) and the source, provide a link to the Creative Commons licence, and indicate if you modified the licensed material. You do 
not have permission under this licence to share adapted material derived from this article or parts of it. The images or other third party material in this 
article are included in the article’s Creative Commons licence, unless indicated otherwise in a credit line to the material. If material is not included in the 
article’s Creative Commons licence and your intended use is not permitted by statutory regulation or exceeds the permitted use, you will need to obtain 
permission directly from the copyright holder. To view a copy of this licence, visit http://creativecommons.org/licenses/by-nc-nd/4.0/.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Feature Centric based Deep Learning Approach for Music Mood 
Recognition with HuBERT Transformer Model
Yaoyu Sun
Department of Vocal Music, School of Arts, Sangmyung University，03016，South Korea
Corresponding Author: Email：13730076667@163.com
ABSTRACT 
In this study, music mood classification is explored using advanced deep learning and transformer-based 
models to accurately predict the emotional content of music. Music plays a crucial role in human life, 
influencing emotions, behaviors, and mental states. Accurately classifying the mood of music is essential 
for applications such as music recommendation systems, emotional intelligence in AI, and mental health 
monitoring. With the growing impact of Artificial Intelligence (AI) in emotion recognition, sentiment 
analysis has become a vital research area, contributing to fields like social media monitoring, customer 
experience analysis, and personalized content delivery. We employ a state-of-the-art transformer-based 
model (HuBERT) in comparison with deep learning models (ConvFormer, LSTM) and pre-trained models 
(YAMNet) to evaluate their effectiveness in music mood classification. The study is conducted on a 
publicly available dataset containing five mood labels such as Aggressive, Happy, Dramatic, Sad, and 
Romantic with 500 audio files per category. To analyze and extract meaningful patterns from the dataset, 
advanced different five audio features such as Short-Time Fourier Transform (STFT), and Mel-Frequency 
Cepstral Coefficients (MFCC) are utilized. To ensure robust model evaluation, an 80-20 holdout split is 
applied. Our experimental results indicate that HuBERT achieves the highest classification accuracy of 
95%, outperforming both traditional deep learning models and pre-trained architecture. This study 
provides a comprehensive evaluation of machine learning approaches for music mood classification, 
demonstrating the potential of transformer-based models in enhancing AI-driven sentiment analysis. 
The findings contribute to the development of intelligent music recommendation systems, emotional AI 
applications, and advancements in affective computing.
INDEX TERMS: Artificial intelligence; Audio Data Processing; Deep Learning; Music Analysis; Vision 
Transformers.
1. INTRODUCTION
In this digital era, the rapid advancement of artificial intelligence (AI) and machine learning has 
significantly transformed various domains, including sentiment analysis and affective computing [1]. 
The ability to analyze and interpret human emotions through computational models has led to 
groundbreaking applications in healthcare, social media analysis, customer feedback processing, and 
music recommendation systems [2]. Among these, music mood classification has gained immense 
importance, as it enables the automatic identification of emotional content in songs, enhancing user 
experiences in streaming platforms, personalized playlists, and therapeutic applications [3].
ARTICLE IN PRESS
Sentiment analysis, a subfield of natural language processing (NLP), has traditionally focused on 
understanding human emotions from text-based data sources such as reviews, tweets, and articles [4]. 
However, with the increasing consumption of multimedia content, researchers have extended 
sentiment analysis to audio and music lyrics, allowing machines to interpret the emotional aspects of 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
songs [5]. Music is a powerful medium that evokes a wide range of emotions, and classifying its mood 
requires analyzing both acoustic signals, wearable devices [6], EEG-based signals and lyrical content 
[7]. This presents a significant challenge due to the complex interaction between melody, rhythm, 
instrumentation, and textual meaning [8].
The growth of AI has led to the emergence of deep learning-based models, which have outperformed 
traditional machine learning methods in sentiment detection, personality detection and emotion 
recognition tasks [9]. Early approaches in music mood classification relied on statistical models, 
handcrafted features, and classical machine learning algorithms such as Support Vector Machines 
(SVMs), Random Forests (RF), and k-Nearest Neighbors (k-NN) [10]. However, these models struggled 
to generalize across diverse datasets due to their dependence on manually extracted features [11]. 
The introduction of Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) 
revolutionized the field by enabling end-to-end feature learning directly from raw audio signals [12].
With the increasing complexity of multimodal sentiment analysis, transformer-based architectures 
have gained prominence due to their ability to process sequential data efficiently [13]. Transformers 
such as BERT, RoBERTa, and Vision Transformers (ViTs) have shown remarkable performance in text, 
image, and audio-based emotion classification tasks [14]. Unlike traditional deep learning models, 
transformers leverage self-attention mechanisms to capture long-range dependencies and contextual 
relationships within music lyrics and acoustic features [15]. This has led to significant improvements in 
music mood classification accuracy, making transformers a promising approach for future research 
[16].
In this research study, we aim to explore the effectiveness of deep learning, and transformer-based 
models in music mood classification. We utilize a comprehensive dataset based on five labels that 
include both audio and lyrical features, extracted using techniques such as Mel-Frequency Cepstral 
Coefficients (MFCC), Chromagram Short-Time Fourier Transform (STFT), waveforms, Root Mean 
Square Error (RMSE), and Mel-spectral contrast analysis. Our study investigates different architectures, 
including LSTMs, and transformers, comparing their classification performance across multiple mood 
categories. Furthermore, we analyze the strengths and limitations of each model to propose optimized 
frameworks for emotion recognition in music.
This research makes the following key contributions to the field of music mood classification using 
deep learning, and transformer-based models:
￿ Evaluates and compares different models, including traditional deep learning (LSTM), Hybrid deep 
learning model (ConvFormer), pre-trained models (YAMNet), and transformer-based architectures 
(HuBERT) for music mood classification.
￿ Extract key audio features such as STFT, waveform, Mel-Spectro, RMSE and MFCC to improve 
classification accuracy.
￿ It demonstrates that HuBERT achieves the highest accuracy of 95%, outperforming traditional and 
deep learning models, achieve state-of-the-art results in music mood classification, demonstrating 
the power of transformer-based architectures in understanding audio features.
ARTICLE IN PRESS
￿ Introduces a layer-wise classification approach that considers different elements of music, 
including melody, rhythm, lyrics, and harmonic structure, to enhance the accuracy of mood 
prediction.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
￿ These contributions provide a comprehensive framework for music mood classification, supporting 
AI-driven applications in music recommendation systems, affective computing, and personalized 
user experiences.
The remainder of this paper is structured as follows. Section 2 presents a review of related work on 
sentiment analysis in music using machine learning and deep learning models. Section 3 discusses the 
proposed methodology, including dataset details, feature extraction techniques, and the architecture 
used. Section 4 describes experimental setup and evaluation metrics. Section 5 provides a 
comprehensive analysis of the results and findings. Finally, Section 6 concludes the paper and outlines 
future research directions in the field of music mood classification.
2. RELATED WORK
Deep learning-based music mood classification has become of primary interest among research and 
has been developed mostly through utilizing lyrics as a main input for sentiment analysis [17]. Deep 
learning architectures, feature extraction techniques, multimodal methods have been proposed to 
increase classification accuracy by integrating some of them [18]. An integrated, multi-modal model of 
lyrics and audio signals is presented which indeed is shown to be effective at combining textual and 
acoustic features for mood classification. The results indicate that deep learning performances are 
almost an order of magnitude better than traditional machine learning techniques in this domain [19].  
Like the above, an ensemble learns based lyric classification approach has also been implemented on 
sentiment-based classification tasks using specific XGBoost and grid search [20]. Latent semantic 
analysis does seem to have some role to play in lyric-based mood classification and that performance 
can be further improved when latent semantic analysis is used with deep learning approaches [21]. 
Building on this, we extend the idea by coupling a listener model that would combine lyrics and audio 
signals with a multi-channel architecture for a more precise emotion detection [22].  With that said, 
pre-trained word embeddings such as GloVe were utilized to improve lyric-based mood classification, 
where we extracted features using Convolutional Neural Networks (CNNs). Our results support that 
pre-trained word vectors can significantly improve classification rate; thus, deep learning models are 
trained to recognize emotions in lyrics better [23]. In another study the connections between deep 
neural networks and music mood classification were emphasized using a dataset of 18,000 songs using 
an end-to-end deep learning model [24]. Alternatively, a sentence level deep learning approach has 
been suggested, where lyrics are sentence segmented to structured data to gain better granularity 
[25]. Further attempts have been made by sentiment based preprocessing methods using 
SentiWordNet to extract sentiment features in the song lyrics and the outcome shows that the 
machine learning algorithms do benefit from sentiment aware feature extraction [26]. 
Then automatic mood classification techniques further evolved by combining sentiment lexicons with 
machine learning classifiers and opened a way for robust/music search engines based on sentiment 
aware model [27]. While lyric based models by themselves do not completely reflect the mood of the 
song, a study found out that combining lyric based models with audio-based classifiers improves the 
classification accuracy [28]. Further, classification performance using recent advancements of the 
transformer models. Self-attention mechanisms can capture contextual nuances of both lyrics and 
audio features in transformer architectures and a multi modern music mood classification system 
based on transformer architectures surpasses traditional model, bi-directional GRU [29]. CNNs can 
also be integrated with Vision Transformers (ViTs) into speech emotion recognition systems and lead 
to an improved classification accuracy by utilizing CNNs for local feature extraction, and ViTs to 
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
capture global relationship [30]. Gathering comparative studies in emotion detection in text imply that 
transformer-based models, being fine-tuned on emotion datasets have significantly outperformed 
traditional machine learning models, based on their superior context understanding and semantic 
processing capabilities [31]. 
Fused by multimodal emotion recognition frameworks using pre-trained transformers across multiple 
text, speech, and video inputs, the maximum accuracy approaches are achieved (to fuse data from 
disparate modalities) [32]. Good results have been obtained in sentiment analysis from noisy and 
unstructured text using transformer-based sentiment analysis models, on social media datasets [33]. 
In addition, the transformer-based methods were used to build depression detection model and 
applied linguistic, sentiment, emotion and topic features to improve the classification accuracy using 
textual representation, which showed that transformers have the potential in mental health 
monitoring through textual analysis [34]. An emotion recognition framework is developed, which is 
based on masked learning techniques to provide more focus on relevant parts of input data to 
enhance the performance of emotion classification, especially in scenarios with incomplete or noisy 
data [35]. This serves as a state-of-the-art review on multimodal emotion recognition using 
transformers, proving to be a key resource for the research community in the same domain [36]. To 
illustrate that transformers can process as well as integrate different data modalities for improving 
classification accuracy, the authors have implemented an automatic music mood classification system 
based on a multi modal framework [37]. In addition, a review of literature on transformer models in 
machine learning emphasizes the application of emotion recognition and showed superiority of these 
models compared to the traditional models in detecting sentiment and mood in various sentiment and 
mood classification tasks [38]. Since the deep learning and transformer-based models are growing in 
music mood classification, these advancements demonstrate that the multimodal approaches are 
crucial to geometric sentiment analysis in music [39]. In recent years, transformer-based models have 
proved to be effective when applying them to mood and emotion classification tasks. Also, they are 
especially good at dealing with complex datasets over multiple modalities, by having the ability to 
capture contextual and sequential information [40]. 
Recent studies have explored emotion recognition across music and speech using deep learning and 
hybrid approaches. One work applied pre-trained CNN models such as AlexNet and VGG16 on chroma 
spectrograms to extract deep visual features for music emotion recognition, achieving up to 89.2% 
accuracy with VGG16 on the Fc7 layer, highlighting the effectiveness of deep feature representations 
in this domain [41]. Another study extended this line of research by focusing on EEG-based emotion 
recognition during music listening, where spectrograms of brain signals were analyzed using transfer 
learning with AlexNet and VGG16, showing promising results in classifying mood states such as happy, 
sad, relaxed, and angry [42]. Complementing these efforts, a hybrid framework for speech emotion 
recognition combined acoustic features (e.g., MFCC, RMS, zero-crossing rate) with deep features 
extracted from CNNs, and further refined them through feature selection, achieving state-of-the-art 
performance across multiple benchmark datasets [43]. Together, these studies demonstrate the 
growing role of deep and hybrid feature extraction methods in advancing emotion recognition tasks 
across music, brain signals, and speech.
ARTICLE IN PRESS
Based on analysis of existing literature, prior work on using various approaches for music mood 
recognition has mostly relied on supervised feature learning and limited contextual representation. To 
fill this gap, the study emphasizes the novelty of applying HuBERT, whose architecture is specifically 
designed to capture fine-grained audio patterns and long-range dependencies through self-supervised 
pretraining. The aspects of its application to music mood recognition that are novel compared to 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
existing transformer-based approaches include the exploitation of hierarchical acoustic 
representations and context-aware embeddings, which allow the model to learn mood-specific cues 
embedded in temporal and spectral domains more effectively. This contribution offers a distinct 
advancement over earlier transformer-driven methods.
3. RESEARCH PROPOSED METHODOLOGY
The research implements a structured approach to transform audio data before performing machine 
learning and deep learning model applications, as shown in figure 1. Noise reduction forms the initial 
step in which audio data processing begins through multiple operations that include digital conversion 
along with trimming sounds to a standard length and padding them when needed. The process of 
feature extraction depends on Short-Time Fourier Transform (STFT), and Mel-Frequency Cepstral 
Coefficients (MFCCs) to extract essential frequency combined with temporal characteristics [44]. Deep 
learning models consisting of ConvFormer, LSTM, and YAMNet receive the extracted features for 
processing various complex audio representations that contain sequential dependencies. The model's 
performance is measured through established evaluation metrics accuracy as well as precision and 
recall and F1-score to conduct a reliable assessment of this approach. The pipeline functions with high 
efficiency and precision to classify audio which makes it suitable across different real-world 
applications [45]. The method for preparing audio data for machine learning application requires a 
standard sequence of preprocessing followed by feature extraction and model training and 
subsequent evaluation steps. Each step receives thorough examination in the description that follows:
Figure 1: Framework of the proposed research methodology, illustrating the sequential stages from feature extraction 
and model training to evaluation and analysis.
3.1 PREPROCESSING 
ARTICLE IN PRESS
Data preprocessing is one most crucial step when preparing dataset for training machine learning as 
well as deep learning models. To improve the quality of the audio data and have consistent data across 
the dataset, several preprocessing techniques were applied in this study. Noise removal was 
performed first to eliminate any unwanted background noises which might have a negative impact on 
the model's capability to learn the real characteristics of the musical instruments [46]. The underlying 
processing rule consists in filtering the frequencies outside the expected range for each instrument 
and retaining only the right acoustic features. Let 𝑥(𝑡) represent the original audio signal and 𝑛(𝑡) 
denote the noise, where the clean signal 𝑠(𝑡) is derived by applying a noise removal filter 𝑓, such that 
ARTICLE IN PRESS
𝑠(𝑡)=𝑓𝑥(𝑡)― 𝑛(𝑡). Next, the audio clips were trimmed to a fixed length of 3 seconds to ensure 
uniformity. This step involves selecting the first 3 seconds of each audio clip 𝑥(𝑡) and discarding any 
excess duration, ensuring consistency across the dataset as 𝑥𝑡𝑟𝑖𝑚𝑚𝑒𝑑(𝑡) represent the trimmed audio 
as 𝑥𝑡𝑟𝑖𝑚𝑚𝑒𝑑(𝑡)=𝑥(𝑡)→𝑡 𝜖 [0,3]. After that, Padding was then applied to the audio clips, involves 
appending zeros to the end of clips that are shorter than the required length as 𝑥𝑝𝑎𝑑𝑑𝑒𝑑(𝑡)→
𝑥(𝑡) 𝑓𝑜𝑟 𝑡 𝜖 [0,𝑇] 
0      𝑓𝑜𝑟  𝑡 𝜖 (𝑇, 3] . Finally, data digitization was applied to convert the continuous audio signals into 
a digital form suitable for model processing. This involves the continuous audio signal at a fixed rate, 
resulting in discrete signal [47]. Let 𝑥𝑑𝑖𝑔𝑖𝑡𝑖𝑧𝑒𝑑(𝑛) represent the digitized signal, where 𝑛 is the discrete 
time index and the signal is obtained by sampling the continuous signal 𝑥(𝑡) at a rate 𝑓𝑠, such that 
�
�𝑑𝑖𝑔𝑖𝑡𝑖𝑧𝑒𝑑(𝑛)= 𝑥(𝑡𝑛) 𝑓𝑜𝑟 𝑡𝑛→𝑛
𝑓𝑠
, 𝑛=0,1,2,….. These steps ensure that the audio data is clean, 
uniform, and ready for further feature extraction and model training, enhancing the effectiveness of 
classification task.
3.2 FEATURE SELECTION
Audio signal processing tasks such as mood classification based on music recognition require a 
fundamental step of feature extraction, following are key extraction techniques applied to audio 
signals [48]. For an audio signal 𝑥(𝑡) sampled at discrete time intervals, the waveform represents the 
value of the signal at each same point 𝑥[𝑛]= 𝑥(𝑡𝑛), define in table I.
TABLE I: Description of the audio features with details on their extraction process and contribution to performance.
Feature Definition Equation
RMSE The square root of the mean of the squared 
amplitudes, representing signal energy.
1
|𝑤| 𝑛𝜖𝑤
𝑥[𝑛]2
MFCC Features that represent the power spectrum of a 
signal on a Mel scale for speech/audio analysis.
𝐾
𝑘=1
log𝑀(𝑡,𝑘) .
cos (
𝜋𝑚𝑘 ― 1
2
𝐾 )
Waveform The representation of the audio signal’s amplitude 
over time. 𝑥[𝑛]= 𝑥(𝑡𝑛)
Mel Spectrogram A spectrogram that maps frequencies to the Mel 
scale, representing perceived pitch.
𝑁
𝑛=1
|𝑋(𝑟,𝑛)|2.  𝑀𝑓(𝑛)
Chroma STFT
Energy distribution across 12 pitch classes 
(chromas) of the musical octave, derived from the 
short-time Fourier transform (STFT).
𝐹
𝑓=1
𝑆(𝑡,𝑓).𝑀𝑘(𝑡)
RMSE models the local energy content, waveform analysis maintains raw temporal structure, Mel 
spectrograms encode perceptual frequency scale information, and Chroma STFT carries harmonic and 
tonal information. All feature sets were extracted via well-established signal processing libraries and 
provided complementary information. MFCC and Mel perform effectively in capturing timbral, 
perceptual information, RMSE has a good high-level understanding of dynamic and temporal 
information and waveform, and Chroma STFT excels in representing harmonic. Their joint use 
enhanced the overall classification performance over individual features, supporting their utility in the 
proposed framework.
3.3 PROPOSED MODEL - HuBERT
ACCEPTED MANUSCRIPT ARTICLE IN PRESS
ARTICLE IN PRESS
The process of audio classification needs deep learning models to extract temporal features and 
spectral features and hierarchical features simultaneously.  HuBERT functions as an autonomous 
learning model dedicated to processing speech together with audio signals, as architecture shown in 
figure 2. [49]. HuBERT extracts hidden units from unlabeled sources to create representations that 
work with speech recognition and emotion detection and speaker verification [50]. It uses discrete 
hidden states to predict them between frames. In its two-stage operation HuBERT performs offline 
clustering before it moves onto masked prediction using transformer encoding.
Feature Extraction Layer
The raw audio waveform 𝑥𝑡 is first processed by convolution neural network (CNN) feature extractor 
that learns lower audio features, computed as in equation 1.
𝑍=∫𝐶𝑁𝑁(𝑥𝑡) (1)
Where 𝑍∈ 𝑅𝑇×𝐷 is the extracted feature sequence, 𝑇 represents the time steps and D is the feature 
dimension. Each convolutional layer applies a transformation, defining in equation 2.
𝑍𝑙= 𝜎 (𝑊𝑖∗ 𝑍𝑙―1+ 𝑏𝑙) (2)
The extracted features undergo layer normalization as follows in equation 3.
𝑍= 𝑍―𝜇
𝜎―∈
 (3)
Masked Prediction with Transformer Encoder
After extraction feature, a masking operation M(Z) is applied, replacing random audio segments with a 
special [𝑀𝐴𝑆𝐾] token, defined as in equation 4.
𝑧𝑚𝑎𝑠𝑘𝑒𝑑=𝑀(𝑍) (4)
Multi-Head Self-Attention (MHSA)
A transformer encoder then processes the masked input to capture long range dependencies. The 
transformer block content of multi head self-attention (MHSA) and position wise feed forward network 
(FFN) [51]. Self-attention in HuBERT is computed as in equation 5.
𝐴=𝑠𝑜𝑓𝑡𝑚𝑎𝑥 𝑄𝐾𝑇
𝑑𝑘
𝑉 (5)
Where  𝑄= 𝑊𝑄𝐹, 𝐾= 𝑊𝐾𝐹, 𝑉= 𝑊𝑉𝐹 are Query, key, and value matrices derived from feature 
representations 𝐹.
Feed Forward Network (FFN)
The multi head extension allows the model to focus on different contextual representations using 
equation 6.
𝑀𝐻𝑆𝐴(𝐻)=𝐶𝑜𝑛𝑎𝑐𝑡(𝐴1,𝐴2, …. , 𝐴ℎ) 𝑊𝑜 (6)
ACCEPTED MANUSCRIPT ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Each transformer layer includes a position wise FFN, computed as in equation 7.
𝐻
𝐹𝐹𝑁
= 𝜎(𝑊
1
𝐻+ 𝑏
1
The final contextual representation using equation 8.
𝐻=𝑙𝑎𝑦𝑒𝑟𝑁𝑜𝑟𝑚(𝐻
′
+𝑀𝐻𝑆𝐴(𝐻)) 
Pseudo – Label Generation via Iterative clustering
(7)
(8)
Instead of explicit supervision, HuBERT learns from pseudo labels generated through iterative 𝐾 means 
clustering. Given the hidden representation 𝐻, a clustering function 𝐶(𝐻) assigns each frame to a 
discrete label, defined using equation 9.
𝑦
𝑖
=𝑎𝑟𝑔𝑚𝑖𝑛 ||𝐻
𝑖―𝑐|| 
(9)
The model optimizes the masked prediction loss, which is a cross-entropy function, computed as in 
equation 10.
ℒ = ―∑
𝑖
𝑦
𝑖
Fully connected classification layer
log𝑝(𝑦
𝑖
|𝐻
𝑖
) 
(10)
The final stage involves a fully connected layer with a softmax classifier that maps HuBERT embedding 
to emotion classes, defined as in equation 11:
𝑦 =  𝑠𝑜𝑓𝑡𝑚𝑎𝑥(𝑊𝐻+𝑏) 
(11)
The final classification is based on categorical cross entropy loss, as in equation 12.
ℒ
𝑁
𝐶𝐸
= ∑
𝑖=1
𝑦
𝑖
log𝑦`
𝑖
(12)
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 2: Architecture Analysis of the proposed HuBERT-based model [52] 
3.4 DATA DESCRIPTION
For this study, the dataset that was used is the Music Mood Classification dataset (source) on Kaggle, 
which is comprised of five labels for expressing emotional content from music. In total, there are 2,500 
audio-based music files, of which 500 are contained in each mood category: Aggressive, Happy, 
Dramatic, Sad, and Romantic, as shown in figure 3. It has a balanced distribution of these mood classes 
so that both the training and the evaluation will be equally distributed. Key audio features included 
STFT, and MFCC, which are fundamental in analysis of timbral, rhythmic and spectral of music from 
each audio file in the dataset. The properties of these features allow models to similarly capture the 
tonal and emotional content of each track.
For evaluating different models their performances are evaluated with 80-20 holdout split where 80% 
of the dataset is used for training and 20% for testing. By doing this, the model is trained on a good 
amount of the dataset and there is a subset that is kept separate for validation, so a fair measure of 
the classification accuracy can be taken. The dataset allows machine learning, deep learning, and 
transformer-based models to be evaluated against for assessing music mood classification and is 
selected due to its diverse range of moods and structured distribution in the dataset.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 3: Distribution of dataset samples across mood categories, showing balanced representation with 500 instances 
per class.
3.5 COMPARISON BASED MODELS
This section investigates the various models of deep learning in music mood classification such as 
LSTM, ConvFormer and YAMNet. Local patterns of an audio signal are learned via spectrograms and 
evaluated models, which are extensively used for feature extraction from spectrograms. Since music 
time-series data has sequential dependency [53]. These models are based on features extraction and 
feature extraction capabilities, accuracy, as the best among these models is identified for music 
sentiment analysis. LSTM which was designed particularly to address vanishing gradient challenges in 
sequential information. Technology finds broad applications in speech recognition systems and both 
emotion analysis and audio event detection tasks. LSTM cells manage extended dependencies through 
their memory cells combined with gated operational elements [54]. Each LSTM cell includes three 
major components: Forgot Gate to Dispose Items and Input Gate to Record Data and Cell State Update 
to Store Information and Output Gate to Shape Final Outputs.
Moreover, YAMNet was developed as a pre-trained model using MobileNetV1 architecture to handle 
audio classification through Mel spectrograms [55]. YAMNet is a deep learning model based on 
MobileNet, a pre-trained embedding from a large-scale dataset is used in audio classification. First, it 
converts audio signals into log-Mel spectrogram representations, that are the input to a series of 
depth wise separable convolutional layers. The hierarchical features of spectrogram are extracted by 
these layers and include temporal and spectral patterns. Then the model applies global average 
pooling, which reduces the dimensionality while preserving most of the information, and a fully 
connected layer that maps the features described to already predefined audio classes. For multi 
classification, YAMNet utilizes SoftMax activation function, such that it outputs probability scores for 
each category. The pre-training of the model also ensures that it can generalize well across different 
sound domains making it a powerful tool for transfer learning in audio-based applications [56].
Additionally, ConvFormer represents a blended system which unites CNN with Transformer 
frameworks to extract local and global relationships from audio information. The short-range 
frequency features of data are processed by CNNs, and Transformers analyze temporal dependencies 
over longer durations through their operation [57]. ConvFormer applies a convolutional stem followed 
by multiple transformer encoder layers with three components: Convolutional feature extraction and 
multi-head self-attention and transformer encoder block. This model unites CNN and Transformer 
components to reach peak performance and processes both neighborhood spectrum characteristics 
along with extended time sequence connections [58].
3.6 PERFORMANCE EVALUATION METRICS 
The assessment of an audio classification model needs thorough evaluation to establish its usefulness 
in real-world applications. Multiple performance indicators serve for evaluating classification models 
specifically within speech recognition and music classification and environmental sound analysis fields 
[59]. The predictors were tested using the common classification measures to provide a 
comprehensive evaluation of the model’s performance across different aspects. Accuracy is defined as 
ARTICLE IN PRESS
𝑁
the extent of true predictions, using  
∑
𝑖=1
𝛿(𝑦
𝑖
, 
�
�
𝑁
𝑖
)
∗ 100→ 𝒚𝒊, 
�
�
𝑖
𝒊 = 1,    𝑖𝑓   𝑦
= 
�
�
𝑖
0,      𝑜𝑡ℎ𝑒𝑟𝑤𝑖𝑠𝑒 where, 𝑦
are the actual and predicted labels for instance  𝑖. 𝑁 is the total number of samples. Precision means 
out of all predictions that we have classified as positive; how many are positive, computed using 
�
�
 and 
�
�
𝑖
�
�
𝛿(
=1 ⋀  𝑦
=1)
𝑦
=1 ⋀  𝑦
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
∑
∑
𝑁
𝑖=1
𝛿 (
𝑦
→𝛿(
𝑖
=1)
∑
𝑁
𝑖=1
𝛿(
𝑦
𝑖=1
𝑦
𝑖
𝑖
𝑖
𝑖
=1 ⋀  𝑦
𝑖
=1) shows function returning 1 if both predicted and actual labels 
are positive. Recall defines the fraction of actual positives that has been correctly classified by the 
model, as  
�
�
=1)
∑
𝑁
𝑖=1
𝛿 (𝑦
𝑖
=1)
 -> 𝛿(𝑦
𝑖
=1) indicator returning 1 if the actual label is positive. F1- score 
is a balanced measurement between precision and recall because it is the harmonic meaning of the 
two 
2(𝑃𝑟𝑒𝑐𝑖𝑠𝑖𝑜𝑛∗𝑅𝑒𝑐𝑎𝑙𝑙)
𝑃𝑟𝑒𝑐𝑖𝑠𝑖𝑜𝑛+𝑅𝑒𝑐𝑎𝑙𝑙
. These evaluation metrics made it possible to have an analysis of how each model in 
the prediction of the types of sentences and identifying the models that can be used in future for 
improving English language teaching.
4. RESULTS AND DISCUSSION
Music mood classification is a challenging and developing task, still a technique needs to be developed 
to analyze such complicated acoustic patterns. As deep learning (DL) models can extract higher level 
features from a raw audio signal, traditional machine learning approaches have been gradually being 
replaced by DL models. To improve classification accuracy and build a solid means to mood 
classification, this research aims to integrate a feature driven scheme with modern deep learning 
methods.
4.1 DESCRIPTIVE ANALYSIS BASED ON FEATURES
The basics of mood recognition are constructed on top of the descriptive analysis of the various Audio 
features such as MFCC, STFT, Mel-Spectrogram, Waveform and RMSE. 
1) Waveform
The waveforms for each mood class—Aggressive, Dramatic, Happy, Romantic, and Sad—reveal 
significant differences in amplitude variation, energy distribution, and temporal characteristics, which 
provide valuable insights for mood classification, shown in figure 4. The Aggressive waveform exhibits 
high amplitude spikes with periodic sharp peaks, indicating strong percussive beats and high-energy 
music patterns. This suggests that aggressive music is characterized by strong rhythmic structures, 
high intensity, and abrupt sound changes, often found in rock, metal, or high-tempo electronic genres. 
The Dramatic waveform, on the other hand, shows fluctuating amplitude variations with a mix of high 
and low energy, reflecting the dynamic and emotional intensity of dramatic compositions. These 
characteristics are common in orchestral, cinematic, or suspenseful tracks, where variations in 
loudness contribute to dramatic expression.
The Happy Waveform displays moderate amplitude variations with consistent energy throughout, 
suggesting a steady rhythm and uplifting harmonies. Happy music often contains repetitive, high
energy beats with smooth transitions, commonly found in pop, dance, and upbeat genres. The 
Romantic waveform, in contrast, features relatively lower amplitude fluctuations with smoother 
transitions, indicating softer instrumentation and a more relaxed energy flow. Romantic music often 
relies on melodic progression, harmonization, and subtle dynamic shifts to evoke emotions of warmth 
and affection. Lastly, the Sad waveform presents irregular yet controlled amplitude fluctuations, with 
less pronounced spikes, indicating softer, more sustained sounds with gradual decays. Sad music 
typically has slower tempos, lower pitch ranges, and smoother transitions, contributing to a 
melancholic or reflective mood. The lower energy variation in sad waveforms aligns with the 
emotional depth associated with this mood. By analyzing waveform structures, deep learning models 
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
can better differentiate rhythmic intensity, energy flow, and harmonic structure, leading to more 
accurate mood classification.
Figure 4: Waveform analysis across all mood labels, illustrating the temporal amplitude variations of the audio signals.
2) Mel-Spectrogram
Figure 5 a) shows the Mel-spectrogram curves of time frequency variations with different mood 
categories, which display impressive differences in the amplitude dynamics and spectral energy 
distributions. Rock, metal, and some high intensity electronic music are known for exhibiting sharp 
peaks, strong percussive beats, rapid energy shifts, and so on; all of which are signatures of aggressive 
music; and which have sharp peaks, high amplitude fluctuations. On the other hand, romantic pieces 
in music are smoother with the amplitude of fluctuations being moderate, meaning that it has the 
softness of transitions and expressive harmonic progressions, which are usually traced in classical and 
jazz music. Ballads and emotionally expressive music tend to have sad music that keeps a low and 
stable amplitude variation, the low and slow variation indicates melancholic slow melodies with not 
many abrupt changes. Mel spectrogram visualizations as in figure 5  b)  also show the frequency 
distributions of moods, while Aggressive and Happy music present high energy broad mid-to high 
frequency bands with Aggressive having some of its distorted components within the low part of the 
mid-range as well as mid and high frequency bands; Sad and Romantic music again with some of its 
components dominating in low frequency one. The frequency spectrum analysis in figure 5 c) also 
shows that Aggressive and Happy music have wider harmonic content, which makes them energetic; 
while Dramatic and Romantic music possess balanced mid-to-low frequencies; and Sad music has 
lower frequency dominance, conforming to their sounds which are melancholic. Spectrogram based 
insights are important in AI based mood classification, as it gives the deep learning models a chance to 
use harmonic and spectral variations for accurate music sentiment-based classification and 
recommendation systems.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
a)
b)
c)
Figure 5. Mel spectrogram–based feature analysis: (a) curve representation across labels, (b) heatmap correlation 
analysis among labels, and (c) amplitude distribution analysis.
3) MFCC
Mel-Frequency Cepstral Coefficients (MFCCs) are a basic feature used in music mood classification like 
any other audio signal parametrization as a function of spectrum and timbral properties. Figure 6 (a, b, 
and c) shows the different interested perspectives of MFCC variations, spectrogram representation 
and frequency based heatmap, which facilitates the analysis of the mood classification pattern very 
well.
ARTICLE IN PRESS
Figures 6 a) show the MFCC curves that reveal the energies fit with distinct energy deviations and 
harmonic structures among mood classes. Like high energy, percussive driven structures frequently 
encountered within rock, metal, and intense electronic music, a sudden constant high energy muscle 
mass of the Aggressive MFCC curve filled with much sharper and flattening peaks. However, the 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Dramatic MFCC curve has more irregular smooth variations, like harmonic shifts and tension build over 
time found in the popular cinematic and orchestral pieces. Rhythmic variations of the Happy MFCC 
curve are consistently happy, corresponding to the harmonic structures of pop and dance music. 
a)
b)
ARTICLE IN PRESS
c)
Figure 6. MFCC-based feature analysis: (a) curve representation across labels, (b) heatmap correlation analysis among 
labels, and (c) waveform amplitude variation across labels.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
The expression of such shape curves reflected in the Romantic MFCC curve is characterized by soft and 
moderate fluctuations that are expressive and smooth transitions as they are found in classical and 
jazz compositions. Lastly, Sad MFCC curve displays low-frequency dominance with slight fluctuation, 
which corresponds to slow and melancholic melody, along with weak harmonic aggression typical of 
ballad and deep emotionally composed pieces. More patterns in Figure 6 a) are reinforced by 
frequency distribution across time in the MFCC spectrograms in Figure 6 b). Sad and Romantic 
spectrograms have smooth transitions over the frequency band with less high frequency dominance 
and more low frequency dominance. On the other hand, Aggressive and Happy spectrograms have 
high energy bursty and strong mid to high frequency components. Dramatic spectrogram presents 
progressive frequency modulations with dynamic parts necessary in emotional and theatrical 
compositions. In the last, the heatmap visualizations in Figure 6 c) allow us to look at spectral 
intensities differently, showing how frequency content is spread over different moods. These MFCC 
based insights have helped to provide deeper cues to learn in harmonic, spectral and temporal 
modalities while still efficiently supporting the usage of AI driven music emotion recognition system.
4) RMSE
Root Mean Square Error (RMSE), Delta RMSE, and analysis of Energy Novelty are used to analyze the 
energy levels dynamics and variations on the stream of music. Figure 7 a) and figure 7 b) especially 
depict the important role which these metrics play in music mood classification in terms of capturing 
the evolution of energy and rhythm, in the temporal domain.
The blue curve of the figures shows the overall energy intensity of the audio signal over time (with 
respect to RMSE). This is particularly evident in aggressive and happy moods for which high and 
variable energy content, and strong amplitude variations are revealed by higher RMSE values. Test 
music with romantic or sad genres has lower RMSE values owing to softer instrumentation, smoother 
harmonic transitions and low dynamic range. The green dashed curve shows the Delta RMSE, which is 
based on the rate of change in energy levels, to understand the speed of the signal's intensity 
fluctuation. Rhythmically complex and high energy content tracks are indicated by frequent and 
significant fluctuations in Delta RMSE, i.e., tracks in aggressive and dramatic moods. In contrast, its 
delta RMSE changes in slower rhythms indicate steadier, flowing compositions in romantic and sad 
moods where energy passes more slowly. The red curve, representing the energy novelty function, 
pinpoints of large energy variation (also matching musical onset, transition, or beat change). The 
novelty energy curve exhibits moments where a new musical element is introduced, which show very 
well if abrupt changes of dynamics occur, as the case in aggressive or dramatic moods. Optimal happy 
music rhythms contain moderate energy novelty peaks to indicate rhythmic consistency with 
occasional variations. In contrast, romantic and sad moods show less and smoother peaks in 
agreement with their gradual and emotional expression manner.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
a)
b)
Figure 7. RMSE-based feature analysis: (a) waveform representation across labels, and (b) density curve distribution 
of RMSE values.
Energy distribution visualization is the kind of visualization that shows how the energy levels cross the 
different frames of audio signal fluctuation, shown in figure 8. Rhythmic components, percussive 
elements and dynamic variations, and associated with aggressive, happy and dramatic moods, high 
energy peaks. Frequent spikes indicate strong beat driven patterns that are common to high tempo 
music of genres such as rock, electronic, and cinematic compositions among others. On the other 
hand, the sections with lower and more stable energy levels, which are commonly found in romantic 
and sad music, are softer, smoother and have the dynamics exercised more and the transitions are 
smoother. Understanding how to distinguish music moods based on energy is an energy-based 
analysis which helps prevent AI models to differentiate music moods using intensity fluctuations and 
temporal energy shift, increasing the accuracy of mood classification system.
ARTICLE IN PRESS
Figure 8: Frame-level energy distribution across the entire dataset, highlighting signal intensity variations over time
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
5) STFT
Figure 9 shows the Chromogram derived from Short Time Fourier Transform (STFT) showing where the 
pitch class energy (C, D, E, etc.) flows across time. Therefore, this can serve as an important feature in 
music mood classification because music harmonic structures, tonal progressions, and key variations 
are directly related to emotional perception of music.
The harmonic content in the chromogram 1 and 2 are dynamic and are represented by red regions of 
high energy intensities and blue regions of low energy levels. On the other hand, some of the highest 
chroma energy in the pitch classes indicate that certain notes or chordal structures are significant 
regarding mood differentiation. For instance, stable harmonic progressions and repetitive chord 
progressions are common in a happy and energetic mood; hence the constant chroma intensities. On 
the other hand, chroma energy in aggressive and dramatic moods changes dramatically and abruptly 
between key, modulations, and tension building harmonic patterns.
The chromatic intensity variations in time (x axis) track how the moods evolve harmonically. 
Transitions with smoother progressions between its notes, and subtle variation in pitch class energy, 
correlate with romantic and sad music that reflects (in melody) the emotional depth and 
expressiveness. On the other hand, aggressive and dramatic music has abrupt chromatic shifts, which 
signal strong rhythmic elements and frequent harmonic modulation. The integration of chromogram 
features with STFT spectral analysis allows music mood classification systems to increase the accuracy 
in discriminating moods based on harmonic complexity, tonal consistency, the chord progression.
Figure 9: Chroma STFT distribution of frames across the dataset, showing harmonic and tonal characteristics of the audio 
samples
4.2 PREDICTIVE ANALYSIS
For the predictive end, we study multiple deep learning architectures such as LSTM, ConvFormer, 
YAMNet and the proposed HuBERT model to check out whether they can perform classifying of music 
moods successfully.
ARTICLE IN PRESS
1) Results with Proposed Model – HuBERT
The classification report as displayed in table II, also gives detailed breakdown of the precision, recall 
and F1 score of each mood class. Overall, the accuracy of the HuBERT model is 95% which is a strong 
indication of the power of the predictive abilities of this model over all categories. Aggressive and 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Happy classes perform the best with precision, recall and F1 scores greater than 0.95 which ensures 
clear and less misclassified features. However, the precision of Romantic class (0.98) for its recall 
(0.93) reveals occasional confusion with the Sad class due to similar harmonic and melodic structures. 
The resulting balanced performance of the model is confirmed by the macro and weighted averages 
(0.95) of average F1 that indicate none of the classes is overpowered or unfairly misclassified.
TABLE II: Results Analysis Among All Performance Measures Across Classes Using Proposed Model
Classes
Accuracy
Precision
Recall
F1-Score
Aggressive
Dramatic
Happy
Romantic
Sad
95
95
95
95
95
96
94
95
98
92
96
96
96
93
94
96
95
95
96
93
Finally, the confusion matrix shown in figure 10 shows a bit more about classification accuracy and its 
misclassification trends. The Aggressive class has a correct classification rate of 99.01% corresponding 
to its separate spectral and rhythmic traits that are effectively captured by HuBERT model. The Happy 
class scores close to that of 97.37 correct classification, thus highlighting its rhythmic consistency and 
high energy spectral content which easily identify it. Nevertheless, misclassifying the instances as the 
Sad class occurs up to 10.28% of the time for the Romantic class. The cause of this confusion is a result 
of the frequency and harmonic qualities overlapping between soft expressive music genres as they 
may contain elements of romantic and melancholic emotions. Like for the Romantic and the Sad 
moods, the Dramatic class (94.57% accuracy) discriminates not only with the different mood, but also 
subtle emotional transitions in cinematic compositions.
Figure 10: Confusion matrix analysis of the HuBERT model, showing class-wise prediction accuracy and misclassification 
patterns
ARTICLE IN PRESS
The curve of the training & validation accuracy shown in figure 11 indicates that accuracy increases 
steadily with the number of epochs of 100, indicating effective learning and converged model. We find 
a good balance between the validation accuracy, making the training of the model stabilize above 
95%, and minimal overfitting and strong generalization on unseen data, as the validation is very close 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
to the training. Validation accuracy fluctuates occasionally, and we confirm that the model assumes an 
adaptive learning path and adapts its feature extraction to each different stage of training. This shows 
that despite having a real-world mood classification task to work on, the model manages to 
consistently and reliably perform with this high validation accuracy. The model’s stability and 
efficiency are also validated by the loss curve analysis further. The training loss also decreases rapidly 
in the early epochs in validating that the model learns discriminative audio features quickly. The 
training and validation loss values remain low and converge around 50 epochs and that means good 
model performance with minimal overfitting. Training data and the HuBERT model can learn mood 
specific features without relying too much on training and can generalize on the given data.
Figure 11: Training and validation curves of the HuBERT model, illustrating accuracy progression and loss reduction 
across epochs
This is a graphical representation of how well extracted audio features can cluster together the 
different mood classes using PCA (Principal Component Analysis) and tSNE (t_Distributed Stochastic 
Neighbor Embedding), shown in figure 12. Clustering is well separated in the PCA plot, indicating that 
HuBERT has captured meaningful features that allow HuBERT to differentiate between moods. 
Nevertheless, some regions overlap between Romantic and Sad moods thereby reaffirming the 
confusion mentioned in classification report and confusion matrix. Indeed, in the t-SNE visualization as 
well, distinct clusters are apparent, but the intersections are small and only few between closely 
related moods. This indicates the possibility of improving furthermore, i.e., multimodal learning (lyrics 
+ audio) for differentiating mood.
ARTICLE IN PRESS
Figure 12: Dimensionality reduction analysis using PCA and t-SNE, visualizing the separability of extracted features across 
emotion classes
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Confidence score visualizations in figure 13 help one discerns from where model is confident and to 
what degree. Confidence scores increase in the upwards direction on the different sample sets, which 
is indicative of the increase in model’s classification reliability as more data is integrated. Overall, 
Aggressive and Happy moods have very high confidence values, and these values make sense given 
their distinct spectral and rhythmic differences. Instead, as with harmonic and structural similarities, 
these two moods are equally confident, and occasionally class ambiguous. In the first phase, samples 
1-25) have moderate confidence levels as predictions are made at a lower threshold and gradually 
increase as training progresses. The extracted audio data enters the learning stage of the model, 
where we see that the model starts to learn the features that are useful in the audio data. The 
confidence curve has exponential growth, and the model becomes increasingly confident about its 
predictions as it is being trained. In samples 76-100 (the fourth and final set), confidence scores very 
near saturation are obtained, reflecting the maximum prediction certainty. This phase shows almost 
linear trend that confirms that, indeed, the model has achieved the optimal convergence and marked 
a large amount of classification ability in all tested samples. A highly stable model with consistent and 
accurate predictions is shown by the large presence of red color in the confidence trend.
Over epochs, these plots depict how the HuBERT model courses over the initial uncertainty state to a 
highly sure and robust classifier. Initially, the model has very little confidence in early epochs as it 
learns to address the complexity of the dataset, but with training, it improves its feature 
representation and therefore, the classification performance. The success of this outcome highlights 
that HuBERT can learn gradually hierarchical representations of audio data while maintaining high 
classification reliability. 
ARTICLE IN PRESS
Figure 13: Confidence score distribution of the HuBERT model across epochs, highlighting consistency in prediction 
reliability
Its trend line consists of periodic fluctuations which fit the validation accuracy pattern that historically 
a consistent pattern exhibits learned behavior throughout epochs, as shown in figure 14. This shows 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
that there is a general and upward trend, and it further reinforces the fact that the model is getting 
better by time. 
Figure 14: Validation performance trends across epochs, indicating stability and convergence of the model during 
training
The periodic dips indicate short periods of adjustments during the feature learning, to keep the model 
flexible for capturing musical emotions. In this case, the 3D confidence plot in figure 15 gives a 
complete view of the classification confidences linked with epochs and mood categories. Higher 
confidence levels of the Aggressive and Happy classes confirm their musical traits. In contrast, Sad and 
Romantic classes have slightly lower confidence scores as is shown by the earlier findings from the 
classification report and PCA visualization. The color intensity variations confirm the certainty of the 
model predictions by the warmer colors associated with high confidence and the cooler tones 
associated with uncertain classifications.
Figure 15: Prediction confidence analysis on randomly selected samples, demonstrating robustness across diverse inputs
ARTICLE IN PRESS
To visually verify the actual vs. predicted class comparison, most samples are correctly classified and 
are close to their respective class indices, in figure 16. The presence of a little misclassification makes 
the former sense as confusion of Romantic and Sad categories, and the trend continues to be strong. 
This further validates that HuBERT indeed learned mood specific patterns with little or no classification 
errors. The predictive power of the music mood classification on HuBERT is very strong with 95% 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
accuracy and high precision and recall over categories. The model separates them well, as the 
classification report and confusion matrix indicate, with Aggressive and Happy nearly perfect and 
moods of Romantic and Sad having some minor misclassification due to harmonic overlaps. The 
accuracy and the loss curves demonstrate stable learning and low overfitting, which verifies the 
generalization ability of the model. Furthermore, we visualize 3D distribution and confidence score 
trend for HuBERT, which can confirm its high certainty in predictions with high energy of mood classes. 
The PCA and t-SNE feature representations also verify their superior mood separation, and it captures 
the emotional and musical aspects of audio signals effectively, and it is a very reliable platform to use 
for analysis of musical sentiment and emotion-based AI applications.
For music mood classification, fine tuning the hyper parameters in the HuBERT model turned out to be 
crucial in evaluating its performance, as display in table III. The learning rate was chosen carefully, 
carefully, to balance convergence speed as well as model stability, that is, to make sure that the model 
converged into a solution without overshooting the optimum points. To make models more adaptable, 
we used a learning rate scheduler which changed the rate of learning during training. The batch size 
was chosen to be as large as possible to compute efficiently while maintaining generalization capability 
and stopped the model from overfitting by exposing the model to different training samples. HuBERT 
model for features extraction by means of fine-tuning it on the target dataset. Instead of treating it 
simply as a frozen feature extractor, fine-tuned certain layers in the transformer to enable the pre
trained representations to better fit the music mood recognition task. This enabled the model-to
model task-specific acoustic and contextual information while maintaining strong hierarchical 
embeddings learned during pretraining. The fine-tuned features were extracted and fed into 
downstream classifiers for the final prediction. By explicitly describing the fine-tuning process and 
corresponding hyperparameters, the study ensures clarity on how features were extracted and 
provides a replicable framework for future research.
ARTICLE IN PRESS
Figure 16: Actual versus predicted outcomes, including instances of overriding samples to analyze model 
misclassifications
Finally, the number of transformer layers was fine tuned to extract the hierarchies of audio features 
representations, each with the next layer performing a better job of refining spectral and temporal 
information. Furthermore, a tradeoff was made such that the number of attention heads maximized 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
the model’s ability to attend to different frequency components. In a bid to prevent overfitting, 
dropout regularization was derived by randomly deactivating part of the neurons in training, resulting 
in a more robust model. 
TABLE III: Hyperparameter Of Fine-Tuned Hubert Model
Parameter
Description
Values
Batch Size
Number of samples processed per iteration.
16
Number of Layers
Total number of transformer layers in the model.
12, 24
Optimizer
Algorithm used to adjust model weights.
AdamW
Dropout Rate
Probability of dropping a neuron during training.
0.1 – 0.3
Epochs
Number of complete training iterations.
100
Learning Rate
Step size for updating model weights.
0.0001
Beta 1
Momentum parameter for optimizer updates.
0.9
Beta 2
Momentum parameter for optimizer updates.
0.999
Weight Decay
Regularization to prevent overfitting.
0.01
Gradient Clipping
Prevents exploding gradients.
1.0 (Max Norm)
L2 Regularization
Applies L2 penalty to weights.
0.0001
Warmup Steps
Gradual increase of learning rate at start of training.
500
Scheduler
Strategy for adjusting learning rate during training.
Linear Decay
The embedding dimension was chosen to strike a good balance between feature richness and 
computational efficiency; it was appropriate to learn representations. Training loss and validation 
accuracy trends were tracked to determine how many epochs, beyond which the model started 
overtraining, the latter reaching maximum performance while not suffering from excessive 
overtraining. Third, a weight decay value to prevent instability of gradient updates was placed directly 
on Adam optimizer. The hyperparameter optimizations were crucial in providing a overall improved 
classification accuracy, precision, recall, and F1-score as compared to other models for audio 
classification tasks, making HuBERT a very effective pre-trained transformer-based audio classification 
model.
The five mood classes included in the bar chart include: Aggressive, Dramatic, Happy, Romantic, and 
Sad. This specifies the distribution of samples within the dataset, based on test data for prediction as 
shown in figure 17. Happy and Romantic are both relatively close to each other with 112 samples 
measured in the class counts and 105 samples in the class counts for Romantic and 103 samples for 
Aggressive. Meanwhile, only 89 instances to Dramatic and only 91 to Sad. This relatively balanced 
distribution guarantees that the model has enough training data per mood, so that a class imbalance 
phenomenon cannot occur and lead to biased training. But the slighter lower representation of 
Dramatic and Sad moods might have some minor classification bias as with higher structure of class 
then the model might perform slightly better. The histogram of this distribution tells us that the 
dataset is diverse and structured well, which means that the pressure should be high for HuBERT to 
learn some mood specific features and generalize well on different mood classes.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 17: Class-wise prediction analysis of the HuBERT model on test data, showing comparative performance across 
emotion categories 
2) YAMNet
From the classification report as shown in table IV, the YAMNet model has achieved very high accuracy 
of 94% in classifying music moods. As all the model's precision, recall and F1-score metrics are high and 
especially in the well-defined classes, Aggressive, Happy and Dramatic, its precision score is all above 
97%. This indicates that YAMNet’s ability to learn key acoustic features introduces spectral energy, 
rhythm and frequency pattern to separate out these moods with few false positives. Nevertheless, F1 
score (0.89 in Romantic and 0.88 in Sad) shows that minor misclassification happens with the 
relationships in the Romantic and Sad categories. If these two emotions share some overlapping 
features such as in slow tempo and similar harmonic progression, it hints at the potential problem in 
distinguishing them.
TABLE IV: Results Analysis Across All Performance Measures Using the YAMNet Model
Classes
Accuracy
Precision
Recall
F1-Score
Aggressive
Dramatic
Happy
Romantic
Sad
94
94
94
94
94
97
98
99
90
86
99
95
97
88
91
98
96
98
89
88
This observation is corroborated by the confusion matrix, in figure 18, which shows that Aggressive 
music gets almost perfect 99.01% correct classification rate indicating that YAMNet can properly identify 
high intensity and percussive music patterns. Like the above, YAMNet is highly sensitive to the rhythmic 
and happy nature of Happy music, with 97.37% accuracy. 
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 18: Confusion matrix analysis of the YAMNet model, illustrating class-wise accuracy and misclassification 
distribution
Nevertheless, Romantic music is wrongly classified in the Sad category by 10.28%, indicating that the 
model sometimes fails to discern small differences between the two moods. Similarly, the drama 
music also misclassifies critically with minor coefficients, with 2.17% instances being confused with 
Romantic and Sad moods, indicating a tough task of assigning harmonic definitions on sensitive 
emotions with similar harmonic structures. The training and validation accuracy curves in figure 19 
clearly show how the model can learn very well, and accuracy becomes greater than 90% from the 
beginning of the first 20 epochs then remains stable during the use of training. This shows that the 
model indeed is converged well and will deliver dependable results on unseen data. 
In addition, once smooth optimization is confirmed by the loss curve, the training and validation loss 
values tend to be quite similar, indicating little overfitting and good generalization in music samples, in 
figure 20. This final stabilized loss value also confirms that the model is minimizing classification errors 
and retaining strong performance on all mood categories. Looking at the class distribution bar chart, 
the dataset has a balanced representation of all five CRYSTAL mood categories and will not display a 
biased distribution for any of them. While these classes represent the two widest discrepancies in 
classification accuracy (Happy being the most represented class with 112 samples and Dramatic the 
least with 89 samples), this still implies that YAMNet does not suffer from class imbalance problems. 
This makes it have a good generalization ability that each mood category is equally well learned and 
classified.
ARTICLE IN PRESS
Figure 19: Training and validation accuracy and loss curves of the YAMNet model, showing learning progression across 
epochs
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 20: Confidence score distribution of the YAMNet model across epochs, highlighting prediction reliability
In addition, validation accuracy trends over epochs in figure 21, and there are some variations, but generally 
model’s overall accuracy is always high throughout training. YAMNet's stability indicates that it performs 
robustly on variations of musical compositions, making it appropriate for the real-world applications such as the 
AI musical recommendations systems and music playlist generation by emotion. The trend line analysis of 
accuracy provides further support to the above conclusion as it is consistent with upward trajectory (supporting 
strong predictive consistency of the model across different training epochs). In addition, further insights are also 
provided by the confidence score analysis for this model’s predictive certainty. It indicates that YAMNet learns 
mood specific features well at time.
ARTICLE IN PRESS
Figure 21: Validation accuracy and loss trends across epochs, reflecting stability and convergence during training
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Aggressive and Happy moods show consistently high confidence scores, and Romantic and Sad moods 
achieve slightly high ones, supporting earlier observed difficulty in classifying similar harmonic and 
melodic features. The 3D confidence distribution plot in figure 22 further confirms this trend where 
Happy and Aggressive classes clearly separate and Romantic and Sad classes are less confident, their 
occasional misclassification.
Figure 22: Prediction confidence analysis on randomly selected samples using the YAMNet model
The visualizations of the PCA and t-SNE show the feature space learnt by the model, in figure 23. High 
classification accuracy of YAMNet shows the well cluster behavior for the Aggressive and Happy 
classes, i.e., YAMNet has learned well defined acoustic properties of these moods. Nevertheless, there 
is some overlap between the Romantic and Sad clusters as previously observed in the confusion matrix 
analysis. This implies that although YAMNet achieves impressive performance in different moods, it 
may suffer when comparing near related emotions. Finally, the actual and predicted class classes are 
classified, and most predictions are in line with the actual class labels, in figure 24. These minimal 
discrepancies suggest that YAMNet is accurate for real world mood classification jobs and so can easily 
be integrated into practical music sentiment analysis applications.
ARTICLE IN PRESS
Figure 23: Feature separability visualization through PCA and t-SNE applied to YAMNet-extracted embeddings
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 24: Actual versus predicted outcomes for YAMNet, including overriding cases to examine misclassifications
Finally, YAMNet achieves high predictive performance while capturing mood dependent acoustic 
features and maintains stability across different music genres and compositions, the prediction on 
unseen data result shown in figure 25. While some nuances of moods exist like Romantic and Sad still 
need additional work, the overall classification accuracy, high confidence scores and well separated class 
indicate that YAMNet is a very good deep learning model for automated music mood classification.
Figure 25: Class-wise prediction analysis on test data using the YAMNet model, presenting comparative label-level 
performance
3) LSTM
ARTICLE IN PRESS
The classification report display in table V contains a comprehensive analysis of the performance of 
the model across all the different moods in which it was evaluated. The test results in an overall 
accuracy of 93% which seems to indicate strong predictive power of the model. The precision, recall 
and F1-score values show that the model’s precision in predicting Aggressive (0.97), Dramatic (0.94) 
and Happy (0.96) moods is almost perfect, and is good but not as precise in predicting Romantic (0.89) 
and Sad (0.89) moods. It suggests that the model sometimes labels instances of Romantic and Sad 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
moods incorrectly because the acoustic properties of these two classes are similar. The balanced 
macro and weighted average values exhibit that the model is doing well in generalizing for various 
mood categories without necessarily giving a better performance for any class over other.
TABLE V: Results Analysis Across All Performance Measures Using the LSTM Model.
Classes
Accuracy
Precision
Recall
F1-Score
Aggressive
Dramatic
Happy
Romantic
Sad
93
93
93
93
93
94
96
95
92
88
99
92
96
87
90
97
94
96
89
89
The confusion matrix as shown in figure 26, is a visual representation of actual versus predicted 
classifications and strengthen model verification. The best values of classificational accuracy, in terms 
of Aggressive and Happy moods both shows, with correctly predicting nearly all samples. Nevertheless, 
we find some misclassification of a small proportion of Romantic samples to Sad and slightly mixed 
Dramatic samples with Happy and Romantic moods. These errors infer that while the accuracy of the 
model is high, small emotional changes in musical compositions can occasionally cause prediction 
errors. Further refinements of classification accuracy could possibly be achieved by improving the 
feature extraction process or adding more contextual acoustic features. The figure 27, for the LSTM 
model in terms of both its accuracy curve and how it learns during each epoch on the training and 
validation datasets. The model starts off rapidly learning and surpasses 80% accuracy in less than 20 
epochs and then continues to improve until stabilization in 93% on more than 60 epochs. Training and 
validation accuracy is very close, which is a good sign for non-overfitting. A few minor fluctuations in 
validation accuracy hint at occasional changes of the performance for the validation data across 
various batches, as expected in deep learning models working with complex audio features.
ARTICLE IN PRESS
Figure 26: Confusion matrix analysis of the LSTM model, presenting class-wise accuracy and misclassification 
distribution.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 27: Training and validation accuracy and loss curves of the LSTM model, showing the progression of learning 
across epochs
The model’s convergence is depicted in the loss graph as it has a sharp decrease in loss at the first 
couple of epochs, and then gradually decreases with training. This implies that the training and 
validation loss curves remain closely aligned and, therefore, the model is not overfitting, and it can 
learn meaningful patterns from the dataset. Smooth loss trajectory also indicates the efficient 
stabilization of LSTM model such that the minimum performance without excessive weight updates 
nor instability. The model’s classification confidence across sorted samples is then plotted as a 
confidence graph in figure 28 which illustrates that confidence scores steadily increase. The trend in 
confidence, however, indicates that the model is very certain in its prediction for well covered 
emotions but, in agreement with the presence of slightly overlapping emotions for some categories, 
the confidence levels are smaller for mood classes. The curve of the confidence score shows the 
upward trajectory which is the model improving in separating between moods as it sees more 
samples. The 3D model accuracy plot in figure 29 gives a multi-dimensional perspective of how well 
models do in validating accuracy levels as well as confidence scores for different epochs and mood 
classes. It validates a rule of thumb that most mood categories result in accuracy rates greater than 
90% with some confidence variation for the Romantic and Sad moods. The confidence distribution of 
confidence levels indicates that the model works well overall, but the classification confidence of a few 
areas indicates there is space for those to improve by a little bit more.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 28: Confidence score trends of the LSTM model across epochs, reflecting prediction stability and reliability.
Figure 29: Prediction confidence analysis on randomly selected samples using the LSTM model.
Deeper insight into the model’s ability to classify at epochs is given by confidence with trend lines 
graph, shown in figure 30. The trend line generally follows an upward trend but there are some points 
where the confidence levels seem to vary because of some training epochs. The variations in the 
complexity of the dataset may be the cause of this, since some musical samples proved more difficult 
to classify than others. These minor fluctuations do not detract from the overall pattern and are 
produced on robust confident time levels. The LSTM model uses and differentiates features in a 
reduced dimensional space as viewed by the PCA and tSNE visualizations, shown in figure 31. The PCA 
plot shows that mood classes are, in general, separated well, though a small amount of overlap 
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
remains for Romantic and Sad moods. This is further highlighted by the t-SNE visualization which 
demonstrates clusters of both mood categories and, in the case of mood categories that have subtle 
acoustic similarities, how separating these is difficult. That last sentence suggests that the model, 
which is already very good at separating these closely related emotional tones, might be further 
improved by including extra spectral or temporal features.
Figure 30: Validation performance trends across epochs, demonstrating convergence behavior of the LSTM model.
Figure 31: PCA and t-SNE visualization of LSTM-extracted features, showing separability across emotion classes.
The class distribution that the model predicted against the actual distribution confirms that there is 
little or no bias in its maintaining class balance. The predicted counts are very close to how the original 
dataset was distributed and hence, the LSTM model is not biased in favor of one mood category over 
the other. It is important that this balance is maintained, otherwise the classification won’t be fair, and 
no mood will be represented in the predictions. The continuous distribution graph backs up the 
model’s consistency in classification by showing sample counts for each mood category, in figure 32. 
As the graph shows, the predicted class distribution also aligns with what the dataset naturally has, 
meaning the LSTM model has been able to capture the dataset naturally. In the classification numbers 
there is consistency, it means that the model’s learning process is stable and reliable, so that the 
predictions are evenly distributed in the mood categories. The LSTM model shows a very effective 
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
prediction of musical moods with classification accuracy of 93% with balanced precision, recall and the 
F1-score, shown in figure 33. 
Figure 32: Actual versus predicted outcomes of the LSTM model, including overriding samples to analyze 
misclassification cases.
Figure 33: Class-wise prediction analysis of the LSTM model on test data, illustrating comparative performance across 
labels.
ARTICLE IN PRESS
On the confusion matrix and visualization analyses it is confirmed that the model can correctly classify 
most moods, with few misclassifications in mood categories with close tonal similarity. We see that the 
model’s learning process is stable and the model’s accuracy and loss graphs, as well as confidence and 
3D accuracy plots provide evidence of the model’s reliability. It is shown from PCA and t-SNE 
visualizations that this feature separability is meaningful, with room for improvement to distinguish 
more closely related moods. These results empower one to use the LSTM model as a highly effective 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
automatic mood recognition tool in music, another way in which the model could be improved is 
through refinement of the feature extraction and more training data
4) ConvFormer
Overall, the results with the pre-trained ConvFormer model on classifying emotional states show that 
ConvFormer is capable in such tasks at a very high accuracy and robustness. The overall accuracy of 
the report is 91%, meaning the model has a strong generalization capability, displayed in table VI. The 
F1-score, precision, recall values for each emotion class are this balanced, meaning that the model 
avoids bias in favor of any class. Also, note that the emotion class, aggressive, had a 100% recall — i.e., 
the model was not wrong in saying that any sample labeled as aggressive was indeed aggressive, with 
no false negatives. However, romantic emotion class had the lowest recall at 79.44 percent, meaning 
that some romantic samples were misclassified perhaps due to similarity in other emotions like sad or 
drama. Both the happy and the dramatic classes did well with recall values of more than 92%, and 
their peculiarities in the dataset should be noted.
TABLE VI: Comparative Results of ConvFormer Across All Evaluated Performance Measures.
Classes
Accuracy
Precision
Recall
F1-Score
Aggressive
Dramatic
Happy
Romantic
Sad
91
91
91
91
91
93
92
99
89
80
100
92
94
79
90
96
92
96
84
85
The confusion matrix, as shown in figure 34, besides showing this pattern, will help you understand 
how the model’s predictions align with the actual ground truth labels. Secondly, most of the classes 
are correctly predicted with high probability, but there are misclassifications between romantic and 
sad emotions. That is, about 14% of romantic samples were misclassified as sad, suggesting that these 
two emotions might differ only in overlap in acoustic, or feature based, representations which would 
make them difficult to discriminate.  Additionally, dramatic samples were classified as being aggressive 
in 3.26% of cases possibly because of the loudness of speech patterns in the 2 samples categories. 
With these findings, it can be said that the model may need to further be tuned fine or to include more 
distinctive feature to reduce the overlap the closely related emotional states.
The accuracy and loss curve in figure 35, shows the ConvFormer model learning progression 
throughout 100 epochs training which the training and validation accuracy is always increasing steadily 
and converge to be close to 90 percent which indicates that the Convformer model is properly trained. 
There are no indications of overfitting as the validation accuracy is close to training accuracy all 
through and this is a good indication of generalizability. This is further reinforced by the loss curve, 
which peaks sharply, dropping both the training and validation loss early and then peaking with stable 
and efficient learning. It is the convergence of two loss curves to a low value which indicates that the 
model indeed converges with a solution minimizing classification errors.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 34: Confusion matrix of the ConvFormer model, illustrating classification strengths and areas of misclassification 
across mood classes.
Figure 35: Accuracy and loss progression curves of the ConvFormer model, tracking model learning dynamics during 
training and validation.
Confidence score visualization in figure 36 represents how confidence calibrates in various subsets of 
test samples. As more samples are sorted, scores of the model gradually increase, an indication that 
the model is more confident in its classification for the later samples (this can probably tell us that the 
model is very confident in assigning well identifiable emotional states, but slightly less confident in the 
more ambiguous samples).  This observation also fits 3D accuracy visualization in figure 37, where the 
confidence scores of the different epochs and emotion categories are plotted. Most of the predictions 
lie in the high confidence range (above 90%) which validates the model’s ability to make predictions at 
different training stages. However, some emotion classes, such as romantic and sad, exhibit slightly 
lower confidence values, consistent with their overlapping nature in the feature space.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 36: Confidence analysis across epochs for ConvFormer, showing fluctuations and stabilization of prediction 
certainty over time.
Figure 37: Confidence prediction evaluation on randomly selected test samples, highlighting ConvFormer’s reliability 
across diverse inputs.
ARTICLE IN PRESS
Validation accuracy fluctuations in the trend analysis graph in figure 38 increased overall, and it also 
exhibited some minor drops. It means that although the model is sometimes confronted with a 
difficult batch in training, it has a solid overall learning tendency. The PCA and tSNE visualizations are 
an in-depth view of the ways that the model arranges data in lower dimensional space. It is confirmed 
that the confusion matrix trends are showing is also presented in the PCA plot since here there are 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
some overlapping clusters between romantic and sad emotions, although sadly the area below the 
diagonal is much larger than on the one above, shown in figure 39. However, t-SNE visualizes this data 
in a more spread-out manner, identifying that many samples make well defined clusters whereas 
some samples remain near decision boundaries, and therefore these could lead to classification error 
points.
Figure 38: Validation accuracy and loss behavior across epochs, indicating the model’s convergence and generalization 
trends.
Figure 39: PCA and t-SNE visualizations of ConvFormer-extracted features, demonstrating clustering patterns and inter
class separability.
Another layer of validation is the predicted vs. actual classification graph in figure 40, wherein, it 
basically confirms that the model’s predictions are quite accurate, or they mostly aligned to the 
ground truth labels. As shown by the confusion matrix, these slight deviations agree with the minor 
scattered misclassified points in the romantic and dramatic categories. Finally, the distribution graph 
shows that the predictions are balanced between the 5 emotion categories and there is no clear 
preference in any of them. Such a distribution balance is needed for practical applications for the real 
world, otherwise the model will excessively favor one emotion class over another.
ARTICLE IN PRESS
In short, the predictive power of the pre-trained ConvFormer model is strong, with high classification 
accuracy and stable training behavior and clear understanding of confidence in predictions. Figure 41 
shows the model accuracy on test data that usually correctly classifies almost all emotional states with 
a high sensitivity & specificity but has a slight misclassification of 2 closely related emotions 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
alphabetically: romantic and sad, because of feature redundancy. Our findings suggest that 
ConvFormer is a very good model for speech-based emotion recognition, but requires further 
refinement, for example, feature engineering or extra fine tuning on ambiguous categories to better 
improve its classification accuracy.
Figure 40: Actual versus predicted outcomes for ConvFormer, including overriding instances used to investigate 
misclassification scenarios.
Figure 41: Per-class prediction performance of ConvFormer on test data, providing a detailed breakdown of accuracy 
across mood categories.
4.3 Discussion
ARTICLE IN PRESS
Finally, the performance on the proposed HuBERT is compared to the baseline models, including 
ConvFormer, LSTM, and YAMNet and results show that HuBERT outperforms all of these in terms of 
few-shot classification metrics. It is clear from the table that HuBERT has the highest accuracy (95), 
precision (95), recall (95) and F1score (95) than all other models, displayed in table VII. However, the 
ConvFormer, as a hybrid deep model, is slowed down to 91% accuracy, probably because 
convolutional operations used therein don’t excel at capturing long term dependencies. Since LSTM is 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
a sequential deep model, it achieves higher accuracy 93% as it is better at learning temporal 
relationships. Although its performance is inferior to that of the transformer-based model, its 
limitation in handling large scale audio sequence may justify this result. 
TABLE VII: Comparative Analysis of All Applied Models Showing Performance Based on Techniques
Technique
Model
Accuracy
Precision
Recall
F1-Score
Hybrid Deep 
Model
Traditional 
Deep Model
Pre-Trained 
Deep
Transformer
based
ConvFormer
LSTM
YAMNet
Proposed- 
HuBERT
91
93
94
95
91
93
94
95
91
93
94
95
91
93
94
95
Both HuBERT and YAMNet are pre-trained deep models, HuBERT achieves 94% accuracy, but with 
slightly worse, though still good, accuracy than the fine-tuned YAMNet. A possible reason for the 
difference in fine tuning strategies. On the other hand, the proposed HuBERT model, based on 
transformer architecture, proved to be a highly effective model in audio classification with prediction 
abilities and generalization capabilities highest among all baselines.
To demonstrate further the robustness of our proposed framework, statistical significance tests were 
carried out with both emotion classes and competing models. Multiple t-test, ANOVA, Chi-square and 
z-test were tested, and the results were indicative of a significant correlation at p = 0.05. The summary 
of the statistical test within the five mood categories is shown in Figure 42. P-values from the t-tests, 
ANOVA, the Chi-squared test, and the z-tests exhibit the natural trend of variation between classes but 
are always above 0.05 significance level. This means that online HuBERT is robust and unbiased on the 
different emotion categories, and they do not show statistically significant deviation for a single class. 
Uniformity of the p-values over all the statistical measures suggests that the resilience of HuBERT 
model while dealing with different mood recognition tasks.
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Figure 42: Statistical Significance Tests Across Classes based on HuBERT Model
The statistical comparison between models ConvFormer, LSTM, YAMNet and the proposed HuBERT 
can be found in Figure 43. Although HuBERT performed the best (95% accuracy), p-values for all tests 
show that the differences between the models are not statistically significant at the 0.05 level. This 
further supports the finding that HuBERT not only achieves superior (raw) performance, but also 
substantial and consistent gains that are not due to statistical bias. Altogether, these results 
demonstrate the competitive advantage of HuBERT, and robustness in both class- and model-level 
comparisons.
Figure 43: Statistical Significance Tests Across Models
In addition to technical contributions, it is essential to address ethical and practical considerations for 
real-world deployment of music mood recognition systems. A major shortcoming is genre bias whish 
highlight the most AI models in music are based on data that are biased towards Western and 
well-known genres, which might systematically marginalize non-Western and less common musical 
traditions, thus, seriously jeopardizing the fairness and generalization of the model [60]. Moreover, 
considering the importance of cultural context for mood interpretation, cultural bias is also a key issue 
as emotion perception to music differs between cultures as Western listeners, for example, are more 
accurate to show anger and joy from Western classical music than from Chinese traditional music [61]. 
One way to address these difficulties may be to include cross-cultural baselines such as Global Mood 
that cover a wide range of linguistic and cultural contexts to collect culture-specific distributions of 
mood descriptions [62].
ARTICLE IN PRESS
Far beyond cultural equity, ethical deployment also includes data ownership and creative rights. AI 
systems trained with copyrighted music without adequate permissions risks of consent and fair use, 
while unacknowledged imitation of an artistic style risks damaging artist integrity [63]. Transparent 
Dataset Curation, Fair Licensing Practices, Inclusiveness for Marginalized Genres are all important 
mechanisms that contribute to promoting responsible AI. Beyond that, transparency can be increased 
by the application of explainable AI (XAI) methods to mood recognition models, and this facilitates the 
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
understanding and acceptance of the decisions taken [64]. In general, such potential limitations are 
required to make sure AI-powered music mood recognition is a fair, culturally aware and well-ethical 
process in real-world apps.
4.4 COMPARISON WITH EXISTING STUDIES
Performance and novelty of the proposed HuBERT model compared to existing studies in music mood 
classification are demonstrated. Earlier models, including CNN+LSTM (82.2%), BERT (77.8%), and CNN
BERT (85.5%), have already shown remarkably high classification accuracy, and through 95.0% 
accuracy, HuBERT proves that it can learn deeper representations from music features from HuBERT, 
displayed in table VIII. HuBERT is different from XGBoost and SVM (89.3%) that highly depend on 
sentiment features of lyrics, and it utilizes MFCC, STFT, Mel-Spectrogram, Waveform, and RMSE to 
learn temporal and spectral characteristics at the same time, which result in richer features. Although 
promising, this work has been done on traditional transformer-based models, like Masked BERT (89%), 
and often they do not consider more features (MFCC, Chroma). However, by fusing the various audio 
descriptors with deep transformer-based processing, HuBERT achieves more robust, and robust more 
generally, mood classification. With a rich, diverse, and comprehensive feature set, it perfectly fits 
these small difficulties in capturing music mode, achieved much better results than any other previous 
approach and set new benchmarks in this field.
TABLE VIII: Comparison Analysis of Proposed Model with State-of-the-art
Ref
Year
Model
Classes
Feature
Results 
[22]
[20]
[37]
[29]
[35]
Proposed
2020
2021
2022
2023
2024
CNN+LSTM
XGBoost, SVM
BERT
CNN-BERT
Masked Transformer
HuBERT
5
4
5
5
4
5
Spectrograms
Lyrics Sentiment Features
MFCC, ZCR, STFT
MFCC, Chroma, Spectral 
Contrast
MFCC, Chroma
MFCC, STFT, Mel-Spec, 
Waveform, RMSE
82.2
89.3
77.8
85.5
89
95
5. CONCLUSION 
This study investigated music mood classification by comparing machine learning, deep learning, pre
trained, and transformer-based models to accurately detect emotional content in music. Given the 
significant role of AI and sentiment analysis in emotion recognition, accurate mood classification is 
essential for applications such as music recommendation systems, emotional AI, and therapeutic 
interventions. We evaluated CNN, LSTM, YAMNet, and HuBERT on a public dataset with five mood 
labels. The findings demonstrated that HuBERT achieved the highest accuracy of 95%, outperforming 
conventional deep learning models in capturing long-range dependencies and patterns. Future 
research can address the limitations of the current study by expanding the dataset to include a wider 
range of musical genres and multilingual lyrics, which will enhance the model’s generalizability. 
ARTICLE IN PRESS
Another direction is the integration of multimodal data, such as combining audio features with lyrical 
content, to capture a broader spectrum of mood-related signals. Ensemble modeling with CNNs, 
LSTMs, and transformers can also be explored to overcome the constraints of relying on a single 
architecture. Furthermore, incorporating explainable AI (XAI) methods more deeply into the 
framework can directly address the limitation of model interpretability observed in transformer-based 
systems, making the results more transparent and actionable.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Data Availability
The dataset freely available at: https://www.kaggle.com/datasets/auliayasmin/music-mood
classification
REFERENCES
[1] S. Iqbal, H. Ullah Khan, U. Ishfaq, M. Alghobiri, and S. Iqbal, “Finding 
influential users in social networks based on novel features &amp; link
based analysis,” Journal of Intelligent & Fuzzy Systems, vol. 40, pp. 1623
1637, 2021, doi: 10.3233/JIFS-201036.
[2] C. Hema and F. P. Garcia Marquez, “Emotional speech Recognition using 
CNN and Deep learning techniques,” Applied Acoustics, vol. 211, p. 109492, 
2023, doi: https://doi.org/10.1016/j.apacoust.2023.109492.
[3] C. Bao and Q. Sun, “Generating Music With Emotions,” IEEE Trans 
Multimedia, vol. 25, pp. 3602–3614, 2023, doi: 10.1109/TMM.2022.3163543.
[4] A. Mahmood, H. U. Khan, and M. Ramzan, “On modelling for bias-aware 
sentiment analysis and its impact in twitter,” Journal of Web Engineering, 
vol. 19, no. 1, pp. 1–28, Mar. 2020, doi: 10.13052/jwe1540-9589.1911.
[5] M. Ahmed, H. U. Khan, and E. U. Munir, “Conversational AI: An Explication 
of Few-Shot Learning Problem in Transformers-Based Chatbot Systems,” 
IEEE Trans Comput Soc Syst, vol. 11, no. 2, pp. 1888–1906, 2024, doi: 
10.1109/TCSS.2023.3281492.
[6] F. Han, P. Yang, H. Du, and X.-Y. Li, “Accuth+: Accelerometer-Based Anti
Spoofing Voice Authentication on Wrist-Worn Wearables,” IEEE Trans Mob 
Comput, vol. 23, no. 5, pp. 5571–5588, 2024, doi: 
10.1109/TMC.2023.3314837.
[7] J. Yin, Z. Qiao, L. Han, and X. Zhang, “EEG-based emotion recognition with 
autoencoder feature fusion and MSC-TimesNet model,” Comput Methods 
Biomech Biomed Engin, vol. 0, no. 0, pp. 1–18, 2025, doi: 
10.1080/10255842.2025.2477801.
[8] H. Guo et al., “EMO-Music: Emotion Recognition Based Music Therapy with 
Deep Learning on Physiological Signals,” in 2024 IEEE First International 
Conference on Artificial Intelligence for Medicine, Health and Care 
(AIMHC), 2024, pp. 10–13. doi: 10.1109/AIMHC59811.2024.00008.
[9] A. Naz, H. U. Khan, S. Alesawi, O. I. Abouola, A. Daud, and M. Ramzan, “AI 
Knows You: Deep Learning Model for Prediction of Extroversion Personality 
Trait,” IEEE Access, p. 1, 2024, doi: 10.1109/ACCESS.2024.3486578.
[10] K. Machová, M. Szabóova, J. Paralič, and J. Mičko, “Detection of emotion by 
text analysis using machine learning,” Front Psychol, vol. 14, 2023, doi: 
10.3389/fpsyg.2023.1190326.
[11] U. Ishfaq, H. U. Khan, and S. Iqbal, “Identifying the influential nodes in 
complex social networks using centrality-based approach,” Journal of King 
Saud University - Computer and Information Sciences, vol. 34, no. 10, pp. 
9376–9392, Nov. 2022, doi: 10.1016/j.jksuci.2022.09.016.
ARTICLE IN PRESS
[12] D. Serdyuk, O. Braga, and O. Siohan, “Transformer-Based Video Front-Ends 
for Audio-Visual Speech Recognition for Single and Multi-Person Video,” 
Jan. 2022, [Online]. Available: http://arxiv.org/abs/2201.10439
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
[13] S. R. Livingstone and F. A. Russo, “The Ryerson Audio-Visual Database of 
Emotional Speech and Song (RAVDESS): A dynamic, multimodal set of facial 
and vocal expressions in North American English,” 2018, doi: 
10.5281/zenodo.1188976.
[14] J. Engel et al., “Neural Audio Synthesis of Musical Notes with WaveNet 
Autoencoders,” Apr. 2017, [Online]. Available: 
http://arxiv.org/abs/1704.01279
[15] A. Raimon, S. Masti, S. K. Sateesh, S. Vengatagiri, and B. Das, “Meta
Learning in Audio and Speech Processing: An End to End Comprehensive 
Review,” Aug. 2024, [Online]. Available: http://arxiv.org/abs/2408.10330
[16] S. Iqbal, F. Khan, H. U. Khan, T. Iqbal, and J. H. Shah, “Sentiment Analysis 
of Social Media Content in Pashto Language using Deep Learning 
Algorithms,” Journal of Internet Technology, vol. 23, no. 7, pp. 1669–1677, 
2022, doi: 10.53106/160792642022122307021.
[17] C. Hernandez-Olivan and J. R. Beltran, “Music Composition with Deep 
Learning: A Review,” Aug. 2021, [Online]. Available: 
http://arxiv.org/abs/2108.12290
[18] W. Ahmad, H. U. Khan, T. Iqbal, and S. Iqbal, “Attention-Based Multi
Channel Gated Recurrent Neural Networks: A Novel Feature-Centric 
Approach for Aspect-Based Sentiment Classification,” IEEE Access, vol. 11, 
pp. 54408–54427, 2023, doi: 10.1109/ACCESS.2023.3281889.
[19] K. Pyrovolakis, P. Tzouveli, and G. Stamou, “Multi-Modal Song Mood 
Detection with Deep Learning,” Sensors, vol. 22, no. 3, 2022, doi: 
10.3390/s22031065.
[20] K. Siriket, V. Sa-ing, and S. Khonthapagdee, “Mood classification from Song 
Lyric using Machine Learning,” in 2021 9th International Electrical 
Engineering Congress (iEECON), 2021, pp. 476–478. doi: 
10.1109/iEECON51072.2021.9440333.
[21] L. Xu, Z. Sun, X. Wen, Z. Huang, C. Chao, and L. Xu, “Using machine 
learning analysis to interpret the relationship between music emotion and 
lyric features,” PeerJ Comput Sci, vol. 7, p. e785, 2021, doi: 10.7717/peerj
cs.785.
[22] K. Pyrovolakis, P. Tzouveli, and G. Stamou, “Mood detection analyzing lyrics 
and audio signal based on deep learning architectures,” in 2020 25th 
International Conference on Pattern Recognition (ICPR), 2021, pp. 9363
9370. doi: 10.1109/ICPR48806.2021.9412361.
[23] R. Akella and T.-S. Moh, “Mood Classification with Lyrics and ConvNets,” in 
2019 18th IEEE International Conference On Machine Learning And 
Applications (ICMLA), 2019, pp. 511–514. doi: 10.1109/ICMLA.2019.00095.
[24] R. Delbouys, R. Hennequin, F. Piccoli, J. Royo-Letelier, and M. Moussallam, 
ARTICLE IN PRESS
“Music Mood Detection Based On Audio And Lyrics With Deep Neural Net,” 
Sep. 2018, [Online]. Available: http://arxiv.org/abs/1809.07276
[25] L. and S. F. Xue Hao and Xue, “Multimodal Music Mood Classification by 
Fusion of Audio and Lyrics,” in MultiMedia Modeling, S. and T. D. and X. C. 
and Y. J. and H. M. A. He Xiangjian and Luo, Ed., Cham: Springer 
International Publishing, 2015, pp. 26–37.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
[26] V. Kumar and S. Minz, “Mood classifiaction of lyrics using SentiWordNet,” 
in 2013 International Conference on Computer Communication and 
Informatics, 2013, pp. 1–5. doi: 10.1109/ICCCI.2013.6466307.
[27] T.-T. Dang and K. Shirai, “Machine Learning Approaches for Mood 
Classification of Songs toward Music Search Engine,” in 2009 International 
Conference on Knowledge and Systems Engineering, 2009, pp. 144–149. 
doi: 10.1109/KSE.2009.10.
[28] M. Zeng, X. Tan, R. Wang, Z. Ju, T. Qin, and T.-Y. Liu, “MusicBERT: 
Symbolic Music Understanding with Large-Scale Pre-Training,” Jun. 2021, 
[Online]. Available: http://arxiv.org/abs/2106.05630
[29] Suresh and R. Rajan, “Transformer-based automatic music mood 
classification using multi-modal framework,” Journal of Computer Science & 
Technology, vol. vol. 23, no. 1, Apr. 2023, doi: 
http://sedici.unlp.edu.ar/handle/10915/152120.
[30] S. Akinpelu, S. Viriri, and A. Adegun, “An enhanced speech emotion 
recognition using vision transformer,” Sci Rep, vol. 14, no. 1, p. 13126, 
2024, doi: 10.1038/s41598-024-63776-4.
[31] Khan, H.U., Naz, A., Alarfaj, F.K. et al. A transformer-based architecture for 
collaborative filtering modeling in personalized recommender systems. Sci 
Rep 15, 24503 (2025). https://doi.org/10.1038/s41598-025-08931-1 
[32] B. Babaali and M. Shayaninasab, “Multi-Modal Emotion Recognition by Text, 
Speech and Video Using Pretrained Transformers.”
[33] S. Tabinda Kokab, S. Asghar, and S. Naz, “Transformer-based deep learning 
models for the sentiment analysis of social media data,” Array, vol. 14, p. 
100157, 2022, doi: https://doi.org/10.1016/j.array.2022.100157.
[34] Md. M. Hassan, Md. A. R. Khan, K. K. Islam, Md. M. Hassan, and M. M. F. 
Rabbi, “Depression Detection system with Statistical Analysis and Data 
Mining Approaches,” in 2021 International Conference on Science & 
Contemporary Technologies (ICSCT), 2021, pp. 1–6. doi: 
10.1109/ICSCT53883.2021.9642550.
[35] S. Min, J. Yang, S. Lim, J. Lee, S. Lee, and S. Lim, “Emotion Recognition 
Using Transformers with Masked Learning,” Mar. 2024, [Online]. Available: 
http://arxiv.org/abs/2403.13731
[36] S. Hazmoune and F. Bougamouza, “Using transformers for multimodal 
emotion recognition: Taxonomies and state of the art review,” Eng Appl Artif 
Intell, vol. 133, p. 108339, 2024, doi: 
https://doi.org/10.1016/j.engappai.2024.108339.
[37] S. Hizlisoy, S. Yildirim, and Z. Tufekci, “Music emotion recognition using 
convolutional long short term memory deep neural networks,” Engineering 
Science and Technology, an International Journal, vol. 24, no. 3, pp. 760
767, 2021, doi: https://doi.org/10.1016/j.jestch.2020.10.009.
[38] Y. R. Pandeya and J. Lee, “Deep learning-based late fusion of multimodal 
information for emotion classification of music video,” Multimed Tools Appl, 
vol. 80, no. 2, pp. 2887–2905, Jan. 2021, doi: 10.1007/s11042-020-08836-3.
[39] F. Nie et al., “An Adaptive Solid-State Synapse with Bi-Directional 
Relaxation for Multimodal Recognition and Spatio-Temporal Learning,” 
ARTICLE IN PRESS
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
Advanced Materials, vol. 37, no. 17, p. 2412006, 2025, doi: 
https://doi.org/10.1002/adma.202412006.
[40] Z. Yin, F. Reuben, S. Stepney, and T. Collins, “Deep learning’s shallow 
gains: a comparative evaluation of algorithms for automatic music 
generation,” Mach Learn, vol. 112, no. 5, pp. 1785–1822, May 2023, doi: 
10.1007/s10994-023-06309-w.
[41] M. Bilal Er and I. B. Aydilek, “Music emotion recognition by using chroma 
spectrogram and deep visual features,” International Journal of 
Computational Intelligence Systems, vol. 12, no. 2, pp. 1622–1634, Dec. 
2019, doi: 10.2991/IJCIS.D.191216.001/METRICS.
[42] M. B. Er, H. Çiğ, and İ. B. Aydilek, “A new approach to recognition of human 
emotions using brain signals and music stimuli,” Applied Acoustics, vol. 175, 
p. 107840, Apr. 2021, doi: 10.1016/J.APACOUST.2020.107840.
[43] M. B. Er, “A Novel Approach for Classification of Speech Emotions Based on 
Deep and Acoustic Features,” IEEE Access, vol. 8, pp. 221640–221653, 
2020, doi: 10.1109/ACCESS.2020.3043201.
[44] P. Tang, H. Zhao, W. Meng, and Y. Wang, “One-shot motion talking head 
generation with audio-driven model,” Expert Syst Appl, vol. 297, p. 129344, 
Feb. 2026, doi: 10.1016/J.ESWA.2025.129344.
[45] U. Ishfaq, H. U. Khan, and D. Shabbir, “Exploring the role of sentiment 
analysis with network and temporal features for finding influential users in 
social media platforms,” Soc Netw Anal Min, vol. 14, no. 1, p. 241, 2025, 
doi: 10.1007/s13278-024-01396-6.
[46] W. Ahmad, H. U. Khan, T. Iqbal, M. A. Khan, U. Tariq, and J. H. Cha, “Hybrid 
Multichannel-Based Deep Models Using Deep Features for Feature-Oriented 
Sentiment Analysis,” Sustainability (Switzerland), vol. 15, no. 9, May 2023, 
doi: 10.3390/su15097213.
[47] S. Deng et al., “Learning to compose diversified prompts for image emotion 
classification,” Comput Vis Media (Beijing), vol. 10, no. 6, pp. 1169–1183, 
2024, doi: 10.1007/s41095-023-0389-6.
[48] M. K. Gourisaria, R. Agrawal, M. Sahni, and P. K. Singh, “Comparative 
analysis of audio classification with MFCC and STFT features using machine 
learning techniques,” Discover Internet of Things, vol. 4, no. 1, p. 1, 2024, 
doi: 10.1007/s43926-023-00049-y.
[49] S. J. Joysingh, P. Vijayalakshmi, and T. Nagarajan, “Significance of chirp 
MFCC as a feature in speech and audio applications,” Comput Speech Lang, 
vol. 89, p. 101713, 2025, doi: https://doi.org/10.1016/j.csl.2024.101713.
[50] Z. Khanam, M. D. Semab, H. Ullah Khan, and M. M. Ali Shahid, “Machine 
Learning based Gender Prediction by Exploring Diverse Audio Features,” in 
2023 International Conference on IT and Industrial Technologies (ICIT), 
2023, pp. 1–6. doi: 10.1109/ICIT59216.2023.10335771.
ARTICLE IN PRESS
[51] G. Shi, S. Deng, B. Wang, C. Feng, Y. Zhuang, and X. Wang, “One for All: A 
Unified Generative Framework for Image Emotion Classification,” IEEE 
Transactions on Circuits and Systems for Video Technology, vol. 34, no. 8, 
pp. 7057–7068, 2024, doi: 10.1109/TCSVT.2023.3341840.
ACCEPTED MANUSCRIPT
ARTICLE IN PRESS
[52] J. W. Yoon, B. J. Woo, and N. S. Kim, “HuBERT-EE: Early Exiting HuBERT 
for Efficient Speech Recognition,” Apr. 2022, [Online]. Available: 
http://arxiv.org/abs/2204.06328
[53] J. Wang et al., “MDKAT: Multimodal Decoupling with Knowledge 
Aggregation and Transfer for Video Emotion Recognition,” IEEE 
Transactions on Circuits and Systems for Video Technology, 2025, doi: 
10.1109/TCSVT.2025.3571534.
[54] R. Alsini, A. Naz, H. U. Khan, A. Bukhari, A. Daud, and M. Ramzan, “Using 
deep learning and word embeddings for predicting human agreeableness 
behavior,” Sci Rep, vol. 14, no. 1, Dec. 2024, doi: 10.1038/s41598-024
81506-8.
[55] B. Wan, P. Wu, C. K. Yeo, and G. Li, “Emotion-cognitive reasoning integrated 
BERT for sentiment analysis of online public opinions on emergencies,” Inf 
Process Manag, vol. 61, no. 2, Mar. 2024, doi: 10.1016/j.ipm.2023.103609.
[56] Q. Deng, X. Chen, P. Lu, Y. Du, and X. Li, “Intervening in Negative Emotion 
Contagion on Social Networks Using Reinforcement Learning,” IEEE Trans 
Comput Soc Syst, pp. 1–12, 2025, doi: 10.1109/TCSS.2025.3555607.
[57] H. Luo et al., “ A2Tformer: Addressing Temporal Bias and Non-Stationarity 
in Transformer-Based IoT Time Series Classification ,” IEEE Internet Things 
J, pp. 1–1, Aug. 2025, doi: 10.1109/JIOT.2025.3595765.
[58] H. Strauss et al., “The Emotion-to-Music Mapping Atlas (EMMA): A 
systematically organized online database of emotionally evocative music 
excerpts,” Behav Res Methods, vol. 56, no. 4, pp. 3560–3577, 2024, doi: 
10.3758/s13428-024-02336-0.
[59] U. Ishfaq, H. U. Khan, and K. Iqbal, “Modeling to find the top bloggers using 
Sentiment Features,” in 2016 International Conference on Computing, 
Electronic and Electrical Engineering (ICE Cube), 2016, pp. 227–233. doi: 
10.1109/ICECUBE.2016.7495229.
[60] R. Boghrati and J. Berger, “Quantifying Cultural Change: Gender Bias in 
Music,” J Exp Psychol Gen, vol. 152, no. 9, pp. 2591–2602, Apr. 2023, doi: 
10.1037/XGE0001412.
[61] M. G. Li, K. N. Olsen, and W. F. Thompson, “Cross-Cultural Biases of 
Emotion Perception in Music,” Brain Sci, vol. 15, no. 5, p. 477, May 2025, 
doi: 10.3390/BRAINSCI15050477/S1.
[62] A. Mehta, S. Chauhan, A. Djanibekov, A. Kulkarni, G. Xia, and M. 
Choudhury, “Music for All: Representational Bias and Cross-Cultural 
Adaptability of Music Generation Models,” pp. 4569–4585, Jun. 2025, doi: 
10.18653/V1/2025.FINDINGS-NAACL.258.
[63] A. M. Soler-Gutiérrez et al., “Emotion processing difficulties in ADHD: a 
Bayesian meta-analysis study,” European Child & Adolescent Psychiatry 
2025 34:8, vol. 34, no. 8, pp. 2369–2390, Jan. 2025, doi: 10.1007/S00787
025-02647-3.
ARTICLE IN PRESS
[64] Q. Wang, B. Gu, H. Zhang, and Y. Li, “Fairness of Large Music Models: From 
a Culturally Diverse Perspective,” Proceeding - 2024 IEEE 9th International 
Conference on Data Science in Cyberspace, DSC 2024, pp. 706–712, 2024, 
doi: 10.1109/DSC63484.2024.00105.