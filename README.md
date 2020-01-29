# analogues
This is the source code of the package analogues. The package is not on [CRAN](https://cran.r-project.org/web/packages/raster/index.html). The analogues package allows calculating climatic distances based on gridded climate data.

## Installation
To install this package you can do:

```r
library(devtools)
install_github("CIAT-DAPA/analogues")
```

## Usage
You can use this package to calculate climatic similarity between a reference site and a prescribed area (e.g. the entire globe). This helps identifying locations with similar climates for, for instance, agricultural technology transfer or germplasm exchange. The following code should get you started (also see package examples):

```r
library(analogues)
data(climstack)

#create parameters
params <- createParameters(x=-75.5, y=3.2, vars=c("prec","tmean"),weights=c(0.5,0.5),
                           ndivisions=c(12,12),growing.season=c(1,12),rotation="tmean",threshold=1,
                           env.data.ref=list(prec,tavg), env.data.targ=list(prec,tavg),
                           outfile="~/.",fname=NA,writefile=FALSE)

#calculate similarity
sim_out <- calc_similarity(params)
```

The above example computes similarity for a site in South America (lon=-75.5, lat=3.2) with respect to the entire world. Climate data is from [WorldClim](http://worldclim.org), aggregated to 2 degrees, and reflects current climatic conditions (1979-2000). The similarity is computed based on both precipitation and average temperature, using the 12 months of the year.

