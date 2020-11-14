# Goal and Background
The goal of this project is to detect trends in twitter accounts who's target audience is accounts interested general health. This data was provided from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter).

# Motivation

Initially, the goal of this project was to perform a very similar analysis on Donald Trump's rally speeches leading up to the 2020 presidential election. The hope was that I would be able to group words together in a meaningful way, such that I would be able to extract topics from his speeches. While I am still working to finalize that project, this accomplishes a similar task, and has better prepared me to revisit that goal.

# Navigation (Need to link notebooks)

[Technical NoteBook](https://github.com/miles-frankllin/Data_602_Hw_2/blob/main/Hw_2/Notebooks/Technical_Notebook.ipynb) -
[Additional Notebok](https://github.com/miles-frankllin/Data_602_Hw_2/blob/main/Hw_2/Notebooks/Exploring_Health_Tweets_Data.ipynb) -
[Data Soucre](https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter)

# Requirements
<pre>
Languages    : Python 3.8.3
Tools/IDE    : Anaconda
Libraries    : pandas, re, glob, textblob, nltk, string, numpy, sns, 
               matplotlib.plt, wordcloud, genism, sklearn, yellowbrick
</pre>

# Data Sources

## Source Data
<pre>
File Name      : bbchealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 3929 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : cbchealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 3741 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : cnnhealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 4061 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : everydayhealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 3239 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : foxnewshealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 2000 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : gdnhealthcare.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 2997 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : goodhealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 7864 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : KaiserHealthNews.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 3509 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : latimeshealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 4171 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : msnhealthnews.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 3199 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : NBChealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 4215 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : nprhealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 4837 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : nytimeshealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 6245 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : reuters_health.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 4719 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : usnewshealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 1400 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>
<pre>
File Name      : wsjhealth.txt
URL            : https://archive.ics.uci.edu/ml/datasets/Health+News+in+Twitter
Limitations    : N/A
Concerns       : N/A
Dimensions     : 3200 rows × 3 columns
Columns        : "tweet id", "date and time", "tweet"
</pre>

## Cleaned Data
<pre>
File Name      : df.csv
URL            : N/A
Limitations    : N/A
Concerns       : N/A
Dimensions     : 63326 rows × 7 columns
Columns        : tweet id (int64), date and time (object), tweet (object), source_file (object)
</pre>
<pre>
File Name      : df_cleaned.csv
URL            : N/A
Limitations    : N/A
Concerns       : N/A
Dimensions     : 63326 rows × 7 columns
Columns        : tweet id (int64), date and time (object), tweet (object), source_file (object), Subjectivity (float64), Polarity (float64), source (object)
</pre>
<pre>
File Name      : df_cleaned_clusters.csv
URL            : N/A
Limitations    : N/A
Concerns       : N/A
Dimensions     : 63326 rows × 7 columns
Columns        : tweet id (int64), date and time (object), tweet (object), source_file (object), Subjectivity (float64), Polarity (float64), source (object), cluster (int64)
</pre>
<pre>
File Name      : df_tfidf.csv
URL            : N/A
Limitations    : N/A
Concerns       : N/A
Dimensions     : 63326 rows × 75 columns
Columns        : (float64)
</pre>
<pre>
File Name      : all_tweets.csv
URL            : N/A
Limitations    : N/A
Concerns       : N/A
Dimensions     : 63326 rows × 1 columns
Columns        : tweet (object)
</pre>
<pre>
File Name      : all_tweets_cleaned.csv
URL            : N/A
Limitations    : N/A
Concerns       : N/A
Dimensions     : 63326 rows × 7 columns
Columns        : tweet (object)
</pre>

# References
<pre>
URL            : https://www.youtube.com/watch?v=Frzg1b5Wn7I&list=PLHutrxqbP1Bx-zZxtex-EgwMFsjjjwYGO&index=10
Author         : LBSocial
Purpose        : A helpful guide to clustering on twitter data.
</pre>
<pre>
URL            : https://www.youtube.com/watch?v=lbR5br5yvrY&list=PLLssT5z_DsK-h9vYZkQkYNWcItqhlRJLN&index=80
Author         : Andrew Ng
Purpose        : A helpful videio for understanding how to choose the number of clusters in a K-Means model.
</pre>
