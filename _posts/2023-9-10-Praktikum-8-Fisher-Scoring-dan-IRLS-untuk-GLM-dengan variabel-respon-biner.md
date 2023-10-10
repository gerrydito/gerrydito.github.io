<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en"><head>

<meta charset="utf-8">
<meta name="generator" content="quarto-1.2.269">

<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">


<title>Praktikum GLM 8 - Fisher Scoring dan IRLS untuk GLM dengan variabel respon biner</title>
<style>
code{white-space: pre-wrap;}
span.smallcaps{font-variant: small-caps;}
div.columns{display: flex; gap: min(4vw, 1.5em);}
div.column{flex: auto; overflow-x: auto;}
div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
ul.task-list{list-style: none;}
ul.task-list li input[type="checkbox"] {
  width: 0.8em;
  margin: 0 0.8em 0.2em -1.6em;
  vertical-align: middle;
}
pre > code.sourceCode { white-space: pre; position: relative; }
pre > code.sourceCode > span { display: inline-block; line-height: 1.25; }
pre > code.sourceCode > span:empty { height: 1.2em; }
.sourceCode { overflow: visible; }
code.sourceCode > span { color: inherit; text-decoration: inherit; }
div.sourceCode { margin: 1em 0; }
pre.sourceCode { margin: 0; }
@media screen {
div.sourceCode { overflow: auto; }
}
@media print {
pre > code.sourceCode { white-space: pre-wrap; }
pre > code.sourceCode > span { text-indent: -5em; padding-left: 5em; }
}
pre.numberSource code
  { counter-reset: source-line 0; }
pre.numberSource code > span
  { position: relative; left: -4em; counter-increment: source-line; }
pre.numberSource code > span > a:first-child::before
  { content: counter(source-line);
    position: relative; left: -1em; text-align: right; vertical-align: baseline;
    border: none; display: inline-block;
    -webkit-touch-callout: none; -webkit-user-select: none;
    -khtml-user-select: none; -moz-user-select: none;
    -ms-user-select: none; user-select: none;
    padding: 0 4px; width: 4em;
    color: #aaaaaa;
  }
pre.numberSource { margin-left: 3em; border-left: 1px solid #aaaaaa;  padding-left: 4px; }
div.sourceCode
  {   }
@media screen {
pre > code.sourceCode > span > a:first-child::before { text-decoration: underline; }
}
code span.al { color: #ff0000; font-weight: bold; } /* Alert */
code span.an { color: #60a0b0; font-weight: bold; font-style: italic; } /* Annotation */
code span.at { color: #7d9029; } /* Attribute */
code span.bn { color: #40a070; } /* BaseN */
code span.bu { color: #008000; } /* BuiltIn */
code span.cf { color: #007020; font-weight: bold; } /* ControlFlow */
code span.ch { color: #4070a0; } /* Char */
code span.cn { color: #880000; } /* Constant */
code span.co { color: #60a0b0; font-style: italic; } /* Comment */
code span.cv { color: #60a0b0; font-weight: bold; font-style: italic; } /* CommentVar */
code span.do { color: #ba2121; font-style: italic; } /* Documentation */
code span.dt { color: #902000; } /* DataType */
code span.dv { color: #40a070; } /* DecVal */
code span.er { color: #ff0000; font-weight: bold; } /* Error */
code span.ex { } /* Extension */
code span.fl { color: #40a070; } /* Float */
code span.fu { color: #06287e; } /* Function */
code span.im { color: #008000; font-weight: bold; } /* Import */
code span.in { color: #60a0b0; font-weight: bold; font-style: italic; } /* Information */
code span.kw { color: #007020; font-weight: bold; } /* Keyword */
code span.op { color: #666666; } /* Operator */
code span.ot { color: #007020; } /* Other */
code span.pp { color: #bc7a00; } /* Preprocessor */
code span.sc { color: #4070a0; } /* SpecialChar */
code span.ss { color: #bb6688; } /* SpecialString */
code span.st { color: #4070a0; } /* String */
code span.va { color: #19177c; } /* Variable */
code span.vs { color: #4070a0; } /* VerbatimString */
code span.wa { color: #60a0b0; font-weight: bold; font-style: italic; } /* Warning */
</style>


<script src="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/clipboard/clipboard.min.js"></script>
<script src="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/quarto-html/quarto.js"></script>
<script src="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/quarto-html/popper.min.js"></script>
<script src="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/quarto-html/tippy.umd.min.js"></script>
<script src="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/quarto-html/anchor.min.js"></script>
<link href="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/quarto-html/tippy.css" rel="stylesheet">
<link href="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/quarto-html/quarto-syntax-highlighting.css" rel="stylesheet" id="quarto-text-highlighting-styles">
<script src="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/bootstrap/bootstrap.min.js"></script>
<link href="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/bootstrap/bootstrap-icons.css" rel="stylesheet">
<link href="Praktikum-8-Fisher-Scoring-dan-IRLS-untuk-GLM-dengan variabel-respon-biner_files/libs/bootstrap/bootstrap.min.css" rel="stylesheet" id="quarto-bootstrap" data-mode="light">

  <script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js" type="text/javascript"></script>

</head>

<body>

<div id="quarto-content" class="page-columns page-rows-contents page-layout-article toc-left">
<div id="quarto-sidebar-toc-left" class="sidebar toc-left">
  <nav id="TOC" role="doc-toc" class="toc-active">
    <h2 id="toc-title">Table of contents</h2>
   
  <ul>
  <li><a href="#package" id="toc-package" class="nav-link active" data-scroll-target="#package">Package</a></li>
  <li><a href="#fisher-scoring-untuk-glm" id="toc-fisher-scoring-untuk-glm" class="nav-link" data-scroll-target="#fisher-scoring-untuk-glm">Fisher Scoring untuk GLM</a></li>
  <li><a href="#iteratively-reweighted-least-squares-irls-untuk-glm" id="toc-iteratively-reweighted-least-squares-irls-untuk-glm" class="nav-link" data-scroll-target="#iteratively-reweighted-least-squares-irls-untuk-glm">Iteratively reweighted least squares (IRLS) untuk GLM</a></li>
  <li><a href="#data" id="toc-data" class="nav-link" data-scroll-target="#data">Data</a></li>
  <li><a href="#import-data" id="toc-import-data" class="nav-link" data-scroll-target="#import-data">Import Data</a></li>
  <li><a href="#fisher-scoring-dan-irls-untuk-binomial-glm" id="toc-fisher-scoring-dan-irls-untuk-binomial-glm" class="nav-link" data-scroll-target="#fisher-scoring-dan-irls-untuk-binomial-glm">Fisher Scoring dan IRLS untuk Binomial GLM</a>
  <ul>
  <li><a href="#binomial-sebagai-distribusi-keluarga-eksponensial" id="toc-binomial-sebagai-distribusi-keluarga-eksponensial" class="nav-link" data-scroll-target="#binomial-sebagai-distribusi-keluarga-eksponensial">Binomial sebagai distribusi keluarga eksponensial</a></li>
  <li><a href="#mendefiniskan-matriks-untuk-fisher-scoring-dan-irls" id="toc-mendefiniskan-matriks-untuk-fisher-scoring-dan-irls" class="nav-link" data-scroll-target="#mendefiniskan-matriks-untuk-fisher-scoring-dan-irls">Mendefiniskan matriks untuk Fisher Scoring dan IRLS</a></li>
  <li><a href="#fisher-scoring" id="toc-fisher-scoring" class="nav-link" data-scroll-target="#fisher-scoring">Fisher Scoring</a></li>
  <li><a href="#irls" id="toc-irls" class="nav-link" data-scroll-target="#irls">IRLS</a></li>
  <li><a href="#default-fungsi-r" id="toc-default-fungsi-r" class="nav-link" data-scroll-target="#default-fungsi-r">Default fungsi R</a></li>
  </ul></li>
  </ul>
</nav>
</div>
<div id="quarto-margin-sidebar" class="sidebar margin-sidebar">
</div>
<main class="content" id="quarto-document-content">

<header id="title-block-header" class="quarto-title-block default">



<div class="quarto-title-meta">

    
  
    
  </div>
  

</header>

<section id="package" class="level2">
<h2 class="anchored" data-anchor-id="package">Package</h2>
<div class="cell">
<div class="sourceCode cell-code" id="cb1"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(tidyverse)</span>
<span id="cb1-2"><a href="#cb1-2" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(Matrix)</span>
<span id="cb1-3"><a href="#cb1-3" aria-hidden="true" tabindex="-1"></a><span class="fu">library</span>(broom)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
</section>
<section id="fisher-scoring-untuk-glm" class="level2">
<h2 class="anchored" data-anchor-id="fisher-scoring-untuk-glm">Fisher Scoring untuk GLM</h2>
<p>Formula Fisher Scoring yang digunakan untuk mendapatkan penduga bagi koefisien GLM adalah sebagai berikut:</p>
<p><span class="math display">\[
\boldsymbol{\beta}_{(p+1) \times 1}^{(i+1)}=\boldsymbol{\beta}_{(p+1) \times 1}^{(i)} + \left[\boldsymbol{\mathcal{I}}_{p \times p }^{(i)} \right]^{-1} \boldsymbol{S}_{(p+1) \times 1}^{(i)}
\]</span></p>
<p>dengan</p>
<p><span class="math display">\[
\boldsymbol{S}_{(p+1) \times 1}^{(i)}= \boldsymbol{X}^{t}_{ (p+1) \times n} \boldsymbol{W}_{n \times n} ^{(i)} (\boldsymbol{D}_{n \times n}^{(i)})^{-1} (\boldsymbol{y}_{n \times 1}-\boldsymbol{\mu}_{n \times 1}^{(i)})
\]</span> dan</p>
<p><span class="math display">\[
\boldsymbol{\mathcal{I}}_{p \times p }^{(i)}=\boldsymbol{X}^{t}_{ (p+1) \times n} \boldsymbol{W}_{n \times n} ^{(i)}  \boldsymbol{X}_{n \times (p+1)}
\]</span></p>
<p>Algoritme Fisher Scoring dapat dituliskan sebagai berikut:</p>
<ol type="1">
<li>Tentukan perkiraan awal nilai optimal <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(0)}\)</span> dan stopping criterion</li>
<li>Tentukan Score function <span class="math inline">\(\boldsymbol{S}_{(p+1) \times 1}^{(0)}\)</span> dan Expected Fisher Information <span class="math inline">\(\boldsymbol{\mathcal{I}}_{p \times p }^{(0)}\)</span>.</li>
<li>Hitung <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(1)}=\boldsymbol{\beta}_{(p+1) \times 1}^{(0)} + \left[\boldsymbol{\mathcal{I}}_{p \times p }^{(0)} \right]^{-1} \boldsymbol{S}_{(p+1) \times 1}^{(0)}\)</span>, sehingga diperoleh perkiraan nilai optimal <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(1)}\)</span></li>
<li>Lakukan Langkah 5 sampai stopping criterion terpenuhi</li>
<li>Hitung <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(i+1)}=\boldsymbol{\beta}_{(p+1) \times 1}^{(i)} + \left[\boldsymbol{\mathcal{I}}_{p \times p }^{(i)} \right]^{-1} \boldsymbol{S}_{(p+1) \times 1}^{(i)}\)</span> untuk iterasi <span class="math inline">\(i=1,2,\ldots\)</span></li>
<li>Saat stopping criterion terpenuhi maka <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(i+1)}\)</span> merupakan nilai penduga bagi parameter <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}\)</span></li>
<li>Ragam dari <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}\)</span> diperoleh dengan $Var(_{(p+1)})=^{-1} $saat stopping criterion terpenuhi</li>
</ol>
</section>
<section id="iteratively-reweighted-least-squares-irls-untuk-glm" class="level2">
<h2 class="anchored" data-anchor-id="iteratively-reweighted-least-squares-irls-untuk-glm">Iteratively reweighted least squares (IRLS) untuk GLM</h2>
<p>IRLS untuk GLM merupakan hasil reformulasi dari Fisher Scoring untuk GLM. Berikut proses penurunanya</p>
<p><span class="math display">\[
\begin{aligned}
\boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)} &amp;= \boldsymbol{\beta}_{((𝑝+1)×1)}^{(i)}+[\boldsymbol{\mathcal{I}}_{p\times p}^{(i)} ]^{−1} \boldsymbol{S}_{(𝑝+1)×1}^{(i)} \\
   \boldsymbol{\mathcal{I}}_{p\times p}^{(i)}  \boldsymbol{\beta}_{(𝑝+1)×1}^{(𝑖+1)}              &amp;= \boldsymbol{\mathcal{I}}_{p\times p}^{(i)} \boldsymbol{\beta}_{((𝑝+1)×1)}^{(i)}+ \boldsymbol{S}_{(𝑝+1)×1}^{(i)}
\end{aligned}
\]</span></p>
<p>kemudiann dengan mensubtitusikan <span class="math inline">\(\boldsymbol{\mathcal{I}}_{p\times p}^{(i)}\)</span> dan <span class="math inline">\(\boldsymbol{S}_{(𝑝+1)×1}^{(i)}\)</span> sesuai dengan definisi yang ada di fisher scoring, didapat</p>
<p><span class="math display">\[
\begin{aligned}
\left\{ \boldsymbol{X}_{(𝑝+1) \times n }^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\} \boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)}              &amp;=  \left\{ \boldsymbol{X}_{(𝑝+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\} \boldsymbol{\beta}_{((𝑝+1)×1)}^{(i)}+ \left[ \boldsymbol{X}_{(𝑝+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} (\boldsymbol{D}_{n \times n}^{^{(i)}})^{-1} (\boldsymbol{y}_{n \times 1}−\boldsymbol{\mu}_{𝑛×1}^{(i)}) \right] \\
&amp;= \boldsymbol{X}_{(𝑝+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \left[\boldsymbol{X}_{(𝑝+1) \times n}^{t}\boldsymbol{\beta}_{((𝑝+1)×1)}^{(i)} + (\boldsymbol{D}_{n \times n}^{^{(i)}})^{-1} (\boldsymbol{y}_{n \times 1}−\boldsymbol{\mu}_{𝑛×1}^{(i)}) \right] \\
&amp;\text{ misal }  \boldsymbol{z}_{n \times1}=\boldsymbol{X}_{(𝑝+1) \times n}^{t}\boldsymbol{\beta}_{((𝑝+1)×1)}^{(i)} + (\boldsymbol{D}_{n \times n}^{^{(i)}})^{-1} (\boldsymbol{y}_{n \times 1}−\boldsymbol{\mu}_{𝑛×1}^{(i)})  \\
&amp;=\boldsymbol{X}_{(p+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)}
\end{aligned}
\]</span></p>
<p>maka diperoleh persamaan normal (normal equation) sebagai berikut:</p>
<p><span class="math display">\[
\begin{aligned}
\left\{ \boldsymbol{X}_{(𝑝+1) \times n }^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)} \right\} \boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)} &amp;= \boldsymbol{X}_{ (p+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)} \\
\boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)}  &amp;= \left\{ \boldsymbol{X}_{ (p+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\}^{-1} \boldsymbol{X}_{ (p+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)}
\end{aligned}
\]</span></p>
<p>Kemudian, solusi dari persamaan normal diatas adalah</p>
<p><span class="math display">\[
\boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)}  = \left\{ \boldsymbol{X}_{(𝑝+1) \times n }^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\}^{-1} \boldsymbol{X}_{(𝑝+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)}
\]</span></p>
<p>jadi, formulasi untuk IRLS adalah</p>
<p><span class="math display">\[
\boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)}  = \left\{ \boldsymbol{X}_{n \times (𝑝+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\}^{-1} \boldsymbol{X}_{n \times (p+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)}
\]</span></p>
<p>Algoritme Fisher Scoring dapat dituliskan sebagai berikut:</p>
<ol type="1">
<li>Tentukan perkiraan awal nilai optimal <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(0)}\)</span> dan stopping criterion</li>
<li>Tentukan <span class="math inline">\(\boldsymbol{W}_{n \times n}^{(0)}\)</span> dan <span class="math inline">\(\boldsymbol{z}_{n \times1}^{(0)}\)</span>.</li>
<li>Hitung <span class="math inline">\(\boldsymbol{\beta}_{(p+1)×1}^{(1)} = \left\{ \boldsymbol{X}_{n \times (𝑝+1)}^{t} \boldsymbol{W}_{n \times n}^{(0)} \boldsymbol{X}_{n \times (𝑝+1)} \right\}^{-1} \boldsymbol{X}_{n \times (p+1)}^{t} \boldsymbol{W}_{n \times n}^{(0)} \boldsymbol{z}_{n \times1}^{(0)}\)</span>, sehingga diperoleh perkiraan nilai optimal <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(1)}\)</span></li>
<li>Lakukan Langkah 5 sampai stopping criterion terpenuhi</li>
<li>Hitung <span class="math inline">\(\boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)} = \left\{ \boldsymbol{X}_{n \times (𝑝+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)} \right\}^{-1} \boldsymbol{X}_{n \times (p+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)}\)</span> untuk iterasi <span class="math inline">\(i=1,2,\ldots\)</span></li>
<li>Saat stopping criterion terpenuhi maka <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}^{(i+1)}\)</span> merupakan nilai penduga bagi parameter <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}\)</span></li>
<li>Ragam dari <span class="math inline">\(\boldsymbol{\beta}_{(p+1) \times 1}\)</span> diperoleh dengan <span class="math inline">\(Var(\boldsymbol{\beta}_{(p+1)})=\left\{ \boldsymbol{X}_{n \times (𝑝+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)} \right\}^{-1}\)</span>saat stopping criterion terpenuhi</li>
</ol>
</section>
<section id="data" class="level2">
<h2 class="anchored" data-anchor-id="data">Data</h2>
<div class="cell">
<div class="cell-output-display">

