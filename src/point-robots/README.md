# Point Robot

* robot is a single point
* constrained environment
* you know where the obstacles are

## PRM

* sampling based algorithms
* drop random nodes / points onto our environment
* for each node, check if it's in collision with an object
  * if it's in an obstacle, throw it away
  * else, connect nodes to their neighbors which are accessible via
    a free ball around a node

### multiple queries

* after a given search / path plan, reuse the stored roadmap to help you with
  following queries

## Tree Planners

* one shot planners
* rather than store the whole graph, just generate a tree on the fly
