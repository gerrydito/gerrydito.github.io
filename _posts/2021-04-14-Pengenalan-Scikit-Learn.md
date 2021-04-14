---
layout: post
title: Pengenalan Scikit Learn
categories: [Machine Learning,python]
excerpt: Scikit-learn (Sklearn) adalah salah satu package paling berguna  untuk machine learning  dengan Python. Package ini menyediakan pilihan alat yang efisien untuk machine learning seperti  klasifikasi, regresi, clustering, dan dimension reduction melalui antarmuka konsistensi dengan Python. Package  in  sebagian besar dibangun di atas NumPy, SciPy dan Matplotlib.
---

<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>PengenalanScikitLearn</title><script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>

<style type="text/css">
  pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: #ffffcc }
.highlight { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
  </style>



<style type="text/css">
/*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook-f:before,
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-feed:before,
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before,
.fa-gratipay:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper-pp:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-resistance:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-y-combinator-square:before,
.fa-yc-square:before,
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
.modal-header {
  cursor: move;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: text-bottom;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
[dir="rtl"] .list_item > div input {
  margin-right: 0;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
div.output_area .mglyph > img {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 1px 0 1px 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
.toolbar-btn-label {
  margin-left: 6px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */</style>
<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  body {
    margin: 0;
  }
  div.cell {
    display: block;
    page-break-inside: avoid;
  }
  div.output_wrapper {
    display: block;
    page-break-inside: avoid;
  }
  div.output {
    display: block;
    page-break-inside: avoid;
  }
}
</style>


<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-MML-AM_CHTML-full,Safe"> </script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    init_mathjax = function() {
        if (window.MathJax) {
        // MathJax loaded
            MathJax.Hub.Config({
                TeX: {
                    equationNumbers: {
                    autoNumber: "AMS",
                    useLabelIds: true
                    }
                },
                tex2jax: {
                    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                    processEscapes: true,
                    processEnvironments: true
                },
                displayAlign: 'center',
                CommonHTML: {
                    linebreaks: { 
                    automatic: true 
                    }
                },
                "HTML-CSS": {
                    linebreaks: { 
                    automatic: true 
                    }
                }
            });
        
            MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
        }
    }
    init_mathjax();
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<br>
<br>
<p>Scikit-learn (Sklearn) adalah salah satu package paling berguna  untuk machine learning  dengan Python. Package ini menyediakan pilihan alat yang efisien untuk machine learning seperti  klasifikasi, regresi, clustering, dan dimension reduction melalui antarmuka konsistensi dengan Python. Package  in  sebagian besar dibangun di atas NumPy, SciPy dan Matplotlib.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Unsupervised-Methods">Unsupervised Methods<a class="anchor-link" href="#Unsupervised-Methods">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Data">Data<a class="anchor-link" href="#Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Data Pelanggan Mall</p>
<p>Seorang pemilik Mall ingin mengelompokan customer di Mall yang ia miliki, sehingga tim marketing bisa mengembangkan strategi yang tepat untuk customer yang tepat pula. Data yang dimiliki oleh Mall tersebut adalah Customer ID, umur pelanggan (age), pendapatan tahunan dalam ribu dollar (annual income) dan spending score. Spending score merupakan nilai yang diberikan oleh Mall kepada customer berbasarkan perilaku customer (waktu kunjungan,jenis barang yang dibeli, dan banyaknya uang yang dihabiskan dalam belanja) yang memiliki rentang nilai 1-100. Semakin besar nilai Spending Score berarti customer semakin loyal pada Mall tersebut dan semakin besar pula uang belanja yang digunakan.</p>
<p>Data bisa diperoleh di link berikut <a href="https://drive.google.com/file/d/1P3WVtw2njbEcxV5y3-5hvO6P52D7j7MB/view?usp=sharing">Mall Customer</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Import-data">Import data<a class="anchor-link" href="#Import-data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>untuk mengimport data dalam bentuk <code>csv</code> kita membutuhkan package <code>pandas</code></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="n">mall</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;Mall_Customers.csv&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>kita bisa menanpilkan 5 baris pertama dengan methods <code>head</code></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[2]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CustomerID</th>
      <th>Genre</th>
      <th>Age</th>
      <th>Annual Income</th>
      <th>Spending Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Male</td>
      <td>19</td>
      <td>15</td>
      <td>39</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Male</td>
      <td>21</td>
      <td>15</td>
      <td>81</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Female</td>
      <td>20</td>
      <td>16</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Female</td>
      <td>23</td>
      <td>16</td>
      <td>77</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Female</td>
      <td>31</td>
      <td>17</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Peubah yang digunakan untuk menerapkan k-means adalah peubah Age Annual Income dan Spending Score. Oleh karena itu peubah yang tidak kita gunakan akan kita hilangkan tersebih dahulu.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall</span> <span class="o">=</span> <span class="n">mall</span><span class="o">.</span><span class="n">filter</span><span class="p">([</span><span class="s2">&quot;Age&quot;</span><span class="p">,</span><span class="s2">&quot;Annual Income&quot;</span><span class="p">,</span><span class="s2">&quot;Spending Score&quot;</span><span class="p">])</span>
<span class="n">mall</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Annual Income</th>
      <th>Spending Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>15</td>
      <td>39</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>15</td>
      <td>81</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20</td>
      <td>16</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23</td>
      <td>16</td>
      <td>77</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31</td>
      <td>17</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Standarisasi">Standarisasi<a class="anchor-link" href="#Standarisasi">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Standarisasi peubah merupakan proses transformasi peubah menjadi peubah yang memiliki rata-rata nol dan simpangan baku satu. Process standarisasi ini dilakukan jika kita melihat perbedanan satuan pengukuran peubah-peubah yang digunakan contoh(umur dan pendapatan). Standarisasi dilakukan karena metode k-means menggunakan konsep jarak antara objek/amatan, yang mana sensitif terhadap satuan pengukuran. Formula untuk standarisasi data adalah sebagai berikut:</p>
