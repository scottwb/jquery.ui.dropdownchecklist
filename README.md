Description
===============================================================================

*Dropdown Check List* is a javascript plugin for the *jQuery* library that
transforms a regular select HTML element into a dropdown checkbox list.

This code is a fork of the [dropdown-check-list plugin](http://code.google.com/p/dropdown-check-list/) (v0.6) created by
[Adrian Tosca](http://aleris.wordpress.com/). All credit goes to him.

This fork builds on that work, only by adding a few small features. If someday Adrian stumbles across this and likes the idea behind these changes, maybe he'll merge them back into his master and I'll discontinue this fork. The only real reason for this fork is as an expedient way to extend this plugin for some of my own immediate needs.


Usage
===============================================================================

    $('#select_id').dropdownchecklist();


Demo
===============================================================================

To get the full demo, download all the source files and open demo.html in your browser.


Documentation
===============================================================================

To view the documentation, see the demo.html file from this project, or view
the [Description and Examples](http://dropdown-check-list.googlecode.com/svn/trunk/demo.html) from the original project this was forked from.


Extensions
===============================================================================

The following features/extensions have been added above and beyond the
original version.

Exclusive Options
-----------------

Adding an `exclusive="true"` attribute to an `<option>` element of a `<select>`
will make that option "exclusive". This means that checking that option will
uncheck all other options. It also means that checking any option will uncheck
all other options that are marked as exclusive. For example:

    <select id="people" name="people" multiple="true">
      <option exclusive="true">Everybody</option>
      <option exclusive="true">Nobody</option>
      <option>Bart</option>
      <option selected="true">Homer</option>
      <option>Lisa</option>
      <option>Maggie</option>
      <option selected="true">Marge</option>
    </select>

Default Empty Text
------------------

The original dropdown-check-list would show the select field as empty when
no options were checked. This extension allows you to specify an optional
`defaultText` option to the `dropdownchecklist()` function. For example:

    $('#select_id').dropdownchecklist({defaultText:'Choose...'});

This will make it so the select shows "Choose..." instead of leaving it empty,
when there are no options checked.

Custom Select Text
------------------

The original dropdown-checklist would show a concatenation of the selected
options in the select field. This extension allows you to specify an optional
`customTextFn` option to the `dropdownchecklist()` function. This function is
called any time the set of selection changes, passing in the set of all
options and their selection state, so that it can be used to implement custom
logic to compute the text string to be displayed. For example, the following
overrides this text with "Nobody", a person's name, "N People", or
"Everybody", based on which options are selected:

    $("#s9").dropdownchecklist({
      customTextFn:function(opts) {
        var count = 0;
        var first = null;
        for (var i=0, len=opts.length; i<len; ++i) {
          if (opts[i].selected) {
            if (!first) {
              first = opts[i].text;
            }
            ++count;
          }
        }
        switch (count) {
        case 0:
          return "Nobody";
        case 1:
          return first;
        case opts.length:
          return "Everybody";
        default:
          return count + " People"
        }
      }
    });


Credits
===============================================================================

The original source was copied verbatim from the [dropdown-check-list plugin](http://code.google.com/p/dropdown-check-list/) created by [Adrian Tosca](http://aleris.wordpress.com/). All credit goes to him.

The few additional features that have been added in this fork were created by [Scott W. Bradley](http://github.com/scottwb). 


License
===============================================================================

As per Adrian's original licence, this project is licensed under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
