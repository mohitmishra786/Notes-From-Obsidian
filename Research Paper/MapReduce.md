- It is associated implementation for processing and generating large datasets.
- Users can specify the `map` function that processes `key/value` pairs and outputs the intermediate key/value pairs.
- And finally `reduce` function can merge all the intermediate values associated with the same key.
- Programs written are already using the parallelism and executed on a large cluster of commodity machines.
- A typical `MapReduce` operation happens on several terabytes of data and thousands of machines.

# **Introduction**
Google already have implemented many special-purpose computations that process large amount of raw data. Most of these computation are usually straightforward. However the input data is usually large and computations have to be distributed among hundreds of machines.

Due to this, we see some of the issues. The issue such as:
- How to parallelize the computations?
- Distribution of the data?
- Handling failures

Due to this complexity, Google came up with the abstraction which will simply let us do the simple computation without letting us know about the complex mechanism of how it is happening.

This abstraction is inspired by the map and reduce primitives that are present in LISP and many other functional languages.

