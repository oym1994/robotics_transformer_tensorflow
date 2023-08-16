# Robotics Transformer

*This is not an officially supported Google product.*


This repository is a collection code files and artifacts for running
Robotics Transformer or RT-1.

## Features

* Film efficient net based image tokenizer backbone
* Token learner based compression of input tokens
* Transformer for end to end robotic control
* Testing utilities

## Getting Started

### Installation
Clone the repo
```bash
git clone https://github.com/google-research/robotics_transformer.git
pip install -r robotics_transformer/requirements.txt
python -m robotics_transformer.tokenizers.action_tokenizer.test
```

### Running Tests

To run RT-1 tests, you can clone the git repo and run
[bazel](https://bazel.build/):

```bash
git clone https://github.com/google_research/robotics_transformer.git
cd robotics_transformer
bazel test ...
```

### Using trained checkpoints
Checkpoints are included in trained_checkpoints/ folder for three models:
1. [RT-1 trained on 700 tasks](trained_checkpoints/rt1main)
2. [RT-1 jointly trained on EDR and Kuka data](trained_checkpoints/rt1multirobot)
3. [RT-1 jointly trained on sim and real data](trained_checkpoints/rt1simreal)

They are tensorflow SavedModel files. Instructions on usage can be found [here](https://www.tensorflow.org/guide/saved_model)


## Future Releases

The current repository includes an initial set of libraries for early adoption.
More components may come in future releases.

## License

The Robotics Transformer library is licensed under the terms of the Apache
license.

## 新增内容
本工程来自于google的robotics transformer工作，在此基础上增加了:
    
    1,读取rlds数据，以language table为例
    2,增加分布式训练代码
   
## 训练
    step1, 下载language_table数据, 见https://github.com/google-research/language-table
    step2, 下载Universal Sentence Encoder模型，将数据集中的文本(UTF-8)转化成USE embedding，依然是RLDS格式
    step3, 设置distribute_train.py里的变量
    step4, 开启训练 python distribute_train.py

## 未来工作
    1, 使用RT1开源的数据集进行训练，编写相应数据加载代码;
    2, 使用梯度累积，混合精度训练，增加单卡batch_size;
    3, 融合更多传感器信息，如深度等;
    抛砖引玉，欢迎大家提pull request

   