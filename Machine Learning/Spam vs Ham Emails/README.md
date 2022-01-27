# Introduction
A common problem everybody faces in the digital age: spam. Spam emails, spam texts, even spam phone calls! While a majority of workers who use email for communications don’t receive spam, for some, filtering out spam can cost up to 30-60 minutes over the course of a work day (Fallows, 2003). Through the use of machine learning and deep learning models, data scientists are able to use classifier models to detect which emails are spam and which are not, which in turn will save workers time and increase productivity. This report’s focus is on: Which models, machine learning or deep learning, and which classifiers are the most effective at classifying spam correctly?
# Dataset
The dataset we chose is: [Enron Spam dataset](http://nlp.cs.aueb.gr/software_and_datasets/Enron-Spam/index.html). This is a real-life dataset consistent of both sent and received emails. It was put together by former employees of Enron, who went through and labelled their work emails as “Ham” or “Spam.” The dataset contains 33665 emails in total. Below we will discuss how the data was picked, cleaned, preprocessed, and how features were selected.
# Preprocessing
1)	Label Encoding
- The first step was to label encode the ‘Spam/Ham’ column with ‘Spam’ values mapped to 0 and ‘Ham’ mapped to 1, followed by renaming the column to ‘label’.
2)	Cleaning
- In the cleaning step, we encountered three distinct cases: first, only the ‘Subject’ field was empty; second, only the ‘Message’ field was empty; and third where both ‘Subject’ and ‘Message’ was empty.
- The following table summarizes the actions we took against each scenario.
