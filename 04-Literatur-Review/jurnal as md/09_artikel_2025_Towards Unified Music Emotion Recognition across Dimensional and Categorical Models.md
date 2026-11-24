<!-- Page 1 -->
Towards Unified Music Emotion Recognition across
Dimensional and Categorical Models
Jaeyong Kang
Information Systems, Technology and Design
Singapore University of Technology and Design
Singapore
jaeyong kang@sutd.edu.sg
Dorien Herremans
Information Systems, Technology and Design
Singapore University of Technology and Design
Singapore
dorien herremans@sutd.edu.sg
Abstract—One of the most significant challenges in Music
Emotion Recognition (MER) comes from the fact that emotion
labels can be heterogeneous across datasets with regard to
the emotion representation, including categorical (e.g., happy,
sad) versus dimensional labels (e.g., valence-arousal). In this
paper, we present a unified multitask learning framework that
combines these two types of labels and is thus able to be trained
on multiple datasets. This framework uses an effective input
representation that combines musical features (i.e., key and
chords) and MERT embeddings. Moreover, knowledge distillation
is employed to transfer the knowledge of teacher models trained
on individual datasets to a student model, enhancing its ability
to generalize across multiple tasks. To validate our proposed
framework, we conducted extensive experiments on a variety
of datasets, including MTG-Jamendo, DEAM, PMEmo, and
EmoMusic. According to our experimental results, the inclusion
of musical features, multitask learning, and knowledge distillation
significantly enhances performance. In particular, our model
outperforms the state-of-the-art models on the MTG-Jamendo
dataset. Our work makes a significant contribution to MER by
allowing the combination of categorical and dimensional emotion
labels in one unified framework, thus enabling training across
datasets.
Index Terms—music emotion recognition, multitask learning,
deep learning, knowledge distillation, music, affective computing
I. INTRODUCTION
Music plays an essential role in influencing human emo-
tions [36]. In the past decades, numerous Music Emotion
Recognition (MER) models been developed. MER has found
applications in various domains, e.g., music recommendation
systems [51], generative systems [32], and music therapy [1].
However, the field faces significant challenges due to the
diversity of available datasets and their inconsistent labeling
schemes [28].
Most MER datasets can be categorized into two types: cate-
gorical labels, which represent discrete emotions such as happy
or sad, and dimensional labels, such as Russell’s circumplex
model of affect [44], which describes emotions on continuous
scales of valence and arousal. While these datasets provide
valuable resources, their heterogeneous nature complicates
efforts to combine them effectively. Previous approaches [5],
[9], [10], [26], [34], [40], [43], [48] have often focused on a
single type of label, limiting their ability as they can only train
on one (often small) dataset.
To address these challenges, we introduce a unified multi-
task learning framework that incorporates both categorical and
dimensional emotion labels within a shared architecture. This
approach enables us to train on multiple datasets. Multitask
learning has been shown to be successful on many other
tasks such as speech emotion recognition [6], symbolic music
emotion recognition [41], genre classification and mood detec-
tion [18], to financial portfolio prediction [37]. These studies
demonstrate the benefits of shared representations across tasks.
To properly represent the input music, our proposed frame-
work combines three types of features: 1) Music undERstand-
ing model with large-scale self-supervised Training (MERT)
embeddings [54], 2) harmonic representations of chord pro-
gressions, and 3) musical key. The MERT embeddings are
able to provide a rich representation of timbre, rhythm, and
high-level musical semantics. Chord progressions and musical
key features are able to encode harmonic and tonal structures,
which are equally vital for understanding emotion in music.
An important innovation of our framework is the use of
knowledge distillation (KD) [21] to unify learning across
datasets with disparate label types. Pre-trained teacher models,
optimized for either categorical or dimensional labels, guide
the multitask student model by providing soft target logits,
which are probability distributions over the possible labels.
These logits help the student model learn more effectively by
transferring the teacher model’s knowledge, thereby improving
generalization and performance across datasets. Additionally,
the framework incorporates data augmentation strategies dur-
ing feature extraction to introduce variability and mitigate
overfitting, ensuring robustness across diverse audio inputs.
To validate our proposed framework, we conducted several
experiments on multiple datasets, including MTG-Jamendo [4]
for categorical labels and DEAM [3], PMEmo [55], and Emo-
Music [46] for dimensional labels. Our experimental results
show that integration of MERT embeddings with high-level
musical feature (i.e., chord progression and key) significantly
enhances performance. In addition, training the network on
heterogeneous datasets with multitask learning can further
improve performance on single datasets, demonstrating the
ability to bridge the gap between diverse label types. On
the MTG-Jamendo dataset, our model achieves state-of-the-art
performance, surpassing the best-performing model, lileonardo
arXiv:2502.03979v3  [cs.SD]  2 Oct 2026

