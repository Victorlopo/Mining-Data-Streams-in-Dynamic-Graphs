# Triangle Counting in Dynamic Graphs with TRIÈST

## Context
In the computational landscape, the analysis of data streams within dynamic graphs, such as those representing social networks, has emerged as a critical necessity. This is particularly evident in tasks like estimating the number of triangles in graphs, which serves as a key indicator of community structure and network cohesion. As these graphs evolve over time through a continuous stream of edge insertions and deletions, traditional static analysis methods fall short, necessitating efficient, real-time algorithms capable of adapting to changes. In graph theory, a triangle is defined as a simple cycle that consists of three vertices (or nodes) and three edges, forming a closed loop. For example, consider a graph with nodes labeled A, B, and C. If there are edges connecting A to B, B to C, and C to A, then these three nodes, along with the edges between them, form a triangle. This configuration highlights the essential unit of connectivity within the graph, indicating strong mutual relationships or a tightly knit community structure.

## Reservoir Sampling
The Reservoir Sampling algorithm is a technique used for sampling a dataset (or "data stream") of unknown size, particularly when the set is too large to fit in memory. This technique is especially useful in the context of "mining data streams", where data flows continuously and it is not practical (or possible) to store the entire stream for later analysis. The goal of Reservoir Sampling is to select a random sample of `k` elements from a stream of size `n`, where `n` is unknown or potentially infinite. The resulting sample should be representative of the entire stream, meaning each element in the stream has the same probability of being included in the sample.

## Algorithms
In this project, I have implemented two prominent algorithms from the paper:
[1] L. De Stefani, A. Epasto, M. Riondato, and E. Upfal, "TRIÈST: Counting Local and Global Triangles in Fully-Dynamic Streams with Fixed Memory Size," KDD'16.

### TRIEST-BASE
TRIEST-BASE focuses on estimating the number of triangles in dynamic graphs represented by a stream of edge insertions. It uses Reservoir Sampling techniques to maintain a representative subset of edges within a predefined memory limit. As each edge is processed, TRIEST-BASE probabilistically updates triangle counters based on the potential triangles formed by the newly added edge and the existing edges in the reservoir. This approach allows for an accurate estimation of the total number of triangles, optimizing memory use and facilitating real-time analysis of large data streams.

### TRIEST-IMPROVED
TRIEST-IMPROVED extends and enhances the TRIEST-BASE algorithm by introducing optimizations that reduce the variance of estimations and increase memory use efficiency. TRIEST-IMPROVED implements a more sophisticated sampling technique that dynamically adjusts the inclusion probability of new edges, based on the current size of the data stream and the memory limit. Additionally, this algorithm applies corrections to the triangle counters to minimize estimation error. Thanks to these improvements, TRIEST-IMPROVED can provide more precise and stable estimates of the number of triangles in dynamic graphs, even under severe memory constraints.

## Dataset
For the evaluation of our implementation of the TRIÈST algorithms (TRIÈST-BASE and TRIÈST-IMPROVED), we utilized a publicly available graph dataset derived from the arXiv's collaboration network [2]. This dataset encapsulates scientific collaborations among authors of papers submitted to the General Relativity and Quantum Cosmology category on arXiv, covering submissions from January 1993 to April 2003. The graph contains a total of 48,260 triangles, highlighting the dense network of collaborations within the specified period.

## Results
My analysis across a spectrum of sample sizes from 2,000 to 14,000 revealed consistent improvement in the accuracy of triangle count estimations as the sample size increased. For the TRIÈST-BASE algorithm, a sample size of 14,000 estimated the triangle count at 48,460 with a minimal error margin of 0.41%. Similarly, the TRIÈST-IMPROVED algorithm estimated the triangle count at 48,482 for the same sample size, resulting in a slightly higher error margin of 0.46%. These results demonstrate the critical role of sample size in enhancing estimation accuracy and highlight the performance distinctions between the two algorithms, with TRIÈST-IMPROVED showing enhanced stability and consistency.


## References
- [1] L. De Stefani, A. Epasto, M. Riondato, and E. Upfal, "TRIÈST: Counting Local and Global Triangles in Fully-Dynamic Streams with Fixed Memory Size," KDD'16.
- [2] https://snap.stanford.edu/data/ca-GrQc.html
