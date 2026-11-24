<!-- Page 1 -->
Known Music, Unknown Response: Leakage-Audited Dynamic Arousal
Forecasting With Scheduled Future Music
Bin Wen1 Dai-Qiao Zhang 2 Tien-Ping Tan1,∗
1School of Computer Sciences, Universiti Sains Malaysia, 11800, Pulau Pinang, Malaysia
2School of Mathematical Sciences, Universiti Sains Malaysia, 11800, Pulau Pinang, Malaysia
∗Correspondence:tienping@usm.my
Abstract
Dynamic music emotion recognition usually estimates concurrent or lag-aligned labels from audio
that has already been observed. We instead forecast the change in consensus arousal when the upcoming
music is scheduled but all later affect labels remain hidden. Evaluation holds out complete songs, encodes
each eligible 4-s chunk independently, predicts arousal innovation, and compares the correct future
with displaced segments from the same song. On PMEmo and a 1,494-song DEAM evaluation pool
excluded from engineering development, a complete past/future MuQ representation raises concordance
correlation coefficient (CCC) by 0.389–0.507 over recent affect and remains 0.268–0.382 above a
calibrated nonlinear state model. A future-only trajectory contains no past or current audio and still
exceeds that state model by 0.150–0.249. The earliest legal future chunk, which ends 5.5–11 s before
the target, also remains informative. Correct placement exceeds an overlapping 5-s shift by 0.100–0.209
and the acoustic-nearest eligible same-song segment by 0.078–0.105, with positive song-cluster lower
bounds. These results show that both scheduled content and its within-song position carry forecast
information under the stated observation rules. The study provides a leakage-controlled reference for
known-future music forecasting without treating predictive substitutions as causal interventions.
Keywords:affective computing; dynamic music emotion recognition; leakage auditing; music emotion
forecasting; negative controls; self-supervised music representation
1 Introduction
Music emotion recognition (MER) estimates emotion expressed or perceived in music, frequently in
Russell’s continuous valence–arousal space [1]. Dynamic MER extends this objective to a time-varying
trajectory. Most systems nevertheless remain recognition models: the acoustic context around an annotated
moment is observed, and the model estimates a concurrent or lag-adjusted label [2–5]. This article asks
a conditional forecasting question instead. If music after a decision time is already scheduled, but its
later affective response has not been observed, can the scheduled segment predict a subsequent change in
arousal?
The distinction matters in playlist planning, soundtrack adaptation, tutoring media, and other systems
where a candidate stimulus is known before its response. Forecasting methods routinely condition on
calendar variables or planned interventions whose future values are available at prediction time [6]. Music
can be treated as such a known future covariate. Doing so does not reveal the future response, but it
changes what a model may observe: it may inspect the scheduled waveform while it must not inspect
affect labels after the forecast origin.
A concrete use is offline candidate screening. A soundtrack editor could provide a measured group-level
starting state and a fixed set of licensed 10–15 s transitions, then use predicted arousal changes to reduce
the set requiring human review. This use does not require the model to choose or causally optimize the
final track. It does require a population and annotation protocol compatible with the training data, an
1
arXiv:2610.23063v1  [cs.SD]  16 Oct 2026

<!-- Page 2 -->
t − 10 s forecast origin t t + H − δ target t + H
Observed state
Affect labels and past music
legal only through t
Scheduled future music
Known waveform
independent 4-s chunk encoding
Response gap
No future label
delay δ
Hidden target
Predict Δyt, H
= yt + H − yt
Correct placement
Original scheduled segment
State-preserving negative control
Replace future only: local shift
or acoustic-nearest same-song segment
Forecast timeline
Figure 1: Forecast setting. Affect labels after origint are hidden although the scheduled waveform is
known. A valid chunk lies completely inside the permitted future interval. Negative controls preserve the
current state and song identity while replacing only the scheduled segment.
observable starting state, the same audio-support rules, uncertainty estimates, and human safety and
preference checks.
This setting is easy to evaluate incorrectly. Continuous emotion annotations are strongly autocorrelated,
so a model can obtain a plausible score by copying the current state. Overlapping windows create many
correlated examples from the same song, enabling track or production-style memorization. A bidirectional
audio encoder can also cross the declared decision boundary if a long waveform is encoded before features
are sliced. Finally, showing that audio improves over state does not establish that thecorrectly placed
future segment matters; another segment from the same song may carry nearly the same global style and
affect.
We address these threats with a declared-origin evaluation (Fig. 1). At origint, labels are available
only throught. The target is the innovation∆yt,H =yt+H−yt. Scheduled music may be used only before
a response-delay boundary, and every 4-s audio chunk is encoded independently. Outer and inner splits
hold out complete songs. Temporal specificity is tested by keeping the state and past anchor fixed while
replacing only the future with a local shift or the most acoustically similar eligible segment from the same
song.
The primary model combines recent affect with a PCA-256 summary of independently encoded MuQ
trajectories [7]. A separate attribution analysis removes all past-audio information and compares a
future-only trajectory with a nonlinear state forecaster trained directly on the evaluation target. This
identifies scheduled-future information without relying on a weak state baseline or future–past relational
descriptors.
The article makes four contributions.
1. It formulates dynamic arousal forecasting with scheduled music as a known-future-covariate problem
with explicit rules for outcomes, audio support, song splits, and temporal controls.
2. It provides an information hierarchy that distinguishes recent affect, observed-past audio, future-only
audio, and a complete past/future representation.
3. It introduces state-preserving same-song controls that retain locality or acoustic similarity and
therefore test within-song placement rather than merely track identity.
4. It audits audio-support isolation, localization within the scheduled segment, absolute prediction
errors, and sensitivity across songs, horizons, and training splits.
Across PMEmo and the engineering-excluded DEAM evaluation pool, the complete representation
raises arousal-innovation CCC by 0.389–0.507 over recent affect and by 0.268–0.382 over a calibrated
nonlinear state model. Future-only audio remains 0.150–0.249 above that state model. The earliest legal
2