<!-- Page 2 -->
[5], from the MediaEval 2021 competition [50], as well as
more recent approaches [18], [19], with the highest PR-AUC
of 0.1543 and ROC-AUC of 0.7810. These results highlight
the effectiveness of our approach in advancing MER.
In summary, our contributions are listed as follows:
•We developed a unified multitask learning framework
for MER that facilitates training on datasets with both
categorical and dimensional emotion labels.
•We combined the high-level musical features with MERT
embeddings for a richer input representation.
•We conducted several experiments and showed the ef-
fectiveness of our proposed framework. In addition, our
proposed model achieves state-of-the-art performance on
the MTG-Jamendo dataset [4].
In the rest of the paper, we first describe the related
work in Section II. This is followed by a description of our
proposed framework in Section III. After that, we describe
our experimental setup and its results in Section IV. Finally,
Section VI offers conclusions from this work.
II. RELATEDWORK
Below we will discuss some of the existing literature in
MER research. For a more comprehensive overview of the
literature, the reader is referred to [28], [45].
A. Single-Task MER Models
Most MER models mainly concentrate on single-task learn-
ing, which involves training models on individual datasets
which use particular emotion labeling schemes, like cate-
gorical labels (e.g., happy, sad) or dimensional labels (e.g.,
valence-arousal). Convolutional neural network (CNN)-based
methods have demonstrated strong performance in MER
across various datasets. For instance, Liu et al. [31] proposed
a spectrogram-based CNN model which captures temporal
and spectral features. This model has a macro F1-score of
0.472 and a micro F1-score of 0.534 on CAL500 dataset
[52], and a macro F1-score of 0.596 and a micro F1-score of
0.709 on CAL500exp dataset [53], outperforming traditional
approaches. Bour et al. [5] introduced the frequency-dependent
convolutions in a CNN model, achieving the highest perfor-
mance at MediaEval 2021 with a PR-AUC-macro of 0.1509
and a ROC-AUC-macro of 0.7748 on MTG-Jamendo dataset
[4]. Recently, Jia [26] introduced a CNN-based model which
combines MFCCs with residual phase features, achieving a
recognition accuracy of 92.06% on a dataset comprising 2,906
songs categorized into four emotion classes: anger, happiness,
relaxation, and sadness.
Given the temporal nature of music, many researchers
use recurrent neural network (RNN)-based architectures, such
as Long-Short Term Memory networks (LSTMs) and Gated
Recurrent Units (GRUs). For instance, Rajesh et al. [43]
used LSTMs with MFCC features to predict emotion on
the DEAM dataset [3], achieving an accuracy of 89.3%,
which is better than SVM’s 85.7%. Chaki et al. [9] added
attention mechanisms to LSTMs to concentrate on emotionally
significant segments, resulting inR 2 scores of 0.53 for valence
and 0.75 for arousal on the EmoMusic dataset [46], surpassing
the performance of the LSTM variant that lacked attention
mechanisms.
Recently, Transformer-based methods have seen a rise in
popularity. For instance, Suresh et al. [47] proposed the
multimodal model with Transformer-based architecture for
classifying the mood of music by leveraging the features from
audio and lyrics. Their proposed model was evaluated on a
subset of the MoodyLyrics dataset [7] which contains audio
and lyrics of 680 songs. Their proposed model outperforms
the unimodal model with an accuracy of 77.94%.
The absence of official train/test splits in many datasets,
such as the PMEmo dataset [55], makes it difficult to compare
models directly, except for the MTG-Jamendo dataset [4],
which provides official splits. This enables us to compare
our model with those from MediaEval 2021 [5], [34], [40],
[48] as well as more recent methods [18], [19], [29] in our
experiments. Despite these achievements, single-task mod-
els frequently face challenges in generalizing across various
datasets, underscoring the need for research that integrates
multiple datasets.
B. MER Models with Multi-Dataset Integration
Integrating multiple datasets is essential for improving gen-
eralization but is challenging due to inconsistencies in labeling
schemes, especially between categorical and dimensional la-
bels. Liu et al. [30] addressed this issue by leveraging a large
language model (LLM) to align categorical labels from various
datasets into a common semantic space. They used three
disjoint datasets with categorical labels, which include MTG-
Jamendo [4], CAL500 [52], and Emotify [2]. They showed
the effectiveness of their approach by performing zero-shot
inference on a new dataset.
Mazzetta et al. [35] introduced a multi-source learning
framework that integrates features and labels from heteroge-
neous datasets, including 4Q [38], PMEmo [55], EmoMusic
[46], and the Bi-Modal Emotion Dataset [33] to enhance the
model’s robustness. These datasets use Russell’s Circumplex
Model of Affect, and focus on the valence and arousal
dimensions. While this framework effectively utilizes dimen-
sional labels to improve robustness, it does not incorporate
categorical labels, thus limiting its ability to fully leverage the
diversity of available datasets [28]. Developing frameworks
that integrate both label types remains an open challenge,
which we address in this work.
C. Multitask Learning in MER
Multitask learning (MTL) [8] aims to enhance the perfor-
mance of multiple related tasks by leveraging shared knowl-
edge among them. Qiu et al. [41] introduced an MTL frame-
work for Symbolic Music Emotion Recognition (SMER). They
combines emotion recognition task with auxiliary tasks such
as key and velocity classification. The idea is that by forcing
the model to learn key and velocity information, it will also
better understand the resulting emotion. Evaluated on the
EMOPIA [24] and VGMIDI [17] datasets, their approach

