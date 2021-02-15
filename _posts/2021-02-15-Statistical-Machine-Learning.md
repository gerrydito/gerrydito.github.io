---
layout: post
title:  Supervised Regression dengan mlr3
categories: [Machine Learning,Supervised,mlr3]
---
Package
=======

Silahkan install jika belum ada

``` r
install.packages("tidyverse")
install.packages("mlr3verse")
install.packages("kknn")
install.packages("e1071")
install.packages("ranger")
install.packages("rpart.plot")
```

Memanggil Package
-----------------

``` r
library(tidyverse)
library(mlr3verse)
```

Deskripsi singkat data
======================

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

Statistical Learning di R
=========================

Di R ada beberapa ekosistem yang bisa digunakan untuk menerapkan
statistical learning atau machine learning, yang paling terkenal adalah
ekosistem `caret` dan juga `mlr`. Jika ingin mempelajari ekosistem
`caret` secara lebih lengkap bisa mengakses link berikut
<a href="https://topepo.github.io/caret/" class="uri">https://topepo.github.io/caret/</a>.
Pada tutorial kali ini kita akan menggunakan ekosistem `mlr` (atau
sekarang berubah nama menjadi `mlr3`). Jika tertarik belajar lebih
lanjut tentang ekosistem ini bisa mengakses link-link berikut:

1.  <a href="https://mlr3.mlr-org.com/" class="uri">https://mlr3.mlr-org.com/</a>
2.  <a href="https://mlr3book.mlr-org.com/" class="uri">https://mlr3book.mlr-org.com/</a>
3.  <a href="https://mlr3gallery.mlr-org.com/" class="uri">https://mlr3gallery.mlr-org.com/</a>
4.  <a href="https://github.com/mlr-org/mlr3/wiki/Extension-Packages" class="uri">https://github.com/mlr-org/mlr3/wiki/Extension-Packages</a>

Proses pemodelan (learning) menggunakan ekosistem mlr3:

1.  Import data di R
2.  Import data ke ekosistem mlr3
3.  Menentukan model yang digunakan
4.  Menentukan cara pembagian data
5.  Melakukan interpretasi model (jika diperlukan)
6.  Melakukan training dan menghitung performa model/ Komparasi model
7.  Memprediksi respon pada data baru (jika tersedia)

Import data di R
----------------

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

``` r
data_house <- data_house %>% 
  select(SalePrice,LotArea,
         LotFrontage,MSSubClass,YrSold) %>% na.omit
```

Import data ke ekosistem mlr3
-----------------------------

Import data ke mlr3 bisa dilakukan dengan menggunakan fungsi
`TaskClassif$new` atau `TaskRegr$new` yang berasal dari package `mlr3`.
`TaskClassif$new` digunakan jika peubah respon kita berupa peubah biner
atau multiclass, sedangkan `TaskRegr$new` digunakan jika responya berupa
peubah numerik.

``` r
task_house = TaskRegr$new(id="house",backend = data_house,
                                target = "SalePrice")
```

Argumen utama dalam fungsi `TaskRegr$new` adalah sebagai berikut:

1.  `id` yang merupakan nama dari task (bisa diisi dengan nama apapun)
2.  `backend` adalah data yang ingin dimodelkan dengan catatan peubah
    respon-nya harus berupa **factor**
3.  `target` adalah nama kolom yang dijadikan peubah respon

Menentukan model yang digunakan
-------------------------------

Pada tahap ini fungsi yang digunakan adalah `lrn` yang memiliki argumen
utama **nama model** yang ingin digunakan. Berikut adalah model-model
yang akan digunakan beserta argumen di dalam fungsi `lrn` dan asal
packagenya:

1.  Regresi Linear - `"regr.lm"`
2.  Regresi Lasso - `"regr.cv_glmnet"` - `library(glmnet)`
3.  Decision Tree - `"regr.rpart"` - `library(rpart)`
4.  Random Forest - `"regr.ranger"` - `library(ranger)`
5.  Gradient Boosting - `"regr.xgboost"` - `library(xgboost)`

Sebagai catatan, untuk model-model yang digunakan dalam `mlr3` berasal
dari package-package lain sehingga package-package tersebut perlu
install terlebih dahulu. Kemudian, untuk model klasifikasi (respon biner
atau multiclass) selalu diawali dengan kata `"classif."`. Sedangkan
model regresi(respon numerik) diawali dengan kata `regr`. Selain itu,
fungsi `lrn` juga memungkinkan untuk memasukan argumen-argumen dari
package asalnya (termasuk hiperparameter). Sebagai contoh model KNN dari
package `cv_glmnet` memiliki argumen-argumen yang bisa dilihat dengan
menggunakan

