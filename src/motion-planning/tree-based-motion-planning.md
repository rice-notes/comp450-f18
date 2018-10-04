# Tree Based Motion Planning

Idea: Build a tree of valid configuration spaces

Motivation:  
* allows us to perform multiple search queries
* provides us discrete configurations to travel between 

Basic Idea of all Tree-Based planners:  
1. Initialize a Tree
2. while the goal state isn't in the tree
    1. get a configuration from the tree
    2. branch off from that configuration

Each specific tree based planner decides how the tree grows, how to sample the
configuration space, etc...

## Rapidly-exploring Random Tree (RRT)

RRT depends on a distance metric $$\rho$$ in the configuration space and it's
effectiveness is highly dependent on this metric.

RRT:

1. Randomly sample point $$q \in \mathcal{C}$$ from configuration space
2. Choose closest point $$p \in T$$
3. Grow tree from $$p$$ in direction of $$q$$ **up to** $$\epsilon$$ (max step
   size)


### Probablisitic Completeness:

As $$n$$ = number of iterations tends to $$\infty$$, the probability that RRT 
completes (finds goal configuration) tends to 1.

## Expansive-Space Tree

Relies on a probablity distribution to determine where to grow the tree from.
Associates a weight $$w(q)$$ with each node, indicating the probability we 
should grow from node $$q$$.  

### Choosing Node Weight

You want to sample from nodes that are in less-well explored areas of the
configuration space, i.e. have less neighbors around them.  Since it can be
expensive to count neighbors in a given neighborhood around every point, these
weights are sometimes approximated by the inverse of the degree of the node.

* $$w(q) = \frac{1}{1 + \text{deg}(q)}$$
* $$w(q) = \frac{1}{1 + \text{ neighbors nearby } q}$$

### Comparison to RRT

Less dependent on the chosen metric than RRT, but often struggles to grow the
tree to unexplored areas of the configuration space as the algorithm continues.

## Bi-directional Trees

Grow from $$q_{init}$$ and $$q_{goal}$$ and attempt to connect the trees at
some point.  Increased efficiency, and growth typically slows down later than 
with a single tree.

Implementation details consider how we attempt to connect trees  

* expansion to a random point
* directly connect two trees

## Sampling-based Roadmap of Trees

Somewhat of a combination of PRM and Tree-based algorithms, attempts to grow
$$n$$ trees from randomly sampled configurations and then continues by
connecting them.