<!-- Page 3 -->
Fig. 1. Overall architecture of our proposed framework.
achieved accuracy improvements of 4.17% and 1.97%, respec-
tively, compared to single-task models. Ji et al. [23] intro-
duced an attention-based deep feature fusion (ADFF) method
for valence-arousal prediction within a multitask learning
framework. They integrate spatial feature extraction using an
adapted VGGNet with a squeeze-and-excitation (SE) attention-
based temporal module to enhance affect-salient features.
Their model achievedR 2 scores of 0.4575 for valence and
0.6394 for arousal on the PMEmo dataset [55].
Existing MTL frameworks in MER are typically still trained
on datasets with one type of emotion label. In this research, we
explore how we can leverage an MTL architecture to enable
predicting across heterogeneous emotion datasets.
D. Knowledge Distillation for MER
Knowledge distillation (KD) is a technique where a smaller
student model learns to replicate the behavior of a larger
teacher model by aligning its soft predictions with those of the
teacher, rather than solely relying on the actual labels [21]. In
contrast to transfer learning, which usually involves adjusting
a pre-trained model for a new task or dataset, KD emphasizes
the use of the teacher model’s outputs (soft labels) to guide
the training of the student model. Tong [49] proposed a KD-
based multimodal MER framework that uses a teacher-student
model, where a pre-trained genre classification model transfers
knowledge to an emotion recognition model. Knowledge trans-
fer is guided by Exponential Moving Average (EMA) analysis
that refines the student model’s parameters without backprop-
agation. The training minimizes a combined KL divergence
and cross-entropy loss, which improves emotion recognition
in terms of both labeled and unlabeled data while maintaining
efficiency. Jeong et al. [25] demonstrated the potential of KD
in a multitask setting for valence-arousal prediction, facial
expression recognition, and action unit prediction. Despite its
promise, the use of KD in multitask frameworks for integrating
heterogeneous labels remains underexplored.
E. Feature Engineering for MER
Feature engineering is a key component in Music Emotion
Recognition (MER). Earlier works relied heavily on hand-
crafted features such as MFCCs, chroma features, and rhyth-
mic descriptors [22], which capture low-level signal properties
but fall short in representing higher-level musical semantics
[39]. Other approaches leverage embeddings from audio mod-
els trained on large-scale datasets. For example, VGGish [20],
a convolutional model trained in a supervised fashion for
audio classification, and CLAP [16], which is trained with
a contrastive audio-text alignment objective, have been used
to extract richer representations of audio content.
Pre-trained encoders have also gained traction in MER due
to their ability to learn from unlabeled audio data. Among
these, MERT [54] has demonstrated strong performance rel-
ative to other pre-trained encoders. For instance, MERT-95M
achieves a PR-AUC of 0.134 and an ROC-AUC of 0.764 on the
MTG-Jamendo dataset, while the larger MERT-330M model
improves these scores slightly to a PR-AUC of 0.14 and an
ROC-AUC of 0.765. These results highlight the potential of
pre-trained encoders for emotion prediction tasks.
Beyond embeddings, high-level musical features such as
key signatures and chord progressions have also been shown
to play a significant role in emotion prediction [11]. In this
study, we aim to enhance MER by integrating large-scale
audio embeddings with these symbolic, high-level musical
descriptors.
III. PROPOSEDMETHOD
In this section, we present our proposed unified multitask
learning framework for Music Emotion Recognition (MER),
which trains on both categorical and dimensional emotion
labels.

<!-- Page 4 -->
Fig. 2. MERT feature extraction and data augmentation workflow.
The overall framework of our proposed MER system is
shown in Figure 1. First, we extract three complementary
features from audio signals: 1) embeddings from the MERT
model [54], 2) harmonic representations of chord progressions,
and 3) musical key. These features are then concatenated
and fed into classifiers in our multitask learning architec-
ture to predict both categorical and dimensional emotion
labels simultaneously. Furthermore, we leverage knowledge
distillation technique, where teacher models are first trained
separately on individual datasets—MTG-Jamendo for cate-
gorical labels and DEAM, PMEmo, and EmoMusic for di-
mensional labels—without multitask-specific branches. These
trained teacher models generate soft logits to guide the student
model during multitask learning, thereby improving perfor-
mance across datasets with different label types.
A. Feature Extraction
To effectively capture music emotion, our proposed frame-
work has two distinct feature extraction pipelines: 1) pre-
trained embeddings from MERT and 2) musical features.
1) Pre-trained embeddings (MERT):The Music undER-
standing model with large-scale self-supervised Training
(MERT) [54] is employed for extracting embeddings from
audio files. MERT is able to learn rich musical representations,
capturing various musical features that make its embeddings
highly effective for downstream tasks such as music emotion
recognition (MER). To optimize performance for emotion
recognition tasks, we derive embeddings by concatenating the
outputs from the 5th and 6th layers of MERT, as these layers
have demonstrated superior performance for music emotion
prediction through preliminary experimentation.
To improve the model’s robustness, the data augmenta-
tion step is incorporated within the MERT feature extraction
pipeline as illustrated in Figure 2. The data augmentation step
is outlined as follows:
1) The audio track is divided into fixed-length segments
(i.e., 30 seconds each).
2) MERT embeddings are obtained for each segment from
the 5th and 6th layers.
3) These embeddings from both layers are then combined
to create the feature vector for each segment.
4) During training, we randomly select a series of consec-
utive segments. The starting index and the number of
segments are chosen uniformly at random (e.g., Seg =
[2,3] in Figure 2).
5) The final feature vector is formed by averaging the
embeddings of the selected segments.
The intuition behind this augmentation strategy is to ex-
pose the model to varying temporal contexts of the same
track across training epochs. Emotion in music can vary
subtly throughout a piece—different sections might convey
slightly different moods due to changes in melody, harmony,
rhythm, or instrumentation. By randomly sampling and aver-
aging different combinations of segments, the model learns
to generalize across these intra-track variations, rather than
overfitting to a single static representation. This not only
improves robustness to local variations in musical content
but also better reflects the dynamic and evolving nature of
emotional expression in music.
2) Musical Features (Chord and Key):Unlike the seg-
mented and augmented MERT features, musical features (such
as chord progressions and key signatures) are calculated over
the whole song, representing global harmonic and tonal infor-
mation. The framework integrates harmonic and tonal informa-
tion by extracting musical features such as chord progressions
and key signatures. A Transformer-based chord recognition
model [27] is used for extracting the chord progressions of the
song. The chord recognition model was evaluated on the fol-
lowing datasets: a subset of 221 songs from Isophonics 1(171
songs by the Beatles, 12 songs by Carole King, 20 songs by
Queen and 18 songs by Zweieck), Robbie Williams [14] (65
songs by Robbie Williams), and a subset of 185 songs from
UsPop20022. The chord recognition model is evaluated using
mir_evalmetrics [42], achieving Weighted Chord Symbol
Recall (WCSR) scores of 83.5% for Root, 80.8% for Thirds,
75.9% for Triads, 71.8% for Sevenths, 65.5% for Tetrads,
82.3% for Maj-min, and 80.8% for the MIREX categories.
These scores are considered acceptable for this study, as most
errors are minor, such as misclassifyingA minorasC major.
In our model, each chord is encoded by its root (e.g.,D) and
quality (e.g.,sus4), representing the chord type, and mapped
into an embedding space to capture harmonic patterns. These
chord progressions are then converted into MIDI representa-
tions based on music theory. For instance, aC majorchord
comprises the notesC, E, G, while aC minor 7thchord
comprises the notesC, E, G, B. The start and end times of
1http://isophonics.net/datasets
2https://github.com/tmc323/Chord-Annotations

