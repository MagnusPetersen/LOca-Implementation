# Introduction
This is an implementation of the LOca, local conformal autoencoder, model as described in the PNAS Paper "Local conformal autoencoder for standardized data coordinates" by Erez Peterfreund et al. [1] More speciffically it is the implementation of their toy model in the section 6.2/6.3 as it higlights the abilities and the use cases of the model well. I have no affiliation with the authors, I just liked the paper and wanted to share my implementation.

# LOca

The LOca is a method for finding standardised data coordinates from measurement data. In doing so it finds a transformation that the measured data has been subjected to and undoes it, finding a untransformed embedding, creating a space that is isometric to the systems latents. In essence this models solves the problem of finding an underlying representation of the studied system obscured by any transformation that it has been subjected to by measurement process or by the nature of the system itself. The input of this
model are clouds of data that capture the deformation the system has been subjected to on a local level. The general structure of the LOca deep learning model is that of an autoencoder with an additional loss function for the encoder.

# Implementation

This is a PyTorch implementation of the example in section 6.3/6.3. I used this example due to its value as a demonstration but all other Problems have a very similar code and tailoring my code to your needs is very easy. If you have any problems just contact me. The begining of the code contains the toy data preperation and the transformation of said data by a function that the model has to undo in its encoder and redo in its decoder. After wards i define and traine the model and test its interpolation capabilites.

# Technical Insights 

If you are working with high dimensional data it is advisable to use residual connections in the encoder and decoder, especially in the encoder as each dimension represents a local minima that represents potential for incomplete training. This happens because during training the model can output clouds that produce partially diagonalized covariance matrices creating a fully diagonal covariance matrix requires a significant change in model output. Residual connections solved this problem for me.

The model worked suprisingly well even for very hard transformationsy especially rotations appeared to be very easy to undo. 

# Sources 

[1] Erez Peterfreund, Ofir Lindenbaum, Felix Dietrich, Tom Bertalan, Matan Gavish, Ioannis G. Kevrekidis, and Ronald R. Coifman "Local conformal autoencoder for standardized data coordinates" PNAS December 8, 2020 117 (49) 30918-30927
