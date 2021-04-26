---
layout: post
title: Text Classification
categories: [Machine Learning,Natural Language Processing,python]
excerpt: 
---

<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Text-Classification</title><script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>

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
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sns</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Data yang akan dipakai pada tutorial kali ini adalah data tentang <strong>Hate Speech</strong> dari twitter. Berikut adalah link downloadnya <a href="https://drive.google.com/file/d/1pDkr0viHOOfIOmO_LXRuy6M5t2I8V-7-/view?usp=sharing">Twitter Hate Speech</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[85]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_hs</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;Twitter Indo HS.csv&quot;</span><span class="p">)</span>
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
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_hs</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[36]:</div>



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
      <th>Tweet</th>
      <th>HS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>- disaat semua cowok berusaha melacak perhatia...</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>RT USER: USER siapa yang telat ngasih tau elu?...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41. Kadang aku berfikir, kenapa aku tetap perc...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>USER USER AKU ITU AKU\n\nKU TAU MATAMU SIPIT T...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>USER USER Kaum cebong kapir udah keliatan dong...</td>
      <td>1</td>
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
<div class="prompt input_prompt">In&nbsp;[37]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Memeriksa Total baris dan kolom</span>
<span class="n">twitter_hs</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[37]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(13169, 2)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[38]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;HS&quot;</span><span class="p">,</span><span class="n">data</span><span class="o">=</span><span class="n">twitter_hs</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[38]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;AxesSubplot:xlabel=&#39;HS&#39;, ylabel=&#39;count&#39;&gt;</pre>
</div>

</div>

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
<h2 id="Text-Preprocessing">Text Preprocessing<a class="anchor-link" href="#Text-Preprocessing">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Cleaning-Twitter-Text">Cleaning Twitter Text<a class="anchor-link" href="#Cleaning-Twitter-Text">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pada twitter terdapat beberapa pola teks khusus yang harus di cleaning terlebih dahulu, seperti adanya alamat url web, simbol @, emoji. Berikut adalah beberapa ilustrasinya</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[54]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_hs</span><span class="o">.</span><span class="n">Tweet</span><span class="p">[</span><span class="n">twitter_hs</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="s2">&quot;http&quot;</span><span class="p">)]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[54]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>79       RT USER: china babi... china maling...\n#UsirC...
1403     RT USER: Jd kan aku tempat pelampiasan nafsu m...
2193     Ahok si penghina Al - Qur&#39;an dan Ulama ini sel...
2578     RT USER: Pngen bngt dudukin kontol kayak gini ...
2958     RT USER: Manusia kampret bernama Syahroni B Da...
3975     USER: ahoker siap bela penista agama https:\/\...
4115     #JakartaBanjir Pemimpinnya gak punya akhlak yg...
5089     RT USER: https:// #ngentoto #mememk #lonte #le...
5138      Hidup china komunis ! https:\/\/t.co\/b1RheVKrXl
5176     RT USER: Ayoo jaga keutuhan NKRI!!! Tangkap Pe...
5774                   CINA ASU https:\/\/t.co\/zM1BsjAIHA
5781     Ini tuh kesalahan Jokowi dan Ahok si babi atei...
6618     Kampungan ya pendukung AHY https:\/\/t.co\/Gme...
6907     RT USER: Iyaa... Ahog Ngak pantes jadi pemimpi...
7024     RT USER: kalo di catatan harian menantu sintin...
8554     Ini pasti salah Jokowi, Ahok dan kafir-kafir a...
8659     RT USER: Gede amat punya on Diego USER USER US...
9050     RT USER: Lagi VIRAL! Ngocokin kontol Om secuit...
9590     RT USER: PENJARAKAN PENISTA AGAMA !!! ATAU USE...
9622     RT USER: Pngen bngt dudukin kontol kayak gini ...
9963     RT USER: ni jilbob pinter nyepong kontol yaakk...
10931    RT USER: https:// #ngentot 1 ronde setelah sub...
11081    RT USER: Sekumpulan Teman Penista Agama\nTdk a...
12187    RT USER: Pacare sopo iki, suruh ngemut kontol ...
Name: Tweet, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[60]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_hs</span><span class="o">.</span><span class="n">Tweet</span><span class="p">[</span><span class="n">twitter_hs</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="s2">&quot;@&quot;</span><span class="p">)]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[60]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>288      USER USER USER USER USER USER USER USER USER U...
2391     Ini lho mengkritik yg dimaui pak USER yaitu kr...
3242     online cuma dapet pajak dr incm persh online n...
4127     Belajar memancing... ???; #fishing #rihlah #ar...
4544     Pemecatan tidak masuk akal USER memberi pelaja...
5324     USER USER USER USER USER USER USER USER USER U...
6332     Team Kagum Hotels lagi di acara Turnament Golf...
7751     USER USER USER USER USER USER USER USER USER U...
8478     Sosok pemimpin yang sederhana, ta&#39;dzim kpd ula...
8840     Bersihkan oknum brutal ini jika #2019GantiPres...
8975     Apa yang DS USER buat adalah demi generasi aka...
10642    USER KEBIJAKAM PENGEMBALIAN BEBAS KERUMITAN\n\...
11830    &#34;Sosialisasi Keamanan Pangan&#34;* - ISWI @ Aula G...
12941    Hasil REVOLUSI MENTAL; Anak seumuran SD tak ma...
Name: Tweet, dtype: object</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Untuk mengidentifikasi emoji kita harus menginstall package berikut</p>

