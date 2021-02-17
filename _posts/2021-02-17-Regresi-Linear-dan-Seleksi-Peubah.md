---
layout: post
title:  Regresi Linear dan Seleksi Peubah
categories: [Machine Learning,Supervised,Regression]
excerpt:
---

Package
-------

Silahkan install jika belum ada

``` r
install.packages("tidyverse")
install.packages("DataExplorer")
install.packages("skimr")
install.packages("corrplot")
install.packages("leaps")
```

Memanggil Package
=================

``` r
library(tidyverse)
library(DataExplorer)
library(skimr)
library(corrplot)
library(leaps)
```

Deskripsi singkat data
----------------------

Ask a home buyer to describe their dream house, and they probably won’t
begin with the height of the basement ceiling or the proximity to an
east-west railroad. But this playground competition’s dataset proves
that much more influences price negotiations than the number of bedrooms
or a white-picket fence.

With 79 explanatory variables describing (almost) every aspect of
residential homes in Ames, Iowa, this competition challenges you to
predict the final price of each home.

data ini bisa diperoleh di link berikut ini

[Data House
Price](https://drive.google.com/drive/folders/1oUczt7jnJq0XXxrVwOsUtBUc7l2pYCYf?usp=sharing)

Import Data
-----------

``` r
data_house <- read.csv("house_price1.csv",stringsAsFactors = TRUE)
glimpse(data_house)
```

    ## Rows: 1,460
    ## Columns: 81
    ## $ Id            <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, ...
    ## $ MSSubClass    <int> 60, 20, 60, 70, 60, 50, 20, 60, 50, 190, 20...
    ## $ MSZoning      <fct> RL, RL, RL, RL, RL, RL, RL, RL, RM, RL, RL,...
    ## $ LotFrontage   <int> 65, 80, 68, 60, 84, 85, 75, NA, 51, 50, 70,...
    ## $ LotArea       <int> 8450, 9600, 11250, 9550, 14260, 14115, 1008...
    ## $ Street        <fct> Pave, Pave, Pave, Pave, Pave, Pave, Pave, P...
    ## $ Alley         <fct> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,...
    ## $ LotShape      <fct> Reg, Reg, IR1, IR1, IR1, IR1, Reg, IR1, Reg...
    ## $ LandContour   <fct> Lvl, Lvl, Lvl, Lvl, Lvl, Lvl, Lvl, Lvl, Lvl...
    ## $ Utilities     <fct> AllPub, AllPub, AllPub, AllPub, AllPub, All...
    ## $ LotConfig     <fct> Inside, FR2, Inside, Corner, FR2, Inside, I...
    ## $ LandSlope     <fct> Gtl, Gtl, Gtl, Gtl, Gtl, Gtl, Gtl, Gtl, Gtl...
    ## $ Neighborhood  <fct> CollgCr, Veenker, CollgCr, Crawfor, NoRidge...
    ## $ Condition1    <fct> Norm, Feedr, Norm, Norm, Norm, Norm, Norm, ...
    ## $ Condition2    <fct> Norm, Norm, Norm, Norm, Norm, Norm, Norm, N...
    ## $ BldgType      <fct> 1Fam, 1Fam, 1Fam, 1Fam, 1Fam, 1Fam, 1Fam, 1...
    ## $ HouseStyle    <fct> 2Story, 1Story, 2Story, 2Story, 2Story, 1.5...
    ## $ OverallQual   <int> 7, 6, 7, 7, 8, 5, 8, 7, 7, 5, 5, 9, 5, 7, 6...
    ## $ OverallCond   <int> 5, 8, 5, 5, 5, 5, 5, 6, 5, 6, 5, 5, 6, 5, 5...
    ## $ YearBuilt     <int> 2003, 1976, 2001, 1915, 2000, 1993, 2004, 1...
    ## $ YearRemodAdd  <int> 2003, 1976, 2002, 1970, 2000, 1995, 2005, 1...
    ## $ RoofStyle     <fct> Gable, Gable, Gable, Gable, Gable, Gable, G...
    ## $ RoofMatl      <fct> CompShg, CompShg, CompShg, CompShg, CompShg...
    ## $ Exterior1st   <fct> VinylSd, MetalSd, VinylSd, Wd Sdng, VinylSd...
    ## $ Exterior2nd   <fct> VinylSd, MetalSd, VinylSd, Wd Shng, VinylSd...
    ## $ MasVnrType    <fct> BrkFace, None, BrkFace, None, BrkFace, None...
    ## $ MasVnrArea    <int> 196, 0, 162, 0, 350, 0, 186, 240, 0, 0, 0, ...
    ## $ ExterQual     <fct> Gd, TA, Gd, TA, Gd, TA, Gd, TA, TA, TA, TA,...
    ## $ ExterCond     <fct> TA, TA, TA, TA, TA, TA, TA, TA, TA, TA, TA,...
    ## $ Foundation    <fct> PConc, CBlock, PConc, BrkTil, PConc, Wood, ...
    ## $ BsmtQual      <fct> Gd, Gd, Gd, TA, Gd, Gd, Ex, Gd, TA, TA, TA,...
    ## $ BsmtCond      <fct> TA, TA, TA, Gd, TA, TA, TA, TA, TA, TA, TA,...
    ## $ BsmtExposure  <fct> No, Gd, Mn, No, Av, No, Av, Mn, No, No, No,...
    ## $ BsmtFinType1  <fct> GLQ, ALQ, GLQ, ALQ, GLQ, GLQ, GLQ, ALQ, Unf...
    ## $ BsmtFinSF1    <int> 706, 978, 486, 216, 655, 732, 1369, 859, 0,...
    ## $ BsmtFinType2  <fct> Unf, Unf, Unf, Unf, Unf, Unf, Unf, BLQ, Unf...
    ## $ BsmtFinSF2    <int> 0, 0, 0, 0, 0, 0, 0, 32, 0, 0, 0, 0, 0, 0, ...
    ## $ BsmtUnfSF     <int> 150, 284, 434, 540, 490, 64, 317, 216, 952,...
    ## $ TotalBsmtSF   <int> 856, 1262, 920, 756, 1145, 796, 1686, 1107,...
    ## $ Heating       <fct> GasA, GasA, GasA, GasA, GasA, GasA, GasA, G...
    ## $ HeatingQC     <fct> Ex, Ex, Ex, Gd, Ex, Ex, Ex, Ex, Gd, Ex, Ex,...
    ## $ CentralAir    <fct> Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y...
    ## $ Electrical    <fct> SBrkr, SBrkr, SBrkr, SBrkr, SBrkr, SBrkr, S...
    ## $ X1stFlrSF     <int> 856, 1262, 920, 961, 1145, 796, 1694, 1107,...
    ## $ X2ndFlrSF     <int> 854, 0, 866, 756, 1053, 566, 0, 983, 752, 0...
    ## $ LowQualFinSF  <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ GrLivArea     <int> 1710, 1262, 1786, 1717, 2198, 1362, 1694, 2...
    ## $ BsmtFullBath  <int> 1, 0, 1, 1, 1, 1, 1, 1, 0, 1, 1, 1, 1, 0, 1...
    ## $ BsmtHalfBath  <int> 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ FullBath      <int> 2, 2, 2, 1, 2, 1, 2, 2, 2, 1, 1, 3, 1, 2, 1...
    ## $ HalfBath      <int> 1, 0, 1, 0, 1, 1, 0, 1, 0, 0, 0, 0, 0, 0, 1...
    ## $ BedroomAbvGr  <int> 3, 3, 3, 3, 4, 1, 3, 3, 2, 2, 3, 4, 2, 3, 2...
    ## $ KitchenAbvGr  <int> 1, 1, 1, 1, 1, 1, 1, 1, 2, 2, 1, 1, 1, 1, 1...
    ## $ KitchenQual   <fct> Gd, TA, Gd, Gd, Gd, TA, Gd, TA, TA, TA, TA,...
    ## $ TotRmsAbvGrd  <int> 8, 6, 6, 7, 9, 5, 7, 7, 8, 5, 5, 11, 4, 7, ...
    ## $ Functional    <fct> Typ, Typ, Typ, Typ, Typ, Typ, Typ, Typ, Min...
    ## $ Fireplaces    <int> 0, 1, 1, 1, 1, 0, 1, 2, 2, 2, 0, 2, 0, 1, 1...
    ## $ FireplaceQu   <fct> NA, TA, TA, Gd, TA, NA, Gd, TA, TA, TA, NA,...
    ## $ GarageType    <fct> Attchd, Attchd, Attchd, Detchd, Attchd, Att...
    ## $ GarageYrBlt   <int> 2003, 1976, 2001, 1998, 2000, 1993, 2004, 1...
    ## $ GarageFinish  <fct> RFn, RFn, RFn, Unf, RFn, Unf, RFn, RFn, Unf...
    ## $ GarageCars    <int> 2, 2, 2, 3, 3, 2, 2, 2, 2, 1, 1, 3, 1, 3, 1...
    ## $ GarageArea    <int> 548, 460, 608, 642, 836, 480, 636, 484, 468...
    ## $ GarageQual    <fct> TA, TA, TA, TA, TA, TA, TA, TA, Fa, Gd, TA,...
    ## $ GarageCond    <fct> TA, TA, TA, TA, TA, TA, TA, TA, TA, TA, TA,...
    ## $ PavedDrive    <fct> Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y, Y...
    ## $ WoodDeckSF    <int> 0, 298, 0, 0, 192, 40, 255, 235, 90, 0, 0, ...
    ## $ OpenPorchSF   <int> 61, 0, 42, 35, 84, 30, 57, 204, 0, 4, 0, 21...
    ## $ EnclosedPorch <int> 0, 0, 0, 272, 0, 0, 0, 228, 205, 0, 0, 0, 0...
    ## $ X3SsnPorch    <int> 0, 0, 0, 0, 0, 320, 0, 0, 0, 0, 0, 0, 0, 0,...
    ## $ ScreenPorch   <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 176, 0,...
    ## $ PoolArea      <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ PoolQC        <fct> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,...
    ## $ Fence         <fct> NA, NA, NA, NA, NA, MnPrv, NA, NA, NA, NA, ...
    ## $ MiscFeature   <fct> NA, NA, NA, NA, NA, Shed, NA, Shed, NA, NA,...
    ## $ MiscVal       <int> 0, 0, 0, 0, 0, 700, 0, 350, 0, 0, 0, 0, 0, ...
    ## $ MoSold        <int> 2, 5, 9, 2, 12, 10, 8, 11, 4, 1, 2, 7, 9, 8...
    ## $ YrSold        <int> 2008, 2007, 2008, 2006, 2008, 2009, 2007, 2...
    ## $ SaleType      <fct> WD, WD, WD, WD, WD, WD, WD, WD, WD, WD, WD,...
    ## $ SaleCondition <fct> Normal, Normal, Normal, Abnorml, Normal, No...
    ## $ SalePrice     <int> 208500, 181500, 223500, 140000, 250000, 143...

Khusus yang menggunakan R versi 4.00 keatas, argumen
`stringsAsFactors = TRUE` disertakan agar data yang berbentuk string
bisa berubah menjadi factor.

Dalam Tutorial ini, kita hanya akan menggunakan predictor numerik
terlebih dahulu.

``` r
data_house <- data_house %>% 
  select(-Id)%>% 
  select_if(is.numeric)
```

Data Exploration
----------------

1.  Memeriksa Gambaran Umum Data

``` r
plot_intro(data = data_house,
           geom_label_args = list(size=2.5))
```

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-113-1.png)
Catatan:

