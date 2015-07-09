---
layout: post
title: PHP Cheat Sheet
---

# Array

*   [**array()**](http://php.net/manual/en/function.array.php): Creates an array
*   [array_change_key_case()](http://php.net/manual/en/function.array-change-key-case.php): Returns an array with all keys in lowercase or uppercase
*   [array_chunk()](http://php.net/manual/en/function.array-chunk.php): Splits an array into chunks of arrays
*   [**array_combine()**](http://php.net/manual/en/function.array-combine.php): Creates an array by using one array for keys and another for its values
*   [array_count_values()](http://php.net/manual/en/function.array-count-values.php): Returns an array with the number of occurrences for each value
*   [**array_diff()**](http://php.net/manual/en/function.array-diff.php): Compares array values, and returns the differences
*   [array_diff_assoc()](http://php.net/manual/en/function.array-diff-assoc.php): Compares array keys and values, and returns the differences
*   [array_diff_key()](http://php.net/manual/en/function.array-diff-key.php): Compares array keys, and returns the differences
*   [array_diff_uassoc()](http://php.net/manual/en/function.array-diff-uassoc.php): Compares array keys and values, with an additional user-made function check, and returns the differences
*   [array_diff_ukey()](http://php.net/manual/en/function.array-diff-ukey.php): Compares array keys, with an additional user-made function check, and returns the differences
*   [**array_fill()**](http://php.net/manual/en/function.array-fill.php): Fills an array with values
*   [array_filter()](http://php.net/manual/en/function.array-filter.php): Filters elements of an array using a user-made function
*   [array_flip()](http://php.net/manual/en/function.array-flip.php): Exchanges all keys with their associated values in an array
*   [array_intersect()](http://php.net/manual/en/function.array-intersect.php): Compares array values, and returns the matches
*   [array_intersect_assoc()](http://php.net/manual/en/function.array-intersect-assoc.php): Compares array keys and values, and returns the matches
*   [array_intersect_key()](http://php.net/manual/en/function.array-intersect-key.php): Compares array keys, and returns the matches
*   [array_intersect_uassoc()](http://php.net/manual/en/function.array-intersect-uassoc.php): Compares array keys and values, with an additional user-made function check, and returns the matches
*   [array_intersect_ukey()](http://php.net/manual/en/function.array-intersect-ukey.php): Compares array keys, with an additional user-made function check, and returns the matches
*   [array_key_exists()](http://php.net/manual/en/function.array-key-exists.php): Checks if the specified key exists in the array
*   [**array_keys()**](http://php.net/manual/en/function.array-keys.php): Returns all the keys of an array
*   [**array_map()**](http://php.net/manual/en/function.array-map.php): Sends each value of an array to a user-made function, which returns new values
*   [**array_merge()**](http://php.net/manual/en/function.array-merge.php): Merges one or more arrays into one array
*   [array_merge_recursive()](http://php.net/manual/en/function.array-merge-recursive.php): Merges one or more arrays into one array
*   [array_multisort()](http://php.net/manual/en/function.array-multisort.php): Sorts multiple or multi-dimensional arrays
*   [array_pad()](http://php.net/manual/en/function.array-pad.php): Inserts a specified number of items, with a specified value, to an array
*   [**array_pop()**](http://php.net/manual/en/function.array-pop.php): Deletes the last element of an array
*   [array_product()](http://php.net/manual/en/function.array-product.php): Calculates the product of the values in an array
*   [**array_push()**](http://php.net/manual/en/function.array-push.php): Inserts one or more elements to the end of an array
*   [**array_rand()**](http://php.net/manual/en/function.array-rand.php): Returns one or more random keys from an array
*   [array_reduce()](http://php.net/manual/en/function.array-reduce.php): Returns an array as a string, using a user-defined function
*   [**array_reverse()**](http://php.net/manual/en/function.array-reverse.php): Returns an array in the reverse order
*   [array_search()](http://php.net/manual/en/function.array-search.php): Searches an array for a given value and returns the key
*   [array_shift()](http://php.net/manual/en/function.array-shift.php): Removes the first element from an array, and returns the value of the removed element
*   [**array_slice()**](http://php.net/manual/en/function.array-slice.php): Returns selected parts of an array
*   [array_splice()](http://php.net/manual/en/function.array-splice.php): Removes and replaces specified elements of an array
*   [**array_sum()**](http://php.net/manual/en/function.array-sum.php): Returns the sum of the values in an array
*   [array_udiff()](http://php.net/manual/en/function.array-udiff.php): Compares array values in a user-made function and returns an array
*   [array_udiff_assoc()](http://php.net/manual/en/function.array-udiff-assoc.php): Compares array keys, and compares array values in a user-made function, and returns an array
*   [array_udiff_uassoc()](http://php.net/manual/en/function.array-udiff-uassoc.php): Compares array keys and array values in user-made functions, and returns an array
*   [array_uintersect()](http://php.net/manual/en/function.array-uintersect.php): Compares array values in a user-made function and returns an array
*   [array_uintersect_assoc()](http://php.net/manual/en/function.array-uintersect-assoc.php): Compares array keys, and compares array values in a user-made function, and returns an array
*   [array_uintersect_uassoc()](http://php.net/manual/en/function.array-uintersect-uassoc.php): Compares array keys and array values in user-made functions, and returns an array
*   [array_unique()](http://php.net/manual/en/function.array-unique.php): Removes duplicate values from an array
*   [array_unshift()](http://php.net/manual/en/function.array-unshift.php): Adds one or more elements to the beginning of an array
*   [**array_values()**](http://php.net/manual/en/function.array-values.php): Returns all the values of an array
*   [array_walk()](http://php.net/manual/en/function.array-walk.php): Applies a user function to every member of an array
*   [array_walk_recursive()](http://php.net/manual/en/function.array-walk-recursive.php): Applies a user function recursively to every member of an array
*   [**arsort()**](http://php.net/manual/en/function.arsort.php): Sorts an array in reverse order and maintain index association
*   [asort()](http://php.net/manual/en/function.asort.php): Sorts an array and maintain index association
*   [compact()](http://php.net/manual/en/function.compact.php): Create array containing variables and their values
*   [**count()**](http://php.net/manual/en/function.count.php): Counts elements in an array, or properties in an object
*   [current()](http://php.net/manual/en/function.current.php): Returns the current element in an array
*   [each()](http://php.net/manual/en/function.each.php): Returns the current key and value pair from an array
*   [**end()**](http://php.net/manual/en/function.end.php): Sets the internal pointer of an array to its last element
*   [extract()](http://php.net/manual/en/function.extract.php): Imports variables into the current symbol table from an array
*   [in_array()](http://php.net/manual/en/function.in-array.php): Checks if a specified value exists in an array
*   [**key()**](http://php.net/manual/en/function.key.php): Fetches a key from an array
*   [krsort()](http://php.net/manual/en/function.krsort.php): Sorts an array by key in reverse order
*   [ksort()](http://php.net/manual/en/function.ksort.php): Sorts an array by key
*   [list()](http://php.net/manual/en/function.list.php): Assigns variables as if they were an array
*   [natcasesort()](http://php.net/manual/en/function.natcasesort.php): Sorts an array using a case insensitive): )
*   [natsort()](http://php.net/manual/en/function.natsort.php): Sorts an array using a): )
*   [next()](http://php.net/manual/en/function.next.php): Advance the internal array pointer of an array
*   [pos()](http://php.net/manual/en/function.current.php): Alias of current()
*   [prev()](http://php.net/manual/en/function.prev.php): Rewinds the internal array pointer
*   [**range()**](http://php.net/manual/en/function.range.php): Creates an array containing a range of elements
*   [reset()](http://php.net/manual/en/function.reset.php): Sets the internal pointer of an array to its first element
*   [**rsort()**](http://php.net/manual/en/function.rsort.php): Sorts an array in reverse order
*   [shuffle()](http://php.net/manual/en/function.shuffle.php): Shuffles an array
*   [sizeof()](http://php.net/manual/en/function.count.php): Alias of count()
*   [sort()](http://php.net/manual/en/function.sort.php): Sorts an array
*   [uasort()](http://php.net/manual/en/function.uasort.php): Sorts an array with a user-defined function and maintain index association
*   [uksort()](http://php.net/manual/en/function.uksort.php): Sorts an array by keys using a user-defined function
*   [usort()](http://php.net/manual/en/function.usort.php): Sorts an array by values using a user-defined  function

# String functions

*   [**addcslashes()**](http://php.net/manual/en/function.addcslashes.php): Returns a string with backslashes in front of the specified characters
*   [**addslashes()**](http://php.net/manual/en/function.addslashes.php): Returns a string with backslashes in front of predefined characters
*   [bin2hex()](http://php.net/manual/en/function.bin2hex.php): Converts a string of ASCII characters to hexadecimal values
*   [chop()](http://php.net/manual/en/function.rtrim.php): Alias of rtrim()
*   [chr()](http://php.net/manual/en/function.chr.php): Returns a character from a specified ASCII value
*   [chunk_split()](http://php.net/manual/en/function.chunk-split.php): Splits a string into a series of smaller parts
*   [convert_cyr_string()](http://php.net/manual/en/function.convert-cyr-string.php): Converts a string from one Cyrillic character-set to another
*   [convert_uudecode()](http://php.net/manual/en/function.convert-uudecode.php): Decodes a uuencoded string
*   [convert_uuencode()](http://php.net/manual/en/function.convert-uuencode.php): Encodes a string using the uuencode algorithm
*   [count_chars()](http://php.net/manual/en/function.count-chars.php): Returns how many times an ASCII character occurs within a string and returns the information
*   [crc32()](http://php.net/manual/en/function.crc32.php): Calculates a 32-bit CRC for a string
*   [crypt()](http://php.net/manual/en/function.crypt.php): One-way string encryption (hashing)
*   [**echo()**](http://php.net/manual/en/function.echo.php): Outputs strings
*   [**explode()**](http://php.net/manual/en/function.explode.php): Breaks a string into an array
*   [**fprintf()**](http://php.net/manual/en/function.fprintf.php): Writes a formatted string to a specified output stream
*   [get_html_translation_table()](http://php.net/manual/en/function.htmlspecialchars.php): Returns the translation table used by htmlspecialchars() and htmlentities()
*   [hebrev()](http://php.net/manual/en/function.hebrev.php): Converts Hebrew text to visual text
*   [hebrevc()](http://php.net/manual/en/function.hebrevc.php): Converts Hebrew text to visual text and new lines (\n) into <br />
*   [**html_entity_decode()**](http://php.net/manual/en/function.html-entity-decode.php): Converts HTML entities to characters
*   [htmlentities()](http://php.net/manual/en/function.htmlentities.php): Converts characters to HTML entities
*   [htmlspecialchars_decode()](http://php.net/manual/en/function.htmlspecialchars-decode.php): Converts some predefined HTML entities to characters
*   [htmlspecialchars()](http://php.net/manual/en/function.htmlspecialchars.php): Converts some predefined characters to HTML entities
*   [**implode()** ](http://php.net/manual/en/function.implode.php): Returns a string from the elements of an array
*   [**join()**](http://php.net/manual/en/function.join.php): Alias of implode()
*   [levenshtein()](http://php.net/manual/en/function.levenshtein.php): Returns the Levenshtein distance between two strings
*   [localeconv()](http://php.net/manual/en/function.localeconv.php): Returns locale numeric and monetary formatting information
*   [ltrim()](http://php.net/manual/en/function.ltrim.php): Strips whitespace from the left side of a string
*   [**md5()**](http://php.net/manual/en/function.md5.php): Calculates the MD5 hash of a string
*   [md5_file()](http://php.net/manual/en/function.md5-file.php): Calculates the MD5 hash of a file
*   [metaphone()](http://php.net/manual/en/function.metaphone.php): Calculates the metaphone key of a string
*   [money_format()](http://php.net/manual/en/function.money-format.php): Returns a string formatted as a currency string
*   [nl_langinfo()](http://php.net/manual/en/function.nl-langinfo.php): Returns specific local information
*   [**nl2br()**](http://php.net/manual/en/function.nl2br.php): Inserts HTML line breaks in front of each newline in a string
*   [**number_format()**](http://php.net/manual/en/function.number-format.php): Formats a number with grouped thousands
*   [ord()](http://php.net/manual/en/function.ord.php): Returns the ASCII value of the first character of a string
*   [parse_str()](http://php.net/manual/en/function.parse-str.php): Parses a query string into variables
*   [**print()**](http://php.net/manual/en/function.print.php): Outputs a string
*   [**printf()**](http://php.net/manual/en/function.printf.php): Outputs a formatted string
*   [quoted_printable_decode()](http://php.net/manual/en/function.quoted-printable-decode.php): Decodes a quoted-printable string
*   [quotemeta()](http://php.net/manual/en/function.quotemeta.php): Quotes meta characters
*   [**rtrim()**](http://php.net/manual/en/function.rtrim.php): Strips whitespace from the right side of a string
*   [setlocale()](http://php.net/manual/en/function.setlocale.php): Sets locale information
*   [**sha1()**](http://php.net/manual/en/function.sha1.php): Calculates the SHA-1 hash of a string
*   [sha1_file()](http://php.net/manual/en/function.sha1-file.php): Calculates the SHA-1 hash of a file
*   [similar_text()](http://php.net/manual/en/function.similar-text.php): Calculates the similarity between two strings
*   [soundex()](http://php.net/manual/en/function.soundex.php): Calculates the soundex key of a string
*   [**sprintf()**](http://php.net/manual/en/function.sprintf.php): Writes a formatted string to a variable
*   [sscanf()](http://php.net/manual/en/function.sscanf.php): Parses input from a string according to a format
*   [str_ireplace()](http://php.net/manual/en/function.str-ireplace.php): Replaces some characters in a string (case-insensitive)
*   [str_pad()](http://php.net/manual/en/function.str-pad.php): Pads a string to a new length
*   [**str_repeat()**](http://php.net/manual/en/function.str-repeat.php): Repeats a string a specified number of times
*   [**str_replace()**](http://php.net/manual/en/function.str-replace.php): Replaces some characters in a string (case-sensitive)
*   [str_rot13()](http://php.net/manual/en/function.str-rot13.php): Performs the ROT13 encoding on a string
*   [str_shuffle()](http://php.net/manual/en/function.str-shuffle.php): Randomly shuffles all characters in a string
*   [**str_split()**](http://php.net/manual/en/function.str-split.php): Splits a string into an array
*   [str_word_count()](http://php.net/manual/en/function.str-word-count.php): Count the number of words in a string
*   [**strcasecmp()**](http://php.net/manual/en/function.strcasecmp.php): Compares two strings (case-insensitive)
*   [strchr()](http://php.net/manual/en/function.strchr.php): Finds the first occurrence of a string inside another string (alias of strstr())
*   [**strcmp()**](http://php.net/manual/en/function.strcmp.php): Compares two strings (case-sensitive)
*   [strcoll()](http://php.net/manual/en/function.strcoll.php): Locale based string comparison
*   [strcspn()](http://php.net/manual/en/function.strcspn.php): Returns the number of characters found in a string before any part of some specified characters are found
*   [strip_tags()](http://php.net/manual/en/function.strip-tags.php): Strips HTML and PHP tags from a string
*   [stripcslashes()](http://php.net/manual/en/function.addcslashes.php): Unquotes a string quoted with addcslashes()
*   [stripslashes()](http://php.net/manual/en/function.addslashes.php): Unquotes a string quoted with addslashes()
*   [stripos()](http://php.net/manual/en/function.stripos.php): Returns the position of the first occurrence of a string inside another string (case-insensitive)
*   [stristr()](http://php.net/manual/en/function.stristr.php): Finds the first occurrence of a string inside another string (case-insensitive)
*   [**strlen()**](http://php.net/manual/en/function.strlen.php): Returns the length of a string
*   [strnatcasecmp()](http://php.net/manual/en/function.strnatcasecmp.php): Compares two strings using a): )
*   [strnatcmp()](http://php.net/manual/en/function.strnatcmp.php): Compares two strings using a): )
*   [strncasecmp()](http://php.net/manual/en/function.strncasecmp.php): String comparison of the first n characters (case-insensitive)
*   [strncmp()](http://php.net/manual/en/function.strncmp.php): String comparison of the first n characters (case-sensitive)
*   [strpbrk()](http://php.net/manual/en/function.strpbrk.php): Searches a string for any of a set of characters
*   [strpos()](http://php.net/manual/en/function.strpos.php): Returns the position of the first occurrence of a string inside another string (case-sensitive)
*   [strrchr()](http://php.net/manual/en/function.strrchr.php): Finds the last occurrence of a string inside another string
*   [strrev()](http://php.net/manual/en/function.strrev.php): Reverses a string
*   [strripos()](http://php.net/manual/en/function.strripos.php): Finds the position of the last occurrence of a string inside another string (case-insensitive)
*   [strrpos()](http://php.net/manual/en/function.strrpos.php): Finds the position of the last occurrence of a string inside another string (case-sensitive)
*   [strspn()](http://php.net/manual/en/function.strspn.php): Returns the number of characters found in a string that contains only characters from a specified charlist
*   [strstr()](http://php.net/manual/en/function.strstr.php): Finds the first occurrence of a string inside another string (case-sensitive)
*   [**strtok()**](http://php.net/manual/en/function.strtok.php): Splits a string into smaller strings
*   [**strtolower()**](http://php.net/manual/en/function.strtolower.php): Converts a string to lowercase letters
*   [strtoupper()](http://php.net/manual/en/function.strtoupper.php): Converts a string to uppercase letters
*   [**strtr()**](http://php.net/manual/en/function.strtr.php): Translates certain characters in a string
*   [**substr()**](http://php.net/manual/en/function.substr.php): Returns a part of a string
*   [substr_compare()](http://php.net/manual/en/function.substr-compare.php): Compares two strings from a specified start position (binary safe and optionally case-sensitive)
*   [substr_count()](http://php.net/manual/en/function.substr-count.php): Counts the number of times a substring occurs in a string
*   [substr_replace()](http://php.net/manual/en/function.substr-replace.php): Replaces a part of a string with another string
*   [**trim()**](http://php.net/manual/en/function.trim.php): Strips whitespace from both sides of a string
*   [ucfirst()](http://php.net/manual/en/function.ucfirst.php): Converts the first character of a string to uppercase
*   [**ucwords()**](http://php.net/manual/en/function.ucwords.php): Converts the first character of each word in a string to uppercase
*   [vfprintf()](http://php.net/manual/en/function.vfprintf.php): Writes a formatted string to a specified output stream
*   [vprintf()](http://php.net/manual/en/function.vprintf.php): Outputs a formatted string
*   [vsprintf()](http://php.net/manual/en/function.vsprintf.php): Writes a formatted string to a variable
*   [wordwrap()](http://php.net/manual/en/function.wordwrap.php): Wraps a string to a given number of characters

# Variable

*   [**boolval**](http://www.php.net/manual/en/function.boolval.php): Get the boolean value of a variable
*   [debug_zval_dump](http://www.php.net/manual/en/function.debug-zval-dump.php): Dumps a string representation of an internal zend value to output
*   [doubleval](http://www.php.net/manual/en/function.doubleval.php): Alias of floatval
*   [**empty**](http://www.php.net/manual/en/function.empty.php): Determine whether a variable is empty
*   [floatval](http://www.php.net/manual/en/function.floatval.php): Get float value of a variable
*   [get_defined_vars](http://www.php.net/manual/en/function.get-defined-vars.php): Returns an array of all defined variables
*   [get_resource_type](http://www.php.net/manual/en/function.get-resource-type.php): Returns the resource type
*   [gettype](http://www.php.net/manual/en/function.gettype.php): Get the type of a variable
*   [import_request_variables](http://www.php.net/manual/en/function.import-request-variables.php): Import GET/POST/Cookie variables into the global scope
*   [**intval**](http://www.php.net/manual/en/function.intval.php): Get the integer value of a variable
*   [**is_array**](http://www.php.net/manual/en/function.is-array.php): Finds whether a variable is an array
*   [**is_bool**](http://www.php.net/manual/en/function.is-bool.php): Finds out whether a variable is a boolean
*   [**is_callable**](http://www.php.net/manual/en/function.is-callable.php): Verify that the contents of a variable can be called as a function
*   [**is_double**](http://www.php.net/manual/en/function.is-double.php): Alias of is_float
*   [**is_float**](http://www.php.net/manual/en/function.is-float.php): Finds whether the type of a variable is float
*   [**is_int**](http://www.php.net/manual/en/function.is-int.php): Find whether the type of a variable is integer
*   [**is_integer**](http://www.php.net/manual/en/function.is-integer.php): Alias of is_int
*   [**is_long**](http://www.php.net/manual/en/function.is-long.php): Alias of is_int
*   [**is_null**](http://www.php.net/manual/en/function.is-null.php): Finds whether a variable is NULL
*   [**is_numeric**](http://www.php.net/manual/en/function.is-numeric.php): Finds whether a variable is a number or a numeric string
*   [**is_object**](http://www.php.net/manual/en/function.is-object.php): Finds whether a variable is an object
*   [**is_real**](http://www.php.net/manual/en/function.is-real.php): Alias of is_float
*   [**is_resource**](http://www.php.net/manual/en/function.is-resource.php): Finds whether a variable is a resource
*   [**is_scalar**](http://www.php.net/manual/en/function.is-scalar.php): Finds whether a variable is a scalar
*   [**is_string**](http://www.php.net/manual/en/function.is-string.php): Find whether the type of a variable is string
*   [**isset**](http://www.php.net/manual/en/function.isset.php): Determine if a variable is set and is not NULL
*   [**print_r**](http://www.php.net/manual/en/function.print-r.php): Prints human-readable information about a variable
*   [**serialize**](http://www.php.net/manual/en/function.serialize.php): Generates a storable representation of a value
*   [settype](http://www.php.net/manual/en/function.settype.php): Set the type of a variable
*   [**strval**](http://www.php.net/manual/en/function.strval.php): Get string value of a variable
*   [**unserialize**](function.unserialize.php): Creates a PHP value from a stored representation
*   [**unset**](http://www.php.net/manual/en/function.unset.php): Unset a given variable
*   [**var_dump**](http://www.php.net/manual/en/function.var-dump.php): Dumps information about a variable
*   [var_export](http://www.php.net/manual/en/function.var-export.php): Outputs or returns a parsable string representation of a variable

# Date time functions 

*   [checkdate()](http://php.net/manual/en/function.checkdate.php): Validates a Gregorian date
*   [date_default_timezone_get()](http://php.net/manual/en/function.date-default-timezone-get.php): Returns the default time zone
*   [date_default_timezone_set()](http://php.net/manual/en/function.date-default-timezone-set.php): Sets the default time zone
*   [date_sunrise()](http://php.net/manual/en/function.date-sunrise.php): Returns the time of sunrise for a given day / location
*   [date_sunset()](http://php.net/manual/en/function.date-sunset.php): Returns the time of sunset for a given day / location
*   [**date()**](http://php.net/manual/en/function.date.php): Formats a local time/date
*   [**getdate()**](http://php.net/manual/en/function.getdate.php): Returns an array that contains date and time information for a Unix timestamp
*   [gettimeofday()](http://php.net/manual/en/function.gettimeofday.php): Returns an array that contains current time information
*   [gmdate()](http://php.net/manual/en/function.gmdate.php): Formats a GMT/UTC date/time
*   [gmmktime()](http://php.net/manual/en/function.gmmktime.php): Returns the Unix timestamp for a GMT date
*   [gmstrftime()](http://php.net/manual/en/function.gmstrftime.php): Formats a GMT/UTC time/date according to locale settings
*   [idate()](http://php.net/manual/en/function.idate.php): Formats a local time/date as integer
*   [localtime()](http://php.net/manual/en/function.localtime.php): Returns an array that contains the time components of a Unix timestamp
*   [**microtime()**](http://php.net/manual/en/function.microtime.php): Returns the microseconds for the current time
*   [**mktime()**](http://php.net/manual/en/function.mktime.php): Returns the Unix timestamp for a date
*   [strftime()](http://php.net/manual/en/function.strftime.php): Formats a local time/date according to locale settings
*   [strptime()](http://php.net/manual/en/function.strftime.php): Parses a time/date generated with strftime()
*   [**strtotime()**](http://php.net/manual/en/function.strtotime.php): Parses an English textual date or time into a Unix timestamp
*   [**time()**](http://php.net/manual/en/function.time.php): Returns the current time as a Unix timestamp
