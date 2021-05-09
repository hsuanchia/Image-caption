# Image caption project
## 規範(主要寫給hsuanchia看的)
1. 能寫中文就寫中文， 除了專有名詞跟大家都有共識的詞彙，否則一律使用中文
   * 包含commit, 註解...etc
2. Code 盡量寫的簡潔，否則一定要寫註解，不寫沒有人看得懂你在衝三小
3. 每次在 Colab 上改完一個段落，就更新上傳到 GitHub
4. 訓練好的Model請放到Models的資料夾下面，傳上來的model請務必要用commit來記錄訓練資訊
   * Model命名規則: Base on 哪篇paper的架構_000n ex.Visualattention_0001
   * 訓練資訊包含: 使用多少資料, epochs
## Dataset
* [MSCOCO 2017](https://drive.google.com/drive/folders/1fN9Zl8yX4MjQY1ljAY2py_7l7-vkCMHu?usp=sharing)

## Feature Map & Captions (pickle)

* [link](https://drive.google.com/drive/folders/1V0qwaIfv6hYvhINFcsSLVRDcovdNX-BD?usp=sharing)
* [忘了補上的新 dataset ...](https://drive.google.com/drive/folders/1MbG8gn-g0_w2MRuWmTwCyQzmKOKVWEyJ?usp=sharing)

### Load
```python
import pickle
with open('output_500.pkl', 'rb') as fp:
  data = pickle.load(fp)
```

### data
```
[
    {
        'filename': '000000415840.jpg',
        'feature': NUMPY_ARRAY,
        'captions': [
            'A silver and red train traveling down a busy city street.',
            'A grey train passes on a city street.',
            'Electric rail cars move along a track between automobile traffic lanes. ',
            'A silver and orange bus is on a city street.',
            'The trolley for the San Francisco Zoo is on its tracks.'
        ]
    }
]
```
## Architecture
### Soft Attention![](https://i.imgur.com/aFu5aEa.jpg)
### Seq2seq![](https://i.imgur.com/dKlAlH8.jpg)