<!-- Page 3 -->
Table 1: Task Taxonomy and Information Available at Prediction Time
Task Target Audio available Future response la-
bels
Main identification ques-
tion
Static MER Song/excerpt emo-
tion
Complete target
excerpt
Not applicable What emotion does the
excerpt express?
Dynamic MER Concurrent/lagged
emotion
Target-era acous-
tic context
Often used for
training alignment
What emotion is ex-
pressed now?
Past-only affect fore-
cast
Future level/change History through
origin
Hidden What follows from state
and observed history?
This work Future arousal inno-
vation
History plus sched-
uled future sup-
port
Hidden after origin Does the known future,
and its placement, add
forecast information?
Causal recommenda-
tion
Individual outcome
under an action
Candidate/action
description
Counterfactual un-
observed
Which action changes an
individual’s outcome?
4-s chunk, ending 5.5–11 s before the target, remains 0.044–0.084 above it; the result is not confined to
target-near audio. Correct placement remains 0.078–0.209 above the two hard same-song controls.
2 Related Work
2.1 Dynamic Music Emotion Recognition
PMEmo and DEAM provide continuous valence–arousal annotations and are widely used for time-varying
MER [8, 9]. Earlier systems modeled temporal emotion distributions with conditional random fields or
deep recurrent networks [2, 3]. Multi-scale context and attention subsequently improved prediction from
acoustic neighborhoods [4, 5], while personalized meta-learning addresses between-listener variation [10].
ENMI uses past emotion and music features to model emotion flow as multivariate time-series regression
[11].
These systems and the present work solve related but nonidentical tasks. Standard dynamic MER
observes acoustic evidence for the moment being labeled and often corrects the response lag. Our setting
declares a forecast origin, hides all later annotations, and permits only music that is scheduled and known
at that origin. Consequently, published dynamic-MER scores are not direct baselines: their targets,
context, splits, and permitted information differ. We compare state and audio forecasts under the same
observation rules and use song-disjoint validation.
Table 1 makes the task boundary explicit. Our setting is neither ordinary recognition nor causal
recommendation. It is a predictive known-covariate problem whose defining object is the information
available at the forecast origin.
2.2 Known Future Covariates and Innovation Targets
Multi-horizon forecasters often separate static, observed, and known-future variables [6]. A calendar event,
tariff plan, or scheduled control may be known even when the corresponding outcome is not. Treating
music as a scheduled covariate places affect forecasting within this framework. Predicting the innovation
rather than the future level reduces the direct reward for persistence and makes the target closer to
the transition a planning system would need to estimate. It does not remove all state predictability, so
state-only models remain necessary controls.
Continuous emotion labels also contain annotation delay and smoothing. Explicit lag correction
and joint alignment improve affect modeling [12, 13]. We therefore insert a response delay between the
permitted music support and the target, with a primary boundary gap of 2 s. Unlike label realignment,
this boundary determines which audio chunks are legally observable by the forecasting model.
3

<!-- Page 4 -->
Table 2: Notation and Terms Used in the Forecast Setting
Term Meaning
tForecast origin; labels are observed only through this time
HForecast horizon
δResponse gap between legal music support and target
st Affect history available at the origin
at,H Scheduled waveform interval permitted at prediction time
∆yt,H Change from the current to the later affect label
Wrong-time control Same state and song, but a displaced future segment
2.3 Music Foundation Representations and Interpretable Factors
MERT and MuQ learn transferable representations from large music collections [7, 14]. Unified and
multimodal MER research combines such embeddings with categorical, dimensional, lyrical, or musical
features [15, 16]. Representation quality alone, however, does not show that the correct within-song future
is being used. Our negative controls hold the embedding family and song identity fixed while changing
temporal placement.
Acoustic studies link loudness, timbre, rhythm, and tonality to multidimensional emotion ratings [17].
Music psychology further associates activation with dynamics, onset strength, temporal regularity, and
tempo, whereas valence depends more strongly on harmony, context, familiarity, and semantic appraisal
[18–20]. Predictive-processing accounts describe listening as hierarchical expectation formation, with
sensory and cognitive expectations contributing separately to musical pleasure and surprise [21, 22]. These
findings motivate studying arousal, while they do not establish the incremental predictive value of a
particular hand-crafted factor set.
2.4 Residual Learning, Cross-Fitting, and Negative Controls
Residual learning is a standard means of decomposing a forecasting problem, and recent neural objectives
explicitly model remaining error streams [23, 24]. Our audio head is fitted to out-of-fold state errors so
that its training target does not use an in-sample state prediction. This uses sample separation, as in
cross-fitting [25, 26], without introducing a Neyman-orthogonal score.
Negative controls are designed to reveal bias or an unintended pathway by preserving much of the
data-generating context while disrupting the relation of interest [27]. A random different-song future is
too easy for our purpose. We use same-song substitutions and quantify their temporal overlap or acoustic
similarity. They are predictive controls, not counterfactual listener outcomes.
3 Methods and Experimental Setup
3.1 Forecast Setting
3.1.1 T arget and Permitted Information
Lety t∈R 2 be the consensus arousal–valence annotation at timet, and letst contain labels available
throught. For horizonHand response delayδ, the scheduled music action is
at,H =x [t,t+H−δ],(1)
wherexis the waveform. The target is the change
∆yt,H =y t+H−yt.(2)
4

<!-- Page 5 -->
Table 3: Primary Threats and Experimental Responses
Threat Failure mode Design response
Emotion inertia Copy current level Predict innovation; strong state controls
Track identity Memorize song/style Hold out complete songs
Encoder leakage Attend beyond support Independent complete 4-s chunks
Coarse content Any segment works Same-song local and nearest controls
Window dependence Narrow uncertainty Song-cluster bootstrap
At inference,at,H is known but every annotation aftert is hidden. We estimate the later level and convert it
to an innovation before scoring. The available corpora represent consensus perceived or expressed emotion;
the estimand is therefore population-level forecast information, not an individual induced-emotion effect.
We view the response as
yt+H =m H(st) +rH(at,H,st) +ϵt,H,(3)
where mH captures state persistence andrH denotes information associated with the scheduled action.
The experiments do not identifyrH causally. They test whether it predicts held-out innovations and
whether it changes when the future is displaced within the same song.
3.1.2 F our Evaluation Rules
The evaluation imposes four rules.
Hidden outcomes: for a held-out prediction, no annotation after its forecast origin enters its input
features. Outcomes from outer held-out songs are used only for evaluation, not for fitting, calibration,
or model selection. Supervised fitting and inner validation use outcomes only from the corresponding
training and development songs.
Separated audio support: a frozen music encoder processes each 4-s chunk independently. A chunk is
eligible only if its start and end lie entirely inside the declared observed-past or scheduled-future interval.
Encoding a whole song and slicing hidden states afterward is prohibited because the encoder could have
attended across the boundary.
For example, on an integer-second grid witht = 20s, H = 10s, and δ = 2s, the target is at 30 s
and the legal scheduled support ends at 28 s. With 4-s chunks and 1-s stride, the eligible future chunks
are[20 , 24],..., [24, 28];[25 , 29]is illegal. All labels after 20 s remain hidden. Thus the first legal chunk
ends 6 s before the target, whereas the last ends 2 s before it. Half-second annotation origins produce the
corresponding 5.5–6.0 s and 2.0–2.5 s gaps used in the experiments.
Held-out songs: every outer and inner split holds out complete songs. Standardization, principal
component analysis (PCA), calibration and residual targets are fit using training songs only.
Fixed temporal anchor: a wrong-time control retains the original affect state, observed-past audio. It
replaces only the future segment and recomputes all future-minus-anchor descriptors against the original
anchor.
3.1.3 State-Preserving T emporal Controls
The unrestricted control chooses an eligible anchort′ from the same song with the same 1-s chunk-sampling
phase. Because such a swap can be acoustically easy to distinguish, we use two more demanding label-free
controls for the primary placement comparison.
Thelocal-shift controlchooses the eligible phase-matched candidate closest to a 5-s displacement. At
the 15-s horizon it still overlaps the correct permitted interval by approximately 62%. Theacoustic-nearest
controlchooses, among same-song candidates at least 5 s away, the future whose mean MuQ embedding
has maximum cosine similarity with the correct candidate. Self-maps are removed before computing
5

