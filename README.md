# PhD-in-Biostatistics-First-year-report
##############################################################
This project is for the First year report of PhD in Biostatistics.
The main purpose of this project is to serve for the report, and it is only partial of the all codes.
It covers all output results in this report.
There exists a range of other explorations that have not been included in that github link. 
However, this code suffices for the results relevant in this report.
The code has only been briefly commented and has not been fully commented as a published package level, 
and it is subject to improvements.
##############################################################
We start introducing and commenting on codes in this project apart from the main code:

###########
layer_train
###########
This program is to train each layer, note the layered network need to be loaded in for the training to be possible:
load(“layered_network_new_new_new”)
Note layers training requires changing the layer matrix input, 
where matrix corresponds to the current layer that need to be trained, 
and last_mat is the previous layer. 
If training the third layer:

matrix<-layered_network_new[[3]]
last_mat<-layered_network_new[[2]]
In particular, if training the first layer, last_mat should be change to a matrix of 1 with diagonal zeros, representing a fully connect network:
last_mat<-matrix(1,7,7)
diag(last_mat)<-0


###########
layer_sim
###########
This program is necessary for both the main code and layer_train. 
It is to simulate network layers, constrained to the previous layer. 
It is recommended to source this code prior running the main code and the layer_train.


###########
time_gergm 1
###########
This program is to assess the computational need for GERGM framework 1. 
Note the current implementation only assess up to network size 21. 
We do not recommend trying size larger than 21 due to the time taken will be too long, 
but this can be achieved by changing size_attempts:

size_attempts <-seq(7,21,1)


###########
evaluation
###########
This is to plot evaluation plots for models. 
The input network_list should be a list of networks in the network.ergm format, 
while the observed_net should be in matrix format.
Two type of evaluation exists, one for binary and one for weighted. 
Binary is to evaluate after binarization by threshold 0.4, such that comparison can be made with binary ERGM.

##############################################################
We start introducing and commenting on the main code:


Code in GERGM 2 and Multi-layered need multiple cores, which has been set to 60 cores. User may adjust it to their preferable level.





GERGM 2
The code of GERGM2 is taking a long fitting time, and should be implemented with care. Note due to the computations of this model is performed in a manner the normal R program cannot directly extract out the output. The grid search as described in the report is manual and rather repetitive, which is therefore excluded from the code section. Note the use_MPLE_only should be switched as F if exploring the training process, and it should be switched to T if want to see the final result with the user_specified_initial_thetas set as the trained parameter estimates.
