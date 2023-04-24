# Metarank ESCI playground

This repo is a complementary set of configs and links for the 
[Haystack US 23 talk on Hybrid Search](https://metarank.github.io/haystack-us23)

## Datasets

We use a combination of original [Amazon ESCI](https://github.com/amazon-science/esci-data) and
community [ESCI-S](https://github.com/shuttie/esci-s) datasets.

The ESCI+ESCI-S small dataset in the Metarank format can be downloaded here: 
[s3://esci-s/metarank-esci-small.jsonl.zst](https://esci-s.s3.amazonaws.com/metarank-esci-small.jsonl.zst)

## Models

See [huggingface.co/metarank](https://huggingface.co/metarank) repo with all models used in the final configuration:
* [metarank/all-MiniLM-L6-v2](https://huggingface.co/metarank/all-MiniLM-L6-v2)
* [metarank/all-mpnet-base-v2](https://huggingface.co/metarank/all-mpnet-base-v2)
* [metarank/esci-MiniLM-L6-v2](https://huggingface.co/metarank/esci-MiniLM-L6-v2)
* [metarank/ce-msmarco-MiniLM-L6-v2](https://huggingface.co/metarank/ce-msmarco-MiniLM-L6-v2)
* [metarank/ce-esci-MiniLM-L6-v2](https://huggingface.co/metarank/ce-esci-MiniLM-L6-v2)

You can always translate your own model to ONNX, see translation scripts on each model repos:
https://huggingface.co/metarank/all-MiniLM-L6-v2/blob/main/convert.py

## Config file

The Metarank config file is stored in this repo: [config.yml](https://github.com/metarank/esci-playground/blob/master/config.yml)

To speed-up all the experiments, we used precomputed embeddings for all models. Otherwise bootstrapping over CE models takes ages.

## BM25

All the BM25 features mention term-frequencies file. You can create it with the following command:
```bash
java -jar metarank.jar termfreq --data events.jsonl --out tf-title.json --fields title
```

Term-freq files should be build per field to match the behavior of Lucene.

## License

Licensed under the Apache 2.0.