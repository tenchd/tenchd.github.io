---
title: Help Us Find Large, Dense Graph Datasets
layout: page
hide: true
---

## What we're looking for:
Real-world graph data sets with _at least tens of million nodes_ (more is better) and at least _100 thousand unique edges per node_ (more is better). By *unique* we mean that multi-edges don't count: if there are 10 copies of an edge between nodes u and v in your dataset, we'd count that as a single edge.

(Graphs that aren't *quite* this large or dense, if you have them, would still be interesting though not ideal.)

The graph data sets can represent anything, we're not picky.  Graphs which change over time (e.g., edges may be inserted or deleted) are especially useful for our purposes.

If you have the datasets we're looking for, please [contact me via email](dtench@pm.me) or using the web form at the bottom of this page.

## Why we want these datasets:

I'm leading a team of researchers in building space-efficient tools for processing dynamic graphs (graphs which change over time).  These tools use linear sketching, which allows us to (sometimes approximately) compute properties of graphs using space much smaller than is required to store the graph losslessly.  The space requirements of these algorithms scale with the number of nodes in the graph, *but not the number of edges*.

This is especially useful when processing *dense* graphs (graphs that have a lot of edges per node).  Most existing graph processing systems assume that large graphs are always sparse, and optimize for computation on sparse graphs.

We believe that tools designed for computing properties of large, dense, dynamic graphs are useful, and are actively looking for real-world graph datasets which are large and dense.



Existing work
--------------

We built [GraphZeppelin](/deeplinks/graphzeppelin.pdf), a graph stream processing system which uses linear sketching techniques to space-efficiently find connected components of dynamic graphs.  The paper is in submission to [SIGMOD 2022](https://2022.sigmod.org/) and you can check out our [code here](https://github.com/GraphStreamingProject/GraphStreamingCC).  GraphZeppelin showcases several other advantages of linear sketching techniques: it is highly parallel, scales well to external memory and can be distributed efficiently on a cluster for even better scaling.

GraphZeppelin uses asymptotically less space to process dense graphs than the current state-of-the-art systems for graph stream processing.  Its space efficiency advantages become apparent even for relatively small dense graphs (hundreds of thousands of nodes).

<img src="public_html/images/size.png" alt="test" width="1000"/>

## Got Graph Datasets?

<p>You can use this form to contact me about graph datasets.</p>

<form method="post" action="https://formspree.io/dtench@pm.me">
  <div class="row">
    <div class="6u 12u$(mobile)"><input type="text" name="name" placeholder="Name" /></div>
    <div class="6u$ 12u$(mobile)"><input type="text" name="email" placeholder="Email" /></div>
    <div class="12u$">
      <textarea name="message" placeholder="Message"></textarea>
    </div>
    <div class="12u$">
      <input type="submit" value="Send Message" />
    </div>
  </div>
</form>

