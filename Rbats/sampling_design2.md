
#Bat survey in Plumas National Forest through the use of acoustic bat detectors
###author: Derek Corcoran
####Last update: 2015-05-23













#Introduction

To study bat occupancy in the Plumas national forest by surveying acustically different areas of the forest, the three objective species for this survey are the Pallid bat, the Townsend's Long-eared bat, and the California Bat. Nevertheless, there is at least 14 species that form the bat ensemble in the national forest, the list of species is the following

- Tadarida brasiliensis – free-tailed bat
- *Antrozous pallidus - Pallid Bat*
- Eptesicus fuscus - Big Brown Bat
- Euderma maculatum - Spotted Bat
- Lasionycteris noctivagans - Silvered-haired Bat
- Lasiurus blossevillii - Western Red Bat
- Lasiurus cinereus - Hoary Bat
- *Corynorhinus townsendii - Townsend's Long-eared Bat*
- *Myotis californicus - California Bat*
- Myotis evotis - Long-eared Bat
- Myotis lucifugus - Little Brown Bat
- Myotis thysanodes - Fringed Bat
- Myotis volans - Hairy-winged bat
- Myotis yumanensis - Yuma myotis

##Objective of the study

To determine the factors that influence bat occupancy in heterogeneous environments of Plumas national forest, including areas corresponding to the moonlight fire and the Storrie fire. Comparing and compementing biotic and abiotic variables. 






```
## OGR data source with driver: ESRI Shapefile 
## Source: "C:/Users/usuario/Bats_California/layers", layer: "NHDFlowline"
## with 119018 features
## It has 13 fields
```

```
## Warning in readOGR(dsn = "C:/Users/usuario/Bats_California/layers", layer
## = "NHDFlowline"): Z-dimension discarded
```

# Specific resear questions and the factors that might influence them

##1. Which factors affect bat occupancy in burned forest?
        
###Does bat occupancy differ with the duration of time since the fire?

-	Explanatory variable = burn age at sampling sites (mean number of years between fires for a given point and the time till the last fire for a given point).

![](Sampling_Design2_files/figure-html/unnamed-chunk-11-1.png) 

###Does bat occupancy differ with burn intensity

- Explanatory variable = burn intensity (in the following figure we see the layers that will allow us to work with burn intensity, this layers are v.1= burn intensity of the soil, v.2= burn intensity of the canopy, and v.3= Burn intensity of the basal area)

![](Sampling_Design2_files/figure-html/unnamed-chunk-12-1.png) 

###Does bat occupancy differ with forest type

- Explanatory variable = Stand type 
-	Explanatory variable = Forest type (type of forest typified in SeralStage, which is seen as band 1.1 in the next figure)
-	Explanatory variable = Historic burn age (Shown as mean year intervals in the next figure as band 1.2)

![](Sampling_Design2_files/figure-html/unnamed-chunk-13-1.png) 


###Does bat occupancy differ with roost site availability?

- Explanatory variable = Associated forest metrics (Lidar???, distance to water) 

**Concidering that we will work using lidar images, the layers to use will be acquired later, since most of this variables are only presented for del black polygon in the next figure.**



```
## Warning in polypath(x = mcrds[, 1], y = mcrds[, 2], border = border, col =
## col, : "legend" is not a graphical parameter
```

![](Sampling_Design2_files/figure-html/unnamed-chunk-14-1.png) 

##Which factors affect bat occupancy in unburned forest?

- explanatory variables = Abiotic variables (Altitud[*shown as band 1 in the next figure*], distance to road [*shown as layer in the next figure*], distance to water *being procesed at the time*, distance to road+trail *being procesed at the time*)

![](Sampling_Design2_files/figure-html/unnamed-chunk-15-1.png) 

##Is occupancy affected by presence of heterospecifics?

###is bat occupancy affected by presence of other bats? (competition)

- Explanatory variable, occupancy of other bats (based on this study)

###is bat occupancy affected by the presence of preys?

