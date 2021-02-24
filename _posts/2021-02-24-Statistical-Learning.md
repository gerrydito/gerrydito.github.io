---
layout: post
title:  Statistical Machine Learning dengan mlr3
categories: [Machine Learning,Supervised,mlr3]
excerpt: 
---

Package
-------

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

``` r
library(tidyverse)
library(mlr3verse)
```

Deskripsi singkat data
----------------------

Data yang digunakan pada tutorial kali ini adalah data yang bernama Pima
Indian Diabetes yang sudah sedikit diedit. Berikut adalah informasi
singkat mengenai data

This dataset is originally from the National Institute of Diabetes and
Digestive and Kidney Diseases. The objective of the dataset is to
diagnostically predict whether or not a patient has diabetes, based on
certain diagnostic measurements included in the dataset. Several
constraints were placed on the selection of these instances from a
larger database. In particular, all patients here are females at least
21 years old of Pima Indian heritage.

Content The datasets consists of several medical predictor variables and
one target variable, Outcome. Predictor variables includes the number of
pregnancies the patient has had, their BMI, insulin level, age, and so
on.

Acknowledgements Smith, J.W., Everhart, J.E., Dickson, W.C., Knowler,
W.C., & Johannes, R.S. (1988). Using the ADAP learning algorithm to
forecast the onset of diabetes mellitus. In Proceedings of the Symposium
on Computer Applications and Medical Care (pp. 261–265). IEEE Computer
Society Press.

data ini bisa diperoleh di link berikut ini
<a href="https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN" class="uri">https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN</a>

Statistical Machine Learning di R
-------------------------

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

Proses pemodelan (learning) menggunakan ekosistem mlr3:

1.  Import data di R
2.  Import data ke ekosistem mlr3
3.  Menentukan model yang digunakan
4.  Menentukan cara pembagian data
5.  Melakukan interpretasi model (jika diperlukan)
6.  Melakukan training dan menghitung performa model/ Komparasi model
7.  Memprediksi respon pada data baru (jika tersedia)

### Import data di R

``` r
data_diabetes <- read.csv("diabetes.csv",stringsAsFactors = TRUE)
head(data_diabetes)
```

    ##   Pregnancies Glucose BloodPressure SkinThickness Insulin  BMI
    ## 1           6     148            72            35       0 33.6
    ## 2           1      85            66            29       0 26.6
    ## 3           8     183            64             0       0 23.3
    ## 4           1      89            66            23      94 28.1
    ## 5           0     137            40            35     168 43.1
    ## 6           5     116            74             0       0 25.6
    ##   DiabetesPedigreeFunction Age Outcome
    ## 1                    0.627  50    Case
    ## 2                    0.351  31 Control
    ## 3                    0.672  32    Case
    ## 4                    0.167  21 Control
    ## 5                    2.288  33    Case
    ## 6                    0.201  30 Control

Khusus yang menggunakan R versi 4.00 keatas, argumen
`stringsAsFactors = TRUE` disertakan agar data yang berbentuk string
bisa berubah menjadi factor.

### Import data ke ekosistem mlr3

Import data ke mlr3 bisa dilakukan dengan menggunakan fungsi
`TaskClassif$new` atau `TaskRegr$new` yang berasal dari package `mlr3`.
`TaskClassif$new` digunakan jika peubah respon kita berupa peubah biner
atau multiclass, sedangkan `TaskRegr$new` digunakan jika responya berupa
peubah numerik.

``` r
task_diabetes = TaskClassif$new(id="diabetes",backend = data_diabetes,
                                target = "Outcome",positive ="Case")
```

Argumen utama dalam fungsi `TaskClassif$new` adalah sebagai berikut:

1.  `id` yang merupakan nama dari task (bisa diisi dengan nama apapun)
2.  `backend` adalah data yang ingin dimodelkan dengan catatan peubah
    respon-nya harus berupa **factor**
3.  `target` adalah nama kolom yang dijadikan peubah respon
4.  `positive` adalah nama kelas positif dari peubah respon

### Menentukan model yang digunakan

