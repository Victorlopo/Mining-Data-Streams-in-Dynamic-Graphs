# Triangle Counting in Dynamic Graphs with TRIÈST

## Context
In the computational landscape, the analysis of data streams within dynamic graphs, such as those representing social networks, has emerged as a critical necessity. This is particularly evident in tasks like estimating the number of triangles in graphs, which serves as a key indicator of community structure and network cohesion. As these graphs evolve over time through a continuous stream of edge insertions and deletions, traditional static analysis methods fall short, necessitating efficient, real-time algorithms capable of adapting to changes. In graph theory, a triangle is defined as a simple cycle that consists of three vertices (or nodes) and three edges, forming a closed loop. For example, consider a graph with nodes labeled A, B, and C. If there are edges connecting A to B, B to C, and C to A, then these three nodes, along with the edges between them, form a triangle. This configuration highlights the essential unit of connectivity within the graph, indicating strong mutual relationships or a tightly knit community structure.

## Reservoir Sampling
The Reservoir Sampling algorithm is a technique used for sampling a set of data (or "data stream") of unknown size, particularly when the set is too large to fit in memory. This technique is especially useful in the context of "mining data streams", where data flows continuously and it is impractical (or impossible) to store the entire stream for later analysis. The goal of Reservoir Sampling is to select a random sample of k elements from a stream of size n, where n is unknown or potentially infinite. The sample result must be representative of the entire stream, meaning each element of the stream has the same probability of being included in the sample.

## ALGORITHMS
In my project, I have implemented two outstanding algorithms from the paper:
- [1] L. De Stefani, A. Epasto, M. Riondato, and E. Upfal, "TRIÈST: Counting Local and Global Triangles in Fully-Dynamic Streams with Fixed Memory Size," KDD'16.

### TRIEST-BASE
The TRIEST-BASE algorithm estimates the number of triangles in dynamic graphs represented by a stream of edge insertions, using Reservoir Sampling techniques to maintain a representative subset of edges within a predefined memory limit.

### TRIEST-IMPROVED
TRIEST-IMPROVED extends TRIEST-BASE with optimizations that reduce the variance of the estimations and increase efficiency in memory use, providing more accurate and stable estimations of the number of triangles in dynamic graphs.

## Dataset
For the evaluation, I utilized a publicly available graph dataset derived from the arXiv's collaboration network [2]. This dataset encapsulates scientific collaborations among authors of papers submitted to the General Relativity and Quantum Cosmology category on arXiv, covering submissions from January 1993 to April 2003.

## RESULTS
My analysis with a known triangle count of 48,260 showed that both TRIÈST-BASE and TRIÈST-IMPROVED algorithms improve in accuracy as the sample size increases. Specifically, for a sample size of 14,000, TRIÈST-BASE estimated the triangle count as 48,460 (0.41% error), and TRIÈST-IMPROVED estimated it as 48,482 (0.46% error).

## References
- [1] L. De Stefani, A. Epasto, M. Riondato, and E. Upfal, "TRIÈST: Counting Local and Global Triangles in Fully-Dynamic Streams with Fixed Memory Size," KDD'16.
- [2] https://snap.stanford.edu/data/ca-GrQc.html