-   `plot_intro` merupakan fungsi yang berasal dari package
    `DataExplorer` dan argumen utamanya adalah object berbentuk
    `data.frame`.
-   argumen `geom_label_args` bisa diisi dengan opsi-opsi yang ada pada
    fungsi `geom_label` pada pacakge `ggplot2`.

Berdasarkan grafik diatas kita tahu bahwa semua kolom kita
teridentifikasi sebagai kolom peubah kontinu. Kemudian, data kita
menngandung missing value sebanyak 0.65% secara keseluruhan. Selanjutnya
ada sebesar 75.78% baris yang tidak memuat missing value sama sekali.
Hal ini bisa jadi dasar pertimbangan bagaimana cara kita menangani
missing value.

``` r
skim_without_charts(data = data_house)
```

|                                                  |             |
|:-------------------------------------------------|:------------|
| Name                                             | data\_house |
| Number of rows                                   | 1460        |
| Number of columns                                | 37          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |             |
| Column type frequency:                           |             |
| numeric                                          | 37          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |             |
| Group variables                                  | None        |

**Variable type: numeric**

| skim\_variable |  n\_missing|  complete\_rate|       mean|        sd|     p0|        p25|       p50|        p75|    p100|
|:---------------|-----------:|---------------:|----------:|---------:|------:|----------:|---------:|----------:|-------:|
| MSSubClass     |           0|            1.00|      56.90|     42.30|     20|      20.00|      50.0|      70.00|     190|
| LotFrontage    |         259|            0.82|      70.05|     24.28|     21|      59.00|      69.0|      80.00|     313|
| LotArea        |           0|            1.00|   10516.83|   9981.26|   1300|    7553.50|    9478.5|   11601.50|  215245|
| OverallQual    |           0|            1.00|       6.10|      1.38|      1|       5.00|       6.0|       7.00|      10|
| OverallCond    |           0|            1.00|       5.58|      1.11|      1|       5.00|       5.0|       6.00|       9|
| YearBuilt      |           0|            1.00|    1971.27|     30.20|   1872|    1954.00|    1973.0|    2000.00|    2010|
| YearRemodAdd   |           0|            1.00|    1984.87|     20.65|   1950|    1967.00|    1994.0|    2004.00|    2010|
| MasVnrArea     |           8|            0.99|     103.69|    181.07|      0|       0.00|       0.0|     166.00|    1600|
| BsmtFinSF1     |           0|            1.00|     443.64|    456.10|      0|       0.00|     383.5|     712.25|    5644|
| BsmtFinSF2     |           0|            1.00|      46.55|    161.32|      0|       0.00|       0.0|       0.00|    1474|
| BsmtUnfSF      |           0|            1.00|     567.24|    441.87|      0|     223.00|     477.5|     808.00|    2336|
| TotalBsmtSF    |           0|            1.00|    1057.43|    438.71|      0|     795.75|     991.5|    1298.25|    6110|
| X1stFlrSF      |           0|            1.00|    1162.63|    386.59|    334|     882.00|    1087.0|    1391.25|    4692|
| X2ndFlrSF      |           0|            1.00|     346.99|    436.53|      0|       0.00|       0.0|     728.00|    2065|
| LowQualFinSF   |           0|            1.00|       5.84|     48.62|      0|       0.00|       0.0|       0.00|     572|
| GrLivArea      |           0|            1.00|    1515.46|    525.48|    334|    1129.50|    1464.0|    1776.75|    5642|
| BsmtFullBath   |           0|            1.00|       0.43|      0.52|      0|       0.00|       0.0|       1.00|       3|
| BsmtHalfBath   |           0|            1.00|       0.06|      0.24|      0|       0.00|       0.0|       0.00|       2|
| FullBath       |           0|            1.00|       1.57|      0.55|      0|       1.00|       2.0|       2.00|       3|
| HalfBath       |           0|            1.00|       0.38|      0.50|      0|       0.00|       0.0|       1.00|       2|
| BedroomAbvGr   |           0|            1.00|       2.87|      0.82|      0|       2.00|       3.0|       3.00|       8|
| KitchenAbvGr   |           0|            1.00|       1.05|      0.22|      0|       1.00|       1.0|       1.00|       3|
| TotRmsAbvGrd   |           0|            1.00|       6.52|      1.63|      2|       5.00|       6.0|       7.00|      14|
| Fireplaces     |           0|            1.00|       0.61|      0.64|      0|       0.00|       1.0|       1.00|       3|
| GarageYrBlt    |          81|            0.94|    1978.51|     24.69|   1900|    1961.00|    1980.0|    2002.00|    2010|
| GarageCars     |           0|            1.00|       1.77|      0.75|      0|       1.00|       2.0|       2.00|       4|
| GarageArea     |           0|            1.00|     472.98|    213.80|      0|     334.50|     480.0|     576.00|    1418|
| WoodDeckSF     |           0|            1.00|      94.24|    125.34|      0|       0.00|       0.0|     168.00|     857|
| OpenPorchSF    |           0|            1.00|      46.66|     66.26|      0|       0.00|      25.0|      68.00|     547|
| EnclosedPorch  |           0|            1.00|      21.95|     61.12|      0|       0.00|       0.0|       0.00|     552|
| X3SsnPorch     |           0|            1.00|       3.41|     29.32|      0|       0.00|       0.0|       0.00|     508|
| ScreenPorch    |           0|            1.00|      15.06|     55.76|      0|       0.00|       0.0|       0.00|     480|
| PoolArea       |           0|            1.00|       2.76|     40.18|      0|       0.00|       0.0|       0.00|     738|
| MiscVal        |           0|            1.00|      43.49|    496.12|      0|       0.00|       0.0|       0.00|   15500|
| MoSold         |           0|            1.00|       6.32|      2.70|      1|       5.00|       6.0|       8.00|      12|
| YrSold         |           0|            1.00|    2007.82|      1.33|   2006|    2007.00|    2008.0|    2009.00|    2010|
| SalePrice      |           0|            1.00|  180921.20|  79442.50|  34900|  129975.00|  163000.0|  214000.00|  755000|

