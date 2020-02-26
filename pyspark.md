## PySpark
PySpark is a Python-based wrapper on top of the Scala API

In a Python context, PySpark has a way to handle parallel processing
without the need for the threading or multiprocessing modules.
All of the complicated communication and synchronization
between threads, processes, and even different CPUs is handled by Spark.

Follow [this blog](https://sharing.luminis.eu/blog/how-to-install-pyspark-and-apache-spark-on-macos/) to install pyspark.
It is a bit annoying, pyspark only works with java8.

```
import pandas as pd
import pyspark
from pyspark import SparkContext
from TextCleaner import clean_text  ## customized module

sc = SparkContext()

df = pd.read_csv("data/Top30.csv")
docs = df.Description
```
`TextCleaner` is a customized module can be found in my [machine leaning notes](https://mlnlp.readthedocs.io/en/latest/Data-cleaning.html).<br>
There are ~70k doc in the file.

**Single core**
```
%%time
tokenss = []
for doc in tqdm(docs):
    tokenss.append(clean_text(doc))
```
Wall time: 2min 30s

**Parallel on 4 cores**
```
%%time
rdd = sc.parallelize(list(docs), 4)
tokenss = rdd.map(lambda x: clean_text(x))
out_docs = tokenss.collect()
```
Wall time: 1min 21s

Image if we need to process 10 millions documents, it takes about 5 hours.<br>
Parallel computation will largely save our time.