<!-- Page 6 -->
margins. We report the realized shift, temporal overlap, cosine similarity, and control coverage so that
control difficulty is observable rather than assumed.
The action-over-state and correct-over-control contrasts answer different questions. The former
measures the value of scheduled audio. The latter tests within-song placement after style, production, and
broad affective content have been preserved. A wrong-time segment can therefore remain better than
state only; the relevant test is whether the correctly placed segment is better.
3.2 Forecasting Models
3.2.1 State Model
The state vector contains the current arousal and valence, differences over one, two, and four annotation
steps, a five-frame mean, and elapsed time in seconds. A standardized ridge regressorfs predictsy t+H
froms t. For the strong-state audit, a fixed histogram gradient booster instead predicts∆yt,H directly
from 10 s of legal label history. A location–scale map for CCC calibration is estimated solely from inner
song-disjoint out-of-fold (OOF) predictions. The outer test songs remain untouched.
3.2.2 Independently Encoded Music Representation
MuQ-large encodes every 4-s waveform chunk independently at a 1-s stride. Mean pooling the final hidden-
state sequence gives a chunk embeddingzk. We denote byzt the independently encoded observed-past
chunk that ends closest to, and no later than, the forecast origin. For future intervalF and matched
observed-past intervalP, the complete relational representation contains
ϕM = [zF,σF,zF,end−zt, zF− zP,η],
η= [mean k∥zk+1−zk∥2,maxk ∥zk+1−zk∥2,∥σF∥2,
∥zF,end−zt∥2,∥ zF− zP∥2,dc(zF, zP ),
dc(zF,end, zP ),dc(zF,zt),dc(zF,end,zt)].
(4)
Here σF = sd(zF ), the path statistics use adjacent chunks withinF, anddc(u, v) = 1−cos (u, v). Thus
the representation has four embedding-vector blocks and nine scalars. The concatenated representation is
standardized and projected by whitened train-fold PCA-256 before ridge regression. To prevent the action
model from simply refitting state, inner-fold OOF state predictions are first produced and the MuQ head
is trained on the remaining target error. The base forecast is
ˆy(0)t+H =f s(st) +fM(ϕM(at,H;t)).(5)
BecauseϕM contains a legal past-audio anchor, its gain over state is described as acomplete past/future
representation gain. Two ablations identify the source of information. Past-only uses a symmetric observed
interval and no future descriptor. Future-only uses the future trajectory mean, dispersion, endpoints, and
within-future changes; it contains no past or current audio descriptor. Both receive identical PCA-256
capacity and the same OOF state residual target. In the nonlinear-state attribution experiment this target
is formed from the raw HGB predictions; CCC calibration is applied only to the separately reported state
comparison.
3.2.3 T raining and Inference
Standardization and PCA are refitted within every relevant training split. For each outer training set,
song-disjoint inner folds generate state predictions for training the MuQ residual head. The final state
model and MuQ head are then fitted using only the outer training songs. At inference, the state forecast
and audio correction are added, and the observed current label is subtracted to score innovation. No
explicit acoustic-factor correction is used in the reported forecasts.
6

<!-- Page 7 -->
Algorithm 1Outer-Fold State and MuQ Training
Require:Training songsD tr, test songsDte
1:Construct legal state and complete-support MuQ windows
2:Cross-fit state predictions withinD tr using song folds
3:Fit train-only standardization, PCA, and MuQ ridge to OOF state residuals
4:Fit the state model on allDtr
5:PredictD te with the state model plus MuQ head
6:Subtract the current label to obtain predicted innovation
7:Repeat prediction with state-preserving wrong futures
Table 4: Evaluation Data After Complete-Support Filtering
Data Horizon Songs Windows Win./song
PMEmo 10 s 611 19,336 31.6
PMEmo 15 s 481 13,677 28.4
DEAM holdout 10 s 1,494 74,181 49.7
DEAM holdout 15 s 1,494 59,241 39.7
After frozen feature extraction, the audio predictor requires only PCA and ridge regression. The
nonlinear state comparison is reported separately under the same song and audio-support rules.
3.3 Experimental Design
3.3.1 Datasets
PMEmocontains 794 chorus clips and dynamic annotations collected from 457 participants at 0.5-s
resolution [8]. The released dynamic table contains 767 song identifiers. Complete-support filtering retains
611 songs and 19,336 windows atH = 10s, and 481 songs and 13,677 windows atH = 15s. The principal
exclusion is geometric: clips without a complete state, past, future, and response-delay support cannot
form a legal example.
DEAMcontains 1,744 excerpts and 58 full-length songs (1,802 in total) with continuous averaged
annotations [9]. A partial engineering run exposed results for 305 songs while extraction and support
handling were being checked. These songs were not selected by labels or scores, but because their partial
outcomes had been observed, all 305 were treated as development data and excluded from primary
estimates. On July 10, 2026, before the complete holdout run, a manifest froze their identifiers together
with the partial-file hash, method-source hash, response delay, folds, factor subset, shrinkage, and horizons.
Of the remaining 1,497 labeled songs, 1,494 yield valid windows: 74,181 at 10 s and 59,241 at 15 s. The
complete MuQ archive contains 88,409 independent chunks.
The archived evaluation rows retain the original intersection of valid MuQ windows and the timestamp-
availability mask used by the earlier factor pipeline. That mask requires a song trajectory with a frame
at or before the origin and frames in the nominal future interval; songs with fewer than two retained
windows are excluded. We keep this common row set for all reported comparisons. It is a historical
coverage restriction: factor values are not inputs to the retained state or MuQ predictors, and timestamp
availability does not establish the waveform support of those excluded factors.
Both corpora primarily provide population-average perceived or expressed emotion. We restrict the
reported inference to arousal. Valence is not used to support the forecasting claim.
3.3.2 Splits, Metrics, and Inference
Every model uses three repeats of five song-disjoint outer folds. Cross-fitted stages use four inner song-
disjoint folds. The primary response delay isδ = 2s. All repeated predictions for a window are averaged
7

