# Physical Object Representations

## Primitive-Based

* build up an object by primities, such as lines, points, etc...
* convex shapes can be made using linear primitives (lines / halfspaces)

### Convexity

A set $$S$$ is convex if 

$$
x, y \in S \implies \lambda x + (1 - \lambda) y \in S
$$

### Algebraic Sets

A generalization of polygons / polyhedra, uses nonlinear primitives, e.g.
circles, elipses, hyperbola, parabola, etc...

### Semi-Algebraic Sets

A set defined by the finite intersection / union of several algebraic sets.

## Polygon Soups

3D surfaces created by joining together several polygons.

## Sensor-Based 

Sensors are error-prone, and do not have a global view of the world.  From
sensor data we'll capture depth data / pixel data, and construct a point cloud
from the data we've collected.  From there, we attempt to construct some sort
of discrete grid that identifies free cells and obstacle cells.

# Rigid Body Transformations

Defined by:
* each point in the body remains the same distance from each other
* points retain relative placement

A rigid body in 2D can be described simply the position / rotation w.r.t. 
a coordinate system.  Two types of transformations possible:
* rotation
* translation

## Rigid Body Rotations (2D)

We view this simply as a rotation matrix applied to a vector in
$$\mathbb{R}^2$$.  For example, a rotation of $$\theta$$ would be

$$
R(\theta) = 
\left[
    \begin{matrix} 
        cos(\theta) & -sin(\theta) \\
        sin(\theta) & cos(\theta) 
    \end{matrix}
\right]
$$

## General Rigid Body Motions (2D)

One way to represent rotations and transformation:
$$
\vec{u} = R(\theta)\vec{v} + \vec{t}
$$

Alternatively, we can use homogenous transformations for convenience like so:
$$
\left[
    \begin{matrix} 
        R(\theta) & \vec{t} \\
        0 & 1 
    \end{matrix}
\right]

\left[
    \begin{matrix} 
        \vec{v} \\
        1 
    \end{matrix}
\right]
$$

### Properties of Rotation Matrices

Columns are mutually orthonormal, i.e. 
$$
r_i^Tr_j = \begin{cases} 1 & i = j \\ 0 & i \ne j \end{cases}
$$

$$
R^TR = RR^T = I
$$
