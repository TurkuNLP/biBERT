# biBERT

## Quickstart

Download the models here:

* [Cased Finnish-English biBERT 70k](http://dl.turkunlp.org/iwpt2020/berts/bibert-70k-base-cased/)
* [Cased Finnish-English biBERT 80k](http://dl.turkunlp.org/iwpt2020/berts/bibert-80k-base-cased/)

## What's this?

Finnish-English bilingual BERT models (biBERTs) are Google's [BERT](https://github.com/google-research/bert) model trained for both English and Finnish.

Two versions of biBERT have been trained, one with a custom 70k wordpiece vocabulary, the other 80k. The vocabulary size is roughly that of the sum of Google's English BERT (30k) and FinBERT (50k). In the vocabulary, there is no distinction between English and Finnish wordpieces, i.e., the models have a joint vocabulary for English and Finnish.

The model's performance have been evaluated on both English and Finnish benchmarks. The Finnish benchmarks have also been used to evaluate [FinBERT](https://github.com/TurkuNLP/FinBERT).

## Data

biBERTs are trained on both English and Finnish data (no parallel corpus is used). For English, Wikipedia and a reconstructed BookCorpus were used for pre-training. For Finnish, the same data used to train [FinBERT](https://github.com/TurkuNLP/FinBERT) were used, which include Finnish news, online discussion, as well as internet crawl.

## Results

### Document classification

![learning curves for Yle and Ylilauta document classification](https://raw.githubusercontent.com/TurkuNLP/biBERT/master/img/yle-ylilauta-curves.png)

[[code](https://github.com/spyysalo/finbert-text-classification)][[Yle data](https://github.com/spyysalo/yle-corpus)] [[Ylilauta data](https://github.com/spyysalo/ylilauta-corpus)]

### Named Entity Recognition

Evaluation on FiNER corpus ([Ruokolainen et al 2019](https://arxiv.org/abs/1908.04212))

| Model        | Accuracy |
|--------------------|----------|
| **FinBERT**  | **92.40%** |
| biBERT 70k | 92.34% |
| biBERT 80k | 92.23% |
| Multilingual BERT | 90.29% |
| [FiNER-tagger](https://github.com/Traubert/FiNer-rules) (rule-based) | 86.82%      |

(FiNER tagger results from [Ruokolainen et al. 2019](https://arxiv.org/pdf/1908.04212.pdf))

[[code](https://github.com/jouniluoma/keras-bert-ner)][[data](https://github.com/mpsilfve/finer-data)]

### Part of speech tagging

Evaluation on three Finnish corpora annotated with [Universal Dependencies](https://universaldependencies.org/) part-of-speech tags: the Turku Dependency Treebank (TDT), FinnTreeBank (FTB), and Parallel UD treebank (PUD)

| Model             |     TDT     |     FTB     |     PUD     |
|-------------------|-------------|-------------|-------------|
| **FinBERT**       | **98.23%**  | **98.39%**  | **98.08%**  |
| biBERT 70k	    |   98.17%    |   98.30%    | **98.08%**  |
| biBERT 80k	    |   98.14%    |   98.16%    |   98.07%    |
| Multilingual BERT |   96.97%    |   95.87%    |   97.58%    |

[[code](https://github.com/spyysalo/bert-pos)][[data](http://hdl.handle.net/11234/1-2837)]

### Dependency parsing

Evaluation on the same corpora used in POS-tagging: TDT, FTB, and PUD

Labeled attachment score (LAS) parsing results for predicted (p.seg.) and gold (g.seg.) segmentation.

|                   |         TDT       |        FTB        |        PUD        |
|       Model       |   p.seg. g.seg.   |   p.seg. g.seg.   |   p.seg. g.seg.   |
|-------------------|-------------------|-------------------|-------------------|
| **FinBERT**       | **91.93% 93.56%** | **92.16% 93.95%** | **92.54% 93.10%** |
| biBERT 70k	    |   91.35% 92.93%   |   91.68% 93.49%   |   92.18% 92.74%   |
| biBERT 80k	    |   91.59% 93.16%   |   91.76% 93.50%   |   92.37% 93.02%   |
| Multilingual BERT |   86.32% 87.99%   |   85.52% 87.46%   |   89.18% 89.75%   |

[[code](https://github.com/jmnybl/udify/)][[data](http://hdl.handle.net/11234/1-2837)]