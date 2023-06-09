# Eigenvector Aggregate

## Description
Eigenvector aggregate is a method to approximate the eigenvector derivatives of the eigenvalue problem used in topology optimization. The method is described in the following paper "Topology Optimization using an Eigenvector Aggregate" by Bao Li, Yicong Fu and Graeme J. Kennedy. The paper is available on (To be added).

## Contents
- `simple_example.py` contains the code for the simple example in paper section 3.1.
- `demo.py` contains the code for a demo to show exact eigenvector derivatives and approximate eigenvector derivatives described in paper sections 4 and 5, respectively.
- `tube_opt.py` is the main file that contains the code for the 2D tube optimization example. There are five problems in the tube example as follows:
  - `plot_E` is used to plot the E matrix shown in Figure 2 in the paper.
  - `accuracy_analysis` is used to plot the accuracy of the approximate eigenvector derivatives shown in section 8.1.1 in the paper.
  - `optimization_eigenvalue` runs the maximization of the fundamental frequency problem with a volume constraint.
  - `optimization_displacement` runs the maximization of the fundamental frequency problem with a volume constraint and displacement constraint.
  - `optimization_stress` runs the maximization of the fundamental frequency problem with a volume constraint and stress constraint.
- `topo_opt.py` is the main file for the topology optimization for the beam and square plate. The function `parse_cmd_args` takes the following arguments as input:
  - For the problem definition parameters:
    - `domain` is the domain of the problem, which can be `beam` or `square`.
    - `objf` is the objective function, which is set to be `frequency` by default.
    - `confs` is the constraint function, which is set to `volume_ub` by default.
    - `vol-frac-ub` is the upper bound of the volume fraction constraint.
    - `stress-ub` is the upper bound of the stress constraint.
    - `dis-ub` is the upper bound of the displacement constraint.
  - For the topology optimization parameters:
    - `nx` is the number of elements along the x direction.
    - `filer` is the density filter, which can be `spectral` or `helmholtz`, with corresponding filter radius `r0` which is set to be `2.1` (2.1 times the element size) by default.
    - `ptype-K` is the material penalization method for the stiffness matrix K, which can be `SIMP` or `RAMP`, with corresponding penalization parameters `p` and `q`. It is set to `SIMP` with `p=3` by default.
    - `ptype-M` is the material penalization method for the mass matrix M, which can be `MSIMP`, `RAMP`, or `LINEAR`.
    - `optimizer` is the optimizer used to solve the optimization problem, which can be `pmma` or `tr`, where `pmma` is the MMA method and `tr` is the trust region method.
    - `maxit` is the maximum number of iterations.
- `output` folder used to save the output figures and log files.
- `other` folder contains the code for generating the figures in the paper, helper functions, and bash scripts used to run the code on Georgia Tech's PACE cluster.
- `run.sh` is the bash script used to run the code.

## Usage
The code is written in Python 3. To run the code, you need to install the following packages:
- [ParOpt](https://github.com/smdogroup/paropt) (version [2.0.2](https://github.com/smdogroup/paropt/tree/v2.0.2) is recommended) is a parallel gradient-based optimizer that integrates the MMA method and the trust region method. The dependencies of ParOpt are listed [MPI](https://www.open-mpi.org/), [BLAS](http://www.netlib.org/blas/), [LAPACK](http://www.netlib.org/lapack/), [mpi4py](https://mpi4py.readthedocs.io/en/stable/), [Cython](https://cython.org/), [numpy](https://numpy.org/), [scipy](https://www.scipy.org/)
- [scienceplots](https://github.com/garrettj403/SciencePlots), [matplotlib](https://matplotlib.org/), [numpy](https://numpy.org/), [scipy](https://www.scipy.org/), [mpmath](http://mpmath.org/), [icecream](https://github.com/gruns/icecream)

To run the code, simply run the bash script `run.sh`:
```
./run.sh
```
The code will run the simple_example, demo, tube, beam, and square plate examples. The user can also run the code with different parameters by modifying the bash script `run.sh`. The output figures and log files will be saved in the `output` folder.

## Citation
If you find this code useful in your research, please consider citing:
```
To be added
```

## Contact
If you have any questions, please contact [Bao Li](libao@gatech.edu), [Yicong Fu](aaronfu@gatech.edu), or [Graeme J. Kennedy](graeme.kennedy@aerospace.gatech.edu).

