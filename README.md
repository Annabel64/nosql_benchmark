# Impact of the number of shards on the performance of a MongoDB cluster

This repo a simple test to see how the number of shards affects the performance of a MongoDB cluster.

# TL;DR
![Benchmark results](/results/images/benchmark_query_for_each_shard_white.svg)
![Benchmark results](/results/images/benchmark_sharding_for_each_query_white.png)

# Setup
We have a set of 8 VMs.
Each VM has 4 cores and 16GB of RAM.

We have 1 config server and 1 mongos.
We have a potential of 6 shards (1 shard per VM) and we will test the performance of the cluster by adding shards to it.

# Data
The data we are using can be found [here](https://relational.fit.cvut.cz/dataset/Grants).

# Data transformation
We are using the [following script](/todo) to denormalize the data and insert it into the cluster.

# Shard key
After some testing, we found that the best shard key is the `investigator.email_id` field.

# Results
## Computing method
You can find the notebook we used to compute the metrics [here](/benchmark_shards.ipynb).
Each of our 8 queries is run 10 times. The min and max values are excluded and the average is then computed and stored. 

## Vizualization
You can find the notebook we used to vizualize the metrics [here](/benchmark_viz.ipynb).