$$y = \frac{y-\bar{y}}{\sigma_{y}}$$<p>dengan $\bar{y}$ merupakan rata-rata dari $y$ dan $\sigma_{y}$ merupakan simpangan baku dari y.</p>
<p>Dalam Python, standarisasi data bisa dilakukan dengan menggunakan fungsi <code>StandardScaler</code> dari package <code>sklearn</code>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="kn">import</span> <span class="n">StandardScaler</span>
<span class="n">scale</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Setelah kita mempersiapkan fungsi untuk standarisasi data, berikutnya kita akan terapkan pada data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">scale</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall</span><span class="p">)</span>
<span class="n">mall_scale</span> <span class="o">=</span> <span class="n">scale</span><span class="o">.</span><span class="n">transform</span><span class="p">(</span><span class="n">mall</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;mean&quot;</span><span class="p">,</span><span class="n">scale</span><span class="o">.</span><span class="n">mean_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;std&quot;</span><span class="p">,</span><span class="n">scale</span><span class="o">.</span><span class="n">scale_</span><span class="p">)</span>
<span class="nb">type</span><span class="p">(</span><span class="n">mall</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>mean [38.85 60.56 50.2 ]
std [13.93404105 26.19897708 25.75888196]
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[5]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>pandas.core.frame.DataFrame</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Memilih-metode-Unsupervised-Learning">Memilih metode Unsupervised Learning<a class="anchor-link" href="#Memilih-metode-Unsupervised-Learning">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Metode yang digunakan untuk tutorial ini adalah metode K-Means dan Hierarchical clustering. Kedua metode tersebut bisa kita dapatkan pada package sklearn</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="kn">import</span> <span class="n">KMeans</span>
<span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="kn">import</span> <span class="n">AgglomerativeClustering</span>
<span class="n">kmeans</span> <span class="o">=</span> <span class="n">KMeans</span><span class="p">()</span>
<span class="n">hclust</span> <span class="o">=</span> <span class="n">AgglomerativeClustering</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Memilih-Jumlah-Cluster-Optimum">Memilih Jumlah Cluster Optimum<a class="anchor-link" href="#Memilih-Jumlah-Cluster-Optimum">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Umumnya, banyaknya cluster dapat ditentukan dengan menggunakan beberapa kriteria statistik, seperti koefisien <strong>silhouette</strong> dan <strong>WSS</strong> atau (Within Sum of Square).</p>
<p>Kriteria koefisien silhouette dihitung berdasarkan jarak antar amatan. Koefisien ini mengukur seberapa dekat suatu amatan dengan amatan lain yang berada di clusterl yang sama (dikenal sebagai ukuran cohesion) dibandingkan dengan jarak terhadap amatan lain yang berada di cluster berbeda (dikenal sebagai ukuran separation).  Koefisien yang nilainya semakin besar menunjukkan bahwa clusterl yang terbentuk sudah sesuai.</p>
<p>Kriteria WSS merupakan kriteria yangmenghitung keragamaan dalam cluster yang terbentuk. Semakin kecil keragaman dalam cluster yang terbentuk menunjukkan bahwa cluster yang terbentuk sudah sesuai.</p>
<p>Dengan menggunakan kriteria tersebut, kita bisa membandingkan banyaknya cluster yang paling sesuai pada data yang kita sedang analisis dengan menggunakan suatu plot. Untuk itu kita perlu menginstall pacakage <code>yellowbrick</code> berikut ini</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">!</span> pip install yellowbrick
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Untuk kriteria koefisien silhoutte, banyaknya cluster dengan nilai koefisien tertinggi yang kita pilih. Sedangkan pada WSS, banyaknya cluster yang kita pilih didasarkan pada banyaknya cluster yang mana garisnya berbentuk seperti siku (elbow).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="K-Means">K-Means<a class="anchor-link" href="#K-Means">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">yellowbrick.cluster</span> <span class="kn">import</span> <span class="n">KElbowVisualizer</span>

<span class="c1"># Silhouette</span>
<span class="n">kmeans_vis_sil</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">kmeans</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;silhouette&quot;</span><span class="p">)</span>

<span class="n">kmeans_vis_sil</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">kmeans_vis_sil</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAiMAAAFlCAYAAAA5w+hdAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAACWz0lEQVR4nOzdd1xV9f/A8de5kwuXvUQElOXeaLlz5syRpWWOpu36tfew3be9bHy/lS2zUlOz0tTSQnODe4AoU/a6wN3n9wdyFRFBBe4FPs/Hw8eDe8963+OF+76f8f5IsizLCIIgCIIgOInC2QEIgiAIgtC6iWREEARBEASnEsmIIAiCIAhOJZIRQRAEQRCcSiQjgiAIgiA4lUhGBEEQBEFwKpGMCA0uISGB2bNnM2nSJCZOnMgtt9zC0aNHAdi7dy/33nsvAI899hj/+9//AOjYsSMFBQVNEt9NN93kuNaPP/7It99+e8Hn+Ouvv5gxYwZXXXUVEyZM4L777uPkyZMNHWqdli1bRt++fZk8eXK1f4888gjQ9Pf44MGDjBo1imnTppGenn5R59i6dSsTJ06s9twXX3zB0KFDOXToEFu3bqVjx448+uijNY6dPXs2vXv3vqjrNqQ///yT2bNnM3nyZCZMmMD9999PVlYWUPl/Nn/+/Is+9wcffMC6desu+Lhbb72VpKSki76uIDQmlbMDEFoWs9nM/Pnz+fzzz+natSsAK1as4NZbb2X9+vV0796d9957z6kxxsfHO37euXMnMTExF3R8dnY2jz76KMuWLSM0NBSAhQsXcv/99/P99983aKz1ERcXxyeffNLk1z2X9evXc9lll/HSSy812Dnffvtt1q5dy+LFiwkNDWXr1q0EBgby559/UlFRgU6nAyAjI4OUlJQGu+7FWrVqFQsXLmThwoVEREQgyzKffvopc+bMYfXq1Zd8/q1btxIdHX3Bx3322WeXfG1BaCwiGREaVEVFBaWlpZSXlzueu+qqq9Dr9dhsNnbs2MELL7zAL7/8UuPY999/n8TERIqKirj55puZNWsWAB9++CGrV69GqVTSoUMHnn76aQIDA5k9ezazZs1i7NixANUeJycn89JLL1FUVITNZmP27NlMnz6dxx9/HIC5c+dy8803s2HDBuLj43Fzc2PWrFksXLiQtWvXYrfbCQ0N5dlnnyU4OLhanIWFhVgslmqvce7cuXTq1Mnx+JNPPmH58uWoVCoiIiJ49dVX8fT0PO9r8fb25tixY1x33XVMmTKFl156iSNHjmCxWBgwYACPPPIIKtWl/cq+88477N27F7vdzv3338/w4cNrvceJiYl8/vnnfPfddwBceeWVTJgwgXvvvZeTJ08yffp0Nm3ahEJR2cC6cuVKFi9ejM1mw2g08uabb9b79c6ePbtGrHa7nQULFnDo0CG+++47fH19Hdt8fHwICwtj3bp1TJo0CYCff/6ZSZMmVUsIf/zxRxYvXozdbsfHx4enn36aqKgoUlJSWLBgAWVlZeTm5tKpUyfeeecdtFot3bt357bbbiM+Pp6cnBxuueUWrr/+enJzc3n00UcpLCwEYNiwYdx///014n777bd54YUXiIiIAECSJG677TZCQkIwm83V9j3fe/i9997jjz/+QK1W4+vryyuvvMIff/zBvn37eP3111EqlQwbNow33niD7du3Y7PZ6NKlC0899RR6vZ4RI0bQo0cPDh8+zAMPPMArr7zCu+++S3l5OW+//TZhYWEcPXoUq9XK888/T9++fSkoKODxxx8nNTUVHx8fAgMDiYmJ4Z577rmo95sg1JfophEalLe3Nw8//DC33HILI0eO5OGHH2bp0qUMHDgQjUZz3mPDwsJYtmwZH3zwAa+++ioWi4WlS5fy999/89NPP7Fq1SpiYmJ47LHHznseq9XKvffey4MPPsiyZcv45ptv+Pzzz0lISOCVV14BYNGiRUyZMoURI0Ywb948Zs2axc8//8yRI0f48ccfWbFiBcOGDeOpp56qcf5OnTpx7bXXMnXqVMaPH89TTz3Fn3/+yZAhQ4DK1oFly5axZMkSfvnlF9q1a8c333xT52vx8vLi119/Zfbs2bz88st07dqVZcuW8fPPP1NYWMgXX3xxzte7Y8eOGt00S5cuPee+7dq1Y/ny5fznP//hscceo6CgoNa4Bg8ezOHDhykpKSE9PZ2ysjI2b97seI2jRo1yJCJQmXTOnDmT8ePH8+abb17Q6z3X/+HDDz/M4sWLueOOO6olIlWmTJnCihUrHI9/++23at0727Zt4+eff+bbb7/l559/5pZbbuHuu+8G4IcffmDKlCn88MMPrF27lvT0dP766y+gsnXP19eX77//nvfee49XXnkFk8nEDz/84Lh/3377LSdOnKC0tLRaTIWFhWRkZNCnT59qz0uS5EjK6yMrK4tFixaxdOlSli1bxqBBg9izZw+zZs2iW7duPPLII4wePZpPP/0UpVLJsmXLWLlyJUFBQbzxxhuO88TExPDbb78xevToauffs2cPN910Ez///DPTpk3j7bffBuDFF18kOjqa3377jXfffZddu3bVK15BuFSiZURocDfeeCPXXHMN27dvZ/v27Xz22Wd89tln/PTTT+c9ruqDpHPnzpjNZgwGA5s2bWLatGm4u7sDMGfOHD7++OMa3zDPdPz4cVJTU3niiScczxmNRg4cOECvXr1qPe7PP/9k7969XH311UDlN/OKiopz7vvYY48xf/58tm3bxvbt23n99df5+uuv+fbbb9myZQtjx47F29sbwNEac9999533tcTFxTnO/9dff7F3717HPTMajbXGfSHdNNdddx0AsbGxREVFsXv37lrvsUKhYODAgcTHx1NYWMiMGTNYsmQJpaWlbNiwgVtuueW816rr/+7M13u2lJQUevfuzWuvvcZjjz3GsmXLCAkJqbbP8OHDee6558jLy+PEiRNERkY67jlU3sMTJ04wc+ZMx3MlJSUUFRXx8MMPEx8fz2effcbx48fJycmp1tI1cuRIALp27YrZbKa8vJwhQ4Zw2223kZWVxcCBA3nwwQfx9PSsFlNVcma32897b+oSHBxMp06dmDp1KkOHDmXo0KEMGDCgxn5//fUXpaWljiTRYrHg7+/v2F7bPW7bti2dO3cGoEuXLixfvhyAjRs3On4OCgpytNgIQmMTyYjQoHbu3Mnu3bu55ZZbGD58OMOHD+eBBx5g4sSJxMfHn/MbbpWqLghJkgCQZRm73e54DJV/5K1Wq+PxmUsrWSwWAGw2G56entW+Nefl5dX44Dib3W53NMlD5Tfk4uLiGvutX7+eoqIirr76aq688kquvPJK/u///o9hw4Zx4MABlEpltZhLSkooKSmp87VUfWhXbXv33XeJiopynOPMYy/WmS0ZdrsdlUp13rhGjRrFpk2bKCkp4ZZbbuHYsWOsW7eOI0eO0L9///Ne60Je79nat2/vaMXatWsX99xzD99991211jWNRsOYMWNYvXo1SUlJTJ06tcb1J0+ezMMPP+x4nJOTg7e3N//3f/+HzWZj3LhxXHHFFWRlZVV7L2m1WqD6e7FHjx6sX7+eLVu28O+//3LNNdfw2Wef0a1bN8dx3t7etG/fnsTERAYOHFgtnvvuu4877rijxms913tYoVDwzTffsHfvXrZs2cLLL7/MkCFDHAOTz3yNTzzxBMOGDQOgrKwMk8lU5z12c3Nz/CxJkiMGlUpVLZ4z3y+C0JjEO01oUH5+fixcuJAdO3Y4nsvNzcVgMBAbG3vB5xsyZAhLly51fGv9+uuv6devHxqNBj8/P/bt2wdAUlIShw8fBqBDhw64ubk5kpGsrCwmTpzo2FepVDo+FM/8efDgwfz0008YDAYA3n333Rp//AE8PDx46623qs1MSEtLQ6lUEh4ezsCBA/njjz8c53n//ff58ssvz/tazjZ48GC+/PJLZFnGbDZzxx138M0331zw/Ttb1bfe/fv3k5qaSs+ePc8b14gRI9iyZQsHDx6kR48eDBo0iHfffZehQ4eiVCrPe60Leb1nU6vVjp+ffPJJbDYbzz//fI39pkyZwvLly9m+fbujm6zK4MGDWb16NTk5OQAsXryYuXPnAvDPP/9w1113MX78eAASExOx2WznjemNN97go48+YtSoUTz55JNER0c7Zomd6e677+all17ixIkTQGVy/NFHH3Ho0CEiIyOr7Vvbe/jQoUNMnDiRqKgo5s+fz7x589i7dy9Q8z377bffYjabsdvtPP3007z11lvnfR3nM2zYMEdrXGFhIevWrWuQJFgQ6iJaRoQG1aFDBz788EPefvttTp48iVarxdPTk5dffpnIyEhyc3Mv6HzTp08nKyuLa665BrvdTkREhKNP/I477uCxxx5j48aNREZGOpqkNRoNH330ES+99BL//e9/sVqt3HffffTt2xeAsWPHMnv2bN5//32GDh3Kq6++ClROfczOzubaa69FkiRCQkIc2850+eWX8/TTT/Poo49SWlqKUqkkMDCQzz77DG9vb4YNG0ZSUpKjSyQ6OpoXXngBd3f3Wl/L2Z588kleeuklJk2ahMViYeDAgbV2i1SNGTlT1TiCs6WlpTFlyhQkSeKtt97Cx8fnvPfY09OTqKgodDodSqWSIUOG8OSTTzJmzJhL+r+7EFqtlnfffZepU6fSo0cP2rdv79jWu3dvKioqGDFiRI3BvYMHD+bWW2/lpptuQpIk9Ho9H3zwAZIk8X//93/cdddduLu7o9fr6devH6mpqeeNY+7cuTz22GNMnDgRjUZDx44d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zJzv4vl6xzH+PpbNl9cNYkhk/QYsNmcDBgzgvffeIzk5maioKDZu3MhDDz3E66+/Xm2/w4cPc/DgQTp37sySJUvo27cvOp2OIUOG8NxzzzF37lz8/PxYunQp3t7eREREMGrUKN58802uueYaoqKiMBgMrFq1isWLF9eIIz4+nuHDh3P99ddjNBr57LPPqs0aUSqVWK3WGscdPnyYjh070rFjR1544QXuvvtufvzxR4KCgqrtd/YHb12mTZvG119/zZAhQ1CpVCxatIgrrriizuPWrl1LbGwsERERlJWVUVJSQqdOndBqtbz11lscOnSIjh07cuLECWw2G927d+edd94hNTUVf39//vvf/5KXl8fVV18NVCYDsbGx1ZLBLl268N5773Hw4EHi4uIwGAz8+++/jBw5sloCdaGv2d3dndGjR/Pee+/x4osvcvDgQdavX8/3339fY98ZM2YwYcLpReI+//xzMjIyeO655xzPPfvssyQnJ/PFF184WpvOtGvXLrKzs8UsmrOIZEQQmgGrzc4r6/fxwh97sMsyDw/vyoKxPdGolLUe87///a/Wb4hVOgZ58889Y3lh7R5eWb+P4R+t5dER3Xh2TI/znru5i46OZsGCBTzwwAPIsoxKpWLhwoU1po9GRkbywQcfkJaWhr+/P6+++ioAgwYNYt68ecydOxe73Y6fnx/vvvsuCoWC0aNH87///Y+BAwcCMHDgQA4fPkxISEiNOGbOnMmDDz7IpEmTsFqtDBo0iLVr12K321EoFIwdO5bZs2fz/vvvO2bOwOlkBGDUqFEcPnyYu+66i2+++eaSpvreeeedFBYWcuWVV6LVahk3bhx33HGHY/utt97KzJkzGTlyZLXjdu7cyYIFCygrKyMoKIjbbrvNMdPkjjvuYP78+ZSUlBAaGsprr71G9+7duf322x1J2MCBA1m0aBE6nQ6oTEbO7trp3bs3d911Fw8//DBFRUV4enoyfPjwBumievbZZ3niiScYOHAgPj4+PPfcc8TExACVLS1xcXHcfvvt6HQ6R4xQmchoNBpHd11GRgZLlixBo9EwePBgx37PP/88V111FVDZRTN69Gj0ev0lx92SSLIsN9sh9aWlpRw5coTY2NhL7jessm3HvwS316PTeBLkFdEg5xRq2rlzJ337ihao+jiWX8rc7+LZfDyXdt7uLLp+EFdEt6n7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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[7]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for KMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Within Sum-of-Squared</span>
<span class="n">kmeans_vis_wss</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">kmeans</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;distortion&quot;</span><span class="p">)</span>
<span class="n">kmeans_vis_wss</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">kmeans_vis_wss</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAiYAAAFlCAYAAADf6iMZAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAACVuElEQVR4nOzdd3hUVfrA8e+dmt57BVLooYOANGnSBFRYxEXsim3Rnw0LrqCL2FkLorsqixUFEQVUqiginYQeEkghCenJpE6m3N8fIQMxCQlhJjNJzud5fCRz7z33nZvJzDvnnvMeSZZlGUEQBEEQBAegsHcAgiAIgiAINURiIgiCIAiCwxCJiSAIgiAIDkMkJoIgCIIgOAyRmAiCIAiC4DBEYiIIgiAIgsMQiYlgNefOnaNr165MnTqVqVOnMmXKFGbNmsXGjRst+yxbtox169Zdtp13332XLVu2XPH5Lz2uKee5Ejt27OBvf/sbN9xwA5MmTeIf//gH58+ft1r7TbV27Vr69etnucY1/z355JMAPP300/z3v/8FoHPnzhQUFNg0nhMnTjBmzBhuvPFGzp0716w29uzZw+TJk2s99sknnzB8+HBOnjzJnj176Ny5M0899VSdY+fMmUOfPn2adV5r2r59O3PmzGHq1KlMmjSJ+fPnk5WVBVT/zu67775mt93cv4d77rmHpKSkZp9XEOxFZe8AhLbFycmJ77//3vJzRkYGt99+O0qlkvHjx/OPf/yj0Tb27NlDdHT0FZ/70uOacp6mys7O5qmnnmLt2rWEhoYCsHz5cubPn89XX31ltfM0Vf/+/VmxYkWLn7c+W7duZdCgQbz88stWa/Ott97il19+4csvvyQ0NJQ9e/bg7+/P9u3bqaiowNnZGah+bZ09e9Zq522uH374geXLl7N8+XIiIyORZZkPP/yQ2267jQ0bNlx1+839e/joo4+u+tyCYA8iMRFsKjQ0lEceeYT//ve/jB8/nqeffpqYmBjuuusu/v3vf7N582bUajXe3t4sWbKEzZs3c/ToUV599VWUSiXXXHMNL774IidPnkSSJIYNG8Zjjz2GSqWiR48ejB49mpMnTzJlypRax23dutVynv379/Pqq69SUVGBWq1m/vz5DB8+nLVr17J582YUCgWpqak4OTmxdOlSoqKiaj2HwsJCDAYD5eXllsfmzp1Lly5dLD+vWLGC7777DpVKRWRkJK+88gru7u689957bNiwAaVSSceOHXn++efx9/dnzpw5eHp6cubMGW655RamTZvGyy+/TGJiIgaDgcGDB/Pkk0+iUl3dn+jbb7/NkSNHMJvNzJ8/n1GjRgHUG1d8fDwff/wxX3zxBQDjx49n0qRJPPLII5w/f56bb76ZnTt3olBUd7SuX7+eL7/8EpPJRGVlJW+88UaTn++cOXPqxGo2m1m0aBEnT57kiy++wNvb27LNy8uL8PBwtmzZwpQpUwBYt24dU6ZMqZUcfvPNN3z55ZeYzWa8vLx4/vnniYqK4uzZsyxatIiysjJyc3Pp0qULb7/9Nlqtlp49e3Lvvfeya9cucnJyuPvuu5k9eza5ubk89dRTFBYWAjBixAjmz59fJ+633nqLxYsXExkZCYAkSdx7770EBwdTVVVVa985c+Zw6623cv3119f5uSl/DyNGjOD1119n3759mEwmunXrxnPPPYebmxvXXXcdcXFxnDp1iscee4wlS5awbNkyysvLeeuttwgPD+f06dMYjUZefPFF+vXrR0FBAQsWLCAtLQ0vLy/8/f2JiYnh4YcfbtbrTRCsQdzKEWyuS5cuJCYm1nosKyuLlStXsmbNGtauXcvQoUNJSEjg1ltvpUePHjz55JOMHTuWl156CS8vL3744QfWrFnDqVOn+PjjjwEwGAyMGjWKn3/+mYceeqjWcTUKCwt55JFHePbZZ/nhhx9YunQpTzzxBOnp6QDs27eP559/nh9//JFevXrx4Ycf1hv/zJkzmT59OhMnTuS5555j+/btDBs2DKjuNVi7di1ff/01P/74I2FhYXz22WesWbOG3377jW+//ZYffviBmJgYnn76aUu7Hh4ebNy4kTlz5vCvf/2L7t27s3btWtatW0dhYSGffPJJvddz//79dW7lrFmzpt59w8LC+O6773jttdd4+umnKSgoaDCua6+9llOnTqHT6Th37hxlZWX88ccfluc4ZswYS1ICcMMNNzBr1iwmTpzIG2+8cUXP96+MRiNPPPEEX375JfPmzauVlNSYNm1ard64TZs21boFtHfvXtatW8fnn3/OunXruPvuu3nooYcAWL16NdOmTWP16tX88ssvnDt3jh07dgBQVVWFt7c3X331Ff/+979ZsmQJer2e1atXW67f559/TmpqKiUlJbViKiwsJCMjg759+9Z6XJIkbrjhBtzc3Or9vfxVU/8ePvzwQ5RKJWvXrmX9+vUEBATw+uuvW9qJiYlh06ZNtf4GABISErjzzjtZt24dN954I2+99RYAL730EtHR0WzatIlly5Zx8ODBJsUrCLYkekwEm5MkCScnp1qPBQYG0qVLF6ZPn87w4cMZPnw4gwcPrnPszp07+fLLL5EkCY1Gw6xZs1i5ciX33nsvUH1b43ISEhKIiIigV69eQPUbd9++fdm7dy+SJNG9e3eCgoIA6NatG5s3b663naeffpr77ruPvXv3sm/fPl599VVWrVrF559/zu7du7n++uvx9PQEYMGCBUD17aQbb7wRFxcXAG677TY++OADy7foS2PfsWMHR44c4dtvvwWgsrKywed0JbdybrnlFgBiY2OJiori0KFD7Ny5s964FAoFQ4YMYdeuXRQWFvK3v/2Nr7/+mpKSErZt28bdd9992XM11G59z/evzp49S58+fVi6dClPP/00a9euJTg4uNY+o0aN4p///Cd5eXmkpqbSqVMnyzWH6muYmprKrFmzLI/pdDqKiop44okn2LVrFx999BEpKSnk5OTU6gEbPXo0AN27d6eqqory8nKGDRvGvffeS1ZWFkOGDOH//u//cHd3rxVTTaJmNpsve20a09S/hx07dlBSUmJJGA0GA76+vpbtDV3jkJAQunbtClS/zr/77jsAfv31V8u/AwICLD05gmBPIjERbO7IkSPExsbWekyhUPDZZ59x5MgRdu/ezb/+9S+GDRtmGcRZw2w2I0lSrZ+NRqPl55oPwYaYTKZaxwPIsozRaEStVtdKmCRJor6lo7Zu3UpRURE33XQT48ePZ/z48Tz66KOMGDGC48ePo1Qqa51Dp9Oh0+muKHaz2cyyZcsst5F0Ol2duJvj0h4Os9mMSqW6bFxjxoxh586d6HQ67r77bs6cOcOWLVtITExk4MCBlz3X1fyuOnTowJIlSwA4ePAgDz/8MF988QUajcayj0ajYdy4cWzYsIGkpCSmT59e5/xTp07liSeesPyck5ODp6cnjz76KCaTiQkTJjBy5EiysrJq/a61Wi2AJX5ZlomLi2Pr1q3s3r2bP//8kxkzZvDRRx/Ro0cPy3Genp506NCB+Ph4hgwZUiuef/zjH8ybN6/Oc730vAaDAbiyv4dnnnmGESNGAFBWVoZer2/0Gjf0OlepVLXiufT1Igj2Il6Fgk2dPXuW999/nzvvvLPW4ydPnmTy5MlERUVx3333cfvtt3PkyBEAlEql5QPt2muv5bPPPkOWZaqqqli9enWdD4Aalx5Xo3fv3pw5c4aEhAQATp8+zb59+xr9kL2Uq6srb775Zq0ZDunp6SiVSiIiIhgyZAibN2+mtLQUgHfeeYdPP/2UYcOGsWbNGss381WrVjFgwIBaH7Y1rr32Wj799FPL85w3bx6fffZZk2NsSM234WPHjpGWlkavXr0uG9d1113H7t27OXHiBHFxcQwdOpRly5YxfPhwlErlZc91Jc/3r9RqteXfzz77LCaTiRdffLHOftOmTeO7775j3759lltpNa699lo2bNhATk4OAF9++SVz584F4Pfff+fBBx9k4sSJAMTHx2MymS4b0+uvv87777/PmDFjePbZZ4mOjub06dN19nvooYd4+eWXSU1NBaqT4ffff5+TJ0/SqVOnWvv6+Phw9OhRAJKSkjh16hRwZX8Pn3/+OVVVVZjNZp5//nnefPPNyz6PyxkxYoSll66wsJAtW7ZYJSEWhKshekwEq6qsrGTq1KlA9bcvrVbLY489xsiRI2vt16VLFyZMmMBNN92Ei4sLTk5OPPfccwBcd911vPnmmxgMBp577jleeuklpkyZgsFgYNiwYdx///31nvvS42r4+PiwbNkyFi9eTGVlJZIksWTJEjp27MihQ4ea9JyuueYann/+eZ566ilKSkpQKpX4+/vz0Ucf4enpyYgRI0hKSrLcNomOjmbx4sW4uLiQlZXFjBkzMJvNREZG1hoPcKlnn32Wl19+2fI8hwwZ0uCtk5oxJpeqGXfwV+np6UybNg1JknjzzTfx8vLi5ptvbjAud3d3oqKicHZ2RqlUMmzYMJ599lnGjRvX6HW6XLtXQqvVsmzZMqZPn05cXBwdOnSwbOvTpw8VFRVcd911dQYGX3vttdxzzz3ceeedSJKEm5sb7777LpIk8eijj/Lggw/i4uKCm5sbAwYMIC0t7bJxzJ07l6effprJkyej0Wjo3LkzkyZNqrPflClTkGWZxx57DKPRiF6vp3v37qxcubJOUjZv3jyefvppfv31Vzp16mS59dLUv4cHHniApUuXMn36dEwmE127dq01judKLViwgOeee44pU6bg5eVFSEhInduugtDSJLm+vmtBEASh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d3L27FmmTp1qSUJ//PFHevbsSWVl9Togzz77LF98Ufv2ptls5qWXXuK2225j4sSJTJgwwbKWy4IFCwCYO3cuWVl1FzmrSUzS09OZPXs2HTt25J133qmVlNx3333079+/3v/uu+++Om0CvPHGGwwaNIhZs2ZZqmw3xZNPPmlZWPWPP/7goYceAuDjjz9m+fLlLF68mH379vHee+8RGhrK22+/zW+//cbXX3/Nrl27qKqq4r333qv1/A4dOsTo0aPZs2cPt912Gx988AFfffUVy5cvZ/fu3QQGBvL222/XiuNyz/mRRx5p8vOB6l6ao0ePUlhYyNixYxk+fDiLFi2y/E4BbrvtNjZs2EBFRQXZ2dn89ttvDBs2rNG28/LySElJITq6+n23tLSUf//73zz99NP17t/c87Rn7bLHpEZN70hmZiYjenVhzue/88yGQ3wxx3FfNEaTAU8Xf0Z0vgVnTesotFOTONXMynF38mk1s3KEajWF5v7q4YcftgwQvv/+++vtYerfvz///e9/AVi5ciVvvvlmnX2aWsAuJSWFt956i//97394e3tz+vRp7rjjDl566aVa+2VlZfH666/Tt29fvv76a5588km++eYbdu/ezX/+8x++/vprfHx8WLt2LQ8++CATJ05k586dDB48mN9++w1PT0/279/P0KFDLV33f403JyeHTz/9FHd3dz788EM++ugj+vXrx5IlS1i7di0rV65s8FaOJEnMnTuXZ555hjFjxtTZZ8WKFU26HjUef/xxoqKi0Gg0bNiwgfvvv5/vv/+eiIiIRo9NT0/HZDJhMpnQarX069ePgoIC3n33Xb744gu6dKkeV9a5c2fy8vL47LPP2Lhxo2Xl+PHjx/Ptt99a2jt58iR33XUXo0ePBqqLgy1fvpx169YRGRkJwM0338yLL77Y5Od86ZpqTZGXl4fBYOCnn37i888/R6VS8cADD7B8+XIeffRRAAYOHMg333xDv379MJlMTJ8+vd7fxaUMBgOPP/4406dPt4wRevvtt7npppsIDg6u95jmnKe9a7c9JjVeGN+Le+MCmNW7AwPCffn6cAp/puY2fqCdBHp2INyna6tJSmoEe0UzNOZmOmlHMDTmZpGUCM2ya9cucnJyuP3225k6dSqPP/44kiTV6T7v3Lkzffv2BWD69OkcPXqUkpISfvvtNyZOnGhJGG68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NRQVFVFVVcXjjz/ORx99hGEYVpcWVuLj46murubOO++kpaWFoqIiq0sKO8uWLRvW4ds0zeDPsdPpjOj29JEgokdMAGpra1m5ciX33nsv99xzj9XlhKX33nuPAwcOsGLFCr777jvWrl1LQ0OD1WWFHZfLxaJFi3A4HOTk5BATE0Nzc7PVZYWd119/nUWLFrF37152797Ns88+G5xykPExtMt3Z2cnSUlJFlYj4y2ig0ljYyOPPPIIa9asoaCgwOpywtZbb73Fm2++yfbt25k1axYbN25k8uTJVpcVdubNm8fnn3+OaZrU1dXR3d2Ny+Wyuqywk5SURGJiIgDJycn09fXR399vcVXhLTc3l+LiYgA+++wz5s+fb3FFMp4ieiqnqKiItrY2Nm/ezObNm4GBRVdaoCkT0dKlSzl48CAFBQWYpsn69eu1bmocPPzwwzz33HMUFhbi9/t56qmniI+Pt7qssLZ27VrWrVvHyy+/TE5ODsuWLbO6JBlHuleOiIiIhIyInsoRERGR0KJgIiIiIiFDwURERERChoKJiIiIhAwFExEREQkZCiYi8pOKi4uDN1QTERlPCiYiIiISMhRMRGRM3njjDVasWEF3d7fVpYhIGIrozq8iMja7du3i448/ZsuWLcTFxVldjoiEIY2YiMgl+eGHH1i3bh0rV64M3plbRORKUzARkUvidDrZtGkTL730El1dXVaXIyJhSsFERC5JZmYmt956KwsWLODVV1+1uhwRCVMKJiIyJs888wwffPABR48etboUEQlDuruwiIiIhAyNmIiIiEjIUDARERGRkKFgIiIiIiFDwURERERChoKJiIiIhAwFExEREQkZCiYiIiISMhRMREREJGT8P1OdeTDpZypRAAAAAElFTkSuQmCC
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[8]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Distortion Score Elbow for KMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;distortion score&#39;&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Hierarchical-clustering">Hierarchical clustering<a class="anchor-link" href="#Hierarchical-clustering">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Silhouette</span>
<span class="n">hclust_vis_sil</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">hclust</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;silhouette&quot;</span><span class="p">)</span>
<span class="n">hclust_vis_sil</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">hclust_vis_sil</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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Y+Xm5l4Sw48//ijNmTNHMhqNkiRJ0rfffivdeeedlz3HpUuXSt26dZPGjx8vPffcc9Ivv/xi3W7z5s3S2LFjpYKCAkmSJGnJkiXSihUraj2XZ555xrr/uXPnSp9//rkkSZJkMpmkJ554Qvrggw8uieOHH36Q+vTpI02ZMqXav++///6y1/j999+XJEmS4uPjpQEDBki5ubk1xlVeXi716dNHKiwslFJSUqQhQ4ZIM2bMkCRJkr788kvphRdeuCSeZcuWSS+99JIkSVK9zvdiRqNRGjp0qLR161ZJr9dL/fv3l/766y9JkiQpLy9PGjBggHT8+HFJkiRp7dq1UlRUlJSSkiJ988030s033yxVVFRIer1euuOOO6RbbrnFerzffvtNSkhIkAYPHiwlJydLkiRJu3btkoYMGSIVFxdLy5Ytk0aOHCkVFRVJ5eXlUv/+/aWlS5dKkiRJf/zxhzR27FhJkq78Ovn3eT366KPSnj17JEmSpJKSEmngwIHS4cOHJUmSpJEjR0qHDh2qFl9ycrI0cOBASa/XS5IkSY888oj03XffSQUFBdLYsWOllJQUSZIk6dy5c9Lw4cOltLQ06eOPP5Yefvjhy17LKlX7T0lJkXr16mV9/uLHy5cvl55//nlJkiSptLRUmjNnjlRUVFRtnSu9t/bs2SN17txZSk1NlSTp0vf6jBkzJL1eLxkMBmnq1KnS999/f8W/58Xy8vKkqKgo6+fI5fzwww/S3XffXe18/33+6enpUp8+fazX9+OPP5b++OOPS7Z59913pZdfflmyWCySJEnSG2+8YX29jxw5Ulq+fLl131V/xz179khdunSRjh07Zt33zTffLElS5evg1VdflSRJkjIzM6UhQ4ZIy5Ytq/kPJrRoomXETtx+++3ceOON7Nu3j3379vHhhx/y4Ycf8v33319xu6pfnV26dMFgMFBSUsL27duZNm0arq6uANx6662sWrXqkl9CF0tMTCQ5OZlnn33W+lxFRQXHjh2jV69eNW73559/cvjwYW644QYALBZLjf0V5s6dyz333MM///zDvn37ePXVV/niiy/46quv2L17N9deey2enp4A1taYRx555Irn0q9fP+v+//rrLw4fPmy9ZhUVFTXGXZ/bNFW3O6KiooiIiODgwYM1XmOlUsngwYPZuXMn+fn5zJgxg9WrV1NcXMzWrVu5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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[9]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for AgglomerativeClustering Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Within Sum-of-Squared</span>
<span class="n">hclust_vis_wss</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">hclust</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;distortion&quot;</span><span class="p">)</span>

<span class="n">hclust_vis_wss</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">hclust_vis_wss</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[10]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Distortion Score Elbow for AgglomerativeClustering Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;distortion score&#39;&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Menerapkan-Metode-Clustering">Menerapkan Metode Clustering<a class="anchor-link" href="#Menerapkan-Metode-Clustering">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="K-means">K-means<a class="anchor-link" href="#K-means">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Berdasarkan kedua kriteria tersebut, banyaknya cluster terbaik yang dipilih berbeda. Jika demikian, banyaknya cluster bisa ditentukan berdasarkan kemudahan interpretasi cluster 
yang terbentuk. Pada tulisan ini kita akan menggunakan 5 cluster saja.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">kmeans</span> <span class="o">=</span> <span class="n">KMeans</span><span class="p">(</span><span class="n">n_clusters</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">kmeans</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[11]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>KMeans(n_clusters=5)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Hierarchical-clustering">Hierarchical clustering<a class="anchor-link" href="#Hierarchical-clustering">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Berdasarkan kedua kriteria tersebut, banyaknya cluster terbaik yang dipilih adalah 6 cluster.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hclust</span> <span class="o">=</span> <span class="n">AgglomerativeClustering</span><span class="p">(</span><span class="n">n_clusters</span><span class="o">=</span><span class="mi">6</span><span class="p">)</span>
<span class="n">hclust</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[12]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>AgglomerativeClustering(n_clusters=6)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall_hclust</span> <span class="o">=</span> <span class="n">mall</span><span class="o">.</span><span class="n">assign</span><span class="p">(</span><span class="n">labels</span> <span class="o">=</span> <span class="n">hclust</span><span class="o">.</span><span class="n">labels_</span><span class="p">)</span>
<span class="n">mall_hclust</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[13]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Annual Income</th>
      <th>Spending Score</th>
      <th>labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>15</td>
      <td>39</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>15</td>
      <td>81</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>20</td>
      <td>16</td>
      <td>6</td>
      <td>4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23</td>
      <td>16</td>
      <td>77</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>31</td>
      <td>17</td>
      <td>40</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Interpretasi-Hasil-Cluster">Interpretasi Hasil Cluster<a class="anchor-link" href="#Interpretasi-Hasil-Cluster">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="K-means">K-means<a class="anchor-link" href="#K-means">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>interpretasi setiap cluster  yang terbentuk dapat dilakukan dengan menggunakan bantuan nilai rata-rata dari masing-masing peubah (centroid) dihitung berdasarkan cluster. Karena kita melakukan standarisasi peubah, maka nilai rata-rata yang diperoleh juga dalam skala standarisasi.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cluster_centers</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">kmeans</span><span class="o">.</span><span class="n">cluster_centers_</span><span class="p">,</span><span class="n">columns</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">mall</span><span class="p">))</span>
<span class="n">cluster_centers</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[14]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Annual Income</th>
      <th>Spending Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.204841</td>
      <td>-0.235773</td>
      <td>-0.052368</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.980679</td>
      <td>-0.743060</td>
      <td>0.467440</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.428806</td>
      <td>0.974847</td>
      <td>1.216085</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.073331</td>
      <td>0.974945</td>
      <td>-1.197297</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.531074</td>
      <td>-1.290508</td>
      <td>-1.236467</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Selanjutkan kita ubah nilai yang masih dalam bentuk standarisasi ke bentuk awalnyanya dengan method <code>inverse_transform</code></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cluster_centers</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">scale</span><span class="o">.</span><span class="n">inverse_transform</span><span class="p">(</span><span class="n">kmeans</span><span class="o">.</span><span class="n">cluster_centers_</span><span class="p">),</span><span class="n">columns</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">mall</span><span class="p">))</span>