<!-- Page 8 -->
Table 5: Fixed Model and Evaluation Settings
Component Setting
Audio support 4-s chunks; 1-s stride
State ridge Standardized;α= 10
MuQ head Train-fold PCA-256; ridgeα= 100
Outer/inner splits3×5/ 4; song-disjoint
Response delay 2 s
Bootstrap 5,000 song-cluster draws
before inferential resampling.
The primary metric is Lin’s concordance correlation coefficient (CCC) on arousal innovation [28]. Mean
absolute error (MAE) is secondary. Paired uncertainty is estimated with 5,000 song-cluster bootstrap
draws, preserving all correlated windows from a resampled song. Within each corpus, the two horizons
form one confirmatory family for the audio-over-state contrast and one for correct-over-basic-wrong-time
placement. Each cell uses one-sidedα = 0.025after correction across the two horizons. Two-sided 97.5%
intervals use bootstrap quantiles 0.0125 and 0.9875; one-sided 97.5% lower bounds use quantile 0.025.
Hard-negative, support-localization, and attribution analyses are diagnostic.
3.3.3 Baselines and Audits
The audio baselines predict the same OOF state residual under identical song folds. They add either the
mean scheduled MuQ embedding or the complete MuQ representation. The attribution analysis compares
state ridge, direct-innovation histogram gradient boosting, past-only audio, future-only audio, and the
complete relation with identical PCA-256 heads. The support-localization diagnostic gives the first chunk,
last chunk, and complete future mean identical ridge heads under one train-fold PCA-256 basis fitted to a
fixed balanced sample of 20,000 representations.
The primary audio head uses PCA-256 and fixed ridge penalties. Attribution and support-localization
comparisons match audio-head capacity and keep all preprocessing within training-song folds.
Adjacent windows share substantial content, so the number of windows overstates the number of
independent musical units. Random cross-validation can be invalid for dependent time-series samples
[29]; we therefore group every split by song rather than randomly splitting windows. The comparisons are
confined to models evaluated under the same observation rules; they do not establish rankings against
systems trained or scored with different acoustic context.
4 Results
4.1 Full-Song Encoding Violates the Declared Support
Before evaluating predictive performance, we test whether encoding an entire song and slicing nominally
earlier hidden states respects the declared audio boundary. For three diagnostic PMEmo songs, the
waveform length is held fixed and all samples after a cutoff are set to zero. The original and altered
waveforms are then separately passed through MuQ, and hidden states with nominal centers before the
cutoff are compared. If full-song slicing isolated the permitted context, changing only the suffix would
leave those states unchanged.
Table 6 shows a material violation. Within the final 10 s before the cutoff, mean relative L2 differences
are 0.350–0.445, minimum cosine similarity falls to 0.294–0.366, and individual relative differences exceed
1.0. Even earlier states change. This diagnostic does not estimate how much any particular published
score is inflated, but it establishes that post-cutoff waveform information can enter nominally pre-cutoff
MuQ states. The tested full-song encode-then-slice procedure therefore fails the declared support-isolation
requirement; independent complete-support chunk encoding is the isolation method used here.
8

<!-- Page 9 -->
Table 6: Suffix-Perturbation Audit of Full-Song MuQ Encoding
Song Cutoff Mean cos. Min cos. Rel. L2
1 19.22 s 0.923 0.366 0.350
10 19.22 s 0.890 0.307 0.445
100 24.03 s 0.899 0.294 0.429
Table 7: Protocol-Matched Forecasts of Arousal Innovation
DataHState MuQ mean MuQ relation Relation–state [adj. 97.5% CI]
PMEmo 10 s 0.028 0.315 0.417 +0.389 [0.342, 0.434]
PMEmo 15 s 0.006 0.335 0.453 +0.446 [0.370, 0.514]
DEAM holdout 10 s 0.041 0.317 0.458 +0.416 [0.391, 0.442]
DEAM holdout 15 s 0.058 0.402 0.564 +0.507 [0.475, 0.536]
Values summarize nominally pre-cutoff states in the final 10 s. The audit is intentionally an encoder
intervention rather than a model comparison: one nonzero dependence is sufficient to disprove context
isolation for full-song slicing, while the reported songs demonstrate that the effect is not confined to one
file.
4.2 Scheduled Music Provides Large Forecast Information
Table 7 measures the complete audio representation. It raises arousal-innovation CCC over the state ridge
by 0.389–0.507, and every corrected interval is above zero. The future-mean baseline reaches 0.315–0.402
CCC, while the relational trajectory reaches 0.417–0.564. The latter comparison shows that trajectory
and anchor-relative structure add information beyond average scheduled content.
PMEmo retains fewer songs at 15 s because a longer horizon requires more complete support. To
separate this composition change from the horizon comparison, we reevaluated both horizons on the
481 songs eligible at 15 s, without refitting or selecting models. At 10 s the common-song state and
complete-representation CCCs are 0.030 and 0.413 (gain 0.383; corrected lower bound 0.337); at 15 s they
are 0.006 and 0.453 (gain 0.446; lower bound 0.382). These values closely match Table 7, so the difference
between horizons is not driven by the additional 130 songs in the 10-s set.
The observed-past audio anchor does not explain the main result. Table 8 replaces the original
state ridge with the nonlinear direct-innovation model and separates past-only from future-only audio.
The future-only trajectory reaches 0.310–0.429 CCC. It exceeds the calibrated nonlinear state model
by 0.150–0.249 and a symmetric past-only trajectory by 0.151–0.261. The complete relation remains
0.268–0.382 above the calibrated nonlinear state model. Corrected lower bounds for future-minus-past
range from 0.093 to 0.236. Thus, scheduled-future information survives both stronger state modeling and
complete removal of past/current audio descriptors.
A support-localization analysis tests whether this result is merely recognition from audio close to the
target. It fits identical future-only heads to the first legal 4-s chunk, the last legal chunk, or the mean of
all legal future chunks; no past/current audio descriptor is present. AtH = 10s, the first chunk ends
5.5–6.0 s before the target; atH = 15s, it ends 10.5–11.0 s before it. Table 9 shows that this early
chunk still exceeds the calibrated HGB state model by 0.044–0.084 CCC, with positive corrected lower
bounds in all four cells. Later and complete-support representations are stronger, and the full-support
mean exceeds the early chunk by 0.076–0.198 CCC. Hence information is already present away from the
target and accumulates across the scheduled segment; the main effect cannot be reduced to reading only
target-adjacent audio. This diagnostic was not used for model or support selection.
The raw HGB predictions generate the held-out residual targets used by the three audio heads; the
calibrated HGB column above is a CCC-only state stress test and is not used for fitting. Table 10
therefore reports MAE and RMSE for this same raw-HGB attribution pipeline. The complete relational
9

