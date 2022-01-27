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

| Subject | Message | Action | #Rows (% of Dataset) |
| :--- | :--- | :--- | :--- |
| EMPTY | EMPTY | DROPPED | 51 (0.15%) |
| EMPTY | DATA AVAILABLE | REPLACED EMPTY SUBJECT WITH “(NO_SUBJECT)” | 238 (0.7%) |
| DATA AVAILABLE | EMPTY | REPLACED EMPTY MESSAGE WITH “(NO_MESSAGE_TEXT)” | 320 (0.95%) |

3) RegEx Expressions – Applied independently on ‘Subject’ and ‘Message’ columns
    - To reduce the complexity and mismatching of regex expressions employed in the following steps, all texts were lowercased.
    - Then we matched and removed all characters except for alphabets (a-z) and full stop (.). This was done to get rid of special characters that we otherwise presumed might interfere during tokenization.
    - This step was followed by removal of extra white spaces and multiple occurrences of full stop (.).
4) Dropping Sentences – Applied independently on ‘Subject’ and ‘Message’ columns
    - The first task was to sentence tokenize each text.
    - Any sentence that contained less than 2 words were dropped and the remaining sentences were joined and replaced the original text.
    - However, if dropping such sentences resulted in an empty text, then original text was retained as such.
5) Lemmatization – Applied independently on ‘Subject’ and ‘Message’ columns
    - Primarily, each text was sentence tokenized.
    -	Then, we realized that lemmatizer output accuracy is improved when, along with the word, its pos-tag is also passed as an additional parameter.
    -	Hence, each sentence was then word tokenized and in turn each word was pos-tagged (part-of-speech).
# Results
We ran all the conventional machine learning models with 100% of the data using a 66/33 train test split. After tuning, SVM was the best model for ‘Subject’ while the artificial neural network was the best for ‘Messages’ scoring 93.8% and 98.3% respectively. Due to our computer configurations, we weren’t able to run the neural network (NN) model at 100%, instead maxing out at 60% of the dataset. For this reason, after finding that SVM was the best conventional machine learning model we ran it again with 60% of the data, maintaining the same train test split, so it could be accurately compared to the NN model.
