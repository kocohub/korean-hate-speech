# Korean HateSpeech Dataset

We provide the first human-annotated Korean corpus for toxic speech detection and the large unlabeled corpus. <br>
The data is comments from the Korean entertainment news aggregation platform. 

## Dataset description

The dataset consists of 3 parts: 1) `labeled` 2) `unlabeled` and 3) `news_title`.

#### 1. `labeled`
There are **9,381** human-labeled comments in total. They are splitted into 7,896 training set, 471 validation set, and 974 test set. (We left test set labels undisclosed for the fair comparison of prediction models. The model can be evaluated via the Kaggle submission which will be described later in this document.) Each comment is annotated on two aspects, the existence of **social bias** and **hate speech**, given that hate speech is closely related to bias. <br>

For social bias, we present `gender`, `others`, and `none` bias labels. Considering the context of Korean entertainment news where public figures encounter stereotypes mostly intertwined with *gender*, we weigh more on the prevalent bias. 
We also added binary label `whether a comment contains gender bias or not`. 
For hate speech, we introduce `hate`, `offensive`, and `none` labels. 
```
comments	contain_gender_bias	bias	hate
송중기 시대극은 믿고본다. 첫회 신선하고 좋았다.	False	none	none
지현우 나쁜놈	False	none	offensive
알바쓰고많이만들면되지 돈욕심없으면골목식당왜나온겨 기댕기게나하고 산에가서팔어라	False	none	hate
설마 ㅈ 현정 작가 아니지??	True	gender	hate
```
Detailed definitions are described in `guideline`.

#### 2. `unlabeled`

We additionally provide **2,033,893** `unlabeled` comments since `labeled` data is limited. <br>
This unlabeled dataset can be used in various ways: pretraining language model, semi-supervised learning, and so on.

#### 3. `news_title`

We release news titles for each comments. To fully understand meaning of the comments, context is must be required. <br>
For the entertainment news, both title and contents can be used for the context. However, we only provide the news articles' title, due to the legal issue.


## Usage

[`koco`](https://github.com/inmoonlight/koco) is a library to easily access `kocohub` datasets.

For `korean-hate-speech`, we can load datasets by using this code:
```python
>>> import koco

>>> train_dev = koco.load_dataset('korean-hate-speech', mode='train_dev')
>>> type(train_dev)
dict
>>> train_dev.keys()
dict_keys(['train', 'dev'])
>>> train_dev['train'][33]
{'comments': '2,30대 골빈여자들은 이 기사에 다 모이는건가ㅋㅋㅋㅋ 이래서 여자는 투표권 주면 안된다. 엠넷사전투표나 하고 살아야지 계집들은',
 'contain_gender_bias': True,
 'bias': 'gender',
 'hate': 'hate',
 'news_title': '"“8년째 연애 중”…‘인생술집’ 블락비 유권♥전선혜, 4살차 연상연하 커플"'}

>>> unlabeled = koco.load_dataset('korean-hate-speech', mode='unlabeled')
>>> type(unlabeled)
list
>>> unlabeled[33]
{'comments': '이주연님 되게 이쁘시다 오빠 오래가요 잘어울려 주연님 울오빠 잘부탁해요',
 'news_title': '"[단독] 지드래곤♥이주연, 제주도 데이트…2018년 1호 커플 탄생"'}

>>> test = koco.load_dataset('korean-hate-speech', mode='test')
>>> type(test)
list
>>> test[33]
{'comments': '끝낼때도 됐지 요즘같은 분위기엔 성드립 잘못쳤다가 난리. 그동안 잘봤습니다',
'news_title': '[단독] ‘SNL 코리아’ 공식적인 폐지 확정…아름다운 종료'}
```


## Kaggle competition

We open Kaggle competition to provide leaderboard system easily. There are 3 competitions:
1. Gender-bias detection: www.kaggle.com/c/korean-gender-bias-detection
1. Bias detection: www.kaggle.com/c/korean-bias-detection
1. Hate speech detection: www.kaggle.com/c/korean-hate-speech-detection

Feel free to participate :tada:

## Annotation Guideline

- [Guideline (`ko`)](https://www.notion.so/c1ecb7cc52d446cc93d928d172ef8442)
- [Guideline (`en`)](guideline/annotation_guideline_en.md)


## Contributors

The main contributors of the work are: 
- [Jihyung Moon](https://github.com/inmoonlight)\*
- [Won Ik Cho](https://github.com/warnikchow)\*
- [Junbum Lee](https://github.com/beomi)

\*: Equal Contribution

Note that this project is an independent research and was not supported by any of the organizations. <br>
Instead, we had an individual sponsor [Hyunjoong Kim](https://github.com/lovit) and we sincerely thank [Hyunjoong Kim](https://github.com/lovit) for providing financial support :heart:

## References

If you find this dataset useful, feel free to cite our publication [BEEP! Korean Corpus of Online News Comments for Toxic Speech Detection](https://www.aclweb.org/anthology/2020.socialnlp-1.4/) which is accepted in [SocialNLP@ACL 2020](https://sites.google.com/site/socialnlp2020):
```
@inproceedings{moon-etal-2020-beep,
    title = "{BEEP}! {K}orean Corpus of Online News Comments for Toxic Speech Detection",
    author = "Moon, Jihyung  and
      Cho, Won Ik  and
      Lee, Junbum",
    booktitle = "Proceedings of the Eighth International Workshop on Natural Language Processing for Social Media",
    month = jul,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.socialnlp-1.4",
    pages = "25--31",
    abstract = "Toxic comments in online platforms are an unavoidable social issue under the cloak of anonymity. Hate speech detection has been actively done for languages such as English, German, or Italian, where manually labeled corpus has been released. In this work, we first present 9.4K manually labeled entertainment news comments for identifying Korean toxic speech, collected from a widely used online news platform in Korea. The comments are annotated regarding social bias and hate speech since both aspects are correlated. The inter-annotator agreement Krippendorff{'}s alpha score is 0.492 and 0.496, respectively. We provide benchmarks using CharCNN, BiLSTM, and BERT, where BERT achieves the highest score on all tasks. The models generally display better performance on bias identification, since the hate speech detection is a more subjective issue. Additionally, when BERT is trained with bias label for hate speech detection, the prediction score increases, implying that bias and hate are intertwined. We make our dataset publicly available and open competitions with the corpus and benchmarks.",
}
```

## License
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