Pada tahap ini fungsi yang digunakan adalah `lrn` yang memiliki argumen
utama **nama model** yang ingin digunakan. Berikut adalah model-model
yang akan digunakan beserta argumen di dalam fungsi `lrn` dan asal
packagenya:

1.  Regresi Logistik - `"classif.log_reg"`
2.  KNN - `"classif.kknn"` - `library(kknn)`
3.  Decision Tree - `"classif.rpart"` - `library(rpart)`
4.  Naive Bayes - `"classif.naive_bayes"` - `library(e1071)`
5.  Random Forest - `"classif.ranger"` - `library(ranger)`

Sebagai catatan, untuk model-model yang digunakan dalam `mlr3` berasal
dari package-package lain sehingga package-package tersebut perlu
install terlebih dahulu. Kemudian, untuk model klasifikasi (respon biner
atau multiclass) selalu diawali dengan kata `"classif."`. Sedangkan
model regresi(respon numerik) diawali dengan kata `regr`. Selain itu,
fungsi `lrn` juga memungkinkan untuk memasukan argumen-argumen dari
package asalnya (termasuk hiperparameter). Sebagai contoh model KNN dari
package `kknn` memiliki argumen-argumen yang bisa dilihat dengan
menggunakan

``` r
as.data.table(lrn("classif.kknn")$param_set)
```

    ##          id    class lower upper
    ## 1:        k ParamInt     1   Inf
    ## 2: distance ParamDbl     0   Inf
    ## 3:   kernel ParamFct    NA    NA
    ## 4:    scale ParamLgl    NA    NA
    ## 5:  ykernel ParamUty    NA    NA
    ##                                                            levels
    ## 1:                                                               
    ## 2:                                                               
    ## 3: rectangular,triangular,epanechnikov,biweight,triweight,cos,...
    ## 4:                                                     TRUE,FALSE
    ## 5:                                                               
    ##    nlevels is_bounded special_vals default storage_type  tags
    ## 1:     Inf      FALSE    <list[0]>       7      integer train
    ## 2:     Inf      FALSE    <list[0]>       2      numeric train
    ## 3:      10       TRUE    <list[0]> optimal    character train
    ## 4:       2       TRUE    <list[0]>    TRUE      logical train
    ## 5:     Inf      FALSE    <list[0]>                 list train

Berdasarkan output diatas argumen-argumen yang bisa digunakan dalam
`classif.kknn` ada di kolom id. Selanjutnya, kolom class menunjukkan
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
learner_logreg <- lrn("classif.log_reg")
learner_knn <- lrn("classif.kknn",k=10,kernel="rectangular")
learner_tree <- lrn("classif.rpart")
learner_nb <- lrn("classif.naive_bayes")
learner_rf <- lrn("classif.ranger",importance="impurity")
```

### Menentukan cara pembagian data

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
resample_diabetes1 = rsmp("holdout", ratio = 0.8)
```

Pembagian data ini dimaksudkan untuk mengevaluasi kemampuan prediksi
model untuk data baru.

### Melakukan interpretasi model (jika diperlukan)

Tahap ini biasanya dilakukan untuk melihat bagaimana pengaruh
peubah-peubah prediktor terhadap respon menurut masing-masing model.
Misalnya saja dalam regresi logistik besarnya nilai koefisien dan p
value bisa menggambarkan bagaimana pengaruh peubah prediktor terhadap
respon. Model-model yang akan digunakan untuk melihat pengaruh tersebut
adalah regresi logistik, decision tree dan Random Forest. Berikut adalah
sintaksnya

