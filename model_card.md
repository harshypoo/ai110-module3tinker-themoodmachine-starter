# Model Card: Mood Machine

This model card is for the Mood Machine project, which includes **two** versions of a mood classifier:

1. A **rule based model** implemented in `mood_analyzer.py`
2. A **machine learning model** implemented in `ml_experiments.py` using scikit learn

You may complete this model card for whichever version you used, or compare both if you explored them.

## 1. Model Overview

**Model type:**  
Describe whether you used the rule based model, the ML model, or both.  
Example: “I used the rule based model only” or “I compared both models.”
I used both models and compared them.

**Intended purpose:**  
What is this model trying to do?  
Example: classify short text messages as moods like positive, negative, neutral, or mixed.
The models are attempting to classify text messages as moods such as positive, negative, neutral, or mixed.

**How it works (brief):**  
For the rule based version, describe the scoring rules you created.  
For the ML version, describe how training works at a high level (no math needed).
The rule based version scores based on the context that I have provided it with. If there are
matches within the context that I have provided, the model increments based off that. The ML version
uses a library and learns from the data provided to classify, which turns out to be more accurate than
my version of the rule based.



## 2. Data

**Dataset description:**  
Summarize how many posts are in `SAMPLE_POSTS` and how you added new ones.
There was originally five posts, but I added five more. I added different labeled posts because
I wanted to test every area of the model.

**Labeling process:**  
Explain how you chose labels for your new examples.  
Mention any posts that were hard to label or could have multiple valid labels.
I chose labels that were kind of confusing to understand until you really thought about it, but also
some easy cases. I wanted to test the limits of the model. There could be multiple
ways to label the tests that I created.

**Important characteristics of your dataset:**  
Examples you might include:  

- Contains slang or emojis  
- Includes sarcasm  
- Some posts express mixed feelings  
- Contains short or ambiguous messages
These could be classified as either or depending on the context. There was sarcasm being tested, contradicting
statements, mixed emotions, and more.

**Possible issues with the dataset:**  
Think about imbalance, ambiguity, or missing kinds of language.
There is a lot of ambiguity with some of the posts. It could be classified in any direction
depending on the context of the situation.

## 3. How the Rule Based Model Works (if used)

**Your scoring rules:**  
Describe the modeling choices you made.  
Examples:  

- How positive and negative words affect score  
- Negation rules you added  
- Weighted words  
- Emoji handling  
- Threshold decisions for labels

I added words that are positive and negative to be used for scoring. I also added negations so that we could
understand different contexts. Some sarcastic statements were added as well to identify that.

**Strengths of this approach:**  
Where does it behave predictably or reasonably well?
Simple statements are predicted well. It has to be pretty straightforward and cannot use mixed feelings.

**Weaknesses of this approach:**  
Where does it fail?  
Examples: sarcasm, subtlety, mixed moods, unfamiliar slang.
There was a lot of failure with sarcasm, mixed emotions, and more.

## 4. How the ML Model Works (if used)

**Features used:**  
Describe the representation.  
Example: “Bag of words using CountVectorizer.”

**Training data:**  
State that the model trained on `SAMPLE_POSTS` and `TRUE_LABELS`.

**Training behavior:**  
Did you observe changes in accuracy when you added more examples or changed labels?

**Strengths and weaknesses:**  
Strengths might include learning patterns automatically.  
Weaknesses might include overfitting to the training data or picking up spurious cues.

## 5. Evaluation

**How you evaluated the model:**  
Both versions can be evaluated on the labeled posts in `dataset.py`.  
Describe what accuracy you observed.
The rule based accuracy was 0.73 and the ML was 1.00.

**Examples of correct predictions:**  
Provide 2 or 3 examples and explain why they were correct.

**Examples of incorrect predictions:**  
Provide 2 or 3 examples and explain why the model made a mistake.  
If you used both models, show how their failures differed.

## 6. Limitations

Describe the most important limitations.  
Examples:  

- The dataset is small  
- The model does not generalize to longer posts  
- It cannot detect sarcasm reliably  
- It depends heavily on the words you chose or labeled

The dataset is very small, so the model does not have much to work with. It cannot reliably detect most
situations where it depends on the context.

## 7. Ethical Considerations

Discuss any potential impacts of using mood detection in real applications.  
Examples: 

- Misclassifying a message expressing distress  
- Misinterpreting mood for certain language communities  
- Privacy considerations if analyzing personal messages

The model may misinterpret the moods and not classify them correctly. Depending on the application, this could
be detrimental. This could lead to even more failures if the model continues to learn on that data as well.

## 8. Ideas for Improvement

List ways to improve either model.  
Possible directions:  

- Add more labeled data  
- Use TF IDF instead of CountVectorizer  
- Add better preprocessing for emojis or slang  
- Use a small neural network or transformer model  
- Improve the rule based scoring method  
- Add a real test set instead of training accuracy only

Add real data and have humans verify every output. It also might be better to rely on the ML version rather than
rule based, because that is a lot of rules. If we are using rule based, we should improve it by putting more
context of real human conversations.