
This project analyzes results of the StackOverflow 2019 Survey results.

This was done with the CRISP-DM framework in mind.

I. Project Motivation / Base questions

For this project, I was interested in using Stack Overflow data from 2019 to better understand:

1. What are the programming languages that developers want to work with most?
2. How the languages the programmer works with influence their salary?
3. What influences an individual’s Job Satisfaction, is it related to the language used by the?

II. Understanding Data

The dataset is built of the answers posed by the individuals involved in the 2019 StackOverflow Survey. It is worth noting that these are not objective data, but subjective answers provided by the respondents, which one needs to keep in mind while analyzing the results.
The dataset consists of 88883 respondent's answers. The answers, however, are at times incomplete. Depending on the problem being analyzed, some rows, where the data is missing, will be dropped to do the analysis.

III. Data Preparation

Data preparation varied depending on the question posed for analysis.

Question 1.  What are the programming languages that developers want to work with most?

This particular question has dealt with the LanguageDesireNext year values, were the survey asked for the programming language the individuals wants to work with in the next 12 months. For this analysis, records with missing answers for this question are dropped.
Individual answers are unpacked using the split function and the values are stored in a list/panda series. Next an analysis is performed
on the frequency of values.

Question 2. How the languages the programmer works with influence their salary?

Here the analysis is performed primarily on the LanguageWorkedWith, so the programming language that the developer used and the ConvertedComp, so the compensation received by the programmer converted into USD. Records with Nan values for these columns are dropped. LanguageWorkedWith is a a multiple-choice question. Unique values are unpacked ito a dictionary that is used to build an array that one-hot encodes the answers for the question. This is later used to analyze the compensation based on the languages the individual has worked with in the last 12 months

People are complex beings and it is very difficult to model their behavior

Question 3. What influences an individual’s Job Satisfaction, is it related to the language used by the?

Similarly to question 2, LanguageWorkedWith is unpacked to create a one-hot encoded values array. Apart from that, questions with numerical answers are taken into consideration, such as the individual's compensation. A few questions of interest that produced categorical answers are encoded, including work location, being an open source contributor or remote work. Job Satisfaction was provided by the respondents in a categorical scale from very dissatisfied to very satisfied. These values have been changed into numerical values.

IV. Based on the preparatory work done for question 3 a linear regression model was built with the Job Satisfaction being the response vector. Values were normalized and the test size was set as 0.25.

V. The model did not provide clear answers for the job satisfaction. While one could think that the individual's compensation should strike out to be one of the main factors contributing to job satisfaction this has not been shown with the model having a low R^2 value.


File Descriptions
There is 1 notebook available here to showcase work related to the above questions. Comments in cells were used to assist in walking through the thought process for individual steps.


Results
The main findings of this analysis together with visualizations can be found at the post available <a href = "https://medium.com/@Jan_Aspirant/programming-languages-developers-are-interested-in-and-their-impact-on-their-job-satisfaction-4c87a4d87e3"> here </a>.

1. Some languages that the individuals want to work with the most have been identified (JavaScript, Python, Html)
2. Based on the respondent's answers best paying languages have been also identified (Clojure, F#, WebAsembly). Quite interestingly,
the least popular languages seem to pay the most, with the individuals taking into consideration multiple factors while choosing a language they want to work with.
3. Based on the survey results, however, it’s difficult to confirm how programming languages used by the respondents have influenced job satisfaction. Especially, that the model 

It’s a great opportunity for you to try to find what has an impact on developers’ job satisfaction!
Licensing, Authors, Acknowledgements
Must give credit to Stack Overflow for the data. You can find the Licensing for the data and other descriptive information at the Kaggle link available here. Otherwise, feel free to use the code here as you would like!
