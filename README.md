# ๐ฌ ๋ค์ค ๋๋ฉ์ธ ๋ํ ์ํ ์ถ์ 

## ๐์ต์ข ์ฑ์ 

- `Public LB`: Joint Goal Accuracy 0.8344 | 1๋ฑ๐ฅ
- `Private LB` : Joint Goal Accuracy 0.7335 | 1๋ฑ๐ฅ



## ๐Task Description

๋ฏธ๋ฆฌ ์ ์๋ ์๋๋ฆฌ์ค์ ๋ํ์์ (System๋ฐํ, User๋ฐํ)๋ฅผ ํ๋์ ํด์ผ๋ก ๋ ๋, ํด๋ง๋ค ์์ฐจ์ ์ผ๋ก ์ ์  ๋ฐํ์ **Dialogue state(๋ํ ์ํ)** ๋ฅผ ์ถ์ ํ๋ Task

- ***๊ธฐ๊ฐ*** : 2021.04.26 ~ 2021.05.21(4์ฃผ)

- ***Dialogue State Tracking description*** :

	- `Input` : Dialogue ๋ด์์ User์ System ๋ฐํ ์ (1 Turn ๋จ์)

	- `Output` : ํด๋น turn๊น์ง ๋์ ๋ Domain-Slot-Value์ pair

		![image](https://user-images.githubusercontent.com/38639633/122345725-23030d00-cf83-11eb-8023-e31719205950.png)

- ***Dataset Overview :*** Wizard-of-Seoul

	- ๋ฐ์ดํฐ๋ ์๋์ ๊ฐ์ ํ์์ผ๋ก ๊ตฌ์ฑ๋์ด ์์ผ๋ฉฐ, ์์ธกํด์ผํ๋ State๋ **"Domain - Slot - Value"** ์ pair๋ก ๊ตฌ์ฑ๋์ด ์์ต๋๋ค. 

		- `Domain`: 5๊ฐ Class
		- `Slot` : 45๊ฐ Class

		![image](https://user-images.githubusercontent.com/38639633/122349426-37490900-cf87-11eb-9573-59351903c8bb.png)

- ***Metric*** : ๋ชจ๋ธ์ **Joint Goal Accuracy**์ **Slot Accuracy**, ๊ทธ๋ฆฌ๊ณ  **Slot F1 Score** ์ธ ๊ฐ์ง๋ก ํ๊ฐ๋ฉ๋๋ค.

	- **Joint Goal Accuracy**๋ ์ถ๋ก ๋ Dialogue State์ ์ค์  Dialogue State์ **set**์ด ์๋ฒฝํ ์ผ์นํ๋์ง๋ฅผ ์ธก์ ํฉ๋๋ค. ์ฆ, ์ฌ๋ฌ ๊ฐ์ Slot ์ค ํ๋๋ผ๋ ํ๋ฆฌ๋ฉด 0์ ์ ๋ฐ๋ ๋งค์ฐ ํน๋ํ Metric์๋๋ค. ์ด์ ๋ฐํด, Slot Accuracy๋ ํด ๋ ๋ฒจ์ ์ธก์ ์ด ์๋ ๊ทธ ์์์ธ **(Slot, Value) pair**์ ๋ํ Accuracy๋ฅผ ์ธก์ ํฉ๋๋ค. ์ฌ์ง์ด ์๋ฌด๋ฐ Value๋ฅผ ์ถ๋ก ํ์ง ์๊ณ ๋ (== "none"์ผ๋ก ์์ธก), ์ ๋ฐ ์ด์์ ์ ์๋ฅผ ๋ผ ์ ์๋ ๋งค์ฐ ๊ด๋ํ Metric์๋๋ค.

	- ๋ฐ๋ผ์ ๋ณธ ๋ํ์์๋ JGA ๋ค์์ผ๋ก Slot-level์ F1 Score๋ฅผ ํจ๊ป ํ๊ฐํฉ๋๋ค. ("none"์ ์ํฅ๋ ฅ ์ฝํ)

	- ๋ฆฌ๋๋ณด๋๋ Joint Goal Accuracy โ Slot F1 Score โ Slot Accuracy๋ก ์ํ๋ฉ๋๋ค.

		![image](https://user-images.githubusercontent.com/38639633/123509101-9527d000-d6ae-11eb-83ff-574cf1248675.png)

<br/>

## :computer:Team Strategy 

[comment]: <> "์๋ ์ด๋ฏธ์ง๋ ์ฃผ์"
[comment]: <> "![image]&#40;https://user-images.githubusercontent.com/38639633/119125512-d0f6c680-ba6c-11eb-952e-fdc6de36fef9.png&#41;"

![image](https://user-images.githubusercontent.com/48181287/119263872-c9c1eb00-bc1b-11eb-916c-f6e171f1ba79.png)



<br><br>

## ๐ํ๋ก์ ํธ ๊ตฌ์กฐ

```
p3-dst-teamed-st>
โโโ README.md
โโโ coco
โ   โโโ classifier_train.py
โ   โโโ data_utils.py
โ   โโโ evaluation.py
โ   โโโ gen_train.py
โ   โโโ model.py
โ   โโโ preprocessor.py
โ   โโโ pretrain.py
โ   โโโ start_coco.py
โโโ data
โ   โโโ ontology.json
โ   โโโ slot_meta.json
โ   โโโ wos-v1_dev.json
โ   โโโ wos-v1_train.json
โโโ data_utils.py
โโโ eval_utils.py
โโโ evaluation.py
โโโ hardvote_v2.py
โโโ inference.py
โโโ loss.py
โโโ model
โ   โโโ somdst.py
โ   โโโ sumbt.py
โ   โโโ trade.py
โโโ preprocessor.py
โโโ requirements.txt
โโโ somdst_train.py
โโโ sumbt_train.py
โโโ trade_train.py
```

### :open_file_folder:File overview 

- `coco` : CoCo augmentation์ ์ํ data generation folder
- `data` : [KLUE WOS](https://klue-benchmark.com/tasks/73/data/description) banchmark dataset (2021.06 ๊ธฐ์ค)
- `model` : ํ์ต์ ์ฌ์ฉํ 3๊ฐ์ง ๋ชจ๋ธ Class
- `data_utils.py` : data util
- `eval_utils.py` : evaluation์ ์ํ utils
- `evaluation.py` : evaluation print
- `hardvote_v2.py` : ์์๋ธ์ ์ํ hardvoting file
- `inference.py` : model prediction์ ์ํ fils
- `loss.py` : masked_cross_entropy loss
- `preprocessor.py` : model๋ณ preprocessor
- `somdst_train.py` : som-dst ํ์ต
- `sumbt_train.py` : sumbt ํ์ต
- `trade_train.py` : trade ํ์ต



<br><br>

## :page_facing_up:Installation 

#### Dependencies

- torch==1.7.0+cu101
- transformers==3.5.1

<!-- - pytorch-pretrained-bert -->

```
pip install -r requirements.txt
```

<br><br>

## ๐งฌFinal Model

###  Trade

- Open vocab ๊ธฐ๋ฐ์ DST model๋ก Unseen value๋ฅผ ๋ง์ถ ์ ์์ต๋๋ค.

- ๋ชจ๋  Slot์ ์ ๋ถ ์์ธกํด์ผ ํ๊ธฐ ๋๋ฌธ์ ์๋๊ฐ ๋๋ฆฌ๋ค๋ ๋จ์ ์ด ์์ง๋ง ๊ทธ ๋จ์ ์ ๋ณด์ํ๊ธฐ ์ํด Parallel decoding์ด ์ฌ์ฉ๋์์ต๋๋ค.

- Utterance Encoder์ ์ฑ๋ฅ๊ฐ์ ์ ์ํด bidirection RNN Encoder๋ฅผ BERT๋ก ๊ต์ฒดํ์์ต๋๋ค.

![แแณแแณแแตแซแแฃแบ 2021-06-18 10 15 51](https://user-images.githubusercontent.com/67869514/122490995-18e21c80-d01e-11eb-93e5-5f44cced27a6.png)


- ์ฌ์ฉ๋ฒ
```
# trade_train.py
python trade_train.py --save_dir ./output
```

<br><br>

### SUMBT

- Ontology ๊ธฐ๋ฐ์ DST model๋ก ์ด๋ฆ๊ฐ์ด value์ ๊ฐฏ์๊ฐ ๋ง์ slot์ ์ ๋ฆฌํฉ๋๋ค.
- Unseen value๋ฅผ ๋ง์ถ์ง ๋ชปํ๋ค๋ ๋จ์ ์ด ์์ง๋ง ๋ํ์์ open vocab ๊ธฐ๋ฐ ๋ชจ๋ธ์ธ SOM-DST์ output์ ์๋ก์ด Ontology๋ก ์ฌ์ฉํ์ฌ ๊ฐ์ ํ์์ต๋๋ค.

![](https://i.imgur.com/kNcXCxB.png)

- ์ฌ์ฉ๋ฒ
```
# sumbt_train.py
python sumbt_train.py --save_dir ./output
```

<br><br>

### SOM-DST

- Open vocab ๊ธฐ๋ฐ์ DST model ์ด๋ฉฐ TRADE์ ๋ชจ๋  slot์ generationํ๋๊ฑด ๋นํจ์จ ์ ์ด๋ผ๋ ๋จ์ ์ ๋ณด์ํ๊ธฐ์ํด ๋ฑ์ฅํ ๋ชจ๋ธ
- Utterance๋ฅผ ๋ณด๊ณ  UPDATE๊ฐ ํ์ํ ๊ฒฝ์ฐ์๋ง generation


![](https://i.imgur.com/d82ZWqz.png)



- ์ฌ์ฉ๋ฒ
```
# somdst_train.py
python somdst_train.py --save_dir ./output
```

<br><br>

### data augumentation

#### CoCo

- ์์ฃผ ์ฌ์ฉ ๋๋ slot์ ์กฐํฉ(ex. ํ์-๋ชฉ์ ์ง, ๋์ฐฉ-์๊ฐ)์ด ์๋๊ฒฝ์ฐ ๋ง์ถ์ง ๋ชปํ๋ Counter factual์ ์ง์ ํ ๋ผ๋ฌธ
- pretrained๋ BartForConditionalGeneration๋ฅผ ์ฌ์ฉํ์ฌ utterance๋ฅผ generation
- pretrained๋ classifier๋ก state๋ฅผ ์ถ์ถํ๊ณ  role based Slot value match filter๋ก ํํฐ๋ง์ ๊ฑฐ์ณ์ง utterance๋ฅผ augumentation data๋ก ์ฌ์ฉ.
![](https://i.imgur.com/EHq2uO3.png)

- :exclamation: ์ ๋๊ฒฝ๋ก ์ฌ์ฉ์ ์ฃผ์
```
# get generation model, classifier model
# coco/pretrain.py
python pretrain.py

# coco/start_coco.py
python start_coco.py
```

<br><br>

### Ensemble

#### hardvoting

![](https://i.imgur.com/soAswyD.png)

`SLOT_FIRST_AND_TOP_VALUE`: ๋๋ถ๋ฅ์ธ ์ฌ๋กฏ์ ๋จผ์  ํฌํ๋ฅผ ํ ๋ค์, ํด๋น ์ฌ๋กฏ ์์์ ๊ฐ์ฅ ๋ง์ ํ๋ฅผ ๋ฐ์ value๊ฐ์ ์ ํ

```
# hardvote_v2.py
python hardvot_v2.py mode=save --csv_dir=./output --save_dir=./hardvoting_result
```

<br><br>

## Reference

### paper

- [SUMBT: Slot-Utterance Matching for Universal and Scalable Belief Tracking](https://www.aclweb.org/anthology/P19-1546/)
- [TRADE: Transferable Multi-Domain State Generator for Task-Oriented Dialogue Systems](https://www.aclweb.org/anthology/P19-1078/)
- [SOM-DST:Efficient Dialogue State Tracking by Selectively Overwriting Memory](https://arxiv.org/abs/1911.03906)
- [TAPT : Don't Stop Pretraining: Adapt Language Models to Domains and Tasks](https://arxiv.org/abs/2004.10964)
- [CoCo : Controllable Counterfactuals for Evaluating Dialogue State Trackers](https://arxiv.org/abs/2010.12850)

### Github

- [SUMBT github](https://github.com/SKTBrain/SUMBT)
- [TRADE github](https://github.com/jasonwu0731/trade-dst)
- [SOM-DST github](https://github.com/clovaai/som-dst)

### Dataset

- [MultiWOZ 2.1](https://paperswithcode.com/dataset/multiwoz)
- [KLUE:WOS](https://klue-benchmark.com/tasks/73/data/description)



## :man_technologist: Contributors

[์ค๋์ฐ(ydy8989)](https://github.com/ydy8989) | [์ ์ฌ์ด(Jayten)](https://github.com/jayten-jeon) | [์ค์ฌํ(anawkward)](https://github.com/anawkward) | [๋ฏผ์ฌ์(ekzm8523)](https://github.com/ekzm8523) | [๊น๋ด์ง(BongjinKim)](https://github.com/BongjinKim) | [์ค์ธ๋ฏผ(osmosm7)](https://github.com/osmosm7)







