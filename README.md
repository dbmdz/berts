# 🤗 + 📚 dbmdz BERT models

In this repository the MDZ Digital Library team (dbmdz) at the Bavarian State
Library open sources another BERT models 🎉

# Changelog

* 18.11.2021: Public release of multilingual and monolingual Historic Language Models.
* 24.09.2021: Public release of cased/uncased Turkish ELECTRA and ConvBERT models, trained on mC4 corpus.
* 17.08.2021: Public release of re-trained German GPT-2 model.
* 24.06.2021: Public release of Turkish ELECTRA model, trained on Turkish part of multilingual C4 corpus.
* 16.03.2021: Public release of ConvBERT model for Turkish: *ConvBERTurk*.
* 06.02.2021: Public release of German Europeana DistilBERT and ConvBERT models.
* 16.11.2020: Public release of French Europeana BERT and ELECTRA models.
* 15.11.2020: Public release of a German GPT-2 model.
* 11.11.2020: Public release of Ukrainian ELECTRA model.
* 02.11.2020: Public release of Italian XXL ELECTRA model.
* 26.10.2020: In collaboration with [Branden Chan](https://github.com/brandenchan) and [Timo Möller](https://github.com/Timoeller) from [deepset](https://deepset.ai/) we've trained larger language models for German. See our [paper](https://arxiv.org/abs/2010.10906) for more information!
* 12.05.2020: Public release of small and base ELECTRA models for Turkish
* 25.03.2020: Public release of *BERTurk* uncased model and *BERTurk* models with larger vocab size (128k, cased and uncased)
* 11.03.2020: Public release of cased distilled BERT model for Turkish: *DistilBERTurk*
* 17.02.2020: Public release of cased BERT model for Turkish: *BERTurk*
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

The Italian ELECTRA model was trained on the "XXL" corpus for 1M steps in total using a batch
size of 128. We pretty much following the ELECTRA training procedure as used for
[BERTurk](https://github.com/stefan-it/turkish-bert/tree/master/electra).

## Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                                                | Downloads
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `dbmdz/bert-base-italian-cased`                      | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-cased/config.json)                                               • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-cased/pytorch_model.bin)                      • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-cased/vocab.txt)
| `dbmdz/bert-base-italian-uncased`                    | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-uncased/config.json)                                             • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-uncased/pytorch_model.bin)                    • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-uncased/vocab.txt)
| `dbmdz/bert-base-italian-xxl-cased`                  | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-cased/config.json)                                           • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-cased/pytorch_model.bin)                  • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-cased/vocab.txt)
| `dbmdz/bert-base-italian-xxl-uncased`                | [`config.json`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-uncased/config.json)                                         • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-uncased/pytorch_model.bin)                • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/bert-base-italian-xxl-uncased/vocab.txt)
| `dbmdz/electra-base-italian-xxl-cased-discriminator` | [`config.json`](https://s3.amazonaws.com/models.huggingface.co/bert/dbmdz/electra-base-italian-xxl-cased-discriminator/config.json) • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/electra-base-italian-xxl-cased-discriminator/pytorch_model.bin) • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/electra-base-italian-xxl-cased-discriminator/vocab.txt)
| `dbmdz/electra-base-italian-xxl-cased-generator`     | [`config.json`](https://s3.amazonaws.com/models.huggingface.co/bert/dbmdz/electra-base-italian-xxl-cased-generator/config.json)     • [`pytorch_model.bin`](https://cdn.huggingface.co/dbmdz/electra-base-italian-xxl-cased-generator/pytorch_model.bin)     • [`vocab.txt`](https://cdn.huggingface.co/dbmdz/electra-base-italian-xxl-cased-generator/vocab.txt)

## Results

For results on downstream tasks like NER or PoS tagging, please refer to
[this repository](https://github.com/stefan-it/italian-bertelectra).

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

# German Europeana BERT, DistilBERT, ELECTRA and ConvBERT

We use the open source [Europeana newspapers](http://www.europeana-newspapers.eu/)
that were provided by *The European Library*. The final
training corpus has a size of 51GB and consists of 8,035,986,369 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/europeana-bert).

## Model weights

The following models are available from the Hugging Face model hub:

| Model                                                     | Downloads
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `dbmdz/bert-base-german-europeana-cased`                  | See [model hub](https://huggingface.co/dbmdz/bert-base-german-europeana-cased)
| `dbmdz/bert-base-german-europeana-uncased`                | See [model hub](https://huggingface.co/dbmdz/bert-base-german-europeana-uncased)
| `dbmdz/electra-base-german-europeana-cased-discriminator` | See [model hub](https://huggingface.co/dbmdz/electra-base-german-europeana-cased-discriminator)
| `dbmdz/electra-base-german-europeana-cased-generator`     | See [model hub](https://huggingface.co/dbmdz/electra-base-german-europeana-cased-generator)
| `dbmdz/convbert-base-german-europeana-cased`              | See [model hub](https://huggingface.co/dbmdz/convbert-base-german-europeana-cased)
| `dbmdz/distilbert-base-german-europeana-cased`            | See [model hub](https://huggingface.co/dbmdz/distilbert-base-german-europeana-cased)

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

# French Europeana BERT and ELECTRA

We use the open source [Europeana newspapers](http://www.europeana-newspapers.eu/)
that were provided by *The European Library*. The final
training corpus has a size of 63GB and consists of 11,052,528,456 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/europeana-bert).

## Model weights

| Model                                                     | Downloads
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------
| `dbmdz/bert-base-french-europeana-cased`                  | See [model hub](https://huggingface.co/dbmdz/bert-base-french-europeana-cased)
| `dbmdz/electra-base-french-europeana-cased-discriminator` | See [model hub](https://huggingface.co/dbmdz/electra-base-french-europeana-cased-discriminator)
| `dbmdz/electra-base-french-europeana-cased-generator`     | See [model hub](https://huggingface.co/dbmdz/electra-base-french-europeana-cased-generator)

## Usage

With Transformers >= 2.3 our French Europeana BERT and ELECTRA models can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

model_name = "dbmdz/bert-base-french-europeana-cased"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```

The ELECTRA (discriminator) model can be used with:

```python
from transformers import AutoModel, AutoTokenizer

model_name = "dbmdz/electra-base-french-europeana-cased-discriminator"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```

# Turkish BERT: BERTurk, DistilBERTurk, ELECTRA and ConvBERTurk

BERTurk are community-driven cased models for Turkish.

Some datasets used for pretraining and evaluation are contributed from the
awesome Turkish NLP community, as well as the decision for the BERT model name: BERTurk.

The final training corpus has a size of 35GB and 44,04,976,662 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/turkish-bert).

Additionally, we trained a distilled version of BERTurk: *DistilBERTurk*, that
uses knowledge-distillation from BERTurk (teacher model). More information on
distillation can be found in the excellent ["DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter"](https://arxiv.org/abs/1910.01108)
paper by Sanh et al. (2019).

Furthermore, we provide cased and uncased models trained with a larger vocab size (128k instead of 32k).

We also trained small and base ELECTRA models. ELECTRA is a new method for self-supervised language
representation learning. More details about ELECTRA can be found in the
[ICLR paper](https://openreview.net/forum?id=r1xMH1BtvB).

In addition to the BERT and ELECTRA based models, we also trained a ConvBERT model. The ConvBERT architecture is presented
in the ["ConvBERT: Improving BERT with Span-based Dynamic Convolution"](https://arxiv.org/abs/2008.02496) paper.

Evaluation of our models can be found in
[this repository](https://github.com/stefan-it/turkish-bert/electra).

We've also trained an ELECTRA (cased) model on the recently released Turkish part of the
[multiligual C4 (mC4) corpus](https://github.com/allenai/allennlp/discussions/5265) from the AI2 team.

After filtering documents with a broken encoding, the training corpus has a size of 242GB resulting
in 31,240,963,926 tokens.

## Model weights

All trained models can be used from the [DBMDZ](https://github.com/dbmdz) Hugging Face [model hub page](https://huggingface.co/dbmdz)
using their model name. The following models are available:

* *BERTurk* models with 32k vocabulary: `dbmdz/bert-base-turkish-cased` and `dbmdz/bert-base-turkish-uncased`
* *BERTurk* models with 128k vocabulary: `dbmdz/bert-base-turkish-128k-cased` and `dbmdz/bert-base-turkish-128k-uncased`
* *ELECTRA* small and base cased models (discriminator): `dbmdz/electra-small-turkish-cased-discriminator` and `dbmdz/electra-base-turkish-cased-discriminator`
* *ELECTRA* base cased and uncased models, trained on Turkish part of mC4 corpus (discriminator): `dbmdz/electra-small-turkish-mc4-cased-discriminator` and `dbmdz/electra-small-turkish-mc4-uncased-discriminator`
* *ConvBERTurk* model with 32k vocabulary: `dbmdz/convbert-base-turkish-cased`
* *ConvBERTurk* base cased and uncased models, trained on Turkish part of mC4 corpus: `dbmdz/convbert-base-turkish-mc4-cased` and `dbmdz/convbert-base-turkish-mc4-uncased`

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

Our ELECTRA models can be used with Transformers >= 2.8 and can be loaded with:

```python
from transformers import AutoModelWithLMHead, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/electra-base-turkish-cased-discriminator")
model = AutoModelWithLMHead.from_pretrained("dbmdz/electra-base-turkish-cased-discriminator")
```

and

```python
from transformers import AutoModelWithLMHead, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/electra-base-turkish-mc4-cased-discriminator")
model = AutoModelWithLMHead.from_pretrained("dbmdz/electra-base-turkish-mc4-cased-discriminator")
```

Our ConvBERT model can be used with Transformers >= 4.3 and can be loaded with:

```python
from transformers import AutoModelWithLMHead, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("dbmdz/convbert-base-turkish-cased")
model = AutoModelWithLMHead.from_pretrained("dbmdz/convbert-base-turkish-cased")
```

# Ukrainian ELECTRA

The source data for the Ukrainian ELECTRA model consists of two corpora:

* Recent Wikipedia dump
* Deduplicated Ukrainian part from the [OSCAR](https://oscar-corpus.com/) corpus

The final training corpus has a size of 30GB and consits of exactly 2,402,761,324 tokens.

Detailed information about the data and pretraining steps can be found in
[this repository](https://github.com/stefan-it/ukrainian-electra).

## Model weights

Currently only PyTorch-[Transformers](https://github.com/huggingface/transformers)
compatible weights are available. If you need access to TensorFlow checkpoints,
please raise an issue!

| Model                                              | Downloads
| -------------------------------------------------- | --------------------------------------------------------------------------------------------------
| `dbmdz/electra-base-ukrainian-cased-discriminator` | See [model hub](https://huggingface.co/dbmdz/electra-base-ukrainian-cased-discriminator/tree/main)
| `dbmdz/electra-base-ukrainian-cased-generator`     | See [model hub](https://huggingface.co/dbmdz/electra-base-ukrainian-cased-generator/tree/main)

## Results

For results on PoS tagging and NER downstream tasks, please refer to [this repository](https://github.com/stefan-it/ukrainian-electra).

## Usage

With Transformers >= 2.3 our Ukrainian ELECTRA model can be loaded like:

```python
from transformers import AutoModel, AutoTokenizer

model_name = "dbmdz/electra-base-ukrainian-cased-discriminator"

tokenizer = AutoTokenizer.from_pretrained(model_name)

model = AutoModelWithLMHead.from_pretrained(model_name)
```

# German GPT-2 model

The German GPT-2 model is meant to be an entry point for fine-tuning on other texts, and it is definitely not as good or "dangerous"
as the English GPT-3 model.

For training we use pretty much the same corpora as used for training the DBMDZ BERT model. We created a 50K byte-level BPE vocab based
on the training corpora.

The model was trained on one v3-8 TPU over the whole training corpus for 20 epochs.

Detailed information can be found in [this repository](https://github.com/stefan-it/german-gpt2).

**Note**: we have released a re-trained version of this model with better results!

## Model weights

In addition to the German GPT-2 model, we release a GPT-2 model, that was fine-tuned on a normalized version of Faust I and II.

| Model                                 | Downloads
| ------------------------------------- | --------------------
| `dbmdz/german-gpt2`                   | See [model hub](https://huggingface.co/dbmdz/german-gpt2/tree/main)
| `dbmdz/german-gpt2-faust` (old model) | See [model hub](https://huggingface.co/dbmdz/german-gpt2-faust/tree/main)

## Usage

With Transformers >= 2.3 our German GPT-2 model can be used for text generation:

```python
from transformers import pipeline

pipe = pipeline('text-generation', model="dbmdz/german-gpt2",
                 tokenizer="dbmdz/german-gpt2", config={'max_length':800})

text = pipe2("Der Sinn des Lebens ist es")[0]["generated_text"]

print(text)
```

# Historic Language Models

We release several BERT-based language models, incl. a multilingual Historic language models that includes
German, French, English, Finnish and Swedish, as well monolingual Historic language models for English,
Finnish and Swedish. The multilingual Historic language model was trained on 130GB of texts, extracted
from Europeana Newspapers and British Library corpus.

More details about our Historic Language Models can be found in
[this repository](https://github.com/stefan-it/clef-hipe/blob/main/hlms.md).

## Model weights

All models are available on the Hugging Face model hub:

| Model identifier                              | Model Hub link
| --------------------------------------------- | --------------------------------------------------------------------------
| `dbmdz/bert-base-historic-multilingual-cased` | [here](https://huggingface.co/dbmdz/bert-base-historic-multilingual-cased)
| `dbmdz/bert-base-historic-english-cased`      | [here](https://huggingface.co/dbmdz/bert-base-historic-english-cased)
| `dbmdz/bert-base-finnish-europeana-cased`     | [here](https://huggingface.co/dbmdz/bert-base-finnish-europeana-cased)
| `dbmdz/bert-base-swedish-europeana-cased`     | [here](https://huggingface.co/dbmdz/bert-base-swedish-europeana-cased)

# License

All models are licensed under [MIT](LICENSE).

# Huggingface model hub

All models are available on the [Huggingface model hub](https://huggingface.co/dbmdz).

# Papers

[Here you can find a list papers](papers.md), that used one of our trained models.
Feel free to open a PR/issue if you want your paper to be included!

# Contact (Bugs, Feedback, Contribution and more)

For questions about our BERT models just open an issue
[here](https://github.com/dbmdz/berts/issues/new) 🤗

# Acknowledgments

Research supported with Cloud TPUs from Google's TensorFlow Research Cloud (TFRC).
Thanks for providing access to the TFRC ❤️

Thanks to the generous support from the [Hugging Face](https://huggingface.co/) team,
it is possible to download both cased and uncased models from their S3 storage 🤗
