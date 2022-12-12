# COMP561

Jupyter notebook for COMP 561 final project

Running mclust in R is done using these commands:

```
library(anndata)
library(mclust)
library(unix)
rlimit_as(1e12)

ad <- anndata::read_h5ad('/home/xding14/projects/def-junding/xding14/gvae_model/adata_z_GVAE_train05.h5ad')
data <- matrix(unlist(ad$X), nrow = 3460)
set.seed(2020)
mod1 <- Mclust(data, G=7, "EEE")
ad$obs["mclust"] <- mod1$classification
write_h5ad(ad, "/home/xding14/projects/def-junding/xding14/gvae_model/adata_GVAE_train05_mclust.h5ad")
'''