- Explanatory variable, athropod emergence (Loren's Study)

###is bat occupancy affected by the presence of predators

- Explanatory variables marten, and spotted owl layers from NFS (Spotted owl habitat foraging and nesting shown as *band 1.1* and *band 1.2* in the next figure and Marten habitat shown as *band 1.3* in the next figure)

![](Sampling_Design2_files/figure-html/unnamed-chunk-16-1.png) 

#Sampling desing and sampling unit

In order for us to study bat occupancy and to spatially predict it using the factors described in the previous section, most of the diversity of the forest has to be included in the model. To include that variability, I classified the environments using the following layers (Topography, Intervals between fires, Forest Type, Distance to roads, Nesting Habitat quality for Spotted owl, foraging Habitat quality for Spotted owl, Habitat Quality for Marten) **[to be included tomorrow, distance to rivers, and distance to roads/path]**

##Check for correlation between rasters

First will scale every layer so that it goes from 0 to 1, in order for no layer to have more weight in the classification. And then we check the correlation between rasters. in the next graph/table, we see the relationship between our predictive variables. Here we see that we might want to take one of the two habitat quality layers for the Spotted Owl (R=0.74), and since we are using the spoted owl as a potential predator, we will keep the foraging habitat quality.




```
## Loading required package: sp
```

![](Sampling_Design2_files/figure-html/unnamed-chunk-17-1.png) ![](Sampling_Design2_files/figure-html/unnamed-chunk-17-2.png) ![](Sampling_Design2_files/figure-html/unnamed-chunk-17-3.png) 

#Clasification

Now we will use kmeans to sort the area into 5 types of habitat using the abovementioned rasterstack, and it will be ploted with different colors for every type of environment.


![](Sampling_Design2_files/figure-html/unnamed-chunk-18-1.png) 

More info on how to do this clasification in *https://geoscripting-wur.github.io/AdvancedRasterAnalysis/*

#separate layers acording to places with or without fire

Now we will separate the whole area in two subtypes burned areas and non-buned areas, based on the burn severity layers

![](Sampling_Design2_files/figure-html/unnamed-chunk-19-1.png) ![](Sampling_Design2_files/figure-html/unnamed-chunk-19-2.png) 

#Extract Random points from each habitat type with equal number in fire and non fire

During the first year of sampling 120 samples will be colected, 60 in burned areas, and 60 in non-burned areas, within each, 12 random points will be sampled in each habtitat type defined by the K-means classification.


- 60 random points in not Fire, 12 random points per each environment type
- 60 random points in Fire, 12 random points per each environment type
- We plot the chosen random points over the topographic map, each color is an environment type, full circles are places where there was no fire, and full triangles, where there was a fire





```
## Loading required package: lattice
## Loading required package: latticeExtra
## Loading required package: RColorBrewer
```

![](Sampling_Design2_files/figure-html/unnamed-chunk-21-1.png) 

###Values


Table: Mean value for every variable for each ID which combines prior classification (1 to 5) and fire or no fire (f or nf)

ID       Height   Fire Interval   Distance to Road   Sage Stage   Distance to Water
----  ---------  --------------  -----------------  -----------  ------------------
1nf    1197.845       -2.609845           170.4107    15.936056             0.00000
1f     1222.889        6.992421           591.0009    16.385627             0.00000
2nf    1690.710     -591.968940           604.5243     8.919113            54.02922
2f     1426.504     -654.369502           272.1700     9.460569            27.12199
3nf    1751.129       16.665731           324.0886     4.355227            27.16567
3f     1677.121       13.078462           459.2075     3.851336            27.15213
4nf    1798.252      -39.535105           380.1112    15.186496             0.00000
4f     1725.804       15.743448           207.7010    15.003658             0.00000
5nf    1022.439      -21.384715           365.6794     5.083759            27.25722
5f     1216.994      -12.469844           713.0377     6.514431            27.09332

#Simulated sampling Dynamic modeling


```r
library("unmarked", lib.loc="~/R/win-library/3.2")
```

###First we simulate our detection history for 30 sites with four primary sampling periods, and three secondary sampling periods each.


 s1.1   s1.2   s1.3   s2.1   s2.2   s2.3   s3.1   s3.2   s3.3   s4.1   s4.2   s4.3
-----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----  -----
    1      1      1      1      1      1      0      1      1      1      1      1
    1      1      1      1      1      1      0      0      1      1      1      1
    1      1      0      1      1      1      1      1      1      1      1      1
    1      1      1      0      1      1      1      1      1      1      1      1
    0      1      0      1      1      1      1      1      1      1      1      1
    0      1      1      1      1      1      1      1      1      1      1      1
    1      1      1      1      1      1      1      1      0      1      1      0
    1      0      1      1      1      1      1      0      1      1      1      1
    1      1      1      1      1      1      1      1      1      1      1      1
    1      1      1      1      1      1      1      0      1      1      1      1
    1      0      0      1      0      0      1      1      1      0      1      1
    1      0      0      1      0      0      1      0      0      0      0      0
    0      0      0      0      1      1      1      1      1      0      0      1
    1      0      0      1      1      1      0      1      1      0      1      0
    0      1      1      0      0      0      1      0      0      1      0      1
    0      0      0      1      1      0      1      1      0      1      0      0
    0      1      0      1      1      0      0      0      0      1      1      0
    0      1      0      1      0      1      0      0      0      1      0      1
    0      0      1      1      0      0      0      0      0      0      1      0
    1      1      0      1      0      1      1      0      0      0      0      1
    0      0      0      0      0      0      0      0      0      0      0      0
    0      0      1      0      1      0      0      0      0      0      0      0
    0      0      0      1      0      0      0      0      0      0      0      0
    0      1      1      1      0      0      0      0      0      0      0      0
    0      0      0      0      1      0      0      1      0      1      1      0
    0      0      0      1      1      0      0      0      0      0      0      0
    1      0      0      0      0      1      0      0      1      0      0      1
    1      0      0      0      1      0      0      0      0      0      0      0
    0      0      0      0      1      1      0      0      0      0      0      0
    0      0      0      0      0      0      0      0      1      0      0      0

This simulated data has some underlying characteristics:

**environment a (top 10 rows, the best environment for bats, also occupancy increases with time)**

```r
mean(sampling.ocup1[1:10])
```

```
## [1] 0.8
```
**environment b (rows 11 to 20, medium environment, occupancy stays the same)**

```r
mean(sampling.ocup1[11:20])
```

```
## [1] 0.4
```
**environment c (rows 21 to 30) poor environment for bats, also there is extintion)**