<!-- Page 5 -->
each chord are mapped to define its duration in the MIDI file.
This MIDI representation serves as input to a key detection
model.
Key detection is performed using the music21 library [12].
To ensure consistency in the representation of chords, we
‘normalize’ them based on the key. Extracted chords from
songs in major keys are transposed to C major, while those
from minor keys are transposed to A minor. The extracted
chord sequences have 13 different chord types such as ‘ma-
jor’, ‘minor’, ‘diminished’, ‘augmented’, ‘suspended’, and
‘seventh’ chords. The key is encoded based on its mode.
For instance, ‘major’ corresponds to C major and ‘minor’
corresponds to A minor. These harmonic features—key (as
a scalar) and chords (as sequences of embedded tokens)—are
integrated with MERT features and used as input to the model.
3) Temporal Modeling of Chord Progressions:The out-
put of the chord detection model gives us a long sequence
of chords. To capture the temporal dependencies and rela-
tionships in these harmonic progressions, we model these
sequences using a Transformer-based encoder architecture,
(marked as ‘Chord Transformer’ in Figure 1). Each chord
in thet-th position of the sequence is represented as a
concatenation of its root embedding,C (t)root ∈R droot, and quality
embedding,C (t)quality ∈R dquality. The combined embedding for
thet-th chord is expressed as follows:
C(t) =C (t)root ⊕C (t)quality,(1)
where⊕denotes vector concatenation, resulting inC (t) ∈
Rdroot+dquality.
To incorporate the sequential structure of the chord progres-
sion, a positional encodingP (t) ∈R droot+dquality is added to the
embeddings:
C(t)enc =C (t) +P (t).(2)
The encoded chord embeddings,C enc =
[C(1)enc ,C (2)enc , . . . ,C(T)enc ], represent the sequence of chords
for the song, whereTis the total number of chords in
the sequence. A special CLS token,CLS∈R droot+dquality, is
prepended to this sequence to aggregate global information:
Cin = [CLS,C (1)enc ,C (2)enc , . . . ,C(T)enc ].(3)
The input sequence is processed by a Transformer encoder
with two layers and eight attention heads, generating output
embeddingsC out, where the first token corresponds to the CLS
representation:
CCLS-out =Transformer(C in)[0].(4)
The outputC CLS-out, taken as the first element of the
Transformer output, serves as a global representation of the
chord progression. Rather than merely reflecting its positional
placement, the CLS token aggregates information from all
chord embeddings via the self-attention mechanism.
It is concatenated with the MERT embeddings,f MERT, and
key embeddings,K, to form the final combined feature vector:
ffinal =C CLS-out ⊕f MERT ⊕K.(5)
The combined feature vector is projected into a latent space
using a feedforward layer with 512 units and ReLU activation
before being passed to task-specific branches for mood classi-
fication and valence-arousal regression. The classification and
regression branches each consist of two feedforward layers
with 256 hidden units.
B. Classification with Multitask Learning
In our proposed multitask learning framework, we have two
different branches to handle both categorical and dimensional
music emotion prediction tasks. We use a Binary Cross-
Entropy (BCE) loss function when training the network on the
dataset with categorical labels, such as “happy” or “sad”. To
address the class imbalance issue, the BCE loss is weighted
based on the frequency of the positive class for each label,
which is defined as follows:
LCat(x, y) =−1c
cX
i=1
(wiyi log(xi) + ¯wi(1−y i) log(1−x i)),
(6)
wherexis the predicted probabilities for each emotion cate-
gory, andyis the corresponding ground-truth binary label (1
for presence and 0 for absence of the category),cdenotes
the total number of emotion labels, ensuring that the loss
is averaged across all categories, and the termw i adjusts
the contribution of the positive class, while¯w i scales the
contribution of the negative class, which can be defined as:
wi = 21 +p i ,¯w i = 2pi1 +p i ,(7)
wherep i is the frequency of the positive class for labeli.
For dimensional labels, the model predicts continuous va-
lence and arousal (V A) values using a Mean Squared Error
(MSE) loss. The MSE loss is given by:
LV A(x, y) = (yv −x v)2 + (ya −x a)2,(8)
wherey v andy a are the ground-truth valence and arousal
values, andx v andx a are their respective predictions.
We use a selective update strategy to mitigate task inter-
ference in our multitask learning framework. For the dataset
with categorical labels such as MTG-Jamendo, we update
only the categorical branch’s parameter. Likewise, for the
datasets with dimensional labels (e.g., DEAM or PMEmo),
we update only the parameters of the dimensional branch. By
taking a selective update strategy, the model can effectively
learn from heterogeneous datasets with preserved task-specific
performance.
C. Knowledge Distillation
We use the knowledge distillation technique to efficiently
train our multitask models by transferring knowledge from
the pre-trained teacher models to the multitask student models
[21]. Separate teacher models are trained on categorical and
dimensional datasets, each optimized for its respective task.
For instance, a teacher model trained on the MTG-Jamendo

<!-- Page 6 -->
dataset generates soft labels for categorical labels, while
teacher models trained on DEAM, PMEmo, and EmoMusic
generate soft labels for dimensional predictions.
The student model learns from both hard labels (ground
truth) and soft logits through the Kullback-Leibler (KL) di-
vergence loss, which is defined as:
LKD(s, t) =
cX
i=1
ti log
 ti
si

