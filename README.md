# Korean HateSpeech Dataset

We provide the first human-annotated Korean corpus for toxic speech detection and the large unlabeled corpus. <br>
The data is comments from the Korean entertainment news aggregation platform. 



## Data description

The dataset consists of 3 parts: 1) `labeled` 2) `unlabeled` and 3) `news_title`.

#### 1. `labeled`
There are **9.4K** human-labeled comments. 
Each comment is annotated on two aspects, the existence of **social bias** and **hate speech**, given that hate speech is closely related to bias. <br>

For social bias, we present `gender bias`, `other biases`, and `none` labels. 
Considering the context of Korean entertainment news where public figures encounter stereotypes mostly intertwined with *gender*, we weigh more on the prevalent bias. <br>
We also added binary label `whether a comment contains gender bias or not`. <br>
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


#### 3. `news_comments`


#### 4. `guideline`

[Guideline (`ko`)](https://www.notion.so/c1ecb7cc52d446cc93d928d172ef8442) is publicly available. 





## Data Statistics

Total: 9,381


## Usage

https://github.com/inmoonlight/koco

## Kaggle competition

www.kaggle.com/c/koreangenderbiasdetection
www.kaggle.com/c/koreanbiasdetection
www.kaggle.com/c/koreanhatespeech

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
