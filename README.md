# Measure sentence similarity by using word2vec 

`word2vec`  
<p align="center">
  <img src="readme/img1.png" alt="model" style="width:700px;"/>
</p>

word2vec 을 사용하여 문장 유사도를 측정합니다.
<p align="center">
  <img src="readme/img2.png" alt="model" style="width:650px;"/>
</p>   

임베딩 영역의 정보를 이용하면 단어들의 유사도를 판단할 수 있다.   
이 방법을 이용하여 문장의 유사도를 측정해보자. 

`news.txt`
```
도널드 트럼프 미국 대통령이 1일(현지시간) 한국과 이탈리아 등 신종 코로나 감염증(코로나 19) 고위험국 여행자는 현지 탑승 전 검사에 더해 미국에 도착해서도 검사를 받을 것이라고 밝혔다. 발열 등 신종 코로나 관련 유증상자의 입국을 차단하겠다는 뜻이다. 한국 대구에 대한 여행금지 경보 발령으로 부족해 하루 만에 한국에서 출발하는 모든 여행자의 출발 전, 미 공항 입국 시 이중 검사를 지시한 것이다. 미 보건장관은 "한국에 대한 입국 제한 등 모든 옵션이 테이블 위에 남아 있다"고 말했다.
트럼프 대통령은 이날 트위터에서 "코로나바이러스: 특정 고위험국 지정 국가 출신의 여행자를 탑승 전 검사하는 조치에 더해 그들은 미국에 도착할 때도 검사를 받게 될 것"이라고 밝혔다. 이 같은 트위터에 백악관 신종 코로나 태스크포스를 이끄는 마이크 펜스 부통령과 알렉스 에이자 보건부 장관, 로버트 레드필드 질병통제센터(CDC) 국장의 트위터 계정도 함께 올렸다. 사실상 고위국 여행자의 출발 전 검사에 더해 미 공항 입국 시 추가 의료 검사를 지시한 셈이다.
케이시 밀러 펜스 부통령 대변인은 CNN 방송에 트럼프 대통령이 언급한 검사 조치에 대해 "최근 14일 중국을 방문한 적이 있는 사람들(미국인)에 대한 입국 시 검사가 이미 시행 중"이라며 "이탈리아와 한국에 이런 검사를 확대한다는 것"이라고 설명했다. "게다가 우리는 한국과 이탈리아, 필요한 경우 다른 유럽 국가에서 출국 전 검사를 시행하고 있다"고 밀러는 덧붙였다.
펜스 부통령도 전날 기자회견에서 한국 대구와 이탈리아 롬바르디아(주도 밀라노)와 베네토(베니스)주에 대한 4단계 여행 금지 경보 발령을 설명하면서 "대통령이 국무부에 이탈리아와 한국 동맹국과 이들 국가에서 미국으로 입국하는 개인들의 의료 검사를 하도록 조율하라고 지시했다"고 밝힌 바 있다.
알렉스 에이자 보건부장관도 이날 한국에 대해 현재는 미국인의 여행 금지 권고가 적절한 조치이지만 "모든 것이 항상 테이블 위에 있다"고 말했다. 중국처럼 언제든 입국제한 조치를 할 수도 있다는 뜻이다.
에이자 장관은 폭스뉴스 선데이와 인터뷰에서 "최근 중국을 방문한 적 있는 모든 외국인의 미국 입국을 금지하고 있지만 한국과 이탈리아는 우수한 의료 시스템을 갖고 있어 여행 경고만 발령했다"고 설명했다. 그는 "한국과 이탈리아에서 중요한 것은 선진 보건 및 의료 체계, 투명한 리더십을 갖고 있을 뿐 아니라 신종 코로나 발생 첫날부터 매우 공세적인 조치를 하고 있다는 점"이라고 했다. "그래서 현시점에선 사람들에게 가지 말라고 조언하는 것이 적절한 조치라고 생각하지만 모든 것은 항상 테이블 위에 있다"고 덧붙였다.
에이자 장관은 CBS 방송과 인터뷰에서도 일본이 한 달간 학교를 폐쇄하고 워싱턴주는 비상사태를 발령했는데 여행 제한이나 봉쇄 조치를 하지 않느냐는 질문에 "주 또는 지방 보건당국이 최일선에서 독자적 결정을 할 수 있겠지만, 현재 미국에는 그런 조치를 할 만큼 충분한 확산이 발생한 게 아니다"라고 답했다. 그러면서 "우리는 어떤 것도 테이블에서 내려놓지 않았으며 모든 옵션은 언제나 테이블 위에 남아 있다"고 강조했다.
```
비교할 문장
```
미국 여행 주의보
```
결과
```
--------------------문장 유사도 순위--------------------
에이자 장관은 폭스뉴스 선데이와 인터뷰에서 "최근 중국을 방문한 적 있는 모든 외국인의 미국 입국을 금지하고 있지만 한국과 이탈리아는 우수한 의료 시스템을 갖고 있어 여행 경고만 발령했다"고 설명했다
유사도 : 0.6993651390075684
************

도널드 트럼프 미국 대통령이 1일(현지시간) 한국과 이탈리아 등 신종 코로나 감염증(코로나 19) 고위험국 여행자는 현지 탑승 전 검사에 더해 미국에 도착해서도 검사를 받을 것이라고 밝혔다
유사도 : 0.636943519115448
************

펜스 부통령도 전날 기자회견에서 한국 대구와 이탈리아 롬바르디아(주도 밀라노)와 베네토(베니스)주에 대한 4단계 여행 금지 경보 발령을 설명하면서 "대통령이 국무부에 이탈리아와 한국 동맹국과 이들 국가에서 미국으로 입국하는 개인들의 의료 검사를 하도록 조율하라고 지시했다"고 밝힌 바 있다
유사도 : 0.6003605127334595
************
...
```

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

run `word2vec_test.ipynb`

## Reference
#### Package
* https://pypi.org/project/gensim/
* https://konlpy.org/ko/v0.5.2/
#### Site
* https://monetd.github.io/python/nlp/Word-Embedding-Word2Vec-%EC%8B%A4%EC%8A%B5/
* https://mr-doosun.tistory.com/22
* https://ratsgo.github.io/from%20frequency%20to%20semantics/2017/03/30/word2vec/
* https://www.sallys.space/blog/2018/04/05/negative-sampling/
* https://tensorflowkorea.gitbooks.io/tensorflow-kr/content/g3doc/tutorials/word2vec/
* https://excelsior-cjh.tistory.com/156
