# 🤗 + 📚 dbmdz BERT models

In this repository the MDZ Digital Library team (dbmdz) at the Bavarian State
Library open sources another BERT models 🎉

# Changelog

* 11.03.2020: Public release of cased distilled BERT model for Turkish: DistilBERTurk
* 17.02.2020: Public release of cased BERT model for Turkish: BERTurk
* 10.02.2020: Public release of cased and uncased BERT models for Historic German: German Europeana BERT
* 20.01.2019: Public release of cased and uncased XXL BERT models for Italian. They can be downloaded from
              the [Huggingface model hub](https://huggingface.co/dbmdz).
* 30.12.2019: Public release of cased and uncased BERT models for Italian.
* 08.12.2019: If you consider using our model for the upcoming GermEval 2020 shared task,
              please read at least this [blog post](https://medium.com/@emilymenonbender/is-there-research-that-shouldnt-be-done-is-there-research-that-shouldn-t-be-encouraged-b1bf7d321bb6)
              by Emily Bender on ethical issues!
* 10.10.2019: Public release
* 24.09.2019: Initial version

# German BERT

## Stats

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

## Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                            | Downloads
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `bert-base-german-dbmdz-cased`   | [`config.json`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-cased-config.json) • [`pytorch_model.bin`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-cased-pytorch_model.bin) • [`vocab.txt`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-cased-vocab.txt)
| `bert-base-german-dbmdz-uncased` | [`config.json`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-uncased-config.json) • [`pytorch_model.bin`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-uncased-pytorch_model.bin) • [`vocab.txt`](https://s3.amazonaws.com/models.huggingface.co/bert/bert-base-german-dbmdz-uncased-vocab.txt)

## Usage

With Transformers >= 2.3 our German BERT models can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/bert-base-german-cased")
model = AutoModel.from_pretrained("dbmdz/bert-base-german-cased")
```

## Results

For results on downstream tasks like NER or PoS tagging, please refer to
[this repository](https://github.com/stefan-it/fine-tuned-berts-seq).

# Italian BERT

The source data for the Italian BERT model consists of a recent Wikipedia dump and
various texts from the [OPUS corpora](http://opus.nlpl.eu/) collection. The final
training corpus has a size of 13GB and 2,050,057,573 tokens.

For sentence splitting, we use NLTK (faster compared to spacy).
Our cased and uncased models are training with an initial sequence length of 512
subwords for ~2-3M steps.

For the XXL Italian models, we use the same training data from OPUS and extend
it with data from the Italian part of the [OSCAR corpus](https://traces1.inria.fr/oscar/).
Thus, the final training corpus has a size of 81GB and 13,138,379,147 tokens.

Note: Unfortunately, a wrong vocab size was used when training the XXL models.
This explains the mismatch of the "real" vocab size of 31102, compared to the
vocab size specified in `config.json`. However, the model is working and all
evaluations were done under those circumstances.
See [this issue](https://github.com/dbmdz/berts/issues/7) for more information.

## Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                                   | Downloads
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `dbmdz/bert-base-italian-cased`         | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-cased/config.json)       • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-cased/pytorch_model.bin)       • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-cased/vocab.txt)
| `dbmdz/bert-base-italian-uncased`       | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-uncased/config.json)     • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-uncased/pytorch_model.bin)     • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-uncased/vocab.txt)
| `dbmdz/bert-base-italian-xxl-cased`     | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-cased/config.json)   • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-cased/pytorch_model.bin)   • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-cased/vocab.txt)
| `dbmdz/bert-base-italian-xxl-uncased`   | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-uncased/config.json) • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-uncased/pytorch_model.bin) • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-uncased/vocab.txt)

## Results

For results on downstream tasks like NER or PoS tagging, please refer to
[this repository](https://github.com/stefan-it/fine-tuned-berts-seq).

## Usage

With Transformers >= 2.3 our Italian BERT models can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/bert-base-italian-cased")
model = AutoModel.from_pretrained("dbmdz/bert-base-italian-cased")
```

To load the (recommended) Italian XXL BERT models, just use:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/bert-base-italian-xxl-cased")
model = AutoModel.from_pretrained("dbmdz/bert-base-italian-xxl-cased")
```

# German Europeana BERT

We use the open source [Europeana newspapers](http://www.europeana-newspapers.eu/)
that were provided by *The European Library*. The final
training corpus has a size of 51GB and consists of 8,035,986,369 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/europeana-bert).

## Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                                      | Downloads
| ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------
| `dbmdz/bert-base-german-europeana-cased`   | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-german-europeana-cased/config.json)   • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-german-europeana-cased/pytorch_model.bin)   • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-german-europeana-cased/vocab.txt)
| `dbmdz/bert-base-german-europeana-uncased` | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-german-europeana-uncased/config.json) • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-german-europeana-uncased/pytorch_model.bin) • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-german-europeana-uncased/vocab.txt)

## Results

For results on Historic NER, please refer to [this repository](https://github.com/stefan-it/europeana-bert).

## Usage

With Transformers >= 2.3 our German Europeana BERT models can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/bert-base-german-europeana-cased")
model = AutoModel.from_pretrained("dbmdz/bert-base-german-europeana-cased")
```

The German Europeana BERT uncased model can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/bert-base-german-europeana-uncased")
model = AutoModel.from_pretrained("dbmdz/bert-base-german-europeana-uncased")
```

# Turkish BERT: BERTurk and DistilBERTurk

BERTurk is community-driven cased BERT model for Turkish.

Some datasets used for pretraining and evaluation are contributed from the
awesome Turkish NLP community, as well as the decision for the model name: BERTurk.

The final training corpus has a size of 35GB and 44,04,976,662 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/turkish-bert).

Additionally, we trained a distilled version of BERTurk: *DistilBERTurk*, that
uses knowledge-distillation from BERTurk (teacher model). More information on
distillation can be found in the excellent ["DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter"](https://arxiv.org/abs/1910.01108)
paper by Sanh et al. (2019).

## Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                                 | Downloads
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `dbmdz/bert-base-turkish-cased`       | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-turkish-cased/config.json) • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-turkish-cased/pytorch_model.bin) • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-turkish-cased/vocab.txt)
| `dbmdz/distilbert-base-turkish-cased` | [`config.json`](https://cdn.huggingface.co/dbmdz/distilbert-base-turkish-cased/config.json) • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/distilbert-base-turkish-cased/pytorch_model.bin) • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/distilbert-base-turkish-cased/vocab.txt)

## Results

For results on PoS tagging or NER tasks, please refer to [this repository](https://github.com/stefan-it/turkish-bert).

## Usage

With Transformers >= 2.3 our BERTurk cased model can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/bert-base-turkish-cased")
model = AutoModel.from_pretrained("dbmdz/bert-base-turkish-cased")
```

The DistilBERTurk model can be loaded with:

```python
from transformers import AutoModel, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/distilbert-base-turkish-cased")
model = AutoModel.from_pretrained("dbmdz/distilbert-base-turkish-cased")
```

# Huggingface model hub

All models are available on the [Huggingface model hub](https://huggingface.co/dbmdz).

# Contact (Bugs, Feedback, Contribution and more)

For questions about our BERT models just open an issue
[here](https://github.com/dbmdz/berts/issues/new) 🤗

# Acknowledgments

Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC).
Thanks for providing access to the TFRC ❤️

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download both cased and uncased models from their S3 storage 🤗
