---
title: OPDS
---

This extension parses OPDS feeds to let you download new ebooks, or at least present a nice description
with links if eBooks are not directly accessible.

## Example OPDS feeds

Feedbooks propose a rich catalog of books in the OPDS format.
See for instance the [Most popular free books](https://catalog.feedbooks.com/publicdomain/browse/top.atom?lang=en).

Also [Gallica](https://api.bnf.fr/api-opds-du-catalogue-de-livres-numeriques-de-gallica)(French national library) proposes
[latest books](https://gallica.bnf.fr/services/engine/search/opds?operation=searchRetrieve&version=1.2&exactSearch=false&query=dc.format%20all%20%22epub%22%20sortby%20indexationdate%2Fsort.descending%20&filter=provenance%20all%20%22bnf.fr%22) and search results as OPDS.


## Calibre

The [Calibre](https://manual.calibre-ebook.com/en/server.html) eBook manager has a built-in OPDS server. Start it from Calibre toolbar and
go to [http://localhost:8080/opds](http://localhost:8080/opds). You'll then be able to get a link to a library.

[calibre-web](https://github.com/janeczku/calibre-web) is an alternate standalone web interface to your calibre library.
It supports OPDS. If your calibre-web is at https://books.example.com, you can subscribe to https://books.example.com/opds/new.
for new books.


## TODO

The main limitation is the inability to browse OPDS catalogs: they are often split by sections and one has to navigate to subsection of interest to get a feed with books.


## Settings

| setting                                   | value          | description                                                                   |
|-------------------------------------------|----------------|-------------------------------------------------------------------------------|
| extensions.opds.formats                   | list           | list ebook mime types in order of preference (eg.  `"epub", "pdf"` if you prefer epub but accept pdf)                 |

Links:

- [Extension Source](https://github.com/gpodder/gpodder/blob/master/share/gpodder/extensions/opds.py)