<span class="n">cluster_centers</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[15]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Annual Income</th>
      <th>Spending Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>55.638298</td>
      <td>54.382979</td>
      <td>48.851064</td>
    </tr>
    <tr>
      <th>1</th>
      <td>25.185185</td>
      <td>41.092593</td>
      <td>62.240741</td>
    </tr>
    <tr>
      <th>2</th>
      <td>32.875000</td>
      <td>86.100000</td>
      <td>81.525000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>39.871795</td>
      <td>86.102564</td>
      <td>19.358974</td>
    </tr>
    <tr>
      <th>4</th>
      <td>46.250000</td>
      <td>26.750000</td>
      <td>18.350000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Dari kelima cluster berikut adalah interpretasinya:</p>
<ul>
<li>Cluster 1 : cluster  ini merupakan customer-customer yang muda (sekitar 25 tahun) dan berpenghasilan cukup besar (sekitar 41 ribu dolar) dan lumayan suka  menghabiskan uangnya untuk berbelanja (spending skor cukup besar).</li>
<li>Cluster 2 : cluster  ini merupakan customer-customer cukup berumur (sekitar 40 tahun) dan berpenghasilan sangat besar (sekitar 86 ribu dolar) dan sangat  jarang menghabiskan uangnya untuk berbelanja (spending sangat rendah).</li>
<li>Cluster 3: cluster  ini merupakan customer-customer sudah tua (sekitar 55 tahun) dan berpenghasilan besar (sekitar 54 ribu dolar) dan jarang menghabiskan uangnya untuk berbelanja (spending rendah).</li>
<li>Cluster 4: cluster  ini merupakan customer-customer cukup tua (sekitar 46 tahun) dan berpenghasilan kecil (sekitar 26 ribu dolar) dan jarang menghabiskan uangnya untuk berbelanja (spending rendah).</li>
<li>Cluster 5 : cluster  ini merupakan customer-customer yang cukup muda (sekitar 32 tahun) dan berpenghasilan sangat besar (sekitar 86 ribu dolar) dan sangat suka  menghabiskan uangnya untuk berbelanja (spending skor besar).</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Hierarchical-clustering">Hierarchical clustering<a class="anchor-link" href="#Hierarchical-clustering">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>interpretasi setiap cluster yang terbentuk dapat dilakukan dengan menggunakan bantuan nilai rata-rata dari masing-masing peubah (centroid) dihitung berdasarkan cluster.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall_hclust</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;labels&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[16]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Annual Income</th>
      <th>Spending Score</th>
    </tr>
    <tr>
      <th>labels</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>27.377778</td>
      <td>57.511111</td>
      <td>45.844444</td>
    </tr>
    <tr>
      <th>1</th>
      <td>56.400000</td>
      <td>55.288889</td>
      <td>48.355556</td>
    </tr>
    <tr>
      <th>2</th>
      <td>32.692308</td>
      <td>86.538462</td>
      <td>82.128205</td>
    </tr>
    <tr>
      <th>3</th>
      <td>43.892857</td>
      <td>91.285714</td>
      <td>16.678571</td>
    </tr>
    <tr>
      <th>4</th>
      <td>44.318182</td>
      <td>25.772727</td>
      <td>20.272727</td>
    </tr>
    <tr>
      <th>5</th>
      <td>24.809524</td>
      <td>25.619048</td>
      <td>80.238095</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Dengan centroid diatas kita bisa melakukan interpretasi seperti pada K-means. Silahkan dicoba!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Supervised-Methods">Supervised Methods<a class="anchor-link" href="#Supervised-Methods">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Data">Data<a class="anchor-link" href="#Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Data yang digunakan pada tutorial kali ini adalah data yang bernama Pima Indian Diabetes yang sudah sedikit diedit. Berikut adalah informasi singkat mengenai data</p>
