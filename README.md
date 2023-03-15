# DL systems || Homework 3

This is assignment is a part of [DL-systems course presented by CMU](https://dlsyscourse.org/). 

## What you will find in this repo


This HW is the third step for building our own DL library. In this HW will finally replace the NUMPY with our own CPP AND CUDA backends. 


Navigating this repo you will find an implementation for the following: 
1.  Functions that do not reallocate any memory by using manipulation on the strided matrice' parmeterss as (shape, strides, and offset):
    * reshape
    * permute
    * broadcast_to
    * __getitem__

2. Both CPU and CUDA Backend will have implementation for the following:
    * **Compact**
    * **SetItem** 
    * **ReduceMax and ReduceSum**
    * **Matrix Multiplication**
        - matmul
        - matmultiled
        - ALignedDot
    * EwiseMul(), ScalarMul()
    * EwiseDiv(), ScalarDiv()
    * ScalarPower()
    * EwiseMaximum(), ScalarMaximum()
    * EwiseEq(), ScalarEq()
    * EwiseGe(), ScalarGe()
    * EwiseLog()
    * EwiseExp()
    * EwiseTanh()


## Tests
To run tests you can use the following commands in the repo directory: 
ps if you are running in jupyter add `!`  before the following commands

- `python3 -m pytest -v -k "(permute or reshape or broadcast or getitem) and cpu and not compact"`
- CPU  functions Testing
    - `python3 -m pytest -s -v -k "(compact or setitem) and cpu"`
    - `python3 -m pytest -v -k "(ewise_fn or ewise_max or log or exp or tanh or (scalar and not setitem)) and cpu"`
    - `python3 -m pytest -v -k "reduce and cpu"`
    - `python3 -m pytest -v -k "matmul and cpu"`

- CUDA functions Testing
    - `python3 -m pytest -v -k "(compact or setitem) and cuda"`
    - `python3 -m pytest -v -k "(ewise_fn or ewise_max or log or exp or tanh or (scalar and not setitem)) and cuda"`
    - `python3 -m pytest -v -k "reduce and cuda"`
    - `!python3 -m pytest -v -k "matmul and cuda"`



---
## my AHA moments
1. **Strided Matrices:**

    In basic programming classes when we got to deal with 2D matrices we hear about column major matrices representation such as `matlab`      and row major representations such as in `C++`. Choosing which representation can have great performance on your program. You can check [this stack to learn more about it](https://scicomp.stackexchange.com/questions/4796/row-major-versus-column-major-layout-of-matrices). 

    But in DL, we do have higher dimensional tensors than 2D, so we do use more general representation, which is stridded matrices. Which stores the data in a contiguous array, and then u try to use some parameters (*shape, stride, offset*) to represent ur matrix in the way u like the most. 

    One advanatage for the strided maatrix is u can do some operations as reshaping, or broadcasting without even reallocating the matrix again!!. You can see here Prof TQ doing a full [tutorial on the strided matrices](https://www.youtube.com/watch?v=XdhUZRXA7fg). 
    
--- 

## Want to see more of the assignments ? 
### Click here to see the rest of the assignments and AHA moments

1. [HW1](https://github.com/ahmedtarek1325/dlsys_hw1)
2. [HW2](https://github.com/ahmedtarek1325/dlsys_hw2)
3. [HW3](https://github.com/ahmedtarek1325/dlsys_hw3)
4. [HW4](https://github.com/ahmedtarek1325/dlsys_hw4)

## Refrences: 
1. [Lectures [11-13] to understand the theory](https://dlsyscourse.org/lectures/)
2. [Row vs column major matrix representation](https://scicomp.stackexchange.com/questions/4796/row-major-versus-column-major-layout-of-matrices). 