```r
mean(sampling.ocup1[21:30])
```

```
## [1] 0.2
```

Now we will simulate some variables for the site covariates.
###Site cov static
**the more variable 1, the better for bats**




```r
mean(v.1[1:10])
```

```
## [1] 20.39816
```

```r
mean(v.1[11:20])
```

```
## [1] 9.724912
```

```r
mean(v.1[21:30])
```

```
## [1] 4.93219
```


###the less variable 2 better for bats



```r
mean(v.2[1:10])
```

```
## [1] 19.85988
```

```r
mean(v.2[11:20])
```

```
## [1] 40.04326
```

```r
mean(v.2[21:30])
```

```
## [1] 60.12082
```

###variable 3 does not mater to bats




```r
mean(v.3[1:10])
```

```
## [1] 19.89459
```

```r
mean(v.3[11:20])
```

```
## [1] 19.93174
```

```r
mean(v.3[21:30])
```

```
## [1] 20.13167
```


```r
sampling.cov<- cbind(v.1,v.2, v.3)
```
###yearly colonization extintion variable


```r
temp1<-rnorm(n=30, mean=20, sd=10)
temp2<-rnorm(n=30, mean=40, sd=10)
temp3<-rnorm(n=30, mean=50, sd=10)
temp4<-rnorm(n=30, mean=60, sd=10)


temps <-cbind(temp1,temp2, temp3, temp4)
```
###observer within secondary it could be variable


###observers dont vary in the model, they should all be the same


```r
obs1<-rnorm(n=30, mean=40, sd=0.7)
obs2<-rnorm(n=30, mean=40, sd=0.7)
obs3<-rnorm(n=30, mean=40, sd=0.7)
obs4<-rnorm(n=30, mean=40, sd=0.7)
obs5<-rnorm(n=30, mean=40, sd=0.7)
obs6<-rnorm(n=30, mean=40, sd=0.7)
obs7<-rnorm(n=30, mean=40, sd=0.7)
obs8<-rnorm(n=30, mean=40, sd=0.7)
obs9<-rnorm(n=30, mean=40, sd=0.7)
obs10<-rnorm(n=30, mean=40, sd=0.7)
obs11<-rnorm(n=30, mean=40, sd=0.7)
obs12<-rnorm(n=30, mean=40, sd=0.7)

observers1<-data.frame(cbind(obs1,obs2,obs3, obs4, obs5, obs6, obs7, obs8, obs9, obs10, obs11, obs12))

observers2<-data.frame(cbind(obs1,obs2,obs3, obs4, obs5, obs6, obs7, obs8, obs9, obs10, obs11, obs12))

observers<-list(observers1, observers2)
names(observers) <-c("obs1", "obs2")
```
###primary model