<p>This dataset is originally from the National Institute of Diabetes and Digestive and Kidney Diseases. The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset. Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years old of Pima Indian heritage.</p>
<p>Content
The datasets consists of several medical predictor variables and one target variable, Outcome. Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on.</p>
<p>Acknowledgements
Smith, J.W., Everhart, J.E., Dickson, W.C., Knowler, W.C., &amp; Johannes, R.S. (1988). Using the ADAP learning algorithm to forecast the onset of diabetes mellitus. In Proceedings of the Symposium on Computer Applications and Medical Care (pp. 261--265). IEEE Computer Society Press.</p>
<p>data ini bisa diperoleh di link berikut ini <a href="https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN">Pima Indian Dataset</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Import-Data">Import Data<a class="anchor-link" href="#Import-Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">diabetes</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;diabetes.csv&quot;</span><span class="p">)</span>
<span class="n">diabetes</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[17]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>148</td>
      <td>72</td>
      <td>35</td>
      <td>0</td>
      <td>33.6</td>
      <td>0.627</td>
      <td>50</td>
      <td>Case</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>85</td>
      <td>66</td>
      <td>29</td>
      <td>0</td>
      <td>26.6</td>
      <td>0.351</td>
      <td>31</td>
      <td>Control</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>183</td>
      <td>64</td>
      <td>0</td>
      <td>0</td>
      <td>23.3</td>
      <td>0.672</td>
      <td>32</td>
      <td>Case</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>89</td>
      <td>66</td>
      <td>23</td>
      <td>94</td>
      <td>28.1</td>
      <td>0.167</td>
      <td>21</td>
      <td>Control</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>137</td>
      <td>40</td>
      <td>35</td>
      <td>168</td>
      <td>43.1</td>
      <td>2.288</td>
      <td>33</td>
      <td>Case</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Menentukan-metode-supervised-learning">Menentukan metode supervised learning<a class="anchor-link" href="#Menentukan-metode-supervised-learning">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">!</span>pip install xgboost
