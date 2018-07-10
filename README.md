# Stanford-NER-Tagger-Config
Short guide to configure Stanford NER for Python

# Stanford NER Tagging
NER stands for **Named Entity Recognition**. It is to extract information from unstructured text, basically by extraction a real world entity from the text (e.g. Person, Organization, Event, etc). This is to determine the relationships between different named entities.

This guide is only relevant to Windows Operating System. <br>
Credits: Code methods belongs to Chuck Dishmon

## Set-up NLTK in Python
Firstly, please install NLTK via Anaconda:
- [Anaconda]https://repo.anaconda.com/archive/Anaconda3-5.2.0-Windows-x86_64.exe

The above link will install a distribution of python packages and applications which includes NLTK.

After installing Anaconda, search and open Jupyter Notebook.
Run this code:
```python
import nltk
nltk.download("punkt")
```

## Set-up Java for Stanford NER
Given Stanford NER runs on Java, we will also need Java Runtime Environment (JRE) in order to use NLTK as a python parser. <br>
To download (only if you do not have Java installed):
- [Java] https://java.com/en/download/


## Set-up Stanford NER for Python
Stanford NER is a Java implementation of a Named Entity Recognizer. NER labels sequences of words in a text whih are the names of things, such as person and company names, or gene and protein names. It has good named entity recognizers for English, particularly for the 3 classes (PERSON, ORGANIZATION, LOCATION) and even for other languages.

Once you have installed NLTK python, please download and extract the following Stanford files into separate folders:

1. [Stanford Parser] https://nlp.stanford.edu/software/stanford-parser-full-2018-02-27.zip
2. [Stanford NER] https://nlp.stanford.edu/software/stanford-ner-2018-02-27.zip
3. [Stanford Log-Linear POS Tagger] https://nlp.stanford.edu/software/stanford-postagger-full-2018-02-27.zip

## Configurations

### 1. Environment Variables Window
Once you have all relevant packages and files, go to the search panel and search for "Environment Variables"

### 2. Create two new variables

#### CLASSPATH
Create a CLASSPATH user variable by clicking on the button New then add the following values
```
Drive:\path\to\stanford-ner-2018-02-27
Drive:\path\to\stanford-parser-full-2018-02-27
Drive:\path\to\stanford-postagger-2018-02-27
```
Example:
```
C:\Users\Daryl\Desktop\Stanford NER\stanford-ner-2018-02-27
C:\Users\Daryl\Desktop\Stanford NER\stanford-parser-full-2018-02-27
C:\Users\Daryl\Desktop\Stanford NER\stanford-postagger-full-2018-02-27
```

#### STANFORD_MODELS
Create another user variable named STANFORD_MODELS and add the following values
```
Drive:\path\to\stanford-postagger-2018-02-27\models
Drive:\path\to\stanford-ner-2018-02-27\classifiers
```
