# 👾 + 📚 dbmdz German BERT model

In this repository the MDZ Digital Library team (dbmdz) at the Bavarian State
Library open source another German BERT model 🎉

# Changelog

* 24.09.2019: Initial version

# Stats

In addition to the recently released [German BERT](https://deepset.ai/german-bert)
model by [deepset](https://deepset.ai/) we provide another model.

We use a recent Wikipedia dump, EU Bookshop corpus, Open Subtitles, CommonCrawl,
ParaCrawl and News Crawl. This results in a dataset with a size of 16GB and
2,350,234,427 token.

We used [spacy](https://spacy.io/) in order to perform sentence splitting. We
follow the pre-processing steps (sentence piece model for vocab generation) as
used for training [SciBERT](https://github.com/allenai/scibert). We train a
model with an initial sequence length of 512 subwords for 1.5M steps.

We train and release both cased and uncased models.

# Model weights

We provide PyTorch-Transformers compatible weights. If you need access to the
TensorFlow checkpoints, please raise an issue!

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