<!-- Page 10 -->
Table 8: Strong-State and Past/Future Attribution. “HGB raw” is the direct-innovation output used to
form residual targets; “cal.” applies an inner-fold location–scale map only for the CCC state comparison.
DataHState ridge HGB raw/cal. Past only Future only Full relation Future–past [LB]
PMEmo 10 s 0.028 0.075/0.159 0.158 0.310 0.427 +0.151 [0.112]
PMEmo 15 s 0.006 0.081/0.127 0.163 0.323 0.462 +0.160 [0.093]
DEAM holdout 10 s 0.041 0.094/0.161 0.128 0.339 0.465 +0.211 [0.190]
DEAM holdout 15 s 0.058 0.129/0.180 0.168 0.429 0.562 +0.261 [0.236]
Table 9: Candidate-Only Localization Within the Legal Future Support (CCC)
DataHState HGB (cal.) Earliest 4 s Latest 4 s Full-support mean Early–state [LB]
PMEmo 10 s 0.159 0.243 0.285 0.319 +0.084 [0.036]
PMEmo 15 s 0.127 0.205 0.306 0.339 +0.078 [0.026]
DEAM holdout 10 s 0.161 0.241 0.290 0.338 +0.080 [0.046]
DEAM holdout 15 s 0.180 0.224 0.352 0.422 +0.044 [0.005]
representation reduces both errors relative to raw HGB in every cell. Its MAE reduction is 3.7–10.0%,
while its RMSE reduction is 10.0–18.2%. The future-only model reduces RMSE in all four cells and MAE
in three; its PMEmo 15-s MAE is 1.2% higher. Thus, the large CCC lift is not only a location–scale
calibration effect; the complete representation also lowers absolute and squared prediction error.
Figure 2(a) visualizes the information hierarchy. The large effect comes from adding a support-separated
scheduled-audio representation to recent affect.
4.3 Correct Within-Song Placement Matters
An arbitrary same-song permutation may be an easy negative. Table 11 therefore reports the two hard
controls. The local candidate is displaced by approximately 5 s and atH = 15s retains 0.615–0.629
temporal overlap with the correct permitted interval. Even under this substantial overlap, correct-minus-
local margins are 0.100–0.209 CCC. The acoustic-nearest candidate has cosine similarity 0.939–0.979 with
the correct future, yet correct-minus-nearest margins remain 0.078–0.105. All diagnostic lower bounds are
positive.
Local self-maps are 0–0.37%; acoustic-nearest self-maps are 0–8.47%, and are excluded from their
margins. Every local-placement difference is positive in all 60 repeat–fold cells. A marginal standardized-
distance diagnostic does not mark the controls as more extreme than the correct inputs, although it is not
a joint density test. The unrestricted phase-matched permutation yields larger 0.129–0.237 margins, but
the placement conclusion no longer depends on this easier comparison.
The full action lift is larger than the placement margin because a displaced segment from the same
song still supplies instrumentation, production, tempo range, and global affective style. The placement
comparison asks whether the correct location adds information after those properties are preserved, not
whether a wrong segment becomes equivalent to no music.
The placement result is also stable across training seeds and outer folds. Table 12 summarizes the
foldwise correct-minus-local diagnostic before predictions are pooled. Every one of the 15 repeat–fold
cells is positive for every dataset/horizon pair; repeat-level standard deviations are 0.0014–0.0043 CCC.
These are dispersion diagnostics rather than independent tests, while the song-cluster intervals in Table 11
remain the inferential results.
4.4 The Audio Representation Is Most Useful for Large Changes
CCC measures agreement over the complete innovation distribution, but a practical interpretation also
requires knowing where absolute-error reductions occur. Figure 3 divides each dataset/horizon cell into
quartiles of absolute ground-truth innovation, with cut points computed within that cell. The state model
10

<!-- Page 11 -->
Table 10: Absolute-Error Audit for the Strong-State Attribution Pipeline
MAE RMSE
DataHHGB raw Future only Full relation HGB raw Future only Full relation
PMEmo 10 s 0.02531 0.025250.024380.03681 0.035020.03312
PMEmo 15 s 0.03174 0.032120.030320.04545 0.043820.04052
DEAM holdout 10 s 0.05562 0.054970.052600.09283 0.084970.08004
DEAM holdout 15 s 0.07713 0.073830.069410.12250 0.108160.10019
PMEmo
10 s
PMEmo
15 s
DEAM
10 s
DEAM
15 s
0.0
0.1
0.2
0.3
0.4
0.5
0.6Arousal-innovation CCC
0.427
0.462 0.465
0.562
(a) Information hierarchy
State only Future only Full relation
PMEmo
10 s
PMEmo
15 s
DEAM
10 s
DEAM
15 s
0.00
0.05
0.10
0.15
0.20
0.25
0.30Correct-minus-control CCC
0.135
0.100
0.209
0.153
0.105
0.086 0.087
0.078
(b) T emporal-placement margins
Local shift Acoustic nearest
Figure 2: Main empirical hierarchy. (a) Candidate-only future audio is well above state, and the complete
past/future relation is higher still. (b) Correct placement remains superior after the future is replaced by
a strongly overlapping local shift or by the acoustic-nearest eligible same-song segment.
has the lowest MAE in the smallest-change quartile, where predicting almost no change is an effective
strategy. This explains why persistence is a strong local default even when its pooled CCC is low.
The ordering reverses for the largest changes. In every cell, the correctly placed audio representation
has lower Q4 MAE than both state and wrong-time audio. For example, DEAM Q4 MAE falls from 0.139
to 0.104 at 10 s and from 0.186 to 0.124 at 15 s; the wrong-time alternatives reach only 0.122 and 0.151.
PMEmo shows the same pattern. Thus, scheduled audio earns its aggregate advantage by forecasting
substantial departures from inertia, while the near-zero regime remains a boundary where a conservative
state prediction is preferable. This analysis was performed on the fixed OOF predictions and does not
alter training or selection.
4.5 Innovation-Label Reliability
Finally, split-half rater agreement provides scale for the innovation target. Randomly splitting DEAM
raters and recomputing two independent group-average arousal trajectories gives CCC 0.472 at 10 s and
0.529 at 15 s over 200 splits (95% intervals [0.450, 0.493] and [0.504, 0.553]). The complete-representation
scores of 0.458/0.564 are in the same range. This comparison is not a human-performance ceiling: each
split-half trajectory averages only about half of the raters, whereas the prediction target averages all
available raters and is therefore less noisy. A model trained across songs can estimate systematic structure
in that all-rater mean and can slightly exceed half-versus-half agreement. This comparison documents
disagreement between half panels; it neither bounds attainable performance on the all-rater target nor
quantifies the remaining room for improvement.
11