``` r
as.data.table(lrn("regr.cv_glmnet")$param_set)
```

    ##                   id    class lower upper                     levels
    ##  1:           family ParamFct    NA    NA           gaussian,poisson
    ##  2:           offset ParamUty    NA    NA                           
    ##  3:            alpha ParamDbl     0     1                           
    ##  4:           nfolds ParamInt     3   Inf                           
    ##  5:     type.measure ParamFct    NA    NA deviance,class,auc,mse,mae
    ##  6:                s ParamDbl     0   Inf                           
    ##  7: lambda.min.ratio ParamDbl     0     1                           
    ##  8:           lambda ParamUty    NA    NA                           
    ##  9:      standardize ParamLgl    NA    NA                 TRUE,FALSE
    ## 10:        intercept ParamLgl    NA    NA                 TRUE,FALSE
    ## 11:           thresh ParamDbl     0   Inf                           
    ## 12:            dfmax ParamInt     0   Inf                           
    ## 13:             pmax ParamInt     0   Inf                           
    ## 14:          exclude ParamInt     1   Inf                           
    ## 15:   penalty.factor ParamUty    NA    NA                           
    ## 16:     lower.limits ParamUty    NA    NA                           
    ## 17:     upper.limits ParamUty    NA    NA                           
    ## 18:            maxit ParamInt     1   Inf                           
    ## 19:    type.gaussian ParamFct    NA    NA           covariance,naive
    ## 20:    type.logistic ParamFct    NA    NA     Newton,modified.Newton
    ## 21: type.multinomial ParamFct    NA    NA          ungrouped,grouped
    ## 22:             keep ParamLgl    NA    NA                 TRUE,FALSE
    ## 23:         parallel ParamLgl    NA    NA                 TRUE,FALSE
    ## 24:         trace.it ParamInt     0     1                           
    ## 25:           foldid ParamUty    NA    NA                           
    ## 26:        alignment ParamFct    NA    NA            lambda,fraction
    ## 27:          grouped ParamLgl    NA    NA                 TRUE,FALSE
    ## 28:            gamma ParamUty    NA    NA                           
    ## 29:            relax ParamLgl    NA    NA                 TRUE,FALSE
    ## 30:             fdev ParamDbl     0     1                           
    ## 31:           devmax ParamDbl     0     1                           
    ## 32:              eps ParamDbl     0     1                           
    ## 33:            epsnr ParamDbl     0     1                           
    ## 34:              big ParamDbl  -Inf   Inf                           
    ## 35:            mnlam ParamInt     1   Inf                           
    ## 36:             pmin ParamDbl     0     1                           
    ## 37:             exmx ParamDbl  -Inf   Inf                           
    ## 38:             prec ParamDbl  -Inf   Inf                           
    ## 39:             mxit ParamInt     1   Inf                           
    ## 40:           mxitnr ParamInt     1   Inf                           
    ## 41:        newoffset ParamUty    NA    NA                           
    ## 42:    predict.gamma ParamDbl  -Inf   Inf                           
    ##                   id    class lower upper                     levels
    ##     nlevels is_bounded special_vals        default storage_type
    ##  1:       2       TRUE    <list[0]>       gaussian    character
    ##  2:     Inf      FALSE    <list[0]>                        list
    ##  3:     Inf       TRUE    <list[0]>              1      numeric
    ##  4:     Inf      FALSE    <list[0]>             10      integer
    ##  5:       5       TRUE    <list[0]>       deviance    character
    ##  6:     Inf      FALSE    <list[2]>     lambda.1se      numeric
    ##  7:     Inf       TRUE    <list[0]> <NoDefault[3]>      numeric
    ##  8:     Inf      FALSE    <list[0]> <NoDefault[3]>         list
    ##  9:       2       TRUE    <list[0]>           TRUE      logical
    ## 10:       2       TRUE    <list[0]>           TRUE      logical
    ## 11:     Inf      FALSE    <list[0]>          1e-07      numeric
    ## 12:     Inf      FALSE    <list[0]> <NoDefault[3]>      integer
    ## 13:     Inf      FALSE    <list[0]> <NoDefault[3]>      integer
    ## 14:     Inf      FALSE    <list[0]> <NoDefault[3]>      integer
    ## 15:     Inf      FALSE    <list[0]> <NoDefault[3]>         list
    ## 16:     Inf      FALSE    <list[0]> <NoDefault[3]>         list
    ## 17:     Inf      FALSE    <list[0]> <NoDefault[3]>         list
    ## 18:     Inf      FALSE    <list[0]>         100000      integer
    ## 19:       2       TRUE    <list[0]> <NoDefault[3]>    character
    ## 20:       2       TRUE    <list[0]> <NoDefault[3]>    character
    ## 21:       2       TRUE    <list[0]> <NoDefault[3]>    character
    ## 22:       2       TRUE    <list[0]>          FALSE      logical
    ## 23:       2       TRUE    <list[0]>          FALSE      logical
    ## 24:       2       TRUE    <list[0]>              0      integer
    ## 25:     Inf      FALSE    <list[0]>                        list
    ## 26:       2       TRUE    <list[0]>         lambda    character
    ## 27:       2       TRUE    <list[0]>           TRUE      logical
    ## 28:     Inf      FALSE    <list[0]> <NoDefault[3]>         list
    ## 29:       2       TRUE    <list[0]>          FALSE      logical
    ## 30:     Inf       TRUE    <list[0]>          1e-05      numeric
    ## 31:     Inf       TRUE    <list[0]>          0.999      numeric
    ## 32:     Inf       TRUE    <list[0]>          1e-06      numeric
    ## 33:     Inf       TRUE    <list[0]>          1e-08      numeric
    ## 34:     Inf      FALSE    <list[0]>        9.9e+35      numeric
    ## 35:     Inf      FALSE    <list[0]>              5      integer
    ## 36:     Inf       TRUE    <list[0]>          1e-09      numeric
    ## 37:     Inf      FALSE    <list[0]>            250      numeric
    ## 38:     Inf      FALSE    <list[0]>          1e-10      numeric
    ## 39:     Inf      FALSE    <list[0]>            100      integer
    ## 40:     Inf      FALSE    <list[0]>             25      integer
    ## 41:     Inf      FALSE    <list[0]> <NoDefault[3]>         list
    ## 42:     Inf      FALSE    <list[0]>              1      numeric
    ##     nlevels is_bounded special_vals        default storage_type
    ##        tags
    ##  1:   train
    ##  2:   train
    ##  3:   train
    ##  4:   train
    ##  5:   train
    ##  6: predict
    ##  7:   train
    ##  8:   train
    ##  9:   train
    ## 10:   train
    ## 11:   train
    ## 12:   train
    ## 13:   train
    ## 14:   train
    ## 15:   train
    ## 16:   train
    ## 17:   train
    ## 18:   train
    ## 19:   train
    ## 20:   train
    ## 21:   train
    ## 22:   train
    ## 23:   train
    ## 24:   train
    ## 25:   train
    ## 26:   train
    ## 27:   train
    ## 28:   train
    ## 29:   train
    ## 30:   train
    ## 31:   train
    ## 32:   train
    ## 33:   train
    ## 34:   train
    ## 35:   train
    ## 36:   train
    ## 37:   train
    ## 38:   train
    ## 39:   train
    ## 40:   train
    ## 41: predict
    ## 42: predict
    ##        tags

