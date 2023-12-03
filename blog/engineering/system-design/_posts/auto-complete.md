![Auto Complete or Typeahead System](/assets/blog/engineering/system-design/sd-auto-complete.png)

# References
* https://www.educative.io/courses/data-structures-coding-interviews-java/trie-vs-hash-table
* https://systemdesignschool.io/problems/typeahead/solution
* http://oldblog.antirez.com/post/autocomplete-with-redis.html

# Notes
Finally, understood why a trie may have a benefit over hashtable when building an autocomplete system. It’s the size of
the “keys”. Number of keys and the storage requirement for storing “value” of keys is comparable across both trie and
hashtable. But keys will require less space in trie, because each key is, roughly 1 character long (~2 bytes), while 
hashtable keys will be several characters long.

Tradeoff is space vs time. Saving space when using a trie, but assuming hashing is performant, more look-ups (and hence 
network I/O) needed in trie per character of the search prefix. Hashtable approach: 1 single look-up per search prefix 
and bam… we have the suggestions.

![Trie vs Hash Table](/assets/blog/engineering/system-design/trie-vs-hast-table.png)

