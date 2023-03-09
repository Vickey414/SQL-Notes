# Bag-of-words and linear models
Some activation function
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224034431-9a548b07-dbb7-4a15-a2e3-e81395eb5690.png">   
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224034455-d61ee630-30d7-4773-9cd0-136240861e4f.png">  

bags-of-words: could be very sparse vector
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224034741-daad18ea-e80c-4010-9e9a-4a22235f2242.png">
Linear model: use softmax
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224034973-f69a96a2-78f4-4bee-8a61-45c83b1228ca.png">


#### Feature Space
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224037002-58f50672-6418-45b0-8163-363bf1b54395.png">
How to do:
1. Filtering stop-words:
from nltk.corpus import stopwords
2. Word normalization:
• Lemmatization: determining the lemma of a word (slower but more precise)就是把同语义的词变成一个，如单复数，时态
from nltk.stem import WordNetLemmatizer
lemmatizer = WordNetLemmatizer()
lemmatizer.lemmatize(w)

• Stemming: “clipping” words to their stem (faster but less precise)
from nltk.stem.snowball import SnowballStemmer
stemmer = SnowballStemmer('english')
stemmer.stem(w)
<img width="215" alt="image" src="https://user-images.githubusercontent.com/29950267/224038630-b06a41a9-52c9-40cf-b2ef-d5f7595c19d1.png">



# word2vec
