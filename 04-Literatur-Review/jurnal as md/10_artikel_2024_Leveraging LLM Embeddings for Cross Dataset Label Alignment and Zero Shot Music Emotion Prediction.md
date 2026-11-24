LEVERAGING LLM EMBEDDINGS FOR CROSS DATASET
LABEL ALIGNMENT AND ZERO SHOT MUSIC EMOTION
PREDICTION
Liu Renhang, Abhinaba Roy, Dorien Herremans
Singapore University of Technology and Design
ABSTRACT
arXiv:2410.11522v2  [cs.SD]  17 Oct 2024
In this work, we present a novel method for music emotion recognition that lever
ages Large Language Model (LLM) embeddings for label alignment across multi
ple datasets and zero-shot prediction on novel categories. First, we compute LLM
embeddings for emotion labels and apply non-parametric clustering to group sim
ilar labels, across multiple datasets containing disjoint labels. We use these cluster
centers to map music features (MERT) to the LLM embedding space. To further
enhance the model, we introduce an alignment regularization that enables disso
ciation of MERT embeddings from different clusters. This further enhances the
model’s ability to better adaptation to unseen datasets. We demonstrate the ef
fectiveness of our approach by performing zero-shot inference on a new dataset,
showcasing its ability to generalize to unseen labels without additional training.
1 INTRODUCTION
The task of automatic music emotion recognition has been a long-standing challenge in the field of
music information retrieval (Yang & Chen, 2012; Kim et al., 2010; Kang & Herremans, 2024). Ac
curately predicting the emotional impact of music has numerous valuable applications, ranging from
enhancing music streaming recommendations to providing more effective tools for music therapists.
By understanding the emotional responses evoked by music, we can improve the user experience
of music listening platforms, tailoring recommendations to individual preferences and emotional
needs. Furthermore, this knowledge can benefit music therapists, enabling them to select and apply
music more effectively in their treatments, ultimately leading to better outcomes for their patients
(Agres et al., 2021).
The predominant approach in this field has been to model emotions using Russell’s two dimensional
valence-arousal space (Russell, 1980). However, this representation fails to be interpreted by hu
man (Eerola & Vuoskoski, 2011). to address this limitation, researchers have explored the use of
comprehensive categorical emotional models, such as the Geneva Emotional Music Scale (Aljanaki
et al., 2014), which encompasses a broad range of discrete emotional attributes. More recent datasets
(Bogdanov et al., 2019; Turnbull et al., 2007) introduce new label categories, sometimes in the form
of free tags, that aim to capture the multifaceted nature of human emotions. Nonetheless, a key
challenge in this area is the lack of a unified emotional taxonomy. Different datasets often employ
disparate and often incompatible sets of emotional labels, posing a significant obstacle. The hetero
geneity of emotion label taxonomies across datasets hinders the ability to effectively compare and
combine findings across studies. This impedes our comprehensive understanding of the nuanced
emotional responses to music. The challenge of aligning these disparate emotion label taxonomies
limits our capacity to develop more comprehensive and robust music emotion recognition models.
Traditionally, the majority of studies have focused on training and testing with a single dataset.
However, recent advances in large language models have resulted in powerful general-purpose text
encoders (Reimers, 2019) that can be leveraged to effectively align emotions across diverse datasets.
The ability to align emotion labels across disparate datasets is a crucial step towards developing more
comprehensive and robust music emotion recognition models that can generalise to a wider range of
emotional experiences.
In this work, we present a novel methodology that leverages the powerful representational capabil
ities of Large Language Model embeddings to enable effective cross-dataset label alignment and
1
facilitate zero-shot inference on new datasets with previously unseen emotion labels. The core of
our approach involves computing LLM embeddings for the emotion labels across multiple datasets,
and then applying non-parametric clustering to group semantically similar labels together. These
cluster centres serve as anchor points that allow us to map the MERT features (Li et al., 2023)
extracted from music wav files into a common label embedding space, effectively aligning the dis
parate emotion taxonomies present across datasets. To further enhance the model’s performance and
ensure it captures the underlying semantic relationships between emotions beyond training data, we
introduce an alignment regularization. This regularization encourages music features from differ
clusters in the label embedding space to dissociate from each other. This, in turn help the model
to generalize better to unseen data and labels. To evaluate the efficacy of our proposed approach,
we conduct extensive experiments on three benchmark datasets for music emotion recognition. The
results demonstrate substantial improvements in the model’s ability to perform zero-shot prediction
on a new dataset containing previously unseen emotion labels, showcasing the strong generalization
capabilities of our method. This is a crucial step towards developing more robust and comprehen
sive music emotion recognition models that can be applied to a wider range of emotional experiences
beyond the singular datasets used during training.
To sum up, the key contributions of this work are:
• This work is the first to leverage the capabilities of Large Language Model embeddings
to enable robust cross-dataset label alignment for the domain of music emotion recogni
tion. By computing LLM embeddings for emotion labels across datasets and applying
non-parametric clustering, we are able to establish a common embedding space that allows
us to align disparate emotion taxonomies.
• We introduce an alignment regularization that further enhances the model’s ability to dis
sociate music features from distinct emotions.
• Wedemonstrate the ability of our approach to perform zero-shot inference on new datasets
with previously unseen emotion labels. This showcases the model’s strong generalization
capabilities and its potential to be applied to a wider range of emotional experiences.
The rest of the paper is organized as follows. Related works in music emotion recognition and cross
dataset transfer learning are discussed in Section 2. We describe our proposed label alignment and
emotion prediction framework in detail in Section 3. Section 4 elaborates on our experimental setup,
followed by a comprehensive discussion of the results. Finally we conclude the paper and outline
future research directions in Section 5.
2 RELATED WORK
The connection between music and emotions has long been a subject of study, dating back to
(Leonard, 1956) and (Hevner, 1935), who explored how different musical elements evoke specific
emotional responses. Over the decades, various frameworks have been proposed to represent emo
tions in music, ranging from categorical models (e.g., happy, sad, angry) to continuous dimensions
like valence and arousal. Valence-arousal models (Russell, 1980) and more sophisticated systems
such as the Geneva Emotional Music Scale (Zentner et al., 2008) have become prominent in recent
studies of music emotion recognition (MER).
Despite these advancements, current models often struggle to achieve robust generalization, par
ticularly across diverse datasets. Existing approaches have attempted to improve performance by
incorporating advanced encoders like MERT (Li et al., 2023), leveraging multi-modal data (e.g.,
lyrics, MIDI, or video), or introducing personalized models that adapt to listener-specific responses
(Chua et al., 2022; Koh et al., 2022; Sams & Zahra, 2023). However, these methods primarily ex
plore single dataset approach, i.e., training and testing done on a single dataset. Compared to other
fields, such as image recognition or natural language processing, datasets for MER are considerably
smaller and more fragmented, making it difficult to develop models that generalize across genres
and emotional taxonomies. Datasets such as MTG-Jamendo (Bogdanov et al., 2019), and smaller,
domain-specific collections like CAL500 (Turnbull et al., 2007) and Emotify (Aljanaki et al., 2016)
all use different emotion representation models, focus on distinct musical genres, and are thus of
ten incompatible. This discrepancy in representation and dataset size presents a major challenge
to building robust models that can generalize across various emotion taxonomies. Addressing this
2
Figure 1: Overview of our approach.
limitation requires innovative solutions that can overcome the dataset heterogeneity. One promising
direction is zero-shot learning, which has shown success in fields such as computer vision (Xian
et al., 2018) and natural language processing (Brown, 2020). Zero-shot learning models generalize
to novel classes or tasks without requiring direct training data for every label. In the context of
music emotion recognition, zero-shot learning enables models to predict emotions in datasets with
unseen labels or emotion taxonomies, potentially overcoming the generalization bottleneck caused
by small, disjoint datasets. Our work builds on these ideas by introducing a novel approach for emo
tion prediction across music datasets with disjoint label sets. By leveraging large language models
(LLMs) to align emotion labels through semantic embeddings and clustering, we bridge the gap be
tween datasets, enabling cross-dataset generalization and zero-shot performance. The next section
provides details of the building blocks of our approach.
3 PRESENT WORK
Our approach leverages the power of Large Language Model (LLM) embeddings to align emotion
labels across multiple music emotion datasets and to enable zero-shot inference on previously unseen
emotion labels. An overview is shown in Figure 1. This section describes the key components of our
methodology, including the label embedding procedure, non-parametric clustering, and the mapping
of MERT features (i.e., encoded audio) (Li et al., 2023) to the label embedding space.
3.1 EMOTION LABEL EMBEDDING
For each dataset, we obtain an embedding for each emotion label using a pre-trained LLM. Let
Ld = {l1,l2,...,lnd
} represent the set of emotion labels in dataset d, where nd is the number
of labels in dataset d. We compute an embedding for each label li ∈ Ld using the LLM, which
produces a vector representation eli 
∈ Rm, where m is the dimension of the LLM’s embedding
space:
eli 
= LLM(li)
This embedding process is performed independently for each dataset. The advantage of using
LLM embeddings is that the pre-trained model captures rich semantic relationships between words
(emotion labels), which allows for natural grouping of labels even when they differ slightly across
datasets. For example, the labels “happy” and “joyful” are likely to have similar embeddings despite
being distinct.
3
3.2 CLUSTERING OF EMOTION EMBEDDINGS
Once we have the LLM embeddings for the emotion labels from multiple datasets, the next step
is to group semantically similar labels. Instead of relying on a predefined number of clusters, we
utilize the Mean Shift clustering algorithm (Cheng, 1995), a non-parametric clustering technique
that automatically determines the number of clusters based on the density of points in the embedding
space.
Let E = {eli
}N
i=1 represent the set of all emotion label embeddings, where N is the total number of
unique labels across all datasets. The Mean Shift algorithm identifies clusters by shifting each point
towards the mode (the densest region of points) iteratively.
The algorithm converges when the embedding positions no longer change significantly, resulting in
a set of cluster centers C = {c1,c2,...,cK}.
3.3 MAPPING MERT FEATURES TO THE LABEL EMBEDDING SPACE
Features extracted with the Music undERstanding model with large-scale self-supervised Training
(MERT) (Li et al., 2023) have shown to achieve state-of-the-art performance in various music un
derstanding tasks. MERT features can be seen as a highly expressive and generalizable feature
representation for music. We leverage these MERT features as the input representation for music
emotion recognition. These features, however, do not directly correspond to the semantic mean
ing of emotion labels. To bridge this gap, we propose a mapping from the MERT feature space to
the LLM emotion embedding space. We employ an attention-based mechanism to map the MERT
features into the label embedding space wherein the emotion label embeddings reside. The model
ingests MERT features extracted from music and outputs corresponding embeddings that are aligned
with the LLM-generated emotion label embeddings. Let xi ∈ Rd be the MERT feature matrix for
the i-th music sample, where d is the feature dimension. The model uses self-attention mechanisms
to process this input, applying two encoder layers and projecting it into the label embedding space.
The model can be mathematically described as follows:
3.3.1 INPUT PROJECTION
We select the 3rd, 6th, 9th, and 12th layers from MERT and concatenate them to linearly
project to a vector of dimension dmodel:
zi = Linearproj Concat(x(3)
i ,x(6)
i ,x(9)
3.3.2 SELF-ATTENTION
i ,x(12)
i
) , zi∈Rdmodel
The projected vector zi is passed through multiple self-attention layers, where each layer applies
multi-head attention followed by a feedforward neural network and layer normalization. The output
of the l-th attention block is:
a(l+1)
i
where a(0)
i
=zi.
=LayerNorm SelfAttention a(l)
i
3.3.3 OUTPUT PROJECTION
+a(l)
i
,
l = 1,2,...,L
The final output from the last attention block is linearly projected to the output size m, where m is
the dimension of the shared LLM embedding space:
fθ(xi) = Linearoutput(a(L)
i
)
Thus, fθ(xi) ∈ Rm represents the projected embedding of the MERT features into the shared emo
tion label embedding space.
3.3.4 ALIGNMENT LOSS
Tofacilitate alignment, we employ a triplet loss based alignment loss that ensures the model learns to
bring MERT embeddings closer to the LLM embeddings of their true emotion labels, while pushing
them apart from embeddings of incorrect emotion categories. In this formulation:
4
• Theanchor fθ(xi) represents the MERT feature of the audio sample xi passed through the
model.
• The positive eLLM(yi) is the LLM embedding of the true label yi for the sample.
• The negative eLLM(yk) is the LLM embedding of an incorrect or different emotion label
yk (where yk ̸ = yi).
The triplet loss is defined based on cosine similarity:
Lalign = 1
N 
N
i=1
Where:
max(0,cos(fθ(xi),eLLM(yi)) − cos(fθ(xi),eLLM(yk)) + margin)
• cos(a,b) is the cosine similarity between vectors a and b,
• margin is a hyperparameter that defines the minimum desired separation between positive
and negative pairs,
• fθ(xi) is the model output for the MERT feature xi,
• eLLM(yi) and eLLM(yk) are the LLM embeddings for the true and incorrect labels, respec
tively.
This loss function encourages the model to map MERT features closer to their corresponding emo
tion label embeddings in the label embedding space while ensuring that they are distinct from em
beddings of incorrect labels.Ultimately, this mapping procedure allows us to project music repre
sentations into the same semantic space as the emotion labels, facilitating more meaningful and
interpretable emotion recognition. By aligning the music features and emotion labels in a label em
bedding space, we can better capture the nuanced relationships between musical characteristics and
emotional responses.
3.4 ALIGNMENT REGULARIZATION
To further improve the alignment between the MERT feature representations and the emotion la
bel embeddings, we introduce an alignment regularization term. This regularization encourages the
model to map MERT features with semantically similar emotion labels to nearby positions in the
label embedding space. By minimizing the distance between the embeddings of MERT features cor
responding to the same or closely related emotion labels, the model is incentivised to position these
representations in close proximity within the label embedding space. The alignment regularization
is formulated as follows:
Let Ck represent the set of samples in cluster k, and xi ∈ Ckl
, xj ∈ Ckm 
be two MERT feature
vectors whose corresponding emotion labels belong to the different clusters, i.e., Ckl
̸ = Ckm
. The
alignment regularization term maximizes the distance between their embeddings fθ(xi) and fθ(xj)
in the label embedding space. We define the alignment regularization loss as:
Lreg = 1
K (xi,xj)
1 − D(fθ(xi),fθ(xj))
Where:
• fθ(xi) and fθ(xj) are the model outputs for the MERT features xi and xj,
• Drepresents the cosine distance,
• The sum is taken over all xi ∈ Ckl
, xj ∈ Ckm 
such that Ckl
̸ = Ckm
. K is the number of
such pairs present in the dataset.
By minimizing Lalign, the model encourages MERT features from different labels to dissociate fur
ther with each other. The final objective function combines the alignment loss and the regularization
term, with a hyperparameter λ controlling the trade-off between these two components:
L =Lalign +λLreg
5
The network is trained to minimize L and we posit this regularization helps the model to generalise
to unseen emotion labels and enables it to perform zero shot classification on new datasets. To test
this, we set up the following zero shot evaluation scenario described in the next subsection.
3.5 ZERO SHOT CLASSIFICATION
We perform zero-shot inference on a new dataset containing disjoint set of labels, some of which
can be previously unseen. Given a new emotion label lnew, we compute its embedding elnew 
using
the LLM:
elnew 
= LLM(lnew)
To predict the top k emotions for a given music sample, we project the MERT features of the sample
into the LLM embedding space using the trained network fθ. The predicted emotions ˆy is given by
the following equation:
ˆ
y = argmink
i
D(fθ(x),yi)
Where (D) is the cosine distance, k is number of top predictions to select. In our experiments we
fix k to 2/3/4 depending on dataset.
In the next section, we detail our empirical setup and demonstrate the effectiveness of our approach.
4 EXPERIMENTS AND RESULTS
To demonstrate the efficacy of our approach, we evaluate on three distinct emotion recognition
datasets. The first subsection provides a concise overview of the datasets. This is then followed by
the experimental setup, and finally, we present the results accompanied by a discussion.
4.1 DATASETS
For the purpose of evaluating our music emotion recognition approach, we have selected three
prominent datasets in this research domain: the MTG-Jamendo Dataset (Bogdanov et al., 2019),
the Computer Audition Lab 500 dataset (Turnbull et al., 2007), and the the Emotify Dataset (Al
janaki et al., 2016).
The MTG-Jamendo dataset is an openly available resource for the task of automatic music tag
ging. It was constructed using music content hosted on the Jamendo platform, which is licensed
under Creative Commons, and incorporating tags provided by the content contributors. This dataset
encompasses a vast collection of over 55,000 full-length audio recordings annotated with 56 relevant
emotion tags.
The Computer Audition Lab 500 (CAL500) dataset is a widely utilised dataset in music emotion
recognition research. It consists of 500 popular Western songs, each annotated with a standard set
of 17 emotion labels by at least 3 human annotators.
Lastly, the Emotify dataset is another prominent open dataset for music emotion recognition. It
contains 400 music excerpts annotated with 9 emotional categories of the Geneva Emotional Music
Scale model, obtained through a crowdsourcing game.
Both the CAL500 and Emotify datasets feature annotations from multiple users. For the CAL500
dataset, we consider a label as true if its average score is greater than 3 on a scale of 1 to 5. In case
none of the emotion score is greater than 3, we select the highest scored emotion. For the Emotify
dataset, we fix the selection process by choosing the top 3 rated labels as the true labels. These
processed labels are made available online to allow future benchmarking with our work1. It is worth
noting that the MTG-Jamendo dataset already incorporates multiple emotion tags, and thus all our
datasets are inherently multi-label in nature. Table 1 contains a brief overview of all the datasets.
1https://github.com/AMAAI-Lab/cross-dataset-emotion-alignment
6
Dataset
Number
of labels
MTG-Jamendo
56
Number of
training data
Number of
test data
Average
duration(s)
9949
3801
216.4
CAL500 17 400 100 186.5
Emotify
9
320
80
59.7
Table 1: Brief overview of the datasets
4.2 EXPERIMENTAL SETUP
For our experimental setup, we employ the standard train-test split as recommended by the original
authors of the datasets. For the MERT feature extraction, we split the songs in 10 second segments
and we utilise the widely-used MERT-v1-95M model available on Hugging Face2. Regarding the
LLM embeddings, we select Sentence Transformers (Reimers, 2019), given the multi-label nature
of all three datasets. Specifically, we use the all-MiniLM-L6-v2 model3, which has been fine-tuned
on 1 billion sentence pairs from a pre-trained MiniLM-L6-H384-uncased model. We leverage the
Hugging Face implementation for this approach. The MERT features for each 10s fragment are
averaged and fed into a shallow two-layered attention network to project these MERT features to the
LLM embedding space. We implement Mean Shift Clustering (Fukunaga & Hostetler, 1975) using
the scikit-learn library. The k parameter to obtain the actual labels ˆy is set to the average number
of labels per instance in the dataset: 2 for Jamendo MTG, 4 for CAL500, and 3 for Emotify. For
all the training processes, we ran for 100 epochs with a batch size of 256, utilising the AdamW
optimiser. The base learning rate is fixed to 2e−4 with a ReduceLROnPlateau scheduler monitoring
the validation macro F1 score and a minimum learning rate threshold of 1.6e−7. All models are
trained on 4 NVIDIA Tesla V100 DGXS 32 GB GPUs, and the training and evaluation code is
implemented using PyTorch and available online4.
4.3 BASELINES
Our experimental evaluation comprises three distinct phases, each designed to systematically assess
the efficacy of our approach for cross-dataset generalization and zero-shot inference. We propose
two baselines and finally, an alignment regularization approach:
Baseline 1- Single Dataset Training: The first baseline experiment assesses the model’s per
formance when trained solely on a single dataset. The evaluation is on the test set of the same
dataset to gauge in-domain performance, as well as the test sets of the other two datasets to measure
cross-dataset generalization. This baseline shows how well the models can generalise across diverse
datasets without any external label alignment or regularization.
Baseline 2- Clustering of LLM Embeddings: In the second baseline experiment, we exploit
alignment of emotion labels by clustering the label embeddings generated by a Large Language
Model across two datasets (see Section 3.2). These clusters capture semantically akin emotions.
The model is then trained on this aligned label space, wherein the target emotion is inferred from the
cluster centroids of the LLM embeddings instead of individual labels. This approach leverages the
presence of common emotion clusters, thereby enhancing the model’s capacity for generalisation
across datasets. In this case, the model is trained on two datasets conjointly and evaluated on the
test sets of all three datasets.
Alignment Regularization: We build upon the second baseline by incorporating alignment reg
ularization as described in Section 3.4. This regularization technique encourages MERT feature
embeddings of semantically similar emotion labels to be mapped to proximate positions within the
shared embedding space. This phase aims to refine the model’s capacity for generalization to unseen
labels and assess the model’s zero-shot performance on new dataset with disjoint sets of labels.
2https://huggingface.co/m-a-p/MERT-v1-95M
3https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2
4https://github.com/AMAAI-Lab/cross-dataset-emotion-alignment
7
Figure 2: Graph of labels taken from CAL500 and Emotify. Nodes with same color belong to the
same cluster. Labels (nodes) from the same cluster are shown connected by an edge. Spatial distance
here is irrelevent.
4.4 RESULTS
This section provides a detailed analysis of our results. The evaluation is structured to assess the
model’s capacity for generalisation from single-dataset training, the enhancement achieved through
label clustering utilising LLM embeddings, and the final improvement attained via alignment regu
larization.
Baseline 1: The first set of experiments evaluates the model’s performance when trained solely on a
single dataset. Table 2 presents the results, showcasing strong in-domain performance with macro F1
scores of 0.078, 0.380 and 0.448 for MTG-Jamendo, CAL500 and Emotify respectively. The large
difference in F1 scores between datasets is partly due to a different number of classes: 56, 17, and
9 respectively. The cross-dataset generalization remains a significant challenge, with performance
drops of over 50 percent when evaluating on the test sets of other datasets. For example, MTG
Jamendo performance drops from 0.078 to 0.0202 when the training dataset switches to CAL500.
The results show that the model’s performance declines when evaluated on unseen datasets. This
highlights the challenge of training a model solely on a limited set of labels and attempting direct
cross-dataset inference without any form of alignment or adaptation.
Tested on
Trained on MTG-Jamendo CAL500 Emotify
MTG-Jamendo
0.105
0.346
CAL500 0.0175 0.291 0.368
Emotify
0.233
0.0193
0.267
0.421
Table 2: Macro F1 scores for baseline 1- single dataset training.
Baseline 2: In the second baseline, we introduce LLM-based clustering of emotion labels across
two datasets. The model is trained on two datasets together, with the emotion labels clustered based
on the semantic similarity of their LLM embeddings. Compared to the first baseline, this approach
leads to new best individual performance improvements for all datasets. For example, the best macro
8
F1 score on the Emotify dataset increases from 0.4483 to 0.5037 when we combine CAL500 and
Emotify through this label alignment technique. We posit this improvement is due to the model’s
enhanced ability to capture the underlying semantic relationships between emotion labels across the
different datasets. Figure 2 plots all the labels from all datasets. A quick inspection of clusters
reveals that semantically akin emotion labels are indeed grouped together. Detailed results can be
seen in Table 3.
Tested on
Trained on MTG-Jamendo CAL500 Emotify
MTG-Jamendo + CAL500
0.123
0.330
CAL500 + Emotify 0.0174 0.287 0.500
Emotify + MTG-Jamendo
0.387
0.103
0.222
0.420
Table 3: Macro F1 scores for baseline 2- clustering of LLM embedings.
Alignment regularization: The final baseline incorporates alignment regularization to further en
hance the model’s cross-dataset and zero-shot capabilities. By regularizing the MERT feature em
beddings of dissimilar examples based on their label embeddings, the model is encouraged to in
crease the separation between examples of dissimilar emotion labels. This aims to refine the model’s
ability to distinguish between distinct emotion categories, even when encountering previously un
seen labels. Table 4 presents the detailed results for this phase. We observe that the cross-dataset
performance is reduced when compared to Baseline 2. For example, Emotify macro F1 score re
duces from 0.5037 to 0.4551 when trained on CAL500 and Emotify combination (row 2, column 3
in Table 3 vs Table 4). This is because the regularization term accentuates the dissociation of dis
similar emotion labels during training, which in turn diminishes the model’s interpolation capacity
between known labels. However, the model’s zero-shot performance on the new dataset improves
significantly, with the F1 score increasing by 15-20% compared to the previous baselines. Specifi
cally, the zero-shot F1 score on the Emotify dataset increased to 0.4022 from 0.3411 in Baseline 2.
Detailed comparisons across different splits are shown in Table 5. These results demonstrate that
the alignment regularisation substantially enhances the model’s ability to generalise in zero-shot
scenarios, where it must effectively handle completely novel emotion labels.
Tested on
Trained on MTG-Jamendo CAL500 Emotify
MTG-Jamendo + CAL500
0.103
0.400
CAL500 + Emotify 0.0202 0.272 0.425
Emotify + MTG-Jamendo
0.320
0.105
0.229
0.379
Table 4: Macro F1 scores for alignment regularization.
Split
Phases
T
Baseline 1
rain-MTG+CAL
Test-EMO
0.315
Train-CAL+EMO
Test-MTG
Train-EMO+MTG
Test-CAL
0.0129
0.252
Baseline 2
Alignment Regularisation
0.346
0.0175
0.400 (λ = 2.5)
0.267
0.0202 (λ = 2.5)
0.229 (λ = 1)
Table 5: Macro F1 scores for zero shot inference. We indicate the empirically determined best
λ values (Section 3.4) for each split in alignment regularization. Legend: MTG: MTG-Jamendo;
CAL: CAL500; EMO: Emotify.
Choice of regularization: We validate the choice of regularizer in the following way: Instead
of regularizing on the pair of examples from disjoint clusters (as described in Section 3.4), we
regularize on the positive examples. In that, we tweak Lreg such that in the new formulation, we
minimize the distance between elements in the same cluster. i.e., xi,xj ∈ Ck. K′ is the number of
9
such positive pairs.
Lreg’ = 1
K′
(xi,xj)
D(fθ(xi),fθ(xj))
We carry out small scale experiment using segment level evaluation. By training on a combination
of Jamendo-MTG + CAL500, we observe that the formulation in Section 3.4, i.e., negative pair
based regularization, outperforms positive pair-based formulation by a considerable margin. Results
in Table 6. Based on this, we decided to use negative pair based formulation for all our experiment.
Tested on
Regulizer MTG-Jamendo CAL500 Emotify
Positive
0.0402
Negative
0.206
0.246
0.0761 0.320 0.402
Table 6: Comparison of positive and negative formulation of alignment regularization. Train only
on MTG-Jamendo+CAL500.
Discussion: Our findings show that combining the Jamendo-MTG dataset with others consistently
enhanced Jamendo-MTG’s performance in Baseline 2. However, this improvement was not ob
served across the other datasets. For instance, when integrating Emotify with Jamendo-MTG, Emo
tify’s performance in Baseline 2 declined in comparison to Baseline 1 (0.448 vs 0.419). This can
be attributed to Jamendo being a more extensive dataset with greater diversity in data and emotion
labels, while Emotify is smaller and focuses on a specific kind of music. Incorporating Jamendo
MTG diluted Emotify’s performance by introducing music of genres that was less representative
of Emotify’s concentrated content consisting of a specific genre. Conversely, adding Emotify to
Jamendo-MTG introduced focused data that enhanced Jamendo-MTG’s performance on that genre.
When merging datasets, we should also be mindful of variations in music emotion datasets and the
resulting challenges as outlined by Kang & Herremans (2024). For instance, the added dataset may
contain noisier data, due to cloud annotation instead of expert annotation. It may contain different
genres of music or fragments of different length. There may also be many labels per instance, versus
only one. Our proposed framework can handle data of all these variations, however, the user should
be mindful to focus on high-quality data with similar distribution to the desired target music, in order
achieve a quality improvement in the model.
Our results suggest that when aiming to improve a dataset’s performance, it is advantageous to
augment it with another dataset that may be smaller but contains music of the same character present
in the original dataset. In such cases, Baseline 2 serves as an effective strategy to enhance the
performance of the larger, more diverse dataset.
Furthermore, for tasks requiring zero-shot learning, alignment regularization proves to be more
effective. However, when all data and labels are available, Baseline 2 should be preferred, as it tends
to yield better results, particularly for larger datasets like Jamendo-MTG, as described earlier.
5 CONCLUSION
In this paper, we introduce a novel approach to music emotion recognition by integrating Large
Language Model (LLM) embeddings to harmonize label spaces across diverse datasets, and enable
zero-shot learning for new emotion categories. Our method not only effectively clusters and aligns
emotion labels through LLM embeddings but also employs a novel alignment regularization, en
hancing the semantic coherence between music features and emotion labels across disjoint datasets.
The experimental results show zero shot performance of 0.402, 0248, 0.262 in terms of macro F1
score for Emotify, MTG-Jamendo, and CAL500 respectively, setting a new benchmark in the field
of music emotion recognition. This approach opens up possibilities for broader applications in af
fective computing where emotional nuances can be universally understood and processed across
contextual bounds.
10
REFERENCES
Kat R Agres, Rebecca S Schaefer, Anja Volk, Susan van Hooren, Andre Holzapfel, Simone
Dalla Bella, Meinard M¨ uller, Martina De Witte, Dorien Herremans, Rafael Ramirez Melendez,
et al. Music, computing, and health: a roadmap for the current and future roles of music technol
ogy for health care and well-being. Music & Science, 4:2059204321997709, 2021.
Anna Aljanaki, Frans Wiering, Remco Veltkamp, et al. Computational modeling of induced emo
tion using gems. In Proceedings of the 15th Conference of the International Society for Music
Information Retrieval (ISMIR 2014), pp. 373–378, 2014.
AnnaAljanaki, Frans Wiering, and RemcoCVeltkamp. Studyingemotioninducedbymusicthrough
a crowdsourcing game. Information Processing & Management, 52(1):115–128, 2016.
Dmitry Bogdanov, MinzWon,PhilipTovstogan, AlastairPorter, and Xavier Serra. The mtg-jamendo
dataset for automatic music tagging. ICML, 2019.
Tom B Brown. Language models are few-shot learners. arXiv preprint arXiv:2005.14165, 2020.
Yizong Cheng. Mean shift, mode seeking, and clustering. IEEE transactions on pattern analysis
and machine intelligence, 17(8):790–799, 1995.
Phoebe Chua, Dimos Makris, Dorien Herremans, Gemma Roig, and Kat Agres. Predicting emo
tion from music videos: exploring the relative contribution of visual and auditory information to
affective responses. arXiv:2202.10453, 2022.
Tuomas Eerola and Jonna K Vuoskoski. A comparison of the discrete and dimensional models of
emotion in music. Psychology of Music, 39(1):18–49, 2011.
Keinosuke Fukunaga and Larry Hostetler. The estimation of the gradient of a density function, with
applications in pattern recognition. IEEE Transactions on information theory, 21(1):32–40, 1975.
Kate Hevner. The affective character of the major and minor modes in music. The American Journal
of Psychology, 47(1):103–118, 1935.
Jaeyong Kang and Dorien Herremans. Are we there yet? a brief survey of music emotion prediction
datasets, models and outstanding challenges. arXiv preprint arXiv:2406.08809, 2024.
Youngmoo E Kim, Erik M Schmidt, Raymond Migneco, Brandon G Morton, Patrick Richardson,
Jeffrey Scott, Jacquelin A Speck, and Douglas Turnbull. Music emotion recognition: A state of
the art review. In Proc. ismir, volume 86, pp. 937–952, 2010.
En Yan Koh, Kin Wai Cheuk, Kwan Yee Heung, Kat R Agres, and Dorien Herremans. Merp: a
music dataset with emotion ratings and raters’ profile information. Sensors, 23(1):382, 2022.
Meyer Leonard. Emotion and meaning in music. Chicago: University of Chicago, 1956.
Yizhi Li, Ruibin Yuan, Ge Zhang, Yinghao Ma, Xingran Chen, Hanzhi Yin, Chenghao Xiao,
Chenghua Lin, Anton Ragni, Emmanouil Benetos, et al. Mert: Acoustic music understanding
model with large-scale self-supervised training. arXiv preprint arXiv:2306.00107, 2023.
N Reimers. Sentence-bert: Sentence embeddings using siamese bert-networks. arXiv preprint
arXiv:1908.10084, 2019.
James A Russell. A circumplex model of affect. Journal of personality and social psychology, 39
(6):1161, 1980.
Andrew Steven Sams and AmaliaZahra. Multimodalmusicemotionrecognitioninindonesiansongs
based on cnn-lstm, xlnet transformers. Bulletin of Electrical Engineering and Informatics, 12(1):
355–364, 2023.
Douglas Turnbull, Luke Barrington, David Torres, and Gert Lanckriet. Towards musical query-by
semantic-description using the cal500 data set. In Proc. of the 30th annual Int. ACM SIGIR Conf.
on Research and development in information retrieval, pp. 439–446, 2007.
11
Yongqin Xian, Tobias Lorenz, Bernt Schiele, and Zeynep Akata. Feature generating networks for
zero-shot learning. In Proceedings of the IEEE conference on computer vision and pattern recog
nition, pp. 5542–5551, 2018.
Yi-Hsuan Yang and Homer H Chen. Machine recognition of music emotion: A review. ACM
Transactions on Intelligent Systems and Technology (TIST), 3(3):1–30, 2012.
Marcel Zentner, Didier Grandjean, and Klaus R Scherer. Emotions evoked by the sound of music:
characterization, classification, and measurement. Emotion, 8(4):494, 2008.
12