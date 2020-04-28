# Course: Unstructured and Distributed Data Modeling and Analysis
#### MSBX 5420 Spring 2020 | Instructor: Dr. Peigang (Peter) Zhang

## Big-Data Project: Sentiment Analysis using Pyspark on coronavirus/COVID-19 news

### Executive Summary:
* We are using the Kaggle dataset on CBC News coronavirus/COVID-19 articles. Our analysis will use Spark with Python, AWS Classroom in order to examine the effects of COVID 19 in the news and how the media has covered this new pandemic.

### Contributors:
* Junji Wiener - GitHub: 8Jun
* Fairy Gandhi - GitHub: FairyGandhi
* Meredith Synnott - GitHub: meredithsynnott
* Whitney Carter - GitHub: Carter-and
* Aldo Peter - GitHub: Aldospy

### Objective:
* The objective of this project is to put into action the big data technology (Hadoop, PySpark, AWS, S3) that we have learned about this semester to ingest a large data set, use basic statistics and analysis of the ingested data set, and display (using Jupyter notebook or other type of visualization) the data set. The application should also show horizontal scaling.

### Data Set:
* https://www.kaggle.com/ryanxjhan/cbc-news-coronavirus-articles-march-26

### Overview:

### Languages and Tools used:
* Python (NumPy, Pandas, Matplotlib, Seaborn, Wordcloud)
* Hadoop
* Apache Spark (PySpark)
* AWS (S3, EMR)
* Jupyter Notebook

### Tasks:
To understand how the main focus of CBC news articles has evolved during this COVID -19 affected time period by doing the following:
  * Analyzing the trend with the word count of the articles.
  * Analyzing the keywords of articles every month using the wordcloud.
  * Performing Sentiment Analysis on texts by caculating the polarity score (NLP).

## [Link to Code file](https://github.com/MSBX5420/team-mount-elbert/blob/master/Project%20Code.ipynb)

### Code Sample:
``` python
#clean columns, remove smybols
from pyspark.sql.functions import *
def cleanColumn(tmpdf,colName,findChar,replaceChar):
    tmpdf = tmpdf.withColumn(colName, regexp_replace(colName, findChar, replaceChar))
    return tmpdf

allColNames = news_df.schema.names
charToRemove= "[\"!@#$%^&*\(\)\{\}\[\]\'\'""',.?/:;-=+`~'...''..']"
replaceWith =""
for colName in allColNames:
    news_df=cleanColumn(news_df,colName,charToRemove,replaceWith)

#drop rows with NAs/ Null values
def dropNA (tmpdf2,columnName):
    tmpdf2 = tmpdf2.where(col(columnName).isNotNull())
    return tmpdf2

columnName = ["authors","title","publish_date","description","text","url"]
allColNames2 = news_df.schema.names

for columnName in allColNames2:
    news_df = dropNA(news_df,columnName)
```

### Project Code Visuals:
![Word Frequency](https://github.com/MSBX5420/team-mount-elbert/blob/master/graph%20images/word%20count.svg)

![Word Cloud](https://github.com/MSBX5420/team-mount-elbert/blob/master/graph%20images/word%20cloud.svg)

![Polarity Histogram](https://github.com/MSBX5420/team-mount-elbert/blob/master/graph%20images/polarity%20hist.svg)

![Author Polarity Boxplot](https://github.com/MSBX5420/team-mount-elbert/blob/master/graph%20images/polarity%20author.svg)

## [Link to Presentation](https://docs.google.com/presentation/d/1eGTa4n1hRyZK8-APtACCzJIBFhgsQEtI_mX2cpkq688/edit?usp=sharing)
![Presentation Preview](https://github.com/MSBX5420/team-mount-elbert/blob/master/graph%20images/canvas.png)