Berdasarkan output diatas argumen-argumen yang bisa digunakan dalam
`regr.cv_glmnet` ada di kolom id. Selanjutnya, kolom class menunjukkan
tipe data argumen tersebut. Kolom lower, upper dan levels merupakan
isi/nilai dari argumen tersebut. Misalnya saja argumen k itu tipe
datanya Interger dan nilai yang paling kecil bisa mengisi minimal 1.

Jika ingin mengetahui model-model apa saja yang sudah bisa dijalankan di
ekosistem `mlr3` bisa dilihat pada link berikut:

1.  <a href="https://mlr3learners.mlr-org.com/" class="uri">https://mlr3learners.mlr-org.com/</a>
2.  <a href="https://mlr3extralearners.mlr-org.com/articles/learners/list_learners.html" class="uri">https://mlr3extralearners.mlr-org.com/articles/learners/list_learners.html</a>

Untuk menjalankan model-model tersebut kita bisa tulis seperti dibawah
ini

``` r
regresi_linear <- lrn("regr.lm")
regresi_lasso <- lrn("regr.cv_glmnet",alpha=1)
pohon_regresi <- lrn("regr.rpart")
gradient_boosting <- lrn("regr.xgboost")
random_forest <- lrn("regr.ranger",importance="impurity")
```

Menentukan cara pembagian data
------------------------------

Penentuan cara pembagian data bisa dilakukan dengan fungsi `rsmp`.
Adapun pembagian data yang bisa digunakan dalam package `mlr3` adalah
sebagai berikut

``` r
as.data.table(mlr_resamplings)
```

    ##            key        params iters
    ## 1:   bootstrap repeats,ratio    30
    ## 2:      custom                   0
    ## 3:          cv         folds    10
    ## 4:     holdout         ratio     1
    ## 5:    insample                   1
    ## 6:         loo                  NA
    ## 7: repeated_cv repeats,folds   100
    ## 8: subsampling repeats,ratio    30

Pada kolom key adalah nama-nama dari tipe-tipe pembagian data.
Penjelasan untuk masing-masing pembagian data tersebut dapat di cari di
internet. Pada tutorial ini kita membagi data menjadi dua bagian yaitu
data training dan data testing dengan proporsi data training sebesar 0.8
dari data dan data testing sebesar 0.2. Pembagian ini bisa dilakukan
dengan menggunakan menggunakan menggunakan pembagian data `"holdout"`
dan proporsi tadi bisa dipenuhi dengan menambahkan argumen `ratio=0.8`.

``` r
resample_holdout = rsmp("holdout", ratio = 0.8)
```

Pembagian data ini dimaksudkan untuk mengevaluasi kemampuan prediksi
model untuk data baru.

### Melakukan interpretasi model (jika diperlukan)

Tahap ini biasanya dilakukan untuk melihat bagaimana pengaruh
peubah-peubah prediktor terhadap respon menurut masing-masing model.
Misalnya saja dalam regresi logistik besarnya nilai koefisien dan p
value bisa menggambarkan bagaimana pengaruh peubah prediktor terhadap
respon. Model-model yang akan digunakan untuk melihat pengaruh tersebut
adalah regresi linear, Regression tree dan Random Forest. Berikut adalah
sintaksnya