,(9)
wheresandtdenote the predicted and teacher-generated soft
labels, respectively,cis the number of output dimensions (i.e.,
emotion categories for classification, or 2 for valence and
arousal in regression), ands i,t i represent thei-th elements of
the student and teacher distributions, respectively.
D. Total Loss Function
The total loss function combines the task-specific loss with
the KL divergence loss derived from the teacher models.
Specifically, for categorical and dimensional datasets, the total
loss functions are defined as:
LTotal,Cat =α·L Cat + (1−α)·L KD,Cat,(10)
LTotal,V A=β·L V A+ (1−β)·L KD,V A,(11)
whereαandβare hyperparameters that control the balance
between the task-specific loss and the KL divergence loss for
classification and regression, respectively.L KD,Cat andL KD,V A
refer to the KL divergence losses computed using the soft
targets generated by the classification and regression teacher
models, respectively.L Total,Cat andL Total,V Arepresent the final
loss values used to update the classification and regression
branches of the multitask model, respectively.
IV. EXPERIMENTAL SETUP
In this section, we discuss the experimental setup of the
proposed unified multitask learning framework.
A. Dataset
In our experiment, we use four different datasets for ei-
ther categorical emotion recognition or dimensional emotion
prediction tasks. For categorical emotion recognition, we use
theMTG-Jamendo dataset[4], which consists of 18,486
full-length tracks labeled with 56 mood/theme tags such as
“happy” and “sad”.
For dimensional emotion prediction, we use three different
datasets with valence-arousal (V A) labels which are normal-
ized within the range of 1 to 9:
•DEAM dataset[3]: This dataset contains 1,802 songs
from Western pop and rock. It has both dynamic and
static V A annotations. We use the static V A annotations.
•PMEmo dataset[55]: This dataset consists of 794 songs
from Western pop. It has both dynamic and static V A
annotations. We use the static V A annotations.
•EmoMusic dataset[46]: This dataset contains 744 songs
spanning diverse genres. It has both dynamic and static
V A annotations. We use the static V A annotations.
To ensure consistency, we follow the official train, val-
idation, and test splits for the MTG-Jamendo dataset. For
the other datasets which do not provide official training,
validation, and test splits, we randomly split the data into 70%
for the training set, 15% for the validation set, and 15% for
the test set. The details of the datasets used in our experiments
are shown in Table I.
B. Implementation details
To extract MERT features, the audio tracks are segmented
into 30-second clips. We leverage the popular MERT-v1-
95M model, accessible via Hugging Face 3, to obtain the
embeddings. Knowledge distillation (KD) is employed, where
teacher models pre-trained on each dataset guide the student
model during multitask learning. The teacher models are
trained separately on each dataset using the same architecture
as the student. For feature extraction, we concatenate the 5th
and 6th layer embeddings of MERT and process chord/key
features with the Chord Transformer with positional encoding.
The hyperparameters for the total loss function (as defined in
Equations 10 and 11) are set toα= 0.2andβ= 0.2. During
training, only the relevant loss components are updated based
on the dataset type (categorical or dimensional). The student
and teacher models are trained for 200 epochs with a batch
size of 8, a learning rate of 0.0001, and the Adam optimizer.
All models, including both the student and teacher models,
are trained on a cluster of four NVIDIA Tesla V100 DGXS
GPUs, each with 32 GB of memory. The code is implemented
in PyTorch and is available online 4.
C. Performance Metrics
Depending on the labeling schemes of datasets, we em-
ploy different metrics for evaluating our proposed models.
For instance, we use both Precision-Recall AUC (PR-AUC)
and Receiver Operating Characteristic AUC (ROC-AUC) for
MTG-Jamendo dataset with categorical labels. On the other
hand, we use theR 2 scores for valence (R 2V ) and arousal
(R2A) for other three datasets with dimensional labels.
1) PR-AUC and ROC-AUC:PR-AUC [13] measures
precision-recall trade-offs to assess classification performance.
This is especially useful for unbalanced datasets. On the other
hand, ROC-AUC [13] assesses how well a model performs by
analyzing true positive and false positive rates across various
decision thresholds.
2)R 2 Scores for Valence and Arousal:TheR 2 score [15]
quantifies how well the model explains variance in valence and
arousal predictions. Higher values indicate better predictive
accuracy, withR 2V used for valence andR 2A for arousal.
3https://huggingface.co/m-a-p/MERT-v1-95M
4https://github.com/AMAAI-Lab/Music2Emotion