```r
umf1 <- unmarkedMultFrame(y = sampling.ocup1, 
                            siteCovs = data.frame(sampling.cov), 
                            yearlySiteCovs=data.frame(temps),
                            obsCovs=observers, numPrimary=3)
```
##Dynamic model
first term static variables
second term colonization (variable)
third extintion (variable)
detection (observer)
###the best model should take into acount v.1 and v.2, but not v.3, it shouldn't take into acount observers


```r
model1 <- colext(~v.1+v.2+v.3, ~1, ~1, ~1, umf1)

model2 <- colext(~1, ~1, ~1, ~1, umf1)

model3 <- colext(~v.1+v.2, ~1, ~1, ~1, umf1) #this should be the best model
model1
```

```
## 
## Call:
## colext(psiformula = ~v.1 + v.2 + v.3, gammaformula = ~1, epsilonformula = ~1, 
##     pformula = ~1, data = umf1)
## 
## Initial:
##             Estimate    SE       z P(>|z|)
## (Intercept)   0.0822  62.0 0.00133   0.999
## v.1           1.1739  73.2 0.01604   0.987
## v.2           2.6773 108.4 0.02471   0.980
## v.3           1.6349  82.4 0.01985   0.984
## 
## Colonization:
##  Estimate   SE      z P(>|z|)
##     -0.69 1.23 -0.562   0.574
## 
## Extinction:
##  Estimate    SE     z  P(>|z|)
##     -1.71 0.419 -4.08 4.56e-05
## 
## Detection:
##  Estimate    SE    z P(>|z|)
##     0.291 0.121 2.41  0.0162
## 
## AIC: 488.0362
```

```r
model2
```

```
## 
## Call:
## colext(psiformula = ~1, gammaformula = ~1, epsilonformula = ~1, 
##     pformula = ~1, data = umf1)
## 
## Initial:
##  Estimate    SE    z P(>|z|)
##      1.78 0.569 3.13 0.00174
## 
## Colonization:
##  Estimate    SE      z P(>|z|)
##    -0.104 0.719 -0.145   0.885
## 
## Extinction:
##  Estimate    SE     z  P(>|z|)
##      -1.8 0.433 -4.15 3.36e-05
## 
## Detection:
##  Estimate    SE    z  P(>|z|)
##      0.45 0.129 3.48 0.000492
## 
## AIC: 470.846
```

```r
model3
```

```
## 
## Call:
## colext(psiformula = ~v.1 + v.2, gammaformula = ~1, epsilonformula = ~1, 
##     pformula = ~1, data = umf1)
## 
## Initial:
##             Estimate    SE       z P(>|z|)
## (Intercept)   0.0822  58.9 0.00139   0.999
## v.1           1.1733  69.6 0.01686   0.987
## v.2           2.6759 103.0 0.02598   0.979
## 
## Colonization:
##  Estimate   SE      z P(>|z|)
##     -0.69 1.23 -0.562   0.574
## 
## Extinction:
##  Estimate    SE     z  P(>|z|)
##     -1.71 0.419 -4.08 4.56e-05
## 
## Detection:
##  Estimate    SE    z P(>|z|)
##     0.291 0.121 2.41  0.0162
## 
## AIC: 486.0355
```

#APENDIX

##Apendix 1


Table: Values recorded for each selected sampling point toghether with it's ID

   Long     Lat    Height   Fire Interval   Distance to Road   Sage Stage   Distance to Water  ID  
