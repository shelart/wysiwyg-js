Wysiwyg.JS for NPM
==================
Based on a delicious Wysiwyg.JS:
**http://wysiwygjs.github.io/**

wysiwyg.js
==========

'wysiwyg.js' is a contenteditable-editor with no dependencies.
It does only:
* Transforms any HTML-element into contenteditable
* onselection-event: e.g. to open a toolbar
* onkeypress-event: e.g. to handle hotkeys
* onplaceholder-event: show/hide a placeholder
* handle popups
* .bold(), .forecolor(), .inserthtml(), ... functions

It works with:
* Internet Explorer 6+
* Firefox 3.5+
* Chrome 4+
* Safari 3.1+

If a &lt;textarea&gt; was used as 'element', the library:
* keeps the &lt;textarea&gt; in sync
* falls back to the &lt;textarea&gt; if the browser does not support 'contenteditable'
* Old iOS and Android 2.3- also degrade to &lt;textarea&gt;

This is the base library for a jQuery-plugin which is a featured editor with a toolbar and bundled popups.

The [original library](https://github.com/wysiwygjs/wysiwyg.js) is used on a website with 300M page impressions a month.

wysiwyg.js-API:
==========

````javascript
// create wysiwyg:
var wysiwygeditor = wysiwyg({
    element: 'editor-id' || document.getElementById('editor-id'),
    onKeyDown: function( key, character, shiftKey, altKey, ctrlKey, metaKey ) {
        },
    onKeyPress: function( key, character, shiftKey, altKey, ctrlKey, metaKey ) {
        },
    onKeyUp: function( key, character, shiftKey, altKey, ctrlKey, metaKey ) {
        },
    onSelection: function( collapsed, rect, nodes, rightclick ) {
        },
    onPlaceholder: function( visible ) {
        },
    onOpenpopup: function() {
        },
    onClosepopup: function() {
        },
    hijackContextmenu: false
});

// properties:
wysiwygeditor.getElement();
wysiwygeditor.getHTML(); -> 'html'
wysiwygeditor.setHTML( html );
wysiwygeditor.getSelectedHTML(); -> 'html'|false
wysiwygeditor.sync();
wysiwygeditor.readOnly(); // -> query
wysiwygeditor.readOnly( true|false );

// selection and popup:
wysiwygeditor.collapseSelection();
wysiwygeditor.expandSelection( preceding, following );
wysiwygeditor.openPopup(); -> popup-handle
wysiwygeditor.closePopup();

// exec commands:
wysiwygeditor.removeFormat();
wysiwygeditor.bold();
wysiwygeditor.italic();
wysiwygeditor.underline();
wysiwygeditor.strikethrough();
wysiwygeditor.forecolor( color );
wysiwygeditor.highlight( color );
wysiwygeditor.fontName( fontname );
wysiwygeditor.fontSize( fontsize );
wysiwygeditor.subscript();
wysiwygeditor.superscript();
wysiwygeditor.align( 'left'|'center'|'right'|'justify' );
wysiwygeditor.format( tagname );
wysiwygeditor.indent( outdent );
wysiwygeditor.insertLink( url );
wysiwygeditor.insertImage( url );
wysiwygeditor.insertHTML( html );
wysiwygeditor.insertList( ordered );
````