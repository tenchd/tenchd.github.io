---
title: Graph Datasets
layout: page
hide: true
---


We are building space-efficient tools for processing dynamic graphs (graphs which change over time).  These tools use linear sketching, which allows us to (sometimes approximately) compute properties of graphs using space much smaller than is required to store the graph losslessly.  The space requirements of these algorithms scale with the number of nodes in the graph, *but not the number of edges*.

This is especially useful when processing *dense* graphs (graphs that have a lot of edges per node).  Most existing graph processing systems assume that large graphs are always sparse, and optimize for computation on sparse graphs.

We believe that tools designed for computing properties of large, dense, dynamic graphs are useful, and are actively looking for real-world graph datasets which are large and dense.

Specifically, we are looking for graphs with _at least tens of million nodes_ (more is better) and at least _100 thousand edges per node_ (more is better).

(Graphs that aren't *quite* this large or dense, if you have them, would still be interesting though not ideal.)



Existing work
--------------

We built [GraphZeppelin](/deeplinks/graphzeppelin.pdf), a graph stream processing system which uses linear sketching techniques to space-efficiently find connected components of dynamic graphs.  The paper will appear in SIGMOD 2022 and you can check out our [code here](https://github.com/GraphStreamingProject/GraphStreamingCC).  GraphZeppelin showcases several other advantages of linear sketching techniques: it is highly parallel, scales well to external memory and can be distributed efficiently on a cluster for even better scaling.