<!-- Page 12 -->
Table 11: Hard Same-Song Temporal Controls
DataHLocal shift Overlap Local margin [LB] NN cosine NN margin [LB]
PMEmo 10 s 4.86 s 0.392 +0.135 [0.108] 0.947 +0.105 [0.078]
PMEmo 15 s 4.83 s 0.629 +0.100 [0.071] 0.979 +0.086 [0.063]
DEAM holdout 10 s 5.00 s 0.375 +0.209 [0.185] 0.939 +0.087 [0.074]
DEAM holdout 15 s 5.00 s 0.615 +0.153 [0.131] 0.973 +0.078 [0.067]
Table 12: Repeat/Fold Stability of the Local-Placement Margin
DataHRepeat SD Fold range Positive
PMEmo 10 s 0.0043 [0.086, 0.192] 15/15
PMEmo 15 s 0.0035 [0.075, 0.144] 15/15
DEAM 10 s 0.0026 [0.152, 0.241] 15/15
DEAM 15 s 0.0014 [0.089, 0.175] 15/15
5 Discussion
5.1 Scheduled-Audio Forecast Information
The 0.389–0.507 CCC lift is the value of the complete scheduled-audio representation over a recent-affect
ridge. The future-only analysis shows that much of this information is present in the candidate segment
itself: it remains 0.150–0.249 above a nonlinear state model and 0.151–0.261 above past-only audio. This
is the primary result.
5.2 Content Versus Placement
Song-disjoint downstream fitting keeps held-out songs out of forecasting-head training. Overlap between
these songs and the foundation encoders’ pretraining corpora has not been excluded. This split also does
not remove global musical structure. A wrong-time segment still carries style, production, instrumentation,
tempo range, and broad affect. This explains why the complete action lift is larger than the within-song
placement margin. The overlapping-shift and acoustic-nearest controls ask a narrower question: whether
the correct location remains informative after much of the track-level and local acoustic content is preserved.
Their positive margins support temporal specificity, but the residual value of wrong-time audio also shows
that the representation uses both track-level content and local placement.
These substitutions are not listener counterfactuals. They test the sensitivity of a fitted forecast while
state and song identity are held fixed. A causal music-selection policy would require randomized or logged
actions, listener-level outcomes, and assumptions beyond those used here.
5.3 Relation to Dynamic MER
Numerical rank claims against ordinary dynamic MER would be misleading. Recognition systems often
observe acoustic context at or around the labeled moment, may align labels retrospectively, and may use
different song or window splits. Our models expose scheduled audio at a declared origin and score a later
innovation. The appropriate comparisons are therefore models trained under the same observation rules.
Within that setting, future-only audio remains useful without past descriptors, the complete representation
adds further relational structure, and the same-song controls verify temporal specificity. These results
provide a reference for the forecasting task, not a replacement for recognition benchmarks.
The same evaluation logic can apply when a future video scene, dialogue response, lesson, or notification
is scheduled before its user response is observed: declare the origin, isolate permitted feature support,
hold out contextual units, predict change, and test temporal placement with within-context substitutions.
12

<!-- Page 13 -->
0.00
0.01
0.02
0.03
0.04
0.05
0.06MAE
PMEmo, H=10 s
0.00
0.01
0.02
0.03
0.04
0.05
0.06
0.07MAE
PMEmo, H=15 s
Q1
small
Q2 Q3 Q4
large
0.000
0.025
0.050
0.075
0.100
0.125MAE
DEAM, H=10 s
Q1
small
Q2 Q3 Q4
large
0.00
0.05
0.10
0.15MAE
DEAM, H=15 s
State Correct Wrong time
Figure 3: MAE stratified by quartiles of absolute true arousal innovation. The state model is difficult to
beat for near-zero changes, whereas correctly placed audio provides the largest benefit in Q4. Wrong-time
audio retains broad song information but is consistently weaker than the correct future for large changes.
5.4 Use Case and Limitations
One immediate use is offline pre-screening rather than automated intervention. Given an observed group-
level state and a fixed set of candidate transitions, a media editor could rank or filter segments for human
review. The model would estimate expected arousal change; it would not decide which segment causes a
desired response. Practical use would additionally require calibrated uncertainty, population matching,
listener or group covariates, preference and safety constraints, and prospective validation. Consensus
labels cannot represent stable subgroups of listeners who respond in opposite ways.
The study is limited to arousal; the retained analyses do not establish corresponding results for valence.
The models use frozen MuQ representations and simple regression heads. They do not establish whether
a large fine-tuned sequence model would improve the same forecasting task.
An audit of the earlier explicit-factor experiments found that their acoustic extraction support
could cross the declared observation boundaries. We therefore exclude those factor predictors and their
augmentation, capacity, backbone, and response-delay results from the evidence reported in this preprint.
They require support-correct feature extraction and new evaluation before they can support a scientific
claim. The retained predictors use affect state and independently encoded MuQ chunks, without an
explicit-factor correction.
PMEmo and DEAM do not establish cross-cultural, artist-disjoint, or listener-specific transport. The
common-song PMEmo analysis removes the immediate 10-s/15-s composition difference, but the horizons
still represent different prediction targets and should not be interpreted as a pure response curve. Future
work should retain synchronized per-rater trajectories and metadata, group by artist or release, use a
denser set of horizons, and evaluate controlled resynthesis that changes one musical factor while preserving
others.
Finally, window counts are not independent sample sizes. Song-disjoint fitting and song-cluster
13