``` r
# Regresi Linear
regresi_linear$train(task = task_house)
summary(regresi_linear$model)
```

    ## 
    ## Call:
    ## stats::lm(formula = task$formula(), data = task$data())
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -373288  -46598  -18389   31847  515175 
    ## 
    ## Coefficients:
    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  2.661e+06  3.339e+06   0.797    0.426    
    ## LotArea      2.098e+00  3.089e-01   6.791 1.75e-11 ***
    ## LotFrontage  9.852e+02  1.070e+02   9.204  < 2e-16 ***
    ## MSSubClass   9.960e+01  5.569e+01   1.788    0.074 .  
    ## YrSold      -1.283e+03  1.663e+03  -0.772    0.441    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 76630 on 1196 degrees of freedom
    ## Multiple R-squared:  0.1583, Adjusted R-squared:  0.1555 
    ## F-statistic: 56.24 on 4 and 1196 DF,  p-value: < 2.2e-16

``` r
# Regression Tree
pohon_regresi$train(task = task_house)
rpart.plot::rpart.plot(pohon_regresi$model,roundint = FALSE,type = 5,tweak = 1.5)
```

![](Statistical-Machine-Learning_files/figure-markdown_github/unnamed-chunk-10-1.png)

``` r
# Random Forest
random_forest$train(task = task_house)
random_forest$model$variable.importance
```

    ##      LotArea  LotFrontage   MSSubClass       YrSold 
    ## 3.416528e+12 2.348911e+12 1.255153e+12 4.880621e+11

Catatan:

1.  Data yang digunakan untuk menjalankan model-model tanpa pembagian
    data (training dan testing)
2.  `rpart.plot` berasal dari package `rpart.plot`.
3.  Argumen `type` dalam `rpart.plot` digunakan untuk menentukan
    bagimana pohon di gambarkan. Argumen `tweak` digunakan untuk
    memperbesar gambar. Lihat help untuk lebih lengkapnya.

Dibawah ini merupakan sintaks untuk mengubah output variable importance
ke dalam `data.frame` agar mudah untuk diurutkan dan di buat grafiknya.

``` r
importance <- data.frame(Predictors = names(random_forest$model$variable.importance),
                         impurity = random_forest$model$variable.importance
                         )
rownames(importance) <- NULL

importance %>% arrange(desc(impurity))
```

    ##    Predictors     impurity
    ## 1     LotArea 3.416528e+12
    ## 2 LotFrontage 2.348911e+12
    ## 3  MSSubClass 1.255153e+12
    ## 4      YrSold 4.880621e+11

Melakukan training dan menghitung performa model
------------------------------------------------

Pada tahap ini kita bisa menerapkan model yang sudah kita definisikan
diawal pada data training dan kemudian mengevaluasi kemampuan prediksi
dengan data testing. Hal tersebut bisa dilakukan dengan menggunakan
fungsi `resample`.

``` r
train_test = resample(task = task_house,
                               learner = regresi_linear,
                               resampling = resample_holdout,
                               store_models = TRUE
                               )
```

    ## INFO  [12:45:58.909] Applying learner 'regr.lm' on task 'house' (iter 1/1)

Berdasarkan sintaks diatas kita melakukan training untuk model regresi
linear, jika ingin melakukan training untuk model lainnya cukup ganti
`learner=regresi_linear` dengan
`regresi_lasso`,`pohon_regresi`,`random_forest` dan `gradient_boosting`.

Jika kita ingin mengeluarkan hasil prediksi pada data testing bisa
menggunakan sintaks dibawah ini.

``` r
prediksi_test = as.data.table(train_test$prediction())
head(prediksi_test)
```

    ##    row_id  truth response
    ## 1:      3 223500 180561.7
    ## 2:      4 140000 174790.0
    ## 3:      5 250000 203169.7
    ## 4:     10 129500 178906.8
    ## 5:     12 279500 202968.6
    ## 6:     23 306000 204545.6

Untuk menghitung performa model dengan menggunakan ukuran akurasi bisa
menggunakan sintaks dibawah ini. Fungsi `msr` merupakan fungsi yang
dapat mengakses ukuran-ukuran kebaikan model yang ada di dalam package
`mlr3`.

``` r
#RMSE
train_test$aggregate(msr("regr.rmse"))
```

    ## regr.rmse 
    ##  74155.19

Ukuran kebaikan model yang ada di package `mlr3` bisa dilihat dalam link
berikut ini:

1.  <a href="https://mlr3.mlr-org.com/reference/mlr_measures" class="uri">https://mlr3.mlr-org.com/reference/mlr_measures</a>
2.  <a href="https://mlr3measures.mlr-org.com/reference/index.html" class="uri">https://mlr3measures.mlr-org.com/reference/index.html</a>

Kemudian jika ada lebih dari satu ukuran kebaikan model yang ingin kita
gunakan, kita bisa melakukannya dengan sintaks dibawah ini.

