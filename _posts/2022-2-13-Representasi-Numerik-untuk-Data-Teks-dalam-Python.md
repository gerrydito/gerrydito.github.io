---
layout: post
title:  Reprenstasi Numerik untuk Data Teks dalam Python
categories: [Natural Language Processing,Text Analytics,python]
excerpt: 
---
<html>
<head><meta charset="utf-8" />

<title>Representasi_Numerik_untuk_Data_Teks_dalam_Python</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>



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
  background: #0a0502;
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
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #4f424c }
.highlight  { background: #2f1e2e; color: #e7e9db }
.highlight .c { color: #776e71 } /* Comment */
.highlight .err { color: #ef6155 } /* Error */
.highlight .k { color: #815ba4 } /* Keyword */
.highlight .l { color: #f99b15 } /* Literal */
.highlight .n { color: #e7e9db } /* Name */
.highlight .o { color: #5bc4bf } /* Operator */
.highlight .p { color: #e7e9db } /* Punctuation */
.highlight .ch { color: #776e71 } /* Comment.Hashbang */
.highlight .cm { color: #776e71 } /* Comment.Multiline */
.highlight .cp { color: #776e71 } /* Comment.Preproc */
.highlight .cpf { color: #776e71 } /* Comment.PreprocFile */
.highlight .c1 { color: #776e71 } /* Comment.Single */
.highlight .cs { color: #776e71 } /* Comment.Special */
.highlight .gd { color: #ef6155 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gh { color: #e7e9db; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #48b685 } /* Generic.Inserted */
.highlight .gp { color: #776e71; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #5bc4bf; font-weight: bold } /* Generic.Subheading */
.highlight .kc { color: #815ba4 } /* Keyword.Constant */
.highlight .kd { color: #815ba4 } /* Keyword.Declaration */
.highlight .kn { color: #5bc4bf } /* Keyword.Namespace */
.highlight .kp { color: #815ba4 } /* Keyword.Pseudo */
.highlight .kr { color: #815ba4 } /* Keyword.Reserved */
.highlight .kt { color: #fec418 } /* Keyword.Type */
.highlight .ld { color: #48b685 } /* Literal.Date */
.highlight .m { color: #f99b15 } /* Literal.Number */
.highlight .s { color: #48b685 } /* Literal.String */
.highlight .na { color: #06b6ef } /* Name.Attribute */
.highlight .nb { color: #e7e9db } /* Name.Builtin */
.highlight .nc { color: #fec418 } /* Name.Class */
.highlight .no { color: #ef6155 } /* Name.Constant */
.highlight .nd { color: #5bc4bf } /* Name.Decorator */
.highlight .ni { color: #e7e9db } /* Name.Entity */
.highlight .ne { color: #ef6155 } /* Name.Exception */
.highlight .nf { color: #06b6ef } /* Name.Function */
.highlight .nl { color: #e7e9db } /* Name.Label */
.highlight .nn { color: #fec418 } /* Name.Namespace */
.highlight .nx { color: #06b6ef } /* Name.Other */
.highlight .py { color: #e7e9db } /* Name.Property */
.highlight .nt { color: #5bc4bf } /* Name.Tag */
.highlight .nv { color: #ef6155 } /* Name.Variable */
.highlight .ow { color: #5bc4bf } /* Operator.Word */
.highlight .w { color: #e7e9db } /* Text.Whitespace */
.highlight .mb { color: #f99b15 } /* Literal.Number.Bin */
.highlight .mf { color: #f99b15 } /* Literal.Number.Float */
.highlight .mh { color: #f99b15 } /* Literal.Number.Hex */
.highlight .mi { color: #f99b15 } /* Literal.Number.Integer */
.highlight .mo { color: #f99b15 } /* Literal.Number.Oct */
.highlight .sb { color: #48b685 } /* Literal.String.Backtick */
.highlight .sc { color: #e7e9db } /* Literal.String.Char */
.highlight .sd { color: #776e71 } /* Literal.String.Doc */
.highlight .s2 { color: #48b685 } /* Literal.String.Double */
.highlight .se { color: #f99b15 } /* Literal.String.Escape */
.highlight .sh { color: #48b685 } /* Literal.String.Heredoc */
.highlight .si { color: #f99b15 } /* Literal.String.Interpol */
.highlight .sx { color: #48b685 } /* Literal.String.Other */
.highlight .sr { color: #48b685 } /* Literal.String.Regex */
.highlight .s1 { color: #48b685 } /* Literal.String.Single */
.highlight .ss { color: #48b685 } /* Literal.String.Symbol */
.highlight .bp { color: #e7e9db } /* Name.Builtin.Pseudo */
.highlight .vc { color: #ef6155 } /* Name.Variable.Class */
.highlight .vg { color: #ef6155 } /* Name.Variable.Global */
.highlight .vi { color: #ef6155 } /* Name.Variable.Instance */
.highlight .il { color: #f99b15 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">
    
/* Temporary definitions which will become obsolete with Notebook release 5.0 */
.ansi-black-fg { color: #3E424D; }
.ansi-black-bg { background-color: #3E424D; }
.ansi-black-intense-fg { color: #282C36; }
.ansi-black-intense-bg { background-color: #282C36; }
.ansi-red-fg { color: #E75C58; }
.ansi-red-bg { background-color: #E75C58; }
.ansi-red-intense-fg { color: #B22B31; }
.ansi-red-intense-bg { background-color: #B22B31; }
.ansi-green-fg { color: #00A250; }
.ansi-green-bg { background-color: #00A250; }
.ansi-green-intense-fg { color: #007427; }
.ansi-green-intense-bg { background-color: #007427; }
.ansi-yellow-fg { color: #DDB62B; }
.ansi-yellow-bg { background-color: #DDB62B; }
.ansi-yellow-intense-fg { color: #B27D12; }
.ansi-yellow-intense-bg { background-color: #B27D12; }
.ansi-blue-fg { color: #208FFB; }
.ansi-blue-bg { background-color: #208FFB; }
.ansi-blue-intense-fg { color: #0065CA; }
.ansi-blue-intense-bg { background-color: #0065CA; }
.ansi-magenta-fg { color: #D160C4; }
.ansi-magenta-bg { background-color: #D160C4; }
.ansi-magenta-intense-fg { color: #A03196; }
.ansi-magenta-intense-bg { background-color: #A03196; }
.ansi-cyan-fg { color: #60C6C8; }
.ansi-cyan-bg { background-color: #60C6C8; }
.ansi-cyan-intense-fg { color: #258F8F; }
.ansi-cyan-intense-bg { background-color: #258F8F; }
.ansi-white-fg { color: #C5C1B4; }
.ansi-white-bg { background-color: #C5C1B4; }
.ansi-white-intense-fg { color: #A1A6B2; }
.ansi-white-intense-bg { background-color: #A1A6B2; }

.ansi-bold { font-weight: bold; }

    </style>


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

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
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
<h2 id="Vector-Space-Model-(VSM).">Vector Space Model (VSM).<a class="anchor-link" href="#Vector-Space-Model-(VSM).">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Vector Space Model merupakan model matematika untuk merepresentasikan dokumen teks sebagai vektor pengidentifikasi (seperti index term)</p>
<p>Ide dasar representasi teks: petakan setiap kata dalam Vocabulary (Term Vector) dari korpus teks ke ID unik (nilai integer),kemudian representasikan setiap kalimat atau dokumen dalam korpus sebagai vektor n-dimensi.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Representasi-Dokumen/Teks"><center><font color="black">Representasi Dokumen/Teks</font></center><a class="anchor-link" href="#Representasi-Dokumen/Teks">&#182;</a></h1><p><img alt="" src="https://github.com/taudata-indonesia/eLearning/blob/master/images/3_Bentuk%20umum%20representasi%20dokumen.JPG?raw=1" style="height: 294px ; width: 620px" /></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Metode-Vektorisasi-Dasar">Metode Vektorisasi Dasar<a class="anchor-link" href="#Metode-Vektorisasi-Dasar">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Data-Berita-Kecelakaan-Indonesia">Data Berita Kecelakaan Indonesia<a class="anchor-link" href="#Data-Berita-Kecelakaan-Indonesia">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Dengan meningkatnya jumlah kecelakaan di Indonesia, analisis data kecelakaan masih perlu diperhatikan dan dianalisis. Apalagi informasi kecelakaan lalu lintas dari media sosial seperti Twitter lebih mudah didapat jika dibandingkan dengan sumber data lain dari kepolisian atau instansi pemerintah.</p>
<p><strong>Acknowledge</strong></p>
<p>Saputro, D. A., &amp; Girsang, A. S. (2020). Classification of Traffic Accident Information Using Machine Learning from Social Media. International Journal of Emerging Trends in Engineering Research, 8(3), 630–637. <a href="https://doi.org/10.30534/ijeter/2020/04832020">https://doi.org/10.30534/ijeter/2020/04832020</a></p>
<p><strong>Download</strong></p>
<p><a href="https://drive.google.com/file/d/1r9M3Tm_CLF4P1w4D7cJJpelzHr0GgSfd/view?usp=sharing">Download Disini</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="kn">as</span> <span class="nn">pd</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">teks_data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;/content/drive/MyDrive/Data Text Analytics/Twitter accident indo/twitter_accident_indo_text_only.csv&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">teks_data</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">

  <div id="df-90ada051-651b-4cdb-b8d7-63595a89a6a5">
    <div class="colab-df-container">
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
      <th>full_text</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Rekaman CCTV Kecelakaan Motor di PIK, depan Ta...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tewaskan 346 Orang dalam 2 Kecelakaan, Boss Bo...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Anggota parlemen Taiwan juga berencana meningk...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C.Gerakan.bicara pertolongan pertama pada kece...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Asuransi mana nih??\n\nhttps://t.co/AJyABmimcY...</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-90ada051-651b-4cdb-b8d7-63595a89a6a5')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">
        
  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>
      
  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-90ada051-651b-4cdb-b8d7-63595a89a6a5 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-90ada051-651b-4cdb-b8d7-63595a89a6a5');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>
  
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">teks_data</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[4]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(1002, 1)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">def</span> <span class="nf">print_text_in_df</span><span class="p">(</span><span class="n">doc</span><span class="p">):</span>
  <span class="k">for</span> <span class="n">row</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="n">doc</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]):</span>
    <span class="k">print</span><span class="p">(</span><span class="n">doc</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="n">row</span><span class="p">,</span><span class="mi">0</span><span class="p">],</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">print_text_in_df</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Rekaman CCTV Kecelakaan Motor di PIK, depan Taman Grisenda :
https://t.co/gMHLep9IvZ mhmmdrhmtrmdhn
Visit Wonderful  #MRahmatRamadhan 


Tewaskan 346 Orang dalam 2 Kecelakaan, Boss Boeing Minta Maaf https://t.co/wLRhFy8oYE 


Anggota parlemen Taiwan juga berencana meningkatkan denda maksimum dan masa hukuman bagi orang yang menyetir dalam keadaan mabuk. https://t.co/GSWqziaKDN 


C.Gerakan.bicara pertolongan pertama pada kecelakaan (P3K-BAKAT) https://t.co/jlPyXK3EBV 


Asuransi mana nih??

https://t.co/AJyABmimcY

PPATK tidak memberikan rincian secara pasti siapa dan darimana asal partai caleg tersebut. Saat ini, pihaknya telah... https://t.co/AJyABmimcY 


</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Text-Preprocessing">Text Preprocessing<a class="anchor-link" href="#Text-Preprocessing">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="err">!</span> <span class="n">pip</span> <span class="n">install</span> <span class="n">Pysastrawi</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Collecting Pysastrawi
  Downloading PySastrawi-1.2.0-py2.py3-none-any.whl (210 kB)
     |████████████████████████████████| 210 kB 26.1 MB/s 
Installing collected packages: Pysastrawi
Successfully installed Pysastrawi-1.2.0
</pre>
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
<div class=" highlight hl-python"><pre><span></span><span class="kn">import</span> <span class="nn">re</span>
<span class="kn">import</span> <span class="nn">string</span>
<span class="kn">from</span> <span class="nn">spacy.lang.id</span> <span class="kn">import</span> <span class="n">Indonesian</span>
<span class="kn">from</span> <span class="nn">spacy.lang.id.stop_words</span> <span class="kn">import</span> <span class="n">STOP_WORDS</span>
<span class="kn">import</span> <span class="nn">spacy</span>
<span class="n">nlp</span> <span class="o">=</span> <span class="n">Indonesian</span><span class="p">()</span>
<span class="kn">from</span> <span class="nn">Sastrawi.Stemmer.StemmerFactory</span> <span class="kn">import</span> <span class="n">StemmerFactory</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>import kamus bahasa baku</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">indo_slang_word</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;https://raw.githubusercontent.com/nasalsabila/kamus-alay/master/colloquial-indonesian-lexicon.csv&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Mendefinisikan fungsi text preprocessing dengan menampilkan setiap langkahnya</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">def</span> <span class="nf">my_tokenizer_print</span><span class="p">(</span><span class="n">doc</span><span class="p">):</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;menghapus url</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">doc1</span> <span class="o">=</span> <span class="n">re</span><span class="o">.</span><span class="n">sub</span><span class="p">(</span><span class="s2">r&quot;https\S+&quot;</span><span class="p">,</span> <span class="s2">&quot;&quot;</span><span class="p">,</span><span class="n">doc</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc1</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;punctuation removal+menghapus angka</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">doc2</span> <span class="o">=</span> <span class="n">doc1</span><span class="o">.</span><span class="n">translate</span><span class="p">(</span><span class="nb">str</span><span class="o">.</span><span class="n">maketrans</span><span class="p">(</span><span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="n">string</span><span class="o">.</span><span class="n">punctuation</span> <span class="o">+</span> <span class="n">string</span><span class="o">.</span><span class="n">digits</span><span class="p">))</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc2</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;whitespace removal</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">doc3</span> <span class="o">=</span> <span class="n">doc2</span><span class="o">.</span><span class="n">strip</span><span class="p">()</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc3</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;word tokenization</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">doc4</span> <span class="o">=</span> <span class="n">nlp</span><span class="p">(</span><span class="n">doc3</span><span class="p">)</span>
  <span class="n">doc_token1</span> <span class="o">=</span> <span class="p">[</span><span class="n">token</span><span class="o">.</span><span class="n">text</span> <span class="k">for</span> <span class="n">token</span> <span class="ow">in</span> <span class="n">doc4</span><span class="p">]</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc_token1</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;Text Normalization/Noise Removal</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">for</span> <span class="n">index</span> <span class="ow">in</span>  <span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="nb">len</span><span class="p">(</span><span class="n">doc_token1</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">):</span>
        <span class="n">index_slang</span> <span class="o">=</span> <span class="n">indo_slang_word</span><span class="o">.</span><span class="n">slang</span><span class="o">==</span><span class="n">doc_token1</span><span class="p">[</span><span class="n">index</span><span class="p">]</span>
        <span class="n">formal</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">set</span><span class="p">(</span><span class="n">indo_slang_word</span><span class="p">[</span><span class="n">index_slang</span><span class="p">]</span><span class="o">.</span><span class="n">formal</span><span class="p">))</span>
        <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">formal</span><span class="p">)</span><span class="o">==</span><span class="mi">1</span><span class="p">:</span>
            <span class="n">doc_token1</span><span class="p">[</span><span class="n">index</span><span class="p">]</span><span class="o">=</span><span class="n">formal</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> 
  <span class="k">print</span><span class="p">(</span><span class="n">doc_token1</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;Stopwords Removal</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">doc_token2</span> <span class="o">=</span> <span class="p">[</span><span class="n">word</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">doc_token1</span> <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">STOP_WORDS</span><span class="p">]</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc_token2</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;Stemming/Lemmatization</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">factory</span> <span class="o">=</span> <span class="n">StemmerFactory</span><span class="p">()</span>
  <span class="n">stemmer</span> <span class="o">=</span> <span class="n">factory</span><span class="o">.</span><span class="n">create_stemmer</span><span class="p">()</span>
  <span class="n">doc_token3</span> <span class="o">=</span> <span class="p">[</span><span class="n">stemmer</span><span class="o">.</span><span class="n">stem</span><span class="p">(</span><span class="n">word</span><span class="p">)</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">doc_token2</span><span class="p">]</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc_token3</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="k">print</span><span class="p">(</span><span class="s2">&quot;menghapus spasi pada list</span><span class="se">\n</span><span class="s2">&quot;</span><span class="p">)</span>
  <span class="n">doc_token4</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">filter</span><span class="p">(</span><span class="k">lambda</span> <span class="n">word</span><span class="p">:</span> <span class="n">word</span> <span class="o">!=</span> <span class="s2">&quot;&quot;</span><span class="p">,</span> <span class="n">doc_token3</span><span class="p">))</span>
  <span class="k">print</span><span class="p">(</span><span class="n">doc_token4</span><span class="p">,</span><span class="s2">&quot;</span><span class="se">\n\n</span><span class="s2">&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>uji coba fungsi text preprocessing</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">my_tokenizer_print</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">0</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>menghapus url

Rekaman CCTV Kecelakaan Motor di PIK, depan Taman Grisenda :
 mhmmdrhmtrmdhn
Visit Wonderful  #MRahmatRamadhan 


punctuation removal+menghapus angka

Rekaman CCTV Kecelakaan Motor di PIK depan Taman Grisenda 
 mhmmdrhmtrmdhn
Visit Wonderful  MRahmatRamadhan 


whitespace removal

Rekaman CCTV Kecelakaan Motor di PIK depan Taman Grisenda 
 mhmmdrhmtrmdhn
Visit Wonderful  MRahmatRamadhan 


word tokenization

[&#39;Rekaman&#39;, &#39;CCTV&#39;, &#39;Kecelakaan&#39;, &#39;Motor&#39;, &#39;di&#39;, &#39;PIK&#39;, &#39;depan&#39;, &#39;Taman&#39;, &#39;Grisenda&#39;, &#39;\n &#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;\n&#39;, &#39;Visit&#39;, &#39;Wonderful&#39;, &#39; &#39;, &#39;MRahmatRamadhan&#39;] 


Text Normalization/Noise Removal

[&#39;Rekaman&#39;, &#39;CCTV&#39;, &#39;Kecelakaan&#39;, &#39;Motor&#39;, &#39;di&#39;, &#39;PIK&#39;, &#39;depan&#39;, &#39;Taman&#39;, &#39;Grisenda&#39;, &#39;\n &#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;\n&#39;, &#39;Visit&#39;, &#39;Wonderful&#39;, &#39; &#39;, &#39;MRahmatRamadhan&#39;] 


Stopwords Removal

[&#39;Rekaman&#39;, &#39;CCTV&#39;, &#39;Kecelakaan&#39;, &#39;Motor&#39;, &#39;PIK&#39;, &#39;Taman&#39;, &#39;Grisenda&#39;, &#39;\n &#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;\n&#39;, &#39;Visit&#39;, &#39;Wonderful&#39;, &#39; &#39;, &#39;MRahmatRamadhan&#39;] 


Stemming/Lemmatization

[&#39;rekam&#39;, &#39;cctv&#39;, &#39;celaka&#39;, &#39;motor&#39;, &#39;pik&#39;, &#39;taman&#39;, &#39;grisenda&#39;, &#39;&#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;&#39;, &#39;visit&#39;, &#39;wonderful&#39;, &#39;&#39;, &#39;mrahmatramadhan&#39;] 


menghapus spasi pada list

[&#39;rekam&#39;, &#39;cctv&#39;, &#39;celaka&#39;, &#39;motor&#39;, &#39;pik&#39;, &#39;taman&#39;, &#39;grisenda&#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;visit&#39;, &#39;wonderful&#39;, &#39;mrahmatramadhan&#39;] 


</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>medefinisikan fungsi text preprocessing fixed</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">def</span> <span class="nf">my_tokenizer</span><span class="p">(</span><span class="n">doc</span><span class="p">):</span>
  <span class="c1">#menghapus url</span>
  <span class="n">doc1</span> <span class="o">=</span> <span class="n">re</span><span class="o">.</span><span class="n">sub</span><span class="p">(</span><span class="s2">r&quot;https\S+&quot;</span><span class="p">,</span> <span class="s2">&quot;&quot;</span><span class="p">,</span><span class="n">doc</span><span class="p">)</span>
  <span class="c1"># punctuation removal+menghapus angka</span>
  <span class="n">doc2</span> <span class="o">=</span> <span class="n">doc1</span><span class="o">.</span><span class="n">translate</span><span class="p">(</span><span class="nb">str</span><span class="o">.</span><span class="n">maketrans</span><span class="p">(</span><span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="s1">&#39;&#39;</span><span class="p">,</span> <span class="n">string</span><span class="o">.</span><span class="n">punctuation</span> <span class="o">+</span> <span class="n">string</span><span class="o">.</span><span class="n">digits</span><span class="p">))</span>
  <span class="c1"># whitespace removal</span>
  <span class="n">doc3</span> <span class="o">=</span> <span class="n">doc2</span><span class="o">.</span><span class="n">strip</span><span class="p">()</span>
  <span class="c1"># word tokenization</span>
  <span class="n">doc4</span> <span class="o">=</span> <span class="n">nlp</span><span class="p">(</span><span class="n">doc3</span><span class="p">)</span>
  <span class="n">doc_token1</span> <span class="o">=</span> <span class="p">[</span><span class="n">token</span><span class="o">.</span><span class="n">text</span> <span class="k">for</span> <span class="n">token</span> <span class="ow">in</span> <span class="n">doc4</span><span class="p">]</span>
  <span class="c1"># Text Normalization/Noise Removal]</span>
  <span class="k">for</span> <span class="n">index</span> <span class="ow">in</span>  <span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="nb">len</span><span class="p">(</span><span class="n">doc_token1</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">):</span>
        <span class="n">index_slang</span> <span class="o">=</span> <span class="n">indo_slang_word</span><span class="o">.</span><span class="n">slang</span><span class="o">==</span><span class="n">doc_token1</span><span class="p">[</span><span class="n">index</span><span class="p">]</span>
        <span class="n">formal</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">set</span><span class="p">(</span><span class="n">indo_slang_word</span><span class="p">[</span><span class="n">index_slang</span><span class="p">]</span><span class="o">.</span><span class="n">formal</span><span class="p">))</span>
        <span class="k">if</span> <span class="nb">len</span><span class="p">(</span><span class="n">formal</span><span class="p">)</span><span class="o">==</span><span class="mi">1</span><span class="p">:</span>
            <span class="n">doc_token1</span><span class="p">[</span><span class="n">index</span><span class="p">]</span><span class="o">=</span><span class="n">formal</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span> 
  <span class="c1">#Stopwords Removal</span>
  <span class="n">doc_token2</span> <span class="o">=</span> <span class="p">[</span><span class="n">word</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">doc_token1</span> <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">STOP_WORDS</span><span class="p">]</span>
  <span class="c1">#Stemming/Lemmatization</span>
  <span class="n">factory</span> <span class="o">=</span> <span class="n">StemmerFactory</span><span class="p">()</span>
  <span class="n">stemmer</span> <span class="o">=</span> <span class="n">factory</span><span class="o">.</span><span class="n">create_stemmer</span><span class="p">()</span>
  <span class="n">doc_token3</span> <span class="o">=</span> <span class="p">[</span><span class="n">stemmer</span><span class="o">.</span><span class="n">stem</span><span class="p">(</span><span class="n">word</span><span class="p">)</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">doc_token2</span><span class="p">]</span>
  <span class="c1"># menghapus spasi pada list</span>
  <span class="n">doc_token4</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="nb">filter</span><span class="p">(</span><span class="k">lambda</span> <span class="n">word</span><span class="p">:</span> <span class="n">word</span> <span class="o">!=</span> <span class="s2">&quot;&quot;</span><span class="p">,</span> <span class="n">doc_token3</span><span class="p">))</span>
  <span class="k">return</span> <span class="n">doc_token4</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="n">my_tokenizer</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">iloc</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span><span class="mi">0</span><span class="p">]))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[&#39;rekam&#39;, &#39;cctv&#39;, &#39;celaka&#39;, &#39;motor&#39;, &#39;pik&#39;, &#39;taman&#39;, &#39;grisenda&#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;visit&#39;, &#39;wonderful&#39;, &#39;mrahmatramadhan&#39;]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Bag-of-Word">Bag of Word<a class="anchor-link" href="#Bag-of-Word">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>Bag of words (BoW)</strong> adalah teknik representasi teks klasik yang umum digunakan dalam NLP, terutama dalam masalah klasifikasi teks. Ide utamanya adalah merepresentasikan teks sebagai <strong>bag</strong> (kumpulan) kata-kata dengan <strong>mengabaikan urutan</strong> dan <strong>konteksnya</strong>. Intuisi di baliknya adalah asumsi bahwa teks yang termasuk dalam <strong>kelas tertentu</strong> dalam kumpulan data dicirikan oleh <strong>kumpulan kata yang unik</strong>. Jika dua dokumen memiliki kata-kata yang hampir sama, maka mereka termasuk dalam <strong>bag (kelas)</strong> yang sama. Jadi, dengan menganalisis kata-kata yang ada dalam sepotong teks, seseorang dapat mengidentifikasi <strong>kelas (bag)</strong> yang dimilikinya.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kelemahan Bag of words:</p>
<ul>
<li><p>Ukuran vektor meningkat dengan ukuran vocabulary. Dengan demikian, sparity terus menjadi masalah. Salah satu cara untuk mengontrolnya adalah dengan membatasi kosakata menjadi n jumlah kata yang paling sering.</p>
</li>
<li><p>Representasi ini tidak menangkap kesamaan antara kata-kata yang berbeda padahal berarti hal yang sama. Misalkan: "I run", "I ran"</p>
</li>
<li><p>Representasi ini tidak memiliki cara untuk menangani kata-kata yang keluar dari kosakata (yaitu, kata-kata baru yang tidak terlihat dalam korpus yang digunakan untuk membangun vectorizer).</p>
</li>
<li><p>Seperti namanya, ini adalah "bag" kata - informasi urutan kata hilang dalam representasi ini.</p>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Binary-Vectorizer">Binary Vectorizer<a class="anchor-link" href="#Binary-Vectorizer">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Terkadang, kita tidak ingin merepresentasikan kata dengan <strong>frekuensi</strong> kemunculan kata dalam teks dan kita hanya ingin merepresentasikan apakah sebuah kata <strong>ada dalam teks</strong> atau <strong>tidak</strong>. Para peneliti telah menunjukkan bahwa representasi seperti itu tanpa mempertimbangkan frekuensi berguna untuk <strong>analisis sentimen</strong>. Dalam kasus seperti itu, kami hanya menginisialisasi <code>CountVectorizer</code> dengan <code>binary = True</code></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.feature_extraction.text</span> <span class="kn">import</span> <span class="n">CountVectorizer</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">binary_vect0</span> <span class="o">=</span> <span class="n">CountVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">,</span><span class="n">binary</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">X_train_binary0</span> <span class="o">=</span> <span class="n">binary_vect0</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">([</span><span class="s2">&quot;Lagu Indonesia Raya merupakan lagu kebangsaan negara Indonesia&quot;</span><span class="p">,</span>
                                              <span class="s2">&quot;Lagu ini sangat jelek&quot;</span><span class="p">])</span>
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
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="n">binary_vect0</span><span class="o">.</span><span class="n">vocabulary_</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_binary0</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_binary0</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>{&#39;lagu&#39;: 3, &#39;indonesia&#39;: 1, &#39;raya&#39;: 5, &#39;bangsa&#39;: 0, &#39;negara&#39;: 4, &#39;jelek&#39;: 2}
[[1 1 0 1 1 1]
 [0 0 1 1 0 0]]
Banyaknya document x banyaknya vocabulary
(2, 6)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">onehot_vect</span> <span class="o">=</span> <span class="n">CountVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">,</span><span class="n">binary</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">X_train_onehot</span> <span class="o">=</span> <span class="n">onehot_vect</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">full_text</span><span class="p">)</span>
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
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">onehot_vect</span><span class="o">.</span><span class="n">vocabulary_</span><span class="o">.</span><span class="n">items</span><span class="p">())[</span><span class="mi">0</span><span class="p">:</span><span class="mi">3</span><span class="p">])</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_onehot</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Memeriksa nilai dari beberapa vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_onehot</span><span class="o">.</span><span class="n">toarray</span><span class="p">()[</span><span class="mi">0</span><span class="p">,[</span><span class="mi">2869</span><span class="p">,</span><span class="mi">575</span><span class="p">,</span><span class="mi">584</span><span class="p">]])</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_onehot</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[(&#39;rekam&#39;, 2869), (&#39;cctv&#39;, 575), (&#39;celaka&#39;, 584)]
[[0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 ...
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]]
Memeriksa nilai dari beberapa vocabulary
[1 1 1]
Banyaknya document x banyaknya vocabulary
(1002, 3877)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[57]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">pd</span><span class="o">.</span><span class="n">options</span><span class="o">.</span><span class="n">plotting</span><span class="o">.</span><span class="n">backend</span> <span class="o">=</span> <span class="s2">&quot;plotly&quot;</span>
<span class="k">def</span> <span class="nf">doc_plot</span><span class="p">(</span><span class="n">bow</span><span class="p">,</span><span class="n">vectorizer</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span><span class="n">desc</span><span class="o">=</span><span class="bp">True</span><span class="p">):</span>
  <span class="n">feature_names</span> <span class="o">=</span> <span class="n">vectorizer</span><span class="o">.</span><span class="n">get_feature_names_out</span><span class="p">()</span>
  <span class="n">bow_result_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">bow</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
  <span class="n">bow_result_df</span> <span class="o">=</span> <span class="n">bow_result_df</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">to_frame</span><span class="p">(</span><span class="n">name</span><span class="o">=</span><span class="s2">&quot;BoW&quot;</span><span class="p">)</span>
  <span class="n">bow_result_df</span><span class="p">[</span><span class="s2">&quot;feature_names&quot;</span><span class="p">]</span> <span class="o">=</span> <span class="n">feature_names</span>
  <span class="k">if</span><span class="p">(</span><span class="n">desc</span><span class="p">):</span>
    <span class="n">fig1</span> <span class="o">=</span> <span class="n">bow_result_df</span><span class="o">.</span><span class="n">nlargest</span><span class="p">(</span><span class="n">n</span><span class="p">,</span><span class="s2">&quot;BoW&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">plot</span><span class="o">.</span><span class="n">barh</span><span class="p">(</span><span class="n">y</span><span class="o">=</span><span class="s2">&quot;feature_names&quot;</span><span class="p">,</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;BoW&quot;</span><span class="p">,</span><span class="n">text</span><span class="o">=</span><span class="s2">&quot;BoW&quot;</span><span class="p">,</span><span class="n">text_auto</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
  <span class="k">else</span><span class="p">:</span>
    <span class="n">fig1</span> <span class="o">=</span> <span class="n">bow_result_df</span><span class="o">.</span><span class="n">nsmallest</span><span class="p">(</span><span class="n">n</span><span class="p">,</span><span class="s2">&quot;BoW&quot;</span><span class="p">)</span><span class="o">.</span><span class="n">plot</span><span class="o">.</span><span class="n">barh</span><span class="p">(</span><span class="n">y</span><span class="o">=</span><span class="s2">&quot;feature_names&quot;</span><span class="p">,</span><span class="n">x</span><span class="o">=</span><span class="s2">&quot;BoW&quot;</span><span class="p">,</span><span class="n">text</span><span class="o">=</span><span class="s2">&quot;BoW&quot;</span><span class="p">,</span><span class="n">text_auto</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
  <span class="n">fig1</span><span class="o">.</span><span class="n">update_traces</span><span class="p">(</span><span class="n">marker_color</span><span class="o">=</span><span class="s1">&#39;darkblue&#39;</span><span class="p">)</span>
  <span class="n">fig1</span><span class="o">.</span><span class="n">update_layout</span><span class="p">(</span><span class="n">yaxis</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;categoryorder&#39;</span><span class="p">:</span><span class="s1">&#39;total ascending&#39;</span><span class="p">})</span>
  <span class="n">fig1</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>plot interactive</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_onehot</span><span class="p">,</span><span class="n">onehot_vect</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>plot static</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[60]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(1).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[60]:</div>




<div class="output_png output_subarea output_execute_result">
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
<h4 id="Frequency-Vectorizer">Frequency Vectorizer<a class="anchor-link" href="#Frequency-Vectorizer">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[59]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">count_vect0</span> <span class="o">=</span> <span class="n">CountVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">X_train_counts0</span> <span class="o">=</span> <span class="n">count_vect0</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">([</span><span class="s2">&quot;Lagu Indonesia Raya merupakan lagu kebangsaan negara Indonesia&quot;</span><span class="p">,</span>
                                              <span class="s2">&quot;Lagu ini sangat jelek&quot;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[61]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="n">count_vect0</span><span class="o">.</span><span class="n">vocabulary_</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_counts0</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_counts0</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>{&#39;lagu&#39;: 3, &#39;indonesia&#39;: 1, &#39;raya&#39;: 5, &#39;bangsa&#39;: 0, &#39;negara&#39;: 4, &#39;jelek&#39;: 2}
[[1 2 0 2 1 1]
 [0 0 1 1 0 0]]
Banyaknya document x banyaknya vocabulary
(2, 6)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[62]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">count_vect</span> <span class="o">=</span> <span class="n">CountVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">X_train_counts</span> <span class="o">=</span> <span class="n">count_vect</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">full_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[63]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">count_vect</span><span class="o">.</span><span class="n">vocabulary_</span><span class="o">.</span><span class="n">items</span><span class="p">())[</span><span class="mi">0</span><span class="p">:</span><span class="mi">3</span><span class="p">])</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_counts</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Memeriksa nilai dari beberapa vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_counts</span><span class="o">.</span><span class="n">toarray</span><span class="p">()[</span><span class="mi">0</span><span class="p">,[</span><span class="mi">2869</span><span class="p">,</span><span class="mi">575</span><span class="p">,</span><span class="mi">584</span><span class="p">]])</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_counts</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[(&#39;rekam&#39;, 2869), (&#39;cctv&#39;, 575), (&#39;celaka&#39;, 584)]
[[0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 ...
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]]
Memeriksa nilai dari beberapa vocabulary
[1 1 1]
Banyaknya document x banyaknya vocabulary
(1002, 3877)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_counts</span><span class="p">,</span><span class="n">count_vect</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[80]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(2).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[80]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_counts</span><span class="p">,</span><span class="n">count_vect</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span><span class="n">desc</span><span class="o">=</span><span class="bp">False</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[81]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(3).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[81]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[66]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">count_vect</span><span class="o">.</span><span class="n">inverse_transform</span><span class="p">(</span><span class="n">X_train_counts</span><span class="o">.</span><span class="n">toarray</span><span class="p">()[</span><span class="mi">0</span><span class="p">:</span><span class="mi">6</span><span class="p">,:])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[66]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>[array([&#39;cctv&#39;, &#39;celaka&#39;, &#39;grisenda&#39;, &#39;mhmmdrhmtrmdhn&#39;, &#39;motor&#39;,
        &#39;mrahmatramadhan&#39;, &#39;pik&#39;, &#39;rekam&#39;, &#39;taman&#39;, &#39;visit&#39;, &#39;wonderful&#39;],
       dtype=&#39;&lt;U56&#39;),
 array([&#39;boeing&#39;, &#39;bos&#39;, &#39;celaka&#39;, &#39;maaf&#39;, &#39;orang&#39;, &#39;tewas&#39;], dtype=&#39;&lt;U56&#39;),
 array([&#39;anggota&#39;, &#39;denda&#39;, &#39;hukum&#39;, &#39;mabuk&#39;, &#39;maksimum&#39;, &#39;orang&#39;,
        &#39;parlemen&#39;, &#39;rencana&#39;, &#39;setir&#39;, &#39;taiwan&#39;, &#39;tingkat&#39;], dtype=&#39;&lt;U56&#39;),
 array([&#39;celaka&#39;, &#39;cgerakanbicara&#39;, &#39;pkbakat&#39;, &#39;tolong&#39;], dtype=&#39;&lt;U56&#39;),
 array([&#39;asuransi&#39;, &#39;caleg&#39;, &#39;darimana&#39;, &#39;nih&#39;, &#39;partai&#39;, &#39;ppatk&#39;,
        &#39;rincian&#39;], dtype=&#39;&lt;U56&#39;),
 array([&#39;arah&#39;, &#39;bahu&#39;, &#39;bitung&#39;, &#39;celaka&#39;, &#39;fuso&#39;, &#39;jalan&#39;, &#39;kendara&#39;,
        &#39;km&#39;, &#39;kuncir&#39;, &#39;padat&#39;, &#39;ptjasamarga&#39;, &#39;tangan&#39;, &#39;truk&#39;],
       dtype=&#39;&lt;U56&#39;)]</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Mengurangi-Vocabulary">Mengurangi Vocabulary<a class="anchor-link" href="#Mengurangi-Vocabulary">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Kita bisa mengurangi vocabulary yang kita gunakan dengan memanfaatkan parameter pada <code>CountVectorizer</code> yaitu</p>
<ul>
<li><code>max_df</code>: digunakan untuk menghapus kata yang terlalu sering muncul<ul>
<li><code>max_df = 0.50</code> berarti "hapus kata yang muncul di lebih dari 50% dokumen".</li>
<li><code>max_df = 25</code> berarti "hapus kata yang muncul di lebih dari 25 dokumen".</li>
<li>Nilai default <code>max_df</code> adalah 1.0, yang berarti "hapus kata yang muncul di lebih dari 100% dokumen". Dengan demikian, nilai default tidak menghapus kata apa pun.</li>
</ul>
</li>
<li><p><code>min_df</code>: digunakan untuk menghapus kata yang terlalu jarang muncul.</p>
<ul>
<li><code>min_df = 0,01</code> berarti "hapus kata yang muncul di kurang dari 1% dokumen".</li>
<li><code>min_df = 5</code> berarti "hapus kata yang muncul di kurang dari 5 dokumen".</li>
<li>Nilai default <code>min_df</code> adalah 1, yang berarti "hapus kata yang muncul di kurang dari 1 dokumen". Dengan demikian, nilai default tidak mengabaikan kata apa pun.</li>
</ul>
</li>
<li><p><code>max_features</code>:memilih sebanyak n vocabulary teratas yang diurutkan berdasarkan frekuensi istilah di seluruh korpus.</p>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[67]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">count_vect2</span> <span class="o">=</span> <span class="n">CountVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">,</span><span class="n">min_df</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">X_train_counts2</span> <span class="o">=</span> <span class="n">count_vect2</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">full_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[68]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="n">X_train_counts2</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_counts2</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 ...
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 0 0]
 [0 0 0 ... 0 4 0]]
Banyaknya document x banyaknya vocabulary
(1002, 443)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_counts2</span><span class="p">,</span><span class="n">count_vect2</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span><span class="n">desc</span><span class="o">=</span><span class="bp">False</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[82]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(4).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[82]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAtgAAAINCAYAAAAEIAiZAAAAAXNSR0IArs4c6QAAIABJREFUeF7t3X18VNW97/FfMjCZAAFCitT4gOW0immR6jmIp9SHxlQ8WC4W5aEiqSCiQq1VkadWbostBBCshwIKEa0YC6blVikc7Q3UaukFOWpReah6UFBSQ6UBAmRISLivtXWmMyHJPGTW3mtlPvlHQvZe67ffv53wzXLNnoxTp06dEj4QQAABBBBAAAEEEEAgJQIZBOyUODIIAggggAACCCCAAAKOAAGbGwEBBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggggAACCCCAAAGbewABBBBAAAEEEEAAgRQKELBTiMlQCCCAAAIIIIAAAggQsLkHEEAAAQQQQAABBBBIoQABO4WYDIUAAggg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
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
<h3 id="Term-frequency&#8211;-Inverse-Document-Frequency-(TF-IDF)">Term frequency&#8211; Inverse Document Frequency (TF-IDF)<a class="anchor-link" href="#Term-frequency&#8211;-Inverse-Document-Frequency-(TF-IDF)">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Pada Bag of Words, semua kata dalam teks diperlakukan sama pentingnya (tidak ada anggapan bahwa beberapa kata dalam dokumen lebih penting daripada yang lain). TF-IDF dapat menyelesaikan masalah ini. TF-IDF bertujuan untuk mengukur pentingnya suatu kata yang diberikan relatif terhadap kata-kata lain dalam dokumen dan dalam korpus(data).</p>
<p>Intuisi di balik TF-IDF adalah sebagai berikut: jika kata <strong>cinta</strong> muncul berkali-kali dalam <strong>dokumen A</strong> tetapi tidak banyak muncul di <strong>dokumen lainnya</strong> di <strong>corpus(data)</strong>, maka kata <strong>cinta</strong> tersebut pasti sangat penting untuk <strong>dokumen A</strong>. Pentingnya kata <strong>cinta</strong> meningkat sebanding dengan frekuensinya di <strong>dokumen A</strong>, tetapi pada saat yang sama, tingkat pentingnya <strong>berkurang</strong> secara proporsional dengan frekuensi kata dalam <strong>dokumen lain</strong> di corpus. Secara matematis, ini ditangkap menggunakan dua besaran: <strong>TF (Term Frequency)</strong> dan <strong>IDF (Inverse Document Frequency)</strong>. Keduanya kemudian digabungkan menjadi <strong>TF-IDF</strong>.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>TF mengukur seberapa sering kata muncul dalam dokumen tertentu.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
 \text{TF}(t,d) = \frac{\text{Banyaknya kata } t \text{ yang muncul pada dokumen d} }{\text{Total Banyaknya kata pada dokumen } d}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>IDF mengukur pentingnya istilah di seluruh corpus.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$
 \text{IDF}(t) = \log{\left(\frac{ \text{Total Banyaknya dokumen pada corpus(data)} }{ \text{Banyaknya dokumen dengan kata } t \text{ di dalamnya} }\right)}
$$
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
$$ \text{TF-IDF}(t,d) = \text{TF}(t,d) \times \text{IDF}(t)$$
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[70]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.feature_extraction.text</span> <span class="kn">import</span> <span class="n">TfidfVectorizer</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[71]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">tf_idf_vect0</span> <span class="o">=</span> <span class="n">TfidfVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">X_train_tf_idf0</span> <span class="o">=</span> <span class="n">tf_idf_vect0</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">([</span><span class="s2">&quot;Lagu Indonesia Raya merupakan lagu kebangsaan negara Indonesia&quot;</span><span class="p">,</span>
                                              <span class="s2">&quot;Lagu ini sangat jelek&quot;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[72]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="n">tf_idf_vect0</span><span class="o">.</span><span class="n">vocabulary_</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf0</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf0</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>{&#39;lagu&#39;: 3, &#39;indonesia&#39;: 1, &#39;raya&#39;: 5, &#39;bangsa&#39;: 0, &#39;negara&#39;: 4, &#39;jelek&#39;: 2}
[[0.33287178 0.66574355 0.         0.47368202 0.33287178 0.33287178]
 [0.         0.         0.81480247 0.57973867 0.         0.        ]]
Banyaknya document x banyaknya vocabulary
(2, 6)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[73]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">tf_idf_vect</span> <span class="o">=</span> <span class="n">TfidfVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
<span class="n">X_train_tf_idf</span> <span class="o">=</span> <span class="n">tf_idf_vect</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">full_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[74]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">tf_idf_vect</span><span class="o">.</span><span class="n">vocabulary_</span><span class="o">.</span><span class="n">items</span><span class="p">())[</span><span class="mi">0</span><span class="p">:</span><span class="mi">3</span><span class="p">])</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Memeriksa nilai dari beberapa vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf</span><span class="o">.</span><span class="n">toarray</span><span class="p">()[</span><span class="mi">0</span><span class="p">,[</span><span class="mi">2869</span><span class="p">,</span><span class="mi">575</span><span class="p">,</span><span class="mi">584</span><span class="p">]])</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[(&#39;rekam&#39;, 2869), (&#39;cctv&#39;, 575), (&#39;celaka&#39;, 584)]
[[0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 ...
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]
 [0. 0. 0. ... 0. 0. 0.]]
Memeriksa nilai dari beberapa vocabulary
[0.31844227 0.3049942  0.0499282 ]
Banyaknya document x banyaknya vocabulary
(1002, 3877)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_tf_idf</span><span class="p">,</span><span class="n">tf_idf_vect</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span><span class="n">desc</span><span class="o">=</span><span class="bp">True</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[83]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(5).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[83]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAtgAAAINCAYAAAAEIAiZAAAAAXNSR0IArs4c6QAAIABJREFUeF7svQuYVNWdr/3vbrppLs1FjAwgguQil3hJGMXLaBQ4yoExJmRQI8JEAR00jEq8gGfkm0PO4eIF9TBAFFADg6MwHzPJBA76NZhgvKDBqAREzaBoaIKmwx2a5vY9azO73F1d1VQ3v11UrXrryfPQXXvt397r/a+Sl5W1VxUdPXr0qPGCAAQgAAEIQAACEIAABCQEihBsCUdCIAABCEAAAhCAAAQgEBBAsBkIEIAABCAAAQhAAAIQEBJAsIUwiYIABCAAAQhAAAIQgACCzRiAAAQgAAEIQAACEICAkACCLYRJFAQgAAEIQAACEIAABBBsxgAEIAABCEAAAhCAAASEBBBsIUyiIAABCEAAAhCAAAQggGAzBiAAAQhAAAIQgAAEICAkgGALYRIFAQhAAAIQgAAEIAABBJsxAAEIQAACEIAABCAAASEBBFsIkygIQAACEIAABCAAAQgg2IwBCEAAAhCAAAQgAAEICAkg2EKYREEAAhCAAAQgAAEIQADBZgxAAAIQgAAEIAABCEBASADBFsIkCgIQgAAEIAABCEAAAgg2YwACEIAABCAAAQhAAAJCAgi2ECZREIAABCAAAQhAAAIQQLAZAxCAAAQgAAEIQAACEBASQLCFMImCAAQgAAEIQAACEIAAgs0YgAAEIAABCEAAAhCAgJAAgi2ESRQEIAABCEAAAhCAAAQQbMYABCAAAQhAAAIQgAAEhAQQbCFMoiAAAQhAAAIQgAAEIIBgMwYgAAEIQAACEIAABCAgJIBgC2ESBQEIQAACEIAABCAAAQSbMQABCEAAAhCAAAQgAAEhAQRbCJMoCEAAAhCAAAQgAAEIINiMAQhAAAIQgAAEIAABCAgJINhCmERBAAIQgAAEIAABCEAAwWYMQAACEIAABCAAAQhAQEgAwRbCJAoCEIAABCAAAQhAAAIINmMAAhCAAAQgAAEIQAACQgIIthAmURCAAAQgAAEIQAACEECwGQMQgAAEIAABCEAAAhAQEkCwhTCJggAEIAABCEAAAhCAAILNGIAABCAAAQhAAAIQgICQAIIthEkUBCAAAQhAAAIQgAAEEGzGAAQgAAEIQAACEIAABIQEEGwhTKIgAAEIQAACEIAABCCAYDMGIAABCEAAAhCAAAQgICSAYAthEgUBCEAAAhCAAAQgAAEEmzEAAQhAAAIQgAAEIAABIQEEWwiTKAhAAAIQgAAEIAABCCDYjAEIQAACEIAABCAAAQgICSDYQphEQQACEIAABCAAAQhAAMFmDEAAAhCAAAQgAAEIQEBIAMEWwiQKAhCAAAQgAAEIQAACCDZjAAIQgAAEIAABCEAAAkICCLYQJlEQgAAEIAABCEAAAhBAsBkDEIAABCAAAQhAAAIQEBJAsIUwiYIABCAAAQhAAAIQgACCzRiAAAQgAAEIQAACEICAkACCLYRJFAQgAAEIQAACEIAABBBsxgAEIAABCEAAAhCAAASEBBBsIUyiIAABCEAAAhCAAAQggGAzBiAAAQhAAAIQgAAEICAkgGALYRIFAQhAAAIQgAAEIAABBJsxAAEIQAACEIAABCAAASEBBFsIkygIQAACEIAABCAAAQgg2DGMgarq/TGkFmZkq/Jm1qykyHbuPViYAGLodcvmJVZWWmI79tTGkF6YkeVlJea4/nk3TFUjoKy02CpalFr1rgOqyILPKS0ptnYVpfb5DpiqBkNJcZGd2ra5bdteo4rMqZzOHVrk1P3k080g2DFUC8HWQUWwdSzDJARbzxTB1jNFsPVMEWw9UwRbz9SXRAQ7hkoi2DqoCLaOJYKtZxkmIth6tgi2nimCrWeKYOuZ+pKIYIsr+dEnu2zP/kPi1MKNK21WbMVFZgcOHilcCOKeu79kS0qKrKb2sDi5cOOalRQHS5lgqhsDTlycZO8/wDhVUS0uLrLysmLbVwNTGdMisxbNm9nemuz8vd/h1Owu2WCJSNNHCoLddHYpz7z6mn+3z7btFacSBwEIQAACEIBAIRP4/o297drv98wqAgS76bgR7KazSyvYv/j578WpxEEAAhCAAAQgUMgEHp05AMHOowGAYIuL5WawEWwxVOIgAAEIQAACBU4Awc6vAYBgi+uFYIuBEgcBCEAAAhCAgCHY+TUIEGxxvRBsMVDiIAABCEAAAhBAsPNsDCDY4oIh2GKgxEEAAhCAAAQggGDn2RhAsMUFQ7DFQImDAAQgAAEIQADBzrMxgGCLC4Zgi4ESBwEIQAACEIAAgp1nYwDBFhcMwRYDJQ4CEIAABCAAAQQ7z8YAgi0uGIItBkocBCAAAQhAAAIIdp6NgYIU7BlPLrFL+51t55+b/huRtu/cbVNnLrKJ44Zb+7YVGZcVwc4YFQ0hAAEIQAACEMiQANv0ZQgqR5oh2GkKgWDnyAjlNiAAAQhAAAJNIDB58iV2330XWFlZie3eXWu3315pCxdusPXrb7LevTsEibW1h2369Dds0qRX6l0h3fmu4bx5V9moUWcH50Sz3e+VlcNswIBuwbEtW/bYyJHLbdWqT6x//zNswYLB1qVL6+DYypWbbeDAJfWu687v2bND4rywAYLdhEFwEk9BsBHskzj8uDQEIAABCEBAT8DJ8Z139rXHHltbR57d++edd5p9+9v/FlzUifKgQWfWk1knw3PnXmmLFr0XnO/aXXRRZ+vT52kbMaK3zZhxhc2Z83ZwzAlxp06tg2Muf+zY82z8+JcSMr91655ApKPtkjNCAu784cN7WU3NYRs3bmUg5gi2fnxkI9ELwd60ucpuvfcRq9pWHTB75vEJwfIPtxRk/rPLgvdG3TDExt8yLPg5ukQk+dwf33uzDR18mSXPYLtz/vhZtU2++2ar2vanOtcLz3HZLBHJxrDlGhCAAAQgAIH0BNws9WuvVdno0S80iCkU2jFjXqwjs8nvR4W4c+fWCdl24VEZv/jizsH1wplpd97UqZfZwoXr7dprz0oIeyj3obRHc1566dMgH8HO7xGe94LtRPj+qfPsnrHXWY9uxwa2ey1dvjr408ly8u/p1mBHpdqd49Zg3zVmmD06d4ld+M3eiaxoyZNFHMHO7w8Edw8BCEAAAvlNwAnvzJkD7D//c4ddffWXg85s2FAdzDAnv5yIhzPM0WPRGetkiY5LsN0M98cf77Jf/epTmzChH4Kd38PQ8l6w33xno728Zl1idtrVo6am1iY9/JQtq3y9TnnCWeyGZrDP6dXDZk+7KzjPibsT6GuvvryOXCfPeofnuIchEew8/0Rw+xCAAAQgkNcE3KzxrFkD7dNPdwdSHa59XrHio2BGO7q2Op14O8Hu3r1NnTXS4ax4VdWeOstAXFt3TbeW28l3dMmJk+YLLugUrP920hzKfHhPO3ceSCwtGTKkh/XtuzDIQrDzeggGN++tYD805zkbPnRgnVntsFyhYH+le5c6s9/JM9hOsH9403ds6fKXE1nJM+bMYOf/h4AeQAACEICAPwTCZRkTJ64O1kG7V/KMdNhb975buhE+ABl9P9XyjXBNdvRBxk2bdgSnhceiD1G+9dY269ixlbl7cS8n/hUVZcHDlb/5zTZr1655MFPtZtynTVsT3C+C7cdYzHvBbmiJyOtvbQjWTJeXl9WpVijYHdq1sYfmPG9TJo4OtuJzs+EzfrI4MYMdbtO3fcfuRLvoz8nnMIPtx4eCXkAAAhCAQP4SSH5AMRTs5Blp936qtu79htZgJ+84kk6Iw5xwZjqZaLgkxL0f7kgSbZO8wwm7iOTXmMx7wXa4M3nI0bWLPvwY7oPt1mo/8OBTQdWuv6a/tWrVwm66blDwe3Qf7Kh8v/TKb1Oeg2Dn1+DnbiEAAQhAwE8C0R07oktE3JKQGTN+k+h0dAb7q19tn1j64bbXc1vqhctKGtptJNouSjPdTiGh8KfavcQdYwbbjzHphWDnUilYg51L1eBeIAABCECgUAlEl2qEe05H9692XKKzxMlb7KXbBzt5P+v589cldisJ13+Hy0Cie2xHrx3dHzu5Pgi2HyMWwRbXEcEWAyUOAhCAAAQgAAG+Kj3PxgCCLS4Ygi0GShwEIAABCEAAAgh2no0BBFtcMARbDJQ4CEAAAhCAAAQQ7DwbAwi2uGAIthgocRCAAAQgAAEIINh5NgYQbHHBEGwxUOIgAAEIQAACEECw82wMINjigiHYYqDEQQACEIAABCCAYOfZGECwxQVDsMVAiYMABCAAAQhAAMHOszGAYIsLhmCLgRIHAQhAAAIQgACCnWdjAMEWFwzBFgMlDgIQgAAEIAABBDvPxgCCLS4Ygi0GShwEIAABCEAAAgh2no0BBFtcsMVLP7BDh4+KUws3rrioKOj8kaMwVY0CmKpIfpFTZEVWXGx2+AjjVEXXffKLi4tgqgJqZjAVwvyvKMe0pLjIDmXps395/zP0nWggsXOHFlm9nk8XQ7DF1XR/wW7bXiNOLdy4ls2bWbOSItu172DhQhD3vEVZiZWWFtuuvTBVoW1eWmItmhfbjj0wVTEtbVZsrVs0s+27a1WRBZ9TWlJsbVo1s+pdMFUNBifXp1SU2ec7D6gicyoHwW56ORDsprNLe2ZV9f4YUgszslX5McHeiQzKBkDL5iVWVlpiO/bwl6wKanlZiTmuf0YGVUitrLTYKlqUWvUuP8VFBqoRQU6w21WU2uc7YNoIbA02dYJ9atvm3k6sIdhNHykIdtPZIdgxsEuORLD1kBFsPVMEW88UwdYzRbD1TBFsPVNfEhHsGCrJDLYOKoKtYxkmIdh6pgi2nimCrWeKYOuZIth6pr4kItgxVBLB1kFFsHUsEWw9yzARwdazRbD1TBFsPVMEW8/Ul0QEO4ZKItg6qAi2jiWCrWeJYMfHFMHWs0Ww9UwRbD1TXxIRbHEl2UVEC5RdRLQ8XRq7iOiZMoOtZ4pg65ki2HqmCLaeqS+JCLa4kuyDrQXKns1ani6t2O2GW+Tn3uLZ3iOWGWz9+AwTEWw9WwRbzxTB1jP1JRHBFleSb3IUAyUOAhkSeHTmALv2+z0zbK1txgy2lqdLQ7D1TBFsPVMEW8/Ul0QEW1xJBFsMlDgIZEgAwc4QVJ40Q7D1hUKw9UwRbD1TXxIRbHElEWwxUOIgkCEBBDtDUHnSDMHWFwrB1jNFsPVMfUlEsMWVRLDFQImDQIYEEOwMQeVJMwRbXygEW88UwdYz9SURwRZXEsEWAyUOAhkSQLAzBJUnzRBsfaEQbD1TBFvP1JdEBFtcSQRbDJQ4CGRIAMHOEFSeNEOw9YVCsPVMEWw9U18SEWxxJRFsMVDiIJAhAQQ7Q1B50gzB1hcKwdYzRbD1TH1JRLDFlUSwxUCJg0CGBBDsDEHlSTMEW18oBFvPFMHWM/UlEcEWVxLBFgMlDgIZEkCwMwSVJ80QbH2hEGw9UwRbz9SXRARbXEkEWwyUOAhkSADBzhBUnjRDsPWFQrD1TBFsPVNfEvNOsGc8ucQu7Xe2nX/uiX1j29Llq4MaDh18mbSWCLYUJ2ExERgxorfNmjXQKirKgiusXLnZBg5ckrha9Hht7WGbPv0NmzTplTp3M3nyJXbffRdYWVlJ8P6GDdXWp8/Twc/9+59hCxYMti5dWge/z5+/zkaPfiH4ed68q2zUqLMTWdFrr19/k/Xu3SE4lnzdysphNmBAt+DY7t21dvvtlbZw4YZEDoId02A5SbEIth48gq1nimDrmfqSiGAj2L6MZfrRCAJr146wZcs2BdLsZHrGjCtszpy3E787+V68+P2EFKeK/vWvv29PPPFOILmhUK9Y8VFwjpNh93LS7vKnTr3MJk5cbVu27LEf//iv7IEHfm2rVn1S59qu/XnnnWbf/va/JUR80KAzbeTI5Xb55V1t7NjzbPz4l4LrufxOnVonhN6dgGA3YgDkQVMEW18kBFvPFMHWM/UlEcFGsH0Zy/TjBAi4mePXXquqJ8eNiQwznn32PZs790pbtOi9xKy3O7Z16546s+Qu24l5ctvwmm6GfPjwXjZmzIt2ww297KKLOieEOnrMiTqC3ZhK5UdbBFtfJwRbzxTB1jP1JTGvBfvNdzba/VPm2hMP/sh6dOtsbvnI/GeXBbU5p1cPmz3tLmvftsI2ba6yypfX2qmntLUHHnzKfnzvzUGb9e9/bKtff8eqtlVb544dEjnumFtC4tq6V/SYe3/f/gP208UrgvPc65nHJySWrLBExJePRuH0I1ly3ey2m2m+6qruwfIP97ObRQ5FNhUZJ7zhDLM7Hs5Yh0s4ojPa0fPdcpFwljo5Pyrl0RlyJ/Bu+Uk4Wx7mMYPt15hFsPX1RLD1TBFsPVNfEvNWsD/d8pm9/tYGm3z3zVZeXhYI8cd/2Gbjbzn2f02738PjVdv+ZLfe+4iN/dtrEmuuo8fd+U7CH5rzvE2ZODqQ8ujLifzLa9YF2e68Jf/xy4S8u2Pu9/A+EGxfPhqF04+o/IYi63ofSnW62efgH6n/tWY6ul7aLQmZMKGfjRu3MiHlTqTDGejo+uzktdTRdd3RNd3uWtHzomu6EWw/xyqCra8rgq1nimDrmfqSmJeC/f7vP7G2bVolpLamptYemvOcDR86MJjJdq/tO3fb1JmLbOK44bZ9x25btLTS7hl7fSDjoYC7P8OHHJMzojPYrt2oG4YkBDt6nrvO08+vsNtGXhNkI9i+fDQKox9R8Q0lNnnJRqrlGMl0QvnduLHafvrT9RnPYIcPU6Za7+3u7dprzwoeZvzqV9vbnXf2tcceWxssO3Fi717hQ5XuZ2aw/RqzCLa+ngi2nimCrWfqS2JeCnb30zsm+DtBVgt29Y5ddWalk2ewEWxfhn9h9yPd8ozoemxHyAn2kCE9rG/fhQ0CC2XdzVxnugbbBaZbPhJdunLxxcf+4RzudOKOzZw5wKZNW5PYSQTB9ms8I9j6eiLYeqYItp6pL4l5Kdhum76zz+phkx5+yoZdfXmw/vl4S0RSzWAnL/WY8ZPFwdKPl175bZ3lJm5tt3uFS0QQbF+Gf+H2o6G1z8nHoktEwp+nTFkTbMEXrrGOzmA7CY7u8hHdpeTDD7cHa7rD9dbRGWy3JGTGjN8kihKdwf7bv+1TZ9eQ6Jrv8B4QbL/GM4KtryeCrWeKYOuZ+pKYt4LtpNotz7htwqM2/u+uDSS7oYccUwl29GHF6IOMbkbcyfuyyteDOrtlJvv219gtN14diDyC7cvwL8x+JO9RHVKIrnmO7jkdfT8q2NF9rl1GJvtgJ++/7c4L98FO3h87eR/shvbIdjkItl/jGcHW1xPB1jNFsPVMfUnMO8HOdfCswc71CnF/vhJAsP2qLIKtryeCrWeKYOuZ+pKIYIsriWCLgRIHgQwJINgZgsqTZgi2vlAItp4pgq1n6ksigi2uJIItBkocBDIkgGBnCCpPmiHY+kIh2HqmCLaeqS+JCLa4kgi2GChxEMiQAIKdIag8aYZg6wuFYOuZIth6pr4kItjiSiLYYqDEQSBDAgh2hqDypBmCrS8Ugq1nimDrmfqSiGCLK4lgi4ESB4EMCSDYGYLKk2YItr5QCLaeKYKtZ+pLIoItriSCLQZKHAQyJIBgZwgqT5oh2PpCIdh6pgi2nqkviQi2uJIIthgocRDIkACCnSGoPGmGYOsLhWDrmSLYeqa+JCLY4koi2GKgxEEgQwIIdoag8qQZgq0vFIKtZ4pg65n6kohgiyuJYIuBEgeBDAkg2BmCypNmCLa+UAi2nimCrWfqSyKCLa6kE+zPtu0VpxIHAQgcj8D3b+xt136/5/GaxXK8vKzEWjYvsT/vro0lvxBDEWx91RFsPVMEW8/Ul0QEW1zJjz7ZZXv2HxKnFm5cabNiKy4yO3DwSOFCEPfc/SVbUlJkNbWHxcknP67DqS1Oyk0g2HrsCLaeKYKtZ4pg65n6kohgx1DJqur9MaQWZmSr8mbWrKTIdu49WJgAYui1m2ktKy2xHXuYbVXhRbBVJL/IQbD1TBFsPVMEW8/Ul0QEO4ZKItg6qAi2jmWYhGDrmSLYeqYItp4pgq1nimDrmfqSiGDHUEkEWwcVwdaxRLD1LMNEBFvPFsHWM0Ww9UwRbD1TXxIR7BgqiWDroCLYOpYItp4lgh0fUwRbzxbB1jNFsPVMfUlEsGOoJIKtg4pg61gi2HqWCHZ8TBFsPVsEW88UwdYz9SURwY6hkgi2DiqCrWOJYOtZItjxMUWw9WwRbD1TBFvP1JdEBFtcSbbp0wJlmz4tT5eWyTZ9J2u7O31vs5PIGmw9ZwRbzxTB1jNFsPVMfUlEsMWV5ItmxECJyzqB6Y9cbl/reUrWr5vPF0Sw9dVDsPVMEWw9UwRbz9SXRARbXEm+Kl0MlLisEiguLrKVq69HsBtJHcFuJLAMmiPYGUBqZBMEu5HAMmiOYGcAqUCbINjiwiPYYqDEZZUAgt003Ah207g1dBaCrWeKYOuZIth6pr4kItjiSiLYYqDEZZUAgt003Ah207gh2HpuDSUi2HreCLaeqS+JCLa4kgi2GChxWSWAYDcNN4LdNG4Itp4bgp1dpgh2dnnn09UQbHG1EGwxUOKySgDBbhpuBLtp3BBsPTcEO7tMEezs8s6nqyHY4moh2GKgxGWVAILdNNwIdtO4Idh6bgh2dpki2NnlnU9XQ7DF1UKwxUCJyyoBBLtpuBHspnFDsPXcEOzsMkWws8s7n66GYIurhWCLgRKXVQIIdtNwI9hN44Zg67kh2NllimBnl3c+XQ3BFlcLwRYDJS6rBBDspuFGsJvGDcHWc0Ows8sUwc4u73y6GoL9X9Vaunx18NPQwZedUP0Q7BPCx8knmQCC3bQCINhN44Zg67kh2NllimBnl3c+XQ3BRrDzabzm3L1OnnyJ3XffBVZWVhLc2/z562z06BeCn/v3P8MWLBhsXbq0rncs2pERI3rbrFkDraKiLHh75crNNnDgkkSTysphNmBAt+D3DRuqrU+fp4Of16+/yXr37pBol3zevHlX2bXXnmW3315pCxduqMPOneteYVZ4EMFu2hBDsJvGDcHWc0Ows8sUwc4u73y6GoKNYOfTeM2pe3UCPXPmAJs2bU0gsE62x449z8aPfyn43YmxezlZdhI9deplNnHi6pSyu3XrnkS7GTOusDlz3rZJk14JMnr27GAjRy63Vas+SfTfXXvu3Ctt0aL3gnbJLyfX7pqff76/3jWdXHftWmEffrjd+vZdWOdUBLtpQwzBbho3BFvPDcHOLlMEO7u88+lqCHYKwd60ucpuvfcRm3L/GOvQro1VvrzW9uyrsfnPLgtaP/P4BHt5zbrE7z++9+bE0hKWiOTT8Nfea1R6f/nLT+sJsBPbUKTDK6cSZdfutdeq7Fe/+jStlCfLfbQn4bF589610aPPSfwDwLVx/wgYMqSHLVu2KfgTwdaMAQRbwzGawlel65nyTY56pgi2nqkviQh2kmB37XKazfjJYps97S5r37bCorJ9/rk9U/7+0JznbcrE0UF7BNuXj0bj+xGdpXZnJ89YR2e0o+lutnnQoDODWeobbuiV+Pnyy7sGElxe3iyxFCRcgpK8rKS29rBNn/5GndnshmbN3TUvuqgzS0QaX+aUZyDYIpCRGARbzxTB1jNFsPVMfUlEsCOC/cIv37Rdu/cm5NodcoK9aGml3TP2eisvL7PtO3fb1JmLbOK44YFQJ/+OYPvy0Wh8P8KZZ7cG28nthAn9bNy4lYmlHemk1l3JHRs16mzbsmVPYjlI+F4o1clLUJIlPXm9NYLd+Bo29QwEu6nk0p+HYOuZIth6pgi2nqkviQh2RLA//sM2u7Tf2cHyj/G3HFs/i2D7MtTj7Ufy7HQquU03gx194NBJ9J139rXHHltrnTu3rjfLHJX4aI9SLTVBsOOteTQdwdazRrD1TBFsPVMEW8/Ul0QEOyLY7ke3Td+MJ5dY99M7Bj8j2L4M9fj64cS5U6fWdZZbpFtbnbwGO5UEu5nr7t3b2KuvVtnw4b1szJgXE7Pga9eOCNZPJz/YiGDHV99MkhHsTCg1rg2C3ThembRGsDOh1Lg2CHbjeBVSawQ7hWDX1NTapIefsgu/2dvO6/MVlogU0ieikX1NJddhRPSYE+lwdxC3e0eqn0NpDh+GnDJlTbDN34oVHwVb/zW0RCTVbiPMYDeymCfQHME+AXhpTkWw9UwRbD1TBFvP1JdEBFtcSdZgi4HmcFzyg4bhrYb7UafbBzsq206qk/fSju51Hb1G9EHG5HOia7fD+0Cwszd4EGw9awRbzxTB1jNFsPVMfUlEsMWVRLDFQInLKgH2wW4abgS7adwaOgvB1jNFsPVMEWw9U18SEWxxJRFsMVDiskoAwW4abgS7adwQbD23hhIRbD1vBFvP1JdEBFtcSQRbDJS4rBJAsJuGG8FuGjcEW88Nwc4uUwQ7u7zz6WoItrhaCLYYKHFZJYBgNw03gt00bgi2nhuCnV2mCHZ2eefT1RBscbUQbDFQ4rJKAMFuGm4Eu2ncEGw9NwQ7u0wR7OzyzqerIdjiaiHYYqDEZZUAgt003Ah207gh2HpuCHZ2mSLY2eWdT1dDsMXVQrDFQInLKgEEu2m4EeymcUOw9dwQ7OwyRbCzyzufroZgi6uFYIuBEpdVAgh203Aj2E3jhmDruSHY2WWKYGeXdz5dDcEWVwvBFgMlLqsEEOym4Uawm8YNwdZzQ7CzyxTBzi7vfLoagi2uFoItBkpcVgkg2E3DjWA3jRuCreeGYGeXKYKdXd75dDUEW1ytxUs/sEOHj4pTCzeuuKgo6PyRozBVjYJiKzL3v3RMO3dubV/reYrqcgWRg2Dry8w3OeqZ8kUzeqYItp6pL4kItriSh48ctW3ba8SphRvXsnkza1ZSZLv2HSxcCOKetygrsdLSYtu1F6YqtAi2iuQXOQi2nimCrWeKYOuZ+pKIYMdQyarq/TGkFmZkq/Jjgr0TGZQNgJbNS6ystMR27KmVZRZ6EIKtHwGfzkqXAAAgAElEQVQItp4pgq1nimDrmfqSiGDHUEkEWwcVwdaxDJMQbD1TBFvPFMHWM0Ww9UwRbD1TXxIR7BgqiWDroCLYOpYItp5lmIhg69ki2HqmCLaeKYKtZ+pLIoIdQyURbB1UBFvHEsHWs0Sw42OKYOvZIth6pgi2nqkviQh2DJVEsHVQEWwdSwRbzxLBjo8pgq1ni2DrmSLYeqa+JCLY4kqyi4gWKLuIaHm6NHYR0TNliYieKYKtZ4pg65ki2HqmviQi2OJKsg+2Fij7YGt5urToPtiX9z9Df4ECTESw9UVHsPVMEWw9UwRbz9SXRARbXEm+yVEMlLjYCEyafIndett5seUXUjCCra82gq1nimDrmSLYeqa+JCLY4koi2GKgxMVGAMHWoUWwdSzDJARbzxTB1jNFsPVMfUlEsMWVRLDFQImLjQCCrUOLYOtYIth6lmEigq1ni2DrmfqSiGCLK4lgi4ESFxsBBFuHFsHWsUSw9SwR7PiYItjxsc33ZARbXEEEWwyUuNgIINg6tAi2jiWCrWeJYMfHFMGOj22+JyPY4goi2GKgxMVGAMHWoUWwdSwRbD1LBDs+pgh2fGzzPRnBFlcQwRYDJS42Agi2Di2CrWOJYOtZItjxMUWw42Ob78kItriCCLYYKHGxEUCwdWgRbB1LBFvPEsGOjymCHR/bfE9GsMUVRLDFQImLjQCCrUOLYOtYIth6lgh2fEwR7PjY5nsygi2uIIItBkpcbAQQbB1aBFvHEsHWs0Sw42OKYMfHNt+TEWxxBRFsMdAciRsxorfNmjXQKirKgjtauXKzDRy4JHF369ffZL17d0h5LLkLrq179enzdOJQcv78+ets9OgXguPHu3Zl5TAbMKBb0HbDhupEbvSeUt0zgq0bXAi2jiWCrWeJYMfHFMGOj22+JyPY4goi2GKgORK3du0IW7Zsk02a9EogvDNmXGFz5rwd/D5v3lV20UWdA7Ht3/8Mmzv3Slu06L3gWCq57tq1wj78cLv17buwjqBv3bonkPbJky+xsWPPs/HjX7KFCzeYE+XwWPK1nVz37NnBRo5cbqtWfZLIO959uIYItm5wIdg6lgi2niWCHR9TBDs+tvmejGCLK4hgi4HmaJyT3tdeqwpmmaM/u9t10tupU+s6M9TufSfOQ4b0CETd/RkKtpPmqVMvs4kTVwdCHWa4P6dMWVNP2MPr/epXn9Y7L8TlBHvmzAE2bdqaRGYySgRbN7gQbB1LBFvPEsGOjymCHR/bfE/2SrBrampt0sNP2bLK14O6DBl4oU2++2YrLy+zpctX26mntLNfVL5qv133oT3x4I+sfbsKu23Co/bue5uC9qNuGGLjbxlm23futqefX2F79+635362ql7Wps1Vduu9j1jVtupE/cNrDbtuuf3i57/P93HB/TdAIDo7/MtfflpPgKMz2qliko83JNhuRtu1HzTozGCW+oYbeiV+vvzyroGol5c3SyxPCZeWJC8rqa09bNOnv1FnVh3B1g1zBFvHEsHWs0Sw42OKYMfHNt+TvRLsGU8use6nd7Shgy8L6uJ+dy8nzU6w5/z0Z4FY9+jWuV7dnJw/NOc5Gz50YEK8h119eZAVirv7/fxzewa5l/Y7O/g5lPHbRl4TiDwz2Pn+kTj+/bsZavdy8ptqptjNVA8f3svGjHmxzrKNMDlZsF3GggWDbcWKj4IZ8VCO33hja2Kdtztn1KizbcuWPYnlIOF7oVQnLy2J9sS1vfbas+z22ysTM9oI9vFrnWkLBDtTUpm3KysttooWpVa960DmJ9GyQQKlJcXWrqLUPt8BU9VQQbBVJP3L8UawnehOnbnIJo4bbu3bVgSVcjPNi5ZW2j1jr7flq47Naofy7X5250RnsDt37JCY2U7OcoLetctpKQU72hbB9u9Dkiyq4Xpr936qtc6NncF2OU6O77vvAisrK7Hdu2uDNdrbt9cEgh19KNK1u/POvvbYY2utc+fWibXf4T0mL1cJ3091nwi2bqwi2DqWYRKCrWeKYOuZIth6pr4kFqxgJ89KJ89gNyTYyUtEnnl8QiDe7oVg+/LRqN+P6FKN6AOFma7BDhOPJ+CuXfhQpRPt5PXZ7vzu3dvYq69W1Zspjz6MGe0Bgh3vuESw9XwRbD1TBFvPFMHWM/Ul0RvBdgU53hKR6Ay2m72+f+o8u2fsdcGSESfN90+bZ1MmjA6WiDQk2G++s9E+3fJZndnwcEAg2L58NOr2I51cu1bRY+736HKP6A4gmQp29CHJ5F1DXEaY6R6AjF6roSUiqXYbYQZbN1YRbB1LZrD1LMNEBFvPFsHWM/Ul0SvBPt5DjlHBdj87Uf7BHdOCWrqHFP/itA72nasuOa5gp1ta4kQdwfblo/FFP8I10l26tK7TuXR7Tkf3yM5UsNPtZe0uGF0+4n6PXjf6MGP0Qcbkc6Jrt8NOINi6sYpg61gi2HqWCHZ8TBHs+Njme7JXgp2NYriZ7ofmPG9TJo5OrPV2ov7ymnXBw5QIdjaqwDUUBBBsBcVjGQi2jiWCrWeJYMfHFMGOj22+JyPYjaxg9MFJt2uIe7kHIN3LPUCJYDcSKM1PGgEEW4cewdaxRLD1LBHs+Jgi2PGxzfdkBLsJFXRrvec/uyxxZrh/tnsDwW4CUE45KQQQbB12BFvHEsHWs0Sw42OKYMfHNt+TEWxxBRFsMVDiYiOAYOvQItg6lgi2niWCHR9TBDs+tvmejGCLK4hgi4ESFxsBBFuHFsHWsUSw9SwR7PiYItjxsc335AYFe81b71n3M/7COp7a3o4ePWqv/uZ3Nu/Z5dapYwe7+9Zr7ZT2bfK9//L7R7DlSAmMiQCCrQOLYOtYIth6lgh2fEwR7PjY5ntyWsHeu6/G/vf/+Wcb/f3BwT7Rn1Z9Zv/4yDN2641X2+Y/bLNPt35ud4waaiUlJfnOQHr/CLYUJ2ExEkCwdXARbB1LBFvPEsGOjymCHR/bfE9OK9jJXz3+L/++yvbu22+jvj/YduzaYw/Nfs7uu/0Ga9umVb4zkN4/gi3FSViMBBBsHVwEW8cSwdazRLDjY4pgx8c235PTCvbuPfts2j89a38/+ntWXlZmDzw4335403fta1/uasnyne8QlPePYCtpkhUnAQRbRxfB1rFEsPUsEez4mCLY8bHN9+S0gu3WXM//l+X2u/c/sn37auwbX/+q3XLjXwdLQpxgz/npz+yO0X9jrVqW5zsD6f0j2FKchMVIAMHWwUWwdSwRbD1LBDs+pgh2fGzzPbnBhxxrDx6y9z7cHPSx11e7WVlps+Bn9/6WP/7Jup/e0YqKivKdgfT+nWB/tm2vNJMwCMRBYNCQHnbrbefFEV1wmQi2vuRlpcVW0aLUqncd0IcXaGJpSbG1qyi1z3fAVDUEEGwVSf9y2KZPXNOPPtlle/YfEqcWblxps2IrLjI7cPBI4UIQ99z9JVtSUmQ1tYetw6ktxOmFGYdg6+uOYOuZIth6pgi2nqkvicedwXZfA/78z1+y8rJSmz3tLmvftsI2/v4T+9Ofd9pfXXC2Lxyk/aiq3i/NK+SwVuXNrFlJke3ce7CQMUj73rJ5iZWVltiOPbXS3EIOQ7D11Uew9UwRbD1TBFvP1JfE467Bdtvz9f+rb9p/vPiq/Y87bgwE++NP/2hzF/3C7v/7G1mDnWIkINi6jweCrWMZJiHYeqYItp4pgq1nimDrmSLYeqa+JGa0i4hbez115iKbOG54INjsItJw+RFs3ccDwdaxRLD1LMNEBFvPFsHWM0Ww9UwRbD1TXxIz2gfbdTYq2Nv+tN0env2c/cOdI9kHmxnsWD8LCLYeLzPYeqYItp4pgq1nimDrmSLYeqa+JKYV7MOHD9uMJ5dYjzM62xUXn2fTZj0bzGCXNy+zWU//u1W0bhls28cuIvWHAjPYuo8Hgq1jyQy2niUz2PExRbD1bBFsPVMEW8/Ul8QGH3L88/Zd9r8eX2gbPthsO3butk4dOwRfkz7oigvs3tu/b+3atPaFg7QfCLYOJ4KtY4lg61ki2PExRbD1bBFsPVMEW8/Ul8TjbtPnvnDm8+qd9vGnW+3wkSPWtfNp1rnjqVbs9k7jVY8A2/RpBwXb9Gl5urSuXVqzi4gYK0tExEDNDMHWM0Ww9UwRbD1TXxKPK9i+dDRb/eCLZrJFmus0hcDcp/+7ndEVwW4Ku4bOQbDVRBFsPVEzBFtPFcHWM/UlsUHBrjlQaytffss++nRrvf62qWhl3xt8Gdv0JZHhq9J9+Wj414+/PP8vbP5PByPYMZQWwdZDZQZbzxTB1jNFsPVMfUls8CHHR55YYr//6A/23cGX1ltv3bys1L7es0fi69N9AXKi/UCwT5Qg58dFAMGOi6wZgq1ni2DrmSLYeqYItp6pL4kNbtP340cX2H0/vME6ntrel/7G3g8EO3bEXKCJBBDsJoLL4DQEOwNIjWyCYDcSWAbNEewMIDWyCYLdSGAF1LzBL5p5aM5zdufov7FT2rcpICQn1lUE+8T4cXZ8BBDs+Ngi2Hq2CLaeKYKtZ4pg65n6ktjgV6U/9dz/tZblze17f/0tloJkWHEEO0NQNMs6AQQ7PuQItp4tgq1nimDrmSLYeqa+JDb4kOOHH/3Bxv/jbNu0uapef8/p1cNmT7sr+Op0Xl8QQLAZDblKAMGOrzIItp4tgq1nimDrmSLYeqa+JKYV7JqaWvt/Hnk62Pfa7RZSXl5Wp8/FRcXBtzmyH3bdoYBg+/LR8K8fCHZ8NUWw9WwRbD1TBFvPFMHWM/UlscGHHKc8/s/B16OzBjvzciPYmbOiZXYJINjx8Uaw9WwRbD1TBFvPFMHWM/UlMa1g79tfYzOeXGJjhv81u4g0otoIdiNg0TSrBBDs+HAj2Hq2CLaeKYKtZ4pg65n6ktjgGuzX39oQfNHM8KEDrW2bViwRSVH17Tt329SZi4KZfrceHcH25aPhXz8Q7PhqimDr2SLYeqYItp4pgq1n6ktig0tEbpvwqL373qaUfeUhx2NYEGxfPgqp+zF58iV255197bHH1tqkSa8kGlVWDrMBA7oFv2/ZssdGjlxuq1Z9Uidk/fqbrHfvDnXeq609bNOnv5HIirZZuXKzDRy4xPr3P8MWLBhsXbq0Ds7dsKHa+vR5OvjZ3c99911gZWUlxz02f/46Gz36hcT1Eez4xiqCrWeLYOuZIth6pgi2nqkviQ3OYPvSycb2w+2a8uFHW+yqy88/7qkI9nER5W2DUK6dFM+e/XZCit37Y8eeZ+PHv2QLF24wJ8lbt+4J5Lihlztv+PBeNmbMi4GMu/PcK5Tn8Fwn7506tQ7eD2V7xYqPAln+9a+/b0888U5w3eixZ599z2bOHGDTpq0JjiXfo8tGsOMbigi2ni2CrWeKYOuZIth6pr4kIthJlXRyfeu9j1jVturgyI/vvdmGDr7M3nxno/3gjmmJ1s88PsHOP7cnM9i+fBJS9GPt2hG2bNkmGzKkR/BnOIPtBNi9QqEeMaK3TZ16mU2cuDqQ23QvJ9SvvVYViHKybEfPibZz7ydfr6G24TEn33PnXmmLFr2XuG8EO77BimDr2SLYeqYItp4pgq1n6ktig4K9v+aALat83f74+Z/r9bdNRatg+75WLct9YZHoh5PpT7d8Foi1eznpfmjO8zZl4uhgnbX7/f5p82zKhNHWvl0Fa7C9GwFfdCiVqDZFsJMlfN68q6xXrw7WrVubYClIdOlIdPb5q19tX2e2PIo61Sx1eDyV9CPY8Q1UBFvPFsHWM0Ww9UwRbD1TXxLTCvbhw4ftkSeW2J+377LLLjzHVr3yWxt0+QX27nv/aWvf/cAm/PAG63PWmV7ug50s2EuXrw7qHQq3+9ntsHJpv7PtK927INi+fBpS9COVYDs5HjTozMS6ayfcF1zQyW6/vTLtDHaylLvfL7309MR67OTMcK31gQOH6+WG67aT13Mfb2YbwY5voCLYerYItp4pgq1nimDrmfqSmNE+2EXFRfb08yvstpHXBF84s+GDzbby5bV22w+usZKSYw9b+fRCsH2q5on1JZVgu8Tow4lvvbXNOnZslXaJiJtNnjHjCpsz54t13MnCHb3OxRd3tp49OwQC72a3Z80aaIsXv1/ngUV3D+Ea7I0bq+us/063pATBPrGx0NDZCLaeLYKtZ4pg65ki2HqmviSmFeydu/ba9FnP2j23XW/lzctszoKf26jrBwfb9bkH+x6a/Zzdd/sN9bbv8wGME+yX16yz8bccW2vLEhEfqtq0PqQT7Giam21267T79l2Y8iJudvqiizrXeZgx+T13HfeQ4s9//nu79tqz6qydbig/OSf6gGTyzSDYTRsDmZyFYGdCqXFtEOzG8cqkNYKdCaXGtUGwG8erkFqnFeyDBw/Zwz953r4z6K/saz1Ot8fnL7V+3+hpl5x/tn1a9Zk98pPn7X/efbOXgu3+ARFuUchDjoX0cajf1+MJdvLsdPK66HTnJ58XLhF59NHf2F13/aWFu4a4Owqledy4lcGMdvggZfIMdkNy7XIQ7PjGMoKtZ4tg65ki2HqmCLaeqS+JDT7kuHVbdbAkxD3Y9/uPt9idk/7JSoqL7U9/3ml3j70ukO+ioiJfWEj6wRfNSDDmTEgqQXZy7JZtVFSU1Xk40d10smAnr61OnvkO97Tevbs2sdY6mu/ah/tsu5+j+2O738M9spPPCa8T7q2NYMc7pBBsPV8EW88UwdYzRbD1TH1JbNQ2fbv37reNv99sXf7iS9bptFOQ6xSjAMH25aPhXz+YwY6vpgi2ni2CrWeKYOuZIth6pr4kNkqwfel0nP1AsOOkS/aJEECwT4Rew+ci2Hq2CLaeKYKtZ4pg65n6ktigYLst+mb/9Ge29t33bdMnW+3QocOJfvNV6amHAILty0fDv34g2PHVFMHWs0Ww9UwRbD1TBFvP1JfEBh9yfHD2c8FDjO4LZdxa7OiruKjYKlq39HIf7BMpLoJ9IvQ4N04CCHZ8dBFsPVsEW88UwdYzRbD1TH1JzGgf7FPat/Glv7H3A8GOHTEXaCIBBLuJ4DI4DcHOAFIjmyDYjQSWQXMEOwNIjWyCYDcSWAE1TyvYu/fss4fmPGd3jv4bQ7AzHxEIduasaJldAgh2fLwRbD1bBFvPFMHWM0Ww9Ux9SWxwDfbPX3zVDh06ZN8ZdClLQTKsOIKdISiaZZ0Agh0fcgRbzxbB1jNFsPVMEWw9U18S0wr23n019tzPVtnS5auDhxvbt6uo0+fTO33JHrhzpJdfNHMixUWwT4Qe58ZJAMGOjy6CrWeLYOuZIth6pgi2nqkviWkFu/bgIfvdxk12oPZgyr42Lyu1r/fsYWWlzXxhIekHgi3BSEgMBBDsGKD+VySCrWeLYOuZIth6pgi2nqkviSe0D7ab5X5t7Xr71oXnWimiHYwJBNuXj4Z//UCw46spgq1ni2DrmSLYeqYItp6pL4knJNjbd+62p59fYbeNvKbeNn6+AGpsPxYv/cAOHT7a2NNon4ZAcVFRcOTIUZgqBsnXv/4lO6NraysrLbEde2oVkWSYGYKtHwYItp4pgq1nimDrmfqSiGCLK3n4yFHbtr1GnFq4cS2bN7NmJUW2a1/qpUqFS6bpPW/ZvATBbjq+lGci2GKgZoZg65ki2HqmCLaeqS+JCHYMlayq3h9DamFGtio/Jtg79yLYqhGAYKtIfpGDYOuZIth6pgi2nimCrWfqSyKCHUMlEWwdVARbxzJMQrD1TBFsPVMEW88UwdYzRbD1TH1JRLBjqCSCrYOKYOtYIth6lmEigq1ni2DrmSLYeqYItp6pL4knJNg7d+21f132K7vxe//N3LZ9vI4RQLB1IwHB1rFEsPUsEez4mCLYerYItp4pgq1n6kvicQX78OHDVrWt2j6v3sG+1xlWHcHOEFQGzRDsDCA1sglLRBoJLIPmzGBnAKmRTRDsRgLLoDmCnQGkRjZBsBsJrICaNyjYH336R5s45Un7+JOt9pUzT7eZ//vvrX3bCnv7d7+3Va/+1u4YNdRKSkoKCNfxu8ouIsdn1JgW7CLSGFqZtUWwM+PUmFYIdmNoZdYWwc6MU2NaIdiNoZVZWwQ7M06F2CqtYB88eMimz/oX+9ZF51qfs860af+0yCaOGx4I9rY/bbeHZz9n/8BXpdcbM+yDrf0YsQ/2Fzy7dWtjZ3653QkDRrBPGGG9AARbzxTB1jNFsPVMEWw9U18S0wq2+xKZqTOPSbV7hT87wY4ec7/z+oIA3+TIaIiDQOcurW3x0msQ7DjgCjIRbAHEpAgEW88UwdYzRbD1TH1JTCvYu/fsC6T670d9z5o3L60j2Bs+2Gz/vPT/s3+440Zr2aLcFxaSfiDYEoyEJBFAsHN7SCDY+vog2HqmCLaeKYKtZ+pLYoNrsH/+wiv2wi/ftFE3DLYF//qi/fCm79qHm/5g//T0vwXifdXl5/vCQdYPBFuGkqAIAQQ7t4cDgq2vD4KtZ4pg65ki2HqmviQ2KNhHjhy119eut7nPLrO31n1ghw4dtj5f6253jPmeXfyXX7eioiJfOMj6gWDLUBKEYOfNGECw9aVCsPVMEWw9UwRbz9SXxONu0+dLR7PVDwQ7W6QL6zrMYOd2vRFsfX0QbD1TBFvPFMHWM/UlscGHHP/P/KXBspAO7dv40t/Y+4Fgx464IC+AYOd22RFsfX0QbD1TBFvPFMHWM/UlscGHHP/X4wtt3M1D7fROX/Klv7H3A8GOHXFBXgDBzu2yI9j6+iDYeqYItp4pgq1n6ktig0tEXn9rg73524025sa/tvLmZb70OdZ+INix4i3YcAQ7t0uPYOvrg2DrmSLYeqYItp6pL4lpBXvvvhr7f5evtrd/96GtffcD69SxQ50+u1ntB/iimXrjAMH25aORW/1AsHOrHsl3g2Dr64Ng65ki2HqmCLaeqS+JaQW79uAh+93GTXag9mDKvjYvK7Wv9+xhZaXNfGEh6QeCLcFISBIBBDu3hwSCra8Pgq1nimDrmSLYeqa+JLKLyH9VUvXtlAh2fnw0Jk++xO68s6899thamzTpleCm16+/yXr3rvv/1NTWHrbp099ItHHtKiuH2YAB3ep1dP78dTZ69At1jm/ZssdGjlxuq1Z9Uu8aK1dutoEDlyRyRozobbNmDbSKijJLvi6CndvjCsHW1wfB1jNFsPVMEWw9U18SC2IGe8aTS6z76R1t6ODL0tYNwfZlSB+/H6FcO4mdPfvtOvIcPdu1Gz68l40Z82JCkFOlOzGeOvUymzhxtX31q+1t7NjzbPz4l2zhwg2BtG/duicQ6XnzrrKLLupsffo8bf37n2Fz515pixa9F1w/lOvFi98PJD35hWAfv64nswWCraePYOuZIth6pgi2nqkviWkFe+euvfbjxxbYH7Z+Xqeve/but6NHjwayev01/a1VSz++Kh3B9mVIH78fa9eOsGXLNtmQIT2CP8MZ7OQznRy/9lpVSuGNtnUz2u7lJDr6s3svKt8TJvSrk+fadurUOhDu5PMQ7OPXMZdaINj6aiDYeqYItp4pgq1n6ktio5eIOLle8cs3bMeOPXb9d/rnxbc5uhnsS/udbeef29M2ba6yW+99xKq2VQc1/PG9Nwf/WEgW7KXLV9sDDz4VtOncsYM98eCPrEe3zube37f/gP108YpExjOPTwiy3YslIvnx0UieQU6+66gYu5nodK/knHSCvXDherv22rMSM9YuLzqj7aTfLSe56qruVlZWEvwcXVrCDHZujysEW18fBFvPFMHWM0Ww9Ux9SWy0YLuOOxl9bO6/2t1/d51VtG6Z8yyigh292ahUu/enzlxkE8cNt/ZtK+r06c13NtrLa9bZ+FuGBYK95D9+abOn3RW0c8fc75PvvtnKy8sQ7JwfDcdu8HiCfbwZ5bCbUUkOpXnQoDMTcuxyLrigk82a9Vv79re/YtOmrQmWjrhXuATFLVO5666/DN4LpTq6tCT4R16X1rZ46TV25pfbnTDhls1LrKy0xHbsqT3hLAKOEUCw9SMBwdYzRbD1TBFsPVNfEpsk2H/eviuQ0fvvuLGejOYimIZmsM/p1SOQ5WTBjs5gu2OjbhiSEGz3e7ie20n608+vsNtGXoNg52Lx09xTQ4LtZq9nzLjC5sxJvz47lPQFCwbbihUf1VlGEn1Y8q23tlnHjq2soRnsceNW1lmPHZXvcP03gp3bgwvB1tcHwdYzRbD1TBFsPVNfEtMK9pEjR233nn125OiROn11a7CXLn/Z3J/33na9lebBNn2hYH+lexe7f+o8u2fsdcFyj3Qz2L//eEudWenkGWwEO/+Hf0OCnTwrna63mTwE6dq4td59+y4MHniMrumOrsFOPhY9jxns3B9vCLa+Rgi2nimCrWeKYOuZ+pLY6IccXce/efbX7JYb/9ratWmdFxxCwe7Qro09NOd5mzJxdGJ5x4yfLK43g/3SK7+1j/+wLZixdi93vnuFS0QQ7Lwoe4M3mU6w073vhDe6O4gLP95DkMkz4U7cw+Uj7vzo7Hf0mNvSjyUi+TXGEGx9vRBsPVMEW88UwdYz9SWxSUtE8q3z0SUi0aUfwS4orVrYTdcNCroUrsFu0by5TXr4KVtW+XrwvluXvW9/jd1y49XBGmwEO99GQP37TSfSyaIbnpks2KmE27VtaC/rUMrDvbaT98GO7q+9YUN1sLtI+GKJSG6POQRbXx8EW88UwdYzRbD1TH1JbPCr0l9bu96+deG59ZaBuK9Rf/U3v7NvXXReXnyTY7qHHOMoIruIxEGVTAQ7t8cAgq2vD4KtZ4pg65ki2HqmviSmFezkh/eiHVbtGZ0tiAh2tkhznbgIINhxkdXkItgajtEUBFvPFMHWM0Ww9Ux9Sawn2LUHD9nvNm6y6u277IVfvmlXX3lxnVnqI0eO2Ctvrrfq7Tvtf/7opmDnjFx9uYcTf3DHNAt3Cknefi+O+3f6ywQAACAASURBVGYGOw6qZCLYuT0GEGx9fRBsPVMEW88UwdYz9SWxnmAfPnzY3tnwn7Z81Rr7vyvXWJdOX7Li4qJEf1uUN7dL+51j11x1iXVo38YXDrJ+INgylARFCCDYuT0cEGx9fRBsPVMEW88UwdYz9SUx7RIR91Dfz1981b773y+15mWlvvQ39n4g2LEjLsgLINi5XXYEW18fBFvPFMHWM0Ww9Ux9SSyIXUSyWSwEO5u0C+daCHZu1xrB1tcHwdYzRbD1TBFsPVNfEhsU7Kpt1fb4vH+1zX/YVq+/p3f6kj1w50hr26aVLywk/UCwJRgJSSKAYOf2kECw9fVBsPVMEWw9UwRbz9SXxLSC7R52/N+PLbQzz+hkf9Xv7OCbDW/83n+z33+0xX72wq/ttr/9jn3ty1194SDrB4ItQ0lQhACCndvDAcHW1wfB1jNFsPVMEWw9U18SG9ymL/ziFdfZp59fYbeNvCbYNeTTqs9syS9+ZeNu+m5efFV6NouFYGeTduFcC8HO7Voj2Pr6INh6pgi2nimCrWfqS2Jawd69Z589NOc5u3P031jLFuU265l/s5uu++92Svs2lm/7YGezWAh2NmkXzrUQ7NyuNYKtrw+CrWeKYOuZIth6pr4kphVst13f4/OXWv+Lv2Hn9vmyzV30CzulXZtge74NH262p/5luf2v+0ZZReuWvrCQ9MMJ9mfb9kqyCIFAlMCM/9PfzvxyuxOG0rJ5iZWVltiOPbUnnEXAMQIItn4kINh6pgi2nimCrWfqS2KDDzkeqD1ozUqKraSkxD6v3mH/Y9o8e+XN39mpp7S16f9wq134zd6+cJD146NPdtme/YdkeYUeVNqs2Nw27AcOHil0FEH/O5za4oQ5INgnjLBeAIKtZ4pg65ki2HqmCLaeqS+Jjdqm78iRo+aWjrRs0Zy11w2MgKrq/b6Mj5Pej1blzaxZSZHt3HvwpN+LLzeAYOsriWDrmSLYeqYItp4pgq1n6kvicQX7T3/eaW+t+8D++Pl2+97gy6xVy3KrqTn2fy3n8tekn8wCIdg6+gi2jmWYhGDrmSLYeqYItp4pgq1nimDrmfqS2KBgv/7WBvvHh5+xLp1OteKiInvwgb+z9m0r7L0PN9u/r/i13f131zGTnWIkINi6jweCrWOJYOtZhokItp4tgq1nimDrmSLYeqa+JKYVbDdLPfWfFtl13+5vnTqeYuGWfU6w/7x9V/D7/XfcGAg3r7oEEGzdiECwdSwRbD1LBDs+pgi2ni2CrWeKYOuZ+pKY8T7YUcFmm76Gy49g6z4eCLaOJYKtZ4lgx8cUwdazRbD1TBFsPVNfEtMK9r79NTZ15rM2ctiVwa4hUcF+5c11VvnyWzZx3HArK23mCwtZPxBsGUpDsHUsEWw9SwQ7PqYItp4tgq1nimDrmfqSeNw12NNn/Yv9zZBvWeXLa23YX3/L3tnwn8HP0/7HLXb+uT194SDrB9v0yVAGQYW4TV/r1mXWvLxECzKSxkOOerSswdYzRbD1TBFsPVMEW8/Ul8Q6gn306FE7fPiINWv2xV/uW/74J/vZil/bq79Zb4cOH7ZvfP2rNvy7A+30zl/yhYG0H3zRjBRnwYW1bdvcnnhqEIKdZ5VHsPUFQ7D1TBFsPVMEW8/Ul8Q6gu32uHYz1neM/p61bdPaPtz0qX21R1eWgTSi2nxVeiNg0bQegf92ZXcEOw/HBYKtLxqCrWeKYOuZIth6pr4k1hHs6MOLroPRdde+dDjufiDYcRP2Ox/Bzs/6Itj6uiHYeqYItp4pgq1n6ktiHcE+ePCQPTj7OXOi3e8bvWz5qjV2w3cHWOtW9b+euXlZqX29Zw9mt5NGAoLty0fj5PQDwT453E/0qgj2iRKsfz6CrWeKYOuZIth6pr4k1nvIcX/NAVv567ds44ef2Mtr3rVL+52T8hsb21S0Snyzoy8wFP1AsBUUCzcDwc7P2iPY+roh2HqmCLaeKYKtZ+pLYtpdRA4fPmzPLH7Bhg6+lC+TaUS1EexGwKJpPQIIdn4OCgRbXzcEW88UwdYzRbD1TH1JbHCbPl86mc1+INjZpO3ftRDs/Kwpgq2vG4KtZ4pg65ki2HqmviQi2OJKIthioAUWh2DnZ8ERbH3dEGw9UwRbzxTB1jP1JRHBFlcSwRYDLbA4BDs/C45g6+uGYOuZIth6pgi2nqkviQi2uJIIthhogcUh2PlZcARbXzcEW88UwdYzRbD1TH1JzEnBju7H3b5tRSysN22uskVLK+2esden3CWlqRdFsJtKjvMcAQQ7P8cBgq2vG4KtZ4pg65ki2HqmviQi2Ah23o/l9etvCvrQp8/TwZ+TJ19i9913gZWVldTp24YN1Yk24YH+/c+wBQsGW5curYO35s9fZ6NHvxD8PG/eVTZq1NmJjC1b9tjIkctt1apPEte5886+9thja23SpFeC9yorh9mAAd3qMY3mhveYfC6Cnb9DEcHW1w7B1jNFsPVMEWw9U18SEWwEO6/HspPrrl0r7MMPt1vfvgvT9sW1e+21qoQ8hw2dELvXwIFLbMSI3jZ16mU2ceJqW7hwQyDL4bHkYCfxTpBraw/b7NlvJwQ7uV1ypjvupH7mzAFWXl5iixa9V+dcZrDzczgi2Pq6Idh6pgi2nimCrWfqS2JeCPaMJ5fYHz+rtsl33xxwn/TwU7as8vXg5x/fe7MNHXxZ8O2TTz+/wvbu3W/P/WxVcGzIwAuDc8rLy6ymprbOeddf0z9oEy4RcdeY/+yy4L1zevWw2dPuCvb/Xrp8tZ16Sjv7ReWr9tt1H9oTD/4oaHPrvY9Y1bbqOvfgfmGJSPY+Gk5yhwzpYcuWbQr+TCfYrt3w4b1szJgXE7PPoejOnXtlHcl1Ir51655AuJ1gf/zxrnpS7s5du3ZE4rru+uEMdnLvU0l6+F779uVBRvRcBDt740d5JQRbSfNYFoKtZ4pg65ki2HqmviTmtGDfNWaYPTp3iV34zd6BRLuXE+FL+51t55/bs87vX+nexW6b8KgNu/ryoG0o1O5319aJ8sd/2Gbjbzk2K+l+f/2tDQkBjxbUHXMvl+N+nvPTnwVi3aNb53p1T14vjmBn/6PhlnJcdFHness/wjtJNxOdanY52tbJdu/eHRIdWrlycyDe4cvNRCcLerT3qY6H/yhw/xgIJR3Bzv6YUV8RwVYTRbD1RM0QbD1VBFvP1JfEnBXs+6fOC2alr/0vYXbA3e9Oot99b1Md/m4W+4pLvmFTZy6yieOGJ7550slx1y6n2dln9bCH5jxnw4cOTEhy8kOO0RlsFx7OjEdlO7yoOzc6gx2d8Uaws//RaEiwU0l0eIfu2IQJ/WzcuJWJme10Wa7trFkDbfHi9xMz2scT7OSscGnItGlrgiUoCHb2x0pcV0Sw9WSZwdYzRbD1TBFsPVNfEnNasH9403ds6fKXE2Lc0O4iqY5lKtjLV71eb3Y7OoMd/hxKvpP/e8ZeF8g6M9gn/6PQkGC7GelOnVqnnN0+3gx2cs+SZ8IbEuzw4ckVKz5KCHnykhME++SPHdUdINgqkl/kINh6pgi2nimCrWfqS2LOCnY4G719x257aM7zNmXi6GBm2s00u1e41CMsREOCfbwlIrMX/My6n96xztKScFlK8gy2m72O3s+b72y0GT9ZnFizzQx29j8a6QT7eDPMqY5H12CfiGAnr/sOZ8ArKsrqAYouPWENdvbHj+KKCLaCYt0MBFvPFMHWM0Ww9Ux9Scx5wXZSHZXYFs2b13lYsXPHDsH66PbtKtIuEXGCnfyQ4x2jv2d79tXYbSOvsf0HDiSWnri8v712kLVs0TyxBjs6g+1+dtL9wINPBWPAPSzZqlULu+m6QcE/ABDs7H800gl2uveTH2QMZ7idBM+YcYXNmVN/V5Bw15DolnwNCXy6XUuidJjBzv5YieuKCLaeLIKtZ4pg65ki2HqmviTmpGDnM1wEO/vVSyXSqZZohHcWFex0+2Anv++245s+/Y06O36kE2wn42PHnmfjx78UrLVO90Kwsz9W4roigq0ni2DrmSLYeqYItp6pL4kItriSCLYYaIHFsUQkPwuOYOvrhmDrmSLYeqYItp6pL4kItriSCLYYaIHFIdj5WXAEW183BFvPFMHWM0Ww9Ux9SUSwxZVEsMVACywOwc7PgiPY+roh2HqmCLaeKYKtZ+pLIoItriSCLQZaYHEIdn4WHMHW1w3B1jNFsPVMEWw9U18SEWxxJRFsMdACi0Ow87PgCLa+bgi2nimCrWeKYOuZ+pKIYIsriWCLgRZYHIKdnwVHsPV1Q7D1TBFsPVMEW8/Ul0QEW1xJBFsMtMDiEOz8LDiCra8bgq1nimDrmSLYeqa+JCLY4koi2GKgBRaHYOdnwRFsfd0QbD1TBFvPFMHWM/UlEcEWVxLBFgMtsDgEOz8LjmDr64Zg65ki2HqmCLaeqS+JCLa4kgi2GGiBxSHY+VlwBFtfNwRbzxTB1jNFsPVMfUlEsMWVXLz0Azt0+Kg4tXDjiouKgs4fOVo4TC+6uIs1Ly+Jregtm5dYWWmJ7dhTG9s1Ci0YwdZXHMHWM0Ww9UwRbD1TXxIRbHElDx85atu214hTCzeuZfNm1qykyHbtO1i4EMQ9R7DFQM0MwdYzRbD1TBFsPVMEW8/Ul0QEO4ZKVlXvjyG1MCNblR8T7J17EWzVCECwVSS/yEGw9UwRbD1TBFvPFMHWM/UlEcGOoZIItg4qgq1jGSYh2HqmCLaeKYKtZ4pg65ki2HqmviQi2DFUEsHWQUWwdSwRbD3LMBHB1rNFsPVMEWw9UwRbz9SXRAQ7hkoi2DqoCLaOJYKtZ4lgx8cUwdazRbD1TBFsPVNfEhHsGCqJYOugItg6lgi2niWCHR9TBFvPFsHWM0Ww9Ux9SUSwxZVkFxEtUHYR0fJ0aazB1jNliYieKYKtZ4pg65ki2HqmviQi2OJKsg+2Fqiv+2Bf3v8MLahGpCHYjYCVYVMEO0NQjWiGYDcCVoZNEewMQTWiGYLdCFgF1hTBFhecb3IUA/Uw7saRvW36jCtOWs8QbD16BFvPFMHWM0Ww9UwRbD1TXxIRbHElEWwxUA/jEGz/iopg62uKYOuZIth6pgi2nqkviQi2uJIIthioh3EItn9FRbD1NUWw9UwRbD1TBFvP1JdEBFtcSQRbDNTDOATbv6Ii2PqaIth6pgi2nimCrWfqSyKCLa4kgi0G6mEcgu1fURFsfU0RbD1TBFvPFMHWM/UlEcEWVxLBFgP1MA7B9q+oCLa+pgi2nimCrWeKYOuZ+pKIYIsriWCLgXoYh2D7V1QEW19TBFvPFMHWM0Ww9Ux9SUSwxZVEsMVAPYxDsP0rKoKtrymCrWeKYOuZIth6pr4kItjiSiLYYqAexiHY/hUVwdbXFMHWM0Ww9UwRbD1TXxIRbHElEWwxUA/jEGz/iopg62uKYOuZIth6pgi2nqkviQi2uJIIthhoBnHr198UtOrT5+k6rUeM6G2zZg20iooyq609bNOnv2GTJr2Sto07sHLlZhs4cEmiTf/+Z9iCBYNt48bqxPuTJ19i9913gZWVldTJ2rChOrgHdz+9e3cIjqW6LoKdQVHzrAmCrS8Ygq1nimDrmSLYeqa+JCLY4koi2GKgx4lzMtu1a4V9+OF269t3YaJ1KNeLF79vo0e/kDZl7doRtmzZpkC83TkzZlxhc+a8HfweynV5eYm9/fZndcQ7OdDdx2uvVVlV1R4777zT7Nvf/regybx5V9mgQWfayJHLbdWqT4L3EOzsjpFsXA3B1lNGsPVMEWw9UwRbz9SXRK8E+813NgZ1Of/cnietPgh29tC7meQhQ3oEguz+jAp2ZeWw4Eais9GZ3Fkoyk7KnRx3797GPv54V/Bnuix3H8OH97IxY15MSHR4rVTHEOxMKpFfbRBsfb0QbD1TBFvPFMHWM/Ul0RvBdnL9gzumJeryzOMTAtGe8eQSm//ssuD9UTcMsfG3DDPX9uU164Kf3cu1ca/o75f2O9u+0r2L3TbhUXv3vU11zne/LF2+2h548Kl610Ows//RcCJ80UWd6ywRcTPTW7bssauu6h4s5XA/R2eRU92lm7GeO/dKW7TovTpLSY4n6w0dd8K+deueOnKOYGd/jMR9RQRbTxjB1jNFsPVMEWw9U18SvRHsUHq7djktMYPtJNi9hg6+LPgz/P28Pl+xRUsr7Z6x19v+Awfsn5469n/n//Dm71qL5s1t9oKf2U3XDbL2bSsSda6pqbWH5jxnw4cOtPbtKuzp51fYbSOvsfLysjpjAcHO/kcjWbDDpR3uTkKpTiW6yXeaTpQbEmi3rGTq1Mts4sTVtnDhhiAyukY7XJcdvRaCnf0xEvcVEWw9YQRbzxTB1jNFsPVMfUn0VrCdEE96+ClbVvl6nVq5WWwnxqEsV+/YZZ9u+Sxo4+S8Q7s2deQ7OoPduWMHe+LBH1mPbp0TM+PhTHl4EQQ7+x+NVIKdPBPd0DIOd8epZsHDnjQk2O5Yp06t6z1gGZ7rcq+99iy7/fbKhIAj2NkfI3FfEcHWE0aw9UwRbD1TBFvP1JdErwU7lGgnxMmvcDb7T3/eaQMv7Rscrnx5rZ16Stvg58H9LwwEfdjVlwcz4tEZ7GheuAQlFG0EO/sfjVRyHF1LHc4qJ6/Tjkpw8oOI0V6kE+x0S0qi56Zqg2Bnf4zEfUUEW08YwdYzRbD1TBFsPVNfEr0TbFeY6JKQ19/aYJPvvrneUo5Nm6uCmepWrVoEM9ru5ZaG7N27P7EM5P6p8+yesdcFM9au/f3T5tmUCaOD36Mvt6bbzYK76yLY2f9opBLs5N07oktEoj+n2uUjuQfpBDvVdceP/0ubMeM3iQhmsLM/Hk7GFRFsPXUEW88UwdYzRbD1TH1J9EqwnQTfeu8jVrWt2lI95OiKFr6/fefu4AFGN0OdTsijD04OGXih/cVpHew7V10SrMGOLh05p1cPmz3trmDNNoKd/Y9GuuUdTowHDOgW3FB0LXQo2FOmrAn2uO7SpXWdm05eN51KsMN13itWfFRnG0B3L6NGnZ3IYx/s7I+Hk3FFBFtPHcHWM0Ww9UwRbD1TXxK9EuxcKAqCnQtVyO17YIlIbtenKXeHYDeFWsPnINh6pgi2nimCrWfqSyKCLa4kgi0G6mEcgu1fURFsfU0RbD1TBFvPFMHWM/UlEcEWVxLBFgP1MA7B9q+oCLa+pgi2nimCrWeKYOuZ+pKIYIsriWCLgXoYh2D7V1QEW19TBFvPFMHWM0Ww9Ux9SUSwxZVEsMVAPYxDsP0rKoKtrymCrWeKYOuZIth6pr4kItjiSiLYYqAexiHY/hUVwdbXFMHWM0Ww9UwRbD1TXxIRbHElEWwxUA/jEGz/iopg62uKYOuZIth6pgi2nqkviQi2uJIIthioh3EItn9FRbD1NUWw9UwRbD1TBFvP1JdEBFtcSQRbDNTDOATbv6Ii2PqaIth6pgi2nimCrWfqSyKCLa4kgi0G6mEcgu1fURFsfU0RbD1TBFvPFMHWM/UlEcEWV9IJ9mfb9opTifOJwNfOam/TZ1xx0rrUsnmJlZWW2I49tSftHny7MIKtryiCrWeKYOuZIth6pr4kItjiSn70yS7bs/+QOLVw40qbFVtxkdmBg0e8gtDh1BYnrT8Ith49gq1nimDrmSLYeqYItp6pL4kIdgyVrKreH0NqYUa2Km9mzUqKbOfeg4UJIIZeI9h6qAi2nimCrWeKYOuZIth6pr4kItgxVBLB1kFFsHUswyQEW88UwdYzRbD1TBFsPVMEW8/Ul0QEO4ZKItg6qAi2jiWCrWcZJiLYerYItp4pgq1nimDrmfqSiGDHUEkEWwcVwdaxRLD1LBHs+Jgi2Hq2CLaeKYKtZ+pLIoIdQyURbB1UBFvHEsHWs0Sw42OKYOvZIth6pgi2nqkviQh2DJVEsHVQEWwdSwRbzxLBjo8pgq1ni2DrmSLYeqa+JCLY4kqyTZ8WaC5u03cyt9hT0OUhRwXFuhmswdYzRbD1TBFsPVMEW8/Ul0QEW1xJvmhGDDTH4u6fdJGd369Tjt1V424HwW4cr0xaI9iZUGpcGwS7cbwyaY1gZ0KpcW0Q7MbxKqTWCLa42nxVuhhojsX9+7KhCHaO1SQXbgfB1lcBwdYzRbD1TBFsPVNfEhFscSURbDHQHItDsHOsIDlyOwi2vhAItp4pgq1nimDrmfqSiGCLK4lgi4HmWByCnWMFyZHbQbD1hUCw9UwRbD1TBFvP1JdEBFtcSQRbDDTH4hDsHCtIjtwOgq0vBIKtZ4pg65ki2HqmviQi2OJKIthioDkWh2DnWEFy5HYQbH0hEGw9UwRbzxTB1jP1JRHBFlcSwRYDzbE4BDvHCpIjt4Ng6wuBYOuZIth6pgi2nqkviQi2uJIIthhojsUh2DlWkBy5HQRbXwgEW88UwdYzRbD1TH1JRLDFlUSwxUBzLA7BzrGC5MjtINj6QiDYeqYItp4pgq1n6ksigi2uJIItBppjcQh2jhUkR24HwdYXAsHWM0Ww9UwRbD1TXxIR7EZWcuny1cEZQwdflvJMBLuRQPOsOYKdZwXL0u0i2HrQCLaeKYKtZ4pg65n6kohgN7KSCHYjgTXQvH//M2zBgsG2cWO1DRy4pF7LESN626xZA23x4vdt9OgXUialyqisHGYDBnSr137+/HWJnPXrb7LevTsEbVau3Fzn+g0dQ7B19fcpCcHWVxPB1jNFsPVMEWw9U18SEexGVhLBbiSwNM1DMS4vL7G33/4spWCvXTvC2rVrbi+99GlKwc4kw13eifrUqZfZxImrbeHCDeYE2r369Hm63t01dMw1RrA19fctBcHWVxTB1jNFsPVMEWw9U18SC0awt+/cbbdNeNTefW9TULtRNwyx8bcMM/f+08+vsL885ywbO2FG4n0n0g88+FTQtnPHDvbEgz+yHt06m3t//fsf2+rX37GqbdXB8Wcen2Dnn9sz+JklIpl9NObNu8q6d29jH3+8K/gzeQbbHb/oos62deueoE2qGezjZYR34ma03ctdY/LkS2z48F42ZsyLtmrVJ3VutqFjYUMEO7P6FlorBFtfcQRbzxTB1jNFsPVMfUksGMGOFqymptYemvOcDR860Nq3qwjE+/xv9AqEO9XrzXc22str1gXHnWAv+Y9f2uxpd1n7thXmjrnfJ999s5WXlyHYjfxkROU3PNXNOE+Y0M/GjVtp99/fL61gpxLo5Mu7We65c6+0RYves0mTXjEn5b16dbBu3dpYly6trbb2sE2f/sZxjyHYjSxsgTVHsPUFR7D1TBFsPVMEW8/Ul8SCEezkGexwVtoJ9tSZi2ziuOGBMIev6Ay2ey+c8U5eIhLOgN828hoEuwmfilSC7ZaGLFu2KZBedzzdDHYmgh3OhIfLQVzepZeeXkeqBw0600aOXB7IfLpj4Ww3M9hNKHIBnIJg64uMYOuZIth6pgi2nqkviQUh2G7GetLDT9mwqy8PlnIkz2AnC3byrHTyDLYrfriLCIJ9Yh+FZMEOl32ES0ZORLDDNdorVnyUWGKSfL3oDPfFF3cOOhNeO3n22x1DsE+s3r6ejWDrK4tg65ki2HqmCLaeqS+JBSHYToLvnzrP7hl7XbCOetPmKrt/2jybMmF0sEQkWbDdLPXHf9iWWDIy48ljO1yES0QQbN3wjwpvKMRu6Ubya8OG6pQPJbp2qWbB3fup1lQnz2i7a86cOcCmTVtj3/pW12DddzjbHT3mHo5EsHV19y0JwdZXFMHWM0Ww9UwRbD1TXxILQrBdsdws9A/umBbUbcjAC+0vTutg37nqkpSCHc54L6t8PWjvlo/s219jt9x4dbAGG8HWDf90chxeITqD7dZmz5hxhc2Z83awfCTaxv2c/KCk2xHktdeq6jwgmZzhhDtcIuLEPpofPcYSEV3NfUxCsPVVRbD1TBFsPVMEW8/Ul8SCEexsFYxdRBpHOi7BdrPXY8eeZ+PHvxRszRd9uWP33XeBlZWV2O7dtXb77ZWJNg0dYwa7cbUtpNYItr7aCLaeKYKtZ4pg65n6kohgiyuJYIuB5lgca7BzrCA5cjsItr4QCLaeKYKtZ4pg65n6kohgiyuJYIuB5lgcgp1jBcmR20Gw9YVAsPVMEWw9UwRbz9SXRARbXEkEWww0x+IQ7BwrSI7cDoKtLwSCrWeKYOuZIth6pr4kItjiSiLYYqA5Fodg51hBcuR2EGx9IRBsPVMEW88UwdYz9SURwRZXEsEWA82xOAQ7xwqSI7eDYOsLgWDrmSLYeqYItp6pL4kItriSCLYYaI7FIdg5VpAcuR0EW18IBFvPFMHWM0Ww9Ux9SUSwxZVEsMVAcywOwc6xguTI7SDY+kIg2HqmCLaeKYKtZ+pLIoItriSCLQaaY3EIdo4VJEduB8HWFwLB1jNFsPVMEWw9U18SEWxxJRFsMdAci0Owc6wgOXI7CLa+EAi2nimCrWeKYOuZ+pKIYIsriWCLgeZYHIKdYwXJkdtBsPWFQLD1TBFsPVMEW8/Ul0QEW1zJxUs/sEOHj4pTCzeuuKgo6PyRo7nBtFWrUju/X6e8LkjL5iVWVlpiO/bU5nU/cunmEWx9NRBsPVMEW88UwdYz9SURwRZX8vCRo7Zte404tXDjWjZvZs1KimzXvoOFC0HccwRbDNTMEGw9UwRbzxTB1jNFsPVMfUlEsGOoZFX1/hhSCzOyVfkxwd65F8FWjQAEW0XyixwEW88UwdYzRbD1TBFsPVNfEhHsGCqJYOugItg6lmESgq1nimDrmSLYeqYItp4pgq1n6ksigh1DJRFsHVQEW8cSwdazDBMRbD1bBFvPFMHWM0Ww9Ux9SUSwY6gkgq2DimDrWCLYepYIdnxMEWw9WwRbzxTB1jP1JRHBjqGSCLYOKoKtY4lg61ki2PExRbD1bBFsPVMEW8/Ul0QEW1xJdhHRAmUXAyH9rwAAFlRJREFUES1Pl8YabD1TlojomSLYeqYItp4pgq1n6ksigi2uJPtga4Hm2j7Yl/c/Q9vBk5CGYOuhI9h6pgi2nimCrWeKYOuZ+pKIYIsryTc5ioHmUNxDM66wG0b2zqE7atqtINhN49bQWQi2nimCrWeKYOuZIth6pr4kItjiSiLYYqA5FIdg51AxcuxWEGx9QRBsPVMEW88UwdYz9SURwRZXEsEWA82hOAQ7h4qRY7eCYOsLgmDrmSLYeqYItp6pL4kItriSCLYYaA7FIdg5VIwcuxUEW18QBFvPFMHWM0Ww9Ux9SUSwxZVEsMVAcygOwc6hYuTYrSDY+oIg2HqmCLaeKYKtZ+pLIoItriSCLQaaQ3EIdg4VI8duBcHWFwTB1jNFsPVMEWw9U18SEWxxJRFsMdAcikOwc6gYOXYrCLa+IAi2nimCrWeKYOuZ+pKIYIsriWCLgeZQHIKdQ8XIsVtBsPUFQbD1TBFsPVMEW8/Ul0QEW1xJBFsMNIfiEOwcKkaO3QqCrS8Igq1nimDrmSLYeqa+JCLY4koi2GKgORSHYOdQMXLsVhBsfUEQbD1TBFvPFMHWM/UlEcE+wUpu37nbps5cZBPHDbf2bSsMwa4LdP36m4I3+vR5OiXpysph1rNnBxs5crmtWvVJvTbu/N69OwTvr1y52QYOXGKTJ19i9913gZWVldRpv2FDdXCdESN626xZA62ioiw4Pn/+Ohs9+oXg53nzrrJRo84Oft69u9Zuv73SFi7cUO9Ybe1hmz79DZs06ZXENRDsE/yweHw6gq0vLoKtZ4pg65ki2HqmviR6I9ibNlfZQ3OetykTRweim60Xgp2etJPjrl0r7MMPt1vfvgvrNXSiPHx4L6upOWzjxq2sJ9hOhi+6qHMgzf37n2Fz515pixa9V0d6w1B3rddeqwpE2v28deuehIyPHXuejR//UtB0xowrbM6ct4MMJ/edOrVOSHn0mLv2oEFn1hF/BDtbn6r8uw6Cra8Zgq1nimDrmSLYeqa+JOatYDuh/vCjLXbV5eef1Fog2KnxO3keMqSHLVu2KfgzWbBDYX7ppU8DiU4l2FFpdleJCnH0qqGojxnzonXp0tqmTr3MJk5cnZiZdue518cf70oIu/s9Ku3udyf7LsPNpLtZ8OQcBPukftRy+uIItr48CLaeKYKtZ4pg65n6kpiXgu3k+tZ7H7GqbdVBHX587812Xp+v2KKllXbP2Outatuf7N9feMX++Fm1Lat8PWgz6oYhNv6WY6L15jsb7Qd3TKtTQ3f8tpHX2KSHn0qc4xp07tjBnnjwR0Hb5GsOHXyZIdgNfxSis9DRlk56nfD+6lef2oQJ/eoJdqoZ64ayXLZbPpJKjDMRbDejHZ35jv4c3jeC7ct/9vT9QLD1TBFsPVMEW88UwdYz9SUxLwU7lORPt3xmTnLdy0l3VLCdDE+5f4ydf27PQILvnzrP7hl7nXXueKo9NOc5Gz50oPXo1jk4r/LltXbLjVcH4v3ymnUJEX/yn//DBl7aN2gXfUWl2r3PGuz0H4dUUhzObrtZbSfE6QR75swBNm3amsRMdHSmOlyvnSzUTswXLBhsK1Z8FCwXCddjv/HGVnv11SoLl4u4ddfu3tzx6FrrcM13uN472jME25f/7On7gWDrmSLYeqYItp4pgq1n6kuit4IdynZ5+bEH3UJZTiXYYdt172+qI9gznlxil/Y7O5D05Fnzc3r1sNnT7gqyEezMBdsJcFScGxLs5DXXqWQ91bKR6EOQ7kFGtwZ8+/aaYIbbtR8woNuxf5Rt2hH86dZ1uzbuwcjFi98PxDzVw5cIti//2dP3A8HWM0Ww9UwRbD1TBFvP1JfEghNsNxsdXSISLgFx79fU1NZZIhIuK4nOgLt2zGBnPvyTpTi6i0c0JdWuHcdbg328Bx/D/LVrRwRrwaM7grhjUbm/4YZeddZnu+PJ5yHYmde90Foi2PqKI9h6pgi2nimCrWfqS2JeC3Z0OUfyEpF0M9hOkJcuX21du5wWzExHX06cn35+RbAWO5z5DmY6k3YocYI+4yeLmcHO4FOQbt10eGryDHZ07XN0Jw/XPrr0w/1+vGzXJt2DkclLSZJ3DXH3Fd1VxGUh2BkUvECbINj6wiPYeqYItp4pgq1n6kti3gq2k+HbJjxq7763KeVDjg0JdrrlHm57P7csZP6zyxL1dQ9QunXeTsofePCp4P3rr+lvrVq1sJuuGxT8zhKR9B+H40lwQ4LtUlPtg+3eTxbk6B1El4GEe2NHz3E7jbhXdH/sUMbD5SOpjiPYvvxnT98PBFvPFMHWM0Ww9UwRbD1TXxLzVrCbWgA3+7zkP35pk+++OTFL7eT54MFDtnbdBzbs6ssTM9vJO4Rkck2+aCYTSvnZBsHOz7pl464RbD1lBFvPFMHWM0Ww9Ux9SSxIwY4uLXGFdLPW/b7R01b9+reJ3UXc+9FlJ9ElIw0VH8H25aNRvx8Itr+1PdGeIdgnSrD++Qi2nimCrWeKYOuZ+pJYcIKd/CCjK2S4DCR5f+xwp5DGfDMkgu3LRwPB9reS+p4h2HqmCLaeKYKtZ4pg65n6klhwgh134RDsuAmfvHxmsE8e+1y/MoKtrxCCrWeKYOuZIth6pr4kItjiSiLYYqA5FIdg51AxcuxWEGx9QRBsPVMEW88UwdYz9SURwRZXEsEWA82hOAQ7h4qRY7eCYOsLgmDrmSLYeqYItp6pL4kItriSCLYYaA7FIdg5VIwcuxUEW18QBFvPFMHWM0Ww9Ux9SUSwxZVEsMVAcyjuoUevsBtG9M6hO2rarbRsXmJlpSW2Y09t0wI4qx4BBFs/KBBsPVMEW88UwdYz9SURwRZXEsEWA82hOAQ7h4qRY7eCYOsLgmDrmSLYeqYItp6pL4kItriSCLYYaA7FsUQkh4qRY7eCYOsLgmDrmSLYeqYItp6pL4kItriSTrA/27ZXnEpcLhAYdl1Pu2EkS0RyoRa5dg8Itr4iCLaeKYKtZ4pg65n6kohgiyv50Se7bM/+Q+LUwo0rbVZsxUVmBw4eyQkIHU5tkRP3cSI3wRrsE6GX+lwEW88UwdYzRbD1TBFsPVNfEhHsGCpZVb0/htTCjGxV3syalRTZzr0HCxNADL1GsPVQEWw9UwRbzxTB1jNFsPVMfUlEsGOoJIKtg4pg61iGSQi2nimCrWeKYOuZIth6pgi2nqkviQh2DJVEsHVQEWwdSwRbzzJMRLD1bBFsPVMEW88UwdYz9SURwfalkvQDAhCAAAQgAAEIQCAnCCDYOVEGbgICEIAABCAAAQhAwBcCCLYvlaQfEIAABCAAAQhAAAI5QQDBzokycBMQgAAEIAABCEAAAr4QQLBFlZzx5BKb/+yyIO3H995sQwdfJkourJiamlqb9PBTduE3e9dhuGlzld167yNWta3azunVw2ZPu8vat60oLDhN6G2Umzv9mccn2Pnn9gySQtbLKl8Pfo8ea8KlCuaUN9/ZaD+4Y1qiv9HPO0xPfBgsXb7aXn9rg02++2YrLy9jnDYRafJnP/rfTcZpE6Ga2fadu+22CY/au+9tss4dO9gTD/7IenTrHATiAU3n6uOZCLagqu4v3JfXrLPxtwwL/jJ4aM5zNnzowMSHTnCJgogI/6P//7d370FXlHUcwH+Ok6J4Vy4CCmNEXkLSEaE0JXS8IWmIkHnjog7mBRGkkdBEURQviA5ekdJXR+U2k2ilYwaVjZNZ2WQ5Wo1aNuk4Y3hJzZTm2em8czgeX9/3vC/rYfdz/mE47O6zz+e355zvPvvssvaNt+PwEUNbA3atabV3KWAa7GRyu+muH8TE8UdkJyPpB/fqm++PKy48Lft7CjLplU4G04/GvBvviQvPOdGJSxveyXT5Q2ti7KiDs/CX3GbNWxwXnDk++7wzbfBg/f9q6Ri9Z+Wj0b37FvGtU47JjJk2ZtrW9yTTxkwr4fr8KeNaByoqW5IDGjMt8loCdhdUN521fmXY4NYPXPryeuHvr2SB26v9AukL6m8vvxq79O2Z/Vm5ClD50b3gzG/UDTXtb6HcS1afqPTptdNHTgTTcTygXy9XXzpwmDDtANYnLFqxPGLk/tmARQrY6VU7YOE4bZ955fu09mpqvUEgpu0zrT4xqV1DDmifYZmWErA7We16X1ZGWDuHWvslVuvpKkFjvtWj1GkLtSPWbf14NNZi8ddKx+ayVauz6QzvvPce006UPB1/6eR64IC+8b37f5wFbKaNgybPi+Yvad3A5G+OygZ96l2t8tlvn/Ntd6+K/v16xzU335dNVxx16PDss1/vRFAOaJ9pkZcSsDtZ3drL8GlztSOunWyidKvXC9jVI9oJpHa0oHRIDXS42iz9yFZCTLoMn15+ENqHWj1/tXpeK9P2+dVbKn1nPvrzp+KMk0ZnAbA6YDtOG3etrFl9b8tXD9jHZ78B0ophWrVyf0Bl5P+okcPXm44nBzQAXMBVBOxOFtUIdicB66xuBHvDmxrF6hrj6jmZaeTVVYGOu9YOUtQGbKYdN623RuUEOt2TwbTjpvV+6yuDaedMGhM3Llm53r1XBiw6bly0NQTsLqiouVddgFi1idqAbQ5253zr3RNgHmbnTKvXrhyvaRTLfOGOu9Y+laWyhfSEhhvmnhvLH1yzXnAxX7jjxtVXqNLUG8dpY4a1v/XVV17kgMZMi7yWgN0F1a2eh5k2lx4zd/zoER+5y7gLmirFJmoDduXSXMW02rsyvaEUMA10sq0bbqv/rfZpGA00VYpVktMWm2+e3WybXrVPFWDa+cOgdqoN064xTY+Wqzz9gmljprW/PdUne3JAY6ZFXkvA7qLqev5lF0FGrPdYrspWPQe7477Vz2utXrvy3GbPwu0aU8/B7rhjW2vUBmzHaWO+1b9JaQuegd+YY+1a1TePVm4crSwjB3SNcVG2ImAXpZL6QYAAAQIECBAg0BQCAnZTlMFOECBAgAABAgQIFEVAwC5KJfWDAAECBAgQIECgKQQE7KYog50gQIAAAQIECBAoioCAXZRK6gcBAgQIECBAgEBTCAjYTVEGO0GAAAECBAgQIFAUAQG7KJXUDwIECBAgQIAAgaYQELCbogx2ggABAgQIECBAoCgCAnZRKqkfBAgQIECAAAECTSEgYDdFGewEAQIECBAgQIBAUQQE7KJUUj8IECBAgAABAgSaQkDAbooy2AkCBAgQIECAAIGiCAjYRamkfhAgQIAAAQIECDSFgIDdFGWwEwQIECBAgAABAkURELCLUkn9IECAAAECBAgQaAoBAbspymAnCBAgQIAAAQIEiiIgYBelkvpBgAABAgQIECDQFAICdlOUwU4QIECAAAECBAgURUDALkol9YMAgY1O4Mmnn40JU69s3e/NN/tM7Dfk8zHphKNi2D57xCabbNJmn9599z9x8TVLYtShX4qDhw9pXXblD38W96x8NG66clr02mn77P0PPvggrlp0b+w+cNcYc9RBG52VHSZAgMDGJCBgb0zVsq8ECBRKIAXsZatWx6UzJkW3bptlIfixx38bt7asigVzzopd+vT8xP62LH8k/rX2rThn8phs2fff/28WpB/7xW/i0pmT4sD9B2fvr33j7bhg7i0x7fSxscfn+n/idi1AgAABAo0LCNiN21mTAAECnRKoDdhpY6+vfTPOnrUwpk8ZF/sOHhTr1q2LX/76D7Hw9hXxzHMvxKDd+sWMM8fHl/f7QjbCnbbRsuyRmDfrjOi+Zbd45bXXY+71LfHFvQbGm2/9O6aedly23J+efzEW3L48rp49Jbbdpnun9tvKBAgQINC2gIDtCCFAgMCnJFBvBPvxJ5+JZQ+ujrkzJ2dB+Ok//iVuuGNFXDzt1Ojfr1e8/M/XYs61349Txx0eBwwdnAXqWfNuj++ce1Ls1r9PrHni6Wz0+oRjD4lbWh6IOdMnZttJ00ae/fNL8e2zTohNN930U+qxZgkQIFAOAQG7HHXWSwIEmlCgdg522sUjRw6LGVPGR++eO2RTRq69dVkMHNBnvXnTlRA9e+rJWa/mLmyJkQfuGwcN2zsWLl4Rew7qHwcNGxKXXX9XjD9mZOw1qH82bSTN7z7s4KFNKGGXCBAgUCwBAbtY9dQbAgQ2IoHaEewPP1wXv3vm+bhh8YqYPe2U6Ne7R3YT4/GjR8TQIbu39uyvL/4jrr75/rjiwtNi+223zkanX3r51Zg4/si4dMGdcdaEY7PR7DQ/+51334uxR4+I2VctzoJ7et+LAAECBDasgIC9YX1tnQABAh8rUG8Odlr4utuWxVZbdotTxh7eroCd5lcvue9H8fUjDozlD62Jy2ZOzuZjV94f97URsfSB1XHJ9AnZ+14ECBAgsGEFBOwN62vrBAgQ6FDATjc1XnvL0thm6y3j9BOPzqZ87Nq350emiDz801/Fd6dPiPRov/SEkIvm3xF9d+4RfXrtGCePPSxrM93kOOe6O6PHjtvF9ttuFWecNFo1CBAgQCAHAQE7B2RNECBAoJ7Ax00RuXzh3XHx+afGkD0/m93kuODWpXHJjIkxYJfe2U2OF81fkt3kWHn2dZqrnaaMPPSTJ2LRFefF3nvsljWXwvptdz+Y3SR5x3UzY/i+eyoEAQIECOQgIGDngKwJAgQIfFzArv6PZtIyew0aEFNPP671MXwpJD/1++di/qJ7Wx/Td/akMTHygH3W+49oHlnzZNy59OG48fKpscN2W7c2l0L83AUtsWjeedFv5x4KQYAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8AgJ2eWqtpwQIECBAgAABAjkICNg5IGuCAAECBAgQIECgPAICdnlqracECBAgQIAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8AgJ2eWqtpwQIECBAgAABAjkICNg5IGuCAAECBAgQIECgPAICdnlqracECBAgQIAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8AgJ2eWqtpwQIECBAgAABAjkICNg5IGuCAAECBAgQIECgPAICdnlqracECBAgQIAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8AgJ2eWqtpwQIECBAgAABAjkICNg5IGuCAAECBAgQIECgPAICdnlqracECBAgQIAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8AgJ2eWqtpwQIECBAgAABAjkICNg5IGuCAAECBAgQIECgPAICdnlqracECBAgQIAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8AgJ2eWqtpwQIECBAgAABAjkICNg5IGuCAAECBAgQIECgPAICdnlqracECBAgQIAAAQI5CAjYOSBrggABAgQIECBAoDwCAnZ5aq2nBAgQIECAAAECOQgI2Dkga4IAAQIECBAgQKA8Av8DuuYGIT8WozUAAAAASUVORK5CYII=
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_tf_idf</span><span class="p">,</span><span class="n">tf_idf_vect</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span><span class="n">desc</span><span class="o">=</span><span class="bp">False</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[84]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(6).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[84]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[77]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">tf_idf_vect2</span> <span class="o">=</span> <span class="n">TfidfVectorizer</span><span class="p">(</span><span class="n">tokenizer</span><span class="o">=</span><span class="n">my_tokenizer</span><span class="p">,</span><span class="n">lowercase</span><span class="o">=</span><span class="bp">True</span><span class="p">,</span><span class="n">max_features</span><span class="o">=</span><span class="mi">500</span><span class="p">)</span>
<span class="n">X_train_tf_idf2</span> <span class="o">=</span> <span class="n">tf_idf_vect2</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">teks_data</span><span class="o">.</span><span class="n">full_text</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[78]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="k">print</span><span class="p">(</span><span class="nb">list</span><span class="p">(</span><span class="n">tf_idf_vect2</span><span class="o">.</span><span class="n">vocabulary_</span><span class="o">.</span><span class="n">items</span><span class="p">())[</span><span class="mi">0</span><span class="p">:</span><span class="mi">3</span><span class="p">])</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf2</span><span class="o">.</span><span class="n">toarray</span><span class="p">())</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Memeriksa nilai dari beberapa vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf2</span><span class="o">.</span><span class="n">toarray</span><span class="p">()[</span><span class="mi">0</span><span class="p">,[</span><span class="mi">89</span><span class="p">,</span><span class="mi">306</span><span class="p">,</span><span class="mi">444</span><span class="p">]])</span>
<span class="k">print</span><span class="p">(</span><span class="s2">&quot;Banyaknya document x banyaknya vocabulary&quot;</span><span class="p">)</span>
<span class="k">print</span><span class="p">(</span><span class="n">X_train_tf_idf2</span><span class="o">.</span><span class="n">toarray</span><span class="p">()</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[(&#39;celaka&#39;, 89), (&#39;motor&#39;, 306), (&#39;tewas&#39;, 444)]
[[0.       0.       0.       ... 0.       0.       0.      ]
 [0.       0.       0.       ... 0.       0.       0.      ]
 [0.       0.       0.       ... 0.       0.       0.      ]
 ...
 [0.       0.       0.       ... 0.       0.       0.      ]
 [0.       0.       0.       ... 0.       0.       0.      ]
 [0.       0.       0.       ... 0.       0.391067 0.      ]]
Memeriksa nilai dari beberapa vocabulary
[0.26392208 0.964544   0.        ]
Banyaknya document x banyaknya vocabulary
(1002, 500)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="n">doc_plot</span><span class="p">(</span><span class="n">X_train_tf_idf2</span><span class="p">,</span><span class="n">tf_idf_vect2</span><span class="p">,</span><span class="n">n</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span><span class="n">desc</span><span class="o">=</span><span class="bp">False</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[85]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-python"><pre><span></span><span class="kn">from</span> <span class="nn">IPython.display</span> <span class="kn">import</span> <span class="n">Image</span>
<span class="n">Image</span><span class="p">(</span><span class="n">filename</span><span class="o">=</span><span class="s1">&#39;/content/drive/MyDrive/STA583_Genap_2022/Praktikum/Week5/newplot(7).png&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[85]:</div>




<div class="output_png output_subarea output_execute_result">
<img src="data:image/png;base64,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W0fhCCCAAAIIIIAAAjoKELB17Ao1IYAAAggggAACCBgrQMA2tnUUjgACCCCAAAIIIKCjAAFbx65QEwIIIIAAAggggICxAgRsY1tH4QgggAACCCCAAAI6ChCwdewKNSGAAAIIIIAAAggYK0DANrZ1FI4AAggggAACCCCgowABW8euUBMCCCCAAAIIIICAsQIEbGNbR+EIIIAAAggggAACOgoQsHXsCjUhgAACCCCAAAIIGCtAwDa2dRSOAAIIIIAAAgggoKMAAVvHrlATAggggAACCCCAgLECBGxjW0fhCCCAAAIIIIAAAjoKELB17Ao1IYAAAggggAACCBgrQMA2tnUUjgACCCCAAAIIIKCjAAFbx65QEwIIIIAAAggggICxAgRsY1tH4QgggAACCCCAAAI6ChCwdewKNSGAAAIIIIAAAggYK0DANrZ1FI4AAggggAACCCCgowABW8euUBMCCCCAAAIIIICAsQIEbGNbR+EIIIAAAggggAACOgoQsHXsCjUhgAACCCCAAAIIGCtAwDa2dRSOAAIIIIAAAgggoKMAAVvHrlATAggggAACCCCAgLECBGxjW0fhCCCAAAIIIIAAAjoKELB17Ao1IYAAAggggAACCBgrQMA2tnUUjgACCCCAAAIIIKCjAAFbx65QEwIIIIAAAggggICxAgRsY1tH4QgggAACCCCAAAI6ChCwdewKNSGAAAIIIIAAAggYK/B/Gxv9A57bjpcAAAAASUVORK5CYII=
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
<h2 id="Referensi">Referensi<a class="anchor-link" href="#Referensi">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<ul>
<li>Vajjala, Sowmya; Majumder, Bodhisattwa; Gupta, Anuj; Surana, Harshit. Practical Natural Language Processing. O'Reilly Media. </li>
<li><a href="https://github.com/taudata-indonesia/">https://github.com/taudata-indonesia/</a></li>
</ul>

</div>
</div>
</div>
    </div>
  </div>
</body>

 


</html>
