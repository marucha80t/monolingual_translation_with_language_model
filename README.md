# Monolingual Translation with Language Model
An implimentation of transformer-based language model for monolingual translation tasks
such as summarization, text simplification, and grammatical error correction.
The following figure is the architecture overview. This model recives a input that
joint original sentence and simplified sentence by special token \<SEP\>, which means
the delimiter. This model is very simple, but significantly outperforms 
the strong baselines in text summarization task.

![]()
<br>


## Installation
```sh
git clone https://github.com/marucha80t/monolingual_translation_with_language_model.git
cd ./monolingual_translation_with_language_model
pip install -r requirements.txt
```
<br>


## Usages
### Training
The datasets for training and validation are must be tsv format.
The source senteces and target sentences must be segmented to words by whitespace.
If you want to use gpu, please set option `--gpu`.
Also, if you want to train a model again, you can use `--re-training /path/to/model`.

```sh
python train.py --train ./data/sample_train.tsv --valid ./data/sample_valid.tsv --savedir ./checkpoints --gpu
```

### Translation
In translation step, you must set option `--model` and `--input`.
You can set sentence length of model's output using `--maxlen` option (default: 100 tokens).

```sh
python generate.py --model ./checkpoints/checkpoint_best.pt --input ./data/sample_test.txt --gpu
```

<br>



## 参考
- [Sample Efficient Text Summarization Using a Single Pre-Trained Transformer](https://arxiv.org/abs/1905.08836)
- [Efficient Adaptation of Pretrained Transformers for Abstractive Summarization](https://arxiv.org/abs/1906.00138)

