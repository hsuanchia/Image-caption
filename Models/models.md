# Model使用說明
* 訓練好的model都放在我的MSCOCO2017雲端資料夾裡面，你們應該都進得去
* 我盡量把我還記得我train出來的model的output跟資料記錄在下面，有的是train起來沒用的或是我忘記在幹嘛的就沒有辦法了
* 以後要做caption用generate_caption.ipynb，詳情請看檔案的comment
* 如果以後你們有train好的model你們有幾個選擇:
  * 放在跟我的model的同一個地方，在下方紀錄
  * 放在你自己的雲端，但要開共用給我們使用，並在下方紀錄
  * 直接傳上來github，model命名規則請參照README
## Model 的基本資料
### Visual attention
* No attention(seq2seq)
  * [Model 1](https://drive.google.com/file/d/1HS_-59ZPN-iFfhbZcXKBOc2O57YHE7L_/view?usp=sharing) 
    * training data: 前 500 句 val_2017 caption
    * Encoder output shape: (None, 4096)
    * 適用Voc: 使用全部Val2017
    * training detail: 100 epochs, loss: 0.4447, sparse_categorical_accuracy: 0.9024
  * [Model 2](https://drive.google.com/file/d/1--a87SVWD326r5raOMyRO-EusW9puaph/view?usp=sharing)
    * training data: 下方將val2017前25000筆資料處理好的資料
    * Encoder output shape: (None, 4096)
    * 適用Voc: 使用全部Val2017統計， 只取出現頻率超過10的詞彙
  * [Model 3](https://drive.google.com/file/d/1EZSKYim10Fa-CJAEhrzE2Og3X1CiPhRg/view?usp=sharing)
    * training data: 將 @snsd0805 給的train2017 5000 筆資料處理好的資料
    * Encoder output shape: (None, 14, 14, 512)
    * 適用Voc: 使用全部Train2017統計， 只取出現頻率超過5的詞彙
    * training detail: 1000 epochs with earlystop(loss = 5) -> stop in 82 epochs, loss: 0.2355, sparse_categorical_accuracy: 0.7767
  * [Model 4](https://drive.google.com/file/d/1MUSx669M3YRU6vDifyK_PYqaGu-4aQrL/view?usp=sharing)
    * training data: [14x14x512 train2017](https://drive.google.com/file/d/1mX6YlBP0BTuW8LZm4-8G62UDgzB8Rr66/view?usp=sharing)
    * Encoder output shape: (None, 14, 14, 512)
    * 適用Voc: 使用全部Train2017統計， 只取出現頻率超過5的詞彙
    * training detail: 100 epochs with earlystop(loss = 5) -> no stop, loss: 0.6586, sparse_categorical_accuracy: 0.6037
    * 備註:有加入unknown token機制, 但有bug -> 每次預測的句尾比出現一個unk
* Soft attention
## Preprocess 好的資料
* [將val2017前25000筆資料處理好的pkl](https://drive.google.com/file/d/1mwQO6DgW_KFJvKQMlQb4bZWoXmx_igoT/view?usp=sharing)
```
[ 'input': [feature_map(none,4096), labeled caption], 'output' : labeled ground truth]
```
* [將 @snsd0805 給的train2017 5000筆資料處理好的pkl](https://drive.google.com/file/d/1--RoXq8R3fQMLkM1VNvCKA6m2NOHfwJJ/view?usp=sharing)
```
[ 'input': [feature_map(none,14,14,512), labeled caption], 'output' : labeled ground truth]
```
* [用 Train2017 的所有annotation統計出來的voc, 只取出現頻率超過5的詞彙, 加上unk](https://drive.google.com/file/d/1Dht3wvrohwqFQziOl8SlPVr0xaLE_pTB/view?usp=sharing)
* [用 Train2017 的所有annotation統計出來的voc, 只取出現頻率超過5的詞彙](https://drive.google.com/file/d/1-4EFf00eOz5uuk5DtIWCz18lHwx1p-ar/view?usp=sharing)
* [用 Val2017 的所有annotation統計出來的voc, 只取出現頻率超過10的詞彙](https://drive.google.com/file/d/1uIbj_PhQBxa7-YTwkwj7Wlr4TfeFCHeM/view?usp=sharing)
* [用 Val2017 的所有annotation統計出來的voc](https://drive.google.com/file/d/1VcbEhK8XmsmtJy8gCtuqn70XF_7Z3HV4/view?usp=sharing)