``` r
train_test$aggregate(list(msr("regr.rmse"),
                          msr("regr.mae"),
                          msr("regr.mape"),
                          msr("regr.srho")
                                   )) %>% round(3)
```

    ## regr.rmse  regr.mae regr.mape regr.srho 
    ## 74155.195 55476.792     0.323     0.511

Komparasi model
---------------

Pada bagian ini kita akan melakukan komparasi model antar model yang
sudah kita definisikan diatas. Langkah pertama yang kita lakukan adalah
mengabungkan learner yang sudah kita definisikan diawal ke dalam list

``` r
model_house <- list(regresi_linear,
                    regresi_lasso,
                    pohon_regresi,
                    random_forest,
                    gradient_boosting
                    )
```

Langkah berikutnya kita menentukan metode pembagian data. Metode
pembagian data yang awal yang sudah disimpan pada objek
`resample_holdout` bisa kita gunakan. Namun disini kita akan mencoba
untuk menggunakan metode cross-validation

``` r
resample_cv = rsmp("cv",folds=10)
```

Metode pembagian data yang dipilih disini adalah metode cross-validation
dengan 10 folds atau lipatan. Setelah kedua hal ini sudah dilakukan,
selanjutnya komparasi model bisa dilakukan

Komparasi model bisa dilakukan dengan menggunakan fungsi
`benchmark_design` dan `benchmark`. Fungsi `benchmark_design` digunakan
untuk memasukan informasi-inforamsi yang dibutuhkan untuk komparasi,
seperti data yang digunakan (tasks), model yang ingin dikomparasi
(learners) dan metode pembagian data yang digunakan (resamplings).

``` r
design <- benchmark_grid(tasks = task_house,
                         learners = model_house,
                         resamplings = resample_cv 
                         )
```

Kemudian fungsi `benchmark` digunakan untuk menjalankan/ running
komparasi model berdasarkan desain yang sudah dirancang.

``` r
bmr = benchmark(design,store_models = TRUE)
```

    ## INFO  [12:45:59.398] Benchmark with 50 resampling iterations 
    ## INFO  [12:45:59.418] Applying learner 'regr.rpart' on task 'house' (iter 3/10) 
    ## INFO  [12:45:59.440] Applying learner 'regr.lm' on task 'house' (iter 9/10) 
    ## INFO  [12:45:59.457] Applying learner 'regr.rpart' on task 'house' (iter 10/10) 
    ## INFO  [12:45:59.478] Applying learner 'regr.xgboost' on task 'house' (iter 5/10) 
    ## [12:45:59] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:45:59.540] Applying learner 'regr.xgboost' on task 'house' (iter 4/10) 
    ## [12:45:59] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:45:59.571] Applying learner 'regr.cv_glmnet' on task 'house' (iter 6/10) 
    ## INFO  [12:45:59.820] Applying learner 'regr.rpart' on task 'house' (iter 9/10) 
    ## INFO  [12:45:59.851] Applying learner 'regr.cv_glmnet' on task 'house' (iter 2/10) 
    ## INFO  [12:45:59.960] Applying learner 'regr.lm' on task 'house' (iter 3/10) 
    ## INFO  [12:45:59.976] Applying learner 'regr.lm' on task 'house' (iter 6/10) 
    ## INFO  [12:45:59.992] Applying learner 'regr.xgboost' on task 'house' (iter 7/10) 
    ## [12:46:00] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:00.017] Applying learner 'regr.rpart' on task 'house' (iter 7/10) 
    ## INFO  [12:46:00.037] Applying learner 'regr.rpart' on task 'house' (iter 5/10) 
    ## INFO  [12:46:00.057] Applying learner 'regr.xgboost' on task 'house' (iter 10/10) 
    ## [12:46:00] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:00.094] Applying learner 'regr.xgboost' on task 'house' (iter 2/10) 
    ## [12:46:00] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:00.121] Applying learner 'regr.lm' on task 'house' (iter 4/10) 
    ## INFO  [12:46:00.136] Applying learner 'regr.ranger' on task 'house' (iter 3/10) 
    ## INFO  [12:46:00.277] Applying learner 'regr.lm' on task 'house' (iter 1/10) 
    ## INFO  [12:46:00.296] Applying learner 'regr.ranger' on task 'house' (iter 2/10) 
    ## INFO  [12:46:00.761] Applying learner 'regr.ranger' on task 'house' (iter 5/10) 
    ## INFO  [12:46:00.898] Applying learner 'regr.ranger' on task 'house' (iter 8/10) 
    ## INFO  [12:46:01.022] Applying learner 'regr.xgboost' on task 'house' (iter 6/10) 
    ## [12:46:01] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:01.046] Applying learner 'regr.cv_glmnet' on task 'house' (iter 9/10) 
    ## INFO  [12:46:01.131] Applying learner 'regr.rpart' on task 'house' (iter 8/10) 
    ## INFO  [12:46:01.147] Applying learner 'regr.ranger' on task 'house' (iter 10/10) 
    ## INFO  [12:46:01.267] Applying learner 'regr.cv_glmnet' on task 'house' (iter 5/10) 
    ## INFO  [12:46:01.567] Applying learner 'regr.xgboost' on task 'house' (iter 8/10) 
    ## [12:46:01] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:01.586] Applying learner 'regr.xgboost' on task 'house' (iter 9/10) 
    ## [12:46:01] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:01.605] Applying learner 'regr.cv_glmnet' on task 'house' (iter 1/10) 
    ## INFO  [12:46:01.667] Applying learner 'regr.lm' on task 'house' (iter 5/10) 
    ## INFO  [12:46:01.679] Applying learner 'regr.rpart' on task 'house' (iter 1/10) 
    ## INFO  [12:46:01.693] Applying learner 'regr.ranger' on task 'house' (iter 7/10) 
    ## INFO  [12:46:01.811] Applying learner 'regr.ranger' on task 'house' (iter 9/10) 
    ## INFO  [12:46:01.921] Applying learner 'regr.lm' on task 'house' (iter 7/10) 
    ## INFO  [12:46:01.932] Applying learner 'regr.xgboost' on task 'house' (iter 3/10) 
    ## [12:46:01] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:01.950] Applying learner 'regr.rpart' on task 'house' (iter 2/10) 
    ## INFO  [12:46:01.964] Applying learner 'regr.xgboost' on task 'house' (iter 1/10) 
    ## [12:46:01] WARNING: amalgamation/../src/objective/regression_obj.cu:174: reg:linear is now deprecated in favor of reg:squarederror.
    ## INFO  [12:46:01.981] Applying learner 'regr.lm' on task 'house' (iter 2/10) 
    ## INFO  [12:46:01.991] Applying learner 'regr.lm' on task 'house' (iter 8/10) 
    ## INFO  [12:46:02.002] Applying learner 'regr.cv_glmnet' on task 'house' (iter 7/10) 
    ## INFO  [12:46:02.070] Applying learner 'regr.ranger' on task 'house' (iter 1/10) 
    ## INFO  [12:46:02.184] Applying learner 'regr.ranger' on task 'house' (iter 4/10) 
    ## INFO  [12:46:02.515] Applying learner 'regr.cv_glmnet' on task 'house' (iter 4/10) 
    ## INFO  [12:46:02.575] Applying learner 'regr.ranger' on task 'house' (iter 6/10) 
    ## INFO  [12:46:02.681] Applying learner 'regr.cv_glmnet' on task 'house' (iter 10/10) 
    ## INFO  [12:46:02.754] Applying learner 'regr.cv_glmnet' on task 'house' (iter 3/10) 
    ## INFO  [12:46:02.835] Applying learner 'regr.rpart' on task 'house' (iter 4/10) 
    ## INFO  [12:46:02.864] Applying learner 'regr.cv_glmnet' on task 'house' (iter 8/10) 
    ## INFO  [12:46:02.954] Applying learner 'regr.lm' on task 'house' (iter 10/10) 
    ## INFO  [12:46:02.965] Applying learner 'regr.rpart' on task 'house' (iter 6/10) 
    ## INFO  [12:46:02.980] Finished benchmark

