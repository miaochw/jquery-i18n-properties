# 1.0.9 #
  * Added option to disable caching ([issue 4](https://code.google.com/p/jquery-i18n-properties/issues/detail?id=4))
  * Completely mimic the Java Resource Bundle ([issue 5](https://code.google.com/p/jquery-i18n-properties/issues/detail?id=5): **Backward compatibility broken! Please read issue comments.)**

# 1.0.8 #
[2010-07-09]
  * Fixed IE bug caused by the MS buggy implementation of String.split() method

# 1.0.7 #
[2010-06-09]
  * Added support for multi-line properties
  * Prevent browser caching of old property files

# 1.0.6 #
[2010-03-28]
  * Fixed checkKeyNamespace issue (FF only)
  * Fixed issue that truncated values when containing ‘=’ symbol
  * Added demo page

# 1.0.4 #
[2009-12-29]
  * When using the map approach to retrieve bundle values, unicode chars may not be properly unescaped

# 1.0.3 #
[2009-10-06]
  * When using the map approach to retrieve bundle values, if there’s no value for a specified key, key is returned (previously, null was returned)
  * Fixed lot of errors accordingly to JSLint

# 1.0.2 #
[2009-09-18]
  * Option to have resource bundle keys available as Javascript vars/functions AND/OR as a map. The later is mandatory if your bundle keys contain Javascript reserved words

# 1.0.1 #
[2009-09-14]
  * Keys with namespaces doesn’t work
  * Values with quotation mark (“) break the code