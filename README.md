# 🤗 + 📚 dbmdz German BERT model

In this repository the MDZ Digital Library team (dbmdz) at the Bavarian State
Library open sources another German BERT model 🎉

# Changelog

* 24.09.2019: Initial version

# Stats

In addition to the recently released [German BERT](https://deepset.ai/german-bert)
model by [deepset](https://deepset.ai/) we provide another German-language model.

The source data for the model consists of a recent Wikipedia dump, EU Bookshop corpus,
Open Subtitles, CommonCrawl, ParaCrawl and News Crawl. This results in a dataset with
a size of 16GB and 2,350,234,427 tokens.

For sentence splitting, we use [spacy](https://spacy.io/). Our preprocessing steps
(sentence piece model for vocab generation) follow those used for training
[SciBERT](https://github.com/allenai/scibert). The model is trained with an initial
sequence length of 512 subwords and was performed for 1.5M steps.

This release includes both cased and uncased models.

# Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                            | Downloads
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `bert-base-german-dbmdz-cased`   | [`config.json`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-cased-config.json) • [`pytorch_model.bin`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-cased-pytorch_model.bin) • [`vocab.txt`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-cased-vocab.txt)
| `bert-base-german-dbmdz-uncased` | [`config.json`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-uncased-config.json) • [`pytorch_model.bin`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-uncased-pytorch_model.bin) • [`vocab.txt`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-uncased-vocab.txt)

## Cased model

* `config.json`, see [link](https://schweter.eu/cloud/germabert-base-cased/config.json)
* `pytorch_model.bin`, see [link](https://schweter.eu/cloud/germabert-base-cased/pytorch_model.bin)
* `vocab.txt`, see [link](https://schweter.eu/cloud/germabert-base-cased/vocab.txt)

## Uncased model

* `config.json`, see [link](https://schweter.eu/cloud/germabert-base-uncased/config.json)
* `pytorch_model.bin`, see [link](https://schweter.eu/cloud/germabert-base-uncased/pytorch_model.bin)
* `vocab.txt`, see [link](https://schweter.eu/cloud/germabert-base-uncased/vocab.txt)

# Results

For results on downstream tasks like NER or PoS tagging, please refer to
[this repository](https://github.com/stefan-it/fine-tuned-berts-seq).

# Contact (Bugs, Feedback, Contribution and more)

For questions about *german-bert* just open an issue
[here](https://github.com/dbmdz/german-bert/issues/new) 🤗