-------  ------  --------  --------------  -----------------  -----------  ------------------  ----
 120.96   39.99   1113.11           16.00             325.01        18.00                0.00  1nf 
 120.98   40.03   1132.27           18.03             324.83        18.00                0.00  1nf 
 120.89   39.97   1200.33           15.04               0.00        14.94                0.00  1nf 
 120.88   39.96   1173.06           16.63               0.00        12.83                0.00  1nf 
 120.79   39.91   1268.44           16.00             534.64        18.00                0.00  1nf 
 121.42   39.75   1058.93           12.80               0.00        12.25                0.00  1nf 
 120.83   40.09   1116.88         -197.89               0.00        15.72                0.00  1nf 
 120.67   40.04   1419.19           16.00             534.24        18.00                0.00  1nf 
 121.36   39.69    848.66           16.08               0.00        17.55                0.00  1nf 
 120.80   40.11   1242.23           12.99               0.00        11.95                0.00  1nf 
 120.55   39.74   1420.45           11.00             326.20        16.00                0.00  1nf 
 120.70   40.04   1380.59           16.00               0.00        18.00                0.00  1nf 
 120.82   40.17   1395.69           16.19             848.42        18.00                0.00  1f  
 121.23   39.74   1348.48           15.97               0.00        17.92                0.00  1f  
 121.29   39.67    804.17           16.00             326.55        17.19                0.00  1f  
 121.27   40.05   1388.46           11.00            2124.84        12.00                0.00  1f  
 121.11   40.10   1194.40           25.42             424.21        13.21                0.00  1f  
 120.78   40.19   1274.34         -106.35             324.05        17.28                0.00  1f  
 121.09   40.10   1386.49           28.30             424.21        17.41                0.00  1f  
 121.35   39.85    999.21           14.12             908.78        13.12                0.00  1f  
 120.79   40.20   1459.12           16.00             648.06        18.00                0.00  1f  
 120.77   40.21   1326.47           15.26               0.00        16.49                0.00  1f  
 121.18   40.02   1315.20           16.00            1062.89        18.00                0.00  1f  
 121.34   39.74    782.64           16.00               0.00        18.00                0.00  1f  
 120.45   39.96   1664.41         -313.32             534.51        10.63                0.00  2nf 
 120.34   39.91   1911.61         -699.58            1301.57        13.07                0.00  2nf 
 120.29   39.93   2123.75         -538.63             776.70         7.69                0.00  2nf 
 121.35   39.65    939.60         -734.65             326.64        10.46                0.00  2nf 
 120.61   40.05   1657.76         -530.30            1313.41        14.77                0.00  2nf 
 120.51   39.75   1671.11         -729.64            1070.17         3.73                0.00  2nf 
 120.81   40.12   1078.75         -999.00             648.75         4.00              324.38  2nf 
 120.36   39.96   1891.77         -393.10             424.21        10.36                0.00  2nf 
 120.52   40.21   1983.61         -403.61             533.78        10.39              323.98  2nf 
 120.36   40.09   1750.29         -549.58             324.56         8.35                0.00  2nf 
 120.90   39.81   1941.00         -697.47               0.00         4.89                0.00  2nf 
 120.43   39.96   1674.85         -514.75               0.00         8.68                0.00  2nf 
 121.19   40.04   1702.91         -352.31             324.78        10.24                0.00  2f  
 120.58   40.18   1543.07         -942.50               0.00        11.28                0.00  2f  
 120.30   40.07   1796.92         -617.69               0.00         4.37                0.00  2f  
 121.36   39.90    684.18         -572.82               0.00        12.93                0.00  2f  
 120.58   40.16   1644.59         -491.82               0.00         3.50                0.00  2f  
 121.38   39.83   1031.00         -429.13             777.46         8.40                0.00  2f  
 120.25   39.84   1635.93         -621.20             534.83         7.65                0.00  2f  
 120.33   39.87   2049.70         -780.87             325.57        12.72                0.00  2f  
 120.32   39.91   2018.50         -667.24             325.39         9.82                0.00  2f  
 121.02   39.72   1622.63         -682.35             652.55        10.79                0.00  2f  
 121.36   39.89    719.03         -999.00             325.46        11.60              325.46  2f  
 121.39   39.86    669.60         -695.51               0.00        10.22                0.00  2f  
 120.42   40.08   1910.09           16.00             324.59         3.00                0.00  3nf 
 120.50   40.09   1784.05           11.00             649.04         6.87                0.00  3nf 
 120.93   39.78   1727.74           16.00             325.99         6.92              325.99  3nf 
 120.59   39.96   2044.71           16.00               0.00         3.00                0.00  3nf 
 120.71   39.78   1657.38           15.98             535.00         6.99                0.00  3nf 
 121.06   39.98   1481.47           11.56             325.07         3.00                0.00  3nf 
 121.13   39.80   1576.90           16.97             325.90         2.61                0.00  3nf 
 121.06   39.85   1628.24           15.06               0.00         7.98                0.00  3nf 
 120.74   39.94   2046.51           21.94               0.00         3.21                0.00  3nf 
 120.72   39.98   1813.63           17.47             424.21         2.85                0.00  3nf 
 120.85   39.69   1637.60           26.00             979.26         2.00                0.00  3nf 
 120.93   39.77   1705.25           16.00               0.00         3.81                0.00  3nf 
 121.20   40.16   1485.50           11.42            1829.58         3.00                0.00  3f  
 120.69   40.18   1924.66           14.36             324.08         3.94                0.00  3f  
 120.45   40.13   1792.21           11.00             533.99         4.03                0.00  3f  
 120.63   39.82   1791.21           16.00               0.00         3.11              325.83  3f  
 120.31   40.13   1636.63           11.00            1550.21         6.00                0.00  3f  
 120.61   40.12   1696.70           15.81               0.00         5.08                0.00  3f  
 121.20   40.10   1540.62           11.00             848.42         3.26                0.00  3f  
 120.74   39.91   1499.65           11.00             424.21         2.03                0.00  3f  
 120.70   40.00   1778.09           11.00               0.00         3.00                0.00  3f  
 120.61   40.16   1612.21           15.81               0.00         3.50                0.00  3f  
 121.18   39.80   1669.78           17.54               0.00         6.23                0.00  3f  
 120.34   40.13   1698.18           11.00               0.00         3.03                0.00  3f  
 120.38   40.10   1835.58           12.61             324.50        11.81                0.00  4nf 
 120.47   40.09   1819.99           25.31             324.52        14.32                0.00  4nf 
 120.81   40.02   2161.92         -115.92             908.50        18.80                0.00  4nf 
 120.51   39.96   1685.56           28.94               0.00        14.50                0.00  4nf 
 120.40   39.98   1707.15         -269.03               0.00        13.71                0.00  4nf 
 120.39   39.88   1825.43         -145.77             651.11        12.50                0.00  4nf 
 120.48   40.02   1729.29           26.47               0.00        14.71                0.00  4nf 
 120.70   40.04   1541.39           24.57             424.21        18.00                0.00  4nf 
 120.75   40.03   1549.05           15.88            1068.61        17.64                0.00  4nf 
 120.37   39.99   1781.29           11.00               0.00        16.00                0.00  4nf 
 120.92   39.82   1844.33         -123.48             534.89        16.24                0.00  4nf 
 120.31   39.99   2098.05           35.00             324.99        14.00                0.00  4nf 
 120.82   40.20   1573.69           15.53               0.00        16.60                0.00  4f  
 120.40   40.02   1831.06           16.00            1068.65        15.58                0.00  4f  
 120.63   40.12   1509.80           14.60               0.00        15.48                0.00  4f  
 120.36   39.90   1769.06           11.00             325.45        16.00                0.00  4f  
 120.79   40.21   1609.06           16.00             774.45        18.00                0.00  4f  
 120.52   40.17   1799.88           11.00               0.00        16.00                0.00  4f  
 120.31   40.08   1815.86           27.02               0.00        14.66                0.00  4f  
 120.50   40.17   1891.75           13.00               0.00        15.83                0.00  4f  
 120.78   40.23   1735.03           16.00             323.87        10.90                0.00  4f  
 120.55   40.15   1718.60           11.00               0.00        16.00                0.00  4f  
 120.82   40.21   1580.65           13.54               0.00        10.62                0.00  4f  
 120.31   40.09   1875.21           24.22               0.00        14.37                0.00  4f  
 121.35   39.69    921.99           14.13               0.00         7.01                0.00  5nf 
 121.33   39.71   1025.25           11.00             326.35         4.28                0.00  5nf 
 121.03   39.56   1050.38           11.13             327.03         7.81                0.00  5nf 
 121.41   39.69    401.41         -420.37            1295.80         8.19                0.00  5nf 
 121.08   39.58   1217.57           11.00             326.94         3.00                0.00  5nf 
 121.03   39.61   1330.10           11.06               0.00         3.18                0.00  5nf 
 121.13   39.55   1154.84           11.00               0.00         3.00              327.09  5nf 
 121.30   39.62    409.66           29.00             909.18         6.00                0.00  5nf 
 121.40   39.69    607.77           26.58             778.64         6.00                0.00  5nf 
 121.12   39.74   1467.85           13.83               0.00         4.13                0.00  5nf 
 121.03   39.69   1485.10           14.02             424.21         5.41                0.00  5nf 
 121.09   39.62   1197.35           11.00               0.00         3.00                0.00  5nf 
 121.03   39.82   1120.74         -294.56            1065.58        10.04                0.00  5f  
 121.16   39.78    858.63           21.24            1958.46         4.97                0.00  5f  
 121.23   39.64   1163.32           11.00             778.94         4.62                0.00  5f  
 121.24   40.06   1451.13           11.00               0.00         9.21                0.00  5f  
 121.11   40.10   1179.25           11.00             775.33         3.00                0.00  5f  
 121.33   39.87   1281.04           11.00             534.75         4.26                0.00  5f  
 121.24   39.76   1383.27           14.01             424.21         6.21                0.00  5f  
 121.30   39.97   1183.63           14.10            1292.77         5.68              325.12  5f  
 121.16   39.80   1168.41           11.00             977.80         5.10                0.00  5f  
 120.79   40.13   1282.01           15.03             424.21         8.44                0.00  5f  
 121.19   40.12   1429.10           12.63             324.39         7.90                0.00  5f  
 121.45   39.84   1103.40           12.92               0.00         8.75                0.00  5f  


