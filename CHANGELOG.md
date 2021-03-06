1.0.3
===========
September 07, 2016

* Fixed attributes processing bug. Not cleared temp values after processing attribute key. What's in rare cases lead to segfault. (https://github.com/lexborisov/myhtml/commit/873d0fa2cbe8ec4a3b8a50b649506e791f0907c7)
* Segfault if build without threads and used parse flag without process token. (https://github.com/lexborisov/myhtml/issues/62)
* Changed rules for parse flag MyHTML_TREE_PARSE_FLAGS_SKIP_WHITESPACE_TOKEN. Now we skip ws tokens, but not for RCDATA, RAWTEXT, CDATA and PLAINTEXT
* Fixes for tokenizer state problem with parse without build tree (https://github.com/lexborisov/myhtml/issues/63)
* Tested by 1 billion HTML pages (by commoncrawl.org)
* Preparing for publication Modest

1.0.2
===========
July 14, 2016

* Fixed a bug that in some cases can lead to an infinite loop (https://github.com/lexborisov/myhtml/issues/49)
* Fixed bug for broken tag (like a `<div/===>`); https://github.com/lexborisov/myhtml/issues/50
* Added function myhtml_version for get current version

1.0.1
===========
July 13, 2016

* First Release
* Remove deprecated functions

1.0.0-rc
===========
June 23, 2016

* Synchronized with the specification of the 19.06.2016
* Changed many "strange" code. Improved code stability and readability
* Сonsumes less RAM
* Added interesting examples: 
	+ `tokenizer_colorize_high_level.c` — colorize input html (work with callbacks)
	+ `parse_without_whitespace.c` — parse and build tree without whitespace tokens (work with parse flags)
	+ `nodes_by_attr_key_high_level.c` — get nodes by attribute key
	+ `nodes_by_attr_value_high_level.c` — get nodes by attribute value (by key), interesting example, look to see

* Added API to work with the Incoming Buffer
* Added API for tokens
* Added original positions in html for tokens

* Added parsing flags (their names speak for themselves):
	+ `MyHTML_TREE_PARSE_FLAGS_WITHOUT_BUILD_TREE`
	+ `MyHTML_TREE_PARSE_FLAGS_WITHOUT_PROCESS_TOKEN`
	+ `MyHTML_TREE_PARSE_FLAGS_SKIP_WHITESPACE_TOKEN`
	+ `MyHTML_TREE_PARSE_FLAGS_WITHOUT_DOCTYPE_IN_TREE`

* Added functions to find nodes by attibutes
	+ `myhtml_get_nodes_by_attribute_key` (like a css [foo])
	+ `myhtml_get_nodes_by_attribute_value` (like a css [foo="bar"])
	+ `myhtml_get_nodes_by_attribute_value_whitespace_separated` (like a css [class~="footer"])
	+ `myhtml_get_nodes_by_attribute_value_begin` (like a css [foo^="bar"])
	+ `myhtml_get_nodes_by_attribute_value_end` (like a css [foo$="bar"])
	+ `myhtml_get_nodes_by_attribute_value_contain` (like a css [foo*="bar"])
	+ `myhtml_get_nodes_by_attribute_value_hyphen_separated` (like a css [foo|="bar"])

* Added callbacks for tokens
	+ `myhtml_callback_before_token_done_set`
	+ `myhtml_callback_after_token_done_set`

* Added conditions in source code to build MinGW
* All functions `html_parser*` now return real status
* Redesigned chunks handler and chunk global position, an Incoming Buffer for utf-16
* `myhtml attribute_name` is now deprecated, use `myhtml_attribute_key`
* Tested `myhtml_t` object for thread safe
* Changed `myhtml_string_realloc` args count
* Changed name for function `myhtml_tree_print_node_childs` to `myhtml_tree_print_node_children`
* Changed name for function `myhtml_node_insert_append_child` to `myhtml_node_append_child`
* Changed `tag_ctx_idx` on tokens to `tag_id`
* Changed `tag_idx` on tree nodes to `tag_id`
* Changed `my_str_tm` to `str` on tokens and `my_namespace` to `ns`
* Changed attributes. Now for the key and value using different strings, not united as before.
* Changed input to tokenizer stages
* Fixed handling of strings in the encoding is not UTF-8
* Fixed a hypothetical possibility of going beyond the limits of the buffer in strings
* Reworked parsers tokens. Now they have become clear and obvious
* Fixed significant bug with memory allocated for strings
* Fixed cache for strings. Previously, due to an error it did not work
* Fixed a bug which caused incorrect handle documents in UTF-16
* Deleted function `myhtml_token_is_whithspace`
* Deleted function `myhtml_tree_incomming_buffer_get_last`
* Deleted `myhtml_tree_temp_stream_t` structure and everything connected with it
