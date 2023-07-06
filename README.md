# Tychos Python Library
The Tychos Python library provides convenient access to the Tychos API from
applications written in the Python language. The Tychos API allows you to query live, hosted vector datasets in your LLM application without needing to manage your own vector database / embedding pipelines.

You can find usage examples for the Tychos Python library in our [BioMed Demo App](https://demo.tychos.ai/) and the [/demo repo folder](https://github.com/tychos-lab/tychos).


## Installation

You don't need this source code unless you want to modify the package. If you just
want to use the package, just run:

```sh
pip install tychos
```

Install from source with:

```sh
python setup.py install
```
### Requirements

-   Python 2.7+ or Python 3.6+
-   Requests

## Usage

The library needs to be configured with your account's secret key which is
available via the [Tychos Website][api-keys]. Set `tychos.api_key` to its
value:

```python
import tychos
tychos.api_key = "sk_a9adji08..."
```

Query live vector datasets
```python
# initialize data store with API key
data_store = tychos.VectorDataStore(api_key="sk_a9adji08...")

# list available datasets
datasets = data_store.list()

# get name of the first dataset's id
print(datasets['data'][0]['name'])

# query the data store object
query_results = data_store.query(
    index_name = "pub-med-abstracts", # dataset
    query_string = "What is the latest research on molecular peptides", # search string
    limit = 5, # number of results
)

# print the metadata associated with the first result
print(query_results[0].payload)
```

## Command-line interface
This library additionally provides a tychos command-line utility to make it easy to interact with the API from your terminal. Run tychos-cli -h for usage.

```sh
tychos-cli query --api-key <YOUR-API-KEY> --name pub-med-abstracts --query-string <"Your query string"> --limit 5

```

## Datasets available
We currently support a handful of research datasets. If there's a particular dataset you'd like to incorporate into your LLM application, feel free to [reach out][twitter].

### Vector datasets
-   PubMed abstracts ([source][pub-med]): 33.2M documents, updated daily at 07:00 UTC.



## Feedback and support
If you'd like to provide feedback, run into issues, or need support using embeddings, feel free to [reach out][twitter] or raise issues via GitHub.


[api-keys]: https://tychos.ai/
[twitter]: https://twitter.com/etpuisfume
[pub-med]: https://pubmed.ncbi.nlm.nih.gov/download/
