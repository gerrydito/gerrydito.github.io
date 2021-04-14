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
<br>
<br>
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
<p>Data bisa diperoleh di link berikut <a href="https://drive.google.com/file/d/1P3WVtw2njbEcxV5y3-5hvO6P52D7j7MB/view?usp=sharing">Mall Customer</a></p>

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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[1]:</div>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[2]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[2]:</div>



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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[3]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[3]:</div>



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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[4]:</div>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[5]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[5]:</div>




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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[6]:</div>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[7]:</div>
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
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAiMAAAFlCAYAAAA5w+hdAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAACWz0lEQVR4nOzdd1xV9f/A8de5kwuXvUQElOXeaLlz5syRpWWOpu36tfew3be9bHy/lS2zUlOz0tTSQnODe4AoU/a6wN3n9wdyFRFBBe4FPs/Hw8eDe8963+OF+76f8f5IsizLCIIgCIIgOInC2QEIgiAIgtC6iWREEARBEASnEsmIIAiCIAhOJZIRQRAEQRCcSiQjgiAIgiA4lUhGBEEQBEFwKpGMCA0uISGB2bNnM2nSJCZOnMgtt9zC0aNHAdi7dy/33nsvAI899hj/+9//AOjYsSMFBQVNEt9NN93kuNaPP/7It99+e8Hn+Ouvv5gxYwZXXXUVEyZM4L777uPkyZMNHWqdli1bRt++fZk8eXK1f4888gjQ9Pf44MGDjBo1imnTppGenn5R59i6dSsTJ06s9twXX3zB0KFDOXToEFu3bqVjx448+uijNY6dPXs2vXv3vqjrNqQ///yT2bNnM3nyZCZMmMD9999PVlYWUPl/Nn/+/Is+9wcffMC6desu+Lhbb72VpKSki76uIDQmlbMDEFoWs9nM/Pnz+fzzz+natSsAK1as4NZbb2X9+vV0796d9957z6kxxsfHO37euXMnMTExF3R8dnY2jz76KMuWLSM0NBSAhQsXcv/99/P99983aKz1ERcXxyeffNLk1z2X9evXc9lll/HSSy812Dnffvtt1q5dy+LFiwkNDWXr1q0EBgby559/UlFRgU6nAyAjI4OUlJQGu+7FWrVqFQsXLmThwoVEREQgyzKffvopc+bMYfXq1Zd8/q1btxIdHX3Bx3322WeXfG1BaCwiGREaVEVFBaWlpZSXlzueu+qqq9Dr9dhsNnbs2MELL7zAL7/8UuPY999/n8TERIqKirj55puZNWsWAB9++CGrV69GqVTSoUMHnn76aQIDA5k9ezazZs1i7NixANUeJycn89JLL1FUVITNZmP27NlMnz6dxx9/HIC5c+dy8803s2HDBuLj43Fzc2PWrFksXLiQtWvXYrfbCQ0N5dlnnyU4OLhanIWFhVgslmqvce7cuXTq1Mnx+JNPPmH58uWoVCoiIiJ49dVX8fT0PO9r8fb25tixY1x33XVMmTKFl156iSNHjmCxWBgwYACPPPIIKtWl/cq+88477N27F7vdzv3338/w4cNrvceJiYl8/vnnfPfddwBceeWVTJgwgXvvvZeTJ08yffp0Nm3ahEJR2cC6cuVKFi9ejM1mw2g08uabb9b79c6ePbtGrHa7nQULFnDo0CG+++47fH19Hdt8fHwICwtj3bp1TJo0CYCff/6ZSZMmVUsIf/zxRxYvXozdbsfHx4enn36aqKgoUlJSWLBgAWVlZeTm5tKpUyfeeecdtFot3bt357bbbiM+Pp6cnBxuueUWrr/+enJzc3n00UcpLCwEYNiwYdx///014n777bd54YUXiIiIAECSJG677TZCQkIwm83V9j3fe/i9997jjz/+QK1W4+vryyuvvMIff/zBvn37eP3111EqlQwbNow33niD7du3Y7PZ6NKlC0899RR6vZ4RI0bQo0cPDh8+zAMPPMArr7zCu+++S3l5OW+//TZhYWEcPXoUq9XK888/T9++fSkoKODxxx8nNTUVHx8fAgMDiYmJ4Z577rmo95sg1JfophEalLe3Nw8//DC33HILI0eO5OGHH2bp0qUMHDgQjUZz3mPDwsJYtmwZH3zwAa+++ioWi4WlS5fy999/89NPP7Fq1SpiYmJ47LHHznseq9XKvffey4MPPsiyZcv45ptv+Pzzz0lISOCVV14BYNGiRUyZMoURI0Ywb948Zs2axc8//8yRI0f48ccfWbFiBcOGDeOpp56qcf5OnTpx7bXXMnXqVMaPH89TTz3Fn3/+yZAhQ4DK1oFly5axZMkSfvnlF9q1a8c333xT52vx8vLi119/Zfbs2bz88st07dqVZcuW8fPPP1NYWMgXX3xxzte7Y8eOGt00S5cuPee+7dq1Y/ny5fznP//hscceo6CgoNa4Bg8ezOHDhykpKSE9PZ2ysjI2b97seI2jRo1yJCJQmXTOnDmT8ePH8+abb17Q6z3X/+HDDz/M4sWLueOOO6olIlWmTJnCihUrHI9/++23at0727Zt4+eff+bbb7/l559/5pZbbuHuu+8G4IcffmDKlCn88MMPrF27lvT0dP766y+gsnXP19eX77//nvfee49XXnkFk8nEDz/84Lh/3377LSdOnKC0tLRaTIWFhWRkZNCnT59qz0uS5EjK6yMrK4tFixaxdOlSli1bxqBBg9izZw+zZs2iW7duPPLII4wePZpPP/0UpVLJsmXLWLlyJUFBQbzxxhuO88TExPDbb78xevToauffs2cPN910Ez///DPTpk3j7bffBuDFF18kOjqa3377jXfffZddu3bVK15BuFSiZURocDfeeCPXXHMN27dvZ/v27Xz22Wd89tln/PTTT+c9ruqDpHPnzpjNZgwGA5s2bWLatGm4u7sDMGfOHD7++OMa3zDPdPz4cVJTU3niiScczxmNRg4cOECvXr1qPe7PP/9k7969XH311UDlN/OKiopz7vvYY48xf/58tm3bxvbt23n99df5+uuv+fbbb9myZQtjx47F29sbwNEac9999533tcTFxTnO/9dff7F3717HPTMajbXGfSHdNNdddx0AsbGxREVFsXv37lrvsUKhYODAgcTHx1NYWMiMGTNYsmQJpaWlbNiwgVtuueW816rr/+7M13u2lJQUevfuzWuvvcZjjz3GsmXLCAkJqbbP8OHDee6558jLy+PEiRNERkY67jlU3sMTJ04wc+ZMx3MlJSUUFRXx8MMPEx8fz2effcbx48fJycmp1tI1cuRIALp27YrZbKa8vJwhQ4Zw2223kZWVxcCBA3nwwQfx9PSsFlNVcma32897b+oSHBxMp06dmDp1KkOHDmXo0KEMGDCgxn5//fUXpaWljiTRYrHg7+/v2F7bPW7bti2dO3cGoEuXLixfvhyAjRs3On4OCgpytNgIQmMTyYjQoHbu3Mnu3bu55ZZbGD58OMOHD+eBBx5g4sSJxMfHn/MbbpWqLghJkgCQZRm73e54DJV/5K1Wq+PxmUsrWSwWAGw2G56entW+Nefl5dX44Dib3W53NMlD5Tfk4uLiGvutX7+eoqIirr76aq688kquvPJK/u///o9hw4Zx4MABlEpltZhLSkooKSmp87VUfWhXbXv33XeJiopynOPMYy/WmS0ZdrsdlUp13rhGjRrFpk2bKCkp4ZZbbuHYsWOsW7eOI0eO0L9///Ne60Je79nat2/vaMXatWsX99xzD99991211jWNRsOYMWNYvXo1SUlJTJ06tcb1J0+ezMMPP+x4nJOTg7e3N//3f/+HzWZj3LhxXHHFFWRlZVV7L2m1WqD6e7FHjx6sX7+eLVu28O+//3LNNdfw2Wef0a1bN8dx3t7etG/fnsTERAYOHFgtnvvuu4877rijxms913tYoVDwzTffsHfvXrZs2cLLL7/MkCFDHAOTz3yNTzzxBMOGDQOgrKwMk8lU5z12c3Nz/CxJkiMGlUpVLZ4z3y+C0JjEO01oUH5+fixcuJAdO3Y4nsvNzcVgMBAbG3vB5xsyZAhLly51fGv9+uuv6devHxqNBj8/P/bt2wdAUlIShw8fBqBDhw64ubk5kpGsrCwmTpzo2FepVDo+FM/8efDgwfz0008YDAYA3n333Rp//AE8PDx46623qs1MSEtLQ6lUEh4ezsCBA/njjz8c53n//ff58ssvz/tazjZ48GC+/PJLZFnGbDZzxx138M0331zw/Ttb1bfe/fv3k5qaSs+ePc8b14gRI9iyZQsHDx6kR48eDBo0iHfffZehQ4eiVCrPe60Leb1nU6vVjp+ffPJJbDYbzz//fI39pkyZwvLly9m+fbujm6zK4MGDWb16NTk5OQAsXryYuXPnAvDPP/9w1113MX78eAASExOx2WznjemNN97go48+YtSoUTz55JNER0c7Zomd6e677+all17ixIkTQGVy/NFHH3Ho0CEiIyOr7Vvbe/jQoUNMnDiRqKgo5s+fz7x589i7dy9Q8z377bffYjabsdvtPP3007z11lvnfR3nM2zYMEdrXGFhIevWrWuQJFgQ6iJaRoQG1aFDBz788EPefvttTp48iVarxdPTk5dffpnIyEhyc3Mv6HzTp08nKyuLa665BrvdTkREhKNP/I477uCxxx5j48aNREZGOpqkNRoNH330ES+99BL//e9/sVqt3HffffTt2xeAsWPHMnv2bN5//32GDh3Kq6++ClROfczOzubaa69FkiRCQkIc2850+eWX8/TTT/Poo49SWlqKUqkkMDCQzz77DG9vb4YNG0ZSUpKjSyQ6OpoXXngBd3f3Wl/L2Z588kleeuklJk2ahMViYeDAgbV2i1SNGTlT1TiCs6WlpTFlyhQkSeKtt97Cx8fnvPfY09OTqKgodDodSqWSIUOG8OSTTzJmzJhL+r+7EFqtlnfffZepU6fSo0cP2rdv79jWu3dvKioqGDFiRI3BvYMHD+bWW2/lpptuQpIk9Ho9H3zwAZIk8X//93/cdddduLu7o9fr6devH6mpqeeNY+7cuTz22GNMnDgRjUZDx44d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zJzv4vl6xzH+PpbNl9cNYkhk/QYsNmcDBgzgvffeIzk5maioKDZu3MhDDz3E66+/Xm2/w4cPc/DgQTp37sySJUvo27cvOp2OIUOG8NxzzzF37lz8/PxYunQp3t7eREREMGrUKN58802uueYaoqKiMBgMrFq1isWLF9eIIz4+nuHDh3P99ddjNBr57LPPqs0aUSqVWK3WGscdPnyYjh070rFjR1544QXuvvtufvzxR4KCgqrtd/YHb12mTZvG119/zZAhQ1CpVCxatIgrrriizuPWrl1LbGwsERERlJWVUVJSQqdOndBqtbz11lscOnSIjh07cuLECWw2G927d+edd94hNTUVf39//vvf/5KXl8fVV18NVCYDsbGx1ZLBLl268N5773Hw4EHi4uIwGAz8+++/jBw5sloCdaGv2d3dndGjR/Pee+/x4osvcvDgQdavX8/3339fY98ZM2YwYcLpReI+//xzMjIyeO655xzPPfvssyQnJ/PFF184WpvOtGvXLrKzs8UsmrOIZEQQmgGrzc4r6/fxwh97sMsyDw/vyoKxPdGolLUe87///a/Wb4hVOgZ58889Y3lh7R5eWb+P4R+t5dER3Xh2TI/znru5i46OZsGCBTzwwAPIsoxKpWLhwoU1po9GRkbywQcfkJaWhr+/P6+++ioAgwYNYt68ecydOxe73Y6fnx/vvvsuCoWC0aNH87///Y+BAwcCMHDgQA4fPkxISEiNOGbOnMmDDz7IpEmTsFqtDBo0iLVr12K321EoFIwdO5bZs2fz/vvvO2bOwOlkBGDUqFEcPnyYu+66i2+++eaSpvreeeedFBYWcuWVV6LVahk3bhx33HGHY/utt97KzJkzGTlyZLXjdu7cyYIFCygrKyMoKIjbbrvNMdPkjjvuYP78+ZSUlBAaGsprr71G9+7duf322x1J2MCBA1m0aBE6nQ6oTEbO7trp3bs3d911Fw8//DBFRUV4enoyfPjwBumievbZZ3niiScYOHAgPj4+PPfcc8TExACVLS1xcXHcfvvt6HQ6R4xQmchoNBpHd11GRgZLlixBo9EwePBgx37PP/88V111FVDZRTN69Gj0ev0lx92SSLIsN9sh9aWlpRw5coTY2NhL7jessm3HvwS316PTeBLkFdEg5xRq2rlzJ337ihao+jiWX8rc7+LZfDyXdt7uLLp+EFdEt6n7QC7sPm9OyWHOd/GkFBjo086Pr66vvdXlfMxmM0CrW7m3rKzsvN0HLcEPP/xAmzZtGDp0qNNiaA33GWr/PWqMzz1XIAawnkXGzsGszWQUHnZ2KEIrJ8syi7Yn0+fN1Ww+nsu1vSJIeGhivRORRYsW8euvv9b7egM7BLH7wYnM6xfFrvQC4t5azUf/HKYZf18RGphSqaxRW0MQGoJIRs6iRINKocFgKnJ2KEIrVlBuYubXf3PT95sB+PK6QXx3wxB83evfBP/WW2/VqGtRF083Nf+bOZAf5w7DQ6PinuXbmPDfDWSVlF/QeYSW6eqrrz7ngExBuFQiGTmLJEno3XwpNxVjtzde+WFBqM2Go1n0euMXfko8waD2gex+cAKz4yKbdHbXtB7hJD48kTEd27LmUCY9//MLy/emNtn1BUFoXUQycg56rS8yMmXmImeHIrQiJquNR1btZMwn6zhZWsGCsT3ZcOcYOvg7p184xMudX28dwXtT+1FmtjL9y43csmQzpUaLU+IRBKHlErNpzqFq4TyDschRIl4QGtOBk0XM/vYfEjILiQ7w5OtZg+kfHuDssJAkibsGd2JETAizv/2HL7YlszE5m0XXDWJgh6C6TyAIwkVpbbWuRMvIOei1vigkJWZrhbNDEVo4WZb58J9D9Hv7VxIyC7n5smh2PjDBJRKRM3UO9mbzvWN5dERXUgoMDPtwLc/+noDFVrP4l0KhOGdtDEEQ6s9ut7eqZES0jJyDn74to7veiCSJXE1oPCdLKrh5yWZ+P5SJv7uWb28YzJTu4c4Oq1YalZKXJ/RhbKdQ5i2O58U/9rLmUCZfzRpMbODpKptKpRKz2YxOp2tVf0wFoSFZLJZzFk1rqUQycg4KkYQIjWzV/jRu/WELuQYTYzq25fOZAwjxcm/Qa2zfvp1du3Y16DkBhkYFs/vBidy7fDvf7DxG37d+4Y2r4rjt8hgkSUKSJDw9PSkuLkaj0aBUKltFUmKxWBy1IYTG09LvsyzLWCwWVCpVq/i9qSI+dWtRZiomsygJuyxm1AgNp8xk4Y6f/mXK539RYrTwzpQ4Vt8yosETEagsltRY0zC9dRoWXT+IxbOHoFUqufOnrUz+/E+ySyu7NpVKJd7e3mg0mlbzBzU5OdnZIbQKLf0+S5KETqfD3b3h/ya4skZrGbHb7Tz33HMcPnwYjUbDiy++SEREzYqmTz/9NN7e3jz00ENYLBaeeOIJMjIyMJvN3HHHHTXKDjeVlNxE0gsP4ek2HU83P6fEILQsO9Pymf3tPxzOLaFHiC9fzxpEtxDfRrvekSNHSE1NbdRKt9f2as+gDkHcuDie1Qcy6PnGKj67dgCTuoY5FpVrTVpb1VlnEfe55Wm0lpF169ZhNptZsmQJDz74oGNNhzN9//33HDlyxPF45cqV+Pj48N133/HZZ5/xwgsvNFZ4ddK7+QBgMJ57oTFBqC+b3c6r6/cy8L3fOJxbwv8N68yW+8Y1aiICcM011/DEE0806jUAQr3d+f22Ubw1OY4So4Upn//F7T/+S5lJTAEWBKF+Gu1ry86dOxkyZAgAvXr1Yt++fdW27969m8TERGbMmMGxY8cAGDt2bLVltpVK5y3UpddWtoYYTCIZES7eiQID8xbHs+lYDm29dHxx3SBGxdZcMK25Uygk7hvamZExbZj9bTyf/XuUv5JO8pWLTFEWBMG1NVoyYjAYqq1KWLUUtkqlIicnhw8++IAPPviA3377zbFP1eJHBoOBe++9l/vvv79e1zqzdaUh7Ny5E6tsotRcytGyA5Skt44+76ZW14qyzd3vx4t5fXsWBoud4WGePN4/BJ/STHbuzGyS61cN8mvq+/zR0GA+3qPg24P5DH7vN27uFsi8rgGoFC3/96ilv6ddhbjPLU+jJSN6vZ6ysjLHY7vd7ug//v333yksLOS2224jNzcXo9FIZGQk06ZNIysri7vuuovrr7+eSZMm1etaDbl6YdUqp7IsU3rgMFq1G31jxeqyDa0lr9pbVGHm7qVbWbw7Aw+Nis+uvYwb+0c1+UBOjUaD2Wx2yn0e0B/mJZ1k3nfxfLo3lz0lMouuH0R0gFfdBzdTLfk97Upa+32uWrW3pWm0ZKRPnz78+eefjB8/noSEBGJjYx3b5syZw5w5cwBYtmwZx44dY9q0aeTl5XHTTTfxzDPPOH1lyKo1aoor8rDLNhSS87qMhOZjU3I2cxfHk1pYxuURAXx1/WCiAlrOMt8XYnh0GxIemsjdy7bx/e7j9HlzNW9NjuPmy6JbzQwbQRDqp9GSkdGjRxMfH8/MmTORZZmXX36ZVatWUV5ezowZM855zMcff0xJSQkfffQRH330EQCfffaZ0wq/9AgbgUbpJhIRoU5mq43n1+7htQ37kJB4ZkwPnhzVHZWydc+e93XX8u0NQ5jQpR13L93K/B//ZfWBdD69dgCB+tZT0EkQmpIs29mSvILCsiwUkpJBMVfjpTs9dist/wAJaRtQSApiguOIbdMfgD1pf5JWcBC73UbHkMuJbdOPkoo8/jn6IyDh6x7M5VGTG6UgaKMlIwqFggULFlR7LioqqsZ+06ZNc/z81FNP8dRTTzVWSBfMXdNym5SFhnM4p5jZ3/7DzvQCIv31fHX9YAa0D3R2WLz77rscPXrU2WEAcH2fDgw+NQV45f50tr6xiv/OGMj4zqHODk0QWpzU/APY7BYm9LyTnJJUtqesZmSXuQDY7Ta2paxmYq+7UCk0/LrnY9r5daa4PIeckhOM73E7VruFfembANiespre4WMI8Ylic9JyUvMPEBHQrcFjbt1f2+ogyzIVZgPlphJnhyI42fNrEnl+TWK152RZ5pMtR4h7ezU70wuY2y+KXQ9MdIlEBOCKK66gT58+zg7DIdzXgz9uH83rE/tQUG5m0n83cPfSrZSbq69jc657LQhC/WWXHCfUtyMAQV7h5BsyHNuKKnLwdPNHq3JHqVAR7BVBTkkKmUVH8fVow4aDX7P+wCLC/DoDkG/IoI13JADtfGPJKk5qlJhbV0WiC2S0lLHx8He08Y6kV/goZ4cjOMnzaxJZsHaP4/GzV/Yk12Dk1h+2sGp/Or46DV/MGcT0njWL+gnVKRQSDw7vyqiOlasAL9x8hA1HK6cAx4X5n/NeC4JwYSw2Ixrl6W5QSZIcYx8tVhMa1eltaqUWs9WI0VJGmamIkV3mYjAWsv7gIqb2eRCZ06sHV+3bGEQych5uag9UCrUofNaKnf3huGDtHo7mlrAh6STZpUZGRLfhi+sG0s7Hw4lRntuoUaMoKytjy5Ytzg6lhp5t/dh2/wSe+HUX7246xKD3fmNIZBB/JmU79qm67yIhEYQLo1a6YbGZHI9lWXaMfVSrtNW2WWwmNCodWrU73rpAlAoV3u6BKCUVRksZElKNfRuD6KY5D0mS8ND6UmYuFmvUtEJnJyJVFu8+Tq7ByH8m9WXN/FEumYgA5ObmUlRU5OwwauWmVvLW5H6smT8KN5WyWiJSZcHaPaLLRhAuUJBXBOmFhwDIKUnF16ONY5uPLoiSijxMlnJsdivZxccJ9Awn2Ks9GUVHkGWZclMJVrsFrdodP4+2ZBVVrgeUXniEYK/2jRKzaBmpQ+X03hzKTSXo3Rq3fLfgOmpLRKrYZSg1WVC0gkJejS0+JQfDWeNGziRaSAThwkT4dyWzKInViZWzUgfFTOdYTgIWu4mObS6jf4cJrN3/Ocgy0cFxeGi98dB6k12cwi+JH4Isc3nUZBSSgn6RE9h8dBm7TqzBWxdIRED3RolZJCN10GsrExCDqVAkI4LgJBWW2pMVQRCqkyQFA6OnVnvOxz3I8XOYfxfC/LvUOC6uw/gaz3nrAhnXY37DB3kW0U1TB7FgXuv07JU9eXp07d8AnhnTQ3xTbyDPXtmTZ8b0OO8+7/19iOu+3sSaQ5nY7PYmikwQhKYiWkbq4KMLpm/7sXi5icW+WhOT1UZaUfk5t4lEpOFV3c+zu8b+b2hngj11fLk9iR8STvBDwglCvd2ZHRfJ3H5RxAaKWkCC0BKIZKQOapWWQM9wZ4chNKGc0gquWbSJf1Jy6Bfmz+AOQby96SDQvBKRmTNnkpWV5eww6u3shOTMe/3Q8C5sS83jy+3JLNl9nFfX7+PV9fsY2D6QOf2imNErAi83jdNiFwTh0ohkpJ6sNjNKhapRyuAKrmNvViGT//cnJwrLmNGrPf+bOQCdWoWnmxpoXoMoH3/88Wa3uumZ9/fMnyVJ4rKIQC6LCOStyXH8vDeNL7cns/5oFpuP5/J/P29navdw5vWLYnh0GzGwWBCaGZGM1MOhrC0cz9vL4JhrHWNIhJZn5b40Zn/3DwaTlefH9uTJUd0dxX6aUxLS3NV1r3VqFdf16cB1fTqQVljG1zuPsWh7Mt/tSuG7XSmE+3ow51Q3TqR/61ykUBCaG/E1vx40KncAykxiEGtLJMsyr2/Yx7Qv/8Iuy/wwdyhPje7R7FeWffrpp/nkk0+cHUajCvP14IlR3Tn02GQ23nUlN/aPoqDcxIt/7CXm5Z8Z/uEavtyWjMFkcXaogiCch2gZqQdPt9PTe4Pp4ORohIZktNi4/ad/+XrHMUK93fn5pivo087f2WE1iJUrV2I2m50dRpOQJInBkUEMjgzi3Sn9WLo3la+2J/NnUjabjuVw7/JtTO8Zwbx+UQyJDGr2iaYgtDQiGakHj6paI2J6b4uSXVrB1V9sZMuJXPqH+7PsxisI8XJ3dljCJfLQqpkTF8WcuChS8kv5escxFu1IZtH2yn+R/nrm9otidt9IIvz0zg5XEAREMlIvOrUepUKFQXTTtBiJmQVM+fwvUgvLuK53ez6bUTlQVWhZOvh78syVPXlqdA82Hcvmy+3JLN1zgmd/T+S5NYmMiG7D3H5RTO0ejrtG/P8LgrOI3756qFqjptSYj122oxAzapq1n/emMue7eMrMVl4c14vHRnYTzfYtnEIhcUV0G66IbsP7U/vzY+IJFm1PZv3Rk6w/ehIvt21c2yuCuXFRDGgfKN4PgtDERDJST5GBPbHLdkB2dijCRZJlmdc27OPJXxNw1yj5ad4wpnYXNWRaG083NTddFs1Nl0WTlFfCou3JfLX9GP/9N4n//ptEbKAXc/tFMjsuilBv0W0nCE1BJCP11MY70tkhCJfAaLFx6w9b+G5XCmE+7vx803B6hfo5O6xGFRERQWlpqbPDcGnRAV68MK43z13Zkw1HT7JoezLL96bx5K8JPP1bIqNiQ5jXL4rJ3cJwUytrPc/zaxLJzMzhk75NGLwgtCAiGRFavJMlFUz74i+2puZxeUQAS+ddQRsvnbPDanQrV65sdkXPnEWpUDC6Y1tGd2xLUYWZJQnH+Wp7MmsPZ7L2cCY+Og0ze7dnXr8o4sL8q3XjnLnCc9s1iaImjSBcBJGM1JPZamR7ymq8dAF0bzfM2eEI9bQ7vYApn/9JenE5s/p24NNrBpz3G64g+Og0zB8Qy/wBsRzMLuar7cl8vfMYH28+wsebj9C1jTdz46KY1TeST7YcqbaeTtXPIiERhAsjkpF6Uiu1lJmKEWNGmo+le04wb3E8FRYbL4/vzSMjuraqgYm//vorycnJ9O0r+g4uVudgb16Z2IcXxvXijyNZfLk9mZX70njkl108+suuc/41EAmJIFw4kYzUkyRJ6N18MBgLxYwaFyfLMi+v28szvyfioVGxdN4VTO4W5uywmtzjjz+O2WzmnnvucXYozZ5KqWBc51DGdQ6loNzEnG//4bdDmbXuLxISocrzaxIB8V6oi0hGLoBe60tJRR4V5lI8tN7ODkc4hwqLlVuWbOH73ccJ9/VgxU3D6dHW19lhCS2In7uWfuEB501GBAGqjycCkZCcj0hGLoDe7XQlVpGMuJ7M4nKmffEX29PyGdQ+kJ/mDSPIs+UPVBWaXtWHypkfNGd6ZkwP8cHTyp2diIjWsvMTycgF0GvPXKOmvXODEarZmZbP1C/+IqO4nDlxkXx8zeVoVWKgqtB4aktI+rbzEx84rdzZiUgVkZDUTiQjF8BL50+YX2e8dYHODkU4w4+JJ7hxcTxGq43XJvbhwSu6tKqBqoLznJ2QBOm17Ewv4PvdKczs7bqLamYVJXEsNwGDsRC9my+Rgb0I8Yl2dlgtQm2JSBWRkJybSEYugJtaT9fQIc4OQzhFlmVeWLuH59fuQa9VsfzGK5jUtfUNVBWcq+pDJTMzkwcmDKTf278y/8d/6dvOn5hALydHV1NWURKJaRscj0uNBY7HIiG5dEaLzdkhNEtiSojQLJWbrVz39d88v3YP7f08+OeesSIROcuvv/7K22+/7ewwWoVnr+zJbT2C6BjkzcLpl2EwWZn51SaX/GA6lpuALNeclHwsN6Hpg2lBMovLeWTVTj7afPi8+4nxROcmkpELlFF4hG3HfqHcXOLsUFqtjOJyrvhwDT8mnmBIZBD/3jee7iFixszZQkNDCQwUXYpNbVbfSG65PJqEzEIeXLnD2eHUUFyRR3FFDkZLOcCpNbfAYCxyYlTN1+GcYm5dsoWol5bz5l8H8NSqeW1iHx4d0bXGviIRqZ3oprlAJks5BWWZlBoLcNe4XhNsS7c9NY+pX/xFVkkFN/aP4qOrL0MjBqqeU1FRkVibxknemdKPrSfy+HjzEYZGBjOjd3tnhwSAzW7FaDZgt9sAGYvVhMFUgLvWhwB9qLPDa1a2p+bx+p/7Wb43FVmGmABPHhreldlxkY7B81qV0jFGRCQi5yeSkQt05vTeYK/2zg2mlVmy+zg3fb8Zk83GG1f15f6hncVA1fMYNmwYZrOZgwcPOjuUVkenVvH97KH0f6dy/Eifdn5OHz8iyzJ70/9CqVSjxR03lQc22QJAmamIrm0HOzW+5kCWZdYdyeL1DfvZkHQSgLgwfx4Z0ZUp3cJQKqp3NpyZfIhE5PxEMnKBzpzeKzQNu13m+bWJvPjHXjy1an6cN4zxncW3OMG1dQquHD8y57t4Zn61ifh7xzl1XaTknF2cLD5GG68OtPPrxPG8PRiMRQR6RVBmKiat4CDt/DrhpvZwWoyuyma3s3RPKq9v2M/ujAIARsWG8MjwroyIaXPeL0UiCakfkYxcIJ1Gj0JSUSb6V5tEmcnCvO83s2xPKh389Ky4eThd2/g4OyxBqJdZfSPZmJzN/7Ym8eDKHXx49WVOiSOnJJWknJ3o1J70ihiNVqUj1DfWsT0ldw+HT/7LrhNruSxyEkqF+GiAypkxi3Yk8+afB0jOL0WSYHrPCB4Z3pW+Yf7ODq9WsmxnS/IKCsuyUEhKBsVcjZcuwLE9Lf8ACWkbUEgKYoLjiG3TH4CVu99FrXQDwNPNj8Gx15BvyGD9gUV4ulW+3k4hl9MhsOETLPGOu0CSpECv9cFgKkSW7UhijZpGk15UxpTP/2J3RgFDI4P4ce4wAvRuzg5LEC7Iu1P7sS21cvzIsKhgru3Vvslj8PNoQ4h3FJFBvdCqalYlbh/QHYOpgIzCIxw5uZXObQc1eYyupLjCzCdbjvDOpoNklxrRKBXcenkMD17RxendbfWRmn8Am93ChJ53klOSyvaU1YzsMhcAu93GtpTVTOx1FyqFhl/3fEw7v85oVJV/W8f1mF/tXPmGDLq0HUy3dkMbNWaRjFyEAM92uGu9sNqtqJUaZ4fTIm09kcu0LzZysrSCmy+L5oNp/cVAVaFZOnP8yG0/VI4fiQ5omg80WZaRJAmVUkPP8JG17idJEl3bDkGpUBMZ2LtJYnNFJ0sqeHfTQT7ecoQSowVPrZpHhnfl3qGdCPFyd3Z49ZZdcpxQ344ABHmFk2/IcGwrqsjB080frary9QR7RZBTkoKH1ger3cLaff/DLtvoEzHWcWxxRS5pBQfw0gXQv8Mk1Cptg8cskpGLUNWkJTSO73alcMuSzVhsMm9PjuOeIZ3EQFWhWesU7M1H0y9j7nfxzPzqb/65Z2yjjx+x2a3sPP4bYX5dCPGJqnN/hUJJlzNaROyyDYXUOr4AJOWV8MafB/hqRzImq51gTzceG9GN+QNj8dE1vy+cFpsRjfJ0K7IkSY7/T4vV5GgFAVArtZitRrx1GrqFDiUmuB8lxjzW7f+CqX0fJMAzjJg2/QjQtyMxbQMJaevo12FCg8cskhHBZdjtMs/8nsAr6/fh5aZm2Y1DGNtJDFS9WE8//TQpKSnODkM45Ya+kWxMyubzbUk8tHIHHzTi+BFZltmXvpGCsizc1J71SkbOVFCWxZ60P+kTMabaWIOWZld6Pq9v2M/SPanYZZlIfz0PDe/K3Lgopw42vlRqpRsWm8nxWJZlR2KpVmmrbbPYTGhUOrx0AXi6+SNJEt66QLQqdyrMpYT7d3V07UX4d2Vr8spGiVkkIxfBZrdyLDcBjdKNiIBuzg6nRTCYLMxdHM/Pe9OI8vdkxc3D6RwsVka+FNOnT2fnzp3ODkM4Q9X4kYWbjzC0EcePHMtNIKs4GR/3YLqGXviUXYvVhNFiYNeJtQyInuJo0m8JZFnmz6STvLZhP+uOZAHQO9SPh4d35eoe4aiUzX8cYJBXBGkFB+kQ2IOcklR8Pdo4tvnogiipyMNkKUel1JBdfJyuoUM5mr2DwrKTDIieQrmpBLPNhE7jya+JH3NZ1FUEeoaRVZSEfyPVoxHJyEVQSApSchPRa31FMnIRnl+TSGZmDp/0rXycWljGlM//JDGzkCuigvlh7jD8PRq+T1IQnM1do2LJnMYdP5Jdcpyj2dtxU+vpHTH6ombGBHu3Jya4H0ezt7P7xB/07zARhaL5thRA5fTcn/el8fqG/exIywdgRHQbHh7RldGxIS2qKzjCvyuZRUmsTvwIgEEx0zmWk4DFbqJjm8vo32ECa/d/DrJMdHAcHlpvYoLj+Ofoj/y6ZyEgMThmOgpJyYDoKfybvAKFpESn8WRg9LRGiVkkIxdBkhR4aH0wmIocA8SE+jlzRcu2axIZ07EtV3/5F9mlRm4bEMN7U/ujbgHfTFzBzJkzKS4u5rfffnN2KMIZGnP8SKkxnz1pG1BIKvpEjLmkFo3IwF4YjAVkFSezL2MT3dtd0Sz/1pmsNr7ecYw3/zrAkdwSJAmmdg/nkRFd6R/eMrugJEnBwOip1Z7zcQ9y/Bzm34Uw/y7VtisVKoZ1vK7Gufz1oUzoeWfjBHoGkYxcJL3Wh1JjPhWWUlEWvp7OXlp7wdo9vPjHHkDi3Sn9uGtwx2b5x85VHTx4ELPZ7OwwhHM4c/zIw6t28v60hhkUr1V54K0LIsK/6yWP9ZAkiW7thlFuLiGz6CheugDaB3RvkDibQonRzGdbjvL2poNklVSgViq4qX80Dw3vQscg0QXsakQycpH0bn5QnIzBWCiSkXo4OxGpYpdhVp/23D2kkxOiEgTnqRo/8lH8YYZGBXNNz4hLPqdG5Ua/DhMaLKlXKlT0jhjD3vSNBHldenxNIbu0gvf/PsTCzUcoqjCj16p48Iou3De0M6HeLWfsS0sjkpGLdGZZ+CCaxy+ps9SWiFT5dlcKUQGeomyy0Kq4a1R8P2co/d9Zza1LttA71Peixo/IssyhrC0EeoYT4NmuwVsX3dQe9OswvkHPebHOHm92pmP5pbz11wG+2JaM0WojUK/lhXG9uGNgLL7uYgyaqxPJyEXSu/m2qBHmgiA0vc7B3nx49WXcuHjzRY8fOZG/lxP5+yiuyMFfH9qoXZ0lFXkcytpCr/DR1WpVNIWzx5tVfXlJzCzg9Q37+SHhBHZZpr2fBw9d0ZV5/aPQqcVHXHMh/qcukofWm+Gdb3B2GM1C1R+N2lpHxNLaQms2Jy6KTcnZfLEt+YLHj+SWpnIo61+0Knd6hY9u9DFXOSUnKCjLYnfqH/TrML7JiqKda7zZ8QID2QYjaw5lAtAjxJdHRnTlmp4RLWJ6bmsjkhGhSdSWkIhEpPGMHDmS3NxcZ4ch1MN7U/s7xo8Miwpmej3GjxiMhSSmrkchKekdMaZJVtuNCupDqbGA7JIUDmTE0zV0SKMnQLV183614xgAw6KCeXh4V8Z2aisGwDdjIn28BKXGfI7n7cVkLXd2KM3Cs1f2pN0ZA8hEItK43nrrLe6//35nhyHUQ2X9kWG4a5Tc+sMWkvNKz7u/2Wpk54nfsdotdG83rNq0zcYkSRLdw67A082f9MJDpObvb9Tr1TXeDCqTkXGdG7d7Smh8Ihm5BDklJziUtYXi8jxnh9IsZJdWkFFSTriPO7d0CxCJiCCcoWr8SInRwsyvN2Gy2mrd1y7bUCu0RAX2JsQnugmjBJVCTZ+IK9GodBzM2kxeaXqTXl9omUQycgnOnFEj1O2XA+nIMtwzpDO39Wiab3Kt2XvvvceSJUucHYZwAebERTGvXxS70gt4eGXtpfzd1B5cFnUV0cFxTRjdaTqNnt7hY/DQeKNV6xrtOk+O6s7A9oG1bhetqy2HSEYugd7tVDJiFMlIfazYlwbAVd3aOTmS1uF///sfq1atcnYYwgV6f1p/urbx5sP4w/yUeKLatvSCwxSV5wCVNUCc2TXh6xHMoNhr8HTzb5Tz55RWMO7T9Ww+novfOVbOFYlIyyKSkUug03ghSQrRMlIPZSYL64+cpEuwd4OvxSEILYm7RsX3s4fWGD+SV5rO/oxNJKSuwy7X3oXTlBRS5UdImamY/Rn/YJftDXLerSdy6ff2r2xIOsnkbmEkPTmVZ8b0cGwXiUjL02izaex2O8899xyHDx9Go9Hw4osvEhFRc4T4008/jbe3Nw899FC9j3EVCkmBXutDmalQrFFTh7VHsjBabVzVLczZoQiCy+vSxsdRf+S6rzex5rYBJKSuA0miZ9jIJptSW1/JObvILDqKQpLo3HbQRZ9HlmU+2XKU+3/ejs0u8/L43jw8vCsKheRIPjIzM0Ui0gI1WsvIunXrMJvNLFmyhAcffJBXX321xj7ff/89R44cuaBjXI1e64ssI2bU1GFlVRdNV9FFIwj1UTV+ZP/JXL7Yshir3Uy30KH4egQ7O7QaurQdhF7ry4n8/aTlH7ioc1RYrNz0/WbuWroVbzc1v902kkdHdkOhOP0l79kre4rxZi1Uo7WM7Ny5kyFDhgDQq1cv9u3bV2377t27SUxMZMaMGRw7dqxex7iirqFD6BE2QrSKnIfVZmf1gQxCvHT0C2uZq2QKQmN4d2ocOsUOckqLCPGJI9Q31tkhnZNKqaFP+yvZkrScA5mbcdf64K9vW+/jj+WXcs2XG0nILKRfmD8/zB1GuG/j100RXEejJSMGgwG9Xu94rFQqsVqtqFQqcnJy+OCDD/jggw+qLW9+vmPO58zWlYawc2fto9iFC7crp4z8chNTo33YvXuX43lxnxuXQqHAzc1N3Ocm1ND32iqbuCxYwa/J7izcWoBH2RZC9TUHc7oKrb0dBZZE/trzI6GavqilumfabM4s5ZnNGZSY7UyN9uGBvoHkHjvE+cr1ifd0y9NoyYher6esrMzx2G63O5KK33//ncLCQm677TZyc3MxGo1ERkae95jziY2NxdPTs0Hi3rlzJ337nmMVplrIsp1SYwE2u80lm09dweKVOwC46Yo+9O0cClz4fRYu3O7du8V9bkKNda/7WPti0x3nh/3beHFXAX/fMxatyrXGjJwprSCUoye30al97HmLsdntMi/+sYcFG9PQKBX8d8YAbuxfd82U1v6eLi0tbfAv4K6g0caM9OnTh02bNgGQkJBAbOzp5sU5c+awbNkyvv76a2677TYmTpzItGnTznuMq5KBLck/cyhrs7NDcUmyLLNyXzp6rYoR0W2cHY4gNAuFZScpNRYAoFZpmde/I3P7RbEzvYBHVrl2q0CYXyeGxM44byJSUG7iqs//5Pm1ewj38eCfe8bWKxERWq5GaxkZPXo08fHxzJw5E1mWefnll1m1ahXl5eXMmDGj3se4OoWkwEPjjcFUJGbUnMOB7GKS80u5ukf4Ba9GKlya7du3c+jQoVb9LbI5KjeVsOvEGgCGdbwOlbKyW+b9qf3YnprHB/8cZlhUG6b1CHdmmOelVmkBMFrKyC45ToR/V8e2hIwCpn+5kZQCA2M6tuWbWYPx99A6K1TBRTRaMqJQKFiwYEG156KiomrsN23atPMe0xzo3XwxmAoxWsrQafR1H9CKOGbRiCm9Te6WW27BbDYze/ZsZ4ci1JPFZmbnid+x2Ex0Cx3qSEQAPLRqlswZymXv/sotSzbTK9SXSP+G6Z5uLHvS/qSgLBOlQkU73458tSOZO37citFq46nR3XlmTA+UClHuShBFzxqEKAtfu5X701AqJMafGisiCMK5ybKdxLT1lJmKaB/QnXZ+nWrs06WNDx9Mu4xio4Xrvv77vOvXuIKuoUNQK7XsTd/EQz//wY2LN6NVKVhx83CeH9tLJCKCg3gnNABRFv7cMovL2Zaaz9DIIPzcRTOsIJzP4ZPbyCtNI0AfRmyby2rdb26/KOb2i2JHWj6P/rKr1v1cgYfWmxDfQexKy8ds3sbl4R5s/78JTOwi6g0J1YlkpAGIlpFzW3WgcjXPq7qKLhpBOB+L1URWUTIeWh96ho90lFmvzftT+9El2Jv3/z7Esj2pTRTlhdtwNIsRH+9i+QFPOvhpeHmsjQhfN2eHJbggkYw0AHetNwOip9K57UBnh+JSxHgRQagftUrLgOgp9I0Yi1pZdx0RD62a7+cMRadWcsuSzRzLL22CKOtPlmXe+HM/V36ynqIKCzddPpLRnS7HYjWIL23COYlkpAEoJAXeukBUCrWzQ3EZpUYLG46epEeIL+39xKBeQTiXCnMpFebKRMJN7YG7tv6LSHY9Y/zI9V//jdlFxo+UGM1cs2gTj/6yizaebvx55xjuHNyJLqEDGRA97bxTfoXWq9Fm07Q2sixTYSlFo9KJpARYczgTs83OVd1E37CzLFq0iIMHDzo7DKEWVpuFXSfWYLKUMyhmOlq1+wWfY17/KDYmn+SrHcd49JddvD2lXyNEWn8HThYx/cuNHM4tYVhUMItnDyHYs7IKq0JS4qH1Biq7pYqNuQToxd8HoZJoGWkgyTm72HT4ewrLTjo7FJewwrEwnuiicZZevXo1i8KBrZEsy+xJ30CpsYBg78iLSkSqfDCtP52DvXnv70Ms3+u88SM/JBzn8nd/43BuCQ9e0YW180c5EpEzybLM9uOr2XV8DUXlOU6IVHBFomWkgVTNqCkzFRLo2bo/gC02O78ezKCdtzt92vk5OxxBcDlHs7eTU3ICP4+2dG474JLO5ag/8s6v3Pz9Znq19aVDE9YfsdrsPLZ6F29vPIheq2LJnKFM7xlR6/6SJBETHMfO47+z+8RaBkRPxU0tFsVrSLJsZ0vyCgrLslBISgbFXI2X7vQipWn5B0hI24BCUhATHEdsm/4ArNz9Lmpl5QBjTzc/BsdeQ0lFHv8c/RGQ8HUP5vKoyUh1DLC+GKJlpIFUzagpFdN7+ftYNkUVZiZ1bScq0jpRXFwcc+fOdXYYwlkyi5I4lpuAu8aL3uGjUUiXXpm461n1R5pq/Eh2aQVjPlnH2xsP0inIi3/vG3/eRKRKoGc4nUIux2QtZ9eJtdjs1iaItvVIzT+AzW5hQs876dt+HNtTVju22e02tqWsZky3mxjb/TYOn9xGubkUq90CwLge8xnXYz6DY68BYHvKanqHj2F8j9uRT527MYhkpIG4a72QUFAmRoqzcv+pKb1iFo1TWSwWbDbXGNQoVLLZrRzO+heVQkOfiLGOsukNYV7/KGbHRbK9ieqPbE7JIe6t1WxMzmZaj3D+vW88nYO96318hH93Qn07UlKRy970v5BluRGjbV2yS44T6tsRgCCvcPINGY5tRRU5eLr5o1W5o1SoCPaKIKckhcKyLKx2C2v3/Y/f935KTklll1++IYM23pEAtPONJas4qVFiFt00DUQhKXHXemEwFrbqNWoqF8ZLw8tNzRVRYhVjQTiTUqGif+QkjJYy9G4+DX7+D6f1Z0daPu/9fYhhUcFM6d7w69fIssxH8Yd5YMUO7DK8PrEPD1zR5YL/5kmSRNe2gyk3FZNTcgKDqQBPN/8Gj7c1stiMaJSn67lIkoRdtqGQlFisJjSq09vUSi1mqxFvnYZuoUOJCe5HiTGPdfu/YGrfB5E5/XlWte/5FJadpKQiDyQJLzd/fD3qt0CqSEYakF7rS5mpCJO1DDd165zOuierkBOFZVzbKwKNCy9zLghNyWa3YrVb0Kp0eGi9HbNKGpqHVs33s4dw+bu/cfOSLfRs4PEjZSYLt/+0le92pRCo17J49lCGX8Jq3AqFkl4Ro6kwl4pEpAGplW5YbCbHY1mWHd2BapW22jaLzYRGpcNLF4Cnmz+SJOGtC0SrcqfCXIqEVGPfs8myzOGTWzmQ+Q9qpRYPrQ8KSYHBWIjZZqJL20F0bNP/vGNNRDLSgDoE9iDMr7NjAFBrtHJfZRfNZNFFIwhA5R/qvel/UVSeQ//Iibhr6l9L5GJ0C/Hl/Wn9uWXJFq77+m823X1lg3wxSMorYfqXG9mbVcTlEQEsmTOUdj6XPvBUq9KhPfUBZ7VbMFnKGy1Zay2CvCJIKzhIh8Ae5JSkVmud8NEFUVKRh8lSjkqpIbv4OF1Dh3I0eweFZScZED2FclMJZpsJncYTP4+2ZBUlE+ITRXrhEUJOddmc6a9D3xDiE8OEnnc5/i+rmK1GknJ2suHg14zsUvsYtnolI6tWrSIpKYnbb7+dNWvWMGXKlHrektbFx110S6zcn4ZaqWBcJ7EwniBA5bT/k8XH8HVv02SzRub1i2JjcjZf7zjGY6t38dbkS6s/smp/GnO/i6fYaOGOgbG8OTkObQO3fNplG9uSV2G2GRkQNeWSpju3dhH+XcksSmJ14kcADIqZzrGcBCx2Ex3bXEb/DhNYu/9zkGWig+Pw0HoTExzHP0d/5Nc9CwGJwTHTUUhK+kVOYPPRZew6sQZvXSARAd1rXG9w7IxaKwdrVG50aTuImODzvwfrTEbeeOMNTp48yf79+7n11ltZunQphw4d4rHHHqvHLWmdqvrmWpu0wjJ2pRcwKjYEb13dJa2FxnX77beTnp7u7DBatayiZJJydqJTe9IromFmztSHJEmO8SPvbjrE0MiLGz9is9t5fs0eXlq3FzeVki+uG8icuKhGiLhy3F0b70iOZG9jd+pa+nWYiFIhGu8vhiQpGBg9tdpzZ1a+DfPvQph/l2rblQoVwzpeV+Nc3rpAxvWYf97rVSUiJks5+WUZtPWJYU/an+QbMunbfixeOv86lzmoczbNP//8w3/+8x+0Wi16vZ4vvviCTZs21XVYqyTLdv469B3bjv3i7FCcYtWpWTSTRaEzl3DHHXcwbdo0Z4fRahVX5LI3fSNKhZo+7cfUaL5ubFXjR3RqJTcv2cLxAsMFHZ9fZmLCZxt4ad1eIv31xN87ttESkSodAnsS4hNNUXkO+zP+FjNsmpmNhxdTYMgis+gox/P2Eu7fmc1JS+t1bJ3JiEJRuUvVaFqz2ex4TqhOkhQoFSrHjJrWZsX+yqqrk7qKEs9C6ybLdvakbsAuW+kZNsJpgzO7hfjy3tT+FFWYue7rTfWuP7IzLZ9+b6/mjyNZjO8cyrb7x9MrtPELGEqSRLfQoXjrAsksOkpK3p5Gv6bQcMzWCrq1G0pq/gGig/sSFdSn2mDZ86kzqxg7diz3338/xcXFfPnll9xwww1MnDjxkoNuqfRaX6x2MyZrubNDaVLFFWY2JmfTp50fYb6imqIruOeee3jzzTedHUarJEkKeoaPpGvbwQR51V0ErDHd2D+KG/pGsi01n8dX765z//9tPcqQD34ntaiM58f2ZMVNw/F1b7h6KHVRKlT0jhiDVuXB0eztVJgvrEVHcB4ZmTxDOqn5Bwjz60S+IRO7bK/XsXV2yN18881s3ryZtm3bkpWVxT333MPw4cMvOeiWSu/mS3ZJCgZjYasqcfzboQwsNrtYi8aFbNq0CbPZ7OwwWhVZlrHJVlQKNV66gGoluJ1FkiQ+vLo/O9LyeGfTQYZGBTO5WxjPr0kE4NkrewJgtNi47+dt/PffJHx1GpbdOJixThqI7qb2oE/7MVhsJnSa1lkmoTnq234cO1J+pWvoEDzd/Pkl8UP6d5hQr2PrTEamT5/O8uXLGTJkyCUH2hpUlYU3mAoJ8Gw93RVVU3rFKr1Ca3YsN4HMoqP0bT+20afwXgj9qfVrLn/3N276fjNz4iJ57+9Dju3z+kVx7Veb2JGWT+9QP36cO7RJ17c5F29doONnu2zDZrM2aMVaoeG19YmmrU+04/HEnnfV+9g6k5GAgAB27NhBjx490GjEDIm6VC2YZ2hFa9SYrTZ+O5RBhK8HPUJ8nR2OIDSprFNrzaQZk5BSbHjpAl1yFkjV+JFbf9hSLRFZsHYP/9mwnwqrjbn9ovjw6v7o1K4Tv9VmZufx3ykzFaNRuZFlSsN4NIXIwF6EnPHB54qq3hsGYyF6N99mEfPF+PKfxzmz/q4kKVFIEja7FbVSy/UDnqvzHHW+4/bu3csNN9xQ7TlJkjh48OCFxtsqeGi9iQrsjZ++rbNDaTIbk7MpMVqY2y+q1ZbBF1qnrKIkEtM2YLVZsMjlKGUlNruFAkOmS37opBaee/xFhdXGhM6h/G/GAJf7HVYq1JhtRk4WJ5+qPaKk1FhAYtoGAJe8z3D6vVGlOcR8seYNfgWALUnLCfJqT2RgLyRJ4njeXjIKj9TrHHUmI//++++lRdnKKCQlMW0urcBQc7NiX+UsmqvELBqhlTmWm4BdtmMwFSAjo9f6olKqOZab4HIfOM+vSeSFP/bWun31wQwWrN3jGEPiKqqSI6VCjclSjt0uQYUZtcrNcZ+P5SZWWwyuipvag+7thgGQZ0gnJTfxnNfoETYCrUqHxWYi4cQf59ynfWAPAj0ra7XsS99Eubmkxj5+HiFEB/cFYE/6X5RU5CNJEp5up2ciueJ7o6HklqYx4Iz6Ju0DurPnjITsfOpMRioqKvjggw/YsmULNpuNyy+/nPvuuw93d1EdT6gcsLdqfzo+Og1DIkUFWlfSs2dPCgtbT3ehM5QaCzEYC7HbbaglN8cCZAZjkXMDa2HKTcV4uvlRYszHajNhsckoFCrHfTYYC8g31Czw56E5XVbebKk4Z8ICYLdXTnm2y3byyzLPuU+bMxKI4opcSo35NfZRK0+PaSkzFWO1mWqsx9KS3xsqpYaj2TtoH9ADZJnk3F1oVfXLFepMRhYsWIBOp+Pll18G4IcffuDZZ5/lP//5z6VF3YJlFSVzLHc3nUIG4K9v2WXRd6UXkF5czvV9OqBWivozruSrr75i586dzg6jRfN088VqM2GyqrCbT7//G2NF3ktV1eKxYO25a3c8M6aHy7WKVNG7+VJqLKhcV8VWiqeH/tTzPgB0azeUbqFDax54Ro9TiE80bXxqrqtSuVvl/51G6caYbrfUss/pk51d3fRcgjwjMBgLzvFafOo8trkaGjuDf5NXsPXYSiQk2vpEMyR2Rr2OrTMZ2b9/PytXrnQ8fuaZZxg/fvzFR9sqyJQaCyg1FrT4ZGTlqUJnV4mF8YRWRpZlIgN7kWjcgEqpodRc6tgWGdjLeYGdR20JiSsnIlB5PxPTNoBUmV9Udd1U3WeFpKyWeJyLJElInL8cf+U+dY+ZOd/qs1WignpVGzNSxVXfGw1B7+bLqK7zLurYOpMRWZYpKSnBy6tymlpJSQlKZetbd+VCtKYZNSv3paNRKhjbsfUM2G0uvvvuO44fP07fvn2dHUqLk1uaSnLObnqFj6Jn2AiO5SZQWmrA083P5WdMnJ2QuHoiAqcHfDan+3xmzAZjEXo3H5eP+VJlFB5h14m1mK3lnFmEfHq/R+o8ts5kZN68eUyfPp0RI0YAsGHDBm677baLj7YV8ND4AFBmKnJqHI0tJb+UPVmFXNmpLZ5uameHI5zltddew2w288QTTzg7lBal1FhAYup67LIdk6WcEJ9oQnyi2Vmyk74xzSPxOzP5cPVEpEpzvM9VMbcWW5NX0i9yAj7uwfVqYTpTncnI1VdfTffu3dm+fTt2u50PPviA2NjYiw62NVAolLhrvDGYKteocbWpcg3FsTCe6KIRWgmz1ciuE2uw2i30DBuJt3tg3Qe5qOaShAjNh1btTphf54s6ts6Or8OHD7Nw4UJmzZrFwIEDef755zl27NhFXaw18XTzxWIzYbZWODuURlM1XmRSFzGlV2j57LKN3al/UGEuJSqoDyE+jbuCrSA0N8FeHdh27BcyCo9wsviY41991Nky8vTTT3P33XcDEBUVxZ133smTTz7J4sWLLy3qFi7QMwKtyh2Zlrl6b0G5iU3Hcugf7k9bbzHNW2j5DmZuprAsi2CvDkQHNY9uAkFoSnmGyi+oBWdNjx7bve6hHfWqMzJ06OkpU4MGDRLTeuuhnV9HoKOzw2g0vx7MwGaXxcJ4QqsR6BmOwVRE97ArWmzXqyBciqqkw2I1YceOVqWr97F1JiN+fn4sXryYq666CoDVq1fj7+9/kaEKLcXKfWJKr9C6BHlFEOgZLhIRQahFqTGfjYcWU2qsqkjswxWdZtVr9eo6k5FXXnmF559/ntdffx2NRkNcXBwvvfRSgwTeksmyzMGszUhA57aDnB1OgzJZbaw5nEmUvyddgr3rPkBwivj4eBISEpwdRrNWZirmaPZ2urYdglqlFYmIIJzH5qTldGs3jPYB3QFIyd1D/NGljOsxv85j60xG2rZtyyeffAJAaWkpJ0+epE2bNpcYcssnSRJ5pelYbEY6hQxsUX/ENhw9icFk5dbL27Wo19XS6PV6dLr6N5MK1VmsJnYe/51yczHBXh3EgFVBqIPJUuZIRAA6BPao99o0dc6m+fHHH3nssccoKChgwoQJ3HvvvXz88ccXH20ronfzqZxRY2tZM2ocVVfFeBGXdvz4cbKyspwdRrNkl+0kpK2j3FxMh4CeIhERhHpQKFTV1v/JM6SjVNavBlWdLSOLFy/m448/5pdffmHkyJE8+eSTXHvttdx+++0XH3Erodf6ksMJDMZCtPqWMePEbq9cGM/fXcvA9s23xkJrMHnyZMxmMxMnTnR2KM3O4awt5BsyCPQMJ7aVrcItCBerf4dJ/HnwG8dMUpO1nCs6XV+vY+tMRgCCgoLYuHEjc+bMQaVSYTKZLing1uLMsvAtZY2aHen5ZJVUMCcuEpVYGE9ogdLyD3Aifz96rS89w0bUax0SQRAgyCucaX0forgiD5DRa31Rq7R1Hgf16KaJjo5m/vz5pKenM2DAAO6//3569OhxqTG3CnrtqWTE1HLWqFkhZtEILZxSqUar8qBP+ytRKTXODkcQmo2U3D2sTHgPX49glAo1y3e9RWr+/nodW2fLyMsvv8zu3buJiYlBo9Fw1VVXVas7ItTOQ+uDp5s/WlXL6KKByim9biolY2JDnB2KIDSKtj4xBHt1QKmoV8OxIAin7EnbwJXdbgHAS+fPpF73sHb//wj371rnsXX+tqlUKvr1O91nWrVgnlA3pULFoJirnR1Gg0nKK+FAdjETuoTioRUL4wkth8VmJjlnFzHBcSgVKpGICM2aLNvZkryCwrIsFJKSQTFXV6v1kZZ/gIS0DSgkBTHBccS26e/YVmE2sCrhfcZ0uxkf9yDyDRmsP7AIT7fK+mKdQi6nQ+C51zWyyTZ0Gk/HY51GT7Xle89D/MYJ9bZyX+XCeGIWjdCSyLKdxLT15JWmoVW50yFQdEMLzVtq/gFsdgsTet5JTkkq21NWM7LLXADsdhvbUlYzsdddqBQaft3zMe38OuOu8cRut7ElaRkqxekvm/mGDLq0HUy3dnX3iAR7RbDx0GIig3oBEsdzEwn0iqhXzCIZaWQlFfmcLD5GiE+kI7NsrlbuT0OSYFJXsTBec/DGG2+QlJTk7DBc3uGTW8krTSNAH0ZEQDdnhyMIlyy75DihvpXLkQR5hVebbltUkVNt+ECwVwQ5JSm0D+jB9pTVdAy5nD1pfzr2zzdkUFyRS1rBAbx0AfTvMKnWQamXR03hYOZmDmdtRaFQEuzVgU4hl9cr5joHsJrNZhYuXMgjjzyCwWDggw8+wGw21+vkAhiMBRzL3U1B2Ulnh3JJ8gxG4lNyGRARSLCnKKTVHIwePZr+/fvXvWMrll5wmON5e/HQ+tAzfCQKMXNGaAEsNiMapZvjsSRJ2GVb5TarCY3q9Da1UovZauRo9g7c1B6E+sZWO1eAZxhxHcYzrsft6N38SEhbV+t1lQoVEQHd6BhyOVd0up5w/y717vKs8zdvwYIFVFRUcODAAZRKJampqTzxxBP1OrlQfXpvc/bLgQzsslgYT2g5CstOsj/zb9RKLX0irkQtZs4ILYRa6YbFdroEhyzLKCRl5TaVtto2i82ERqUjKXsHmUVJ/LbnEwrKsvjnyA+Um0sJ9+9KgL6yNTzCvysFhuor8p4pJTeR9QcWse3YKkyWClYnfkRyzu56xVxnMrJ//34eeOABVCoVOp2O1157jUOHDtXr5ELljBpo/tN7HVVXu4kumuZi3Lhx3H///c4Ow2UZTEVISPQKH4WHVqyxJLQcQV4RpBdWfk7nlKTi63F6CRcfXRAlFXmYLOXY7Fayi48T6BnOuB63M67HfMb1mI+fRwiDY6/FXePJH/s+J7e08u9/VlHSeWtm7U3fyIQed6JWatBp9FzV+172pv9Z6/5nqrP9RJIkzGazYw2SwsJCsR7JBVAqVLhrvChrxi0jFRYrfxzJpGOgFx2DxB/t5iIzM1N0qZ5HmF8nAj3DcFN7ODsUQWhQEf5dySxKYnXiRwAMipnOsZwELHYTHdtcRv8OE1i7/3OQZaKD486bjA+InsK/yStQSEp0Gk8GRk+rdV9JUlQbT+Ku8QLqly/UmYzMmTOHG2+8kdzcXF566SXWrVvHnXfeWa+TC5X0Wl9ySk9gslagVTW/8RbrjmRRbraJQmdCsyfLMmkFB2nn1xGFpBSJiNAiSZKCgdFTqz3n4x7k+DnMvwth/l1qPf7MVXb99aFM6Fm/z3wf9yAOZm7GLtvJN2RyOOtf/Dza1uvYOpORKVOm0K1bN7Zu3YrNZmPhwoV06tSpXicXKundfCkx5mO2ljfLZOT0lF7RRSM0b0ezt3MsNwGjxVCttoIgCJfu8qgp7EnbgFKhJv7oT4T4RNMvbEK9jq0zGbnnnnt4//33iY6Odjw3d+5cFi1adPERtzIxwf2a7R8+m93OLwfSCdK7cVlEQN0HCIKLyiw8yrHcBNw1XnQIOHfRJkEQLp5aqaFX+Cj6th9LSUUexRV5qC511d67776bgwcPkp2dzciRIx3P22w22rRpU9thwjk05zE2W0/kkWMwclP/aJQKMe1RaJ6KyrPZl7EJlUJDn4ix9V68SxCE+ktIXUdxeS5924/jt72f4OMeTGbhES6LuqrOY2tNRl599VWKiop46aWXeOqpp04foFLh79+8i3c5Q15pOhabiRCfKGeHckFW7j/VRSNm0TQ7V199NSdPNu/6Ng2hwmxg14m12GUbfSLGoHfzcXZIgtAipeUfZFyP2zmQGU9kYG/6dRjPqoT363VsrcmIXq9Hr9fTtm1bQkOrT+V59NFHee211857YrvdznPPPcfhw4fRaDS8+OKLREScLgu7Zs0aPv30UyRJYsaMGVxzzTVYLBYee+wxMjIyUCgUvPDCC0RFNa8P79rsz/wbm83S/JKRfWm4a5SMEgvjNTvPPPMMO3fudHYYTpdnSMNsraBTyAACPMUgbEFoLDJ2VEo16YUH6R0+Blm2Y7XVb0ZfrcnIk08+SVpaGvv27ePo0aOO561WK6WlpXWeeN26dZjNZpYsWUJCQgKvvvoqCxcuBCq7et58802WLl2Ku7s748ePZ+TIkezatQur1cr3339PfHw877zzDu+/X7+sytXptb7klqZithqrVb9zZYeyizmcW8LkbmHo1GLlAKF5CvPrjKebP966QGeHIggtWohPDD/vehuVQk0b7w78tvdTwvxqn7Vzplo/Ye644w4yMjJ46aWXuPvuux3PK5XKerVW7Ny5kyFDhgDQq1cv9u3bV+0cv/76KyqVivz8fAA8PDzo0KEDNpsNu92OwWBApWo5H4B6t8pkxGAqxE/VPFoZHIXORNXVZmnBggWcPHmSvn37OjsUp8g3ZODn0RZJkqpNaxQEoXH06zCeziEDcdd6IUkKLou8Cn/9JU7tbdeuHe3atWPlypWkp6eTlJTEkCFDyMzMxMfHp84TGwwG9Hq947FSqcRqtToSDJVKxdq1a1mwYAHDhg1DpVLh7u5ORkYG48aNo7CwkI8//rheL+LIkSP12q++GqNpu9SWR6m1lMT92/FS1l7BzpV8tzUFhQRhljx27ixq8POLLoTGtXjxYqB13meDLYcc6wG8lKEEqGKa7Lqt8V47g7jPruWfIz/SPewKvHWB1cZkVSUihWXZ7M/YxODYa2o9R51ND7/++isLFy6koqKCJUuWMHPmTB555BEmT5583uP0ej1lZWWOx3a7vUZLx5gxYxg1ahSPPfYYP//8M0eOHGHw4ME8+OCDZGVlMXfuXFatWoVWe/6R77GxsXh6etb1Uupl586djfJNsrgily1JGQT7+9Olret/U80urWDf4gMM7hDEyEGXNfj5G+s+C6dpNBrMZnOru8/FFblsTU7ER/Lj8qgxeLr5Ncl1xXu6abT2+1xaWtrgX8AvVe+IMWw79gsVlhKCvNrjofFGISkxmArJKk7GQ+NNvw4Tz3uOOudqfvbZZyxevBi9Xo+/vz/Lly/n008/rTO4Pn36sGnTJgASEhKIjT29EqDBYOCGG27AbDajUCjQ6XQoFAq8vLwcSYW3tzdWqxWbzVbntZqDqjVqyk0lzg2knlbtT0eWRReN0LwYLWXsOr4Wu2ylZ9iIJktEBKE189B6M7zzLIbEXou72pPiilwKy0+iU+sZGjuT4Z1vqHMWW50tIwqFolp3S1BQEIp61JsYPXo08fHxzJw5E1mWefnll1m1ahXl5eXMmDGDSZMmMWvWLFQqFR07duSqq67CaDTyxBNPcP3112OxWPi///s/3N3d674TzYBKoeaKTtejVTWP8tNiYTyhubHZrew+sRaTtYzYNpcR5BVR90GCIDQYTzd/uoQOvqhj60xGYmJi+Oabb7BarRw8eJDvvvuuXuXgFQoFCxYsqPbcmQNfZ8yYwYwZM6pt9/Dw4N13361v7M2Om1pf904uoMxkYf2Rk3Rt4010gJezwxGEejlZfIziilza+sTQIaCHs8MRBOEC1NnE8cwzz5CdnY1Wq+WJJ55Ar9fz7LPPNkVsLY7VbqGoPAeTpdzZoZzX2iNZGK020UXTzLVt25aAgNZTwj/UN5aeYSPpGjqkWVc9FoTWqM6WEXd3dx588EEefPDBpoinRTtZfIx96Rvp2nbweVdMdLaV+6q6aEQy0pz99ttvrWLWQZmpGHeNF5IkNbuigoLQ0lhsZkqN+fi6t8Fqt6BWaup1XJ3JSKdOnWp8ywgMDHQMThXqT6/1BcBgKnRyJLWz2uysPpBBiJeOuHai7L/g2koq8tl6bAWhvh3p0naQs8MRhFYtsyiJLUnLkWU743veyYpdbzO040xCfWPrPLbOZOTQoUOOny0WC+vWrSMhIeGSAm6tHMmI0XWTkc3Hc8kvN3HbgBgUCtHU3Zz98ccfJCUltdhpkCZrObtOrMFmt+LvUb/CSoIgNJ5dx9cwrsftrNv/Oe4aT8b1mM/GQ4vrlYxc0DKsarWacePG8e+//150sK2ZSqnGTa3HYCpydii1ElVXW46HHnqI9957z9lhNAq73cbuE39gtBiICe5HsHcHZ4ckCK2ejIy75nTNLx/34HofW2fLyM8//3z6QrLM0aNHW1SZ9qamd/MlrzQNi9XkcsuYy7LMyn3p6LUqRsS0cXY4gnBOsiyzP/NvisqzCfGOIjKwl7NDEgQB8NB4kVZwEJAwWSs4lLXFUWOrLnVmFVu3bq322NfXl3feeeciwhSgsqsmrzQNg6kQX5VrfeAfyC4mOb+Uq3uEo1UpnR2OIJxTbmkqGYVH8NIF0q3dMDFzRhBcxIDoaWw7tooyUzFLd7xOiHc0A2Om1evYOpORV155BYvFQkpKCjabjZiYGNEycgnC/bvQ1ifaMX7ElYhZNEJzEOgZTqeQy2njHYVSIf4WCYKr0Gn0DOt03UUdW+dv8r59+7j33nvx8fHBbreTl5fHhx9+SM+ePS/qgq2du8Z1i4it3J+GUiExvnPzWMhPaF2sNjMqpQZJkmgvipoJgss5nreXvWl/YbJWVHt+er9H6jy2zmTkxRdf5O2333YkHwkJCbzwwgv89NNPFxetgCzbMVkrcFO7Tmn4zOJytqXmMzw6GD931xrLIghmq5Etyctp4xVJbJv+omtGEFzQ9pTVDIm99qJa/utMRsrLy6u1gvTq1QuTyXTBFxJO++fIj1jtFoZ3vsHZoTis3J8OiFk0LcmKFSvYt2+fs8O4ZHbZxu7UP6gwl6JQKEUiIgguysvNn2Cv9kjSBU3UBeqRjHh7e7Nu3TpGjRoFwLp16/Dx8bngCwmn6bReLjej5vTCeCIZaSnat29Pfn6+s8O4JLIscyAjnsKyLIK9OhAd1DJrpghCS9A1dAi/7/2MNt4dqiUkvcJH1XlsncnICy+8wMMPP8yTTz4JQFhYGK+//volhCu42oyaUqOFP4+epEeIL+39msdifkLdDAYDFRUVde/owlLz95NeeAhPN3+6h10hWkUEwYUlpm3AWxfYOC0j7du358cff6S8vBy73Y5eLz6sLtWZZeF9PZyfjPx+OBOzzc5V3do5OxShAQ0aNAiz2czBgwedHcpFKSrP4WDWZjQqHX0irkSlUDs7JEEQzsMu2xkce81FHVtnMrJnzx4+//xzCgsLkWXZ8fxXX311URcUKgufARiMRc4N5JSqKb2TRReN4GRZRUkcy03AYCzEQ+uDr3sIHUP6o9OIL0GCUF+ybGdL8goKy7JQSEoGxVyNl+70Ct5p+QdISNuAQlIQExxHbJv+jm0VZgOrEt5nTLeb8XEPoqQij3+O/ghI+LoHc3nU5FpbPtr6RHMwczOhvrEopNPphd7Np86Y60xGHn30UW644Qaio6NFE2kD0Z+qSOcKC+ZZbHZ+PZhBmI87vUP9nB2O0ECyipIYPasbel834o/+RGRgL0J8op0d1nllFSWRmLYBZBkkyfH7UWEuvaCy0oLQ2qXmH8BmtzCh553klKSyPWU1I7vMBSqXUtiWspqJve5CpdDw656PaefXGXeNJ3a7jS1Jy6q1Qm5PWU3v8DGE+ESxOWk5qfkHiAjods7rpuQmArA/4+8znpUaZmqvm5sbs2bNqvNEQv2plBq6hQ7FwwUKn/19LJuiCjPX9+kgks0WoupD3TvAHUkhUWosIDFtAyUV+Y5WuTOplW4EeYUDUGYqpqg8+5znbeMdiVKhwmqzkF2Scs59fD3aOGrpZBenYLGZa+zjrvXCzyMEgKLybEcL4YHMfzBZyjFZK1ArtejUepDgWG6CyydSguBKskuOE+rbEYAgr3DyDRmObUUVOXi6+aNVuQMQ7BVBTkkK7QN6sD1lNR1DLmdP2p+O/fMNGbTxjgSgnW8smUVHa01Gpvd79KJjrjUZyczMBKBz5858+eWXjBw5EqXydInwtm3FKpmXop1fJ2eHAJw5pVeMF2kpjuUmgAxefjqsVpvj+cMn/0Wj0tXY38stwJGMFJRlnvWt5rRAz3CUChUWm5G96X+dc58eYcMdycjhk9soNxfX2KetT4wjGckqSuJE/v7KaxsyHfucmRi7SnemIDQXFpsRjdLN8ViSJOyyDYWkxGI1oVGd3qZWajFbjRzN3oGb2oNQ39hqyYiM7Ph9rNr3bLtP/EHviNH8c+THc8ZTn3EktSYjN9xwugbGv//+W22MiCRJrF+/vs6TC3WTZdlpLRKVC+Ol4eWmZliUaAZvKQzGQiosBrTuauQy2dHtoZCUdAsdWmN/9Rl/tPw8QugWOuyc560qva5WutW6j4/u9PuoY5v+WO2WGvucWYU4xCcGL10gUNm0W2EuRZKkyphO/VrUp79ZEITT1Eo3LLbT9cBkWUYhVTYmqFXaatssNhMalY6DmfGARGZREgVlWfxz5AdGdJmLhFRj37MF6Curdle1oFyMWpORDRs2XPRJhbrllqayN30jMcH9CHNSK8merEJOFJYxo1d7NGJhvBZDqVBRYS7BTeuGZHGDU8mur0ebOlvkPLQ+da6yqVKqaefXsc44gr071LmPj3sQPu5BACgkReWYkbOIVXkF4cIEeUWQVnCQDoE9yClJrTZr00dXOSjVZClHpdSQXXycrqFDad+ju2Of3/Z8woDoqbhrPPHzaEtWUTIhPlGkFx4h5BwJR5h/FwDKzSX0CBtebdvO47/XK+Zak5HHH3/8vAe+8sor9bqAcG4qhRaztYIyJw5iXbnvVBeNmNLbYpRU5FFhLgNJIsC7LRXq002qrv6hXjUupHI2TRF6N59mMfBWEFxNhH9XMouSWJ34EQCDYqZzLCcBi91ExzaX0b/DBNbu/xxkmejgODy03rWeq1/kBDYfXcauE2vw1gUSEdC9xj47jv+G0WwgreAgJRV5judl2U5uaRp924+tM+Zak5H+/fvXtkloAFUDCUuNTkxG9qehVioY10ksjNcSmK1Gdp1Yi1qloVfQSArLT1JRnoqnm1+z+VAP8YluFnEKgiuTJAUDo6dWe66qBRIqWzKqWjPOZVyP+Y6fvXWB1R6fS3v/bhSV55BVnFytq0aSFPQMH1mvmGtNRgYPHkxgYKBjIKvQsNRKDVqVh9NaRtIKy9iVXsCo2BC8dRqnxCA0LJVSQ7BXBBqVO1FBvZkzZw6FhYWsWrXK2aEJgtCCBXiGEeAZRrh/12qDYy9ErcnIU089xSeffMINN9yAJEnVCp6JAawNQ+/mS74hHYvNjFrZtAnBqlOzaCaLhfFaDIWkoHPbQY7f1cTERMzmmlNrBUEQGsPFJiJwnmTkk08+AcRA1sbkeSoZMRgL8fVo2tksK04tjDdJTOlt9lJyE5GBDgE9kCRJ1IsRBKHZqXM1mz179vDFF19gNpu56aabuPzyy9m0aVNTxNbiBXqGEx3UF6265lSpxlRcYWZjcjZ92vkR5uvRpNcWGlZOyQkOn9zKibx9WM9RYEwQBKGpJGXvrPHcwcwt9Tq2zgqsL774Ivfccw9r1qxBq9WybNky7rnnHoYOrVmvQLgw/vpQ/PVNP3j0t0MZWGx2rhJdNM1aVWVVhaSiT/sxqFVaZ4ckCEIrtD/jHyw2I4dPbq22zIldtpOSm0DntgPqPEedLSN2u50hQ4bw119/ceWVV9K2bVtsNltdhwkubMWphfHElN7my2StYNfxNdjsFrq3G4b3qcJhgiAITc2xCJ9c/XmlQsXgmPqt4ltny4hOp+Pzzz9n69atPPPMM3z11Vd4eIim/YayP+Mfyk1F9Iuc2CTXM1tt/H4okwhfD3qEOH9tHOHC2WUbCSf+oMJSSlRQH0J8os6539ChQ8nPz2/i6ARBaG3C/DoR5teJ9gE9qk0hvhB1JiNvvPEGP/74I++99x7e3t5kZ2fz5ptvXtTFhJrKzSXkl2VitZlRNcGMmr+SsykxWpjXL0oMdGymZFnGTaOnjTqS6KC+te73/vvvs3NnzT5cQRCEhrRu/5eM6jqPdfu/AGp+rjTIqr3BwcHcfffdjscPP/zwhUUpnJde61M5o8ZUdNEZ5YVY6eiiEeNFmiulQkWPdsORsYuEUhAEp4sM6gXAFZ2ux02tv6hz1DlmRGhcVZVYDU1QiVWWZVbtT8dXp2FIh8ZPfISGlVuaRnrBIaCy1k/Vwle1WbhwIcuWLWuK0ARBaMV2n/gDu2xjc9Jy9G6+Nf7VR50tI0Lj0mtPJSNNUIl1V3oB6cXlzOrbAZVS5KHNicFYSGLqOuyyHX99O3Saur99fPzxx5jNZl566aUmiFAQhNYq2Ks9X8c/hQws+uf0unYylZ02cwfXvZadSEacrCmTkZWnCp2JKb3NS+WaM2uw2i30CBtRr0REEAShqQyOvYbBsdew/sAiRnaZe1HnEMmIk6lVWtp4RzqSksa0cl86GqWCKzu2bfRrCQ3DLttISP2DcnMJkYG9aSsWkRMEwUVdbCICIhlxCb3CRzX6NVLyS9mTVcjYTm3xdFM3+vWESyfLMgczN1NQlkWwV3tiguOcHZIgCEKjEAMHWomqhfHELJrmQ8ZOhcWAp5sf3dsNFzNnBEFosUTLiAsoNRZwIm8fwd7tCfQMb5RrVI0XmdRFVF1tLhSSkr4RV2KxmVEpL7w1S61Wi2rJgiA0CyIZcQFWm5n0wkOolJpGSUYKyk1sOpZD/3B/2nq7N/j5hYZVZirGYCwk2Ls9kqS46GW5d+zYIYqeCYLQLIhuGhfQ2DNqfj2Ygc0ui1k0zYDFamLn8d/ZnbqWUmOBs8MRBEFoEiIZcQFqlRatStdohc9E1dXmwS7bSUhbR7m5mA4BPfF087uk8yUkJHDkyJEGik4QBKHxiG4aF6HX+p5ao8ZyUeMDamOy2lhzOJMof0+6BHs32HmFhnc4awv5hgyCPCOIbdPvks83d+5czGYz1113XQNEJwiC0HhEy4iLcJSFb+Cumg1HT2IwWbmqWzsxG8OFpeUf4ET+fvRaX3qEDUeSxK+mIAith/iL5yI8dQF4uQVglxt29sOKfaLqqquTZZms4mOolW70aX9lk6zeLAiC4EpEN42LaOfbkXa+HRv0nHZ75cJ4/u5aBrYPbNBzCw1HkiTi2o+j3FyCu8bL2eEIgiA0OdEy0oJtT8vjZGkFE7u2EwvjuSCLzUxBWRYACoWy3qtbCoIgtDTiE8qFZBencCwnocHOt7Kq6mpXUejM1ciyncS09Ww/9guFZSedHY4gCIJTiW4aF3Iifz8FZZmEB3RFpbj0GTUr96XhplIyOjakAaITGtLhk1vJK00jQB+Gt3tQo1zjv//9L4cOHWqUcwuCIDQkkYy4EL2bLwVlmZSZivDWXdoYj6S8Eg5kFzOxSzs8tGJhPFeSXnCI43l78dD60DN8JIpGmjnTr18/FArR+CkIrY0s29mSvILCsiwUkpJBMVfjpQtwbE/LP0BC2gYUkoKY4Dhi2/THLtvZfHQpJRV5SJLEoJhr8NL5k2/IYP2BRXi6+QPQKeRyOgT2bPCYRTLiQvRaHwAMxsJLTkZW7qtaGE900biSgrIs9mf+g1qppU/ElajFzBlBEBpYav4BbHYLE3reSU5JKttTVjOyy1wA7HYb21JWM7HXXagUGn7d8zHt/DqTW5oKwPied5BVlMz2lF8Y2WUu+YYMurQdTLd2Qxs1ZpGMuJCGLAu/cn8akgQTxcJ4LiU5ZxfI0Ct8FB7axi1CN2DAAIxGI7t3727U6wiC4FqyS44Temp2ZpBXOPmGDMe2ooocPN380aoq1ykL9oogpySF9gE9CPPrBECZqQid2hOAfEMGxRW5pBUcwEsXQP8Ok1CrtA0ec6MlI3a7neeee47Dhw+j0Wh48cUXiYiIcGxfs2YNn376KZIkMWPGDK655hoAPvnkEzZs2IDFYuG6665zPN8a6E+V/y4zFl3SefIMRuJTchkQEUiwp64BIhMaSu/wMRSWn8RfH9ro1yovL8dsNjf6dQRBcC0WmxGN8vQCm5IkYZdtKCQlFqup2uKbaqUWs9UIVK4U/veRH0jN388VnWYBEOAZRkybfgTo25GYtoGEtHX06zChwWNutGRk3bp1mM1mlixZQkJCAq+++ioLFy4EwGaz8eabb7J06VLc3d0ZP348I0eO5OjRo+zevZvFixdTUVHB559/3ljhuSSNyg2NSofFfmkfIL8cyMAui4XxXIUs2ykzlaB380GlVBPoKf5fBEFoPGqlGxabyfFYlmUUkrJym0pbbZvFZkKjOv2ldUjstZSbS1md+CFT+jxAuH9XtKe2R/h3ZWvyykaJudFGt+3cuZMhQ4YA0KtXL/bt2+fYplQq+fXXX/H09KSoqAgADw8P/vnnH2JjY7nrrru4/fbbueKKKxorPJd1RcfruSxy0iWdY+X+qoXxRBeNKzhycjubk5ZWayoVBEFoLEFeEaQXVs6kyylJxdejjWObjy6Ikoo8TJZybHYr2cXHCfQMJzlnF3vS/gRApVAjISFJEn/s+5zc0srPlKyipEZr1W20lhGDwYBer3c8ViqVWK1WVKrKS6pUKtauXcuCBQsYNmwYKpWKwsJCMjMz+fjjj0lPT+eOO+7g999/r3NNlYZemXTnzp0Ner6mZLTaWXMwnQgvDYa0JHamOTui2jXn+1xfpbaT5FoPoZZ0JB9K47jUdDVFqrpoWsN9dhXiXjcNcZ/PL8K/K5lFSaxO/AiAQTHTOZaTgMVuomOby+jfYQJr938Oskx0cBweWm/C/bsRf/RHftvzMXbZTv/IiagUagZET+Hf5BUoJCU6jScDo6c1SsyNlozo9XrKysocj+12uyMRqTJmzBhGjRrFY489xs8//4yPjw+RkZFoNBoiIyPRarUUFBTg7+9/3mvFxsbi6enZIHHv3LmTvn37Nsi5LobFZqKwLBudRn9RS8iv2p+G0XaIa/vG0Ldvn0aIsGE4+z43hcKybLal7MZX8mdA9NRGH7B6No1Gg9lsbvH32VW0hve0K2jt97m0tLTOL+CSpGBg9NRqz/mcUc8ozL8LYf5dqm1XKzWOcSJn8teHMqHnnZcQcf00WjdNnz592LRpEwAJCQnExsY6thkMBm644QbMZjMKhQKdTodCoaBv3778/fffyLJMdnY2FRUV+Pj4NFaILqm0Ip9dJ34nqyjpoo53TOkVVVedqsJcyu4Ta0CWm2TmzLncfPPNTJp0aV1+giAITaHRWkZGjx5NfHw8M2fORJZlXn75ZVatWkV5eTkzZsxg0qRJzJo1C5VKRceOHbnqqqtQKpVs376d6dOnI8syzzzzDEqlsrFCdEkep9YnMRgvfHqvzW7nlwPpBOnduCwioO4DhEZzKGsLZpuRziEDCfB0TmJ47733iuZsQRCahUZLRhQKBQsWLKj2XFRUlOPnGTNmMGPGjBrHPfLII40VUrOgVenQKN0uqtbI1hN55BiM3NQ/GqWovOlUXUOH4ufRlnD/rs4ORRAEweWJTywX5OHmS7m5BJvdekHHrdgnZtE4m8VaOWVOo3IjIqBbnYOvG9MDDzzAO++847TrC4Ig1JeowOqC9FpfCsuyKDMVVVtPoC4r96fjrlEyyoUXxssqSuJYbgKZplSMR1OIDOxFiE+0s8NqEJlFSRzI+IfeEaObpKhZXdavXy+KngmC0CyIlhEXpK8aN2Iqqvcxh7KLOZJbwpiObdGpXTPHzCpKIjFtAyUVedhkM8XluSSmbrjowbqupKg8h33pGwHZUWZZEARBqB/X/NRq5dp6RxPs1f6CPtQchc5cuOrqsdwEkKHUWIBZrqCo3IgkKdh67Be6hg4mQN+uWnGe5sJoKWP3ibXYZRu9I0Y7kklBEAShfkQy4oLUKi1qLmwhopX70lFIEhM6O797oDYGYyFI4KbWY7FYUas02OwWyk3FJOfswmytcCQjGYVHMFnK8XIPwFsXiFrZ8AszNQSb3cquE2swWcvpFHI5gZ7hzg5JEASh2RHJiIuy2EyUm0vw1gXWuW92aQX/puYypEMQAXq3Ovd3Fr2bL6XGgso1eCQPPN0qC9W5a7zo3HZgtZag9IJDFJafrlbqrvHGWxdAgGcYob6xNc7tLIey/qWkIo92vh2J8O/u7HAEQRCaJZGMuKhdx9dQWH6S0V1vQqmo/b/p+TWJ7ErPR5bhqm6u20Vjs1tRKtTYZTsKqfpQpZjguBotCj3CRlBSkUtxRS7F5TkUV+SRVZwM4EhG0goOUlSeg7cuEG/3QDzd/ByLQTWVqKBeAHRuO8CpM2fOpXPnzhQXFzs7DEEQhDqJZMRF6d18KSw/ed4ZNc+vSWTB2j2Ox648XuRQ1haKyrMJ1IdhtlVQWmrA082v1tk0Oo0enUZPsHcHoHLVyXJzCbIsO/bJK00ju+Q4GYWHgcoSyF5u/gTo2xHTpl+jvp6q5bjd1Hq6hg5u1GtdrO+//14UPRMEoVkQyYiL0mtPz6g5VzJydiIC8M3OYzx7Zc8mie9C5JScIK3gIJ5ufvRpfyVKhYqdJTvpG1P/9SUkSapRUr1n+CjKTIUUl59qQanIpcSYj1p1uqsqreAgmYVH8XYPwlsXgLcuCJ3G85JaMYorcklIXUfPsBH4uAdf9HkEQRCESiIZcVGO6b3GghrbzpWIAI7nXCkhMVnK2Zu+EYWkpEfYiPN2OV0ohaTA080fTzd/2tEJqOwOsthMjn3KTSUUlp+sNv5ErdTi5xFC74gxQGWrS32TE6OljF3H12KylmG2GhvstTSGn376iZSUlFa9qJggCM2DSEZc1OlaI9XLwteWiFRxpYRElmX2pm/EYjPSKWTARa1CfKGUClW1hKdjyGVEBfWhxJhXOQblVCvKmYlERuERjmZvx1sXiJcu4FQrSiCaUy0sVYXaSo0FVJhLUShUdG93BUFeEY3+ei7FCy+8gNls5uGHH3Z2KIIgCOclkhEXpVHqUCu1GIxFzg7lohlMBRSUZRKgb0eEfzenxaFSqvHzCMHP43RlWrtsc/wsyzZAIqf0BDmlJxzPu2u8iArqw970v5BlGYOpEIvViEalw03l0ZQvQRAEoUUTyYiLkiSJnuEjaxQ+q2rxqK115JkxPVyiVQTA082fgdHTUCk1LjfT5MxZN2H+XQjz74LRUkZJRd6pGTy52GUrx/Mq77PZZsRiNaJSavDQ+pCSl0Bb35ZRxl4QBMHZRDLiwgL0517w7ro+HXh1/T7MNnu1510lEbHbbcjIKBWqZlWN1E3tgZvao1r3y5q9nwEgIaFR6XDXeiFJUrNusRIEQXA1Ym0aF2eX7VjtFsfjUqOFaV/8hdlmZ8oZdUVcJREBOJK9nS1Jyyk3lzg7lEtWlUxpVG7o3XwdLSp6Nx8nRiUIgtCyiJYRF1ZYls22lFV0COhJbJt+2O0y876P52B2MfcN7cRbk/vx/JpEwDUGrALkGdI5nrcHd403GpXO2eFcssjAXiSmbTjn84IgCELDEMmIC9Np9MiynbJTM2peWb+Xn/emcUVUMK9NrJyu6SpJCIDZamRv2l9IKOgRNhyVQu3skC5ZVUG2Y7kJGIxF6N18ai3U5mo2btxIQkKCs8MQBEGok0hGXJhW5X5qRk0hqw+k8+yaRMJ9Pfh+zlDUStfqYZNlmf0Zf2OylhMT3A8f9yBnh9RgQnyim0XycTYfHx88PT2dHYYgCEKdXOsTTaimsuqoD3llBcz97m+0SiVL5w0j0AUXw8soPEJ2SQq+7m2IDHSd1prWLCMjg9zcXGeHIQiCUCfRMuLi1Epv9mbtRylp+Pia4fRp5+/skM5Jp9Gj1/rSI2w4kiRyXFcwfvx4zGYzY8eOdXYogiAI5yWSERcmyzJfbM9Gr7Jy2+VtmB0X6eyQauWvD2VQzHSXqyciCIIguD7xFdaFvbp+Hz8kGsgqi+LhEYOcHc45ZRYexWgpAxCJiCAIgnBRRDLion49mMHTvyfgrvXhP5On4aXzcXZINRSWZbMn/U92HV+DLMvODkcQBEFopkQ3jQs6mlvCDd/8jUap4Kd5VxDk6Xr1Oqw2M3vSK+tvdGo7QLSKCIIguAhZtrMleQWFZVkoJCWDYq7GSxfg2J6Wf4CEtA0oJAUxwXHEtumPXbaz+ehSSirykCSJQTHX4KXzp6Qij3+O/ghI+LoHc3nU5EYZFyhaRlxMVYXVYqOFj6+5nLgwfw5kxvPnwa+x2211n6CJHMiMp8JcSmRgr2oL0AmCIAjOlZp/AJvdwoSed9K3/Ti2p6x2bLPbbWxLWc2YbjcxtvttHD65jXJzKWkFBwEY3/MOeoWPZnvKLwBsT1lN7/AxjO9xO/KpczcG0TLiQmRZ5qYlmzmQXcw9QzoxJy4KqHzzmKwVlJmL8HRz/myarKJkMouO4qULJDq4r7PDEWrxyiuvkJyc7OwwBEFoYtklxwn17QhAkFc4+YYMx7aiihw83fwdi7AGe0WQU5JC+4AehPl1AqDMVIROXVmjKN+QQRvvyskT7XxjySw6SkRAw6/CLlpGXMhrG/axbE8qw6KC+c+k0x/yVeujuMLibHbZxuGTW1FIKnqGjai2+q3gWsaPH8/AgQOdHYYgCE3MYjOiUZ6uRyVJEna5smXdYjWhUZ3eplZqMVuNQOVq5n8f+YGtx1Y6Eg4Z2dENf+a+DU20jLiI3w5m8NRvCbTzduf72UOqVVjVa08lI6fKwjuTQlLSP3IiBmMhHlpvZ4cjCIIgnEWtdMNiMzkey7Ls+OKoVmmrbbPYTNXWERsSey3l5lJWJ37IlD4PICHVum9DEi0jLiApr4Qbvv0HjVLB0htrDlg93TLi3GRElu0AuGu8CPKKcGosQt2uuuoqHnroIWeHIQhCEwvyiiC98BAAOSWp+Hq0cWzz0QVRUpGHyVKOzW4lu/g4gZ7hJOfsYk/anwCoFGokJCRJws+jLVlFld296YVHCPZq3ygxi5YRJzOYKgesFlWY+d+MgcSF1RwTolW5o1JonNoyUlKRR2LaBrq3G4aPe7DT4hDq78SJE5jNZmeHIQhCE4vw70pmURKrEz8CYFDMdI7lJGCxm+jY5jL6d5jA2v2fgywTHRyHh9abcP9uxB/9kd/2fIxdttM/ciIqhZp+kRPYfHQZu06swVsXSERA90aJWSQjTiTLMjd9v5n9J4u5a1BH5vWPOud+kiQREdANpcI5/102u5XEtA2UmYqw2sSHmyAIgiuTJAUDo6dWe+7MxUvD/LsQ5t+l2na1UsMVnWbVOJe3LpBxPeY3TqBnEMmIE72+YT9L96QyNDKINyfHnXffmODzb29Mh7L+pcxURIR/VwI8w5wWhyAIgtAyiTEjTvL7oQye/G135YDVOUOrDVh1JTklJ0grOIBe60tsm8ucHY4gCILQArnmJ2ALl5xXyqxv/jlVYXUYwfWosFpuKmH3ibWk5u9vgggrmazl7Evf+P/t3X9UlPWeB/D3Mz9g+D2CqIiiIOJF71U3DdFUyi2t7WrdZBei0MpqK89Jy2O6ncRz9ZyMdnNdPccI3bt6UFMpTubWSdKuqWmsouAVzN+C/AhlGIThx/x89g9gEi+C4DPzheH9+kvmmXnmfZ4znvnM83yezxeSpMKEiFnCLhMREZFn47eLm93dsPpwxMCuXwRApVKhqu46JEmFiJBxLk7ZwmJrhkbtjahBE3vFsDXqnnnz5qGqqkp0DCKiLrEYcSNZlrFozwmc+7UWb3XSsNoRb40fNCot6ptrXJiwvQBdMKaNfg5qiR+Tvmjt2rXIz88XHYOIqEu8TONG//7XInxRWIIZUYOwvouG1btJkgR/3QA0muuck/RcpcF8Gw3m2wBa7zfnInhERORCLEbc5MAvFXj/2zMID/LFnh42rPp5D4AMBxrNdS5I2MLhsKOg9CCOX/4STRaTy96HXG/dunXYvn276BhERF3i+Xc3uFJdj5QdR7vVsNqRO8fCt01lVdqlqlOobzZg2IAx8PHyd8l7kHvs3r2bQ8+IqE9gMeJiDWYr5m9raVjdmjQVcffZsNqRIN9QDPQfBo1Kq2DC3xhM5bhWXQhfr0D8LowLrBERkXuwGHGhtobVv1XW4s1pMXg5LvqB9hfsF4bgyDCF0rVntZlx9sZhSJAwfvgsaNSuKXiIiIjuxp4RF/qPvxYju7AE0yO737Dqbhd+zYPZ1oDowZPajQ0mIiJyNZ4ZcZHcC+0bVr00akX2W1l7GQZTBcaGP+JcEloJowdPhlbjjajQiYrtk4iI6H7wzIgLXDXUIyXrKDQqCdkLZ2JIYM8aVjtSbSpHmfEXxe+o8db6YsyQKZAkfiQ8RWhoKPR6vegYRERd4pkRhTW0Tlg1NlmQ+S/xmDIiVNH9K3lHjUN2oLD0IIYHx3IBPA908OBBDj0joj6BP4MVJMsyXt3b0rD6xrQYLJoyWvH38NfpAQCmZuMD7+vqzTOoqruOcuPFB94XERFRT7EYUdAnh4uxt6AEj4wMxX+6qGHV3zsYQMuZkQdhbKjC5Zv50Gn9MTZ8uhLRqJc5fPgwTp8+LToGEVGXeJlGId9fqMC/fXMGQwN9sHdhgmINq3fTaf2gVmkf6MyIzW7B2bIfAADjhz0KrdpbqXjUiyxZsgQWiwWvvfaa6ChERJ1iMaKAa4aWCasalYTslxIUbVi9myRJCPIJhSw7IMtyj9aNOV95HE2WekSFTkSw/1AXpCQiIrp/LEYeUEvD6o+oabTgs3+OR7zCDasdiYv6Y49fa7NbUddkQKBuIKIHT1IwFRERUc+wGHkAsizjtb0/42ylEf86NQavxivfsKo0jVqLqaOehcXerOicEiIiop5yWQOrw+FAWloakpKSkJqaipKSknbbDxw4gPnz5yMxMRHZ2dntthkMBiQkJODKlSuuiqeI9YeLsafgOqaNDMWGZ903YdVqN6PMeAEGU/l9v0aWZTSYawEAKpUaOq2fi9IRERF1j8uKkYMHD8JisWDPnj1YtmwZPvroI+c2u92OTz75BNu2bcOePXuwdetW1NTUAACsVivS0tKg0+lcFU0RBy9WYqWzYVW5Cav3w2q34FzZjyir+eW+X3O9+iyOXfoCN+tKun4yERGRG7nsMk1+fj5mzJgBAJg4cSLOnTvn3KZWq/Htt99Co9HAYDAAAPz8Wn6pp6enIzk5GZmZma6K9sCuGerxfNYRqFsbVsMCfd36/j5af6hVmvu+vbeuqRoXq07CS+2NIK47029kZ2ejqKhIdAwioi65rBgxmUzw9/d3/q1Wq2Gz2aDRtLylRqNBbm4u1qxZg4SEBGg0GuTk5CA4OBgzZszoVjFy8aKyQ7s6m1rZbHNgUe411DRa8H5cGLTVpcivLlX0/e9Hk8WG23IpTt0+1ekdNQ7ZjnJrPqxyI4Zox+NcYbEbU3aO00FdLyIigsfZjXis3YPH2fO4rBjx9/dHQ0OD82+Hw+EsRNrMnj0bjz/+OFauXImvvvoKOTk5kCQJJ06cwPnz57FixQp8+umnCA3t/A6VmJgYBAQEKJI7Pz8fkyZ1fJeJLMt4cecxXKo14/Wpo7E2MV6R9+wJ7Y16VNReRGxMNPy89fd8XnH5Mehq1BgTEo/YoY+4L2AXOjvOpAyLxYLTp08jPl7c57Q/4WfaPfr7ca6vr1f8B3hv4LKekYceeghHjhwBABQUFCAmJsa5zWQy4cUXX4TFYoFKpYKPjw9UKhV27tyJHTt2ICsrC7GxsUhPT++yEHGnDUfOY/eZ65g6IhQbnn1YaJa2dWk6G35WXX8DpTXF8PcegJghU9wVjXqJhx9+GC+//LLoGEREXXLZmZEnnngCP/30E5KTkyHLMj788EPs378fjY2NSEpKwty5c/HCCy9Ao9FgzJgxmDdvnquiKOLQxUq8t/80wgJ9kP3STHi7sWG1I20L5jVbG+75nCCfQRiqH42RA8dDreJd3ERE/YEsO3Diyj4YGyqhktR4ZPR8BPoMdG6/YShGwY0foJJUGD14MmKGxMHhsOPYpS9gMhvhcNgwfvgsRISMhcFUjkPF2xGgCwEA/C4sHpGhExTP7LJvKJVKhTVr1rR7bNSoUc5/JyUlISkp6Z6vz8rKclW0brteY8LzWUehVknYu2Cm2xtWOzLQPxxPjHul0yJDq/HG+OGPuTEVERGJVmooht1hxdMT3sLNulKcvPYN/nHsQgCAw2HH/137Bn+cuBgalRe+PZuBYcGxKDdegLfWFzPHJKHZ2oD9BRudxcjYodPx+2EzXZqZP5e70GixYf7/HIah0YxPE6dgWmTvuBtFpbr3mZky4wWoJQ3C9KPu+RwiIvJMVXXXET5gDABgUGBEu5lUtU03EaALgbem5Uf14MARuFl3DSMH/gEjQ/7gfJ6Elu8Yg6kct5tu4UZNMQJ9BiIuci60GuXXM+OqvZ2QZRmv7z2BggojXo2PxutTY7p+kRs1WUy4WVcCh+xwPmZqrkVx+U8orjgGq90sMB0REYlgtTfDS/3brC5JkuCQ7S3bbGZ4aX7bplV7w2JrhlbtDa3GG1abGYd/2YmHRswGAAwMGI7Jkf+Ep8a/AX9dMApuHHRJZhYjnfivI+fxeWvD6sY/xYmO83cuVZ3E6ZIDaLLUA2i5jffsjR/gkG34ffhMrsZLRNQPadW6dj9GZVl2Lv+h1Xi322a1m+GlaVnctcFci+/OZWJU6D8gatBEAEBEyDgM9B8GABgRMg41pgqXZGYxcoc/HyhE5tmbAIAfLlXivf89jSEBLRNWRTesduTuO2ouVZ1CXXM1wgeMweCgSJHRqBd49913kZKSIjoGEbnZoMARKDO2TOi+WVeKAX5DnNv0PoNQ11QNs7URdocNVbevIzQgAk2WeuSe+29MGvkURg/57W7R78/9BbfqbwAAKmsvI8Q/3CWZ2TPS6s8HCrEm9ywAwPerk9iZfw0qSUL2wpkYGiS+YbUjbXfUmMxGaExeuHarEL5egYgNmyY4GfUGCxcu5HAoon5oRMg4VNRexjeFmwEAj4xOxNWbBbA6zBgzZAriIp9GbtFfAFlG9ODJ8PMOQt6Vr2G2NaGw9BAKSw8BAJ4Y9wqmRj+Ln6/sg0pSw8crANOin3NJZhYjaF+IAMDGoy0V5eZe1LDakQbLbdxuvIUzJd+3XgOUET/qWWjUWtHRiIhIEElSYVr0n9o9pr9jKZDhIWMxPGRsu+1TRs3DlFF/P2IjxD8cT094yzVB79Dvi5G7C5E7Vd5udHOa+1dZexkXKn6GXbYBDkCrDoLNYUWTpa7dh476r0WLFsFoNCInJ0d0FCKiTvXrYqSzQgQA1n7/N0iShNVzlB/w8qCu3ioAJEAtaWCXbZAAaNVeuHqrAGH6aNHxqBc4deoULBaL6BhERF3q18VIX9bWtOqvGwAJEgCp9fFacaGIiIh6oF/fTbN6zgSkzR5/z+1ps8f3yrMiwG930qhVmpYBaFLb43pxoYiIiHqgXxcjwL0Lkt5ciABAVOjEbj1ORETUW/EyDeAsOtr6R3p7IQLA2Rdy9VYBTM218NfpERU6kf0iRETU57AYadVWfFRUVPT6QqRNmD6axQfd09SpU2EwGETHICLqEouRO6yeMwH5+TbRMYgUkZGRwaFnRNQn9PueESIiIhKLxQiRh9q6dSv27dsnOgYRUZdYjBB5qE2bNiE7O1t0DCKiLrEYISIiIqFYjBAREZFQLEaIiIhIKBYjREREJFSfnjPicDgAAI2NjYrut76+XtH9Ucd4nF0rOjoaNpuNx9mNeKzdoz8f57bvu7bvP08hybIsiw7RU1VVVSgrKxMdg4iIyK2GDRuGwYMHi46hmD59ZiQkJAQAoNPpoFLxihMREXk2h8OB5uZm5/efp+jTZ0aIiIio7+PpBCIiIhKKxQgREREJxWKEiIiIhGIxQkREREKxGGlltVqxfPlypKSkIDExEYcOHRIdyaMZDAYkJCTgypUroqN4rM8++wxJSUl47rnnuGCei1itVixbtgzJyclISUnh59kFCgsLkZqaCgAoKSnB888/j5SUFKxevdrjZm30ZyxGWn399dfQ6/XYtWsXtmzZgrVr14qO5LGsVivS0tKg0+lER/FYeXl5OHPmDD7//HNkZWXh119/FR3JI/3444+w2WzYvXs3Fi9ejA0bNoiO5FG2bNmCDz74AGazGQCwbt06LF26FLt27YIsy/zR6EFYjLR68sknsWTJEuffarVaYBrPlp6ejuTkZAwaNEh0FI917NgxxMTEYPHixXjjjTfw6KOPio7kkSIjI2G32+FwOGAymaDR9OnRTb1OREQENm3a5Py7qKgIcXFxAICZM2fi+PHjoqKRwvg/p5Wfnx8AwGQy4e2338bSpUvFBvJQOTk5CA4OxowZM5CZmSk6jscyGo2oqKhARkYGysrK8Oabb+K7776DJEmio3kUX19flJeX46mnnoLRaERGRoboSB5lzpw57aZsy7Ls/Az7+fn167HwnoZnRu5QWVmJBQsW4JlnnsHcuXNFx/FIX375JY4fP47U1FScP38eK1aswK1bt0TH8jh6vR7Tp0+Hl5cXoqKi4O3tjZqaGtGxPM62bdswffp0HDhwAPv27cPKlSudlxRIeXdO2m5oaEBgYKDANKQkFiOtqqur8corr2D58uVITEwUHcdj7dy5Ezt27EBWVhZiY2ORnp6O0NBQ0bE8zqRJk3D06FHIsoyqqio0NTVBr9eLjuVxAgMDERAQAAAICgqCzWaD3W4XnMpzjR07Fnl5eQCAI0eOYPLkyYITkVJ4maZVRkYG6urqsHnzZmzevBlAS/MUmyypL3rsscdw8uRJJCYmQpZlpKWlsQ/KBV566SW8//77SElJgdVqxTvvvANfX1/RsTzWihUrsGrVKqxfvx5RUVGYM2eO6EikEK5NQ0RERELxMg0REREJxWKEiIiIhGIxQkREREKxGCEiIiKhWIwQERGRUCxGiKhb8vLynAuXEREpgcUIERERCcVihIh6bPv27UhNTUVTU5PoKETUh3ECKxH1SE5ODnJzc5GZmQkfHx/RcYioD+OZESLqtosXL2LVqlVYsGCBc8VrIqKeYjFCRN3m5+eHTZs24eOPP0ZjY6PoOETUx7EYIaJuCw8Px6xZsxAXF4eNGzeKjkNEfRyLESLqsffeew/79+9HUVGR6ChE1Idx1V4iIiISimdGiIiISCgWI0RERCQUixEiIiISisUIERERCcVihIiIiIRiMUJERERCsRghIiIioViMEBERkVD/D+LOlvl4PX/rAAAAAElFTkSuQmCC
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[7]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for KMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[8]:</div>
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
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAiYAAAFlCAYAAADf6iMZAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAACVuElEQVR4nOzdd3hUVfrA8e+dmt57BVLooYOANGnSBFRYxEXsim3Rnw0LrqCL2FkLorsqixUFEQVUqiginYQeEkghCenJpE6m3N8fIQMxCQlhJjNJzud5fCRz7z33nZvJzDvnnvMeSZZlGUEQBEEQBAegsHcAgiAIgiAINURiIgiCIAiCwxCJiSAIgiAIDkMkJoIgCIIgOAyRmAiCIAiC4DBEYiIIgiAIgsMQiYlgNefOnaNr165MnTqVqVOnMmXKFGbNmsXGjRst+yxbtox169Zdtp13332XLVu2XPH5Lz2uKee5Ejt27OBvf/sbN9xwA5MmTeIf//gH58+ft1r7TbV27Vr69etnucY1/z355JMAPP300/z3v/8FoHPnzhQUFNg0nhMnTjBmzBhuvPFGzp0716w29uzZw+TJk2s99sknnzB8+HBOnjzJnj176Ny5M0899VSdY+fMmUOfPn2adV5r2r59O3PmzGHq1KlMmjSJ+fPnk5WVBVT/zu67775mt93cv4d77rmHpKSkZp9XEOxFZe8AhLbFycmJ77//3vJzRkYGt99+O0qlkvHjx/OPf/yj0Tb27NlDdHT0FZ/70uOacp6mys7O5qmnnmLt2rWEhoYCsHz5cubPn89XX31ltfM0Vf/+/VmxYkWLn7c+W7duZdCgQbz88stWa/Ott97il19+4csvvyQ0NJQ9e/bg7+/P9u3bqaiowNnZGah+bZ09e9Zq522uH374geXLl7N8+XIiIyORZZkPP/yQ2267jQ0bNlx1+839e/joo4+u+tyCYA8iMRFsKjQ0lEceeYT//ve/jB8/nqeffpqYmBjuuusu/v3vf7N582bUajXe3t4sWbKEzZs3c/ToUV599VWUSiXXXHMNL774IidPnkSSJIYNG8Zjjz2GSqWiR48ejB49mpMnTzJlypRax23dutVynv379/Pqq69SUVGBWq1m/vz5DB8+nLVr17J582YUCgWpqak4OTmxdOlSoqKiaj2HwsJCDAYD5eXllsfmzp1Lly5dLD+vWLGC7777DpVKRWRkJK+88gru7u689957bNiwAaVSSceOHXn++efx9/dnzpw5eHp6cubMGW655RamTZvGyy+/TGJiIgaDgcGDB/Pkk0+iUl3dn+jbb7/NkSNHMJvNzJ8/n1GjRgHUG1d8fDwff/wxX3zxBQDjx49n0qRJPPLII5w/f56bb76ZnTt3olBUd7SuX7+eL7/8EpPJRGVlJW+88UaTn++cOXPqxGo2m1m0aBEnT57kiy++wNvb27LNy8uL8PBwtmzZwpQpUwBYt24dU6ZMqZUcfvPNN3z55ZeYzWa8vLx4/vnniYqK4uzZsyxatIiysjJyc3Pp0qULb7/9Nlqtlp49e3Lvvfeya9cucnJyuPvuu5k9eza5ubk89dRTFBYWAjBixAjmz59fJ+633nqLxYsXExkZCYAkSdx7770EBwdTVVVVa985c+Zw6623cv3119f5uSl/DyNGjOD1119n3759mEwmunXrxnPPPYebmxvXXXcdcXFxnDp1iscee4wlS5awbNkyysvLeeuttwgPD+f06dMYjUZefPFF+vXrR0FBAQsWLCAtLQ0vLy/8/f2JiYnh4YcfbtbrTRCsQdzKEWyuS5cuJCYm1nosKyuLlStXsmbNGtauXcvQoUNJSEjg1ltvpUePHjz55JOMHTuWl156CS8vL3744QfWrFnDqVOn+PjjjwEwGAyMGjWKn3/+mYceeqjWcTUKCwt55JFHePbZZ/nhhx9YunQpTzzxBOnp6QDs27eP559/nh9//JFevXrx4Ycf1hv/zJkzmT59OhMnTuS5555j+/btDBs2DKjuNVi7di1ff/01P/74I2FhYXz22WesWbOG3377jW+//ZYffviBmJgYnn76aUu7Hh4ebNy4kTlz5vCvf/2L7t27s3btWtatW0dhYSGffPJJvddz//79dW7lrFmzpt59w8LC+O6773jttdd4+umnKSgoaDCua6+9llOnTqHT6Th37hxlZWX88ccfluc4ZswYS1ICcMMNNzBr1iwmTpzIG2+8cUXP96+MRiNPPPEEX375JfPmzauVlNSYNm1ard64TZs21boFtHfvXtatW8fnn3/OunXruPvuu3nooYcAWL16NdOmTWP16tX88ssvnDt3jh07dgBQVVWFt7c3X331Ff/+979ZsmQJer2e1atXW67f559/TmpqKiUlJbViKiwsJCMjg759+9Z6XJIkbrjhBtzc3Or9vfxVU/8ePvzwQ5RKJWvXrmX9+vUEBATw+uuvW9qJiYlh06ZNtf4GABISErjzzjtZt24dN954I2+99RYAL730EtHR0WzatIlly5Zx8ODBJsUrCLYkekwEm5MkCScnp1qPBQYG0qVLF6ZPn87w4cMZPnw4gwcPrnPszp07+fLLL5EkCY1Gw6xZs1i5ciX33nsvUH1b43ISEhKIiIigV69eQPUbd9++fdm7dy+SJNG9e3eCgoIA6NatG5s3b663naeffpr77ruPvXv3sm/fPl599VVWrVrF559/zu7du7n++uvx9PQEYMGCBUD17aQbb7wRFxcXAG677TY++OADy7foS2PfsWMHR44c4dtvvwWgsrKywed0JbdybrnlFgBiY2OJiori0KFD7Ny5s964FAoFQ4YMYdeuXRQWFvK3v/2Nr7/+mpKSErZt28bdd9992XM11G59z/evzp49S58+fVi6dClPP/00a9euJTg4uNY+o0aN4p///Cd5eXmkpqbSqVMnyzWH6muYmprKrFmzLI/pdDqKiop44okn2LVrFx999BEpKSnk5OTU6gEbPXo0AN27d6eqqory8nKGDRvGvffeS1ZWFkOGDOH//u//cHd3rxVTTaJmNpsve20a09S/hx07dlBSUmJJGA0GA76+vpbtDV3jkJAQunbtClS/zr/77jsAfv31V8u/AwICLD05gmBPIjERbO7IkSPExsbWekyhUPDZZ59x5MgRdu/ezb/+9S+GDRtmGcRZw2w2I0lSrZ+NRqPl55oPwYaYTKZaxwPIsozRaEStVtdKmCRJor6lo7Zu3UpRURE33XQT48ePZ/z48Tz66KOMGDGC48ePo1Qqa51Dp9Oh0+muKHaz2cyyZcsst5F0Ol2duJvj0h4Os9mMSqW6bFxjxoxh586d6HQ67r77bs6cOcOWLVtITExk4MCBlz3X1fyuOnTowJIlSwA4ePAgDz/8MF988QUajcayj0ajYdy4cWzYsIGkpCSmT59e5/xTp07liSeesPyck5ODp6cnjz76KCaTiQkTJjBy5EiysrJq/a61Wi2AJX5ZlomLi2Pr1q3s3r2bP//8kxkzZvDRRx/Ro0cPy3Genp506NCB+Ph4hgwZUiuef/zjH8ybN6/Oc730vAaDAbiyv4dnnnmGESNGAFBWVoZer2/0Gjf0OlepVLXiufT1Igj2Il6Fgk2dPXuW999/nzvvvLPW4ydPnmTy5MlERUVx3333cfvtt3PkyBEAlEql5QPt2muv5bPPPkOWZaqqqli9enWdD4Aalx5Xo3fv3pw5c4aEhAQATp8+zb59+xr9kL2Uq6srb775Zq0ZDunp6SiVSiIiIhgyZAibN2+mtLQUgHfeeYdPP/2UYcOGsWbNGss381WrVjFgwIBaH7Y1rr32Wj799FPL85w3bx6fffZZk2NsSM234WPHjpGWlkavXr0uG9d1113H7t27OXHiBHFxcQwdOpRly5YxfPhwlErlZc91Jc/3r9RqteXfzz77LCaTiRdffLHOftOmTeO7775j3759lltpNa699lo2bNhATk4OAF9++SVz584F4Pfff+fBBx9k4sSJAMTHx2MymS4b0+uvv87777/PmDFjePbZZ4mOjub06dN19nvooYd4+eWXSU1NBaqT4ffff5+TJ0/SqVOnWvv6+Phw9OhRAJKSkjh16hRwZX8Pn3/+OVVVVZjNZp5//nnefPPNyz6PyxkxYoSll66wsJAtW7ZYJSEWhKshekwEq6qsrGTq1KlA9bcvrVbLY489xsiRI2vt16VLFyZMmMBNN92Ei4sLTk5OPPfccwBcd911vPnmmxgMBp577jleeuklpkyZgsFgYNiwYdx///31nvvS42r4+PiwbNkyFi9eTGVlJZIksWTJEjp27MihQ4ea9JyuueYann/+eZ566ilKSkpQKpX4+/vz0Ucf4enpyYgRI0hKSrLcNomOjmbx4sW4uLiQlZXFjBkzMJvNREZG1hoPcKlnn32Wl19+2fI8hwwZ0uCtk5oxJpeqGXfwV+np6UybNg1JknjzzTfx8vLi5ptvbjAud3d3oqKicHZ2RqlUMmzYMJ599lnGjRvX6HW6XLtXQqvVsmzZMqZPn05cXBwdOnSwbOvTpw8VFRVcd911dQYGX3vttdxzzz3ceeedSJKEm5sb7777LpIk8eijj/Lggw/i4uKCm5sbAwYMIC0t7bJxzJ07l6effprJkyej0Wjo3LkzkyZNqrPflClTkGWZxx57DKPRiF6vp3v37qxcubJOUjZv3jyefvppfv31Vzp16mS59dLUv4cHHniApUuXMn36dEwmE127dq01judKLViwgOeee44pU6bg5eVFSEhInduugtDSJLm+vmtBEASh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d3L27FmmTp1qSUJ//PFHevbsSWVl9Togzz77LF98Ufv2ptls5qWXXuK2225j4sSJTJgwwbKWy4IFCwCYO3cuWVl1FzmrSUzS09OZPXs2HTt25J133qmVlNx3333079+/3v/uu+++Om0CvPHGGwwaNIhZs2ZZqmw3xZNPPmlZWPWPP/7goYceAuDjjz9m+fLlLF68mH379vHee+8RGhrK22+/zW+//cbXX3/Nrl27qKqq4r333qv1/A4dOsTo0aPZs2cPt912Gx988AFfffUVy5cvZ/fu3QQGBvL222/XiuNyz/mRRx5p8vOB6l6ao0ePUlhYyNixYxk+fDiLFi2y/E4BbrvtNjZs2EBFRQXZ2dn89ttvDBs2rNG28/LySElJITq6+n23tLSUf//73zz99NP17t/c87Rn7bLHpEZN70hmZiYjenVhzue/88yGQ3wxx3FfNEaTAU8Xf0Z0vgVnTesotFOTONXMynF38mk1s3KEajWF5v7q4YcftgwQvv/+++vtYerfvz///e9/AVi5ciVvvvlmnX2aWsAuJSWFt956i//97394e3tz+vRp7rjjDl566aVa+2VlZfH666/Tt29fvv76a5588km++eYbdu/ezX/+8x++/vprfHx8WLt2LQ8++CATJ05k586dDB48mN9++w1PT0/279/P0KFDLV33f403JyeHTz/9FHd3dz788EM++ugj+vXrx5IlS1i7di0rV65s8FaOJEnMnTuXZ555hjFjxtTZZ8WKFU26HjUef/xxoqKi0Gg0bNiwgfvvv5/vv/+eiIiIRo9NT0/HZDJhMpnQarX069ePgoIC3n33Xb744gu6dKkeV9a5c2fy8vL47LPP2Lhxo2Xl+PHjx/Ptt99a2jt58iR33XUXo0ePBqqLgy1fvpx169YRGRkJwM0338yLL77Y5Od86ZpqTZGXl4fBYOCnn37i888/R6VS8cADD7B8+XIeffRRAAYOHMg333xDv379MJlMTJ8+vd7fxaUMBgOPP/4406dPt4wRevvtt7npppsIDg6u95jmnKe9a7c9JjVeGN+Le+MCmNW7AwPCffn6cAp/puY2fqCdBHp2INyna6tJSmoEe0UzNOZmOmlHMDTmZpGUCM2ya9cucnJyuP3225k6dSqPP/44kiTV6T7v3Lkzffv2BWD69OkcPXqUkpISfvvtNyZOnGhJGG68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NRQVFVFVVcXjjz/ORx99hGEYVpcWVuLj46murubOO++kpaWFoqIiq0sKO8uWLRvW4ds0zeDPsdPpjOj29JEgokdMAGpra1m5ciX33nsv99xzj9XlhKX33nuPAwcOsGLFCr777jvWrl1LQ0OD1WWFHZfLxaJFi3A4HOTk5BATE0Nzc7PVZYWd119/nUWLFrF37152797Ns88+G5xykPExtMt3Z2cnSUlJFlYj4y2ig0ljYyOPPPIIa9asoaCgwOpywtZbb73Fm2++yfbt25k1axYbN25k8uTJVpcVdubNm8fnn3+OaZrU1dXR3d2Ny+Wyuqywk5SURGJiIgDJycn09fXR399vcVXhLTc3l+LiYgA+++wz5s+fb3FFMp4ieiqnqKiItrY2Nm/ezObNm4GBRVdaoCkT0dKlSzl48CAFBQWYpsn69eu1bmocPPzwwzz33HMUFhbi9/t56qmniI+Pt7qssLZ27VrWrVvHyy+/TE5ODsuWLbO6JBlHuleOiIiIhIyInsoRERGR0KJgIiIiIiFDwURERERChoKJiIiIhAwFExEREQkZCiYi8pOKi4uDN1QTERlPCiYiIiISMhRMRGRM3njjDVasWEF3d7fVpYhIGIrozq8iMja7du3i448/ZsuWLcTFxVldjoiEIY2YiMgl+eGHH1i3bh0rV64M3plbRORKUzARkUvidDrZtGkTL730El1dXVaXIyJhSsFERC5JZmYmt956KwsWLODVV1+1uhwRCVMKJiIyJs888wwffPABR48etboUEQlDuruwiIiIhAyNmIiIiEjIUDARERGRkKFgIiIiIiFDwURERERChoKJiIiIhAwFExEREQkZCiYiIiISMhRMREREJGT8P1OdeTDpZypRAAAAAElFTkSuQmCC
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[8]:</div>




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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[9]:</div>
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
<img src="data:image/png;base64,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Y+Xm5l4Sw48//ijNmTNHMhqNkiRJ0rfffivdeeedlz3HpUuXSt26dZPGjx8vPffcc9Ivv/xi3W7z5s3S2LFjpYKCAkmSJGnJkiXSihUraj2XZ555xrr/uXPnSp9//rkkSZJkMpmkJ554Qvrggw8uieOHH36Q+vTpI02ZMqXav++///6y1/j999+XJEmS4uPjpQEDBki5ubk1xlVeXi716dNHKiwslFJSUqQhQ4ZIM2bMkCRJkr788kvphRdeuCSeZcuWSS+99JIkSVK9zvdiRqNRGjp0qLR161ZJr9dL/fv3l/766y9JkiQpLy9PGjBggHT8+HFJkiRp7dq1UlRUlJSSkiJ988030s033yxVVFRIer1euuOOO6RbbrnFerzffvtNSkhIkAYPHiwlJydLkiRJu3btkoYMGSIVFxdLy5Ytk0aOHCkVFRVJ5eXlUv/+/aWlS5dKkiRJf/zxhzR27FhJkq78Ovn3eT366KPSnj17JEmSpJKSEmngwIHS4cOHJUmSpJEjR0qHDh2qFl9ycrI0cOBASa/XS5IkSY888oj03XffSQUFBdLYsWOllJQUSZIk6dy5c9Lw4cOltLQ06eOPP5Yefvjhy17LKlX7T0lJkXr16mV9/uLHy5cvl55//nlJkiSptLRUmjNnjlRUVFRtnSu9t/bs2SN17txZSk1NlSTp0vf6jBkzJL1eLxkMBmnq1KnS999/f8W/58Xy8vKkqKgo6+fI5fzwww/S3XffXe18/33+6enpUp8+fazX9+OPP5b++OOPS7Z59913pZdfflmyWCySJEnSG2+8YX29jxw5Ulq+fLl131V/xz179khdunSRjh07Zt33zTffLElS5evg1VdflSRJkjIzM6UhQ4ZIy5Ytq/kPJrRoomXETtx+++3ceOON7Nu3j3379vHhhx/y4Ycf8v33319xu6pfnV26dMFgMFBSUsL27duZNm0arq6uANx6662sWrXqkl9CF0tMTCQ5OZlnn33W+lxFRQXHjh2jV69eNW73559/cvjwYW644QYALBZLjf0V5s6dyz333MM///zDvn37ePXVV/niiy/46quv2L17N9deey2enp4A1taYRx555Irn0q9fP+v+//rrLw4fPmy9ZhUVFTXGXZ/bNFW3O6KiooiIiODgwYM1XmOlUsngwYPZuXMn+fn5zJgxg9WrV1NcXMzWrVu5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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[9]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for AgglomerativeClustering Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[10]:</div>
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
<img src="data:image/png;base64,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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[10]:</div>




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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[11]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[11]:</div>




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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[12]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[12]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>AgglomerativeClustering(n_clusters=6)</pre>
</div>

</div>

</div>

</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[13]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[13]:</div>



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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[14]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[14]:</div>



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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Selanjutkan kita ubah nilai yang masih dalam bentuk standarisasi ke bentuk awalnyanya dengan method <code>inverse_transform</code></p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[15]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[15]:</div>



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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[16]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[16]:</div>



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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[17]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[17]:</div>



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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[18]:</div>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[19]:</div>
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
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[&nbsp;]:</div>
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

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[21]:</div>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[22]:</div>
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

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[22]:</div>



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
</body>







</html>