<!-- Page 7 -->
TABLE I
DETAILS OF THE DATASET.
Dataset # of training data # of validation data # of test data Length Emotion model
MTG-Jamendo 9,949 3,802 4,231 full Categoric (56 labels)
DEAM 1,261 271 270 45s Dimensional
PMEmo 536 116 115 full Dimensional
EmoMusic 495 124 125 45s Dimensional
TABLE II
ABLATION STUDY ON INFLUENCE OF INPUT FEATURES ON PERFORMANCE METRICS ACROSS DATASETS. HERE, FNNSTANDS FORFEEDFORWARD
NEURALNETWORK.
Input feature Model MTG-Jamendo DEAM EmoMusic PMEmo
PR-AUC ROC-AUCR 2V R2A R2V R2A R2V R2A
MERT FNN 0.1297 0.7590 0.4972 0.5951 0.5657 0.7404 0.5231 0.7670
Chord/Key Transformer + FNN 0.0531 0.6158 0.0706 0.0770 0.0781 0.0585 0.0149 0.0337
MERT + Chord/Key Transformer + FNN0.1521 0.7806 0.5131 0.6025 0.5957 0.7489 0.5360 0.7772
TABLE III
COMPARISON OF PERFORMANCE METRICS FOR OUR MULTITASK LEARNING MODEL ACROSS MULTIPLE(TEST)DATASETS,WHEN TRAINED ON
DIFFERENT TRAINING SETS. HERE, J, D, E,ANDPSTAND FOR THEMTG-JAMENDO, DEAM, EMOMUSIC,ANDPMEMO DATASETS,RESPECTIVELY.
Training datasets MTG-Jamendo (J.) DEAM (D.) EmoMusic (E.) PMEmo (P.)
PR-AUC ROC-AUCR 2V R2A R2V R2A R2V R2A
Single dataset training (X) 0.1521 0.7806 0.5131 0.6025 0.5957 0.7489 0.5360 0.7772
J + D 0.1526 0.7806 0.5144 0.6046 - - - -
J + E 0.1540 0.7809 - - 0.6091 0.7525 - -
J + P 0.1522 0.7806 - - - - 0.5401 0.7780
J + D + E + P0.1543 0.7810 0.5184 0.6228 0.6512 0.7616 0.5473 0.7940
TABLE IV
COMPARISON OF OUR PROPOSED MODEL WITH EXISTING MODELS ON
MTG-JAMENDO DATASET.
Model PR-AUC ROC-AUC
lileonardo [5] 0.1508 0.7747
SELAB-HCMUS [40] 0.1435 0.7599
Mirable [48] 0.1356 0.7687
UIBK-DBIS [34] 0.1087 0.7046
Hasumi et al. [19] 0.0730 0.7750
Greer et al. [18] 0.1082 0.7354
MERT-95M [54] 0.1340 0.7640
MERT-330M [54] 0.1400 0.7650
Proposed (Ours)0.1543 0.7810
D. Baseline Models on MTG-Jamendo
To evaluate the effectiveness of our approach, we compare it
against several representative models developed for the MTG-
Jamendo dataset, as shown in Table IV: 1)lileonardo[5], a
deep CNN that applies frequency-dependent convolutions to
mel spectrograms, achieving the top score in the MediaEval
2021 competition; 2)SELAB-HCMUS[40], which uses a
co-teaching training strategy and short audio segments to
enhance performance and reduce training time; 3)Mirable
[48], which explores semi-supervised learning through noisy
student training and harmonic pitch class profiles (HPCP);
4)UIBK-DBIS[34], an ensemble-based model that clusters
emotion labels to train specialized classifiers; 5)Hasumi et
al.[19], which proposes classifier group chains to capture tag
dependencies for improved music tagging; 6)Greer et al.
[18], who introduce M3BERT, a multi-task, self-supervised
transformer trained via masked reconstruction and fine-tuned
for emotion recognition; and 7)MERT[29], a large-scale
acoustic music understanding model (with 95M and 330M
parameters) pre-trained using pseudo labels from acoustic and
musical teachers, demonstrating strong performance across
several music understanding tasks.
V. RESULTS
In a first experiment, we removed the high-level musical
features (i.e., key and chords) from our proposed framework
and trained the network using the MERT features only. The
performance of the models with these different input feature
configurations is shown in Table II. As can be seen from the
table, incorporating both the MERT and high-level musical
features significantly enhanced the performance of our model.
The model with high-level musical features includes the Chord
Transformer model. This achieves the best results, including a