Catatan:

-   `skim_without_charts` merupakan fungsi yang berasal dari package
    `skimr` dan argumen utamanya adalah object berbentuk `data.frame`.

Berdasarkan informasi diatas, kita tahu bahwa missing data hanya terjadi
di 3 kolom saja yaitu LotFrontage, MasVnrArea dan GarageYrblt.

1.  Menangani Missing Value

Missing Value akan ditangani dengan menghapus baris-baris yang
mengandung missing value.

``` r
data_house1 <- data_house %>% na.omit
```

Data yang kita peroleh observasinya akan berkurang sebesar 23.22%.

1.  Memeriksa Sebaran Data

``` r
plot_histogram(data = data_house1,nrow=3,ncol = 3,
               geom_histogram_args = list(fill="steelblue")
               )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-116-1.png)

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-116-2.png)

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-116-3.png)

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-116-4.png)

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-116-5.png)

1.  Memeriksa Korelasi Peubah

``` r
plot_scatterplot(data = data_house1,by="SalePrice",geom_point_args = list(color="steelblue") )
```

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-117-1.png)![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-117-2.png)![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-117-3.png)![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-117-4.png)

``` r
cor_mat <- cor(data_house1,method = "spearman")
cor_mat[upper.tri(cor_mat,diag = TRUE)] <- NA 
cor_df <- cor_mat   %>%
    as.data.frame() %>% 
    rownames_to_column(var = "Var1") %>%
  pivot_longer(names_to = "Var2",
               values_to = "corr",
               -Var1) %>% na.omit

