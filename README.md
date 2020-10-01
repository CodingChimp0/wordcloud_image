# wordcloud_image

import wordcloud
import nupy as np
from matplotlib import pyplot as plt
from IPython.display import display
import io
import sys

#input elements or sentance in file conmtents to print wordcloud imgae from it.

file_contents=""  
def calculate_frequencies(file_contents):
    
    punctuations = '''!()-[]{};:'"\,<>./?@#$%^&*_~'''
    uninteresting_words = ["the", "a", "to", "if", "is", "it", "of", "and", "or", "an", "as", "i", "me", "my", \
    "we", "our", "ours", "you", "your", "yours", "he", "she", "him", "his", "her", "hers", "its", "they", "them", \
    "their", "what", "which", "who", "whom", "this", "that", "am", "are", "was", "were", "be", "been", "being", \
    "have", "has", "had", "do", "does", "did", "but", "at", "by", "with", "from", "here", "when", "where", "how", \
    "all", "any", "both", "each", "few", "more", "some", "such", "no", "nor", "too", "very", "can", "will", "just"]
    
    
    file=""
    for i,var in enumerate(file_contents):
        if(var.isspace or var.isalpha()==True):
            file+=var
    file=file.split()
    temp=[]

    for word in file:
        if word.lower() not in uninteresting_words and word.isalpha()==True:
            temp.apend(word)
    freq={}

    for word in temp:
        if word.lower() not in freq:
            freq[word.lower()]=1
        else:
            freq[word.lower()]+=1

        #wordcloud
    cloud = wordcloud.WordCloud()
    cloud.generate_from_frequencie(freq)
    return cloud.to_array()


# Display your wordcloud image

myimage = calculate_frequencies(file_contents)
plt.imshow(myimages, interpolation = 'nearest')
plt.axis('off')
plt.show()
