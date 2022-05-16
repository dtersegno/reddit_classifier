---
# Classifying subreddit posts by origin subreddit: r/haskell or r/lisp
---
David Tersegno

4/1/22
 
DSIR 222 Project-3 Classifiers


Haskell and Lisp are two programming languages with histories of strong, knowledgable, and curious users and contributors. There is likely to be a lot of overlap in what they talk about, and how they talk about it! This project attempts to take normal text posts from these two languages' respective Reddit communities and identify which one they came from. This kind of classification model can be extended to a plethora of complicated information inference and sorting tasks. It can grab a piece of text and identify its proper place in a matter of a few milliseconds.

---
## Problem statement
---
We want to answer this: Can we scrape text from two similar Reddit communities, chop it up into word bits, remove the standard identifying information, and still be able to correctly name the source of every piece? If not perfectly, how well can it be done?

Specifically, it applies a gauntlet of classifiers to the data and compares them, settling on a DecisionTreeClassifier with 100% accuracy on the test data. This classifier is also very quick, even by computer standards!

The motivation for a model such as this is to apply a way of identifying and revealing "hidden" information in text. It could also be extended to sorting a large volume of text into manageable sizes for analysis. This is an extremely broad type of problem. Applications could be found in any field with any kind of literature.

---
## The files
---
The analysis is performed in a series of four ipython notebooks in this directory. The data passes through them sequentially, being collected or modified in each, and exported to the next. The four notebooks are:

    - Notebook1GatheringData.ipynb
    - Notebook2EDAandCleaning.ipynb
    - Notebook3MoreEDANumericFeatures.ipynb
    - Notebook4TextFeaturesandModelFits.ipynb

The data at different points in the procedure is stored in three directories here:

    - ./data/
    - ./data_clean/
    - ./data_clean_num/
    
The folder `./slides/` contains a PDF slide deck for the accompanying presentation.

The remaining file is this readme:
       
    - README.md
---
## The data
---
    
Data is collected using the [PushShift Reddit API](https://github.com/pushshift/api). The format of this data is detailed in the second notebook. The most critical features are `selftext` and `title`, the body text and title of posts from [r/haskell](https://www.reddit.com/r/haskell/) and [r/lisp](https://www.reddit.com/r/lisp/). The target is `subreddit`, which can either be classified as `haskell` or `lisp` originating post.

---
## The model
---

The best model fit was a `sklearn` default-parameter DecisionTreeClassifier(). This is a widely used and trusted kind of classifier that has been fit to this particular data. It performs faster than all of the other classifiers fit in Notebook 4, and has perfect accuracy on the test data.
