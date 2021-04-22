---
layout: post
title: Text Clustering
categories: [Machine Learning,Natural Language Processing,python]
excerpt: 
---

<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Text-Clustering</title><script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>

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
<h2 id="Import-Data">Import Data<a class="anchor-link" href="#Import-Data">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Data ini bisa diperoleh dengan mengakses link berikut <a href="https://drive.google.com/file/d/1sQgzfuhgSCU8o-Apy7aYcl7WeddKPeKM/view?usp=sharing">Cust Review</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="n">hotel</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_excel</span><span class="p">(</span><span class="s2">&quot;Raw Data - Combined - Cust Review.xlsx&quot;</span><span class="p">,</span><span class="n">sheet_name</span><span class="o">=</span><span class="s2">&quot;Raw Data&quot;</span><span class="p">)</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[1]:</div>



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
      <th>ID</th>
      <th>hotel_id</th>
      <th>kota_id</th>
      <th>rtg_htl</th>
      <th>tanggal_id</th>
      <th>trip_id</th>
      <th>review</th>
      <th>rtg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ID_1</td>
      <td>Hotel Pacific Balikpapan</td>
      <td>Balikpapan</td>
      <td>8.8</td>
      <td>2019-05-07</td>
      <td>Family Trip</td>
      <td>Ac nya tidak dingin samasekali, ruangan sempit...</td>
      <td>6.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>ID_2</td>
      <td>Hotel Pacific Balikpapan</td>
      <td>Balikpapan</td>
      <td>8.8</td>
      <td>2019-05-06</td>
      <td>Solo/Non-Family Trip</td>
      <td>Recom bgt nie hotel buat nginap harga terjangk...</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ID_3</td>
      <td>Hotel Pacific Balikpapan</td>
      <td>Balikpapan</td>
      <td>8.8</td>
      <td>2019-05-04</td>
      <td>Solo/Non-Family Trip</td>
      <td>Sangat memuaskan harganya murah</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ID_4</td>
      <td>Hotel Pacific Balikpapan</td>
      <td>Balikpapan</td>
      <td>8.8</td>
      <td>2019-04-29</td>
      <td>Business Trip</td>
      <td>Bersih, lengkap, nyaman melebihi angka nominal...</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ID_5</td>
      <td>Hotel Pacific Balikpapan</td>
      <td>Balikpapan</td>
      <td>8.8</td>
      <td>2019-04-25</td>
      <td>Family Trip</td>
      <td>Tisu, sabun sudah hampir habis tapi tidak diis...</td>
      <td>6.4</td>
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
<p>Melihat banyaknya baris dan kolom di data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[2]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(51305, 8)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Menghitung 10 Besar hotel yang memiliki jumlah review dan rating terbanyak</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span><span class="o">.</span><span class="n">hotel_id</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>Cabin Hotel                                                   909
Centro City Service Apartment                                 763
STAR Hotel Semarang                                           651
eL Hotel Royale Bandung                                       588
Sahid Mutiara Karawaci formerly ParagonBiz Hotel Tangerang    567
MaxOneHotels at Vivo Palembang                                495
favehotel Kelapa Gading                                       487
Medan Ville Hotel                                             478
favehotel Solo Baru                                           476
Best City Hotel                                               444
Name: hotel_id, dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pada tutorial ini kita akan menggunakan data hotel <strong>favehotel Kelapa Gading</strong> saja yang ada sebanyak 487 hotel</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span> <span class="o">=</span> <span class="n">hotel</span><span class="o">.</span><span class="n">query</span><span class="p">(</span><span class="s2">&quot;hotel_id == &#39;favehotel Kelapa Gading&#39;&quot;</span><span class="p">)</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[4]:</div>



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
      <th>ID</th>
      <th>hotel_id</th>
      <th>kota_id</th>
      <th>rtg_htl</th>
      <th>tanggal_id</th>
      <th>trip_id</th>
      <th>review</th>
      <th>rtg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>13535</th>
      <td>ID_14360</td>
      <td>favehotel Kelapa Gading</td>
      <td>Jakarta</td>
      <td>8.0</td>
      <td>2019-05-06</td>
      <td>Business Trip</td>
      <td>Hanya saja area untuk parkir motor yg tidak ad...</td>
      <td>7.6</td>
    </tr>
    <tr>
      <th>13536</th>
      <td>ID_14361</td>
      <td>favehotel Kelapa Gading</td>
      <td>Jakarta</td>
      <td>8.0</td>
      <td>2019-04-09</td>
      <td>Business Trip</td>
      <td>Breakfast nya enak, karyawan hotel ramah</td>
      <td>9.6</td>
    </tr>
    <tr>
      <th>13537</th>
      <td>ID_14362</td>
      <td>favehotel Kelapa Gading</td>
      <td>Jakarta</td>
      <td>8.0</td>
      <td>2019-03-15</td>
      <td>Family Trip</td>
      <td>Fo ramah, lah ini mba2 resto nya, jutek mana a...</td>
      <td>6.4</td>
    </tr>
    <tr>
      <th>13538</th>
      <td>ID_14363</td>
      <td>favehotel Kelapa Gading</td>
      <td>Jakarta</td>
      <td>8.0</td>
      <td>2019-02-17</td>
      <td>Solo/Non-Family Trip</td>
      <td>Sangat nyaman, lokasi strategis, kamar bersih,...</td>
      <td>8.8</td>
    </tr>
    <tr>
      <th>13539</th>
      <td>ID_14364</td>
      <td>favehotel Kelapa Gading</td>
      <td>Jakarta</td>
      <td>8.0</td>
      <td>2019-01-25</td>
      <td>Family Trip</td>
      <td>Hotelny cukup nyaman. Ac dingin. Makanan enak....</td>
      <td>9.2</td>
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
<p>Selanjutnya kita akan ambil kolom <strong>review</strong> saja untuk dianalisis</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span> <span class="o">=</span> <span class="n">hotel</span><span class="p">[</span><span class="s2">&quot;review&quot;</span><span class="p">]</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[5]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13535    Hanya saja area untuk parkir motor yg tidak ad...
13536             Breakfast nya enak, karyawan hotel ramah
13537    Fo ramah, lah ini mba2 resto nya, jutek mana a...
13538    Sangat nyaman, lokasi strategis, kamar bersih,...
13539    Hotelny cukup nyaman. Ac dingin. Makanan enak....
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kita pastikan terlebih dahulu apakah text yang kita miliki ada na atau tidak</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Jumlah amatan NaN adalah&quot;</span><span class="p">,</span><span class="n">hotel</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">())</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Contoh amatan yang NAN&quot;</span><span class="p">)</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">hotel</span><span class="o">.</span><span class="n">isnull</span><span class="p">()]</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Jumlah amatan NaN adalah 2
Contoh amatan yang NAN
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[6]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13712    NaN
13742    NaN
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Karena kita memiliki 2 amatan yang berupa <code>NaN</code>. Berikutnya kita akan hapus <code>NaN</code> tersebut</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span> <span class="o">=</span> <span class="n">hotel</span><span class="o">.</span><span class="n">dropna</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Jumlah amatan NaN adalah&quot;</span><span class="p">,</span><span class="n">hotel</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">())</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Jumlah amatan NaN adalah 0
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Text-Preprocessing">Text Preprocessing<a class="anchor-link" href="#Text-Preprocessing">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Noise-Removal">Noise Removal<a class="anchor-link" href="#Noise-Removal">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">string</span>
<span class="k">def</span> <span class="nf">noise_removal</span><span class="p">(</span><span class="n">words</span><span class="p">):</span>
    <span class="n">words</span> <span class="o">=</span> <span class="n">words</span><span class="o">.</span><span class="n">translate</span><span class="p">(</span><span class="nb">str</span><span class="o">.</span><span class="n">maketrans</span><span class="p">(</span><span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="n">string</span><span class="o">.</span><span class="n">punctuation</span> <span class="o">+</span> <span class="n">string</span><span class="o">.</span><span class="n">digits</span><span class="p">))</span>
    <span class="n">words</span> <span class="o">=</span> <span class="n">words</span><span class="o">.</span><span class="n">strip</span><span class="p">()</span>
    <span class="k">return</span> <span class="n">words</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">lower</span><span class="p">()</span>
