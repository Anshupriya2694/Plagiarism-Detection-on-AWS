## Plagiarism-Detection-on-AWS

This project is a part ML Engineer Nanodegree on Udacity. This project aims to build a plagiarism detector for text files. The model will examine a text file and perform binary classification (0 or 1) labeling that file as either plagiarized or not, depending on how similar that text file is to a provided source text.

### Types of Plagiarism

Every text file is associated with one **Task** and one **Category** of plagiarism. Tasks refer to the topic on which the paper has been written. The category of plagiarism is as explained below: 

1. **cut**: An answer is plagiarized; it is copy-pasted directly from the relevant Wikipedia source text.
2. **light**: An answer is plagiarized; it is based on the Wikipedia source text and includes some copying and paraphrasing.
3. **heavy**: An answer is plagiarized; it is based on the Wikipedia source text but expressed using different words and structure. Since this doesn't copy directly from a source text, this will likely be the most challenging kind of plagiarism to detect.
4. **non**: An answer is not plagiarized; the Wikipedia source text is not used to create this answer.
5. **orig**: This is a specific category for the original, Wikipedia source text. We will use these files only for comparison purposes.


### Similarity Features

This is the measure of how similar a given answer is as compared to original wikipedia. The similarity features used in this project ar informed by this [paper](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/January/5c412841_developing-a-corpus-of-plagiarised-short-answers/developing-a-corpus-of-plagiarised-short-answers.pdf). 

#### Contaiment 

Containment is defined as **intersection** of the n-gram word count of the Wikipedia Source Text (S) with the n-gram word count of the Student Answer Text (S) divided by the n-gram word count of the Student Answer Text.

![equation](Tex2Img_1602260180.jpg)

If the two texts have no n-grams in common, the containment will be 0, but if all their n-grams intersect then the containment will be 1. Longer the n-grams have in common, more will there be an indication of cut and paste plagiarism.

#### Longest Common Subsequence

The longest common subsequence is the longest string of words (or letters) that are the same between the Wikipedia Source Text (S) and the Student Answer Text (A). This value is also normalized by dividing by the total number of words (or letters) in the Student Answer Text.



