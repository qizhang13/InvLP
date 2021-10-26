# InvLP

## Introduction
This repository contains a snapshot of the Julia code used to generate computational results presented in the following paper:
> Gupta, R., & Zhang, Q. (2020). Decomposition and Adaptive Sampling for Data-Driven Inverse Linear Optimization. arXiv preprint arXiv:2009.07961.

(To be updated to the correct <em>INFORMS Journal of Computing</em> reference)

A preprint of this paper is also available on [arXiv](https://arxiv.org/abs/2009.07961) and our research group's [website](https://qizh.cems.umn.edu/publications/journal-articles).

The code in this repository here requires the following software:
1. [Gurobi](https://www.gurobi.com/)
2. [BARON](https://minlp.com/baron-solver)
3. [Julia](https://julialang.org/) with the following packages:
    - JuMP
    - Gurobi
    - Linear Algebra
    - CSV
    - DataFrames
    - Printf
    - BARON

Details of the specific versions of these softwares used by us can be found in Section 6 of the paper.

Next, we provide the steps that one needs to follow to reproduce our results.

## Reproduction of Results

### Table 1
The code used to generate results presented in this table can be found [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/RandomSampling). The main program is in [RandomSampling.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy1_Customer_Preference_Learning/RandomSampling/RandomSampling.jl). One needs to edit the values of ``n`` (dimension of (FOP)) and ``J_scheme`` (J_scheme = 1 for the low J case, and J_scheme = 2 to set J as 250 irrespective of the level of noise in data) parameters in line 159 and line 160 of the main program, respectively to generate computational performance data for different n values considered in the paper. The main program will generate 10 random instances of training data for each of the three levels of noise in Table 1 and solve the resulting instances of (IOP) by both Algorithm 1 and Algorithm 2. The results for Algorithm 1 will be available in the Julia REPL, and more detailed results for Algorithm 2 will become available in a "Results" folder in the root directory that you specify on line 2 of the main program.

We provide the raw results files, that we used to obtain Table 1, [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/Results/RandomSampling). These can be considered as a sample of what the output from the main program will be.

### Figure 5
Data for the three subplots here can also be obtained by running [RandomSampling.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy1_Customer_Preference_Learning/RandomSampling/RandomSampling.jl). Specifically, solving the random training instances with Algorithm 2 will generate "ErrEvolSummary_dim_n_Noise_w.csv" files where, "n" stands for the dimension of (FOP) and "w" is such that &sigma; = 1/w. These ".csv" files will have the data on how the prediction error evolves as Algorithm 2 processes data for all 100 experiments sequentially. 

Sample output data for this figure can be found [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/Results/RandomSampling/Decomposition/High_fixed_J_250/Results1_dim_25_noise_10).

### Figure 6
The code for generating results in Figure 6 is available [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/AdaptiveSampling); main program is [InstanceGenerator.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy1_Customer_Preference_Learning/AdaptiveSampling/InstanceGenerator.jl). One needs to edit the values of ``n`` and ``S`` parameters on lines 11 and 12 of the main program, respectively to generate the different curves shown in Figure 6. Running the main program will store the prediction error evolution data in a "Results" folder in the root directory. 

Sample output data for this program is shown [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/Results/AdaptiveSampling). 

### Figure 7
Both the subplots in this figure can be generated by running the main file [InstanceGenerator.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy2_Production_Planning/InstanceGenerator.jl) in this [folder](https://github.com/ddolab/InvLP/tree/main/CaseStudy2_Production_Planning). Curves for different H values can be generated by editing the value of ``H`` parameter on line 80 of the main program. The main program will initialize a random instance of the production planning program and prepare a training dataset for the inverse optimization problem by both random and adaptive sampling methods. The final output of this program, consisting of prediction error evolution data for both the sampling approaches, will become available in a "Results" folder in the root directory. 

Our raw results files used to construct Figure 7 are available [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy2_Production_Planning/Results).

## Support
We welcome any feedback and suggestions. Please feel free to get in touch with us in case you face any difficulties executing the code files.