cor_df %>% filter(abs(corr)>0.6) %>% arrange(desc(abs(corr)))
```

    ## # A tibble: 28 x 3
    ##    Var1         Var2          corr
    ##    <chr>        <chr>        <dbl>
    ##  1 GarageYrBlt  YearBuilt    0.893
    ##  2 X1stFlrSF    TotalBsmtSF  0.840
    ##  3 GarageArea   GarageCars   0.839
    ##  4 TotRmsAbvGrd GrLivArea    0.828
    ##  5 SalePrice    OverallQual  0.827
    ##  6 GarageYrBlt  YearRemodAdd 0.741
    ##  7 YearRemodAdd YearBuilt    0.731
    ##  8 SalePrice    GrLivArea    0.725
    ##  9 BsmtFullBath BsmtFinSF1   0.674
    ## 10 SalePrice    YearBuilt    0.670
    ## # ... with 18 more rows

``` r
cor_df %>% filter(abs(corr)<=0.6)  
```

    ## # A tibble: 638 x 3
    ##    Var1        Var2            corr
    ##    <chr>       <chr>          <dbl>
    ##  1 LotFrontage MSSubClass  -0.313  
    ##  2 LotArea     MSSubClass  -0.258  
    ##  3 OverallQual MSSubClass   0.0920 
    ##  4 OverallQual LotFrontage  0.240  
    ##  5 OverallQual LotArea      0.279  
    ##  6 OverallCond MSSubClass  -0.0854 
    ##  7 OverallCond LotFrontage -0.0691 
    ##  8 OverallCond LotArea     -0.0883 
    ##  9 OverallCond OverallQual -0.235  
    ## 10 YearBuilt   MSSubClass   0.00361
    ## # ... with 628 more rows

Seleksi Peubah
--------------

1.  Regresi Linear

``` r
regresi1 <- lm(formula = SalePrice~.,data = data_house1)
summary(regresi1)
```

    ## 
    ## Call:
    ## lm(formula = SalePrice ~ ., data = data_house1)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -442865  -16873   -2581   14998  318042 
    ## 
    ## Coefficients: (2 not defined because of singularities)
    ##                 Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   -3.232e+05  1.701e+06  -0.190 0.849317    
    ## MSSubClass    -2.005e+02  3.449e+01  -5.814 8.03e-09 ***
    ## LotFrontage   -1.161e+02  6.124e+01  -1.896 0.058203 .  
    ## LotArea        5.454e-01  1.573e-01   3.466 0.000548 ***
    ## OverallQual    1.870e+04  1.478e+03  12.646  < 2e-16 ***
    ## OverallCond    5.227e+03  1.367e+03   3.824 0.000139 ***
    ## YearBuilt      3.170e+02  8.762e+01   3.617 0.000311 ***
    ## YearRemodAdd   1.206e+02  8.661e+01   1.392 0.164174    
    ## MasVnrArea     3.160e+01  7.006e+00   4.511 7.15e-06 ***
    ## BsmtFinSF1     1.739e+01  5.835e+00   2.980 0.002947 ** 
    ## BsmtFinSF2     8.362e+00  8.763e+00   0.954 0.340205    
    ## BsmtUnfSF      5.006e+00  5.275e+00   0.949 0.342890    
    ## TotalBsmtSF           NA         NA      NA       NA    
    ## X1stFlrSF      4.591e+01  7.356e+00   6.241 6.21e-10 ***
    ## X2ndFlrSF      4.668e+01  6.099e+00   7.654 4.28e-14 ***
    ## LowQualFinSF   3.415e+01  2.788e+01   1.225 0.220788    
    ## GrLivArea             NA         NA      NA       NA    
    ## BsmtFullBath   8.980e+03  3.194e+03   2.812 0.005018 ** 
    ## BsmtHalfBath   2.490e+03  5.071e+03   0.491 0.623487    
    ## FullBath       5.390e+03  3.529e+03   1.527 0.126941    
    ## HalfBath      -1.119e+03  3.320e+03  -0.337 0.736244    
    ## BedroomAbvGr  -1.023e+04  2.154e+03  -4.750 2.30e-06 ***
    ## KitchenAbvGr  -2.193e+04  6.704e+03  -3.271 0.001105 ** 
    ## TotRmsAbvGrd   5.440e+03  1.486e+03   3.661 0.000263 ***
    ## Fireplaces     4.375e+03  2.188e+03   2.000 0.045793 *  
    ## GarageYrBlt   -4.914e+01  9.093e+01  -0.540 0.589011    
    ## GarageCars     1.679e+04  3.487e+03   4.815 1.68e-06 ***
    ## GarageArea     6.488e+00  1.211e+01   0.536 0.592338    
    ## WoodDeckSF     2.155e+01  1.002e+01   2.151 0.031713 *  
    ## OpenPorchSF   -2.315e+00  1.948e+01  -0.119 0.905404    
    ## EnclosedPorch  7.233e+00  2.061e+01   0.351 0.725733    
    ## X3SsnPorch     3.458e+01  3.749e+01   0.922 0.356593    
    ## ScreenPorch    5.797e+01  2.040e+01   2.842 0.004572 ** 
    ## PoolArea      -6.126e+01  2.984e+01  -2.053 0.040326 *  
    ## MiscVal       -3.850e+00  6.955e+00  -0.554 0.579980    
    ## MoSold        -2.240e+02  4.227e+02  -0.530 0.596213    
    ## YrSold        -2.536e+02  8.454e+02  -0.300 0.764216    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 36790 on 1086 degrees of freedom
    ## Multiple R-squared:  0.8095, Adjusted R-squared:  0.8036 
    ## F-statistic: 135.7 on 34 and 1086 DF,  p-value: < 2.2e-16

1.  Best Subset

``` r
best_subset <- regsubsets(SalePrice~.,data = data_house1,method = "exhaustive",nvmax = 36)
```

    ## Warning in leaps.setup(x, y, wt = wt, nbest = nbest, nvmax = nvmax,
    ## force.in = force.in, : 2 linear dependencies found

    ## Reordering variables and trying again:

``` r
summ_subset <- summary(best_subset)
data.frame(
  Adj.R2 = c(which.max(summ_subset$adjr2),max(summ_subset$adjr2)),
  CP = c(which.min(summ_subset$cp),min(summ_subset$cp)),
  BIC = c(which.min(summ_subset$bic),min(summ_subset$bic))
)
```

    ##       Adj.R2        CP       BIC
    ## 1 21.0000000 20.000000    14.000
    ## 2  0.8053568  9.639685 -1724.191

``` r
coef(best_subset,14)
```

    ##   (Intercept)    MSSubClass       LotArea   OverallQual   OverallCond 
    ## -9.647855e+05 -1.926758e+02  7.884685e-01  2.754663e+04  5.053679e+03 
    ##     YearBuilt    MasVnrArea    BsmtFinSF1  BsmtHalfBath      FullBath 
    ##  1.550663e+02  4.631951e+01  2.629517e+01 -2.515710e+03  1.204446e+04 
    ##  TotRmsAbvGrd    Fireplaces   GarageYrBlt    WoodDeckSF       MiscVal 
    ##  9.772038e+03  1.019163e+04  2.726877e+02  3.069779e+01 -5.786461e+00

``` r
plot_subset <- data.frame(subset=seq_along(summ_subset$bic),
                           BIC = summ_subset$bic
                          )