<span class="o">!</span>pip install lightgbm
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.svm</span> <span class="kn">import</span> <span class="n">SVC</span><span class="p">,</span> <span class="n">LinearSVC</span>
<span class="kn">from</span> <span class="nn">sklearn.tree</span> <span class="kn">import</span> <span class="n">DecisionTreeClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.naive_bayes</span> <span class="kn">import</span> <span class="n">GaussianNB</span>
<span class="kn">from</span> <span class="nn">sklearn.linear_model</span> <span class="kn">import</span> <span class="n">LogisticRegression</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="kn">import</span> <span class="n">RandomForestClassifier</span><span class="p">,</span><span class="n">GradientBoostingClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="kn">import</span> <span class="n">ExtraTreesClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.neighbors</span> <span class="kn">import</span> <span class="n">KNeighborsClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.neural_network</span> <span class="kn">import</span> <span class="n">MLPClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.discriminant_analysis</span> <span class="kn">import</span>  <span class="n">LinearDiscriminantAnalysis</span><span class="p">,</span> <span class="n">QuadraticDiscriminantAnalysis</span>
<span class="kn">from</span> <span class="nn">xgboost</span> <span class="kn">import</span> <span class="n">XGBClassifier</span>
<span class="kn">from</span> <span class="nn">lightgbm</span> <span class="kn">import</span> <span class="n">LGBMClassifier</span>