<!-- Page 14 -->
resampling address the main dependence, but the reported intervals remain conditional on the fixed
representation and development path. They do not replace independent replication.
5.5 Threats to Validity
Construct validity: the target is consensus perceived/expressed arousal innovation, not an individual’s felt
emotion. Split-half agreement indicates label noise, but does not resolve the construct gap.
Internal validity: outcome and encoder leakage are addressed through declared support and nesting.
Nevertheless, representations can reflect unmeasured production variables, and observational same-song
controls cannot establish intervention effects.
External validity: results cover PMEmo and an engineering-excluded DEAM evaluation pool at 10
and 15 s. They do not establish performance for other genres, cultures, annotation protocols, or longer
policies.
Statistical conclusion validity: windows are highly correlated. All splits and bootstrap units are songs,
and repeat/fold dispersion is inspected separately. Diagnostic analyses are not relabeled as confirmatory
evidence.
6 Conclusion
Music may be known before its response is known. This article formalized that distinction as dynamic
arousal forecasting with a scheduled future covariate and evaluated it under explicit rules for outcomes,
audio support, song splits, and temporal controls. A complete independently encoded MuQ representation
improved CCC by 0.389–0.507 over recent affect and remained 0.268–0.382 above a calibrated nonlinear
state model, while future-only audio remained well above both that model and a matched past-only
trajectory. The first legal 4-s chunk remained informative 5.5–11 s before the target, and correct placement
survived strongly overlapping shifts and acoustic-nearest same-song controls. These results show that
both scheduled content and its within-song timing contain forecast information.
The contribution is a known-future forecasting framework in which state, future content, and temporal
placement are evaluated separately. These results concern consensus arousal under the tested corpora
and observation rules, and do not establish causal music-selection effects or generalization to individual
listeners.
Reproducibility and Data A vailability
All experiments were executed on an Apple M5 Pro system with 24 GB unified memory. Context-isolated
MuQ extraction required 5,028 s for 28,495 PMEmo chunks and 2,851 s for 88,409 DEAM chunks; the
resulting compressed archives occupy 52 and 161 MB. The frozen MuQ encoder was used only for feature
extraction; downstream forecasting fits train PCA and ridge heads. The implementation uses explicit
seeds and records source hashes, fold assignments, eligible intervals, encoder revisions, and model settings.
The ancillary materials contain preprocessing and extraction code, forecasting implementations, same-
song control construction, grouped-bootstrap utilities, stored aggregate audits, and compressed prediction
files. A prediction-recomputation script permits inspection of the principal point estimates and intervals
without rerunning the music encoder. The preprint excludes the earlier explicit-factor predictor results
after a code audit identified centered and whole-song feature operations that did not satisfy the declared
audio-support rule. Legacy factor outputs are not evidence for this preprint’s conclusions.
PMEmo and DEAM must be obtained under their original distribution terms [8, 9]; raw audio and
individual participant records are not redistributed. Rebuilding the experiments requires those datasets
and the frozen encoder checkpoints. Fixed seeds and stored-prediction agreement support inspection but
do not certify full independent reproduction or the absence of all preprocessing errors.
14

<!-- Page 15 -->
The historical DEAM manifest records the 305 engineering songs and the settings frozen before the
complete evaluation. The current implementation’s hash differs from the method hash recorded in that
manifest. The historical manifest is preserved unchanged, but hash continuity of the current code cannot
be established from the supplied files. We therefore treat the date and original code-freeze claim as
historical provenance rather than an independently verified guarantee. The evaluation uses repeated
song-disjoint outer cross-validation within the 1,494-song pool excluded from engineering development; it
is not one permanently isolated outer test fold.
Acknowledgements
The authors thank the creators and annotators of PMEmo and DEAM for making their data available.
The authors used OpenAI Codex for language editing, document organization, reference and mathematical-
consistency review, LATEX preparation, and software-assisted checks of stored predictions and experimental
code. The authors remain responsible for the research, interpretations, and manuscript contents.
Author contributions
B.W. designed the study, implemented the method and experiments, analyzed the results, and drafted the
manuscript. D.-Q.Z. contributed to the statistical analysis and manuscript review. T.-P.T. supervised the
study and reviewed and revised the manuscript. All authors read and approved the final manuscript.
Funding
This work received no specific grant from any funding agency in the public, commercial, or not-for-profit
sectors.
A vailability of data and materials
PMEmo and DEAM must be obtained from their original distributors under their respective terms [8, 9];
source audio and individual participant records are not redistributed. The ancillary materials contain
implementation scripts, aggregate audit summaries, and compressed consensus-target prediction files for
inspecting the reported music-forecasting results. The reproducibility statement describes their scope and
verification limits.
Declarations
Competing interests
The authors declare no competing interests.
Ethics approval and consent to participate
Not applicable. This secondary analysis collected no new human-subject or animal data; it uses the
existing, publicly documented PMEmo and DEAM music-emotion annotation datasets.
Consent for publication
Not applicable.
15