```

``` r
ggplot(plot_subset,aes(subset,BIC))+
  geom_line(size=1)+
  geom_point(color="red",size=2)+
  theme_bw()
```

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-123-1.png)

1.  Forward Selection

``` r
best_forward <- regsubsets(SalePrice~.,data = data_house1,method = "forward",nvmax = 36)
```

    ## Warning in leaps.setup(x, y, wt = wt, nbest = nbest, nvmax = nvmax,
    ## force.in = force.in, : 2 linear dependencies found

    ## Reordering variables and trying again:

    ## Warning in rval$lopt[] <- rval$vorder[rval$lopt]: number of items to
    ## replace is not a multiple of replacement length

``` r
summ_forward <- summary(best_forward)
data.frame(
  Adj.R2 = c(which.max(summ_forward$adjr2),max(summ_forward$adjr2)),
  CP = c(which.min(summ_forward$cp),min(summ_forward$cp)),
  BIC = c(which.min(summ_forward$bic),min(summ_forward$bic))
)
```

    ##       Adj.R2        CP       BIC
    ## 1 21.0000000 21.000000    15.000
    ## 2  0.8053568  9.921363 -1719.271

``` r
coef(best_forward,15)
```

    ##   (Intercept)    MSSubClass       LotArea   OverallQual   OverallCond 
    ## -1.280925e+06 -1.904318e+02  7.969132e-01  2.640574e+04  2.792115e+03 
    ##     YearBuilt  YearRemodAdd    MasVnrArea    BsmtFinSF1  BsmtHalfBath 
    ##  7.631146e+01  3.326844e+02  4.867384e+01  2.678033e+01 -2.634423e+03 
    ##      FullBath  TotRmsAbvGrd    Fireplaces   GarageYrBlt    WoodDeckSF 
    ##  1.055430e+04  9.827926e+03  1.048794e+04  1.876492e+02  2.944775e+01 
    ##       MiscVal 
    ## -5.128721e+00

``` r
plot_forward <- data.frame(subset=seq_along(summ_forward$bic),
                           BIC = summ_forward$bic
                          )
