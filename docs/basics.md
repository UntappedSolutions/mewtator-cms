---
title: Basics
date: 2021-07-28
slug: basics

---
Mewtator is intended to make common things simple, but still be flexible enough to allow for complex things when needed. This section tries to navigate the challenge of whether to start by presenting the simple case or the flexible case.

* A query or transformation is anything with an execute() function that takes a string to execute over (plus an optional debug flag to provide insight into why searches might not be matching). Executing a query returns an array of matches. Executing a transformation returns a new string. A transformation might also be deemed to have an associated query that can be used to show what _would be_ changed, but this is not essential. (Somewhat like Tests, a lot about building your own is about debugging).
* Mewtator provides a query implementation that allows multiple searches terms to be composed together, where each term may be:
  * A regular expression
  * A string, which is interpreted using a defined search language
  * A function which can perform any text match (returning the same match objects as a regular expression match)
  * A string flagged as being part of a regular expression, but is not valid regular expression in its own right (eg capture brackets on either side of other embedded expressions)
  * A string flagged as requiring an exact match (ie not in the search language, but needs escaping), eg for matching text already returned from a previous search
  * Another query
* The Mewtator query will combine the regular expressions together except where this cannot be done (eg there is a non-regex function call, or regexes with different flags). Combining helps solve problems with matching small regex snippets such as the ^ anchor on its own). Whether the regex’es are actually combined or not though the same principle applies that the whole search must be matched as a single entity, as if it were just one long match pattern. The user doesn’t need to worry about this except when debugging searches.
* _Mewtator provides another query mechanism that wraps the above, that allows queries that are combinations of only search language and regex’es (ie most of them) to be expressed in a single string with selected character used to switch between the two modes. \[NOT YET\]_