``` r
# Regresi Logistik
learner_logreg$train(task = task_diabetes)
summary(learner_logreg$model)
```

    ## 
    ## Call:
    ## stats::glm(formula = task$formula(), family = "binomial", data = task$data(), 
    ##     model = FALSE)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -2.9139  -0.7278   0.4194   0.7338   2.5393  
    ## 
    ## Coefficients:
    ##                            Estimate Std. Error z value Pr(>|z|)    
    ## (Intercept)               8.3697127  0.7241555  11.558  < 2e-16 ***
    ## Age                      -0.0162950  0.0094134  -1.731 0.083443 .  
    ## BMI                      -0.0894983  0.0152167  -5.882 4.06e-09 ***
    ## BloodPressure             0.0136704  0.0052846   2.587 0.009686 ** 
    ## DiabetesPedigreeFunction -0.9255279  0.3006644  -3.078 0.002082 ** 
    ## Glucose                  -0.0349069  0.0037467  -9.317  < 2e-16 ***
    ## Insulin                   0.0012331  0.0009118   1.352 0.176249    
    ## Pregnancies              -0.1188551  0.0322586  -3.684 0.000229 ***
    ## SkinThickness            -0.0014183  0.0069417  -0.204 0.838109    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 972.27  on 751  degrees of freedom
    ## Residual deviance: 711.73  on 743  degrees of freedom
    ## AIC: 729.73
    ## 
    ## Number of Fisher Scoring iterations: 5

``` r
# Decision Tree
learner_tree$train(task = task_diabetes)
rpart.plot::rpart.plot(learner_tree$model,roundint = F,type = 5,tweak = 1.75)
```

