---
title: Introduction
date: 2021-07-27
slug: introduction

---
Mewtator is used to transform text from one form to another according to a designed set of rules. A related task is looking for occurrences of constructs throughout the code base, eg to understand what the transformation rules need to cater for.

The fundamental use case for Mewtator is the translation of code, e.g. when porting a system to a new technology.

Mewtator works on text - not on a parsed form of the code. This keeps simple transformations simple, using straightforward text replacements. Mewtator does however provide tools to deal with more complex constructs. Another benefit of working at the text level is that it works equally well for any source language, without having to worry about the availability of compilers, on which platforms, and which versions.

The process of understanding the source text is simplified by the fact that it already compiles, and is probably auto-formatted, linted etc. It is therefore possible to work from what is actually in the source code, rather than all the possible variants that the language makes possible.

Mewtator is primarily built on javascript regular expressions, but provides mechanisms to simplify the process of composing and testing searches. It is not however limited to regular expressions. A regular expression is one way of identifying some text within a source string and capturing information from it, but any function that performs an equivalent operation can be used, combining all the differing mechanisms together to keep searches as simple as possible. Non-regular expressions are used, for example, for finding matches brackets that are recursively nested (possible in some regular expression implementations, but not in javascript, and using a dedicated function we can avoid matching with comments and string literals.

Another key principle is to allow search expressions to directly match the code being searched, in a way that is difficult with standard regular expressions. The central idea is that the user defines their own search languages (or languages). This is converted to the more complex underlying search forms with some basic substitutions (the simplest example is that a space in the search string converts to a regex matching multiple space characters, including new lines, but that same idea can be used for any level of complexity). This approach means that the user can define specific symbols to have meaning that they know don’t appear in their specific code, rather than trying to define a universal language and then having to escape it in places.

The value in Mewtator is in the framework, but also in the search, transformation and search language sets that might have been built elsewhere and can be reused. It is expected that in time a public library of useful pre-built sets will become available, but as a starting point Mewtator comes with predefined sets that are aimed the C family of languages including Java, C#, Javascript etc, and Html templating.