### Installing `rjags` and `jagsUI` R packages on Yeti

#### Login to Yeti

```
ssh username@yeti.cr.usgs.gov
```

where `username` is your AD username and the password is your AD password.

Load jags module:

```
module load jags/4.3.0-gcc
```

Download `rjags` tar ball and install from source:

```bash
wget https://cran.r-project.org/src/contrib/rjags_4-8.tar.gz

R CMD INSTALL rjags_4-8.tar.gz --configure-args="--with-jags-libdir=/cxfs/projects/root/opt/JAGS-4.3.0/gcc/lib --with-jags-includedir=/cxfs/projects/root/opt/JAGS-4.3.0/gcc/include"

rm rjags_4-8.tar.gz
```





### Installing `jagsUI` R package

Load jags module first:

```
module load jags/4.3.0-gcc
```

In R:

```R
> install.packages('jagsUI', dep=TRUE)
```