<div id="petjltdqfv" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>#petjltdqfv table {
  font-family: system-ui, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', 'Noto Color Emoji';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#petjltdqfv thead, #petjltdqfv tbody, #petjltdqfv tfoot, #petjltdqfv tr, #petjltdqfv td, #petjltdqfv th {
  border-style: none;
}

#petjltdqfv p {
  margin: 0;
  padding: 0;
}

#petjltdqfv .gt_table {
  display: table;
  border-collapse: collapse;
  line-height: normal;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #A8A8A8;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #A8A8A8;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#petjltdqfv .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#petjltdqfv .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#petjltdqfv .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 3px;
  padding-bottom: 5px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#petjltdqfv .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#petjltdqfv .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#petjltdqfv .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#petjltdqfv .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#petjltdqfv .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#petjltdqfv .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#petjltdqfv .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#petjltdqfv .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#petjltdqfv .gt_spanner_row {
  border-bottom-style: hidden;
}

#petjltdqfv .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#petjltdqfv .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  vertical-align: middle;
}

#petjltdqfv .gt_from_md > :first-child {
  margin-top: 0;
}

#petjltdqfv .gt_from_md > :last-child {
  margin-bottom: 0;
}

#petjltdqfv .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#petjltdqfv .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
}

#petjltdqfv .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#petjltdqfv .gt_row_group_first td {
  border-top-width: 2px;
}

#petjltdqfv .gt_row_group_first th {
  border-top-width: 2px;
}

#petjltdqfv .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#petjltdqfv .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#petjltdqfv .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#petjltdqfv .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#petjltdqfv .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#petjltdqfv .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#petjltdqfv .gt_last_grand_summary_row_top {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: double;
  border-bottom-width: 6px;
  border-bottom-color: #D3D3D3;
}

#petjltdqfv .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#petjltdqfv .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#petjltdqfv .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#petjltdqfv .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#petjltdqfv .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#petjltdqfv .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#petjltdqfv .gt_left {
  text-align: left;
}

#petjltdqfv .gt_center {
  text-align: center;
}

#petjltdqfv .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#petjltdqfv .gt_font_normal {
  font-weight: normal;
}

#petjltdqfv .gt_font_bold {
  font-weight: bold;
}

#petjltdqfv .gt_font_italic {
  font-style: italic;
}

#petjltdqfv .gt_super {
  font-size: 65%;
}

#petjltdqfv .gt_footnote_marks {
  font-size: 75%;
  vertical-align: 0.4em;
  position: initial;
}

#petjltdqfv .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#petjltdqfv .gt_indent_1 {
  text-indent: 5px;
}

#petjltdqfv .gt_indent_2 {
  text-indent: 10px;
}

#petjltdqfv .gt_indent_3 {
  text-indent: 15px;
}

#petjltdqfv .gt_indent_4 {
  text-indent: 20px;
}

#petjltdqfv .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table" data-quarto-disable-processing="false" data-quarto-bootstrap="false">
  <thead>
    
    <tr class="gt_col_headings">
      <th class="gt_col_heading gt_columns_bottom_border gt_right" rowspan="1" colspan="1" scope="col" id="No">No</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="Variabel">Variabel</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="Keterangan">Keterangan</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="No" class="gt_row gt_right">   1</td>
<td headers="Variabel" class="gt_row gt_left">age</td>
<td headers="Keterangan" class="gt_row gt_left">umur nasabah(numeric)</td></tr>
    <tr><td headers="No" class="gt_row gt_right">   2</td>
<td headers="Variabel" class="gt_row gt_left">job</td>
<td headers="Keterangan" class="gt_row gt_left">jenis pekerjaan nasabah(categorical:"admin.","unknown","unemployed","management","housemaid","entrepreneur","student","blue-collar","self-employed","retired","technician","services") </td></tr>
    <tr><td headers="No" class="gt_row gt_right">   3</td>
<td headers="Variabel" class="gt_row gt_left">marital</td>
<td headers="Keterangan" class="gt_row gt_left">status perkawinan nasabah (categorical: "married","divorced","single")</td></tr>
    <tr><td headers="No" class="gt_row gt_right">   4</td>
<td headers="Variabel" class="gt_row gt_left">education</td>
<td headers="Keterangan" class="gt_row gt_left">tingkat pendidikan(categorical: "unknown","secondary","primary","tertiary")</td></tr>
    <tr><td headers="No" class="gt_row gt_right">   5</td>
<td headers="Variabel" class="gt_row gt_left">default</td>
<td headers="Keterangan" class="gt_row gt_left">apakah nasabah memiliki kredit yang macet? (binary: "yes","no")</td></tr>
    <tr><td headers="No" class="gt_row gt_right">   6</td>
<td headers="Variabel" class="gt_row gt_left">balance</td>
<td headers="Keterangan" class="gt_row gt_left">saldo tahunan rata-rata dalam euros (numeric) </td></tr>
    <tr><td headers="No" class="gt_row gt_right">   7</td>
<td headers="Variabel" class="gt_row gt_left">housing</td>
<td headers="Keterangan" class="gt_row gt_left">apakah nasabah memiliki cicilan rumah? (binary: "yes","no")</td></tr>
    <tr><td headers="No" class="gt_row gt_right">   8</td>
<td headers="Variabel" class="gt_row gt_left">loan</td>
<td headers="Keterangan" class="gt_row gt_left">apakah nasabah memiliki pinjaman pribadi? (binary: "yes","no")</td></tr>
    <tr><td headers="No" class="gt_row gt_right">   9</td>
<td headers="Variabel" class="gt_row gt_left">contact</td>
<td headers="Keterangan" class="gt_row gt_left">perangkat telekomunikasi (categorical: "unknown","telephone","cellular") </td></tr>
    <tr><td headers="No" class="gt_row gt_right">   10</td>
<td headers="Variabel" class="gt_row gt_left">duration</td>
<td headers="Keterangan" class="gt_row gt_left">durasi panggilan terakhir, dalam detik (numeric)</td></tr>
    <tr><td headers="No" class="gt_row gt_right">  11</td>
<td headers="Variabel" class="gt_row gt_left">pdays</td>
<td headers="Keterangan" class="gt_row gt_left"> banyaknya hari yang telah berlalu setelah klien terakhir kali dihubungi dari campaign sebelumnya (angka, -1 berarti klien tidak dihubungi sebelumnya)</td></tr>
    <tr><td headers="No" class="gt_row gt_right">  12</td>
<td headers="Variabel" class="gt_row gt_left">previous</td>
<td headers="Keterangan" class="gt_row gt_left">banyaknya komunikasi yang dilakukan sebelum campaign ini(numeric)</td></tr>
    <tr><td headers="No" class="gt_row gt_right">  13</td>
<td headers="Variabel" class="gt_row gt_left">poutcome</td>
<td headers="Keterangan" class="gt_row gt_left">hasil dari promosi campaign sebelumnya (categorical: "unknown","other","failure","success")</td></tr>
    <tr><td headers="No" class="gt_row gt_right">  14</td>
<td headers="Variabel" class="gt_row gt_left">subscribed</td>
<td headers="Keterangan" class="gt_row gt_left">response variable (desired target),apakah nasabah telah berlangganan deposito berjangka? (binary: "yes","no")</td></tr>
  </tbody>
  
  
