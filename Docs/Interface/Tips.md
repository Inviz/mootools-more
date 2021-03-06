Class: Tips {#Tips}
===================

Display a tip on any element with a title and/or href.

### Credits:

- The idea behind Tips.js is based on [Bubble Tooltips](http://web-graphics.com/mtarchive/001717.php) by [Alessandro Fulcitiniti](http://web-graphics.com/)

### Note:

- Tips requires the page to be in [Standards Mode](http://hsivonen.iki.fi/doctype/).

### Implements:

- [Events][], [Options][]

Tips Method: constructor {#Tips:constructor}
--------------------------------------------

### Arguments:

* elements - (*mixed*: optional) A collection of elements, a string Selector, or an Element to apply the tooltips to.
* options  - (*object*) An object to customize this Tips instance.

### Options:

* showDelay     - (*number*: defaults to 100) The delay the show event is fired.
* hideDelay     - (*number*: defaults to 100) The delay the hide hide is fired.
* title			- (*string|function*: defaults to title) The property of the element to be used for the tip-title. If this option is a
					function it will execute it on every element with it passed as the first argument. It uses the return value of this function
					as the tip-title
* text			- (*string|function*) Behaves the same as the `title` option but for tip-title. By default it either uses the `rel` or the `href` attribute as tip-title.
* className     - (*string*: defaults to null) the className your tooltip container will get. Useful for extreme styling.
 * The tooltip element inside the tooltip container above will have 'tip' as classname.
 * The title will have as classname: tip-title
 * The text will have as classname: tip-text
* offset       - (*object*: defaults to {'x': 16, 'y': 16}) The distance of your tooltip from the mouse.
* fixed         - (*boolean*: defaults to false) If set to true, the toolTip will not follow the mouse.


### Events:

 * show: fires when the tip is shown; passed the tip dom element
 * hide: fires when the tip is being hidden; passed the tip dom element

### Example:

#### HTML:

	<a href="http://mootools.net" title="mootools homepage" class="thisisatooltip" />

#### JavaScript

	var myTips = new Tips('.thisisatooltip');



Tips Event: show {#Tips:show}
---------------------------------

* (*function*) Fires when the Tip is starting to show and by default sets the tip visible.

### Signature:

	onShow(tip)

### Arguments:

1. tip - (*element*) The tip element. Useful if you want to apply effects to it.
2. el - (*element*) The element on which the tip is based on.

### Example:

	myTips.addEvent('show', function(tip, el){
		tip.fade('in');
	});

Tips Event: hide {#Tips:hide}
---------------------------------

* (*function*) Fires when the Tip is starting to hide and by default sets the tip hidden.

### Signature:

	onHide(tip)

### Arguments:

1. tip - (*element*) The tip element. Useful if you want to apply effects to it.
2. el - (*element*) The element on which the tip is based on.

### Example:

	myTips.addEvent('hide', function(tip, el){
		tip.fade('out');
	});



Tips Method: attach {#Tips:attach}
----------------------------------

Attaches tooltips to elements. Useful to add more elements to a tips instance.

### Syntax:

	myTips.attach(elements);

### Arguments:

1. elements - (*mixed*) A collection of elements, a string Selector, or an Element to apply the tooltips to.

### Returns:

* (*object*) This Tips instance.

### Example:

	myTips.attach('a.thisisatip');


Tips Method: detach {#Tips:detach}
----------------------------------

Detaches tooltips from elements. Useful to remove elements from a tips instance.

### Syntax:

	myTips.detach(elements);

### Arguments:

1. elements - (*mixed*) A collection of elements, a string Selector, or an Element to apply the tooltips to.

### Returns:

* (*object*) This Tips instance.

### Example:

	myTips.detach('a.thisisatip');


Tips HTML Structure {#Tips:HTML}
--------------------------------

	<div class="options.className"> //the className you pass in options will be assigned here.
		<div class="tip-top"></div> //useful for styling

		<div class="tip">

			<div class="tip-title"></div>

			<div class="tip-text"></div>

		</div>

		<div class="tip-bottom"></div> //useful for styling
	</div>


Tips with storage {#Tips:Storage}
---------------------------------

You can also assign tips titles and contents via [Element Storage](/Element/Element/#ElementStorage).

### Example:

#### HTML:

	<a id="tip1" href="http://mootools.net" title="mootools homepage" class="thisisatooltip" />

#### JavaScript

	$('tip1').store('tip:title', 'custom title for tip 1');

	$('tip1').store('tip:text', 'custom text for tip 1');

### Note:

If you use tips storage you can use elements and / or html as tips title and text.


[Events]: /docs/core/Class/Class.Extras#Events
[Options]: /docs/core/Class/Class.Extras#Options