<!-- Page 8 -->
PR-AUC of 0.1521 and an ROC-AUC of 0.7806 on the MTG-
Jamendo dataset. Furthermore, the framework achieves higher
R2V andR 2A scores for valence and arousal on the dimensional
datasets (DEAM, EmoMusic, and PMEmo), demonstrating the
importance of including the musical features.
In a second experiment, we explore how training the net-
work on heterogeneous datasets can improve performance on
single datasets. Table III shows the comparison of performance
metrics when training on multiple datasets. We trained the
network on multiple datasets as indicated in the leftmost
column. When comparing our results without data fusion to
the results for our model trained on each of the datasets
separately (row 1), we notice that the performance clearly
increases when adding a second dataset. However, the best
performance is reached when training on all datasets (MTG-
Jamendo + DEAM + EmoMusic + PMEmo), with a PR-AUC
of 0.1543 and an ROC-AUC of 0.7810 on the MTG-Jamendo
dataset, as well as the bestR 2V andR 2A scores across the
dimensional datasets. These results show the importance of
leveraging diverse datasets in a unified multitask framework.
Lastly, we evaluated our proposed model on the MTG-
Jamendo dataset using its official train-validation-test split,
which enables direct comparison with prior work. As shown
in Table IV, our model achieves strong performance compared
to both earlier baselines such as lileonardo [5] from the
MediaEval 2021 competition [50], as well as more recent
representative methods [18], [19], [54], which reflect current
directions in MER modeling. The substantial improvement
over these models suggests that our proposed framework is
a promising approach for categorical emotion recognition in
music. In contrast, other MER datasets do not offer official
splits, which makes direct performance comparison less con-
sistent across studies.
These results confirm our proposed framework as a tool to
unify categorical and dimensional emotion recognition without
sacrificing state-of-the-art performance. The integration of
MERT embeddings, musical features, multitask learning, and
knowledge distillation proves to be a highly effective method
that enhances music emotion recognition on diverse datasets
and labeling schemes.
VI. CONCLUSION
In this study, we propose a unified multitask learning frame-
work for Music Emotion Recognition (MER) that facilitates
training on datasets with both categorical and dimensional
emotion labels. Our proposed architecture incorporates knowl-
edge distillation and takes both high-level musical features
such as chords and key signatures, as well as pre-trained em-
beddings from MERT as input, thus enabling it to effectively
capture emotional nuances in music. The experimental results
demonstrate that our framework outperforms state-of-the-art
models on the MTG-Jamendo dataset, including the winners
of the MediaEval 2021 competition. Our best model achieves
a PR-AUC of 0.1543 and an ROC-AUC of 0.7810. This
model is made available open-source online. Our results show
that our multitask learning approach enables generalization
across diverse datasets, while knowledge distillation facilitates
efficient knowledge transfer from teacher to student models.
In summary, our work provides a robust solution for training
on multiple datasets with different types of emotion labels. In
future research, we may explore the addition of different mu-
sical features as input to the model, refine data augmentation
techniques, and expand the framework’s applicability to other
affective computing domains.
ACKNOWLEDGMENT
This work has received funding from grant no. SUTD SKI
2021 04 06 and MOE under grant number MOE-T2EP20124-
0014. We acknowledge the use of ChatGPT for grammar
refinement.
REFERENCES
[1] K. R. Agres, R. S. Schaefer, A. V olk, S. van Hooren, A. Holzapfel,
S. Dalla Bella, M. M ¨uller, M. De Witte, D. Herremans, R. Ramirez Me-
lendez, et al. Music, computing, and health: a roadmap for the current
and future roles of music technology for health care and well-being.
Music & Science, 4:2059204321997709, 2021.
[2] A. Aljanaki, F. Wiering, and R. C. Veltkamp. Studying emotion induced
by music through a crowdsourcing game.Information Processing &
Management, 52(1):115–128, 2016.
[3] A. Aljanaki, Y .-H. Yang, and M. Soleymani. Developing a benchmark
for emotional analysis of music.PloS one, 12(3):e0173392, 2017.
[4] D. Bogdanov, M. Won, P. Tovstogan, A. Porter, and X. Serra. The
mtg-jamendo dataset for automatic music tagging. ICML, 2019.
[5] V . Bour. Frequency dependent convolutions for music tagging. In
MediaEval, 2021.
[6] X. Cai, J. Yuan, R. Zheng, L. Huang, and K. Church. Speech emotion
recognition with multi-task learning. InInterspeech, volume 2021, pages
4508–4512. Brno, 2021.
[7] E. C ¸ ano and M. Morisio. Moodylyrics: A sentiment annotated lyrics
dataset. InProceedings of the 2017 international conference on
intelligent systems, metaheuristics & swarm intelligence, pages 118–
124, 2017.
[8] R. Caruana. Multitask learning.Machine learning, 28:41–75, 1997.
[9] S. Chaki, P. Doshi, P. Patnaik, and S. Bhattacharya. Attentive rnns for
continuous-time emotion prediction in music clips. InAffCon@ AAAI,
pages 36–46, 2020.
[10] C. Chen and Q. Li. A multimodal music emotion classification method
based on multifeature combined network classifier.Mathematical
Problems in Engineering, 2020(1):4606027, 2020.
[11] Y .-H. Cho, H. Lim, D.-W. Kim, and I.-K. Lee. Music emotion
recognition using chord progressions. In2016 IEEE Int. Conf. on
Systems, Man, and Cybernetics (SMC), pages 002588–002593. IEEE,
2016.
[12] M. S. Cuthbert and C. Ariza. music21: A toolkit for computer-aided
musicology and symbolic music data. 2010.
[13] J. Davis and M. Goadrich. The relationship between precision-recall and
roc curves. InProc. of the 23rd Int. conference on Machine learning,
pages 233–240, 2006.
[14] B. Di Giorgi, M. Zanoni, A. Sarti, and S. Tubaro. Automatic chord
recognition based on the probabilistic modeling of diatonic modal
harmony. InnDS’13; Proceedings of the 8th International Workshop
on Multidimensional Systems, pages 1–6. VDE, 2013.
[15] N. Draper.Applied regression analysis. McGraw-Hill. Inc, 1998.
[16] B. Elizalde, S. Deshmukh, M. Al Ismail, and H. Wang. Clap learning
audio concepts from natural language supervision. InICASSP 2023-2023
IEEE Int. Conf. on Acoustics, Speech and Signal Processing (ICASSP),
pages 1–5. IEEE, 2023.
[17] L. N. Ferreira and J. Whitehead. Learning to generate music with
sentiment.arXiv:2103.06125, 2021.
[18] T. Greer, X. Shi, B. Ma, and S. Narayanan. Creating musical features us-
ing multi-faceted, multi-task encoders based on transformers.Scientific
Reports, 13(1):10713, 2023.
[19] T. Hasumi, T. Komatsu, and Y . Fujita. Music tagging with classifier
group chains.arXiv:2501.05050, 2025.