<span class="k">def</span> <span class="nf">base_models</span><span class="p">():</span>
    <span class="n">svc</span> <span class="o">=</span> <span class="n">SVC</span><span class="p">()</span>
    <span class="n">lsvc</span> <span class="o">=</span> <span class="n">LinearSVC</span><span class="p">()</span>
    <span class="n">tree</span> <span class="o">=</span> <span class="n">DecisionTreeClassifier</span><span class="p">()</span>
    <span class="n">nb</span> <span class="o">=</span> <span class="n">GaussianNB</span><span class="p">()</span>
    <span class="n">logr</span> <span class="o">=</span> <span class="n">LogisticRegression</span><span class="p">()</span>
    <span class="n">rf</span> <span class="o">=</span> <span class="n">RandomForestClassifier</span><span class="p">()</span>
    <span class="n">gb</span> <span class="o">=</span> <span class="n">GradientBoostingClassifier</span><span class="p">()</span>
    <span class="n">knn</span> <span class="o">=</span> <span class="n">KNeighborsClassifier</span><span class="p">()</span>
    <span class="n">nn</span> <span class="o">=</span> <span class="n">MLPClassifier</span><span class="p">()</span>
    <span class="n">lda</span> <span class="o">=</span> <span class="n">LinearDiscriminantAnalysis</span><span class="p">()</span>
    <span class="n">qda</span> <span class="o">=</span> <span class="n">QuadraticDiscriminantAnalysis</span><span class="p">()</span>
    <span class="n">xgb</span> <span class="o">=</span> <span class="n">XGBClassifier</span><span class="p">()</span>
    <span class="n">lgb</span> <span class="o">=</span> <span class="n">LGBMClassifier</span><span class="p">()</span>
    <span class="n">et</span>  <span class="o">=</span> <span class="n">ExtraTreesClassifier</span><span class="p">()</span>
    <span class="n">models</span><span class="o">=</span><span class="p">{</span><span class="s2">&quot;svc&quot;</span><span class="p">:</span><span class="n">svc</span><span class="p">,</span><span class="s2">&quot;lsvc&quot;</span><span class="p">:</span><span class="n">lsvc</span><span class="p">,</span><span class="s2">&quot;tree&quot;</span><span class="p">:</span><span class="n">tree</span><span class="p">,</span><span class="s2">&quot;nb&quot;</span><span class="p">:</span><span class="n">nb</span><span class="p">,</span><span class="s2">&quot;logr&quot;</span><span class="p">:</span><span class="n">logr</span><span class="p">,</span><span class="s2">&quot;rf&quot;</span><span class="p">:</span><span class="n">rf</span><span class="p">,</span><span class="s2">&quot;gb&quot;</span><span class="p">:</span><span class="n">gb</span><span class="p">,</span><span class="s2">&quot;knn&quot;</span><span class="p">:</span><span class="n">knn</span><span class="p">,</span>
       <span class="s2">&quot;nn&quot;</span><span class="p">:</span><span class="n">nn</span><span class="p">,</span><span class="s2">&quot;lda&quot;</span><span class="p">:</span><span class="n">lda</span><span class="p">,</span><span class="s2">&quot;qda&quot;</span><span class="p">:</span><span class="n">qda</span><span class="p">,</span><span class="s2">&quot;xgb&quot;</span><span class="p">:</span><span class="n">xgb</span><span class="p">,</span><span class="s2">&quot;et&quot;</span><span class="p">:</span><span class="n">et</span><span class="p">,</span><span class="s2">&quot;lgb&quot;</span><span class="p">:</span><span class="n">lgb</span><span class="p">}</span>
    <span class="k">return</span> <span class="n">models</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Menentukan-Metode-pembagian-data">Menentukan Metode pembagian data<a class="anchor-link" href="#Menentukan-Metode-pembagian-data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[19]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#cross validation</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">cross_validate</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Melakukan-Proses-Evaluasi-model">Melakukan Proses Evaluasi model<a class="anchor-link" href="#Melakukan-Proses-Evaluasi-model">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn</span> <span class="kn">import</span> <span class="n">preprocessing</span>
