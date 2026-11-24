Flow Moods: Recommending Music by Moods on Deezer
THÉOBONTEMPELLI,BENJAMINCHAPUS,FRANÇOISRIGAUD,MATHIEUMORLON,MARIN
LORANT, and GUILLAUME SALHA-GALVAN,Deezer,France
The music streaming service Deezer extensively relies on its Flow algorithm, which generates personalized radio-style playlists of
songs, to help users discover musical content. Nonetheless, despite promising results over the past years, Flow used to ignore the
moods of users when providing recommendations. In this paper, we present Flow Moods, an improved version of Flow that addresses
this limitation. Flow Moods leverages collaborative filtering, audio content analysis, and mood annotations from professional music
curators to generate personalized mood-specific playlists at scale. We detail the motivations, the development, and the deployment of
arXiv:2207.11229v1  [cs.IR]  15 Jul 2022
this system on Deezer. Since its release in 2021, Flow Moods has been recommending music by moods to millions of users every day.
CCS Concepts: • Information systems → Recommender systems; Personalization.
Additional Key Words and Phrases: Music Recommendation, Moods, Music Streaming Service, Real-World Deployment
ACM Reference Format:
Théo Bontempelli, Benjamin Chapus, François Rigaud, Mathieu Morlon, Marin Lorant, and Guillaume Salha-Galvan. 2022. Flow Moods:
Recommending Music by Moods on Deezer. In Sixteenth ACM Conference on Recommender Systems (RecSys ’22), September 18–23, 2022,
Seattle, WA, USA. ACM, New York, NY, USA, 5 pages. https://doi.org/10.1145/3523227.3547378
1 INTRODUCTION
Recommender systems are an essential part of music streaming services [1, 13, 20, 21]. They allow users to discover new
songs or artists they may like within large music catalogs, and they are known to improve the overall user experience
on these services [5, 22]. In particular, the French music streaming service Deezer [7], offering 90 million music tracks
to 16 million active users from 180 countries, extensively relies on its homemade Flow feature to recommend music.
Flow materializes as a simple button, proposed to Deezer users on the homepage of the service. A click on this button
launches a personalized and virtually infinite radio-style playlist of songs, computed internally using collaborative
filtering methods [3, 16]. However, despite promising results over the past years, Flow used to ignore the moods of
users when generating playlists. This was a limitation since, as we detail in the next section, users can perceive the
same recommendation very differently depending on their current state of mind [10, 17, 19].
In this paper, we present Flow Moods, an improved version of Flow that addresses this limitation. Flow Moods invites
users to specify their current mood among six pre-defined categories (“Chill”, “Focus”, “Melancholy”, “Motivation”,
“Party”, and “You & Me”), and generates personalized playlists in accordance with this mood. Since its global release in
October 2021, Flow Moods has been used by millions of Deezer users every day. This paper is organized as follows. In
Section 2.1, we further detail our motivations for such a system. In Section 2.2, we describe the challenges we faced and
our practical solutions to develop Flow Moods, combining collaborative filtering, audio content analysis, and mood
annotations from professional music curators. Then, in Section 2.3, we explain how Flow Moods was deployed on Deezer,
and we analyze its empirical performance on the service. We conclude and discuss areas of improvement in Section 3.
Permission to make digital or hard copies of part or all of this work for personal or classroom use is granted without fee provided that copies are not
made or distributed for profit or commercial advantage and that copies bear this notice and the full citation on the first page. Copyrights for third-party
components of this work must be honored. For all other uses, contact the owner/author(s).
©2022 Copyright held by the owner/author(s).
Manuscript submitted to ACM
1
RecSys ’22, September 18–23, 2022, Seattle, WA, USA
T. Bontempelli, et al.
Fig. 1. Interface of Flow Moods on the Deezer mobile app. After clicking on the Flow button on the homepage (left), the user can select
a moodonan interactive wheel(middle). This generates a mood-specific personalized playlist of songs (right), computed as described in
Section 2.2. Note: a click at the center of the wheel would launch the “regular” Flow algorithm ignoring moods, described in Section 2.1.
2 FLOWMOODS,APERSONALIZEDJUKEBOXPLAYINGMUSICBYMOODS
2.1 Generating Personalized Playlists with Flow
2.1.1 The Flow Feature. First launched in 2014, Flow is an exclusive feature helping Deezer users discover and enjoy
musical content. As illustrated in Figure 1 (left), it materializes as a simple button, appearing on the homepage of any
user having at least 16 favorite songs or artists. A click on this button launches a virtually infinite radio-style playlist of
songs, mixing the user’s favorite ones along with new personalized recommendations. To generate these playlists, we
leverage a latent model for collaborative filtering [3, 16]. By analyzing usage data on Deezer1, this model learns vector
representations of users and songs, in the same embedding space where proximity should reflect musical preferences [5].
Then, a homemade algorithm1 navigates in this space, identifies songs whose vectors are close to each user, reorders
them using internal heuristics, and recommends them within Flow. This algorithm is adaptive to user feedback: users
can like songs, skip them, and manually exclude songs or artists from future recommendations.
2.1.2 Limitation. Over the years, numerous users have adopted Flow as their personalized jukebox. Nonetheless, they
also sometimes criticized it for launching songs “at the wrong time”. For instance, some users reported that, while they
enjoyed listening to calming music when focusing at work or when relaxing, they did not want such music to appear in
their Flow playlists when partying on a Friday night or when doing sport. This example illustrates that people listen to
music differently depending on the context [11, 17], which Flow used to overlook. This was an important limitation since,
as emphasized in the scientific literature, a user’s current state of mind, thoughts, or activities can extensively impact the
way the same recommendation will be perceived [10, 17, 19]. For Deezer users, it was furthermore arduous to redirect
Flow to fit their context using the available interactions (likes, skips, and exclusions), strengthening their frustration.
2.2 From Flow to Flow Moods
2.2.1 Mood Selection. Developed in 2021, the Flow Moods system aims to address this limitation, by encouraging
users to provide contextual information before recommending any music. Specifically, Flow Moods invites users to
1Technical details on the exact input data, and on the algorithm for playlist generation, are voluntarily omitted in this paper for confidentiality reasons.
2
Flow Moods: Recommending Music by Moods on Deezer
RecSys ’22, September 18–23, 2022, Seattle, WA, USA
Table 1. Description of the six moods, as adver
tised in a Deezer public communication [12].
Mood
Description
Chill
Time to kick back? Relax with your favorite
artists that help you unwind and let go.
Focus
Melancholy
Motivation
No distractions, please! Let us help you stay
in your zone with the right kind of music
to help you achieve your goal.
We all get the blues now and then. If you
are in the mood for a good cry or want
to wallow in sorrow– let it all out here.
Need a little nudge? Make workouts a
joyful experience with a power mix
to keep you moving.
Party
Whether it’s a party of one or party of more,
get in the spirit with an endless mix of
crowd-pleasing music to get you dancing.
You &Me
Feeling a little frisky? Let us set the mood
for romance with feel-good tracks that
you and your partner will love.
30
25
20
15
Streams (in %)
10
Motivation
Chill
Party
Focus
Melancholy
You & Me
5
Mon. 4th
Tue. 5th
Wed. 6th
Thu. 7th
Fri. 8th
Sat. 9th
Sun. 10th
Mon. 11th
Tue. 12th
Wed. 13th
Thu. 14th
Fri. 15th
Sat. 16th
Sun. 17th
Fig. 2. Daily distribution of streams by Flow Moods category (April 4th to 17th, 2022).
select their current mood, by interacting with the wheel illustrated in Figure 1 (middle). At Deezer, we pre-selected
six contextual moods that, according to internal investigations conducted with product and user experience teams,
particularly impact the way users listen to music. These six moods, named “Chill”, “Focus”, “Melancholy”, “Motivation”,
“Party”, and “You & Me”, are described in Table 1. As these names suggest, we adopted a relatively broad definition of
the term “mood”, simultaneously encompassing emotions– which is often used as a synonym of moods [15]– and
activities associated with specific states of mind.
2.2.2 Mood Annotations from Music Experts. The objective of Flow Moods is to recommend personalized playlists
matching the mood selected by each user. Nonetheless, associating music with moods is a challenging task [8, 9].
To address this problem, we collaborated with professional music curators from Deezer. These music experts manually
annotated thousands of songs that, based on their expertise, comply or do not comply with each of the six pre-selected
moods–e.g., they manually identified thousands of “Chill” and “Not Chill” songs. This annotation work, covering songs
from various music genres and countries, provided valuable mood labels that we treat as ground truth in the following.
2.2.3 Large-Scale Audio-Based Mood Classification. However, it was practically impossible for music curators to
manually annotate all the recommendable content from the Deezer catalog, which includes millions of songs. To address
this problem, we chose to leverage audio data. Specifically, we computed a 256-dimensional embedding vector for
each song from its audio signal, using a VGG-like [6] convolutional neural network designed for music audio tagging
tasks [18]. This model is publicly available within the musicnn Python library [18]. Then, we used these vectors as
input for six random forest binary classifiers [4]. Each of them returns a “mood score” between 0 and 1, estimating the
likelihood of the presence of one of the six moods in each song. We trained these six classifiers using songs manually
annotated with ground truth moods as the training set. We subsequently employed the trained models to infer moods
from the vectors of unannotated songs. Using this strategy, we collected mood scores for millions of songs from the
Deezer catalog and for each of the six moods under consideration. Some songs obtained high scores for several moods.
2.2.4 Mood-Specific Playlist Generation. Finally, we combined these mood scores with the collaborative filtering
system from Section 2.1.1 to generate personalized mood-specific playlists. Flow Moods still recommends songs close
to each user in the user-song embedding space, but now also filters them by moods. Precisely, we only recommend
3
RecSys ’22, September 18–23, 2022, Seattle, WA, USA
T. Bontempelli, et al.
songs with scores larger than a fixed threshold for the selected mood. In addition, Flow Moods includes a fallback
system, which recommends pre-selected songs when users who do not have enough neighbors associated with the
requested mood in the user-song embedding space.
2.3 Deploying Flow Moods on Deezer
2.3.1 System Deployment. After weeks of internal tests, Flow Moods was released globally on the Deezer mobile app
in October 2021. Since March 2022, Flow Moods is also available on the desktop version of Deezer. From a technical
standpoint, we designed this system for online production use on large-scale services. Song-related data, including
mood scores, embedding vectors, and metadata, are exported daily in a Cassandra cluster. They are updated weekly,
e.g., to take into account changes in mood classification models. Computation services run on a Kubernetes cluster.
Playlist generation operations, including song filtering, reordering, and adaptation to user feedback, are computed on a
Scala server. For scalability reasons, we use approximate nearest neighbors techniques to retrieve songs whose vectors
are close to each user in the user-song embedding space, via a Golang application that includes the Faiss library [14].
2.3.2 Empirical Analysis. Since its release, Flow Moods has been recommending music by moods to millions of users
every day. Over the last months, we observed the improvement of several internal performance indicators, such as
the penetration rate of the Flow feature, i.e., the percentage of users listening to music via Flow (we omit numbers for
confidentiality reasons). Flow Moods has also been covered in press articles and has generated numerous reactions on
social media such as Twitter, which we will discuss during the presentation associated with this paper. Lastly, we report
in Figure 2 the daily distribution of streams by Flow Moods categoryover two whole weeks.Weobservethat“Motivation”
consistently appears as the most streamed mood, while the usage of “Party” significantly increases on Fridays and
weekends. Users also tend to “Focus” more on weekdays, and to “Chill” slightly more on Sundays. These observations,
confirmed over longer periods, provide valuable insights illustrating how users listen to music on Deezer over time.
3 CONCLUSIONAND DISCUSSION
In this paper, we presented Flow Moods, a personalized jukebox recommending music by moods at scale. Flow Moods
was successfully deployed on the music streaming service Deezer in 2021. Besides its promising performance, this
system helps us to study interactions between users and music (e.g., are the temporal differences from Figure 2 similar
across countries?). Our team also plans to further investigate correlations between moods and music genres (e.g., is
the “You & Me” classifier essentially learning soul songs?), and to develop tools to spot discrepancies between score
predictions and manual annotations from music curators. Moreover, future work will aim to improve Flow Moods by
examining more advanced models for music mood detection. For instance, while our current classifiers only rely on
audio signals, we could consider complementing them with lyrics data, as in the work of Delbouys et al. [8]. We could
also aim to extend the current system to provide other contextual recommendations, e.g., a “Christmas” version of Flow
in December. These future research directions would definitely help improving music personalization on Deezer.
SPEAKER BIO
Théo Bontempelli is a data scientist at Deezer. In the Recommendation team, he designs and deploys large-scale
machine learning systems to improve music recommendation on the service.Hisrecentworkoncarouselpersonalization
using contextual bandits [2] was nominated among the “best short paper candidates” at the RecSys 2020 conference.
4
Flow Moods: Recommending Music by Moods on Deezer
RecSys ’22, September 18–23, 2022, Seattle, WA, USA
REFERENCES
[1] Darius Afchar, Alessandro B Melchiorre, Markus Schedl, Romain Hennequin, Elena V Epure, and Manuel Moussallam. 2022. Explainability in Music
Recommender Systems. AI Magazine 43 (2022), 190–208.
[2] Walid Bendada, Guillaume Salha, and Théo Bontempelli. 2020. Carousel Personalization in Music Streaming Apps with Contextual Bandits.
Proceedings of the 14th ACM Conference on Recommender Systems (2020), 420–425.
[3] Dheeraj Bokde, Sheetal Girase, and Debajyoti Mukhopadhyay. 2015. Matrix Factorization Model in Collaborative Filtering Algorithms: A Survey.
Procedia Computer Science 49 (2015), 136–146.
[4] Leo Breiman. 2001. Random Forests. Machine Learning 45, 1 (2001), 5–32.
[5] Léa Briand, Guillaume Salha-Galvan, Walid Bendada, Mathieu Morlon, and Viet-Anh Tran. 2021. A Semi-Personalized System for User Cold Start
Recommendation on Music Streaming Apps. Proceedings of the 27th ACM SIGKDD Conference on Knowledge Discovery and Data Mining (2021),
2601–2609.
[6] Keunwoo Choi, George Fazekas, and Mark Sandler. 2016. Automatic Tagging using Deep Convolutional Neural Networks. Proceedings of the 17th
International Society for Music Information Retrieval Conference (2016), 805–811.
[7] Deezer. 2022. https://www.deezer.com.
[8] Rémi Delbouys, Romain Hennequin, Francesco Piccoli, Jimena Royo-Letelier, and Manuel Moussallam. 2018. Music Mood Detection Based on Audio
and Lyrics with Deep Neural Net. Proceedings of the 19th International Society for Music Information Retrieval Conference (2018), 370–375.
[9] Mehmet Bilal Er and Ibrahim Berkan Aydilek. 2019. Music Emotion Recognition by using Chroma Spectrogram and Deep Visual Features.
International Journal of Computational Intelligence Systems 12, 2 (2019), 1622–1634.
[10] Bruce Ferwerda, Markus Schedl, and Marko Tkalcic. 2015. Personality & Emotional States: Understanding Users’ Music Listening Needs. Posters,
Demos, Late-breaking Results and Workshop Proceedings of the 23rd Conference on User Modeling, Adaptation, and Personalization 1388 (2015).
[11] Alinka E Greasley and Alexandra Lamont. 2011. Exploring Engagement with Music in Everyday Life using Experience Sampling Methodology.
Musicae Scientiae 15, 1 (2011), 45–71.
[12] Isobel Hambleton. 2022. Get in Touch with your Feelings with Flow Moods. Blog post on: https://www.deezer-blog.com/press/flow-moods/.
[13] Kurt Jacobson, Vidhya Murali, Edward Newett, Brian Whitman, and Romain Yon. 2016. Music Personalization at Spotify. Proceedings of the 10th
ACM Conference on Recommender Systems (2016), 373–373.
[14] Jeff Johnson, Matthijs Douze, and Hervé Jégou. 2019. Billion-Scale Similarity Search with GPUs. IEEE Transactions on Big Data 7, 3 (2019), 535–547.
[15] Youngmoo E Kim, Erik M Schmidt, Raymond Migneco, Brandon G Morton, Patrick Richardson, Jeffrey Scott, Jacquelin A Speck, and Douglas
Turnbull. 2010. Music Emotion Recognition: A State of the Art Review. Proceedings of the 11th International Society for Music Information Retrieval
Conference 86 (2010), 937–952.
[16] Yehuda Koren and Robert Bell. 2015. Advances in Collaborative Filtering. Recommender Systems Handbook (2015), 77–118.
[17] Adrian C North and David J Hargreaves. 1996. Situational Influences on Reported Musical Preference. Psychomusicology: A Journal of Research in
Music Cognition 15, 1-2 (1996), 30.
[18] Jordi Pons and Xavier Serra. 2019. musicnn: Pre-trained Convolutional Neural Networks for Music Audio Tagging. Late Breaking/Demo Session of
the 20th International Society for Music Information Retrieval Conference (2019).
[19] Peter J Rentfrow, Lewis R Goldberg, and Ran Zilca. 2011. Listening, Watching, and Reading: The Structure and Correlates of Entertainment
Preferences. Journal of Personality 79, 2 (2011), 223–258.
[20] Guillaume Salha-Galvan, Romain Hennequin, Benjamin Chapus, Viet-Anh Tran, and Michalis Vazirgiannis. 2021. Cold Start Similar Artists Ranking
with Gravity-Inspired Graph Autoencoders. Proceedings of the Fifteenth ACM Conference on Recommender Systems (2021), 443–452.
[21] Markus Schedl, Hamed Zamani, Ching-Wei Chen, Yashar Deldjoo, and Mehdi Elahi. 2018. Current Challenges and Visions in Music Recommender
Systems Research. Proceedings of the International Journal of Multimedia Information Retrieval 7, 2 (2018), 95–116.
[22] Shuai Zhang, Lina Yao, Aixin Sun, and Yi Tay. 2019. Deep Learning Based Recommender System: A Survey and New Perspectives. ACM Computing
Surveys (CSUR) 52, 1 (2019), 1–38.
5