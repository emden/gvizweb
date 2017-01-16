---
layout: page
title: FaqLarger
permalink: /FaqAnswers/FaqLarger/
---

*I'm trying to make a layout larger. How?*

There are various ways to increase the size of a layout. In doing this, one has to decide if the sizes of the nodes and text should be increased as well.

One approach is to adjust individual parameters such as fontsize, nodesep and ranksep. For example,

````C++
digraph G {
  graph [fontsize=24]
  edge [fontsize=24]
  node [fontsize=24]
  ranksep = 1.5
  nodesep = .25
  edge [style="setlinewidth(3)"]
  a -> b -> c
}
````

If you do this, make sure you are not fighting a conflicting graph size 
setting, like `size="6,6"`, which will then scale everything back down.

If you are using fdp or neato, increasing the edge len will tend to expand the layout.

````C++
graph G {
  edge [len=3]
  a -- { b c d }
}
````

For twopi and circo, there are other parameters such as `ranksep` which can be 
used. See the [graph attributes](../../_pages/doc/info/attrs.html).

You can also use the `ratio` attribute. If you set the `size` attribute to the 
desired drawing size, and then set `ratio=fill`, node positions are scaled 
separately in x and y until the drawing fills the specified size. Note that 
node sizes stay the same. If, instead, you set `ratio=expand`, the layout is 
uniformly scaled up in x and y until at least one dimension fits size.

If you specify the `size` attribute but end it with an exclamation mark (!), 
the final drawing will be scaled up uniformly in x and y until at least one 
dimension fits size. Note that everything is scaled up, including text and 
node sizes.

If you're using Postscript, you can just scale up the output by manually 
adding a command such as `2 2 scale` where the Postscript environment is set 
up. Make sure to adjust the BoundingBox too if your tools look at this header.


