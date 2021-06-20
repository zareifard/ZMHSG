# ZMHSG
                                    
Description: 
The function ZMHSG is taken from the paper "Zareifard, H., and Jafari Khaledi, M.(2021). A heterogeneous Bayesian regression model for skewed spatial data". 
The paper develops a hierarchical skew-Gaussian process which is capable of simultaneously handling skewness and nonstationarity.

Usage:
      ZMHSG(coord.y,coord.p,simulate,burnin,Break,pred,Fix.kappa,n.cluster,initial,hyper,tuning)


Arguments:

coord.y:
           An n * 3 matrix with the coordinates of the n sampling locations and the value of n observations. 

coord.p:	
           An N * 2 (N>1) matrix with the 2-D coordinates of the N prediction locations. 

simulate:
           The total number of samples to be simulated.

burnin:
           The burn-in time. Number of samples in MCMC sampling to be discarded as burn-in phase, must be non-negative.

Break:
           The lag value. It is used for reducing autocorrelation of random points in Gibbs sampling. Must be an integer >= 1.

pred:
           If TRUE, then predction in the coordinates of matrix "coord.p" is done.

Fix.kappa:
           logical; determines whether the smoothness parameter should be fitted. 
           If TRUE, then it is estimated and if FALSE it is fixed at initial value for this parameter.

n.cluster
           A list containing two values. 
           The first value is the number of clusters for the locations in places where the less-than-median responses occurred.
           The second value is the number of clusters for the locations in places where the larger-than-median responses occurred.

initial:    
           a list containing the initial value of parameters sig2, tau2 , alpha

hyper:
           a list with the specification of priors for the model parameters. 
           D.phi:         refer to equation 29 of Zareifard and Khaledi (2021)
           E.kappa:       is a priori expected value for kappa
           S.kappa:       sets uncertainty on E.kappa
           Ls, Us:        the prior on sigma is uniform on (Ls,Us)
           Lt, Ut:        the prior on tau is uniform on (Lt,Ut)
           m.b,c.b:       the prior on beta is N(m.b,c.b)
           m.a,c.a,La,Ua: the prior on the skewness parameter is truncated normal, TN(La,Ua;m.a,c.a),
                          where the hyperparameters La and Ua show our knowledge about the possible values for the skewness parameter. 
                          The hyperparameter m.a should be chosen in the interval (La,Ua) which is an indication of the mode of our priori knowledge. 
                          Finally, the value of c.a sets uncertainty on m.a.

tuning:
           A list containing the tuning parameters for the range and smoothness parameters, respectively.
             




Outputs:


   1- summary information on the posterior distribution of the model parametes.
   2- results on on the posterior distribution of the model parameters. 
   3- results on the predictive distribution at the prediction locations, if provided. 