Karena terdapat 5 model dan masing-masing model menjalankan 10-folds
cross-validation maka iterasi yang dilakukan ada sebanyak 50 kali.

Hasil Komparasi model
---------------------

Hasil komparasi model dapat berupa nilai-nilai ukuran kebaikan model
yang ditentukan oleh pengguna.

``` r
result = bmr$aggregate(list(msr("regr.rmse"),
                          msr("regr.mae"),
                          msr("regr.mape")
                                   )
              )
result
```

    ##    nr      resample_result task_id     learner_id resampling_id iters
    ## 1:  1 <ResampleResult[21]>   house        regr.lm            cv    10
    ## 2:  2 <ResampleResult[21]>   house regr.cv_glmnet            cv    10
    ## 3:  3 <ResampleResult[21]>   house     regr.rpart            cv    10
    ## 4:  4 <ResampleResult[21]>   house    regr.ranger            cv    10
    ## 5:  5 <ResampleResult[21]>   house   regr.xgboost            cv    10
    ##    regr.rmse  regr.mae regr.mape
    ## 1:  79512.09  56357.67 0.3469887
    ## 2:  83037.68  60259.05 0.3816259
    ## 3:  70007.96  48230.19 0.2845832
    ## 4:  63406.04  42842.67 0.2515385
    ## 5: 147978.85 127433.27 0.6742634

Berdasarkan nilai akurasi model yang memiliki performa prediksi terbaik
adalah model **Random Forest**.

Memprediksi respon pada data baru (jika tersedia)
-------------------------------------------------

Pada bagian ini akan diilustrasikan bagimana jika kita menerima data
baru yang tidak memiliki peubah respon. Berikut dibawah ini adalah
datanya.

