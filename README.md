# KsponSpeech-preprocess
#### Pre-processing KsponSpeech corpus priveded by AI Hub
  
[Soohwan Kim](https://github.com/sooftware)<sup>1,3</sup>, [Seyoung Bae](https://github.com/triplet02)<sup>1</sup>, [Cheolhwang Won](https://github.com/wch18735)<sup>1</sup>, [Soyoung Cho](https://github.com/SoYoungCho)<sup>2</sup> [Jeongwon Kwak](https://github.com/jeongwonkwak)<sup>2</sup>  
  
<sup>1</sup>Electronic and Communication Engineering, Kwangwoon Univ. <sup>2</sup>Data Science, Kwangwoon Univ. <sup>3</sup>KakaoBrain Corp.  
   
It's been a while since KsponSpeech was released, but it's hard to compare performance because there's no established preprocessing method. So we're revealing the pre-processing method we used in the [KoSpeech](https://github.com/sooftware/KoSpeech) project. This project provides processing in characters, subwords, and grapheme units.    
  
## Intro

`KsponSpeech-preprocess` is repository for pre-processing `KsponSpeech corpus` provided by AI Hub.  
**KsponSpeech corpus** is a **1000h** Korean speech data corpus provided by [AI Hub](http://www.aihub.or.kr/) in Korea.   
Anyone can download this dataset just by applying. The transcription rules can see [here](http://www.aihub.or.kr/sites/default/files/2019-12/%ED%95%9C%EA%B5%AD%EC%96%B4%20%EC%9D%8C%EC%84%B1%20%EC%A0%84%EC%82%AC%EA%B7%9C%EC%B9%99%20v1.0.pdf).  
  
You can pre-process in various output-units, such as ***character, subword, grapheme***  
We will explain the details in the **Output-Unit** part below.
   
## Prerequisites
* Pandas: `pip install pandas` (Refer [here](https://github.com/pandas-dev/pandas) for problem installing Pandas)  
* Sentencepiece: `pip install sentencepiece` (Refer [here](https://github.com/google/sentencepiece) for problem installing Sentencepiece) 
* hgtk: `pip install hgtk` (Refer [here](https://github.com/bluedisk/hangul-toolkit) for problem installing hgtk)   
* gluonnlp: `pip install gluonnlp` (Refer [here](https://github.com/dmlc/gluon-nlp) for problem installing gluonnlp)
* KoBert: (Optional) Refer [here](https://github.com/SKTBrain/KoBERT) for installing   
  
## Usage
  
1. Set options in [run.sh](https://github.com/sooftware/KsponSpeech-preprocess/blob/master/run.sh)  
  
<img src="https://user-images.githubusercontent.com/42150335/90811422-8ae6c800-e35f-11ea-8768-5b9cd3417fab.png" width=700>
  
  
2. Run [run.sh](https://github.com/sooftware/KsponSpeech-preprocess/blob/master/run.sh)  
```shell
$ ./run.sh
```
  
3. Leave the computer for hours or days.  
   
## Preprocess
  
You can choose between phonetic transcription and spelling transcription to preprocess.  
  
* Raw data
```
b/ (70%)/(칠 십 퍼센트) 확률이라니 아/ (뭐+ 뭔)/(모+ 몬) 소리야 진짜 (100%)(백 프로)가 왜 안돼? n/
``` 
  
* Delete noise labels, such as b/, n/, / ..
```
(70%)/(칠 십 퍼센트) 확률이라니 아/ (뭐+ 뭔)/(모+ 몬) 소리야 진짜 (100%)(백 프로)가 왜 안돼?
```
  
* Delete labels such as '/', '*', '+', etc. (used for interjection representation)
```
(70%)/(칠 십 퍼센트) 확률이라니 아 (뭐 뭔)/(모 몬) 소리야 진짜 (100%)(백 프로)가 왜 안돼?
```
  
* Option1 : phonetic transcript
```
칠 십 퍼센트 확률이라니 아 모 몬 소리야 진짜 백 프로가 왜 안돼?
```

* Option2 : spelling transcript
```
70% 확률이라니 아 뭐 뭔 소리야 진짜 100%가 왜 안돼?
```
* Option3 : numeric_phonetic_otherwise_spelling
```
칠 십 퍼센트 확률이라니 아 뭐 뭔 소리야 진짜 백 프로가 왜 안돼?
```
  
## Output-Unit
   
This project provides processing in characters, subwords, and grapheme units.   
  
* Character-Unit
```
아 모 몬 소리야 칠 십 퍼센트 확률이라니
```
  
* Subword-Unit
```
▁아 ▁모 ▁ 몬 ▁소리 야 ▁ 칠 ▁ 십 ▁퍼 센트 ▁확 률 이라 니
```

* Grapheme-Unit
```
ㅇㅏ ㅁㅗ ㅁㅗㄴ ㅅㅗㄹㅣㅇㅑ ㅊㅣㄹ ㅅㅣㅂ ㅍㅓㅅㅔㄴㅌㅡ ㅎㅘㄱㄹㅠㄹㅇㅣㄹㅏㄴㅣ
```
   
## Conversion to id
  
* transcript
```
아 모 몬 소리야 칠 십 퍼센트 확률이라니
```

* conversion
```
7 3 106 3 730 3 173 32 26 3 319 3 120 3 490 552 157 3 315 747 5 33 22
```
   
## Troubleshoots and Contributing
  
If you have any questions, bug reports, and feature requests, please [open an issue](https://github.com/sooftware/KsponSpeech.preprocess/issues) on Github.   
For live discussions, please go to our [gitter](https://gitter.im/Korean-Speech-Recognition/community) or Contacts sh951011@gmail.com please.  
  
I appreciate any kind of feedback or contribution.  Feel free to proceed with small issues like bug fixes, documentation improvement.  For major contributions and new features, please discuss with the collaborators in corresponding issues.  
  
## Reference
  
* [KoBert](https://github.com/SKTBrain/KoBERT)  
* [Sentencepiece](https://github.com/google/sentencepiece)  
* [hgtk](https://github.com/bluedisk/hangul-toolkit)  
  
## Author
* [Soohwan Kim](https://github.com/sooftware), [Seyoung Bae](https://github.com/triplet02),  [Cheolhwang Won](https://github.com/wch18735), [Soyoung Cho](https://github.com/SoYoungCho), [Jeongwon Kwak](https://github.com/jeongwonkwak)
* Contacts: sh951011@gmail.com
