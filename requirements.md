# Software requirements

The original notebook used R 4.4.1 with the following packages:

```r
install.packages(c(
  "dplyr",
  "tidyr",
  "ggplot2",
  "reshape2"
))
```

To run the `.ipynb` file, install the R kernel for Jupyter:

```r
install.packages("IRkernel")
IRkernel::installspec()
```

For a production-quality revision, consider initializing an `renv` environment and committing the generated `renv.lock` file.

