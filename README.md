![DIT](./img/Logo.png)

# Polars : a blazingly fast dataframe library
Two languages have made a big impression on the lasts stackoverflow's most loved survey: the rapidly rising **Elixir** and the dominating **Rust**. As the first one is developping as a python-like functionnal language for resilient and highly concurrent systems, the second is getting a lot of traction in type safe, fast and reliable systems.

When the functionnal pythonic Elixir got it's own NumPy (multi-dimensional arrays), it chose the shiny rust based framework for it's backend : Polars.
But don't worry, they have a [Python package](https://pypi.org/project/polars/) for Pandas users.


# Why
To follow the trend of rewriting [everything](https://zaiste.net/posts/shell-commands-rust/) in Rust but also to adress the shortcomings of Pandas, a project born in 2011 that didn't envision the scale of the data needs in 2023 by the words of it's own [author](https://wesmckinney.com/blog/apache-arrow-pandas-internals/). So just as Pandas, it offers tools to read and write data in various formats with it's fast parsers, including a highly performant [Apache Parquet](https://parquet.apache.org/) reader. Most of it's difference with Pandas are what makes its strength.


## Apache Arrow
Apache  is a columnar in-memory format designed for efficiency in analytics operations on our modern computation units (both CPUs and GPUs). It also allow zero-copy data-access to manipulate large datasets at maximum speed.
![Arrow Memory Buffer](./img/arrow_memory.png)

Columnar databases store multiples row's column values together for a more efficient data access even on large sources. It also allows to load only the relevant data in memory.

##  Lazy and Eager API
Polars offer two types of API, an Eager one that evaluate the code as soon as it's run (Pandas style) and a Lazy that generates a query plan that will be optimized before running.

The difference ? You start an eager query with `read_*` and a lazy one with `scan_*`. The `*` can be replaced with any valid file type and in both case, the query end with a `.collect()` to capture the result and save it in a variable. Without collection, only the query plan will be displayed.

## Query optimization and parallelization
Lazy query evaluation will looks for way to run the query the fastest way and reduce the memory usage. Some of its strategies to reach this goal are :
- the execution of some operations at scan level : aggregate and projection
- simplification of expressions
- parallel execution at the physical plan
The last strategy on the parallelization is actually a crucial step to leverage the true potential of our multi-core processing units. The data is split into chunk and processed in multiple threads allowing a larger amount of data to be processed in the same time. Both Pandas and Python lack the ability to multithread as easily.

## Memory manaagement
Polars also allow to load larger data that doesn't fir into memory with it's streaming capabilities. A simple `collect(streaming=True)` is enough to run the slower but still fast streaming query.

# Installation

# Theory

# Practical example

# alternatives

# Data analysis use cases

# Conclusion

# Sources
