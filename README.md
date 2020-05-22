# Korean HateSpeech Dataset

We provide the first human-annotated Korean corpus for toxic speech detection and the large unlabeled corpus. <br>
The data is comments from the Korean entertainment news aggregation platform. 

## Dataset description

The dataset consists of 3 parts: 1) `labeled` 2) `unlabeled` and 3) `news_title`.

#### 1. `labeled`
There are **9,381** human-labeled comments in total. They are splitted into 7,896 training set, 471 validation set, and 974 test set. (We left test set labels undisclosed for the fair comparison of prediction models. One can be evaluated via the Kaggle submission which will be described later in this document.) Each comment is annotated on two aspects, the existence of **social bias** and **hate speech**, given that hate speech is closely related to bias. <br>

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

We additionally provide 2,034,837 `unlabeled` comments since `labeled` data is limited. <br>
This unlabeled dataset can be used in various ways: pretraining language model, semi-supervised learning, and so on.

#### 3. `news_title`




## Usage

[`koco`](https://github.com/inmoonlight/koco) is a library to easily access `kocohub` datasets.

For `korean-hate-speech`, we can load datasets by using this code:
```python
import koco

train_dev = koco.load_dataset('korean-hate-speech', mode='train_dev')
unlabeled = koco.load_dataset('korean-hate-speech', mode='unlabeled')
test = koco.load_dataset('korean-hate-speech', mode='test')
```



## Kaggle competition

www.kaggle.com/c/koreangenderbiasdetection

www.kaggle.com/c/koreanbiasdetection

www.kaggle.com/c/koreanhatespeech


## Annotation Guideline

[Guideline (`ko`)](https://www.notion.so/c1ecb7cc52d446cc93d928d172ef8442) is publicly available. 


## Contributors

The main contributors of the work are: 
- [Jihyung Moon](https://github.com/inmoonlight)\*
- [Won Ik Cho](https://github.com/warnikchow)\*
- [Junbum Lee](https://github.com/beomi)

\*: Equal Contribution

Note that this project is an independent research and was not supported by any of the organizations. <br>
Instead, we had an individual sponsor [Hyunjoong Kim](https://github.com/lovit) and we sincerely thank [Hyunjoong Kim](https://github.com/lovit) for providing financial support :heart:

## References

If you find this dataset useful, feel free to cite our publication [BEEP! Korean Corpus of Online News Comments for Toxic Speech Detection]():
```
TBD
```

## License
<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
