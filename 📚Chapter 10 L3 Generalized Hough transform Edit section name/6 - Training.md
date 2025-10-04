When training computer vision models, one key step is developing something called visual code-words (also called a visual vocabulary). These are essentially compact, representative “words” that describe important image patterns.

Think of it like this: just as text documents are represented by words, images can be represented by visual words. These words come from patches of images where interesting stuff is happening — corners, textures, or edges.


## 📑 Table of Contents  

- [What is Machine Learning](#What-is-Machine-Learning)  
- [Unsupervised learning](#Unsupervised-learning)  
- [Reinforcement learning](#Reinforcement-learning)  
- [Supervised learning explanation](#Supervised-learning-explanation)
- [Supervised learning in Python](#Supervised-learning-in-Python)    

### **Step 1: Detecting Interest Points** 

The process starts by finding interest points in an image. These are locations where something meaningful is going on — like a corner of a tire, an edge of a window, or a textured spot on the road.

- Common algorithms for finding interest points include:
- Harris Corner Detector
- SIFT (Scale-Invariant Feature Transform)
- SURF (Speeded-Up Robust Features)

Each interest point is surrounded by a small image patch that captures local texture or structure.
So, the first step in training, are developing what's called visual code-words.  And, basically the way it works is this, you have some sort of an operator, and  we'll talk about interest point operators,  that generate what are called interest points.  That is, these are points in the image where reasonable amounts of  interesting stuff is happening.  And we'll talk about Harris corners and other ways of finding that. 

<p align="center">
<img src="https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%2010%20L3%20Generalized%20Hough%20transform%20Edit%20section%20name/1.png"></a>
</p>

 ## **Step 2: Building Visual Code-Words**
 
Once we’ve collected patches from many training images, we cluster them using an algorithm like k-means clustering.

- Each cluster center becomes a visual code-word.
- These code-words act like a dictionary that represents visual patterns.

For example:

- A small patch of a tire tread might form one code-word.
- A corner of a car window might form another code-word.
When combined, these code-words give us a structured way to describe and recognize objects.

What you do is, you take your interest point operator,  pull out all the interesting points on a bunch of training images.  You collect the little image patch right around those points,  you may get hundreds of them, or thousands of them, and then you cluster them,  and you use some algorithm for doing a clustering.  And when you're all done with those clusters,  the centers of those clusters are referred to, as visual code words.  So here, you can see all of these images that were  taken from something like tires, then they were all clustered, and so  the code word is this little tire piece. 

## **Step 3: Labeling Interest Points** 

Now, for every interest point in a new image:
- We compare its patch with the dictionary of visual code-words.
- We assign it the label of the code-word it matches best.
This way, each image can be described as a bag of visual words, similar to how text documents are represented by a bag of words in Natural Language Processing.

<p align="center">
<img src="[https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%2010%20L3%20Generalized%20Hough%20transform%20Edit%20section%20name/1.png](https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%2010%20L3%20Generalized%20Hough%20transform%20Edit%20section%20name/333.png)"></a>
</p>

## **Supervised learning explanation** 

In supervised learning, we have several data points or samples, described using predictor variables or features and a target variable. Our data is commonly represented in a table structure such as the one you see here, in which there is a row for each data point and a column for each feature. Here, we see the iris dataset: each row represents measurements of a different flower and each column is a particular kind of measurement, like the width and length of a certain part of the flower. The aim of supervised learning is to build a model that is able to predict the target variable, here the particular species of a flower, given the predictor variables, here the physical measurements. If the target variable consists of categories, like ‘click’ or ‘no click’, ‘spam’ or ‘not spam’, or different species of flowers, we call the learning task classification. Alternatively, if the target is a continuously varying variable, for example, the price of a house, it is a regression task. In this chapter, we will focus on classification. In the following, on regression.

<p align="center">
<img src="https://github.com/dr-mushtaq/Machine-Learning/blob/master/Supervised%20Learning%20with%20scikit_learn/Chapter1-Classification/2.png"></a>
</p>

The goal of supervised learning is frequently to either automate a time-consuming or expensive manual task, such as a doctor’s diagnosis or to make predictions about the future, say whether a customer will click on an ad or not. For supervised learning, you need labeled data and there are many ways to get it: you can get historical data, which already has labels that you are interested in; you can perform experiments to get labeled data, such as A/B-testing to see how many clicks you get; or you can also crowdsourced labeling data which, like reCAPTCHA does for text recognition. In any case, the goal is to learn from data for which the right output is known, so that we can make predictions on new data for which we don’t know the output.
 
 **Naming conventions**

A note on naming conventions: out in the wild, you will find that what we call a feature, others may call a predictor variable or independent variable, and what we call the target variable, others may call dependent variable or response variable.

## **Supervised learning in Python** 

There are many ways to perform supervised learning in Python. In this course, we will use scikit-learn, or sklearn, one of the most popular and user-friendly machine-learning libraries for Python. It also integrates very well with the SciPy stack, including libraries such as NumPy. There are a number of other ML libraries out there, such as TensorFlow and Keras, which are well worth checking out once you got the basics down.

1- **What is scikit -Learn?**

What is it:In simple terms, Scikit Learn is an open source and one of the most useful libraries for machine learning in Python. It has tools for predictive data analysis [6]. Scikit learn is a library that is written in Python and built upon Scipy, Matplotlib and Numpy provides a set of useful and efficient tools for machine learning and statistical modeling including regression, classification, clustering, predictive data analysis and dimensionality reduction etc and known as the most robust and useful library for Machine Learning .

Background: A developer named David Cournapeau originally released scikit-learn as a student in 2007. The open source community quickly adopted it and has updated it numerous times over the years [5]. This library, which is largely written in Python, is built upon NumPy, SciPy and Matplotlib [2].The library provides a unified API (Application Programming Interface) for practitioners to ease the use of machine learning algorithms with only writing a few lines to accomplish the predictive or classification task [3].The package is written heavily in python, and it incorporates C++ libraries like LibSVM and LibLinear for support vector machines and generalized linear model implementation [3]

Features: The packages in Scikit-learn focus on modeling data.One of the most prominent Python libraries for machine learning:
Contains many state-of-the-art machine learning algorithms

It was designed to work seamlessly with NumPy and SciPy (both described below) for data cleaning, preparation, and calculation.

Builds on numpy (fast), implements advanced techniques

It has modules for loading data as well as splitting it into training and test sets.

It supports feature extraction for text and image data.

Wide range of evaluation measures and techniques

Offers comprehensive documentation about each algorithm

Widely used, and a wealth of tutorials and code snippets are available

<p align="center">
<img src="https://github.com/dr-mushtaq/Machine-Learning/blob/master/Supervised%20Learning%20with%20scikit_learn/Chapter1-Classification/3.jpg"></a>
</p>

<p align="center">
<img src="https://github.com/dr-mushtaq/Machine-Learning/blob/master/Supervised%20Learning%20with%20scikit_learn/Chapter1-Classification/4.jpg"></a>
</p>

### References

1-[Scikit Learn Tutorial](https://www.tutorialspoint.com/scikit_learn/index.htm)

2-[Scikit-Learn: A silver bullet for basic machine learning](https://medium.com/analytics-vidhya/scikit-learn-a-silver-bullet-for-basic-machine-learning-13c7d8b248ee)

4-[Machine Learning with scikit-learning (Datacamp)](https://www.datacamp.com/users/sign_in?redirect=http%3A%2F%2Fapp.datacamp.com%2Flearn%2Fcourses%2Fmachine-learning-with-scikit-learn)

5-[-Essential Python Libraries for Machine Learning and Data Science](https://www.deeplearning.ai/blog/essential-python-libraries-for-machine-learning-and-data-science/?utm_campaign=DLAI+Blog&utm_content=248986290&utm_medium=social&utm_source=facebook&hss_channel=fbp-1027125564106325)


<p align="center">
  <a href="#previous-section" style="text-decoration:none;">
    <button style="padding:20px 40px; font-size:24px; font-weight:bold; border-radius:12px; background-color:#007BFF; color:white; border:none; cursor:pointer;">
      ⬅️ Previous
    </button>
  </a>

  <a href="#next-section" style="text-decoration:none;">
    <button style="padding:20px 40px; font-size:24px; font-weight:bold; border-radius:12px; background-color:#28A745; color:white; border:none; cursor:pointer;">
      Next ➡️
    </button>
  </a>
</p>



