</table>
</div>
</div>
</div>
<p>Data bisa didownload di link berikut</p>
<p><a href="https://drive.google.com/file/d/11e5IwdRsIepcUwS6OQQAdYb6_6mJsKSD/view?usp=drive_link">Download Data</a></p>
</section>
<section id="import-data" class="level2">
<h2 class="anchored" data-anchor-id="import-data">Import Data</h2>
<div class="cell">
<div class="sourceCode cell-code" id="cb2"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb2-1"><a href="#cb2-1" aria-hidden="true" tabindex="-1"></a>bank_marketing <span class="ot">&lt;-</span> <span class="fu">read.csv</span>(<span class="st">"bank_marketing.csv"</span>,<span class="at">stringsAsFactors =</span> <span class="cn">TRUE</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb3"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="fu">glimpse</span>(bank_marketing)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>Rows: 45,211
Columns: 14
$ subscribed &lt;fct&gt; no, no, no, no, no, no, no, no, no, no, no, no, no, no, no,…
$ age        &lt;int&gt; 58, 44, 33, 47, 33, 35, 28, 42, 58, 43, 41, 29, 53, 58, 57,…
$ job        &lt;fct&gt; management, technician, entrepreneur, blue-collar, unknown,…
$ marital    &lt;fct&gt; married, single, married, married, single, married, single,…
$ education  &lt;fct&gt; tertiary, secondary, secondary, unknown, unknown, tertiary,…
$ default    &lt;fct&gt; no, no, no, no, no, no, no, yes, no, no, no, no, no, no, no…
$ balance    &lt;int&gt; 2143, 29, 2, 1506, 1, 231, 447, 2, 121, 593, 270, 390, 6, 7…
$ housing    &lt;fct&gt; yes, yes, yes, yes, no, yes, yes, yes, yes, yes, yes, yes, …
$ loan       &lt;fct&gt; no, no, yes, no, no, no, yes, no, no, no, no, no, no, no, n…
$ contact    &lt;fct&gt; unknown, unknown, unknown, unknown, unknown, unknown, unkno…
$ duration   &lt;int&gt; 261, 151, 76, 92, 198, 139, 217, 380, 50, 55, 222, 137, 517…
$ pdays      &lt;int&gt; -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1,…
$ previous   &lt;int&gt; 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,…
$ poutcome   &lt;fct&gt; unknown, unknown, unknown, unknown, unknown, unknown, unkno…</code></pre>
</div>
</div>
</section>
<section id="fisher-scoring-dan-irls-untuk-binomial-glm" class="level2">
<h2 class="anchored" data-anchor-id="fisher-scoring-dan-irls-untuk-binomial-glm">Fisher Scoring dan IRLS untuk Binomial GLM</h2>
<p>Misal Binomial GLM didefinisikan sebagai</p>
<p><span class="math display">\[
\boldsymbol{\pi} = \frac{\exp{( \boldsymbol{X}\boldsymbol{\beta} )}}{1+\exp{( \boldsymbol{X}\boldsymbol{\beta} )}}
\]</span> atau</p>
<p><span class="math display">\[
\text{logit}(\boldsymbol{\pi}) = \log{ \left( \frac{\boldsymbol{\pi}}{1-\boldsymbol{\pi}} \right)}= \boldsymbol{X}\boldsymbol{\beta}
\]</span> dengan</p>
<p><span class="math display">\[
\boldsymbol{\pi}=P(\boldsymbol{y}=1)
\]</span></p>
<p>Untuk ilustrasi penggunaan Fisher-scoring dan IRLS kita akan menggunakan variabel prediktor <code>balance</code>, <code>age</code>, <code>housing</code> dan <code>marital</code></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb5"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb5-1"><a href="#cb5-1" aria-hidden="true" tabindex="-1"></a><span class="fu">set.seed</span>(<span class="dv">2045</span>)</span>
<span id="cb5-2"><a href="#cb5-2" aria-hidden="true" tabindex="-1"></a>bank_marketing_mini <span class="ot">&lt;-</span>  bank_marketing <span class="sc">%&gt;%</span> </span>
<span id="cb5-3"><a href="#cb5-3" aria-hidden="true" tabindex="-1"></a>                            <span class="fu">select</span>(subscribed,balance,age,housing,marital) <span class="sc">%&gt;%</span> </span>
<span id="cb5-4"><a href="#cb5-4" aria-hidden="true" tabindex="-1"></a>                            <span class="fu">slice_sample</span>(<span class="at">n=</span><span class="dv">250</span>,<span class="at">by =</span> subscribed)</span>
<span id="cb5-5"><a href="#cb5-5" aria-hidden="true" tabindex="-1"></a><span class="fu">glimpse</span>(bank_marketing_mini)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>Rows: 500
Columns: 5
$ subscribed &lt;fct&gt; no, no, no, no, no, no, no, no, no, no, no, no, no, no, no,…
$ balance    &lt;int&gt; 354, 5838, 39, -123, 1150, 263, -11, 1733, 14, 416, 2, 0, 4…
$ age        &lt;int&gt; 29, 56, 55, 35, 33, 40, 51, 33, 50, 34, 26, 27, 32, 23, 45,…
$ housing    &lt;fct&gt; yes, no, no, yes, yes, yes, no, yes, yes, no, yes, yes, yes…
$ marital    &lt;fct&gt; single, married, married, single, single, single, married, …</code></pre>
</div>
</div>
<p>Kemudian kita akan ekstrak matriks modelnya <span class="math inline">\(\boldsymbol{X}_{n \times (p+1)}\)</span></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb7"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb7-1"><a href="#cb7-1" aria-hidden="true" tabindex="-1"></a>X <span class="ot">&lt;-</span> <span class="fu">model.matrix</span>(subscribed<span class="sc">~</span>balance<span class="sc">+</span>age<span class="sc">+</span>housing<span class="sc">+</span>marital,<span class="at">data =</span> bank_marketing_mini)</span>
<span id="cb7-2"><a href="#cb7-2" aria-hidden="true" tabindex="-1"></a><span class="co">#dimensi matrix X</span></span>
<span id="cb7-3"><a href="#cb7-3" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(X)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500   6</code></pre>
</div>
</div>
<p>dan kemudian untuk <span class="math inline">\(\boldsymbol{y}_{n\times 1}\)</span>, kita misalkan kategori <code>yes</code> sebagai 1 dan 0 adalah untuk kategori <code>no</code></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb9"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb9-1"><a href="#cb9-1" aria-hidden="true" tabindex="-1"></a>y <span class="ot">&lt;-</span> <span class="fu">ifelse</span>(bank_marketing_mini<span class="sc">$</span>subscribed<span class="sc">==</span><span class="st">"yes"</span>,<span class="dv">1</span>,<span class="dv">0</span>)</span>
<span id="cb9-2"><a href="#cb9-2" aria-hidden="true" tabindex="-1"></a><span class="co"># ukuran variabel respon</span></span>
<span id="cb9-3"><a href="#cb9-3" aria-hidden="true" tabindex="-1"></a><span class="fu">length</span>(y)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500</code></pre>
</div>
<div class="sourceCode cell-code" id="cb11"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb11-1"><a href="#cb11-1" aria-hidden="true" tabindex="-1"></a><span class="co"># banyaknya nilai 1 dan 0</span></span>
<span id="cb11-2"><a href="#cb11-2" aria-hidden="true" tabindex="-1"></a><span class="fu">table</span>(y)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>y
  0   1 