```

``` r
ggplot(plot_forward,aes(subset,BIC))+
  geom_line(size=1)+
  geom_point(color="red",size=2)+
  theme_bw()
```

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-127-1.png)

1.  Backward Selection

``` r
best_backward <- regsubsets(SalePrice~.,data = data_house1,method = "backward",nvmax = 36)
```

    ## Warning in leaps.setup(x, y, wt = wt, nbest = nbest, nvmax = nvmax,
    ## force.in = force.in, : 2 linear dependencies found

    ## Reordering variables and trying again:

    ## Warning in rval$lopt[] <- rval$vorder[rval$lopt]: number of items to
    ## replace is not a multiple of replacement length

``` r
summ_backward <- summary(best_backward)
data.frame(
  Adj.R2 = c(which.max(summ_backward$adjr2),max(summ_backward$adjr2)),
  CP = c(which.min(summ_backward$cp),min(summ_backward$cp)),
  BIC = c(which.min(summ_backward$bic),min(summ_backward$bic))
)
```

    ##       Adj.R2       CP       BIC
    ## 1 22.0000000 20.00000    15.000
    ## 2  0.8050191 11.95807 -1718.128

``` r
coef(best_backward,15)
```

    ##   (Intercept)    MSSubClass       LotArea   OverallQual   OverallCond 
    ## -1.009408e+06 -2.311797e+02  7.837025e-01  2.727737e+04  4.711214e+03 
    ##     YearBuilt    MasVnrArea    BsmtFinSF1     X2ndFlrSF  LowQualFinSF 
    ##  1.872403e+02  4.560010e+01  2.806163e+01  1.291378e+01  2.274362e+01 
    ##      FullBath  TotRmsAbvGrd    Fireplaces   GarageYrBlt    WoodDeckSF 
    ##  1.089197e+04  7.843221e+03  1.003158e+04  2.707822e+02  2.889695e+01 
    ##       MiscVal 
    ## -6.115813e+00

``` r
plot_backward <- data.frame(subset=seq_along(summ_backward$bic),
                           BIC = summ_backward$bic
                          )
```

``` r
ggplot(plot_backward,aes(subset,BIC))+
  geom_line(size=1)+
  geom_point(color="red",size=2)+
  theme_bw()
```

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Regresi-Linear-dan-Seleksi-Peubah_files/figure-markdown_github/unnamed-chunk-131-1.png)