<span class="n">le</span> <span class="o">=</span> <span class="n">preprocessing</span><span class="o">.</span><span class="n">LabelEncoder</span><span class="p">()</span>

<span class="n">predictors</span> <span class="o">=</span> <span class="n">diabetes</span><span class="o">.</span><span class="n">drop</span><span class="p">(</span><span class="s2">&quot;Outcome&quot;</span><span class="p">,</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
<span class="n">response</span> <span class="o">=</span> <span class="n">le</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">diabetes</span><span class="p">[</span><span class="s2">&quot;Outcome&quot;</span><span class="p">])</span>

<span class="n">models_name</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;svc&quot;</span><span class="p">,</span><span class="s2">&quot;lsvc&quot;</span><span class="p">,</span><span class="s2">&quot;tree&quot;</span><span class="p">,</span><span class="s2">&quot;nb&quot;</span><span class="p">,</span><span class="s2">&quot;logr&quot;</span><span class="p">,</span><span class="s2">&quot;rf&quot;</span><span class="p">,</span><span class="s2">&quot;gb&quot;</span><span class="p">,</span><span class="s2">&quot;knn&quot;</span><span class="p">,</span>
       <span class="s2">&quot;nn&quot;</span><span class="p">,</span><span class="s2">&quot;lda&quot;</span><span class="p">,</span><span class="s2">&quot;qda&quot;</span><span class="p">,</span><span class="s2">&quot;xgb&quot;</span><span class="p">,</span><span class="s2">&quot;et&quot;</span><span class="p">,</span><span class="s2">&quot;lgb&quot;</span><span class="p">]</span>
