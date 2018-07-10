### Methods

```python
#Process and tokenize the words in the text file
def process_text(text_file):
    text = open(text_file,errors = "ignore")
    text = text.read()
    tokenized_text = word_tokenize(text)
    return tokenized_text
```

```python
#Create a Stanford NER Tagger object and use to tag each tokenized word
def stanford_tagger(tokenized_text):
    #create tagger 
    st = StanfordNERTagger(stanford_classifier, stanford_ner_path, encoding='utf-8')
    #tag every tokenized word
    classified_text = st.tag(tokenized_text)
    return classified_text
```

```python
#Tag tokens with standard NLP BIO tags
def bio_tagger(classified_text):
    bio_tagged = []
    prev_tag = "O"
    for token, tag in classified_text:
        if tag == "O": #O
            bio_tagged.append((token,tag))
            prev_tag = tag
            continue
        if tag != "O" and prev_tag == "O": #Begin NE
            bio_tagged.append((token, "B-" + tag))
            prev_tag = tag
        elif prev_tag != "O" and prev_tag == tag: #Inside NE
            bio_tagged.append((token, "I-" + tag))
            prev_tag = tag
        elif prev_tag != "O" and prev_tag != tag: #Adjacent NE
            bio_tagged.append((token, "B-" + tag))
            prev_tag = tag
    return bio_tagged
```

```python
#Create Chunk Tree
def stanford_tree(bio_tagged):
    tokens, ne_tags = zip(*bio_tagged)
    pos_tags = [pos for token, pos in pos_tags(tokens)]
    conlltags = [(token, pos, ne) for token, pos, ne in zip(tokens, pos_tags, ne_tags)]
    ne_tree = conlltags2tree(conlltags)
    return ne_tree
```

```python
#Parse named entities from tree
def structure_ne(ne_tree):
    ne = []
    for subtree in ne_tree:
        #if subtree is a noun chunk; NE != "O"
        if type(subtree) == Tree: 
            ne_label = subtree.label()
            ne_string = " ".join([token for token, pos in subtree.leaves()])
            ne.append((ne_string, ne_label))
    return ne
```

```python
#Process the whole tagging by calling the methods
def main():
    tokenized_text = process_text(r"C:\Users\Daryl\Desktop\Data Analysis\Stanford NER\text1.txt")
    tagged = stanford_tagger(tokenized_text)
```

```Sample Output:
[('``', 'O'),
 ('Singapore', 'LOCATION'),
 ('has', 'O'),
 ('also', 'O'),
 ('registered', 'O'),
 ('our', 'O'),
 ('concerns', 'O'),
 ('with', 'O'),
 ('the', 'O'),
 ('relevant', 'O'),
 ('US', 'LOCATION'),
 ('and', 'O'),
 ('China', 'LOCATION'),
 ('departments', 'O'),
 ('and', 'O'),
 ('is', 'O'),
 ('continuing', 'O'),
 ('to', 'O'),
 ('engage', 'O'),
 ('them', 'O'),
 (',', 'O'),
 ("''", 'O'),
 ('said', 'O'),
 ('the', 'O'),
 ('spokesperson', 'O'),
 (',', 'O'),
 ('who', 'O'),
 ('did', 'O'),
 ('not', 'O'),
 ('respond', 'O'),
 ('to', 'O'),
 ('a', 'O'),
 ('query', 'O'),
 ('on', 'O'),
 ('the', 'O'),
 ('number', 'O'),
 ('of', 'O'),
 ('firms', 'O'),
 ('affected', 'O'),
 ('.', 'O'),
 ('In', 'O'),
 ('January', 'O'),
 (',', 'O'),
 ('US', 'LOCATION'),
 ('President', 'O'),
 ('Donald', 'PERSON'),
 ('Trump', 'PERSON')]
```
