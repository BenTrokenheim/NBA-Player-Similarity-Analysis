# NBA-Player-Similarity-Analysis
This project was created by by @BenTrokenheim and @ssfb1430

## Overview
In this project, we aimed to use natural language processing models to uncover similarities in scouting reports of basketball players in the 2024 class compared to past draft picks. For this project, we took prospect write-ups from The Ringer's Kevin O'Connor over the past eight seasons (2017-2024) and used latent sentiment analysis and cosine similarity to calculate similarity scores between the text in prospects’ scouting reports.

## Data Set
Each scouting report has statistical information about the player such college stats, wingspan, height, and weight, as well as a brief player headline and lengthy descriptions of pluses and minuses. For this project, we were only interested in analyzing the text from the Pluses and Minuses sections.

## Machine Learning Model
For the machine learning model, we used Latent Sentiment Analysis to capture the underlying themes across the scouting reports. By reducing the dimensionality of the data, LSA enabled us to uncover the most important concepts across scouting reports, allowing for more accurate comparisons between players. Determining the right number of components involved weighting a trade-off between bias and variange. Too many components and the model might overfit, but too few components risks oversimplifying the data. We determined that the optimal number of components was 46 by evaluating the coherence scores generated from different numbers of components. What the coherence scores measured was how similar the terms in each component was related to each other. 36 components provided enough complexity to capture the significant themes in the data without introducing excessive noise or reducing interpretability. Next, we generated cosine similarity scores to quantify the similarity between players based on their scouting reports, which measures the cosine angle between two players' vectors in a high dimensional space. Finally, we decided to score each prospect using a weighted average of similar player's Daily Plus Minus (DPM) score. We opted for DPM because it is the most preferred composite catch-all statistic among NBA professionals.

## Results and Analysis
Using these metrics, we can analyze prospects in several meaningful ways. First, we employed cosine similarity scores to compare players from the 2017-2023 period with those in the 2024 draft class. This approach allowed us to identify which current prospects closely resemble players from previous years. 

For instance, here are the most similar players to the #1 pick Zaccharie Risacher, along with their respective similarity scores:
- Ochai Agbaji with similarity score: 0.7613
- Andrew Nembhard with similarity score: 0.7442
- Christian Braun with similarity score: 0.7067
- Ben Sheppard with similarity score: 0.6798
- Jd Davison with similarity score: 0.6627

Similarly, for the #2 pick Alex Sarr, the closest matches were:
- Scoot Henderson with similarity score: 0.6813
- Victor Wembanyama with similarity score: 0.6764
- Jarace Walker with similarity score: 0.6671
- Colby Jones with similarity score: 0.6604
- Keyontae Johnson with similarity score: 0.6506

Using these rankings, we can examine player comparisons of interest for noteworthy prospects. Looking at the text from these reports, we can see why players like Zaccharie Risacher and Ochai Agbaji are so similar. They are both described as being versatile players in transition with long arms that are big advantages on defense. Analyzing scouting report language from similar players can provide insight into potential ceilings and floors these players can develop into.

Additionally, we calculated composite scores for each player by combining the similarity ratings with Defensive Player Metrics (DPM) of their most similar counterparts. For instance:
- Alex Sarr's composite score: -1.25
- Zaccharie Risacher's composite score: -1.44

The league median for DPM is -0.96, so scores around -1.00 are generally considered solid for incoming rookies.
We sorted all draft prospects by their composite DPM scores, revealing the following rankings:
1.              yves missi       0.269086
2.           bobi klintman       0.153924
3.             jamal shead       0.123689
4            oso ighodaro       0.105067
5        tristan da silva       0.063410
6             judah mintz      -0.010741
7                 pj hall      -0.068733
8             kel'el ware      -0.081553
9          ulrich chomche      -0.100972
10       cameron christie      -0.108806
11              adem bona      -0.124486
12          reed sheppard      -0.178148
13           izan almansa      -0.205795
14           alex karaban      -0.331152
15          melvin ajinca      -0.341247
16           dillon jones      -0.362502
17        donovan clingan      -0.412829
18              zach edey      -0.469285
19         keshad johnson      -0.487202
20         stephon castle      -0.533169
21            baba miller      -0.536990
22         tristen newton      -0.541882
23           devin carter      -0.573241
24              ryan dunn      -0.617934
25           quinten post      -0.632071
26          pacome dadiet      -0.642996
27     carlton carrington      -0.658448
28              dj wagner      -0.702616
29          matas buzelis      -0.737676
30           bronny james      -0.789669
31          jalen bridges      -0.799387
32          reece beekman      -0.805253
33         kyshawn george      -0.808362
34     zaccharie risacher      -0.873763
35        harrison ingram      -0.881020
36            cam spencer      -0.903628
37        kyle filipowski      -0.904070
38           nikola topic      -0.953428
39          ajay mitchell      -0.953772
40         thierry darlan      -0.958948
41          cody williams      -0.989087
42         isaiah collier      -1.038281
43        coleman hawkins      -1.050343
44             mark sears      -1.076237
45            ron holland      -1.120780
46          pelle larsson      -1.122394
47           jared mccain      -1.129424
48            tyler smith      -1.146945
49         ja'kobe walter      -1.156459
50     kevin mccullar jr.      -1.161154
51        daron holmes ii      -1.169968
52            zyon pullin      -1.190015
53            tyler kolek      -1.197179
54          johnny furphy      -1.227214
55              alex sarr      -1.227308
56         tidjane salaun      -1.266673
57             aj johnson      -1.293075
58      baylor scheierman      -1.307401
59          hunter sallis      -1.311549
60  terrence shannon, jr.      -1.422513
61          dalton knecht      -1.430549
62         trevon brazile      -1.457191
63        payton sandfort      -1.462614
64           jaylon tyson      -1.499974
65          jamir watkins      -1.504365
66        nikola djurisic      -1.635081
67        trentyn flowers      -1.657588
68             kj simpson      -1.751095
69         justin edwards      -1.759367
70         rob dillingham      -2.000928

The composite scores provide a quantatitive way to assess these players, however a more robust analysis is needed to assess their accuracy and if there is any correlation with draft position and future DPM.

## Future Directions
One potential direction for future research is to revisit the expected DPM values for the 2024 players after the next  season to see how closely these values align with their actual performance. This comparison would provide insight into the predictive accuracy of our model and its practical applications.

Another area for improvement involves refining our model by training it on players from the 2023 class. By using more recent data, we could enhance the model's ability to identify relevant patterns and improve the accuracy of the similarity scores.

Finally, incorporating positional attributes, college statistics, and the player headline into the similarity rankings could add depth and detail to the analysis. This integration would allow the model to consider a broader range of factors when comparing players, potentially leading to more nuanced and accurate similarity rankings.
