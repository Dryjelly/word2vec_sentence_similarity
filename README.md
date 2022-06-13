# Measure sentence similarity by using word2vec 

word2vec을 사용하여 문장 유사도를 측정합니다.

## Environment
python

## Run
install required packages
```
pip install konlpy
pip install gensim==3.8.1
```
download Pre-trained model zip file (from: https://github.com/Kyubyong/wordvectors) 
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=0B0ZXk88koS2KbDhXdWg1Q2RydlU' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=0B0ZXk88koS2KbDhXdWg1Q2RydlU" -O ko.zip && rm -rf ~/cookies.txt
```
unzip file
```
unzip ko.zip -d ko
```

## Reference
#### Package
* https://pypi.org/project/gensim/
* https://konlpy.org/ko/v0.5.2/
#### Site
* https://monetd.github.io/python/nlp/Word-Embedding-Word2Vec-%EC%8B%A4%EC%8A%B5/
* https://mr-doosun.tistory.com/22
