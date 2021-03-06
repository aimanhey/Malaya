# Tiny-BERT-Bahasa

Thanks to [huawei-noah](https://github.com/huawei-noah) for opensourcing most of the source code to develop Tiny-BERT, https://github.com/huawei-noah/Pretrained-Language-Model/tree/master/TinyBERT. Malaya just edit the scripts to accept sentencepience tokenizer and save it to Tensorflow.

## Table of contents
  * [Objective](#objective)
  * [Acknowledgement](#acknowledgement)
  * [How-to](#how-to)
  * [Citation](#citation)
  * [Donation](#donation)

## Objective

1. Provide Tiny-BERT for Bahasa.

## Acknowledgement

Thanks to [Im Big](https://www.facebook.com/imbigofficial/), [LigBlou](https://www.facebook.com/ligblou), [Mesolitica](https://mesolitica.com/) and [KeyReply](https://www.keyreply.com/) for sponsoring AWS, Google and GPU clouds to train Tiny-BERT for Bahasa.

## How-to

1. Copy any sentencepiece tokenizer you need, in the script, I will use [sp10m.cased.bert.model](../preprocess/sp10m.cased.bert.model) and [sp10m.cased.bert.vocab](../preprocess/sp10m.cased.bert.vocab)

2. Run [pregenerate_training_data.py](pregenerate_training_data.py),

```bash
python3 pregenerate_training_data.py --train_corpus ../bert/dumping-pdf.txt \
--num_workers 10 \
--output_dir .
```

3. Run [general_distill.py](general_distill.py),

```bash
python3 general_distill.py --pregenerated_data . --num_train_epochs 10 \
--teacher_model bert-base-bahasa-cased \
--student_model student \
--train_batch_size 128 --output_dir tiny-bert-bahasa-cased
```

4. Run [bert-pytorch-to-tf1.ipynb](bert-pytorch-to-tf1.ipynb) to convert Pytorch to TF 1.X model.

## Citation

1. Please citate the repository if use these checkpoints.

```
@misc{Malaya, Natural-Language-Toolkit library for bahasa Malaysia, powered by Deep Learning Tensorflow,
  author = {Husein, Zolkepli},
  title = {Malaya},
  year = {2018},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/huseinzol05/malaya}}
}
```

2. Please at least email us first before distributing these checkpoints. Remember all these hard workings we want to give it for free.
3. What do you see just the checkpoints, but nobody can see how much we spent our cost to make it public.

## Donation

<a href="https://www.patreon.com/bePatron?u=7291337"><img src="https://static1.squarespace.com/static/54a1b506e4b097c5f153486a/t/58a722ec893fc0a0b7745b45/1487348853811/patreon+art.jpeg" width="40%"></a>

Or, One time donation without credit card hustle, **7053174643, CIMB Bank, Husein Zolkepli**
