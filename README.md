**Fireball (c) Mike McNelis and Seyed Sabok-Sayr**

Created on 5/31/2020 by Mike McNelis\
Last edited on 5/24/2021 by Mike McNelis

## Summary

A multivariate regression model that optimizes the Eulerian grid volume in computational fluid dynamics. 

This repository trains a Lasso regression model to predict the maximum fireball radius in heavy-ion collision simulations. We incorporated these scripts in the hydrodynamic code [VAH](https://github.com/mjmcnelis/cpu_vah) to automatically configure the grid size for a given impact parameter and Bayesian model parameter set. The optimization scheme provides an additional 1.5x speedup for 2+1d simulations (the algorithm has not yet been tested for 3-D grids).

We worked on this project during the Erdos Institute Data Science Boot Camp in 2020. Our powerpoint presentation video explains how the machine learning algorithm works. We also refer the reader to Sec. 5.2 of the VAH paper

    M. McNelis, D. Bazow and U. Heinz, arXiv:2101.02827 (2021)

These techniques can also be generalized to any fluid dynamics code that uses an Eulerian grid.

## Data

The training and test data sets were generated by [VAH](https://github.com/mjmcnelis/cpu_vah) (see the VAH user manual Sec. 7 for more details). 

You can visualize the training data with the notebook `visualize_train_data.ipynb`.


## Regression model

The notebook `grid_regression.ipynb` fits a cubic polynomial Lasso regression model to the training data. You can also evaluate the auto-grid's success rate at enclosing the fireball sizes of a separate data set `launch/fixed_grid/fireball_sizes`.

Note: the default regression fit in the code [VAH](https://github.com/mjmcnelis/cpu_vah) excludes the standard deviation since it takes much more computational resources to produce this data set.


## Benchmarks

You can run the notebook `benchmark_runtimes.ipynb` to compare the simulation runtimes of the auto-grid and fixed-grid.