<span class="k">for</span> <span class="n">model</span> <span class="ow">in</span> <span class="n">models_name</span><span class="p">:</span>
    <span class="n">hasil_cv</span> <span class="o">=</span> <span class="n">cross_validate</span><span class="p">(</span><span class="n">X</span><span class="o">=</span><span class="n">predictors</span><span class="p">,</span><span class="n">y</span><span class="o">=</span><span class="n">response</span><span class="p">,</span>
                          <span class="n">estimator</span><span class="o">=</span><span class="n">base_models</span><span class="p">()[</span><span class="n">model</span><span class="p">],</span> <span class="n">cv</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span>
                          <span class="n">scoring</span><span class="o">=</span><span class="p">(</span><span class="s1">&#39;accuracy&#39;</span><span class="p">,</span> <span class="s1">&#39;recall&#39;</span><span class="p">,</span><span class="s2">&quot;roc_auc&quot;</span><span class="p">,</span><span class="s2">&quot;f1&quot;</span><span class="p">))</span>
    <span class="k">if</span><span class="p">(</span><span class="n">model</span> <span class="o">!=</span><span class="s2">&quot;svc&quot;</span><span class="p">):</span>
        <span class="n">score_cv</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="o">.</span><span class="n">from_dict</span><span class="p">(</span><span class="n">hasil_cv</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span><span class="o">.</span><span class="n">to_frame</span><span class="p">()</span><span class="o">.</span><span class="n">T</span>
        <span class="n">score_cv_fin</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">score_cv_fin</span><span class="p">,</span><span class="n">score_cv</span><span class="p">])</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">score_cv_fin</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="o">.</span><span class="n">from_dict</span><span class="p">(</span><span class="n">hasil_cv</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span><span class="o">.</span><span class="n">to_frame</span><span class="p">()</span><span class="o">.</span><span class="n">T</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[21]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">score_cv_fin</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="s2">&quot;models_name&quot;</span><span class="p">,</span><span class="n">models_name</span><span class="p">,</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[22]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">score_cv_fin</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[22]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>models_name</th>
      <th>fit_time</th>
      <th>score_time</th>
      <th>test_accuracy</th>
      <th>test_recall</th>
      <th>test_roc_auc</th>
      <th>test_f1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>svc</td>
      <td>0.025481</td>
      <td>0.013829</td>
      <td>0.758000</td>
      <td>0.916327</td>
      <td>0.816763</td>
      <td>0.831185</td>
    </tr>
    <tr>
      <th>0</th>
      <td>lsvc</td>
      <td>0.034561</td>
      <td>0.008421</td>
      <td>0.575912</td>
      <td>0.661224</td>
      <td>0.677339</td>
      <td>0.579651</td>
    </tr>
    <tr>
      <th>0</th>
      <td>tree</td>
      <td>0.008000</td>
      <td>0.005575</td>
      <td>0.688860</td>
      <td>0.763265</td>
      <td>0.656633</td>
      <td>0.761335</td>
    </tr>
    <tr>
      <th>0</th>
      <td>nb</td>
      <td>0.002400</td>
      <td>0.006401</td>
      <td>0.756702</td>
      <td>0.844898</td>
      <td>0.815771</td>
      <td>0.818780</td>
    </tr>
    <tr>
      <th>0</th>
      <td>logr</td>
      <td>0.027176</td>
      <td>0.008828</td>
      <td>0.768632</td>
      <td>0.883673</td>
      <td>0.818321</td>
      <td>0.832492</td>
    </tr>
    <tr>
      <th>0</th>
      <td>rf</td>
      <td>0.221663</td>
      <td>0.028504</td>
      <td>0.775263</td>
      <td>0.865306</td>
      <td>0.826406</td>
      <td>0.833045</td>
    </tr>
    <tr>
      <th>0</th>
      <td>gb</td>
      <td>0.154911</td>
      <td>0.007068</td>
      <td>0.761947</td>
      <td>0.859184</td>
      <td>0.829191</td>
      <td>0.823942</td>
    </tr>
    <tr>
      <th>0</th>
      <td>knn</td>
      <td>0.002828</td>
      <td>0.006879</td>
      <td>0.724649</td>
      <td>0.828571</td>
      <td>0.747381</td>
      <td>0.796843</td>
    </tr>
    <tr>
      <th>0</th>
      <td>nn</td>
      <td>0.170590</td>
      <td>0.006401</td>
      <td>0.678298</td>
      <td>0.800000</td>
      <td>0.701776</td>
      <td>0.760657</td>
    </tr>
    <tr>
      <th>0</th>
      <td>lda</td>
      <td>0.003200</td>
      <td>0.002400</td>
      <td>0.770018</td>
      <td>0.881633</td>
      <td>0.827400</td>
      <td>0.832638</td>
    </tr>
    <tr>
      <th>0</th>
      <td>qda</td>
      <td>0.004000</td>
      <td>0.002400</td>
      <td>0.736737</td>
      <td>0.836735</td>
      <td>0.808910</td>
      <td>0.805109</td>
    </tr>
    <tr>
      <th>0</th>
      <td>xgb</td>
      <td>0.079208</td>
      <td>0.010402</td>
      <td>0.732702</td>
      <td>0.812245</td>
      <td>0.785804</td>
      <td>0.797685</td>
    </tr>
    <tr>
      <th>0</th>
      <td>et</td>
      <td>0.104755</td>
      <td>0.020859</td>
      <td>0.779193</td>
      <td>0.889796</td>
      <td>0.824076</td>
      <td>0.839669</td>
    </tr>
    <tr>
      <th>0</th>
      <td>lgb</td>
      <td>0.053659</td>
      <td>0.006805</td>
      <td>0.728789</td>
      <td>0.820408</td>
      <td>0.792101</td>
      <td>0.797108</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
    </div>
  </div>
</body>




 


</html>
