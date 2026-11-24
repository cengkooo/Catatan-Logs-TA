PDF Download
3796518.pdf
10 February 2026
Total Citations: 0
Total Downloads: 0
.
.
Latest updates: hps://dl.acm.org/doi/10.1145/3796518
.
.
SURVEY
A Meta-Analysis of Music Emotion Recognition Studies
.
.
Accepted: 03 February 2026
Revised: 26 December 2025
Received: 15 April 2025
.
.
Citation in BibTeX format
.
.
ACM Computing Surveys
hps://doi.org/10.1145/3796518
EISSN: 1557-7341
.
AMeta-Analysis of Music Emotion Recognition Studies
TUOMASEEROLA, Music,DurhamUniversity, Durham, United Kingdom of Great Britain and Northern
Ireland
CAMERONANDERSON, DepartmentofPsychology, Neuroscience & Behaviour, McMaster University,
Hamilton, Canada
This meta-analysis examines music emotion recognition (MER) models published between 2014 and 2024, focusing on
predictions of valence, arousal, and categorical emotions. A total of 553 studies were identiied, of which 96 full-text articles
were assessed, resulting in a inalreviewof34studies.Thesestudiesreported290models,including86foremotionclassiication
and 204 for regression. Using the best-performing model from each study, we found that valence and arousal were predicted
with reasonable accuracy (r = 0.67 and r = 0.81, respectively), while classiication models achieved an accuracy of 0.87 as
measured with Matthews correlation coeicient. Across modelling approaches, linear and tree-based methods generally
outperformed neural networks in regression tasks, whereas neural networks and support vector machines (SVMs) showed
highest performance in classiication tasks. We highlight key recommendations for future MER research, emphasizing the
need for greater transparency, feature validation, and standardized reporting to improve comparability across studies.
CCS Concepts: · Applied computing → Psychology; Sound and music computing; · Computing methodologies →
Model development and analysis.
Additional Key Words and Phrases: music, emotion, recognition, computational, meta-analysis
1 Introduction
Emotional engagement is a key reason why people engage with music in their everyday activities, and it is
also why music is increasingly being used in various health applications [2, 54]. In recent years, signiicant
advances have been made in music information retrieval (MIR), particularly in emotion prediction tasks [41, 79].
Music Emotion Recognition (MER) is an interdisciplinary ield that combines computer science, psychology, and
musicology to identify the emotions conveyed by music. Research in this area involves developing computational
models capable of recognizing emotions from musical content. The emotional attributions of music are based
on various theoretical frameworks for emotion and require annotated datasets to build and train these models.
Improvements to modelling techniques, datasets, and available features have created new opportunities to improve
the accuracy and reliability of MER systems developed to predict emotion labels or ratings in music using audio
features. Over the past 25 years, these studies have established the types of emotions that listeners perceive and
recognize in music. In the last 15 years, research has increasingly focused on tracing these recognized emotions
back to speciic musical components, such as expressive features [67], structural aspects of music [7, 29, 45],
acoustic features [28, 79, 80, 84, 106], or emergent properties revealed through deep learning techniques [33, 88].
Despite increasing interest in MER studies, there is no consensus on the degree to which emotions can be
accurately recognized by computational models. The current literature presents a diverse and mixed picture on
Authors’ Contact Information: Tuomas Eerola, Music, Durham University, Durham, United Kingdom of Great Britain and Northern Ireland;
e-mail: tuomas.eerola@durham.ac.uk; Cameron Anderson, Department of Psychology, Neuroscience & Behaviour, McMaster University,
Hamilton, Ontario, Canada; e-mail: andersoc@mcmaster.ca.
This work is licensed under a Creative Commons Attribution 4.0 International License.
© 2026 Copyright held by the owner/author(s).
ACM1557-7341/2026/2-ART
https://doi.org/10.1145/3796518
ACMComput. Surv.
2 • T.EerolaandC. Anderson
the success of models in predicting emotions within the afective circumplex, valence and arousal [105] and in
classifying distinct emotion categories [38].
1.1 A brief history of MER
Music’s capacity to convey emotions has been widely discussed since the earliest artiicial intelligence (AI)
applications were developed in the 1950s. Whereas early discourse largely focused on generative composition
using computers [110], attention later shifted to creating methods to predict emotion using music’s structural cues.
Novel techniques for information retrieval emerged in the 1950s and 1960s [35], inspiring analogous developments
for automated music analysis [56, 73]. These developments would set the stage for early work in MER. Katayose
conducted the irst study of this nature in the 1980s [57], creating an algorithm that associated emotions with
analyzed chords to generate descriptions like "there is [a] hopeful mood on chord[s] from 69 to 97." [57, p. 1087].
1.2 Classification and regression approaches
In the early 2000s, several research groups conducted studies using regression [37, 68] and classiication [36,
69, 71] techniques to predict emotion in music audio or MIDI. Citing "MIR researchers’ growing interest in
classifying music by moods" [26, p. 1], the Music Information Retrieval EXchange (MIREX) introduced Audio
Mood Classiication (AMC) to their rotation of tasks in 2007. In the irst year, nine systems classiied mood labels
in a common data set, reaching 52.65% in classiication accuracy (SD = 11.19%). These annual events, along with
the growing interest in the burgeoning ield of afective computing [82], would lead to an explosion of interest in
MERresearch.
In the tenth annual AMC task, the highest performing model reached 69.83% accuracy [81]. In parallel, research
groups began independently evaluating MER using regression algorithms. The irst study to popularize this
approach predicted valence (i.e., the negativeÐpositive emotional quality) and arousal (i.e., the calmÐexciting
quality) in 195 Chinese pop songs [106] using 114 audio-extracted features. Applying support vector regression,
the study achieved 58.3% accuracy in predicting arousal and 28.1% in predicting valence. This diference in
prediction accuracy between dimensions has reappeared in several subsequent studies [e.g., 8, 22], some research
suggesting that this challenge relects fewer well-established predictors and more individual diferences for
valence than arousal [28, 107].
Across regression and classiication paradigms, a wide range of models have been used, ranging from multiple
linear regression (MLR) [44, 85, 106] to deep neural networks [49, 77]. In classiication tasks, early studies
commonly employed Gaussian mixture models [68, 69] and support vector machines [66, 70, 96], whereas
convolutional, recurrent, and fully-connected neural networks have become increasingly popular in recent years
[23, 43, 92]. In regression tasks, a wide range of algorithms have been tested, including partial least squares (PLS)
[39, 98], support vector machines (SVMs) [1, 42, 52], random forests (RFs) [11, 101], and convolutional neural
networks [77].
1.3 Dataset size and scope
MER studies apply regression and classiication techniques to predict emotion in diverse datasets, using features
derived from both music (e.g., audio, MIDI, metadata) and participants (e.g., demographic information, survey
responses, physiological signals, etc.). To facilitate model comparison, several databases have been publicly
shared, including DEAM [4, 91] and AMG1608 [18]. These datasets predominately use Western pop music, are
moderate in size (containing 744 to 1802 music excerpts) and have been manually annotated by a variable number
of participants (either experts, students, or crowdsourced workers). Several publicly available datasets include
features analyzed using audio software suites such as OpenSMILE [34] and MIR Toolbox [63] ś enabling predictions
from tens or even hundreds of audio features.
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 3
Animportant factor often afecting the size of datasets employed in MER concerns whether they use a predictive
or explanatory modelling framework. Large datasets are necessary in predictive studies, where the predominant
goal is to generalize predictions across diverse samples, especially for deep learning and complex machine
learning models that require extensive pre-training. Conversely, small, carefully-curated datasets are useful
when attempting to explain how musical factors such as amplitude normalization [39] or diferent performers’
interpretations [10], afect variance in emotion ratings. In these studies, statistical models serve a diferent
purpose. Instead of predicting emotion labels for new music, psychological studies on music emotion test causal
theories about the relationship between musical predictors and emotion labels. Whether models serve predictive
or explanatory goals is importantÐafecting both data curation and modeling decisions, and the models’ resulting
predictive and explanatory power [90].
In predictive MER tasks, the size of the data set tends to be modest compared to other ields, as the direct
annotation of music examples is resource-intensive. For example, in the visual domain, datasets are often
signiicantly larger (e.g., EmoSet with 118,102 images [103] and AfectNet with 450,000 images [74]). Some eforts
havebeenmade to scale up MER datasets by inferring emotions from tags(MTG-Jamendo with18,486excerpts[13]
and Music4all with 109,269 excerpts [87]), but these have not yet found their way into standard emotion prediction
or classiication tasks. However, small datasets can also be useful in predictive contexts when greater control over
stimuli or features is necessary. These have been useful in applications testing new feature representations [85]
or identifying relevant features for multi-genre predictions [44], or as reference standards for comparison with
novel feature sets [21]. Findings from explanatory studies often inform theory-driven applications in predictive
tasks, helping to improve current benchmarks.
1.4 The current benchmarks of MER
Predictive accuracy in MER taskshasimproved as datasetsandmodelshavebecomemore sophisticated;Regression
models for arousal/valence have been reported to peak at 58%/28% accuracy in 2008 [106], 70%/26% in 2010 [53],
and 67%/46% in 2021 [102]. In the same period, classiication rates have increased from 53% [26] to 70% [81] to
83% [88]. Comparing these past eforts, however, is challenging due to inconsistencies between studies in metrics,
modelling architectures, datasets, and evaluation criteria. Although we assume that the overall accuracy has
improved signiicantly in the past decade, valence remains more challenging to predict than arousal.
Recent studies have sought to improve emotion prediction by identifying more relevant feature sets [21, 79],
integrating low-, mid-, and high-level features through multimodal data [16], and leveraging neural networks to
learn features directly from audio [1, 112]. Other eforts have attempted to improve the MER pipeline by taking
into account the diferences between studies in how emotions are represented [55], as well as how emotions
are represented in diferent languages [50, 64]. These approaches aim to overcome ceiling efects on predictive
accuracy [26], which some scholars refer to as a semantic gap [16, 100]. However, this prediction ceiling may
be better understood as an inherent measurement error arising from annotations, feature representations, and
model limitations. Although isolating the sources of these errors remains infeasible at this stage, comparing
success rates between modeling techniques, feature set sizes, and other meaningful factors ofers a step toward
addressing this challenge. However, to date, no study has systematically compared the results of the diverse
approaches used in MER research.
1.5 Aims
Our aim is to evaluate the predictive accuracy of two types of emotional expression in music: (a) models that
predict track-speciic coordinates in afective circumplex space (valence and arousal) and (b) models that classify
discrete emotion categories. We focus on recent studies to identify the overall success rate in MER tasks and key
factors such as modeling techniques, the number of features, or the inferential goal (explanation vs prediction)
ACMComput. Surv.
4 • T.EerolaandC. Anderson
that might contribute to the prediction accuracy of the models. To achieve this, we conducted a meta-analysis
of journal articles published in the past 10 years, focusing on subgroup analyzes that capture these diferences
(model type, feature N, and predictive vs explanatory modeling). Based on the existing literature, we hypothesize
that arousal will be predicted with higher accuracy than valence, as valence tends to be more context-dependent
and challenging to model [104].
In terms of the modelling techniques and the number of features, a reasonable hypothesis is that advanced
techniques (e.g., neural networks) and larger number of features will lead to higher prediction rates than
conventional techniques (e.g., logistic regression or linear regression) and smaller feature sets. However, this
relationship might not be as straightforward as this due to the demands complex models place on the size of the
dataset [6, 94].
2 Methods
We preregistered the meta-analysis plan on 21 June 2024 at OSF, https://osf.io/c5wgd, and the plan is also available
at Study Data and Code Repository- Preregistration.
2.1 Study identification
In the search stage, we used three databases, Web of Science, Scopus, and Open Alex to identify journal articles
published between 2014 and 2024 containing keywords/title valence OR arousal OR classi* OR categor*
OR algorithm AND music AND emotion AND recognition. For a complete account of the speciic search
strings for each database, see Study Data and Code Repository- Search Syntax. All searches were done in May
2024.
The initial search yielded 553 potential studies after excluding duplicate entries. We interactively screened
them for relevance in three stages, resulting in 46 studies that passed our inclusion criteria (music emotion studies
using classiication or regression methods to predict emotion ratings of music using symbolic or audio features,
and containing suicient detail to convert results to � or ��� values; see Study Data and Code Repository
Extraction Details). After the screening stage, we deined a set of entities to extract characterising (i) music (genre,
stimulus number [N]1, duration), (ii) features extracted (number, type, and source, as deined by Panda et al.,
[79]), (iii) model type (regression, neural network, SVM, etc.) and outcome measure (�2, ���, ���), (iv) model
complexity (i.e., approximate number of features used to predict ratings), and (v) type of model cross-validation.
A summary of the common datasets used in the studies is available at Study Data and Code Repository- Datasets.
We converted all regression results from �2 values into � values for valence and arousal, and the classiication
results into the Matthews correlation coeicient [���, 19]. We excluded irrelevant emotion dimensions (e.g.,
resonance in [25] or activation in [85]). Some regression studies operationalized arousal using dimensions of
energy and tension [99]. For these studies, we excluded tension, as it has been shown to overlap considerably
with valence, and with energy after partialling out the efect of valence [31]. To increase consistency in our
analyses, we excluded studies using incompatible features (e.g., spectrograms of audio iles [75]), or dependent
variables (e.g., a regression study analyzed valence and arousal together, but not separately [20]).
For classiication studies, the number of emotion classes ranged from two to eight. Most studies predicted
classes corresponding to the afective dimensions of the circumplex model, or discrete emotion labels mapping
onto them (e.g., happy, sad, nervous, and calm or variants [1, 5, 108]). Despite the popularity of the circumplex,
its treatment varied substantially between studies. Examples range from predicting quadrants in a multi-class
problem [78] or in a series of binary classiication problems [12], or dividing each quadrant into multiple
sublevels [76, 93]. Some studies separately predicted valence and arousal [51, 112], while others excluded valence
[e.g., all models in 112, 113] or speciic quadrants [49, excludes the bottom-right quadrant]. Only a few studies
1Stimulus number refers to total number of music excerpts used in a study, which is usually called dataset size in machine learning studies.
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 5
Table 1. Count of models across model tasks, techniques, and summaries of feature and stimulus N.
Regression
Classiication
Total
Study N
Model N
Techniques
Neural Nets (NN)
Support Vector Machines (SVM)
Linear Methods (LM)
22
204
64
62
62
12
86
21
26
19
Tree-based Methods (TM)
KS, Add. & KNN
Feature N
Stimulus N
14
2
Min=3, ���=653, Max=14460
16
4
Min=6, ���=98, Max=8904
Min=20, ���=324, Max=2486 Min=124, ���=300, Max=5192
34
290
85
88
81
30
6
classiied valence and arousal separately; for these studies we averaged prediction success across both emotion
concepts.
2.2 uality control
The search yielded studies of variable (and occasionally questionable) quality. To mitigate the potentially spurious
efects resulting from the inclusion of low-quality studies, we excluded studies lacking suicient details about
stimuli, features analyzed, or model architecture (see Study Data and Code Repository- Comparison). Finally,
we excluded studies published in journals of questionable relevance/quality, (e.g., Mathematical Problems in
Engineering ceased publication following 17 retractions published between July and September 2024). Overall,
this step eliminated 12 studies, leaving us with 34 studies in total.
2.3 Study encoding
To capture key details of each study, we added additional ields to the BibTeX entries for each study. The ields
included information about the genre/type of stimuli employed, along with their duration and number, the
number of analyzed features, and the model type ś Neural Nets (NN), Support Vector Machines (SVM)2, Linear
Methods (LM), Tree-based Methods (TM), Kernel Smoothing, Additive and KNN Methods (KM) ś validation
procedure and output measures. Furthermore, we included the study results using executable R code containing
custom functions for meta-analysis. For complete details on our encoding procedure, see Study Data and Code
Repository- Extraction Details.
The low of the study selection process is summarised in Figure 1.
3 Results
First we describe the overall pattern of data (regression vs. classiication, modelling techniques, feature numbers,
stimulus numbers (i.e., dataset size), datasets, and other details). The analysis code is available at Study Data and
Code Repository- Analysis. The counts of studies, models, and features are shown in Table 1.
Although the total number of studies meeting the criteria described in the previous section is modest (34 in
total), they encompass a wide array of models (290 in total) with a relatively uniform distribution among the three
2The study by Chen et al.[17] was the only study of those included to use Gaussian Mixture Models. We decided to group this with Support
Vector Machines as they have been reported to perform similarly on mid-sized data sets [72].
ACMComput. Surv.
6 • T.EerolaandC. Anderson
Fig. 1. Flowchart showing the study inclusions and eliminations.
most popular techniques: Neural Networks (85 models in total), SVMs (88), and Linear Methods (81). Tree-based
models are used less frequently (30 in total), and there is a small number (6) of other model techniques, such as
kernel smoothing or K-nearest neighbors (KNN) techniques, used in the models. However, these techniques will
not be visible in the breakdown of the results as these models were not among the strongest models per study (see
reporting principles in the results). The number of features and stimuli within these studies varies signiicantly,
ranging from as few as three features [10] to a maximum of almost 14,500 features [115]. The median number
of features difers between the regression (653) and classiication (98) studies, mainly relecting the nature of
the datasets used in each approach. The number of stimuli is typically around 300-400 (with a median of 324 for
regression and 300 for classiication), although there is substantial variation, with extremes of 20 stimuli [11] to
5192 stimuli [5]. There are also additional dimensions to consider, such as the type of cross-validation used, the
music genres analyzed (whether a single genre, multiple genres, or a mix), the type of modelling (predictive or
explanatory) framework, and the extraction tool used to extract features. However, these variables do not lend
themselves to a simple summary, so we will revisit them during the interpretation and discussion stages.
We irst report regression studies that predict valence and arousal.
3.1 Results for regression studies
Since there are many models contained within each of the studies, we will report the results in two parts; We
irst give an overview of the results for all models, and then we focus on the best performing models of each
study. The best performing model is the model within each study with the highest correlation coeicient. This
reduction is done to avoid the issue of multiple models from the same study delating the results, as the majority
of the models included are relative modest baseline or alternative models that do not represent the novelty or
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 7
Table 2. Meta-analytic summary measures for all regression studies predicting valence from audio. See Table 1 for the
acronyms of the modelling techniques.
Concept
Models, obs
� [95% CI]
�
�
�2
�2
Valence All
102, 60017 0.583 [0.541ś0.623] 21.41 .0001 0.094 97.7%
Valence Max 22, 14172 0.669 [0.560ś0.755] 9.58 .0001 0.148 98.4%
N Features
<30
30ś300
300+
6 ,3140
8, 4098
8, 6934
0.766 [0.488ś0.903]
0.580 [0.276ś0.778]
0.666 [0.531ś0.767]
Ð
Ð
Ð
Ð 0.198 98.6%
Ð 0.188 97.4%
Ð 0.062 98.0%
Techniques
LM
SVM
9, 2457
4, 5068
0.784 [0.652ś0.870]
0.539 [0.171ś0.774]
Ð
Ð
Ð 0.1194 96.3%
Ð 0.0702 97.1%
NN
TM
6, 3317
3, 3330
0.473 [0.167ś0.696]
0.750 [0.292ś0.928]
Ð
Ð
Ð 0.1029 98.2%
Ð 0.0740 98.8%
content of the article. We also provide a summary of the results with all models included in addition to the chosen
strategy, where the best model of each study is considered.
3.1.1 Results for valence. Table 2 summarises the results for all models (All) as well as the best performing models
(Max) for each study for valence. The summary includes the number of models and observations, the correlation
coeicient and its 95% conidence interval, the �-value and �-value for the correlation, the heterogeneity statistics
�2 and �2, calculated through appropriate transformations (Fisher’s �) for the correlation coeicient as part of a
random-efects model using meta library [9]. We used Paule-Mandel estimator for between-study heterogeneity
[62] and Knapp-Hartung [58] adjustments for conidence intervals. In this table, we also report two subgroup
analyses. One in which we have divided the studies according to the number of features they contain (three
categories based on quantiles to keep the group size comparable) and into four modelling techniques introduced
earlier (see Table 1).
The results indicate that valence can generally be predicted with moderate accuracy, with the best model from
each of the 22 studies achieving an average correlation of � = 0.669 (95% CI: 0.560-0.755), called "Valence Max"
in Table 2. However, when considering all models in these studies (n = 102), the overall prediction rate drops
signiicantly to � = 0.583. We argue that this lower correlation is likely due to the inclusion of baseline models
reported in these studies, which may not relect the true success of the task for the purposes of our analysis.
3.1.2 uantifying study heterogeneity. Further analysis of between-study heterogeneity, as indexed by the �2
(0.148) and the Higgins & Thompson’s �2 statistic [48] at 98.4%, reveals substantial heterogeneity. Since �2 is
heavily inluenced by the size of the study (with larger N leading to lower sampling error), its value may be less
informative in this context. In contrast, �2, which is less sensitive to the number of studies and directly related to
the outcome metric (�), provides a more reliable measure of heterogeneity in this case. Also, we note that, because
the overall heterogeneity in the data is high, we are cautious in our interpretation of publication bias [97].
To better understand the efects between studies and the nature of the observed heterogeneity, Figure 2 presents
a forest plot of the random-efects model, based on the models that perform the best in all studies. The efects of
individual studies are represented by rectangles, with the size relecting the weight based on the sample size.
Lines relect 95% conidence intervals around study efects, and the summary efect appears at the bottom of the
ACMComput. Surv.
8 • T.EerolaandC. Anderson
Fig. 2. Forest plot of the best valence models from all MER studies.
graph, represented as a dark diamond [65]. In terms of the forest plot, the range of prediction values (correlations)
is broad, ranging from 0.13 to 0.92, with all studies except Koh et al. [59] demonstrating evidence of positive
correlations. 15 of the 22 models achieved a mean estimate of 0.669. While the conidence intervals are generally
narrow due to the large sample sizes in each study, there are exceptions, such as smaller sample sizes (n = 20) in
Beveridge et al. [11], and (n = 40) in Griiths et al. [44]. If we explore the asymmetry of the model prediction
rate across standard error, we do not observe particular asymmetries that would indicate particular bias in the
reported studies. This is veriied by a non-signiicant Egger’s test [32] (� = 5.05, 95% CI:-0.99ś11.09, � = 1.64, � =
0.112).
Returning to the mean valence correlation of 0.669 by all studies and the possible impact of study heterogeneity
on this estimation, we also calculated the correlation without studies outside the 95% CI for the pooled efect.
This left 12 studies in the data and resulted in a meta-analytical pooled correlation of 0.686 (95% CI: 0.635ś0.731).
In other words, despite the large variation in correlations and standard errors in the studies, this variation in
itself does not seem to be a signiicant driver behind the overall efect.
3.1.3 Reporting splits. To gain insight into the factors that contribute to the wide range of model success, we
explored several ways of splitting the data. Table 2 presents two key splits: one based on the number of features
used, which we hypothesized might inluence model performance, and another based on the modeling techniques
used. In terms of feature sets, we categorized them into three groups: few features (<30, where the range of feature
counts is 3ś22 and ��� = 16.5), a large number of features (30Ð300, where the actual range is 45ś260 features,
��� = 101), and massive feature sets (300+, range 388-14460, ��� = 654). These splits produced reasonably
comparable representations of regression and classiication studies, although the actual ranges difered. Models
using a relatively small number of features (<30, 6 in total) performed best (� = 0.766, 95% CI: 0.488ś0.903)
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 9
compared to those utilizing larger feature sets. However, it should be noted that models that use massive feature
sets (300+, 8 studies in total) also performed reasonably well (� = 0.666), achieving more consistent results than
the overall prediction rate (� = 0.669). This observation is supported by the lowest heterogeneity index for the
massive feature set group (�2 = 0.062), indicating more consistent results in all studies. Studies with a large
number of features (30-300 features, 8 studies in total) delivered the worst results, � = 0.580 (95% CI: 0.276ś0.778).
Despite the luctuation in the overall model accuracy between the number of features, the diferences are not
substantially large to pass the statistical signiicance test (�(2) = 2.03, � = .363).
When analyzing the studies using the four modeling techniques used, the predictions difer signiicantly (�(3)
= 12.43, � = .0061). In particular, linear models (LM) and neural networks (NN) were the most common, with
9 and 6 studies, respectively, allowing for more conident interpretations. Linear models achieved the highest
prediction rate (� = 0.784, 95% CI: 0.652ś0.870), although this may be inluenced by the smaller datasets typically
used in these studies. These studies also exhibited higher heterogeneity (�2 = 0.119) compared to other techniques.
Although there were only 3 studies involving tree-based models (TM), these performed well, achieving � = 0.750,
95% CI: 0.292ś0.928). The relatively poor performance of the neural network (NN) models represented in six
studies (� = 0.473, 95% CI: 0.167ś0.696) is diicult to explain without a more detailed examination of the speciic
model architectures and the stimuli used in these studies.
We also performed sub-grouping analyzes across stimulus genres (single vs mixed), inding no signiicant
diferences (�(1) = 0.01, � = .9158). Both single-genre (� = 0.675 95% CI: 0.465, 0.813, � = 8) and multi-genre
(� = 0.665, 95% CI: 0.508ś0.779, � = 14) studies achieved similar prediction rates, although multi-genre studies
exhibited slightly higher heterogeneity (�2 = 0.167) than single-genre studies (�2 = 0.137).
These comparisons of sub-groupings may also be inluenced by other factors, such as whether the study utilised
a predictive or explanatory modelling framework. To address this, we used the type of journal in which each
study was published as a proxy indicator for predictive or explanatory modelling, where we classiied studies
published in psychology journals as explanatory and those published in engineering journals as predictive. Of the
22 regression studies, 13 were classiied into predictive frameworks, yielding an average correlation of � = 0.656
(95% CI: 0.505ś0.769). Studies with explanatory frameworks (9 in total) showed a similar overall correlation of � =
0.688 (95% CI: 0.468ś0.827). No signiicant diferences in model accuracy were observed between the two types of
frameworks, �(1) = 0.10, � = 0.748. More broadly, while the sub-groupings based on modelling techniques result
in an uneven distribution of studies and observations, the two main sub-groupings presented in Table 2 highlight
valuable diferences in model performance across the studies.
3.1.4 Results for arousal. Moving on the arousal, we carry out the same meta-analytical analysis applying the
random-efects model to arousal. Table 3 describes the broad pattern of results in tabular format, and Figure 3
illustrates the spread and heterogeneity of all studies for arousal. The overall correlation across the studies using
the best performing model in each study (Max) is 0.809 (95% CI: 0.740ś0.860). If we examine all the models
reported in each study, the correlation drops marginally, to 0.791 (95% CI: 0.770ś0.810), despite this analysis
including about four times as many models as taking the best model out of each study. For arousal, even the
baseline models seem to perform at a relatively high level.
3.1.5 uantifying study heterogeneity. For arousal, the heterogeneity indicators are again high (�2 = 0.141 and
�2 = 97.9%), suggesting that the summary may be misleading. However, analysis of asymmetry does not reveal
signiicant issues (Eggers test, � = 0.789 95% CI:-4.87ś6.45, � = 0.273, � = 0.788). If we remove studies that are
outside the 95% CI in heterogeneity, this leaves 13 studies in the summary where � = 0.826 (95% CI: 0.806ś0.845),
�2 = 0.0042 and �2 = 76.8%. In other words, we did not observe material diferences with a limited set of studies to
the results obtained with the 22 studies.
Figure 3 presents a forest plot of the random-efects model of the models that perform the best in all studies.
Similarly to valence, the range of correlations is also wide for arousal, ranging from 0.35 to 0.95, and all studies
ACMComput. Surv.
10 • T.Eerola and C. Anderson
Table 3. Meta-analytic summaries for all regression studies predicting arousal from audio.
Concept
Models, obs
� [95% CI]
�
�
�2
�2
Arousal All
102, 60017 0.791 [0.770ś0.810] 39.9 0.0001 0.069 96.2%
Arousal Max 22, 14172 0.809 [0.740ś0.860] 13.6 0.0001 0.141 97.9%
N Features
<30
30ś300
300+
6, 3140
8, 4098
8, 6934
0.885 [0.782ś0.940]
0.735 [0.501ś0.868]
0.804 [0.716ś0.867]
Ð
Ð
Ð
Ð 0.0948 93.5%
Ð 0.1971 98.2%
Ð 0.0612 97.4%
Techniques
LM
SVM
NN
TM
8, 1713
5, 5812
6, 3317
3, 3330
0.882 [0.809ś0.928]
0.796 [0.559ś0.913]
0.660 [0.395ś0.823]
0.809 [0.733ś0.864]
Ð
Ð
Ð
Ð
Ð 0.0846 93.3%
Ð 0.1325 98.3%
Ð 0.1209 98.1%
Ð 0.0025 65.4%
Fig. 3. Forest plot of the best arousal models from all MER studies.
demonstrate evidence of positive correlations. The majority of models achieve a mean estimate of 0.809 or higher
(14 out of 22 models). Due to the large sample in most studies, the conidence intervals are narrow, although the
exceptions (� < 55) are clearly visible [11, 44, 59, 85, 98].
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 11
Table 4. Meta-analytic diagnostic for all classification studies predicting emotion categories from audio.
Concept
Models, obs
� [95% CI]
�
�
�2
�2
All Models
Best Models
86, 80544
12, 15696
0.825 [0.790ś0.854] 23.7 0.0001 0.2082 99.7%
0.868 [0.748ś0.934] 8.13 0.0001 0.3180 99.8%
N Features
<30
30ś300
300+
4, 6179
5, 8193
3, 1324
0.929 [0.816ś0.974]
0.846 [0.361ś0.971]
0.775 [-0.271ś0.982]
Ð
Ð
Ð
Ð 0.098 96.2%
Ð 0.482 99.9%
Ð 0.272 97.7%
Techniques
LM
SVM
NN
TM
2, 735
3, 6556
3, 2313
4, 6092
0.728 [-0.996ś0.999]
0.870 [-0.727ś0.998]
0.931 [0.652ś0.988]
0.853 [0.446ś0.968]
Ð
Ð
Ð
Ð
Ð 0.194 98.0%
Ð 0.823 99.9%
Ð 0.125 98.8%
Ð 0.243 99.1%
3.1.6 Reporting splits. The analysis of the subdivision of studies shows that there are no signiicant diferences
between studies using diferent numbers of features (�(2) = 5.20, � = .074) despite the difering means (� = 0.885
for studies with less than 30 features, � = 0.735 for 30 to 300 features, and� = 0.804 for studies using more than 300
features). The diferences in the techniques, however, show statistically signiicant variance between subgroups
(�(3) = 10.83, � = .0127). Neural networks (NN) achieve poor prediction of arousal (� = 0.660) compared to other
techniques. The caveat of this subgroup analysis is the small number of observations for four techniques. We
also found no diferences between studies that used predictive frameworks (� = 0.786, 95% CI: 0.669ś0.865) or
explanatory frameworks (� = 0.839, 95% CI: 0.742ś0.902) (�(1) = 0.94, � = .333). We interpret the absence of
diferences as relecting high variance within these splits and an insuicient number of studies to detect such
efects.
3.2 Results for classification studies
We next evaluated classiication studies. Figure 4 shows forest plot visualization from the random-efects model
of the best-performing models in classiication studies. The ���s vary over a wide range, ranging from 0.55 to
0.98. Table 4 indicates that using the best model of each study increases performance relative to all models (���
= 0.868, 95% CI: 0.748ś0.934), yet slightly increases heterogeneity (�2 = 0.318, �2 = 99.8%).
3.2.1 uantifying study heterogeneity. Accounting for outliers among the classiication results removes 6 studies,
afecting both performance (��� = 0.894, 95% CI: 0.828ś0.936) and heterogeneity scores (�2 = 0.057, �2 = 97.7%).
However, we did not observe signiicant issues in the analysis of asymmetry (� =-19.77, 95% CI:-39.29ś0.24).
After aggregating across dimensions, we found that some studies with the best results only involved arousal
classiication [112, 113]. To assess their impact on interpretations, we evaluated how their exclusion afected
average classiication accuracy. These analyses revealed that accuracy (��� = 0.8758, 95% CI: 0.7235ś0.9468)
did not change signiicantly, nor did the rank order of model classes in terms of performance. Consequently, we
report on all 12 in subsequent analyses.
ACMComput. Surv.
12 • T.Eerola and C. Anderson
Fig. 4. Forest plot of the best classification models from all MER studies.
3.2.2 Reporting splits. Analyzing subgroups revealed that the number of features (as classiied into under 30,
between 30 and 300, and above 300 features1) does not signiicantly impact results (�(2) = 3.91, � = 0.1419),
despite ���s difering on average (<30 features: ��� = 0.929, 30ś300 features: ��� = 0.846, 300+ features ���
= 0.775). Similarly, model classes did not difer signiicantly (�(3) = 4.22, � = 0.239) although neural networks
reached higher ���� (0.931), followed by SVMs (0.870), tree-based methods (0.854), then linear methods (0.728).
Finally, neither single vs. multigenre (�(1) = 0.12, � = 0.732), nor binary vs. multi-class models (�(1) = 0.03, �
= 0.869) difered signiicantly. Again, high variance between studies and the overall small number of studies
within the splits produce a lack of sensitivity between the techniques. All classiication studies were published in
engineering journals and thus represent the predictive framework in our earlier typology.
3.3 Model success across concepts, model types and feature counts
To assess how the use of diferent model types afected performance, we prepared heatmap visualizations (see
Figure 5) showing diferences in success between features �, model types, and algorithms. We collapsed SVM and
Tree-Based categories due to their low representation in the model summary. Figure 5 summarizes diferences
in success (a) across categories, as well as (b) the algorithms in each model class. In general, studies that use
smaller feature sets tend to perform best, while the best type of model is highly dependent on the nature of
the prediction task. For valence and arousal, linear models perform better than other model types, whereas for
emotion classiication, neural networks show the best overall performance. The overall pattern aligns with the
analyses of the splits reported earlier concerning model types and feature counts, but the visualization also
highlights concurrent information about the feature �, model types, study counts, and the average number of
1Features <30 features contains a range of 6ś11 features and ��� = 9, features 30ś300 contain 98 to 231 features with ��� of 122, and
features above 300+ consist of 397 to 8904 features with ��� of 1702
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 13
Fig. 5. Heatmaps summarizing models. Panel a depicts overall success across tasks according to model type and feature �
summaries. Text labels summarize the number of models belonging to each subgroup, whereas the numbers in parentheses
summarize the median number of stimuli used. Panel b summarizes the algorithms pertaining to each class, colour-coded by
success rate, and the numbers refer to how many studies used each model.
stimuli within each combination. For example, studies with the lowest number of features (<30) also tend to
have the highest mean number of stimuli (� = 749.5), while the middle range of characteristic counts (30ś300)
corresponds to the lowest mean number of stimuli (� = 522.5). It is also reassuring to observe that studies utilizing
neural networks and other model types tend to use a higher number of features and stimuli than those employing
linear models, as this relects the capabilities and internal training requirements built into these models.
4 Discussion and conclusions
Research on Music Emotion Recognition has steadily increased in popularity since the early 2000s, with techno
logical advancements facilitating sharing of data sets, analysis tools, and music stimuli. Public forums like the
Music Information Retrieval Exchange (MIREX) have facilitated collaborations between computer scientists, musi
cologists, and psychologists alike ś spurring improvements in performance. Despite the increasing complexity of
models and datasets, no existing study has rigorously compared the overall success of Music Emotion Recognition
research using standardized metrics, nor has there been an analysis of the relative merits of the model techniques
and feature sets employed. This study presents the irst meta-analysis of music emotion recognition, breaking
down accuracy in terms of the model types, number of features, and empirical frameworks used.
ACMComput. Surv.
14 • T.Eerola and C. Anderson
We initially identiied 96 studies involving MER models, but narrowed our selection to 34 after iltering studies
to ensure consistent quality, reporting standards, and a speciic focus on evaluating emotions using musical
features. From these studies, we encoded accuracy scores for 290 models, with 204 related to regression and 86
to classiication. Comparing the most accurate model in each study revealed reasonably accurate prediction of
valence (� = 0.669, 95% CI: 0.560ś0.755), and arousal (� = 0.809, 95% CI: 0.740ś0.860) in regression studies. For both
afective dimensions of the circumplex model, linear methods (valence � = 0.784, arousal � = 0.882) and tree-based
models (valence � = 0.750, arousal � = 0.809) outperformed support vector machines (SVMs) (valence � = 0.539,
arousal � = 0.796) and neural networks (valence = 0.473, arousal = 0.660). In contrast, neural networks performed
the most accurately in classiication studies (��� = 0.931), followed by SVMs (��� = 0.870) and tree-based
models (��� = 0.853).
Despite the high overall success of the research in this topic, the models exhibited several diferences relating
to (i) the scale and quantity of data sets employed, (ii) feature extraction methods, (iii) the number and types of
features and reduction methods used, (iv) the actual modelling architecture, and (v) how model outcomes were
cross-validated.
4.1 Improvements in predictive accuracy
The results of the meta-analysis ofer several important insights. First, compared to a 2010 report by Huq et
al.[53], the prediction ceiling for valence has increased from � = 0.51 to 0.67. Conversely, the predictive accuracy
for arousal has not shown improvement (reported already in 2013 at � = 0.83). For classiication, studies reached
variable classiication rates from 0.497 using the �1 score [86] to 79% average precision [95] in the past, while
prediction rates have improved considerably, here ��� = 0.87, although diferences in metrics.
Second, there is no single modelling technique that seems to emerge on top, although linear models and
random forests perform best in regression studies, and neural networks and support vector machines excel in
classiication tasks. We note that the model accuracy is surprisingly little afected by the number of features or
the dataset siześlikely the result of cross-validation techniques used to avoid overittingśbut the heterogeneity of
the materials used in diferent studies may also mask substantial diferences. For instance, smaller datasets tend
to use linear models and deliver higher model accuracy than larger datasets and those with a large number of
features. We surmise that this might be related to disciplinary diferences. For example, smaller datasets often
come from music psychology studies, which put a premium on data quality (quality control of the ground-truth
data and extracted features) rather than on dataset size and model techniques. This argument is largely consistent
with the analysis of the studies divided across predictive and explanatory modelling frameworks (which we
determined based on journals representing psychology or engineering discipline), even though the pattern is not
well-deined.
Third, there is little work on the relevance of the features and how these impact the accuracy of the models.
Unfortunately, in many cases, it is impossible to attribute the sources of error to features (as opposed to the target
emotions obtained from participants or from the modelling architecture, cross-validation, or the size of data), as
the studies so far have not compared the feature sets systematically, nor has a comparison of the datasets with
identical features has been performed [79]. In the future, it would be advantageous to systematically assess these
sources of error in MER studies to allow us to focus on where and how signiicant improvements can be made.
4.2 Limitations
The main limitations of this study are: (i) the sample size is based on the number of stimuli, (ii) constraints in
database selection and search term deinitions, and (iii) issues with study quality. Using the number of stimuli as
the sample size, rather than the sizes of the training or testing sets or the number of annotators, is a defensible
choice. The diference between the size of the complete dataset and the size of the training set is typically constant
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 15
(70ś80%), so the impact mainly concerns the sensitivity of the random-efects model. Adjusting sample size
based on annotator counts would introduce large inconsistencies, as these vary widely (from a few individuals to
hundreds). If we view MER models as aiming for generalisability, the number of unique stimuli is an appropriate
unit.
Some relevant studies are likely missing because they are not indexed in the three main databases (Web of
Science, Scopus, and Open Alex) or use uncommon keywords. Several originally eligible papers were excluded
because they lacked suicient methodological detail. A meta-analysis ultimately ofers a snapshot of the available
literature within a deined period. Additional studies outside this window or in non-indexed sources (e.g.,
preprints) do not appear to challenge our overall conclusions, although we did not analyse them formally.
4.3 Recommendations for future MER studies
In general, the present study revealed an uncomfortably large variability in overall quality control and reporting
practices in MERstudies. In manycases, the reporting wasinsuicient to determine the features used in the models
or their sources. In addition, a signiicant number of studies had to be discarded due to a lack of information on
data, model architectures, or outcome measures. We summarize these issues in the following as recommendations
for improving (1) reporting and transparency, (2) deinition of features, (3) scale and content of the data set, and
(4) selection of emotion frameworks.
Future reports should contain viable information about the data, models, and success metrics. The modelling
process should include a description of cross-validation, feature extraction technique, feature reduction (if used),
and actual accuracy measures. We would recommend future studies to use the Matthews Correlation Coeicient
(���) for classiication studies, as currently there are numerous metrics (�1, precision, recall, balanced accuracy,
etc.) that do not operate in the same range. The situation for regression studies tends to be less volatile, but model
accuracy may be reported with error measures (Mean Squared Error, Root Mean Squared Error, or Mean Absolute
Error, or ���, ����, ���), which cannot be converted to relative measure such as �2 without knowing the
variance of the data. Again, we recommend using �2 as it being a relative measure and scale invariant to allow
comparison between models, datasets, and studies. There is potential confusion in using the �2 measure since
some studies report �2
adj , which is a less biased estimate of the model’s explanatory power as it incorporates the
number of predictors as a penalty. However, since there are other measures that calculate penalties for complex
models (such as AIC or BIC), and the diference between the two measures (�2 and �2
adj ) is small in large datasets,
we recommend �2 as the most transparent accuracy measure for regression studies.
We also note that inter-rater agreement provides a useful upper-bound reference for human performance [14],
even though computational models can exceed this level [83]. Currently, MER datasets vary widely in how they
report participant agreement. We therefore recommend that annotation quality and variability be treated as
essential components in future evaluations of model performance.
It would also be highly beneicial to share models and features transparently. If a study relies on published
datasets, as most do, sharing the actual model (as code/notebooks) and features would allow for a more direct
comparison of model techniques for the same dataset. In addition, not all datasets are shared [e.g., 3, 49, 87, 113].
Standardizing the reporting of datasets to include subsections explaining detailed information about stimuli
(including genre, duration, sampling rate, and encoding format), features (types, extraction/analysis software,
quantity of features, transformations, reduction methods), and models (types, tuning parameters, cross-validation)
will enable more accurate comparisons between studies. The reporting in Grekow’s study [42] serves as a useful
example by providing enough detail in these areas to facilitate reproducibility. Although copyright restrictions
may limit the sharing of some datasets, features and examples should be made available through reliable external
repositories (e.g., Zenodo, Open Science Framework, or Kaggle datasets).
ACMComput. Surv.
16 • T.Eerola and C. Anderson
One of the crucial aspects of modelling is the choice of features, their quantity, and their validation. In the
present materials, we observe a continuum deined by two extremes: one approach relies on domain knowledge,
starting with a limited number of features that are assumed to be perceptually relevant, while the other employs
a large number of features, allowing the model to determine which are most relevant for prediction. The former
is typically favored in music psychology studies, whereas the latter is more common in engineering and machine
learning ields. Our results suggest that the domain knowledge-driven approach leads to the highest model
accuracy across all studies and techniques. However, since our sample includes studies from the past 10 years, it is
important to note that deep learning models have only gained prominence in this ield since 2021. Consequently,
it is too early to generalize that models based on domain knowledge, with a limited number of features and
classical techniques, will continue to outperform machine learning approaches that utilize large (300+) feature
sets. We believe that the relatively modest size of datasets available so far has prevented deep learning approaches
from fully leveraging their potential to learn generalizable patterns in the data. For reference, the size of the
datasets in MER is currently comparable to the data set sizes to model facial expressions (median N=502, [61])
and speech expressions (median of 1287, [47]). However, annotated datasets for visual scenes and objects tend to
be much larger, often exceeding 100,000 annotated examples [24, 60]. In many applications, large datasets would
be required for appropriate utilization of deep-learning algorithms, however, recent proposals to overcome the
dataset-size limitation involve the use of pre-training and unsupervised techniques to learn general features
[see MERT, 109]. Although this approach has not yet fully resolved the issue, the bottleneck related to data set
size can be partially mitigated by judicious use of self-supervised learning.
An encouraging inding is that 94% of the studies analyzed here reported some form of model validation. The
majority of studies validated models by splitting the dataset into separate sets for training and testing [e.g., 102],
sometimes including an additional set for validation [93]. Most used some form of cross validation (CV), with
the most common type being 10-fold CV. Other varieties included 3-fold, 5-fold, or 6-fold CV, as well as more
complex variants like nested leave-one-out CV [23] and 20 × 10-fold CV [78]. Whereas many engineering studies
performed model validation using one or more large databases, some psychological studies evaluating smaller
datasets validated models by designing new experiments. Examples include comparing a model’s performance
on ground-truth data with annotations from a second experiment [11, 44], or comparing a model’s performance
across diferent versions of the same music pieces [10].
Currently, the majority of the datasets are Western pop, representing only a fraction of the musical styles
consumed globally. In addition, the annotators representing the Global North dominate the studies at the moment,
with some exceptions [40, 114]. This lack of diversity may contribute to the success of the task, but presents a
signiicant limitation in our understanding of MER more broadly [15]. Greater exploration of multi-genre MER
[e.g., 44], and cross-cultural applications [1, 52, 98, 99] will provide an important step toward establishing more
generalizable models.
Finally, we note that the relevance of the emotion frameworks used in MER is not always explicitly discussed.
The majority studies rely on valence and arousal or some combination of basic emotion categories. However, these
frameworks may have limited usefulness in practical applications that aim to capture the diversity of emotion
experiences with music. For example, some experiences align with models of music-induced emotions, such as
GEMS[111] or AESTHEMOS[89], whereas other explore what emotions can be expressed through music [30], or
what are assumed to be worthwhile clusters of concepts (moods, emotions, tags) from crowdsourced, non-theory
driven data [84]. Understanding the limitations of diferent emotion taxonomies can also help improve modelling
practices. For example, some scholars have explored treating MER as a circular regression problem, which can
help overcome practical challenges such as the diiculty in relating to the abstract dimensions of valence and
arousal, as well as the modelling assumptions required when translating a circular afective space into regression
problems [27, 46].
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 17
The present meta-analysis demonstrates that signiicant progress has been made in developing accurate and
scalable MER models over the past decade. Future eforts should prioritize feature validation, standardized
reporting, the construction of larger and more diverse datasets, and the transparent sharing of research materials
to ensure further consistent improvements in MER.
Acknowledgments
We thank Prof. Michael Schutz for creating the opportunity for collaboration.
References
[1] Gaurav AgarwalandHariOm.2021. Aneicientsupervised framework for music mood recognition using autoencoder-based optimised
support vector regression model. IET Signal Processing 15, 2 (2021), 98 ś 121. doi:10.1049/sil2.12015
[2] Kat R. Agres, Rebecca S. Schaefer, Anja Volk, Susan van Hooren, Andre Holzapfel, Simone Dalla Bella, Meinard Müller, Martina de
Witte, Dorien Herremans, Rafael Ramirez Melendez, Mark Neerincx, Sebastian Ruiz, David Meredith, Theo Dimitriadis, and Wendy L.
Magee. 2021. Music, computing, and health: a roadmap for the current and future roles of music technology for health care and
well-being. Music & Science 4 (2021), 2059204321997709.
[3] Christopher Akiki and Manuel Burghardt. 2021. MuSe: The Musical Sentiment Dataset. Journal of Open Humanities Data 7 (July 2021),
10. doi:10.5334/johd.33
[4] Anna Aljanaki, Yi-Hsuan Yang, and Mohammad Soleymani. 2017. Developing a benchmark for emotional analysis of music. PloS one
12, 3 (2017), e0173392.
[5] P. Álvarez, J. García de Quirós, and S. Baldassarri. 2023. RIADA: A Machine-Learning Based Infrastructure for Recognising the Emotions
of Spotify Songs. International Journal of Interactive Multimedia and Artiicial Intelligence 8, 2 (2023), 168 ś 181. doi:10.9781/ijimai.2022.
04.002
[6] Ahmad Alwosheel, Sander van Cranenburgh, and Caspar G. Chorus. 2018. Is your dataset big enough? Sample size requirements when
using artiicial neural networks for discrete choice analysis. Journal of Choice Modelling 28 (2018), 167ś182. doi:10.1016/j.jocm.2018.07.
002
[7] Cameron J. Anderson and Michael Schutz. 2022. Exploring historic changes in musical communication: Deconstructing emotional cues
in preludes by Bach and Chopin. Psychology of Music 50, 5 (2022), 1424ś1442.
[8] Junjie Bai, Jun Peng, Jinliang Shi, Dedong Tang, Ying Wu, Jianqing Li, and Kan Luo. 2016. Dimensional music emotion recognition by
valence-arousal regression. In 2016 IEEE 15th International Conference on Cognitive Informatics & Cognitive Computing. IEEE, IEEE, Palo
Alto, CA, 42ś49.
[9] Sara Balduzzi, Gerta Rücker, and Guido Schwarzer. 2019. How to perform a meta-analysis with R: a practical tutorial. Evidence-Based
Mental Health 22, 4 (2019), 153ś160. doi:10.1136/ebmental-2019-300117
[10] Aimee Battcock and Michael Schutz. 2021. Individualized interpretation: Exploring structural and interpretive efects on evaluations of
emotional content in Bach’s Well Tempered Clavier. Journal of New Music Research 50, 5 (2021), 447ś468. doi:10.1080/09298215.2021.
1979050
[11] Scott Beveridge and Don Knox. 2018. Popular music and the role of vocal melody in perceived emotion. Psychology of Music 46, 3
(MAY 2018), 411ś423. doi:10.1177/0305735617713834
[12] Vankayalpati Bhuvana Kumar and M. Kathiravan. 2023. Emotion recognition from MIDI musical ile using Enhanced Residual Gated
Recurrent Unit architecture. Frontiers in Computer Science 5 (2023), 1305413. doi:10.3389/fcomp.2023.1305413
[13] Dmitry Bogdanov, Minz Won, Philip Tovstogan, Alastair Porter, and Xavier Serra. 2019. The MTG-jamendo Dataset for Automatic
Music Tagging. In Machine Learning for Music Discovery Workshop, International Conference on Machine Learning (ICML 2019). LM4MD,
Long Beach, CA, United States. http://hdl.handle.net/10230/42015
[14] Mayla Boguslav and Kevin Bretonnel Cohen. 2017. Inter-annotator agreement and the upper limit on machine performance: evidence
from biomedical natural language processing. In MEDINFO 2017: Precision Healthcare through Informatics. IOS Press, Hangzhou, China,
298ś302. doi:10.3233/978-1-61499-830-3-298
[15] Georgina Born. 2020. Diversifying MIR: Knowledge and Real-World Challenges, and New Interdisciplinary Futures. Transactions of the
International Society for Music Information Retrieval 3, 1 (Oct. 2020), 193ś204. doi:10.5334/tismir.58
[16] Oscar Celma. 2006. Foaing the music: Bridging the semantic gap in music recommendation. In The 5th International Semantic Web
Conference. Springer, Athens, GA, 927ś934.
[17] Yu-AnChen,Ju-ChiangWang,Y.-H.Yang,andHomerH.Chen.2017. ComponentTyingforMixtureModelAdaptationinPersonalization
of Music Emotion Recognition. IEEE-ACM TRANSACTIONS ON AUDIO SPEECH AND LANGUAGE PROCESSING 25, 7 (JUL 2017),
1409ś1420. doi:10.1109/TASLP.2017.2693565
ACMComput. Surv.
18 • T.Eerola and C. Anderson
[18] Yu-An Chen, Yi-Hsuan Yang, Ju-Chiang Wang, and Homer Chen. 2015. The AMG1608 dataset for music emotion recognition. In 2015
IEEE international conference on acoustics, speech and signal processing (ICASSP). IEEE, Brisbane, Australia, 693ś697.
[19] Davide Chicco and Giuseppe Jurman. 2020. The advantages of the Matthews correlation coeicient (MCC) over F1 score and accuracy
in binary classiication evaluation. BMC genomics 21 (2020), 1ś13.
[20] Yu-Hao Chin, Jia-Ching Wang, Ju-Chiang Wang, and Y.-H. Yang. 2018. Predicting the Probability Density Function of Music Emotion
Using Emotion Space Mapping. IEEE Transactions on Afective Computing 9, 4 (2018), 541 ś 549. doi:10.1109/TAFFC.2016.2628794
[21] Shreyan Chowdhury and Gerhard Widmer. 2021. On perceived emotion in expressive piano performance: Further experimental
evidence for the relevance of mid-level perceptual features. In International Society for Music Information Retrieval Conference (ISMIR
2023). ISMIR, Milan, Italy, 128ś134.
[22] Eduardo Coutinho and Nicola Dibben. 2013. Psychoacoustic cues to emotion in speech prosody and music. Cognition & Emotion 27, 4
(2013), 658ś684.
[23] Eduardo Coutinho and Bjorn Schuller. 2017. Shared acoustic codes underlie emotional communication in music and speech-Evidence
from deep transfer learning. PLOS ONE 13, 6 (2017), e0179289. doi:10.1371/journal.pone.0179289
[24] Jia Deng, Wei Dong, Richard Socher, Li-Jia Li, Kai Li, and Li Fei-Fei. 2009. Imagenet: A Large-Scale Hierarchical Image Database. In
2009 IEEE Conference on Computer Vision and Pattern Recognition. Ieee, Miami, FL, 248ś255.
[25] James J. Deng, Clement H. C. Leung, Alfredo Milani, and Li Chen. 2015. Emotional States Associated with Music: Classiication,
Prediction of Changes, and Consideration in Recommendation. ACM Transactions on Interactive Intelligent Systems 5, 1 (2015), 1ś36.
doi:10.1145/2723575
[26] John Stephen Downie. 2008. The music information retrieval evaluation exchange (2005ś2007): A window into music information
retrieval research. Acoustical Science and Technology 29, 4 (2008), 247ś255.
[27] Isabelle Dufour and George Tzanetakis. 2021. Using Circular Models to Improve Music Emotion Recognition. IEEE Transactions on
Afective Computing 12, 3 (JUL-SEP 2021), 666ś681. doi:10.1109/TAFFC.2018.2885744
[28] Tuomas Eerola. 2011. Are the emotions expressed in music genre-speciic? An audio-based evaluation of datasets spanning classical,
ilm, pop and mixed genres. Journal of New Music Research 40, 4 (2011), 349ś366. https://doi.org/10.1080/09298215.2011.602195
[29] Tuomas Eerola, Anders Friberg, and Roberto Bresin. 2013. Emotional Expression in Music: Contribution, Linearity, and Additivity of
Primary Musical Cues. Frontiers in Psychology 4, 487 (2013), 1ś12. doi:10.3389/fpsyg.2013.00487
[30] TuomasEerolaandPasiSaari. 2025. What emotionsdoes musicexpress? Structure of afect terms in music using iterative crowdsourcing
paradigm. Plos ONE 20, 1 (2025), e0313502. doi:10.1371/journal.pone.0313502
[31] Tuomas Eerola and Jonna K Vuoskoski. 2011. A comparison of the discrete and dimensional models of emotion in music. Psychology of
Music 39, 1 (2011), 18ś49.
[32] Matthias Egger, George Davey Smith, Martin Schneider, and Christoph Minder. 1997. Bias in meta-analysis detected by a simple,
graphical test. British Medical Journal 315, 7109 (1997), 629ś634.
[33] Mehmet Bilal Er and Ibrahim Berkan Aydilek. 2019. Music emotion recognition by using chroma spectrogram and deep visual features.
International Journal of Computational Intelligence Systems 12, 2 (2019), 1622ś1634.
[34] Florian Eyben, Martin Wöllmer, and Björn Schuller. 2010. Opensmile: the Munich versatile and fast open-source audio feature extractor.
In Proceedings of the 18th ACM international conference on Multimedia. ACM, Firenze, Italy, 1459ś1462.
[35] Robert A. Fairthorne. 1968. Towards information retrieval. Archon Books, New York, US.
[36] Yazhong Feng, Yueting Zhuang, and Yunhe Pan. 2003. Popular music retrieval by detecting mood. In Proceedings of the 26th annual
international ACM SIGIR conference on Research and development in informaion retrieval. ACM, Toronto, Canada, 375ś376.
[37] Anders Friberg, Erwin Schoonderwaldt, Patrik N Juslin, and Roberto Bresin. 2002. Automatic real-time extraction of musical expression.
In International Computer Music Conference. ISMIR, Gothenburg, Sweden, 365ś367.
[38] Zhouyu Fu, Guojun Lu, Kai Ming Ting, and Dengsheng Zhang. 2010. A survey of audio-based music classiication and annotation.
IEEE Transactions on Multimedia 13, 2 (2010), 303ś319.
[39] Bruno Gingras, Manuela M. Marin, and W. Tecumseh Fitch. 2014. Beyond intensity: Spectral features efectively predict music-induced
subjective arousal. Quarterly Journal of Experimental Psychology 67, 7 (2014), 1428 ś 1446. doi:10.1080/17470218.2013.863954
[40] Juan Sebastián Gómez-Cañón, Nicolás Gutiérrez-Páez, Lorenzo Porcaro, Alastair Porter, Estefanía Cano, Perfecto Herrera-Boyer,
Aggelos Gkiokas, Patricia Santos, Davinia Hernández-Leo, Casper Karreman, and Emilia Gómez. 2023. TROMPA-MER: An Open Dataset
for Personalized Music Emotion Recognition. Journal of Intelligent Information Systems 60, 2 (April 2023), 549ś570. doi:10.1007/s10844
022-00746-0
[41] Juan Sebastián Gómez-Cañón, Estefanía Cano, T. Eerola, Perfecto Herrera, Xiao Hu, Y.-H. Yang, and Emilia Gómez. 2021. Music Emotion
Recognition: Toward new, robust standards in personalized and context-sensitive applications. IEEE Signal Processing Magazine 38, 6
(2021), 106ś114. doi:10.1109/MSP.2021.3106232
[42] Jacek Grekow. 2018. Audio features dedicated to the detection and tracking of arousal and valence in musical compositions. Journal of
Information and Telecommunication 2, 3 (2018), 322ś333.
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 19
[43] Jacek Grekow. 2021. Music emotion recognition using recurrent neural networks and pretrained models. Journal of Intelligent
Information Systems 57, 3 (2021), 531ś546.
[44] Darryl Griiths, Stuart Cunningham, Jonathan Weinel, and Richard Picking. 2021. A multi-genre model for music emotion recognition
using linear regressors. Journal of New Music Research 50, 4 (AUG 8 2021), 355ś372. doi:10.1080/09298215.2021.1977336
[45] Annaliese Micallef Grimaud and T. Eerola. 2022. An Interactive Approach to Emotional Expression through Musical Cues. Music &
Science 5 (2022), 1ś23. doi:10.1177/20592043211061745
[46] Byeong-jun Han, Seungmin Rho, Roger B Dannenberg, and Eenjun Hwang. 2009. SMERS: Music Emotion Recognition Using Support
Vector Regression. In 10th International Society for Music Information Retrieval Conference. ISMIR, Kobe, Japan, 651ś656.
[47] Ahlam Hashem, Muhammad Arif, and Manal Alghamdi. 2023. Speech Emotion Recognition Approaches: A Systematic Review. Speech
Communication 154 (Oct. 2023), 102974. doi:10.1016/j.specom.2023.102974
[48] Julian PT Higgins and Simon G Thompson. 2002. Quantifying heterogeneity in a meta-analysis. Statistics in Medicine 21, 11 (2002),
1539ś1558.
[49] Serhat Hizlisoy, Serdar Yildirim, and Zekeriya Tufekci. 2021. Music emotion recognition using convolutional long short term memory
deep neural networks. Engineering Science and Technology, an International Journal 24, 3 (2021), 760 ś 767. doi:10.1016/j.jestch.2020.10.009
[50] Qiong Hu, Masrah Azrifah Azmi Murad, and Qi Li. 2025. Advancing Music Emotion Recognition: Large-Scale Dataset Construction
and Evaluator Impact Analysis. Multimedia Systems 31, 2 (Feb. 2025), 123. doi:10.1007/s00530-025-01701-z
[51] Xiao Hu, Fanjie Li, and Ruilun Liu. 2022. Detecting Music-Induced Emotion Based on Acoustic Analysis and Physiological Sensing: A
Multimodal Approach. Applied Sciences 12, 18 (2022), 9354. doi:10.3390/app12189354
[52] Xiao Hu and Yi-Hsuan Yang. 2017. Cross-Dataset and Cross-Cultural Music Mood Prediction: A Case on Western and Chinese Pop
Songs. IEEE TRANSACTIONS ON AFFECTIVE COMPUTING 8, 2 (APR-JUN 2017), 228ś240. doi:10.1109/TAFFC.2016.2523503
[53] Arein Huq, Juan Pablo Bello, and Robert Rowe. 2010. Automated music emotion recognition: A systematic evaluation. Journal of New
Music Research 39, 3 (2010), 227ś244.
[54] Patrik N. Juslin, Laura S Sakka, Gonçalo T Barradas, and Olivier Lartillot. 2022. Emotions, mechanisms, and individual diferences in
music listening: A stratiied random sampling approach. Music Perception: An Interdisciplinary Journal 40, 1 (2022), 55ś86.
[55] Jaeyong Kang and Dorien Herremans. 2025. Towards Uniied Music Emotion Recognition across Dimensional and Categorical Models.
arXiv:2502.03979 [cs.SD] https://arxiv.org/abs/2502.03979
[56] Michael Kassler. 1966. Toward musical information retrieval. Perspectives of New Music 4 (1966), 59ś67. Issue 2.
[57] Haruhiro Katayose, Masakazu Imai, and Seiji Inokuchi. 1988. Sentiment extraction in music. In 9th International Conference on Pattern
Recognition. IEEE Computer Society, Rome, Italy, 1083ś1084.
[58] Guido Knapp and Joachim Hartung. 2003. Improved tests for a random efects meta-regression with a single covariate. Statistics in
Medicine 22, 17 (2003), 2693ś2710.
[59] En Yan Koh, Kin Wai Cheuk, Kwan Yee Heung, Kat R. Agres, and Dorien Herremans. 2023. MERP: A Music Dataset with Emotion
Ratings and Raters’ Proile Information. Sensors 23, 1 (2023), 382. doi:10.3390/s23010382
[60] Ranjay Krishna, Yuke Zhu, Oliver Groth, Justin Johnson, Kenji Hata, Joshua Kravitz, Stephanie Chen, Yannis Kalantidis, Li-Jia Li,
David A. Shamma, Michael S. Bernstein, and Fei-Fei Li. 2017. Visual Genome: Connecting Language and Vision Using Crowdsourced
Dense Image Annotations. International Journal of Computer Vision 123 (2017), 32ś73.
[61] Eva G. Krumhuber, Lina Skora, Dennis Küster, and Linyun Fou. 2017. A Review of Dynamic Datasets for Facial Expression Research.
Emotion Review 9, 3 (2017), 280ś292. doi:10.1177/1754073916670022
[62] Dean Langan, Julian P.T. Higgins, Dan Jackson, Jack Bowden, Areti Angeliki Veroniki, Evangelos Kontopantelis, Wolfgang Viechtbauer,
and Mark Simmonds. 2019. A comparison of heterogeneity variance estimators in simulated random-efects meta-analyses. Research
Synthesis Methods 10, 1 (2019), 83ś98.
[63] Olivier Lartillot and Petri Toiviainen. 2007. A Matlab toolbox for musical feature extraction from audio. In International Conference on
Digital Audio Efects, Vol. 237. DAFx, Bordeaux, France, 237ś244.
[64] Harin Lee, Elif Çelen, Peter Harrison, Manuel Anglada-Tort, Pol van Rijn, Minsu Park, Marc Schönwiesner, and Nori Jacoby. 2025.
GlobalMood: A cross-cultural benchmark for music emotion recognition. arXiv:2505.09539 [cs.IR] https://arxiv.org/abs/2505.09539
[65] S. Lewis and M. Clarke. 2001. Forest plots: trying to see the wood and the trees. BMJ 322, 7300 (2001), 1479ś1480.
[66] Yuan-Pin Lin, Chi-Hong Wang, Tien-Lin Wu, Shyh-Kang Jeng, and Jyh-Horng Chen. 2009. EEG-based emotion recognition in music
listening: A comparison of schemes for multiclass support vector machine. In 2009 IEEE International Conference on Acoustics, Speech
and Signal Processing. IEEE, Taipei, Taiwan, 489ś492.
[67] ErikLindström,PatrikNJuslin, RobertoBresin, andAaronWilliamon.2003. "Expressivitycomesfromwithinyoursoulž:Aquestionnaire
study of music students’ perspectives on expressivity. Research Studies in Music Education 20, 1 (2003), 23ś47.
[68] Dan Liu, Lie Lu, and Hong-Jiang Zhang. 2003. Automatic Mood Detection from Acoustic Music Data. In Proc. ISMIR 2003; 4th Int. Symp.
Music Information Retrieval. Johns Hopkins University, Baltimore, Maryland, 1ś7.
[69] Lie Lu, Dan Liu, and Hong-Jiang Zhang. 2005. Automatic mood detection and tracking of music audio signals. IEEE Transactions on
audio, speech, and language processing 14, 1 (2005), 5ś18.
ACMComput. Surv.
20 • T.Eerola and C. Anderson
[70] Michael I Mandel and Dan P W Ellis. 2007. LABROSA’s audio music similarity and classiication submissions. In MIREX 2007-Music
Information Retrieval Evaluation eXchange. ISMIR, Vienna, Austria.
[71] Michael I Mandel, Graham E Poliner, and Daniel PW Ellis. 2006. Support vector machine active learning for music retrieval. Multimedia
systems 12, 1 (2006), 3ś13.
[72] Daniel J. Mashao. 2003. Comparing SVM and GMM on parametric feature-sets. In Proceedings of the 14th Annual Symposium of the
Pattern Recognition Association of South Africa. IAPR, Grabouw, South Africa, 27ś28.
[73] Arthur Mendel. 1969. Some preliminary attempts at computer-assisted style analysis in music. Computers and the Humanities 4 (1969),
41ś52. Issue 1.
[74] Ali Mollahosseini, Behzad Hasani, and Mohammad H Mahoor. 2017. Afectnet: A database for facial expression, valence, and arousal
computing in the wild. IEEE Transactions on Afective Computing 10, 1 (2017), 18ś31.
[75] Sayan Nag, Medha Basu, Shankha Sanyal, Archi Banerjee, and Dipak Ghosh. 2022. On the application of deep learning and multifractal
techniques to classify emotions and instruments using Indian Classical Music. Physica A: Statistical Mechanics and its Applications 597
(2022), 127261. doi:10.1016/j.physa.2022.127261
[76] Van Loi Nguyen, Donglim Kim, Van Phi Ho, and Younghwan Lim. 2017. A new recognition method for visualizing music emotion.
International Journal of Electrical and Computer Engineering 7, 3 (2017), 1246 ś 1254. doi:10.11591/ijece.v7i3.pp1246-1254
[77] Richard Orjesek, RomanJarina, and Michal Chmulik.2022. End-to-end musicemotionvariation detection using iteratively reconstructed
deep features. Multimedia Tools and Applications 81, 4 (2022), 5017ś5031. doi:10.1007/s11042-021-11584-7
[78] Renato Panda, Ricardo Malheiro, and Rui Pedro Paiva. 2020. Novel Audio Features for Music Emotion Recognition. IEEE Transactions
on Afective Computing 11, 4 (2020), 614 ś 626. doi:10.1109/TAFFC.2018.2820691
[79] Renato Panda, Ricardo Malheiro, and Rui Pedro Paiva. 2023. Audio Features for Music Emotion Recognition: A Survey. IEEE Transactions
on Afective Computing 14, 1 (2023), 68ś88. doi:10.1109/TAFFC.2020.3032373
[80] Renato Panda, Ricardo Malheiro, Bruno Rocha, António Pedro Oliveira, and Rui Pedro Paiva. 2013. Multi-modal music emotion
recognition: A new dataset, methodology and comparative analysis. In 10th International symposium on computer music multidisciplinary
research (CMMR 2013). Springer, Berlin, 570ś582.
[81] Jiyoung Park, Jongpil Lee, Juhan Nam, Jangyeon Park, and Jung-Woo Ha. 2017. Representation learning using artist labels for audio
classiication tasks. In 18th International Society for Music Information Retrieval Conference. ISMIR, Suzhou, China.
[82] Rosalind Picard. 1997. Afective Computing. MIT Press, Boston, MA.
[83] Russell Richie, Sachin Grover, and Fuchiang Rich Tsui. 2022. Inter-annotator agreement is not the ceiling of machine learning
performance: Evidence from a comprehensive set of simulations. In Proceedings of the 21st workshop on biomedical language processing.
Association for Computational Linguistics, Dublin, Ireland, 275ś284.
[84] Pasi Saari, György Fazekas, Tuomas Eerola, Mathieu Barthet, Olivier Lartillot, and Mark Sandler. 2015. Genre-adaptive Semantic
Computing and Audio-based Modelling for Music Mood Annotation. IEEE Transactions on Afective Computing 7, 2 (2015), 122ś135.
[85] Elena Saiz-Clar, Miguel Angel Serrano, and Jose Manuel Reales. 2022. Predicting emotions in music using the onset curve. Psychology
of Music 50, 4 (2022), 1107ś1120. doi:10.1177/03057356211031658
[86] Chris Sanden and John Z. Zhang. 2011. An Empirical Study of Multi-Label Classiiers for Music Tag Annotation. In Proceedings of the
12th International Society for Music Information Retrieval Conference. ISMIR, Miami, FL, 717ś722.
[87] Igor André Pegoraro Santana, Fabio Pinhelli, Juliano Donini, Leonardo Catharin, Rafael Biazus Mangolin, Valéria Delisandra Feltrim,
Marcos Aurélio Domingues, et al. 2020. Music4all: A New Music Database and Its Applications. In 2020 International Conference on
Systems, Signals and Image Processing (IWSSIP). IEEE, Rio de Janeiro, Brazil, 399ś404.
[88] Rajib Sarkar, Sombuddha Choudhury, Saikat Dutta, Aneek Roy, and Sanjoy Kumar Saha. 2020. Recognition of emotion in music based
on deep convolutional neural network. Multimedia Tools and Applications 79, 1 (2020), 765ś783.
[89] Ines Schindler, Georg Hosoya, Winfried Menninghaus, Ursula Beermann, Valentin Wagner, Michael Eid, and Klaus R. Scherer. 2017.
Measuring aesthetic emotions: A review of the literature and a new assessment tool. PloS One 12, 6 (2017), e0178899.
[90] Galit Shmueli. 2010. To Explain or to Predict? Statist. Sci. 25, 3 (2010), 289ś310.
[91] Mohammad Soleymani, Micheal N. Caro, Erik M. Schmidt, Cheng-Ya Sha, and Yi-Hsuan Yang. 2013. 1000 Songs for Emotional Analysis
of Music. In Proceedings of the 2nd ACM International Workshop on Crowdsourcing for Multimedia (Barcelona, Spain) (CrowdMM ’13).
Association for Computing Machinery, New York, NY, USA, 1ś6. doi:10.1145/2506364.2506365
[92] Guangxiao Song, Shenyi Ding, and Zhijie Wang. 2018. Audio classiication tasks using recurrent neural network. In MIREX 2018-Music
Information Retrieval Evaluation eXchange. ISMIR, Paris, France.
[93] Kanawat Sorussa, Anant Choksuriwong, and Montri Karnjanadecha. 2020. Emotion classiication system for digital music with a
cascaded technique. ECTI Transactions on Computer and Information Technology 14, 1 (2020), 53ś66. doi:10.37936/ecti-cit.2020141.205317
[94] Chen Sun, Abhinav Shrivastava, Saurabh Singh, and Abhinav Gupta. 2017. Revisiting unreasonable efectiveness of data in deep
learning era. In Proceedings of the IEEE international conference on computer vision. IEEE, Venice, Italy, 843ś852.
[95] Konstantinos Trohidis, Grigorios Tsoumakas, George Kalliris, and Ioannis Vlahavas. 2008. Multi-label classiication of music into
emotions. In Proceedings of the 9th International Conference on Music Information Retrieval, Vol. 8. Drexel University, Philadelphia, USA,
ACMComput. Surv.
AMeta-Analysis of Music Emotion Recognition Studies • 21
325ś330.
[96] George Tzanetakis. 2007. Marsyas submissions to MIREX 2007. In 8th International Conference on Music Information Retrieval. Austrian
Computer Society, Vienna, Austria, 1ś3.
[97] Robbie CM Van Aert, Jelte M Wicherts, and Marcel ALM van Assen. 2016. Conducting meta-analyses based on p values: Reservations
and recommendations for applying p-uniform and p-curve. Perspectives on Psychological Science 11, 5 (2016), 713ś729.
[98] XinWang,YujiaWei,LenaHeng,andStephenMcAdams.2021. ACross-CulturalAnalysisoftheInluenceofTimbreonAfectPerception
in Western Classical Music and Chinese Music Traditions. Frontiers in Psychology 12 (2021), 732865. doi:10.3389/fpsyg.2021.732865
[99] Xin Wang, Yujia Wei, and Dasheng Yang. 2022. Cross-cultural analysis of the correlation between musical elements and emotion.
Cognitive Computation and Systems 4, 2, SI (2022), 116ś129. doi:10.1049/ccs2.12032
[100] Geraint A Wiggins. 2009. Semantic gap?? Schemantic schmap!! Methodological considerations in the scientiic study of music. In 2009
11th IEEE International Symposium on Multimedia. IEEE, San Diego, CA, 477ś482.
[101] Liang Xu, Zaoyi Sun, Xin Wen, Zhengxi Huang, Chi-ju Chao, and Liuchang Xu. 2021. Using machine learning analysis to interpret the
relationship between music emotion and lyric features. PEERJ Computer Science 7 (2021), e785. doi:10.7717/peerj-cs.785
[102] Jing Yang. 2021. A Novel Music Emotion Recognition Model Using Neural Network Technology. Frontiers in Psychology 12 (2021),
760060. doi:10.3389/fpsyg.2021.760060
[103] Jingyuan Yang, Qirui Huang, Tingting Ding, Dani Lischinski, Danny Cohen-Or, and Hui Huang. 2023. Emoset: A large-scale visual
emotion dataset with rich attributes. In Proceedings of the IEEE/CVF International Conference on Computer Vision. IEEE, Paris, France,
20383ś20394.
[104] Xinyu Yang, Yizhuo Dong, and Juan Li. 2018. Review of data features-based music emotion recognition methods. Multimedia systems
24 (2018), 365ś389.
[105] Yi-Hsuan Yang and Homer H. Chen. 2011. Music Emotion Recognition. CRC Press, Boca Raton, US. doi:10.1201/b10731
[106] Yi-Hsuan Yang, Yu-Ching Lin, Ya-Fan Su, and Homer H. Chen. 2008. A regression approach to music emotion recognition. IEEE
Transactions on Audio Speech and Language Processing 16, 2 (2008), 448ś457.
[107] Y.-H. Yang, Y.-F. Su, Y.-C. Lin, and H. H. Chen. 2007. Music emotion recognition: The role of individuality. In Proceedings of the
International Workshop on Human-centered Multimedia. Association for Computing Machinery, Augsburg, Germany, 13ś22.
[108] Chia-Hung Yeh, Wen-Yu Tseng, Chia-Yen Chen, Yu-Dun Lin, Yi-Ren Tsai, Hsuan-I Bi, Yu-Ching Lin, and Ho-Yi Lin. 2014. Popular music
representation: chorus detection & emotion recognition. Multimedia Tools and Applications 73, 3 (2014), 2103 ś 2128. doi:10.1007/s11042
013-1687-2
[109] LI Yizhi, Ruibin Yuan, Ge Zhang, Yinghao Ma, Xingran Chen, Hanzhi Yin, Chenghao Xiao, Chenghua Lin, Anton Ragni, Emmanouil
Benetos, et al. 2023. MERT: Acoustic music understanding model with large-scale self-supervised training. In The Twelfth International
Conference on Learning Representations. IEEE Information Theory Society, Vienna, Austria, 1ś12.
[110] R Kh Zaripov and JGK Russell. 1969. Cybernetics and music. Perspectives of New Music 7, 2 (1969), 115ś154.
[111] Marcel Zentner, Didier Grandjean, and Klaus R. Scherer. 2008. Emotions evoked by the sound of music: characterization, classiication,
and measurement. Emotion 8, 4 (2008), 494ś521.
[112] Jiang Long Zhang, Xiang Lin Huang, Li Fang Yang, and Liqiang Nie. 2016. Bridge the semantic gap between pop music acoustic feature
and emotion: Build an interpretable model. Neurocomputing 208, SI (2016), 333ś341. doi:10.1016/j.neucom.2016.01.099
[113] Jiang Long Zhang, Xiang Lin Huang, Li Fang Yang, Ye Xu, and Shu Tao Sun. 2017. Feature selection and feature learning in arousal
dimension of music emotion by using shrinkage methods. Multimedia Systems 23, 2 (2017), 251 ś 264. doi:10.1007/s00530-015-0489-y
[114] Kejun Zhang, Hui Zhang, Simeng Li, Changyuan Yang, and Lingyun Sun. 2018. The PMEmo Dataset for Music Emotion Recognition.
In Proceedings of the 2018 ACM on International Conference on Multimedia Retrieval (ICMR ’18). Association for Computing Machinery,
NewYork, NY, USA, 135ś142. doi:10.1145/3206025.3206037
[115] Meixian Zhang, Yonghua Zhu, Wenjun Zhang, Yunwen Zhu, and Tianyu Feng. 2023. Modularized composite attention network for
continuous music emotion recognition. Multimedia Tools and Applications 82, 5 (2023), 7319ś7341. doi:10.1007/s11042-022-13577-6
Received 15 April 2025; revised 26 December 2025; accepted 3 February 2026
ACMComput. Surv.