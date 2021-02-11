## Scenario

Based on the sample website data our goal is to find the target attendees of the upcoming SXSW festival in 2019. The objective is to identify which content will turn first-time visitors into loyal readers and subscribers and also there relationship with other features.
Each row in data.csv represents a single page view.

## RESULT OF MY MODEL:

Our model can predict with 88% accuracy the likelihood of a first time visitor returning, based on the customers interaction with the articles. Please read through the analysis, the model has been built and explained below.

## Data

| Column Name     | Description       |
| --------------- | ----------------- |
| customerID | unique customer ID
| firstVisitDate | Date and time of customer's first visit
| secondVisitDate | Date and time of customer's second visit, if any
| articleID | unique ID of the article read on the customer's the first visit
| section | section of the article read on the first visit
| author | author(s) of the article read on the first visit
| headline | headline of the article read on the first visit
| topicKeywords | topic keywords in article read on the first visit
| totalVisits | the customer's total visits to-date since `firstVisitDate`
| wordCount | word count of the customer's first article
| videoCount | number of videos in article


## Questions & Answers

##Treat Missing Values before further analysis
1. Treat wordcount column: Take the average of word count and replace NA values in the wordcount column with the average
2. We are not removing missing values for the author name as we are not using that column currently in our analysis. If we would have intended to use that column we would have removed the rows with NA values as it is a categorical column and we can't assume that.

1. What percent of customers returned after the first visit?

Based on the analysis 11.82% of users came back after the first contact.

## My Insights

This is good but it does not say much about the company’s current ability to get its attendees to come back, nor does it report the effect of past actions taken by the organization to improve retention.
One way to address this issue is to get more granular and instead of a single number i.e 11.82% here, retention is defined as a table of multiple retention rates. This table tells the story of how multiple user groups/cohorts retain over time called range retention. Simply it tells us who retains and when.
We select a period of interest for example last 12 months based on the current dataset, we will work on it to get the retention story.
We can break this period further into weekly or monthly, that is how we achieve the 'when'.
Finally, users are grouped into cohorts and that is how we achieve the 'who'.
Then all we have to do is calculate the retention rate of each user cohort during each window.

2. What are the top three best-performing stories in each section, by pageviews?

Based on the analysis the most viewed articles under each section are as follows:


section	        articleID	                                TotalVisits
WSJ_Tech		SB11210326209662973945104584087492498923938	144
				SB11210326209662973945104584093530025809224	79
				SB10961112392510633702504584105390792934438	66
WSJ_Politics	SB10053721253826474326804584099101464018882	1517
				SB11210326209662973945104584091642991444798	1022
				SB11704195083378974371404584099474288368000	496
WSJ_Opinion		SB10863058833601644371104583000294067613334	175
				SB10385287216379884548704584103473343707450	127
				SB11513260795640254558004584085581177203524	98
WSJ_Markets		SB12775101498795324251604584091654130126032	238
				SB11027093093037343542404584103340219066918	175
				SB12008635076439604245104584089491434195378	101
WSJ_Life		SB11513260795640254558004584085750469425772	144
				SB11805791893646614375304584073542435430108	141
				SB12775101498795324251604584089691304167728	135
WSJ_Business	SB11704195083378974371404584097403724108802	741
				SB11027093093037343542404584101822248659720	220
				SB10342241267609484717704584101481939436054	183

3. Based on this data, what should we choose to promote a Tech story or a Markets story on social media?

I would choose to promote Markets stories because based on the data the section WSJ_Market has a higher number of visitors in comparison with the WSJ_Tech. Our goal is to increase customer engagement and target attendees for the SXSW festival in 2019. We would need to enhance our content strategy and calculate how much time and energy we’ll need to dedicate to promote these stories.
Since market stories are doing well we should focus on it first as it can attract a more customer base. So, rather than looking for the biggest conversations, look for the right conversations that will contribute to success and sustain our audience longer.


4. Creating a visualization exploring the relationship between any of the content characteristics (such as section, keywords, first time visitors and returning visitors.

## 1st Visualization

The visualization represents the relationship between the first-time visitors and the second-time visitors for each section based on the keyword count.
The highest keyword count tells us a story about which news section is doing good and attracting a large base of customers. The lowest keyword count tells us a story of those sections that are not performing well and hence need more visibility and improved marketing strategies.

## 2nd Visualization

The below graph represents the story of the most trending keywords overall in comparison with the same keywords used by second-time visitors.
We can understand the most trending keyword's amount of usage by the second time visitors in comparison with the overall first time visitors. It would help us in improving our SEO and target a more customer base.


The below two graphs shows us the most trending keywords based on two different bag of words.
First time visitor most trending keywords.
Second time visitor most trending keywords.

## 3rd Visualization

Simple representation of the most trending keywords based on first time users

## 4th Visualization

Simple representation of the most trending keywords based on second time users


5. Creating a simple model predicting the likelihood of a first-time visitor returning.

Based on the dataset we took test size 0.33 i.e. 3300 out of 10000 records and achieved an accuracy of 88% which is very good.
 Steps followed to achieve the result:        
1. Normalise the numerical columns totalVisits, wordCount, videoCount.
2. Encode categorical value i.e.'Section' with unique value.
3. Create returned column users with binary data based on secondVisitDate.
4. Train and split data using sklearn.model_selection

## Using Logistic Regression

Encode categorical value i.e.'Section' with unique value.
Normalise the numerical columns totalVisits, wordCount, videoCount.
Predictions and Evaluations

## Our model can predict with 88% accuracy the likelihood of a first time visitor returning, based on the customers interaction with the articles.


6. What additional data we can add to improve our model?

Having more data is always a good idea, instead of relying on assumptions and weak correlations.
We can add columns with more correlation like customer demographics(age, location, etc.) and social network shares.
Example: analyzing data based on different cities or states which would help us find a meaningful correlation between the age group of customers and the articles. Also, In which area we have the highest number of readers.
The current data require heavy feature engineering to convert the current columns into meaningful columns.

7. What are the other interesting stories we can tell with this sample data?


1. Percentage of customers returned between the window of 1 to 30 days, 31 to 60 days, 61 to 90 days, >90 days.
2. Including the share link data, information might help us to track the viral articles and sections.
3. Most read articles and least read articles based on the existing data.
4. Define retention as a table of multiple retention rates and target quaterly, monthly, weekly trends based on previous year data.














