
# Project Title: Diabetes in America and why we should screen for it early
## Group 5 
(Edilberto Vinas, Al Wagner, Frances Hollan, Nick Santos)

Presentation: https://docs.google.com/presentation/d/1upCUDoCPzsJN8KhqM4GvqQBzZQ1ELZFgFAr6_qD_mBc/edit#slide=id.p

Group 5 notebook: https://colab.research.google.com/drive/1nHaYV428N4MQWNnT6yVkwfOaumhoUuEV#scrollTo=V5a6LpH1Flva

## Works cited
1. Center for Disease Control - https://diabetes.org/about-diabetes/statistics/about-diabetes
2. Diabetes Prediction - https://www.cdc.gov/diabetes/library/socialmedia/infographics/diabetes.html
3. Google Colab AI

## Sections Included
Section 1: Overview<br>
Section 2: Scope<br>
Section 3: Data Collection<br>
Section 4: Data Cleaning<br>
Section 5: Approach and Methodology<br>
Section 6: Data Optimization<br>
Section 7: Conclusion<br>

# Section 1: Overview
Current CDC (Center for Disease Control) statistics show that about 38 million people in America (or 1 in every 10) suffer from diabetes with a whopping 1 in 5 of those people not even being aware that they have the disease. What's more shocking and perhaps more worrisome is that 98 million people, (or 1 in every 3), are considered prediabetic, with 8 out of 10 of them also not aware that they are in danger of contracting diabetes.[1]

With such a high rate of contracting a disease that can lead to blindness, kidney failure, heart disease, stroke, or the risk of amputating toes, feet or legs, early screening and awareness is something that can potentially benefit over 100 million Americans. Especially considering that type-2 diabetes (or adult-onset diabetes) can be prevented or treated by simply adjusting one's diet.

This is why our group chose to create a model that could help health clinicians deliver at-risk patients a probability of their chances of contracting diabetes. In our initial conversations the group had endeavored to create a chatbot that would actually interact with patients. For various reasons (stated in the Section 2 below) we abandoned the idea of interacting with patients and instead pivoted to gearing the model toward health clinicians who would be running tests on patients.

# Section 2: Scope
While the final objective of this project would still be to eventually create a chatbot that a qualified health clinician could use to screen for diabetes, due to time constraints, the group decided to focus on creating a predictive model that would be the basis for said chatbot as a proof of concept.

At the end of the day the focus remains the same. To create a tool to decide a) does this patient currently have diabetes and b) what is the probability that the patient will contract diabetes considering their test scores.

# Section 3: Data Collection
The search for data was relatively painless for this project. The group settled on a data set that we found on Kaggle [2] that included nine initial fields, most of which are generally considered indicators for diabetes (age, hypertension, smoking history, blood glucose level, body mass index, HbA1c level and gender). The data set consisted of 100,000 patients giving us a healthy sample size. 

Initially we had planned to create this chatbot for patients to use. We pivoted, given that the data set included clinical categories that a patient might not be aware of like hypertension and blood glucose levels, HbA1c scores or body mass index. As such, we decided that qualified health clinicians would be a better target audience with the idea that the chatbot would function as a quick screener that could be utilized and reviewed by a health professional who could administer the tests and create a health care plan.

# Section 4: Data Cleaning
The data set was very clean, albeit heavily biased toward "no" in the predictive "diabetes" category. There were no NaN values or missing values however we did have to use get_dummies to numerate the columns, "gender" and "smoking history". The "smoking history" column would eventually be expounded on into the new categories of, "smoking history no info", "smoking history current", "smoking history ever", "smoking history former", "smoking history never", and "smoking history not current".

# Section 6: Approach and Methodology
Since the answers are a binary "yes" or "no" to our query of, "does the patient have diabetes?", our initial approach was to use logistic regression to create the predictive model. After running a confusion matrix on the initial model however, the group was unsatisified with a 36% reporting of false negatives that we received. Given the severity for receiving a false negative in our case (the patient having diabetes but being told that they do not) it was decidied that the data would have to be optimized for the model to work.

After optimizing the data we did our due diligence and checked the accuracy score of the logistic regression model against other predictive models using an accuracy score pipeline which gave us a surprising outcome. After running the optimized data through the different models we found that the Random Forest classifier actually gave us the most accurate model, scoring an accuracy score of 99%. Although we all acknowledged the risk of having a slightly overfit model the decision was that we were willing to live with more false-positives (given that the penalty for a false-positive in our case was not that severe).

All in all these are the methods we used and their respective libraries. We used pandas to read the .csv file into a DataFrame. We used Python to assure the quality of the data set, check value counts and check data types. We utilized matplotlib to create a correlation plot of the X_train variables. Finally we used Sklearn to run the Logistic Regression model, the Random Forest model, the train_test_splits and the accuracy scores.

# Section 7: Data Optimization
To optimize our data we chose to oversample and undersample our two main models (Linear Regression and Random Forest) to combat bias and the false-negatives we were encountering. There was a concern with the Random Forest classifier, as it had an accuracy score of 99%, being overfit. To treat this the group cross validated the model with hyperparameter tuning which brought the accuracy score down to 97% which assuaged the concern a little bit but was still inconclusive.

# Section 8: Conclusion
There was debate within the group as to what model would be best for our project but ultimately we landed on using a Logistic Regression model because of its flexibility and the fact that it provides the user with a percentage of likelihood rather than just classifying a patient as diabetic or non-diabetic. Although the accuracy score for the Logistic Regression was only 88% (in comparison to the 99% accuracy score of the Random Forest classifier), its ability to give a percentage to a health clinician made for a more reliable model in the field.

The Logistic Regression model also put the onus on a qualified health clinician to make the final call. It provides them the chance to adjust where in that percentage spectrum a "yes" or "no" determination would land. So although the Random Forest classifier gave a higher accuracy score, the Logistic Regression model made more sense in a clinical setting considering that there would be other factors (HbA1c score, medical history, etc.) that would go into the final diagnoses.