</div>
</div>
</div>! pip install emoji
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>mendefinisikan fungsi cleaning untuk text twitter</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[74]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">re</span>
<span class="kn">import</span> <span class="nn">emoji</span>
<span class="k">def</span> <span class="nf">clean_tweet</span><span class="p">(</span><span class="n">tweet</span><span class="p">):</span>
    <span class="n">tweet</span> <span class="o">=</span> <span class="n">re</span><span class="o">.</span><span class="n">sub</span><span class="p">(</span><span class="s2">&quot;@[A-Za-z0-9]+&quot;</span><span class="p">,</span><span class="s2">&quot;&quot;</span><span class="p">,</span><span class="n">tweet</span><span class="p">)</span> <span class="c1">#Remove @ sign</span>
    <span class="n">tweet</span> <span class="o">=</span> <span class="n">re</span><span class="o">.</span><span class="n">sub</span><span class="p">(</span><span class="sa">r</span><span class="s2">&quot;(?:\@|http?\://|https?\://|www)\S+&quot;</span><span class="p">,</span> <span class="s2">&quot;&quot;</span><span class="p">,</span> <span class="n">tweet</span><span class="p">)</span> <span class="c1">#Remove http links</span>
    <span class="n">tweet</span> <span class="o">=</span> <span class="s2">&quot; &quot;</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">tweet</span><span class="o">.</span><span class="n">split</span><span class="p">())</span>
    <span class="n">tweet</span> <span class="o">=</span> <span class="s1">&#39;&#39;</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">c</span> <span class="k">for</span> <span class="n">c</span> <span class="ow">in</span> <span class="n">tweet</span> <span class="k">if</span> <span class="n">c</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">emoji</span><span class="o">.</span><span class="n">UNICODE_EMOJI</span><span class="p">)</span> <span class="c1">#Remove Emojis</span>
    <span class="n">tweet</span> <span class="o">=</span> <span class="n">tweet</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="s2">&quot;#&quot;</span><span class="p">,</span> <span class="s2">&quot;&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">replace</span><span class="p">(</span><span class="s2">&quot;_&quot;</span><span class="p">,</span> <span class="s2">&quot; &quot;</span><span class="p">)</span> <span class="c1">#Remove hashtag sign but keep the text</span>

    <span class="k">return</span> <span class="n">tweet</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[87]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span> <span class="o">=</span> <span class="n">twitter_hs</span>
<span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">clean_tweet</span><span class="p">)</span>
<span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">re</span><span class="o">.</span><span class="n">sub</span><span class="p">(</span><span class="s2">&quot;RT USER|USER&quot;</span><span class="p">,</span><span class="s2">&quot;&quot;</span><span class="p">,</span><span class="n">x</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[88]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[88]:</div>



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
      <th>Tweet</th>
      <th>HS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>- disaat semua cowok berusaha melacak perhatia...</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>:  siapa yang telat ngasih tau elu?edan sarap ...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41. Kadang aku berfikir, kenapa aku tetap perc...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>AKU ITU AKU\n\nKU TAU MATAMU SIPIT TAPI DILI...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Kaum cebong kapir udah keliatan dongoknya da...</td>
      <td>1</td>
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
<h4 id="Noise-Removal">Noise Removal<a class="anchor-link" href="#Noise-Removal">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
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
<div class="prompt input_prompt">In&nbsp;[89]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">lower</span><span class="p">()</span>
<span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">noise_removal</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[90]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[90]:</div>



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
      <th>Tweet</th>
      <th>HS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>disaat semua cowok berusaha melacak perhatian ...</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>siapa yang telat ngasih tau eluedan sarap gue ...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>kadang aku berfikir kenapa aku tetap percaya p...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>aku itu akunnku tau matamu sipit tapi diliat d...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>kaum cebong kapir udah keliatan dongoknya dari...</td>
      <td>1</td>
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
<h4 id="Tokenization">Tokenization<a class="anchor-link" href="#Tokenization">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[81]:</div>
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
<div class="prompt input_prompt">In&nbsp;[91]:</div>
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
<div class="prompt input_prompt">In&nbsp;[93]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">tokenize_fun</span><span class="p">)</span>
<span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[93]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>0    [disaat, semua, cowok, berusaha, melacak, perh...
1    [siapa, yang, telat, ngasih, tau, eluedan, sar...
2    [kadang, aku, berfikir, kenapa, aku, tetap, pe...
3    [aku, itu, akunnku, tau, matamu, sipit, tapi, ...
4    [kaum, cebong, kapir, udah, keliatan, dongokny...
Name: Tweet, dtype: object</pre>
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
<div class="prompt input_prompt">In&nbsp;[94]:</div>
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

    <div class="prompt output_prompt">Out[94]:</div>



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
<div class="prompt input_prompt">In&nbsp;[95]:</div>
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
<div class="prompt input_prompt">In&nbsp;[96]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">replace_slang_word</span><span class="p">)</span>
<span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[96]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>0    [disaat, semua, cowok, berusaha, melacak, perh...
1    [siapa, yang, telat, mengasih, tau, eluedan, s...
2    [kadang, aku, berpikir, kenapa, aku, tetap, pe...
3    [aku, itu, akunnku, tau, matamu, sipit, tapi, ...
4    [kaum, cebong, kapir, sudah, kelihatan, dongok...
Name: Tweet, dtype: object</pre>
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
<div class="prompt input_prompt">In&nbsp;[100]:</div>
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
<div class="prompt input_prompt">In&nbsp;[101]:</div>
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
<div class="prompt input_prompt">In&nbsp;[103]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">stopwords_removal</span><span class="p">)</span>
<span class="n">twitter_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[103]:</div>



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
      <th>Tweet</th>
      <th>HS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[disaat, cowok, berusaha, melacak, perhatian, ...</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>[telat, mengasih, tau, eluedan, sarap, gue, be...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>[kadang, berpikir, percaya, tuhan, jatuh, berk...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>[akunnku, tau, matamu, sipit]</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>[kaum, cebong, kapir, dongoknya, dongok, hahahah]</td>
      <td>1</td>
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
<h4 id="Stemming">Stemming<a class="anchor-link" href="#Stemming">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[104]:</div>
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
<div class="prompt input_prompt">In&nbsp;[105]:</div>
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
<div class="prompt input_prompt">In&nbsp;[107]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">word_dict</span> <span class="o">=</span> <span class="p">{}</span>

<span class="k">for</span> <span class="n">document</span> <span class="ow">in</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="p">:</span>
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
<div class="prompt input_prompt">In&nbsp;[108]:</div>
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
<div class="prompt input_prompt">In&nbsp;[109]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">get_stemmer_word</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[110]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[110]:</div>



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
      <th>Tweet</th>
      <th>HS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>[saat, cowok, usaha, lacak, perhati, gue, lo, ...</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>[telat, asih, tau, eluedan, sarap, gue, gaul, ...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>[kadang, pikir, percaya, tuhan, jatuh, berkali...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>[akunnku, tau, mata, sipit]</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>[kaum, cebong, kapir, dongok, dongok, hahahah]</td>
      <td>1</td>
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
<h4 id="Convert-to-Text">Convert to Text<a class="anchor-link" href="#Convert-to-Text">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[111]:</div>
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
<div class="prompt input_prompt">In&nbsp;[112]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">list_to_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[113]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[113]:</div>



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
      <th>Tweet</th>
      <th>HS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>saat cowok usaha lacak perhati gue lo lantas r...</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>telat asih tau eluedan sarap gue gaul cigax ji...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>kadang pikir percaya tuhan jatuh berkalikali k...</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>akunnku tau mata sipit</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>kaum cebong kapir dongok dongok hahahah</td>
      <td>1</td>
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
<h4 id="Menampilkan-WordCloud">Menampilkan WordCloud<a class="anchor-link" href="#Menampilkan-WordCloud">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[114]:</div>
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
<p>menyatukan setiap baris pada <code>twitter_clean</code> dan mengubahnya menjadi bentuk <code>string</code></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[115]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tweet_text</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">to_string</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[116]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">wordcloud</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span><span class="n">background_color</span><span class="o">=</span><span class="s2">&quot;white&quot;</span><span class="p">,</span> <span class="n">width</span> <span class="o">=</span> <span class="mi">1920</span><span class="p">,</span> <span class="n">height</span> <span class="o">=</span> <span class="mi">1080</span><span class="p">)</span>
<span class="n">wordcloud</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">tweet_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[116]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;wordcloud.wordcloud.WordCloud at 0x1e9c38ae3a0&gt;</pre>
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
<div class="prompt input_prompt">In&nbsp;[117]:</div>
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
<p>Pada wordcloud diatas terdapat kata-kata yang terindikasi sebagai stopword. Oleh karena itu, kita akan membuang kata-kata tersebut dengan proses dibawah ini</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[118]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">re</span>
<span class="k">def</span> <span class="nf">remove_certain_word</span><span class="p">(</span><span class="n">words</span><span class="p">,</span><span class="n">text</span><span class="p">):</span>
    <span class="k">return</span> <span class="n">re</span><span class="o">.</span><span class="n">sub</span><span class="p">(</span><span class="n">text</span><span class="p">,</span><span class="s2">&quot;&quot;</span><span class="p">,</span><span class="n">words</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[135]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">remove_certain_word</span><span class="p">(</span><span class="n">x</span><span class="p">,</span><span class="s2">&quot;ya|gue|gua|orang|url|kalo|nya|sih|tau|lu|lo|deh|nih|tuh|kak&quot;</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[136]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tweet_text</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="o">.</span><span class="n">to_string</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[137]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">wordcloud</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span><span class="n">background_color</span><span class="o">=</span><span class="s2">&quot;white&quot;</span><span class="p">,</span> <span class="n">width</span> <span class="o">=</span> <span class="mi">1920</span><span class="p">,</span> <span class="n">height</span> <span class="o">=</span> <span class="mi">1080</span><span class="p">)</span>
<span class="n">wordcloud</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">tweet_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[137]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;wordcloud.wordcloud.WordCloud at 0x1e9c1e3bd00&gt;</pre>
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
<div class="prompt input_prompt">In&nbsp;[138]:</div>
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
<h2 id="Term-Weighting">Term Weighting<a class="anchor-link" href="#Term-Weighting">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[139]:</div>
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
<div class="prompt input_prompt">In&nbsp;[142]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tf_idf_vectorizer</span> <span class="o">=</span> <span class="n">TfidfVectorizer</span><span class="p">()</span>
<span class="n">tf_idf_result</span> <span class="o">=</span> <span class="n">tf_idf_vectorizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">twitter_clean</span><span class="o">.</span><span class="n">Tweet</span><span class="p">)</span>
<span class="n">tf_idf_result_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="o">.</span><span class="n">toarray</span><span class="p">(),</span><span class="n">columns</span><span class="o">=</span><span class="n">tf_idf_vectorizer</span><span class="o">.</span><span class="n">get_feature_names</span><span class="p">())</span>
<span class="n">tf_idf_result_df</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[142]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>jokowi       177.444285
presiden     150.811222
indonesia    132.679393
agama        128.603519
islam        127.795281
                ...    
gakerasa       0.145298
football       0.145146
deli           0.145146
hanc           0.141421
jiamput        0.076291
Length: 23255, dtype: float64</pre>
</div>

</div>

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
<h3 id="Menyiapkan-data">Menyiapkan data<a class="anchor-link" href="#Menyiapkan-data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[143]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">response</span> <span class="o">=</span> <span class="n">twitter_clean</span><span class="o">.</span><span class="n">HS</span>
<span class="n">predictors</span> <span class="o">=</span> <span class="n">tf_idf_result</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[204]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.svm</span> <span class="kn">import</span> <span class="n">SVC</span>
<span class="kn">from</span> <span class="nn">sklearn.tree</span> <span class="kn">import</span> <span class="n">DecisionTreeClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.naive_bayes</span> <span class="kn">import</span> <span class="n">MultinomialNB</span>
<span class="kn">from</span> <span class="nn">sklearn.ensemble</span> <span class="kn">import</span> <span class="n">RandomForestClassifier</span><span class="p">,</span><span class="n">GradientBoostingClassifier</span><span class="p">,</span><span class="n">AdaBoostClassifier</span>
<span class="kn">from</span> <span class="nn">sklearn.neighbors</span> <span class="kn">import</span> <span class="n">KNeighborsClassifier</span>

<span class="k">def</span> <span class="nf">base_models</span><span class="p">():</span>
    <span class="n">svc</span> <span class="o">=</span> <span class="n">SVC</span><span class="p">()</span>
    <span class="n">tree</span> <span class="o">=</span> <span class="n">DecisionTreeClassifier</span><span class="p">()</span>
    <span class="n">nb</span> <span class="o">=</span> <span class="n">MultinomialNB</span><span class="p">()</span>
    <span class="n">rf</span> <span class="o">=</span> <span class="n">RandomForestClassifier</span><span class="p">()</span>
    <span class="n">knn</span> <span class="o">=</span> <span class="n">KNeighborsClassifier</span><span class="p">()</span>
    <span class="n">ada</span> <span class="o">=</span> <span class="n">AdaBoostClassifier</span><span class="p">()</span>
    <span class="n">models</span><span class="o">=</span><span class="p">{</span><span class="s2">&quot;svc&quot;</span><span class="p">:</span><span class="n">svc</span><span class="p">,</span><span class="s2">&quot;tree&quot;</span><span class="p">:</span><span class="n">tree</span><span class="p">,</span><span class="s2">&quot;nb&quot;</span><span class="p">:</span><span class="n">nb</span><span class="p">,</span><span class="s2">&quot;rf&quot;</span><span class="p">:</span><span class="n">rf</span><span class="p">,</span><span class="s2">&quot;knn&quot;</span><span class="p">:</span><span class="n">knn</span><span class="p">,</span>
       <span class="s2">&quot;ada&quot;</span><span class="p">:</span><span class="n">ada</span><span class="p">}</span>
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
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pada tutorial ini pembagian data yang akan dipilih adalah holdout, karena akan dibandingkan dengan model hasil tuning</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[145]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">train_test_split</span>
<span class="n">X_train</span><span class="p">,</span> <span class="n">X_test</span><span class="p">,</span> <span class="n">y_train</span><span class="p">,</span> <span class="n">y_test</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">predictors</span><span class="p">,</span><span class="n">response</span><span class="p">,</span> <span class="n">test_size</span><span class="o">=</span><span class="mf">0.3</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><code>test size</code> pada sintaks diatas menggambarkan proporsi data testing. Kemudian hasil output dari fungsi <code>train_test_split</code> ada 4 output yang berkaitan dengan prediktor dan respon pada data training dan testing</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Tuning-Hyperparamters">Tuning Hyperparamters<a class="anchor-link" href="#Tuning-Hyperparamters">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Package <code>sklearn</code> memiliki fungsi bawaan untuk melakukan tuning hyperparamter, namun kecepatan waktu tuning tidaklah terlalu baik. Untuk mengatasi hal tersebut, kita bisa menggunakan package <code>tune-sklearn</code> yang diklaim bisa mempercepat waktu tuning. Jika tertarik membaca lebih lanjut silahkan kunjungi <a href="https://medium.com/distributed-computing-with-ray/gridsearchcv-2-0-new-and-improved-ee56644cbabf">artikel ini</a>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Pada tutorial ini proses tuning akan dilakukan pada data training yang sudah diperoleh sebelumnya. Sedangkan proses evaluasi akan dilakukan pada data testing</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Memilih-Parameter-Tuning">Memilih Parameter Tuning<a class="anchor-link" href="#Memilih-Parameter-Tuning">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pada Tahap ini kita akan memilih parameter yang akan dituning pada masing-masing model. Untuk penjelasan masing-masing paramter bisa dilihat di website sklearn</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[237]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="n">parameters_svc</span> <span class="o">=</span> <span class="p">{</span>
   <span class="s1">&#39;C&#39;</span><span class="p">:</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mf">0.5</span><span class="p">,</span><span class="mi">20</span><span class="p">,</span><span class="mf">0.5</span><span class="p">)</span>
<span class="p">}</span>
<span class="n">parameters_tree</span> <span class="o">=</span> <span class="p">{</span>
   <span class="s1">&#39;min_samples_split&#39;</span><span class="p">:</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mf">0.2</span><span class="p">,</span><span class="mf">0.9</span><span class="p">,</span><span class="mf">0.1</span><span class="p">)</span>
<span class="p">}</span>
<span class="n">parameters_nb</span> <span class="o">=</span> <span class="p">{</span>
   <span class="s1">&#39;alpha&#39;</span><span class="p">:</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mf">0.05</span><span class="p">)</span>
<span class="p">}</span>
<span class="n">parameters_rf</span> <span class="o">=</span> <span class="p">{</span>
   <span class="s1">&#39;max_depth&#39;</span><span class="p">:</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span><span class="mi">32</span><span class="p">,</span><span class="mi">1</span><span class="p">)</span>
<span class="p">}</span>

<span class="n">parameters_ada</span> <span class="o">=</span> <span class="p">{</span>
   <span class="s1">&#39;learning_rate&#39;</span><span class="p">:</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mf">0.2</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mf">0.05</span><span class="p">)</span>
<span class="p">}</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Untuk tuning parameter kita menginstall terlebih dahulu pacakge <code>tune-sklearn</code></p>

</div>
</div>
</div>pip install tune-sklearn ray[tune]
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Medefinisikan-Fungsi-Tuning-Hyperparameter">Medefinisikan Fungsi Tuning Hyperparameter<a class="anchor-link" href="#Medefinisikan-Fungsi-Tuning-Hyperparameter">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[239]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">tune_sklearn</span> <span class="kn">import</span> <span class="n">TuneGridSearchCV</span>
<span class="n">tune_search_svc</span> <span class="o">=</span> <span class="n">TuneGridSearchCV</span><span class="p">(</span><span class="n">base_models</span><span class="p">()[</span><span class="s2">&quot;svc&quot;</span><span class="p">],</span>
                                   <span class="n">parameters_svc</span><span class="p">,</span>
                                   <span class="n">scoring</span><span class="o">=</span><span class="s2">&quot;balanced_accuracy&quot;</span><span class="p">,</span>
                                   <span class="n">cv</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span>
                                   <span class="n">max_iters</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
<span class="n">tune_search_tree</span> <span class="o">=</span> <span class="n">TuneGridSearchCV</span><span class="p">(</span><span class="n">base_models</span><span class="p">()[</span><span class="s2">&quot;tree&quot;</span><span class="p">],</span>
                                   <span class="n">parameters_tree</span><span class="p">,</span>
                                   <span class="n">scoring</span><span class="o">=</span><span class="s2">&quot;balanced_accuracy&quot;</span><span class="p">,</span>
                                   <span class="n">cv</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span>
                                   <span class="n">max_iters</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
<span class="n">tune_search_nb</span> <span class="o">=</span> <span class="n">TuneGridSearchCV</span><span class="p">(</span><span class="n">base_models</span><span class="p">()[</span><span class="s2">&quot;nb&quot;</span><span class="p">],</span>
                                   <span class="n">parameters_nb</span><span class="p">,</span>
                                   <span class="n">scoring</span><span class="o">=</span><span class="s2">&quot;balanced_accuracy&quot;</span><span class="p">,</span>
                                   <span class="n">cv</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span>
                                   <span class="n">max_iters</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
<span class="n">tune_search_rf</span> <span class="o">=</span> <span class="n">TuneGridSearchCV</span><span class="p">(</span><span class="n">base_models</span><span class="p">()[</span><span class="s2">&quot;rf&quot;</span><span class="p">],</span>
                                   <span class="n">parameters_rf</span><span class="p">,</span>
                                   <span class="n">scoring</span><span class="o">=</span><span class="s2">&quot;balanced_accuracy&quot;</span><span class="p">,</span>
                                   <span class="n">cv</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span>
                                   <span class="n">max_iters</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
<span class="n">tune_search_ada</span> <span class="o">=</span> <span class="n">TuneGridSearchCV</span><span class="p">(</span><span class="n">base_models</span><span class="p">()[</span><span class="s2">&quot;ada&quot;</span><span class="p">],</span>
                                   <span class="n">parameters_ada</span><span class="p">,</span>
                                   <span class="n">scoring</span><span class="o">=</span><span class="s2">&quot;balanced_accuracy&quot;</span><span class="p">,</span>
                                   <span class="n">cv</span><span class="o">=</span><span class="mi">5</span><span class="p">,</span>
                                   <span class="n">max_iters</span><span class="o">=</span><span class="mi">100</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Menjalankan-Tuning">Menjalankan Tuning<a class="anchor-link" href="#Menjalankan-Tuning">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Perhatian :</strong></p>
<ol>
<li><strong>Jika muncul beberapa pop up windows silahkan klik allow</strong></li>
<li><strong>Jika muncul beberapa tulisan dengan background merah dapat diabaikan</strong></li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="SVM">SVM<a class="anchor-link" href="#SVM">&#182;</a></h5>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[240]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">time</span> <span class="c1"># Just to compare fit times</span>
<span class="n">start</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="n">tune_search_svc</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">end</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Tune Fit Time:&quot;</span><span class="p">,</span> <span class="n">end</span> <span class="o">-</span> <span class="n">start</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre><span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Tune Fit Time: 254.2466835975647
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Decision-Tree">Decision Tree<a class="anchor-link" href="#Decision-Tree">&#182;</a></h5>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[241]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">time</span> <span class="c1"># Just to compare fit times</span>
<span class="n">start</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="n">tune_search_tree</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">end</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Tune Fit Time:&quot;</span><span class="p">,</span> <span class="n">end</span> <span class="o">-</span> <span class="n">start</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Tune Fit Time: 29.85234022140503
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Naive-Bayes">Naive Bayes<a class="anchor-link" href="#Naive-Bayes">&#182;</a></h5>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[242]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">time</span> <span class="c1"># Just to compare fit times</span>
<span class="n">start</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="n">tune_search_nb</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">end</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Tune Fit Time:&quot;</span><span class="p">,</span> <span class="n">end</span> <span class="o">-</span> <span class="n">start</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre><span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
<span class="ansi-cyan-fg">(pid=39600)</span> C:\ProgramData\Anaconda3\lib\site-packages\sklearn\naive_bayes.py:508: UserWarning: alpha too small will result in numeric errors, setting alpha = 1.0e-10
<span class="ansi-cyan-fg">(pid=39600)</span>   warnings.warn(&#39;alpha too small will result in numeric errors, &#39;
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Tune Fit Time: 21.74986171722412
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="Random-Forest">Random Forest<a class="anchor-link" href="#Random-Forest">&#182;</a></h5>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[243]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">time</span> <span class="c1"># Just to compare fit times</span>
<span class="n">start</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="n">tune_search_rf</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">end</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Tune Fit Time:&quot;</span><span class="p">,</span> <span class="n">end</span> <span class="o">-</span> <span class="n">start</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre><span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Tune Fit Time: 71.51042199134827
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h5 id="AdaBoost">AdaBoost<a class="anchor-link" href="#AdaBoost">&#182;</a></h5>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[244]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">time</span> <span class="c1"># Just to compare fit times</span>
<span class="n">start</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="n">tune_search_ada</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span> <span class="n">y_train</span><span class="p">)</span>
<span class="n">end</span> <span class="o">=</span> <span class="n">time</span><span class="o">.</span><span class="n">time</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Tune Fit Time:&quot;</span><span class="p">,</span> <span class="n">end</span> <span class="o">-</span> <span class="n">start</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre><span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
<span class="ansi-cyan-fg">(pid=None)</span> C:\ProgramData\Anaconda3\lib\site-packages\ray\autoscaler\_private\cli_logger.py:57: FutureWarning: Not all Ray CLI dependencies were found. In Ray 1.4+, the Ray CLI, autoscaler, and dashboard will only be usable via `pip install &#39;ray[default]&#39;`. Please update your install command.
<span class="ansi-cyan-fg">(pid=None)</span>   warnings.warn(
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Tune Fit Time: 95.98581719398499
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Menampilkan-hasil-Output-Tuning">Menampilkan hasil Output Tuning<a class="anchor-link" href="#Menampilkan-hasil-Output-Tuning">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[245]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hiperparameter terbaik untuk SVM adalah &quot;</span><span class="p">,</span><span class="n">tune_search_svc</span><span class="o">.</span><span class="n">best_params_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Niai Score Hiperparameter terbaik SVM adalah &quot;</span><span class="p">,</span><span class="n">tune_search_svc</span><span class="o">.</span><span class="n">best_score_</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Hiperparameter terbaik untuk SVM adalah  {&#39;C&#39;: 6.0}
Niai Score Hiperparameter terbaik SVM adalah  0.8088054638627243
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[246]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hiperparameter terbaik untuk Decision Tree adalah &quot;</span><span class="p">,</span><span class="n">tune_search_tree</span><span class="o">.</span><span class="n">best_params_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Niai Score Hiperparameter terbaik Decision Tree adalah &quot;</span><span class="p">,</span><span class="n">tune_search_tree</span><span class="o">.</span><span class="n">best_score_</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Hiperparameter terbaik untuk Decision Tree adalah  {&#39;min_samples_split&#39;: 0.5000000000000001}
Niai Score Hiperparameter terbaik Decision Tree adalah  0.7754178920350991
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[247]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hiperparameter terbaik untuk Naive Bayes adalah &quot;</span><span class="p">,</span><span class="n">tune_search_nb</span><span class="o">.</span><span class="n">best_params_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Niai Score Hiperparameter terbaik Naive Bayes adalah &quot;</span><span class="p">,</span><span class="n">tune_search_nb</span><span class="o">.</span><span class="n">best_score_</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Hiperparameter terbaik untuk Naive Bayes adalah  {&#39;alpha&#39;: 0.35000000000000003}
Niai Score Hiperparameter terbaik Naive Bayes adalah  0.8072619572527462
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[248]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hiperparameter terbaik untuk Random Forest adalah &quot;</span><span class="p">,</span><span class="n">tune_search_rf</span><span class="o">.</span><span class="n">best_params_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Niai Score Hiperparameter terbaik Random Forest adalah &quot;</span><span class="p">,</span><span class="n">tune_search_rf</span><span class="o">.</span><span class="n">best_score_</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Hiperparameter terbaik untuk Random Forest adalah  {&#39;max_depth&#39;: 31}
Niai Score Hiperparameter terbaik Random Forest adalah  0.6851528052957804
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[249]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hiperparameter terbaik untuk Adaboost adalah &quot;</span><span class="p">,</span><span class="n">tune_search_ada</span><span class="o">.</span><span class="n">best_params_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Niai Score Hiperparameter terbaik Adaboost adalah &quot;</span><span class="p">,</span><span class="n">tune_search_ada</span><span class="o">.</span><span class="n">best_score_</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Hiperparameter terbaik untuk Adaboost adalah  {&#39;learning_rate&#39;: 0.8999999999999999}
Niai Score Hiperparameter terbaik Adaboost adalah  0.7486714313303964
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Memandingkan-hasil-Tuning-dengan-model-lain">Memandingkan hasil Tuning dengan model lain<a class="anchor-link" href="#Memandingkan-hasil-Tuning-dengan-model-lain">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pembandingan model ini dilakukan dengan menggunakan model yang belum dituning sebelumnya. Oleh karena itu kita akan melakukan proses training terlebih dahulu.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Training-model">Training model<a class="anchor-link" href="#Training-model">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[205]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">models_name</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;svc&quot;</span><span class="p">,</span><span class="s2">&quot;tree&quot;</span><span class="p">,</span><span class="s2">&quot;nb&quot;</span><span class="p">,</span><span class="s2">&quot;knn&quot;</span><span class="p">,</span><span class="s2">&quot;ada&quot;</span><span class="p">]</span>
<span class="n">fit_model</span> <span class="o">=</span><span class="p">{}</span>
<span class="k">for</span> <span class="n">model</span> <span class="ow">in</span> <span class="n">models_name</span><span class="p">:</span>
    <span class="n">fit_model</span><span class="p">[</span><span class="n">model</span><span class="p">]</span> <span class="o">=</span> <span class="n">base_models</span><span class="p">()[</span><span class="n">model</span><span class="p">]</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">X_train</span><span class="p">,</span><span class="n">y_train</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Evaluasi-model">Evaluasi model<a class="anchor-link" href="#Evaluasi-model">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Evaluasi model ini dilakukan pada data testing. Pada tahap inilah akan dibandingkan hasil dari model sebelum dan sesudah training</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Berikut dibawah ini adalah nilai metric pada model yang belum di tuning</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[207]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">models_name</span> <span class="o">=</span> <span class="p">[</span><span class="s2">&quot;svc&quot;</span><span class="p">,</span><span class="s2">&quot;tree&quot;</span><span class="p">,</span><span class="s2">&quot;nb&quot;</span><span class="p">,</span><span class="s2">&quot;knn&quot;</span><span class="p">,</span><span class="s2">&quot;ada&quot;</span><span class="p">]</span>
<span class="n">predict_model</span> <span class="o">=</span><span class="p">{}</span>
<span class="k">for</span> <span class="n">model</span> <span class="ow">in</span> <span class="n">models_name</span><span class="p">:</span>
    <span class="n">predict_model</span><span class="p">[</span><span class="n">model</span><span class="p">]</span> <span class="o">=</span> <span class="n">fit_model</span><span class="p">[</span><span class="n">model</span><span class="p">]</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[208]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="kn">import</span> <span class="n">balanced_accuracy_score</span>
<span class="n">metric</span> <span class="o">=</span><span class="p">{}</span>
<span class="k">for</span> <span class="n">model</span> <span class="ow">in</span> <span class="n">models_name</span><span class="p">:</span>
    <span class="n">metric</span><span class="p">[</span><span class="n">model</span><span class="p">]</span> <span class="o">=</span> <span class="n">balanced_accuracy_score</span><span class="p">(</span><span class="n">predict_model</span><span class="p">[</span><span class="n">model</span><span class="p">],</span><span class="n">y_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[209]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">metric</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[209]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>{&#39;svc&#39;: 0.8299030632579856,
 &#39;tree&#39;: 0.7743840019045352,
 &#39;nb&#39;: 0.8206429211469535,
 &#39;knn&#39;: 0.623093080083335,
 &#39;ada&#39;: 0.7734328185612313}</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Sedangkan dibawah ini adalah nilai metric model yang sudah dituning</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[251]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pred_svc_tune</span> <span class="o">=</span> <span class="n">tune_search_svc</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
<span class="n">pred_tree_tune</span> <span class="o">=</span> <span class="n">tune_search_tree</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
<span class="n">pred_nb_tune</span> <span class="o">=</span> <span class="n">tune_search_nb</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
<span class="n">pred_rf_tune</span> <span class="o">=</span> <span class="n">tune_search_rf</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
<span class="n">pred_ada_tune</span> <span class="o">=</span> <span class="n">tune_search_ada</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">X_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[252]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">metric_tune</span> <span class="o">=</span> <span class="p">{}</span>
<span class="n">metric_tune</span><span class="p">[</span><span class="s2">&quot;svc&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">balanced_accuracy_score</span><span class="p">(</span><span class="n">pred_svc_tune</span><span class="p">,</span><span class="n">y_test</span><span class="p">)</span>
<span class="n">metric_tune</span><span class="p">[</span><span class="s2">&quot;tree&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">balanced_accuracy_score</span><span class="p">(</span><span class="n">pred_tree_tune</span><span class="p">,</span><span class="n">y_test</span><span class="p">)</span>
<span class="n">metric_tune</span><span class="p">[</span><span class="s2">&quot;nb&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">balanced_accuracy_score</span><span class="p">(</span><span class="n">pred_nb_tune</span><span class="p">,</span><span class="n">y_test</span><span class="p">)</span>
<span class="n">metric_tune</span><span class="p">[</span><span class="s2">&quot;rf&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">balanced_accuracy_score</span><span class="p">(</span><span class="n">pred_rf_tune</span><span class="p">,</span><span class="n">y_test</span><span class="p">)</span>
<span class="n">metric_tune</span><span class="p">[</span><span class="s2">&quot;ada&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">balanced_accuracy_score</span><span class="p">(</span><span class="n">pred_ada_tune</span><span class="p">,</span><span class="n">y_test</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[253]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">metric_tune</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[253]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>{&#39;svc&#39;: 0.829850923209152,
 &#39;tree&#39;: 0.773637837760271,
 &#39;nb&#39;: 0.807493470947561,
 &#39;rf&#39;: 0.816918885258954,
 &#39;ada&#39;: 0.7735283820720611}</pre>
</div>

</div>

</div>
</div>

</div>
    </div>
  </div>
</body>




 


</html>
