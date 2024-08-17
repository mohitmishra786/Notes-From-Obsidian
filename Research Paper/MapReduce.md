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

They realized that most of the computations requires applying of the map function to each of the logical record in the input to derive the intermediate key/value pairs which will be passed through reduce function. Here reduce function will combine all the values shared by the same key.

# **Programming Model**
In simple words, computation takes the input key-value pairs and outputs the set of key-value pairs. User has to provide the two function: `map` and `reduce`.

`Map` written by the user will take the input pair and produces a set of intermediate key-value pairs. The `MapReduce` library groups together all intermediate key-value associated with the same intermediate key and passes them to the `Reduce` function.

The `Reduce` function, which is also written by user take the intermediate key (let's say K) and set of value for that key K.  It will merge together all the values for that key. Here, the intermediate values are provided to reduce function through `iterator`. This helps to handle list of values which are large to fit into memory.