250 250 </code></pre>
</div>
</div>
<p>berikut overview dari matriks <span class="math inline">\(\boldsymbol{X}_{n \times (p+1)}\)</span></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb13"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb13-1"><a href="#cb13-1" aria-hidden="true" tabindex="-1"></a>X[<span class="dv">1</span><span class="sc">:</span><span class="dv">10</span>,]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>   (Intercept) balance age housingyes maritalmarried maritalsingle
1            1     354  29          1              0             1
2            1    5838  56          0              1             0
3            1      39  55          0              1             0
4            1    -123  35          1              0             1
5            1    1150  33          1              0             1
6            1     263  40          1              0             1
7            1     -11  51          0              1             0
8            1    1733  33          1              0             1
9            1      14  50          1              1             0
10           1     416  34          0              0             1</code></pre>
</div>
</div>
<section id="binomial-sebagai-distribusi-keluarga-eksponensial" class="level3">
<h3 class="anchored" data-anchor-id="binomial-sebagai-distribusi-keluarga-eksponensial">Binomial sebagai distribusi keluarga eksponensial</h3>
<p>Selanjutnya kita akan mendefinisikan matriks-matriks lain yang dibutuhkan untuk fisher scoring dan IRLS. Pertama-tama kita ingat terlebih dahulu tentang distribusi binomail sebagai distribusi keluarga eksponensial.</p>
<p>Distribusi Binomial yang digunakan untuk GLM adalah <span class="math inline">\(Y \sim\frac{\text{Binomial}(m,\pi)}{m}\)</span>. Ingat bahwa, Cumulant function <span class="math inline">\(b(\theta)\)</span> untuk <span class="math inline">\(Y \sim\frac{\text{Binomial}(m,\pi)}{m}\)</span> adalah</p>
<p><span class="math display">\[
b(\theta) = \log{[1 + \exp{(\theta})]}
\]</span></p>
<p>dan parameter dispersi <span class="math inline">\(a(\phi)\)</span></p>
<p><span class="math display">\[
a(\phi)=\frac{1}{m}
\]</span></p>
<p>Kemudian, <span class="math inline">\(\mu\)</span> dan <span class="math inline">\(Var(Y)\)</span> dari <span class="math inline">\(Y\frac{\text{Binomial}(m,\pi)}{m}\)</span> sebagai keluarga eksponensial adalah</p>
<p><span class="math display">\[
\begin{aligned}
\mu=E(Y)    &amp;= \frac{d b(\theta)}{d\theta} \\
            &amp;=\frac{\exp{(\theta)}}{1+\exp{(\theta)}}
\end{aligned}
\]</span></p>
<p>dan</p>
$$
<span class="math display">\[\begin{aligned}

Var(Y) &amp;= Var(\mu) a(\phi) \\
       &amp;=  \frac{d ^{2}b(\theta)}{d\theta^{2}} a(\phi)\\
       &amp;= \frac{\exp{(\theta)}}{[1+\exp{(\theta)}]^{2}} \frac{1}{m}
\end{aligned}\]</span>
<p>$$</p>
<p>Ingat bahwa koneksi (pemisalan) <span class="math inline">\(\theta\)</span> dengan parameter <span class="math inline">\(\pi\)</span> adalah sebagai berikut</p>
<p><span class="math display">\[
\theta            =    \log{ \left( \frac{\pi}{1-\pi} \right)}
\]</span></p>
<p>Jika kita subtitusi ke dalam <span class="math inline">\(\mu\)</span> dan <span class="math inline">\(Var(Y)\)</span></p>
<p><span class="math display">\[
\begin{aligned}
\mu &amp;= \frac{\exp{(\theta)}}{1+\exp{(\theta)}} \\
    &amp;= \frac{ \left( \frac{\pi}{1-\pi} \right) }{1 +  \left( \frac{\pi}{1-\pi} \right)} \\
    &amp;= \pi
\end{aligned}
\]</span></p>
<p><span class="math display">\[
\begin{aligned}
Var(Y) &amp;= \frac{\exp{(\theta)}}{[1+\exp{(\theta)}]^{2}} \frac{1}{m} \\
       &amp;= \frac{ \left( \frac{\pi}{1-\pi} \right) }{ \left[1 +  \left( \frac{\pi}{1-\pi} \right) \right]^{2}} \frac{1}{m} \\
       &amp;= \pi (1-\pi) \frac{1}{m} \\
       &amp;= \frac{\pi (1-\pi)}{m}
\end{aligned}
\]</span></p>
<p>jadi <span class="math inline">\(\mu=\pi\)</span> dan <span class="math inline">\(Var(Y)=\frac{\pi (1-\pi)}{m}\)</span>. Kemudian, fungsi hubung (link function) yang digunakan adalah fungsi hubung kanonik (canonical link function) yaitu</p>
<p><span class="math display">\[
\eta=\text{logit}(\mu)=\text{logit}(\pi)=\log{\left( \frac{\pi}{1-\pi} \right)}
\]</span></p>
<p>jika kita ubah menjadi fungsi dari <span class="math inline">\(\eta\)</span></p>
<p><span class="math display">\[
g^{-1}(\eta)=\mu=\pi = \frac{\exp{(\eta)}}{1+\exp{(\eta)}}
\]</span></p>
</section>
<section id="mendefiniskan-matriks-untuk-fisher-scoring-dan-irls" class="level3">
<h3 class="anchored" data-anchor-id="mendefiniskan-matriks-untuk-fisher-scoring-dan-irls">Mendefiniskan matriks untuk Fisher Scoring dan IRLS</h3>
<p>Kemudian kita akan dapatkan matriks <span class="math inline">\(\boldsymbol{W}_{n \times n}\)</span> yang didefinisikan</p>
<p><span class="math display">\[
\boldsymbol{W}_{n \times n} = \begin{bmatrix}
\frac{\left(\frac{d \mu_{1}}{d\eta_{1}} \right)^{2}}{Var(y_{1})}  &amp; 0 &amp; \ldots &amp; 0 \\
0 &amp; \frac{\left(\frac{d \mu_{2}}{d\eta_{2}} \right)^{2}}{Var(y_{2})}  &amp; \ldots &amp; 0 \\
\vdots &amp; \vdots                                                       &amp; \ddots &amp; \vdots \\
0      &amp;                           0                                  &amp; 0      &amp; \frac{\left(\frac{d \mu_{n}}{d\eta_{2}} \right)^{2}}{Var(y_{n})}
\end{bmatrix}
\]</span></p>
<p>elemen-elemen diagonalnya sebagai berikut:</p>
<p><span class="math display">\[
\begin{aligned}
\frac{d \mu_{i}}{d\eta_{i}} =\frac{d \pi_{i}}{d\eta_{i}}
        &amp;= \frac{d \left( \frac{\exp{(\eta_i)}}{1+\exp{(\eta_i)}} \right)}{d\eta_{i}} \\
        &amp;=  \frac{\exp{(\eta_i)}}{[1+\exp{(\eta_i)}]^{2}} \\
        &amp;=  \frac{ \left( \frac{\pi_i}{1-\pi_i} \right) }{ \left[1 +  \left( \frac{\pi_i}{1-\pi_i} \right) \right]^{2}}\\
       &amp;= \pi_i (1-\pi_i)
\end{aligned}
\]</span></p>
<p>dan</p>
<p><span class="math display">\[
Var(y_{i})= \frac{\pi_i (1-\pi_i)}{m_i}
\]</span></p>
<p>sehingga</p>
<p><span class="math display">\[
\frac{\left(\frac{d \mu_{i}}{d\eta_{i}} \right)^{2}}{Var(y_{i})} = \frac{[\pi_i (1-\pi_i)]^{2}}{\frac{\pi_i (1-\pi_i)}{m_i}} = m_i\pi_i (1-\pi_i)
\]</span></p>
<p>Jadi matriks <span class="math inline">\(\boldsymbol{W}_{n \times n}\)</span> adalah</p>
<p><span class="math display">\[
\boldsymbol{W}_{n \times n}= \begin{bmatrix}
m_{1}\pi_1 (1-\pi_1)  &amp; 0 &amp; \ldots &amp; 0 \\
0 &amp; m_{2}\pi_2 (1-\pi_2)  &amp; \ldots &amp; 0 \\
\vdots &amp; \vdots                                                       &amp; \ddots &amp; \vdots \\
0      &amp;                           0                                  &amp; 0      &amp; m_{n}\pi_n (1-\pi_n)
\end{bmatrix}
\]</span></p>
<p>kita tuliskan matriks <span class="math inline">\(\boldsymbol{W}_{n \times n}\)</span> dalam sintaks R</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb15"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb15-1"><a href="#cb15-1" aria-hidden="true" tabindex="-1"></a>W <span class="ot">&lt;-</span> <span class="cf">function</span>(m,pi){</span>
<span id="cb15-2"><a href="#cb15-2" aria-hidden="true" tabindex="-1"></a>wi <span class="ot">&lt;-</span> m <span class="sc">*</span> pi <span class="sc">*</span> ( <span class="dv">1</span><span class="sc">-</span> pi )</span>
<span id="cb15-3"><a href="#cb15-3" aria-hidden="true" tabindex="-1"></a><span class="fu">Diagonal</span>(<span class="at">x=</span><span class="fu">as.numeric</span>(wi))</span>
<span id="cb15-4"><a href="#cb15-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>misalkan <span class="math inline">\(m_1=m_2=m_3=1\)</span> dan <span class="math inline">\(\pi_{1}=0.5,\pi_{2}=0.6,\pi_{3}=0.7\)</span> maka <span class="math inline">\(\boldsymbol{W}_{n \times n}\)</span> adalah</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb16"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb16-1"><a href="#cb16-1" aria-hidden="true" tabindex="-1"></a><span class="fu">W</span>(<span class="at">m=</span><span class="fu">c</span>(<span class="dv">1</span>,<span class="dv">1</span>,<span class="dv">1</span>),<span class="at">pi=</span><span class="fu">c</span>(<span class="fl">0.5</span>,<span class="fl">0.6</span>,<span class="fl">0.7</span>))</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>3 x 3 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3]
[1,] 0.25    .    .
[2,]    . 0.24    .
[3,]    .    . 0.21</code></pre>
</div>
</div>
<p>Selanjutnya kita akan dapatkan matriks <span class="math inline">\(D_{n \times n}\)</span> yang didefinisikan</p>
<p><span class="math display">\[
\boldsymbol{D}_{n \times n} = \begin{bmatrix}
\frac{d \mu_{1}}{d\eta_{1}}   &amp; 0 &amp; \ldots &amp; 0 \\
0 &amp; \frac{d \mu_{2}}{d\eta_{2}}   &amp; \ldots &amp; 0 \\
\vdots &amp; \vdots                                                       &amp; \ddots &amp; \vdots \\
0      &amp;                           0                                  &amp; 0      &amp; \frac{d \mu_{n}}{d\eta_{n}}
\end{bmatrix}
\]</span></p>
<p>elemen-elemen diagonalnya sebagai berikut:</p>
<p><span class="math display">\[
\begin{aligned}
\frac{d \mu_{i}}{d\eta_{i}} =\frac{d \pi_{i}}{d\eta_{i}}
        &amp;= \frac{d \left( \frac{\exp{(\eta_i)}}{1+\exp{(\eta_i)}} \right)}{d\eta_{i}} \\
        &amp;=  \frac{\exp{(\eta_i)}}{[1+\exp{(\eta_i)}]^{2}} \\
        &amp;=  \frac{ \left( \frac{\pi_i}{1-\pi_i} \right) }{ \left[1 +  \left( \frac{\pi_i}{1-\pi_i} \right) \right]^{2}}\\
       &amp;= \pi_i (1-\pi_i)
\end{aligned}
\]</span></p>
<p>Jadi matriks <span class="math inline">\(\boldsymbol{D}_{n \times n}\)</span> adalah</p>
<p><span class="math display">\[
\boldsymbol{D}_{n \times n}= \begin{bmatrix}
\pi_1 (1-\pi_1)  &amp; 0 &amp; \ldots &amp; 0 \\
0 &amp; \pi_2 (1-\pi_2)  &amp; \ldots &amp; 0 \\
\vdots &amp; \vdots                                                       &amp; \ddots &amp; \vdots \\
0      &amp;                           0                                  &amp; 0      &amp; \pi_n (1-\pi_n)
\end{bmatrix}
\]</span></p>
<p>kita tuliskan matriks <span class="math inline">\(\boldsymbol{D}_{n \times n}\)</span> dalam sintaks R</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb18"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb18-1"><a href="#cb18-1" aria-hidden="true" tabindex="-1"></a>D <span class="ot">&lt;-</span> <span class="cf">function</span>(pi){</span>
<span id="cb18-2"><a href="#cb18-2" aria-hidden="true" tabindex="-1"></a>di <span class="ot">&lt;-</span> pi <span class="sc">*</span> ( <span class="dv">1</span><span class="sc">-</span> pi )</span>
<span id="cb18-3"><a href="#cb18-3" aria-hidden="true" tabindex="-1"></a><span class="fu">Diagonal</span>(<span class="at">x=</span><span class="fu">as.numeric</span>(di))</span>
<span id="cb18-4"><a href="#cb18-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>misalkan <span class="math inline">\(\pi_{1}=0.5,\pi_{2}=0.6,\pi_{3}=0.7\)</span> maka <span class="math inline">\(\boldsymbol{D}_{n \times n}\)</span> adalah</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb19"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb19-1"><a href="#cb19-1" aria-hidden="true" tabindex="-1"></a><span class="fu">D</span>(<span class="at">pi=</span><span class="fu">c</span>(<span class="fl">0.5</span>,<span class="fl">0.6</span>,<span class="fl">0.7</span>))</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>3 x 3 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3]
[1,] 0.25    .    .
[2,]    . 0.24    .
[3,]    .    . 0.21</code></pre>
</div>
</div>
<p>Selanjutnya kita akan dapatkan matriks <span class="math inline">\(\boldsymbol{\mu}_{n \times 1}\)</span> yang didefinisikan</p>
<p><span class="math display">\[
\boldsymbol{\mu}_{n \times 1}=g^{-1}(\boldsymbol{X}\boldsymbol{\beta})=\frac{\exp{(\boldsymbol{X}_{n \times (p+1)}\boldsymbol{\beta}_{(p+1)})}}{1+\exp{(\boldsymbol{X}_{n \times (p+1)}\boldsymbol{\beta}_{(p+1)})}}
\]</span></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb21"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb21-1"><a href="#cb21-1" aria-hidden="true" tabindex="-1"></a>mu <span class="ot">&lt;-</span> <span class="cf">function</span>(X,beta){</span>
<span id="cb21-2"><a href="#cb21-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">exp</span>(X <span class="sc">%*%</span> beta) <span class="sc">/</span> ( <span class="dv">1</span><span class="sc">+</span><span class="fu">exp</span>( X<span class="sc">%*%</span> beta) )</span>
<span id="cb21-3"><a href="#cb21-3" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>misalkan <span class="math inline">\(\boldsymbol{X}_{n \times (p+1)}\)</span> berasal dari data <code>bank_marketing_mini</code> dan <span class="math inline">\(\boldsymbol{\beta}_{(p+1)}=[0.230 0.001 \space 0.002 \space -0.769 \space -0.166 \space 0.109]^{t}\)</span> maka <span class="math inline">\(\boldsymbol{\mu}_{n \times 1}\)</span> adalah</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb22"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb22-1"><a href="#cb22-1" aria-hidden="true" tabindex="-1"></a><span class="co"># memeriksa dimensi</span></span>
<span id="cb22-2"><a href="#cb22-2" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>( <span class="fu">mu</span>(<span class="at">X=</span>X,<span class="at">beta =</span> <span class="fu">c</span>(<span class="fl">0.230</span>,<span class="fl">0.001</span>,<span class="fl">0.002</span>,<span class="sc">-</span><span class="fl">0.769</span>,<span class="sc">-</span><span class="fl">0.166</span>,<span class="fl">0.109</span>) ) )</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500   1</code></pre>
</div>
<div class="sourceCode cell-code" id="cb24"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb24-1"><a href="#cb24-1" aria-hidden="true" tabindex="-1"></a><span class="co"># menampilkan 10 elemen pertama</span></span>
<span id="cb24-2"><a href="#cb24-2" aria-hidden="true" tabindex="-1"></a><span class="fu">mu</span>(<span class="at">X=</span>X,<span class="at">beta =</span> <span class="fu">c</span>(<span class="fl">0.230</span>,<span class="fl">0.001</span>,<span class="fl">0.002</span>,<span class="sc">-</span><span class="fl">0.769</span>,<span class="sc">-</span><span class="fl">0.166</span>,<span class="fl">0.109</span>) )[<span class="dv">1</span><span class="sc">:</span><span class="dv">10</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code> [1] 0.4955001 0.9975617 0.5530496 0.3815440 0.6869718 0.4782637 0.5386726
 [8] 0.7972185 0.3564054 0.6948728</code></pre>
</div>
</div>
</section>
<section id="fisher-scoring" class="level3">
<h3 class="anchored" data-anchor-id="fisher-scoring">Fisher Scoring</h3>
<p>matriks <span class="math inline">\(\boldsymbol{S}_{(p+1) \times 1}\)</span> adalah</p>
<p><span class="math display">\[
\boldsymbol{S}_{(p+1) \times 1}= \boldsymbol{X}^{t}_{ (p+1) \times n} \boldsymbol{W}_{n \times n}  (\boldsymbol{D}_{n \times n})^{-1} (\boldsymbol{y}_{n \times 1}-\boldsymbol{\mu}_{n \times 1})
\]</span></p>
<p>kita tuliskan matriks <span class="math inline">\(\boldsymbol{S}_{(p+1) \times 1}\)</span> dalam sintaks R</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb26"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb26-1"><a href="#cb26-1" aria-hidden="true" tabindex="-1"></a>S <span class="ot">&lt;-</span> <span class="cf">function</span>(X,W,D,y,mu){</span>
<span id="cb26-2"><a href="#cb26-2" aria-hidden="true" tabindex="-1"></a>  inv_D <span class="ot">&lt;-</span> <span class="fu">chol2inv</span>(<span class="fu">chol</span>(D))</span>
<span id="cb26-3"><a href="#cb26-3" aria-hidden="true" tabindex="-1"></a> <span class="fu">crossprod</span>( X, W <span class="sc">%*%</span> inv_D <span class="sc">%*%</span> (y<span class="sc">-</span>mu) )</span>
<span id="cb26-4"><a href="#cb26-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>misalkan <span class="math inline">\(\boldsymbol{W}_{n \times n} ,\boldsymbol{D}_{n \times n}\)</span> dan <span class="math inline">\(\boldsymbol{\mu}_{n \times 1}\)</span> adalah sebagai berikut:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb27"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb27-1"><a href="#cb27-1" aria-hidden="true" tabindex="-1"></a><span class="fu">set.seed</span>(<span class="dv">2045</span>)</span>
<span id="cb27-2"><a href="#cb27-2" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb27-3"><a href="#cb27-3" aria-hidden="true" tabindex="-1"></a>W_coba <span class="ot">&lt;-</span> <span class="fu">W</span>(<span class="at">m =</span> <span class="dv">1</span>,<span class="at">pi =</span> <span class="fu">rep</span>(<span class="fl">0.5</span>,<span class="fu">nrow</span>(X)))</span>
<span id="cb27-4"><a href="#cb27-4" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(W_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500 500</code></pre>
</div>
<div class="sourceCode cell-code" id="cb29"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb29-1"><a href="#cb29-1" aria-hidden="true" tabindex="-1"></a>W_coba[<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>,<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>5 x 5 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3] [,4] [,5]
[1,] 0.25    .    .    .    .
[2,]    . 0.25    .    .    .
[3,]    .    . 0.25    .    .
[4,]    .    .    . 0.25    .
[5,]    .    .    .    . 0.25</code></pre>
</div>
<div class="sourceCode cell-code" id="cb31"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb31-1"><a href="#cb31-1" aria-hidden="true" tabindex="-1"></a>D_coba <span class="ot">&lt;-</span> <span class="fu">D</span>(<span class="at">pi =</span> <span class="fu">rep</span>(<span class="fl">0.5</span>,<span class="fu">nrow</span>(X)))</span>
<span id="cb31-2"><a href="#cb31-2" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(D_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500 500</code></pre>
</div>
<div class="sourceCode cell-code" id="cb33"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb33-1"><a href="#cb33-1" aria-hidden="true" tabindex="-1"></a>D_coba[<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>,<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>5 x 5 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3] [,4] [,5]
[1,] 0.25    .    .    .    .
[2,]    . 0.25    .    .    .
[3,]    .    . 0.25    .    .
[4,]    .    .    . 0.25    .
[5,]    .    .    .    . 0.25</code></pre>
</div>
<div class="sourceCode cell-code" id="cb35"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb35-1"><a href="#cb35-1" aria-hidden="true" tabindex="-1"></a>mu_coba <span class="ot">&lt;-</span> <span class="fu">as.matrix</span>( <span class="fu">runif</span>(<span class="at">n =</span> <span class="fu">nrow</span>(X),<span class="at">min =</span> <span class="dv">0</span>,<span class="at">max =</span> <span class="dv">1</span> ) )</span>
<span id="cb35-2"><a href="#cb35-2" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(mu_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500   1</code></pre>
</div>
<div class="sourceCode cell-code" id="cb37"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb37-1"><a href="#cb37-1" aria-hidden="true" tabindex="-1"></a><span class="fu">head</span>(mu_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>           [,1]
[1,] 0.77550659
[2,] 0.94264755
[3,] 0.47241345
[4,] 0.08665263
[5,] 0.63646300
[6,] 0.42453500</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb39"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb39-1"><a href="#cb39-1" aria-hidden="true" tabindex="-1"></a><span class="fu">S</span>(<span class="at">X =</span> X,<span class="at">W =</span> W_coba,<span class="at">D =</span> D_coba,<span class="at">y =</span> y,<span class="at">mu =</span> mu_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>6 x 1 Matrix of class "dgeMatrix"
                      [,1]
(Intercept)       -5.12588
balance        64379.67806
age             -132.00826
housingyes       -27.00537
maritalmarried    -9.45959
maritalsingle      5.37219</code></pre>
</div>
</div>
<p>matriks <span class="math inline">\(\boldsymbol{\mathcal{I}}_{p \times p}\)</span> adalah</p>
<p><span class="math display">\[
\boldsymbol{\mathcal{I}}_{p \times p }=\boldsymbol{X}_{ (p+1) \times n} \boldsymbol{W}_{n \times n}  \boldsymbol{X}_{n \times (p+1)}
\]</span></p>
<p>kita tuliskan matriks <span class="math inline">\(\boldsymbol{\mathcal{I}}_{p \times p }\)</span> dalam sintaks R</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb41"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb41-1"><a href="#cb41-1" aria-hidden="true" tabindex="-1"></a>I_fs <span class="ot">&lt;-</span> <span class="cf">function</span>(X,W){</span>
<span id="cb41-2"><a href="#cb41-2" aria-hidden="true" tabindex="-1"></a> <span class="fu">crossprod</span>(X,W <span class="sc">%*%</span> X)</span>
<span id="cb41-3"><a href="#cb41-3" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb42"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb42-1"><a href="#cb42-1" aria-hidden="true" tabindex="-1"></a><span class="fu">set.seed</span>(<span class="dv">2045</span>)</span>
<span id="cb42-2"><a href="#cb42-2" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb42-3"><a href="#cb42-3" aria-hidden="true" tabindex="-1"></a>W_coba <span class="ot">&lt;-</span> <span class="fu">W</span>(<span class="at">m =</span> <span class="dv">1</span>,<span class="at">pi =</span> <span class="fu">rep</span>(<span class="fl">0.5</span>,<span class="fu">nrow</span>(X)))</span>
<span id="cb42-4"><a href="#cb42-4" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(W_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500 500</code></pre>
</div>
<div class="sourceCode cell-code" id="cb44"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb44-1"><a href="#cb44-1" aria-hidden="true" tabindex="-1"></a>W_coba[<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>,<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>5 x 5 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3] [,4] [,5]
[1,] 0.25    .    .    .    .
[2,]    . 0.25    .    .    .
[3,]    .    . 0.25    .    .
[4,]    .    .    . 0.25    .
[5,]    .    .    .    . 0.25</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb46"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb46-1"><a href="#cb46-1" aria-hidden="true" tabindex="-1"></a><span class="fu">I_fs</span>(<span class="at">X =</span> X,<span class="at">W =</span> W_coba)[<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>,<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>5 x 5 Matrix of class "dgeMatrix"
               (Intercept)      balance        age housingyes maritalmarried
(Intercept)          125.0 1.901443e+05    5160.00      58.00          68.50
balance           190144.2 1.821748e+09 8400186.75   59549.75      101843.00
age                 5160.0 8.400187e+06  230156.50    2279.50        3062.25
housingyes            58.0 5.954975e+04    2279.50      58.00          31.00
maritalmarried        68.5 1.018430e+05    3062.25      31.00          68.50</code></pre>
</div>
</div>
<p>Supaya lebih mudah, kita kumpulkan semua definisi matriks yang sudah dituliskan ke program R dibawah ini</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb48"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb48-1"><a href="#cb48-1" aria-hidden="true" tabindex="-1"></a>W <span class="ot">&lt;-</span> <span class="cf">function</span>(m,pi){</span>
<span id="cb48-2"><a href="#cb48-2" aria-hidden="true" tabindex="-1"></a>wi <span class="ot">&lt;-</span> m <span class="sc">*</span> pi <span class="sc">*</span> ( <span class="dv">1</span><span class="sc">-</span> pi )</span>
<span id="cb48-3"><a href="#cb48-3" aria-hidden="true" tabindex="-1"></a><span class="fu">Diagonal</span>(<span class="at">x=</span><span class="fu">as.numeric</span>(wi))</span>
<span id="cb48-4"><a href="#cb48-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb49"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb49-1"><a href="#cb49-1" aria-hidden="true" tabindex="-1"></a>D <span class="ot">&lt;-</span> <span class="cf">function</span>(pi){</span>
<span id="cb49-2"><a href="#cb49-2" aria-hidden="true" tabindex="-1"></a>di <span class="ot">&lt;-</span> pi <span class="sc">*</span> ( <span class="dv">1</span><span class="sc">-</span> pi )</span>
<span id="cb49-3"><a href="#cb49-3" aria-hidden="true" tabindex="-1"></a><span class="fu">Diagonal</span>(<span class="at">x=</span><span class="fu">as.numeric</span>(di))</span>
<span id="cb49-4"><a href="#cb49-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb50"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb50-1"><a href="#cb50-1" aria-hidden="true" tabindex="-1"></a>mu <span class="ot">&lt;-</span> <span class="cf">function</span>(X,beta){</span>
<span id="cb50-2"><a href="#cb50-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">exp</span>(X <span class="sc">%*%</span> beta) <span class="sc">/</span> ( <span class="dv">1</span><span class="sc">+</span><span class="fu">exp</span>( X<span class="sc">%*%</span> beta) )</span>
<span id="cb50-3"><a href="#cb50-3" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb51"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb51-1"><a href="#cb51-1" aria-hidden="true" tabindex="-1"></a>S <span class="ot">&lt;-</span> <span class="cf">function</span>(X,W,D,y,mu){</span>
<span id="cb51-2"><a href="#cb51-2" aria-hidden="true" tabindex="-1"></a>  inv_D <span class="ot">&lt;-</span> <span class="fu">chol2inv</span>(<span class="fu">chol</span>(D))</span>
<span id="cb51-3"><a href="#cb51-3" aria-hidden="true" tabindex="-1"></a> <span class="fu">crossprod</span>( X, W <span class="sc">%*%</span> inv_D <span class="sc">%*%</span> (y<span class="sc">-</span>mu) )</span>
<span id="cb51-4"><a href="#cb51-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb52"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb52-1"><a href="#cb52-1" aria-hidden="true" tabindex="-1"></a>I_fs <span class="ot">&lt;-</span> <span class="cf">function</span>(X,W){</span>
<span id="cb52-2"><a href="#cb52-2" aria-hidden="true" tabindex="-1"></a> <span class="fu">crossprod</span>(X,W <span class="sc">%*%</span> X)</span>
<span id="cb52-3"><a href="#cb52-3" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>Selanjutnya kita akan mulai menuliskan program R untuk iterasi fisher scoring</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb53"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb53-1"><a href="#cb53-1" aria-hidden="true" tabindex="-1"></a>stop_criterion <span class="ot">&lt;-</span> <span class="cf">function</span>(beta_old,beta_new,tol) {</span>
<span id="cb53-2"><a href="#cb53-2" aria-hidden="true" tabindex="-1"></a>  error <span class="ot">&lt;-</span> <span class="fu">as.matrix</span>(<span class="fu">abs</span>(beta_new<span class="sc">-</span>beta_old))</span>
<span id="cb53-3"><a href="#cb53-3" aria-hidden="true" tabindex="-1"></a>  status <span class="ot">&lt;-</span> <span class="fu">all</span>(error  <span class="sc">&lt;</span> tol)</span>
<span id="cb53-4"><a href="#cb53-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">return</span>(<span class="fu">list</span>(<span class="at">error=</span><span class="fu">as.data.frame</span>(<span class="fu">t</span>(error)),<span class="at">status=</span>status))</span>
<span id="cb53-5"><a href="#cb53-5" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb54"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb54-1"><a href="#cb54-1" aria-hidden="true" tabindex="-1"></a><span class="fu">stop_criterion</span>(<span class="at">beta_old =</span> <span class="fu">c</span>(<span class="fl">0.5</span>,<span class="sc">-</span><span class="fl">0.9</span>),<span class="at">beta_new =</span> <span class="fu">c</span>(<span class="fl">0.51</span>,<span class="sc">-</span><span class="fl">0.91</span>),<span class="at">tol =</span> <span class="fl">1e-5</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$error
    V1   V2
1 0.01 0.01

$status
[1] FALSE</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb56"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb56-1"><a href="#cb56-1" aria-hidden="true" tabindex="-1"></a><span class="fu">stop_criterion</span>(<span class="at">beta_old =</span> <span class="fu">c</span>(<span class="fl">0.5</span>,<span class="sc">-</span><span class="fl">0.9</span>),<span class="at">beta_new =</span> <span class="fu">c</span>(<span class="fl">0.50001</span>,<span class="sc">-</span><span class="fl">0.90001</span>),<span class="at">tol =</span> <span class="fl">1e-5</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$error
     V1    V2
1 1e-05 1e-05

$status
[1] TRUE</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb58"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb58-1"><a href="#cb58-1" aria-hidden="true" tabindex="-1"></a><span class="fu">stop_criterion</span>(<span class="at">beta_old =</span> <span class="fu">c</span>(<span class="fl">0.5</span>,<span class="sc">-</span><span class="fl">0.9</span>),<span class="at">beta_new =</span> <span class="fu">c</span>(<span class="fl">0.5001</span>,<span class="sc">-</span><span class="fl">0.90001</span>),<span class="at">tol =</span> <span class="fl">1e-5</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$error
     V1    V2
1 1e-04 1e-05

$status
[1] FALSE</code></pre>
</div>
</div>
<p>berikut adalah nilai awal dari <span class="math inline">\(\boldsymbol{\beta}_{(p+1)}\)</span>, nilai toleransi, iterasi maksimum dan nilai dari <span class="math inline">\(m_i\)</span>. Khusus untuk <span class="math inline">\(m_i=1\)</span> karena respon <code>subscribed</code> adalah respon distribusi bernouli.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb60"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb60-1"><a href="#cb60-1" aria-hidden="true" tabindex="-1"></a>beta_new <span class="ot">&lt;-</span> <span class="fu">rep</span>(<span class="dv">0</span>,<span class="fu">ncol</span>(X))</span>
<span id="cb60-2"><a href="#cb60-2" aria-hidden="true" tabindex="-1"></a><span class="fu">names</span>(beta_new) <span class="ot">&lt;-</span> <span class="fu">colnames</span>(X)</span>
<span id="cb60-3"><a href="#cb60-3" aria-hidden="true" tabindex="-1"></a>beta_new</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>   (Intercept)        balance            age     housingyes maritalmarried 
             0              0              0              0              0 
 maritalsingle 
             0 </code></pre>
</div>
<div class="sourceCode cell-code" id="cb62"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb62-1"><a href="#cb62-1" aria-hidden="true" tabindex="-1"></a>max_iter <span class="ot">&lt;-</span> <span class="dv">1000</span></span>
<span id="cb62-2"><a href="#cb62-2" aria-hidden="true" tabindex="-1"></a>mi <span class="ot">&lt;-</span> <span class="dv">1</span></span>
<span id="cb62-3"><a href="#cb62-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb62-4"><a href="#cb62-4" aria-hidden="true" tabindex="-1"></a>tolerance <span class="ot">&lt;-</span>  <span class="fl">1e-15</span></span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>Ingat Formula Fisher Scoring yang digunakan adalah sebagai berikut:</p>
<p><span class="math display">\[
\boldsymbol{\beta}_{(p+1) \times 1}^{(i+1)}=\boldsymbol{\beta}_{(p+1) \times 1}^{(i)} + \left[\boldsymbol{\mathcal{I}}_{p \times p }^{(i)} \right]^{-1} \boldsymbol{S}_{(p+1) \times 1}^{(i)}
\]</span></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb63"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb63-1"><a href="#cb63-1" aria-hidden="true" tabindex="-1"></a><span class="cf">for</span>(i <span class="cf">in</span> <span class="dv">1</span><span class="sc">:</span>max_iter){</span>
<span id="cb63-2"><a href="#cb63-2" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-3"><a href="#cb63-3" aria-hidden="true" tabindex="-1"></a>  <span class="co">#menyimpan beta lama</span></span>
<span id="cb63-4"><a href="#cb63-4" aria-hidden="true" tabindex="-1"></a>  beta_old <span class="ot">&lt;-</span> beta_new</span>
<span id="cb63-5"><a href="#cb63-5" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-6"><a href="#cb63-6" aria-hidden="true" tabindex="-1"></a>  mu_new <span class="ot">&lt;-</span> <span class="fu">mu</span>(<span class="at">X =</span> X,<span class="at">beta =</span> beta_new)</span>
<span id="cb63-7"><a href="#cb63-7" aria-hidden="true" tabindex="-1"></a>  W_new <span class="ot">&lt;-</span> <span class="fu">W</span>(<span class="at">m =</span> mi,<span class="at">pi =</span> mu_new)</span>
<span id="cb63-8"><a href="#cb63-8" aria-hidden="true" tabindex="-1"></a>  D_new <span class="ot">&lt;-</span> <span class="fu">D</span>(<span class="at">pi =</span> mu_new)</span>
<span id="cb63-9"><a href="#cb63-9" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-10"><a href="#cb63-10" aria-hidden="true" tabindex="-1"></a>  I_inv <span class="ot">&lt;-</span> <span class="fu">chol2inv</span>(<span class="fu">chol</span>( <span class="fu">I_fs</span>(<span class="at">X =</span> X,<span class="at">W =</span> W_new) ))</span>
<span id="cb63-11"><a href="#cb63-11" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-12"><a href="#cb63-12" aria-hidden="true" tabindex="-1"></a>  <span class="co">#formulasi fisher scoring</span></span>
<span id="cb63-13"><a href="#cb63-13" aria-hidden="true" tabindex="-1"></a>  beta_new <span class="ot">&lt;-</span> beta_new <span class="sc">+</span>I_inv <span class="sc">%*%</span> <span class="fu">S</span>(<span class="at">X=</span>X,<span class="at">W =</span> W_new,<span class="at">D =</span> D_new,<span class="at">y =</span>y ,<span class="at">mu =</span> mu_new) </span>
<span id="cb63-14"><a href="#cb63-14" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-15"><a href="#cb63-15" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb63-16"><a href="#cb63-16" aria-hidden="true" tabindex="-1"></a>  <span class="co">#menghitung stopping criterion</span></span>
<span id="cb63-17"><a href="#cb63-17" aria-hidden="true" tabindex="-1"></a>  stop_criterion_iter <span class="ot">&lt;-</span> <span class="fu">stop_criterion</span>(</span>
<span id="cb63-18"><a href="#cb63-18" aria-hidden="true" tabindex="-1"></a>                 <span class="at">beta_old =</span> beta_old,</span>
<span id="cb63-19"><a href="#cb63-19" aria-hidden="true" tabindex="-1"></a>                 <span class="at">beta_new =</span> beta_new,</span>
<span id="cb63-20"><a href="#cb63-20" aria-hidden="true" tabindex="-1"></a>                 <span class="at">tol =</span> tolerance)</span>
<span id="cb63-21"><a href="#cb63-21" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-22"><a href="#cb63-22" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb63-23"><a href="#cb63-23" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb63-24"><a href="#cb63-24" aria-hidden="true" tabindex="-1"></a>  <span class="co">#iterasi berhenti jika sudah memenuhi stopping criterion</span></span>
<span id="cb63-25"><a href="#cb63-25" aria-hidden="true" tabindex="-1"></a>  <span class="cf">if</span>(stop_criterion_iter<span class="sc">$</span>status) <span class="cf">break</span></span>
<span id="cb63-26"><a href="#cb63-26" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>Saat Convergent maka kita mendapatkan</p>
<p><span class="math display">\[
Var(\hat{\boldsymbol{\beta}}_{(p+1) \times 1})= \left[\boldsymbol{\mathcal{I}}_{p \times p } \right]^{-1}
\]</span> kemudian standard error dari <span class="math inline">\(\hat{\boldsymbol{\beta}}_{(p+1) \times 1}\)</span> adalah akar dari diagonal utama <span class="math inline">\(\left[\boldsymbol{\mathcal{I}}_{p \times p } \right]^{-1}\)</span>.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb64"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb64-1"><a href="#cb64-1" aria-hidden="true" tabindex="-1"></a>result_fs <span class="ot">&lt;-</span> <span class="fu">list</span>(<span class="at">iter_convergence=</span>i,<span class="at">coefficients=</span><span class="fu">as.numeric</span>(beta_new),<span class="at">var_beta=</span>I_inv)</span>
<span id="cb64-2"><a href="#cb64-2" aria-hidden="true" tabindex="-1"></a>result_fs<span class="sc">$</span>iter_convergence</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 31</code></pre>
</div>
<div class="sourceCode cell-code" id="cb66"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb66-1"><a href="#cb66-1" aria-hidden="true" tabindex="-1"></a>result_fs<span class="sc">$</span>var_beta</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>6 x 6 Matrix of class "dpoMatrix"
                 (Intercept)       balance           age    housingyes
(Intercept)     2.743637e-01 -5.891964e-07 -4.050466e-03 -3.584211e-02
balance        -5.891964e-07  1.308069e-09 -3.003060e-08  6.255880e-07
age            -4.050466e-03 -3.003060e-08  8.377425e-05  3.146135e-04
housingyes     -3.584211e-02  6.255880e-07  3.146135e-04  3.568298e-02
maritalmarried -7.623728e-02 -2.022522e-07  2.006810e-04  5.139815e-03
maritalsingle  -1.230458e-01 -4.027429e-07  1.169965e-03  8.360438e-03
               maritalmarried maritalsingle
(Intercept)     -7.623728e-02 -1.230458e-01
balance         -2.022522e-07 -4.027429e-07
age              2.006810e-04  1.169965e-03
housingyes       5.139815e-03  8.360438e-03
maritalmarried   8.060487e-02  6.751034e-02
maritalsingle    6.751034e-02  1.072151e-01</code></pre>
</div>
<div class="sourceCode cell-code" id="cb68"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb68-1"><a href="#cb68-1" aria-hidden="true" tabindex="-1"></a>summary_fs <span class="ot">&lt;-</span> <span class="fu">data.frame</span>(<span class="at">variables=</span><span class="fu">rownames</span>(beta_new),</span>
<span id="cb68-2"><a href="#cb68-2" aria-hidden="true" tabindex="-1"></a>                         <span class="at">Estimate=</span><span class="fu">round</span>(result_fs<span class="sc">$</span>coefficients,<span class="dv">10</span>),</span>
<span id="cb68-3"><a href="#cb68-3" aria-hidden="true" tabindex="-1"></a>                         <span class="at">Std_Err=</span><span class="fu">round</span>(<span class="fu">sqrt</span>(<span class="fu">diag</span>(<span class="fu">as.matrix</span>(result_fs<span class="sc">$</span>var_beta))),<span class="dv">10</span>),<span class="at">row.names =</span> <span class="cn">NULL</span>) <span class="sc">%&gt;%</span> </span>
<span id="cb68-4"><a href="#cb68-4" aria-hidden="true" tabindex="-1"></a>              <span class="fu">mutate</span>(<span class="at">z=</span>Estimate <span class="sc">/</span> Std_Err, <span class="at">p_value=</span><span class="fu">round</span>(<span class="dv">2</span><span class="sc">*</span><span class="fu">pnorm</span>(<span class="at">q=</span><span class="fu">abs</span>(z),<span class="at">lower.tail =</span> F),<span class="dv">3</span>))</span>
<span id="cb68-5"><a href="#cb68-5" aria-hidden="true" tabindex="-1"></a>summary_fs</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>       variables      Estimate      Std_Err          z p_value
1    (Intercept)  0.2300633445 0.5237974260  0.4392220   0.661
2        balance  0.0000557833 0.0000361672  1.5423726   0.123
3            age  0.0024653247 0.0091528273  0.2693512   0.788
4     housingyes -0.7690447815 0.1888993831 -4.0711874   0.000
5 maritalmarried -0.1661114916 0.2839099667 -0.5850851   0.558
6  maritalsingle  0.1087506638 0.3274371898  0.3321268   0.740</code></pre>
</div>
</div>
</section>
<section id="irls" class="level3">
<h3 class="anchored" data-anchor-id="irls">IRLS</h3>
<p>matriks <span class="math inline">\(\boldsymbol{z}\)</span> adalah</p>
<p><span class="math display">\[
\boldsymbol{z}_{n \times 1}=\boldsymbol{X}_{ n \times (p+1) }\boldsymbol{\beta}_{((𝑝+1)×1)} + (\boldsymbol{D}_{n \times n})^{-1} (\boldsymbol{y}_{n \times 1}−\boldsymbol{\mu}_{𝑛×1})
\]</span></p>
<p>kita tuliskan matriks <span class="math inline">\(\boldsymbol{z}\)</span> dalam sintaks R</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb70"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb70-1"><a href="#cb70-1" aria-hidden="true" tabindex="-1"></a>z <span class="ot">&lt;-</span> <span class="cf">function</span>(X,beta,D,y,mu){</span>
<span id="cb70-2"><a href="#cb70-2" aria-hidden="true" tabindex="-1"></a>  inv_D <span class="ot">&lt;-</span> <span class="fu">chol2inv</span>(<span class="fu">chol</span>(D))</span>
<span id="cb70-3"><a href="#cb70-3" aria-hidden="true" tabindex="-1"></a> X <span class="sc">%*%</span> beta <span class="sc">+</span> inv_D <span class="sc">%*%</span>  (y<span class="sc">-</span>mu)</span>
<span id="cb70-4"><a href="#cb70-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>misalkan <span class="math inline">\(\boldsymbol{W}_{n \times n} ,\boldsymbol{\beta}_{((𝑝+1)×1)},\boldsymbol{D}_{n \times n}\)</span> dan <span class="math inline">\(\boldsymbol{\mu}_{n \times 1}\)</span> adalah sebagai berikut:</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb71"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb71-1"><a href="#cb71-1" aria-hidden="true" tabindex="-1"></a><span class="fu">set.seed</span>(<span class="dv">2045</span>)</span>
<span id="cb71-2"><a href="#cb71-2" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb71-3"><a href="#cb71-3" aria-hidden="true" tabindex="-1"></a>W_coba <span class="ot">&lt;-</span> <span class="fu">W</span>(<span class="at">m =</span> <span class="dv">1</span>,<span class="at">pi =</span> <span class="fu">rep</span>(<span class="fl">0.5</span>,<span class="fu">nrow</span>(X)))</span>
<span id="cb71-4"><a href="#cb71-4" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(W_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500 500</code></pre>
</div>
<div class="sourceCode cell-code" id="cb73"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb73-1"><a href="#cb73-1" aria-hidden="true" tabindex="-1"></a>W_coba[<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>,<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>5 x 5 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3] [,4] [,5]
[1,] 0.25    .    .    .    .
[2,]    . 0.25    .    .    .
[3,]    .    . 0.25    .    .
[4,]    .    .    . 0.25    .
[5,]    .    .    .    . 0.25</code></pre>
</div>
<div class="sourceCode cell-code" id="cb75"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb75-1"><a href="#cb75-1" aria-hidden="true" tabindex="-1"></a>beta_coba <span class="ot">&lt;-</span> <span class="fu">c</span>(<span class="fl">0.230</span>,<span class="fl">0.001</span>,<span class="fl">0.002</span>,<span class="sc">-</span><span class="fl">0.769</span>,<span class="sc">-</span><span class="fl">0.166</span>,<span class="fl">0.109</span>)</span>
<span id="cb75-2"><a href="#cb75-2" aria-hidden="true" tabindex="-1"></a>beta_coba</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1]  0.230  0.001  0.002 -0.769 -0.166  0.109</code></pre>
</div>
<div class="sourceCode cell-code" id="cb77"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb77-1"><a href="#cb77-1" aria-hidden="true" tabindex="-1"></a>D_coba <span class="ot">&lt;-</span> <span class="fu">D</span>(<span class="at">pi =</span> <span class="fu">rep</span>(<span class="fl">0.5</span>,<span class="fu">nrow</span>(X)))</span>
<span id="cb77-2"><a href="#cb77-2" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(mu_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500   1</code></pre>
</div>
<div class="sourceCode cell-code" id="cb79"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb79-1"><a href="#cb79-1" aria-hidden="true" tabindex="-1"></a>D_coba[<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>,<span class="dv">1</span><span class="sc">:</span><span class="dv">5</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>5 x 5 diagonal matrix of class "ddiMatrix"
     [,1] [,2] [,3] [,4] [,5]
[1,] 0.25    .    .    .    .
[2,]    . 0.25    .    .    .
[3,]    .    . 0.25    .    .
[4,]    .    .    . 0.25    .
[5,]    .    .    .    . 0.25</code></pre>
</div>
<div class="sourceCode cell-code" id="cb81"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb81-1"><a href="#cb81-1" aria-hidden="true" tabindex="-1"></a>mu_coba <span class="ot">&lt;-</span> <span class="fu">as.matrix</span>( <span class="fu">runif</span>(<span class="at">n =</span> <span class="fu">nrow</span>(X),<span class="at">min =</span> <span class="dv">0</span>,<span class="at">max =</span> <span class="dv">1</span> ) )</span>
<span id="cb81-2"><a href="#cb81-2" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(mu_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500   1</code></pre>
</div>
<div class="sourceCode cell-code" id="cb83"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb83-1"><a href="#cb83-1" aria-hidden="true" tabindex="-1"></a><span class="fu">head</span>(mu_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>           [,1]
[1,] 0.77550659
[2,] 0.94264755
[3,] 0.47241345
[4,] 0.08665263
[5,] 0.63646300
[6,] 0.42453500</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb85"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb85-1"><a href="#cb85-1" aria-hidden="true" tabindex="-1"></a>z_coba <span class="ot">&lt;-</span> <span class="fu">z</span>(<span class="at">X =</span> X,<span class="at">beta =</span> beta_coba,<span class="at">D =</span> D_coba,<span class="at">y =</span> y,<span class="at">mu =</span> mu_coba)</span>
<span id="cb85-2"><a href="#cb85-2" aria-hidden="true" tabindex="-1"></a><span class="fu">dim</span>(z_coba)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 500   1</code></pre>
</div>
<div class="sourceCode cell-code" id="cb87"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb87-1"><a href="#cb87-1" aria-hidden="true" tabindex="-1"></a>z_coba[<span class="dv">1</span><span class="sc">:</span><span class="dv">10</span>]</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code> [1] -3.1200264  2.2434098 -1.6766538 -0.8296105 -1.7598520 -1.7851400
 [7] -3.2987687 -1.1895575 -1.5743409  0.1808609</code></pre>
</div>
</div>
<p>Supaya lebih mudah, kita kumpulkan semua definisi matriks yang sudah dituliskan ke program R dibawah ini</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb89"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb89-1"><a href="#cb89-1" aria-hidden="true" tabindex="-1"></a>mu <span class="ot">&lt;-</span> <span class="cf">function</span>(X,beta){</span>
<span id="cb89-2"><a href="#cb89-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">exp</span>(X <span class="sc">%*%</span> beta) <span class="sc">/</span> ( <span class="dv">1</span><span class="sc">+</span><span class="fu">exp</span>( X<span class="sc">%*%</span> beta) )</span>
<span id="cb89-3"><a href="#cb89-3" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb90"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb90-1"><a href="#cb90-1" aria-hidden="true" tabindex="-1"></a>W <span class="ot">&lt;-</span> <span class="cf">function</span>(m,pi){</span>
<span id="cb90-2"><a href="#cb90-2" aria-hidden="true" tabindex="-1"></a>wi <span class="ot">&lt;-</span> m <span class="sc">*</span> pi <span class="sc">*</span> ( <span class="dv">1</span><span class="sc">-</span> pi )</span>
<span id="cb90-3"><a href="#cb90-3" aria-hidden="true" tabindex="-1"></a><span class="fu">Diagonal</span>(<span class="at">x=</span><span class="fu">as.numeric</span>(wi))</span>
<span id="cb90-4"><a href="#cb90-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb91"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb91-1"><a href="#cb91-1" aria-hidden="true" tabindex="-1"></a>D <span class="ot">&lt;-</span> <span class="cf">function</span>(pi){</span>
<span id="cb91-2"><a href="#cb91-2" aria-hidden="true" tabindex="-1"></a>di <span class="ot">&lt;-</span> pi <span class="sc">*</span> ( <span class="dv">1</span><span class="sc">-</span> pi )</span>
<span id="cb91-3"><a href="#cb91-3" aria-hidden="true" tabindex="-1"></a><span class="fu">Diagonal</span>(<span class="at">x=</span><span class="fu">as.numeric</span>(di))</span>
<span id="cb91-4"><a href="#cb91-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb92"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb92-1"><a href="#cb92-1" aria-hidden="true" tabindex="-1"></a>z <span class="ot">&lt;-</span> <span class="cf">function</span>(X,beta,D,y,mu){</span>
<span id="cb92-2"><a href="#cb92-2" aria-hidden="true" tabindex="-1"></a>  inv_D <span class="ot">&lt;-</span> <span class="fu">chol2inv</span>(<span class="fu">chol</span>(D))</span>
<span id="cb92-3"><a href="#cb92-3" aria-hidden="true" tabindex="-1"></a> X <span class="sc">%*%</span> beta <span class="sc">+</span> inv_D <span class="sc">%*%</span>  (y<span class="sc">-</span>mu)</span>
<span id="cb92-4"><a href="#cb92-4" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>Selanjutnya kita akan mulai menuliskan program R untuk iterasi IRLS</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb93"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb93-1"><a href="#cb93-1" aria-hidden="true" tabindex="-1"></a>stop_criterion <span class="ot">&lt;-</span> <span class="cf">function</span>(beta_old,beta_new,tol) {</span>
<span id="cb93-2"><a href="#cb93-2" aria-hidden="true" tabindex="-1"></a>  error <span class="ot">&lt;-</span> <span class="fu">as.matrix</span>(<span class="fu">abs</span>(beta_new<span class="sc">-</span>beta_old))</span>
<span id="cb93-3"><a href="#cb93-3" aria-hidden="true" tabindex="-1"></a>  status <span class="ot">&lt;-</span> <span class="fu">all</span>(error  <span class="sc">&lt;</span> tol)</span>
<span id="cb93-4"><a href="#cb93-4" aria-hidden="true" tabindex="-1"></a>  <span class="fu">return</span>(<span class="fu">list</span>(<span class="at">error=</span><span class="fu">as.data.frame</span>(<span class="fu">t</span>(error)),<span class="at">status=</span>status))</span>
<span id="cb93-5"><a href="#cb93-5" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb94"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb94-1"><a href="#cb94-1" aria-hidden="true" tabindex="-1"></a><span class="fu">stop_criterion</span>(<span class="at">beta_old =</span> <span class="fu">c</span>(<span class="fl">0.5</span>,<span class="sc">-</span><span class="fl">0.9</span>),<span class="at">beta_new =</span> <span class="fu">c</span>(<span class="fl">0.51</span>,<span class="sc">-</span><span class="fl">0.91</span>),<span class="at">tol =</span> <span class="fl">1e-5</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$error
    V1   V2
1 0.01 0.01

$status
[1] FALSE</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb96"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb96-1"><a href="#cb96-1" aria-hidden="true" tabindex="-1"></a><span class="fu">stop_criterion</span>(<span class="at">beta_old =</span> <span class="fu">c</span>(<span class="fl">0.5</span>,<span class="sc">-</span><span class="fl">0.9</span>),<span class="at">beta_new =</span> <span class="fu">c</span>(<span class="fl">0.50001</span>,<span class="sc">-</span><span class="fl">0.90001</span>),<span class="at">tol =</span> <span class="fl">1e-5</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$error
     V1    V2
1 1e-05 1e-05

$status
[1] TRUE</code></pre>
</div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb98"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb98-1"><a href="#cb98-1" aria-hidden="true" tabindex="-1"></a><span class="fu">stop_criterion</span>(<span class="at">beta_old =</span> <span class="fu">c</span>(<span class="fl">0.5</span>,<span class="sc">-</span><span class="fl">0.9</span>),<span class="at">beta_new =</span> <span class="fu">c</span>(<span class="fl">0.5001</span>,<span class="sc">-</span><span class="fl">0.90001</span>),<span class="at">tol =</span> <span class="fl">1e-5</span>)</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>$error
     V1    V2
1 1e-04 1e-05

$status
[1] FALSE</code></pre>
</div>
</div>
<p>berikut adalah nilai awal dari <span class="math inline">\(\boldsymbol{\beta}_{(p+1)})}\)</span>, nilai toleransi, iterasi maksimum dan nilai dari <span class="math inline">\(m_i\)</span>. Khusus untuk <span class="math inline">\(m_i=1\)</span> karena respon <code>subscribed</code> adalah respon distribusi bernouli.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb100"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb100-1"><a href="#cb100-1" aria-hidden="true" tabindex="-1"></a>beta_new <span class="ot">&lt;-</span> <span class="fu">rep</span>(<span class="dv">0</span>,<span class="fu">ncol</span>(X))</span>
<span id="cb100-2"><a href="#cb100-2" aria-hidden="true" tabindex="-1"></a><span class="fu">names</span>(beta_new) <span class="ot">&lt;-</span> <span class="fu">colnames</span>(X)</span>
<span id="cb100-3"><a href="#cb100-3" aria-hidden="true" tabindex="-1"></a>beta_new</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>   (Intercept)        balance            age     housingyes maritalmarried 
             0              0              0              0              0 
 maritalsingle 
             0 </code></pre>
</div>
<div class="sourceCode cell-code" id="cb102"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb102-1"><a href="#cb102-1" aria-hidden="true" tabindex="-1"></a>max_iter <span class="ot">&lt;-</span> <span class="dv">1000</span></span>
<span id="cb102-2"><a href="#cb102-2" aria-hidden="true" tabindex="-1"></a>mi <span class="ot">&lt;-</span> <span class="dv">1</span></span>
<span id="cb102-3"><a href="#cb102-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb102-4"><a href="#cb102-4" aria-hidden="true" tabindex="-1"></a>tolerance <span class="ot">&lt;-</span>  <span class="fl">1e-15</span></span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>Ingat Formula IRLS yang digunakan adalah sebagai berikut:</p>
<p><span class="math display">\[
\boldsymbol{\beta}_{(p+1)×1}^{(𝑖+1)}  = \left\{ \boldsymbol{X}_{(𝑝+1) \times n }^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\}^{-1} \boldsymbol{X}_{(𝑝+1) \times n}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{z}_{n \times1}^{(i)}
\]</span></p>
<div class="cell">
<div class="sourceCode cell-code" id="cb103"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb103-1"><a href="#cb103-1" aria-hidden="true" tabindex="-1"></a><span class="cf">for</span>(i <span class="cf">in</span> <span class="dv">1</span><span class="sc">:</span>max_iter){</span>
<span id="cb103-2"><a href="#cb103-2" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-3"><a href="#cb103-3" aria-hidden="true" tabindex="-1"></a>  <span class="co">#menyimpan beta lama</span></span>
<span id="cb103-4"><a href="#cb103-4" aria-hidden="true" tabindex="-1"></a>  beta_old <span class="ot">&lt;-</span> beta_new</span>
<span id="cb103-5"><a href="#cb103-5" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-6"><a href="#cb103-6" aria-hidden="true" tabindex="-1"></a>  mu_new <span class="ot">&lt;-</span> <span class="fu">mu</span>(<span class="at">X =</span> X,<span class="at">beta =</span> beta_new)</span>
<span id="cb103-7"><a href="#cb103-7" aria-hidden="true" tabindex="-1"></a>  W_new <span class="ot">&lt;-</span> <span class="fu">W</span>(<span class="at">m =</span> mi,<span class="at">pi =</span> mu_new)</span>
<span id="cb103-8"><a href="#cb103-8" aria-hidden="true" tabindex="-1"></a>  D_new <span class="ot">&lt;-</span> <span class="fu">D</span>(<span class="at">pi =</span> mu_new)</span>
<span id="cb103-9"><a href="#cb103-9" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-10"><a href="#cb103-10" aria-hidden="true" tabindex="-1"></a>  z_new <span class="ot">&lt;-</span> <span class="fu">z</span>(<span class="at">X =</span> X,<span class="at">beta =</span> beta_new,<span class="at">D =</span> D_new,<span class="at">y =</span> y,<span class="at">mu =</span> mu_new)</span>
<span id="cb103-11"><a href="#cb103-11" aria-hidden="true" tabindex="-1"></a>  inv_XWX <span class="ot">&lt;-</span> <span class="fu">chol2inv</span>(<span class="fu">chol</span>(<span class="fu">crossprod</span>(X,W_new <span class="sc">%*%</span> X)))</span>
<span id="cb103-12"><a href="#cb103-12" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-13"><a href="#cb103-13" aria-hidden="true" tabindex="-1"></a>  <span class="co">#formulasi fisher scoring</span></span>
<span id="cb103-14"><a href="#cb103-14" aria-hidden="true" tabindex="-1"></a>  beta_new <span class="ot">&lt;-</span> inv_XWX <span class="sc">%*%</span> <span class="fu">crossprod</span>(X,W_new <span class="sc">%*%</span> z_new) </span>
<span id="cb103-15"><a href="#cb103-15" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-16"><a href="#cb103-16" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb103-17"><a href="#cb103-17" aria-hidden="true" tabindex="-1"></a>  <span class="co">#menghitung stopping criterion</span></span>
<span id="cb103-18"><a href="#cb103-18" aria-hidden="true" tabindex="-1"></a>  stop_criterion_iter <span class="ot">&lt;-</span> <span class="fu">stop_criterion</span>(</span>
<span id="cb103-19"><a href="#cb103-19" aria-hidden="true" tabindex="-1"></a>                 <span class="at">beta_old =</span> beta_old,</span>
<span id="cb103-20"><a href="#cb103-20" aria-hidden="true" tabindex="-1"></a>                 <span class="at">beta_new =</span> beta_new,</span>
<span id="cb103-21"><a href="#cb103-21" aria-hidden="true" tabindex="-1"></a>                 <span class="at">tol =</span> tolerance)</span>
<span id="cb103-22"><a href="#cb103-22" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-23"><a href="#cb103-23" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb103-24"><a href="#cb103-24" aria-hidden="true" tabindex="-1"></a>  </span>
<span id="cb103-25"><a href="#cb103-25" aria-hidden="true" tabindex="-1"></a>  <span class="co">#iterasi berhenti jika sudah memenuhi stopping criterion</span></span>
<span id="cb103-26"><a href="#cb103-26" aria-hidden="true" tabindex="-1"></a>  <span class="cf">if</span>(stop_criterion_iter<span class="sc">$</span>status) <span class="cf">break</span></span>
<span id="cb103-27"><a href="#cb103-27" aria-hidden="true" tabindex="-1"></a>}</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<p>Saat Convergent maka kita mendapatkan</p>
<p><span class="math display">\[
Var(\hat{\boldsymbol{\beta}}_{(p+1) \times 1})=  \left\{ \boldsymbol{X}_{n \times (𝑝+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)}  \right\}^{-1}
\]</span></p>
<p>kemudian standard error dari <span class="math inline">\(\hat{\boldsymbol{\beta}}_{(p+1) \times 1}\)</span> adalah akar dari diagonal utama <span class="math inline">\(\left\{ \boldsymbol{X}_{n \times (𝑝+1)}^{t} \boldsymbol{W}_{n \times n}^{(i)} \boldsymbol{X}_{n \times (𝑝+1)} \right\}^{-1}\)</span>.</p>
<div class="cell">
<div class="sourceCode cell-code" id="cb104"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb104-1"><a href="#cb104-1" aria-hidden="true" tabindex="-1"></a>result_irls <span class="ot">&lt;-</span> <span class="fu">list</span>(<span class="at">iter_convergence=</span>i,<span class="at">coefficients=</span><span class="fu">as.numeric</span>(beta_new),<span class="at">var_beta=</span>inv_XWX)</span>
<span id="cb104-2"><a href="#cb104-2" aria-hidden="true" tabindex="-1"></a>result_irls<span class="sc">$</span>iter_convergence</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>[1] 33</code></pre>
</div>
<div class="sourceCode cell-code" id="cb106"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb106-1"><a href="#cb106-1" aria-hidden="true" tabindex="-1"></a>result_irls<span class="sc">$</span>var_beta</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>6 x 6 Matrix of class "dpoMatrix"
                 (Intercept)       balance           age    housingyes
(Intercept)     2.743637e-01 -5.891964e-07 -4.050466e-03 -3.584211e-02
balance        -5.891964e-07  1.308069e-09 -3.003060e-08  6.255880e-07
age            -4.050466e-03 -3.003060e-08  8.377425e-05  3.146135e-04
housingyes     -3.584211e-02  6.255880e-07  3.146135e-04  3.568298e-02
maritalmarried -7.623728e-02 -2.022522e-07  2.006810e-04  5.139815e-03
maritalsingle  -1.230458e-01 -4.027429e-07  1.169965e-03  8.360438e-03
               maritalmarried maritalsingle
(Intercept)     -7.623728e-02 -1.230458e-01
balance         -2.022522e-07 -4.027429e-07
age              2.006810e-04  1.169965e-03
housingyes       5.139815e-03  8.360438e-03
maritalmarried   8.060487e-02  6.751034e-02
maritalsingle    6.751034e-02  1.072151e-01</code></pre>
</div>
<div class="sourceCode cell-code" id="cb108"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb108-1"><a href="#cb108-1" aria-hidden="true" tabindex="-1"></a>summary_irls <span class="ot">&lt;-</span> <span class="fu">data.frame</span>(<span class="at">variables=</span><span class="fu">rownames</span>(beta_new),</span>
<span id="cb108-2"><a href="#cb108-2" aria-hidden="true" tabindex="-1"></a>                         <span class="at">Estimate=</span><span class="fu">round</span>(result_irls<span class="sc">$</span>coefficients,<span class="dv">10</span>),</span>
<span id="cb108-3"><a href="#cb108-3" aria-hidden="true" tabindex="-1"></a>                         <span class="at">Std_Err=</span><span class="fu">round</span>(<span class="fu">sqrt</span>(<span class="fu">diag</span>(<span class="fu">as.matrix</span>(result_irls<span class="sc">$</span>var_beta))),<span class="dv">10</span>),<span class="at">row.names =</span> <span class="cn">NULL</span>) <span class="sc">%&gt;%</span> </span>
<span id="cb108-4"><a href="#cb108-4" aria-hidden="true" tabindex="-1"></a>              <span class="fu">mutate</span>(<span class="at">z=</span>Estimate <span class="sc">/</span> Std_Err, <span class="at">p_value=</span><span class="fu">round</span>(<span class="dv">2</span><span class="sc">*</span><span class="fu">pnorm</span>(<span class="at">q=</span><span class="fu">abs</span>(z),<span class="at">lower.tail =</span> F),<span class="dv">3</span>))</span>
<span id="cb108-5"><a href="#cb108-5" aria-hidden="true" tabindex="-1"></a>summary_irls</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code>       variables      Estimate      Std_Err          z p_value
1    (Intercept)  0.2300633445 0.5237974260  0.4392220   0.661
2        balance  0.0000557833 0.0000361672  1.5423726   0.123
3            age  0.0024653247 0.0091528273  0.2693512   0.788
4     housingyes -0.7690447815 0.1888993831 -4.0711874   0.000
5 maritalmarried -0.1661114916 0.2839099667 -0.5850851   0.558
6  maritalsingle  0.1087506638 0.3274371898  0.3321268   0.740</code></pre>
</div>
</div>
</section>
<section id="default-fungsi-r" class="level3">
<h3 class="anchored" data-anchor-id="default-fungsi-r">Default fungsi R</h3>
<div class="cell">
<div class="sourceCode cell-code" id="cb110"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb110-1"><a href="#cb110-1" aria-hidden="true" tabindex="-1"></a>mod1 <span class="ot">&lt;-</span> <span class="fu">glm</span>(<span class="at">formula =</span> subscribed<span class="sc">~</span>.,</span>
<span id="cb110-2"><a href="#cb110-2" aria-hidden="true" tabindex="-1"></a>            <span class="at">data =</span> bank_marketing_mini,</span>
<span id="cb110-3"><a href="#cb110-3" aria-hidden="true" tabindex="-1"></a>            <span class="at">family =</span> <span class="fu">binomial</span>(<span class="at">link =</span> <span class="st">"logit"</span>))</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
</div>
<div class="cell">
<div class="sourceCode cell-code" id="cb111"><pre class="sourceCode r code-with-copy"><code class="sourceCode r"><span id="cb111-1"><a href="#cb111-1" aria-hidden="true" tabindex="-1"></a><span class="fu">tidy</span>(mod1) <span class="sc">%&gt;%</span> </span>
<span id="cb111-2"><a href="#cb111-2" aria-hidden="true" tabindex="-1"></a>  <span class="fu">mutate</span>(<span class="fu">across</span>(<span class="fu">where</span>(is.numeric),<span class="cf">function</span>(x) <span class="fu">round</span>(x,<span class="dv">7</span>)))</span></code><button title="Copy to Clipboard" class="code-copy-button"><i class="bi"></i></button></pre></div>
<div class="cell-output cell-output-stdout">
<pre><code># A tibble: 6 × 5
  term             estimate std.error statistic   p.value
  &lt;chr&gt;               &lt;dbl&gt;     &lt;dbl&gt;     &lt;dbl&gt;     &lt;dbl&gt;
1 (Intercept)     0.230     0.524         0.439 0.661    
2 balance         0.0000558 0.0000362     1.54  0.123    
3 age             0.00247   0.00915       0.269 0.788    
4 housingyes     -0.769     0.189        -4.07  0.0000468
5 maritalmarried -0.166     0.284        -0.585 0.558    
6 maritalsingle   0.109     0.327         0.332 0.740    </code></pre>
</div>
</div>
</section>
</section>

</main>
<!-- /main column -->
<script id="quarto-html-after-body" type="application/javascript">
window.document.addEventListener("DOMContentLoaded", function (event) {
  const toggleBodyColorMode = (bsSheetEl) => {
    const mode = bsSheetEl.getAttribute("data-mode");
    const bodyEl = window.document.querySelector("body");
    if (mode === "dark") {
      bodyEl.classList.add("quarto-dark");
      bodyEl.classList.remove("quarto-light");
    } else {
      bodyEl.classList.add("quarto-light");
      bodyEl.classList.remove("quarto-dark");
    }
  }
  const toggleBodyColorPrimary = () => {
    const bsSheetEl = window.document.querySelector("link#quarto-bootstrap");
    if (bsSheetEl) {
      toggleBodyColorMode(bsSheetEl);
    }
  }
  toggleBodyColorPrimary();  
  const icon = "";
  const anchorJS = new window.AnchorJS();
  anchorJS.options = {
    placement: 'right',
    icon: icon
  };
  anchorJS.add('.anchored');
  const clipboard = new window.ClipboardJS('.code-copy-button', {
    target: function(trigger) {
      return trigger.previousElementSibling;
    }
  });
  clipboard.on('success', function(e) {
    // button target
    const button = e.trigger;
    // don't keep focus
    button.blur();
    // flash "checked"
    button.classList.add('code-copy-button-checked');
    var currentTitle = button.getAttribute("title");
    button.setAttribute("title", "Copied!");
    let tooltip;
    if (window.bootstrap) {
      button.setAttribute("data-bs-toggle", "tooltip");
      button.setAttribute("data-bs-placement", "left");
      button.setAttribute("data-bs-title", "Copied!");
      tooltip = new bootstrap.Tooltip(button, 
        { trigger: "manual", 
          customClass: "code-copy-button-tooltip",
          offset: [0, -8]});
      tooltip.show();    
    }
    setTimeout(function() {
      if (tooltip) {
        tooltip.hide();
        button.removeAttribute("data-bs-title");
        button.removeAttribute("data-bs-toggle");
        button.removeAttribute("data-bs-placement");
      }
      button.setAttribute("title", currentTitle);
      button.classList.remove('code-copy-button-checked');
    }, 1000);
    // clear code selection
    e.clearSelection();
  });
  function tippyHover(el, contentFn) {
    const config = {
      allowHTML: true,
      content: contentFn,
      maxWidth: 500,
      delay: 100,
      arrow: false,
      appendTo: function(el) {
          return el.parentElement;
      },
      interactive: true,
      interactiveBorder: 10,
      theme: 'quarto',
      placement: 'bottom-start'
    };
    window.tippy(el, config); 
  }
  const noterefs = window.document.querySelectorAll('a[role="doc-noteref"]');
  for (var i=0; i<noterefs.length; i++) {
    const ref = noterefs[i];
    tippyHover(ref, function() {
      // use id or data attribute instead here
      let href = ref.getAttribute('data-footnote-href') || ref.getAttribute('href');
      try { href = new URL(href).hash; } catch {}
      const id = href.replace(/^#\/?/, "");
      const note = window.document.getElementById(id);
      return note.innerHTML;
    });
  }
  const findCites = (el) => {
    const parentEl = el.parentElement;
    if (parentEl) {
      const cites = parentEl.dataset.cites;
      if (cites) {
        return {
          el,
          cites: cites.split(' ')
        };
      } else {
        return findCites(el.parentElement)
      }
    } else {
      return undefined;
    }
  };
  var bibliorefs = window.document.querySelectorAll('a[role="doc-biblioref"]');
  for (var i=0; i<bibliorefs.length; i++) {
    const ref = bibliorefs[i];
    const citeInfo = findCites(ref);
    if (citeInfo) {
      tippyHover(citeInfo.el, function() {
        var popup = window.document.createElement('div');
        citeInfo.cites.forEach(function(cite) {
          var citeDiv = window.document.createElement('div');
          citeDiv.classList.add('hanging-indent');
          citeDiv.classList.add('csl-entry');
          var biblioDiv = window.document.getElementById('ref-' + cite);
          if (biblioDiv) {
            citeDiv.innerHTML = biblioDiv.innerHTML;
          }
          popup.appendChild(citeDiv);
        });
        return popup.innerHTML;
      });
    }
  }
});
</script>
</div> <!-- /content -->



</body></html>