![](https://raw.githubusercontent.com/gerrydito/gerrydito.github.io/main/_posts/Statistical-Learning_files/figure-markdown_github/unnamed-chunk-9-1.png)

``` r
# Random Forest
learner_rf$train(task = task_diabetes)
learner_rf$model$variable.importance
```

    ##                      Age                      BMI 
    ##                 47.62452                 55.32196 
    ##            BloodPressure DiabetesPedigreeFunction 
    ##                 29.70532                 42.03994 
    ##                  Glucose                  Insulin 
    ##                 87.53307                 24.42128 
    ##              Pregnancies            SkinThickness 
    ##                 29.26089                 23.83322

Catatan:

1.  Data yang digunakan untuk menjalankan model-model tanpa pembagian
    data (training dan testing)
2.  `rpart.plot` berasal dari package `rpart.plot`.
3.  Argumen `type` dalam `rpart.plot` digunakan untuk menentukan
    bagimana pohon di gambarkan. Argumen `tweak` digunakan untuk
    memperbesar gambar. Lihat help untuk lebih lengkapnya.
4.  Nilai variable importance untuk Random Forest diatas adalah nilai
    Gini Impurity. Semakin besar nilainya maka akan semakin berpengaruh
    prediktor tersebut. Jika ingin mengetahui Gini Impurity secara lebih
    lengkap bisa melihat link berikut
    <a href="https://victorzhou.com/blog/gini-impurity/" class="uri">https://victorzhou.com/blog/gini-impurity/</a>

Dibawah ini merupakan sintaks untuk mengubah output variable importance
ke dalam `data.frame` agar mudah untuk diurutkan dan di buat grafiknya.

``` r
importance <- data.frame(Predictors = names(learner_rf$model$variable.importance),
                         impurity = learner_rf$model$variable.importance
                         )
rownames(importance) <- NULL

importance %>% arrange(desc(impurity))
```

    ##                 Predictors impurity
    ## 1                  Glucose 87.53307
    ## 2                      BMI 55.32196
    ## 3                      Age 47.62452
    ## 4 DiabetesPedigreeFunction 42.03994
    ## 5            BloodPressure 29.70532
    ## 6              Pregnancies 29.26089
    ## 7                  Insulin 24.42128
    ## 8            SkinThickness 23.83322

### Melakukan training dan menghitung performa model

Pada tahap ini kita bisa menerapkan model yang sudah kita definisikan
diawal pada data training dan kemudian mengevaluasi kemampuan prediksi
dengan data testing. Hal tersebut bisa dilakukan dengan menggunakan
fungsi `resample`.

``` r
train_test_diabetes = resample(task = task_diabetes,
                               learner = learner_knn,
                               resampling = resample_diabetes1,
                               store_models = TRUE
                               )
```

    ## INFO  [08:54:57.665] Applying learner 'classif.kknn' on task 'diabetes' (iter 1/1)

Berdasarkan sintaks diatas kita melakukan training untuk model KNN, jika
ingin melakukan training untuk model lainnya cukup ganti
`learner=learner_knn` dengan
`learner_logreg`,`learner_nb`,`learner_tree` dan `learner_rf`.

Jika kita ingin mengeluarkan hasil prediksi pada data testing bisa
menggunakan sintaks dibawah ini.

``` r
prediksi_test = as.data.table(train_test_diabetes$prediction())
head(prediksi_test)
```

    ##    row_id   truth response
    ## 1:      2 Control  Control
    ## 2:     11    Case     Case
    ## 3:     12 Control     Case
    ## 4:     13    Case     Case
    ## 5:     15    Case  Control
    ## 6:     18 Control  Control

Confusion matrix bisa dikeluarkan dengan sintaks dibawah ini

``` r
train_test_diabetes$prediction()$confusion
```

    ##          truth
    ## response  Case Control
    ##   Case      24      16
    ##   Control   32      78

Untuk menghitung performa model dengan menggunakan ukuran akurasi bisa
menggunakan sintaks dibawah ini. Fungsi `msr` merupakan fungsi yang
dapat mengakses ukuran-ukuran kebaikan model yang ada di dalam package
`mlr3`.

``` r
train_test_diabetes$aggregate(msr("classif.acc"))
```

    ## classif.acc 
    ##        0.68

Ukuran kebaikan model yang ada di package `mlr3` bisa dilihat di link
<a href="https://mlr3.mlr-org.com/reference/mlr_measures.html" class="uri">https://mlr3.mlr-org.com/reference/mlr_measures.html</a>.
Sebagai catatan, terdapat beberapa ukuran yang membutuhkan prediksi yang
dikeluarkan berupa peluang bukan berupa kelas.

Kemudian jika ada lebih dari satu ukuran kebaikan model yang ingin kita
gunakan, kita bisa melakukannya dengan sintaks dibawah ini.

``` r
train_test_diabetes$aggregate(list(msr("classif.acc"),
                                   msr("classif.specificity"),
                                   msr("classif.sensitivity")
                                   ))
```

    ##         classif.acc classif.specificity classif.sensitivity 
    ##           0.6800000           0.8297872           0.4285714

### Komparasi model

Pada bagian ini kita akan melakukan komparasi model antar model yang
sudah kita definisikan diatas. Langkah pertama yang kita lakukan adalah
mengabungkan learner yang sudah kita definisikan diawal ke dalam list

``` r
learner_diabetes <- list(learner_logreg,learner_knn,
                         learner_tree,learner_nb,learner_rf)
```

Langkah berikutnya kita menentukan metode pembagian data. Metode
pembagian data yang awal yang sudah disimpan pada objek
`resample_diabetes1` bisa kita gunakan. Namun disini kita akan mencoba
untuk menggunakan metode cross-validation

``` r
resample_diabetes_cv = rsmp("cv",folds=10)
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
design <- benchmark_grid(tasks = task_diabetes,
                         learners = learner_diabetes,
                         resamplings = resample_diabetes_cv 
                         )
```

Kemudian fungsi `benchmark` digunakan untuk menjalankan/ running
komparasi model berdasarkan desain yang sudah dirancang.

``` r
bmr = benchmark(design,store_models = TRUE)
```

    ## INFO  [08:54:59.020] Benchmark with 50 resampling iterations 
    ## INFO  [08:54:59.043] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 10/10) 
    ## INFO  [08:54:59.433] Applying learner 'classif.rpart' on task 'diabetes' (iter 3/10) 
    ## INFO  [08:54:59.457] Applying learner 'classif.rpart' on task 'diabetes' (iter 4/10) 
    ## INFO  [08:54:59.480] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 9/10) 
    ## INFO  [08:54:59.512] Applying learner 'classif.kknn' on task 'diabetes' (iter 9/10) 
    ## INFO  [08:54:59.546] Applying learner 'classif.rpart' on task 'diabetes' (iter 6/10) 
    ## INFO  [08:54:59.569] Applying learner 'classif.log_reg' on task 'diabetes' (iter 1/10) 
    ## INFO  [08:54:59.594] Applying learner 'classif.kknn' on task 'diabetes' (iter 4/10) 
    ## INFO  [08:54:59.635] Applying learner 'classif.kknn' on task 'diabetes' (iter 2/10) 
    ## INFO  [08:54:59.687] Applying learner 'classif.ranger' on task 'diabetes' (iter 8/10) 
    ## INFO  [08:54:59.787] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 6/10) 
    ## INFO  [08:54:59.834] Applying learner 'classif.ranger' on task 'diabetes' (iter 4/10) 
    ## INFO  [08:54:59.930] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 4/10) 
    ## INFO  [08:54:59.962] Applying learner 'classif.kknn' on task 'diabetes' (iter 6/10) 
    ## INFO  [08:54:59.997] Applying learner 'classif.kknn' on task 'diabetes' (iter 8/10) 
    ## INFO  [08:55:00.034] Applying learner 'classif.rpart' on task 'diabetes' (iter 8/10) 
    ## INFO  [08:55:00.070] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 8/10) 
    ## INFO  [08:55:00.103] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 7/10) 
    ## INFO  [08:55:00.135] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 3/10) 
    ## INFO  [08:55:00.182] Applying learner 'classif.rpart' on task 'diabetes' (iter 5/10) 
    ## INFO  [08:55:00.204] Applying learner 'classif.log_reg' on task 'diabetes' (iter 4/10) 
    ## INFO  [08:55:00.226] Applying learner 'classif.log_reg' on task 'diabetes' (iter 8/10) 
    ## INFO  [08:55:00.248] Applying learner 'classif.ranger' on task 'diabetes' (iter 9/10) 
    ## INFO  [08:55:00.348] Applying learner 'classif.log_reg' on task 'diabetes' (iter 2/10) 
    ## INFO  [08:55:00.388] Applying learner 'classif.ranger' on task 'diabetes' (iter 1/10) 
    ## INFO  [08:55:00.506] Applying learner 'classif.ranger' on task 'diabetes' (iter 3/10) 
    ## INFO  [08:55:00.613] Applying learner 'classif.ranger' on task 'diabetes' (iter 5/10) 
    ## INFO  [08:55:00.712] Applying learner 'classif.kknn' on task 'diabetes' (iter 1/10) 
    ## INFO  [08:55:00.747] Applying learner 'classif.log_reg' on task 'diabetes' (iter 3/10) 
    ## INFO  [08:55:00.771] Applying learner 'classif.rpart' on task 'diabetes' (iter 10/10) 
    ## INFO  [08:55:00.793] Applying learner 'classif.kknn' on task 'diabetes' (iter 10/10) 
    ## INFO  [08:55:00.829] Applying learner 'classif.rpart' on task 'diabetes' (iter 1/10) 
    ## INFO  [08:55:00.865] Applying learner 'classif.log_reg' on task 'diabetes' (iter 5/10) 
    ## INFO  [08:55:00.904] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 5/10) 
    ## INFO  [08:55:00.937] Applying learner 'classif.kknn' on task 'diabetes' (iter 3/10) 
    ## INFO  [08:55:00.971] Applying learner 'classif.kknn' on task 'diabetes' (iter 7/10) 
    ## INFO  [08:55:01.007] Applying learner 'classif.log_reg' on task 'diabetes' (iter 7/10) 
    ## INFO  [08:55:01.030] Applying learner 'classif.rpart' on task 'diabetes' (iter 2/10) 
    ## INFO  [08:55:01.053] Applying learner 'classif.rpart' on task 'diabetes' (iter 9/10) 
    ## INFO  [08:55:01.076] Applying learner 'classif.rpart' on task 'diabetes' (iter 7/10) 
    ## INFO  [08:55:01.098] Applying learner 'classif.log_reg' on task 'diabetes' (iter 10/10) 
    ## INFO  [08:55:01.120] Applying learner 'classif.ranger' on task 'diabetes' (iter 2/10) 
    ## INFO  [08:55:01.228] Applying learner 'classif.kknn' on task 'diabetes' (iter 5/10) 
    ## INFO  [08:55:01.263] Applying learner 'classif.ranger' on task 'diabetes' (iter 7/10) 
    ## INFO  [08:55:01.466] Applying learner 'classif.ranger' on task 'diabetes' (iter 6/10) 
    ## INFO  [08:55:01.558] Applying learner 'classif.log_reg' on task 'diabetes' (iter 6/10) 
    ## INFO  [08:55:01.582] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 2/10) 
    ## INFO  [08:55:01.614] Applying learner 'classif.log_reg' on task 'diabetes' (iter 9/10) 
    ## INFO  [08:55:01.637] Applying learner 'classif.ranger' on task 'diabetes' (iter 10/10) 
    ## INFO  [08:55:01.733] Applying learner 'classif.naive_bayes' on task 'diabetes' (iter 1/10) 
    ## INFO  [08:55:01.788] Finished benchmark

Karena terdapat 5 model dan masing-masing model menjalankan 10-folds
cross-validation maka iterasi yang dilakukan ada sebanyak 50 kali.

### Hasil Komparasi model

Hasil komparasi model dapat berupa nilai-nilai ukuran kebaikan model
yang ditentukan oleh pengguna.

``` r
result = bmr$aggregate(msr("classif.acc")
              )
result
```

    ##    nr      resample_result  task_id          learner_id resampling_id
    ## 1:  1 <ResampleResult[21]> diabetes     classif.log_reg            cv
    ## 2:  2 <ResampleResult[21]> diabetes        classif.kknn            cv
    ## 3:  3 <ResampleResult[21]> diabetes       classif.rpart            cv
    ## 4:  4 <ResampleResult[21]> diabetes classif.naive_bayes            cv
    ## 5:  5 <ResampleResult[21]> diabetes      classif.ranger            cv
    ##    iters classif.acc
    ## 1:    10   0.7672807
    ## 2:    10   0.7407719
    ## 3:    10   0.7553509
    ## 4:    10   0.7473860
    ## 5:    10   0.7646140

Berdasarkan nilai akurasi model yang memiliki performa prediksi terbaik
adalah model regresi logistik.

### Memprediksi respon pada data baru (jika tersedia)

Pada bagian ini akan diilustrasikan bagimana jika kita menerima data
baru yang tidak memiliki peubah respon. Berikut dibawah ini adalah
datanya. Datanya bisa di download di link berikut

<a href="https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN" class="uri">https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN</a>

``` r
data_diabetes_baru <- read.csv("diabetes_baru.csv")
head(data_diabetes)
```

    ##   Pregnancies Glucose BloodPressure SkinThickness Insulin  BMI
    ## 1           6     148            72            35       0 33.6
    ## 2           1      85            66            29       0 26.6
    ## 3           8     183            64             0       0 23.3
    ## 4           1      89            66            23      94 28.1
    ## 5           0     137            40            35     168 43.1
    ## 6           5     116            74             0       0 25.6
    ##   DiabetesPedigreeFunction Age Outcome
    ## 1                    0.627  50    Case
    ## 2                    0.351  31 Control
    ## 3                    0.672  32    Case
    ## 4                    0.167  21 Control
    ## 5                    2.288  33    Case
    ## 6                    0.201  30 Control

Sebagai contoh kita menggunakan model regresi logistik sebagai model
terbaik, berikut sintaksnya.

``` r
learner_logreg$train(task = task_diabetes)
prediksi_data_baru_logreg <- learner_logreg$predict_newdata(newdata = data_diabetes_baru)
as.data.table(prediksi_data_baru_logreg)
```

    ##     row_id truth response
    ##  1:      1  <NA>     Case
    ##  2:      2  <NA>  Control
    ##  3:      3  <NA>  Control
    ##  4:      4  <NA>     Case
    ##  5:      5  <NA>  Control
    ##  6:      6  <NA>  Control
    ##  7:      7  <NA>     Case
    ##  8:      8  <NA>  Control
    ##  9:      9  <NA>  Control
    ## 10:     10  <NA>     Case
    ## 11:     11  <NA>     Case
    ## 12:     12  <NA>  Control
    ## 13:     13  <NA>  Control
    ## 14:     14  <NA>     Case
    ## 15:     15  <NA>     Case
    ## 16:     16  <NA>  Control

Fungsi `$train` digunakan untuk melakukan training pada data keseluruhan
(tanpa ada proses pembagian data). Terakhir, fungsi `predict_newdata`
digunakan untuk melakukan prediksi pada data baru.

[1] <a href="mailto:gdito@apps.ipb.ac.id" class="email">gdito@apps.ipb.ac.id</a>
