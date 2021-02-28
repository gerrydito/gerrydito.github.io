---
layout: post
title:  Statistical Machine Learning dengan mlr3
categories: [Machine Learning,Supervised Learning,mlr3]
excerpt: Di R ada beberapa ekosistem yang bisa digunakan untuk menerapkan statistical learning atau machine learning, yang paling terkenal antara lain adalah juga <code>mlr3</code>
---

<html xmlns="http://www.w3.org/1999/xhtml">
  
<body class="preload">

    
   <div class="container-fluid main-container">
     <div class="row">
       <div class="col-md-10">
<!-- Don't indent these lines or it will mess pre blocks indentation --> 
<div id="content">
<div id="statistical-learning-di-r" class="section level2">
<h2>Statistical Learning di R</h2>
<p>Di R ada beberapa ekosistem yang bisa digunakan untuk menerapkan statistical learning atau machine learning, yang paling terkenal adalah ekosistem <code>caret</code> dan juga <code>mlr</code>. Jika ingin mempelajari ekosistem <code>caret</code> secara lebih lengkap bisa mengakses link berikut <a href="https://topepo.github.io/caret/" class="uri">https://topepo.github.io/caret/</a>. Pada tutorial kali ini kita akan menggunakan ekosistem <code>mlr</code> (atau sekarang berubah nama menjadi <code>mlr3</code>). Jika tertarik belajar lebih lanjut tentang ekosistem ini bisa mengakses link-link berikut:</p>
<ol style="list-style-type: decimal">
<li><a href="https://mlr3.mlr-org.com/" class="uri">https://mlr3.mlr-org.com/</a></li>
<li><a href="https://mlr3book.mlr-org.com/" class="uri">https://mlr3book.mlr-org.com/</a></li>
<li><a href="https://mlr3gallery.mlr-org.com/" class="uri">https://mlr3gallery.mlr-org.com/</a></li>
</ol>
<p>Proses pemodelan (learning) menggunakan ekosistem mlr3:</p>
<ol style="list-style-type: decimal">
<li>Import data di R</li>
<li>Import data ke ekosistem mlr3</li>
<li>Menentukan model yang digunakan</li>
<li>Menentukan cara pembagian data</li>
<li>Melakukan interpretasi model (jika diperlukan)</li>
<li>Melakukan training dan menghitung performa model/ Komparasi model</li>
<li>Memprediksi respon pada data baru (jika tersedia)</li>
</ol>
</div>
<div id="package" class="section level2">
<h2>Package</h2>
<p>Silahkan install jika belum ada</p>
<div class="sourceCode" id="cb1"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1"></a><span class="kw">install.packages</span>(<span class="st">&quot;tidyverse&quot;</span>)</span>
<span id="cb1-2"><a href="#cb1-2"></a><span class="kw">install.packages</span>(<span class="st">&quot;mlr3verse&quot;</span>)</span>
<span id="cb1-3"><a href="#cb1-3"></a><span class="kw">install.packages</span>(<span class="st">&quot;kknn&quot;</span>)</span>
<span id="cb1-4"><a href="#cb1-4"></a><span class="kw">install.packages</span>(<span class="st">&quot;e1071&quot;</span>)</span>
<span id="cb1-5"><a href="#cb1-5"></a><span class="kw">install.packages</span>(<span class="st">&quot;ranger&quot;</span>)</span>
<span id="cb1-6"><a href="#cb1-6"></a><span class="kw">install.packages</span>(<span class="st">&quot;rpart.plot&quot;</span>)</span></code></pre></div>
<p>Memanggil Package</p>
<div class="sourceCode" id="cb2"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb2-1"><a href="#cb2-1"></a><span class="kw">library</span>(tidyverse)</span>
<span id="cb2-2"><a href="#cb2-2"></a><span class="kw">library</span>(mlr3verse)</span></code></pre></div>
</div>
<div id="deskripsi-singkat-data" class="section level2">
<h2>Deskripsi singkat data</h2>
<p>Data yang digunakan pada tutorial kali ini adalah data yang bernama Pima Indian Diabetes yang sudah sedikit diedit. Berikut adalah informasi singkat mengenai data</p>
<p>This dataset is originally from the National Institute of Diabetes and Digestive and Kidney Diseases. The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset. Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years old of Pima Indian heritage.</p>
<p>Content The datasets consists of several medical predictor variables and one target variable, Outcome. Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on.</p>
<p>Acknowledgements Smith, J.W., Everhart, J.E., Dickson, W.C., Knowler, W.C., &amp; Johannes, R.S. (1988). Using the ADAP learning algorithm to forecast the onset of diabetes mellitus. In Proceedings of the Symposium on Computer Applications and Medical Care (pp. 261–265). IEEE Computer Society Press.</p>
<p>data ini bisa diperoleh di link berikut ini <a href="https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN" class="uri">https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN</a></p>
<div id="import-data-di-r" class="section level3">
<h3>Import data di R</h3>
<div class="sourceCode" id="cb3"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1"></a>data_diabetes &lt;-<span class="st"> </span><span class="kw">read.csv</span>(<span class="st">&quot;diabetes.csv&quot;</span>,<span class="dt">stringsAsFactors =</span> <span class="ot">TRUE</span>)</span>
<span id="cb3-2"><a href="#cb3-2"></a><span class="kw">head</span>(data_diabetes)</span></code></pre></div>
<pre><code>##   Pregnancies Glucose BloodPressure SkinThickness Insulin  BMI
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
## 6                    0.201  30 Control</code></pre>
<p>Khusus yang menggunakan R versi 4.00 keatas, argumen <code>stringsAsFactors = TRUE</code> disertakan agar data yang berbentuk string bisa berubah menjadi factor.</p>
</div>
<div id="import-data-ke-ekosistem-mlr3" class="section level3">
<h3>Import data ke ekosistem mlr3</h3>
<p>Import data ke mlr3 bisa dilakukan dengan menggunakan fungsi <code>TaskClassif$new</code> atau <code>TaskRegr$new</code> yang berasal dari package <code>mlr3</code>. <code>TaskClassif$new</code> digunakan jika peubah respon kita berupa peubah biner atau multiclass, sedangkan <code>TaskRegr$new</code> digunakan jika responya berupa peubah numerik.</p>
<div class="sourceCode" id="cb5"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb5-1"><a href="#cb5-1"></a>task_diabetes =<span class="st"> </span>TaskClassif<span class="op">$</span><span class="kw">new</span>(<span class="dt">id=</span><span class="st">&quot;diabetes&quot;</span>,<span class="dt">backend =</span> data_diabetes,</span>
<span id="cb5-2"><a href="#cb5-2"></a>                                <span class="dt">target =</span> <span class="st">&quot;Outcome&quot;</span>,<span class="dt">positive =</span><span class="st">&quot;Case&quot;</span>)</span></code></pre></div>
<p>Argumen utama dalam fungsi <code>TaskClassif$new</code> adalah sebagai berikut:</p>
<ol style="list-style-type: decimal">
<li><code>id</code> yang merupakan nama dari task (bisa diisi dengan nama apapun)</li>
<li><code>backend</code> adalah data yang ingin dimodelkan dengan catatan peubah respon-nya harus berupa <strong>factor</strong></li>
<li><code>target</code> adalah nama kolom yang dijadikan peubah respon</li>
<li><code>positive</code> adalah nama kelas positif dari peubah respon</li>
</ol>
</div>
<div id="menentukan-model-yang-digunakan" class="section level3">
<h3>Menentukan model yang digunakan</h3>
<p>Pada tahap ini fungsi yang digunakan adalah <code>lrn</code> yang memiliki argumen utama <strong>nama model</strong> yang ingin digunakan. Berikut adalah model-model yang akan digunakan beserta argumen di dalam fungsi <code>lrn</code> dan asal packagenya:</p>
<ol style="list-style-type: decimal">
<li>Regresi Logistik - <code>"classif.log_reg"</code></li>
<li>KNN - <code>"classif.kknn"</code> - <code>library(kknn)</code></li>
<li>Decision Tree - <code>"classif.rpart"</code> - <code>library(rpart)</code></li>
<li>Naive Bayes - <code>"classif.naive_bayes"</code> - <code>library(e1071)</code></li>
<li>Random Forest - <code>"classif.ranger"</code> - <code>library(ranger)</code></li>
</ol>
<p>Sebagai catatan, untuk model-model yang digunakan dalam <code>mlr3</code> berasal dari package-package lain sehingga package-package tersebut perlu install terlebih dahulu. Kemudian, untuk model klasifikasi (respon biner atau multiclass) selalu diawali dengan kata <code>"classif."</code>. Sedangkan model regresi(respon numerik) diawali dengan kata <code>regr</code>. Selain itu, fungsi <code>lrn</code> juga memungkinkan untuk memasukan argumen-argumen dari package asalnya (termasuk hiperparameter). Sebagai contoh model KNN dari package <code>kknn</code> memiliki argumen-argumen yang bisa dilihat dengan menggunakan</p>
<div class="sourceCode" id="cb6"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb6-1"><a href="#cb6-1"></a><span class="kw">as.data.table</span>(<span class="kw">lrn</span>(<span class="st">&quot;classif.kknn&quot;</span>)<span class="op">$</span>param_set)</span></code></pre></div>
<pre><code>##          id    class lower upper
## 1:        k ParamInt     1   Inf
## 2: distance ParamDbl     0   Inf
## 3:   kernel ParamFct    NA    NA
## 4:    scale ParamLgl    NA    NA
## 5:  ykernel ParamUty    NA    NA
##                                                            levels nlevels
## 1:                                                                    Inf
## 2:                                                                    Inf
## 3: rectangular,triangular,epanechnikov,biweight,triweight,cos,...      10
## 4:                                                     TRUE,FALSE       2
## 5:                                                                    Inf
##    is_bounded special_vals default storage_type  tags
## 1:      FALSE    &lt;list[0]&gt;       7      integer train
## 2:      FALSE    &lt;list[0]&gt;       2      numeric train
## 3:       TRUE    &lt;list[0]&gt; optimal    character train
## 4:       TRUE    &lt;list[0]&gt;    TRUE      logical train
## 5:      FALSE    &lt;list[0]&gt;                 list train</code></pre>
<p>Berdasarkan output diatas argumen-argumen yang bisa digunakan dalam <code>classif.kknn</code> ada di kolom id. Selanjutnya, kolom class menunjukkan tipe data argumen tersebut. Kolom lower, upper dan levels merupakan isi/nilai dari argumen tersebut. Misalnya saja argumen k itu tipe datanya Interger dan nilai yang paling kecil bisa mengisi minimal 1.</p>
<p>Jika ingin mengetahui model-model apa saja yang sudah bisa dijalankan di ekosistem <code>mlr3</code> bisa dilihat pada link berikut:</p>
<ol style="list-style-type: decimal">
<li><a href="https://mlr3learners.mlr-org.com/" class="uri">https://mlr3learners.mlr-org.com/</a></li>
<li><a href="https://mlr3extralearners.mlr-org.com/articles/learners/list_learners.html" class="uri">https://mlr3extralearners.mlr-org.com/articles/learners/list_learners.html</a></li>
</ol>
<p>Untuk menjalankan model-model tersebut kita bisa tulis seperti dibawah ini</p>
<div class="sourceCode" id="cb8"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb8-1"><a href="#cb8-1"></a>learner_logreg &lt;-<span class="st"> </span><span class="kw">lrn</span>(<span class="st">&quot;classif.log_reg&quot;</span>)</span>
<span id="cb8-2"><a href="#cb8-2"></a>learner_knn &lt;-<span class="st"> </span><span class="kw">lrn</span>(<span class="st">&quot;classif.kknn&quot;</span>,<span class="dt">k=</span><span class="dv">10</span>,<span class="dt">kernel=</span><span class="st">&quot;rectangular&quot;</span>)</span>
<span id="cb8-3"><a href="#cb8-3"></a>learner_tree &lt;-<span class="st"> </span><span class="kw">lrn</span>(<span class="st">&quot;classif.rpart&quot;</span>)</span>
<span id="cb8-4"><a href="#cb8-4"></a>learner_nb &lt;-<span class="st"> </span><span class="kw">lrn</span>(<span class="st">&quot;classif.naive_bayes&quot;</span>)</span>
<span id="cb8-5"><a href="#cb8-5"></a>learner_rf &lt;-<span class="st"> </span><span class="kw">lrn</span>(<span class="st">&quot;classif.ranger&quot;</span>,<span class="dt">importance=</span><span class="st">&quot;impurity&quot;</span>)</span></code></pre></div>
</div>
<div id="menentukan-cara-pembagian-data" class="section level3">
<h3>Menentukan cara pembagian data</h3>
<p>Penentuan cara pembagian data bisa dilakukan dengan fungsi <code>rsmp</code>. Adapun pembagian data yang bisa digunakan dalam package <code>mlr3</code> adalah sebagai berikut</p>
<div class="sourceCode" id="cb9"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb9-1"><a href="#cb9-1"></a><span class="kw">as.data.table</span>(mlr_resamplings)</span></code></pre></div>
<pre><code>##            key        params iters
## 1:   bootstrap repeats,ratio    30
## 2:      custom                   0
## 3:          cv         folds    10
## 4:     holdout         ratio     1
## 5:    insample                   1
## 6:         loo                  NA
## 7: repeated_cv repeats,folds   100
## 8: subsampling repeats,ratio    30</code></pre>
<p>Pada kolom key adalah nama-nama dari tipe-tipe pembagian data. Penjelasan untuk masing-masing pembagian data tersebut dapat di cari di internet. Pada tutorial ini kita membagi data menjadi dua bagian yaitu data training dan data testing dengan proporsi data training sebesar 0.8 dari data dan data testing sebesar 0.2. Pembagian ini bisa dilakukan dengan menggunakan menggunakan menggunakan pembagian data <code>"holdout"</code> dan proporsi tadi bisa dipenuhi dengan menambahkan argumen <code>ratio=0.8</code>.</p>
<div class="sourceCode" id="cb11"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb11-1"><a href="#cb11-1"></a>resample_diabetes1 =<span class="st"> </span><span class="kw">rsmp</span>(<span class="st">&quot;holdout&quot;</span>, <span class="dt">ratio =</span> <span class="fl">0.8</span>)</span></code></pre></div>
<p>Pembagian data ini dimaksudkan untuk mengevaluasi kemampuan prediksi model untuk data baru.</p>
</div>
<div id="melakukan-interpretasi-model-jika-diperlukan" class="section level3">
<h3>Melakukan interpretasi model (jika diperlukan)</h3>
<p>Tahap ini biasanya dilakukan untuk melihat bagaimana pengaruh peubah-peubah prediktor terhadap respon menurut masing-masing model. Misalnya saja dalam regresi logistik besarnya nilai koefisien dan p value bisa menggambarkan bagaimana pengaruh peubah prediktor terhadap respon. Model-model yang akan digunakan untuk melihat pengaruh tersebut adalah regresi logistik, decision tree dan Random Forest. Berikut adalah sintaksnya</p>
<div class="sourceCode" id="cb12"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb12-1"><a href="#cb12-1"></a><span class="co"># Regresi Logistik</span></span>
<span id="cb12-2"><a href="#cb12-2"></a>learner_logreg<span class="op">$</span><span class="kw">train</span>(<span class="dt">task =</span> task_diabetes)</span>
<span id="cb12-3"><a href="#cb12-3"></a><span class="kw">summary</span>(learner_logreg<span class="op">$</span>model)</span></code></pre></div>
<pre><code>## 
## Call:
## stats::glm(formula = task$formula(), family = &quot;binomial&quot;, data = task$data(), 
##     model = FALSE)
## 
## Deviance Residuals: 
##     Min       1Q   Median       3Q      Max  
## -2.9139  -0.7278   0.4194   0.7338   2.5393  
## 
## Coefficients:
##                            Estimate Std. Error z value Pr(&gt;|z|)    
## (Intercept)               8.3697127  0.7241555  11.558  &lt; 2e-16 ***
## Age                      -0.0162950  0.0094134  -1.731 0.083443 .  
## BMI                      -0.0894983  0.0152167  -5.882 4.06e-09 ***
## BloodPressure             0.0136704  0.0052846   2.587 0.009686 ** 
## DiabetesPedigreeFunction -0.9255279  0.3006644  -3.078 0.002082 ** 
## Glucose                  -0.0349069  0.0037467  -9.317  &lt; 2e-16 ***
## Insulin                   0.0012331  0.0009118   1.352 0.176249    
## Pregnancies              -0.1188551  0.0322586  -3.684 0.000229 ***
## SkinThickness            -0.0014183  0.0069417  -0.204 0.838109    
## ---
## Signif. codes:  0 &#39;***&#39; 0.001 &#39;**&#39; 0.01 &#39;*&#39; 0.05 &#39;.&#39; 0.1 &#39; &#39; 1
## 
## (Dispersion parameter for binomial family taken to be 1)
## 
##     Null deviance: 972.27  on 751  degrees of freedom
## Residual deviance: 711.73  on 743  degrees of freedom
## AIC: 729.73
## 
## Number of Fisher Scoring iterations: 5</code></pre>
<div class="sourceCode" id="cb14"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb14-1"><a href="#cb14-1"></a><span class="co"># Decision Tree</span></span>
<span id="cb14-2"><a href="#cb14-2"></a>learner_tree<span class="op">$</span><span class="kw">train</span>(<span class="dt">task =</span> task_diabetes)</span>
<span id="cb14-3"><a href="#cb14-3"></a>rpart.plot<span class="op">::</span><span class="kw">rpart.plot</span>(learner_tree<span class="op">$</span>model,<span class="dt">roundint =</span> F,<span class="dt">type =</span> <span class="dv">5</span>,<span class="dt">tweak =</span> <span class="fl">1.75</span>)</span></code></pre></div>
<p><img src="Statistical-Learning_files/figure-html/unnamed-chunk-9-1.png" width="576" /></p>
<div class="sourceCode" id="cb15"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb15-1"><a href="#cb15-1"></a><span class="co"># Random Forest</span></span>
<span id="cb15-2"><a href="#cb15-2"></a>learner_rf<span class="op">$</span><span class="kw">train</span>(<span class="dt">task =</span> task_diabetes)</span>
<span id="cb15-3"><a href="#cb15-3"></a>learner_rf<span class="op">$</span>model<span class="op">$</span>variable.importance</span></code></pre></div>
<pre><code>##                      Age                      BMI            BloodPressure 
##                 46.75628                 56.15204                 30.14740 
## DiabetesPedigreeFunction                  Glucose                  Insulin 
##                 42.64641                 88.23512                 24.09207 
##              Pregnancies            SkinThickness 
##                 28.47267                 22.83240</code></pre>
<p>Catatan:</p>
<ol style="list-style-type: decimal">
<li>Data yang digunakan untuk menjalankan model-model tanpa pembagian data (training dan testing)</li>
<li><code>rpart.plot</code> berasal dari package <code>rpart.plot</code>.</li>
<li>Argumen <code>type</code> dalam <code>rpart.plot</code> digunakan untuk menentukan bagimana pohon di gambarkan. Argumen <code>tweak</code> digunakan untuk memperbesar gambar. Lihat help untuk lebih lengkapnya.</li>
<li>Nilai variable importance untuk Random Forest diatas adalah nilai Gini Impurity. Semakin besar nilainya maka akan semakin berpengaruh prediktor tersebut. Jika ingin mengetahui Gini Impurity secara lebih lengkap bisa melihat link berikut <a href="https://victorzhou.com/blog/gini-impurity/" class="uri">https://victorzhou.com/blog/gini-impurity/</a></li>
</ol>
<p>Dibawah ini merupakan sintaks untuk mengubah output variable importance ke dalam <code>data.frame</code> agar mudah untuk diurutkan dan di buat grafiknya.</p>
<div class="sourceCode" id="cb17"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb17-1"><a href="#cb17-1"></a>importance &lt;-<span class="st"> </span><span class="kw">data.frame</span>(<span class="dt">Predictors =</span> <span class="kw">names</span>(learner_rf<span class="op">$</span>model<span class="op">$</span>variable.importance),</span>
<span id="cb17-2"><a href="#cb17-2"></a>                         <span class="dt">impurity =</span> learner_rf<span class="op">$</span>model<span class="op">$</span>variable.importance</span>
<span id="cb17-3"><a href="#cb17-3"></a>                         )</span>
<span id="cb17-4"><a href="#cb17-4"></a><span class="kw">rownames</span>(importance) &lt;-<span class="st"> </span><span class="ot">NULL</span></span>
<span id="cb17-5"><a href="#cb17-5"></a></span>
<span id="cb17-6"><a href="#cb17-6"></a>importance <span class="op">%&gt;%</span><span class="st"> </span><span class="kw">arrange</span>(<span class="kw">desc</span>(impurity))</span></code></pre></div>
<pre><code>##                 Predictors impurity
## 1                  Glucose 88.23512
## 2                      BMI 56.15204
## 3                      Age 46.75628
## 4 DiabetesPedigreeFunction 42.64641
## 5            BloodPressure 30.14740
## 6              Pregnancies 28.47267
## 7                  Insulin 24.09207
## 8            SkinThickness 22.83240</code></pre>
</div>
<div id="melakukan-training-dan-menghitung-performa-model" class="section level3">
<h3>Melakukan training dan menghitung performa model</h3>
<p>Pada tahap ini kita bisa menerapkan model yang sudah kita definisikan diawal pada data training dan kemudian mengevaluasi kemampuan prediksi dengan data testing. Hal tersebut bisa dilakukan dengan menggunakan fungsi <code>resample</code>.</p>
<div class="sourceCode" id="cb19"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb19-1"><a href="#cb19-1"></a>train_test_diabetes =<span class="st"> </span><span class="kw">resample</span>(<span class="dt">task =</span> task_diabetes,</span>
<span id="cb19-2"><a href="#cb19-2"></a>                               <span class="dt">learner =</span> learner_knn,</span>
<span id="cb19-3"><a href="#cb19-3"></a>                               <span class="dt">resampling =</span> resample_diabetes1,</span>
<span id="cb19-4"><a href="#cb19-4"></a>                               <span class="dt">store_models =</span> <span class="ot">TRUE</span></span>
<span id="cb19-5"><a href="#cb19-5"></a>                               )</span></code></pre></div>
<pre><code>## INFO  [18:39:35.576] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 1/1)</code></pre>
<p>Berdasarkan sintaks diatas kita melakukan training untuk model KNN, jika ingin melakukan training untuk model lainnya cukup ganti <code>learner=learner_knn</code> dengan <code>learner_logreg</code>,<code>learner_nb</code>,<code>learner_tree</code> dan <code>learner_rf</code>.</p>
<p>Jika kita ingin mengeluarkan hasil prediksi pada data testing bisa menggunakan sintaks dibawah ini.</p>
<div class="sourceCode" id="cb21"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb21-1"><a href="#cb21-1"></a>prediksi_test =<span class="st"> </span><span class="kw">as.data.table</span>(train_test_diabetes<span class="op">$</span><span class="kw">prediction</span>())</span>
<span id="cb21-2"><a href="#cb21-2"></a><span class="kw">head</span>(prediksi_test)</span></code></pre></div>
<pre><code>##    row_id   truth response
## 1:      6 Control  Control
## 2:     10 Control  Control
## 3:     16    Case  Control
## 4:     22    Case     Case
## 5:     31    Case  Control
## 6:     32 Control  Control</code></pre>
<p>Confusion matrix bisa dikeluarkan dengan sintaks dibawah ini</p>
<div class="sourceCode" id="cb23"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb23-1"><a href="#cb23-1"></a>train_test_diabetes<span class="op">$</span><span class="kw">prediction</span>()<span class="op">$</span>confusion</span></code></pre></div>
<pre><code>##          truth
## response  Case Control
##   Case      26      12
##   Control   27      85</code></pre>
<p>Untuk menghitung performa model dengan menggunakan ukuran akurasi bisa menggunakan sintaks dibawah ini. Fungsi <code>msr</code> merupakan fungsi yang dapat mengakses ukuran-ukuran kebaikan model yang ada di dalam package <code>mlr3</code>.</p>
<div class="sourceCode" id="cb25"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb25-1"><a href="#cb25-1"></a>train_test_diabetes<span class="op">$</span><span class="kw">aggregate</span>(<span class="kw">msr</span>(<span class="st">&quot;classif.acc&quot;</span>))</span></code></pre></div>
<pre><code>## classif.acc 
##        0.74</code></pre>
<p>Ukuran kebaikan model yang ada di package <code>mlr3</code> bisa dilihat di link <a href="https://mlr3.mlr-org.com/reference/mlr_measures.html" class="uri">https://mlr3.mlr-org.com/reference/mlr_measures.html</a>. Sebagai catatan, terdapat beberapa ukuran yang membutuhkan prediksi yang dikeluarkan berupa peluang bukan berupa kelas.</p>
<p>Kemudian jika ada lebih dari satu ukuran kebaikan model yang ingin kita gunakan, kita bisa melakukannya dengan sintaks dibawah ini.</p>
<div class="sourceCode" id="cb27"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb27-1"><a href="#cb27-1"></a>train_test_diabetes<span class="op">$</span><span class="kw">aggregate</span>(<span class="kw">list</span>(<span class="kw">msr</span>(<span class="st">&quot;classif.acc&quot;</span>),</span>
<span id="cb27-2"><a href="#cb27-2"></a>                                   <span class="kw">msr</span>(<span class="st">&quot;classif.specificity&quot;</span>),</span>
<span id="cb27-3"><a href="#cb27-3"></a>                                   <span class="kw">msr</span>(<span class="st">&quot;classif.sensitivity&quot;</span>)</span>
<span id="cb27-4"><a href="#cb27-4"></a>                                   ))</span></code></pre></div>
<pre><code>##         classif.acc classif.specificity classif.sensitivity 
##           0.7400000           0.8762887           0.4905660</code></pre>
</div>
<div id="komparasi-model" class="section level3">
<h3>Komparasi model</h3>
<p>Pada bagian ini kita akan melakukan komparasi model antar model yang sudah kita definisikan diatas. Langkah pertama yang kita lakukan adalah mengabungkan learner yang sudah kita definisikan diawal ke dalam list</p>
<div class="sourceCode" id="cb29"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb29-1"><a href="#cb29-1"></a>learner_diabetes &lt;-<span class="st"> </span><span class="kw">list</span>(learner_logreg,learner_knn,</span>
<span id="cb29-2"><a href="#cb29-2"></a>                         learner_tree,learner_nb,learner_rf)</span></code></pre></div>
<p>Langkah berikutnya kita menentukan metode pembagian data. Metode pembagian data yang awal yang sudah disimpan pada objek <code>resample_diabetes1</code> bisa kita gunakan. Namun disini kita akan mencoba untuk menggunakan metode cross-validation</p>
<div class="sourceCode" id="cb30"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb30-1"><a href="#cb30-1"></a>resample_diabetes_cv =<span class="st"> </span><span class="kw">rsmp</span>(<span class="st">&quot;cv&quot;</span>,<span class="dt">folds=</span><span class="dv">10</span>)</span></code></pre></div>
<p>Metode pembagian data yang dipilih disini adalah metode cross-validation dengan 10 folds atau lipatan. Setelah kedua hal ini sudah dilakukan, selanjutnya komparasi model bisa dilakukan</p>
<p>Komparasi model bisa dilakukan dengan menggunakan fungsi <code>benchmark_design</code> dan <code>benchmark</code>. Fungsi <code>benchmark_design</code> digunakan untuk memasukan informasi-inforamsi yang dibutuhkan untuk komparasi, seperti data yang digunakan (tasks), model yang ingin dikomparasi (learners) dan metode pembagian data yang digunakan (resamplings).</p>
<div class="sourceCode" id="cb31"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb31-1"><a href="#cb31-1"></a>design &lt;-<span class="st"> </span><span class="kw">benchmark_grid</span>(<span class="dt">tasks =</span> task_diabetes,</span>
<span id="cb31-2"><a href="#cb31-2"></a>                         <span class="dt">learners =</span> learner_diabetes,</span>
<span id="cb31-3"><a href="#cb31-3"></a>                         <span class="dt">resamplings =</span> resample_diabetes_cv </span>
<span id="cb31-4"><a href="#cb31-4"></a>                         )</span></code></pre></div>
<p>Kemudian fungsi <code>benchmark</code> digunakan untuk menjalankan/ running komparasi model berdasarkan desain yang sudah dirancang.</p>
<div class="sourceCode" id="cb32"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb32-1"><a href="#cb32-1"></a>bmr =<span class="st"> </span><span class="kw">benchmark</span>(design,<span class="dt">store_models =</span> <span class="ot">TRUE</span>)</span></code></pre></div>
<pre><code>## INFO  [18:39:36.293] Benchmark with 50 resampling iterations 
## INFO  [18:39:36.312] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 1/10) 
## INFO  [18:39:36.402] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 7/10) 
## INFO  [18:39:36.501] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 2/10) 
## INFO  [18:39:36.541] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 9/10) 
## INFO  [18:39:36.576] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 6/10) 
## INFO  [18:39:36.600] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 6/10) 
## INFO  [18:39:36.702] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 7/10) 
## INFO  [18:39:36.754] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 5/10) 
## INFO  [18:39:36.778] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 8/10) 
## INFO  [18:39:36.800] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 8/10) 
## INFO  [18:39:36.833] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 6/10) 
## INFO  [18:39:36.865] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 6/10) 
## INFO  [18:39:36.898] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 5/10) 
## INFO  [18:39:37.173] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 4/10) 
## INFO  [18:39:37.282] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 3/10) 
## INFO  [18:39:37.330] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 6/10) 
## INFO  [18:39:37.352] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 4/10) 
## INFO  [18:39:37.384] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 9/10) 
## INFO  [18:39:37.495] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 2/10) 
## INFO  [18:39:37.535] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 1/10) 
## INFO  [18:39:37.571] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 8/10) 
## INFO  [18:39:37.593] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 1/10) 
## INFO  [18:39:37.614] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 3/10) 
## INFO  [18:39:37.636] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 7/10) 
## INFO  [18:39:37.658] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 5/10) 
## INFO  [18:39:37.698] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 10/10) 
## INFO  [18:39:37.719] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 1/10) 
## INFO  [18:39:37.806] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 10/10) 
## INFO  [18:39:37.825] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 5/10) 
## INFO  [18:39:37.852] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 9/10) 
## INFO  [18:39:37.881] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 5/10) 
## INFO  [18:39:37.995] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 4/10) 
## INFO  [18:39:38.021] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 10/10) 
## INFO  [18:39:38.046] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 4/10) 
## INFO  [18:39:38.063] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 8/10) 
## INFO  [18:39:38.090] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 7/10) 
## INFO  [18:39:38.108] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 2/10) 
## INFO  [18:39:38.134] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 3/10) 
## INFO  [18:39:38.160] Applying learner &#39;classif.kknn&#39; on task &#39;diabetes&#39; (iter 10/10) 
## INFO  [18:39:38.197] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 2/10) 
## INFO  [18:39:38.278] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 1/10) 
## INFO  [18:39:38.293] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 3/10) 
## INFO  [18:39:38.311] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 10/10) 
## INFO  [18:39:38.584] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 2/10) 
## INFO  [18:39:38.604] Applying learner &#39;classif.rpart&#39; on task &#39;diabetes&#39; (iter 9/10) 
## INFO  [18:39:38.619] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 8/10) 
## INFO  [18:39:38.693] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 7/10) 
## INFO  [18:39:38.714] Applying learner &#39;classif.log_reg&#39; on task &#39;diabetes&#39; (iter 9/10) 
## INFO  [18:39:38.728] Applying learner &#39;classif.ranger&#39; on task &#39;diabetes&#39; (iter 3/10) 
## INFO  [18:39:38.797] Applying learner &#39;classif.naive_bayes&#39; on task &#39;diabetes&#39; (iter 4/10) 
## INFO  [18:39:38.821] Finished benchmark</code></pre>
<p>Karena terdapat 5 model dan masing-masing model menjalankan 10-folds cross-validation maka iterasi yang dilakukan ada sebanyak 50 kali.</p>
</div>
<div id="hasil-komparasi-model" class="section level3">
<h3>Hasil Komparasi model</h3>
<p>Hasil komparasi model dapat berupa nilai-nilai ukuran kebaikan model yang ditentukan oleh pengguna.</p>
<div class="sourceCode" id="cb34"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb34-1"><a href="#cb34-1"></a>result =<span class="st"> </span>bmr<span class="op">$</span><span class="kw">aggregate</span>(<span class="kw">msr</span>(<span class="st">&quot;classif.acc&quot;</span>)</span>
<span id="cb34-2"><a href="#cb34-2"></a>              )</span>
<span id="cb34-3"><a href="#cb34-3"></a>result</span></code></pre></div>
<pre><code>##    nr      resample_result  task_id          learner_id resampling_id iters
## 1:  1 &lt;ResampleResult[21]&gt; diabetes     classif.log_reg            cv    10
## 2:  2 &lt;ResampleResult[21]&gt; diabetes        classif.kknn            cv    10
## 3:  3 &lt;ResampleResult[21]&gt; diabetes       classif.rpart            cv    10
## 4:  4 &lt;ResampleResult[21]&gt; diabetes classif.naive_bayes            cv    10
## 5:  5 &lt;ResampleResult[21]&gt; diabetes      classif.ranger            cv    10
##    classif.acc
## 1:   0.7725789
## 2:   0.7473860
## 3:   0.7646842
## 4:   0.7593333
## 5:   0.7699298</code></pre>
<p>Berdasarkan nilai akurasi model yang memiliki performa prediksi terbaik adalah model regresi logistik.</p>
</div>
<div id="memprediksi-respon-pada-data-baru-jika-tersedia" class="section level3">
<h3>Memprediksi respon pada data baru (jika tersedia)</h3>
<p>Pada bagian ini akan diilustrasikan bagimana jika kita menerima data baru yang tidak memiliki peubah respon. Berikut dibawah ini adalah datanya. Datanya bisa di download di link berikut</p>
<p><a href="https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN" class="uri">https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN</a></p>
<div class="sourceCode" id="cb36"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb36-1"><a href="#cb36-1"></a>data_diabetes_baru &lt;-<span class="st"> </span><span class="kw">read.csv</span>(<span class="st">&quot;diabetes_baru.csv&quot;</span>)</span>
<span id="cb36-2"><a href="#cb36-2"></a><span class="kw">head</span>(data_diabetes)</span></code></pre></div>
<pre><code>##   Pregnancies Glucose BloodPressure SkinThickness Insulin  BMI
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
## 6                    0.201  30 Control</code></pre>
<p>Sebagai contoh kita menggunakan model regresi logistik sebagai model terbaik, berikut sintaksnya.</p>
<div class="sourceCode" id="cb38"><pre class="sourceCode r"><code class="sourceCode r"><span id="cb38-1"><a href="#cb38-1"></a>learner_logreg<span class="op">$</span><span class="kw">train</span>(<span class="dt">task =</span> task_diabetes)</span>
<span id="cb38-2"><a href="#cb38-2"></a>prediksi_data_baru_logreg &lt;-<span class="st"> </span>learner_logreg<span class="op">$</span><span class="kw">predict_newdata</span>(<span class="dt">newdata =</span> data_diabetes_baru)</span>
<span id="cb38-3"><a href="#cb38-3"></a><span class="kw">as.data.table</span>(prediksi_data_baru_logreg)</span></code></pre></div>
<pre><code>##     row_id truth response
##  1:      1  &lt;NA&gt;     Case
##  2:      2  &lt;NA&gt;  Control
##  3:      3  &lt;NA&gt;  Control
##  4:      4  &lt;NA&gt;     Case
##  5:      5  &lt;NA&gt;  Control
##  6:      6  &lt;NA&gt;  Control
##  7:      7  &lt;NA&gt;     Case
##  8:      8  &lt;NA&gt;  Control
##  9:      9  &lt;NA&gt;  Control
## 10:     10  &lt;NA&gt;     Case
## 11:     11  &lt;NA&gt;     Case
## 12:     12  &lt;NA&gt;  Control
## 13:     13  &lt;NA&gt;  Control
## 14:     14  &lt;NA&gt;     Case
## 15:     15  &lt;NA&gt;     Case
## 16:     16  &lt;NA&gt;  Control</code></pre>
<p>Fungsi <code>$train</code> digunakan untuk melakukan training pada data keseluruhan (tanpa ada proses pembagian data). Terakhir, fungsi <code>predict_newdata</code> digunakan untuk melakukan prediksi pada data baru.</p>
</div>
</div>
</div>

   
   
      </div>
   <div class="col-md-2">
          <div id="toc">
       <button type="button" class="close">×</button>
       <ul>
       <li><a href="#statistical-learning-di-r">Statistical Learning di R</a></li>
       <li><a href="#package">Package</a></li>
       <li><a href="#deskripsi-singkat-data">Deskripsi singkat data</a></li>
       </ul>
     </div>
        </div>
   </div>
   </div>
            
      

  <script>
    $(document).ready(function () {

		// add bootstrap table styles to pandoc tables
	$('tr.header').parent('thead').parent('table').addClass('table table-condensed');
		
 	 	$('#content img').addClass("image-thumb");
		
		$('#content img').addClass("image-lb");
	$('#content').magnificPopup({
	    type:'image',
	    closeOnContentClick: false,
	    closeBtnInside: false,
	    delegate: '.image-lb',
	    gallery: {enabled: false },
	    image: {
	        verticalFit: true,
		titleSrc: 'alt'
	    }
 	});
 	    });
  </script>



    <!-- dynamically load mathjax for compatibility with self-contained -->
  <script>
    (function () {
	var script = document.createElement("script");
	script.type = "text/javascript";
	script.src  = "https://mathjax.rstudio.com/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML";
	document.getElementsByTagName("head")[0].appendChild(script);
    })();
  </script>
  
</body>
</html>
