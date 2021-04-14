---
layout: post
title: Pengenalan Scikit Learn
categories: [Machine Learning,python]
excerpt: Scikit-learn (Sklearn) adalah salah satu package paling berguna  untuk machine learning  dengan Python. Package ini menyediakan pilihan alat yang efisien untuk machine learning seperti  klasifikasi, regresi, clustering, dan dimension reduction melalui antarmuka konsistensi dengan Python. Package  in  sebagian besar dibangun di atas NumPy, SciPy dan Matplotlib.
---

<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Pengenalan Scikit Learn</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>




<style type="text/css">
    pre { line-height: 125%; }
td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
.highlight .hll { background-color: var(--jp-cell-editor-active-background) }
.highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
.highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
.highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
.highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
.highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
.highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
.highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
.highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
.highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
.highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
.highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
.highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
.highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
.highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
.highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
.highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
.highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
.highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
.highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
.highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
.highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
.highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
.highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
.highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
.highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
.highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
.highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
.highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
.highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
.highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
.highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
.highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
.highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
.highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
.highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
  </style>



<style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
 * Mozilla scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */
[data-jp-theme-scrollbars='true'] {
  scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar. These selectors
 * will match lower in the tree, and so will override the above */
[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
  scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
}

/*
 * Webkit scrollbar styling
 */

/* use standard opaque scrollbars for most nodes */

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-corner {
  background: var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-thumb {
  background: rgb(var(--jp-scrollbar-thumb-color));
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-right: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

[data-jp-theme-scrollbars='true'] ::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
  border-bottom: var(--jp-scrollbar-endpad) solid
    var(--jp-scrollbar-background-color);
}

/* for code nodes, use a transparent style of scrollbar */

[data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar::-webkit-scrollbar,
[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-corner,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-corner {
  background-color: transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-thumb,
[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-thumb {
  background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
  border: var(--jp-scrollbar-thumb-margin) solid transparent;
  background-clip: content-box;
  border-radius: var(--jp-scrollbar-thumb-radius);
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-hscrollbar::-webkit-scrollbar-track:horizontal {
  border-left: var(--jp-scrollbar-endpad) solid transparent;
  border-right: var(--jp-scrollbar-endpad) solid transparent;
}

[data-jp-theme-scrollbars='true']
  .CodeMirror-vscrollbar::-webkit-scrollbar-track:vertical {
  border-top: var(--jp-scrollbar-endpad) solid transparent;
  border-bottom: var(--jp-scrollbar-endpad) solid transparent;
}

/*
 * Phosphor
 */

.lm-ScrollBar[data-orientation='horizontal'] {
  min-height: 16px;
  max-height: 16px;
  min-width: 45px;
  border-top: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] {
  min-width: 16px;
  max-width: 16px;
  min-height: 45px;
  border-left: 1px solid #a0a0a0;
}

.lm-ScrollBar-button {
  background-color: #f0f0f0;
  background-position: center center;
  min-height: 15px;
  max-height: 15px;
  min-width: 15px;
  max-width: 15px;
}

.lm-ScrollBar-button:hover {
  background-color: #dadada;
}

.lm-ScrollBar-button.lm-mod-active {
  background-color: #cdcdcd;
}

.lm-ScrollBar-track {
  background: #f0f0f0;
}

.lm-ScrollBar-thumb {
  background: #cdcdcd;
}

.lm-ScrollBar-thumb:hover {
  background: #bababa;
}

.lm-ScrollBar-thumb.lm-mod-active {
  background: #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
  height: 100%;
  min-width: 15px;
  border-left: 1px solid #a0a0a0;
  border-right: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
  width: 100%;
  min-height: 15px;
  border-top: 1px solid #a0a0a0;
  border-bottom: 1px solid #a0a0a0;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-left);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='horizontal']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-right);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='decrement'] {
  background-image: var(--jp-icon-caret-up);
  background-size: 17px;
}

.lm-ScrollBar[data-orientation='vertical']
  .lm-ScrollBar-button[data-action='increment'] {
  background-image: var(--jp-icon-caret-down);
  background-size: 17px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Widget, /* </DEPRECATED> */
.lm-Widget {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  cursor: default;
}


/* <DEPRECATED> */ .p-Widget.p-mod-hidden, /* </DEPRECATED> */
.lm-Widget.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-CommandPalette, /* </DEPRECATED> */
.lm-CommandPalette {
  display: flex;
  flex-direction: column;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-CommandPalette-search, /* </DEPRECATED> */
.lm-CommandPalette-search {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-content, /* </DEPRECATED> */
.lm-CommandPalette-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  min-height: 0;
  overflow: auto;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-CommandPalette-header, /* </DEPRECATED> */
.lm-CommandPalette-header {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}


/* <DEPRECATED> */ .p-CommandPalette-item, /* </DEPRECATED> */
.lm-CommandPalette-item {
  display: flex;
  flex-direction: row;
}


/* <DEPRECATED> */ .p-CommandPalette-itemIcon, /* </DEPRECATED> */
.lm-CommandPalette-itemIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemContent, /* </DEPRECATED> */
.lm-CommandPalette-itemContent {
  flex: 1 1 auto;
  overflow: hidden;
}


/* <DEPRECATED> */ .p-CommandPalette-itemShortcut, /* </DEPRECATED> */
.lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-CommandPalette-itemLabel, /* </DEPRECATED> */
.lm-CommandPalette-itemLabel {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-DockPanel, /* </DEPRECATED> */
.lm-DockPanel {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-widget, /* </DEPRECATED> */
.lm-DockPanel-widget {
  z-index: 0;
}


/* <DEPRECATED> */ .p-DockPanel-tabBar, /* </DEPRECATED> */
.lm-DockPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-DockPanel-handle, /* </DEPRECATED> */
.lm-DockPanel-handle {
  z-index: 2;
}


/* <DEPRECATED> */ .p-DockPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-DockPanel-handle:after, /* </DEPRECATED> */
.lm-DockPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal'] {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical'] {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='horizontal']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='horizontal']:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-DockPanel-handle[data-orientation='vertical']:after,
/* </DEPRECATED> */
.lm-DockPanel-handle[data-orientation='vertical']:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}


/* <DEPRECATED> */ .p-DockPanel-overlay, /* </DEPRECATED> */
.lm-DockPanel-overlay {
  z-index: 3;
  box-sizing: border-box;
  pointer-events: none;
}


/* <DEPRECATED> */ .p-DockPanel-overlay.p-mod-hidden, /* </DEPRECATED> */
.lm-DockPanel-overlay.lm-mod-hidden {
  display: none !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-Menu, /* </DEPRECATED> */
.lm-Menu {
  z-index: 10000;
  position: absolute;
  white-space: nowrap;
  overflow-x: hidden;
  overflow-y: auto;
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-Menu-content, /* </DEPRECATED> */
.lm-Menu-content {
  margin: 0;
  padding: 0;
  display: table;
  list-style-type: none;
}


/* <DEPRECATED> */ .p-Menu-item, /* </DEPRECATED> */
.lm-Menu-item {
  display: table-row;
}


/* <DEPRECATED> */
.p-Menu-item.p-mod-hidden,
.p-Menu-item.p-mod-collapsed,
/* </DEPRECATED> */
.lm-Menu-item.lm-mod-hidden,
.lm-Menu-item.lm-mod-collapsed {
  display: none !important;
}


/* <DEPRECATED> */
.p-Menu-itemIcon,
.p-Menu-itemSubmenuIcon,
/* </DEPRECATED> */
.lm-Menu-itemIcon,
.lm-Menu-itemSubmenuIcon {
  display: table-cell;
  text-align: center;
}


/* <DEPRECATED> */ .p-Menu-itemLabel, /* </DEPRECATED> */
.lm-Menu-itemLabel {
  display: table-cell;
  text-align: left;
}


/* <DEPRECATED> */ .p-Menu-itemShortcut, /* </DEPRECATED> */
.lm-Menu-itemShortcut {
  display: table-cell;
  text-align: right;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-MenuBar, /* </DEPRECATED> */
.lm-MenuBar {
  outline: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-MenuBar-content, /* </DEPRECATED> */
.lm-MenuBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: row;
  list-style-type: none;
}


/* <DEPRECATED> */ .p--MenuBar-item, /* </DEPRECATED> */
.lm-MenuBar-item {
  box-sizing: border-box;
}


/* <DEPRECATED> */
.p-MenuBar-itemIcon,
.p-MenuBar-itemLabel,
/* </DEPRECATED> */
.lm-MenuBar-itemIcon,
.lm-MenuBar-itemLabel {
  display: inline-block;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-ScrollBar, /* </DEPRECATED> */
.lm-ScrollBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='horizontal'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='horizontal'] {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-ScrollBar[data-orientation='vertical'],
/* </DEPRECATED> */
.lm-ScrollBar[data-orientation='vertical'] {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-ScrollBar-button, /* </DEPRECATED> */
.lm-ScrollBar-button {
  box-sizing: border-box;
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-track, /* </DEPRECATED> */
.lm-ScrollBar-track {
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  flex: 1 1 auto;
}


/* <DEPRECATED> */ .p-ScrollBar-thumb, /* </DEPRECATED> */
.lm-ScrollBar-thumb {
  box-sizing: border-box;
  position: absolute;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-SplitPanel-child, /* </DEPRECATED> */
.lm-SplitPanel-child {
  z-index: 0;
}


/* <DEPRECATED> */ .p-SplitPanel-handle, /* </DEPRECATED> */
.lm-SplitPanel-handle {
  z-index: 1;
}


/* <DEPRECATED> */ .p-SplitPanel-handle.p-mod-hidden, /* </DEPRECATED> */
.lm-SplitPanel-handle.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-SplitPanel-handle:after, /* </DEPRECATED> */
.lm-SplitPanel-handle:after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
  cursor: ew-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
  cursor: ns-resize;
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='horizontal'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
  left: 50%;
  min-width: 8px;
  transform: translateX(-50%);
}


/* <DEPRECATED> */
.p-SplitPanel[data-orientation='vertical'] > .p-SplitPanel-handle:after,
/* </DEPRECATED> */
.lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
  top: 50%;
  min-height: 8px;
  transform: translateY(-50%);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabBar, /* </DEPRECATED> */
.lm-TabBar {
  display: flex;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='horizontal'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] {
  flex-direction: row;
}


/* <DEPRECATED> */ .p-TabBar[data-orientation='vertical'], /* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-TabBar-content, /* </DEPRECATED> */
.lm-TabBar-content {
  margin: 0;
  padding: 0;
  display: flex;
  flex: 1 1 auto;
  list-style-type: none;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='horizontal'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
  flex-direction: row;
}


/* <DEPRECATED> */
.p-TabBar[data-orientation='vertical'] > .p-TabBar-content,
/* </DEPRECATED> */
.lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
  flex-direction: column;
}


/* <DEPRECATED> */ .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar-tab {
  display: flex;
  flex-direction: row;
  box-sizing: border-box;
  overflow: hidden;
}


/* <DEPRECATED> */
.p-TabBar-tabIcon,
.p-TabBar-tabCloseIcon,
/* </DEPRECATED> */
.lm-TabBar-tabIcon,
.lm-TabBar-tabCloseIcon {
  flex: 0 0 auto;
}


/* <DEPRECATED> */ .p-TabBar-tabLabel, /* </DEPRECATED> */
.lm-TabBar-tabLabel {
  flex: 1 1 auto;
  overflow: hidden;
  white-space: nowrap;
}


/* <DEPRECATED> */ .p-TabBar-tab.p-mod-hidden, /* </DEPRECATED> */
.lm-TabBar-tab.lm-mod-hidden {
  display: none !important;
}


/* <DEPRECATED> */ .p-TabBar.p-mod-dragging .p-TabBar-tab, /* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
  position: relative;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='horizontal'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
  left: 0;
  transition: left 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging[data-orientation='vertical'] .p-TabBar-tab,
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
  top: 0;
  transition: top 150ms ease;
}


/* <DEPRECATED> */
.p-TabBar.p-mod-dragging .p-TabBar-tab.p-mod-dragging
/* </DEPRECATED> */
.lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
  transition: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ .p-TabPanel-tabBar, /* </DEPRECATED> */
.lm-TabPanel-tabBar {
  z-index: 1;
}


/* <DEPRECATED> */ .p-TabPanel-stackedPanel, /* </DEPRECATED> */
.lm-TabPanel-stackedPanel {
  z-index: 0;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/

@charset "UTF-8";
/*!

Copyright 2015-present Palantir Technologies, Inc. All rights reserved.
Licensed under the Apache License, Version 2.0.

*/
html{
  -webkit-box-sizing:border-box;
          box-sizing:border-box; }

*,
*::before,
*::after{
  -webkit-box-sizing:inherit;
          box-sizing:inherit; }

body{
  text-transform:none;
  line-height:1.28581;
  letter-spacing:0;
  font-size:14px;
  font-weight:400;
  color:#182026;
  font-family:-apple-system, "BlinkMacSystemFont", "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Open Sans", "Helvetica Neue", "Icons16", sans-serif; }

p{
  margin-top:0;
  margin-bottom:10px; }

small{
  font-size:12px; }

strong{
  font-weight:600; }

::-moz-selection{
  background:rgba(125, 188, 255, 0.6); }

::selection{
  background:rgba(125, 188, 255, 0.6); }
.bp3-heading{
  color:#182026;
  font-weight:600;
  margin:0 0 10px;
  padding:0; }
  .bp3-dark .bp3-heading{
    color:#f5f8fa; }

h1.bp3-heading, .bp3-running-text h1{
  line-height:40px;
  font-size:36px; }

h2.bp3-heading, .bp3-running-text h2{
  line-height:32px;
  font-size:28px; }

h3.bp3-heading, .bp3-running-text h3{
  line-height:25px;
  font-size:22px; }

h4.bp3-heading, .bp3-running-text h4{
  line-height:21px;
  font-size:18px; }

h5.bp3-heading, .bp3-running-text h5{
  line-height:19px;
  font-size:16px; }

h6.bp3-heading, .bp3-running-text h6{
  line-height:16px;
  font-size:14px; }
.bp3-ui-text{
  text-transform:none;
  line-height:1.28581;
  letter-spacing:0;
  font-size:14px;
  font-weight:400; }

.bp3-monospace-text{
  text-transform:none;
  font-family:monospace; }

.bp3-text-muted{
  color:#5c7080; }
  .bp3-dark .bp3-text-muted{
    color:#a7b6c2; }

.bp3-text-disabled{
  color:rgba(92, 112, 128, 0.6); }
  .bp3-dark .bp3-text-disabled{
    color:rgba(167, 182, 194, 0.6); }

.bp3-text-overflow-ellipsis{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal; }
.bp3-running-text{
  line-height:1.5;
  font-size:14px; }
  .bp3-running-text h1{
    color:#182026;
    font-weight:600;
    margin-top:40px;
    margin-bottom:20px; }
    .bp3-dark .bp3-running-text h1{
      color:#f5f8fa; }
  .bp3-running-text h2{
    color:#182026;
    font-weight:600;
    margin-top:40px;
    margin-bottom:20px; }
    .bp3-dark .bp3-running-text h2{
      color:#f5f8fa; }
  .bp3-running-text h3{
    color:#182026;
    font-weight:600;
    margin-top:40px;
    margin-bottom:20px; }
    .bp3-dark .bp3-running-text h3{
      color:#f5f8fa; }
  .bp3-running-text h4{
    color:#182026;
    font-weight:600;
    margin-top:40px;
    margin-bottom:20px; }
    .bp3-dark .bp3-running-text h4{
      color:#f5f8fa; }
  .bp3-running-text h5{
    color:#182026;
    font-weight:600;
    margin-top:40px;
    margin-bottom:20px; }
    .bp3-dark .bp3-running-text h5{
      color:#f5f8fa; }
  .bp3-running-text h6{
    color:#182026;
    font-weight:600;
    margin-top:40px;
    margin-bottom:20px; }
    .bp3-dark .bp3-running-text h6{
      color:#f5f8fa; }
  .bp3-running-text hr{
    margin:20px 0;
    border:none;
    border-bottom:1px solid rgba(16, 22, 26, 0.15); }
    .bp3-dark .bp3-running-text hr{
      border-color:rgba(255, 255, 255, 0.15); }
  .bp3-running-text p{
    margin:0 0 10px;
    padding:0; }

.bp3-text-large{
  font-size:16px; }

.bp3-text-small{
  font-size:12px; }
a{
  text-decoration:none;
  color:#106ba3; }
  a:hover{
    cursor:pointer;
    text-decoration:underline;
    color:#106ba3; }
  a .bp3-icon, a .bp3-icon-standard, a .bp3-icon-large{
    color:inherit; }
  a code,
  .bp3-dark a code{
    color:inherit; }
  .bp3-dark a,
  .bp3-dark a:hover{
    color:#48aff0; }
    .bp3-dark a .bp3-icon, .bp3-dark a .bp3-icon-standard, .bp3-dark a .bp3-icon-large,
    .bp3-dark a:hover .bp3-icon,
    .bp3-dark a:hover .bp3-icon-standard,
    .bp3-dark a:hover .bp3-icon-large{
      color:inherit; }
.bp3-running-text code, .bp3-code{
  text-transform:none;
  font-family:monospace;
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2);
  background:rgba(255, 255, 255, 0.7);
  padding:2px 5px;
  color:#5c7080;
  font-size:smaller; }
  .bp3-dark .bp3-running-text code, .bp3-running-text .bp3-dark code, .bp3-dark .bp3-code{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    background:rgba(16, 22, 26, 0.3);
    color:#a7b6c2; }
  .bp3-running-text a > code, a > .bp3-code{
    color:#137cbd; }
    .bp3-dark .bp3-running-text a > code, .bp3-running-text .bp3-dark a > code, .bp3-dark a > .bp3-code{
      color:inherit; }

.bp3-running-text pre, .bp3-code-block{
  text-transform:none;
  font-family:monospace;
  display:block;
  margin:10px 0;
  border-radius:3px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
  background:rgba(255, 255, 255, 0.7);
  padding:13px 15px 12px;
  line-height:1.4;
  color:#182026;
  font-size:13px;
  word-break:break-all;
  word-wrap:break-word; }
  .bp3-dark .bp3-running-text pre, .bp3-running-text .bp3-dark pre, .bp3-dark .bp3-code-block{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
    background:rgba(16, 22, 26, 0.3);
    color:#f5f8fa; }
  .bp3-running-text pre > code, .bp3-code-block > code{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:none;
    padding:0;
    color:inherit;
    font-size:inherit; }

.bp3-running-text kbd, .bp3-key{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  background:#ffffff;
  min-width:24px;
  height:24px;
  padding:3px 6px;
  vertical-align:middle;
  line-height:24px;
  color:#5c7080;
  font-family:inherit;
  font-size:12px; }
  .bp3-running-text kbd .bp3-icon, .bp3-key .bp3-icon, .bp3-running-text kbd .bp3-icon-standard, .bp3-key .bp3-icon-standard, .bp3-running-text kbd .bp3-icon-large, .bp3-key .bp3-icon-large{
    margin-right:5px; }
  .bp3-dark .bp3-running-text kbd, .bp3-running-text .bp3-dark kbd, .bp3-dark .bp3-key{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
    background:#394b59;
    color:#a7b6c2; }
.bp3-running-text blockquote, .bp3-blockquote{
  margin:0 0 10px;
  border-left:solid 4px rgba(167, 182, 194, 0.5);
  padding:0 20px; }
  .bp3-dark .bp3-running-text blockquote, .bp3-running-text .bp3-dark blockquote, .bp3-dark .bp3-blockquote{
    border-color:rgba(115, 134, 148, 0.5); }
.bp3-running-text ul,
.bp3-running-text ol, .bp3-list{
  margin:10px 0;
  padding-left:30px; }
  .bp3-running-text ul li:not(:last-child), .bp3-running-text ol li:not(:last-child), .bp3-list li:not(:last-child){
    margin-bottom:5px; }
  .bp3-running-text ul ol, .bp3-running-text ol ol, .bp3-list ol,
  .bp3-running-text ul ul,
  .bp3-running-text ol ul,
  .bp3-list ul{
    margin-top:5px; }

.bp3-list-unstyled{
  margin:0;
  padding:0;
  list-style:none; }
  .bp3-list-unstyled li{
    padding:0; }
.bp3-rtl{
  text-align:right; }

.bp3-dark{
  color:#f5f8fa; }

:focus{
  outline:rgba(19, 124, 189, 0.6) auto 2px;
  outline-offset:2px;
  -moz-outline-radius:6px; }

.bp3-focus-disabled :focus{
  outline:none !important; }
  .bp3-focus-disabled :focus ~ .bp3-control-indicator{
    outline:none !important; }

.bp3-alert{
  max-width:400px;
  padding:20px; }

.bp3-alert-body{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-alert-body .bp3-icon{
    margin-top:0;
    margin-right:20px;
    font-size:40px; }

.bp3-alert-footer{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:reverse;
      -ms-flex-direction:row-reverse;
          flex-direction:row-reverse;
  margin-top:10px; }
  .bp3-alert-footer .bp3-button{
    margin-left:10px; }
.bp3-breadcrumbs{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:wrap;
      flex-wrap:wrap;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  margin:0;
  cursor:default;
  height:30px;
  padding:0;
  list-style:none; }
  .bp3-breadcrumbs > li{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center; }
    .bp3-breadcrumbs > li::after{
      display:block;
      margin:0 5px;
      background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M10.71 7.29l-4-4a1.003 1.003 0 0 0-1.42 1.42L8.59 8 5.3 11.29c-.19.18-.3.43-.3.71a1.003 1.003 0 0 0 1.71.71l4-4c.18-.18.29-.43.29-.71 0-.28-.11-.53-.29-.71z' fill='%235C7080'/%3e%3c/svg%3e");
      width:16px;
      height:16px;
      content:""; }
    .bp3-breadcrumbs > li:last-of-type::after{
      display:none; }

.bp3-breadcrumb,
.bp3-breadcrumb-current,
.bp3-breadcrumbs-collapsed{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  font-size:16px; }

.bp3-breadcrumb,
.bp3-breadcrumbs-collapsed{
  color:#5c7080; }

.bp3-breadcrumb:hover{
  text-decoration:none; }

.bp3-breadcrumb.bp3-disabled{
  cursor:not-allowed;
  color:rgba(92, 112, 128, 0.6); }

.bp3-breadcrumb .bp3-icon{
  margin-right:5px; }

.bp3-breadcrumb-current{
  color:inherit;
  font-weight:600; }
  .bp3-breadcrumb-current .bp3-input{
    vertical-align:baseline;
    font-size:inherit;
    font-weight:inherit; }

.bp3-breadcrumbs-collapsed{
  margin-right:2px;
  border:none;
  border-radius:3px;
  background:#ced9e0;
  cursor:pointer;
  padding:1px 5px;
  vertical-align:text-bottom; }
  .bp3-breadcrumbs-collapsed::before{
    display:block;
    background:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cg fill='%235C7080'%3e%3ccircle cx='2' cy='8.03' r='2'/%3e%3ccircle cx='14' cy='8.03' r='2'/%3e%3ccircle cx='8' cy='8.03' r='2'/%3e%3c/g%3e%3c/svg%3e") center no-repeat;
    width:16px;
    height:16px;
    content:""; }
  .bp3-breadcrumbs-collapsed:hover{
    background:#bfccd6;
    text-decoration:none;
    color:#182026; }

.bp3-dark .bp3-breadcrumb,
.bp3-dark .bp3-breadcrumbs-collapsed{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumbs > li::after{
  color:#a7b6c2; }

.bp3-dark .bp3-breadcrumb.bp3-disabled{
  color:rgba(167, 182, 194, 0.6); }

.bp3-dark .bp3-breadcrumb-current{
  color:#f5f8fa; }

.bp3-dark .bp3-breadcrumbs-collapsed{
  background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-breadcrumbs-collapsed:hover{
    background:rgba(16, 22, 26, 0.6);
    color:#f5f8fa; }
.bp3-button{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  padding:5px 10px;
  vertical-align:middle;
  text-align:left;
  font-size:14px;
  min-width:30px;
  min-height:30px; }
  .bp3-button > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-button > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-button::before,
  .bp3-button > *{
    margin-right:7px; }
  .bp3-button:empty::before,
  .bp3-button > :last-child{
    margin-right:0; }
  .bp3-button:empty{
    padding:0 !important; }
  .bp3-button:disabled, .bp3-button.bp3-disabled{
    cursor:not-allowed; }
  .bp3-button.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button.bp3-align-right,
  .bp3-align-right .bp3-button{
    text-align:right; }
  .bp3-button.bp3-align-left,
  .bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-button:not([class*="bp3-intent-"]){
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    color:#182026; }
    .bp3-button:not([class*="bp3-intent-"]):hover{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
      background-clip:padding-box;
      background-color:#ebf1f5; }
    .bp3-button:not([class*="bp3-intent-"]):active, .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#d8e1e8;
      background-image:none; }
    .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      outline:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      cursor:not-allowed;
      color:rgba(92, 112, 128, 0.6); }
      .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active:hover, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active, .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-button.bp3-intent-primary{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover, .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-primary:hover{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      background-color:#106ba3; }
    .bp3-button.bp3-intent-primary:active, .bp3-button.bp3-intent-primary.bp3-active{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#0e5a8a;
      background-image:none; }
    .bp3-button.bp3-intent-primary:disabled, .bp3-button.bp3-intent-primary.bp3-disabled{
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(19, 124, 189, 0.5);
      background-image:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-success{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#0f9960;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    color:#ffffff; }
    .bp3-button.bp3-intent-success:hover, .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-success:hover{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      background-color:#0d8050; }
    .bp3-button.bp3-intent-success:active, .bp3-button.bp3-intent-success.bp3-active{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#0a6640;
      background-image:none; }
    .bp3-button.bp3-intent-success:disabled, .bp3-button.bp3-intent-success.bp3-disabled{
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(15, 153, 96, 0.5);
      background-image:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-warning{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#d9822b;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover, .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-warning:hover{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      background-color:#bf7326; }
    .bp3-button.bp3-intent-warning:active, .bp3-button.bp3-intent-warning.bp3-active{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#a66321;
      background-image:none; }
    .bp3-button.bp3-intent-warning:disabled, .bp3-button.bp3-intent-warning.bp3-disabled{
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(217, 130, 43, 0.5);
      background-image:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button.bp3-intent-danger{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#db3737;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover, .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      color:#ffffff; }
    .bp3-button.bp3-intent-danger:hover{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
      background-color:#c23030; }
    .bp3-button.bp3-intent-danger:active, .bp3-button.bp3-intent-danger.bp3-active{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#a82a2a;
      background-image:none; }
    .bp3-button.bp3-intent-danger:disabled, .bp3-button.bp3-intent-danger.bp3-disabled{
      border-color:transparent;
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(219, 55, 55, 0.5);
      background-image:none;
      color:rgba(255, 255, 255, 0.6); }
  .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
    stroke:#ffffff; }
  .bp3-button.bp3-large,
  .bp3-large .bp3-button{
    min-width:40px;
    min-height:40px;
    padding:5px 15px;
    font-size:16px; }
    .bp3-button.bp3-large::before,
    .bp3-button.bp3-large > *,
    .bp3-large .bp3-button::before,
    .bp3-large .bp3-button > *{
      margin-right:10px; }
    .bp3-button.bp3-large:empty::before,
    .bp3-button.bp3-large > :last-child,
    .bp3-large .bp3-button:empty::before,
    .bp3-large .bp3-button > :last-child{
      margin-right:0; }
  .bp3-button.bp3-small,
  .bp3-small .bp3-button{
    min-width:24px;
    min-height:24px;
    padding:0 7px; }
  .bp3-button.bp3-loading{
    position:relative; }
    .bp3-button.bp3-loading[class*="bp3-icon-"]::before{
      visibility:hidden; }
    .bp3-button.bp3-loading .bp3-button-spinner{
      position:absolute;
      margin:0; }
    .bp3-button.bp3-loading > :not(.bp3-button-spinner){
      visibility:hidden; }
  .bp3-button[class*="bp3-icon-"]::before{
    line-height:1;
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-weight:400;
    font-style:normal;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    color:#5c7080; }
  .bp3-button .bp3-icon, .bp3-button .bp3-icon-standard, .bp3-button .bp3-icon-large{
    color:#5c7080; }
    .bp3-button .bp3-icon.bp3-align-right, .bp3-button .bp3-icon-standard.bp3-align-right, .bp3-button .bp3-icon-large.bp3-align-right{
      margin-left:7px; }
  .bp3-button .bp3-icon:first-child:last-child,
  .bp3-button .bp3-spinner + .bp3-icon:last-child{
    margin:0 -7px; }
  .bp3-dark .bp3-button:not([class*="bp3-intent-"]){
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover, .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      background-color:#30404d; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#202b33;
      background-image:none; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-button:not([class*="bp3-intent-"]):disabled.bp3-active, .bp3-dark .bp3-button:not([class*="bp3-intent-"]).bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"])[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
    .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-button:not([class*="bp3-intent-"]) .bp3-icon-large{
      color:#a7b6c2; }
  .bp3-dark .bp3-button[class*="bp3-intent-"]{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:active, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2); }
    .bp3-dark .bp3-button[class*="bp3-intent-"]:disabled, .bp3-dark .bp3-button[class*="bp3-intent-"].bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none;
      background-image:none;
      color:rgba(255, 255, 255, 0.3); }
    .bp3-dark .bp3-button[class*="bp3-intent-"] .bp3-button-spinner .bp3-spinner-head{
      stroke:#8a9ba8; }
  .bp3-button:disabled::before,
  .bp3-button:disabled .bp3-icon, .bp3-button:disabled .bp3-icon-standard, .bp3-button:disabled .bp3-icon-large, .bp3-button.bp3-disabled::before,
  .bp3-button.bp3-disabled .bp3-icon, .bp3-button.bp3-disabled .bp3-icon-standard, .bp3-button.bp3-disabled .bp3-icon-large, .bp3-button[class*="bp3-intent-"]::before,
  .bp3-button[class*="bp3-intent-"] .bp3-icon, .bp3-button[class*="bp3-intent-"] .bp3-icon-standard, .bp3-button[class*="bp3-intent-"] .bp3-icon-large{
    color:inherit !important; }
  .bp3-button.bp3-minimal{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:none; }
    .bp3-button.bp3-minimal:hover{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(167, 182, 194, 0.3);
      text-decoration:none;
      color:#182026; }
    .bp3-button.bp3-minimal:active, .bp3-button.bp3-minimal.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(115, 134, 148, 0.3);
      color:#182026; }
    .bp3-button.bp3-minimal:disabled, .bp3-button.bp3-minimal:disabled:hover, .bp3-button.bp3-minimal.bp3-disabled, .bp3-button.bp3-minimal.bp3-disabled:hover{
      background:none;
      cursor:not-allowed;
      color:rgba(92, 112, 128, 0.6); }
      .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button.bp3-minimal{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none;
      color:inherit; }
      .bp3-dark .bp3-button.bp3-minimal:hover, .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none; }
      .bp3-dark .bp3-button.bp3-minimal:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button.bp3-minimal:active, .bp3-dark .bp3-button.bp3-minimal.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button.bp3-minimal:disabled, .bp3-dark .bp3-button.bp3-minimal:disabled:hover, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover{
        background:none;
        cursor:not-allowed;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-button.bp3-minimal:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal:disabled:hover.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover, .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-success{
      color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover, .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover, .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button.bp3-minimal.bp3-intent-danger{
      color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover, .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button.bp3-minimal.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button.bp3-minimal.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }

a.bp3-button{
  text-align:center;
  text-decoration:none;
  -webkit-transition:none;
  transition:none; }
  a.bp3-button, a.bp3-button:hover, a.bp3-button:active{
    color:#182026; }
  a.bp3-button.bp3-disabled{
    color:rgba(92, 112, 128, 0.6); }

.bp3-button-text{
  -webkit-box-flex:0;
      -ms-flex:0 1 auto;
          flex:0 1 auto; }

.bp3-button.bp3-align-left .bp3-button-text, .bp3-button.bp3-align-right .bp3-button-text,
.bp3-button-group.bp3-align-left .bp3-button-text,
.bp3-button-group.bp3-align-right .bp3-button-text{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto; }
.bp3-button-group{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex; }
  .bp3-button-group .bp3-button{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    position:relative;
    z-index:4; }
    .bp3-button-group .bp3-button:focus{
      z-index:5; }
    .bp3-button-group .bp3-button:hover{
      z-index:6; }
    .bp3-button-group .bp3-button:active, .bp3-button-group .bp3-button.bp3-active{
      z-index:7; }
    .bp3-button-group .bp3-button:disabled, .bp3-button-group .bp3-button.bp3-disabled{
      z-index:3; }
    .bp3-button-group .bp3-button[class*="bp3-intent-"]{
      z-index:9; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:focus{
        z-index:10; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:hover{
        z-index:11; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:active, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-active{
        z-index:12; }
      .bp3-button-group .bp3-button[class*="bp3-intent-"]:disabled, .bp3-button-group .bp3-button[class*="bp3-intent-"].bp3-disabled{
        z-index:8; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:first-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:first-child){
    border-top-left-radius:0;
    border-bottom-left-radius:0; }
  .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    margin-right:-1px;
    border-top-right-radius:0;
    border-bottom-right-radius:0; }
  .bp3-button-group.bp3-minimal .bp3-button{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:none; }
    .bp3-button-group.bp3-minimal .bp3-button:hover{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(167, 182, 194, 0.3);
      text-decoration:none;
      color:#182026; }
    .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(115, 134, 148, 0.3);
      color:#182026; }
    .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
      background:none;
      cursor:not-allowed;
      color:rgba(92, 112, 128, 0.6); }
      .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
        background:rgba(115, 134, 148, 0.3); }
    .bp3-dark .bp3-button-group.bp3-minimal .bp3-button{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none;
      color:inherit; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:hover{
        background:rgba(138, 155, 168, 0.15); }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-active{
        background:rgba(138, 155, 168, 0.3);
        color:#f5f8fa; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover{
        background:none;
        cursor:not-allowed;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button:disabled:hover.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-disabled:hover.bp3-active{
          background:rgba(138, 155, 168, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
      color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.15);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#106ba3; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(16, 107, 163, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
        stroke:#106ba3; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary{
        color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:hover{
          background:rgba(19, 124, 189, 0.2);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-active{
          background:rgba(19, 124, 189, 0.3);
          color:#48aff0; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled{
          background:none;
          color:rgba(72, 175, 240, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-primary.bp3-disabled.bp3-active{
            background:rgba(19, 124, 189, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
      color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.15);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#0d8050; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(13, 128, 80, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
        stroke:#0d8050; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success{
        color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:hover{
          background:rgba(15, 153, 96, 0.2);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-active{
          background:rgba(15, 153, 96, 0.3);
          color:#3dcc91; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled{
          background:none;
          color:rgba(61, 204, 145, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-success.bp3-disabled.bp3-active{
            background:rgba(15, 153, 96, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
      color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.15);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#bf7326; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(191, 115, 38, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
        stroke:#bf7326; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning{
        color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:hover{
          background:rgba(217, 130, 43, 0.2);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-active{
          background:rgba(217, 130, 43, 0.3);
          color:#ffb366; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled{
          background:none;
          color:rgba(255, 179, 102, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-warning.bp3-disabled.bp3-active{
            background:rgba(217, 130, 43, 0.3); }
    .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
      color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:none;
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.15);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#c23030; }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(194, 48, 48, 0.5); }
        .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }
      .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
        stroke:#c23030; }
      .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger{
        color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:hover{
          background:rgba(219, 55, 55, 0.2);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-active{
          background:rgba(219, 55, 55, 0.3);
          color:#ff7373; }
        .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled{
          background:none;
          color:rgba(255, 115, 115, 0.5); }
          .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-button-group.bp3-minimal .bp3-button.bp3-intent-danger.bp3-disabled.bp3-active{
            background:rgba(219, 55, 55, 0.3); }
  .bp3-button-group .bp3-popover-wrapper,
  .bp3-button-group .bp3-popover-target{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-button-group .bp3-button.bp3-fill,
  .bp3-button-group.bp3-fill .bp3-button:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-button-group.bp3-vertical{
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch;
    vertical-align:top; }
    .bp3-button-group.bp3-vertical.bp3-fill{
      width:unset;
      height:100%; }
    .bp3-button-group.bp3-vertical .bp3-button{
      margin-right:0 !important;
      width:100%; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:first-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:first-child{
      border-radius:3px 3px 0 0; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:last-child .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:last-child{
      border-radius:0 0 3px 3px; }
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
    .bp3-button-group.bp3-vertical:not(.bp3-minimal) > .bp3-button:not(:last-child){
      margin-bottom:-1px; }
  .bp3-button-group.bp3-align-left .bp3-button{
    text-align:left; }
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group:not(.bp3-minimal) > .bp3-button:not(:last-child){
    margin-right:1px; }
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-popover-wrapper:not(:last-child) .bp3-button,
  .bp3-dark .bp3-button-group.bp3-vertical > .bp3-button:not(:last-child){
    margin-bottom:1px; }
.bp3-callout{
  line-height:1.5;
  font-size:14px;
  position:relative;
  border-radius:3px;
  background-color:rgba(138, 155, 168, 0.15);
  width:100%;
  padding:10px 12px 9px; }
  .bp3-callout[class*="bp3-icon-"]{
    padding-left:40px; }
    .bp3-callout[class*="bp3-icon-"]::before{
      line-height:1;
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-weight:400;
      font-style:normal;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      position:absolute;
      top:10px;
      left:10px;
      color:#5c7080; }
  .bp3-callout.bp3-callout-icon{
    padding-left:40px; }
    .bp3-callout.bp3-callout-icon > .bp3-icon:first-child{
      position:absolute;
      top:10px;
      left:10px;
      color:#5c7080; }
  .bp3-callout .bp3-heading{
    margin-top:0;
    margin-bottom:5px;
    line-height:20px; }
    .bp3-callout .bp3-heading:last-child{
      margin-bottom:0; }
  .bp3-dark .bp3-callout{
    background-color:rgba(138, 155, 168, 0.2); }
    .bp3-dark .bp3-callout[class*="bp3-icon-"]::before{
      color:#a7b6c2; }
  .bp3-callout.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15); }
    .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-primary .bp3-heading{
      color:#106ba3; }
    .bp3-dark .bp3-callout.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-primary[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-primary > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-primary .bp3-heading{
        color:#48aff0; }
  .bp3-callout.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15); }
    .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-success .bp3-heading{
      color:#0d8050; }
    .bp3-dark .bp3-callout.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-success[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-success > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-success .bp3-heading{
        color:#3dcc91; }
  .bp3-callout.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15); }
    .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-warning .bp3-heading{
      color:#bf7326; }
    .bp3-dark .bp3-callout.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-warning[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-warning > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-warning .bp3-heading{
        color:#ffb366; }
  .bp3-callout.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15); }
    .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
    .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
    .bp3-callout.bp3-intent-danger .bp3-heading{
      color:#c23030; }
    .bp3-dark .bp3-callout.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25); }
      .bp3-dark .bp3-callout.bp3-intent-danger[class*="bp3-icon-"]::before,
      .bp3-dark .bp3-callout.bp3-intent-danger > .bp3-icon:first-child,
      .bp3-dark .bp3-callout.bp3-intent-danger .bp3-heading{
        color:#ff7373; }
  .bp3-running-text .bp3-callout{
    margin:20px 0; }
.bp3-card{
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
  background-color:#ffffff;
  padding:20px;
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-card.bp3-dark,
  .bp3-dark .bp3-card{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
    background-color:#30404d; }

.bp3-elevation-0{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.15), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }
  .bp3-elevation-0.bp3-dark,
  .bp3-dark .bp3-elevation-0{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), 0 0 0 rgba(16, 22, 26, 0), 0 0 0 rgba(16, 22, 26, 0); }

.bp3-elevation-1{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-1.bp3-dark,
  .bp3-dark .bp3-elevation-1{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-elevation-2{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 1px 1px rgba(16, 22, 26, 0.2), 0 2px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-2.bp3-dark,
  .bp3-dark .bp3-elevation-2{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.4), 0 2px 6px rgba(16, 22, 26, 0.4); }

.bp3-elevation-3{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-3.bp3-dark,
  .bp3-dark .bp3-elevation-3{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-elevation-4{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2); }
  .bp3-elevation-4.bp3-dark,
  .bp3-dark .bp3-elevation-4{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:hover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  cursor:pointer; }
  .bp3-card.bp3-interactive:hover.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:hover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }

.bp3-card.bp3-interactive:active{
  opacity:0.9;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  -webkit-transition-duration:0;
          transition-duration:0; }
  .bp3-card.bp3-interactive:active.bp3-dark,
  .bp3-dark .bp3-card.bp3-interactive:active{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-collapse{
  height:0;
  overflow-y:hidden;
  -webkit-transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:height 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-collapse .bp3-collapse-body{
    -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-collapse .bp3-collapse-body[aria-hidden="true"]{
      display:none; }

.bp3-context-menu .bp3-popover-target{
  display:block; }

.bp3-context-menu-popover-target{
  position:fixed; }

.bp3-divider{
  margin:5px;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  border-bottom:1px solid rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-divider{
    border-color:rgba(16, 22, 26, 0.4); }
.bp3-dialog-container{
  opacity:1;
  -webkit-transform:scale(1);
          transform:scale(1);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  width:100%;
  min-height:100%;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-dialog-container.bp3-overlay-enter > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5); }
  .bp3-dialog-container.bp3-overlay-enter-active > .bp3-dialog, .bp3-dialog-container.bp3-overlay-appear-active > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-dialog-container.bp3-overlay-exit > .bp3-dialog{
    opacity:1;
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-dialog-container.bp3-overlay-exit-active > .bp3-dialog{
    opacity:0;
    -webkit-transform:scale(0.5);
            transform:scale(0.5);
    -webkit-transition-property:opacity, -webkit-transform;
    transition-property:opacity, -webkit-transform;
    transition-property:opacity, transform;
    transition-property:opacity, transform, -webkit-transform;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
    -webkit-transition-delay:0;
            transition-delay:0; }

.bp3-dialog{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:30px 0;
  border-radius:6px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  background:#ebf1f5;
  width:500px;
  padding-bottom:20px;
  pointer-events:all;
  -webkit-user-select:text;
     -moz-user-select:text;
      -ms-user-select:text;
          user-select:text; }
  .bp3-dialog:focus{
    outline:0; }
  .bp3-dialog.bp3-dark,
  .bp3-dark .bp3-dialog{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    background:#293742;
    color:#f5f8fa; }

.bp3-dialog-header{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  border-radius:6px 6px 0 0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  background:#ffffff;
  min-height:40px;
  padding-right:5px;
  padding-left:20px; }
  .bp3-dialog-header .bp3-icon-large,
  .bp3-dialog-header .bp3-icon{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px;
    color:#5c7080; }
  .bp3-dialog-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    margin:0;
    line-height:inherit; }
    .bp3-dialog-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-dialog-header{
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
    background:#30404d; }
    .bp3-dark .bp3-dialog-header .bp3-icon-large,
    .bp3-dark .bp3-dialog-header .bp3-icon{
      color:#a7b6c2; }

.bp3-dialog-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  margin:20px;
  line-height:18px; }

.bp3-dialog-footer{
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  margin:0 20px; }

.bp3-dialog-footer-actions{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-pack:end;
      -ms-flex-pack:end;
          justify-content:flex-end; }
  .bp3-dialog-footer-actions .bp3-button{
    margin-left:10px; }
.bp3-drawer{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  background:#ffffff;
  padding:0; }
  .bp3-drawer:focus{
    outline:0; }
  .bp3-drawer.bp3-position-top{
    top:0;
    right:0;
    left:0;
    height:50%; }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter, .bp3-drawer.bp3-position-top.bp3-overlay-appear{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%); }
    .bp3-drawer.bp3-position-top.bp3-overlay-enter-active, .bp3-drawer.bp3-position-top.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-top.bp3-overlay-exit-active{
      -webkit-transform:translateY(-100%);
              transform:translateY(-100%);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
  .bp3-drawer.bp3-position-bottom{
    right:0;
    bottom:0;
    left:0;
    height:50%; }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-enter-active, .bp3-drawer.bp3-position-bottom.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer.bp3-position-bottom.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
  .bp3-drawer.bp3-position-left{
    top:0;
    bottom:0;
    left:0;
    width:50%; }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter, .bp3-drawer.bp3-position-left.bp3-overlay-appear{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%); }
    .bp3-drawer.bp3-position-left.bp3-overlay-enter-active, .bp3-drawer.bp3-position-left.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-left.bp3-overlay-exit-active{
      -webkit-transform:translateX(-100%);
              transform:translateX(-100%);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
  .bp3-drawer.bp3-position-right{
    top:0;
    right:0;
    bottom:0;
    width:50%; }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter, .bp3-drawer.bp3-position-right.bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer.bp3-position-right.bp3-overlay-enter-active, .bp3-drawer.bp3-position-right.bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer.bp3-position-right.bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right):not(.bp3-vertical){
    top:0;
    right:0;
    bottom:0;
    width:50%; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear{
      -webkit-transform:translateX(100%);
              transform:translateX(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-appear-active{
      -webkit-transform:translateX(0);
              transform:translateX(0);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit{
      -webkit-transform:translateX(0);
              transform:translateX(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right):not(.bp3-vertical).bp3-overlay-exit-active{
      -webkit-transform:translateX(100%);
              transform:translateX(100%);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
  .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
  .bp3-position-right).bp3-vertical{
    right:0;
    bottom:0;
    left:0;
    height:50%; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear{
      -webkit-transform:translateY(100%);
              transform:translateY(100%); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-enter-active, .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-appear-active{
      -webkit-transform:translateY(0);
              transform:translateY(0);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:200ms;
              transition-duration:200ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit{
      -webkit-transform:translateY(0);
              transform:translateY(0); }
    .bp3-drawer:not(.bp3-position-top):not(.bp3-position-bottom):not(.bp3-position-left):not(
    .bp3-position-right).bp3-vertical.bp3-overlay-exit-active{
      -webkit-transform:translateY(100%);
              transform:translateY(100%);
      -webkit-transition-property:-webkit-transform;
      transition-property:-webkit-transform;
      transition-property:transform;
      transition-property:transform, -webkit-transform;
      -webkit-transition-duration:100ms;
              transition-duration:100ms;
      -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
              transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
      -webkit-transition-delay:0;
              transition-delay:0; }
  .bp3-drawer.bp3-dark,
  .bp3-dark .bp3-drawer{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    background:#30404d;
    color:#f5f8fa; }

.bp3-drawer-header{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  position:relative;
  border-radius:0;
  -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:0 1px 0 rgba(16, 22, 26, 0.15);
  min-height:40px;
  padding:5px;
  padding-left:20px; }
  .bp3-drawer-header .bp3-icon-large,
  .bp3-drawer-header .bp3-icon{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    margin-right:10px;
    color:#5c7080; }
  .bp3-drawer-header .bp3-heading{
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    margin:0;
    line-height:inherit; }
    .bp3-drawer-header .bp3-heading:last-child{
      margin-right:20px; }
  .bp3-dark .bp3-drawer-header{
    -webkit-box-shadow:0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:0 1px 0 rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-drawer-header .bp3-icon-large,
    .bp3-dark .bp3-drawer-header .bp3-icon{
      color:#a7b6c2; }

.bp3-drawer-body{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  overflow:auto;
  line-height:18px; }

.bp3-drawer-footer{
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  position:relative;
  -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
  padding:10px 20px; }
  .bp3-dark .bp3-drawer-footer{
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.4); }
.bp3-editable-text{
  display:inline-block;
  position:relative;
  cursor:text;
  max-width:100%;
  vertical-align:top;
  white-space:nowrap; }
  .bp3-editable-text::before{
    position:absolute;
    top:-3px;
    right:-3px;
    bottom:-3px;
    left:-3px;
    border-radius:3px;
    content:"";
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9), box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-editable-text.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
    background-color:#ffffff; }
  .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#137cbd; }
  .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(19, 124, 189, 0.4); }
  .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#0f9960; }
  .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px rgba(15, 153, 96, 0.4); }
  .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#d9822b; }
  .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px rgba(217, 130, 43, 0.4); }
  .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-input,
  .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#db3737; }
  .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px rgba(219, 55, 55, 0.4); }
  .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-editable-text:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(255, 255, 255, 0.15); }
  .bp3-dark .bp3-editable-text.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    background-color:rgba(16, 22, 26, 0.3); }
  .bp3-dark .bp3-editable-text.bp3-disabled::before{
    -webkit-box-shadow:none;
            box-shadow:none; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary .bp3-editable-text-content{
    color:#48aff0; }
  .bp3-dark .bp3-editable-text.bp3-intent-primary:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4);
            box-shadow:0 0 0 0 rgba(72, 175, 240, 0), 0 0 0 0 rgba(72, 175, 240, 0), inset 0 0 0 1px rgba(72, 175, 240, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-primary.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #48aff0, 0 0 0 3px rgba(72, 175, 240, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success .bp3-editable-text-content{
    color:#3dcc91; }
  .bp3-dark .bp3-editable-text.bp3-intent-success:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4);
            box-shadow:0 0 0 0 rgba(61, 204, 145, 0), 0 0 0 0 rgba(61, 204, 145, 0), inset 0 0 0 1px rgba(61, 204, 145, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-success.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #3dcc91, 0 0 0 3px rgba(61, 204, 145, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning .bp3-editable-text-content{
    color:#ffb366; }
  .bp3-dark .bp3-editable-text.bp3-intent-warning:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4);
            box-shadow:0 0 0 0 rgba(255, 179, 102, 0), 0 0 0 0 rgba(255, 179, 102, 0), inset 0 0 0 1px rgba(255, 179, 102, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-warning.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ffb366, 0 0 0 3px rgba(255, 179, 102, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger .bp3-editable-text-content{
    color:#ff7373; }
  .bp3-dark .bp3-editable-text.bp3-intent-danger:hover::before{
    -webkit-box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4);
            box-shadow:0 0 0 0 rgba(255, 115, 115, 0), 0 0 0 0 rgba(255, 115, 115, 0), inset 0 0 0 1px rgba(255, 115, 115, 0.4); }
  .bp3-dark .bp3-editable-text.bp3-intent-danger.bp3-editable-text-editing::before{
    -webkit-box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #ff7373, 0 0 0 3px rgba(255, 115, 115, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-editable-text-input,
.bp3-editable-text-content{
  display:inherit;
  position:relative;
  min-width:inherit;
  max-width:inherit;
  vertical-align:top;
  text-transform:inherit;
  letter-spacing:inherit;
  color:inherit;
  font:inherit;
  resize:none; }

.bp3-editable-text-input{
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  background:none;
  width:100%;
  padding:0;
  white-space:pre-wrap; }
  .bp3-editable-text-input::-webkit-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-editable-text-input::-moz-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-editable-text-input:-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-editable-text-input::-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-editable-text-input::placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-editable-text-input:focus{
    outline:none; }
  .bp3-editable-text-input::-ms-clear{
    display:none; }

.bp3-editable-text-content{
  overflow:hidden;
  padding-right:2px;
  text-overflow:ellipsis;
  white-space:pre; }
  .bp3-editable-text-editing > .bp3-editable-text-content{
    position:absolute;
    left:0;
    visibility:hidden; }
  .bp3-editable-text-placeholder > .bp3-editable-text-content{
    color:rgba(92, 112, 128, 0.6); }
    .bp3-dark .bp3-editable-text-placeholder > .bp3-editable-text-content{
      color:rgba(167, 182, 194, 0.6); }

.bp3-editable-text.bp3-multiline{
  display:block; }
  .bp3-editable-text.bp3-multiline .bp3-editable-text-content{
    overflow:auto;
    white-space:pre-wrap;
    word-wrap:break-word; }
.bp3-control-group{
  -webkit-transform:translateZ(0);
          transform:translateZ(0);
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:stretch;
      -ms-flex-align:stretch;
          align-items:stretch; }
  .bp3-control-group > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select,
  .bp3-control-group .bp3-input,
  .bp3-control-group .bp3-select{
    position:relative; }
  .bp3-control-group .bp3-input{
    z-index:2;
    border-radius:inherit; }
    .bp3-control-group .bp3-input:focus{
      z-index:14;
      border-radius:3px; }
    .bp3-control-group .bp3-input[class*="bp3-intent"]{
      z-index:13; }
      .bp3-control-group .bp3-input[class*="bp3-intent"]:focus{
        z-index:15; }
    .bp3-control-group .bp3-input[readonly], .bp3-control-group .bp3-input:disabled, .bp3-control-group .bp3-input.bp3-disabled{
      z-index:1; }
  .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input{
    z-index:13; }
    .bp3-control-group .bp3-input-group[class*="bp3-intent"] .bp3-input:focus{
      z-index:15; }
  .bp3-control-group .bp3-button,
  .bp3-control-group .bp3-html-select select,
  .bp3-control-group .bp3-select select{
    -webkit-transform:translateZ(0);
            transform:translateZ(0);
    z-index:4;
    border-radius:inherit; }
    .bp3-control-group .bp3-button:focus,
    .bp3-control-group .bp3-html-select select:focus,
    .bp3-control-group .bp3-select select:focus{
      z-index:5; }
    .bp3-control-group .bp3-button:hover,
    .bp3-control-group .bp3-html-select select:hover,
    .bp3-control-group .bp3-select select:hover{
      z-index:6; }
    .bp3-control-group .bp3-button:active,
    .bp3-control-group .bp3-html-select select:active,
    .bp3-control-group .bp3-select select:active{
      z-index:7; }
    .bp3-control-group .bp3-button[readonly], .bp3-control-group .bp3-button:disabled, .bp3-control-group .bp3-button.bp3-disabled,
    .bp3-control-group .bp3-html-select select[readonly],
    .bp3-control-group .bp3-html-select select:disabled,
    .bp3-control-group .bp3-html-select select.bp3-disabled,
    .bp3-control-group .bp3-select select[readonly],
    .bp3-control-group .bp3-select select:disabled,
    .bp3-control-group .bp3-select select.bp3-disabled{
      z-index:3; }
    .bp3-control-group .bp3-button[class*="bp3-intent"],
    .bp3-control-group .bp3-html-select select[class*="bp3-intent"],
    .bp3-control-group .bp3-select select[class*="bp3-intent"]{
      z-index:9; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:focus,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:focus{
        z-index:10; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:hover,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:hover{
        z-index:11; }
      .bp3-control-group .bp3-button[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:active,
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:active{
        z-index:12; }
      .bp3-control-group .bp3-button[class*="bp3-intent"][readonly], .bp3-control-group .bp3-button[class*="bp3-intent"]:disabled, .bp3-control-group .bp3-button[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-html-select select[class*="bp3-intent"].bp3-disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"][readonly],
      .bp3-control-group .bp3-select select[class*="bp3-intent"]:disabled,
      .bp3-control-group .bp3-select select[class*="bp3-intent"].bp3-disabled{
        z-index:8; }
  .bp3-control-group .bp3-input-group > .bp3-icon,
  .bp3-control-group .bp3-input-group > .bp3-button,
  .bp3-control-group .bp3-input-group > .bp3-input-action{
    z-index:16; }
  .bp3-control-group .bp3-select::after,
  .bp3-control-group .bp3-html-select::after,
  .bp3-control-group .bp3-select > .bp3-icon,
  .bp3-control-group .bp3-html-select > .bp3-icon{
    z-index:17; }
  .bp3-control-group:not(.bp3-vertical) > *{
    margin-right:-1px; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > *{
    margin-right:0; }
  .bp3-dark .bp3-control-group:not(.bp3-vertical) > .bp3-button + .bp3-button{
    margin-left:1px; }
  .bp3-control-group .bp3-popover-wrapper,
  .bp3-control-group .bp3-popover-target{
    border-radius:inherit; }
  .bp3-control-group > :first-child{
    border-radius:3px 0 0 3px; }
  .bp3-control-group > :last-child{
    margin-right:0;
    border-radius:0 3px 3px 0; }
  .bp3-control-group > :only-child{
    margin-right:0;
    border-radius:3px; }
  .bp3-control-group .bp3-input-group .bp3-button{
    border-radius:3px; }
  .bp3-control-group > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-fill > *:not(.bp3-fixed){
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto; }
  .bp3-control-group.bp3-vertical{
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column; }
    .bp3-control-group.bp3-vertical > *{
      margin-top:-1px; }
    .bp3-control-group.bp3-vertical > :first-child{
      margin-top:0;
      border-radius:3px 3px 0 0; }
    .bp3-control-group.bp3-vertical > :last-child{
      border-radius:0 0 3px 3px; }
.bp3-control{
  display:block;
  position:relative;
  margin-bottom:10px;
  cursor:pointer;
  text-transform:none; }
  .bp3-control input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    color:#ffffff; }
  .bp3-control:hover input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#106ba3; }
  .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background:#0e5a8a; }
  .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(19, 124, 189, 0.5); }
  .bp3-dark .bp3-control input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control:hover input:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    background-color:#106ba3; }
  .bp3-dark .bp3-control input:not(:disabled):active:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#0e5a8a; }
  .bp3-dark .bp3-control input:disabled:checked ~ .bp3-control-indicator{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(14, 90, 138, 0.5); }
  .bp3-control:not(.bp3-align-right){
    padding-left:26px; }
    .bp3-control:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-26px; }
  .bp3-control.bp3-align-right{
    padding-right:26px; }
    .bp3-control.bp3-align-right .bp3-control-indicator{
      margin-right:-26px; }
  .bp3-control.bp3-disabled{
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-control.bp3-inline{
    display:inline-block;
    margin-right:20px; }
  .bp3-control input{
    position:absolute;
    top:0;
    left:0;
    opacity:0;
    z-index:-1; }
  .bp3-control .bp3-control-indicator{
    display:inline-block;
    position:relative;
    margin-top:-3px;
    margin-right:10px;
    border:none;
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-clip:padding-box;
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    cursor:pointer;
    width:1em;
    height:1em;
    vertical-align:middle;
    font-size:16px;
    -webkit-user-select:none;
       -moz-user-select:none;
        -ms-user-select:none;
            user-select:none; }
    .bp3-control .bp3-control-indicator::before{
      display:block;
      width:1em;
      height:1em;
      content:""; }
  .bp3-control:hover .bp3-control-indicator{
    background-color:#ebf1f5; }
  .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background:#d8e1e8; }
  .bp3-control input:disabled ~ .bp3-control-indicator{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(206, 217, 224, 0.5);
    cursor:not-allowed; }
  .bp3-control input:focus ~ .bp3-control-indicator{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:2px;
    -moz-outline-radius:6px; }
  .bp3-control.bp3-align-right .bp3-control-indicator{
    float:right;
    margin-top:1px;
    margin-left:10px; }
  .bp3-control.bp3-large{
    font-size:16px; }
    .bp3-control.bp3-large:not(.bp3-align-right){
      padding-left:30px; }
      .bp3-control.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
        margin-left:-30px; }
    .bp3-control.bp3-large.bp3-align-right{
      padding-right:30px; }
      .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
        margin-right:-30px; }
    .bp3-control.bp3-large .bp3-control-indicator{
      font-size:20px; }
    .bp3-control.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-top:0; }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#137cbd;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.1)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.1), rgba(255, 255, 255, 0));
    color:#ffffff; }
  .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 -1px 0 rgba(16, 22, 26, 0.2);
    background-color:#106ba3; }
  .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background:#0e5a8a; }
  .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(19, 124, 189, 0.5); }
  .bp3-dark .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-checkbox:hover input:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    background-color:#106ba3; }
  .bp3-dark .bp3-control.bp3-checkbox input:not(:disabled):active:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#0e5a8a; }
  .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(14, 90, 138, 0.5); }
  .bp3-control.bp3-checkbox .bp3-control-indicator{
    border-radius:3px; }
  .bp3-control.bp3-checkbox input:checked ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M12 5c-.28 0-.53.11-.71.29L7 9.59l-2.29-2.3a1.003 1.003 0 0 0-1.42 1.42l3 3c.18.18.43.29.71.29s.53-.11.71-.29l5-5A1.003 1.003 0 0 0 12 5z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-checkbox input:indeterminate ~ .bp3-control-indicator::before{
    background-image:url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 16 16'%3e%3cpath fill-rule='evenodd' clip-rule='evenodd' d='M11 7H5c-.55 0-1 .45-1 1s.45 1 1 1h6c.55 0 1-.45 1-1s-.45-1-1-1z' fill='white'/%3e%3c/svg%3e"); }
  .bp3-control.bp3-radio .bp3-control-indicator{
    border-radius:50%; }
  .bp3-control.bp3-radio input:checked ~ .bp3-control-indicator::before{
    background-image:radial-gradient(#ffffff, #ffffff 28%, transparent 32%); }
  .bp3-control.bp3-radio input:checked:disabled ~ .bp3-control-indicator::before{
    opacity:0.5; }
  .bp3-control.bp3-radio input:focus ~ .bp3-control-indicator{
    -moz-outline-radius:16px; }
  .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(167, 182, 194, 0.5); }
  .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(115, 134, 148, 0.5); }
  .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(92, 112, 128, 0.5); }
  .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(206, 217, 224, 0.5); }
    .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(19, 124, 189, 0.5); }
    .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(255, 255, 255, 0.8); }
  .bp3-control.bp3-switch:not(.bp3-align-right){
    padding-left:38px; }
    .bp3-control.bp3-switch:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-38px; }
  .bp3-control.bp3-switch.bp3-align-right{
    padding-right:38px; }
    .bp3-control.bp3-switch.bp3-align-right .bp3-control-indicator{
      margin-right:-38px; }
  .bp3-control.bp3-switch .bp3-control-indicator{
    border:none;
    border-radius:1.75em;
    -webkit-box-shadow:none !important;
            box-shadow:none !important;
    width:auto;
    min-width:1.75em;
    -webkit-transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:background-color 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
    .bp3-control.bp3-switch .bp3-control-indicator::before{
      position:absolute;
      left:0;
      margin:2px;
      border-radius:50%;
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
      background:#ffffff;
      width:calc(1em - 4px);
      height:calc(1em - 4px);
      -webkit-transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
      transition:left 100ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    left:calc(100% - 1em); }
  .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right){
    padding-left:45px; }
    .bp3-control.bp3-switch.bp3-large:not(.bp3-align-right) .bp3-control-indicator{
      margin-left:-45px; }
  .bp3-control.bp3-switch.bp3-large.bp3-align-right{
    padding-right:45px; }
    .bp3-control.bp3-switch.bp3-large.bp3-align-right .bp3-control-indicator{
      margin-right:-45px; }
  .bp3-dark .bp3-control.bp3-switch input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-control.bp3-switch:hover input ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.7); }
  .bp3-dark .bp3-control.bp3-switch input:not(:disabled):active ~ .bp3-control-indicator{
    background:rgba(16, 22, 26, 0.9); }
  .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator{
    background:rgba(57, 75, 89, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator{
    background:#137cbd; }
  .bp3-dark .bp3-control.bp3-switch:hover input:checked ~ .bp3-control-indicator{
    background:#106ba3; }
  .bp3-dark .bp3-control.bp3-switch input:checked:not(:disabled):active ~ .bp3-control-indicator{
    background:#0e5a8a; }
  .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator{
    background:rgba(14, 90, 138, 0.5); }
    .bp3-dark .bp3-control.bp3-switch input:checked:disabled ~ .bp3-control-indicator::before{
      background:rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-control.bp3-switch .bp3-control-indicator::before{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    background:#394b59; }
  .bp3-dark .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator::before{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
  .bp3-control.bp3-switch .bp3-switch-inner-text{
    text-align:center;
    font-size:0.7em; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:first-child{
    visibility:hidden;
    margin-right:1.2em;
    margin-left:0.5em;
    line-height:0; }
  .bp3-control.bp3-switch .bp3-control-indicator-child:last-child{
    visibility:visible;
    margin-right:0.5em;
    margin-left:1.2em;
    line-height:1em; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:first-child{
    visibility:visible;
    line-height:1em; }
  .bp3-control.bp3-switch input:checked ~ .bp3-control-indicator .bp3-control-indicator-child:last-child{
    visibility:hidden;
    line-height:0; }
  .bp3-dark .bp3-control{
    color:#f5f8fa; }
    .bp3-dark .bp3-control.bp3-disabled{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-control .bp3-control-indicator{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0)); }
    .bp3-dark .bp3-control:hover .bp3-control-indicator{
      background-color:#30404d; }
    .bp3-dark .bp3-control input:not(:disabled):active ~ .bp3-control-indicator{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background:#202b33; }
    .bp3-dark .bp3-control input:disabled ~ .bp3-control-indicator{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(57, 75, 89, 0.5);
      cursor:not-allowed; }
    .bp3-dark .bp3-control.bp3-checkbox input:disabled:checked ~ .bp3-control-indicator, .bp3-dark .bp3-control.bp3-checkbox input:disabled:indeterminate ~ .bp3-control-indicator{
      color:rgba(167, 182, 194, 0.6); }
.bp3-file-input{
  display:inline-block;
  position:relative;
  cursor:pointer;
  height:30px; }
  .bp3-file-input input{
    opacity:0;
    margin:0;
    min-width:200px; }
    .bp3-file-input input:disabled + .bp3-file-upload-input,
    .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(206, 217, 224, 0.5);
      cursor:not-allowed;
      color:rgba(92, 112, 128, 0.6);
      resize:none; }
      .bp3-file-input input:disabled + .bp3-file-upload-input::after,
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
        outline:none;
        -webkit-box-shadow:none;
                box-shadow:none;
        background-color:rgba(206, 217, 224, 0.5);
        background-image:none;
        cursor:not-allowed;
        color:rgba(92, 112, 128, 0.6); }
        .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active:hover,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active,
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active:hover{
          background:rgba(206, 217, 224, 0.7); }
      .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input, .bp3-dark
      .bp3-file-input input.bp3-disabled + .bp3-file-upload-input{
        -webkit-box-shadow:none;
                box-shadow:none;
        background:rgba(57, 75, 89, 0.5);
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after, .bp3-dark
        .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after{
          -webkit-box-shadow:none;
                  box-shadow:none;
          background-color:rgba(57, 75, 89, 0.5);
          background-image:none;
          color:rgba(167, 182, 194, 0.6); }
          .bp3-dark .bp3-file-input input:disabled + .bp3-file-upload-input::after.bp3-active, .bp3-dark
          .bp3-file-input input.bp3-disabled + .bp3-file-upload-input::after.bp3-active{
            background:rgba(57, 75, 89, 0.7); }
  .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#182026; }
  .bp3-dark .bp3-file-input.bp3-file-input-has-selection .bp3-file-upload-input{
    color:#f5f8fa; }
  .bp3-file-input.bp3-fill{
    width:100%; }
  .bp3-file-input.bp3-large,
  .bp3-large .bp3-file-input{
    height:40px; }
  .bp3-file-input .bp3-file-upload-input-custom-text::after{
    content:attr(bp3-button-text); }

.bp3-file-upload-input{
  outline:none;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  background:#ffffff;
  height:30px;
  padding:0 10px;
  vertical-align:middle;
  line-height:30px;
  color:#182026;
  font-size:14px;
  font-weight:400;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none;
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  position:absolute;
  top:0;
  right:0;
  left:0;
  padding-right:80px;
  color:rgba(92, 112, 128, 0.6);
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-file-upload-input::-webkit-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-file-upload-input::-moz-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-file-upload-input:-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-file-upload-input::-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-file-upload-input::placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-file-upload-input:focus, .bp3-file-upload-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-file-upload-input[type="search"], .bp3-file-upload-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-file-upload-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-file-upload-input:disabled, .bp3-file-upload-input.bp3-disabled{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(206, 217, 224, 0.5);
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6);
    resize:none; }
  .bp3-file-upload-input::after{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-color:#f5f8fa;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
    color:#182026;
    min-width:24px;
    min-height:24px;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    position:absolute;
    top:0;
    right:0;
    margin:3px;
    border-radius:3px;
    width:70px;
    text-align:center;
    line-height:24px;
    content:"Browse"; }
    .bp3-file-upload-input::after:hover{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
      background-clip:padding-box;
      background-color:#ebf1f5; }
    .bp3-file-upload-input::after:active, .bp3-file-upload-input::after.bp3-active{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#d8e1e8;
      background-image:none; }
    .bp3-file-upload-input::after:disabled, .bp3-file-upload-input::after.bp3-disabled{
      outline:none;
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(206, 217, 224, 0.5);
      background-image:none;
      cursor:not-allowed;
      color:rgba(92, 112, 128, 0.6); }
      .bp3-file-upload-input::after:disabled.bp3-active, .bp3-file-upload-input::after:disabled.bp3-active:hover, .bp3-file-upload-input::after.bp3-disabled.bp3-active, .bp3-file-upload-input::after.bp3-disabled.bp3-active:hover{
        background:rgba(206, 217, 224, 0.7); }
  .bp3-file-upload-input:hover::after{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-clip:padding-box;
    background-color:#ebf1f5; }
  .bp3-file-upload-input:active::after{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#d8e1e8;
    background-image:none; }
  .bp3-large .bp3-file-upload-input{
    height:40px;
    line-height:40px;
    font-size:16px;
    padding-right:95px; }
    .bp3-large .bp3-file-upload-input[type="search"], .bp3-large .bp3-file-upload-input.bp3-round{
      padding:0 15px; }
    .bp3-large .bp3-file-upload-input::after{
      min-width:30px;
      min-height:30px;
      margin:5px;
      width:85px;
      line-height:30px; }
  .bp3-dark .bp3-file-upload-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    background:rgba(16, 22, 26, 0.3);
    color:#f5f8fa;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-file-upload-input:disabled, .bp3-dark .bp3-file-upload-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(57, 75, 89, 0.5);
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-file-upload-input::after{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      background-color:#394b59;
      background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
      background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
      color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover, .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        color:#f5f8fa; }
      .bp3-dark .bp3-file-upload-input::after:hover{
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
        background-color:#30404d; }
      .bp3-dark .bp3-file-upload-input::after:active, .bp3-dark .bp3-file-upload-input::after.bp3-active{
        -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
                box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
        background-color:#202b33;
        background-image:none; }
      .bp3-dark .bp3-file-upload-input::after:disabled, .bp3-dark .bp3-file-upload-input::after.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none;
        background-color:rgba(57, 75, 89, 0.5);
        background-image:none;
        color:rgba(167, 182, 194, 0.6); }
        .bp3-dark .bp3-file-upload-input::after:disabled.bp3-active, .bp3-dark .bp3-file-upload-input::after.bp3-disabled.bp3-active{
          background:rgba(57, 75, 89, 0.7); }
      .bp3-dark .bp3-file-upload-input::after .bp3-button-spinner .bp3-spinner-head{
        background:rgba(16, 22, 26, 0.5);
        stroke:#8a9ba8; }
    .bp3-dark .bp3-file-upload-input:hover::after{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      background-color:#30404d; }
    .bp3-dark .bp3-file-upload-input:active::after{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#202b33;
      background-image:none; }

.bp3-file-upload-input::after{
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1); }
.bp3-form-group{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin:0 0 15px; }
  .bp3-form-group label.bp3-label{
    margin-bottom:5px; }
  .bp3-form-group .bp3-control{
    margin-top:7px; }
  .bp3-form-group .bp3-form-helper-text{
    margin-top:5px;
    color:#5c7080;
    font-size:12px; }
  .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#106ba3; }
  .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#0d8050; }
  .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#bf7326; }
  .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#c23030; }
  .bp3-form-group.bp3-inline{
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start; }
    .bp3-form-group.bp3-inline.bp3-large label.bp3-label{
      margin:0 10px 0 0;
      line-height:40px; }
    .bp3-form-group.bp3-inline label.bp3-label{
      margin:0 10px 0 0;
      line-height:30px; }
  .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-dark .bp3-form-group.bp3-intent-primary .bp3-form-helper-text{
    color:#48aff0; }
  .bp3-dark .bp3-form-group.bp3-intent-success .bp3-form-helper-text{
    color:#3dcc91; }
  .bp3-dark .bp3-form-group.bp3-intent-warning .bp3-form-helper-text{
    color:#ffb366; }
  .bp3-dark .bp3-form-group.bp3-intent-danger .bp3-form-helper-text{
    color:#ff7373; }
  .bp3-dark .bp3-form-group .bp3-form-helper-text{
    color:#a7b6c2; }
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-label,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-text-muted,
  .bp3-dark .bp3-form-group.bp3-disabled .bp3-form-helper-text{
    color:rgba(167, 182, 194, 0.6) !important; }
.bp3-input-group{
  display:block;
  position:relative; }
  .bp3-input-group .bp3-input{
    position:relative;
    width:100%; }
    .bp3-input-group .bp3-input:not(:first-child){
      padding-left:30px; }
    .bp3-input-group .bp3-input:not(:last-child){
      padding-right:30px; }
  .bp3-input-group .bp3-input-action,
  .bp3-input-group > .bp3-button,
  .bp3-input-group > .bp3-icon{
    position:absolute;
    top:0; }
    .bp3-input-group .bp3-input-action:first-child,
    .bp3-input-group > .bp3-button:first-child,
    .bp3-input-group > .bp3-icon:first-child{
      left:0; }
    .bp3-input-group .bp3-input-action:last-child,
    .bp3-input-group > .bp3-button:last-child,
    .bp3-input-group > .bp3-icon:last-child{
      right:0; }
  .bp3-input-group .bp3-button{
    min-width:24px;
    min-height:24px;
    margin:3px;
    padding:0 7px; }
    .bp3-input-group .bp3-button:empty{
      padding:0; }
  .bp3-input-group > .bp3-icon{
    z-index:1;
    color:#5c7080; }
    .bp3-input-group > .bp3-icon:empty{
      line-height:1;
      font-family:"Icons16", sans-serif;
      font-size:16px;
      font-weight:400;
      font-style:normal;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased; }
  .bp3-input-group > .bp3-icon,
  .bp3-input-group .bp3-input-action > .bp3-spinner{
    margin:7px; }
  .bp3-input-group .bp3-tag{
    margin:5px; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus),
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
    color:#5c7080; }
    .bp3-dark .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus), .bp3-dark
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus){
      color:#a7b6c2; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:not(:hover):not(:focus) .bp3-icon-large{
      color:#5c7080; }
  .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled,
  .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled{
    color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-standard, .bp3-input-group .bp3-input:not(:focus) + .bp3-button.bp3-minimal:disabled .bp3-icon-large,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-standard,
    .bp3-input-group .bp3-input:not(:focus) + .bp3-input-action .bp3-button.bp3-minimal:disabled .bp3-icon-large{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-input-group.bp3-disabled{
    cursor:not-allowed; }
    .bp3-input-group.bp3-disabled .bp3-icon{
      color:rgba(92, 112, 128, 0.6); }
  .bp3-input-group.bp3-large .bp3-button{
    min-width:30px;
    min-height:30px;
    margin:5px; }
  .bp3-input-group.bp3-large > .bp3-icon,
  .bp3-input-group.bp3-large .bp3-input-action > .bp3-spinner{
    margin:12px; }
  .bp3-input-group.bp3-large .bp3-input{
    height:40px;
    line-height:40px;
    font-size:16px; }
    .bp3-input-group.bp3-large .bp3-input[type="search"], .bp3-input-group.bp3-large .bp3-input.bp3-round{
      padding:0 15px; }
    .bp3-input-group.bp3-large .bp3-input:not(:first-child){
      padding-left:40px; }
    .bp3-input-group.bp3-large .bp3-input:not(:last-child){
      padding-right:40px; }
  .bp3-input-group.bp3-small .bp3-button{
    min-width:20px;
    min-height:20px;
    margin:2px; }
  .bp3-input-group.bp3-small .bp3-tag{
    min-width:20px;
    min-height:20px;
    margin:2px; }
  .bp3-input-group.bp3-small > .bp3-icon,
  .bp3-input-group.bp3-small .bp3-input-action > .bp3-spinner{
    margin:4px; }
  .bp3-input-group.bp3-small .bp3-input{
    height:24px;
    padding-right:8px;
    padding-left:8px;
    line-height:24px;
    font-size:12px; }
    .bp3-input-group.bp3-small .bp3-input[type="search"], .bp3-input-group.bp3-small .bp3-input.bp3-round{
      padding:0 12px; }
    .bp3-input-group.bp3-small .bp3-input:not(:first-child){
      padding-left:24px; }
    .bp3-input-group.bp3-small .bp3-input:not(:last-child){
      padding-right:24px; }
  .bp3-input-group.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-input-group.bp3-round .bp3-button,
  .bp3-input-group.bp3-round .bp3-input,
  .bp3-input-group.bp3-round .bp3-tag{
    border-radius:30px; }
  .bp3-dark .bp3-input-group .bp3-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-input-group.bp3-disabled .bp3-icon{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-input-group.bp3-intent-primary .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-primary .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input-group.bp3-intent-primary .bp3-input:disabled, .bp3-input-group.bp3-intent-primary .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-primary > .bp3-icon{
    color:#106ba3; }
    .bp3-dark .bp3-input-group.bp3-intent-primary > .bp3-icon{
      color:#48aff0; }
  .bp3-input-group.bp3-intent-success .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-success .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input-group.bp3-intent-success .bp3-input:disabled, .bp3-input-group.bp3-intent-success .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-success > .bp3-icon{
    color:#0d8050; }
    .bp3-dark .bp3-input-group.bp3-intent-success > .bp3-icon{
      color:#3dcc91; }
  .bp3-input-group.bp3-intent-warning .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-warning .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input-group.bp3-intent-warning .bp3-input:disabled, .bp3-input-group.bp3-intent-warning .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-warning > .bp3-icon{
    color:#bf7326; }
    .bp3-dark .bp3-input-group.bp3-intent-warning > .bp3-icon{
      color:#ffb366; }
  .bp3-input-group.bp3-intent-danger .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input-group.bp3-intent-danger .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input-group.bp3-intent-danger .bp3-input:disabled, .bp3-input-group.bp3-intent-danger .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-input-group.bp3-intent-danger > .bp3-icon{
    color:#c23030; }
    .bp3-dark .bp3-input-group.bp3-intent-danger > .bp3-icon{
      color:#ff7373; }
.bp3-input{
  outline:none;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
  background:#ffffff;
  height:30px;
  padding:0 10px;
  vertical-align:middle;
  line-height:30px;
  color:#182026;
  font-size:14px;
  font-weight:400;
  -webkit-transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-box-shadow 100ms cubic-bezier(0.4, 1, 0.75, 0.9);
  -webkit-appearance:none;
     -moz-appearance:none;
          appearance:none; }
  .bp3-input::-webkit-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input::-moz-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input:-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input::-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input::placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input:focus, .bp3-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-input[type="search"], .bp3-input.bp3-round{
    border-radius:30px;
    -webkit-box-sizing:border-box;
            box-sizing:border-box;
    padding-left:10px; }
  .bp3-input[readonly]{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.15); }
  .bp3-input:disabled, .bp3-input.bp3-disabled{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(206, 217, 224, 0.5);
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6);
    resize:none; }
  .bp3-input.bp3-large{
    height:40px;
    line-height:40px;
    font-size:16px; }
    .bp3-input.bp3-large[type="search"], .bp3-input.bp3-large.bp3-round{
      padding:0 15px; }
  .bp3-input.bp3-small{
    height:24px;
    padding-right:8px;
    padding-left:8px;
    line-height:24px;
    font-size:12px; }
    .bp3-input.bp3-small[type="search"], .bp3-input.bp3-small.bp3-round{
      padding:0 12px; }
  .bp3-input.bp3-fill{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:100%; }
  .bp3-dark .bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    background:rgba(16, 22, 26, 0.3);
    color:#f5f8fa; }
    .bp3-dark .bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-input:disabled, .bp3-dark .bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(57, 75, 89, 0.5);
      color:rgba(167, 182, 194, 0.6); }
  .bp3-input.bp3-intent-primary{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-primary[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #137cbd;
              box-shadow:inset 0 0 0 1px #137cbd; }
    .bp3-input.bp3-intent-primary:disabled, .bp3-input.bp3-intent-primary.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px #137cbd, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary:focus{
        -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-primary[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #137cbd;
                box-shadow:inset 0 0 0 1px #137cbd; }
      .bp3-dark .bp3-input.bp3-intent-primary:disabled, .bp3-dark .bp3-input.bp3-intent-primary.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-success{
    -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success:focus{
      -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-success[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #0f9960;
              box-shadow:inset 0 0 0 1px #0f9960; }
    .bp3-input.bp3-intent-success:disabled, .bp3-input.bp3-intent-success.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-success{
      -webkit-box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), 0 0 0 0 rgba(15, 153, 96, 0), inset 0 0 0 1px #0f9960, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success:focus{
        -webkit-box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #0f9960, 0 0 0 1px #0f9960, 0 0 0 3px rgba(15, 153, 96, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-success[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #0f9960;
                box-shadow:inset 0 0 0 1px #0f9960; }
      .bp3-dark .bp3-input.bp3-intent-success:disabled, .bp3-dark .bp3-input.bp3-intent-success.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-warning{
    -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning:focus{
      -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-warning[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #d9822b;
              box-shadow:inset 0 0 0 1px #d9822b; }
    .bp3-input.bp3-intent-warning:disabled, .bp3-input.bp3-intent-warning.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), 0 0 0 0 rgba(217, 130, 43, 0), inset 0 0 0 1px #d9822b, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning:focus{
        -webkit-box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #d9822b, 0 0 0 1px #d9822b, 0 0 0 3px rgba(217, 130, 43, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-warning[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #d9822b;
                box-shadow:inset 0 0 0 1px #d9822b; }
      .bp3-dark .bp3-input.bp3-intent-warning:disabled, .bp3-dark .bp3-input.bp3-intent-warning.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input.bp3-intent-danger{
    -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger:focus{
      -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-input.bp3-intent-danger[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px #db3737;
              box-shadow:inset 0 0 0 1px #db3737; }
    .bp3-input.bp3-intent-danger:disabled, .bp3-input.bp3-intent-danger.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none; }
    .bp3-dark .bp3-input.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), 0 0 0 0 rgba(219, 55, 55, 0), inset 0 0 0 1px #db3737, inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger:focus{
        -webkit-box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
                box-shadow:0 0 0 1px #db3737, 0 0 0 1px #db3737, 0 0 0 3px rgba(219, 55, 55, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
      .bp3-dark .bp3-input.bp3-intent-danger[readonly]{
        -webkit-box-shadow:inset 0 0 0 1px #db3737;
                box-shadow:inset 0 0 0 1px #db3737; }
      .bp3-dark .bp3-input.bp3-intent-danger:disabled, .bp3-dark .bp3-input.bp3-intent-danger.bp3-disabled{
        -webkit-box-shadow:none;
                box-shadow:none; }
  .bp3-input::-ms-clear{
    display:none; }
textarea.bp3-input{
  max-width:100%;
  padding:10px; }
  textarea.bp3-input, textarea.bp3-input.bp3-large, textarea.bp3-input.bp3-small{
    height:auto;
    line-height:inherit; }
  textarea.bp3-input.bp3-small{
    padding:8px; }
  .bp3-dark textarea.bp3-input{
    -webkit-box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    background:rgba(16, 22, 26, 0.3);
    color:#f5f8fa; }
    .bp3-dark textarea.bp3-input::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input::placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark textarea.bp3-input:focus{
      -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input[readonly]{
      -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark textarea.bp3-input:disabled, .bp3-dark textarea.bp3-input.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:rgba(57, 75, 89, 0.5);
      color:rgba(167, 182, 194, 0.6); }
label.bp3-label{
  display:block;
  margin-top:0;
  margin-bottom:15px; }
  label.bp3-label .bp3-html-select,
  label.bp3-label .bp3-input,
  label.bp3-label .bp3-select,
  label.bp3-label .bp3-slider,
  label.bp3-label .bp3-popover-wrapper{
    display:block;
    margin-top:5px;
    text-transform:none; }
  label.bp3-label .bp3-button-group{
    margin-top:5px; }
  label.bp3-label .bp3-select select,
  label.bp3-label .bp3-html-select select{
    width:100%;
    vertical-align:top;
    font-weight:400; }
  label.bp3-label.bp3-disabled,
  label.bp3-label.bp3-disabled .bp3-text-muted{
    color:rgba(92, 112, 128, 0.6); }
  label.bp3-label.bp3-inline{
    line-height:30px; }
    label.bp3-label.bp3-inline .bp3-html-select,
    label.bp3-label.bp3-inline .bp3-input,
    label.bp3-label.bp3-inline .bp3-input-group,
    label.bp3-label.bp3-inline .bp3-select,
    label.bp3-label.bp3-inline .bp3-popover-wrapper{
      display:inline-block;
      margin:0 0 0 5px;
      vertical-align:top; }
    label.bp3-label.bp3-inline .bp3-button-group{
      margin:0 0 0 5px; }
    label.bp3-label.bp3-inline .bp3-input-group .bp3-input{
      margin-left:0; }
    label.bp3-label.bp3-inline.bp3-large{
      line-height:40px; }
  label.bp3-label:not(.bp3-inline) .bp3-popover-target{
    display:block; }
  .bp3-dark label.bp3-label{
    color:#f5f8fa; }
    .bp3-dark label.bp3-label.bp3-disabled,
    .bp3-dark label.bp3-label.bp3-disabled .bp3-text-muted{
      color:rgba(167, 182, 194, 0.6); }
.bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button{
  -webkit-box-flex:1;
      -ms-flex:1 1 14px;
          flex:1 1 14px;
  width:30px;
  min-height:0;
  padding:0; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:first-child{
    border-radius:0 3px 0 0; }
  .bp3-numeric-input .bp3-button-group.bp3-vertical > .bp3-button:last-child{
    border-radius:0 0 3px 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:first-child{
  border-radius:3px 0 0 0; }

.bp3-numeric-input .bp3-button-group.bp3-vertical:first-child > .bp3-button:last-child{
  border-radius:0 0 0 3px; }

.bp3-numeric-input.bp3-large .bp3-button-group.bp3-vertical > .bp3-button{
  width:40px; }

form{
  display:block; }
.bp3-html-select select,
.bp3-select select{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  border:none;
  border-radius:3px;
  cursor:pointer;
  padding:5px 10px;
  vertical-align:middle;
  text-align:left;
  font-size:14px;
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  color:#182026;
  border-radius:3px;
  width:100%;
  height:30px;
  padding:0 25px 0 10px;
  -moz-appearance:none;
  -webkit-appearance:none; }
  .bp3-html-select select > *, .bp3-select select > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-html-select select > .bp3-fill, .bp3-select select > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-html-select select::before,
  .bp3-select select::before, .bp3-html-select select > *, .bp3-select select > *{
    margin-right:7px; }
  .bp3-html-select select:empty::before,
  .bp3-select select:empty::before,
  .bp3-html-select select > :last-child,
  .bp3-select select > :last-child{
    margin-right:0; }
  .bp3-html-select select:hover,
  .bp3-select select:hover{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-clip:padding-box;
    background-color:#ebf1f5; }
  .bp3-html-select select:active,
  .bp3-select select:active, .bp3-html-select select.bp3-active,
  .bp3-select select.bp3-active{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#d8e1e8;
    background-image:none; }
  .bp3-html-select select:disabled,
  .bp3-select select:disabled, .bp3-html-select select.bp3-disabled,
  .bp3-select select.bp3-disabled{
    outline:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6); }
    .bp3-html-select select:disabled.bp3-active,
    .bp3-select select:disabled.bp3-active, .bp3-html-select select:disabled.bp3-active:hover,
    .bp3-select select:disabled.bp3-active:hover, .bp3-html-select select.bp3-disabled.bp3-active,
    .bp3-select select.bp3-disabled.bp3-active, .bp3-html-select select.bp3-disabled.bp3-active:hover,
    .bp3-select select.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }

.bp3-html-select.bp3-minimal select,
.bp3-select.bp3-minimal select{
  -webkit-box-shadow:none;
          box-shadow:none;
  background:none; }
  .bp3-html-select.bp3-minimal select:hover,
  .bp3-select.bp3-minimal select:hover{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(167, 182, 194, 0.3);
    text-decoration:none;
    color:#182026; }
  .bp3-html-select.bp3-minimal select:active,
  .bp3-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal select.bp3-active,
  .bp3-select.bp3-minimal select.bp3-active{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:rgba(115, 134, 148, 0.3);
    color:#182026; }
  .bp3-html-select.bp3-minimal select:disabled,
  .bp3-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal select:disabled:hover,
  .bp3-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal select.bp3-disabled,
  .bp3-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal select.bp3-disabled:hover,
  .bp3-select.bp3-minimal select.bp3-disabled:hover{
    background:none;
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6); }
    .bp3-html-select.bp3-minimal select:disabled.bp3-active,
    .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active,
    .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active{
      background:rgba(115, 134, 148, 0.3); }
  .bp3-dark .bp3-html-select.bp3-minimal select, .bp3-html-select.bp3-minimal .bp3-dark select,
  .bp3-dark .bp3-select.bp3-minimal select, .bp3-select.bp3-minimal .bp3-dark select{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:none;
    color:inherit; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover, .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none; }
    .bp3-dark .bp3-html-select.bp3-minimal select:hover, .bp3-html-select.bp3-minimal .bp3-dark select:hover,
    .bp3-dark .bp3-select.bp3-minimal select:hover, .bp3-select.bp3-minimal .bp3-dark select:hover{
      background:rgba(138, 155, 168, 0.15); }
    .bp3-dark .bp3-html-select.bp3-minimal select:active, .bp3-html-select.bp3-minimal .bp3-dark select:active,
    .bp3-dark .bp3-select.bp3-minimal select:active, .bp3-select.bp3-minimal .bp3-dark select:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-active,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-active{
      background:rgba(138, 155, 168, 0.3);
      color:#f5f8fa; }
    .bp3-dark .bp3-html-select.bp3-minimal select:disabled, .bp3-html-select.bp3-minimal .bp3-dark select:disabled,
    .bp3-dark .bp3-select.bp3-minimal select:disabled, .bp3-select.bp3-minimal .bp3-dark select:disabled, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select:disabled:hover, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover{
      background:none;
      cursor:not-allowed;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-html-select.bp3-minimal select:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select:disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select:disabled:hover.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-disabled:hover.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-disabled:hover.bp3-active{
        background:rgba(138, 155, 168, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-primary,
  .bp3-select.bp3-minimal select.bp3-intent-primary{
    color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none;
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover,
    .bp3-select.bp3-minimal select.bp3-intent-primary:hover{
      background:rgba(19, 124, 189, 0.15);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:active,
    .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active{
      background:rgba(19, 124, 189, 0.3);
      color:#106ba3; }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled{
      background:none;
      color:rgba(16, 107, 163, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active{
        background:rgba(19, 124, 189, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-primary .bp3-button-spinner .bp3-spinner-head{
      stroke:#106ba3; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary{
      color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:hover{
        background:rgba(19, 124, 189, 0.2);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-active{
        background:rgba(19, 124, 189, 0.3);
        color:#48aff0; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled{
        background:none;
        color:rgba(72, 175, 240, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-primary.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-primary.bp3-disabled.bp3-active{
          background:rgba(19, 124, 189, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-success,
  .bp3-select.bp3-minimal select.bp3-intent-success{
    color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none;
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:hover,
    .bp3-select.bp3-minimal select.bp3-intent-success:hover{
      background:rgba(15, 153, 96, 0.15);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:active,
    .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active{
      background:rgba(15, 153, 96, 0.3);
      color:#0d8050; }
    .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled{
      background:none;
      color:rgba(13, 128, 80, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active{
        background:rgba(15, 153, 96, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-success .bp3-button-spinner .bp3-spinner-head{
      stroke:#0d8050; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success{
      color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:hover{
        background:rgba(15, 153, 96, 0.2);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-active{
        background:rgba(15, 153, 96, 0.3);
        color:#3dcc91; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled{
        background:none;
        color:rgba(61, 204, 145, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-success.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-success.bp3-disabled.bp3-active{
          background:rgba(15, 153, 96, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-warning,
  .bp3-select.bp3-minimal select.bp3-intent-warning{
    color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none;
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover,
    .bp3-select.bp3-minimal select.bp3-intent-warning:hover{
      background:rgba(217, 130, 43, 0.15);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:active,
    .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active{
      background:rgba(217, 130, 43, 0.3);
      color:#bf7326; }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled{
      background:none;
      color:rgba(191, 115, 38, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active{
        background:rgba(217, 130, 43, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-warning .bp3-button-spinner .bp3-spinner-head{
      stroke:#bf7326; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning{
      color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:hover{
        background:rgba(217, 130, 43, 0.2);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-active{
        background:rgba(217, 130, 43, 0.3);
        color:#ffb366; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled{
        background:none;
        color:rgba(255, 179, 102, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-warning.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-warning.bp3-disabled.bp3-active{
          background:rgba(217, 130, 43, 0.3); }
  .bp3-html-select.bp3-minimal select.bp3-intent-danger,
  .bp3-select.bp3-minimal select.bp3-intent-danger{
    color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      -webkit-box-shadow:none;
              box-shadow:none;
      background:none;
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover,
    .bp3-select.bp3-minimal select.bp3-intent-danger:hover{
      background:rgba(219, 55, 55, 0.15);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:active,
    .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active{
      background:rgba(219, 55, 55, 0.3);
      color:#c23030; }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled,
    .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled{
      background:none;
      color:rgba(194, 48, 48, 0.5); }
      .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active,
      .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active{
        background:rgba(219, 55, 55, 0.3); }
    .bp3-html-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head, .bp3-select.bp3-minimal select.bp3-intent-danger .bp3-button-spinner .bp3-spinner-head{
      stroke:#c23030; }
    .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger,
    .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger{
      color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:hover, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:hover{
        background:rgba(219, 55, 55, 0.2);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-active{
        background:rgba(219, 55, 55, 0.3);
        color:#ff7373; }
      .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled,
      .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled{
        background:none;
        color:rgba(255, 115, 115, 0.5); }
        .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger:disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger:disabled.bp3-active, .bp3-dark .bp3-html-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-html-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active,
        .bp3-dark .bp3-select.bp3-minimal select.bp3-intent-danger.bp3-disabled.bp3-active, .bp3-select.bp3-minimal .bp3-dark select.bp3-intent-danger.bp3-disabled.bp3-active{
          background:rgba(219, 55, 55, 0.3); }

.bp3-html-select.bp3-large select,
.bp3-select.bp3-large select{
  height:40px;
  padding-right:35px;
  font-size:16px; }

.bp3-dark .bp3-html-select select, .bp3-dark .bp3-select select{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
  background-color:#394b59;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
  color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover, .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select select:hover, .bp3-dark .bp3-select select:hover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    background-color:#30404d; }
  .bp3-dark .bp3-html-select select:active, .bp3-dark .bp3-select select:active, .bp3-dark .bp3-html-select select.bp3-active, .bp3-dark .bp3-select select.bp3-active{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#202b33;
    background-image:none; }
  .bp3-dark .bp3-html-select select:disabled, .bp3-dark .bp3-select select:disabled, .bp3-dark .bp3-html-select select.bp3-disabled, .bp3-dark .bp3-select select.bp3-disabled{
    -webkit-box-shadow:none;
            box-shadow:none;
    background-color:rgba(57, 75, 89, 0.5);
    background-image:none;
    color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-html-select select:disabled.bp3-active, .bp3-dark .bp3-select select:disabled.bp3-active, .bp3-dark .bp3-html-select select.bp3-disabled.bp3-active, .bp3-dark .bp3-select select.bp3-disabled.bp3-active{
      background:rgba(57, 75, 89, 0.7); }
  .bp3-dark .bp3-html-select select .bp3-button-spinner .bp3-spinner-head, .bp3-dark .bp3-select select .bp3-button-spinner .bp3-spinner-head{
    background:rgba(16, 22, 26, 0.5);
    stroke:#8a9ba8; }

.bp3-html-select select:disabled,
.bp3-select select:disabled{
  -webkit-box-shadow:none;
          box-shadow:none;
  background-color:rgba(206, 217, 224, 0.5);
  cursor:not-allowed;
  color:rgba(92, 112, 128, 0.6); }

.bp3-html-select .bp3-icon,
.bp3-select .bp3-icon, .bp3-select::after{
  position:absolute;
  top:7px;
  right:7px;
  color:#5c7080;
  pointer-events:none; }
  .bp3-html-select .bp3-disabled.bp3-icon,
  .bp3-select .bp3-disabled.bp3-icon, .bp3-disabled.bp3-select::after{
    color:rgba(92, 112, 128, 0.6); }
.bp3-html-select,
.bp3-select{
  display:inline-block;
  position:relative;
  vertical-align:middle;
  letter-spacing:normal; }
  .bp3-html-select select::-ms-expand,
  .bp3-select select::-ms-expand{
    display:none; }
  .bp3-html-select .bp3-icon,
  .bp3-select .bp3-icon{
    color:#5c7080; }
    .bp3-html-select .bp3-icon:hover,
    .bp3-select .bp3-icon:hover{
      color:#182026; }
    .bp3-dark .bp3-html-select .bp3-icon, .bp3-dark
    .bp3-select .bp3-icon{
      color:#a7b6c2; }
      .bp3-dark .bp3-html-select .bp3-icon:hover, .bp3-dark
      .bp3-select .bp3-icon:hover{
        color:#f5f8fa; }
  .bp3-html-select.bp3-large::after,
  .bp3-html-select.bp3-large .bp3-icon,
  .bp3-select.bp3-large::after,
  .bp3-select.bp3-large .bp3-icon{
    top:12px;
    right:12px; }
  .bp3-html-select.bp3-fill,
  .bp3-html-select.bp3-fill select,
  .bp3-select.bp3-fill,
  .bp3-select.bp3-fill select{
    width:100%; }
  .bp3-dark .bp3-html-select option, .bp3-dark
  .bp3-select option{
    background-color:#30404d;
    color:#f5f8fa; }
  .bp3-dark .bp3-html-select::after, .bp3-dark
  .bp3-select::after{
    color:#a7b6c2; }

.bp3-select::after{
  line-height:1;
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-weight:400;
  font-style:normal;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  content:""; }
.bp3-running-text table, table.bp3-html-table{
  border-spacing:0;
  font-size:14px; }
  .bp3-running-text table th, table.bp3-html-table th,
  .bp3-running-text table td,
  table.bp3-html-table td{
    padding:11px;
    vertical-align:top;
    text-align:left; }
  .bp3-running-text table th, table.bp3-html-table th{
    color:#182026;
    font-weight:600; }
  
  .bp3-running-text table td,
  table.bp3-html-table td{
    color:#182026; }
  .bp3-running-text table tbody tr:first-child th, table.bp3-html-table tbody tr:first-child th,
  .bp3-running-text table tbody tr:first-child td,
  table.bp3-html-table tbody tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-running-text table th, .bp3-running-text .bp3-dark table th, .bp3-dark table.bp3-html-table th{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table td, .bp3-running-text .bp3-dark table td, .bp3-dark table.bp3-html-table td{
    color:#f5f8fa; }
  .bp3-dark .bp3-running-text table tbody tr:first-child th, .bp3-running-text .bp3-dark table tbody tr:first-child th, .bp3-dark table.bp3-html-table tbody tr:first-child th,
  .bp3-dark .bp3-running-text table tbody tr:first-child td,
  .bp3-running-text .bp3-dark table tbody tr:first-child td,
  .bp3-dark table.bp3-html-table tbody tr:first-child td{
    -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }

table.bp3-html-table.bp3-html-table-condensed th,
table.bp3-html-table.bp3-html-table-condensed td, table.bp3-html-table.bp3-small th,
table.bp3-html-table.bp3-small td{
  padding-top:6px;
  padding-bottom:6px; }

table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
  background:rgba(191, 204, 214, 0.15); }

table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
  -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered tbody tr td{
  -webkit-box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15);
          box-shadow:inset 0 1px 0 0 rgba(16, 22, 26, 0.15); }
  table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child){
    -webkit-box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 1px 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
  -webkit-box-shadow:none;
          box-shadow:none; }
  table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:not(:first-child){
    -webkit-box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 1px 0 0 0 rgba(16, 22, 26, 0.15); }

table.bp3-html-table.bp3-interactive tbody tr:hover td{
  background-color:rgba(191, 204, 214, 0.3);
  cursor:pointer; }

table.bp3-html-table.bp3-interactive tbody tr:active td{
  background-color:rgba(191, 204, 214, 0.4); }

.bp3-dark table.bp3-html-table.bp3-html-table-striped tbody tr:nth-child(odd) td{
  background:rgba(92, 112, 128, 0.15); }

.bp3-dark table.bp3-html-table.bp3-html-table-bordered th:not(:first-child){
  -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
          box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }

.bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td{
  -webkit-box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15);
          box-shadow:inset 0 1px 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered tbody tr td:not(:first-child){
    -webkit-box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15);
            box-shadow:inset 1px 1px 0 0 rgba(255, 255, 255, 0.15); }

.bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td{
  -webkit-box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15);
          box-shadow:inset 1px 0 0 0 rgba(255, 255, 255, 0.15); }
  .bp3-dark table.bp3-html-table.bp3-html-table-bordered.bp3-html-table-striped tbody tr:not(:first-child) td:first-child{
    -webkit-box-shadow:none;
            box-shadow:none; }

.bp3-dark table.bp3-html-table.bp3-interactive tbody tr:hover td{
  background-color:rgba(92, 112, 128, 0.3);
  cursor:pointer; }

.bp3-dark table.bp3-html-table.bp3-interactive tbody tr:active td{
  background-color:rgba(92, 112, 128, 0.4); }

.bp3-key-combo{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center; }
  .bp3-key-combo > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-key-combo > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-key-combo::before,
  .bp3-key-combo > *{
    margin-right:5px; }
  .bp3-key-combo:empty::before,
  .bp3-key-combo > :last-child{
    margin-right:0; }

.bp3-hotkey-dialog{
  top:40px;
  padding-bottom:0; }
  .bp3-hotkey-dialog .bp3-dialog-body{
    margin:0;
    padding:0; }
  .bp3-hotkey-dialog .bp3-hotkey-label{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1; }

.bp3-hotkey-column{
  margin:auto;
  max-height:80vh;
  overflow-y:auto;
  padding:30px; }
  .bp3-hotkey-column .bp3-heading{
    margin-bottom:20px; }
    .bp3-hotkey-column .bp3-heading:not(:first-child){
      margin-top:40px; }

.bp3-hotkey{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:justify;
      -ms-flex-pack:justify;
          justify-content:space-between;
  margin-right:0;
  margin-left:0; }
  .bp3-hotkey:not(:last-child){
    margin-bottom:10px; }
.bp3-icon{
  display:inline-block;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  vertical-align:text-bottom; }
  .bp3-icon:not(:empty)::before{
    content:"" !important;
    content:unset !important; }
  .bp3-icon > svg{
    display:block; }
    .bp3-icon > svg:not([fill]){
      fill:currentColor; }

.bp3-icon.bp3-intent-primary, .bp3-icon-standard.bp3-intent-primary, .bp3-icon-large.bp3-intent-primary{
  color:#106ba3; }
  .bp3-dark .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-icon-large.bp3-intent-primary{
    color:#48aff0; }

.bp3-icon.bp3-intent-success, .bp3-icon-standard.bp3-intent-success, .bp3-icon-large.bp3-intent-success{
  color:#0d8050; }
  .bp3-dark .bp3-icon.bp3-intent-success, .bp3-dark .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-icon-large.bp3-intent-success{
    color:#3dcc91; }

.bp3-icon.bp3-intent-warning, .bp3-icon-standard.bp3-intent-warning, .bp3-icon-large.bp3-intent-warning{
  color:#bf7326; }
  .bp3-dark .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-icon-large.bp3-intent-warning{
    color:#ffb366; }

.bp3-icon.bp3-intent-danger, .bp3-icon-standard.bp3-intent-danger, .bp3-icon-large.bp3-intent-danger{
  color:#c23030; }
  .bp3-dark .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-icon-large.bp3-intent-danger{
    color:#ff7373; }

span.bp3-icon-standard{
  line-height:1;
  font-family:"Icons16", sans-serif;
  font-size:16px;
  font-weight:400;
  font-style:normal;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon-large{
  line-height:1;
  font-family:"Icons20", sans-serif;
  font-size:20px;
  font-weight:400;
  font-style:normal;
  -moz-osx-font-smoothing:grayscale;
  -webkit-font-smoothing:antialiased;
  display:inline-block; }

span.bp3-icon:empty{
  line-height:1;
  font-family:"Icons20";
  font-size:inherit;
  font-weight:400;
  font-style:normal; }
  span.bp3-icon:empty::before{
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased; }

.bp3-icon-add::before{
  content:""; }

.bp3-icon-add-column-left::before{
  content:""; }

.bp3-icon-add-column-right::before{
  content:""; }

.bp3-icon-add-row-bottom::before{
  content:""; }

.bp3-icon-add-row-top::before{
  content:""; }

.bp3-icon-add-to-artifact::before{
  content:""; }

.bp3-icon-add-to-folder::before{
  content:""; }

.bp3-icon-airplane::before{
  content:""; }

.bp3-icon-align-center::before{
  content:""; }

.bp3-icon-align-justify::before{
  content:""; }

.bp3-icon-align-left::before{
  content:""; }

.bp3-icon-align-right::before{
  content:""; }

.bp3-icon-alignment-bottom::before{
  content:""; }

.bp3-icon-alignment-horizontal-center::before{
  content:""; }

.bp3-icon-alignment-left::before{
  content:""; }

.bp3-icon-alignment-right::before{
  content:""; }

.bp3-icon-alignment-top::before{
  content:""; }

.bp3-icon-alignment-vertical-center::before{
  content:""; }

.bp3-icon-annotation::before{
  content:""; }

.bp3-icon-application::before{
  content:""; }

.bp3-icon-applications::before{
  content:""; }

.bp3-icon-archive::before{
  content:""; }

.bp3-icon-arrow-bottom-left::before{
  content:"↙"; }

.bp3-icon-arrow-bottom-right::before{
  content:"↘"; }

.bp3-icon-arrow-down::before{
  content:"↓"; }

.bp3-icon-arrow-left::before{
  content:"←"; }

.bp3-icon-arrow-right::before{
  content:"→"; }

.bp3-icon-arrow-top-left::before{
  content:"↖"; }

.bp3-icon-arrow-top-right::before{
  content:"↗"; }

.bp3-icon-arrow-up::before{
  content:"↑"; }

.bp3-icon-arrows-horizontal::before{
  content:"↔"; }

.bp3-icon-arrows-vertical::before{
  content:"↕"; }

.bp3-icon-asterisk::before{
  content:"*"; }

.bp3-icon-automatic-updates::before{
  content:""; }

.bp3-icon-badge::before{
  content:""; }

.bp3-icon-ban-circle::before{
  content:""; }

.bp3-icon-bank-account::before{
  content:""; }

.bp3-icon-barcode::before{
  content:""; }

.bp3-icon-blank::before{
  content:""; }

.bp3-icon-blocked-person::before{
  content:""; }

.bp3-icon-bold::before{
  content:""; }

.bp3-icon-book::before{
  content:""; }

.bp3-icon-bookmark::before{
  content:""; }

.bp3-icon-box::before{
  content:""; }

.bp3-icon-briefcase::before{
  content:""; }

.bp3-icon-bring-data::before{
  content:""; }

.bp3-icon-build::before{
  content:""; }

.bp3-icon-calculator::before{
  content:""; }

.bp3-icon-calendar::before{
  content:""; }

.bp3-icon-camera::before{
  content:""; }

.bp3-icon-caret-down::before{
  content:"⌄"; }

.bp3-icon-caret-left::before{
  content:"〈"; }

.bp3-icon-caret-right::before{
  content:"〉"; }

.bp3-icon-caret-up::before{
  content:"⌃"; }

.bp3-icon-cell-tower::before{
  content:""; }

.bp3-icon-changes::before{
  content:""; }

.bp3-icon-chart::before{
  content:""; }

.bp3-icon-chat::before{
  content:""; }

.bp3-icon-chevron-backward::before{
  content:""; }

.bp3-icon-chevron-down::before{
  content:""; }

.bp3-icon-chevron-forward::before{
  content:""; }

.bp3-icon-chevron-left::before{
  content:""; }

.bp3-icon-chevron-right::before{
  content:""; }

.bp3-icon-chevron-up::before{
  content:""; }

.bp3-icon-circle::before{
  content:""; }

.bp3-icon-circle-arrow-down::before{
  content:""; }

.bp3-icon-circle-arrow-left::before{
  content:""; }

.bp3-icon-circle-arrow-right::before{
  content:""; }

.bp3-icon-circle-arrow-up::before{
  content:""; }

.bp3-icon-citation::before{
  content:""; }

.bp3-icon-clean::before{
  content:""; }

.bp3-icon-clipboard::before{
  content:""; }

.bp3-icon-cloud::before{
  content:"☁"; }

.bp3-icon-cloud-download::before{
  content:""; }

.bp3-icon-cloud-upload::before{
  content:""; }

.bp3-icon-code::before{
  content:""; }

.bp3-icon-code-block::before{
  content:""; }

.bp3-icon-cog::before{
  content:""; }

.bp3-icon-collapse-all::before{
  content:""; }

.bp3-icon-column-layout::before{
  content:""; }

.bp3-icon-comment::before{
  content:""; }

.bp3-icon-comparison::before{
  content:""; }

.bp3-icon-compass::before{
  content:""; }

.bp3-icon-compressed::before{
  content:""; }

.bp3-icon-confirm::before{
  content:""; }

.bp3-icon-console::before{
  content:""; }

.bp3-icon-contrast::before{
  content:""; }

.bp3-icon-control::before{
  content:""; }

.bp3-icon-credit-card::before{
  content:""; }

.bp3-icon-cross::before{
  content:"✗"; }

.bp3-icon-crown::before{
  content:""; }

.bp3-icon-cube::before{
  content:""; }

.bp3-icon-cube-add::before{
  content:""; }

.bp3-icon-cube-remove::before{
  content:""; }

.bp3-icon-curved-range-chart::before{
  content:""; }

.bp3-icon-cut::before{
  content:""; }

.bp3-icon-dashboard::before{
  content:""; }

.bp3-icon-data-lineage::before{
  content:""; }

.bp3-icon-database::before{
  content:""; }

.bp3-icon-delete::before{
  content:""; }

.bp3-icon-delta::before{
  content:"Δ"; }

.bp3-icon-derive-column::before{
  content:""; }

.bp3-icon-desktop::before{
  content:""; }

.bp3-icon-diagram-tree::before{
  content:""; }

.bp3-icon-direction-left::before{
  content:""; }

.bp3-icon-direction-right::before{
  content:""; }

.bp3-icon-disable::before{
  content:""; }

.bp3-icon-document::before{
  content:""; }

.bp3-icon-document-open::before{
  content:""; }

.bp3-icon-document-share::before{
  content:""; }

.bp3-icon-dollar::before{
  content:"$"; }

.bp3-icon-dot::before{
  content:"•"; }

.bp3-icon-double-caret-horizontal::before{
  content:""; }

.bp3-icon-double-caret-vertical::before{
  content:""; }

.bp3-icon-double-chevron-down::before{
  content:""; }

.bp3-icon-double-chevron-left::before{
  content:""; }

.bp3-icon-double-chevron-right::before{
  content:""; }

.bp3-icon-double-chevron-up::before{
  content:""; }

.bp3-icon-doughnut-chart::before{
  content:""; }

.bp3-icon-download::before{
  content:""; }

.bp3-icon-drag-handle-horizontal::before{
  content:""; }

.bp3-icon-drag-handle-vertical::before{
  content:""; }

.bp3-icon-draw::before{
  content:""; }

.bp3-icon-drive-time::before{
  content:""; }

.bp3-icon-duplicate::before{
  content:""; }

.bp3-icon-edit::before{
  content:"✎"; }

.bp3-icon-eject::before{
  content:"⏏"; }

.bp3-icon-endorsed::before{
  content:""; }

.bp3-icon-envelope::before{
  content:"✉"; }

.bp3-icon-equals::before{
  content:""; }

.bp3-icon-eraser::before{
  content:""; }

.bp3-icon-error::before{
  content:""; }

.bp3-icon-euro::before{
  content:"€"; }

.bp3-icon-exchange::before{
  content:""; }

.bp3-icon-exclude-row::before{
  content:""; }

.bp3-icon-expand-all::before{
  content:""; }

.bp3-icon-export::before{
  content:""; }

.bp3-icon-eye-off::before{
  content:""; }

.bp3-icon-eye-on::before{
  content:""; }

.bp3-icon-eye-open::before{
  content:""; }

.bp3-icon-fast-backward::before{
  content:""; }

.bp3-icon-fast-forward::before{
  content:""; }

.bp3-icon-feed::before{
  content:""; }

.bp3-icon-feed-subscribed::before{
  content:""; }

.bp3-icon-film::before{
  content:""; }

.bp3-icon-filter::before{
  content:""; }

.bp3-icon-filter-keep::before{
  content:""; }

.bp3-icon-filter-list::before{
  content:""; }

.bp3-icon-filter-open::before{
  content:""; }

.bp3-icon-filter-remove::before{
  content:""; }

.bp3-icon-flag::before{
  content:"⚑"; }

.bp3-icon-flame::before{
  content:""; }

.bp3-icon-flash::before{
  content:""; }

.bp3-icon-floppy-disk::before{
  content:""; }

.bp3-icon-flow-branch::before{
  content:""; }

.bp3-icon-flow-end::before{
  content:""; }

.bp3-icon-flow-linear::before{
  content:""; }

.bp3-icon-flow-review::before{
  content:""; }

.bp3-icon-flow-review-branch::before{
  content:""; }

.bp3-icon-flows::before{
  content:""; }

.bp3-icon-folder-close::before{
  content:""; }

.bp3-icon-folder-new::before{
  content:""; }

.bp3-icon-folder-open::before{
  content:""; }

.bp3-icon-folder-shared::before{
  content:""; }

.bp3-icon-folder-shared-open::before{
  content:""; }

.bp3-icon-follower::before{
  content:""; }

.bp3-icon-following::before{
  content:""; }

.bp3-icon-font::before{
  content:""; }

.bp3-icon-fork::before{
  content:""; }

.bp3-icon-form::before{
  content:""; }

.bp3-icon-full-circle::before{
  content:""; }

.bp3-icon-full-stacked-chart::before{
  content:""; }

.bp3-icon-fullscreen::before{
  content:""; }

.bp3-icon-function::before{
  content:""; }

.bp3-icon-gantt-chart::before{
  content:""; }

.bp3-icon-geolocation::before{
  content:""; }

.bp3-icon-geosearch::before{
  content:""; }

.bp3-icon-git-branch::before{
  content:""; }

.bp3-icon-git-commit::before{
  content:""; }

.bp3-icon-git-merge::before{
  content:""; }

.bp3-icon-git-new-branch::before{
  content:""; }

.bp3-icon-git-pull::before{
  content:""; }

.bp3-icon-git-push::before{
  content:""; }

.bp3-icon-git-repo::before{
  content:""; }

.bp3-icon-glass::before{
  content:""; }

.bp3-icon-globe::before{
  content:""; }

.bp3-icon-globe-network::before{
  content:""; }

.bp3-icon-graph::before{
  content:""; }

.bp3-icon-graph-remove::before{
  content:""; }

.bp3-icon-greater-than::before{
  content:""; }

.bp3-icon-greater-than-or-equal-to::before{
  content:""; }

.bp3-icon-grid::before{
  content:""; }

.bp3-icon-grid-view::before{
  content:""; }

.bp3-icon-group-objects::before{
  content:""; }

.bp3-icon-grouped-bar-chart::before{
  content:""; }

.bp3-icon-hand::before{
  content:""; }

.bp3-icon-hand-down::before{
  content:""; }

.bp3-icon-hand-left::before{
  content:""; }

.bp3-icon-hand-right::before{
  content:""; }

.bp3-icon-hand-up::before{
  content:""; }

.bp3-icon-header::before{
  content:""; }

.bp3-icon-header-one::before{
  content:""; }

.bp3-icon-header-two::before{
  content:""; }

.bp3-icon-headset::before{
  content:""; }

.bp3-icon-heart::before{
  content:"♥"; }

.bp3-icon-heart-broken::before{
  content:""; }

.bp3-icon-heat-grid::before{
  content:""; }

.bp3-icon-heatmap::before{
  content:""; }

.bp3-icon-help::before{
  content:"?"; }

.bp3-icon-helper-management::before{
  content:""; }

.bp3-icon-highlight::before{
  content:""; }

.bp3-icon-history::before{
  content:""; }

.bp3-icon-home::before{
  content:"⌂"; }

.bp3-icon-horizontal-bar-chart::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-asc::before{
  content:""; }

.bp3-icon-horizontal-bar-chart-desc::before{
  content:""; }

.bp3-icon-horizontal-distribution::before{
  content:""; }

.bp3-icon-id-number::before{
  content:""; }

.bp3-icon-image-rotate-left::before{
  content:""; }

.bp3-icon-image-rotate-right::before{
  content:""; }

.bp3-icon-import::before{
  content:""; }

.bp3-icon-inbox::before{
  content:""; }

.bp3-icon-inbox-filtered::before{
  content:""; }

.bp3-icon-inbox-geo::before{
  content:""; }

.bp3-icon-inbox-search::before{
  content:""; }

.bp3-icon-inbox-update::before{
  content:""; }

.bp3-icon-info-sign::before{
  content:"ℹ"; }

.bp3-icon-inheritance::before{
  content:""; }

.bp3-icon-inner-join::before{
  content:""; }

.bp3-icon-insert::before{
  content:""; }

.bp3-icon-intersection::before{
  content:""; }

.bp3-icon-ip-address::before{
  content:""; }

.bp3-icon-issue::before{
  content:""; }

.bp3-icon-issue-closed::before{
  content:""; }

.bp3-icon-issue-new::before{
  content:""; }

.bp3-icon-italic::before{
  content:""; }

.bp3-icon-join-table::before{
  content:""; }

.bp3-icon-key::before{
  content:""; }

.bp3-icon-key-backspace::before{
  content:""; }

.bp3-icon-key-command::before{
  content:""; }

.bp3-icon-key-control::before{
  content:""; }

.bp3-icon-key-delete::before{
  content:""; }

.bp3-icon-key-enter::before{
  content:""; }

.bp3-icon-key-escape::before{
  content:""; }

.bp3-icon-key-option::before{
  content:""; }

.bp3-icon-key-shift::before{
  content:""; }

.bp3-icon-key-tab::before{
  content:""; }

.bp3-icon-known-vehicle::before{
  content:""; }

.bp3-icon-label::before{
  content:""; }

.bp3-icon-layer::before{
  content:""; }

.bp3-icon-layers::before{
  content:""; }

.bp3-icon-layout::before{
  content:""; }

.bp3-icon-layout-auto::before{
  content:""; }

.bp3-icon-layout-balloon::before{
  content:""; }

.bp3-icon-layout-circle::before{
  content:""; }

.bp3-icon-layout-grid::before{
  content:""; }

.bp3-icon-layout-group-by::before{
  content:""; }

.bp3-icon-layout-hierarchy::before{
  content:""; }

.bp3-icon-layout-linear::before{
  content:""; }

.bp3-icon-layout-skew-grid::before{
  content:""; }

.bp3-icon-layout-sorted-clusters::before{
  content:""; }

.bp3-icon-learning::before{
  content:""; }

.bp3-icon-left-join::before{
  content:""; }

.bp3-icon-less-than::before{
  content:""; }

.bp3-icon-less-than-or-equal-to::before{
  content:""; }

.bp3-icon-lifesaver::before{
  content:""; }

.bp3-icon-lightbulb::before{
  content:""; }

.bp3-icon-link::before{
  content:""; }

.bp3-icon-list::before{
  content:"☰"; }

.bp3-icon-list-columns::before{
  content:""; }

.bp3-icon-list-detail-view::before{
  content:""; }

.bp3-icon-locate::before{
  content:""; }

.bp3-icon-lock::before{
  content:""; }

.bp3-icon-log-in::before{
  content:""; }

.bp3-icon-log-out::before{
  content:""; }

.bp3-icon-manual::before{
  content:""; }

.bp3-icon-manually-entered-data::before{
  content:""; }

.bp3-icon-map::before{
  content:""; }

.bp3-icon-map-create::before{
  content:""; }

.bp3-icon-map-marker::before{
  content:""; }

.bp3-icon-maximize::before{
  content:""; }

.bp3-icon-media::before{
  content:""; }

.bp3-icon-menu::before{
  content:""; }

.bp3-icon-menu-closed::before{
  content:""; }

.bp3-icon-menu-open::before{
  content:""; }

.bp3-icon-merge-columns::before{
  content:""; }

.bp3-icon-merge-links::before{
  content:""; }

.bp3-icon-minimize::before{
  content:""; }

.bp3-icon-minus::before{
  content:"−"; }

.bp3-icon-mobile-phone::before{
  content:""; }

.bp3-icon-mobile-video::before{
  content:""; }

.bp3-icon-moon::before{
  content:""; }

.bp3-icon-more::before{
  content:""; }

.bp3-icon-mountain::before{
  content:""; }

.bp3-icon-move::before{
  content:""; }

.bp3-icon-mugshot::before{
  content:""; }

.bp3-icon-multi-select::before{
  content:""; }

.bp3-icon-music::before{
  content:""; }

.bp3-icon-new-drawing::before{
  content:""; }

.bp3-icon-new-grid-item::before{
  content:""; }

.bp3-icon-new-layer::before{
  content:""; }

.bp3-icon-new-layers::before{
  content:""; }

.bp3-icon-new-link::before{
  content:""; }

.bp3-icon-new-object::before{
  content:""; }

.bp3-icon-new-person::before{
  content:""; }

.bp3-icon-new-prescription::before{
  content:""; }

.bp3-icon-new-text-box::before{
  content:""; }

.bp3-icon-ninja::before{
  content:""; }

.bp3-icon-not-equal-to::before{
  content:""; }

.bp3-icon-notifications::before{
  content:""; }

.bp3-icon-notifications-updated::before{
  content:""; }

.bp3-icon-numbered-list::before{
  content:""; }

.bp3-icon-numerical::before{
  content:""; }

.bp3-icon-office::before{
  content:""; }

.bp3-icon-offline::before{
  content:""; }

.bp3-icon-oil-field::before{
  content:""; }

.bp3-icon-one-column::before{
  content:""; }

.bp3-icon-outdated::before{
  content:""; }

.bp3-icon-page-layout::before{
  content:""; }

.bp3-icon-panel-stats::before{
  content:""; }

.bp3-icon-panel-table::before{
  content:""; }

.bp3-icon-paperclip::before{
  content:""; }

.bp3-icon-paragraph::before{
  content:""; }

.bp3-icon-path::before{
  content:""; }

.bp3-icon-path-search::before{
  content:""; }

.bp3-icon-pause::before{
  content:""; }

.bp3-icon-people::before{
  content:""; }

.bp3-icon-percentage::before{
  content:""; }

.bp3-icon-person::before{
  content:""; }

.bp3-icon-phone::before{
  content:"☎"; }

.bp3-icon-pie-chart::before{
  content:""; }

.bp3-icon-pin::before{
  content:""; }

.bp3-icon-pivot::before{
  content:""; }

.bp3-icon-pivot-table::before{
  content:""; }

.bp3-icon-play::before{
  content:""; }

.bp3-icon-plus::before{
  content:"+"; }

.bp3-icon-polygon-filter::before{
  content:""; }

.bp3-icon-power::before{
  content:""; }

.bp3-icon-predictive-analysis::before{
  content:""; }

.bp3-icon-prescription::before{
  content:""; }

.bp3-icon-presentation::before{
  content:""; }

.bp3-icon-print::before{
  content:"⎙"; }

.bp3-icon-projects::before{
  content:""; }

.bp3-icon-properties::before{
  content:""; }

.bp3-icon-property::before{
  content:""; }

.bp3-icon-publish-function::before{
  content:""; }

.bp3-icon-pulse::before{
  content:""; }

.bp3-icon-random::before{
  content:""; }

.bp3-icon-record::before{
  content:""; }

.bp3-icon-redo::before{
  content:""; }

.bp3-icon-refresh::before{
  content:""; }

.bp3-icon-regression-chart::before{
  content:""; }

.bp3-icon-remove::before{
  content:""; }

.bp3-icon-remove-column::before{
  content:""; }

.bp3-icon-remove-column-left::before{
  content:""; }

.bp3-icon-remove-column-right::before{
  content:""; }

.bp3-icon-remove-row-bottom::before{
  content:""; }

.bp3-icon-remove-row-top::before{
  content:""; }

.bp3-icon-repeat::before{
  content:""; }

.bp3-icon-reset::before{
  content:""; }

.bp3-icon-resolve::before{
  content:""; }

.bp3-icon-rig::before{
  content:""; }

.bp3-icon-right-join::before{
  content:""; }

.bp3-icon-ring::before{
  content:""; }

.bp3-icon-rotate-document::before{
  content:""; }

.bp3-icon-rotate-page::before{
  content:""; }

.bp3-icon-satellite::before{
  content:""; }

.bp3-icon-saved::before{
  content:""; }

.bp3-icon-scatter-plot::before{
  content:""; }

.bp3-icon-search::before{
  content:""; }

.bp3-icon-search-around::before{
  content:""; }

.bp3-icon-search-template::before{
  content:""; }

.bp3-icon-search-text::before{
  content:""; }

.bp3-icon-segmented-control::before{
  content:""; }

.bp3-icon-select::before{
  content:""; }

.bp3-icon-selection::before{
  content:"⦿"; }

.bp3-icon-send-to::before{
  content:""; }

.bp3-icon-send-to-graph::before{
  content:""; }

.bp3-icon-send-to-map::before{
  content:""; }

.bp3-icon-series-add::before{
  content:""; }

.bp3-icon-series-configuration::before{
  content:""; }

.bp3-icon-series-derived::before{
  content:""; }

.bp3-icon-series-filtered::before{
  content:""; }

.bp3-icon-series-search::before{
  content:""; }

.bp3-icon-settings::before{
  content:""; }

.bp3-icon-share::before{
  content:""; }

.bp3-icon-shield::before{
  content:""; }

.bp3-icon-shop::before{
  content:""; }

.bp3-icon-shopping-cart::before{
  content:""; }

.bp3-icon-signal-search::before{
  content:""; }

.bp3-icon-sim-card::before{
  content:""; }

.bp3-icon-slash::before{
  content:""; }

.bp3-icon-small-cross::before{
  content:""; }

.bp3-icon-small-minus::before{
  content:""; }

.bp3-icon-small-plus::before{
  content:""; }

.bp3-icon-small-tick::before{
  content:""; }

.bp3-icon-snowflake::before{
  content:""; }

.bp3-icon-social-media::before{
  content:""; }

.bp3-icon-sort::before{
  content:""; }

.bp3-icon-sort-alphabetical::before{
  content:""; }

.bp3-icon-sort-alphabetical-desc::before{
  content:""; }

.bp3-icon-sort-asc::before{
  content:""; }

.bp3-icon-sort-desc::before{
  content:""; }

.bp3-icon-sort-numerical::before{
  content:""; }

.bp3-icon-sort-numerical-desc::before{
  content:""; }

.bp3-icon-split-columns::before{
  content:""; }

.bp3-icon-square::before{
  content:""; }

.bp3-icon-stacked-chart::before{
  content:""; }

.bp3-icon-star::before{
  content:"★"; }

.bp3-icon-star-empty::before{
  content:"☆"; }

.bp3-icon-step-backward::before{
  content:""; }

.bp3-icon-step-chart::before{
  content:""; }

.bp3-icon-step-forward::before{
  content:""; }

.bp3-icon-stop::before{
  content:""; }

.bp3-icon-stopwatch::before{
  content:""; }

.bp3-icon-strikethrough::before{
  content:""; }

.bp3-icon-style::before{
  content:""; }

.bp3-icon-swap-horizontal::before{
  content:""; }

.bp3-icon-swap-vertical::before{
  content:""; }

.bp3-icon-symbol-circle::before{
  content:""; }

.bp3-icon-symbol-cross::before{
  content:""; }

.bp3-icon-symbol-diamond::before{
  content:""; }

.bp3-icon-symbol-square::before{
  content:""; }

.bp3-icon-symbol-triangle-down::before{
  content:""; }

.bp3-icon-symbol-triangle-up::before{
  content:""; }

.bp3-icon-tag::before{
  content:""; }

.bp3-icon-take-action::before{
  content:""; }

.bp3-icon-taxi::before{
  content:""; }

.bp3-icon-text-highlight::before{
  content:""; }

.bp3-icon-th::before{
  content:""; }

.bp3-icon-th-derived::before{
  content:""; }

.bp3-icon-th-disconnect::before{
  content:""; }

.bp3-icon-th-filtered::before{
  content:""; }

.bp3-icon-th-list::before{
  content:""; }

.bp3-icon-thumbs-down::before{
  content:""; }

.bp3-icon-thumbs-up::before{
  content:""; }

.bp3-icon-tick::before{
  content:"✓"; }

.bp3-icon-tick-circle::before{
  content:""; }

.bp3-icon-time::before{
  content:"⏲"; }

.bp3-icon-timeline-area-chart::before{
  content:""; }

.bp3-icon-timeline-bar-chart::before{
  content:""; }

.bp3-icon-timeline-events::before{
  content:""; }

.bp3-icon-timeline-line-chart::before{
  content:""; }

.bp3-icon-tint::before{
  content:""; }

.bp3-icon-torch::before{
  content:""; }

.bp3-icon-tractor::before{
  content:""; }

.bp3-icon-train::before{
  content:""; }

.bp3-icon-translate::before{
  content:""; }

.bp3-icon-trash::before{
  content:""; }

.bp3-icon-tree::before{
  content:""; }

.bp3-icon-trending-down::before{
  content:""; }

.bp3-icon-trending-up::before{
  content:""; }

.bp3-icon-truck::before{
  content:""; }

.bp3-icon-two-columns::before{
  content:""; }

.bp3-icon-unarchive::before{
  content:""; }

.bp3-icon-underline::before{
  content:"⎁"; }

.bp3-icon-undo::before{
  content:"⎌"; }

.bp3-icon-ungroup-objects::before{
  content:""; }

.bp3-icon-unknown-vehicle::before{
  content:""; }

.bp3-icon-unlock::before{
  content:""; }

.bp3-icon-unpin::before{
  content:""; }

.bp3-icon-unresolve::before{
  content:""; }

.bp3-icon-updated::before{
  content:""; }

.bp3-icon-upload::before{
  content:""; }

.bp3-icon-user::before{
  content:""; }

.bp3-icon-variable::before{
  content:""; }

.bp3-icon-vertical-bar-chart-asc::before{
  content:""; }

.bp3-icon-vertical-bar-chart-desc::before{
  content:""; }

.bp3-icon-vertical-distribution::before{
  content:""; }

.bp3-icon-video::before{
  content:""; }

.bp3-icon-volume-down::before{
  content:""; }

.bp3-icon-volume-off::before{
  content:""; }

.bp3-icon-volume-up::before{
  content:""; }

.bp3-icon-walk::before{
  content:""; }

.bp3-icon-warning-sign::before{
  content:""; }

.bp3-icon-waterfall-chart::before{
  content:""; }

.bp3-icon-widget::before{
  content:""; }

.bp3-icon-widget-button::before{
  content:""; }

.bp3-icon-widget-footer::before{
  content:""; }

.bp3-icon-widget-header::before{
  content:""; }

.bp3-icon-wrench::before{
  content:""; }

.bp3-icon-zoom-in::before{
  content:""; }

.bp3-icon-zoom-out::before{
  content:""; }

.bp3-icon-zoom-to-fit::before{
  content:""; }
.bp3-submenu > .bp3-popover-wrapper{
  display:block; }

.bp3-submenu .bp3-popover-target{
  display:block; }

.bp3-submenu.bp3-popover{
  -webkit-box-shadow:none;
          box-shadow:none;
  padding:0 5px; }
  .bp3-submenu.bp3-popover > .bp3-popover-content{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-submenu.bp3-popover, .bp3-submenu.bp3-popover.bp3-dark{
    -webkit-box-shadow:none;
            box-shadow:none; }
    .bp3-dark .bp3-submenu.bp3-popover > .bp3-popover-content, .bp3-submenu.bp3-popover.bp3-dark > .bp3-popover-content{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
.bp3-menu{
  margin:0;
  border-radius:3px;
  background:#ffffff;
  min-width:180px;
  padding:5px;
  list-style:none;
  text-align:left;
  color:#182026; }

.bp3-menu-divider{
  display:block;
  margin:5px;
  border-top:1px solid rgba(16, 22, 26, 0.15); }
  .bp3-dark .bp3-menu-divider{
    border-top-color:rgba(255, 255, 255, 0.15); }

.bp3-menu-item{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  border-radius:2px;
  padding:5px 7px;
  text-decoration:none;
  line-height:20px;
  color:inherit;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-menu-item > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-menu-item > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-menu-item::before,
  .bp3-menu-item > *{
    margin-right:7px; }
  .bp3-menu-item:empty::before,
  .bp3-menu-item > :last-child{
    margin-right:0; }
  .bp3-menu-item > .bp3-fill{
    word-break:break-word; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    background-color:rgba(167, 182, 194, 0.3);
    cursor:pointer;
    text-decoration:none; }
  .bp3-menu-item.bp3-disabled{
    background-color:inherit;
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-dark .bp3-menu-item{
    color:inherit; }
    .bp3-dark .bp3-menu-item:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
      background-color:rgba(138, 155, 168, 0.15);
      color:inherit; }
    .bp3-dark .bp3-menu-item.bp3-disabled{
      background-color:inherit;
      color:rgba(167, 182, 194, 0.6); }
  .bp3-menu-item.bp3-intent-primary{
    color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-primary::before, .bp3-menu-item.bp3-intent-primary::after,
    .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
      color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary.bp3-active{
      background-color:#137cbd; }
    .bp3-menu-item.bp3-intent-primary:active{
      background-color:#106ba3; }
    .bp3-menu-item.bp3-intent-primary:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary:active, .bp3-menu-item.bp3-intent-primary:active::before, .bp3-menu-item.bp3-intent-primary:active::after,
    .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-menu-item.bp3-intent-primary.bp3-active::after,
    .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-success{
    color:#0d8050; }
    .bp3-menu-item.bp3-intent-success .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-success::before, .bp3-menu-item.bp3-intent-success::after,
    .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
      color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success.bp3-active{
      background-color:#0f9960; }
    .bp3-menu-item.bp3-intent-success:active{
      background-color:#0d8050; }
    .bp3-menu-item.bp3-intent-success:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-menu-item.bp3-intent-success:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-menu-item.bp3-intent-success:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success:active, .bp3-menu-item.bp3-intent-success:active::before, .bp3-menu-item.bp3-intent-success:active::after,
    .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-menu-item.bp3-intent-success.bp3-active::after,
    .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-warning{
    color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-warning::before, .bp3-menu-item.bp3-intent-warning::after,
    .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
      color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning.bp3-active{
      background-color:#d9822b; }
    .bp3-menu-item.bp3-intent-warning:active{
      background-color:#bf7326; }
    .bp3-menu-item.bp3-intent-warning:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning:active, .bp3-menu-item.bp3-intent-warning:active::before, .bp3-menu-item.bp3-intent-warning:active::after,
    .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-menu-item.bp3-intent-warning.bp3-active::after,
    .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item.bp3-intent-danger{
    color:#c23030; }
    .bp3-menu-item.bp3-intent-danger .bp3-icon{
      color:inherit; }
    .bp3-menu-item.bp3-intent-danger::before, .bp3-menu-item.bp3-intent-danger::after,
    .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
      color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger.bp3-active{
      background-color:#db3737; }
    .bp3-menu-item.bp3-intent-danger:active{
      background-color:#c23030; }
    .bp3-menu-item.bp3-intent-danger:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
    .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
    .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger:active, .bp3-menu-item.bp3-intent-danger:active::before, .bp3-menu-item.bp3-intent-danger:active::after,
    .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-menu-item.bp3-intent-danger.bp3-active::after,
    .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
      color:#ffffff; }
  .bp3-menu-item::before{
    line-height:1;
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-weight:400;
    font-style:normal;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    margin-right:7px; }
  .bp3-menu-item::before,
  .bp3-menu-item > .bp3-icon{
    margin-top:2px;
    color:#5c7080; }
  .bp3-menu-item .bp3-menu-item-label{
    color:#5c7080; }
  .bp3-menu-item:hover, .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-menu-item{
    color:inherit; }
  .bp3-menu-item.bp3-active, .bp3-menu-item:active{
    background-color:rgba(115, 134, 148, 0.3); }
  .bp3-menu-item.bp3-disabled{
    outline:none !important;
    background-color:inherit !important;
    cursor:not-allowed !important;
    color:rgba(92, 112, 128, 0.6) !important; }
    .bp3-menu-item.bp3-disabled::before,
    .bp3-menu-item.bp3-disabled > .bp3-icon,
    .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
      color:rgba(92, 112, 128, 0.6) !important; }
  .bp3-large .bp3-menu-item{
    padding:9px 7px;
    line-height:22px;
    font-size:16px; }
    .bp3-large .bp3-menu-item .bp3-icon{
      margin-top:3px; }
    .bp3-large .bp3-menu-item::before{
      line-height:1;
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-weight:400;
      font-style:normal;
      -moz-osx-font-smoothing:grayscale;
      -webkit-font-smoothing:antialiased;
      margin-top:1px;
      margin-right:10px; }

button.bp3-menu-item{
  border:none;
  background:none;
  width:100%;
  text-align:left; }
.bp3-menu-header{
  display:block;
  margin:5px;
  border-top:1px solid rgba(16, 22, 26, 0.15);
  cursor:default;
  padding-left:2px; }
  .bp3-dark .bp3-menu-header{
    border-top-color:rgba(255, 255, 255, 0.15); }
  .bp3-menu-header:first-of-type{
    border-top:none; }
  .bp3-menu-header > h6{
    color:#182026;
    font-weight:600;
    overflow:hidden;
    text-overflow:ellipsis;
    white-space:nowrap;
    word-wrap:normal;
    margin:0;
    padding:10px 7px 0 1px;
    line-height:17px; }
    .bp3-dark .bp3-menu-header > h6{
      color:#f5f8fa; }
  .bp3-menu-header:first-of-type > h6{
    padding-top:0; }
  .bp3-large .bp3-menu-header > h6{
    padding-top:15px;
    padding-bottom:5px;
    font-size:18px; }
  .bp3-large .bp3-menu-header:first-of-type > h6{
    padding-top:0; }

.bp3-dark .bp3-menu{
  background:#30404d;
  color:#f5f8fa; }

.bp3-dark .bp3-menu-item.bp3-intent-primary{
  color:#48aff0; }
  .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-icon{
    color:inherit; }
  .bp3-dark .bp3-menu-item.bp3-intent-primary::before, .bp3-dark .bp3-menu-item.bp3-intent-primary::after,
  .bp3-dark .bp3-menu-item.bp3-intent-primary .bp3-menu-item-label{
    color:#48aff0; }
  .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active{
    background-color:#137cbd; }
  .bp3-dark .bp3-menu-item.bp3-intent-primary:active{
    background-color:#106ba3; }
  .bp3-dark .bp3-menu-item.bp3-intent-primary:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item::after,
  .bp3-dark .bp3-menu-item.bp3-intent-primary:hover .bp3-menu-item-label,
  .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label,
  .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-primary.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary:active, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary:active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-primary:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-primary.bp3-active .bp3-menu-item-label{
    color:#ffffff; }

.bp3-dark .bp3-menu-item.bp3-intent-success{
  color:#3dcc91; }
  .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-icon{
    color:inherit; }
  .bp3-dark .bp3-menu-item.bp3-intent-success::before, .bp3-dark .bp3-menu-item.bp3-intent-success::after,
  .bp3-dark .bp3-menu-item.bp3-intent-success .bp3-menu-item-label{
    color:#3dcc91; }
  .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active{
    background-color:#0f9960; }
  .bp3-dark .bp3-menu-item.bp3-intent-success:active{
    background-color:#0d8050; }
  .bp3-dark .bp3-menu-item.bp3-intent-success:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-success:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item::after,
  .bp3-dark .bp3-menu-item.bp3-intent-success:hover .bp3-menu-item-label,
  .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label,
  .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-success.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success:active, .bp3-dark .bp3-menu-item.bp3-intent-success:active::before, .bp3-dark .bp3-menu-item.bp3-intent-success:active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-success:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-success.bp3-active .bp3-menu-item-label{
    color:#ffffff; }

.bp3-dark .bp3-menu-item.bp3-intent-warning{
  color:#ffb366; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-icon{
    color:inherit; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning::before, .bp3-dark .bp3-menu-item.bp3-intent-warning::after,
  .bp3-dark .bp3-menu-item.bp3-intent-warning .bp3-menu-item-label{
    color:#ffb366; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active{
    background-color:#d9822b; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning:active{
    background-color:#bf7326; }
  .bp3-dark .bp3-menu-item.bp3-intent-warning:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item::after,
  .bp3-dark .bp3-menu-item.bp3-intent-warning:hover .bp3-menu-item-label,
  .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label,
  .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-warning.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning:active, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning:active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-warning:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-warning.bp3-active .bp3-menu-item-label{
    color:#ffffff; }

.bp3-dark .bp3-menu-item.bp3-intent-danger{
  color:#ff7373; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-icon{
    color:inherit; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger::before, .bp3-dark .bp3-menu-item.bp3-intent-danger::after,
  .bp3-dark .bp3-menu-item.bp3-intent-danger .bp3-menu-item-label{
    color:#ff7373; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active{
    background-color:#db3737; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger:active{
    background-color:#c23030; }
  .bp3-dark .bp3-menu-item.bp3-intent-danger:hover, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::before, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:hover::after, .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after, .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item::after,
  .bp3-dark .bp3-menu-item.bp3-intent-danger:hover .bp3-menu-item-label,
  .bp3-dark .bp3-submenu .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label,
  .bp3-submenu .bp3-dark .bp3-popover-target.bp3-popover-open > .bp3-intent-danger.bp3-menu-item .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger:active, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger:active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-danger:active .bp3-menu-item-label, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::before, .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active::after,
  .bp3-dark .bp3-menu-item.bp3-intent-danger.bp3-active .bp3-menu-item-label{
    color:#ffffff; }

.bp3-dark .bp3-menu-item::before,
.bp3-dark .bp3-menu-item > .bp3-icon{
  color:#a7b6c2; }

.bp3-dark .bp3-menu-item .bp3-menu-item-label{
  color:#a7b6c2; }

.bp3-dark .bp3-menu-item.bp3-active, .bp3-dark .bp3-menu-item:active{
  background-color:rgba(138, 155, 168, 0.3); }

.bp3-dark .bp3-menu-item.bp3-disabled{
  color:rgba(167, 182, 194, 0.6) !important; }
  .bp3-dark .bp3-menu-item.bp3-disabled::before,
  .bp3-dark .bp3-menu-item.bp3-disabled > .bp3-icon,
  .bp3-dark .bp3-menu-item.bp3-disabled .bp3-menu-item-label{
    color:rgba(167, 182, 194, 0.6) !important; }

.bp3-dark .bp3-menu-divider,
.bp3-dark .bp3-menu-header{
  border-color:rgba(255, 255, 255, 0.15); }

.bp3-dark .bp3-menu-header > h6{
  color:#f5f8fa; }

.bp3-label .bp3-menu{
  margin-top:5px; }
.bp3-navbar{
  position:relative;
  z-index:10;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.2);
  background-color:#ffffff;
  width:100%;
  height:50px;
  padding:0 15px; }
  .bp3-navbar.bp3-dark,
  .bp3-dark .bp3-navbar{
    background-color:#394b59; }
  .bp3-navbar.bp3-dark{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-dark .bp3-navbar{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 0 0 rgba(16, 22, 26, 0), 0 1px 1px rgba(16, 22, 26, 0.4); }
  .bp3-navbar.bp3-fixed-top{
    position:fixed;
    top:0;
    right:0;
    left:0; }

.bp3-navbar-heading{
  margin-right:15px;
  font-size:16px; }

.bp3-navbar-group{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  height:50px; }
  .bp3-navbar-group.bp3-align-left{
    float:left; }
  .bp3-navbar-group.bp3-align-right{
    float:right; }

.bp3-navbar-divider{
  margin:0 10px;
  border-left:1px solid rgba(16, 22, 26, 0.15);
  height:20px; }
  .bp3-dark .bp3-navbar-divider{
    border-left-color:rgba(255, 255, 255, 0.15); }
.bp3-non-ideal-state{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  width:100%;
  height:100%;
  text-align:center; }
  .bp3-non-ideal-state > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-non-ideal-state > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-non-ideal-state::before,
  .bp3-non-ideal-state > *{
    margin-bottom:20px; }
  .bp3-non-ideal-state:empty::before,
  .bp3-non-ideal-state > :last-child{
    margin-bottom:0; }
  .bp3-non-ideal-state > *{
    max-width:400px; }

.bp3-non-ideal-state-visual{
  color:rgba(92, 112, 128, 0.6);
  font-size:60px; }
  .bp3-dark .bp3-non-ideal-state-visual{
    color:rgba(167, 182, 194, 0.6); }

.bp3-overflow-list{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-wrap:nowrap;
      flex-wrap:nowrap;
  min-width:0; }

.bp3-overflow-list-spacer{
  -ms-flex-negative:1;
      flex-shrink:1;
  width:1px; }

body.bp3-overlay-open{
  overflow:hidden; }

.bp3-overlay{
  position:static;
  top:0;
  right:0;
  bottom:0;
  left:0;
  z-index:20; }
  .bp3-overlay:not(.bp3-overlay-open){
    pointer-events:none; }
  .bp3-overlay.bp3-overlay-container{
    position:fixed;
    overflow:hidden; }
    .bp3-overlay.bp3-overlay-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-scroll-container{
    position:fixed;
    overflow:auto; }
    .bp3-overlay.bp3-overlay-scroll-container.bp3-overlay-inline{
      position:absolute; }
  .bp3-overlay.bp3-overlay-inline{
    display:inline;
    overflow:visible; }

.bp3-overlay-content{
  position:fixed;
  z-index:20; }
  .bp3-overlay-inline .bp3-overlay-content,
  .bp3-overlay-scroll-container .bp3-overlay-content{
    position:absolute; }

.bp3-overlay-backdrop{
  position:fixed;
  top:0;
  right:0;
  bottom:0;
  left:0;
  opacity:1;
  z-index:20;
  background-color:rgba(16, 22, 26, 0.7);
  overflow:auto;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-overlay-backdrop.bp3-overlay-enter, .bp3-overlay-backdrop.bp3-overlay-appear{
    opacity:0; }
  .bp3-overlay-backdrop.bp3-overlay-enter-active, .bp3-overlay-backdrop.bp3-overlay-appear-active{
    opacity:1;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-overlay-backdrop.bp3-overlay-exit{
    opacity:1; }
  .bp3-overlay-backdrop.bp3-overlay-exit-active{
    opacity:0;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-overlay-backdrop:focus{
    outline:none; }
  .bp3-overlay-inline .bp3-overlay-backdrop{
    position:absolute; }
.bp3-panel-stack{
  position:relative;
  overflow:hidden; }

.bp3-panel-stack-header{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -ms-flex-negative:0;
      flex-shrink:0;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  z-index:1;
  -webkit-box-shadow:0 1px rgba(16, 22, 26, 0.15);
          box-shadow:0 1px rgba(16, 22, 26, 0.15);
  height:30px; }
  .bp3-dark .bp3-panel-stack-header{
    -webkit-box-shadow:0 1px rgba(255, 255, 255, 0.15);
            box-shadow:0 1px rgba(255, 255, 255, 0.15); }
  .bp3-panel-stack-header > span{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-flex:1;
        -ms-flex:1;
            flex:1;
    -webkit-box-align:stretch;
        -ms-flex-align:stretch;
            align-items:stretch; }
  .bp3-panel-stack-header .bp3-heading{
    margin:0 5px; }

.bp3-button.bp3-panel-stack-header-back{
  margin-left:5px;
  padding-left:0;
  white-space:nowrap; }
  .bp3-button.bp3-panel-stack-header-back .bp3-icon{
    margin:0 2px; }

.bp3-panel-stack-view{
  position:absolute;
  top:0;
  right:0;
  bottom:0;
  left:0;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  margin-right:-1px;
  border-right:1px solid rgba(16, 22, 26, 0.15);
  background-color:#ffffff;
  overflow-y:auto; }
  .bp3-dark .bp3-panel-stack-view{
    background-color:#30404d; }

.bp3-panel-stack-push .bp3-panel-stack-enter, .bp3-panel-stack-push .bp3-panel-stack-appear{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0; }

.bp3-panel-stack-push .bp3-panel-stack-enter-active, .bp3-panel-stack-push .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease;
  -webkit-transition-delay:0;
          transition-delay:0; }

.bp3-panel-stack-push .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-push .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease;
  -webkit-transition-delay:0;
          transition-delay:0; }

.bp3-panel-stack-pop .bp3-panel-stack-enter, .bp3-panel-stack-pop .bp3-panel-stack-appear{
  -webkit-transform:translateX(-50%);
          transform:translateX(-50%);
  opacity:0; }

.bp3-panel-stack-pop .bp3-panel-stack-enter-active, .bp3-panel-stack-pop .bp3-panel-stack-appear-active{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease;
  -webkit-transition-delay:0;
          transition-delay:0; }

.bp3-panel-stack-pop .bp3-panel-stack-exit{
  -webkit-transform:translate(0%);
          transform:translate(0%);
  opacity:1; }

.bp3-panel-stack-pop .bp3-panel-stack-exit-active{
  -webkit-transform:translateX(100%);
          transform:translateX(100%);
  opacity:0;
  -webkit-transition-property:opacity, -webkit-transform;
  transition-property:opacity, -webkit-transform;
  transition-property:transform, opacity;
  transition-property:transform, opacity, -webkit-transform;
  -webkit-transition-duration:400ms;
          transition-duration:400ms;
  -webkit-transition-timing-function:ease;
          transition-timing-function:ease;
  -webkit-transition-delay:0;
          transition-delay:0; }
.bp3-popover{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1);
  display:inline-block;
  z-index:20;
  border-radius:3px; }
  .bp3-popover .bp3-popover-arrow{
    position:absolute;
    width:30px;
    height:30px; }
    .bp3-popover .bp3-popover-arrow::before{
      margin:5px;
      width:20px;
      height:20px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover{
    margin-top:-17px;
    margin-bottom:17px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
      bottom:-11px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover{
    margin-left:17px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
      left:-11px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover{
    margin-top:17px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
      top:-11px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover{
    margin-right:17px;
    margin-left:-17px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
      right:-11px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-popover > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-popover > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-popover > .bp3-popover-arrow{
    top:-0.3934px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-popover > .bp3-popover-arrow{
    right:-0.3934px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-popover > .bp3-popover-arrow{
    left:-0.3934px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-popover > .bp3-popover-arrow{
    bottom:-0.3934px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-popover{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-popover{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-popover{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-popover .bp3-popover-content{
    background:#ffffff;
    color:inherit; }
  .bp3-popover .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-popover .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-popover .bp3-popover-arrow-fill{
    fill:#ffffff; }
  .bp3-popover-enter > .bp3-popover, .bp3-popover-appear > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3); }
  .bp3-popover-enter-active > .bp3-popover, .bp3-popover-appear-active > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-popover-exit > .bp3-popover{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-popover{
    -webkit-transform:scale(0.3);
            transform:scale(0.3);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-popover .bp3-popover-content{
    position:relative;
    border-radius:3px; }
  .bp3-popover.bp3-popover-content-sizing .bp3-popover-content{
    max-width:350px;
    padding:20px; }
  .bp3-popover-target + .bp3-overlay .bp3-popover.bp3-popover-content-sizing{
    width:350px; }
  .bp3-popover.bp3-minimal{
    margin:0 !important; }
    .bp3-popover.bp3-minimal .bp3-popover-arrow{
      display:none; }
    .bp3-popover.bp3-minimal.bp3-popover{
      -webkit-transform:scale(1);
              transform:scale(1); }
      .bp3-popover-enter > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-enter-active > .bp3-popover.bp3-minimal.bp3-popover, .bp3-popover-appear-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
        -webkit-transition-delay:0;
                transition-delay:0; }
      .bp3-popover-exit > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1); }
      .bp3-popover-exit-active > .bp3-popover.bp3-minimal.bp3-popover{
        -webkit-transform:scale(1);
                transform:scale(1);
        -webkit-transition-property:-webkit-transform;
        transition-property:-webkit-transform;
        transition-property:transform;
        transition-property:transform, -webkit-transform;
        -webkit-transition-duration:100ms;
                transition-duration:100ms;
        -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
                transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
        -webkit-transition-delay:0;
                transition-delay:0; }
  .bp3-popover.bp3-dark,
  .bp3-dark .bp3-popover{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-popover .bp3-popover-content{
      background:#30404d;
      color:inherit; }
    .bp3-popover.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-popover .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-popover.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-popover .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-popover.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-popover .bp3-popover-arrow-fill{
      fill:#30404d; }

.bp3-popover-arrow::before{
  display:block;
  position:absolute;
  -webkit-transform:rotate(45deg);
          transform:rotate(45deg);
  border-radius:2px;
  content:""; }

.bp3-tether-pinned .bp3-popover-arrow{
  display:none; }

.bp3-popover-backdrop{
  background:rgba(255, 255, 255, 0); }

.bp3-transition-container{
  opacity:1;
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  z-index:20; }
  .bp3-transition-container.bp3-popover-enter, .bp3-transition-container.bp3-popover-appear{
    opacity:0; }
  .bp3-transition-container.bp3-popover-enter-active, .bp3-transition-container.bp3-popover-appear-active{
    opacity:1;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-transition-container.bp3-popover-exit{
    opacity:1; }
  .bp3-transition-container.bp3-popover-exit-active{
    opacity:0;
    -webkit-transition-property:opacity;
    transition-property:opacity;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-transition-container:focus{
    outline:none; }
  .bp3-transition-container.bp3-popover-leave .bp3-popover-content{
    pointer-events:none; }
  .bp3-transition-container[data-x-out-of-boundaries]{
    display:none; }

span.bp3-popover-target{
  display:inline-block; }

.bp3-popover-wrapper.bp3-fill{
  width:100%; }

.bp3-portal{
  position:absolute;
  top:0;
  right:0;
  left:0; }
@-webkit-keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }
@keyframes linear-progress-bar-stripes{
  from{
    background-position:0 0; }
  to{
    background-position:30px 0; } }

.bp3-progress-bar{
  display:block;
  position:relative;
  border-radius:40px;
  background:rgba(92, 112, 128, 0.2);
  width:100%;
  height:8px;
  overflow:hidden; }
  .bp3-progress-bar .bp3-progress-meter{
    position:absolute;
    border-radius:40px;
    background:linear-gradient(-45deg, rgba(255, 255, 255, 0.2) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.2) 50%, rgba(255, 255, 255, 0.2) 75%, transparent 75%);
    background-color:rgba(92, 112, 128, 0.8);
    background-size:30px 30px;
    width:100%;
    height:100%;
    -webkit-transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:width 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-progress-bar:not(.bp3-no-animation):not(.bp3-no-stripes) .bp3-progress-meter{
    animation:linear-progress-bar-stripes 300ms linear infinite reverse; }
  .bp3-progress-bar.bp3-no-stripes .bp3-progress-meter{
    background-image:none; }

.bp3-dark .bp3-progress-bar{
  background:rgba(16, 22, 26, 0.5); }
  .bp3-dark .bp3-progress-bar .bp3-progress-meter{
    background-color:#8a9ba8; }

.bp3-progress-bar.bp3-intent-primary .bp3-progress-meter{
  background-color:#137cbd; }

.bp3-progress-bar.bp3-intent-success .bp3-progress-meter{
  background-color:#0f9960; }

.bp3-progress-bar.bp3-intent-warning .bp3-progress-meter{
  background-color:#d9822b; }

.bp3-progress-bar.bp3-intent-danger .bp3-progress-meter{
  background-color:#db3737; }
@-webkit-keyframes skeleton-glow{
  from{
    border-color:rgba(206, 217, 224, 0.2);
    background:rgba(206, 217, 224, 0.2); }
  to{
    border-color:rgba(92, 112, 128, 0.2);
    background:rgba(92, 112, 128, 0.2); } }
@keyframes skeleton-glow{
  from{
    border-color:rgba(206, 217, 224, 0.2);
    background:rgba(206, 217, 224, 0.2); }
  to{
    border-color:rgba(92, 112, 128, 0.2);
    background:rgba(92, 112, 128, 0.2); } }
.bp3-skeleton{
  border-color:rgba(206, 217, 224, 0.2) !important;
  border-radius:2px;
  -webkit-box-shadow:none !important;
          box-shadow:none !important;
  background:rgba(206, 217, 224, 0.2);
  background-clip:padding-box !important;
  cursor:default;
  color:transparent !important;
  -webkit-animation:1000ms linear infinite alternate skeleton-glow;
          animation:1000ms linear infinite alternate skeleton-glow;
  pointer-events:none;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-skeleton::before, .bp3-skeleton::after,
  .bp3-skeleton *{
    visibility:hidden !important; }
.bp3-slider{
  width:100%;
  min-width:150px;
  height:40px;
  position:relative;
  outline:none;
  cursor:default;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-slider:hover{
    cursor:pointer; }
  .bp3-slider:active{
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-slider.bp3-disabled{
    opacity:0.5;
    cursor:not-allowed; }
  .bp3-slider.bp3-slider-unlabeled{
    height:16px; }

.bp3-slider-track,
.bp3-slider-progress{
  top:5px;
  right:0;
  left:0;
  height:6px;
  position:absolute; }

.bp3-slider-track{
  border-radius:3px;
  overflow:hidden; }

.bp3-slider-progress{
  background:rgba(92, 112, 128, 0.2); }
  .bp3-dark .bp3-slider-progress{
    background:rgba(16, 22, 26, 0.5); }
  .bp3-slider-progress.bp3-intent-primary{
    background-color:#137cbd; }
  .bp3-slider-progress.bp3-intent-success{
    background-color:#0f9960; }
  .bp3-slider-progress.bp3-intent-warning{
    background-color:#d9822b; }
  .bp3-slider-progress.bp3-intent-danger{
    background-color:#db3737; }

.bp3-slider-handle{
  -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
          box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
  background-color:#f5f8fa;
  background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.8)), to(rgba(255, 255, 255, 0)));
  background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0));
  color:#182026;
  position:absolute;
  top:0;
  left:0;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
  cursor:pointer;
  width:16px;
  height:16px; }
  .bp3-slider-handle:hover{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-clip:padding-box;
    background-color:#ebf1f5; }
  .bp3-slider-handle:active, .bp3-slider-handle.bp3-active{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#d8e1e8;
    background-image:none; }
  .bp3-slider-handle:disabled, .bp3-slider-handle.bp3-disabled{
    outline:none;
    -webkit-box-shadow:none;
            box-shadow:none;
    background-color:rgba(206, 217, 224, 0.5);
    background-image:none;
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6); }
    .bp3-slider-handle:disabled.bp3-active, .bp3-slider-handle:disabled.bp3-active:hover, .bp3-slider-handle.bp3-disabled.bp3-active, .bp3-slider-handle.bp3-disabled.bp3-active:hover{
      background:rgba(206, 217, 224, 0.7); }
  .bp3-slider-handle:focus{
    z-index:1; }
  .bp3-slider-handle:hover{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 -1px 0 rgba(16, 22, 26, 0.1);
    background-clip:padding-box;
    background-color:#ebf1f5;
    z-index:2;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 1px 1px rgba(16, 22, 26, 0.2);
    cursor:-webkit-grab;
    cursor:grab; }
  .bp3-slider-handle.bp3-active{
    -webkit-box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
            box-shadow:inset 0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 2px rgba(16, 22, 26, 0.2);
    background-color:#d8e1e8;
    background-image:none;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), inset 0 1px 1px rgba(16, 22, 26, 0.1);
    cursor:-webkit-grabbing;
    cursor:grabbing; }
  .bp3-disabled .bp3-slider-handle{
    -webkit-box-shadow:none;
            box-shadow:none;
    background:#bfccd6;
    pointer-events:none; }
  .bp3-dark .bp3-slider-handle{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
    background-color:#394b59;
    background-image:-webkit-gradient(linear, left top, left bottom, from(rgba(255, 255, 255, 0.05)), to(rgba(255, 255, 255, 0)));
    background-image:linear-gradient(to bottom, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0));
    color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover, .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle:hover{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.4);
      background-color:#30404d; }
    .bp3-dark .bp3-slider-handle:active, .bp3-dark .bp3-slider-handle.bp3-active{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.6), inset 0 1px 2px rgba(16, 22, 26, 0.2);
      background-color:#202b33;
      background-image:none; }
    .bp3-dark .bp3-slider-handle:disabled, .bp3-dark .bp3-slider-handle.bp3-disabled{
      -webkit-box-shadow:none;
              box-shadow:none;
      background-color:rgba(57, 75, 89, 0.5);
      background-image:none;
      color:rgba(167, 182, 194, 0.6); }
      .bp3-dark .bp3-slider-handle:disabled.bp3-active, .bp3-dark .bp3-slider-handle.bp3-disabled.bp3-active{
        background:rgba(57, 75, 89, 0.7); }
    .bp3-dark .bp3-slider-handle .bp3-button-spinner .bp3-spinner-head{
      background:rgba(16, 22, 26, 0.5);
      stroke:#8a9ba8; }
    .bp3-dark .bp3-slider-handle, .bp3-dark .bp3-slider-handle:hover{
      background-color:#394b59; }
    .bp3-dark .bp3-slider-handle.bp3-active{
      background-color:#293742; }
  .bp3-dark .bp3-disabled .bp3-slider-handle{
    border-color:#5c7080;
    -webkit-box-shadow:none;
            box-shadow:none;
    background:#5c7080; }
  .bp3-slider-handle .bp3-slider-label{
    margin-left:8px;
    border-radius:3px;
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
    background:#394b59;
    color:#f5f8fa; }
    .bp3-dark .bp3-slider-handle .bp3-slider-label{
      -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
      background:#e1e8ed;
      color:#394b59; }
    .bp3-disabled .bp3-slider-handle .bp3-slider-label{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-slider-handle.bp3-start, .bp3-slider-handle.bp3-end{
    width:8px; }
  .bp3-slider-handle.bp3-start{
    border-top-right-radius:0;
    border-bottom-right-radius:0; }
  .bp3-slider-handle.bp3-end{
    margin-left:8px;
    border-top-left-radius:0;
    border-bottom-left-radius:0; }
    .bp3-slider-handle.bp3-end .bp3-slider-label{
      margin-left:0; }

.bp3-slider-label{
  -webkit-transform:translate(-50%, 20px);
          transform:translate(-50%, 20px);
  display:inline-block;
  position:absolute;
  padding:2px 5px;
  vertical-align:top;
  line-height:1;
  font-size:12px; }

.bp3-slider.bp3-vertical{
  width:40px;
  min-width:40px;
  height:150px; }
  .bp3-slider.bp3-vertical .bp3-slider-track,
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    top:0;
    bottom:0;
    left:5px;
    width:6px;
    height:auto; }
  .bp3-slider.bp3-vertical .bp3-slider-progress{
    top:auto; }
  .bp3-slider.bp3-vertical .bp3-slider-label{
    -webkit-transform:translate(20px, 50%);
            transform:translate(20px, 50%); }
  .bp3-slider.bp3-vertical .bp3-slider-handle{
    top:auto; }
    .bp3-slider.bp3-vertical .bp3-slider-handle .bp3-slider-label{
      margin-top:-8px;
      margin-left:0; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end, .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      margin-left:0;
      width:16px;
      height:8px; }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start{
      border-top-left-radius:0;
      border-bottom-right-radius:3px; }
      .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-start .bp3-slider-label{
        -webkit-transform:translate(20px);
                transform:translate(20px); }
    .bp3-slider.bp3-vertical .bp3-slider-handle.bp3-end{
      margin-bottom:8px;
      border-top-left-radius:3px;
      border-bottom-left-radius:0;
      border-bottom-right-radius:0; }

@-webkit-keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

@keyframes pt-spinner-animation{
  from{
    -webkit-transform:rotate(0deg);
            transform:rotate(0deg); }
  to{
    -webkit-transform:rotate(360deg);
            transform:rotate(360deg); } }

.bp3-spinner{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  -webkit-box-pack:center;
      -ms-flex-pack:center;
          justify-content:center;
  overflow:visible;
  vertical-align:middle; }
  .bp3-spinner svg{
    display:block; }
  .bp3-spinner path{
    fill-opacity:0; }
  .bp3-spinner .bp3-spinner-head{
    -webkit-transform-origin:center;
            transform-origin:center;
    -webkit-transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    transition:stroke-dashoffset 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
    stroke:rgba(92, 112, 128, 0.8);
    stroke-linecap:round; }
  .bp3-spinner .bp3-spinner-track{
    stroke:rgba(92, 112, 128, 0.2); }

.bp3-spinner-animation{
  -webkit-animation:pt-spinner-animation 500ms linear infinite;
          animation:pt-spinner-animation 500ms linear infinite; }
  .bp3-no-spin > .bp3-spinner-animation{
    -webkit-animation:none;
            animation:none; }

.bp3-dark .bp3-spinner .bp3-spinner-head{
  stroke:#8a9ba8; }

.bp3-dark .bp3-spinner .bp3-spinner-track{
  stroke:rgba(16, 22, 26, 0.5); }

.bp3-spinner.bp3-intent-primary .bp3-spinner-head{
  stroke:#137cbd; }

.bp3-spinner.bp3-intent-success .bp3-spinner-head{
  stroke:#0f9960; }

.bp3-spinner.bp3-intent-warning .bp3-spinner-head{
  stroke:#d9822b; }

.bp3-spinner.bp3-intent-danger .bp3-spinner-head{
  stroke:#db3737; }
.bp3-tabs.bp3-vertical{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex; }
  .bp3-tabs.bp3-vertical > .bp3-tab-list{
    -webkit-box-orient:vertical;
    -webkit-box-direction:normal;
        -ms-flex-direction:column;
            flex-direction:column;
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start; }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab{
      border-radius:3px;
      width:100%;
      padding:0 10px; }
      .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab[aria-selected="true"]{
        -webkit-box-shadow:none;
                box-shadow:none;
        background-color:rgba(19, 124, 189, 0.2); }
    .bp3-tabs.bp3-vertical > .bp3-tab-list .bp3-tab-indicator-wrapper .bp3-tab-indicator{
      top:0;
      right:0;
      bottom:0;
      left:0;
      border-radius:3px;
      background-color:rgba(19, 124, 189, 0.2);
      height:auto; }
  .bp3-tabs.bp3-vertical > .bp3-tab-panel{
    margin-top:0;
    padding-left:20px; }

.bp3-tab-list{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  -webkit-box-align:end;
      -ms-flex-align:end;
          align-items:flex-end;
  position:relative;
  margin:0;
  border:none;
  padding:0;
  list-style:none; }
  .bp3-tab-list > *:not(:last-child){
    margin-right:20px; }

.bp3-tab{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  -webkit-box-flex:0;
      -ms-flex:0 0 auto;
          flex:0 0 auto;
  position:relative;
  cursor:pointer;
  max-width:100%;
  vertical-align:top;
  line-height:30px;
  color:#182026;
  font-size:14px; }
  .bp3-tab a{
    display:block;
    text-decoration:none;
    color:inherit; }
  .bp3-tab-indicator-wrapper ~ .bp3-tab{
    -webkit-box-shadow:none !important;
            box-shadow:none !important;
    background-color:transparent !important; }
  .bp3-tab[aria-disabled="true"]{
    cursor:not-allowed;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-tab[aria-selected="true"]{
    border-radius:0;
    -webkit-box-shadow:inset 0 -3px 0 #106ba3;
            box-shadow:inset 0 -3px 0 #106ba3; }
  .bp3-tab[aria-selected="true"], .bp3-tab:not([aria-disabled="true"]):hover{
    color:#106ba3; }
  .bp3-tab:focus{
    -moz-outline-radius:0; }
  .bp3-large > .bp3-tab{
    line-height:40px;
    font-size:16px; }

.bp3-tab-panel{
  margin-top:20px; }
  .bp3-tab-panel[aria-hidden="true"]{
    display:none; }

.bp3-tab-indicator-wrapper{
  position:absolute;
  top:0;
  left:0;
  -webkit-transform:translateX(0), translateY(0);
          transform:translateX(0), translateY(0);
  -webkit-transition:height, width, -webkit-transform;
  transition:height, width, -webkit-transform;
  transition:height, transform, width;
  transition:height, transform, width, -webkit-transform;
  -webkit-transition-duration:200ms;
          transition-duration:200ms;
  -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
          transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
  pointer-events:none; }
  .bp3-tab-indicator-wrapper .bp3-tab-indicator{
    position:absolute;
    right:0;
    bottom:0;
    left:0;
    background-color:#106ba3;
    height:3px; }
  .bp3-tab-indicator-wrapper.bp3-no-animation{
    -webkit-transition:none;
    transition:none; }

.bp3-dark .bp3-tab{
  color:#f5f8fa; }
  .bp3-dark .bp3-tab[aria-disabled="true"]{
    color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tab[aria-selected="true"]{
    -webkit-box-shadow:inset 0 -3px 0 #48aff0;
            box-shadow:inset 0 -3px 0 #48aff0; }
  .bp3-dark .bp3-tab[aria-selected="true"], .bp3-dark .bp3-tab:not([aria-disabled="true"]):hover{
    color:#48aff0; }

.bp3-dark .bp3-tab-indicator{
  background-color:#48aff0; }

.bp3-flex-expander{
  -webkit-box-flex:1;
      -ms-flex:1 1;
          flex:1 1; }
.bp3-tag{
  display:-webkit-inline-box;
  display:-ms-inline-flexbox;
  display:inline-flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  position:relative;
  border:none;
  border-radius:3px;
  -webkit-box-shadow:none;
          box-shadow:none;
  background-color:#5c7080;
  min-width:20px;
  max-width:100%;
  min-height:20px;
  padding:2px 6px;
  line-height:16px;
  color:#f5f8fa;
  font-size:12px; }
  .bp3-tag.bp3-interactive{
    cursor:pointer; }
    .bp3-tag.bp3-interactive:hover{
      background-color:rgba(92, 112, 128, 0.85); }
    .bp3-tag.bp3-interactive.bp3-active, .bp3-tag.bp3-interactive:active{
      background-color:rgba(92, 112, 128, 0.7); }
  .bp3-tag > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag > .bp3-fill{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag::before,
  .bp3-tag > *{
    margin-right:4px; }
  .bp3-tag:empty::before,
  .bp3-tag > :last-child{
    margin-right:0; }
  .bp3-tag:focus{
    outline:rgba(19, 124, 189, 0.6) auto 2px;
    outline-offset:0;
    -moz-outline-radius:6px; }
  .bp3-tag.bp3-round{
    border-radius:30px;
    padding-right:8px;
    padding-left:8px; }
  .bp3-dark .bp3-tag{
    background-color:#bfccd6;
    color:#182026; }
    .bp3-dark .bp3-tag.bp3-interactive{
      cursor:pointer; }
      .bp3-dark .bp3-tag.bp3-interactive:hover{
        background-color:rgba(191, 204, 214, 0.85); }
      .bp3-dark .bp3-tag.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-interactive:active{
        background-color:rgba(191, 204, 214, 0.7); }
    .bp3-dark .bp3-tag > .bp3-icon, .bp3-dark .bp3-tag .bp3-icon-standard, .bp3-dark .bp3-tag .bp3-icon-large{
      fill:currentColor; }
  .bp3-tag > .bp3-icon, .bp3-tag .bp3-icon-standard, .bp3-tag .bp3-icon-large{
    fill:#ffffff; }
  .bp3-tag.bp3-large,
  .bp3-large .bp3-tag{
    min-width:30px;
    min-height:30px;
    padding:0 10px;
    line-height:20px;
    font-size:14px; }
    .bp3-tag.bp3-large::before,
    .bp3-tag.bp3-large > *,
    .bp3-large .bp3-tag::before,
    .bp3-large .bp3-tag > *{
      margin-right:7px; }
    .bp3-tag.bp3-large:empty::before,
    .bp3-tag.bp3-large > :last-child,
    .bp3-large .bp3-tag:empty::before,
    .bp3-large .bp3-tag > :last-child{
      margin-right:0; }
    .bp3-tag.bp3-large.bp3-round,
    .bp3-large .bp3-tag.bp3-round{
      padding-right:12px;
      padding-left:12px; }
  .bp3-tag.bp3-intent-primary{
    background:#137cbd;
    color:#ffffff; }
    .bp3-tag.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.85); }
      .bp3-tag.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.7); }
  .bp3-tag.bp3-intent-success{
    background:#0f9960;
    color:#ffffff; }
    .bp3-tag.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.85); }
      .bp3-tag.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.7); }
  .bp3-tag.bp3-intent-warning{
    background:#d9822b;
    color:#ffffff; }
    .bp3-tag.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.85); }
      .bp3-tag.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.7); }
  .bp3-tag.bp3-intent-danger{
    background:#db3737;
    color:#ffffff; }
    .bp3-tag.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.85); }
      .bp3-tag.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.7); }
  .bp3-tag.bp3-fill{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    width:100%; }
  .bp3-tag.bp3-minimal > .bp3-icon, .bp3-tag.bp3-minimal .bp3-icon-standard, .bp3-tag.bp3-minimal .bp3-icon-large{
    fill:#5c7080; }
  .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
    background-color:rgba(138, 155, 168, 0.2);
    color:#182026; }
    .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
        background-color:rgba(92, 112, 128, 0.3); }
      .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
        background-color:rgba(92, 112, 128, 0.4); }
    .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]){
      color:#f5f8fa; }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:hover{
          background-color:rgba(191, 204, 214, 0.3); }
        .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]).bp3-interactive:active{
          background-color:rgba(191, 204, 214, 0.4); }
      .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) > .bp3-icon, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-standard, .bp3-dark .bp3-tag.bp3-minimal:not([class*="bp3-intent-"]) .bp3-icon-large{
        fill:#a7b6c2; }
  .bp3-tag.bp3-minimal.bp3-intent-primary{
    background-color:rgba(19, 124, 189, 0.15);
    color:#106ba3; }
    .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
        background-color:rgba(19, 124, 189, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
        background-color:rgba(19, 124, 189, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-primary > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-primary .bp3-icon-large{
      fill:#137cbd; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary{
      background-color:rgba(19, 124, 189, 0.25);
      color:#48aff0; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:hover{
          background-color:rgba(19, 124, 189, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-primary.bp3-interactive:active{
          background-color:rgba(19, 124, 189, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-success{
    background-color:rgba(15, 153, 96, 0.15);
    color:#0d8050; }
    .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
        background-color:rgba(15, 153, 96, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
        background-color:rgba(15, 153, 96, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-success > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-success .bp3-icon-large{
      fill:#0f9960; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success{
      background-color:rgba(15, 153, 96, 0.25);
      color:#3dcc91; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:hover{
          background-color:rgba(15, 153, 96, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-success.bp3-interactive:active{
          background-color:rgba(15, 153, 96, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-warning{
    background-color:rgba(217, 130, 43, 0.15);
    color:#bf7326; }
    .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
        background-color:rgba(217, 130, 43, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
        background-color:rgba(217, 130, 43, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-warning > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-warning .bp3-icon-large{
      fill:#d9822b; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning{
      background-color:rgba(217, 130, 43, 0.25);
      color:#ffb366; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:hover{
          background-color:rgba(217, 130, 43, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-warning.bp3-interactive:active{
          background-color:rgba(217, 130, 43, 0.45); }
  .bp3-tag.bp3-minimal.bp3-intent-danger{
    background-color:rgba(219, 55, 55, 0.15);
    color:#c23030; }
    .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
      cursor:pointer; }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
        background-color:rgba(219, 55, 55, 0.25); }
      .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
        background-color:rgba(219, 55, 55, 0.35); }
    .bp3-tag.bp3-minimal.bp3-intent-danger > .bp3-icon, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-standard, .bp3-tag.bp3-minimal.bp3-intent-danger .bp3-icon-large{
      fill:#db3737; }
    .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger{
      background-color:rgba(219, 55, 55, 0.25);
      color:#ff7373; }
      .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive{
        cursor:pointer; }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:hover{
          background-color:rgba(219, 55, 55, 0.35); }
        .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive.bp3-active, .bp3-dark .bp3-tag.bp3-minimal.bp3-intent-danger.bp3-interactive:active{
          background-color:rgba(219, 55, 55, 0.45); }

.bp3-tag-remove{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  opacity:0.5;
  margin-top:-2px;
  margin-right:-6px !important;
  margin-bottom:-2px;
  border:none;
  background:none;
  cursor:pointer;
  padding:2px;
  padding-left:0;
  color:inherit; }
  .bp3-tag-remove:hover{
    opacity:0.8;
    background:none;
    text-decoration:none; }
  .bp3-tag-remove:active{
    opacity:1; }
  .bp3-tag-remove:empty::before{
    line-height:1;
    font-family:"Icons16", sans-serif;
    font-size:16px;
    font-weight:400;
    font-style:normal;
    -moz-osx-font-smoothing:grayscale;
    -webkit-font-smoothing:antialiased;
    content:""; }
  .bp3-large .bp3-tag-remove{
    margin-right:-10px !important;
    padding:5px;
    padding-left:0; }
    .bp3-large .bp3-tag-remove:empty::before{
      line-height:1;
      font-family:"Icons20", sans-serif;
      font-size:20px;
      font-weight:400;
      font-style:normal; }
.bp3-tag-input{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-orient:horizontal;
  -webkit-box-direction:normal;
      -ms-flex-direction:row;
          flex-direction:row;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  cursor:text;
  height:auto;
  min-height:30px;
  padding-right:0;
  padding-left:5px;
  line-height:inherit; }
  .bp3-tag-input > *{
    -webkit-box-flex:0;
        -ms-flex-positive:0;
            flex-grow:0;
    -ms-flex-negative:0;
        flex-shrink:0; }
  .bp3-tag-input > .bp3-tag-input-values{
    -webkit-box-flex:1;
        -ms-flex-positive:1;
            flex-grow:1;
    -ms-flex-negative:1;
        flex-shrink:1; }
  .bp3-tag-input .bp3-tag-input-icon{
    margin-top:7px;
    margin-right:7px;
    margin-left:2px;
    color:#5c7080; }
  .bp3-tag-input .bp3-tag-input-values{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-orient:horizontal;
    -webkit-box-direction:normal;
        -ms-flex-direction:row;
            flex-direction:row;
    -ms-flex-wrap:wrap;
        flex-wrap:wrap;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center;
    -ms-flex-item-align:stretch;
        align-self:stretch;
    margin-top:5px;
    margin-right:7px;
    min-width:0; }
    .bp3-tag-input .bp3-tag-input-values > *{
      -webkit-box-flex:0;
          -ms-flex-positive:0;
              flex-grow:0;
      -ms-flex-negative:0;
          flex-shrink:0; }
    .bp3-tag-input .bp3-tag-input-values > .bp3-fill{
      -webkit-box-flex:1;
          -ms-flex-positive:1;
              flex-grow:1;
      -ms-flex-negative:1;
          flex-shrink:1; }
    .bp3-tag-input .bp3-tag-input-values::before,
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-right:5px; }
    .bp3-tag-input .bp3-tag-input-values:empty::before,
    .bp3-tag-input .bp3-tag-input-values > :last-child{
      margin-right:0; }
    .bp3-tag-input .bp3-tag-input-values:first-child .bp3-input-ghost:first-child{
      padding-left:5px; }
    .bp3-tag-input .bp3-tag-input-values > *{
      margin-bottom:5px; }
  .bp3-tag-input .bp3-tag{
    overflow-wrap:break-word; }
    .bp3-tag-input .bp3-tag.bp3-active{
      outline:rgba(19, 124, 189, 0.6) auto 2px;
      outline-offset:0;
      -moz-outline-radius:6px; }
  .bp3-tag-input .bp3-input-ghost{
    -webkit-box-flex:1;
        -ms-flex:1 1 auto;
            flex:1 1 auto;
    width:80px;
    line-height:20px; }
    .bp3-tag-input .bp3-input-ghost:disabled, .bp3-tag-input .bp3-input-ghost.bp3-disabled{
      cursor:not-allowed; }
  .bp3-tag-input .bp3-button,
  .bp3-tag-input .bp3-spinner{
    margin:3px;
    margin-left:0; }
  .bp3-tag-input .bp3-button{
    min-width:24px;
    min-height:24px;
    padding:0 7px; }
  .bp3-tag-input.bp3-large{
    height:auto;
    min-height:40px; }
    .bp3-tag-input.bp3-large::before,
    .bp3-tag-input.bp3-large > *{
      margin-right:10px; }
    .bp3-tag-input.bp3-large:empty::before,
    .bp3-tag-input.bp3-large > :last-child{
      margin-right:0; }
    .bp3-tag-input.bp3-large .bp3-tag-input-icon{
      margin-top:10px;
      margin-left:5px; }
    .bp3-tag-input.bp3-large .bp3-input-ghost{
      line-height:30px; }
    .bp3-tag-input.bp3-large .bp3-button{
      min-width:30px;
      min-height:30px;
      padding:5px 10px;
      margin:5px;
      margin-left:0; }
    .bp3-tag-input.bp3-large .bp3-spinner{
      margin:8px;
      margin-left:0; }
  .bp3-tag-input.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
    background-color:#ffffff; }
    .bp3-tag-input.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
    .bp3-tag-input.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.2); }
  .bp3-dark .bp3-tag-input .bp3-tag-input-icon, .bp3-tag-input.bp3-dark .bp3-tag-input-icon{
    color:#a7b6c2; }
  .bp3-dark .bp3-tag-input .bp3-input-ghost, .bp3-tag-input.bp3-dark .bp3-input-ghost{
    color:#f5f8fa; }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-webkit-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-webkit-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-moz-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-moz-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost:-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost:-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::-ms-input-placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::-ms-input-placeholder{
      color:rgba(167, 182, 194, 0.6); }
    .bp3-dark .bp3-tag-input .bp3-input-ghost::placeholder, .bp3-tag-input.bp3-dark .bp3-input-ghost::placeholder{
      color:rgba(167, 182, 194, 0.6); }
  .bp3-dark .bp3-tag-input.bp3-active, .bp3-tag-input.bp3-dark.bp3-active{
    -webkit-box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px #137cbd, 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
    background-color:rgba(16, 22, 26, 0.3); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-primary, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-primary{
      -webkit-box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #106ba3, 0 0 0 3px rgba(16, 107, 163, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-success, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-success{
      -webkit-box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #0d8050, 0 0 0 3px rgba(13, 128, 80, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-warning, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-warning{
      -webkit-box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #bf7326, 0 0 0 3px rgba(191, 115, 38, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }
    .bp3-dark .bp3-tag-input.bp3-active.bp3-intent-danger, .bp3-tag-input.bp3-dark.bp3-active.bp3-intent-danger{
      -webkit-box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4);
              box-shadow:0 0 0 1px #c23030, 0 0 0 3px rgba(194, 48, 48, 0.3), inset 0 0 0 1px rgba(16, 22, 26, 0.3), inset 0 1px 1px rgba(16, 22, 26, 0.4); }

.bp3-input-ghost{
  border:none;
  -webkit-box-shadow:none;
          box-shadow:none;
  background:none;
  padding:0; }
  .bp3-input-ghost::-webkit-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input-ghost::-moz-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input-ghost:-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input-ghost::-ms-input-placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input-ghost::placeholder{
    opacity:1;
    color:rgba(92, 112, 128, 0.6); }
  .bp3-input-ghost:focus{
    outline:none !important; }
.bp3-toast{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-align:start;
      -ms-flex-align:start;
          align-items:flex-start;
  position:relative !important;
  margin:20px 0 0;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  background-color:#ffffff;
  min-width:300px;
  max-width:500px;
  pointer-events:all; }
  .bp3-toast.bp3-toast-enter, .bp3-toast.bp3-toast-appear{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active, .bp3-toast.bp3-toast-appear-active{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-toast.bp3-toast-enter ~ .bp3-toast, .bp3-toast.bp3-toast-appear ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px); }
  .bp3-toast.bp3-toast-enter-active ~ .bp3-toast, .bp3-toast.bp3-toast-appear-active ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
            transition-timing-function:cubic-bezier(0.54, 1.12, 0.38, 1.11);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-toast.bp3-toast-exit{
    opacity:1;
    -webkit-filter:blur(0);
            filter:blur(0); }
  .bp3-toast.bp3-toast-exit-active{
    opacity:0;
    -webkit-filter:blur(10px);
            filter:blur(10px);
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:opacity, filter;
    transition-property:opacity, filter, -webkit-filter;
    -webkit-transition-duration:300ms;
            transition-duration:300ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-toast.bp3-toast-exit ~ .bp3-toast{
    -webkit-transform:translateY(0);
            transform:translateY(0); }
  .bp3-toast.bp3-toast-exit-active ~ .bp3-toast{
    -webkit-transform:translateY(-40px);
            transform:translateY(-40px);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:50ms;
            transition-delay:50ms; }
  .bp3-toast .bp3-button-group{
    -webkit-box-flex:0;
        -ms-flex:0 0 auto;
            flex:0 0 auto;
    padding:5px;
    padding-left:0; }
  .bp3-toast > .bp3-icon{
    margin:12px;
    margin-right:0;
    color:#5c7080; }
  .bp3-toast.bp3-dark,
  .bp3-dark .bp3-toast{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
    background-color:#394b59; }
    .bp3-toast.bp3-dark > .bp3-icon,
    .bp3-dark .bp3-toast > .bp3-icon{
      color:#a7b6c2; }
  .bp3-toast[class*="bp3-intent-"] a{
    color:rgba(255, 255, 255, 0.7); }
    .bp3-toast[class*="bp3-intent-"] a:hover{
      color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] > .bp3-icon{
    color:#ffffff; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button, .bp3-toast[class*="bp3-intent-"] .bp3-button::before,
  .bp3-toast[class*="bp3-intent-"] .bp3-button .bp3-icon, .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    color:rgba(255, 255, 255, 0.7) !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:focus{
    outline-color:rgba(255, 255, 255, 0.5); }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:hover{
    background-color:rgba(255, 255, 255, 0.15) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button:active{
    background-color:rgba(255, 255, 255, 0.3) !important;
    color:#ffffff !important; }
  .bp3-toast[class*="bp3-intent-"] .bp3-button::after{
    background:rgba(255, 255, 255, 0.3) !important; }
  .bp3-toast.bp3-intent-primary{
    background-color:#137cbd;
    color:#ffffff; }
  .bp3-toast.bp3-intent-success{
    background-color:#0f9960;
    color:#ffffff; }
  .bp3-toast.bp3-intent-warning{
    background-color:#d9822b;
    color:#ffffff; }
  .bp3-toast.bp3-intent-danger{
    background-color:#db3737;
    color:#ffffff; }

.bp3-toast-message{
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  padding:11px;
  word-break:break-word; }

.bp3-toast-container{
  display:-webkit-box !important;
  display:-ms-flexbox !important;
  display:flex !important;
  -webkit-box-orient:vertical;
  -webkit-box-direction:normal;
      -ms-flex-direction:column;
          flex-direction:column;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  position:fixed;
  right:0;
  left:0;
  z-index:40;
  overflow:hidden;
  padding:0 20px 20px;
  pointer-events:none; }
  .bp3-toast-container.bp3-toast-container-top{
    top:0;
    bottom:auto; }
  .bp3-toast-container.bp3-toast-container-bottom{
    -webkit-box-orient:vertical;
    -webkit-box-direction:reverse;
        -ms-flex-direction:column-reverse;
            flex-direction:column-reverse;
    top:auto;
    bottom:0; }
  .bp3-toast-container.bp3-toast-container-left{
    -webkit-box-align:start;
        -ms-flex-align:start;
            align-items:flex-start; }
  .bp3-toast-container.bp3-toast-container-right{
    -webkit-box-align:end;
        -ms-flex-align:end;
            align-items:flex-end; }

.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-enter:not(.bp3-toast-enter-active) ~ .bp3-toast, .bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active),
.bp3-toast-container-bottom .bp3-toast.bp3-toast-appear:not(.bp3-toast-appear-active) ~ .bp3-toast,
.bp3-toast-container-bottom .bp3-toast.bp3-toast-leave-active ~ .bp3-toast{
  -webkit-transform:translateY(60px);
          transform:translateY(60px); }
.bp3-tooltip{
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 2px 4px rgba(16, 22, 26, 0.2), 0 8px 24px rgba(16, 22, 26, 0.2);
  -webkit-transform:scale(1);
          transform:scale(1); }
  .bp3-tooltip .bp3-popover-arrow{
    position:absolute;
    width:22px;
    height:22px; }
    .bp3-tooltip .bp3-popover-arrow::before{
      margin:4px;
      width:14px;
      height:14px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip{
    margin-top:-11px;
    margin-bottom:11px; }
    .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
      bottom:-8px; }
      .bp3-tether-element-attached-bottom.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(-90deg);
                transform:rotate(-90deg); }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip{
    margin-left:11px; }
    .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
      left:-8px; }
      .bp3-tether-element-attached-left.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(0);
                transform:rotate(0); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip{
    margin-top:11px; }
    .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
      top:-8px; }
      .bp3-tether-element-attached-top.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(90deg);
                transform:rotate(90deg); }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip{
    margin-right:11px;
    margin-left:-11px; }
    .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
      right:-8px; }
      .bp3-tether-element-attached-right.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow svg{
        -webkit-transform:rotate(180deg);
                transform:rotate(180deg); }
  .bp3-tether-element-attached-middle > .bp3-tooltip > .bp3-popover-arrow{
    top:50%;
    -webkit-transform:translateY(-50%);
            transform:translateY(-50%); }
  .bp3-tether-element-attached-center > .bp3-tooltip > .bp3-popover-arrow{
    right:50%;
    -webkit-transform:translateX(50%);
            transform:translateX(50%); }
  .bp3-tether-element-attached-top.bp3-tether-target-attached-top > .bp3-tooltip > .bp3-popover-arrow{
    top:-0.22183px; }
  .bp3-tether-element-attached-right.bp3-tether-target-attached-right > .bp3-tooltip > .bp3-popover-arrow{
    right:-0.22183px; }
  .bp3-tether-element-attached-left.bp3-tether-target-attached-left > .bp3-tooltip > .bp3-popover-arrow{
    left:-0.22183px; }
  .bp3-tether-element-attached-bottom.bp3-tether-target-attached-bottom > .bp3-tooltip > .bp3-popover-arrow{
    bottom:-0.22183px; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:top left;
            transform-origin:top left; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:top center;
            transform-origin:top center; }
  .bp3-tether-element-attached-top.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:top right;
            transform-origin:top right; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:center left;
            transform-origin:center left; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:center center;
            transform-origin:center center; }
  .bp3-tether-element-attached-middle.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:center right;
            transform-origin:center right; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-left > .bp3-tooltip{
    -webkit-transform-origin:bottom left;
            transform-origin:bottom left; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-center > .bp3-tooltip{
    -webkit-transform-origin:bottom center;
            transform-origin:bottom center; }
  .bp3-tether-element-attached-bottom.bp3-tether-element-attached-right > .bp3-tooltip{
    -webkit-transform-origin:bottom right;
            transform-origin:bottom right; }
  .bp3-tooltip .bp3-popover-content{
    background:#394b59;
    color:#f5f8fa; }
  .bp3-tooltip .bp3-popover-arrow::before{
    -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2);
            box-shadow:1px 1px 6px rgba(16, 22, 26, 0.2); }
  .bp3-tooltip .bp3-popover-arrow-border{
    fill:#10161a;
    fill-opacity:0.1; }
  .bp3-tooltip .bp3-popover-arrow-fill{
    fill:#394b59; }
  .bp3-popover-enter > .bp3-tooltip, .bp3-popover-appear > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8); }
  .bp3-popover-enter-active > .bp3-tooltip, .bp3-popover-appear-active > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-popover-exit > .bp3-tooltip{
    -webkit-transform:scale(1);
            transform:scale(1); }
  .bp3-popover-exit-active > .bp3-tooltip{
    -webkit-transform:scale(0.8);
            transform:scale(0.8);
    -webkit-transition-property:-webkit-transform;
    transition-property:-webkit-transform;
    transition-property:transform;
    transition-property:transform, -webkit-transform;
    -webkit-transition-duration:100ms;
            transition-duration:100ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-tooltip .bp3-popover-content{
    padding:10px 12px; }
  .bp3-tooltip.bp3-dark,
  .bp3-dark .bp3-tooltip{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 2px 4px rgba(16, 22, 26, 0.4), 0 8px 24px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-content,
    .bp3-dark .bp3-tooltip .bp3-popover-content{
      background:#e1e8ed;
      color:#394b59; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow::before,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow::before{
      -webkit-box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4);
              box-shadow:1px 1px 6px rgba(16, 22, 26, 0.4); }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-border,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-border{
      fill:#10161a;
      fill-opacity:0.2; }
    .bp3-tooltip.bp3-dark .bp3-popover-arrow-fill,
    .bp3-dark .bp3-tooltip .bp3-popover-arrow-fill{
      fill:#e1e8ed; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-content{
    background:#137cbd;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-primary .bp3-popover-arrow-fill{
    fill:#137cbd; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-content{
    background:#0f9960;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-success .bp3-popover-arrow-fill{
    fill:#0f9960; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-content{
    background:#d9822b;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-warning .bp3-popover-arrow-fill{
    fill:#d9822b; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-content{
    background:#db3737;
    color:#ffffff; }
  .bp3-tooltip.bp3-intent-danger .bp3-popover-arrow-fill{
    fill:#db3737; }

.bp3-tooltip-indicator{
  border-bottom:dotted 1px;
  cursor:help; }
.bp3-tree .bp3-icon, .bp3-tree .bp3-icon-standard, .bp3-tree .bp3-icon-large{
  color:#5c7080; }
  .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-tree .bp3-icon.bp3-intent-success, .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-tree-node-list{
  margin:0;
  padding-left:0;
  list-style:none; }

.bp3-tree-root{
  position:relative;
  background-color:transparent;
  cursor:default;
  padding-left:0; }

.bp3-tree-node-content-0{
  padding-left:0px; }

.bp3-tree-node-content-1{
  padding-left:23px; }

.bp3-tree-node-content-2{
  padding-left:46px; }

.bp3-tree-node-content-3{
  padding-left:69px; }

.bp3-tree-node-content-4{
  padding-left:92px; }

.bp3-tree-node-content-5{
  padding-left:115px; }

.bp3-tree-node-content-6{
  padding-left:138px; }

.bp3-tree-node-content-7{
  padding-left:161px; }

.bp3-tree-node-content-8{
  padding-left:184px; }

.bp3-tree-node-content-9{
  padding-left:207px; }

.bp3-tree-node-content-10{
  padding-left:230px; }

.bp3-tree-node-content-11{
  padding-left:253px; }

.bp3-tree-node-content-12{
  padding-left:276px; }

.bp3-tree-node-content-13{
  padding-left:299px; }

.bp3-tree-node-content-14{
  padding-left:322px; }

.bp3-tree-node-content-15{
  padding-left:345px; }

.bp3-tree-node-content-16{
  padding-left:368px; }

.bp3-tree-node-content-17{
  padding-left:391px; }

.bp3-tree-node-content-18{
  padding-left:414px; }

.bp3-tree-node-content-19{
  padding-left:437px; }

.bp3-tree-node-content-20{
  padding-left:460px; }

.bp3-tree-node-content{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  -webkit-box-align:center;
      -ms-flex-align:center;
          align-items:center;
  width:100%;
  height:30px;
  padding-right:5px; }
  .bp3-tree-node-content:hover{
    background-color:rgba(191, 204, 214, 0.4); }

.bp3-tree-node-caret,
.bp3-tree-node-caret-none{
  min-width:30px; }

.bp3-tree-node-caret{
  color:#5c7080;
  -webkit-transform:rotate(0deg);
          transform:rotate(0deg);
  cursor:pointer;
  padding:7px;
  -webkit-transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:-webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9);
  transition:transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9), -webkit-transform 200ms cubic-bezier(0.4, 1, 0.75, 0.9); }
  .bp3-tree-node-caret:hover{
    color:#182026; }
  .bp3-dark .bp3-tree-node-caret{
    color:#a7b6c2; }
    .bp3-dark .bp3-tree-node-caret:hover{
      color:#f5f8fa; }
  .bp3-tree-node-caret.bp3-tree-node-caret-open{
    -webkit-transform:rotate(90deg);
            transform:rotate(90deg); }
  .bp3-tree-node-caret.bp3-icon-standard::before{
    content:""; }

.bp3-tree-node-icon{
  position:relative;
  margin-right:7px; }

.bp3-tree-node-label{
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
  word-wrap:normal;
  -webkit-box-flex:1;
      -ms-flex:1 1 auto;
          flex:1 1 auto;
  position:relative;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-label span{
    display:inline; }

.bp3-tree-node-secondary-label{
  padding:0 5px;
  -webkit-user-select:none;
     -moz-user-select:none;
      -ms-user-select:none;
          user-select:none; }
  .bp3-tree-node-secondary-label .bp3-popover-wrapper,
  .bp3-tree-node-secondary-label .bp3-popover-target{
    display:-webkit-box;
    display:-ms-flexbox;
    display:flex;
    -webkit-box-align:center;
        -ms-flex-align:center;
            align-items:center; }

.bp3-tree-node.bp3-disabled .bp3-tree-node-content{
  background-color:inherit;
  cursor:not-allowed;
  color:rgba(92, 112, 128, 0.6); }

.bp3-tree-node.bp3-disabled .bp3-tree-node-caret,
.bp3-tree-node.bp3-disabled .bp3-tree-node-icon{
  cursor:not-allowed;
  color:rgba(92, 112, 128, 0.6); }

.bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content,
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-standard, .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-icon-large{
    color:#ffffff; }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret::before{
    color:rgba(255, 255, 255, 0.7); }
  .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content .bp3-tree-node-caret:hover::before{
    color:#ffffff; }

.bp3-dark .bp3-tree-node-content:hover{
  background-color:rgba(92, 112, 128, 0.3); }

.bp3-dark .bp3-tree .bp3-icon, .bp3-dark .bp3-tree .bp3-icon-standard, .bp3-dark .bp3-tree .bp3-icon-large{
  color:#a7b6c2; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-primary, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-primary{
    color:#137cbd; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-success, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-success{
    color:#0f9960; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-warning, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-warning{
    color:#d9822b; }
  .bp3-dark .bp3-tree .bp3-icon.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-standard.bp3-intent-danger, .bp3-dark .bp3-tree .bp3-icon-large.bp3-intent-danger{
    color:#db3737; }

.bp3-dark .bp3-tree-node.bp3-tree-node-selected > .bp3-tree-node-content{
  background-color:#137cbd; }
/*!

Copyright 2017-present Palantir Technologies, Inc. All rights reserved.
Licensed under the Apache License, Version 2.0.

*/
.bp3-omnibar{
  -webkit-filter:blur(0);
          filter:blur(0);
  opacity:1;
  top:20vh;
  left:calc(50% - 250px);
  z-index:21;
  border-radius:3px;
  -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
          box-shadow:0 0 0 1px rgba(16, 22, 26, 0.1), 0 4px 8px rgba(16, 22, 26, 0.2), 0 18px 46px 6px rgba(16, 22, 26, 0.2);
  background-color:#ffffff;
  width:500px; }
  .bp3-omnibar.bp3-overlay-enter, .bp3-omnibar.bp3-overlay-appear{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2; }
  .bp3-omnibar.bp3-overlay-enter-active, .bp3-omnibar.bp3-overlay-appear-active{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-omnibar.bp3-overlay-exit{
    -webkit-filter:blur(0);
            filter:blur(0);
    opacity:1; }
  .bp3-omnibar.bp3-overlay-exit-active{
    -webkit-filter:blur(20px);
            filter:blur(20px);
    opacity:0.2;
    -webkit-transition-property:opacity, -webkit-filter;
    transition-property:opacity, -webkit-filter;
    transition-property:filter, opacity;
    transition-property:filter, opacity, -webkit-filter;
    -webkit-transition-duration:200ms;
            transition-duration:200ms;
    -webkit-transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
            transition-timing-function:cubic-bezier(0.4, 1, 0.75, 0.9);
    -webkit-transition-delay:0;
            transition-delay:0; }
  .bp3-omnibar .bp3-input{
    border-radius:0;
    background-color:transparent; }
    .bp3-omnibar .bp3-input, .bp3-omnibar .bp3-input:focus{
      -webkit-box-shadow:none;
              box-shadow:none; }
  .bp3-omnibar .bp3-menu{
    border-radius:0;
    -webkit-box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
            box-shadow:inset 0 1px 0 rgba(16, 22, 26, 0.15);
    background-color:transparent;
    max-height:calc(60vh - 40px);
    overflow:auto; }
    .bp3-omnibar .bp3-menu:empty{
      display:none; }
  .bp3-dark .bp3-omnibar, .bp3-omnibar.bp3-dark{
    -webkit-box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
            box-shadow:0 0 0 1px rgba(16, 22, 26, 0.2), 0 4px 8px rgba(16, 22, 26, 0.4), 0 18px 46px 6px rgba(16, 22, 26, 0.4);
    background-color:#30404d; }

.bp3-omnibar-overlay .bp3-overlay-backdrop{
  background-color:rgba(16, 22, 26, 0.2); }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-width:400px;
  max-height:300px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }

.bp3-multi-select{
  min-width:150px; }

.bp3-multi-select-popover .bp3-menu{
  max-width:400px;
  max-height:300px;
  overflow:auto; }

.bp3-select-popover .bp3-popover-content{
  padding:5px; }

.bp3-select-popover .bp3-input-group{
  margin-bottom:0; }

.bp3-select-popover .bp3-menu{
  max-width:400px;
  max-height:300px;
  overflow:auto;
  padding:0; }
  .bp3-select-popover .bp3-menu:not(:first-child){
    padding-top:5px; }
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

/* Icons urls */

:root {
  --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDhoLTIuODFjLS40NS0uNzgtMS4wNy0xLjQ1LTEuODItMS45NkwxNyA0LjQxIDE1LjU5IDNsLTIuMTcgMi4xN0MxMi45NiA1LjA2IDEyLjQ5IDUgMTIgNWMtLjQ5IDAtLjk2LjA2LTEuNDEuMTdMOC40MSAzIDcgNC40MWwxLjYyIDEuNjNDNy44OCA2LjU1IDcuMjYgNy4yMiA2LjgxIDhINHYyaDIuMDljLS4wNS4zMy0uMDkuNjYtLjA5IDF2MUg0djJoMnYxYzAgLjM0LjA0LjY3LjA5IDFINHYyaDIuODFjMS4wNCAxLjc5IDIuOTcgMyA1LjE5IDNzNC4xNS0xLjIxIDUuMTktM0gyMHYtMmgtMi4wOWMuMDUtLjMzLjA5LS42Ni4wOS0xdi0xaDJ2LTJoLTJ2LTFjMC0uMzQtLjA0LS42Ny0uMDktMUgyMFY4em0tNiA4aC00di0yaDR2MnptMC00aC00di0yaDR2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
  --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTYuMTdMNC44MyAxMmwtMS40MiAxLjQxTDkgMTkgMjEgN2wtMS40MS0xLjQxeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1pY29uLWJyYW5kMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNmZmYiPgogICAgPHBhdGggZD0iTTEwNSAxMjcuM2g0MHYxMi44aC00MHpNNTEuMSA3N0w3NCA5OS45bC0yMy4zIDIzLjMgMTAuNSAxMC41IDIzLjMtMjMuM0w5NSA5OS45IDg0LjUgODkuNCA2MS42IDY2LjV6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
  --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
  --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMSBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNGOUE4MjUiPgogICAgPHBhdGggZD0iTTIwLjIgMTEuOGMtMS42IDAtMS43LjUtMS43IDEgMCAuNC4xLjkuMSAxLjMuMS41LjEuOS4xIDEuMyAwIDEuNy0xLjQgMi4zLTMuNSAyLjNoLS45di0xLjloLjVjMS4xIDAgMS40IDAgMS40LS44IDAtLjMgMC0uNi0uMS0xIDAtLjQtLjEtLjgtLjEtMS4yIDAtMS4zIDAtMS44IDEuMy0yLTEuMy0uMi0xLjMtLjctMS4zLTIgMC0uNC4xLS44LjEtMS4yLjEtLjQuMS0uNy4xLTEgMC0uOC0uNC0uNy0xLjQtLjhoLS41VjQuMWguOWMyLjIgMCAzLjUuNyAzLjUgMi4zIDAgLjQtLjEuOS0uMSAxLjMtLjEuNS0uMS45LS4xIDEuMyAwIC41LjIgMSAxLjcgMXYxLjh6TTEuOCAxMC4xYzEuNiAwIDEuNy0uNSAxLjctMSAwLS40LS4xLS45LS4xLTEuMy0uMS0uNS0uMS0uOS0uMS0xLjMgMC0xLjYgMS40LTIuMyAzLjUtMi4zaC45djEuOWgtLjVjLTEgMC0xLjQgMC0xLjQuOCAwIC4zIDAgLjYuMSAxIDAgLjIuMS42LjEgMSAwIDEuMyAwIDEuOC0xLjMgMkM2IDExLjIgNiAxMS43IDYgMTNjMCAuNC0uMS44LS4xIDEuMi0uMS4zLS4xLjctLjEgMSAwIC44LjMuOCAxLjQuOGguNXYxLjloLS45Yy0yLjEgMC0zLjUtLjYtMy41LTIuMyAwLS40LjEtLjkuMS0xLjMuMS0uNS4xLS45LjEtMS4zIDAtLjUtLjItMS0xLjctMXYtMS45eiIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSIxMy44IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY3g9IjExIiBjeT0iOC4yIiByPSIyLjEiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgPGcgY2xhc3M9ImpwLWljb24td2FybjAiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
  --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
  --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
  --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
  --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4=);
  --jp-icon-listings-info: url(data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pg0KPHN2ZyB2ZXJzaW9uPSIxLjEiIGlkPSJDYXBhXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4Ig0KCSB2aWV3Qm94PSIwIDAgNTAuOTc4IDUwLjk3OCIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgNTAuOTc4IDUwLjk3ODsiIHhtbDpzcGFjZT0icHJlc2VydmUiPg0KPGc+DQoJPGc+DQoJCTxnPg0KCQkJPHBhdGggc3R5bGU9ImZpbGw6IzAxMDAwMjsiIGQ9Ik00My41Miw3LjQ1OEMzOC43MTEsMi42NDgsMzIuMzA3LDAsMjUuNDg5LDBDMTguNjcsMCwxMi4yNjYsMi42NDgsNy40NTgsNy40NTgNCgkJCQljLTkuOTQzLDkuOTQxLTkuOTQzLDI2LjExOSwwLDM2LjA2MmM0LjgwOSw0LjgwOSwxMS4yMTIsNy40NTYsMTguMDMxLDcuNDU4YzAsMCwwLjAwMSwwLDAuMDAyLDANCgkJCQljNi44MTYsMCwxMy4yMjEtMi42NDgsMTguMDI5LTcuNDU4YzQuODA5LTQuODA5LDcuNDU3LTExLjIxMiw3LjQ1Ny0xOC4wM0M1MC45NzcsMTguNjcsNDguMzI4LDEyLjI2Niw0My41Miw3LjQ1OHoNCgkJCQkgTTQyLjEwNiw0Mi4xMDVjLTQuNDMyLDQuNDMxLTEwLjMzMiw2Ljg3Mi0xNi42MTUsNi44NzJoLTAuMDAyYy02LjI4NS0wLjAwMS0xMi4xODctMi40NDEtMTYuNjE3LTYuODcyDQoJCQkJYy05LjE2Mi05LjE2My05LjE2Mi0yNC4wNzEsMC0zMy4yMzNDMTMuMzAzLDQuNDQsMTkuMjA0LDIsMjUuNDg5LDJjNi4yODQsMCwxMi4xODYsMi40NCwxNi42MTcsNi44NzINCgkJCQljNC40MzEsNC40MzEsNi44NzEsMTAuMzMyLDYuODcxLDE2LjYxN0M0OC45NzcsMzEuNzcyLDQ2LjUzNiwzNy42NzUsNDIuMTA2LDQyLjEwNXoiLz4NCgkJPC9nPg0KCQk8Zz4NCgkJCTxwYXRoIHN0eWxlPSJmaWxsOiMwMTAwMDI7IiBkPSJNMjMuNTc4LDMyLjIxOGMtMC4wMjMtMS43MzQsMC4xNDMtMy4wNTksMC40OTYtMy45NzJjMC4zNTMtMC45MTMsMS4xMS0xLjk5NywyLjI3Mi0zLjI1Mw0KCQkJCWMwLjQ2OC0wLjUzNiwwLjkyMy0xLjA2MiwxLjM2Ny0xLjU3NWMwLjYyNi0wLjc1MywxLjEwNC0xLjQ3OCwxLjQzNi0yLjE3NWMwLjMzMS0wLjcwNywwLjQ5NS0xLjU0MSwwLjQ5NS0yLjUNCgkJCQljMC0xLjA5Ni0wLjI2LTIuMDg4LTAuNzc5LTIuOTc5Yy0wLjU2NS0wLjg3OS0xLjUwMS0xLjMzNi0yLjgwNi0xLjM2OWMtMS44MDIsMC4wNTctMi45ODUsMC42NjctMy41NSwxLjgzMg0KCQkJCWMtMC4zMDEsMC41MzUtMC41MDMsMS4xNDEtMC42MDcsMS44MTRjLTAuMTM5LDAuNzA3LTAuMjA3LDEuNDMyLTAuMjA3LDIuMTc0aC0yLjkzN2MtMC4wOTEtMi4yMDgsMC40MDctNC4xMTQsMS40OTMtNS43MTkNCgkJCQljMS4wNjItMS42NCwyLjg1NS0yLjQ4MSw1LjM3OC0yLjUyN2MyLjE2LDAuMDIzLDMuODc0LDAuNjA4LDUuMTQxLDEuNzU4YzEuMjc4LDEuMTYsMS45MjksMi43NjQsMS45NSw0LjgxMQ0KCQkJCWMwLDEuMTQyLTAuMTM3LDIuMTExLTAuNDEsMi45MTFjLTAuMzA5LDAuODQ1LTAuNzMxLDEuNTkzLTEuMjY4LDIuMjQzYy0wLjQ5MiwwLjY1LTEuMDY4LDEuMzE4LTEuNzMsMi4wMDINCgkJCQljLTAuNjUsMC42OTctMS4zMTMsMS40NzktMS45ODcsMi4zNDZjLTAuMjM5LDAuMzc3LTAuNDI5LDAuNzc3LTAuNTY1LDEuMTk5Yy0wLjE2LDAuOTU5LTAuMjE3LDEuOTUxLTAuMTcxLDIuOTc5DQoJCQkJQzI2LjU4OSwzMi4yMTgsMjMuNTc4LDMyLjIxOCwyMy41NzgsMzIuMjE4eiBNMjMuNTc4LDM4LjIydi0zLjQ4NGgzLjA3NnYzLjQ4NEgyMy41Nzh6Ii8+DQoJCTwvZz4NCgk8L2c+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8Zz4NCjwvZz4NCjxnPg0KPC9nPg0KPGc+DQo8L2c+DQo8L3N2Zz4NCg==);
  --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
  --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
  --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMEQ0N0ExIj4KICAgIDxwYXRoIGQ9Ik0xMS4xIDYuOVY1LjhINi45YzAtLjUgMC0xLjMuMi0xLjYuNC0uNy44LTEuMSAxLjctMS40IDEuNy0uMyAyLjUtLjMgMy45LS4xIDEgLjEgMS45LjkgMS45IDEuOXY0LjJjMCAuNS0uOSAxLjYtMiAxLjZIOC44Yy0xLjUgMC0yLjQgMS40LTIuNCAyLjh2Mi4ySDQuN0MzLjUgMTUuMSAzIDE0IDMgMTMuMVY5Yy0uMS0xIC42LTIgMS44LTIgMS41LS4xIDYuMy0uMSA2LjMtLjF6Ii8+CiAgICA8cGF0aCBkPSJNMTAuOSAxNS4xdjEuMWg0LjJjMCAuNSAwIDEuMy0uMiAxLjYtLjQuNy0uOCAxLjEtMS43IDEuNC0xLjcuMy0yLjUuMy0zLjkuMS0xLS4xLTEuOS0uOS0xLjktMS45di00LjJjMC0uNS45LTEuNiAyLTEuNmgzLjhjMS41IDAgMi40LTEuNCAyLjQtMi44VjYuNmgxLjdDMTguNSA2LjkgMTkgOCAxOSA4LjlWMTNjMCAxLS43IDIuMS0xLjkgMi4xaC02LjJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
  --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
  --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
  --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
  --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
  --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMikiIGZpbGw9IiMzMzMzMzMiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uLWFjY2VudDIganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGQ9Ik01LjA1NjY0IDguNzYxNzJDNS4wNTY2NCA4LjU5NzY2IDUuMDMxMjUgOC40NTMxMiA0Ljk4MDQ3IDguMzI4MTJDNC45MzM1OSA4LjE5OTIyIDQuODU1NDcgOC4wODIwMyA0Ljc0NjA5IDcuOTc2NTZDNC42NDA2MiA3Ljg3MTA5IDQuNSA3Ljc3NTM5IDQuMzI0MjIgNy42ODk0NUM0LjE1MjM0IDcuNTk5NjEgMy45NDMzNiA3LjUxMTcyIDMuNjk3MjcgNy40MjU3OEMzLjMwMjczIDcuMjg1MTYgMi45NDMzNiA3LjEzNjcyIDIuNjE5MTQgNi45ODA0N0MyLjI5NDkyIDYuODI0MjIgMi4wMTc1OCA2LjY0MjU4IDEuNzg3MTEgNi40MzU1NUMxLjU2MDU1IDYuMjI4NTIgMS4zODQ3NyA1Ljk4ODI4IDEuMjU5NzcgNS43MTQ4NEMxLjEzNDc3IDUuNDM3NSAxLjA3MjI3IDUuMTA5MzggMS4wNzIyNyA0LjczMDQ3QzEuMDcyMjcgNC4zOTg0NCAxLjEyODkxIDQuMDk1NyAxLjI0MjE5IDMuODIyMjdDMS4zNTU0NyAzLjU0NDkyIDEuNTE1NjIgMy4zMDQ2OSAxLjcyMjY2IDMuMTAxNTZDMS45Mjk2OSAyLjg5ODQ0IDIuMTc5NjkgMi43MzQzNyAyLjQ3MjY2IDIuNjA5MzhDMi43NjU2MiAyLjQ4NDM4IDMuMDkxOCAyLjQwNDMgMy40NTExNyAyLjM2OTE0VjEuMTA5MzhINC4zODg2N1YyLjM4MDg2QzQuNzQwMjMgMi40Mjc3MyA1LjA1NjY0IDIuNTIzNDQgNS4zMzc4OSAyLjY2Nzk3QzUuNjE5MTQgMi44MTI1IDUuODU3NDIgMy4wMDE5NSA2LjA1MjczIDMuMjM2MzNDNi4yNTE5NSAzLjQ2NjggNi40MDQzIDMuNzQwMjMgNi41MDk3NyA0LjA1NjY0QzYuNjE5MTQgNC4zNjkxNCA2LjY3MzgzIDQuNzIwNyA2LjY3MzgzIDUuMTExMzNINS4wNDQ5MkM1LjA0NDkyIDQuNjM4NjcgNC45Mzc1IDQuMjgxMjUgNC43MjI2NiA0LjAzOTA2QzQuNTA3ODEgMy43OTI5NyA0LjIxNjggMy42Njk5MiAzLjg0OTYxIDMuNjY5OTJDMy42NTAzOSAzLjY2OTkyIDMuNDc2NTYgMy42OTcyNyAzLjMyODEyIDMuNzUxOTVDMy4xODM1OSAzLjgwMjczIDMuMDY0NDUgMy44NzY5NSAyLjk3MDcgMy45NzQ2MUMyLjg3Njk1IDQuMDY4MzYgMi44MDY2NCA0LjE3OTY5IDIuNzU5NzcgNC4zMDg1OUMyLjcxNjggNC40Mzc1IDIuNjk1MzEgNC41NzgxMiAyLjY5NTMxIDQuNzMwNDdDMi42OTUzMSA0Ljg4MjgxIDIuNzE2OCA1LjAxOTUzIDIuNzU5NzcgNS4xNDA2MkMyLjgwNjY0IDUuMjU3ODEgMi44ODI4MSA1LjM2NzE5IDIuOTg4MjggNS40Njg3NUMzLjA5NzY2IDUuNTcwMzEgMy4yNDAyMyA1LjY2Nzk3IDMuNDE2MDIgNS43NjE3MkMzLjU5MTggNS44NTE1NiAzLjgxMDU1IDUuOTQzMzYgNC4wNzIyNyA2LjAzNzExQzQuNDY2OCA2LjE4NTU1IDQuODI0MjIgNi4zMzk4NCA1LjE0NDUzIDYuNUM1LjQ2NDg0IDYuNjU2MjUgNS43MzgyOCA2LjgzOTg0IDUuOTY0ODQgNy4wNTA3OEM2LjE5NTMxIDcuMjU3ODEgNi4zNzEwOSA3LjUgNi40OTIxOSA3Ljc3NzM0QzYuNjE3MTkgOC4wNTA3OCA2LjY3OTY5IDguMzc1IDYuNjc5NjkgOC43NUM2LjY3OTY5IDkuMDkzNzUgNi42MjMwNSA5LjQwNDMgNi41MDk3NyA5LjY4MTY0QzYuMzk2NDggOS45NTUwOCA2LjIzNDM4IDEwLjE5MTQgNi4wMjM0NCAxMC4zOTA2QzUuODEyNSAxMC41ODk4IDUuNTU4NTkgMTAuNzUgNS4yNjE3MiAxMC44NzExQzQuOTY0ODQgMTAuOTg4MyA0LjYzMjgxIDExLjA2NDUgNC4yNjU2MiAxMS4wOTk2VjEyLjI0OEgzLjMzMzk4VjExLjA5OTZDMy4wMDE5NSAxMS4wNjg0IDIuNjc5NjkgMTAuOTk2MSAyLjM2NzE5IDEwLjg4MjhDMi4wNTQ2OSAxMC43NjU2IDEuNzc3MzQgMTAuNTk3NyAxLjUzNTE2IDEwLjM3ODlDMS4yOTY4OCAxMC4xNjAyIDEuMTA1NDcgOS44ODQ3NyAwLjk2MDkzOCA5LjU1MjczQzAuODE2NDA2IDkuMjE2OCAwLjc0NDE0MSA4LjgxNDQ1IDAuNzQ0MTQxIDguMzQ1N0gyLjM3ODkxQzIuMzc4OTEgOC42MjY5NSAyLjQxOTkyIDguODYzMjggMi41MDE5NSA5LjA1NDY5QzIuNTgzOTggOS4yNDIxOSAyLjY4OTQ1IDkuMzkyNTggMi44MTgzNiA5LjUwNTg2QzIuOTUxMTcgOS42MTUyMyAzLjEwMTU2IDkuNjkzMzYgMy4yNjk1MyA5Ljc0MDIzQzMuNDM3NSA5Ljc4NzExIDMuNjA5MzggOS44MTA1NSAzLjc4NTE2IDkuODEwNTVDNC4yMDMxMiA5LjgxMDU1IDQuNTE5NTMgOS43MTI4OSA0LjczNDM4IDkuNTE3NThDNC45NDkyMiA5LjMyMjI3IDUuMDU2NjQgOS4wNzAzMSA1LjA1NjY0IDguNzYxNzJaTTEzLjQxOCAxMi4yNzE1SDguMDc0MjJWMTFIMTMuNDE4VjEyLjI3MTVaIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzLjk1MjY0IDYpIiBmaWxsPSJ3aGl0ZSIvPgo8L3N2Zz4K);
  --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTUgMTVIM3YyaDEydi0yem0wLThIM3YyaDEyVjd6TTMgMTNoMTh2LTJIM3Yyem0wIDhoMTh2LTJIM3Yyek0zIDN2MmgxOFYzSDN6Ii8+Cjwvc3ZnPgo=);
  --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
  --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
  --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
}

/* Icon CSS class declarations */

.jp-AddIcon {
  background-image: var(--jp-icon-add);
}
.jp-BugIcon {
  background-image: var(--jp-icon-bug);
}
.jp-BuildIcon {
  background-image: var(--jp-icon-build);
}
.jp-CaretDownEmptyIcon {
  background-image: var(--jp-icon-caret-down-empty);
}
.jp-CaretDownEmptyThinIcon {
  background-image: var(--jp-icon-caret-down-empty-thin);
}
.jp-CaretDownIcon {
  background-image: var(--jp-icon-caret-down);
}
.jp-CaretLeftIcon {
  background-image: var(--jp-icon-caret-left);
}
.jp-CaretRightIcon {
  background-image: var(--jp-icon-caret-right);
}
.jp-CaretUpEmptyThinIcon {
  background-image: var(--jp-icon-caret-up-empty-thin);
}
.jp-CaretUpIcon {
  background-image: var(--jp-icon-caret-up);
}
.jp-CaseSensitiveIcon {
  background-image: var(--jp-icon-case-sensitive);
}
.jp-CheckIcon {
  background-image: var(--jp-icon-check);
}
.jp-CircleEmptyIcon {
  background-image: var(--jp-icon-circle-empty);
}
.jp-CircleIcon {
  background-image: var(--jp-icon-circle);
}
.jp-ClearIcon {
  background-image: var(--jp-icon-clear);
}
.jp-CloseIcon {
  background-image: var(--jp-icon-close);
}
.jp-ConsoleIcon {
  background-image: var(--jp-icon-console);
}
.jp-CopyIcon {
  background-image: var(--jp-icon-copy);
}
.jp-CutIcon {
  background-image: var(--jp-icon-cut);
}
.jp-DownloadIcon {
  background-image: var(--jp-icon-download);
}
.jp-EditIcon {
  background-image: var(--jp-icon-edit);
}
.jp-EllipsesIcon {
  background-image: var(--jp-icon-ellipses);
}
.jp-ExtensionIcon {
  background-image: var(--jp-icon-extension);
}
.jp-FastForwardIcon {
  background-image: var(--jp-icon-fast-forward);
}
.jp-FileIcon {
  background-image: var(--jp-icon-file);
}
.jp-FileUploadIcon {
  background-image: var(--jp-icon-file-upload);
}
.jp-FilterListIcon {
  background-image: var(--jp-icon-filter-list);
}
.jp-FolderIcon {
  background-image: var(--jp-icon-folder);
}
.jp-Html5Icon {
  background-image: var(--jp-icon-html5);
}
.jp-ImageIcon {
  background-image: var(--jp-icon-image);
}
.jp-InspectorIcon {
  background-image: var(--jp-icon-inspector);
}
.jp-JsonIcon {
  background-image: var(--jp-icon-json);
}
.jp-JupyterFaviconIcon {
  background-image: var(--jp-icon-jupyter-favicon);
}
.jp-JupyterIcon {
  background-image: var(--jp-icon-jupyter);
}
.jp-JupyterlabWordmarkIcon {
  background-image: var(--jp-icon-jupyterlab-wordmark);
}
.jp-KernelIcon {
  background-image: var(--jp-icon-kernel);
}
.jp-KeyboardIcon {
  background-image: var(--jp-icon-keyboard);
}
.jp-LauncherIcon {
  background-image: var(--jp-icon-launcher);
}
.jp-LineFormIcon {
  background-image: var(--jp-icon-line-form);
}
.jp-LinkIcon {
  background-image: var(--jp-icon-link);
}
.jp-ListIcon {
  background-image: var(--jp-icon-list);
}
.jp-ListingsInfoIcon {
  background-image: var(--jp-icon-listings-info);
}
.jp-MarkdownIcon {
  background-image: var(--jp-icon-markdown);
}
.jp-NewFolderIcon {
  background-image: var(--jp-icon-new-folder);
}
.jp-NotTrustedIcon {
  background-image: var(--jp-icon-not-trusted);
}
.jp-NotebookIcon {
  background-image: var(--jp-icon-notebook);
}
.jp-PaletteIcon {
  background-image: var(--jp-icon-palette);
}
.jp-PasteIcon {
  background-image: var(--jp-icon-paste);
}
.jp-PythonIcon {
  background-image: var(--jp-icon-python);
}
.jp-RKernelIcon {
  background-image: var(--jp-icon-r-kernel);
}
.jp-ReactIcon {
  background-image: var(--jp-icon-react);
}
.jp-RefreshIcon {
  background-image: var(--jp-icon-refresh);
}
.jp-RegexIcon {
  background-image: var(--jp-icon-regex);
}
.jp-RunIcon {
  background-image: var(--jp-icon-run);
}
.jp-RunningIcon {
  background-image: var(--jp-icon-running);
}
.jp-SaveIcon {
  background-image: var(--jp-icon-save);
}
.jp-SearchIcon {
  background-image: var(--jp-icon-search);
}
.jp-SettingsIcon {
  background-image: var(--jp-icon-settings);
}
.jp-SpreadsheetIcon {
  background-image: var(--jp-icon-spreadsheet);
}
.jp-StopIcon {
  background-image: var(--jp-icon-stop);
}
.jp-TabIcon {
  background-image: var(--jp-icon-tab);
}
.jp-TerminalIcon {
  background-image: var(--jp-icon-terminal);
}
.jp-TextEditorIcon {
  background-image: var(--jp-icon-text-editor);
}
.jp-TrustedIcon {
  background-image: var(--jp-icon-trusted);
}
.jp-UndoIcon {
  background-image: var(--jp-icon-undo);
}
.jp-VegaIcon {
  background-image: var(--jp-icon-vega);
}
.jp-YamlIcon {
  background-image: var(--jp-icon-yaml);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * (DEPRECATED) Support for consuming icons as CSS background images
 */

:root {
  --jp-icon-search-white: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
}

.jp-Icon,
.jp-MaterialIcon {
  background-position: center;
  background-repeat: no-repeat;
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-cover {
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

/**
 * (DEPRECATED) Support for specific CSS icon sizes
 */

.jp-Icon-16 {
  background-size: 16px;
  min-width: 16px;
  min-height: 16px;
}

.jp-Icon-18 {
  background-size: 18px;
  min-width: 18px;
  min-height: 18px;
}

.jp-Icon-20 {
  background-size: 20px;
  min-width: 20px;
  min-height: 20px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for icons as inline SVG HTMLElements
 */

/* recolor the primary elements of an icon */
.jp-icon0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}
/* recolor the accent elements of an icon */
.jp-icon-accent0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-accent1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-accent2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-accent3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-accent4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-accent0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-accent1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-accent2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-accent3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-accent4[stroke] {
  stroke: var(--jp-layout-color4);
}
/* set the color of an icon to transparent */
.jp-icon-none[fill] {
  fill: none;
}

.jp-icon-none[stroke] {
  stroke: none;
}
/* brand icon colors. Same for light and dark */
.jp-icon-brand0[fill] {
  fill: var(--jp-brand-color0);
}
.jp-icon-brand1[fill] {
  fill: var(--jp-brand-color1);
}
.jp-icon-brand2[fill] {
  fill: var(--jp-brand-color2);
}
.jp-icon-brand3[fill] {
  fill: var(--jp-brand-color3);
}
.jp-icon-brand4[fill] {
  fill: var(--jp-brand-color4);
}

.jp-icon-brand0[stroke] {
  stroke: var(--jp-brand-color0);
}
.jp-icon-brand1[stroke] {
  stroke: var(--jp-brand-color1);
}
.jp-icon-brand2[stroke] {
  stroke: var(--jp-brand-color2);
}
.jp-icon-brand3[stroke] {
  stroke: var(--jp-brand-color3);
}
.jp-icon-brand4[stroke] {
  stroke: var(--jp-brand-color4);
}
/* warn icon colors. Same for light and dark */
.jp-icon-warn0[fill] {
  fill: var(--jp-warn-color0);
}
.jp-icon-warn1[fill] {
  fill: var(--jp-warn-color1);
}
.jp-icon-warn2[fill] {
  fill: var(--jp-warn-color2);
}
.jp-icon-warn3[fill] {
  fill: var(--jp-warn-color3);
}

.jp-icon-warn0[stroke] {
  stroke: var(--jp-warn-color0);
}
.jp-icon-warn1[stroke] {
  stroke: var(--jp-warn-color1);
}
.jp-icon-warn2[stroke] {
  stroke: var(--jp-warn-color2);
}
.jp-icon-warn3[stroke] {
  stroke: var(--jp-warn-color3);
}
/* icon colors that contrast well with each other and most backgrounds */
.jp-icon-contrast0[fill] {
  fill: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[fill] {
  fill: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[fill] {
  fill: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[fill] {
  fill: var(--jp-icon-contrast-color3);
}

.jp-icon-contrast0[stroke] {
  stroke: var(--jp-icon-contrast-color0);
}
.jp-icon-contrast1[stroke] {
  stroke: var(--jp-icon-contrast-color1);
}
.jp-icon-contrast2[stroke] {
  stroke: var(--jp-icon-contrast-color2);
}
.jp-icon-contrast3[stroke] {
  stroke: var(--jp-icon-contrast-color3);
}

/* CSS for icons in selected items in the settings editor */
#setting-editor .jp-PluginList .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
#setting-editor
  .jp-PluginList
  .jp-mod-selected
  .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected filebrowser listing items */
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}
.jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}

/* CSS for icons in selected tabs in the sidebar tab manager */
#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable[fill] {
  fill: #fff;
}

#tab-manager .lm-TabBar-tab.jp-mod-active .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable[fill] {
  fill: var(--jp-brand-color1);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-active
  .jp-icon-hover
  :hover
  .jp-icon-selectable-inverse[fill] {
  fill: #fff;
}

/**
 * TODO: come up with non css-hack solution for showing the busy icon on top
 *  of the close icon
 * CSS for complex behavior of close icon of tabs in the sidebar tab manager
 */
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
#tab-manager
  .lm-TabBar-tab.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

#tab-manager
  .lm-TabBar-tab.jp-mod-dirty.jp-mod-active
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: #fff;
}

/**
* TODO: come up with non css-hack solution for showing the busy icon on top
*  of the close icon
* CSS for complex behavior of close icon of tabs in the main area tabbar
*/
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon3[fill] {
  fill: none;
}
.lm-DockPanel-tabBar
  .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
  > .lm-TabBar-tabCloseIcon
  > :not(:hover)
  > .jp-icon-busy[fill] {
  fill: var(--jp-inverse-layout-color3);
}

/* CSS for icons in status bar */
#jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
  fill: #fff;
}

#jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
  fill: var(--jp-brand-color1);
}
/* special handling for splash icon CSS. While the theme CSS reloads during
   splash, the splash icon can loose theming. To prevent that, we set a
   default for its color variable */
:root {
  --jp-warn-color0: var(--md-orange-700);
}

/* not sure what to do with this one, used in filebrowser listing */
.jp-DragIcon {
  margin-right: 4px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/**
 * Support for alt colors for icons as inline SVG HTMLElements
 */

/* alt recolor the primary elements of an icon */
.jp-icon-alt .jp-icon0[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-alt .jp-icon0[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-alt .jp-icon1[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-alt .jp-icon2[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-alt .jp-icon3[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-alt .jp-icon4[stroke] {
  stroke: var(--jp-layout-color4);
}

/* alt recolor the accent elements of an icon */
.jp-icon-alt .jp-icon-accent0[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-alt .jp-icon-accent0[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-alt .jp-icon-accent1[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-alt .jp-icon-accent2[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-alt .jp-icon-accent3[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-alt .jp-icon-accent4[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-icon-hoverShow:not(:hover) svg {
  display: none !important;
}

/**
 * Support for hover colors for icons as inline SVG HTMLElements
 */

/**
 * regular colors
 */

/* recolor the primary elements of an icon */
.jp-icon-hover :hover .jp-icon0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/* recolor the accent elements of an icon */
.jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* set the color of an icon to transparent */
.jp-icon-hover :hover .jp-icon-none-hover[fill] {
  fill: none;
}

.jp-icon-hover :hover .jp-icon-none-hover[stroke] {
  stroke: none;
}

/**
 * inverse colors
 */

/* inverse recolor the primary elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
  fill: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
  fill: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
  fill: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
  fill: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
  fill: var(--jp-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
  stroke: var(--jp-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
  stroke: var(--jp-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
  stroke: var(--jp-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
  stroke: var(--jp-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
  stroke: var(--jp-layout-color4);
}

/* inverse recolor the accent elements of an icon */
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
  fill: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
  fill: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
  fill: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
  fill: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
  fill: var(--jp-inverse-layout-color4);
}

.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
  stroke: var(--jp-inverse-layout-color0);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
  stroke: var(--jp-inverse-layout-color1);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
  stroke: var(--jp-inverse-layout-color2);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
  stroke: var(--jp-inverse-layout-color3);
}
.jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
  stroke: var(--jp-inverse-layout-color4);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* Sibling imports */

/* Override Blueprint's _reset.scss styles */
html {
  box-sizing: unset;
}

*,
*::before,
*::after {
  box-sizing: unset;
}

body {
  color: unset;
  font-family: var(--jp-ui-font-family);
}

p {
  margin-top: unset;
  margin-bottom: unset;
}

small {
  font-size: unset;
}

strong {
  font-weight: unset;
}

/* Override Blueprint's _typography.scss styles */
a {
  text-decoration: unset;
  color: unset;
}
a:hover {
  text-decoration: unset;
  color: unset;
}

/* Override Blueprint's _accessibility.scss styles */
:focus {
  outline: unset;
  outline-offset: unset;
  -moz-outline-radius: unset;
}

/* Styles for ui-components */
.jp-Button {
  border-radius: var(--jp-border-radius);
  padding: 0px 12px;
  font-size: var(--jp-ui-font-size1);
}

/* Use our own theme for hover styles */
button.jp-Button.bp3-button.bp3-minimal:hover {
  background-color: var(--jp-layout-color2);
}
.jp-Button.minimal {
  color: unset !important;
}

.jp-Button.jp-ToolbarButtonComponent {
  text-transform: none;
}

.jp-InputGroup input {
  box-sizing: border-box;
  border-radius: 0;
  background-color: transparent;
  color: var(--jp-ui-font-color0);
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.jp-InputGroup input:focus {
  box-shadow: inset 0 0 0 var(--jp-border-width)
      var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.jp-InputGroup input::placeholder,
input::placeholder {
  color: var(--jp-ui-font-color3);
}

.jp-BPIcon {
  display: inline-block;
  vertical-align: middle;
  margin: auto;
}

/* Stop blueprint futzing with our icon fills */
.bp3-icon.jp-BPIcon > svg:not([fill]) {
  fill: var(--jp-inverse-layout-color3);
}

.jp-InputGroupAction {
  padding: 6px;
}

.jp-HTMLSelect.jp-DefaultStyle select {
  background-color: initial;
  border: none;
  border-radius: 0;
  box-shadow: none;
  color: var(--jp-ui-font-color0);
  display: block;
  font-size: var(--jp-ui-font-size1);
  height: 24px;
  line-height: 14px;
  padding: 0 25px 0 10px;
  text-align: left;
  -moz-appearance: none;
  -webkit-appearance: none;
}

/* Use our own theme for hover and option styles */
.jp-HTMLSelect.jp-DefaultStyle select:hover,
.jp-HTMLSelect.jp-DefaultStyle select > option {
  background-color: var(--jp-layout-color2);
  color: var(--jp-ui-font-color0);
}
select {
  box-sizing: border-box;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapse {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-top: 1px solid var(--jp-border-color2);
  border-bottom: 1px solid var(--jp-border-color2);
}

.jp-Collapse-header {
  padding: 1px 12px;
  color: var(--jp-ui-font-color1);
  background-color: var(--jp-layout-color1);
  font-size: var(--jp-ui-font-size2);
}

.jp-Collapse-header:hover {
  background-color: var(--jp-layout-color2);
}

.jp-Collapse-contents {
  padding: 0px 12px 0px 12px;
  background-color: var(--jp-layout-color1);
  color: var(--jp-ui-font-color1);
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-commandpalette-search-height: 28px;
}

/*-----------------------------------------------------------------------------
| Overall styles
|----------------------------------------------------------------------------*/

.lm-CommandPalette {
  padding-bottom: 0px;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Search
|----------------------------------------------------------------------------*/

.lm-CommandPalette-search {
  padding: 4px;
  background-color: var(--jp-layout-color1);
  z-index: 2;
}

.lm-CommandPalette-wrapper {
  overflow: overlay;
  padding: 0px 9px;
  background-color: var(--jp-input-active-background);
  height: 30px;
  box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
}

.lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
  box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
    inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
}

.lm-CommandPalette-wrapper::after {
  content: ' ';
  color: white;
  background-color: var(--jp-brand-color1);
  position: absolute;
  top: 4px;
  right: 4px;
  height: 30px;
  width: 10px;
  padding: 0px 10px;
  background-image: var(--jp-icon-search-white);
  background-size: 20px;
  background-repeat: no-repeat;
  background-position: center;
}

.lm-CommandPalette-input {
  background: transparent;
  width: calc(100% - 18px);
  float: left;
  border: none;
  outline: none;
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  line-height: var(--jp-private-commandpalette-search-height);
}

.lm-CommandPalette-input::-webkit-input-placeholder,
.lm-CommandPalette-input::-moz-placeholder,
.lm-CommandPalette-input:-ms-input-placeholder {
  color: var(--jp-ui-font-color3);
  font-size: var(--jp-ui-font-size1);
}

/*-----------------------------------------------------------------------------
| Results
|----------------------------------------------------------------------------*/

.lm-CommandPalette-header:first-child {
  margin-top: 0px;
}

.lm-CommandPalette-header {
  border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
  color: var(--jp-ui-font-color1);
  cursor: pointer;
  display: flex;
  font-size: var(--jp-ui-font-size0);
  font-weight: 600;
  letter-spacing: 1px;
  margin-top: 8px;
  padding: 8px 0 8px 12px;
  text-transform: uppercase;
}

.lm-CommandPalette-header.lm-mod-active {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-header > mark {
  background-color: transparent;
  font-weight: bold;
  color: var(--jp-ui-font-color1);
}

.lm-CommandPalette-item {
  padding: 4px 12px 4px 4px;
  color: var(--jp-ui-font-color1);
  font-size: var(--jp-ui-font-size1);
  font-weight: 400;
  display: flex;
}

.lm-CommandPalette-item.lm-mod-disabled {
  color: var(--jp-ui-font-color3);
}

.lm-CommandPalette-item.lm-mod-active {
  background: var(--jp-layout-color3);
}

.lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
  background: var(--jp-layout-color4);
}

.lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
  background: var(--jp-layout-color2);
}

.lm-CommandPalette-itemContent {
  overflow: hidden;
}

.lm-CommandPalette-itemLabel > mark {
  color: var(--jp-ui-font-color0);
  background-color: transparent;
  font-weight: bold;
}

.lm-CommandPalette-item.lm-mod-disabled mark {
  color: var(--jp-ui-font-color3);
}

.lm-CommandPalette-item .lm-CommandPalette-itemIcon {
  margin: 0 4px 0 0;
  position: relative;
  width: 16px;
  top: 2px;
  flex: 0 0 auto;
}

.lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
  opacity: 0.4;
}

.lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
  flex: 0 0 auto;
}

.lm-CommandPalette-itemCaption {
  display: none;
}

.lm-CommandPalette-content {
  background-color: var(--jp-layout-color1);
}

.lm-CommandPalette-content:empty:after {
  content: 'No results';
  margin: auto;
  margin-top: 20px;
  width: 100px;
  display: block;
  font-size: var(--jp-ui-font-size2);
  font-family: var(--jp-ui-font-family);
  font-weight: lighter;
}

.lm-CommandPalette-emptyMessage {
  text-align: center;
  margin-top: 24px;
  line-height: 1.32;
  padding: 0px 8px;
  color: var(--jp-content-font-color3);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Dialog {
  position: absolute;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  top: 0px;
  left: 0px;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-dialog-background);
}

.jp-Dialog-content {
  display: flex;
  flex-direction: column;
  margin-left: auto;
  margin-right: auto;
  background: var(--jp-layout-color1);
  padding: 24px;
  padding-bottom: 12px;
  min-width: 300px;
  min-height: 150px;
  max-width: 1000px;
  max-height: 500px;
  box-sizing: border-box;
  box-shadow: var(--jp-elevation-z20);
  word-wrap: break-word;
  border-radius: var(--jp-border-radius);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color1);
}

.jp-Dialog-button {
  overflow: visible;
}

button.jp-Dialog-button:focus {
  outline: 1px solid var(--jp-brand-color1);
  outline-offset: 4px;
  -moz-outline-radius: 0px;
}

button.jp-Dialog-button:focus::-moz-focus-inner {
  border: 0;
}

.jp-Dialog-header {
  flex: 0 0 auto;
  padding-bottom: 12px;
  font-size: var(--jp-ui-font-size3);
  font-weight: 400;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-body {
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
  font-size: var(--jp-ui-font-size1);
  background: var(--jp-layout-color1);
  overflow: auto;
}

.jp-Dialog-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  flex: 0 0 auto;
  margin-left: -12px;
  margin-right: -12px;
  padding: 12px;
}

.jp-Dialog-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.jp-Dialog-body > .jp-select-wrapper {
  width: 100%;
}

.jp-Dialog-body > button {
  padding: 0px 16px;
}

.jp-Dialog-body > label {
  line-height: 1.4;
  color: var(--jp-ui-font-color0);
}

.jp-Dialog-button.jp-mod-styled:not(:last-child) {
  margin-right: 12px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-HoverBox {
  position: fixed;
}

.jp-HoverBox.jp-mod-outofview {
  display: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-IFrame {
  width: 100%;
  height: 100%;
}

.jp-IFrame > iframe {
  border: none;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-IFrame {
  position: relative;
}

body.lm-mod-override-cursor .jp-IFrame:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MainAreaWidget > :focus {
  outline: none;
}

/**
 * google-material-color v1.2.6
 * https://github.com/danlevan/google-material-color
 */
:root {
  --md-red-50: #ffebee;
  --md-red-100: #ffcdd2;
  --md-red-200: #ef9a9a;
  --md-red-300: #e57373;
  --md-red-400: #ef5350;
  --md-red-500: #f44336;
  --md-red-600: #e53935;
  --md-red-700: #d32f2f;
  --md-red-800: #c62828;
  --md-red-900: #b71c1c;
  --md-red-A100: #ff8a80;
  --md-red-A200: #ff5252;
  --md-red-A400: #ff1744;
  --md-red-A700: #d50000;

  --md-pink-50: #fce4ec;
  --md-pink-100: #f8bbd0;
  --md-pink-200: #f48fb1;
  --md-pink-300: #f06292;
  --md-pink-400: #ec407a;
  --md-pink-500: #e91e63;
  --md-pink-600: #d81b60;
  --md-pink-700: #c2185b;
  --md-pink-800: #ad1457;
  --md-pink-900: #880e4f;
  --md-pink-A100: #ff80ab;
  --md-pink-A200: #ff4081;
  --md-pink-A400: #f50057;
  --md-pink-A700: #c51162;

  --md-purple-50: #f3e5f5;
  --md-purple-100: #e1bee7;
  --md-purple-200: #ce93d8;
  --md-purple-300: #ba68c8;
  --md-purple-400: #ab47bc;
  --md-purple-500: #9c27b0;
  --md-purple-600: #8e24aa;
  --md-purple-700: #7b1fa2;
  --md-purple-800: #6a1b9a;
  --md-purple-900: #4a148c;
  --md-purple-A100: #ea80fc;
  --md-purple-A200: #e040fb;
  --md-purple-A400: #d500f9;
  --md-purple-A700: #aa00ff;

  --md-deep-purple-50: #ede7f6;
  --md-deep-purple-100: #d1c4e9;
  --md-deep-purple-200: #b39ddb;
  --md-deep-purple-300: #9575cd;
  --md-deep-purple-400: #7e57c2;
  --md-deep-purple-500: #673ab7;
  --md-deep-purple-600: #5e35b1;
  --md-deep-purple-700: #512da8;
  --md-deep-purple-800: #4527a0;
  --md-deep-purple-900: #311b92;
  --md-deep-purple-A100: #b388ff;
  --md-deep-purple-A200: #7c4dff;
  --md-deep-purple-A400: #651fff;
  --md-deep-purple-A700: #6200ea;

  --md-indigo-50: #e8eaf6;
  --md-indigo-100: #c5cae9;
  --md-indigo-200: #9fa8da;
  --md-indigo-300: #7986cb;
  --md-indigo-400: #5c6bc0;
  --md-indigo-500: #3f51b5;
  --md-indigo-600: #3949ab;
  --md-indigo-700: #303f9f;
  --md-indigo-800: #283593;
  --md-indigo-900: #1a237e;
  --md-indigo-A100: #8c9eff;
  --md-indigo-A200: #536dfe;
  --md-indigo-A400: #3d5afe;
  --md-indigo-A700: #304ffe;

  --md-blue-50: #e3f2fd;
  --md-blue-100: #bbdefb;
  --md-blue-200: #90caf9;
  --md-blue-300: #64b5f6;
  --md-blue-400: #42a5f5;
  --md-blue-500: #2196f3;
  --md-blue-600: #1e88e5;
  --md-blue-700: #1976d2;
  --md-blue-800: #1565c0;
  --md-blue-900: #0d47a1;
  --md-blue-A100: #82b1ff;
  --md-blue-A200: #448aff;
  --md-blue-A400: #2979ff;
  --md-blue-A700: #2962ff;

  --md-light-blue-50: #e1f5fe;
  --md-light-blue-100: #b3e5fc;
  --md-light-blue-200: #81d4fa;
  --md-light-blue-300: #4fc3f7;
  --md-light-blue-400: #29b6f6;
  --md-light-blue-500: #03a9f4;
  --md-light-blue-600: #039be5;
  --md-light-blue-700: #0288d1;
  --md-light-blue-800: #0277bd;
  --md-light-blue-900: #01579b;
  --md-light-blue-A100: #80d8ff;
  --md-light-blue-A200: #40c4ff;
  --md-light-blue-A400: #00b0ff;
  --md-light-blue-A700: #0091ea;

  --md-cyan-50: #e0f7fa;
  --md-cyan-100: #b2ebf2;
  --md-cyan-200: #80deea;
  --md-cyan-300: #4dd0e1;
  --md-cyan-400: #26c6da;
  --md-cyan-500: #00bcd4;
  --md-cyan-600: #00acc1;
  --md-cyan-700: #0097a7;
  --md-cyan-800: #00838f;
  --md-cyan-900: #006064;
  --md-cyan-A100: #84ffff;
  --md-cyan-A200: #18ffff;
  --md-cyan-A400: #00e5ff;
  --md-cyan-A700: #00b8d4;

  --md-teal-50: #e0f2f1;
  --md-teal-100: #b2dfdb;
  --md-teal-200: #80cbc4;
  --md-teal-300: #4db6ac;
  --md-teal-400: #26a69a;
  --md-teal-500: #009688;
  --md-teal-600: #00897b;
  --md-teal-700: #00796b;
  --md-teal-800: #00695c;
  --md-teal-900: #004d40;
  --md-teal-A100: #a7ffeb;
  --md-teal-A200: #64ffda;
  --md-teal-A400: #1de9b6;
  --md-teal-A700: #00bfa5;

  --md-green-50: #e8f5e9;
  --md-green-100: #c8e6c9;
  --md-green-200: #a5d6a7;
  --md-green-300: #81c784;
  --md-green-400: #66bb6a;
  --md-green-500: #4caf50;
  --md-green-600: #43a047;
  --md-green-700: #388e3c;
  --md-green-800: #2e7d32;
  --md-green-900: #1b5e20;
  --md-green-A100: #b9f6ca;
  --md-green-A200: #69f0ae;
  --md-green-A400: #00e676;
  --md-green-A700: #00c853;

  --md-light-green-50: #f1f8e9;
  --md-light-green-100: #dcedc8;
  --md-light-green-200: #c5e1a5;
  --md-light-green-300: #aed581;
  --md-light-green-400: #9ccc65;
  --md-light-green-500: #8bc34a;
  --md-light-green-600: #7cb342;
  --md-light-green-700: #689f38;
  --md-light-green-800: #558b2f;
  --md-light-green-900: #33691e;
  --md-light-green-A100: #ccff90;
  --md-light-green-A200: #b2ff59;
  --md-light-green-A400: #76ff03;
  --md-light-green-A700: #64dd17;

  --md-lime-50: #f9fbe7;
  --md-lime-100: #f0f4c3;
  --md-lime-200: #e6ee9c;
  --md-lime-300: #dce775;
  --md-lime-400: #d4e157;
  --md-lime-500: #cddc39;
  --md-lime-600: #c0ca33;
  --md-lime-700: #afb42b;
  --md-lime-800: #9e9d24;
  --md-lime-900: #827717;
  --md-lime-A100: #f4ff81;
  --md-lime-A200: #eeff41;
  --md-lime-A400: #c6ff00;
  --md-lime-A700: #aeea00;

  --md-yellow-50: #fffde7;
  --md-yellow-100: #fff9c4;
  --md-yellow-200: #fff59d;
  --md-yellow-300: #fff176;
  --md-yellow-400: #ffee58;
  --md-yellow-500: #ffeb3b;
  --md-yellow-600: #fdd835;
  --md-yellow-700: #fbc02d;
  --md-yellow-800: #f9a825;
  --md-yellow-900: #f57f17;
  --md-yellow-A100: #ffff8d;
  --md-yellow-A200: #ffff00;
  --md-yellow-A400: #ffea00;
  --md-yellow-A700: #ffd600;

  --md-amber-50: #fff8e1;
  --md-amber-100: #ffecb3;
  --md-amber-200: #ffe082;
  --md-amber-300: #ffd54f;
  --md-amber-400: #ffca28;
  --md-amber-500: #ffc107;
  --md-amber-600: #ffb300;
  --md-amber-700: #ffa000;
  --md-amber-800: #ff8f00;
  --md-amber-900: #ff6f00;
  --md-amber-A100: #ffe57f;
  --md-amber-A200: #ffd740;
  --md-amber-A400: #ffc400;
  --md-amber-A700: #ffab00;

  --md-orange-50: #fff3e0;
  --md-orange-100: #ffe0b2;
  --md-orange-200: #ffcc80;
  --md-orange-300: #ffb74d;
  --md-orange-400: #ffa726;
  --md-orange-500: #ff9800;
  --md-orange-600: #fb8c00;
  --md-orange-700: #f57c00;
  --md-orange-800: #ef6c00;
  --md-orange-900: #e65100;
  --md-orange-A100: #ffd180;
  --md-orange-A200: #ffab40;
  --md-orange-A400: #ff9100;
  --md-orange-A700: #ff6d00;

  --md-deep-orange-50: #fbe9e7;
  --md-deep-orange-100: #ffccbc;
  --md-deep-orange-200: #ffab91;
  --md-deep-orange-300: #ff8a65;
  --md-deep-orange-400: #ff7043;
  --md-deep-orange-500: #ff5722;
  --md-deep-orange-600: #f4511e;
  --md-deep-orange-700: #e64a19;
  --md-deep-orange-800: #d84315;
  --md-deep-orange-900: #bf360c;
  --md-deep-orange-A100: #ff9e80;
  --md-deep-orange-A200: #ff6e40;
  --md-deep-orange-A400: #ff3d00;
  --md-deep-orange-A700: #dd2c00;

  --md-brown-50: #efebe9;
  --md-brown-100: #d7ccc8;
  --md-brown-200: #bcaaa4;
  --md-brown-300: #a1887f;
  --md-brown-400: #8d6e63;
  --md-brown-500: #795548;
  --md-brown-600: #6d4c41;
  --md-brown-700: #5d4037;
  --md-brown-800: #4e342e;
  --md-brown-900: #3e2723;

  --md-grey-50: #fafafa;
  --md-grey-100: #f5f5f5;
  --md-grey-200: #eeeeee;
  --md-grey-300: #e0e0e0;
  --md-grey-400: #bdbdbd;
  --md-grey-500: #9e9e9e;
  --md-grey-600: #757575;
  --md-grey-700: #616161;
  --md-grey-800: #424242;
  --md-grey-900: #212121;

  --md-blue-grey-50: #eceff1;
  --md-blue-grey-100: #cfd8dc;
  --md-blue-grey-200: #b0bec5;
  --md-blue-grey-300: #90a4ae;
  --md-blue-grey-400: #78909c;
  --md-blue-grey-500: #607d8b;
  --md-blue-grey-600: #546e7a;
  --md-blue-grey-700: #455a64;
  --md-blue-grey-800: #37474f;
  --md-blue-grey-900: #263238;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Spinner {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: var(--jp-layout-color0);
  outline: none;
}

.jp-SpinnerContent {
  font-size: 10px;
  margin: 50px auto;
  text-indent: -9999em;
  width: 3em;
  height: 3em;
  border-radius: 50%;
  background: var(--jp-brand-color3);
  background: linear-gradient(
    to right,
    #f37626 10%,
    rgba(255, 255, 255, 0) 42%
  );
  position: relative;
  animation: load3 1s infinite linear, fadeIn 1s;
}

.jp-SpinnerContent:before {
  width: 50%;
  height: 50%;
  background: #f37626;
  border-radius: 100% 0 0 0;
  position: absolute;
  top: 0;
  left: 0;
  content: '';
}

.jp-SpinnerContent:after {
  background: var(--jp-layout-color0);
  width: 75%;
  height: 75%;
  border-radius: 50%;
  content: '';
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes load3 {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

button.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: none;
  box-sizing: border-box;
  text-align: center;
  line-height: 32px;
  height: 32px;
  padding: 0px 12px;
  letter-spacing: 0.8px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled {
  background: var(--jp-input-background);
  height: 28px;
  box-sizing: border-box;
  border: var(--jp-border-width) solid var(--jp-border-color1);
  padding-left: 7px;
  padding-right: 7px;
  font-size: var(--jp-ui-font-size2);
  color: var(--jp-ui-font-color0);
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

input.jp-mod-styled:focus {
  border: var(--jp-border-width) solid var(--md-blue-500);
  box-shadow: inset 0 0 4px var(--md-blue-300);
}

.jp-select-wrapper {
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 1px;
  background-color: var(--jp-layout-color1);
  height: 28px;
  box-sizing: border-box;
  margin-bottom: 12px;
}

.jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-input-active-background);
}

select.jp-mod-styled:hover {
  background-color: var(--jp-layout-color1);
  cursor: pointer;
  color: var(--jp-ui-font-color0);
  background-color: var(--jp-input-hover-background);
  box-shadow: inset 0 0px 1px rgba(0, 0, 0, 0.5);
}

select.jp-mod-styled {
  flex: 1 1 auto;
  height: 32px;
  width: 100%;
  font-size: var(--jp-ui-font-size2);
  background: var(--jp-input-background);
  color: var(--jp-ui-font-color0);
  padding: 0 25px 0 8px;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

:root {
  --jp-private-toolbar-height: calc(
    28px + var(--jp-border-width)
  ); /* leave 28px for content */
}

.jp-Toolbar {
  color: var(--jp-ui-font-color1);
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
  box-shadow: var(--jp-toolbar-box-shadow);
  background: var(--jp-toolbar-background);
  min-height: var(--jp-toolbar-micro-height);
  padding: 2px;
  z-index: 1;
}

/* Toolbar items */

.jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
  flex-grow: 1;
  flex-shrink: 1;
}

.jp-Toolbar-item.jp-Toolbar-kernelStatus {
  display: inline-block;
  width: 32px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 16px;
}

.jp-Toolbar > .jp-Toolbar-item {
  flex: 0 0 auto;
  display: flex;
  padding-left: 1px;
  padding-right: 1px;
  font-size: var(--jp-ui-font-size1);
  line-height: var(--jp-private-toolbar-height);
  height: 100%;
}

/* Toolbar buttons */

/* This is the div we use to wrap the react component into a Widget */
div.jp-ToolbarButton {
  color: transparent;
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px;
  margin: 0px;
}

button.jp-ToolbarButtonComponent {
  background: var(--jp-layout-color1);
  border: none;
  box-sizing: border-box;
  outline: none;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 0px 6px;
  margin: 0px;
  height: 24px;
  border-radius: var(--jp-border-radius);
  display: flex;
  align-items: center;
  text-align: center;
  font-size: 14px;
  min-width: unset;
  min-height: unset;
}

button.jp-ToolbarButtonComponent:disabled {
  opacity: 0.4;
}

button.jp-ToolbarButtonComponent span {
  padding: 0px;
  flex: 0 0 auto;
}

button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
  font-size: var(--jp-ui-font-size1);
  line-height: 100%;
  padding-left: 2px;
  color: var(--jp-ui-font-color1);
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2017, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Copyright (c) 2014-2017, PhosphorJS Contributors
|
| Distributed under the terms of the BSD 3-Clause License.
|
| The full license is in the file LICENSE, distributed with this software.
|----------------------------------------------------------------------------*/


/* <DEPRECATED> */ body.p-mod-override-cursor *, /* </DEPRECATED> */
body.lm-mod-override-cursor * {
  cursor: inherit !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) 2014-2016, Jupyter Development Team.
|
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-JSONEditor {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.jp-JSONEditor-host {
  flex: 1 1 auto;
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  border-radius: 0px;
  background: var(--jp-layout-color0);
  min-height: 50px;
  padding: 1px;
}

.jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
  border-color: red;
  outline-color: red;
}

.jp-JSONEditor-header {
  display: flex;
  flex: 1 0 auto;
  padding: 0 0 0 12px;
}

.jp-JSONEditor-header label {
  flex: 0 0 auto;
}

.jp-JSONEditor-commitButton {
  height: 16px;
  width: 16px;
  background-size: 18px;
  background-repeat: no-repeat;
  background-position: center;
}

.jp-JSONEditor-host.jp-mod-focused {
  background-color: var(--jp-input-active-background);
  border: 1px solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

.jp-Editor.jp-mod-dropTarget {
  border: var(--jp-border-width) solid var(--jp-input-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* BASICS */

.CodeMirror {
  /* Set height, width, borders, and global font properties here */
  font-family: monospace;
  height: 300px;
  color: black;
  direction: ltr;
}

/* PADDING */

.CodeMirror-lines {
  padding: 4px 0; /* Vertical padding around content */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  padding: 0 4px; /* Horizontal padding of content */
}

.CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  background-color: white; /* The little square between H and V scrollbars */
}

/* GUTTER */

.CodeMirror-gutters {
  border-right: 1px solid #ddd;
  background-color: #f7f7f7;
  white-space: nowrap;
}
.CodeMirror-linenumbers {}
.CodeMirror-linenumber {
  padding: 0 3px 0 5px;
  min-width: 20px;
  text-align: right;
  color: #999;
  white-space: nowrap;
}

.CodeMirror-guttermarker { color: black; }
.CodeMirror-guttermarker-subtle { color: #999; }

/* CURSOR */

.CodeMirror-cursor {
  border-left: 1px solid black;
  border-right: none;
  width: 0;
}
/* Shown when moving in bi-directional text */
.CodeMirror div.CodeMirror-secondarycursor {
  border-left: 1px solid silver;
}
.cm-fat-cursor .CodeMirror-cursor {
  width: auto;
  border: 0 !important;
  background: #7e7;
}
.cm-fat-cursor div.CodeMirror-cursors {
  z-index: 1;
}
.cm-fat-cursor-mark {
  background-color: rgba(20, 255, 20, 0.5);
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
}
.cm-animate-fat-cursor {
  width: auto;
  border: 0;
  -webkit-animation: blink 1.06s steps(1) infinite;
  -moz-animation: blink 1.06s steps(1) infinite;
  animation: blink 1.06s steps(1) infinite;
  background-color: #7e7;
}
@-moz-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@-webkit-keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}
@keyframes blink {
  0% {}
  50% { background-color: transparent; }
  100% {}
}

/* Can style cursor different in overwrite (non-insert) mode */
.CodeMirror-overwrite .CodeMirror-cursor {}

.cm-tab { display: inline-block; text-decoration: inherit; }

.CodeMirror-rulers {
  position: absolute;
  left: 0; right: 0; top: -50px; bottom: 0;
  overflow: hidden;
}
.CodeMirror-ruler {
  border-left: 1px solid #ccc;
  top: 0; bottom: 0;
  position: absolute;
}

/* DEFAULT THEME */

.cm-s-default .cm-header {color: blue;}
.cm-s-default .cm-quote {color: #090;}
.cm-negative {color: #d44;}
.cm-positive {color: #292;}
.cm-header, .cm-strong {font-weight: bold;}
.cm-em {font-style: italic;}
.cm-link {text-decoration: underline;}
.cm-strikethrough {text-decoration: line-through;}

.cm-s-default .cm-keyword {color: #708;}
.cm-s-default .cm-atom {color: #219;}
.cm-s-default .cm-number {color: #164;}
.cm-s-default .cm-def {color: #00f;}
.cm-s-default .cm-variable,
.cm-s-default .cm-punctuation,
.cm-s-default .cm-property,
.cm-s-default .cm-operator {}
.cm-s-default .cm-variable-2 {color: #05a;}
.cm-s-default .cm-variable-3, .cm-s-default .cm-type {color: #085;}
.cm-s-default .cm-comment {color: #a50;}
.cm-s-default .cm-string {color: #a11;}
.cm-s-default .cm-string-2 {color: #f50;}
.cm-s-default .cm-meta {color: #555;}
.cm-s-default .cm-qualifier {color: #555;}
.cm-s-default .cm-builtin {color: #30a;}
.cm-s-default .cm-bracket {color: #997;}
.cm-s-default .cm-tag {color: #170;}
.cm-s-default .cm-attribute {color: #00c;}
.cm-s-default .cm-hr {color: #999;}
.cm-s-default .cm-link {color: #00c;}

.cm-s-default .cm-error {color: #f00;}
.cm-invalidchar {color: #f00;}

.CodeMirror-composing { border-bottom: 2px solid; }

/* Default styles for common addons */

div.CodeMirror span.CodeMirror-matchingbracket {color: #0b0;}
div.CodeMirror span.CodeMirror-nonmatchingbracket {color: #a22;}
.CodeMirror-matchingtag { background: rgba(255, 150, 0, .3); }
.CodeMirror-activeline-background {background: #e8f2ff;}

/* STOP */

/* The rest of this file contains styles related to the mechanics of
   the editor. You probably shouldn't touch them. */

.CodeMirror {
  position: relative;
  overflow: hidden;
  background: white;
}

.CodeMirror-scroll {
  overflow: scroll !important; /* Things will break if this is overridden */
  /* 30px is the magic margin used to hide the element's real scrollbars */
  /* See overflow: hidden in .CodeMirror */
  margin-bottom: -30px; margin-right: -30px;
  padding-bottom: 30px;
  height: 100%;
  outline: none; /* Prevent dragging from highlighting the element */
  position: relative;
}
.CodeMirror-sizer {
  position: relative;
  border-right: 30px solid transparent;
}

/* The fake, visible scrollbars. Used to force redraw during scrolling
   before actual scrolling happens, thus preventing shaking and
   flickering artifacts. */
.CodeMirror-vscrollbar, .CodeMirror-hscrollbar, .CodeMirror-scrollbar-filler, .CodeMirror-gutter-filler {
  position: absolute;
  z-index: 6;
  display: none;
}
.CodeMirror-vscrollbar {
  right: 0; top: 0;
  overflow-x: hidden;
  overflow-y: scroll;
}
.CodeMirror-hscrollbar {
  bottom: 0; left: 0;
  overflow-y: hidden;
  overflow-x: scroll;
}
.CodeMirror-scrollbar-filler {
  right: 0; bottom: 0;
}
.CodeMirror-gutter-filler {
  left: 0; bottom: 0;
}

.CodeMirror-gutters {
  position: absolute; left: 0; top: 0;
  min-height: 100%;
  z-index: 3;
}
.CodeMirror-gutter {
  white-space: normal;
  height: 100%;
  display: inline-block;
  vertical-align: top;
  margin-bottom: -30px;
}
.CodeMirror-gutter-wrapper {
  position: absolute;
  z-index: 4;
  background: none !important;
  border: none !important;
}
.CodeMirror-gutter-background {
  position: absolute;
  top: 0; bottom: 0;
  z-index: 4;
}
.CodeMirror-gutter-elt {
  position: absolute;
  cursor: default;
  z-index: 4;
}
.CodeMirror-gutter-wrapper ::selection { background-color: transparent }
.CodeMirror-gutter-wrapper ::-moz-selection { background-color: transparent }

.CodeMirror-lines {
  cursor: text;
  min-height: 1px; /* prevents collapsing before first draw */
}
.CodeMirror pre.CodeMirror-line,
.CodeMirror pre.CodeMirror-line-like {
  /* Reset some styles that the rest of the page might have set */
  -moz-border-radius: 0; -webkit-border-radius: 0; border-radius: 0;
  border-width: 0;
  background: transparent;
  font-family: inherit;
  font-size: inherit;
  margin: 0;
  white-space: pre;
  word-wrap: normal;
  line-height: inherit;
  color: inherit;
  z-index: 2;
  position: relative;
  overflow: visible;
  -webkit-tap-highlight-color: transparent;
  -webkit-font-variant-ligatures: contextual;
  font-variant-ligatures: contextual;
}
.CodeMirror-wrap pre.CodeMirror-line,
.CodeMirror-wrap pre.CodeMirror-line-like {
  word-wrap: break-word;
  white-space: pre-wrap;
  word-break: normal;
}

.CodeMirror-linebackground {
  position: absolute;
  left: 0; right: 0; top: 0; bottom: 0;
  z-index: 0;
}

.CodeMirror-linewidget {
  position: relative;
  z-index: 2;
  padding: 0.1px; /* Force widget margins to stay inside of the container */
}

.CodeMirror-widget {}

.CodeMirror-rtl pre { direction: rtl; }

.CodeMirror-code {
  outline: none;
}

/* Force content-box sizing for the elements where we expect it */
.CodeMirror-scroll,
.CodeMirror-sizer,
.CodeMirror-gutter,
.CodeMirror-gutters,
.CodeMirror-linenumber {
  -moz-box-sizing: content-box;
  box-sizing: content-box;
}

.CodeMirror-measure {
  position: absolute;
  width: 100%;
  height: 0;
  overflow: hidden;
  visibility: hidden;
}

.CodeMirror-cursor {
  position: absolute;
  pointer-events: none;
}
.CodeMirror-measure pre { position: static; }

div.CodeMirror-cursors {
  visibility: hidden;
  position: relative;
  z-index: 3;
}
div.CodeMirror-dragcursors {
  visibility: visible;
}

.CodeMirror-focused div.CodeMirror-cursors {
  visibility: visible;
}

.CodeMirror-selected { background: #d9d9d9; }
.CodeMirror-focused .CodeMirror-selected { background: #d7d4f0; }
.CodeMirror-crosshair { cursor: crosshair; }
.CodeMirror-line::selection, .CodeMirror-line > span::selection, .CodeMirror-line > span > span::selection { background: #d7d4f0; }
.CodeMirror-line::-moz-selection, .CodeMirror-line > span::-moz-selection, .CodeMirror-line > span > span::-moz-selection { background: #d7d4f0; }

.cm-searching {
  background-color: #ffa;
  background-color: rgba(255, 255, 0, .4);
}

/* Used to force a border model for a node */
.cm-force-border { padding-right: .1px; }

@media print {
  /* Hide the cursor when printing */
  .CodeMirror div.CodeMirror-cursors {
    visibility: hidden;
  }
}

/* See issue #2901 */
.cm-tab-wrap-hack:after { content: ''; }

/* Help users use markselection to safely style text background */
span.CodeMirror-selectedtext { background: none; }

.CodeMirror-dialog {
  position: absolute;
  left: 0; right: 0;
  background: inherit;
  z-index: 15;
  padding: .1em .8em;
  overflow: hidden;
  color: inherit;
}

.CodeMirror-dialog-top {
  border-bottom: 1px solid #eee;
  top: 0;
}

.CodeMirror-dialog-bottom {
  border-top: 1px solid #eee;
  bottom: 0;
}

.CodeMirror-dialog input {
  border: none;
  outline: none;
  background: transparent;
  width: 20em;
  color: inherit;
  font-family: monospace;
}

.CodeMirror-dialog button {
  font-size: 70%;
}

.CodeMirror-foldmarker {
  color: blue;
  text-shadow: #b9f 1px 1px 2px, #b9f -1px -1px 2px, #b9f 1px -1px 2px, #b9f -1px 1px 2px;
  font-family: arial;
  line-height: .3;
  cursor: pointer;
}
.CodeMirror-foldgutter {
  width: .7em;
}
.CodeMirror-foldgutter-open,
.CodeMirror-foldgutter-folded {
  cursor: pointer;
}
.CodeMirror-foldgutter-open:after {
  content: "\25BE";
}
.CodeMirror-foldgutter-folded:after {
  content: "\25B8";
}

/*
  Name:       material
  Author:     Mattia Astorino (http://github.com/equinusocio)
  Website:    https://material-theme.site/
*/

.cm-s-material.CodeMirror {
  background-color: #263238;
  color: #EEFFFF;
}

.cm-s-material .CodeMirror-gutters {
  background: #263238;
  color: #546E7A;
  border: none;
}

.cm-s-material .CodeMirror-guttermarker,
.cm-s-material .CodeMirror-guttermarker-subtle,
.cm-s-material .CodeMirror-linenumber {
  color: #546E7A;
}

.cm-s-material .CodeMirror-cursor {
  border-left: 1px solid #FFCC00;
}

.cm-s-material div.CodeMirror-selected {
  background: rgba(128, 203, 196, 0.2);
}

.cm-s-material.CodeMirror-focused div.CodeMirror-selected {
  background: rgba(128, 203, 196, 0.2);
}

.cm-s-material .CodeMirror-line::selection,
.cm-s-material .CodeMirror-line>span::selection,
.cm-s-material .CodeMirror-line>span>span::selection {
  background: rgba(128, 203, 196, 0.2);
}

.cm-s-material .CodeMirror-line::-moz-selection,
.cm-s-material .CodeMirror-line>span::-moz-selection,
.cm-s-material .CodeMirror-line>span>span::-moz-selection {
  background: rgba(128, 203, 196, 0.2);
}

.cm-s-material .CodeMirror-activeline-background {
  background: rgba(0, 0, 0, 0.5);
}

.cm-s-material .cm-keyword {
  color: #C792EA;
}

.cm-s-material .cm-operator {
  color: #89DDFF;
}

.cm-s-material .cm-variable-2 {
  color: #EEFFFF;
}

.cm-s-material .cm-variable-3,
.cm-s-material .cm-type {
  color: #f07178;
}

.cm-s-material .cm-builtin {
  color: #FFCB6B;
}

.cm-s-material .cm-atom {
  color: #F78C6C;
}

.cm-s-material .cm-number {
  color: #FF5370;
}

.cm-s-material .cm-def {
  color: #82AAFF;
}

.cm-s-material .cm-string {
  color: #C3E88D;
}

.cm-s-material .cm-string-2 {
  color: #f07178;
}

.cm-s-material .cm-comment {
  color: #546E7A;
}

.cm-s-material .cm-variable {
  color: #f07178;
}

.cm-s-material .cm-tag {
  color: #FF5370;
}

.cm-s-material .cm-meta {
  color: #FFCB6B;
}

.cm-s-material .cm-attribute {
  color: #C792EA;
}

.cm-s-material .cm-property {
  color: #C792EA;
}

.cm-s-material .cm-qualifier {
  color: #DECB6B;
}

.cm-s-material .cm-variable-3,
.cm-s-material .cm-type {
  color: #DECB6B;
}


.cm-s-material .cm-error {
  color: rgba(255, 255, 255, 1.0);
  background-color: #FF5370;
}

.cm-s-material .CodeMirror-matchingbracket {
  text-decoration: underline;
  color: white !important;
}
/**
 * "
 *  Using Zenburn color palette from the Emacs Zenburn Theme
 *  https://github.com/bbatsov/zenburn-emacs/blob/master/zenburn-theme.el
 *
 *  Also using parts of https://github.com/xavi/coderay-lighttable-theme
 * "
 * From: https://github.com/wisenomad/zenburn-lighttable-theme/blob/master/zenburn.css
 */

.cm-s-zenburn .CodeMirror-gutters { background: #3f3f3f !important; }
.cm-s-zenburn .CodeMirror-foldgutter-open, .CodeMirror-foldgutter-folded { color: #999; }
.cm-s-zenburn .CodeMirror-cursor { border-left: 1px solid white; }
.cm-s-zenburn { background-color: #3f3f3f; color: #dcdccc; }
.cm-s-zenburn span.cm-builtin { color: #dcdccc; font-weight: bold; }
.cm-s-zenburn span.cm-comment { color: #7f9f7f; }
.cm-s-zenburn span.cm-keyword { color: #f0dfaf; font-weight: bold; }
.cm-s-zenburn span.cm-atom { color: #bfebbf; }
.cm-s-zenburn span.cm-def { color: #dcdccc; }
.cm-s-zenburn span.cm-variable { color: #dfaf8f; }
.cm-s-zenburn span.cm-variable-2 { color: #dcdccc; }
.cm-s-zenburn span.cm-string { color: #cc9393; }
.cm-s-zenburn span.cm-string-2 { color: #cc9393; }
.cm-s-zenburn span.cm-number { color: #dcdccc; }
.cm-s-zenburn span.cm-tag { color: #93e0e3; }
.cm-s-zenburn span.cm-property { color: #dfaf8f; }
.cm-s-zenburn span.cm-attribute { color: #dfaf8f; }
.cm-s-zenburn span.cm-qualifier { color: #7cb8bb; }
.cm-s-zenburn span.cm-meta { color: #f0dfaf; }
.cm-s-zenburn span.cm-header { color: #f0efd0; }
.cm-s-zenburn span.cm-operator { color: #f0efd0; }
.cm-s-zenburn span.CodeMirror-matchingbracket { box-sizing: border-box; background: transparent; border-bottom: 1px solid; }
.cm-s-zenburn span.CodeMirror-nonmatchingbracket { border-bottom: 1px solid; background: none; }
.cm-s-zenburn .CodeMirror-activeline { background: #000000; }
.cm-s-zenburn .CodeMirror-activeline-background { background: #000000; }
.cm-s-zenburn div.CodeMirror-selected { background: #545454; }
.cm-s-zenburn .CodeMirror-focused div.CodeMirror-selected { background: #4f4f4f; }

.cm-s-abcdef.CodeMirror { background: #0f0f0f; color: #defdef; }
.cm-s-abcdef div.CodeMirror-selected { background: #515151; }
.cm-s-abcdef .CodeMirror-line::selection, .cm-s-abcdef .CodeMirror-line > span::selection, .cm-s-abcdef .CodeMirror-line > span > span::selection { background: rgba(56, 56, 56, 0.99); }
.cm-s-abcdef .CodeMirror-line::-moz-selection, .cm-s-abcdef .CodeMirror-line > span::-moz-selection, .cm-s-abcdef .CodeMirror-line > span > span::-moz-selection { background: rgba(56, 56, 56, 0.99); }
.cm-s-abcdef .CodeMirror-gutters { background: #555; border-right: 2px solid #314151; }
.cm-s-abcdef .CodeMirror-guttermarker { color: #222; }
.cm-s-abcdef .CodeMirror-guttermarker-subtle { color: azure; }
.cm-s-abcdef .CodeMirror-linenumber { color: #FFFFFF; }
.cm-s-abcdef .CodeMirror-cursor { border-left: 1px solid #00FF00; }

.cm-s-abcdef span.cm-keyword { color: darkgoldenrod; font-weight: bold; }
.cm-s-abcdef span.cm-atom { color: #77F; }
.cm-s-abcdef span.cm-number { color: violet; }
.cm-s-abcdef span.cm-def { color: #fffabc; }
.cm-s-abcdef span.cm-variable { color: #abcdef; }
.cm-s-abcdef span.cm-variable-2 { color: #cacbcc; }
.cm-s-abcdef span.cm-variable-3, .cm-s-abcdef span.cm-type { color: #def; }
.cm-s-abcdef span.cm-property { color: #fedcba; }
.cm-s-abcdef span.cm-operator { color: #ff0; }
.cm-s-abcdef span.cm-comment { color: #7a7b7c; font-style: italic;}
.cm-s-abcdef span.cm-string { color: #2b4; }
.cm-s-abcdef span.cm-meta { color: #C9F; }
.cm-s-abcdef span.cm-qualifier { color: #FFF700; }
.cm-s-abcdef span.cm-builtin { color: #30aabc; }
.cm-s-abcdef span.cm-bracket { color: #8a8a8a; }
.cm-s-abcdef span.cm-tag { color: #FFDD44; }
.cm-s-abcdef span.cm-attribute { color: #DDFF00; }
.cm-s-abcdef span.cm-error { color: #FF0000; }
.cm-s-abcdef span.cm-header { color: aquamarine; font-weight: bold; }
.cm-s-abcdef span.cm-link { color: blueviolet; }

.cm-s-abcdef .CodeMirror-activeline-background { background: #314151; }

/*

    Name:       Base16 Default Light
    Author:     Chris Kempson (http://chriskempson.com)

    CodeMirror template by Jan T. Sott (https://github.com/idleberg/base16-codemirror)
    Original Base16 color scheme by Chris Kempson (https://github.com/chriskempson/base16)

*/

.cm-s-base16-light.CodeMirror { background: #f5f5f5; color: #202020; }
.cm-s-base16-light div.CodeMirror-selected { background: #e0e0e0; }
.cm-s-base16-light .CodeMirror-line::selection, .cm-s-base16-light .CodeMirror-line > span::selection, .cm-s-base16-light .CodeMirror-line > span > span::selection { background: #e0e0e0; }
.cm-s-base16-light .CodeMirror-line::-moz-selection, .cm-s-base16-light .CodeMirror-line > span::-moz-selection, .cm-s-base16-light .CodeMirror-line > span > span::-moz-selection { background: #e0e0e0; }
.cm-s-base16-light .CodeMirror-gutters { background: #f5f5f5; border-right: 0px; }
.cm-s-base16-light .CodeMirror-guttermarker { color: #ac4142; }
.cm-s-base16-light .CodeMirror-guttermarker-subtle { color: #b0b0b0; }
.cm-s-base16-light .CodeMirror-linenumber { color: #b0b0b0; }
.cm-s-base16-light .CodeMirror-cursor { border-left: 1px solid #505050; }

.cm-s-base16-light span.cm-comment { color: #8f5536; }
.cm-s-base16-light span.cm-atom { color: #aa759f; }
.cm-s-base16-light span.cm-number { color: #aa759f; }

.cm-s-base16-light span.cm-property, .cm-s-base16-light span.cm-attribute { color: #90a959; }
.cm-s-base16-light span.cm-keyword { color: #ac4142; }
.cm-s-base16-light span.cm-string { color: #f4bf75; }

.cm-s-base16-light span.cm-variable { color: #90a959; }
.cm-s-base16-light span.cm-variable-2 { color: #6a9fb5; }
.cm-s-base16-light span.cm-def { color: #d28445; }
.cm-s-base16-light span.cm-bracket { color: #202020; }
.cm-s-base16-light span.cm-tag { color: #ac4142; }
.cm-s-base16-light span.cm-link { color: #aa759f; }
.cm-s-base16-light span.cm-error { background: #ac4142; color: #505050; }

.cm-s-base16-light .CodeMirror-activeline-background { background: #DDDCDC; }
.cm-s-base16-light .CodeMirror-matchingbracket { color: #f5f5f5 !important; background-color: #6A9FB5 !important}

/*

    Name:       Base16 Default Dark
    Author:     Chris Kempson (http://chriskempson.com)

    CodeMirror template by Jan T. Sott (https://github.com/idleberg/base16-codemirror)
    Original Base16 color scheme by Chris Kempson (https://github.com/chriskempson/base16)

*/

.cm-s-base16-dark.CodeMirror { background: #151515; color: #e0e0e0; }
.cm-s-base16-dark div.CodeMirror-selected { background: #303030; }
.cm-s-base16-dark .CodeMirror-line::selection, .cm-s-base16-dark .CodeMirror-line > span::selection, .cm-s-base16-dark .CodeMirror-line > span > span::selection { background: rgba(48, 48, 48, .99); }
.cm-s-base16-dark .CodeMirror-line::-moz-selection, .cm-s-base16-dark .CodeMirror-line > span::-moz-selection, .cm-s-base16-dark .CodeMirror-line > span > span::-moz-selection { background: rgba(48, 48, 48, .99); }
.cm-s-base16-dark .CodeMirror-gutters { background: #151515; border-right: 0px; }
.cm-s-base16-dark .CodeMirror-guttermarker { color: #ac4142; }
.cm-s-base16-dark .CodeMirror-guttermarker-subtle { color: #505050; }
.cm-s-base16-dark .CodeMirror-linenumber { color: #505050; }
.cm-s-base16-dark .CodeMirror-cursor { border-left: 1px solid #b0b0b0; }

.cm-s-base16-dark span.cm-comment { color: #8f5536; }
.cm-s-base16-dark span.cm-atom { color: #aa759f; }
.cm-s-base16-dark span.cm-number { color: #aa759f; }

.cm-s-base16-dark span.cm-property, .cm-s-base16-dark span.cm-attribute { color: #90a959; }
.cm-s-base16-dark span.cm-keyword { color: #ac4142; }
.cm-s-base16-dark span.cm-string { color: #f4bf75; }

.cm-s-base16-dark span.cm-variable { color: #90a959; }
.cm-s-base16-dark span.cm-variable-2 { color: #6a9fb5; }
.cm-s-base16-dark span.cm-def { color: #d28445; }
.cm-s-base16-dark span.cm-bracket { color: #e0e0e0; }
.cm-s-base16-dark span.cm-tag { color: #ac4142; }
.cm-s-base16-dark span.cm-link { color: #aa759f; }
.cm-s-base16-dark span.cm-error { background: #ac4142; color: #b0b0b0; }

.cm-s-base16-dark .CodeMirror-activeline-background { background: #202020; }
.cm-s-base16-dark .CodeMirror-matchingbracket { text-decoration: underline; color: white !important; }

/*

    Name:       dracula
    Author:     Michael Kaminsky (http://github.com/mkaminsky11)

    Original dracula color scheme by Zeno Rocha (https://github.com/zenorocha/dracula-theme)

*/


.cm-s-dracula.CodeMirror, .cm-s-dracula .CodeMirror-gutters {
  background-color: #282a36 !important;
  color: #f8f8f2 !important;
  border: none;
}
.cm-s-dracula .CodeMirror-gutters { color: #282a36; }
.cm-s-dracula .CodeMirror-cursor { border-left: solid thin #f8f8f0; }
.cm-s-dracula .CodeMirror-linenumber { color: #6D8A88; }
.cm-s-dracula .CodeMirror-selected { background: rgba(255, 255, 255, 0.10); }
.cm-s-dracula .CodeMirror-line::selection, .cm-s-dracula .CodeMirror-line > span::selection, .cm-s-dracula .CodeMirror-line > span > span::selection { background: rgba(255, 255, 255, 0.10); }
.cm-s-dracula .CodeMirror-line::-moz-selection, .cm-s-dracula .CodeMirror-line > span::-moz-selection, .cm-s-dracula .CodeMirror-line > span > span::-moz-selection { background: rgba(255, 255, 255, 0.10); }
.cm-s-dracula span.cm-comment { color: #6272a4; }
.cm-s-dracula span.cm-string, .cm-s-dracula span.cm-string-2 { color: #f1fa8c; }
.cm-s-dracula span.cm-number { color: #bd93f9; }
.cm-s-dracula span.cm-variable { color: #50fa7b; }
.cm-s-dracula span.cm-variable-2 { color: white; }
.cm-s-dracula span.cm-def { color: #50fa7b; }
.cm-s-dracula span.cm-operator { color: #ff79c6; }
.cm-s-dracula span.cm-keyword { color: #ff79c6; }
.cm-s-dracula span.cm-atom { color: #bd93f9; }
.cm-s-dracula span.cm-meta { color: #f8f8f2; }
.cm-s-dracula span.cm-tag { color: #ff79c6; }
.cm-s-dracula span.cm-attribute { color: #50fa7b; }
.cm-s-dracula span.cm-qualifier { color: #50fa7b; }
.cm-s-dracula span.cm-property { color: #66d9ef; }
.cm-s-dracula span.cm-builtin { color: #50fa7b; }
.cm-s-dracula span.cm-variable-3, .cm-s-dracula span.cm-type { color: #ffb86c; }

.cm-s-dracula .CodeMirror-activeline-background { background: rgba(255,255,255,0.1); }
.cm-s-dracula .CodeMirror-matchingbracket { text-decoration: underline; color: white !important; }

/*

    Name:       Hopscotch
    Author:     Jan T. Sott

    CodeMirror template by Jan T. Sott (https://github.com/idleberg/base16-codemirror)
    Original Base16 color scheme by Chris Kempson (https://github.com/chriskempson/base16)

*/

.cm-s-hopscotch.CodeMirror {background: #322931; color: #d5d3d5;}
.cm-s-hopscotch div.CodeMirror-selected {background: #433b42 !important;}
.cm-s-hopscotch .CodeMirror-gutters {background: #322931; border-right: 0px;}
.cm-s-hopscotch .CodeMirror-linenumber {color: #797379;}
.cm-s-hopscotch .CodeMirror-cursor {border-left: 1px solid #989498 !important;}

.cm-s-hopscotch span.cm-comment {color: #b33508;}
.cm-s-hopscotch span.cm-atom {color: #c85e7c;}
.cm-s-hopscotch span.cm-number {color: #c85e7c;}

.cm-s-hopscotch span.cm-property, .cm-s-hopscotch span.cm-attribute {color: #8fc13e;}
.cm-s-hopscotch span.cm-keyword {color: #dd464c;}
.cm-s-hopscotch span.cm-string {color: #fdcc59;}

.cm-s-hopscotch span.cm-variable {color: #8fc13e;}
.cm-s-hopscotch span.cm-variable-2 {color: #1290bf;}
.cm-s-hopscotch span.cm-def {color: #fd8b19;}
.cm-s-hopscotch span.cm-error {background: #dd464c; color: #989498;}
.cm-s-hopscotch span.cm-bracket {color: #d5d3d5;}
.cm-s-hopscotch span.cm-tag {color: #dd464c;}
.cm-s-hopscotch span.cm-link {color: #c85e7c;}

.cm-s-hopscotch .CodeMirror-matchingbracket { text-decoration: underline; color: white !important;}
.cm-s-hopscotch .CodeMirror-activeline-background { background: #302020; }

/****************************************************************/
/*   Based on mbonaci's Brackets mbo theme                      */
/*   https://github.com/mbonaci/global/blob/master/Mbo.tmTheme  */
/*   Create your own: http://tmtheme-editor.herokuapp.com       */
/****************************************************************/

.cm-s-mbo.CodeMirror { background: #2c2c2c; color: #ffffec; }
.cm-s-mbo div.CodeMirror-selected { background: #716C62; }
.cm-s-mbo .CodeMirror-line::selection, .cm-s-mbo .CodeMirror-line > span::selection, .cm-s-mbo .CodeMirror-line > span > span::selection { background: rgba(113, 108, 98, .99); }
.cm-s-mbo .CodeMirror-line::-moz-selection, .cm-s-mbo .CodeMirror-line > span::-moz-selection, .cm-s-mbo .CodeMirror-line > span > span::-moz-selection { background: rgba(113, 108, 98, .99); }
.cm-s-mbo .CodeMirror-gutters { background: #4e4e4e; border-right: 0px; }
.cm-s-mbo .CodeMirror-guttermarker { color: white; }
.cm-s-mbo .CodeMirror-guttermarker-subtle { color: grey; }
.cm-s-mbo .CodeMirror-linenumber { color: #dadada; }
.cm-s-mbo .CodeMirror-cursor { border-left: 1px solid #ffffec; }

.cm-s-mbo span.cm-comment { color: #95958a; }
.cm-s-mbo span.cm-atom { color: #00a8c6; }
.cm-s-mbo span.cm-number { color: #00a8c6; }

.cm-s-mbo span.cm-property, .cm-s-mbo span.cm-attribute { color: #9ddfe9; }
.cm-s-mbo span.cm-keyword { color: #ffb928; }
.cm-s-mbo span.cm-string { color: #ffcf6c; }
.cm-s-mbo span.cm-string.cm-property { color: #ffffec; }

.cm-s-mbo span.cm-variable { color: #ffffec; }
.cm-s-mbo span.cm-variable-2 { color: #00a8c6; }
.cm-s-mbo span.cm-def { color: #ffffec; }
.cm-s-mbo span.cm-bracket { color: #fffffc; font-weight: bold; }
.cm-s-mbo span.cm-tag { color: #9ddfe9; }
.cm-s-mbo span.cm-link { color: #f54b07; }
.cm-s-mbo span.cm-error { border-bottom: #636363; color: #ffffec; }
.cm-s-mbo span.cm-qualifier { color: #ffffec; }

.cm-s-mbo .CodeMirror-activeline-background { background: #494b41; }
.cm-s-mbo .CodeMirror-matchingbracket { color: #ffb928 !important; }
.cm-s-mbo .CodeMirror-matchingtag { background: rgba(255, 255, 255, .37); }

/*
  MDN-LIKE Theme - Mozilla
  Ported to CodeMirror by Peter Kroon <plakroon@gmail.com>
  Report bugs/issues here: https://github.com/codemirror/CodeMirror/issues
  GitHub: @peterkroon

  The mdn-like theme is inspired on the displayed code examples at: https://developer.mozilla.org/en-US/docs/Web/CSS/animation

*/
.cm-s-mdn-like.CodeMirror { color: #999; background-color: #fff; }
.cm-s-mdn-like div.CodeMirror-selected { background: #cfc; }
.cm-s-mdn-like .CodeMirror-line::selection, .cm-s-mdn-like .CodeMirror-line > span::selection, .cm-s-mdn-like .CodeMirror-line > span > span::selection { background: #cfc; }
.cm-s-mdn-like .CodeMirror-line::-moz-selection, .cm-s-mdn-like .CodeMirror-line > span::-moz-selection, .cm-s-mdn-like .CodeMirror-line > span > span::-moz-selection { background: #cfc; }

.cm-s-mdn-like .CodeMirror-gutters { background: #f8f8f8; border-left: 6px solid rgba(0,83,159,0.65); color: #333; }
.cm-s-mdn-like .CodeMirror-linenumber { color: #aaa; padding-left: 8px; }
.cm-s-mdn-like .CodeMirror-cursor { border-left: 2px solid #222; }

.cm-s-mdn-like .cm-keyword { color: #6262FF; }
.cm-s-mdn-like .cm-atom { color: #F90; }
.cm-s-mdn-like .cm-number { color:  #ca7841; }
.cm-s-mdn-like .cm-def { color: #8DA6CE; }
.cm-s-mdn-like span.cm-variable-2, .cm-s-mdn-like span.cm-tag { color: #690; }
.cm-s-mdn-like span.cm-variable-3, .cm-s-mdn-like span.cm-def, .cm-s-mdn-like span.cm-type { color: #07a; }

.cm-s-mdn-like .cm-variable { color: #07a; }
.cm-s-mdn-like .cm-property { color: #905; }
.cm-s-mdn-like .cm-qualifier { color: #690; }

.cm-s-mdn-like .cm-operator { color: #cda869; }
.cm-s-mdn-like .cm-comment { color:#777; font-weight:normal; }
.cm-s-mdn-like .cm-string { color:#07a; font-style:italic; }
.cm-s-mdn-like .cm-string-2 { color:#bd6b18; } /*?*/
.cm-s-mdn-like .cm-meta { color: #000; } /*?*/
.cm-s-mdn-like .cm-builtin { color: #9B7536; } /*?*/
.cm-s-mdn-like .cm-tag { color: #997643; }
.cm-s-mdn-like .cm-attribute { color: #d6bb6d; } /*?*/
.cm-s-mdn-like .cm-header { color: #FF6400; }
.cm-s-mdn-like .cm-hr { color: #AEAEAE; }
.cm-s-mdn-like .cm-link { color:#ad9361; font-style:italic; text-decoration:none; }
.cm-s-mdn-like .cm-error { border-bottom: 1px solid red; }

div.cm-s-mdn-like .CodeMirror-activeline-background { background: #efefff; }
div.cm-s-mdn-like span.CodeMirror-matchingbracket { outline:1px solid grey; color: inherit; }

.cm-s-mdn-like.CodeMirror { background-image: url(data:image/png;base64,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); }

/*

    Name:       seti
    Author:     Michael Kaminsky (http://github.com/mkaminsky11)

    Original seti color scheme by Jesse Weed (https://github.com/jesseweed/seti-syntax)

*/


.cm-s-seti.CodeMirror {
  background-color: #151718 !important;
  color: #CFD2D1 !important;
  border: none;
}
.cm-s-seti .CodeMirror-gutters {
  color: #404b53;
  background-color: #0E1112;
  border: none;
}
.cm-s-seti .CodeMirror-cursor { border-left: solid thin #f8f8f0; }
.cm-s-seti .CodeMirror-linenumber { color: #6D8A88; }
.cm-s-seti.CodeMirror-focused div.CodeMirror-selected { background: rgba(255, 255, 255, 0.10); }
.cm-s-seti .CodeMirror-line::selection, .cm-s-seti .CodeMirror-line > span::selection, .cm-s-seti .CodeMirror-line > span > span::selection { background: rgba(255, 255, 255, 0.10); }
.cm-s-seti .CodeMirror-line::-moz-selection, .cm-s-seti .CodeMirror-line > span::-moz-selection, .cm-s-seti .CodeMirror-line > span > span::-moz-selection { background: rgba(255, 255, 255, 0.10); }
.cm-s-seti span.cm-comment { color: #41535b; }
.cm-s-seti span.cm-string, .cm-s-seti span.cm-string-2 { color: #55b5db; }
.cm-s-seti span.cm-number { color: #cd3f45; }
.cm-s-seti span.cm-variable { color: #55b5db; }
.cm-s-seti span.cm-variable-2 { color: #a074c4; }
.cm-s-seti span.cm-def { color: #55b5db; }
.cm-s-seti span.cm-keyword { color: #ff79c6; }
.cm-s-seti span.cm-operator { color: #9fca56; }
.cm-s-seti span.cm-keyword { color: #e6cd69; }
.cm-s-seti span.cm-atom { color: #cd3f45; }
.cm-s-seti span.cm-meta { color: #55b5db; }
.cm-s-seti span.cm-tag { color: #55b5db; }
.cm-s-seti span.cm-attribute { color: #9fca56; }
.cm-s-seti span.cm-qualifier { color: #9fca56; }
.cm-s-seti span.cm-property { color: #a074c4; }
.cm-s-seti span.cm-variable-3, .cm-s-seti span.cm-type { color: #9fca56; }
.cm-s-seti span.cm-builtin { color: #9fca56; }
.cm-s-seti .CodeMirror-activeline-background { background: #101213; }
.cm-s-seti .CodeMirror-matchingbracket { text-decoration: underline; color: white !important; }

/*
Solarized theme for code-mirror
http://ethanschoonover.com/solarized
*/

/*
Solarized color palette
http://ethanschoonover.com/solarized/img/solarized-palette.png
*/

.solarized.base03 { color: #002b36; }
.solarized.base02 { color: #073642; }
.solarized.base01 { color: #586e75; }
.solarized.base00 { color: #657b83; }
.solarized.base0 { color: #839496; }
.solarized.base1 { color: #93a1a1; }
.solarized.base2 { color: #eee8d5; }
.solarized.base3  { color: #fdf6e3; }
.solarized.solar-yellow  { color: #b58900; }
.solarized.solar-orange  { color: #cb4b16; }
.solarized.solar-red { color: #dc322f; }
.solarized.solar-magenta { color: #d33682; }
.solarized.solar-violet  { color: #6c71c4; }
.solarized.solar-blue { color: #268bd2; }
.solarized.solar-cyan { color: #2aa198; }
.solarized.solar-green { color: #859900; }

/* Color scheme for code-mirror */

.cm-s-solarized {
  line-height: 1.45em;
  color-profile: sRGB;
  rendering-intent: auto;
}
.cm-s-solarized.cm-s-dark {
  color: #839496;
  background-color: #002b36;
  text-shadow: #002b36 0 1px;
}
.cm-s-solarized.cm-s-light {
  background-color: #fdf6e3;
  color: #657b83;
  text-shadow: #eee8d5 0 1px;
}

.cm-s-solarized .CodeMirror-widget {
  text-shadow: none;
}

.cm-s-solarized .cm-header { color: #586e75; }
.cm-s-solarized .cm-quote { color: #93a1a1; }

.cm-s-solarized .cm-keyword { color: #cb4b16; }
.cm-s-solarized .cm-atom { color: #d33682; }
.cm-s-solarized .cm-number { color: #d33682; }
.cm-s-solarized .cm-def { color: #2aa198; }

.cm-s-solarized .cm-variable { color: #839496; }
.cm-s-solarized .cm-variable-2 { color: #b58900; }
.cm-s-solarized .cm-variable-3, .cm-s-solarized .cm-type { color: #6c71c4; }

.cm-s-solarized .cm-property { color: #2aa198; }
.cm-s-solarized .cm-operator { color: #6c71c4; }

.cm-s-solarized .cm-comment { color: #586e75; font-style:italic; }

.cm-s-solarized .cm-string { color: #859900; }
.cm-s-solarized .cm-string-2 { color: #b58900; }

.cm-s-solarized .cm-meta { color: #859900; }
.cm-s-solarized .cm-qualifier { color: #b58900; }
.cm-s-solarized .cm-builtin { color: #d33682; }
.cm-s-solarized .cm-bracket { color: #cb4b16; }
.cm-s-solarized .CodeMirror-matchingbracket { color: #859900; }
.cm-s-solarized .CodeMirror-nonmatchingbracket { color: #dc322f; }
.cm-s-solarized .cm-tag { color: #93a1a1; }
.cm-s-solarized .cm-attribute { color: #2aa198; }
.cm-s-solarized .cm-hr {
  color: transparent;
  border-top: 1px solid #586e75;
  display: block;
}
.cm-s-solarized .cm-link { color: #93a1a1; cursor: pointer; }
.cm-s-solarized .cm-special { color: #6c71c4; }
.cm-s-solarized .cm-em {
  color: #999;
  text-decoration: underline;
  text-decoration-style: dotted;
}
.cm-s-solarized .cm-error,
.cm-s-solarized .cm-invalidchar {
  color: #586e75;
  border-bottom: 1px dotted #dc322f;
}

.cm-s-solarized.cm-s-dark div.CodeMirror-selected { background: #073642; }
.cm-s-solarized.cm-s-dark.CodeMirror ::selection { background: rgba(7, 54, 66, 0.99); }
.cm-s-solarized.cm-s-dark .CodeMirror-line::-moz-selection, .cm-s-dark .CodeMirror-line > span::-moz-selection, .cm-s-dark .CodeMirror-line > span > span::-moz-selection { background: rgba(7, 54, 66, 0.99); }

.cm-s-solarized.cm-s-light div.CodeMirror-selected { background: #eee8d5; }
.cm-s-solarized.cm-s-light .CodeMirror-line::selection, .cm-s-light .CodeMirror-line > span::selection, .cm-s-light .CodeMirror-line > span > span::selection { background: #eee8d5; }
.cm-s-solarized.cm-s-light .CodeMirror-line::-moz-selection, .cm-s-ligh .CodeMirror-line > span::-moz-selection, .cm-s-ligh .CodeMirror-line > span > span::-moz-selection { background: #eee8d5; }

/* Editor styling */



/* Little shadow on the view-port of the buffer view */
.cm-s-solarized.CodeMirror {
  -moz-box-shadow: inset 7px 0 12px -6px #000;
  -webkit-box-shadow: inset 7px 0 12px -6px #000;
  box-shadow: inset 7px 0 12px -6px #000;
}

/* Remove gutter border */
.cm-s-solarized .CodeMirror-gutters {
  border-right: 0;
}

/* Gutter colors and line number styling based of color scheme (dark / light) */

/* Dark */
.cm-s-solarized.cm-s-dark .CodeMirror-gutters {
  background-color: #073642;
}

.cm-s-solarized.cm-s-dark .CodeMirror-linenumber {
  color: #586e75;
  text-shadow: #021014 0 -1px;
}

/* Light */
.cm-s-solarized.cm-s-light .CodeMirror-gutters {
  background-color: #eee8d5;
}

.cm-s-solarized.cm-s-light .CodeMirror-linenumber {
  color: #839496;
}

/* Common */
.cm-s-solarized .CodeMirror-linenumber {
  padding: 0 5px;
}
.cm-s-solarized .CodeMirror-guttermarker-subtle { color: #586e75; }
.cm-s-solarized.cm-s-dark .CodeMirror-guttermarker { color: #ddd; }
.cm-s-solarized.cm-s-light .CodeMirror-guttermarker { color: #cb4b16; }

.cm-s-solarized .CodeMirror-gutter .CodeMirror-gutter-text {
  color: #586e75;
}

/* Cursor */
.cm-s-solarized .CodeMirror-cursor { border-left: 1px solid #819090; }

/* Fat cursor */
.cm-s-solarized.cm-s-light.cm-fat-cursor .CodeMirror-cursor { background: #77ee77; }
.cm-s-solarized.cm-s-light .cm-animate-fat-cursor { background-color: #77ee77; }
.cm-s-solarized.cm-s-dark.cm-fat-cursor .CodeMirror-cursor { background: #586e75; }
.cm-s-solarized.cm-s-dark .cm-animate-fat-cursor { background-color: #586e75; }

/* Active line */
.cm-s-solarized.cm-s-dark .CodeMirror-activeline-background {
  background: rgba(255, 255, 255, 0.06);
}
.cm-s-solarized.cm-s-light .CodeMirror-activeline-background {
  background: rgba(0, 0, 0, 0.06);
}

.cm-s-the-matrix.CodeMirror { background: #000000; color: #00FF00; }
.cm-s-the-matrix div.CodeMirror-selected { background: #2D2D2D; }
.cm-s-the-matrix .CodeMirror-line::selection, .cm-s-the-matrix .CodeMirror-line > span::selection, .cm-s-the-matrix .CodeMirror-line > span > span::selection { background: rgba(45, 45, 45, 0.99); }
.cm-s-the-matrix .CodeMirror-line::-moz-selection, .cm-s-the-matrix .CodeMirror-line > span::-moz-selection, .cm-s-the-matrix .CodeMirror-line > span > span::-moz-selection { background: rgba(45, 45, 45, 0.99); }
.cm-s-the-matrix .CodeMirror-gutters { background: #060; border-right: 2px solid #00FF00; }
.cm-s-the-matrix .CodeMirror-guttermarker { color: #0f0; }
.cm-s-the-matrix .CodeMirror-guttermarker-subtle { color: white; }
.cm-s-the-matrix .CodeMirror-linenumber { color: #FFFFFF; }
.cm-s-the-matrix .CodeMirror-cursor { border-left: 1px solid #00FF00; }

.cm-s-the-matrix span.cm-keyword { color: #008803; font-weight: bold; }
.cm-s-the-matrix span.cm-atom { color: #3FF; }
.cm-s-the-matrix span.cm-number { color: #FFB94F; }
.cm-s-the-matrix span.cm-def { color: #99C; }
.cm-s-the-matrix span.cm-variable { color: #F6C; }
.cm-s-the-matrix span.cm-variable-2 { color: #C6F; }
.cm-s-the-matrix span.cm-variable-3, .cm-s-the-matrix span.cm-type { color: #96F; }
.cm-s-the-matrix span.cm-property { color: #62FFA0; }
.cm-s-the-matrix span.cm-operator { color: #999; }
.cm-s-the-matrix span.cm-comment { color: #CCCCCC; }
.cm-s-the-matrix span.cm-string { color: #39C; }
.cm-s-the-matrix span.cm-meta { color: #C9F; }
.cm-s-the-matrix span.cm-qualifier { color: #FFF700; }
.cm-s-the-matrix span.cm-builtin { color: #30a; }
.cm-s-the-matrix span.cm-bracket { color: #cc7; }
.cm-s-the-matrix span.cm-tag { color: #FFBD40; }
.cm-s-the-matrix span.cm-attribute { color: #FFF700; }
.cm-s-the-matrix span.cm-error { color: #FF0000; }

.cm-s-the-matrix .CodeMirror-activeline-background { background: #040; }

/*
Copyright (C) 2011 by MarkLogic Corporation
Author: Mike Brevoort <mike@brevoort.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
*/
.cm-s-xq-light span.cm-keyword { line-height: 1em; font-weight: bold; color: #5A5CAD; }
.cm-s-xq-light span.cm-atom { color: #6C8CD5; }
.cm-s-xq-light span.cm-number { color: #164; }
.cm-s-xq-light span.cm-def { text-decoration:underline; }
.cm-s-xq-light span.cm-variable { color: black; }
.cm-s-xq-light span.cm-variable-2 { color:black; }
.cm-s-xq-light span.cm-variable-3, .cm-s-xq-light span.cm-type { color: black; }
.cm-s-xq-light span.cm-property {}
.cm-s-xq-light span.cm-operator {}
.cm-s-xq-light span.cm-comment { color: #0080FF; font-style: italic; }
.cm-s-xq-light span.cm-string { color: red; }
.cm-s-xq-light span.cm-meta { color: yellow; }
.cm-s-xq-light span.cm-qualifier { color: grey; }
.cm-s-xq-light span.cm-builtin { color: #7EA656; }
.cm-s-xq-light span.cm-bracket { color: #cc7; }
.cm-s-xq-light span.cm-tag { color: #3F7F7F; }
.cm-s-xq-light span.cm-attribute { color: #7F007F; }
.cm-s-xq-light span.cm-error { color: #f00; }

.cm-s-xq-light .CodeMirror-activeline-background { background: #e8f2ff; }
.cm-s-xq-light .CodeMirror-matchingbracket { outline:1px solid grey;color:black !important;background:yellow; }

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.CodeMirror {
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  border: 0;
  border-radius: 0;
  height: auto;
  /* Changed to auto to autogrow */
}

.CodeMirror pre {
  padding: 0 var(--jp-code-padding);
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-dialog {
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* This causes https://github.com/jupyter/jupyterlab/issues/522 */
/* May not cause it not because we changed it! */
.CodeMirror-lines {
  padding: var(--jp-code-padding) 0;
}

.CodeMirror-linenumber {
  padding: 0 8px;
}

.jp-CodeMirrorEditor-static {
  margin: var(--jp-code-padding);
}

.jp-CodeMirrorEditor,
.jp-CodeMirrorEditor-static {
  cursor: text;
}

.jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}

/* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width1) solid
      var(--jp-editor-cursor-color);
  }
}

/* When zoomed out less than 33% */
@media screen and (min-width: 4320px) {
  .jp-CodeMirrorEditor[data-type='inline'] .CodeMirror-cursor {
    border-left: var(--jp-code-cursor-width2) solid
      var(--jp-editor-cursor-color);
  }
}

.CodeMirror.jp-mod-readOnly .CodeMirror-cursor {
  display: none;
}

.CodeMirror-gutters {
  border-right: 1px solid var(--jp-border-color2);
  background-color: var(--jp-layout-color0);
}

.jp-CollaboratorCursor {
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: none;
  border-bottom: 3px solid;
  background-clip: content-box;
  margin-left: -5px;
  margin-right: -5px;
}

.CodeMirror-selectedtext.cm-searching {
  background-color: var(--jp-search-selected-match-background-color) !important;
  color: var(--jp-search-selected-match-color) !important;
}

.cm-searching {
  background-color: var(
    --jp-search-unselected-match-background-color
  ) !important;
  color: var(--jp-search-unselected-match-color) !important;
}

.CodeMirror-focused .CodeMirror-selected {
  background-color: var(--jp-editor-selected-focused-background);
}

.CodeMirror-selected {
  background-color: var(--jp-editor-selected-background);
}

.jp-CollaboratorCursor-hover {
  position: absolute;
  z-index: 1;
  transform: translateX(-50%);
  color: white;
  border-radius: 3px;
  padding-left: 4px;
  padding-right: 4px;
  padding-top: 1px;
  padding-bottom: 1px;
  text-align: center;
  font-size: var(--jp-ui-font-size1);
  white-space: nowrap;
}

.jp-CodeMirror-ruler {
  border-left: 1px dashed var(--jp-border-color2);
}

/**
 * Here is our jupyter theme for CodeMirror syntax highlighting
 * This is used in our marked.js syntax highlighting and CodeMirror itself
 * The string "jupyter" is set in ../codemirror/widget.DEFAULT_CODEMIRROR_THEME
 * This came from the classic notebook, which came form highlight.js/GitHub
 */

/**
 * CodeMirror themes are handling the background/color in this way. This works
 * fine for CodeMirror editors outside the notebook, but the notebook styles
 * these things differently.
 */
.CodeMirror.cm-s-jupyter {
  background: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
}

/* In the notebook, we want this styling to be handled by its container */
.jp-CodeConsole .CodeMirror.cm-s-jupyter,
.jp-Notebook .CodeMirror.cm-s-jupyter {
  background: transparent;
}

.cm-s-jupyter .CodeMirror-cursor {
  border-left: var(--jp-code-cursor-width0) solid var(--jp-editor-cursor-color);
}
.cm-s-jupyter span.cm-keyword {
  color: var(--jp-mirror-editor-keyword-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-atom {
  color: var(--jp-mirror-editor-atom-color);
}
.cm-s-jupyter span.cm-number {
  color: var(--jp-mirror-editor-number-color);
}
.cm-s-jupyter span.cm-def {
  color: var(--jp-mirror-editor-def-color);
}
.cm-s-jupyter span.cm-variable {
  color: var(--jp-mirror-editor-variable-color);
}
.cm-s-jupyter span.cm-variable-2 {
  color: var(--jp-mirror-editor-variable-2-color);
}
.cm-s-jupyter span.cm-variable-3 {
  color: var(--jp-mirror-editor-variable-3-color);
}
.cm-s-jupyter span.cm-punctuation {
  color: var(--jp-mirror-editor-punctuation-color);
}
.cm-s-jupyter span.cm-property {
  color: var(--jp-mirror-editor-property-color);
}
.cm-s-jupyter span.cm-operator {
  color: var(--jp-mirror-editor-operator-color);
  font-weight: bold;
}
.cm-s-jupyter span.cm-comment {
  color: var(--jp-mirror-editor-comment-color);
  font-style: italic;
}
.cm-s-jupyter span.cm-string {
  color: var(--jp-mirror-editor-string-color);
}
.cm-s-jupyter span.cm-string-2 {
  color: var(--jp-mirror-editor-string-2-color);
}
.cm-s-jupyter span.cm-meta {
  color: var(--jp-mirror-editor-meta-color);
}
.cm-s-jupyter span.cm-qualifier {
  color: var(--jp-mirror-editor-qualifier-color);
}
.cm-s-jupyter span.cm-builtin {
  color: var(--jp-mirror-editor-builtin-color);
}
.cm-s-jupyter span.cm-bracket {
  color: var(--jp-mirror-editor-bracket-color);
}
.cm-s-jupyter span.cm-tag {
  color: var(--jp-mirror-editor-tag-color);
}
.cm-s-jupyter span.cm-attribute {
  color: var(--jp-mirror-editor-attribute-color);
}
.cm-s-jupyter span.cm-header {
  color: var(--jp-mirror-editor-header-color);
}
.cm-s-jupyter span.cm-quote {
  color: var(--jp-mirror-editor-quote-color);
}
.cm-s-jupyter span.cm-link {
  color: var(--jp-mirror-editor-link-color);
}
.cm-s-jupyter span.cm-error {
  color: var(--jp-mirror-editor-error-color);
}
.cm-s-jupyter span.cm-hr {
  color: #999;
}

.cm-s-jupyter span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}

.cm-s-jupyter .CodeMirror-activeline-background,
.cm-s-jupyter .CodeMirror-gutter {
  background-color: var(--jp-layout-color2);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| RenderedText
|----------------------------------------------------------------------------*/

.jp-RenderedText {
  text-align: left;
  padding-left: var(--jp-code-padding);
  line-height: var(--jp-code-line-height);
  font-family: var(--jp-code-font-family);
}

.jp-RenderedText pre,
.jp-RenderedJavaScript pre,
.jp-RenderedHTMLCommon pre {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-code-font-size);
  border: none;
  margin: 0px;
  padding: 0px;
  line-height: normal;
}

.jp-RenderedText pre a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}
.jp-RenderedText pre a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* console foregrounds and backgrounds */
.jp-RenderedText pre .ansi-black-fg {
  color: #3e424d;
}
.jp-RenderedText pre .ansi-red-fg {
  color: #e75c58;
}
.jp-RenderedText pre .ansi-green-fg {
  color: #00a250;
}
.jp-RenderedText pre .ansi-yellow-fg {
  color: #ddb62b;
}
.jp-RenderedText pre .ansi-blue-fg {
  color: #208ffb;
}
.jp-RenderedText pre .ansi-magenta-fg {
  color: #d160c4;
}
.jp-RenderedText pre .ansi-cyan-fg {
  color: #60c6c8;
}
.jp-RenderedText pre .ansi-white-fg {
  color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-bg {
  background-color: #3e424d;
}
.jp-RenderedText pre .ansi-red-bg {
  background-color: #e75c58;
}
.jp-RenderedText pre .ansi-green-bg {
  background-color: #00a250;
}
.jp-RenderedText pre .ansi-yellow-bg {
  background-color: #ddb62b;
}
.jp-RenderedText pre .ansi-blue-bg {
  background-color: #208ffb;
}
.jp-RenderedText pre .ansi-magenta-bg {
  background-color: #d160c4;
}
.jp-RenderedText pre .ansi-cyan-bg {
  background-color: #60c6c8;
}
.jp-RenderedText pre .ansi-white-bg {
  background-color: #c5c1b4;
}

.jp-RenderedText pre .ansi-black-intense-fg {
  color: #282c36;
}
.jp-RenderedText pre .ansi-red-intense-fg {
  color: #b22b31;
}
.jp-RenderedText pre .ansi-green-intense-fg {
  color: #007427;
}
.jp-RenderedText pre .ansi-yellow-intense-fg {
  color: #b27d12;
}
.jp-RenderedText pre .ansi-blue-intense-fg {
  color: #0065ca;
}
.jp-RenderedText pre .ansi-magenta-intense-fg {
  color: #a03196;
}
.jp-RenderedText pre .ansi-cyan-intense-fg {
  color: #258f8f;
}
.jp-RenderedText pre .ansi-white-intense-fg {
  color: #a1a6b2;
}

.jp-RenderedText pre .ansi-black-intense-bg {
  background-color: #282c36;
}
.jp-RenderedText pre .ansi-red-intense-bg {
  background-color: #b22b31;
}
.jp-RenderedText pre .ansi-green-intense-bg {
  background-color: #007427;
}
.jp-RenderedText pre .ansi-yellow-intense-bg {
  background-color: #b27d12;
}
.jp-RenderedText pre .ansi-blue-intense-bg {
  background-color: #0065ca;
}
.jp-RenderedText pre .ansi-magenta-intense-bg {
  background-color: #a03196;
}
.jp-RenderedText pre .ansi-cyan-intense-bg {
  background-color: #258f8f;
}
.jp-RenderedText pre .ansi-white-intense-bg {
  background-color: #a1a6b2;
}

.jp-RenderedText pre .ansi-default-inverse-fg {
  color: var(--jp-ui-inverse-font-color0);
}
.jp-RenderedText pre .ansi-default-inverse-bg {
  background-color: var(--jp-inverse-layout-color0);
}

.jp-RenderedText pre .ansi-bold {
  font-weight: bold;
}
.jp-RenderedText pre .ansi-underline {
  text-decoration: underline;
}

.jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
  background: var(--jp-rendermime-error-background);
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| RenderedLatex
|----------------------------------------------------------------------------*/

.jp-RenderedLatex {
  color: var(--jp-content-font-color1);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
}

/* Left-justify outputs.*/
.jp-OutputArea-output.jp-RenderedLatex {
  padding: var(--jp-code-padding);
  text-align: left;
}

/*-----------------------------------------------------------------------------
| RenderedHTML
|----------------------------------------------------------------------------*/

.jp-RenderedHTMLCommon {
  color: var(--jp-content-font-color1);
  font-family: var(--jp-content-font-family);
  font-size: var(--jp-content-font-size1);
  line-height: var(--jp-content-line-height);
  /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
  padding-right: 20px;
}

.jp-RenderedHTMLCommon em {
  font-style: italic;
}

.jp-RenderedHTMLCommon strong {
  font-weight: bold;
}

.jp-RenderedHTMLCommon u {
  text-decoration: underline;
}

.jp-RenderedHTMLCommon a:link {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:hover {
  text-decoration: underline;
  color: var(--jp-content-link-color);
}

.jp-RenderedHTMLCommon a:visited {
  text-decoration: none;
  color: var(--jp-content-link-color);
}

/* Headings */

.jp-RenderedHTMLCommon h1,
.jp-RenderedHTMLCommon h2,
.jp-RenderedHTMLCommon h3,
.jp-RenderedHTMLCommon h4,
.jp-RenderedHTMLCommon h5,
.jp-RenderedHTMLCommon h6 {
  line-height: var(--jp-content-heading-line-height);
  font-weight: var(--jp-content-heading-font-weight);
  font-style: normal;
  margin: var(--jp-content-heading-margin-top) 0
    var(--jp-content-heading-margin-bottom) 0;
}

.jp-RenderedHTMLCommon h1:first-child,
.jp-RenderedHTMLCommon h2:first-child,
.jp-RenderedHTMLCommon h3:first-child,
.jp-RenderedHTMLCommon h4:first-child,
.jp-RenderedHTMLCommon h5:first-child,
.jp-RenderedHTMLCommon h6:first-child {
  margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
}

.jp-RenderedHTMLCommon h1:last-child,
.jp-RenderedHTMLCommon h2:last-child,
.jp-RenderedHTMLCommon h3:last-child,
.jp-RenderedHTMLCommon h4:last-child,
.jp-RenderedHTMLCommon h5:last-child,
.jp-RenderedHTMLCommon h6:last-child {
  margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
}

.jp-RenderedHTMLCommon h1 {
  font-size: var(--jp-content-font-size5);
}

.jp-RenderedHTMLCommon h2 {
  font-size: var(--jp-content-font-size4);
}

.jp-RenderedHTMLCommon h3 {
  font-size: var(--jp-content-font-size3);
}

.jp-RenderedHTMLCommon h4 {
  font-size: var(--jp-content-font-size2);
}

.jp-RenderedHTMLCommon h5 {
  font-size: var(--jp-content-font-size1);
}

.jp-RenderedHTMLCommon h6 {
  font-size: var(--jp-content-font-size0);
}

/* Lists */

.jp-RenderedHTMLCommon ul:not(.list-inline),
.jp-RenderedHTMLCommon ol:not(.list-inline) {
  padding-left: 2em;
}

.jp-RenderedHTMLCommon ul {
  list-style: disc;
}

.jp-RenderedHTMLCommon ul ul {
  list-style: square;
}

.jp-RenderedHTMLCommon ul ul ul {
  list-style: circle;
}

.jp-RenderedHTMLCommon ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol ol {
  list-style: upper-alpha;
}

.jp-RenderedHTMLCommon ol ol ol {
  list-style: lower-alpha;
}

.jp-RenderedHTMLCommon ol ol ol ol {
  list-style: lower-roman;
}

.jp-RenderedHTMLCommon ol ol ol ol ol {
  list-style: decimal;
}

.jp-RenderedHTMLCommon ol,
.jp-RenderedHTMLCommon ul {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon ul ul,
.jp-RenderedHTMLCommon ul ol,
.jp-RenderedHTMLCommon ol ul,
.jp-RenderedHTMLCommon ol ol {
  margin-bottom: 0em;
}

.jp-RenderedHTMLCommon hr {
  color: var(--jp-border-color2);
  background-color: var(--jp-border-color1);
  margin-top: 1em;
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon > pre {
  margin: 1.5em 2em;
}

.jp-RenderedHTMLCommon pre,
.jp-RenderedHTMLCommon code {
  border: 0;
  background-color: var(--jp-layout-color0);
  color: var(--jp-content-font-color1);
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  line-height: var(--jp-code-line-height);
  padding: 0;
  white-space: pre-wrap;
}

.jp-RenderedHTMLCommon :not(pre) > code {
  background-color: var(--jp-layout-color2);
  padding: 1px 5px;
}

/* Tables */

.jp-RenderedHTMLCommon table {
  border-collapse: collapse;
  border-spacing: 0;
  border: none;
  color: var(--jp-ui-font-color1);
  font-size: 12px;
  table-layout: fixed;
  margin-left: auto;
  margin-right: auto;
}

.jp-RenderedHTMLCommon thead {
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  vertical-align: bottom;
}

.jp-RenderedHTMLCommon td,
.jp-RenderedHTMLCommon th,
.jp-RenderedHTMLCommon tr {
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}

.jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
.jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
  max-width: none;
}

:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
:not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
  text-align: right;
}

.jp-RenderedHTMLCommon th {
  font-weight: bold;
}

.jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
  background: var(--jp-layout-color0);
}

.jp-RenderedHTMLCommon tbody tr:nth-child(even) {
  background: var(--jp-rendermime-table-row-background);
}

.jp-RenderedHTMLCommon tbody tr:hover {
  background: var(--jp-rendermime-table-row-hover-background);
}

.jp-RenderedHTMLCommon table {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon p {
  text-align: left;
  margin: 0px;
}

.jp-RenderedHTMLCommon p {
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon img {
  -moz-force-broken-image-icon: 1;
}

/* Restrict to direct children as other images could be nested in other content. */
.jp-RenderedHTMLCommon > img {
  display: block;
  margin-left: 0;
  margin-right: 0;
  margin-bottom: 1em;
}

/* Change color behind transparent images if they need it... */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
  background-color: var(--jp-inverse-layout-color1);
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
  background-color: var(--jp-inverse-layout-color1);
}
/* ...or leave it untouched if they don't */
[data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-dark-background {
}
[data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-light-background {
}

.jp-RenderedHTMLCommon img,
.jp-RenderedImage img,
.jp-RenderedHTMLCommon svg,
.jp-RenderedSVG svg {
  max-width: 100%;
  height: auto;
}

.jp-RenderedHTMLCommon img.jp-mod-unconfined,
.jp-RenderedImage img.jp-mod-unconfined,
.jp-RenderedHTMLCommon svg.jp-mod-unconfined,
.jp-RenderedSVG svg.jp-mod-unconfined {
  max-width: none;
}

.jp-RenderedHTMLCommon .alert {
  padding: var(--jp-notebook-padding);
  border: var(--jp-border-width) solid transparent;
  border-radius: var(--jp-border-radius);
  margin-bottom: 1em;
}

.jp-RenderedHTMLCommon .alert-info {
  color: var(--jp-info-color0);
  background-color: var(--jp-info-color3);
  border-color: var(--jp-info-color2);
}
.jp-RenderedHTMLCommon .alert-info hr {
  border-color: var(--jp-info-color3);
}
.jp-RenderedHTMLCommon .alert-info > p:last-child,
.jp-RenderedHTMLCommon .alert-info > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-warning {
  color: var(--jp-warn-color0);
  background-color: var(--jp-warn-color3);
  border-color: var(--jp-warn-color2);
}
.jp-RenderedHTMLCommon .alert-warning hr {
  border-color: var(--jp-warn-color3);
}
.jp-RenderedHTMLCommon .alert-warning > p:last-child,
.jp-RenderedHTMLCommon .alert-warning > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-success {
  color: var(--jp-success-color0);
  background-color: var(--jp-success-color3);
  border-color: var(--jp-success-color2);
}
.jp-RenderedHTMLCommon .alert-success hr {
  border-color: var(--jp-success-color3);
}
.jp-RenderedHTMLCommon .alert-success > p:last-child,
.jp-RenderedHTMLCommon .alert-success > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon .alert-danger {
  color: var(--jp-error-color0);
  background-color: var(--jp-error-color3);
  border-color: var(--jp-error-color2);
}
.jp-RenderedHTMLCommon .alert-danger hr {
  border-color: var(--jp-error-color3);
}
.jp-RenderedHTMLCommon .alert-danger > p:last-child,
.jp-RenderedHTMLCommon .alert-danger > ul:last-child {
  margin-bottom: 0;
}

.jp-RenderedHTMLCommon blockquote {
  margin: 1em 2em;
  padding: 0 1em;
  border-left: 5px solid var(--jp-border-color2);
}

a.jp-InternalAnchorLink {
  visibility: hidden;
  margin-left: 8px;
  color: var(--md-blue-800);
}

h1:hover .jp-InternalAnchorLink,
h2:hover .jp-InternalAnchorLink,
h3:hover .jp-InternalAnchorLink,
h4:hover .jp-InternalAnchorLink,
h5:hover .jp-InternalAnchorLink,
h6:hover .jp-InternalAnchorLink {
  visibility: visible;
}

.jp-RenderedHTMLCommon kbd {
  background-color: var(--jp-rendermime-table-row-background);
  border: 1px solid var(--jp-border-color0);
  border-bottom-color: var(--jp-border-color2);
  border-radius: 3px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
  display: inline-block;
  font-size: 0.8em;
  line-height: 1em;
  padding: 0.2em 0.5em;
}

/* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
 * At the bottom of cells this is a bit too much as there is also spacing
 * between cells. Going all the way to 0 gets too tight between markdown and
 * code cells.
 */
.jp-RenderedHTMLCommon > *:last-child {
  margin-bottom: 0.5em;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-MimeDocument {
  outline: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-filebrowser-button-height: 28px;
  --jp-private-filebrowser-button-width: 48px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-FileBrowser {
  display: flex;
  flex-direction: column;
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
   * relative to this base size */
  font-size: var(--jp-ui-font-size1);
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  border-bottom: none;
  height: auto;
  margin: var(--jp-toolbar-header-margin);
  box-shadow: none;
}

.jp-BreadCrumbs {
  flex: 0 0 auto;
  margin: 4px 12px;
}

.jp-BreadCrumbs-item {
  margin: 0px 2px;
  padding: 0px 2px;
  border-radius: var(--jp-border-radius);
  cursor: pointer;
}

.jp-BreadCrumbs-item:hover {
  background-color: var(--jp-layout-color2);
}

.jp-BreadCrumbs-item:first-child {
  margin-left: 0px;
}

.jp-BreadCrumbs-item.jp-mod-dropTarget {
  background-color: var(--jp-brand-color2);
  opacity: 0.7;
}

/*-----------------------------------------------------------------------------
| Buttons
|----------------------------------------------------------------------------*/

.jp-FileBrowser-toolbar.jp-Toolbar {
  padding: 0px;
}

.jp-FileBrowser-toolbar.jp-Toolbar {
  justify-content: space-evenly;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-Toolbar-item {
  flex: 1;
}

.jp-FileBrowser-toolbar.jp-Toolbar .jp-ToolbarButtonComponent {
  width: 100%;
}

/*-----------------------------------------------------------------------------
| DirListing
|----------------------------------------------------------------------------*/

.jp-DirListing {
  flex: 1 1 auto;
  display: flex;
  flex-direction: column;
  outline: 0;
}

.jp-DirListing-header {
  flex: 0 0 auto;
  display: flex;
  flex-direction: row;
  overflow: hidden;
  border-top: var(--jp-border-width) solid var(--jp-border-color2);
  border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
  box-shadow: var(--jp-toolbar-box-shadow);
  z-index: 2;
}

.jp-DirListing-headerItem {
  padding: 4px 12px 2px 12px;
  font-weight: 500;
}

.jp-DirListing-headerItem:hover {
  background: var(--jp-layout-color2);
}

.jp-DirListing-headerItem.jp-id-name {
  flex: 1 0 84px;
}

.jp-DirListing-headerItem.jp-id-modified {
  flex: 0 0 112px;
  border-left: var(--jp-border-width) solid var(--jp-border-color2);
  text-align: right;
}

.jp-DirListing-narrow .jp-id-modified,
.jp-DirListing-narrow .jp-DirListing-itemModified {
  display: none;
}

.jp-DirListing-headerItem.jp-mod-selected {
  font-weight: 600;
}

/* increase specificity to override bundled default */
.jp-DirListing-content {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

/* Style the directory listing content when a user drops a file to upload */
.jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
  outline: 5px dashed rgba(128, 128, 128, 0.5);
  outline-offset: -10px;
  cursor: copy;
}

.jp-DirListing-item {
  display: flex;
  flex-direction: row;
  padding: 4px 12px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-DirListing-item.jp-mod-selected {
  color: white;
  background: var(--jp-brand-color1);
}

.jp-DirListing-item.jp-mod-dropTarget {
  background: var(--jp-brand-color3);
}

.jp-DirListing-item:hover:not(.jp-mod-selected) {
  background: var(--jp-layout-color2);
}

.jp-DirListing-itemIcon {
  flex: 0 0 20px;
  margin-right: 4px;
}

.jp-DirListing-itemText {
  flex: 1 0 64px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  user-select: none;
}

.jp-DirListing-itemModified {
  flex: 0 0 125px;
  text-align: right;
}

.jp-DirListing-editor {
  flex: 1 0 64px;
  outline: none;
  border: none;
}

.jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon:before {
  color: limegreen;
  content: '\25CF';
  font-size: 8px;
  position: absolute;
  left: -8px;
}

.jp-DirListing-item.lm-mod-drag-image,
.jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
  font-size: var(--jp-ui-font-size1);
  padding-left: 4px;
  margin-left: 4px;
  width: 160px;
  background-color: var(--jp-ui-inverse-font-color2);
  box-shadow: var(--jp-elevation-z2);
  border-radius: 0px;
  color: var(--jp-ui-font-color1);
  transform: translateX(-40%) translateY(-58%);
}

.jp-DirListing-deadSpace {
  flex: 1 1 auto;
  margin: 0;
  padding: 0;
  list-style-type: none;
  overflow: auto;
  background-color: var(--jp-layout-color1);
}

.jp-Document {
  min-width: 120px;
  min-height: 120px;
  outline: none;
}

.jp-FileDialog.jp-mod-conflict input {
  color: red;
}

.jp-FileDialog .jp-new-name-title {
  margin-top: 12px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
}

/*-----------------------------------------------------------------------------
| Main OutputArea
| OutputArea has a list of Outputs
|----------------------------------------------------------------------------*/

.jp-OutputArea {
  overflow-y: auto;
}

.jp-OutputArea-child {
  display: flex;
  flex-direction: row;
}

.jp-OutputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-outprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.jp-OutputArea-output {
  height: auto;
  overflow: auto;
  user-select: text;
  -moz-user-select: text;
  -webkit-user-select: text;
  -ms-user-select: text;
}

.jp-OutputArea-child .jp-OutputArea-output {
  flex-grow: 1;
  flex-shrink: 1;
}

/**
 * Isolated output.
 */
.jp-OutputArea-output.jp-mod-isolated {
  width: 100%;
  display: block;
}

/*
When drag events occur, `p-mod-override-cursor` is added to the body.
Because iframes steal all cursor events, the following two rules are necessary
to suppress pointer events while resize drags are occurring. There may be a
better solution to this problem.
*/
body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
  position: relative;
}

body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated:before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: transparent;
}

/* pre */

.jp-OutputArea-output pre {
  border: none;
  margin: 0px;
  padding: 0px;
  overflow-x: auto;
  overflow-y: auto;
  word-break: break-all;
  word-wrap: break-word;
  white-space: pre-wrap;
}

/* tables */

.jp-OutputArea-output.jp-RenderedHTMLCommon table {
  margin-left: 0;
  margin-right: 0;
}

/* description lists */

.jp-OutputArea-output dl,
.jp-OutputArea-output dt,
.jp-OutputArea-output dd {
  display: block;
}

.jp-OutputArea-output dl {
  width: 100%;
  overflow: hidden;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dt {
  font-weight: bold;
  float: left;
  width: 20%;
  padding: 0;
  margin: 0;
}

.jp-OutputArea-output dd {
  float: left;
  width: 80%;
  padding: 0;
  margin: 0;
}

/* Hide the gutter in case of
 *  - nested output areas (e.g. in the case of output widgets)
 *  - mirrored output areas
 */
.jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
  display: none;
}

/*-----------------------------------------------------------------------------
| executeResult is added to any Output-result for the display of the object
| returned by a cell
|----------------------------------------------------------------------------*/

.jp-OutputArea-output.jp-OutputArea-executeResult {
  margin-left: 0px;
  flex: 1 1 auto;
}

.jp-OutputArea-executeResult.jp-RenderedText {
  padding-top: var(--jp-code-padding);
}

/*-----------------------------------------------------------------------------
| The Stdin output
|----------------------------------------------------------------------------*/

.jp-OutputArea-stdin {
  line-height: var(--jp-code-line-height);
  padding-top: var(--jp-code-padding);
  display: flex;
}

.jp-Stdin-prompt {
  color: var(--jp-content-font-color0);
  padding-right: var(--jp-code-padding);
  vertical-align: baseline;
  flex: 0 0 auto;
}

.jp-Stdin-input {
  font-family: var(--jp-code-font-family);
  font-size: inherit;
  color: inherit;
  background-color: inherit;
  width: 42%;
  min-width: 200px;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
  flex: 0 0 70%;
}

.jp-Stdin-input:focus {
  box-shadow: none;
}

/*-----------------------------------------------------------------------------
| Output Area View
|----------------------------------------------------------------------------*/

.jp-LinkedOutputView .jp-OutputArea {
  height: 100%;
  display: block;
}

.jp-LinkedOutputView .jp-OutputArea-output:only-child {
  height: 100%;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

.jp-Collapser {
  flex: 0 0 var(--jp-cell-collapser-width);
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
  border-radius: var(--jp-border-radius);
  opacity: 1;
}

.jp-Collapser-child {
  display: block;
  width: 100%;
  box-sizing: border-box;
  /* height: 100% doesn't work because the height of its parent is computed from content */
  position: absolute;
  top: 0px;
  bottom: 0px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Header/Footer
|----------------------------------------------------------------------------*/

/* Hidden by zero height by default */
.jp-CellHeader,
.jp-CellFooter {
  height: 0px;
  width: 100%;
  padding: 0px;
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Input
|----------------------------------------------------------------------------*/

/* All input areas */
.jp-InputArea {
  display: flex;
  flex-direction: row;
}

.jp-InputArea-editor {
  flex: 1 1 auto;
}

.jp-InputArea-editor {
  /* This is the non-active, default styling */
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  border-radius: 0px;
  background: var(--jp-cell-editor-background);
}

.jp-InputPrompt {
  flex: 0 0 var(--jp-cell-prompt-width);
  color: var(--jp-cell-inprompt-font-color);
  font-family: var(--jp-cell-prompt-font-family);
  padding: var(--jp-code-padding);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  opacity: var(--jp-cell-prompt-opacity);
  line-height: var(--jp-code-line-height);
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
  opacity: var(--jp-cell-prompt-opacity);
  /* Right align prompt text, don't wrap to handle large prompt numbers */
  text-align: right;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  /* Disable text selection */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Placeholder
|----------------------------------------------------------------------------*/

.jp-Placeholder {
  display: flex;
  flex-direction: row;
  flex: 1 1 auto;
}

.jp-Placeholder-prompt {
  box-sizing: border-box;
}

.jp-Placeholder-content {
  flex: 1 1 auto;
  border: none;
  background: transparent;
  height: 20px;
  box-sizing: border-box;
}

.jp-Placeholder-content .jp-MoreHorizIcon {
  width: 32px;
  height: 16px;
  border: 1px solid transparent;
  border-radius: var(--jp-border-radius);
}

.jp-Placeholder-content .jp-MoreHorizIcon:hover {
  border: 1px solid var(--jp-border-color1);
  box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.25);
  background-color: var(--jp-layout-color0);
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-cell-scrolling-output-offset: 5px;
}

/*-----------------------------------------------------------------------------
| Cell
|----------------------------------------------------------------------------*/

.jp-Cell {
  padding: var(--jp-cell-padding);
  margin: 0px;
  border: none;
  outline: none;
  background: transparent;
}

/*-----------------------------------------------------------------------------
| Common input/output
|----------------------------------------------------------------------------*/

.jp-Cell-inputWrapper,
.jp-Cell-outputWrapper {
  display: flex;
  flex-direction: row;
  padding: 0px;
  margin: 0px;
  /* Added to reveal the box-shadow on the input and output collapsers. */
  overflow: visible;
}

/* Only input/output areas inside cells */
.jp-Cell-inputArea,
.jp-Cell-outputArea {
  flex: 1 1 auto;
}

/*-----------------------------------------------------------------------------
| Collapser
|----------------------------------------------------------------------------*/

/* Make the output collapser disappear when there is not output, but do so
 * in a manner that leaves it in the layout and preserves its width.
 */
.jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
  border: none !important;
  background: transparent !important;
}

.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
  min-height: var(--jp-cell-collapser-min-height);
}

/*-----------------------------------------------------------------------------
| Output
|----------------------------------------------------------------------------*/

/* Put a space between input and output when there IS output */
.jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
  margin-top: 5px;
}

/* Text output with the Out[] prompt needs a top padding to match the
 * alignment of the Out[] prompt itself.
 */
.jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
  padding-top: var(--jp-code-padding);
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
  overflow-y: auto;
  max-height: 200px;
  box-shadow: inset 0 0 6px 2px rgba(0, 0, 0, 0.3);
  margin-left: var(--jp-private-cell-scrolling-output-offset);
}

.jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
  flex: 0 0
    calc(
      var(--jp-cell-prompt-width) -
        var(--jp-private-cell-scrolling-output-offset)
    );
}

/*-----------------------------------------------------------------------------
| CodeCell
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| MarkdownCell
|----------------------------------------------------------------------------*/

.jp-MarkdownOutput {
  flex: 1 1 auto;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: var(--jp-code-padding);
}

.jp-MarkdownOutput.jp-RenderedHTMLCommon {
  overflow: auto;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Variables
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------

/*-----------------------------------------------------------------------------
| Styles
|----------------------------------------------------------------------------*/

.jp-NotebookPanel-toolbar {
  padding: 2px;
}

.jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
  border: none;
  box-shadow: none;
}

.jp-Notebook-toolbarCellTypeDropdown select {
  height: 24px;
  font-size: var(--jp-ui-font-size1);
  line-height: 14px;
  border-radius: 0;
  display: block;
}

.jp-Notebook-toolbarCellTypeDropdown span {
  top: 5px !important;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Private CSS variables
|----------------------------------------------------------------------------*/

:root {
  --jp-private-notebook-dragImage-width: 304px;
  --jp-private-notebook-dragImage-height: 36px;
  --jp-private-notebook-selected-color: var(--md-blue-400);
  --jp-private-notebook-active-color: var(--md-green-400);
}

/*-----------------------------------------------------------------------------
| Imports
|----------------------------------------------------------------------------*/

/*-----------------------------------------------------------------------------
| Notebook
|----------------------------------------------------------------------------*/

.jp-NotebookPanel {
  display: block;
  height: 100%;
}

.jp-NotebookPanel.jp-Document {
  min-width: 240px;
  min-height: 120px;
}

.jp-Notebook {
  padding: var(--jp-notebook-padding);
  outline: none;
  overflow: auto;
  background: var(--jp-layout-color0);
}

.jp-Notebook.jp-mod-scrollPastEnd::after {
  display: block;
  content: '';
  min-height: var(--jp-notebook-scroll-padding);
}

.jp-Notebook .jp-Cell {
  overflow: visible;
}

.jp-Notebook .jp-Cell .jp-InputPrompt {
  cursor: move;
}

/*-----------------------------------------------------------------------------
| Notebook state related styling
|
| The notebook and cells each have states, here are the possibilities:
|
| - Notebook
|   - Command
|   - Edit
| - Cell
|   - None
|   - Active (only one can be active)
|   - Selected (the cells actions are applied to)
|   - Multiselected (when multiple selected, the cursor)
|   - No outputs
|----------------------------------------------------------------------------*/

/* Command or edit modes */

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

.jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
  opacity: var(--jp-cell-prompt-not-active-opacity);
  color: var(--jp-cell-prompt-not-active-font-color);
}

/* cell is active */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
  background: var(--jp-brand-color1);
}

/* collapser is hovered */
.jp-Notebook .jp-Cell .jp-Collapser:hover {
  box-shadow: var(--jp-elevation-z2);
  background: var(--jp-brand-color1);
  opacity: var(--jp-cell-collapser-not-active-hover-opacity);
}

/* cell is active and collapser is hovered */
.jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
  background: var(--jp-brand-color0);
  opacity: 1;
}

/* Command mode */

.jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
  background: var(--jp-notebook-multiselected-color);
}

.jp-Notebook.jp-mod-commandMode
  .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
  background: transparent;
}

/* Edit mode */

.jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
  border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
  box-shadow: var(--jp-input-box-shadow);
  background-color: var(--jp-cell-editor-active-background);
}

/*-----------------------------------------------------------------------------
| Notebook drag and drop
|----------------------------------------------------------------------------*/

.jp-Notebook-cell.jp-mod-dropSource {
  opacity: 0.5;
}

.jp-Notebook-cell.jp-mod-dropTarget,
.jp-Notebook.jp-mod-commandMode
  .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
  border-top-color: var(--jp-private-notebook-selected-color);
  border-top-style: solid;
  border-top-width: 2px;
}

.jp-dragImage {
  display: flex;
  flex-direction: row;
  width: var(--jp-private-notebook-dragImage-width);
  height: var(--jp-private-notebook-dragImage-height);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background);
  overflow: visible;
}

.jp-dragImage-singlePrompt {
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

.jp-dragImage .jp-dragImage-content {
  flex: 1 1 auto;
  z-index: 2;
  font-size: var(--jp-code-font-size);
  font-family: var(--jp-code-font-family);
  line-height: var(--jp-code-line-height);
  padding: var(--jp-code-padding);
  border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
  background: var(--jp-cell-editor-background-color);
  color: var(--jp-content-font-color3);
  text-align: left;
  margin: 4px 4px 4px 0px;
}

.jp-dragImage .jp-dragImage-prompt {
  flex: 0 0 auto;
  min-width: 36px;
  color: var(--jp-cell-inprompt-font-color);
  padding: var(--jp-code-padding);
  padding-left: 12px;
  font-family: var(--jp-cell-prompt-font-family);
  letter-spacing: var(--jp-cell-prompt-letter-spacing);
  line-height: 1.9;
  font-size: var(--jp-code-font-size);
  border: var(--jp-border-width) solid transparent;
}

.jp-dragImage-multipleBack {
  z-index: -1;
  position: absolute;
  height: 32px;
  width: 300px;
  top: 8px;
  left: 8px;
  background: var(--jp-layout-color2);
  border: var(--jp-border-width) solid var(--jp-input-border-color);
  box-shadow: 2px 2px 4px 0px rgba(0, 0, 0, 0.12);
}

/*-----------------------------------------------------------------------------
| Cell toolbar
|----------------------------------------------------------------------------*/

.jp-NotebookTools {
  display: block;
  min-width: var(--jp-sidebar-min-width);
  color: var(--jp-ui-font-color1);
  background: var(--jp-layout-color1);
  /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
  font-size: var(--jp-ui-font-size1);
  overflow: auto;
}

.jp-NotebookTools-tool {
  padding: 0px 12px 0 12px;
}

.jp-ActiveCellTool {
  padding: 12px;
  background-color: var(--jp-layout-color1);
  border-top: none !important;
}

.jp-ActiveCellTool .jp-InputArea-prompt {
  flex: 0 0 auto;
  padding-left: 0px;
}

.jp-ActiveCellTool .jp-InputArea-editor {
  flex: 1 1 auto;
  background: var(--jp-cell-editor-background);
  border-color: var(--jp-cell-editor-border-color);
}

.jp-ActiveCellTool .jp-InputArea-editor .CodeMirror {
  background: transparent;
}

.jp-MetadataEditorTool {
  flex-direction: column;
  padding: 12px 0px 12px 0px;
}

.jp-RankedPanel > :not(:first-child) {
  margin-top: 12px;
}

.jp-KeySelector select.jp-mod-styled {
  font-size: var(--jp-ui-font-size1);
  color: var(--jp-ui-font-color0);
  border: var(--jp-border-width) solid var(--jp-border-color1);
}

.jp-KeySelector label,
.jp-MetadataEditorTool label {
  line-height: 1.4;
}

/*-----------------------------------------------------------------------------
| Presentation Mode (.jp-mod-presentationMode)
|----------------------------------------------------------------------------*/

.jp-mod-presentationMode .jp-Notebook {
  --jp-content-font-size1: var(--jp-content-presentation-font-size1);
  --jp-code-font-size: var(--jp-code-presentation-font-size);
}

.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
.jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
  flex: 0 0 110px;
}

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/* This file was auto-generated by ensurePackage() in @jupyterlab/buildutils */

/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

</style>

    <style type="text/css">
/*-----------------------------------------------------------------------------
| Copyright (c) Jupyter Development Team.
| Distributed under the terms of the Modified BSD License.
|----------------------------------------------------------------------------*/

/*
The following CSS variables define the main, public API for styling JupyterLab.
These variables should be used by all plugins wherever possible. In other
words, plugins should not define custom colors, sizes, etc unless absolutely
necessary. This enables users to change the visual theme of JupyterLab
by changing these variables.

Many variables appear in an ordered sequence (0,1,2,3). These sequences
are designed to work well together, so for example, `--jp-border-color1` should
be used with `--jp-layout-color1`. The numbers have the following meanings:

* 0: super-primary, reserved for special emphasis
* 1: primary, most important under normal situations
* 2: secondary, next most important under normal situations
* 3: tertiary, next most important under normal situations

Throughout JupyterLab, we are mostly following principles from Google's
Material Design when selecting colors. We are not, however, following
all of MD as it is not optimized for dense, information rich UIs.
*/

:root {
  /* Elevation
   *
   * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
   *
   * https://github.com/material-components/material-components-web
   * https://material-components-web.appspot.com/elevation.html
   */

  --jp-shadow-base-lightness: 0;
  --jp-shadow-umbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.2
  );
  --jp-shadow-penumbra-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.14
  );
  --jp-shadow-ambient-color: rgba(
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    var(--jp-shadow-base-lightness),
    0.12
  );
  --jp-elevation-z0: none;
  --jp-elevation-z1: 0px 2px 1px -1px var(--jp-shadow-umbra-color),
    0px 1px 1px 0px var(--jp-shadow-penumbra-color),
    0px 1px 3px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z2: 0px 3px 1px -2px var(--jp-shadow-umbra-color),
    0px 2px 2px 0px var(--jp-shadow-penumbra-color),
    0px 1px 5px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z4: 0px 2px 4px -1px var(--jp-shadow-umbra-color),
    0px 4px 5px 0px var(--jp-shadow-penumbra-color),
    0px 1px 10px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z6: 0px 3px 5px -1px var(--jp-shadow-umbra-color),
    0px 6px 10px 0px var(--jp-shadow-penumbra-color),
    0px 1px 18px 0px var(--jp-shadow-ambient-color);
  --jp-elevation-z8: 0px 5px 5px -3px var(--jp-shadow-umbra-color),
    0px 8px 10px 1px var(--jp-shadow-penumbra-color),
    0px 3px 14px 2px var(--jp-shadow-ambient-color);
  --jp-elevation-z12: 0px 7px 8px -4px var(--jp-shadow-umbra-color),
    0px 12px 17px 2px var(--jp-shadow-penumbra-color),
    0px 5px 22px 4px var(--jp-shadow-ambient-color);
  --jp-elevation-z16: 0px 8px 10px -5px var(--jp-shadow-umbra-color),
    0px 16px 24px 2px var(--jp-shadow-penumbra-color),
    0px 6px 30px 5px var(--jp-shadow-ambient-color);
  --jp-elevation-z20: 0px 10px 13px -6px var(--jp-shadow-umbra-color),
    0px 20px 31px 3px var(--jp-shadow-penumbra-color),
    0px 8px 38px 7px var(--jp-shadow-ambient-color);
  --jp-elevation-z24: 0px 11px 15px -7px var(--jp-shadow-umbra-color),
    0px 24px 38px 3px var(--jp-shadow-penumbra-color),
    0px 9px 46px 8px var(--jp-shadow-ambient-color);

  /* Borders
   *
   * The following variables, specify the visual styling of borders in JupyterLab.
   */

  --jp-border-width: 1px;
  --jp-border-color0: var(--md-grey-400);
  --jp-border-color1: var(--md-grey-400);
  --jp-border-color2: var(--md-grey-300);
  --jp-border-color3: var(--md-grey-200);
  --jp-border-radius: 2px;

  /* UI Fonts
   *
   * The UI font CSS variables are used for the typography all of the JupyterLab
   * user interface elements that are not directly user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-ui-font-scale-factor: 1.2;
  --jp-ui-font-size0: 0.83333em;
  --jp-ui-font-size1: 13px; /* Base font size */
  --jp-ui-font-size2: 1.2em;
  --jp-ui-font-size3: 1.44em;

  --jp-ui-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica,
    Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';

  /*
   * Use these font colors against the corresponding main layout colors.
   * In a light theme, these go from dark to light.
   */

  /* Defaults use Material Design specification */
  --jp-ui-font-color0: rgba(0, 0, 0, 1);
  --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
  --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
  --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

  /*
   * Use these against the brand/accent/warn/error colors.
   * These will typically go from light to darker, in both a dark and light theme.
   */

  --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
  --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
  --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

  /* Content Fonts
   *
   * Content font variables are used for typography of user generated content.
   *
   * The font sizing here is done assuming that the body font size of --jp-content-font-size1
   * is applied to a parent element. When children elements, such as headings, are sized
   * in em all things will be computed relative to that body size.
   */

  --jp-content-line-height: 1.6;
  --jp-content-font-scale-factor: 1.2;
  --jp-content-font-size0: 0.83333em;
  --jp-content-font-size1: 14px; /* Base font size */
  --jp-content-font-size2: 1.2em;
  --jp-content-font-size3: 1.44em;
  --jp-content-font-size4: 1.728em;
  --jp-content-font-size5: 2.0736em;

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-content-presentation-font-size1: 17px;

  --jp-content-heading-line-height: 1;
  --jp-content-heading-margin-top: 1.2em;
  --jp-content-heading-margin-bottom: 0.8em;
  --jp-content-heading-font-weight: 500;

  /* Defaults use Material Design specification */
  --jp-content-font-color0: rgba(0, 0, 0, 1);
  --jp-content-font-color1: rgba(0, 0, 0, 0.87);
  --jp-content-font-color2: rgba(0, 0, 0, 0.54);
  --jp-content-font-color3: rgba(0, 0, 0, 0.38);

  --jp-content-link-color: var(--md-blue-700);

  --jp-content-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Helvetica, Arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
    'Segoe UI Symbol';

  /*
   * Code Fonts
   *
   * Code font variables are used for typography of code and other monospaces content.
   */

  --jp-code-font-size: 13px;
  --jp-code-line-height: 1.3077; /* 17px for 13px base */
  --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
  --jp-code-font-family-default: Menlo, Consolas, 'DejaVu Sans Mono', monospace;
  --jp-code-font-family: var(--jp-code-font-family-default);

  /* This gives a magnification of about 125% in presentation mode over normal. */
  --jp-code-presentation-font-size: 16px;

  /* may need to tweak cursor width if you change font size */
  --jp-code-cursor-width0: 1.4px;
  --jp-code-cursor-width1: 2px;
  --jp-code-cursor-width2: 4px;

  /* Layout
   *
   * The following are the main layout colors use in JupyterLab. In a light
   * theme these would go from light to dark.
   */

  --jp-layout-color0: white;
  --jp-layout-color1: white;
  --jp-layout-color2: var(--md-grey-200);
  --jp-layout-color3: var(--md-grey-400);
  --jp-layout-color4: var(--md-grey-600);

  /* Inverse Layout
   *
   * The following are the inverse layout colors use in JupyterLab. In a light
   * theme these would go from dark to light.
   */

  --jp-inverse-layout-color0: #111111;
  --jp-inverse-layout-color1: var(--md-grey-900);
  --jp-inverse-layout-color2: var(--md-grey-800);
  --jp-inverse-layout-color3: var(--md-grey-700);
  --jp-inverse-layout-color4: var(--md-grey-600);

  /* Brand/accent */

  --jp-brand-color0: var(--md-blue-700);
  --jp-brand-color1: var(--md-blue-500);
  --jp-brand-color2: var(--md-blue-300);
  --jp-brand-color3: var(--md-blue-100);
  --jp-brand-color4: var(--md-blue-50);

  --jp-accent-color0: var(--md-green-700);
  --jp-accent-color1: var(--md-green-500);
  --jp-accent-color2: var(--md-green-300);
  --jp-accent-color3: var(--md-green-100);

  /* State colors (warn, error, success, info) */

  --jp-warn-color0: var(--md-orange-700);
  --jp-warn-color1: var(--md-orange-500);
  --jp-warn-color2: var(--md-orange-300);
  --jp-warn-color3: var(--md-orange-100);

  --jp-error-color0: var(--md-red-700);
  --jp-error-color1: var(--md-red-500);
  --jp-error-color2: var(--md-red-300);
  --jp-error-color3: var(--md-red-100);

  --jp-success-color0: var(--md-green-700);
  --jp-success-color1: var(--md-green-500);
  --jp-success-color2: var(--md-green-300);
  --jp-success-color3: var(--md-green-100);

  --jp-info-color0: var(--md-cyan-700);
  --jp-info-color1: var(--md-cyan-500);
  --jp-info-color2: var(--md-cyan-300);
  --jp-info-color3: var(--md-cyan-100);

  /* Cell specific styles */

  --jp-cell-padding: 5px;

  --jp-cell-collapser-width: 8px;
  --jp-cell-collapser-min-height: 20px;
  --jp-cell-collapser-not-active-hover-opacity: 0.6;

  --jp-cell-editor-background: var(--md-grey-100);
  --jp-cell-editor-border-color: var(--md-grey-300);
  --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-cell-editor-active-background: var(--jp-layout-color0);
  --jp-cell-editor-active-border-color: var(--jp-brand-color1);

  --jp-cell-prompt-width: 64px;
  --jp-cell-prompt-font-family: 'Source Code Pro', monospace;
  --jp-cell-prompt-letter-spacing: 0px;
  --jp-cell-prompt-opacity: 1;
  --jp-cell-prompt-not-active-opacity: 0.5;
  --jp-cell-prompt-not-active-font-color: var(--md-grey-700);
  /* A custom blend of MD grey and blue 600
   * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
  --jp-cell-inprompt-font-color: #307fc1;
  /* A custom blend of MD grey and orange 600
   * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
  --jp-cell-outprompt-font-color: #bf5b3d;

  /* Notebook specific styles */

  --jp-notebook-padding: 10px;
  --jp-notebook-select-background: var(--jp-layout-color1);
  --jp-notebook-multiselected-color: var(--md-blue-50);

  /* The scroll padding is calculated to fill enough space at the bottom of the
  notebook to show one single-line cell (with appropriate padding) at the top
  when the notebook is scrolled all the way to the bottom. We also subtract one
  pixel so that no scrollbar appears if we have just one single-line cell in the
  notebook. This padding is to enable a 'scroll past end' feature in a notebook.
  */
  --jp-notebook-scroll-padding: calc(
    100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
      var(--jp-code-padding) - var(--jp-cell-padding) - 1px
  );

  /* Rendermime styles */

  --jp-rendermime-error-background: #fdd;
  --jp-rendermime-table-row-background: var(--md-grey-100);
  --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

  /* Dialog specific styles */

  --jp-dialog-background: rgba(0, 0, 0, 0.25);

  /* Console specific styles */

  --jp-console-padding: 10px;

  /* Toolbar specific styles */

  --jp-toolbar-border-color: var(--jp-border-color1);
  --jp-toolbar-micro-height: 8px;
  --jp-toolbar-background: var(--jp-layout-color1);
  --jp-toolbar-box-shadow: 0px 0px 2px 0px rgba(0, 0, 0, 0.24);
  --jp-toolbar-header-margin: 4px 4px 0px 4px;
  --jp-toolbar-active-background: var(--md-grey-300);

  /* Input field styles */

  --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
  --jp-input-active-background: var(--jp-layout-color1);
  --jp-input-hover-background: var(--jp-layout-color1);
  --jp-input-background: var(--md-grey-100);
  --jp-input-border-color: var(--jp-border-color1);
  --jp-input-active-border-color: var(--jp-brand-color1);
  --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

  /* General editor styles */

  --jp-editor-selected-background: #d9d9d9;
  --jp-editor-selected-focused-background: #d7d4f0;
  --jp-editor-cursor-color: var(--jp-ui-font-color0);

  /* Code mirror specific styles */

  --jp-mirror-editor-keyword-color: #008000;
  --jp-mirror-editor-atom-color: #88f;
  --jp-mirror-editor-number-color: #080;
  --jp-mirror-editor-def-color: #00f;
  --jp-mirror-editor-variable-color: var(--md-grey-900);
  --jp-mirror-editor-variable-2-color: #05a;
  --jp-mirror-editor-variable-3-color: #085;
  --jp-mirror-editor-punctuation-color: #05a;
  --jp-mirror-editor-property-color: #05a;
  --jp-mirror-editor-operator-color: #aa22ff;
  --jp-mirror-editor-comment-color: #408080;
  --jp-mirror-editor-string-color: #ba2121;
  --jp-mirror-editor-string-2-color: #708;
  --jp-mirror-editor-meta-color: #aa22ff;
  --jp-mirror-editor-qualifier-color: #555;
  --jp-mirror-editor-builtin-color: #008000;
  --jp-mirror-editor-bracket-color: #997;
  --jp-mirror-editor-tag-color: #170;
  --jp-mirror-editor-attribute-color: #00c;
  --jp-mirror-editor-header-color: blue;
  --jp-mirror-editor-quote-color: #090;
  --jp-mirror-editor-link-color: #00c;
  --jp-mirror-editor-error-color: #f00;
  --jp-mirror-editor-hr-color: #999;

  /* Vega extension styles */

  --jp-vega-background: white;

  /* Sidebar-related styles */

  --jp-sidebar-min-width: 180px;

  /* Search-related styles */

  --jp-search-toggle-off-opacity: 0.5;
  --jp-search-toggle-hover-opacity: 0.8;
  --jp-search-toggle-on-opacity: 1;
  --jp-search-selected-match-background-color: rgb(245, 200, 0);
  --jp-search-selected-match-color: black;
  --jp-search-unselected-match-background-color: var(
    --jp-inverse-layout-color0
  );
  --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

  /* Icon colors that work well with light or dark backgrounds */
  --jp-icon-contrast-color0: var(--md-purple-600);
  --jp-icon-contrast-color1: var(--md-green-600);
  --jp-icon-contrast-color2: var(--md-pink-600);
  --jp-icon-contrast-color3: var(--md-blue-600);
}
</style>

<style type="text/css">
a.anchor-link {
   display: none;
}
.highlight  {
    margin: 0.4em;
}

/* Input area styling */
.jp-InputArea {
    overflow: hidden;
}

.jp-InputArea-editor {
    overflow: hidden;
}

@media print {
  body {
    margin: 0;
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
<body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">

<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Scikit-learn (Sklearn) adalah salah satu package paling berguna  untuk machine learning  dengan Python. Package ini menyediakan pilihan alat yang efisien untuk machine learning seperti  klasifikasi, regresi, clustering, dan dimension reduction melalui antarmuka konsistensi dengan Python. Package  in  sebagian besar dibangun di atas NumPy, SciPy dan Matplotlib.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2 id="Unsupervised-Methods">Unsupervised Methods<a class="anchor-link" href="#Unsupervised-Methods">&#182;</a></h2>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Data">Data<a class="anchor-link" href="#Data">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Data Pelanggan Mall</p>
<p>Seorang pemilik Mall ingin mengelompokan customer di Mall yang ia miliki, sehingga tim marketing bisa mengembangkan strategi yang tepat untuk customer yang tepat pula. Data yang dimiliki oleh Mall tersebut adalah Customer ID, umur pelanggan (age), pendapatan tahunan dalam ribu dollar (annual income) dan spending score. Spending score merupakan nilai yang diberikan oleh Mall kepada customer berbasarkan perilaku customer (waktu kunjungan,jenis barang yang dibeli, dan banyaknya uang yang dihabiskan dalam belanja) yang memiliki rentang nilai 1-100. Semakin besar nilai Spending Score berarti customer semakin loyal pada Mall tersebut dan semakin besar pula uang belanja yang digunakan.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Import-data">Import data<a class="anchor-link" href="#Import-data">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>untuk mengimport data dalam bentuk <code>csv</code> kita membutuhkan package <code>pandas</code></p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="n">mall</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;Mall_Customers.csv&quot;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>kita bisa menanpilkan 5 baris pertama dengan methods <code>head</code></p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[7]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[7]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Peubah yang digunakan untuk menerapkan k-means adalah peubah Age Annual Income dan Spending Score. Oleh karena itu peubah yang tidak kita gunakan akan kita hilangkan tersebih dahulu.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[11]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall</span> <span class="o">=</span> <span class="n">mall</span><span class="o">.</span><span class="n">filter</span><span class="p">([</span><span class="s2">&quot;Age&quot;</span><span class="p">,</span><span class="s2">&quot;Annual Income&quot;</span><span class="p">,</span><span class="s2">&quot;Spending Score&quot;</span><span class="p">])</span>
<span class="n">mall</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[11]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Standarisasi">Standarisasi<a class="anchor-link" href="#Standarisasi">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Standarisasi peubah merupakan proses transformasi peubah menjadi peubah yang memiliki rata-rata nol dan simpangan baku satu. Process standarisasi ini dilakukan jika kita melihat perbedanan satuan pengukuran peubah-peubah yang digunakan contoh(umur dan pendapatan). Standarisasi dilakukan karena metode k-means menggunakan konsep jarak antara objek/amatan, yang mana sensitif terhadap satuan pengukuran. Formula untuk standarisasi data adalah sebagai berikut:</p>
$$y = \frac{y-\bar{y}}{\sigma_{y}}$$<p>dengan $\bar{y}$ merupakan rata-rata dari $y$ dan $\sigma_{y}$ merupakan simpangan baku dari y.</p>
<p>Dalam Python, standarisasi data bisa dilakukan dengan menggunakan fungsi <code>StandardScaler</code> dari package <code>sklearn</code>.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[14]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.preprocessing</span> <span class="kn">import</span> <span class="n">StandardScaler</span>
<span class="n">scale</span> <span class="o">=</span> <span class="n">StandardScaler</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Setelah kita mempersiapkan fungsi untuk standarisasi data, berikutnya kita akan terapkan pada data</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[59]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">scale</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall</span><span class="p">)</span>
<span class="n">mall_scale</span> <span class="o">=</span> <span class="n">scale</span><span class="o">.</span><span class="n">transform</span><span class="p">(</span><span class="n">mall</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;mean&quot;</span><span class="p">,</span><span class="n">scale</span><span class="o">.</span><span class="n">mean_</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;std&quot;</span><span class="p">,</span><span class="n">scale</span><span class="o">.</span><span class="n">scale_</span><span class="p">)</span>
<span class="nb">type</span><span class="p">(</span><span class="n">mall</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>mean [38.85 60.56 50.2 ]
std [13.93404105 26.19897708 25.75888196]
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[59]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>pandas.core.frame.DataFrame</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Memilih-metode-Unsupervised-Learning">Memilih metode Unsupervised Learning<a class="anchor-link" href="#Memilih-metode-Unsupervised-Learning">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Metode yang digunakan untuk tutorial ini adalah metode K-Means dan Hierarchical clustering. Kedua metode tersebut bisa kita dapatkan pada package sklearn</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[36]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="kn">import</span> <span class="n">KMeans</span>
<span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="kn">import</span> <span class="n">AgglomerativeClustering</span>
<span class="n">kmeans</span> <span class="o">=</span> <span class="n">KMeans</span><span class="p">()</span>
<span class="n">hclust</span> <span class="o">=</span> <span class="n">AgglomerativeClustering</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Memilih-Jumlah-Cluster-Optimum">Memilih Jumlah Cluster Optimum<a class="anchor-link" href="#Memilih-Jumlah-Cluster-Optimum">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Umumnya, banyaknya cluster dapat ditentukan dengan menggunakan beberapa kriteria statistik, seperti koefisien <strong>silhouette</strong> dan <strong>WSS</strong> atau (Within Sum of Square).</p>
<p>Kriteria koefisien silhouette dihitung berdasarkan jarak antar amatan. Koefisien ini mengukur seberapa dekat suatu amatan dengan amatan lain yang berada di clusterl yang sama (dikenal sebagai ukuran cohesion) dibandingkan dengan jarak terhadap amatan lain yang berada di cluster berbeda (dikenal sebagai ukuran separation).  Koefisien yang nilainya semakin besar menunjukkan bahwa clusterl yang terbentuk sudah sesuai.</p>
<p>Kriteria WSS merupakan kriteria yangmenghitung keragamaan dalam cluster yang terbentuk. Semakin kecil keragaman dalam cluster yang terbentuk menunjukkan bahwa cluster yang terbentuk sudah sesuai.</p>
<p>Dengan menggunakan kriteria tersebut, kita bisa membandingkan banyaknya cluster yang paling sesuai pada data yang kita sedang analisis dengan menggunakan suatu plot. Untuk itu kita perlu menginstall pacakage <code>yellowbrick</code> berikut ini</p>

</div>
</div>! pip install yellowbrick
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Untuk kriteria koefisien silhoutte, banyaknya cluster dengan nilai koefisien tertinggi yang kita pilih. Sedangkan pada WSS, banyaknya cluster yang kita pilih didasarkan pada banyaknya cluster yang mana garisnya berbentuk seperti siku (elbow).</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="K-Means">K-Means<a class="anchor-link" href="#K-Means">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[38]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">yellowbrick.cluster</span> <span class="kn">import</span> <span class="n">KElbowVisualizer</span>

<span class="c1"># Silhouette</span>
<span class="n">kmeans_vis_sil</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">kmeans</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;silhouette&quot;</span><span class="p">)</span>

<span class="n">kmeans_vis_sil</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">kmeans_vis_sil</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAiMAAAFlCAYAAAA5w+hdAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAACNe0lEQVR4nOzdd3iT5dfA8W9G073poFBaWlp2GWVP2RsRUHAgDtx741ZQUX/uhRP1RUUUEEFQEFCQDYWWVUahC1q698p63j8qgcpoKU3ScT7X5WXzrPvkSUhO7qlSFEVBCCGEEMJO1PYOQAghhBBNmyQjQgghhLArSUaEEEIIYVeSjAghhBDCriQZEUIIIYRdSTIihBBCCLuSZETUudjYWGbMmMGECRMYP348s2bN4tixYwDs37+fBx98EIDZs2fz1VdfAdC2bVtyc3NtEt9tt91mKevnn3/m+++/v+xr/P3330ybNo2JEycybtw4HnroIU6fPl3XoVZr2bJlREdHc/XVV1f578knnwRsf4/j4+MZPnw4kydP5uTJk7W6xo4dOxg/fnyVbV9//TWDBg3i8OHD7Nixg7Zt2/LUU0+dd+6MGTPo1q1brcqtS3/99RczZszg6quvZty4cTz88MOkp6cDla/ZXXfdVetrf/TRR6xbt+6yz7vjjjtISEiodblCWJPW3gGIxkWv13PXXXexYMECOnbsCMCvv/7KHXfcwfr16+ncuTMffPCBXWPcsmWL5e+YmBgiIiIu6/yMjAyeeuopli1bRosWLQCYP38+Dz/8MD/++GOdxloTPXr04LPPPrN5uReyfv16evfuzauvvlpn13z33XdZu3YtixYtokWLFuzYsQM/Pz/++usvysrKcHZ2BuDUqVMkJibWWbm1tXLlSubPn8/8+fMJCQlBURQ+//xzbr75ZlatWnXF19+xYwdt2rS57PO++OKLKy5bCGuRZETUqbKyMoqKiigtLbVsmzhxIm5ubphMJnbv3s3cuXP57bffzjv3ww8/JC4ujvz8fG6//XZuvPFGAD7++GNWrVqFRqOhdevWPP/88/j5+TFjxgxuvPFGRo8eDVDl8fHjx3n11VfJz8/HZDIxY8YMpk6dytNPPw3AzJkzuf3229mwYQNbtmzBycmJG2+8kfnz57N27VrMZjMtWrTgxRdfJCAgoEqceXl5GAyGKs9x5syZtGvXzvL4s88+45dffkGr1RISEsLrr7+Ou7v7JZ+Lp6cnJ06c4Prrr2fSpEm8+uqrHD16FIPBQN++fXnyySfRaq/sn+x7773H/v37MZvNPPzwwwwZMuSi9zguLo4FCxbwww8/ADBq1CjGjRvHgw8+yOnTp5k6dSqbNm1Cra6sYF2xYgWLFi3CZDJRXl7O22+/XePnO2PGjPNiNZvNzJkzh8OHD/PDDz/g7e1t2efl5UVwcDDr1q1jwoQJACxfvpwJEyZUSQh//vlnFi1ahNlsxsvLi+eff57w8HASExOZM2cOJSUlZGVl0a5dO9577z0cHR3p3Lkzd955J1u2bCEzM5NZs2Zxww03kJWVxVNPPUVeXh4AgwcP5uGHHz4v7nfffZe5c+cSEhICgEql4s4776R58+bo9foqx17qPfzBBx/w559/4uDggLe3N/PmzePPP//kwIEDvPnmm2g0GgYPHsxbb73Frl27MJlMdOjQgeeeew43NzeGDh1KVFQUR44c4dFHH2XevHm8//77lJaW8u677xIcHMyxY8cwGo28/PLLREdHk5uby9NPP01KSgpeXl74+fkRERHBAw88UKv3mxA1Jc00ok55enryxBNPMGvWLIYNG8YTTzzB0qVL6devHzqd7pLnBgcHs2zZMj766CNef/11DAYDS5cu5Z9//mHJkiWsXLmSiIgIZs+efcnrGI1GHnzwQR577DGWLVvGd999x4IFC4iNjWXevHkAfPvtt0yaNImhQ4dyyy23cOONN7J8+XKOHj3Kzz//zK+//srgwYN57rnnzrt+u3btuO6667jmmmsYO3Yszz33HH/99RcDBw4EKmsHli1bxuLFi/ntt99o2bIl3333XbXPxcPDg9WrVzNjxgxee+01OnbsyLJly1i+fDl5eXl8/fXXF3y+u3fvPq+ZZunSpRc8tmXLlvzyyy/873//Y/bs2eTm5l40rgEDBnDkyBEKCws5efIkJSUlbN261fIchw8fbklEoDLpnD59OmPHjuXtt9++rOd7odfwiSeeYNGiRdxzzz1VEpEzJk2axK+//mp5/Pvvv1dp3tm5cyfLly/n+++/Z/ny5cyaNYv7778fgJ9++olJkybx008/sXbtWk6ePMnff/8NVNbueXt78+OPP/LBBx8wb948Kioq+Omnnyz37/vvvyc5OZmioqIqMeXl5XHq1Cm6d+9eZbtKpbIk5TWRnp7Ot99+y9KlS1m2bBn9+/dn37593HjjjXTq1Iknn3ySESNG8Pnnn6PRaFi2bBkrVqzA39+ft956y3KdiIgIfv/9d0aMGFHl+vv27eO2225j+fLlTJ48mXfffReAV155hTZt2vD777/z/vvvs2fPnhrFK8SVkpoRUeduvfVWrr32Wnbt2sWuXbv44osv+OKLL1iyZMklzzvzRdK+fXv0ej3FxcVs2rSJyZMn4+LiAsDNN9/Mp59+et4vzHMlJSWRkpLCM888Y9lWXl7OoUOH6Nq160XP++uvv9i/fz9TpkwBKn+Zl5WVXfDY2bNnc9ddd7Fz50527drFm2++ycKFC/n+++/Ztm0bo0ePxtPTE8BSG/PQQw9d8rn06NHDcv2///6b/fv3W+5ZeXn5ReO+nGaa66+/HoDIyEjCw8PZu3fvRe+xWq2mX79+bNmyhby8PKZNm8bixYspKipiw4YNzJo165JlVffanft8/ysxMZFu3brxxhtvMHv2bJYtW0bz5s2rHDNkyBBeeuklsrOzSU5OJiwszHLPofIeJicnM336dMu2wsJC8vPzeeKJJ9iyZQtffPEFSUlJZGZmVqnpGjZsGAAdO3ZEr9dTWlrKwIEDufPOO0lPT6dfv3489thjuLu7V4npTHJmNpsveW+qExAQQLt27bjmmmsYNGgQgwYNom/fvucd9/fff1NUVGRJEg0GA76+vpb9F7vHQUFBtG/fHoAOHTrwyy+/ALBx40bL3/7+/pYaGyGsTZIRUadiYmLYu3cvs2bNYsiQIQwZMoRHH32U8ePHs2XLlgv+wj3jTBOESqUCQFEUzGaz5TFUfsgbjUbL43OXVjIYDACYTCbc3d2r/GrOzs4+74vjv8xms6VKHip/IRcUFJx33Pr168nPz2fKlCmMGjWKUaNG8cgjjzB48GAOHTqERqOpEnNhYSGFhYXVPpczX9pn9r3//vuEh4dbrnHuubV1bk2G2WxGq9VeMq7hw4ezadMmCgsLmTVrFidOnGDdunUcPXqUXr16XbKsy3m+/xUaGmqpxdqzZw8PPPAAP/zwQ5XaNZ1Ox8iRI1m1ahUJCQlcc80155V/9dVX88QTT1geZ2Zm4unpySOPPILJZGLMmDFcddVVpKenV3kvOTo6AlXfi1FRUaxfv55t27axfft2rr32Wr744gs6depkOc/T05PQ0FDi4uLo169flXgeeugh7rnnnvOe64Xew2q1mu+++479+/ezbds2XnvtNQYOHGjpmHzuc3zmmWcYPHgwACUlJVRUVFR7j52cnCx/q1QqSwxarbZKPOe+X4SwJnmniTrl4+PD/Pnz2b17t2VbVlYWxcXFREZGXvb1Bg4cyNKlSy2/WhcuXEjPnj3R6XT4+Phw4MABABISEjhy5AgArVu3xsnJyZKMpKenM378eMuxGo3G8qV47t8DBgxgyZIlFBcXA/D++++f9+EP4OrqyjvvvFNlZEJqaioajYZWrVrRr18//vzzT8t1PvzwQ7755ptLPpf/GjBgAN988w2KoqDX67nnnnv47rvvLvv+/deZX70HDx4kJSWFLl26XDKuoUOHsm3bNuLj44mKiqJ///68//77DBo0CI1Gc8myLuf5/peDg4Pl72effRaTycTLL7983nGTJk3il19+YdeuXZZmsjMGDBjAqlWryMzMBGDRokXMnDkTgM2bN3PfffcxduxYAOLi4jCZTJeM6a233uKTTz5h+PDhPPvss7Rp08YySuxc999/P6+++irJyclAZXL8ySefcPjwYcLCwqoce7H38OHDhxk/fjzh4eHcdddd3HLLLezfvx84/z37/fffo9frMZvNPP/887zzzjuXfB6XMnjwYEttXF5eHuvWrauTJFiI6kjNiKhTrVu35uOPP+bdd9/l9OnTODo64u7uzmuvvUZYWBhZWVmXdb2pU6eSnp7Otddei9lsJiQkxNImfs899zB79mw2btxIWFiYpUpap9PxySef8Oqrr/Lll19iNBp56KGHiI6OBmD06NHMmDGDDz/8kEGDBvH6668DlUMfMzIyuO6661CpVDRv3tyy71x9+vTh+eef56mnnqKoqAiNRoOfnx9ffPEFnp6eDB48mISEBEuTSJs2bZg7dy4uLi4XfS7/9eyzz/Lqq68yYcIEDAYD/fr1u2izyJk+I+c604/gv1JTU5k0aRIqlYp33nkHLy+vS95jd3d3wsPDcXZ2RqPRMHDgQJ599llGjhx5Ra/d5XB0dOT999/nmmuuISoqitDQUMu+bt26UVZWxtChQ8/r3DtgwADuuOMObrvtNlQqFW5ubnz00UeoVCoeeeQR7rvvPlxcXHBzc6Nnz56kpKRcMo6ZM2cye/Zsxo8fj06no23btowbN+684yZMmICi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9PTTTwMwc+ZM0tPTz4vtTDKSmprKDTfcQOvWrfnwww+rdO6866676NGjxwX/u+uuqrNqmkwmDhw4QF5eHiNGjGDQoEHMmTPHEn91nnzySQYNGsTWrVvZunUr999/PwALFixg/vz5zJ07l127dvHxxx/TokUL3nvvPf755x8WL17Mli1b0Ov1fPzxx1We3969exk2bBg7duzg5ptv5tNPP2XJkiXMnz+fbdu2ERAQwHvvvVcljst5zlDZ3KJWq2nd+uyaYe3atSMhIeGCz7O4uJgPPviA2bNnV3tPsrOzSUpKok2bNuft++WXX5g0aVKTG8J7MU1jardaSM0r4aFfduLmqGXB9H6o1fZ5w/i6taBn6/EoioJWc/HRCdnFqZTqC2jhHSn9RUS91KXLhRdrfOCBB5g1axYAd999t+XL/Fw9evTgq6++AuDbb7+94GrEcXFxNY4lKSmJd999l//7v//D29ubY8eOceutt/LKK69UOS49PZ233nqL7t27s3jxYp588kl+/vlntm3bxpdffsnixYvx8fFh2bJlPProo4wfP55NmzbRt29f/vnnHzw9Pdm9ezf9+/e3VNn/N+bMzEwWL16MWq3m888/54svviA6Opp58+axbNkyvv3224s206hUKmbOnMkzzzzD8OHDzzvms88+q/E9yc7OxmAw8Mcff/D999+j1Wq59957mT9/Po888ki156empmIymTCZTDg6OhIdHU1ubi4fffQRP/zwA+3atQOgbdu2ZGdn891337F69WrLnFKjRo1iyZIllusdPnyY22+/nWHDhgGVo0jmz5/PokWLLLN5T506lZdffrnWzxkqE87/jsZ0d3e/aA3Te++9x5QpU2jevPklr2swGHj88ce55pprzuvXk5aWxq5du3j11VcvK9bGTJKRc7y8Jo60tEw+7a4w66dtFJQb+PTaPrT2te9Cc+eOiqkwlpFRkEiwT/sqGXVydmU1YIhvJ5vHJ+qnRx99lJSUFHuHUS9t2bKFzMxMbrnlFss2lUpFcnJylePatm1L9+7dAbjmmmt46aWXKCoq4p9//mHs2LGWJGHy5Mm8+uqrjBgxgkcffZQnn3yS3bt3c8stt7BlyxZcXV1p1arVeaMDu3XrhqenJz/++COpqans2LGjRsNWFUXh6NGjpKamcsstt1wwEblcZ2a9njFjhiVBuPXWW2uc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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[38]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for KMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[40]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Within Sum-of-Squared</span>
<span class="n">kmeans_vis_wss</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">kmeans</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;distortion&quot;</span><span class="p">)</span>
<span class="n">kmeans_vis_wss</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">kmeans_vis_wss</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAiAAAAFlCAYAAADS9FNeAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAACOt0lEQVR4nOzdd3hUZfbA8e+dlt476SEJgUAgJPTee1VYxMXesOKuBbCtoMu6utjF8tOVxYIoRRCUjkiREiD0npBKepm0yZT7+yNkJEIKkMmkvJ/n4XmYmVtObpLJmfe+7zmSLMsygiAIgiAITUhh7QAEQRAEQWh7RAIiCIIgCEKTEwmIIAiCIAhNTiQggiAIgiA0OZGACIIgCILQ5EQCIgiCIAhCkxMJiNBo0tLS6NixI5MmTWLSpElMmDCBGTNmsGHDBvM27777LmvWrKnzOB988AFbtmy54fNfvV9DznMjduzYwV/+8hcmTpzIuHHjeOqpp7h8+XKjHb+hVq1aRVxcnPkaV/977rnnAJg7dy6ff/45AB06dCA/P9+i8Zw6dYrhw4czdepU0tLSbuoY+/btY/z48TWe++9//8vAgQM5ffo0+/bto0OHDjz//PPX7Dtr1ixiY2Nv6ryNafv27cyaNYtJkyYxbtw45syZQ2ZmJlD1PXv44Ydv+tg3+/vw4IMPcv78+Zs+ryBYmsraAQiti62tLT/++KP5cXp6Ovfccw9KpZJRo0bx1FNP1XuMffv2ER4efsPnvnq/hpynobKysnj++edZtWoV/v7+ACxZsoQ5c+awfPnyRjtPQ8XHx/PJJ580+XmvZ+vWrfTq1YvXX3+90Y759ttvs2nTJr799lv8/f3Zt28fXl5ebN++nfLycuzs7ICqn62kpKRGO+/NWrduHUuWLGHJkiUEBwcjyzKffvopd911F+vXr7/l49/s78Nnn312y+cWBEsSCYhgUf7+/jz55JN8/vnnjBo1irlz5xIREcH999/Pe++9x+bNm1Gr1bi5ubFo0SI2b97M8ePH+fe//41SqaR37968+uqrnD59GkmSGDBgAH/7299QqVR07tyZYcOGcfr0aSZMmFBjv61bt5rPc/DgQf79739TXl6OWq1mzpw5DBw4kFWrVrF582YUCgWXLl3C1taWN954g/bt29f4GgoKCtDr9ZSVlZmfu/vuu4mKijI//uSTT1i9ejUqlYrg4GD+9a9/4eTkxIcffsj69etRKpWEhoby0ksv4eXlxaxZs3BxceHixYvccccdTJ48mddff52zZ8+i1+vp06cPzz33HCrVrf2KvvPOOxw7dgyTycScOXMYMmQIwHXjSkxM5IsvvuCbb74BYNSoUYwbN44nn3ySy5cvc/vtt7Nz504UiqqB07Vr1/Ltt99iNBqpqKjgP//5T4O/3lmzZl0Tq8lkYsGCBZw+fZpvvvkGNzc382uurq4EBgayZcsWJkyYAMCaNWuYMGFCjSTw+++/59tvv8VkMuHq6spLL71E+/btSUpKYsGCBZSWlpKTk0NUVBTvvPMONjY2dOnShYceeojdu3eTnZ3NAw88wMyZM8nJyeH555+noKAAgEGDBjFnzpxr4n777bdZuHAhwcHBAEiSxEMPPYSfnx+VlZU1tp01axZ33nkno0ePvuZxQ34fBg0axFtvvcWBAwcwGo106tSJF198EUdHR4YOHUpMTAxnzpzhb3/7G4sWLeLdd9+lrKyMt99+m8DAQM6dO4fBYODVV18lLi6O/Px85s2bR0pKCq6urnh5eREREcETTzxxUz9vgnAjxC0YweKioqI4e/ZsjecyMzNZunQpK1euZNWqVfTr14+jR49y55130rlzZ5577jlGjBjBa6+9hqurK+vWrWPlypWcOXOGL774AgC9Xs+QIUPYuHEjjz/+eI39qhUUFPDkk0/ywgsvsG7dOt544w2effZZUlNTAThw4AAvvfQSP/30E127duXTTz+9bvzTp09nypQpjB07lhdffJHt27czYMAAoGoUYNWqVXz33Xf89NNPBAQE8NVXX7Fy5Up+++03fvjhB9atW0dERARz5841H9fZ2ZkNGzYwa9Ys/vnPfxIdHc2qVatYs2YNBQUF/Pe//73u9Tx48OA1t2BWrlx53W0DAgJYvXo1b775JnPnziU/P7/WuPr378+ZM2coLi4mLS2N0tJS9uzZY/4ahw8fbk4+ACZOnMiMGTMYO3Ys//nPf27o6/0zg8HAs88+y7fffsvs2bNrJB/VJk+eXGN07eeff65x62b//v2sWbOGr7/+mjVr1vDAAw/w+OOPA7BixQomT57MihUr2LRpE2lpaezYsQOAyspK3NzcWL58Oe+99x6LFi1Cp9OxYsUK8/X7+uuvuXTpElqttkZMBQUFpKen07179xrPS5LExIkTcXR0vO735c8a+vvw6aefolQqWbVqFWvXrsXb25u33nrLfJyIiAh+/vnnGr8DAEePHuW+++5jzZo1TJ06lbfffhuA1157jfDwcH7++WfeffddDh061KB4BaExiBEQweIkScLW1rbGcz4+PkRFRTFlyhQGDhzIwIED6dOnzzX77ty5k2+//RZJktBoNMyYMYOlS5fy0EMPAVW3I+py9OhRgoKC6Nq1K1D1Bt29e3f279+PJElER0fj6+sLQKdOndi8efN1jzN37lwefvhh9u/fz4EDB/j3v//NsmXL+Prrr9m7dy+jR4/GxcUFgHnz5gFVt4GmTp2Kvb09AHfddRcff/yx+VPx1bHv2LGDY8eO8cMPPwBQUVFR69d0I7dg7rjjDgAiIyNp3749hw8fZufOndeNS6FQ0LdvX3bv3k1BQQF/+ctf+O6779BqtWzbto0HHnigznPVdtzrfb1/lpSURGxsLG+88QZz585l1apV+Pn51dhmyJAh/OMf/yA3N5dLly4RFhZmvuZQdQ0vXbrEjBkzzM8VFxdTWFjIs88+y+7du/nss89ITk4mOzu7xojWsGHDAIiOjqayspKysjIGDBjAQw89RGZmJn379uXvf/87Tk5ONWKqTshMJlOd16Y+Df192LFjB1qt1pwY6vV6PDw8zK/Xdo3btWtHx44dgaqf89WrVwPw66+/mv/v7e1tHpkRhKYgEhDB4o4dO0ZkZGSN5xQKBV999RXHjh1j7969/POf/2TAgAHmyZTVTCYTkiTVeGwwGMyPq//Y1cZoNNbYH0CWZQwGA2q1ukZiJEkS12uNtHXrVgoLC7ntttsYNWoUo0aN4umnn2bQoEGcPHkSpVJZ4xzFxcUUFxffUOwmk4l3333XfPunuLj4mrhvxtUjFiaTCZVKVWdcw4cPZ+fOnRQXF/PAAw9w8eJFtmzZwtmzZ+nZs2ed57qV71VISAiLFi0C4NChQzzxxBN88803aDQa8zYajYaRI0eyfv16zp8/z5QpU645/6RJk3j22WfNj7Ozs3FxceHpp5/GaDQyZswYBg8eTGZmZo3vtY2NDYA5flmWiYmJYevWrezdu5fff/+dadOm8dlnn9G5c2fzfi4uLoSEhJCYmEjfvn1rxPPUU08xe/bsa77Wq8+r1+uBG/t9mD9/PoMGDQKgtLQUnU5X7zWu7edcpVLViOfqnxdBsDTx0yZYVFJSEh999BH33XdfjedPnz7N+PHjad++PQ8//DD33HMPx44dA0CpVJr/cPXv35+vvvoKWZaprKxkxYoV17zRV7t6v2rdunXj4sWLHD16FIBz585x4MCBev+YXs3BwYHFixfXWFGQmpqKUqkkKCiIvn37snnzZkpKSgB4//33+fLLLxkwYAArV640f9JetmwZPXr0qPFHtVr//v358ssvzV/n7Nmz+eqrrxocY22qP92eOHGClJQUunbtWmdcQ4cOZe/evZw6dYqYmBj69evHu+++y8CBA1EqlXWe60a+3j9Tq9Xm/7/wwgsYjUZeffXVa7abPHkyq1ev5sCBA+ZbYNX69+/P+vXryc7OBuDbb7/l7rvvBmDXrl089thjjB07FoDExESMRmOdMb311lt89NFHDB8+nBdeeIHw8HDOnTt3zXaPP/44r7/+OpcuXQKqkt6PPvqI06dPExYWVmNbd3d3jh8/DsD58+c5c+YMcGO/D19//TWVlZWYTCZeeuklFi9eXOfXUZdBgwaZR90KCgrYsmVLoyS+gtAQYgREaFQVFRVMmjQJqPo0ZWNjw9/+9jcGDx5cY7uoqCjGjBnDbbfdhr29Pba2trz44osADB06lMWLF6PX63nxxRd57bXXmDBhAnq9ngEDBvDII49c99xX71fN3d2dd999l4ULF1JRUYEkSSxatIjQ0FAOHz7coK+pd+/evPTSSzz//PNotVqUSiVeXl589tlnuLi4MGjQIM6fP2++3REeHs7ChQuxt7cnMzOTadOmYTKZCA4OrnG//movvPACr7/+uvnr7Nu3b623PKrngFytel7An6WmpjJ58mQkSWLx4sW4urpy++231xqXk5MT7du3x87ODqVSyYABA3jhhRcYOXJkvdepruPeCBsbG959912mTJlCTEwMISEh5tdiY2MpLy9n6NCh10zQ7d+/Pw8++CD33XcfkiTh6OjIBx98gCRJPP300zz22GPY29vj6OhIjx49SElJqTOOu+++m7lz5zJ+/Hg0Gg0dOnRg3Lhx12w3YcIEZFnmb3/7GwaDAZ1OR3R0NEuXLr0m+Zo9ezZz587l119/JSwszHzLpKG/D48++ihvvPEGU6ZMwWg00rFjxxrzbG7UvHnzePHFF5kwYQKurq60a9fumtulgmApkny9MWdBEASh1fv666/p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hvL+++/j4OBg3ubhhx8mPj7+uv8efvjh616X//znP/Tq1YsZM2aYq043xHPPPWduELpnzx4ef/xxAL744guWLFnCwoULOXDgAB9++CH+/v688847/Pbbb3z33Xfs3r2byspKPvzwwxpf3+HDhxk2bBj79u3jrrvu4uOPP2b58uUsWbKEvXv34uPjwzvvvFMjjrq+5ieffLLBXw9UjbocP36cgoICRowYwcCBA1mwYIH5ewpw1113sX79esrLy8nKyuK3335jwIAB9R47NzeX5ORkwsOrfq9KSkp47733rnsL6FbO0xa0yVUw1apHOzIyMhjcNYq/fr2LeesPs/yugVaOTBBunMGox9nOHV+XEIw57rRvF4jeWFH/jg1Q3RPnz5544gnzJN1HHnnkuqNF8fHxfP755wAsXbqUxYsXX7NNQ3vtJCcn8/bbb/O///0PNzc3zp07x7333strr71WY7vMzEzeeustunfvznfffcdzzz3H999/z969e/m///s/vvvuO9zd3Vm1ahWPPfYYY8eOZefOnfTp04fffvsNFxcXDh48SL9+/fj111+ZM2fONfFmZ2fz5Zdf4uTkxKeffspnn31GXFwcixYtYtWqVSxduhR3d/drvoazZ88iSRJ333038+fPZ/jw4dds88knnzToelR75plnaN++PRqNhvXr1/PII4/w448/EhQUVO++qampGI1GjEYjNjY2xMXFkZ+fzwcffMA333xDVFQUAB06dCA3N5evvvqKDRs2mDudjxo1ih9++MF8vNOnT3P//fczbNgwoKq0/5IlS1izZg3BwcEA3H777bz66qsN/ppvdHQoNzcXvV7PL7/8wtdff41KpeLRRx9lyZIlPP300wD07NmT77//nri4OIxGI1OmTLnu9+Jqer2eZ555hilTppjn8Lzzzjvcdttt+Pn5XXefmzlPW9FmR0CqvTKqKw/FeDMjNoSeQR58n3iJPUnZ1g5LEG6YSqmmX8TtdAsagYyRA0nrOZmxG1luPZUVd+/eTXZ2Nvfccw+TJk3imWeeQZIkLl26VGO7Dh060L17dwCmTJnC8ePH0Wq1/Pbbb4wdO9acGEydOpWsrCxGjBjBzp07kWWZgwcPcs8997B7926OHDlCUFAQXl5eNY4fGxvLnDlzWLlyJW+88Qa//PJLg/5IyrLM2bNn2bJlCzNmzGi0P0Rd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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[40]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Distortion Score Elbow for KMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;distortion score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Hierarchical-clustering">Hierarchical clustering<a class="anchor-link" href="#Hierarchical-clustering">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[42]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Silhouette</span>
<span class="n">hclust_vis_sil</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">hclust</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;silhouette&quot;</span><span class="p">)</span>
<span class="n">hclust_vis_sil</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">hclust_vis_sil</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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ajtWWlpamRjWr18vz58/XzabzbIsy/KPP/4o33fffeWe47Jly+QuXbrI48ePl1988UX5t99+s5Xbtm2bPGbMGDkzM1OWZVleunSpvHLlyirP5fnnn7ft/7nnnpO//vprWZZl2WKxyE899ZT8ySeflInj559/lnv16iVPmTKl1L+ffvqp3Gv88ccfy7Isy5GRkXK/fv3ktLS0CuPKz8+Xe/XqJWdlZclxcXHyoEGD5JkzZ8qyLMvffvut/PLLL5eJZ8WKFfKrr74qy7J8TedbktlslgcPHizv2LFDLiwslPv27Sv//fffsizLcnp6utyvXz/59OnTsizL8rp16+SQkBA5Li5O/uGHH+Q77rhDLigokAsLC+V7771XvvPOO23H+/333+Xz58/LAwcOlGNjY2VZluV9+/bJgwYNkrOzs+UVK1bIw4cPl41Go5yfny/37dtXXrZsmSzLsvznn3/KY8aMkWW58tfJ1ef1+OOPywcOHJBlWZZzcnLk/v37y8ePH5dlWZaHDx8uHzt2rFR8sbGxcv/+/eXCwkJZlmX5sccek//3v//JmZmZ8pgxY+S4uDhZlmX58uXL8tChQ+VLly7Jn3/+ufzoo4+Wey2LFe8/Li5O7tGjh215yccffvih/NJLL8myLMu5ubny/PnzZaPRWGqbyt5bBw4ckDt27CjHx8fLslz2vT5z5ky5sLBQNplM8rRp0+Sffvqp0uezpPT0dDkkJMT2OVKen3/+WZ47d26p8736/BMSEuRevXrZru/nn38u//nnn2XKfPDBB/Lrr78uS5Iky7Isv/3227bX+/Dhw+UPP/zQtu/i5/HAgQNyp06d5FOnTtn2fccdd8iyXPQ6eOONN2RZluWkpCR50KBB8ooVKyp+woQmQ9S4NBL33HMPt9xyC4cPH+bw4cN8+umnfPrpp/z000+Vliv+NdupUydMJhM5OTns2rWL6dOn4+joCMBdd93F6tWry/zCKik6OprY2FheeOEF27KCggJOnTpFjx49Kiz3119/cfz4cW6++WYAJEmqsH3Fc889x7x58zh06BCHDx/mjTfe4JtvvuG7775j//79jBs3DldXVwBbLc9jjz1W6bn06dPHtv+///6b48eP265ZQUFBhXFfy62i4lsuISEhBAcHc/To0QqvsVKpZODAgezdu5eMjAxmzpzJmjVryM7OZseOHdx3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oaFA0RfxihUreOONNygsLESWZd544w1bYrJixQreffddpk+fjkqlQpIkpk2bxn/+859S+3Z2dubpp5/m//7v//Dw8Ch1y2LOnDk899xzTJo0Ca1WS4cOHZg4cSIqlYrQ0FAmTpzId999V+F76+DBg9W+hsXc3NwqfD6vNnnyZGRZ5oknnsBisVBYWEiXLl346quvyiTDFX02dOzYkfHjx3PzzTfj6OiIXq9nwYIFAIwYMYJ33nkHs9nMgw8+yPLly7npppuwWq106tSJ55577prPr9jzzz/PggULmDx5Mm5ubvj7+5eqnRGaLoVcGzdyBUFotHJycli5ciWPPPIIDg4OnDx5knnz5rF792727t1LWlqaLYlbvHgxOp2Op59+2s5RCxWp7PlsSjUS3333HZ07d6Znz56YTCZuv/12HnnkEdutKKHpEjUugtDMGQwGNBoNM2bMQK1Wo1aree+991AoFLRv357PP/+czz77DEmS6NixY5naDKFhqez5bEqKa10lScJsNjNu3DiRtDQTosZFEARBEIRGQzTOFQRBEASh0RCJiyAIgiAIjUajbuNisVhIS0tDr9eLPvyCIAhCkydJEgUFBXh6el73dCWNVaM+67S0tOueLVcQBEEQGqOr53xrLhp14lLcZ79Vq1aVji55Lc6ePVujQd2EayOuc927++67sVgstTLInlA18ZquH839Oufl5REfH9+sx6xp1IlL8e0hR0fHaxrsqiq1uS+hYuI6163XXnuNU6dOietcj8S1rh/iOjfvKQ4adeIiCELFOnfuXOGEloIgCI1V803ZBEEQBEFodESNiyA0Ud27d8dkMnH69Gm7HL94hujmNMalyWSydwjNQlO/zkqlstn2GKoOUeMiCEKty8vLIzs7G6vVau9Q6k1wcLC9Q2gWmsN1NplMZGdn2zuMBkukdIIg1Cqr1YokSbi4uNg7lHplNpvLzKgs1L7mcJ21Wi15eXlYLBZR81IOcUUEoYnKzDfZpcbDarU2+S8WQahrKpUKSZJqVFaWJfZf+JWM3ESUChWD2t+Mi4OXbX1c2inC43agVChp79uHEL9+FZbJzEti3/l1IIO7Uwv6B09BqVBy9vIhIi8fRKFQ0j1gBAEenbBYzew++yP55lw0Kh1DQm5BrzHU1iWxEbeKBKEJenVLBFkFZnLMEq9uibB3OIIgXKPrmc07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vffeS0xMDFOnTmX//v1A0Zd1t27dKCgoaqD44osv8v3335favyRJLF68mFtuuYUJEyYwfvx4W43Y888/D8CcOXNITEwsE1tkZCQhISHExcVx++2307ZtWz744INSScu8efPo06dPuf/mzZtXan9Wq5UTJ06QkZHB6NGjGTp0KIsWLbLFX5VnnnmGoUOHsm/fPvbt28fDDz8MwBdffMGqVat47bXXOHz4MB999BEtW7bkvffeY/fu3axZs4a9e/diMpn46KOPSp3f0aNHGTlyJAcPHuSuu+5i9erV/PTTT6xatYr9+/fj6+vLe++9VyqOazlnKLrlo1Qqadu2rW1Zx44dOX/+fLnnmZOTw4oVK3juueeqvCapqalER0fTrl27az6OULE6q3EZPXo0e/fuZdasWciyzNKlS9m4cSN5eXml2rWUtHr1aoxGIytXrmTlyqLqqk8//RS9Xl/u9rWphVs7PJz82XB4FS3cgkTSIjRKVkni6Y1hKBRg0KlBkvjvbYPo4ufGs7/9w+3f7mbrvFGoVfU/hFP37uX3aHrkkUe47777ALj//vttX/wl9enTh88//xyAr776infeeafMNhER1W94HB0dzbvvvsvXX3+Nu7s7586d45577mHx4sWltktMTOStt96iV69erFmzhmeeeYa1a9eyf/9+PvvsM9asWYOHhwfr1q3jiSeeYNKkSezatYsBAwawe/duXF1dOXLkCIMGDWLnzp1lbn9HRESQnJzMmjVrUCqVfPLJJ3z66af07t2bZcuWsW7dOr766is8PDzKnMPZs2dRKBTMmTOHF154gVGjRpXZ5uOPP672NUlNTcVsNvPHH3/w3XffoVarefDBB1m1ahWPP/54leXj4uKwWq1YrVZ0Oh29e/cmPT2dDz/8kO+//56OHTsC0KFDB1JTU/n222/ZvHkzPj5FNQFjx47lp59+su3vzJkz/Oc//7H1LM3OzmbVqlX88MMPth6qM2bM4NVXX63xOUNRcnp1zZKzs3OFt6Pee+89br75Zlq0aFHpfs1mM0899RQ33XQTwcHBHDly5JqOI1SszhIXpVLJokWLSi0r7z7e9OnTbX8vWLCABQsW1FVIVdKqHVCiJvvfxrqC0Nh8cegCxxMzubtvMEf+1Nlu2zx5Y2cOxKSy/ngsL24+yvLJzfs23d69e0lOTubuu++2LVMoFMTE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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[42]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for AgglomerativeClustering Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[41]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Within Sum-of-Squared</span>
<span class="n">hclust_vis_wss</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">hclust</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;distortion&quot;</span><span class="p">)</span>

<span class="n">hclust_vis_wss</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
<span class="n">hclust_vis_wss</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>        <span class="c1"># Finalize and render the figure</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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tVMPHDhgi6V169ZqZGSkunz5cjUkJES9dOmSqqqqOmPGDPW1117L9bnNmjVLbdSokdqnTx/1jTfeUP/880/VZDKpqqqq69evV3v16qUmJCSoqqqq7777rrpgwQL1119/VR999FE1JSVFVVVVnTt3rjpy5EhbrJMmTbJt//XXX1e/++47VVVV1Ww2q6+88or6+eef54hj+fLlaosWLdSHHnoo279ff/012/POPD6Zx+rEiRNq69at1bi4uDzjSktLU1u0aKFev35djYqKUjt06KA++uijqqqq6vfff69Onz49Rzxz585V33rrLVVV1Tt6vlmZTCa1Y8eO6saNG1WDwaC2atVK3bx5s6qqqnrt2jW1devW6rFjx1RVVdUVK1aoQUFBalRUlPrTTz+pw4YNU9PT023vjccff9y2v7///ls9ffq02r59ezUyMlJVVVXdsWOH2qFDBzUpKUmdO3eu2rVrVzUxMVFNS0tTW7Vqpc6aNUtVVVVdt26d2qtXL1VVVXXlypXqhAkTbK/30qVL1WeeeSbX5/XSSy+pu3btUlVVVZOTk9U2bdqohw4dUlVVVbt27aoePHgwW3yRkZFqmzZtbJ+DF198UV22bJmakJCg9urVS42KilJVVVUvX76sdu7cWb148aL61VdfqePHj8/1WGbK3P6tn8mst+fPn69OnTpVVVVVTUlJUSdMmKAmJiZmW8ZkMqn333+/evjwYVVVVTUxMVHt06ePun//fnXXrl1q/fr11QsXLqiqqqq7du1SH3jgAVVVM96Hjz76qGowGFSj0ag+/PDD6q+//nrb1zOra9euqUFBQWpqamqez3H58uXqc889l+353vr8C/o9M2/ePPW9995TrVarqqqq+tFHH9ne7127dlXnz59v23bm67hr1y61QYMG6tGjR23bHjZsmKqqGe+D999/X1VVVY2JiVE7dOigzp07N+8XTNiFtFSUUoqi4OTklO0+f39/6tevT//+/encuTOdO3emXbt2OdbdsmULP/30E4qioNfrGTJkCN9++y3PPfcckHEp4HYOHjxIYGAgTZs2BaBu3bq0aNGCPXv2oCgKjRo1IiAgAICGDRuybt26XLfz+uuvM2rUKPbs2cPevXt5//33WbJkCT/88AM7d+6kd+/eVKhQAYBJkyYBGZdgBgwYgIuLCwBPPPEEixYtsv3Kyhr75s2bOXToEL/++isA6enpeT6nO7n8kXkZISgoiNq1a7N//362bNmSa1wajYb27duzfft24uPjefTRR/n5559JSkpi48aNPPPMM7fdV17bze35ZrVhwwasViudOnVCp9Nx//33891339GlSxf27dtH7dq1ba1C/fv35+233wYyftX369cPR0dHAB599NEcrRS7du2ibdu2VKtWDYB27drh7e1t69vQvn173N3dAfDz86NTp04ABAYGkpCQAGRc1z906BCPPPIIAFarNVu/j6zP67333mPLli0sWrSIs2fPYjAYsrVw3apatWrUq1ePjRs30q5dO3bt2sU777zDvn37iI2NZcyYMbZlFUXhxIkTaDQaW9+Je9GpUyeee+45Ll26RPv27fnf//6Hu7s7169fty0TERFBZGQkkydPtt2Xnp7O0aNHqV27NpUqVbJdEsxt+3q9Hsh4/12/fv22r2dWma1hVqv1np5jQb9nNm/eTFJSkq2fi8lkwsfHx/Z4Xu/dypUr06BBAyDj+2PlypVAxnsz828/Pz9bC4ooWSSpKKUOHTpEUFBQtvs0Gg3ff/89hw4dYufOnbz77rt06tTJ1uEwk9VqtTWDZ942m82225knsLxYLJZs60PGNWmz2YyDg0O2ZEdRlFy/rDds2EBCQgKPPPIIoaGhhIaG8tJLL9GlSxeOHj2KVqvNto/ExEQSExPvKHar1cqnn35qu/SSmJiYI+67kfnlnLkPnU5327h69OjBli1bSExM5JlnnuHs2bOsX7+ekydP0rp169vu625fqx9//JH09HR69eoFYLt0cOrUKbRabY7XJPM53XppKOtzzSsmuPn6A7aTXqbcLjdZrVaeeeYZhg4daosv64k36/N6/PHHqVevHp06daJPnz6Eh4fnmwAMHjyY3377jbi4OHr06IGrqysWi4XatWvzyy+/2JaLiYnB29sbT09Pvv32WywWi+3yB2Qk0EuWLOGDDz6w3Xfre9pkMtn+Dg4OZsOGDezcuZNdu3YxaNAgvvjiCzw9PW3LWCwW3N3ds/WTunr1Ku7u7hw4cOC2n7/cPlu3ez2zqlChAjVq1CA8PJz27dtne+zFF19k9OjROdbJ7XneyffM5MmT6dKlCwApKSkYDAbb43k9z7y+P3Q6XbZ4cnuOwv7kVSmFzp07x4IFCxg5cmS2+48fP86DDz5I7dq1GTVq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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[41]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Distortion Score Elbow for AgglomerativeClustering Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;distortion score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Menerapkan-Metode-Clustering">Menerapkan Metode Clustering<a class="anchor-link" href="#Menerapkan-Metode-Clustering">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="K-means">K-means<a class="anchor-link" href="#K-means">&#182;</a></h4>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Berdasarkan kedua kriteria tersebut, banyaknya cluster terbaik yang dipilih berbeda. Jika demikian, banyaknya cluster bisa ditentukan berdasarkan kemudahan interpretasi cluster 
yang terbentuk. Pada tulisan ini kita akan menggunakan 5 cluster saja.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[44]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">kmeans</span> <span class="o">=</span> <span class="n">KMeans</span><span class="p">(</span><span class="n">n_clusters</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">kmeans</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[44]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>KMeans(n_clusters=5)</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Hierarchical-clustering">Hierarchical clustering<a class="anchor-link" href="#Hierarchical-clustering">&#182;</a></h4>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Berdasarkan kedua kriteria tersebut, banyaknya cluster terbaik yang dipilih adalah 6 cluster.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[73]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hclust</span> <span class="o">=</span> <span class="n">AgglomerativeClustering</span><span class="p">(</span><span class="n">n_clusters</span><span class="o">=</span><span class="mi">6</span><span class="p">)</span>
<span class="n">hclust</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">mall_scale</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[73]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>AgglomerativeClustering(n_clusters=6)</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[82]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall_hclust</span> <span class="o">=</span> <span class="n">mall</span><span class="o">.</span><span class="n">assign</span><span class="p">(</span><span class="n">labels</span> <span class="o">=</span> <span class="n">hclust</span><span class="o">.</span><span class="n">labels_</span><span class="p">)</span>
<span class="n">mall_hclust</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[82]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Interpretasi-Hasil-Cluster">Interpretasi Hasil Cluster<a class="anchor-link" href="#Interpretasi-Hasil-Cluster">&#182;</a></h4>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="K-means">K-means<a class="anchor-link" href="#K-means">&#182;</a></h4>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>interpretasi setiap cluster  yang terbentuk dapat dilakukan dengan menggunakan bantuan nilai rata-rata dari masing-masing peubah (centroid) dihitung berdasarkan cluster. Karena kita melakukan standarisasi peubah, maka nilai rata-rata yang diperoleh juga dalam skala standarisasi.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[66]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cluster_centers</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">kmeans</span><span class="o">.</span><span class="n">cluster_centers_</span><span class="p">,</span><span class="n">columns</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">mall</span><span class="p">))</span>
<span class="n">cluster_centers</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[66]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
      <td>-0.980679</td>
      <td>-0.743060</td>
      <td>0.467440</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.073331</td>
      <td>0.974945</td>
      <td>-1.197297</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1.204841</td>
      <td>-0.235773</td>
      <td>-0.052368</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.531074</td>
      <td>-1.290508</td>
      <td>-1.236467</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-0.428806</td>
      <td>0.974847</td>
      <td>1.216085</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Selanjutkan kita ubah nilai yang masih dalam bentuk standarisasi ke bentuk awalnyanya dengan method <code>inverse_transform</code></p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[71]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">cluster_centers</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">scale</span><span class="o">.</span><span class="n">inverse_transform</span><span class="p">(</span><span class="n">kmeans</span><span class="o">.</span><span class="n">cluster_centers_</span><span class="p">),</span><span class="n">columns</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">mall</span><span class="p">))</span>
<span class="n">cluster_centers</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[71]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
      <td>25.185185</td>
      <td>41.092593</td>
      <td>62.240741</td>
    </tr>
    <tr>
      <th>1</th>
      <td>39.871795</td>
      <td>86.102564</td>
      <td>19.358974</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55.638298</td>
      <td>54.382979</td>
      <td>48.851064</td>
    </tr>
    <tr>
      <th>3</th>
      <td>46.250000</td>
      <td>26.750000</td>
      <td>18.350000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32.875000</td>
      <td>86.100000</td>
      <td>81.525000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Hierarchical-clustering">Hierarchical clustering<a class="anchor-link" href="#Hierarchical-clustering">&#182;</a></h4>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>interpretasi setiap cluster yang terbentuk dapat dilakukan dengan menggunakan bantuan nilai rata-rata dari masing-masing peubah (centroid) dihitung berdasarkan cluster.</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[86]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mall_hclust</span><span class="o">.</span><span class="n">groupby</span><span class="p">(</span><span class="s1">&#39;labels&#39;</span><span class="p">)</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[86]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Dengan centroid diatas kita bisa melakukan interpretasi seperti pada K-means. Silahkan dicoba!</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2 id="Supervised-Methods">Supervised Methods<a class="anchor-link" href="#Supervised-Methods">&#182;</a></h2>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Data">Data<a class="anchor-link" href="#Data">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Data yang digunakan pada tutorial kali ini adalah data yang bernama Pima Indian Diabetes yang sudah sedikit diedit. Berikut adalah informasi singkat mengenai data</p>
<p>This dataset is originally from the National Institute of Diabetes and Digestive and Kidney Diseases. The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset. Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years old of Pima Indian heritage.</p>
<p>Content
The datasets consists of several medical predictor variables and one target variable, Outcome. Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on.</p>
<p>Acknowledgements
Smith, J.W., Everhart, J.E., Dickson, W.C., Knowler, W.C., &amp; Johannes, R.S. (1988). Using the ADAP learning algorithm to forecast the onset of diabetes mellitus. In Proceedings of the Symposium on Computer Applications and Medical Care (pp. 261--265). IEEE Computer Society Press.</p>
<p>data ini bisa diperoleh di link berikut ini <a href="https://github.com/gerrydito/Model-Klasifikasi/tree/master/Praktikum/KNN">Pima Indian Dataset</a></p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Import-Data">Import Data<a class="anchor-link" href="#Import-Data">&#182;</a></h3>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[89]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">diabetes</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;diabetes.csv&quot;</span><span class="p">)</span>
<span class="n">diabetes</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[89]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Menentukan-metode-supervised-learning">Menentukan metode supervised learning<a class="anchor-link" href="#Menentukan-metode-supervised-learning">&#182;</a></h3>
</div>
</div>!pip install xgboost
!pip install lightgbm<div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[111]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
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

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Menentukan-Metode-pembagian-data">Menentukan Metode pembagian data<a class="anchor-link" href="#Menentukan-Metode-pembagian-data">&#182;</a></h3>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[105]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#cross validation</span>
<span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="kn">import</span> <span class="n">cross_validate</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="Melakukan-Proses-Evaluasi-model">Melakukan Proses Evaluasi model<a class="anchor-link" href="#Melakukan-Proses-Evaluasi-model">&#182;</a></h3>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[143]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
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

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
<pre>C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\svm\_base.py:985: ConvergenceWarning: Liblinear failed to converge, increase the number of iterations.
  warnings.warn(&#34;Liblinear failed to converge, increase &#34;
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\sklearn\linear_model\_logistic.py:763: ConvergenceWarning: lbfgs failed to converge (status=1):
STOP: TOTAL NO. of ITERATIONS REACHED LIMIT.

Increase the number of iterations (max_iter) or scale the data as shown in:
    https://scikit-learn.org/stable/modules/preprocessing.html
Please also refer to the documentation for alternative solver options:
    https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression
  n_iter_i = _check_optimize_result(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>[12:47:57] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
<pre>C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
<pre>C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
<pre>C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\sklearn.py:1146: UserWarning: The use of label encoder in XGBClassifier is deprecated and will be removed in a future release. To remove this warning, do the following: 1) Pass option use_label_encoder=False when constructing XGBClassifier object; and 2) Encode your labels (y) as integers starting with 0, i.e. 0, 1, 2, ..., [num_class - 1].
  warnings.warn(label_encoder_deprecation_msg, UserWarning)
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain">
<pre>[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
[12:47:58] WARNING: C:/Users/Administrator/workspace/xgboost-win64_release_1.4.0/src/learner.cc:1095: Starting in XGBoost 1.3.0, the default evaluation metric used with the objective &#39;binary:logistic&#39; was changed from &#39;error&#39; to &#39;logloss&#39;. Explicitly set eval_metric if you&#39;d like to restore the old behavior.
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>


<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="application/vnd.jupyter.stderr">
<pre>C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
C:\ProgramData\Anaconda3\lib\site-packages\xgboost\data.py:112: UserWarning: Use subset (sliced data) of np.ndarray is not recommended because it will generate extra copies and increase memory consumption
  warnings.warn(
</pre>
</div>
</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[145]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">score_cv_fin</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span><span class="s2">&quot;models_name&quot;</span><span class="p">,</span><span class="n">models_name</span><span class="p">,</span><span class="kc">True</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[146]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">score_cv_fin</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[146]:</div>



<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/html">
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
      <td>0.026403</td>
      <td>0.016926</td>
      <td>0.758000</td>
      <td>0.916327</td>
      <td>0.816763</td>
      <td>0.831185</td>
    </tr>
    <tr>
      <th>0</th>
      <td>lsvc</td>
      <td>0.036734</td>
      <td>0.005009</td>
      <td>0.597193</td>
      <td>0.691837</td>
      <td>0.684665</td>
      <td>0.613448</td>
    </tr>
    <tr>
      <th>0</th>
      <td>tree</td>
      <td>0.004004</td>
      <td>0.006395</td>
      <td>0.703474</td>
      <td>0.765306</td>
      <td>0.676741</td>
      <td>0.770536</td>
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
      <td>0.027202</td>
      <td>0.008802</td>
      <td>0.768632</td>
      <td>0.883673</td>
      <td>0.818321</td>
      <td>0.832492</td>
    </tr>
    <tr>
      <th>0</th>
      <td>rf</td>
      <td>0.237783</td>
      <td>0.034401</td>
      <td>0.763316</td>
      <td>0.861224</td>
      <td>0.823006</td>
      <td>0.824842</td>
    </tr>
    <tr>
      <th>0</th>
      <td>gb</td>
      <td>0.184600</td>
      <td>0.007326</td>
      <td>0.763281</td>
      <td>0.861224</td>
      <td>0.830301</td>
      <td>0.825215</td>
    </tr>
    <tr>
      <th>0</th>
      <td>knn</td>
      <td>0.003198</td>
      <td>0.010401</td>
      <td>0.724649</td>
      <td>0.828571</td>
      <td>0.747381</td>
      <td>0.796843</td>
    </tr>
    <tr>
      <th>0</th>
      <td>nn</td>
      <td>0.381292</td>
      <td>0.008000</td>
      <td>0.699596</td>
      <td>0.785714</td>
      <td>0.709765</td>
      <td>0.769856</td>
    </tr>
    <tr>
      <th>0</th>
      <td>lda</td>
      <td>0.004802</td>
      <td>0.005736</td>
      <td>0.770018</td>
      <td>0.881633</td>
      <td>0.827400</td>
      <td>0.832638</td>
    </tr>
    <tr>
      <th>0</th>
      <td>qda</td>
      <td>0.000800</td>
      <td>0.006400</td>
      <td>0.736737</td>
      <td>0.836735</td>
      <td>0.808910</td>
      <td>0.805109</td>
    </tr>
    <tr>
      <th>0</th>
      <td>xgb</td>
      <td>0.082608</td>
      <td>0.009601</td>
      <td>0.732702</td>
      <td>0.812245</td>
      <td>0.785804</td>
      <td>0.797685</td>
    </tr>
    <tr>
      <th>0</th>
      <td>et</td>
      <td>0.104361</td>
      <td>0.017604</td>
      <td>0.763263</td>
      <td>0.863265</td>
      <td>0.815199</td>
      <td>0.825260</td>
    </tr>
    <tr>
      <th>0</th>
      <td>lgb</td>
      <td>0.054860</td>
      <td>0.006751</td>
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
</body>







</html>
