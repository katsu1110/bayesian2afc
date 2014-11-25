# A Introductory Tutorial On Bayesian Modelling For Perception Researchers

**PLEASE RESPECT THAT THIS IS PRE-RELEASE CODE, ASSOCIATED WITH A PAPER THAT IS UNDER REVIEW. Citation details and a link to the paper will be provided if the manuscript is accepted for publication**

**This code is published under the MIT licence, see LICENSE.txt.**

## About this respository
This repository contains Matlab files that produced many of the figures in my paper:

- Vincent, B. T. (submitted) A introductory tutorial on Bayesian modelling for perception researchers. [LINK TO PUBLISHER'S SITE HERE]()

The paper and other Supplementary Material is available here: [PROVIDE URL HERE]()

## If... then...
* **You can't get the code to work**, then feel free to email and I'll try my best to respond to clarify things. 

* **You want to use the code for learning alongside the paper**, then feel free to clone or fork this repository, or download a .zip of the code.

* **If you find a bug**, then:
	* create an Issue, or...
	* create a pull request through GitHub with fixed code :)

* If you find the paper useful in your academic work, or adapt any of the code for your own work, please to share the love and cite the paper.

## Subdirectories

* `~` the root directory contains the main Matlab scripts and functions for producing the figures, see the section below.
* `figs/` output of the code saved in .fig and .pdf format.
* `funcs/` contains the majority of the Matlab functions and JAGS model files. You don't need to run any of these files as they are called by the main scripts in the root directory.
* `output/` data generated by the code is saved here.

## Reproducing the figures

* `generate_common_data.m` generates and saves a set of common data which can be used with all of the models. There is no need to run this as example data is already included in the files `commondata_model*.mat`.
* `model1runme.m` By changing the input variable `{'gridApprox', 'mcmcJAGS', 'mcmcCustom'}` this file will run the 3 inference steps using the different respective methods:
	*  `gridApprox` will conduct parameter estimation via grid approximation.
	*  `mcmcCustom` will conduct parameter estimation with an implementation of the Metropolis-Hastings sampling algorithm (see `mhAlgorithm.m`).
	*  `mcmcJAGS` will use the JAGS inference software to conduct parameter estimation using MCMC methods.
* `model1MCMCse.m` runs a large simulation to study the variability in MCMC-derived estimates of an observers internal variance. Warning: this function can take days to run even on a fast multi-core machine with lots of RAM.
* `model1MCMCconvergence`
* `model2runme.m`
* `model2psychometric`
* `model3runme.m` 


## Options when running the code
* If you have a computer with multiple CPU cores, then you can run the MCMC chains in parallel by setting `mcmcparams.doparallel = 1` in the file `/funcs/define_mcmcparams.m`. 
* You can elect to make inferences based upon the common dataset generated by the file `/generate_common_data.m` by setting `DATAMODE='load'`. Otherwise, new simulated observer behaviour can be generated by `DATAMODE='generate'`.

## Dependencies
* This code was generated and tested with **Matlab 2014a**.
* The **Matlab Statistics Toolbox** is required for Stage 3 of Model 1, when using grid approximation.
* Models using JAGS to make inferences require:
	* **JAGS**, which can be downloaded from [http://mcmc-jags.sourceforge.net](http://mcmc-jags.sourceforge.net)
	* **matjags.m** is included in `/funcs` and works with the code here. Updated versions may be found in the repository [https://github.com/msteyvers/matjags](https://github.com/msteyvers/matjags) but of course future changes may introduce incompatibilities.



