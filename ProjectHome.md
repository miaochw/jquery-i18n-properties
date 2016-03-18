# This project has moved to Github! #
### Please check the new homepage: ###
### https://github.com/jquery-i18n-properties/jquery-i18n-properties ###

<a href='Hidden comment: 
=About=
*jQuery.i18n.properties* is a lightweight jQuery plugin for providing internationalization to javascript from ‘.properties’ files, just like in Java Resource Bundles. It loads and parses resource bundles (.properties) based on provided language and country codes (ISO-639 and ISO-3166) or language reported by browser.

Resource bundles are ‘.properties‘ files containing locale specific key-value pairs. The use of ‘.properties‘ files for translation is specially useful when sharing i18n files between Java and Javascript projects. This plugin loads the default file (eg, Messages.properties) first and then locale specific files (Messages_pt.properties, then Messages_pt_PT.properties), so that a default value is always available when there is no translation provided. Translation keys will be available to developer as javascript variables/functions (functions, if translated value contains substitutions (eg, {0}) or as a map.

This plugin was inspired on the [http://keith-wood.name/localisation.html Localisation assistance for jQuery from Keith Wood], and is made available under a dual license (GPL and MIT).


=Features=
* Use Java standard ‘.properties‘ files for translations
* Use standard ISO-639 for language code and ISO-3166 for country code
* Sequential loading of resource bundles from base language to user-specified/browser-specified so there is always a default value for an untranslated string (eg: msg.properties, msg_pt.properties, msg_pt_PT.properties)
* Use browser reported language if no language was specified
* Placeholder substitution in resource bundle strings (eg, msg_hello = Hello {0}!!)
* Suport for namespaces in keys (eg, com.company.msgs.hello = Hello!)
* Support for multi-line property values
* Resource bundle keys available as Javascript vars/functions or as a map


=Example=
Take as an example the following Messages.properties, Messages_pt.properties and Messages_pt_PT.properties:

*Messages.properties*
```
# This line is ignored by the plugin
msg_hello = Hello
msg_world = World
msg_complex = Good morning {0}!
```

*Messages_pt.properties*
```
# We only provide a translation for the "msg_hello" key
msg_hello = Bom dia
```

*Messages_pt_PT.properties*
```
# We only provide a translation for the "msg_hello" key
msg_hello = Olá
```

Now, suppose these files are located on the ‘bundle/‘ folder. One can invoke the plugin like below:
```
// This will initialize the plugin 
// and show two dialog boxes: one with the text "Olá World"
// and other with the text "Good morning John!" 
jQuery.i18n.properties({
    name:"Messages", 
    path:"bundle/", 
    mode:"both",
    language:"pt_PT", 
    callback: function() {
        // We specified mode: "both" so translated values will be
        // available as JS vars/functions and as a map

        // Accessing a simple value through the map
        jQuery.i18n.prop("msg_hello");
        // Accessing a value with placeholders through the map
        jQuery.i18n.prop("msg_complex", "John");

        // Accessing a simple value through a JS variable
        alert(msg_hello +" "+ msg_world);
        // Accessing a value with placeholders through a JS function
        alert(msg_complex("John"));
    }
});
```

This will initialize the plugin (loading bundle files and parsing them) and show a dialog box with the text *“Olá World”* and other with *“Good morning John!”*. The english word “World” is shown because we didn’t provide a translation for the _msg_world_ key. Also notice that keys are available as a *map* and also as *javascript variables* (for simple strings) and *javascript functions* (for strings with placeholders for substitution).


=Usage=

==Options==
|| *Option* || *Description* || *Notes* ||
|| name || Partial name (or names) of files representing resource bundles (eg, ‘Messages’ or ["Msg1","Msg2"]). Defaults to "Messages" || *Optional* String or String[] ||
|| language || ISO-639 Language code and, optionally, ISO-3166 country code (eg, ‘en’, ‘en_US’, ‘pt_PT’). If not specified, language reported by the browser will be used instead. || *Optional* String ||
|| path || Path to directory that contains ‘.properties‘ files to load. || *Optional* String ||
|| mode || Option to have resource bundle keys available as Javascript vars/functions OR as a map. The ‘map’ option is mandatory if your bundle keys contain [http://javascript.about.com/library/blreserved.htm Javascript Reserved Words]. Possible options: ‘vars’ (default), ‘map’ or ‘both’ || *Optional* String ||
|| cache || Whether bundles should be cached by the browser, or forcibly reloaded on each page load. Defaults to false (i.e. forcibly reloaded). || *Optional* boolean ||
|| encoding || The encoding to request for bundles. Property file resource bundles are specified to be in ISO-8859-1 format. Defaults to UTF-8 for backward compatibility. || *Optional* string ||
|| callback || Callback function to be called uppon script execution completion. || *Optional* function() ||

==Including and invoking the plugin==
1. Load the script:
```
<script type="text/javascript" language="JavaScript"
  src="js/jquery.i18n.properties-min.js"></script>
```
2. Initialize the plugin (minimal usage, will use language reported by browser), and access a translated value (assuming a key named ‘org.somekey‘ exists):
```
jQuery.i18n.properties({
  name: "Messages", 
  callback: function(){ alert( org.somekey ); }
});
```


=Demo=
See a small [http://codingwithcoffee.com/files/trunk/index.html demonstration].


=Downloads=
* [http://code.google.com/p/jquery-i18n-properties/downloads/list Downloads page]
* Read [http://code.google.com/p/jquery-i18n-properties/wiki/ChangeLog Change Log] first


=Known issues=
* Cross-site requests not allowed (see [http://en.wikipedia.org/wiki/Same_origin_policy Same Origin policy])
* Local file requests (file://) may fail in some browsers ([http://code.google.com/p/chromium/issues/detail?id=40787 Chrome Issue 40787])
* Having HTML elements with IDs equal to key values in .properties files will fail on some browsers (IE, Chrome) when values are not accessed through jQuery.i18n.prop() method.
Example:
```
<!-- on HTML file: -->
<div id="test123">ola</div>

# on .properties file:
test123 = qwerty
```
Executing alert(test123); will output the div object with id “ola” and not the “qwerty” string!
'></a>