<span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">noise_removal</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Tokenization">Tokenization<a class="anchor-link" href="#Tokenization">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">nltk.tokenize</span> <span class="kn">import</span> <span class="n">word_tokenize</span> 
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">tokenize_fun</span><span class="p">(</span><span class="n">words</span><span class="p">):</span>
    <span class="k">return</span> <span class="n">word_tokenize</span><span class="p">(</span><span class="n">words</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">tokenize_fun</span><span class="p">)</span>
<span class="n">hotel_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[12]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13535    [hanya, saja, area, untuk, parkir, motor, yg, ...
13536       [breakfast, nya, enak, karyawan, hotel, ramah]
13537    [fo, ramah, lah, ini, mba, resto, nya, jutek, ...
13538    [sangat, nyaman, lokasi, strategis, kamar, ber...
13539    [hotelny, cukup, nyaman, ac, dingin, makanan, ...
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Normalization">Normalization<a class="anchor-link" href="#Normalization">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">indo_slang_words</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;https://raw.githubusercontent.com/nasalsabila/kamus-alay/master/colloquial-indonesian-lexicon.csv&quot;</span><span class="p">)</span>
<span class="n">indo_slang_words</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
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
      <th>slang</th>
      <th>formal</th>
      <th>In-dictionary</th>
      <th>context</th>
      <th>category1</th>
      <th>category2</th>
      <th>category3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>woww</td>
      <td>wow</td>
      <td>1</td>
      <td>wow</td>
      <td>elongasi</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>aminn</td>
      <td>amin</td>
      <td>1</td>
      <td>Selamat ulang tahun kakak tulus semoga panjang...</td>
      <td>elongasi</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>met</td>
      <td>selamat</td>
      <td>1</td>
      <td>Met hari netaas kak!? Wish you all the best @t...</td>
      <td>abreviasi</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>netaas</td>
      <td>menetas</td>
      <td>1</td>
      <td>Met hari netaas kak!? Wish you all the best @t...</td>
      <td>afiksasi</td>
      <td>elongasi</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>keberpa</td>
      <td>keberapa</td>
      <td>0</td>
      <td>Birthday yg keberpa kak?</td>
      <td>abreviasi</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">new_entry</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">{</span><span class="s2">&quot;slang&quot;</span><span class="p">:[</span><span class="s2">&quot;bokis&quot;</span><span class="p">],</span><span class="s2">&quot;formal&quot;</span><span class="p">:[</span><span class="s2">&quot;bohong&quot;</span><span class="p">],</span><span class="s2">&quot;In-dictionary&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span><span class="s2">&quot;context&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span>
                          <span class="s2">&quot;category1&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span><span class="s2">&quot;category2&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span><span class="s2">&quot;category3&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">]})</span>
<span class="n">new_indo_slang_words</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">indo_slang_words</span><span class="p">,</span><span class="n">new_entry</span><span class="p">])</span>
<span class="n">new_indo_slang_words</span><span class="o">.</span><span class="n">tail</span><span class="p">()</span>
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
      <th>slang</th>
      <th>formal</th>
      <th>In-dictionary</th>
      <th>context</th>
      <th>category1</th>
      <th>category2</th>
      <th>category3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>15002</th>
      <td>gtau</td>
      <td>enggak tau</td>
      <td>0</td>
      <td>Stidaknya mrka may berkarya Dan berusaha yg tr...</td>
      <td>akronim</td>
      <td>abreviasi</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15003</th>
      <td>gatau</td>
      <td>enggak tau</td>
      <td>0</td>
      <td>Ih gatau malu</td>
      <td>akronim</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15004</th>
      <td>fans2</td>
      <td>fan-fan</td>
      <td>0</td>
      <td>Jkt48 adalah tempat di mana sesama fans saling...</td>
      <td>reduplikasi</td>
      <td>naturalisasi</td>
      <td>0</td>
    </tr>
    <tr>
      <th>15005</th>
      <td>gaharus</td>
      <td>enggak harus</td>
      <td>0</td>
      <td>belajar tuh bisa dimana aja gaharus belajar di...</td>
      <td>akronim</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>0</th>
      <td>bokis</td>
      <td>bohong</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">replace_slang_word</span><span class="p">(</span><span class="n">words</span><span class="p">):</span>
    <span class="k">for</span> <span class="n">index</span> <span class="ow">in</span>  <span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="nb">len</span><span class="p">(</span><span class="n">words</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">):</span>
        <span class="n">index_slang</span> <span class="o">=</span> <span class="n">indo_slang_words</span><span class="o">.</span><span class="n">slang</span><span class="o">==</span><span class="n">words</span><span class="p">[</span><span class="n">index</span><span class="p">]</span>
        <span class="n">formal</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">set</span><span class="p">(</span><span class="n">indo_slang_words</span><span class="p">[</span><span class="n">index_slang</span><span class="p">]</span><span class="o">.</span><span class="n">formal</span><span class="p">))</span>
        <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">formal</span><span class="p">)</span><span class="o">==</span><span class="mi">1</span><span class="p">:</span>
            <span class="n">words</span><span class="p">[</span><span class="n">index</span><span class="p">]</span><span class="o">=</span><span class="n">formal</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>
    <span class="k">return</span> <span class="n">words</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">replace_slang_word</span><span class="p">)</span>
<span class="n">hotel_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[16]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13535    [hanya, saja, area, untuk, parkir, motor, yang...
13536       [breakfast, nya, enak, karyawan, hotel, ramah]
13537    [fo, ramah, lah, ini, mbak, resto, nya, jutek,...
13538    [sangat, nyaman, lokasi, strategis, kamar, ber...
13539    [hotelny, cukup, nyaman, ac, dingin, makanan, ...
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Menghapus-Stopwrods">Menghapus Stopwrods<a class="anchor-link" href="#Menghapus-Stopwrods">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">nltk.corpus</span> <span class="kn">import</span> <span class="n">stopwords</span>
<span class="n">indo_stopwords</span> <span class="o">=</span> <span class="n">stopwords</span><span class="o">.</span><span class="n">words</span><span class="p">(</span><span class="s1">&#39;indonesian&#39;</span><span class="p">)</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># menambhakan stopwords bahasa indonesia</span>
<span class="n">indo_stopwords</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s2">&quot;nya&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[19]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#fungsi menghapus stopword</span>
<span class="k">def</span> <span class="nf">stopwords_removal</span><span class="p">(</span><span class="n">words</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">[</span><span class="n">word</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">words</span> <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">indo_stopwords</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean2</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">stopwords_removal</span><span class="p">)</span>
<span class="n">hotel_clean2</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[20]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13535         [area, parkir, motor, parkir, mesin, jenset]
13536            [breakfast, enak, karyawan, hotel, ramah]
13537    [fo, ramah, mbak, resto, jutek, adaaaa, piring...
13538    [nyaman, lokasi, strategis, kamar, bersih, ac,...
13539    [hotelny, nyaman, ac, dingin, makanan, enak, k...
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Stemming">Stemming<a class="anchor-link" href="#Stemming">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[21]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">Sastrawi.Stemmer.StemmerFactory</span> <span class="kn">import</span> <span class="n">StemmerFactory</span>
<span class="c1"># create stemmer</span>
<span class="n">factory</span> <span class="o">=</span> <span class="n">StemmerFactory</span><span class="p">()</span>
<span class="n">stemmer</span> <span class="o">=</span> <span class="n">factory</span><span class="o">.</span><span class="n">create_stemmer</span><span class="p">()</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">stemmer_func</span><span class="p">(</span><span class="n">word</span><span class="p">):</span>
    <span class="k">return</span> <span class="n">stemmer</span><span class="o">.</span><span class="n">stem</span><span class="p">(</span><span class="n">word</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[23]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">word_dict</span> <span class="o">=</span> <span class="p">{}</span>

<span class="k">for</span> <span class="n">document</span> <span class="ow">in</span> <span class="n">hotel_clean</span><span class="p">:</span>
    <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">document</span><span class="p">:</span>
        <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">word_dict</span><span class="p">:</span>
            <span class="n">word_dict</span><span class="p">[</span><span class="n">word</span><span class="p">]</span> <span class="o">=</span> <span class="s1">&#39; &#39;</span>

<span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">word_dict</span><span class="p">:</span>
    <span class="n">word_dict</span><span class="p">[</span><span class="n">word</span><span class="p">]</span> <span class="o">=</span> <span class="n">stemmer_func</span><span class="p">(</span><span class="n">word</span><span class="p">)</span>
    
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">get_stemmer_word</span><span class="p">(</span><span class="n">document</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">[</span><span class="n">word_dict</span><span class="p">[</span><span class="n">word</span><span class="p">]</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">document</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[25]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean3</span> <span class="o">=</span> <span class="n">hotel_clean2</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">get_stemmer_word</span><span class="p">)</span>
<span class="n">hotel_clean3</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[25]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13535         [area, parkir, motor, parkir, mesin, jenset]
13536            [breakfast, enak, karyawan, hotel, ramah]
13537    [fo, ramah, mbak, resto, jutek, adaaaa, piring...
13538    [nyaman, lokasi, strategis, kamar, bersih, ac,...
13539    [hotelny, nyaman, ac, dingin, makan, enak, kam...
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Convert-to-Text">Convert to Text<a class="anchor-link" href="#Convert-to-Text">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">list_to_text</span><span class="p">(</span><span class="n">token</span><span class="p">):</span>
    <span class="n">text</span> <span class="o">=</span> <span class="s2">&quot; &quot;</span>
    <span class="k">return</span> <span class="n">text</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">token</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean_fin</span> <span class="o">=</span> <span class="n">hotel_clean3</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">list_to_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean_fin</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[28]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13535                area parkir motor parkir mesin jenset
13536                  breakfast enak karyawan hotel ramah
13537    fo ramah mbak resto jutek adaaaa piring lempar...
13538       nyaman lokasi strategis kamar bersih ac dingin
13539    hotelny nyaman ac dingin makan enak kamar semp...
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Menampilkan-WordCloud">Menampilkan WordCloud<a class="anchor-link" href="#Menampilkan-WordCloud">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">wordcloud</span> <span class="kn">import</span> <span class="n">WordCloud</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>menyatukan setiap baris pada <code>hotel_clean_fin</code> dan mengubahnya menjadi bentuk <code>string</code></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[30]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_text</span> <span class="o">=</span> <span class="n">hotel_clean_fin</span><span class="o">.</span><span class="n">to_string</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">wordcloud</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span><span class="n">background_color</span><span class="o">=</span><span class="s2">&quot;white&quot;</span><span class="p">)</span>
<span class="n">wordcloud</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">hotel_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[31]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;wordcloud.wordcloud.WordCloud at 0x18b03af9df0&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Menampilkan wordcloud</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Display the generated image:</span>
<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">wordcloud</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s2">&quot;off&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
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

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Berdasarkan wordcloud diatas <strong>hotel</strong> bisa kita anggap sebagai <strong>stopwords</strong> karena data kita adalah review hotel sehingga kata hotel pastilah ada di dalam review itu, jadi kurang bermakna dalam kasus ini.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>menyimpan dalam bentuk png</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">wordcloud</span><span class="o">.</span><span class="n">to_file</span><span class="p">(</span><span class="s2">&quot;review.png&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[33]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;wordcloud.wordcloud.WordCloud at 0x18b03af9df0&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>sebelum lajut kita akan hapus dulu kata hotel dengan menggunakan fungsi berikut</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">remove_certain_word</span><span class="p">(</span><span class="n">words</span><span class="p">,</span><span class="n">text</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">[</span><span class="n">word</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">words</span> <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">text</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean3</span> <span class="o">=</span> <span class="n">hotel_clean3</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">remove_certain_word</span><span class="p">(</span><span class="n">x</span><span class="p">,</span><span class="s2">&quot;hotel&quot;</span><span class="p">))</span>
<span class="n">hotel_clean_fin</span> <span class="o">=</span> <span class="n">hotel_clean3</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">list_to_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[36]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean_fin</span><span class="p">[</span><span class="n">hotel_clean_fin</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="s2">&quot;hotel&quot;</span><span class="p">)]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[36]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>13539    hotelny nyaman ac dingin makan enak kamar semp...
13586    inap kasi smooking room jendela pesan komplain...
13660    inap favehotel pilih baik tarif murah bersih k...
13674      favehotel good kamar ac good kamar mandi bersih
13684    dear pegi trimakasih aplikasi traveler baik ba...
13689    favorit kawasan kelapa gading akses tinggal li...
13716    favehotel standard milik akses mudah kamar ber...
13719    kali inap fave hotelsl kelapa gading perlu bis...
13729    nginep favehotel pgc cililitan banget layan ma...
13777    kali inap vafehotel kamar bagus layan bagus ny...
13785    harga murah untung inap suguh welcome drink la...
13834    inap favehotel indonesia favehotel buruk segi ...
13876    favehotel kelapa gading strategis banget bange...
13879    layan staf bagus ramah kamar bagus bersih kama...
13887    favehotel klp gading lokasi bagus lapiaza hote...
13896    favehotel kelapa gading lokasi mudah cari stra...
13905    keren deh favehotel layan bagus staff ramah se...
13930    favehotel kelapa gading kamar lantai nyaman ti...
13945    over all ok kendala favhotel klp gading area p...
13960    favehotel nyaman banget tempat kamar mandi ber...
13985    favehotel kelapa gading bsanget strategis laha...
13991    kriteria murah milik favehotel kelapa gading m...
13995    malam d fave hotelmaaf puas fasilitas d bersih...
14017    alam malam favehotel kelapa gading kendala kur...
14019    favehotel kelapa gading tawar kamar nyaman kon...
Name: review, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Term-Weighting">Term Weighting<a class="anchor-link" href="#Term-Weighting">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[37]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.feature_extraction.text</span> <span class="kn">import</span> <span class="n">TfidfVectorizer</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="TF-IDF">TF-IDF<a class="anchor-link" href="#TF-IDF">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[38]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tf_idf_vectorizer</span> <span class="o">=</span> <span class="n">TfidfVectorizer</span><span class="p">()</span>
<span class="n">tf_idf_result</span> <span class="o">=</span> <span class="n">tf_idf_vectorizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">hotel_clean_fin</span><span class="p">)</span>
<span class="n">tf_idf_result_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="o">.</span><span class="n">toarray</span><span class="p">(),</span><span class="n">columns</span><span class="o">=</span><span class="n">tf_idf_vectorizer</span><span class="o">.</span><span class="n">get_feature_names</span><span class="p">())</span>
<span class="n">tf_idf_result_df</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[38]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>kamar          35.566894
nyaman         30.482740
bersih         28.945236
layan          26.289328
lokasi         25.525125
                 ...    
usir            0.158620
buruburu        0.158620
resepsionis     0.158620
scurity         0.158620
trmksh          0.158620
Length: 1191, dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Unsupervised-Learning">Unsupervised Learning<a class="anchor-link" href="#Unsupervised-Learning">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="K-Means">K-Means<a class="anchor-link" href="#K-Means">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Untuk menjalankan K-Means kita akan menggunakan <code>MiniBatchKMeans</code> dimana KMeans versi ini lebih <strong>scaleable</strong> dibandingkan dengan KMeans yang biasa</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[39]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="kn">import</span> <span class="n">MiniBatchKMeans</span>
<span class="n">kmeans</span> <span class="o">=</span> <span class="n">MiniBatchKMeans</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Memilih-Jumlah-Cluster-Optimum">Memilih Jumlah Cluster Optimum<a class="anchor-link" href="#Memilih-Jumlah-Cluster-Optimum">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[40]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">yellowbrick.cluster</span> <span class="kn">import</span> <span class="n">KElbowVisualizer</span>

<span class="c1"># Silhouette</span>
<span class="n">kmeans_vis_sil</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">kmeans</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;silhouette&quot;</span><span class="p">)</span>

<span class="n">kmeans_vis_sil</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
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
<img src="data:image/png;base64,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b948Xn75Zfr27cuGDRv44YcfKCsr45NPPmn09cbHx1/STfPdd981um9oaCjff/89r776KosXL6a0tLTJuEaPHs3p06eprKwkOzsbjUbDvn37zK/x2muvNSciUPdhOnfuXKZMmcLrr7/eotfbmJkzZ7Jx40bz459//pmpU6c2ui9AZmYma9as4ccff2TPnj0cPHiwyXs1ffp0Ro8ezcGDB5k9ezYAmzdvZtCgQaxdu5YdO3bg5OTExo0bmTRpUoPfk6+++ooTJ06wceNGfvrpJzQaDVu2bAHquhzeeustfvnlFzw8PBp0ZRw+fJh58+bRrVs3pk+ffklsvXv3RqVSkZSUBMC2bduYMGFCgwT03//+N7NmzTJ/MO/bt48tW7aQk5PDvn37WLNmDZs2beKf//xngxbI+Ph4c1zOzs588803GI1GXn75ZT766CO+++47br31VhISEi6J6/jx4wwZMuSS5/v27cugQYOa/Hlc7OOPP2bChAnm5CA+Ph6ZTMZLL71EeHg4H3/8MRUVFTz11FP85z//4fvvv+d///sfL7zwArm5uQCkpqayZs0a1qxZc8n5G/v5p6am8tprr/Hpp5/yww8/mL8UCV2DaBnp4u6++25uueUWDh06xKFDh1i1ahWrVq1i/fr1lz2u/oOmd+/e6HQ61Go1e/bs4eabb8bFxQWAv/3tb7z//vvodLomz5Oenk5mZiZPP/20+bna2lpOnjx52TfP3377jWPHjjFr1iwATCYTNTU1je67ePFi7r33Xg4ePMihQ4f4z3/+w5o1a/jyyy/Zv38/119/PZ6engDm1phHHnnksq9l6NCh5vPv2rWLY8eOme9ZbW1tk3G3pJvmtttuAyA2Npbo6GiOHDnS5D2Wy+VcffXV7N27l7KyMubMmcPatWupqqpi586dLFq06LLXau5nd+Hrbcz48eN54YUXKC4uJiMjg+7du5vvaVP7y+Vy3NzciIiIoKKigtDQ0Ab7XHivTCYTK1euZNGiRWzZsoW77rqL+Ph4PvnkE9LT0zlz5gwDBw685Dr79u1jxowZODk5AXWtTVDXsjdq1Ch8fHyAuqT1wjE6P/74I++99x4vvfQSb775Jo8//vgl554xYwY//vgjAwcO5IcffuCpp55i9erVAFRXV3Po0CEqKip46623zM+dOnWKKVOm8J///IdNmzaRkZFBUlIS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CQDffvstU6ZMIS4ujkWLFlFSUtKq11uvurqabdu2cf/99+Pq6srQoUOZMGECGzdubHLfRx55pMl9r7vuOq699lq8vLwaHHul97ded/9BSJIJSarrn1EqHEGqe15oO00lJF09EQGRjAhCm9q5cye33HILM2fOZO7cuRw5cuSSfaqrq3n44YeZMWMG8+bN49y5c+Zta9euZerUqUyfPp0FCxZw7tw5ZsyYwf79+4G6D+D+/ftTW1v3DXbJkiV89dVXDc5vMpl46aWXuOWWW5gyZQo33HADCQkJADz11FMA3HvvveTl5V0SW30ykpWVxe23305UVBTvvPMOrq6u5n3uvfdehg4d2ui/e++997L3p7i4mPT0dGJiLBsU+cQTTzB27Fj27dvHvn37ePDBBwFYvXo1K1euZNmyZRw6dIj33nuPkJAQ/vvf//L777+zdu1a9u7di06n47333mvw+o4cOcLEiRM5cOAAf/vb33j//ff55ptvWLlyJfv37ycwMJD//ve/DeJo6WtOT09HLpcTERFhfq5Xr16kpqY2uW9UVFSz+zanpfe3XpBXDFF+g1DIHXBWuRPoEcHA8Ali8KoV3DWsYReoSETqiNk0Qoc3cGDjf8gPPfQQixYtAuq62uo/0C80dOhQPv74YwA+++wz3njjjUv2SUqybFBZeno6b775Jp9//jne3t6cOXOGu+++m5deeqnBfnl5ebz22msMGTKEtWvX8sQTT7Bu3Tr279/PRx99xNq1a/Hx8WHDhg088MADTJkyhT179jBy5Eh+//13PD09iY+PZ9SoUezevZtHH330kngLCwtZu3YtcrmcDz/8kFWrVhEXF8crr7zChg0b+OCDDwgKCrrkNaSkpCCTybjrrrt4+umnufbaay/Z54MPPrDoflxMr9fzr3/9i5tuusniMSlZWVkYjUaMRiOOjo7ExcVRWlrKu+++y1dffUWvXr0A6NmzJ8XFxXzxxRds2bKFgIAAACZPnsz69evN5zt16hQLFy5k4sSJQN3yAitXruSHH34wJw6zZ8/mxRdfvKLXXF1dfcmS9u7u7o22MLVk38tpzf29UKR/f1wc3fFyCcTD2Q9JkpAkSdQmaWO70woAmNwziBER/iIROc9qyYjJZOKFF17g9OnTqFQqXnrppQbfEnbu3Ml7772HUqlk1qxZ3Hrrrej1ep5++mlycnLQ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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[40]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for MiniBatchKMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Menerapkan-Metode-Cluster">Menerapkan Metode Cluster<a class="anchor-link" href="#Menerapkan-Metode-Cluster">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[41]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">kmeans</span> <span class="o">=</span> <span class="n">MiniBatchKMeans</span><span class="p">(</span><span class="n">n_clusters</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="n">kmeans</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[41]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>MiniBatchKMeans(n_clusters=4)</pre>
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
<p>Interpretasi Hasil Cluster menggunakan 10 kata-kata paling penting dari masing-masing kluster. Kata-kata penting ini diukur dengan nilai TF-IDF dimana semakin besar nilainya maka semakin penting kata tersebut</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[42]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># extract cluster&#39;s label</span>
<span class="n">cluster_label</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">kmeans</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="p">),</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s2">&quot;cluster&quot;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[43]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tf_idf_df_lab</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">tf_idf_result_df</span><span class="p">,</span><span class="n">cluster_label</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[44]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>

<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">4</span><span class="p">):</span>
    <span class="n">cluster_df</span> <span class="o">=</span> <span class="n">tf_idf_df_lab</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s2">&quot;cluster&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span><span class="n">by</span><span class="o">=</span><span class="n">i</span><span class="p">)</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">10</span><span class="p">)[</span><span class="n">i</span><span class="p">]</span><span class="o">.</span><span class="n">to_frame</span><span class="p">()</span><span class="o">.</span><span class="n">reset_index</span><span class="p">()</span>
    <span class="n">cluster_df</span><span class="o">.</span><span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;words&quot;</span><span class="p">,</span><span class="s2">&quot;TF_IDF&quot;</span><span class="p">]</span>
    <span class="n">sns</span><span class="o">.</span><span class="n">barplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;TF_IDF&quot;</span><span class="p">,</span><span class="n">y</span><span class="o">=</span><span class="s2">&quot;words&quot;</span><span class="p">,</span><span class="n">data</span><span class="o">=</span><span class="n">cluster_df</span><span class="p">)</span><span class="o">.</span><span class="n">set_title</span><span class="p">(</span><span class="s1">&#39;Cluster &#39;</span><span class="o">+</span><span class="nb">str</span><span class="p">(</span><span class="n">i</span><span class="p">))</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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9UiSpDAp9pyCPXv2sHHjxlDUIkmSwqjYkYLt27fTtm1batWqRUxMDIFAgIiICBYuXBiK+iRJUogUGwqeeuqpUNQhSZLCrNhQcNxxx/HMM8+wZMkS8vPzOeecc+jVq1coaguZ/q+9xI78veEuIzS+/jzcFRyWl7tfEe4SJKncKjYUPPDAA3z77bdccsklBAIBMjIyWL9+PXfccUco6pMkSSFSbChYvHgx//M//0Nk5M/nJJ5//vl07ty5xAuTJEmhVezVB/v27SM/P7/I86ioqBItSpIkhV6xIwVdunShT58+dOzYEYBXXnmFTp06lXhhkiQptIoNBR999BFdu3Zl5cqVVK9enQEDBnD++eeHoDRJkhRKv2tGw3fffZfVq1ezb98+YmJiOProo2nWrFko6pMkSSFSbCho3rw5zZs354orrmDevHlMnjyZp556ipUrV4aiPkmSFCLFhoJRo0aRmZlJVFQUZ555JiNHjuSss84KRW2SJCmEir36YOfOnQQCARo0aECjRo1o2LAh8fHxoajtTxk8eDB5eXl8//33vPnmm+EuR5KkMqPYkYIHH3wQgLVr1/LBBx8wYMAAdu/ezbvvvlvixf0ZEyZMAGDJkiV89dVXtG3bNswVSZJUNhQbCr766is++OADPvjgAz7//HOaNWtG69at//QLfv3114wYMYJKlSoRFRXFAw88wMyZM1m2bBmBQIArr7ySCy+8kN69e3PSSSexZs0aYmNjOeOMM3jvvffYuXMnaWlpLFy4kIULF5KVlcX27du58cYbad++PW3btuXll19mypQp5OTkcPrpp3PBBRf86XolSaooig0FgwYNok2bNlx55ZWcfvrphz1x0fvvv0/Tpk0ZPnw4H374IQsWLGDDhg08++yz5Obmcumll9KyZUsAmjVrxp133kn//v2pUqUK06ZNY9iwYSxbtgyA3bt3M23aNLZt20ZKSkrhl39UVBTXXnstX331lYFAkqTfqdhQMHfu3CP6gt27d+fJJ5/k6quvJj4+npNPPplVq1bRu3dvAPLz8/n+++8BaNq0KQDVq1encePGhY9zc3MBOPPMM4mMjKR27dpUr16dbdu2HdFaJUmqSIo90fBIW7hwIUlJSaSnp9OhQwcyMjI4++yzmTFjBunp6Vx44YUcf/zxv2tfq1atAuCHH34gKyuLWrVqFa6LjIykoKCg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8ssvueyyy4osLw/Htn79+kycOLHw+apVqzjrrLMAaNWqFe+//36R9r/12S7tft3Xhx56iFNOOQWAffv2HXA/lt96r5d2v+7rypUrefvtt7niiiu4/fbbycrKKtK+PB3X/SZOnEivXr045phjiiwvbce1QoSCrKws4uLiCp9HRUWRn59fuO6XszpVq1btgDdoWVKtWjXi4uLIyspi4MCB3HzzzUXWd+zYkdTUVNLT08nMzOStt94KT6FHSJUqVejfvz9Tp05l1KhR3HrrreX22O73xBNPcOONNx6wvDwc2/bt21Op0v//qhkIBAonFqtWrRq7du0q0v63Ptul3a/7uv/L4qOPPmLmzJlceeWVRdr/1nu9tPt1X5s1a8Ztt93G008/Tb169XjssceKtC9PxxXgxx9/5IMPPiA5OfmA9qXtuFaIUBAXF0d2dnbh84KCgsKD9ut12dnZB536sSzZuHEjffr0oWvXrnTu3LlweSAQoG/fvhx99NFER0fTunVrPv300zBWevgaNGhAly5diIiIoEGDBtSsWZOtW7cC5fPY7ty5k6+++opzzjmnyPLyeGyBIucPZGdnF54/sd9vfbbLoldffZWRI0cyZcqUwnND9vut93pZ849//IPExMTCx79+r5a34zpv3jw6dep0wMgtlL7jWiFCQYsWLVi0aBEAy5cvp0mTJoXrGjVqxLfffsuOHTvIy8vjww8/5PTTTw9XqYfthx9+oF+/fgwdOpTu3bsXWZeVlUWnTp3Izs4mEAiwdOnSwg9mWTV79mzuu+8+ADZv3kxWVhYJCQlA+Tu2AMuWLePcc889YHl5PLYAp556KkuXLgVg0aJFnHHGGUXW/9Znu6x56aWXmDlzJjNmzKBevXoHrP+t93pZ079/f/79738D8MEHH9C0adMi68vTcYWf+9iqVauDrittx7XsRq8/4B//+AeLFy/m8ssvJxAIMHbsWObOncvu3bu57LLLGD58OP379ycQCHDJJZdQp06dcJf8p02ePJmdO3cyadIkJk2aBEBKSgp79uzhsssuY/DgwfTp04fo6Gj+9re/0bp16zBXfHi6d+/OiBEj6NGjBxEREYwdO5bXXnutXB5bgK+//prjjz++8Pkv38fl7dgCDBs2jLvuuouHHnqIhg0b0r59ewBuu+02br755oN+tsuiffv2MWbMGOrWrctNN90EwJlnnsnAgQML+3qw93pZ/d9zamoq99xzD5UrV6Z27drcc889QPk7rvt9/fXXBwS90npcvfeBJEkCKsjPB5IkqXiGAkmSBBgKJElSkKFAkiQBhgJJkhRkKJAkSUAFmadA0pEzatQoPvroI/bu3cu6deto1KgRAH369OH++++nbt26hW1r167N1KlTD7mv/XPE33TTTQwfPpwlS5ZQo0aNwhnsrrnmmsK75/1y/X7nn38+gwcPLoluShWSoUDSHzJy5EgANmzYQJ8+fXjppZeAn2/t3LZt28LZ2f6MgQMHFs4Pv379enr27EnNmjULZ3H85XpJR54/H0gqlerVq0efPn2YNWtWuEuRKgxHCiQdMW+++SZdu3YtfD5ixIgDbt70RzRp0oQ5c+YUPn/kkUdIT08vfP70008XuZuepMNjKJB0xBzuzwcHU6VKlcLH/nwglSx/PpBUan3xxReFJzJKKnmGAkml0jfffMOsWbPo0aNHuEuRKgx/PpBUauw/ZyAiIoKoqCiGDRtGixYtwl2WVGF462RJkgQ4UiCphN1yyy18+eWXByxv27YtgwYNCkNFkg7FkQJJkgR4oqEkSQoyFEiSJMBQIEmSggwFkiQJMBRIkqSg/wPkmGe7POtgTwAAAABJRU5ErkJggg==
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAggAAAFlCAYAAACOfhB6AAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAAArnElEQVR4nO3dfWDN9f//8cfZpc0uii2fVawR/cR3YWrlI0o+5aMx5iphGl+fSC6TaxmaLiw+zEXI1QclF0e+6pP6pPrqo/hqyFXLNRFGm7SxM2d7//4o59O8MWnb+5y53/7pnPN+nfeeT+9z8eh13hc2wzAMAQAA/IaX1QUAAAD3Q0AAAAAmBAQAAGBCQAAAACYEBAAAYEJAAAAAJgQEANeloKBACxYsUEJCguLj49WyZUtNmjRJ+fn5kqThw4dr3rx5N7z+Hj16KCsrq0RqzcjIUOPGjUtkXcDNioAA4LokJydr27ZtWrRokdasWaOVK1fq0KFDGjVqVImsf+PGjX94HU6nUwsXLlTPnj2Vm5tbAlUBNy8CAoBiHTt2TGvXrtXEiRMVHBwsSQoMDNS4cePUvHlz0/h77rmnyGzApfu5ubnq37+/4uPj1bZtW40ePVqFhYUaMWKEJKl79+46ceKETp06pb59+yohIUGtWrXSm2++6aqjadOm6tGjh5544gllZmYW+bt79uzRd999p+nTp5fWPwVw0/CxugAA7m/37t26++67FRQUVOTx8PBwPfHEE9e9nn/961/Kzc3VmjVrVFBQoLFjx+r777/XK6+8IrvdrkWLFqlSpUpKTEzUM888o2bNmsnhcKhXr16qVq2aoqOjdfLkSb3xxhtq2LChaf3R0dGKjo7WsWPH/nDPwM2OgACgWF5eXiosLPzD64mJidGUKVPUrVs3NWrUSN27d1dkZGSRMefPn9eWLVv0008/aerUqa7HMjIyFB0dLR8fH9WrV+8P1wLg2ggIAIoVHR2tgwcPKicnp8gswqlTpzRmzBhNmzbtqs+9tBOjJFWtWlX/+te/tHnzZm3atElJSUkaP368mjVr5hpTWFgowzC0bNkyBQQESJKysrLk7++v7Oxs+fn5yceHjy6gtLEPAoBiValSRa1atdLIkSOVk5MjScrJyVFycrJuueUWVahQocj4SpUqaefOnZKk999/3/X422+/rREjRqhx48Z68cUX1bhxY+3Zs0eS5O3tLafTqaCgINWrV08LFiyQJJ07d06dO3fW+vXry6JVAL8ihgO4LmPHjtXMmTP11FNPydvbW/n5+WrevLn69etnGjt69GiNHz9eISEhatSokcLDwyVJbdq00f/93/+pZcuWCggIUEREhLp16yZJatGihbp166a0tDSlpqZqwoQJatWqlfLz8xUXF6fWrVuzbwFQhmxc7hkAAFyOnxgAAIAJAQEAAJgQEAAAgAkBAQAAmHAUw68KCwuVm5srX19f2Ww2q8sBAKBUGYahixcvqmLFivLyMs8XEBB+lZubq71791pdBgAAZapWrVqua6z8FgHhV76+vpJ++Yfy8/OzuJqSs2vXLtWtW9fqMkocfXkW+vIc5bEnib6uJD8/X3v37nV9/12OgPCrSz8r+Pn5yd/f3+JqSlZ56+cS+vIs9OU5ymNPEn1dzdV+VudESb9yOBzatWuXbt++Xz75F60uBwCAIsL7dDU9lp6erpiYmBta36Xvvbp1614xZHAUAwAAMCEgAAAAEwICAAAwISAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAE7cJCHa7XampqVdclpaWpnfeeeeG152SkqIffvjhhp8PAMDN5qY41fKoUaOsLgEAAI/iNjMIl8yfP1/t2rVTp06dNGnSpCLLjhw5onbt2ikjI0MnT55U7969lZSUpLZt2+qTTz6RJE2ZMkWdOnVShw4dtHDhQklSt27ddODAgbJuBQAAj+VWMwhHjhzR5s2btWzZMvn4+Khfv3767LPPJEmHDh3SqlWr9MYbb+iuu+7Sl19+qaSkJMXGxmrr1q1KS0tT8+bN9d5772nJkiWqUqWK7Ha7xR0BAOCZ3CogfPvtt3rkkUdcl55s2LCh9u3bJ0nasGGDfHx85O3tLUkKDw/XrFmztHLlStlsNjmdTknS5MmTNXnyZJ05c0YPP/ywNY0AAODh3Oonhtq1a2vHjh1yOp0yDENbtmxRVFSUJKl79+4aOXKkhg4dqoKCAk2dOlXx8fGaNGmSYmNjZRiG8vPztW7dOk2ePFmLFi3S6tWrdfz4cYu7AgDA87jVDEJkZKQaNGigzp07q7CwUDExMWrevLkyMjIkSY0aNdK6des0d+5ctWjRQikpKZo9e7YiIiKUnZ0tPz8/hYaGKj4+XqGhofrzn/+s22+/3eKuAADwPDbDMAyri3AHl66Lffv2/fLJv2h1OQAAFBHep6vpsfT0dMXExNzQ+i5979WtW1f+/v6m5W71EwMAAHAPBAQAAGBCQAAAACYEBAAAYEJAAAAAJgQEAABgQkAAAAAmbnWiJHdQqWubKx4P6qn+yDGy7oy+PAt9eY7y2JNUfvsqTcwgAAAAEwICAAAwISAAAAATAgIAADAhIAAAABOu5virS1e1Ctg2VV6On6wuBwBggf/Xd43VJfwuXM0RAACUKQICAAAwISAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwcbuAYLfblZqaanUZAADc1NwuIAAAAOv5WF3A1bzxxhvatWuXcnNzVaNGDb3yyit66qmnNGHCBNWsWVP/+7//q88//1zPPvuskpOT5XA4dPbsWfXt21fNmzdXq1at9MADD+i7776TzWbTzJkzFRwcbHVbAAB4BLecQbh48aJCQkK0YMECLVu2TNu3b9epU6fUoUMHrV69WpK0atUqtW/fXgcPHlRSUpIWLFigMWPGaOnSpZKk3NxcPfnkk1qyZIluu+02bdiwwcqWAADwKG45g2Cz2ZSVlaXBgwcrMDBQ58+f18WLF9WyZUu1bdtWPXv21MmTJ1WnTh3t27dPs2bN0sqVK2Wz2eR0Ol3ruffeeyVJERERcjgcVrUDAIDHccsZhM2bN+vEiROaPHmyBg8erLy8PBmGoYCAAMXGxiolJUXx8fGSpKlTpyo+Pl6TJk1SbGysfntxSpvNZlULAAB4NLecQfiv//ov7d69Wx07dpSfn5+qVq2qzMxMVa1aVR07dlTnzp2VnJwsSWrRooVSUlI0e/ZsRUREKDs729riAQAoB9wuICQkJCghIeGqywsKCtSiRQuFhIRIkuLi4hQXF2ca9+mnn7puDxkypOQLBQCgHHO7gHAtS5Ys0apVqzRt2jSrSwEAoFzzqIDQtWtXde3a1eoyAAAo99xyJ0UAAGAtAgIAADAhIAAAABMCAgAAMCEgAAAAE486iqEs1Og2V/7+/laXUWLS09MVExNjdRkljr48C315jvLYk1R++ypNzCAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAE45iuMyHK7rLefGs1WWUqEM7rK6gdNCXZ6Evz3EjPbVPWlfyhcBSzCAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwISAAAACTMg0IS5Ysue6xDodDK1as+N1/Y8OGDXr33Xd/9/MAAMB/lGlAmDVr1nWPPX369A0FhCZNmqhTp06/+3kAAOA/Su1MiocOHdKIESPk4+Mjb29vPfjgg/rpp5+UnJys6OhorVq1SoWFherfv78OHDigjz/+WE6nU8HBwUpLS9Obb76p/fv3a/r06erevbtGjRql7OxsSdLo0aN1zz33aMWKFVq6dKlCQ0Pl6+urli1bSpIOHjyofv36acCAAcrJyVFeXp5efPFFxcbGlla7AACUK6UWEL788kvVqVNHw4cP19dff63KlStryZIlSk5Olt1uV0hIiGbNmqXCwkKlp6dr4cKF8vLyUs+ePbVz50717t1be/fu1fPPP69JkybpwQcf1NNPP63Dhw9rxIgRmjFjht566y2999578vPzU2JiYpG/f/ToUZ05c0YLFy7Ujz/+qMOHD5dWqwAAlDulFhDat2+vuXPn6r//+78VHBysQYMGFVkeFRUlSfLy8pKvr68GDx6swMBAnTx5Uk6ns8jYvXv3atOmTfrwww8lSefOndPRo0dVo0YNBQQESJLq169f5Dk1a9ZUly5dNHjwYDmdTnXr1q20WgUAoNwptYCwfv16xcTE6Pnnn9f777+vt956S4ZhuJZ7ef2y+0NGRoY++eQTrVixQhcuXFBCQoIMw5CXl5cKCwslSdWrV1fr1q3VqlUr/fjjj1qxYoWqVaumgwcPKi8vT35+ftqxY4eqV6/uWv93332n3NxczZkzR5mZmXrqqaf06KOPlla7AACUK6UWEOrWrasXX3xRaWlp8vLy0ogRI3Ts2DENGTJEjRo1co2LjIxUQECAEhIS5Ofnp/DwcGVmZqp+/fq6ePGiJk2apN69e2vUqFFavny5cnJy9Pzzz6tSpUrq1auXnn76ad1yyy1yOBzy8fFxzT7cddddmjFjht577z35+vqqf//+pdUqAADlTqkFhGrVqpkON1y8eLFpXEBAgP7xj39ccR1r1qxx3Z45c2aRZU6nU5mZmbLb7ZKkLl26KCIiQvfff79rzLRp0264fgAAbmalFhBKm4+Pjy5cuKC2bdvK19dX0dHRatiwodVlAQBQLnhsQJCkwYMHa/DgwVaXAQBAucOplgEAgAkBAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJh49GGOpeGvHRbJ39/f6jJKTHp6umJiYqwuo8TRl2ehL89RHnvCjWEGAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJhwFMNl/v5Boi44z1pdRolae8DqCkoHfXkW+nJ/yR0/sroEuBFmEAAAgAkBAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJgQEAAAgIlbBAS73a7U1FSrywAAAL9yi4AAAADci9ucSXH79u3q3r27cnJy1K9fP+Xl5Wnp0qWu5VOnTtWtt96qcePGadeuXQoLC9Px48c1a9YsTZ8+XS1btlSTJk20YcMG/fOf/9Srr76q4cOH6+jRo3I4HOrZs6datmxpYYcAAHgOtwkIAQEBmjNnjrKystShQwd17NhRc+bMUUBAgF566SX9+9//VmBgoM6ePauVK1cqKytLjz/++FXXl5OTo82bN2vVqlWSpI0bN5ZVKwAAeDy3CQgxMTGy2WyqXLmygoOD5ePjo2HDhqlixYo6ePCg6tWr5/qvJFWqVEnVq1c3rccwDElSUFCQxowZozFjxignJ0etW7cuy3YAAPBobhMQdu7cKUk6ffq0fv75Zy1atEiff/65JCkpKUmGYahmzZpas2aNJOmnn37S4cOHJUl+fn46ffq0JGnPnj2SpMzMTO3evVszZsyQw+FQ06ZNFR8fLx8ft2kZAAC35Tbflnl5eUpMTNT58+eVkpKiZcuWqW3btgoMDFRISIgyMzOVkJCgDRs26KmnnlJYWJgqVKggX19fdejQQSNHjtTatWt11113SZLCw8N1+vRptWnTRoGBgerRowfhAACA6+QW35gJCQlKSEgo8thDDz1kGnfgwAE1bNhQY8eOVXZ2tuLi4nTrrbeqSpUqWrt2rWn8+PHjS61mAADKM7cICNcrIiJCqampWrRokQoKCjRkyBD5+flZXRYAAOWORwWEwMBAzZo1y+oyAAAo9zhREgAAMCEgAAAAEwICAAAwISAAAAATAgIAADDxqKMYysLAJ/8hf39/q8soMenp6YqJibG6jBJHX56FvgDPwwwCAAAwISAAAAATAgIAADAhIAAAABMCAgAAMOEohsskfTRdZwsuWF1GyTr6odUVlA768iz0Var+2Xa01SWgnGEGAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJgQEAAAgAkBAQAAmBAQAACASbkOCHa7XampqTp27Jg6duxodTkAAHiMch0QAADAjfGYUy3b7XZ99tlnysvL0+nTp5WYmKj169dr3759Gjp0qE6ePKmPP/5YTqdTwcHBSktLs7pkAAA8lscEBEnKzc3V/Pnz9cEHH2jhwoVavny5Nm/erIULF6pu3bpauHChvLy81LNnT+3cudPqcgEA8FgeFRBq164tSQoODlaNGjVks9kUGhqqixcvytfXV4MHD1ZgYKBOnjwpp9NpcbUAAHgujwoINpvtio9fvHhRn3zyiVasWKELFy4oISFBhmGUcXUAAJQfxe6kuGPHDi1YsED5+fnq0aOHHnzwQW3YsKEsartuPj4+CggIUEJCgpKSkhQeHq7MzEyrywIAwGMVO4Pw8ssvq3///vroo49UoUIFrV69Ws8//7yaNGlSFvW5JCQkuG43adLE9fdr166t+fPnF/v85cuXl1ptAACUN8XOIBQWFqpx48b6/PPP9fjjjysiIkIFBQVlURsAALBIsQEhICBA8+fP16ZNm/Too4/qH//4hypWrFgWtQEAAIsUGxBSU1N1/vx5paWlKTQ0VKdOndLkyZPLojYAAGCRq+6DsGXLFtft2NhYFRQUaMuWLXrkkUd09OhRValSpUwKBAAAZe+qAWHatGmSpLNnz+r7779X/fr15eXlpW3btqlWrVpatmxZmRUJAADK1lUDwuLFiyVJvXr10vTp0xUZGSlJOn78uF566aWyqQ4AAFii2H0QfvjhB1c4kKTbb79dP/zwQ6kWBQAArFXseRDuvfdeDRs2TH/9619lGIbWrl2rhg0blkVtlljwxPPy9/e3uowSk56erpiYGKvLKHH05VnoC/A8xQaElJQULVmyxLXPQaNGjfT000+XemEAAMA6xQaEPn36aN68eerRo0dZ1AMAANxAsfsgXLhwQSdOnCiLWgAAgJsodgYhOztbzZo1U+XKleXv7y/DMGSz2bR+/fqyqA8AAFig2IDw1ltvlUUdAADAjRQbEG6//Xa988472rRpk5xOpx588EF17dq1LGqzRM8P1+is86LVZZSsQxlWV1A66Muz0Ncf8n77LmXyd4BLig0Ir7/+uo4cOaJ27drJMAzZ7XZ9//33GjVqVFnUBwAALFBsQNi4caPee+89eXn9sj/jI488olatWpV6YQAAwDrFHsVQUFAgp9NZ5L63t3epFgUAAKxV7AxC69atlZiYqCeffFKS9MEHHyguLq7UCwMAANYpNiBs3bpV8fHx2rVrl0JCQtS7d2898sgjZVAaAACwynWdSfGLL77Q3r17VVBQIH9/f1WqVEnR0dFlUR8AALBAsQGhXr16qlevnrp06aJ169bpzTff1FtvvaVdu3aVRX0AAMACxQaEcePGKT09Xd7e3rr//vs1duxYPfDAA2VRGwAAsEixRzGcO3dOhmEoKipKNWrUUPXq1RUcHFzihdjtdqWmppb4egEAwO9X7AzCG2+8IUk6cOCAvvrqK/Xu3Vvnz5/XF198UerFAQAAaxQbEA4ePKivvvpKX331lTIyMhQdHa2mTZuWSjHffPONevTooaysLHXu3FmhoaFaunSpa/nUqVO1b98+paamytfXVx07dlRoaKimTZumoKAghYaG6p577tFzzz2nl156SSdPnlR2draaNGmigQMHlkrNAACUR8UGhAEDBujRRx/VM888o/r165fqSZJ8fHw0b948HT9+XH/729/UunVrzZkzRwEBAXrppZf073//W1WqVJHD4dCKFStUUFCgxx9/XO+++67CwsL0wgsvSJJOnDihevXqqUOHDnI4HAQEAAB+p2IDwtq1a8uiDknSvffeK5vNpvDwcOXl5aly5coaNmyYKlasqIMHD6pevXqSpKioKElSVlaWgoKCFBYWJklq2LChzpw5o1tuuUU7d+7Upk2bFBQUpPz8/DLrAQCA8qDYgFCWbDab6/bPP/+sadOm6fPPP5ckJSUlyTAMSXJdF6Jy5crKzc1VVlaWKlWqpG+++UZ33HGH7Ha7goODNX78eB05ckTLly+XYRhF1g8AAK7OrQLCbwUFBSk6Olpt27ZVYGCgQkJClJmZqTvvvNM1xsvLS2PGjFGvXr0UHByswsJCRUZG6qGHHtLgwYOVnp6ugIAARUZGKjMzU1WqVLGwIwAAPIfbBISEhATXbX9/f3322WdXHRsbG+u6nZGRoXfeeUd+fn4aMmSIIiIiVLNmzTL9aQQAgPLGbQLCjapYsaI6duyoChUq6I477lDLli2tLgkAAI/n8QGha9eu6tq1q9VlAABQrhR7JkUAAHDzISAAAAATAgIAADAhIAAAABMCAgAAMPH4oxhK2ry/xsvf39/qMkpMenq6YmJirC6jxNGXZ6EvwPMwgwAAAEwICAAAwISAAAAATAgIAADAhIAAAABMOIrhMs+u+1o/OQ2ryyhZh/9tdQWlg748y03Q1+p2jS0sBChZzCAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwISAAAAATAgIAADDxuIDQsWNHHTt2THa7XevXr7e6HAAAyiWPPZNiQkKC1SUAAFBuWRYQ8vLyNHToUGVmZioiIkJbtmzR5MmTNX36dNfy1157TVFRUZoyZYq++OIL/elPf1J2drYkKS0tTWFhYapevbrmzp0rX19fHTt2TC1btlSfPn105MgRDR8+XD4+Prrjjjt0/PhxLV682Kp2AQDwKJYFhHfffVd33nmnpk2bpgMHDiguLk779u3TpEmTVKVKFb355ptat26dHnvsMW3ZskUrV67U+fPn9fjjj5vW9cMPP+h//ud/lJ+fr4cfflh9+vTR66+/rt69e6tp06Zavny5jh8/bkGXAAB4JssCwoEDB9SkSRNJUo0aNVSpUiVVqVJFKSkpCgwM1KlTp9SgQQPt379fdevWlZeXl4KCglSrVi3TumrVqiUfHx/5+PioQoUKrvXXr19fkhQTE6O1a9eWXXMAAHg4y3ZSrFWrlrZt2yZJOnr0qLKzszV69GhNnDhRr776qm677TYZhqGoqCjt2LFDhYWFOn/+vPbv329al81mu+b6v/nmm9JtBgCAcsayGYT27dtr+PDh6tKli26//Xb5+/srPj5eHTt2VEhIiMLCwpSZmanatWurRYsWat++vW677TZVrlz5utY/ZMgQjRw5UvPnz1dwcLB8fDx2f0wAAMqcZd+ae/bsUfv27dW4cWMdPnxY27Zt04gRIzRixAjT2GeeeUbPPPNMkcf69evnuh0bG+u6vXHjRknS9u3blZKSosjISK1YsUJbt24tnUYAACiHLAsIVatW1eDBgzV9+nQ5nU699NJLJbr+iIgIDRo0SAEBAfLy8tLEiRNLdP0AAJRnlgWE8PDwUj3s8P7775fdbi+19QMAUJ553JkUAQBA6SMgAAAAEwICAAAwISAAAAATAgIAADDh7EGXmd2iofz9/a0uo8Skp6crJibG6jJKHH15FvoCPA8zCAAAwISAAAAATAgIAADAhIAAAABMCAgAAMCEoxgus/ijM3IUlKd/lju16egpq4soBfTlWcp3X33bVrG6EKDEMYMAAABMCAgAAMCEgAAAAEwICAAAwISAAAAATAgIAADAhIAAAABMCAgAAMDELQKC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ERER6tevnyTp/vvvV//+/V19Xem16gn/p52cnKwJEybI19dXYWFhmjBhgiTP3l6XHDp0yBTmPGV7XekzfdSoUXr55ZfL7L3FtRgAAIDJTfcTAwAAKB4BAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJi4z0GfADzKuHHjtHXrVl28eFFHjx5VjRo1JEmJiYl67bXXFBER4RobFhamefPmXXVdl86h369fPw0fPlybNm1SaGio60xwvXr1cl1h8LfLL3nkkUc0aNCg0mgTuGkREADckLFjx0qSjh07psTERK1Zs0bSL5ezbtasmessdTeif//+rvPnf//993r66ad1yy23uM4++dvlAEoHPzEAcGtVq1ZVYmKi3n77batLAW4qzCAAKHGffvqp4uPjXfdHjBhhujDV71GrVi2tXr3adX/atGlatGiR6/7SpUuLXMUOwB9HQABQ4v7oTwxXUqFCBddtfmIASh8/MQBwe999951rJ0gAZYOAAMCtHT58WG+//bY6d+5sdSnATYWfGAC4nUv7GNhsNnl7e2vYsGFq0KCB1WUBNxUu9wwAAEyYQQBQJl544QXt37/f9HizZs00YMAACyoCcC3MIAAAABN2UgQAACYEBAAAYEJAAAAAJgQEAABgQkAAAAAm/x/gFXyxawUpQQAAAABJRU5ErkJggg==
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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AADAxCXug+BKqvV4R/7+/laXUWLS0tIUFRVldRkl6lboIwCUNEYQAACACQEBAACYEBAAAIAJAQEAAJgQEAAAgAlXMVzm4yU9lZ93zuoyStTB7VZXUFSHXiutLgEAcBlGEAAAgAkBAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJgQEAAAgInlAcHhcCgxMdHqMgAAwG9YHhAAAIDrcZk7KWZkZOjpp5/W3//+d6Wmpurnn3/W2bNnFRsbq65du6pHjx669957tW/fPgUGBqp+/fr64osvdP78ec2ePVve3t4aNWrUFde77bbbdP78eSUnJ8vb29vqrgIA4PJcYgThxx9/1FNPPaURI0YoMjJSLVu21OzZs/XWW29p7ty5znZ16tRRSkqKcnNzVaZMGc2ZM0f33HOPtmzZosOHD191vdatW2vu3LmEAwAArpNLjCB8/vnnioiIUGFhocLDw5WSkqLVq1crODhY+fn5zna1atWSJIWGhuqee+5xTufk5FxzvSpVqpRuhwAAcHMuERDatm2rtm3batCgQXrkkUdUt25dde3aVZs2bdJnn312XduYPXv2Vdez2WwlVToAAB7JJQKCJN1zzz1q06aNli1bJi8vL6Wmpqps2bLy9vZWbm5uses/+uijSkhI+J/XAwAAZpYHBLvd7px+8skn9eSTT16x3bx585zTkydPdk6PGjXKOb1ypfmxwb9dDwAAXB+XOEkRAAC4FgICAAAwISAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwsfxGSa7mr7Ep8vf3t7qMEpOWlqaoqCirywAAuDhGEAAAgAkBAQAAmBAQAACACQEBAACYEBAAAIAJVzFc5p//itPF/HNWl1GiUvffnO0kdFx1czYEAHA5jCAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwISAAAAATlwgIDodDiYmJVpcBAAB+5RIBAQAAuBaXuZPitm3b1LNnT2VmZmrAgAHKzs7WggULnMvffPNN3XbbbRo7dqx27typ8PBwHT9+XDNmzNDUqVPVokULRUdHa/369froo4/06quvavjw4Tpy5IhycnLUp08ftWjRwsIeAgDgPlwmIAQEBGjmzJnKyMhQbGysOnbsqJkzZyogIEAvvviivvjiCwUGBurcuXNaunSpMjIy9Pjjj191e5mZmdq8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
"
>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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IF28eFEzZsxQYmKi+vTpI29vb/n5+enMmTO66667DLd99dVX1a9fP7Vv397BqQEAqHostst/mjuBxMREHTp0SOPHj3fo+17+Te07D/yoakXFDn1vAADK02DkwNuyn9TUVAUGBkr6v+++li1bytPT03B9pzvcAAAAnINTHW6wWq1mRwAAAP8fMwkAAMAQJQEAABiiJAAAAEOUBAAAYIiSAAAADDnV1Q1mqzvwyeteK1rVXXntrKth7Izd1bjy2CXG/3swkwAAAAxREgAAgCFKAgAAMERJAAAAhigJAADAEFc3XCEz/jm5FZ43O4Ypakr6fo/ZKcxRkWN/YFRSxewYAByAmQQAAGCIkgAAAAxREgAAgCFKAgAAMERJAAAAhigJAADAECUBAAAYoiQAAABDVbYkjB07VkVFRTpx4oS2bdtmdhwAACqdKlsSFixYIA8PD+3Zs0f79+83Ow4AAJWOabdl/umnnzR58mRVq1ZN7u7u+sc//qGEhATt27dPNptNgwcPVo8ePRQeHq77779fGRkZ8vb21sMPP6ydO3fqwoULWrlypVJSUpSSkqLc3FxlZ2dr1KhR6tatm7p06aIPPvhAy5cvV0FBgR566CH99a9/NWu4AABUOqbNJHz55Zdq0aKFYmNjNWLECH388cc6duyY1q1bp3fffVdLly7VhQsXJEmtWrVSXFycioqKVKNGDcXGxqpp06bat2+fJCk/P1+xsbFauXKl5syZo5KSEkmSu7u7nn/+eQUFBVEQAAD4nUybSejbt6/efvttPfvss/L19dUDDzyg9PR0hYeHS5JKSkp04sQJSVKLFi0kSX5+fmratKl9ubCwUJLUpk0bubm5qX79+vLz81NWVpYJIwIAoGoxbSYhJSVFgYGBiouLU/fu3ZWYmKi2bdsqPj5ecXFx6tGjh+66666b2ld6erok6dy5c8rNzVW9evXsr7m5uamsrKxCxgAAQFVm2kxCy5YtNWHCBC1evFhubm5atGiRkpOTFRYWpvz8fHXt2lU+Pj43ta9z585p0KBBunjxombMmCF3d3f7a82aNdOSJUvUokUL9erVq6KGAwBAlWNaSbj77ru1fv36q55r2bLlNevFx8fblxcsWGBfnjp1qiQpMTFRbdq00fjx46/a7vJlj82bN9fWrVtvW24AAFxFlb0EEgAA3BrTZhJuF6vVanYEAACq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HB09elQPPfSQ3Nzc9M0336hZs2Zat26dw0ICAADHu25JiI+PlyQ999xzeuutt9S4cWNJ0vHjxzV9+nTHpAMAAKYp95yEEydO2AuCJN155506ceJEhYYCAADmK/c+Cc2bN9fEiRPVo0cP2Ww2JScn6+GHH3ZENoeL7faiPD09zY5hitTUVAUGBpodAwDgRMotCVFRUUpISLCfg9ChQweFhYVVeDAAAGCuckvCyJEjtWLFCg0dOtQReQAAgJMo95yES5cu6eTJk47IAgAAnEi5MwnZ2dnq0qWL6tWrJ09PT9lsNlksFqWkpDgiHwAAMEm5JeGdd95xRA4AAOBkyi0Jd955p9auXas9e/aopKRE7dq108CBAx2RzeGGfZSknJJis2OY56fvf/cmH/R9pgKCAACcQbkl4R//+IcOHz6sp556SjabTYmJiTp69KimTp3qiHwAAMAk5ZaEXbt26X/+53/k5vbrOY6dO3dWcHBwhQcDAADmKvfqhtLSUpWUlFz12N3dvUJDAQAA85U7k9C7d29FRESoV69ekqTNmzcrKCiowoMBAABzlVsS9u/fr5CQEKWlpcnPz08jRoxQ586dHRANAACY6abuuPjFF1/o4MGDKi0tlaenp+rWratWrVo5Ih8AADBJuSWhdevWat26tZ555hlt2bJFS5cu1TvvvKO0tDRH5AMAACYptyTMnDlTqampcnd3V5s2bTRjxgw98sgjjsgGAABMVO7VDRcuXJDNZlOTJk0UEBCge++9V76+vuXuODExUdHR0bclJAAAcLxyZxLeeOMNSVJmZqZ2796tESNGKD8/X1988UWFhwMAAOYptyQcOnRIu3fv1u7du/X999+rVatWevTRR29q58ePH1doaKjee+89SVJoaKjmz5+vTZs26fDhw8rOztb58+cVFhamjz/+WD/99JPmzp2r1q1b64033lBaWpry8vIUEBCg2bNnq3///nrttdd03333afv27fr88881fPhwRUZGqrCwUDk5ORo1apS6du2q4OBgPfLII/rhhx9ksVgUExNzUzMgAADgV+UebhgzZoxOnz6twYMHa+vWrZo/f75CQkJu+Y1r1KihFStW6IknntD27du1dOlSPf/889q8ebNyc3Pl5+en2NhYrVu3TgcOHNDp06fVr18/bdq0SZK0ceNG9e3bV4cOHdKQIUMUGxuradOm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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Berdasarkan Grafik diatas Interpretasi dari masing-masing cluster:</p>
<ul>
<li>Cluster 0 : Fasilitas Oke (positive)</li>
<li>Cluster 1 : Lokasi dekat Mall (positive)</li>
<li>Cluster 2 : Tempat Nyaman dan Bersih(positive)</li>
<li>Cluster 3 : Parkir Sempit (positive)</li>
</ul>
</div>
</div>
</div>
    </div>
  </div>
</body>




 


</html>