<!-- Page 16 -->
References
[1] James A. Russell. A circumplex model of affect.Journal of Personality and Social Psychology, 39(6):
1161–1178, 1980. doi: 10.1037/h0077714.
[2] Erik M. Schmidt and Youngmoo E. Kim. Modeling musical emotion dynamics with conditional
random fields. InProceedings of the 12th International Society for Music Information Retrieval
Conference, pages 777–782, 2011.
[3] Felix Weninger, Florian Eyben, and Björn Schuller. On-line continuous-time music mood regression
with deep recurrent neural networks. InProceedings of the IEEE International Conference on
Acoustics, Speech and Signal Processing, pages 5412–5416, 2014. doi: 10.1109/ICASSP.2014.6854637.
[4] Yajie Ma, Xianyu Li, Min Xu, Jia Jia, and Lianhong Cai. Multi-scale context based attention
for dynamic music emotion prediction. InProceedings of the ACM Multimedia Conference, pages
1443–1450, 2017. doi: 10.1145/3123266.3123408.
[5] Liyue Zhang, Xinyu Yang, Yichi Zhang, and Jing Luo. Dual attention-based multi-scale feature
fusion approach for dynamic music emotion recognition. InProceedings of the 24th International
Society for Music Information Retrieval Conference, pages 207–214, 2023.
[6] Bryan Lim, Sercan O. Arik, Nicolas Loeff, and Tomas Pfister. Temporal fusion transformers for
interpretable multi-horizon time series forecasting.International Journal of Forecasting, 37(4):
1748–1764, 2021. doi: 10.1016/j.ijforecast.2021.03.012.
[7] Haina Zhu, Yizhi Zhou, Hangting Chen, Jianwei Yu, Ziyang Ma, Rongzhi Gu, Yi Luo, Wei Tan, and
Xie Chen. MuQ: Self-supervised music representation learning with mel residual vector quantization.
arXiv preprint arXiv:2501.01108, 2025.
[8] Kejun Zhang, Hui Zhang, Simeng Li, Changyuan Yang, and Lingyun Sun. The PMEmo dataset
for music emotion recognition. InProceedings of the ACM International Conference on Multimedia
Retrieval, pages 135–142, 2018. doi: 10.1145/3206025.3206037.
[9] Anna Aljanaki, Yi-Hsuan Yang, and Mohammad Soleymani. Developing a benchmark for emotional
analysis of music.PLOS ONE, 12(3):e0173392, 2017. doi: 10.1371/journal.pone.0173392.
[10] Dengming Zhang, Weitao You, Ziheng Liu, Lingyun Sun, and Pei Chen. Personalized dynamic music
emotion recognition with dual-scale attention-based meta-learning. InProceedings of the AAAI
Conference on Artificial Intelligence, volume 39, pages 1629–1637, 2025. doi: 10.1609/aaai.v39i2.32155.
[11] Yunrui Shang, Qi Peng, Zixuan Wu, and Yinhua Liu. Music-induced emotion flow modeling by ENMI
network.PLOS ONE, 19(10):e0297712, 2024. doi: 10.1371/journal.pone.0297712.
[12] Soroosh Mariooryad and Carlos Busso. Correcting time-continuous emotional labels by modeling
the reaction lag of evaluators.IEEE Transactions on Affective Computing, 6(2):97–108, 2015. doi:
10.1109/TAFFC.2014.2334294.
[13] Soheil Khorram, Melvin G. McInnis, and Emily Mower Provost. Jointly aligning and predicting
continuous emotion annotations.IEEE Transactions on Affective Computing, 12(4):1069–1083, 2021.
doi: 10.1109/TAFFC.2019.2917047.
[14] Yizhi Li, Ruibin Yuan, Ge Zhang, Yinghao Ma, Xingran Chen, Hanzhi Yin, Chenghao Xiao, Chenghua
Lin, Anton Ragni, Emmanouil Benetos, et al. MERT: Acoustic music understanding model with
large-scale self-supervised training. InInternational Conference on Learning Representations, 2024.
16

<!-- Page 17 -->
[15] Jaeyong Kang and Dorien Herremans. Towards unified music emotion recognition across dimensional
and categorical models.arXiv preprint arXiv:2502.03979, 2025.
[16] Rashini Liyanarachchi, Aditya Joshi, and Erik Meijering. A survey on multimodal music emotion
recognition.arXiv preprint arXiv:2504.18799, 2025.
[17] Tuomas Eerola, Olivier Lartillot, and Petri Toiviainen. Prediction of multidimensional emotional
ratings in music from audio using multivariate regression models. InProceedings of the 10th
International Society for Music Information Retrieval Conference, pages 621–626, 2009.
[18] Patrik N. Juslin and Daniel Västfjäll. Emotional responses to music: The need to consider underlying
mechanisms.Behavioral and Brain Sciences, 31(5):559–575, 2008. doi: 10.1017/S0140525X08005293.
[19] Elliot X. Pring, Kirk N. Olsen, Anthony E. D. Mobbs, and William Forde Thompson. Music
communicates social emotions: Evidence from 750 music excerpts.Scientific Reports, 14:27766, 2024.
doi: 10.1038/s41598-024-78156-1.
[20] Yiming Gu, Chen Shao, Jingze Li, and Yinghan Fan. Interpretable deep learning reveals distinct
spectral and temporal drivers of perceived musical emotion.Scientific Reports, 16:4205, 2026. doi:
10.1038/s41598-025-34238-2.
[21] Stefan Koelsch, Peter Vuust, and Karl Friston. Predictive processes and the peculiar case of music.
Trends in Cognitive Sciences, 23(1):63–77, 2019. doi: 10.1016/j.tics.2018.10.006.
[22] Vincent K. M. Cheung, Peter M. C. Harrison, Stefan Koelsch, Marcus T. Pearce, Angela D. Friederici,
and Lars Meyer. Cognitive and sensory expectations independently shape musical expectancy and
pleasure.Philosophical Transactions of the Royal Society B: Biological Sciences, 379(1895):20220420,
2024. doi: 10.1098/rstb.2022.0420.
[23] Daojun Liang, Jing Chen, Xiao Wang, Yinglong Wang, and Shuo Li. DeepBooTS: Dual-stream
residual boosting for drift-resilient time-series forecasting. InProceedings of the AAAI Conference on
Artificial Intelligence, volume 40, pages 23391–23400, 2026. doi: 10.1609/aaai.v40i28.39509.
[24] Jieting Wang, Xiaolei Shang, Feijiang Li, and Furong Peng. RI-Loss: A learnable residual-informed
loss for time series forecasting. InProceedings of the AAAI Conference on Artificial Intelligence,
volume 40, pages 26277–26284, 2026. doi: 10.1609/aaai.v40i31.39832.
[25] Lester Mackey, Vasilis Syrgkanis, and Ilias Zadik. Orthogonal machine learning: Power and limitations.
InProceedings of the 35th International Conference on Machine Learning, volume 80 ofPMLR, pages
3375–3383, 2018.
[26] Lang Liu, Carlos Cinelli, and Zaid Harchaoui. Orthogonal statistical learning with self-concordant loss.
InProceedings of the 35th Conference on Learning Theory, volume 178 ofPMLR, pages 5253–5277,
2022.
[27] Marc Lipsitch, Eric Tchetgen Tchetgen, and Ted Cohen. Negative controls: A tool for detecting
confounding and bias in observational studies.Epidemiology, 21(3):383–388, 2010. doi: 10.1097/EDE.
0b013e3181d61eeb.
[28] Lawrence I-Kuei Lin. A concordance correlation coefficient to evaluate reproducibility.Biometrics,
45(1):255–268, 1989.
[29] Christoph Bergmeir and José M. Benítez. On the use of cross-validation for time series predictor
evaluation.Information Sciences, 191:192–213, 2012. doi: 10.1016/j.ins.2011.12.028.
17