<!-- Page 9 -->
[20] S. Hershey, S. Chaudhuri, D. P. Ellis, J. F. Gemmeke, A. Jansen, R. C.
Moore, M. Plakal, D. Platt, R. A. Saurous, B. Seybold, et al. Cnn
architectures for large-scale audio classification. In2017 ieee Int.
conference on acoustics, speech and signal processing (icassp), pages
131–135. IEEE, 2017.
[21] G. Hinton. Distilling the knowledge in a neural network.
arXiv:1503.02531, 2015.
[22] S. Hizlisoy, S. Yildirim, and Z. Tufekci. Music emotion recognition
using convolutional long short term memory deep neural networks.Eng.
Sci. Technol. Int J., 24(3):760–767, 2021.
[23] Z. Huang, S. Ji, Z. Hu, C. Cai, J. Luo, and X. Yang. Adff: Attention
based deep feature fusion approach for music emotion recognition.
arXiv:2204.05649, 2022.
[24] H.-T. Hung, J. Ching, S. Doh, N. Kim, J. Nam, and Y .-H. Yang. Emopia:
A multi-modal pop piano dataset for emotion recognition and emotion-
based music generation.arXiv:2108.01374, 2021.
[25] E. Jeong, G. Oh, and S. Lim. Multitask emotion recognition model with
knowledge distillation and task discriminator.arXiv:2203.13072, 2022.
[26] X. Jia. A music emotion classification model based on the improved
convolutional neural network.Computational Intelligence and Neuro-
science, 2022(1):6749622, 2022.
[27] P. Jonggwon, C. Kyoyun, J. Sungwook, K. Dokyun, and P. Jonghun. A
bi-directional transformer for musical chord recognition. In20th Inter-
national Society for Music Information Retrieval Conference (ISMIR),
Delft, The Netherlands, 2019.
[28] J. Kang and D. Herremans. Are we there yet? a brief survey of
music emotion prediction datasets, models and outstanding challenges.
arXiv:2406.08809, 2024.
[29] Y . Li, R. Yuan, G. Zhang, Y . Ma, X. Chen, H. Yin, C. Xiao, C. Lin,
A. Ragni, E. Benetos, et al. Mert: Acoustic music understanding model
with large-scale self-supervised training.arXiv:2306.00107, 2023.
[30] R. Liu, A. Roy, and D. Herremans. Leveraging llm embeddings for
cross dataset label alignment and zero shot music emotion prediction.
arXiv:2410.11522, 2024.
[31] X. Liu, Q. Chen, X. Wu, Y . Liu, and Y . Liu. Cnn based music emotion
classification.arXiv:1704.05665, 2017.
[32] D. Makris, K. R. Agres, and D. Herremans. Generating lead sheets with
affect: A novel conditional seq2seq framework. In2021 Int. Joint Conf.
on Neural Networks (IJCNN), pages 1–8. IEEE, 2021.
[33] R. Malheiro, R. Panda, P. J. Gomes, and R. P. Paiva. Bi-modal music
emotion recognition: Novel lyrical features and dataset. In9th Int.
Workshop on Music and Machine Learning–MML, 2016.
[34] M. Mayerl, M. V ¨otter, A. Peintner, G. Specht, and E. Zangerle.
Recognizing song mood and theme: Clustering-based ensembles. In
MediaEval, 2021.
[35] G. Mazzetta, A. Greco, M. Tagliasacchi, and A. Pescap `e. A multi-
source deep learning model for music emotion recognition. InProc. of
the AIxHMI Workshop at CEUR-WS, volume 3903, pages 1–8. CEUR
Workshop Proc., 2024.
[36] L. B. Meyer.Emotion and meaning in music. PhD thesis, The University
of Chicago, 1954.
[37] J. Ong and D. Herremans. Constructing time-series momentum portfo-
lios with deep multi-task learning.Expert Systems with Applications,
230:120587, 2023.
[38] R. Panda, R. Malheiro, and R. P. Paiva. Musical texture and expressivity
features for music emotion recognition. In19th Int. Society for Music
Information Retrieval Conf. (ISMIR 2018), pages 383–391, 2018.
[39] R. Panda, R. Malheiro, and R. P. Paiva. Novel audio features for
music emotion recognition.IEEE Transactions on Affective Computing,
11(4):614–626, 2018.
[40] P.-T. Pham, M.-H. Huynh, H.-D. Nguyen, and M.-T. Tran. Selab-hcmus
at mediaeval 2021: Music theme and emotion classification with co-
teaching training strategy. InMediaEval, 2021.
[41] J. Qiu, C. Chen, and T. Zhang. A novel multi-task learning method for
symbolic music emotion recognition.arXiv:2201.05782, 2022.
[42] C. Raffel, B. McFee, E. J. Humphrey, J. Salamon, O. Nieto, D. Liang,
D. P. Ellis, and C. C. Raffel. Mir eval: A transparent implementation
of common mir metrics. InISMIR, volume 10, page 2014, 2014.
[43] S. Rajesh and N. Nalini. Musical instrument emotion recognition using
deep recurrent neural network.Procedia Comput. Sci., 167:16–25, 2020.
[44] J. A. Russell. A circumplex model of affect.Journal of personality and
social psychology, 39(6):1161, 1980.
[45] S. Shelke and M. Patil. Exploring machine learning techniques for music
emotion classification: A comprehensive review. In2024 11th Int. Conf.
on Computing for Sustainable Global Development (INDIACom), pages
1188–1195. IEEE, 2024.
[46] M. Soleymani, M. N. Caro, E. M. Schmidt, C.-Y . Sha, and Y .-H. Yang.
1000 songs for emotional analysis of music. InProc. of the 2nd ACM
Int. workshop on Crowdsourcing for multimedia, pages 1–6, 2013.
[47] S. A. Suresh Kumar and R. Rajan. Transformer-based automatic music
mood classification using multi-modal framework.Journal of Computer
Science & Technology, 23, 2023.
[48] H. H. Tan. Semi-supervised music emotion recognition using noisy
student training and harmonic pitch class profiles.arXiv:2112.00702,
2021.
[49] G. Tong. Multimodal music emotion recognition method based on the
combination of knowledge distillation and transfer learning.Scientific
Programming, 2022(1):2802573, 2022.
[50] P. Tovstogan, D. Bogdanov, and A. Porter. Mediaeval 2021: Emotion
and theme recognition in music using jamendo. InMediaEval, 2021.
[51] H. Tran, T. Le, A. Do, T. Vu, S. Bogaerts, and B. Howard. Emotion-
aware music recommendation. InProc. of the AAAI Conf. on Artificial
Intelligence, volume 37, pages 16087–16095, 2023.
[52] D. Turnbull, L. Barrington, D. Torres, and G. Lanckriet. Towards musical
query-by-semantic-description using the cal500 data set. InProc. of the
30th annual Int. ACM SIGIR Conf. on Research and development in
information retrieval, pages 439–446, 2007.
[53] S.-Y . Wang, J.-C. Wang, Y .-H. Yang, and H.-M. Wang. Towards time-
varying music auto-tagging based on cal500 expansion. In2014 IEEE
Int. Conf. on Multimedia and Expo (ICME), pages 1–6. IEEE, 2014.
[54] L. Yizhi, R. Yuan, G. Zhang, Y . Ma, X. Chen, H. Yin, C. Xiao, C. Lin,
A. Ragni, E. Benetos, et al. Mert: Acoustic music understanding model
with large-scale self-supervised training. InThe Twelfth International
Conference on Learning Representations, 2023.
[55] K. Zhang, H. Zhang, S. Li, C. Yang, and L. Sun. The pmemo dataset
for music emotion recognition. InProc. of the 2018 acm on Int. Conf.
on multimedia retrieval, pages 135–142, 2018.