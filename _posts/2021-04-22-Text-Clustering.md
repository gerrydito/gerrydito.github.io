---
layout: post
title: Text Clustering
categories: [Machine Learning,Natural Language Processing,python]
excerpt: 
---


<html>
<head><meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Text Clustering</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>




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
<h2 id="Import-Data">Import Data<a class="anchor-link" href="#Import-Data">&#182;</a></h2>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[1]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="n">hotel</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_excel</span><span class="p">(</span><span class="s2">&quot;Raw Data - Combined - Cust Review.xlsx&quot;</span><span class="p">,</span><span class="n">sheet_name</span><span class="o">=</span><span class="s2">&quot;Raw Data&quot;</span><span class="p">)</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[1]:</div>



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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Melihat banyaknya baris dan kolom di data</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[2]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[2]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>(51305, 8)</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Menghitung 10 Besar hotel yang memiliki jumlah review dan rating terbanyak</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[3]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span><span class="o">.</span><span class="n">hotel_id</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">10</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[3]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Pada tutorial ini kita akan menggunakan data hotel <strong>favehotel Kelapa Gading</strong> saja yang ada sebanyak 487 hotel</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[4]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span> <span class="o">=</span> <span class="n">hotel</span><span class="o">.</span><span class="n">query</span><span class="p">(</span><span class="s2">&quot;hotel_id == &#39;favehotel Kelapa Gading&#39;&quot;</span><span class="p">)</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[4]:</div>



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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Selanjutnya kita akan ambil kolom <strong>review</strong> saja untuk dianalisis</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[5]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span> <span class="o">=</span> <span class="n">hotel</span><span class="p">[</span><span class="s2">&quot;review&quot;</span><span class="p">]</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[5]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Kita pastikan terlebih dahulu apakah text yang kita miliki ada na atau tidak</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Jumlah amatan NaN adalah&quot;</span><span class="p">,</span><span class="n">hotel</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">())</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Contoh amatan yang NAN&quot;</span><span class="p">)</span>
<span class="n">hotel</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">hotel</span><span class="o">.</span><span class="n">isnull</span><span class="p">()]</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
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
<pre>Jumlah amatan NaN adalah 2
Contoh amatan yang NAN
</pre>
</div>
</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[6]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>13712    NaN
13742    NaN
Name: review, dtype: object</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Karena kita memiliki 2 amatan yang berupa <code>NaN</code>. Berikutnya kita akan hapus <code>NaN</code> tersebut</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[7]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel</span> <span class="o">=</span> <span class="n">hotel</span><span class="o">.</span><span class="n">dropna</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Jumlah amatan NaN adalah&quot;</span><span class="p">,</span><span class="n">hotel</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">())</span>
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
<pre>Jumlah amatan NaN adalah 0
</pre>
</div>
</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2 id="Text-Preprocessing">Text Preprocessing<a class="anchor-link" href="#Text-Preprocessing">&#182;</a></h2>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Noise-Removal">Noise Removal<a class="anchor-link" href="#Noise-Removal">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[8]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
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

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[9]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">lower</span><span class="p">()</span>
<span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">noise_removal</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Tokenization">Tokenization<a class="anchor-link" href="#Tokenization">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[10]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">nltk.tokenize</span> <span class="kn">import</span> <span class="n">word_tokenize</span> 
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[11]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">tokenize_fun</span><span class="p">(</span><span class="n">words</span><span class="p">):</span>
    <span class="k">return</span> <span class="n">word_tokenize</span><span class="p">(</span><span class="n">words</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[12]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">tokenize_fun</span><span class="p">)</span>
<span class="n">hotel_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Normalization">Normalization<a class="anchor-link" href="#Normalization">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[13]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">indo_slang_words</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s2">&quot;https://raw.githubusercontent.com/nasalsabila/kamus-alay/master/colloquial-indonesian-lexicon.csv&quot;</span><span class="p">)</span>
<span class="n">indo_slang_words</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
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

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[14]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">new_entry</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">{</span><span class="s2">&quot;slang&quot;</span><span class="p">:[</span><span class="s2">&quot;bokis&quot;</span><span class="p">],</span><span class="s2">&quot;formal&quot;</span><span class="p">:[</span><span class="s2">&quot;bohong&quot;</span><span class="p">],</span><span class="s2">&quot;In-dictionary&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span><span class="s2">&quot;context&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span>
                          <span class="s2">&quot;category1&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span><span class="s2">&quot;category2&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">],</span><span class="s2">&quot;category3&quot;</span><span class="p">:[</span><span class="s2">&quot; &quot;</span><span class="p">]})</span>
<span class="n">new_indo_slang_words</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">indo_slang_words</span><span class="p">,</span><span class="n">new_entry</span><span class="p">])</span>
<span class="n">new_indo_slang_words</span><span class="o">.</span><span class="n">tail</span><span class="p">()</span>
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

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[15]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
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

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[16]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">replace_slang_word</span><span class="p">)</span>
<span class="n">hotel_clean</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[16]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Menghapus-Stopwrods">Menghapus Stopwrods<a class="anchor-link" href="#Menghapus-Stopwrods">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[17]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">nltk.corpus</span> <span class="kn">import</span> <span class="n">stopwords</span>
<span class="n">indo_stopwords</span> <span class="o">=</span> <span class="n">stopwords</span><span class="o">.</span><span class="n">words</span><span class="p">(</span><span class="s1">&#39;indonesian&#39;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[18]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># menambhakan stopwords bahasa indonesia</span>
<span class="n">indo_stopwords</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="s2">&quot;nya&quot;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[19]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#fungsi menghapus stopword</span>
<span class="k">def</span> <span class="nf">stopwords_removal</span><span class="p">(</span><span class="n">words</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">[</span><span class="n">word</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">words</span> <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">indo_stopwords</span><span class="p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[20]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean2</span> <span class="o">=</span> <span class="n">hotel_clean</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">stopwords_removal</span><span class="p">)</span>
<span class="n">hotel_clean2</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[20]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Stemming">Stemming<a class="anchor-link" href="#Stemming">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[21]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">Sastrawi.Stemmer.StemmerFactory</span> <span class="kn">import</span> <span class="n">StemmerFactory</span>
<span class="c1"># create stemmer</span>
<span class="n">factory</span> <span class="o">=</span> <span class="n">StemmerFactory</span><span class="p">()</span>
<span class="n">stemmer</span> <span class="o">=</span> <span class="n">factory</span><span class="o">.</span><span class="n">create_stemmer</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[22]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">stemmer_func</span><span class="p">(</span><span class="n">word</span><span class="p">):</span>
    <span class="k">return</span> <span class="n">stemmer</span><span class="o">.</span><span class="n">stem</span><span class="p">(</span><span class="n">word</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[23]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
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

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[24]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">get_stemmer_word</span><span class="p">(</span><span class="n">document</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">[</span><span class="n">word_dict</span><span class="p">[</span><span class="n">word</span><span class="p">]</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">document</span><span class="p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[25]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean3</span> <span class="o">=</span> <span class="n">hotel_clean2</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">get_stemmer_word</span><span class="p">)</span>
<span class="n">hotel_clean3</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[25]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Convert-to-Text">Convert to Text<a class="anchor-link" href="#Convert-to-Text">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[26]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">list_to_text</span><span class="p">(</span><span class="n">token</span><span class="p">):</span>
    <span class="n">text</span> <span class="o">=</span> <span class="s2">&quot; &quot;</span>
    <span class="k">return</span> <span class="n">text</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">token</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[27]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean_fin</span> <span class="o">=</span> <span class="n">hotel_clean3</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">list_to_text</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[28]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean_fin</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[28]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Menampilkan-WordCloud">Menampilkan WordCloud<a class="anchor-link" href="#Menampilkan-WordCloud">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[29]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">wordcloud</span> <span class="kn">import</span> <span class="n">WordCloud</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>menyatukan setiap baris pada <code>hotel_clean_fin</code> dan mengubahnya menjadi bentuk <code>string</code></p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[30]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_text</span> <span class="o">=</span> <span class="n">hotel_clean_fin</span><span class="o">.</span><span class="n">to_string</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[31]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">wordcloud</span> <span class="o">=</span> <span class="n">WordCloud</span><span class="p">(</span><span class="n">background_color</span><span class="o">=</span><span class="s2">&quot;white&quot;</span><span class="p">)</span>
<span class="n">wordcloud</span><span class="o">.</span><span class="n">generate</span><span class="p">(</span><span class="n">hotel_text</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[31]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;wordcloud.wordcloud.WordCloud at 0x18b03af9df0&gt;</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Menampilkan wordcloud</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[32]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Display the generated image:</span>
<span class="n">plt</span><span class="o">.</span><span class="n">imshow</span><span class="p">(</span><span class="n">wordcloud</span><span class="p">,</span> <span class="n">interpolation</span><span class="o">=</span><span class="s1">&#39;bilinear&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">axis</span><span class="p">(</span><span class="s2">&quot;off&quot;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
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

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Berdasarkan wordcloud diatas <strong>hotel</strong> bisa kita anggap sebagai <strong>stopwords</strong> karena data kita adalah review hotel sehingga kata hotel pastilah ada di dalam review itu, jadi kurang bermakna dalam kasus ini.</p>

</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>menyimpan dalam bentuk png</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[33]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">wordcloud</span><span class="o">.</span><span class="n">to_file</span><span class="p">(</span><span class="s2">&quot;review.png&quot;</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[33]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;wordcloud.wordcloud.WordCloud at 0x18b03af9df0&gt;</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>sebelum lajut kita akan hapus dulu kata hotel dengan menggunakan fungsi berikut</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[34]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">remove_certain_word</span><span class="p">(</span><span class="n">words</span><span class="p">,</span><span class="n">text</span><span class="p">):</span>
    <span class="k">return</span> <span class="p">[</span><span class="n">word</span> <span class="k">for</span> <span class="n">word</span> <span class="ow">in</span> <span class="n">words</span> <span class="k">if</span> <span class="n">word</span> <span class="ow">not</span> <span class="ow">in</span> <span class="n">text</span><span class="p">]</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[35]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean3</span> <span class="o">=</span> <span class="n">hotel_clean3</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">remove_certain_word</span><span class="p">(</span><span class="n">x</span><span class="p">,</span><span class="s2">&quot;hotel&quot;</span><span class="p">))</span>
<span class="n">hotel_clean_fin</span> <span class="o">=</span> <span class="n">hotel_clean3</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="n">list_to_text</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[36]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">hotel_clean_fin</span><span class="p">[</span><span class="n">hotel_clean_fin</span><span class="o">.</span><span class="n">str</span><span class="o">.</span><span class="n">contains</span><span class="p">(</span><span class="s2">&quot;hotel&quot;</span><span class="p">)]</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[36]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2 id="Term-Weighting">Term Weighting<a class="anchor-link" href="#Term-Weighting">&#182;</a></h2>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[37]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.feature_extraction.text</span> <span class="kn">import</span> <span class="n">TfidfVectorizer</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="TF-IDF">TF-IDF<a class="anchor-link" href="#TF-IDF">&#182;</a></h3>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[38]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tf_idf_vectorizer</span> <span class="o">=</span> <span class="n">TfidfVectorizer</span><span class="p">()</span>
<span class="n">tf_idf_result</span> <span class="o">=</span> <span class="n">tf_idf_vectorizer</span><span class="o">.</span><span class="n">fit_transform</span><span class="p">(</span><span class="n">hotel_clean_fin</span><span class="p">)</span>
<span class="n">tf_idf_result_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="o">.</span><span class="n">toarray</span><span class="p">(),</span><span class="n">columns</span><span class="o">=</span><span class="n">tf_idf_vectorizer</span><span class="o">.</span><span class="n">get_feature_names</span><span class="p">())</span>
<span class="n">tf_idf_result_df</span><span class="o">.</span><span class="n">sum</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">)</span><span class="o">.</span><span class="n">T</span><span class="o">.</span><span class="n">sort_values</span><span class="p">(</span><span class="n">ascending</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[38]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
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
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h2 id="Unsupervised-Learning">Unsupervised Learning<a class="anchor-link" href="#Unsupervised-Learning">&#182;</a></h2>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h3 id="K-Means">K-Means<a class="anchor-link" href="#K-Means">&#182;</a></h3>
</div>
</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Untuk menjalankan K-Means kita akan menggunakan <code>MiniBatchKMeans</code> dimana KMeans versi ini lebih <strong>scaleable</strong> dibandingkan dengan KMeans yang biasa</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[39]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.cluster</span> <span class="kn">import</span> <span class="n">MiniBatchKMeans</span>
<span class="n">kmeans</span> <span class="o">=</span> <span class="n">MiniBatchKMeans</span><span class="p">()</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Memilih-Jumlah-Cluster-Optimum">Memilih Jumlah Cluster Optimum<a class="anchor-link" href="#Memilih-Jumlah-Cluster-Optimum">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[40]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">yellowbrick.cluster</span> <span class="kn">import</span> <span class="n">KElbowVisualizer</span>

<span class="c1"># Silhouette</span>
<span class="n">kmeans_vis_sil</span> <span class="o">=</span> <span class="n">KElbowVisualizer</span><span class="p">(</span><span class="n">kmeans</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="p">(</span><span class="mi">2</span><span class="p">,</span><span class="mi">12</span><span class="p">),</span><span class="n">metric</span><span class="o">=</span><span class="s2">&quot;silhouette&quot;</span><span class="p">)</span>

<span class="n">kmeans_vis_sil</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="p">)</span>        <span class="c1"># Fit the data to the visualizer</span>
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
<img src="data:image/png;base64,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b948Xn75Zfr27cuGDRv44YcfKCsr45NPPmn09cbHx1/STfPdd981um9oaCjff/89r776KosXL6a0tLTJuEaPHs3p06eprKwkOzsbjUbDvn37zK/x2muvNSciUPdhOnfuXKZMmcLrr7/eotfbmJkzZ7Jx40bz459//pmpU6c2ui9AZmYma9as4ccff2TPnj0cPHiwyXs1ffp0Ro8ezcGDB5k9ezYAmzdvZtCgQaxdu5YdO3bg5OTExo0bmTRpUoPfk6+++ooTJ06wceNGfvrpJzQaDVu2bAHquhzeeustfvnlFzw8PBp0ZRw+fJh58+bRrVs3pk+ffklsvXv3RqVSkZSUBMC2bduYMGFCgwT03//+N7NmzTJ/MO/bt48tW7aQk5PDvn37WLNmDZs2beKf//xngxbI+Ph4c1zOzs588803GI1GXn75ZT766CO+++47br31VhISEi6J6/jx4wwZMuSS5/v27cugQYOa/Hlc7OOPP2bChAnm5CA+Ph6ZTMZLL71EeHg4H3/8MRUVFTz11FP85z//4fvvv+d///sfL7zwArm5uQCkpqayZs0a1qxZc8n5G/v5p6am8tprr/Hpp5/yww8/mL8UCV2DaBnp4u6++25uueUWDh06xKFDh1i1ahWrVq1i/fr1lz2u/oOmd+/e6HQ61Go1e/bs4eabb8bFxQWAv/3tb7z//vvodLomz5Oenk5mZiZPP/20+bna2lpOnjx52TfP3377jWPHjjFr1iwATCYTNTU1je67ePFi7r33Xg4ePMihQ4f4z3/+w5o1a/jyyy/Zv38/119/PZ6engDm1phHHnnksq9l6NCh5vPv2rWLY8eOme9ZbW1tk3G3pJvmtttuAyA2Npbo6GiOHDnS5D2Wy+VcffXV7N27l7KyMubMmcPatWupqqpi586dLFq06LLXau5nd+Hrbcz48eN54YUXKC4uJiMjg+7du5vvaVP7y+Vy3NzciIiIoKKigtDQ0Ab7XHivTCYTK1euZNGiRWzZsoW77rqL+Ph4PvnkE9LT0zlz5gwDBw685Dr79u1jxowZODk5AXWtTVDXsjdq1Ch8fHyAuqT1wjE6P/74I++99x4vvfQSb775Jo8//vgl554xYwY//vgjAwcO5IcffuCpp55i9erVAFRXV3Po0CEqKip46623zM+dOnWKKVOm8J///IdNmzaRkZFBUlIS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CQDffvstU6ZMIS4ujkWLFlFSUtKq11uvurqabdu2cf/99+Pq6srQoUOZMGECGzdubHLfRx55pMl9r7vuOq699lq8vLwaHHul97ded/9BSJIJSarrn1EqHEGqe15oO00lJF09EQGRjAhCm9q5cye33HILM2fOZO7cuRw5cuSSfaqrq3n44YeZMWMG8+bN49y5c+Zta9euZerUqUyfPp0FCxZw7tw5ZsyYwf79+4G6D+D+/ftTW1v3DXbJkiV89dVXDc5vMpl46aWXuOWWW5gyZQo33HADCQkJADz11FMA3HvvveTl5V0SW30ykpWVxe23305UVBTvvPMOrq6u5n3uvfdehg4d2ui/e++997L3p7i4mPT0dGJiLBsU+cQTTzB27Fj27dvHvn37ePDBBwFYvXo1K1euZNmyZRw6dIj33nuPkJAQ/vvf//L777+zdu1a9u7di06n47333mvw+o4cOcLEiRM5cOAAf/vb33j//ff55ptvWLlyJfv37ycwMJD//ve/DeJo6WtOT09HLpcTERFhfq5Xr16kpqY2uW9UVFSz+zanpfe3XpBXDFF+g1DIHXBWuRPoEcHA8Ali8KoV3DWsYReoSETqiNk0Qoc3cGDjf8gPPfQQixYtAuq62uo/0C80dOhQPv74YwA+++wz3njjjUv2SUqybFBZeno6b775Jp9//jne3t6cOXOGu+++m5deeqnBfnl5ebz22msMGTKEtWvX8sQTT7Bu3Tr279/PRx99xNq1a/Hx8WHDhg088MADTJkyhT179jBy5Eh+//13PD09iY+PZ9SoUezevZtHH330kngLCwtZu3YtcrmcDz/8kFWrVhEXF8crr7zChg0b+OCDDwgKCrrkNaSkpCCTybjrrrt4+umnufbaay/Z54MPPrDoflxMr9fzr3/9i5tuusniMSlZWVkYjUaMRiOOjo7ExcVRWlrKu+++y1dffUWvXr0A6NmzJ8XFxXzxxRds2bKFgIAAACZPnsz69evN5zt16hQLFy5k4sSJQN3yAitXruSHH34wJw6zZ8/mxRdfvKLXXF1dfcmS9u7u7o22MLVk38tpzf29UKR/f1wc3fFyCcTD2Q9JkpAkSdQmaWO70woAmNwziBER/iIROc9qyYjJZOKFF17g9OnTqFQqXnrppQbfEnbu3Ml7772HUqlk1qxZ3Hrrrej1ep5++mlycnLQ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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[40]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>&lt;AxesSubplot:title={&#39;center&#39;:&#39;Silhouette Score Elbow for MiniBatchKMeans Clustering&#39;}, xlabel=&#39;k&#39;, ylabel=&#39;silhouette score&#39;&gt;</pre>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<h4 id="Menerapkan-Metode-Cluster">Menerapkan Metode Cluster<a class="anchor-link" href="#Menerapkan-Metode-Cluster">&#182;</a></h4>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[41]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">kmeans</span> <span class="o">=</span> <span class="n">MiniBatchKMeans</span><span class="p">(</span><span class="n">n_clusters</span><span class="o">=</span><span class="mi">4</span><span class="p">)</span>
<span class="n">kmeans</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt">Out[41]:</div>




<div class="jp-RenderedText jp-OutputArea-output jp-OutputArea-executeResult" data-mime-type="text/plain">
<pre>MiniBatchKMeans(n_clusters=4)</pre>
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
<p>Interpretasi Hasil Cluster menggunakan 10 kata-kata paling penting dari masing-masing kluster. Kata-kata penting ini diukur dengan nilai TF-IDF dimana semakin besar nilainya maka semakin penting kata tersebut</p>

</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[42]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># extract cluster&#39;s label</span>
<span class="n">cluster_label</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">kmeans</span><span class="o">.</span><span class="n">predict</span><span class="p">(</span><span class="n">tf_idf_result</span><span class="p">),</span><span class="n">columns</span><span class="o">=</span><span class="p">[</span><span class="s2">&quot;cluster&quot;</span><span class="p">])</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs  ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[43]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">tf_idf_df_lab</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">concat</span><span class="p">([</span><span class="n">tf_idf_result_df</span><span class="p">,</span><span class="n">cluster_label</span><span class="p">],</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>
</pre></div>

     </div>
</div>
</div>
</div>

</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell   ">
<div class="jp-Cell-inputWrapper">
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In&nbsp;[44]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
     <div class="CodeMirror cm-s-jupyter">
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
</div>

<div class="jp-Cell-outputWrapper">


<div class="jp-OutputArea jp-Cell-outputArea">

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAgUAAAFlCAYAAAB7gJvKAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjMuNCwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8QVMy6AAAACXBIWXMAAAsTAAALEwEAmpwYAAAoA0lEQVR4nO3de5xN9f7H8dfMMMOYQTFJJ/q5pIvJkel20iFyDuXaZCpyKbqofhEldPkZhS6UU0pShvmRbhq/HrqgdFGKn6Z00IV0QbkVYoaZMWb//mibXxOaitl7Lq/nX3uv9V1rf76z9rbfvnut74oIBAIBJElShRcZ7gIkSVLpYCiQJEmAoUCSJAUZCiRJEmAokCRJQYYCSZIEGAok/YZ9+/Yxbdo0kpOT6dq1KxdddBHjxo0jLy8PgOHDhzN16tQ/vf9+/fqxbdu2w6pxz5493HLLLVx44YW0b9+eN95447D2J1VklcJdgKTSKzU1lZ9++on09HTi4+PZvXs3t956K3fccQfjxo077P0vXrz4sPcxceJEYmNjee211/j++++57LLLSExM5Nhjjz3sfUsVjSMFkg5qw4YNzJ07l7FjxxIfHw9AbGwso0aNol27dge0P+mkk4r8r3//8+zsbAYOHEjXrl25+OKLufPOOykoKGDEiBEA9O3bl40bN7J582ZuvPFGkpOT6dy5M5MnTy6so3Xr1vTr14/27duzZcuWIq/7xhtvkJKSAsBxxx1Hy5Ytee2110rkbyKVd4YCSQe1atUqGjduTFxcXJHlCQkJtG/f/nfv5/XXXyc7O5uXXnqJ2bNnA7B+/XruvfdeANLT06lbty5Dhw7lkksuISMjg9mzZ/P+++/z6quvArBp0yZuuOEG5s+fzzHHHFNk/xs3bqRu3bqFz+vUqcOmTZv+VJ+lis6fDyQdVGRkJAUFBYe9n6SkJCZMmEDv3r0599xz6du3LyeccEKRNrt372bZsmX89NNPPPzww4XLPv/8c5o1a0alSpVo3rz5QfcfCASIiIg4oHZJf5yhQNJBNWvWjK+++oqsrKwiowWbN2/mrrvu4pFHHjnktvtPRASoV68er7/+OkuXLmXJkiVcddVV3H333bRt27awTUFBAYFAgGeffZaqVasCsG3bNmJiYti+fTvR0dFUqnTwf67q1q3Lli1bqF27NgBbtmzh5JNPPqy+SxWVcVrSQdWpU4fOnTtz++23k5WVBUBWVhapqanUrFmTKlWqFGl/9NFHs2LFCgBefvnlwuWzZs1ixIgRnHfeeQwdOpTzzjuPTz/9FICoqCjy8/OJi4ujefPmTJs2DYCdO3fSo0cPFi5cWGydF1xwAc899xzw888M7777Lm3atDn8P4BUARkKJB3SyJEjady4MZdffjldu3YlJSWFxo0bM3r06APa3nnnndx9991cfPHFrF27loSEBAC6devGvn37uOiii0hOTmbXrl307t0bgA4dOtC7d29Wr17N+PHj+eSTT+jcuTMpKSl06tSJLl26FFvjTTfdxO7du+nYsSNXXnklQ4cOpX79+kf2DyFVEBHeOlmSJIEjBZIkKchQIEmSAEOBJEkKMhRIkiSggs9TUFBQQHZ2NpUrVz5g8hNJksqbQCDA3r17qVat2kEn+arQoSA7O5vVq1eHuwxJkkKqSZMmhfc0+aUKHQoqV64M/PzHiY6ODnM1JW/lypUkJiaGu4yQsK/lk30tn+xr6OTl5bF69erC779fq9ChYP9PBtHR0cTExIS5mtCoKP0E+1pe2dfyyb6G1qF+Mq/Qkxfl5uaycuVKjlv+JZXy9oa7HEmSiki4vtcR3d/+773ExMSDhhOvPpAkSYChQJIkBRkKJEkSYCiQJElBhgJJkgQYCiRJUpChQJIkAYYCSZIUFLZQkJGRwfjx48P18pIk6VccKZAkSUApuPfBtm3buOGGG7j66quZO3cuu3btYvv27aSkpNCzZ0969+7NSSedxJo1a4iNjeWMM87gvffeY+fOnaSlpREVFcUdd9xx0O2OOuoodu7cydSpU4mKigp3VyVJKtXCOlLw448/cv311zNixAjq1q1Lx44dSUtLY/LkyUyfPr2wXbNmzUhPTycvL48qVaowbdo0GjduzLJly/j2228PuV3nzp2ZPn26gUCSpN8hrCMF7777LgkJCRQUFFC7dm3S09NZsGABcXFx5OfnF7Zr2rQpANWrV6dx48aFj3Nzc39zuwYNGoS2Q5IklWFhDQXdunWjW7duDBo0iJYtW9K8eXN69uzJkiVLeOedd37XPtLS0g653aFuDSlJkg4U9nMKGjduTJcuXXjxxReJjIxk7ty51KxZk6ioKPLy8ordvk2bNqSmpv7h7SRJUlERgUAgEO4iwmX/faWPW/4llfL2hrscSZKKSLi+1xHd3/7vvcTERGJiYg5Y7yWJkiQJMBRIkqQgQ4EkSQIMBZIkKchQIEmSAEOBJEkKMhRIkiSgFExeVBoc3avbQa/XLG8yMzNJSkoKdxkhYV/LJ/taPtnX0sORAkmSBBgKJElSkKFAkiQBhgJJkhRkKJAkSYBXHwCwdsY1ROb+FO4ySlw14PMl4a4iNOzr4Tn5xpeO7A4llQmOFEiSJMBQIEmSggwFkiQJMBRIkqQgQ4EkSQIMBZIkKchQIEmSAEOBJEkKClsoyMjIYPz48UdkX4MHDyYvL4/hw4ezaNGiI7JPSZIqmnIxo+GECRPCXYIkSWVeWEPB8uXL6du3L1lZWdx0003ExsYyYcIEoqKiqFevHnfffTdz587lxRdfpKCggIEDB/LSSy+xbt06cnNz6d+/PxdddBFt27bltddeA+C5557jqaeeIisri9TUVJo1axbOLkqSVGaENRRUrVqVKVOmsG3bNlJSUqhcuTKzZs2iVq1a/Otf/2LOnDlUqlSJ6tWr8/jjj5OVlcXtt9/Oiy++CMDixYsP2GfTpk254YYbyMjIICMjw1AgSdLvFNZQkJSUREREBLVq1aJKlSps2LCBm2++GYCcnBxatmxJ/fr1adCgAQBxcXHcdddd3HXXXWRlZdGlS5cD9tm0aVMAateuTU5OTsj6IklSWRfWULBixQoAtm7dSm5uLn/5y1+YNGkS8fHxLFy4kNjYWDZu3Ehk5M/nQ27ZsoVVq1bx2GOPkZubS+vWrenatWuRfUZERIS8H5IklQdhDQU5OTn06dOH3bt3M3r0aPbt28e1115LIBCgWrVqPPDAA2zcuLGwfUJCAlu3bqVbt27ExsbSr18/KlUqF+dKSpIUdhGBQCAQ7iLCJTc3l5UrV1L144eJzP0p3OVIpcbJN74U7hIOKjMzk6SkpHCXERL2tXwKd1/3f+8lJiYSExNzwHonL5IkSYChQJIkBRkKJEkSYCiQJElBhgJJkgQYCiRJUpChQJIkAeXkLomHq1HvJw96vWZ5E+7rY0PJvkrSH+dIgSRJAgwFkiQpyFAgSZIAQ4EkSQoyFEiSJMCrDwB47YW+5O/dEe4yQuLrf4e7gtApy33tftW8cJcgqQJypECSJAGGAkmSFGQokCRJgKFAkiQFGQokSRJgKJAkSUGGAkmSBJTDUPDMM88wceJEtm7dSmpqarjLkSSpzCh3oWC/hIQEQ4EkSX9A2GY0zMjI4K233iInJ4etW7fSp08fFi5cyJo1a7jtttvYtGkTCxYsID8/n/j4eCZOnMjLL7/MO++8Q05ODuvWreOaa64hOTmZDz/8kLFjx1KjRg0iIyNp3rw5GzZsYMiQITz//PPh6qIkSWVKWKc5zs7OJi0tjVdeeYXp06fz/PPPs3TpUqZPn05iYiLTp08nMjKS/v37s2LFCgCysrKYOnUq33zzDQMGDCA5OZl7772XBx98kAYNGjBy5MhwdkmSpDIrrKHglFNOASA+Pp5GjRoRERFBjRo12Lt3L5UrV2bIkCHExsayadMm8vPzATj55JMBqFu3Lnl5eQBs3ryZBg0aANCiRQvWrVsXht5IklS2hTUUREREHHT53r17eeONN3jhhRfYs2cPycnJBAKBQ26TkJDA2rVradSoEStWrKBGjRolWrckSeVRqbxLYqVKlahatSrJyclER0eTkJDAli1bDtl+3LhxDBs2jGrVqlGtWjVDgSRJf0LYQkFycnLh41atWtGqVSvg558U0tLSit0+JiaGN998E4DGjRsze/bsA9p4kqEkSb9fub0kUZIk/TGGAkmSBBgKJElSkKFAkiQBhgJJkhRkKJAkSYChQJIkBRkKJEkSUEpnNAy1C1PSiYmJCXcZJS4zM5OkpKRwlxESFamvknSkOFIgSZIAQ4EkSQoyFEiSJMBQIEmSggwFkiQJ8OoDAP71Sh/25O8IdxkhMXdtuCsInUP1NfXS+aEtRJLKCEcKJEkSYCiQJElBhgJJkgQYCiRJUpChQJIkAYYCSZIUZCiQJElAGQkFGRkZjB8//g9tk5ubS9u2bUuoIkmSyp8yEQokSVLJKzMzGi5fvpy+ffuSlZXFTTfdRGxsLBMmTCAqKop69epx9913k5eXx6233srOnTupX79+uEuWJKlMKTOhoGrVqkyZMoVt27aRkpJC5cqVmTVrFrVq1eJf//oXc+bMIS8vjyZNmjB48GA++eQTli5dGu6yJUkqM8pMKEhKSiIiIoJatWpRpUoVNmzYwM033wxATk4OLVu2ZPv27fz9738H4K9//SuVKpWZ7kmSFHZl5ltzxYoVAGzdupXc3Fz+8pe/MGnSJOLj41m4cCGxsbGsXr2a5cuX065dOz799FPy8/PDXLUkSWVHmQkFOTk59OnTh927dzN69Gj27dvHtddeSyAQoFq1ajzwwAOceeaZjBgxgh49etCwYUMqV64c7rIlSSozykQoSE5OJjk5+YDl55133gHLxo0bF4qSJEkqd7wkUZIkAYYCSZIUZCiQJEmAoUCSJAUZCiRJEmAokCRJQYYCSZIElJF5CkrazR3/m5iYmHCXUeIyMzNJSkoKdxkhUZH6KklHiiMFkiQJMBRIkqQgQ4EkSQIMBZIkKchQIEmSAK8+AOCq+Y+yY9+ecJcRGuteC3cFofOrvr568Z1hKkSSygZHCiRJEmAokCRJQYYCSZIEGAokSVKQoUCSJAGGAkmSFGQokCRJgKFAkiQFGQokSRJgKJAkSUFleprjrKws7rjjDnbt2sX27dtJSUmhadOmjBkzhkAgQJ06dRg/fjxVqlQJd6mSJJV6ZToUfPvtt3Ts2JF//vOfbN68md69e1OlShUmTJhAo0aNePrpp1m7di1NmzYNd6mSJJV6ZToU1K5dm/T0dBYsWEBcXBz5+fn8+OOPNGrUCIArrrgizBVKklR2lOlzCtLS0mjevDnjx4+nQ4cOBAIBjjnmGL755hsApkyZwuuvvx7eIiVJKiOKDQX//ve/mTZtGnl5efTr149zzjmHRYsWhaK2YrVp04b//u//pkePHqSnpxMVFUVqaiq33347vXr14rPPPqN169bhLlOSpDKh2J8PRo8ezcCBA5k/fz5VqlRhzpw5/Od//ietWrUKRX2/6ZxzzmHevHkHLJ81a1YYqpEkqWwrdqSgoKCA8847j7fffpt//vOf1K1bl3379oWiNkmSFELFhoKqVauSlpbGkiVLCofrq1WrForaJElSCBUbCsaPH8/u3buZOHEiNWrUYPPmzTz00EOhqE2SJIXQIc8pWLZsWeHjs88+m3379rFs2TLOP/981q1bR506dUJSoCRJCo1DhoJHHnkEgB07drB+/XpOP/10IiMj+fjjj2nSpAnPPvtsyIqUJEkl75ChYMaMGQBcc801PProo5xwwgkAfPfdd/zXf/1XaKqTJEkhU+w5Bd9//31hIAA47rjj+P7770u0KEmSFHrFzlNw6qmnMmzYMC688EICgQBz587ljDPOCEVtITOt/X8SExMT7jJKXGZmJklJSeEuIyQqUl8l6UgpNhSMGTOGmTNnFp5DcO6559KzZ88SL0ySJIVWsaHg+uuvZ+rUqfTr1y8U9UiSpDAp9pyCPXv2sHHjxlDUIkmSwqjYkYLt27fTtm1batWqRUxMDIFAgIiICBYuXBiK+iRJUogUGwqeeuqpUNQhSZLCrNhQcNxxx/HMM8+wZMkS8vPzOeecc+jVq1coaguZ/q+9xI78veEuIzS+/jzcFRyWl7tfEe4SJKncKjYUPPDAA3z77bdccsklBAIBMjIyWL9+PXfccUco6pMkSSFSbChYvHgx//M//0Nk5M/nJJ5//vl07ty5xAuTJEmhVezVB/v27SM/P7/I86ioqBItSpIkhV6xIwVdunShT58+dOzYEYBXXnmFTp06lXhhkiQptIoNBR999BFdu3Zl5cqVVK9enQEDBnD++eeHoDRJkhRKv2tGw3fffZfVq1ezb98+YmJiOProo2nWrFko6pMkSSFSbCho3rw5zZs354orrmDevHlMnjyZp556ipUrV4aiPkmSFCLFhoJRo0aRmZlJVFQUZ555JiNHjuSss84KRW2SJCmEir36YOfOnQQCARo0aECjRo1o2LAh8fHxoajtTxk8eDB5eXl8//33vPnmm+EuR5KkMqPYkYIHH3wQgLVr1/LBBx8wYMAAdu/ezbvvvlvixf0ZEyZMAGDJkiV89dVXtG3bNswVSZJUNhQbCr766is++OADPvjgAz7//HOaNWtG69at//QLfv3114wYMYJKlSoRFRXFAw88wMyZM1m2bBmBQIArr7ySCy+8kN69e3PSSSexZs0aYmNjOeOMM3jvvffYuXMnaWlpLFy4kIULF5KVlcX27du58cYbad++PW3btuXll19mypQp5OTkcPrpp3PBBRf86XolSaooig0FgwYNok2bNlx55ZWcfvrphz1x0fvvv0/Tpk0ZPnw4H374IQsWLGDDhg08++yz5Obmcumll9KyZUsAmjVrxp133kn//v2pUqUK06ZNY9iwYSxbtgyA3bt3M23aNLZt20ZKSkrhl39UVBTXXnstX331lYFAkqTfqdhQMHfu3CP6gt27d+fJJ5/k6quvJj4+npNPPplVq1bRu3dvAPLz8/n+++8BaNq0KQDVq1encePGhY9zc3MBOPPMM4mMjKR27dpUr16dbdu2HdFaJUmqSIo90fBIW7hwIUlJSaSnp9OhQwcyMjI4++yzmTFjBunp6Vx44YUcf/zxv2tfq1atAuCHH34gKyuLWrVqFa6LjIykoKCg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8ssvueyyy4osLw/Htn79+kycOLHw+apVqzjrrLMAaNWqFe+//36R9r/12S7tft3Xhx56iFNOOQWAffv2HXA/lt96r5d2v+7rypUrefvtt7niiiu4/fbbycrKKtK+PB3X/SZOnEivXr045phjiiwvbce1QoSCrKws4uLiCp9HRUWRn59fuO6XszpVq1btgDdoWVKtWjXi4uLIyspi4MCB3HzzzUXWd+zYkdTUVNLT08nMzOStt94KT6FHSJUqVejfvz9Tp05l1KhR3HrrreX22O73xBNPcOONNx6wvDwc2/bt21Op0v//qhkIBAonFqtWrRq7du0q0v63Ptul3a/7uv/L4qOPPmLmzJlceeWVRdr/1nu9tPt1X5s1a8Ztt93G008/Tb169XjssceKtC9PxxXgxx9/5IMPPiA5OfmA9qXtuFaIUBAXF0d2dnbh84KCgsKD9ut12dnZB536sSzZuHEjffr0oWvXrnTu3LlweSAQoG/fvhx99NFER0fTunVrPv300zBWevgaNGhAly5diIiIoEGDBtSsWZOtW7cC5fPY7ty5k6+++opzzjmnyPLyeGyBIucPZGdnF54/sd9vfbbLoldffZWRI0cyZcqUwnND9vut93pZ849//IPExMTCx79+r5a34zpv3jw6dep0wMgtlL7jWiFCQYsWLVi0aBEAy5cvp0mTJoXrGjVqxLfffsuOHTvIy8vjww8/5PTTTw9XqYfthx9+oF+/fgwdOpTu3bsXWZeVlUWnTp3Izs4mEAiwdOnSwg9mWTV79mzuu+8+ADZv3kxWVhYJCQlA+Tu2AMuWLePcc889YHl5PLYAp556KkuXLgVg0aJFnHHGGUXW/9Znu6x56aWXmDlzJjNmzKBevXoHrP+t93pZ079/f/79738D8MEHH9C0adMi68vTcYWf+9iqVauDrittx7XsRq8/4B//+AeLFy/m8ssvJxAIMHbsWObOncvu3bu57LLLGD58OP379ycQCHDJJZdQp06dcJf8p02ePJmdO3cyadIkJk2aBEBKSgp79uzhsssuY/DgwfTp04fo6Gj+9re/0bp16zBXfHi6d+/OiBEj6NGjBxEREYwdO5bXXnutXB5bgK+//prjjz++8Pkv38fl7dgCDBs2jLvuuouHHnqIhg0b0r59ewBuu+02br755oN+tsuiffv2MWbMGOrWrctNN90EwJlnnsnAgQML+3qw93pZ/d9zamoq99xzD5UrV6Z27drcc889QPk7rvt9/fXXBwS90npcvfeBJEkCKsjPB5IkqXiGAkmSBBgKJElSkKFAkiQBhgJJkhRkKJAkSUAFmadA0pEzatQoPvroI/bu3cu6deto1KgRAH369OH++++nbt26hW1r167N1KlTD7mv/XPE33TTTQwfPpwlS5ZQo0aNwhnsrrnmmsK75/1y/X7nn38+gwcPLoluShWSoUDSHzJy5EgANmzYQJ8+fXjppZeAn2/t3LZt28LZ2f6MgQMHFs4Pv379enr27EnNmjULZ3H85XpJR54/H0gqlerVq0efPn2YNWtWuEuRKgxHCiQdMW+++SZdu3YtfD5ixIgDbt70RzRp0oQ5c+YUPn/kkUdIT08vfP70008XuZuepMNjKJB0xBzuzwcHU6VKlcLH/nwglSx/PpBUan3xxReFJzJKKnmGAkml0jfffMOsWbPo0aNHuEuRKgx/PpBUauw/ZyAiIoKoqCiGDRtGixYtwl2WVGF462RJkgQ4UiCphN1yyy18+eWXByxv27YtgwYNCkNFkg7FkQJJkgR4oqEkSQoyFEiSJMBQIEmSggwFkiQJMBRIkqSg/wPkmGe7POtgTwAAAABJRU5ErkJggg==
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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AADAjfGYUy3b7XZ99tlnysvL0+nTp5WYmKj169dr3759Gjp0qE6ePKmPP/5YTqdTwcHBSktLs7pkAAA8lscEBEnKzc3V/Pnz9cEHH2jhwoVavny5Nm/erIULF6pu3bpauHChvLy81LNnT+3cudPqcgEA8FgeFRBq164tSQoODlaNGjVks9kUGhqqixcvytfXV4MHD1ZgYKBOnjwpp9NpcbUAAHgujwoINpvtio9fvHhRn3zyiVasWKELFy4oISFBhmGUcXUAAJQfxe6kuGPHDi1YsED5+fnq0aOHHnzwQW3YsKEsartuPj4+CggIUEJCgpKSkhQeHq7MzEyrywIAwGMVO4Pw8ssvq3///vroo49UoUIFrV69Ws8//7yaNGlSFvW5JCQkuG43adLE9fdr166t+fPnF/v85cuXl1ptAACUN8XOIBQWFqpx48b6/PPP9fjjjysiIkIFBQVlURsAALBIsQEhICBA8+fP16ZNm/Too4/qH//4hypWrFgWtQEAAIsUGxBSU1N1/vx5paWlKTQ0VKdOndLkyZPLojYAAGCRq+6DsGXLFtft2NhYFRQUaMuWLXrkkUd09OhRValSpUwKBAAAZe+qAWHatGmSpLNnz+r7779X/fr15eXlpW3btqlWrVpatmxZmRUJAADK1lUDwuLFiyVJvXr10vTp0xUZGSlJOn78uF566aWyqQ4AAFii2H0QfvjhB1c4kKTbb79dP/zwQ6kWBQAArFXseRDuvfdeDRs2TH/9619lGIbWrl2rhg0blkVtlljwxPPy9/e3uowSk56erpiYGKvLKHH05VnoC/A8xQaElJQULVmyxLXPQaNGjfT000+XemEAAMA6xQaEPn36aN68eerRo0dZ1AMAANxAsfsgXLhwQSdOnCiLWgAAgJsodgYhOztbzZo1U+XKleXv7y/DMGSz2bR+/fqyqA8AAFig2IDw1ltvlUUdAADAjRQbEG6//Xa988472rRpk5xOpx588EF17dq1LGqzRM8P1+is86LVZZSsQxlWV1A66Muz0Ncf8n77LmXyd4BLig0Ir7/+uo4cOaJ27drJMAzZ7XZ9//33GjVqVFnUBwAALFBsQNi4caPee+89eXn9sj/jI488olatWpV6YQAAwDrFHsVQUFAgp9NZ5L63t3epFgUAAKxV7AxC69atlZiYqCeffFKS9MEHHyguLq7UCwMAANYpNiBs3bpV8fHx2rVrl0JCQtS7d2898sgjZVAaAACwynWdSfGLL77Q3r17VVBQIH9/f1WqVEnR0dFlUR8AALBAsQGhXr16qlevnrp06aJ169bpzTff1FtvvaVdu3aVRX0AAMACxQaEcePGKT09Xd7e3rr//vs1duxYPfDAA2VRGwAAsEixRzGcO3dOhmEoKipKNWrUUPXq1RUcHFzihdjtdqWmppb4egEAwO9X7AzCG2+8IUk6cOCAvvrqK/Xu3Vvnz5/XF198UerFAQAAaxQbEA4ePKivvvpKX331lTIyMhQdHa2mTZuWSjHffPONevTooaysLHXu3FmhoaFaunSpa/nUqVO1b98+paamytfXVx07dlRoaKimTZumoKAghYaG6p577tFzzz2nl156SSdPnlR2draaNGmigQMHlkrNAACUR8UGhAEDBujRRx/VM888o/r165fqSZJ8fHw0b948HT9+XH/729/UunVrzZkzRwEBAXrppZf073//W1WqVJHD4dCKFStUUFCgxx9/XO+++67CwsL0wgsvSJJOnDihevXqqUOHDnI4HAQEAAB+p2IDwtq1a8uiDknSvffeK5vNpvDwcOXl5aly5coaNmyYKlasqIMHD6pevXqSpKioKElSVlaWgoKCFBYWJklq2LChzpw5o1tuuUU7d+7Upk2bFBQUpPz8/DLrAQCA8qDYgFCWbDab6/bPP/+sadOm6fPPP5ckJSUlyTAMSXJdF6Jy5crKzc1VVlaWKlWqpG+++UZ33HGH7Ha7goODNX78eB05ckTLly+XYRhF1g8AAK7OrQLCbwUFBSk6Olpt27ZVYGCgQkJClJmZqTvvvNM1xsvLS2PGjFGvXr0UHByswsJCRUZG6qGHHtLgwYOVnp6ugIAARUZGKjMzU1WqVLGwIwAAPIfbBISEhATXbX9/f3322WdXHRsbG+u6nZGRoXfeeUd+fn4aMmSIIiIiVLNmzTL9aQQAgPLGbQLCjapYsaI6duyoChUq6I477lDLli2tLgkAAI/n8QGha9eu6tq1q9VlAABQrhR7JkUAAHDzISAAAAATAgIAADAhIAAAABMCAgAAMPH4oxhK2ry/xsvf39/qMkpMenq6YmJirC6jxNGXZ6EvwPMwgwAAAEwICAAAwISAAAAATAgIAADAhIAAAABMOIrhMs+u+1o/OQ2ryyhZh/9tdQWlg748y03Q1+p2jS0sBChZzCAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwISAAAAATAgIAADDxuIDQsWNHHTt2THa7XevXr7e6HAAAyiWPPZNiQkKC1SUAAFBuWRYQ8vLyNHToUGVmZioiIkJbtmzR5MmTNX36dNfy1157TVFRUZoyZYq++OIL/elPf1J2drYkKS0tTWFhYapevbrmzp0rX19fHTt2TC1btlSfPn105MgRDR8+XD4+Prrjjjt0/PhxLV682Kp2AQDwKJYFhHfffVd33nmnpk2bpgMHDiguLk779u3TpEmTVKVKFb355ptat26dHnvsMW3ZskUrV67U+fPn9fjjj5vW9cMPP+h//ud/lJ+fr4cfflh9+vTR66+/rt69e6tp06Zavny5jh8/bkGXAAB4JssCwoEDB9SkSRNJUo0aNVSpUiVVqVJFKSkpCgwM1KlTp9SgQQPt379fdevWlZeXl4KCglSrVi3TumrVqiUfHx/5+PioQoUKrvXXr19fkhQTE6O1a9eWXXMAAHg4y3ZSrFWrlrZt2yZJOnr0qLKzszV69GhNnDhRr776qm677TYZhqGoqCjt2LFDhYWFOn/+vPbv329al81mu+b6v/nmm9JtBgCAcsayGYT27dtr+PDh6tKli26//Xb5+/srPj5eHTt2VEhIiMLCwpSZmanatWurRYsWat++vW677TZVrlz5utY/ZMgQjRw5UvPnz1dwcLB8fDx2f0wAAMqcZd+ae/bsUfv27dW4cWMdPnxY27Zt04gRIzRixAjT2GeeeUbPPPNMkcf69evnuh0bG+u6vXHjRknS9u3blZKSosjISK1YsUJbt24tnUYAACiHLAsIVatW1eDBgzV9+nQ5nU699NJLJbr+iIgIDRo0SAEBAfLy8tLEiRNLdP0AAJRnlgWE8PDwUj3s8P7775fdbi+19QMAUJ553JkUAQBA6SMgAAAAEwICAAAwISAAAAATAgIAADDh7EGXmd2iofz9/a0uo8Skp6crJibG6jJKHH15FvoCPA8zCAAAwISAAAAATAgIAADAhIAAAABMCAgAAMCEoxgus/ijM3IUlKd/lju16egpq4soBfTlWcp3X33bVrG6EKDEMYMAAABMCAgAAMCEgAAAAEwICAAAwISAAAAATAgIAADAhIAAAABMCAgAAMDELQKC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ERER6tevnyTp/vvvV//+/V19Xem16gn/p52cnKwJEybI19dXYWFhmjBhgiTP3l6XHDp0yBTmPGV7XekzfdSoUXr55ZfL7L3FtRgAAIDJTfcTAwAAKB4BAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJi4z0GfADzKuHHjtHXrVl28eFFHjx5VjRo1JEmJiYl67bXXFBER4RobFhamefPmXXVdl86h369fPw0fPlybNm1SaGio60xwvXr1cl1h8LfLL3nkkUc0aNCg0mgTuGkREADckLFjx0qSjh07psTERK1Zs0bSL5ezbtasmessdTeif//+rvPnf//993r66ad1yy23uM4++dvlAEoHPzEAcGtVq1ZVYmKi3n77batLAW4qzCAAKHGffvqp4uPjXfdHjBhhujDV71GrVi2tXr3adX/atGlatGiR6/7SpUuLXMUOwB9HQABQ4v7oTwxXUqFCBddtfmIASh8/MQBwe999951rJ0gAZYOAAMCtHT58WG+//bY6d+5sdSnATYWfGAC4nUv7GNhsNnl7e2vYsGFq0KCB1WUBNxUu9wwAAEyYQQBQJl544QXt37/f9HizZs00YMAACyoCcC3MIAAAABN2UgQAACYEBAAAYEJAAAAAJgQEAABgQkAAAAAm/x/gFXyxawUpQQAAAABJRU5ErkJggg==
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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AADAxCXug+BKqvV4R/7+/laXUWLS0tIUFRVldRkl6lboIwCUNEYQAACACQEBAACYEBAAAIAJAQEAAJgQEAAAgAlXMVzm4yU9lZ93zuoyStTB7VZXUFSHXiutLgEAcBlGEAAAgAkBAQAAmBAQAACACQEBAACYEBAAAIAJAQEAAJgQEAAAgInlAcHhcCgxMdHqMgAAwG9YHhAAAIDrcZk7KWZkZOjpp5/W3//+d6Wmpurnn3/W2bNnFRsbq65du6pHjx669957tW/fPgUGBqp+/fr64osvdP78ec2ePVve3t4aNWrUFde77bbbdP78eSUnJ8vb29vqrgIA4PJcYgThxx9/1FNPPaURI0YoMjJSLVu21OzZs/XWW29p7ty5znZ16tRRSkqKcnNzVaZMGc2ZM0f33HOPtmzZosOHD191vdatW2vu3LmEAwAArpNLjCB8/vnnioiIUGFhocLDw5WSkqLVq1crODhY+fn5zna1atWSJIWGhuqee+5xTufk5FxzvSpVqpRuhwAAcHMuERDatm2rtm3batCgQXrkkUdUt25dde3aVZs2bdJnn312XduYPXv2Vdez2WwlVToAAB7JJQKCJN1zzz1q06aNli1bJi8vL6Wmpqps2bLy9vZWbm5uses/+uijSkhI+J/XAwAAZpYHBLvd7px+8skn9eSTT16x3bx585zTkydPdk6PGjXKOb1ypfmxwb9dDwAAXB+XOEkRAAC4FgICAAAwISAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwsfxGSa7mr7Ep8vf3t7qMEpOWlqaoqCirywAAuDhGEAAAgAkBAQAAmBAQAACACQEBAACYEBAAAIAJVzFc5p//itPF/HNWl1GiUvffnO0kdFx1czYEAHA5jCAAAAATAgIAADAhIAAAABMCAgAAMCEgAAAAEwICAAAwISAAAAATlwgIDodDiYmJVpcBAAB+5RIBAQAAuBaXuZPitm3b1LNnT2VmZmrAgAHKzs7WggULnMvffPNN3XbbbRo7dqx27typ8PBwHT9+XDNmzNDUqVPVokULRUdHa/369froo4/06quvavjw4Tpy5IhycnLUp08ftWjRwsIeAgDgPlwmIAQEBGjmzJnKyMhQbGysOnbsqJkzZyogIEAvvviivvjiCwUGBurcuXNaunSpMjIy9Pjjj191e5mZmdq8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
"
>
</div>

</div>

<div class="jp-OutputArea-child">

    
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>




<div class="jp-RenderedImage jp-OutputArea-output ">
<img src="data:image/png;base64,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IF28eFEzZsxQYmKi+vTpI29vb/n5+enMmTO66667DLd99dVX1a9fP7Vv397BqQEAqHostst/mjuBxMREHTp0SOPHj3fo+17+Te07D/yoakXFDn1vAADK02DkwNuyn9TUVAUGBkr6v+++li1bytPT03B9pzvcAAAAnINTHW6wWq1mRwAAAP8fMwkAAMAQJQEAABiiJAAAAEOUBAAAYIiSAAAADDnV1Q1mqzvwyeteK1rVXXntrKth7Izd1bjy2CXG/3swkwAAAAxREgAAgCFKAgAAMERJAAAAhigJAADAEFc3XCEz/jm5FZ43O4Ypakr6fo/ZKcxRkWN/YFRSxewYAByAmQQAAGCIkgAAAAxREgAAgCFKAgAAMERJAAAAhigJAADAECUBAAAYoiQAAABDVbYkjB07VkVFRTpx4oS2bdtmdhwAACqdKlsSFixYIA8PD+3Zs0f79+83Ow4AAJWOabdl/umnnzR58mRVq1ZN7u7u+sc//qGEhATt27dPNptNgwcPVo8ePRQeHq77779fGRkZ8vb21sMPP6ydO3fqwoULWrlypVJSUpSSkqLc3FxlZ2dr1KhR6tatm7p06aIPPvhAy5cvV0FBgR566CH99a9/NWu4AABUOqbNJHz55Zdq0aKFYmNjNWLECH388cc6duyY1q1bp3fffVdLly7VhQsXJEmtWrVSXFycioqKVKNGDcXGxqpp06bat2+fJCk/P1+xsbFauXKl5syZo5KSEkmSu7u7nn/+eQUFBVEQAAD4nUybSejbt6/efvttPfvss/L19dUDDzyg9PR0hYeHS5JKSkp04sQJSVKLFi0kSX5+fmratKl9ubCwUJLUpk0bubm5qX79+vLz81NWVpYJIwIAoGoxbSYhJSVFgYGBiouLU/fu3ZWYmKi2bdsqPj5ecXFx6tGjh+66666b2ld6erok6dy5c8rNzVW9evXsr7m5uamsrKxCxgAAQFVm2kxCy5YtNWHCBC1evFhubm5atGiRkpOTFRYWpvz8fHXt2lU+Pj43ta9z585p0KBBunjxombMmCF3d3f7a82aNdOSJUvUokUL9erVq6KGAwBAlWNaSbj77ru1fv36q55r2bLlNevFx8fblxcsWGBfnjp1qiQpMTFRbdq00fjx46/a7vJlj82bN9fWrVtvW24AAFxFlb0EEgAA3BrTZhJuF6vVanYEAACq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HB09elQPPfSQ3Nzc9M0336hZs2Zat26dw0ICAADHu25JiI+PlyQ999xzeuutt9S4cWNJ0vHjxzV9+nTHpAMAAKYp95yEEydO2AuCJN155506ceJEhYYCAADmK/c+Cc2bN9fEiRPVo0cP2Ww2JScn6+GHH3ZENoeL7faiPD09zY5hitTUVAUGBpodAwDgRMotCVFRUUpISLCfg9ChQweFhYVVeDAAAGCuckvCyJEjtWLFCg0dOtQReQAAgJMo95yES5cu6eTJk47IAgAAnEi5MwnZ2dnq0qWL6tWrJ09PT9lsNlksFqWkpDgiHwAAMEm5JeGdd95xRA4AAOBkyi0Jd955p9auXas9e/aopKRE7dq108CBAx2RzeGGfZSknJJis2OY56fvf/cmH/R9pgKCAACcQbkl4R//+IcOHz6sp556SjabTYmJiTp69KimTp3qiHwAAMAk5ZaEXbt26X/+53/k5vbrOY6dO3dWcHBwhQcDAADmKvfqhtLSUpWUlFz12N3dvUJDAQAA85U7k9C7d29FRESoV69ekqTNmzcrKCiowoMBAABzlVsS9u/fr5CQEKWlpcnPz08jRoxQ586dHRANAACY6abuuPjFF1/o4MGDKi0tlaenp+rWratWrVo5Ih8AADBJuSWhdevWat26tZ555hlt2bJFS5cu1TvvvKO0tDRH5AMAACYptyTMnDlTqampcnd3V5s2bTRjxgw98sgjjsgGAABMVO7VDRcuXJDNZlOTJk0UEBCge++9V76+vuXuODExUdHR0bclJAAAcLxyZxLeeOMNSVJmZqZ2796tESNGKD8/X1988UWFhwMAAOYptyQcOnRIu3fv1u7du/X999+rVatWevTRR29q58ePH1doaKjee+89SVJoaKjmz5+vTZs26fDhw8rOztb58+cVFhamjz/+WD/99JPmzp2r1q1b64033lBaWpry8vIUEBCg2bNnq3///nrttdd03333afv27fr88881fPhwRUZGqrCwUDk5ORo1apS6du2q4OBgPfLII/rhhx9ksVgUExNzUzMgAADgV+UebhgzZoxOnz6twYMHa+vWrZo/f75CQkJu+Y1r1KihFStW6IknntD27du1dOlSPf/889q8ebNyc3Pl5+en2NhYrVu3TgcOHNDp06fVr18/bdq0SZK0ceNG9e3bV4cOHdKQIUMUGxuradOm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
"
>
</div>

</div>

</div>

</div>

</div>
<div class="jp-Cell-inputWrapper"><div class="jp-InputPrompt jp-InputArea-prompt">
</div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput " data-mime-type="text/markdown">
<p>Berdasarkan Grafik diatas Interpretasi dari masing-masing cluster:</p>
<ul>
<li>Cluster 0 : Lokasi dekat Mall (positive)</li>
<li>Cluster 1 : Pelayanan Oke (positive)</li>
<li>Cluster 2 : Fasilitas Oke (positive)</li>
<li>Cluster 3 : Tempat Nyaman (positive)</li>
</ul>

</div>
</div>
</body>







</html>