```r
summary(Vegetation_existing)
```

```
##               band1
## Min.        1.00000
## 1st Qu.     4.00000
## Median      7.00000
## 3rd Qu.    13.49004
## Max.       25.56028
## NA's    64040.00000
```

```r
str(Vegetation_existing)
```

```
## Formal class 'RasterLayer' [package "raster"] with 12 slots
##   ..@ file    :Formal class '.RasterFile' [package "raster"] with 13 slots
##   .. .. ..@ name        : chr ""
##   .. .. ..@ datanotation: chr "FLT4S"
##   .. .. ..@ byteorder   : chr "little"
##   .. .. ..@ nodatavalue : num -Inf
##   .. .. ..@ NAchanged   : logi FALSE
##   .. .. ..@ nbands      : int 1
##   .. .. ..@ bandorder   : chr "BIL"
##   .. .. ..@ offset      : int 0
##   .. .. ..@ toptobottom : logi TRUE
##   .. .. ..@ blockrows   : int 0
##   .. .. ..@ blockcols   : int 0
##   .. .. ..@ driver      : chr ""
##   .. .. ..@ open        : logi FALSE
##   ..@ data    :Formal class '.SingleLayerData' [package "raster"] with 13 slots
##   .. .. ..@ values    : num [1:108500] NA NA NA NA NA NA NA NA NA NA ...
##   .. .. ..@ offset    : num 0
##   .. .. ..@ gain      : num 1
##   .. .. ..@ inmemory  : logi TRUE
##   .. .. ..@ fromdisk  : logi FALSE
##   .. .. ..@ isfactor  : logi FALSE
##   .. .. ..@ attributes: list()
##   .. .. ..@ haveminmax: logi TRUE
##   .. .. ..@ min       : num 1
##   .. .. ..@ max       : num 25.6
##   .. .. ..@ band      : int 1
##   .. .. ..@ unit      : chr ""
##   .. .. ..@ names     : chr "band1"
##   ..@ legend  :Formal class '.RasterLegend' [package "raster"] with 5 slots
##   .. .. ..@ type      : chr(0) 
##   .. .. ..@ values    : logi(0) 
##   .. .. ..@ color     : logi(0) 
##   .. .. ..@ names     : logi(0) 
##   .. .. ..@ colortable: logi(0) 
##   ..@ title   : chr(0) 
##   ..@ extent  :Formal class 'Extent' [package "raster"] with 4 slots
##   .. .. ..@ xmin: num -122
##   .. .. ..@ xmax: num -120
##   .. .. ..@ ymin: num 39.4
##   .. .. ..@ ymax: num 40.3
##   ..@ rotated : logi FALSE
##   ..@ rotation:Formal class '.Rotation' [package "raster"] with 2 slots
##   .. .. ..@ geotrans: num(0) 
##   .. .. ..@ transfun:function ()  
##   ..@ ncols   : int 434
##   ..@ nrows   : int 250
##   ..@ crs     :Formal class 'CRS' [package "sp"] with 1 slot
##   .. .. ..@ projargs: chr "+proj=longlat +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +no_defs"
##   ..@ history : list()
##   ..@ z       : list()
```

```r
names(Vegetation_existing)
```

```
## [1] "band1"
```