``` r
data_house_baru <- read.csv("house_price2.csv")
glimpse(data_house_baru)
```

    ## Rows: 1,459
    ## Columns: 80
    ## $ Id            <int> 1461, 1462, 1463, 1464, 1465, 1466, 1467, 1...
    ## $ MSSubClass    <int> 20, 20, 60, 60, 120, 60, 20, 60, 20, 20, 12...
    ## $ MSZoning      <chr> "RH", "RL", "RL", "RL", "RL", "RL", "RL", "...
    ## $ LotFrontage   <int> 80, 81, 74, 78, 43, 75, NA, 63, 85, 70, 26,...
    ## $ LotArea       <int> 11622, 14267, 13830, 9978, 5005, 10000, 798...
    ## $ Street        <chr> "Pave", "Pave", "Pave", "Pave", "Pave", "Pa...
    ## $ Alley         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,...
    ## $ LotShape      <chr> "Reg", "IR1", "IR1", "IR1", "IR1", "IR1", "...
    ## $ LandContour   <chr> "Lvl", "Lvl", "Lvl", "Lvl", "HLS", "Lvl", "...
    ## $ Utilities     <chr> "AllPub", "AllPub", "AllPub", "AllPub", "Al...
    ## $ LotConfig     <chr> "Inside", "Corner", "Inside", "Inside", "In...
    ## $ LandSlope     <chr> "Gtl", "Gtl", "Gtl", "Gtl", "Gtl", "Gtl", "...
    ## $ Neighborhood  <chr> "NAmes", "NAmes", "Gilbert", "Gilbert", "St...
    ## $ Condition1    <chr> "Feedr", "Norm", "Norm", "Norm", "Norm", "N...
    ## $ Condition2    <chr> "Norm", "Norm", "Norm", "Norm", "Norm", "No...
    ## $ BldgType      <chr> "1Fam", "1Fam", "1Fam", "1Fam", "TwnhsE", "...
    ## $ HouseStyle    <chr> "1Story", "1Story", "2Story", "2Story", "1S...
    ## $ OverallQual   <int> 5, 6, 5, 6, 8, 6, 6, 6, 7, 4, 7, 6, 5, 6, 7...
    ## $ OverallCond   <int> 6, 6, 5, 6, 5, 5, 7, 5, 5, 5, 5, 5, 5, 6, 6...
    ## $ YearBuilt     <int> 1961, 1958, 1997, 1998, 1992, 1993, 1992, 1...
    ## $ YearRemodAdd  <int> 1961, 1958, 1998, 1998, 1992, 1994, 2007, 1...
    ## $ RoofStyle     <chr> "Gable", "Hip", "Gable", "Gable", "Gable", ...
    ## $ RoofMatl      <chr> "CompShg", "CompShg", "CompShg", "CompShg",...
    ## $ Exterior1st   <chr> "VinylSd", "Wd Sdng", "VinylSd", "VinylSd",...
    ## $ Exterior2nd   <chr> "VinylSd", "Wd Sdng", "VinylSd", "VinylSd",...
    ## $ MasVnrType    <chr> "None", "BrkFace", "None", "BrkFace", "None...
    ## $ MasVnrArea    <int> 0, 108, 0, 20, 0, 0, 0, 0, 0, 0, 0, 504, 49...
    ## $ ExterQual     <chr> "TA", "TA", "TA", "TA", "Gd", "TA", "TA", "...
    ## $ ExterCond     <chr> "TA", "TA", "TA", "TA", "TA", "TA", "Gd", "...
    ## $ Foundation    <chr> "CBlock", "CBlock", "PConc", "PConc", "PCon...
    ## $ BsmtQual      <chr> "TA", "TA", "Gd", "TA", "Gd", "Gd", "Gd", "...
    ## $ BsmtCond      <chr> "TA", "TA", "TA", "TA", "TA", "TA", "TA", "...
    ## $ BsmtExposure  <chr> "No", "No", "No", "No", "No", "No", "No", "...
    ## $ BsmtFinType1  <chr> "Rec", "ALQ", "GLQ", "GLQ", "ALQ", "Unf", "...
    ## $ BsmtFinSF1    <int> 468, 923, 791, 602, 263, 0, 935, 0, 637, 80...
    ## $ BsmtFinType2  <chr> "LwQ", "Unf", "Unf", "Unf", "Unf", "Unf", "...
    ## $ BsmtFinSF2    <int> 144, 0, 0, 0, 0, 0, 0, 0, 0, 78, 0, 0, 0, 0...
    ## $ BsmtUnfSF     <int> 270, 406, 137, 324, 1017, 763, 233, 789, 66...
    ## $ TotalBsmtSF   <int> 882, 1329, 928, 926, 1280, 763, 1168, 789, ...
    ## $ Heating       <chr> "GasA", "GasA", "GasA", "GasA", "GasA", "Ga...
    ## $ HeatingQC     <chr> "TA", "TA", "Gd", "Ex", "Ex", "Gd", "Ex", "...
    ## $ CentralAir    <chr> "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y"...
    ## $ Electrical    <chr> "SBrkr", "SBrkr", "SBrkr", "SBrkr", "SBrkr"...
    ## $ X1stFlrSF     <int> 896, 1329, 928, 926, 1280, 763, 1187, 789, ...
    ## $ X2ndFlrSF     <int> 0, 0, 701, 678, 0, 892, 0, 676, 0, 0, 0, 50...
    ## $ LowQualFinSF  <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ GrLivArea     <int> 896, 1329, 1629, 1604, 1280, 1655, 1187, 14...
    ## $ BsmtFullBath  <int> 0, 0, 0, 0, 0, 0, 1, 0, 1, 1, 1, 0, 0, 0, 0...
    ## $ BsmtHalfBath  <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ FullBath      <int> 1, 1, 2, 2, 2, 2, 2, 2, 1, 1, 2, 1, 1, 2, 1...
    ## $ HalfBath      <int> 0, 1, 1, 1, 0, 1, 0, 1, 1, 0, 0, 1, 1, 1, 0...
    ## $ BedroomAbvGr  <int> 2, 3, 3, 3, 2, 3, 3, 3, 2, 2, 2, 2, 3, 3, 2...
    ## $ KitchenAbvGr  <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1...
    ## $ KitchenQual   <chr> "TA", "Gd", "TA", "Gd", "Gd", "TA", "TA", "...
    ## $ TotRmsAbvGrd  <int> 5, 6, 6, 7, 5, 7, 6, 7, 5, 4, 5, 5, 6, 6, 4...
    ## $ Functional    <chr> "Typ", "Typ", "Typ", "Typ", "Typ", "Typ", "...
    ## $ Fireplaces    <int> 0, 0, 1, 1, 0, 1, 0, 1, 1, 0, 1, 0, 0, 1, 0...
    ## $ FireplaceQu   <chr> NA, NA, "TA", "Gd", NA, "TA", NA, "Gd", "Po...
    ## $ GarageType    <chr> "Attchd", "Attchd", "Attchd", "Attchd", "At...
    ## $ GarageYrBlt   <int> 1961, 1958, 1997, 1998, 1992, 1993, 1992, 1...
    ## $ GarageFinish  <chr> "Unf", "Unf", "Fin", "Fin", "RFn", "Fin", "...
    ## $ GarageCars    <int> 1, 1, 2, 2, 2, 2, 2, 2, 2, 2, 2, 1, 1, 2, 1...
    ## $ GarageArea    <int> 730, 312, 482, 470, 506, 440, 420, 393, 506...
    ## $ GarageQual    <chr> "TA", "TA", "TA", "TA", "TA", "TA", "TA", "...
    ## $ GarageCond    <chr> "TA", "TA", "TA", "TA", "TA", "TA", "TA", "...
    ## $ PavedDrive    <chr> "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y"...
    ## $ WoodDeckSF    <int> 140, 393, 212, 360, 0, 157, 483, 0, 192, 24...
    ## $ OpenPorchSF   <int> 0, 36, 34, 36, 82, 84, 21, 75, 0, 0, 68, 0,...
    ## $ EnclosedPorch <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ X3SsnPorch    <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ ScreenPorch   <int> 120, 0, 0, 0, 144, 0, 0, 0, 0, 0, 0, 0, 0, ...
    ## $ PoolArea      <int> 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...
    ## $ PoolQC        <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA,...
    ## $ Fence         <chr> "MnPrv", NA, "MnPrv", NA, NA, NA, "GdPrv", ...
    ## $ MiscFeature   <chr> NA, "Gar2", NA, NA, NA, NA, "Shed", NA, NA,...
    ## $ MiscVal       <int> 0, 12500, 0, 0, 0, 0, 500, 0, 0, 0, 0, 0, 0...
    ## $ MoSold        <int> 6, 6, 3, 6, 1, 4, 3, 5, 2, 4, 6, 2, 3, 6, 6...
    ## $ YrSold        <int> 2010, 2010, 2010, 2010, 2010, 2010, 2010, 2...
    ## $ SaleType      <chr> "WD", "WD", "WD", "WD", "WD", "WD", "WD", "...
    ## $ SaleCondition <chr> "Normal", "Normal", "Normal", "Normal", "No...

``` r
data_house_baru <- data_house_baru %>% select(names(data_house)[-1]) %>% na.omit
```

Sebagai contoh kita menggunakan model random forest sebagai model
terbaik, berikut sintaksnya.

``` r
random_forest$train(task = task_house)
prediksi_random_forest_new <- random_forest$predict_newdata(newdata = data_house_baru)
as.data.table(prediksi_random_forest_new)
```

    ##       row_id truth  response
    ##    1:      1    NA 206744.25
    ##    2:      2    NA 223285.96
    ##    3:      3    NA 281189.75
    ##    4:      4    NA 239465.53
    ##    5:      5    NA 220816.98
    ##   ---                       
    ## 1228:   1228    NA  92345.09
    ## 1229:   1229    NA 100015.68
    ## 1230:   1230    NA 275245.97
    ## 1231:   1231    NA 163027.84
    ## 1232:   1232    NA 243073.19

Fungsi `$train` digunakan untuk melakukan training pada data keseluruhan
(tanpa ada proses pembagian data). Terakhir, fungsi `predict_newdata`
digunakan untuk melakukan prediksi pada data baru.

[1] <a href="mailto:gdito@apps.ipb.ac.id" class="email">gdito@apps.ipb.ac.id</a>
