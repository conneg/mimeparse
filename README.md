# mimeparse

_This library was automatically exported from [code.google.com/archive/p/mimeparse/](https://code.google.com/archive/p/mimeparse/)._

This module provides **basic functions for parsing mime-type names and matching them against a list of media-ranges**.

See [section 14.1](http://tools.ietf.org/html/rfc2616#section-14.1) of [RFC 2616 (the HTTP specification)](http://tools.ietf.org/html/rfc2616) for a complete explanation. More information on the library can be found in the XML.com article "[Just Use Media Types?](http://www.xml.com/pub/a/2005/06/08/restful.html)."

## Contents

| Function/Method | Description |
| --------------- | ----------- |
| `parse_mime_type()` | Parses a mime-type into its component parts. |
| `parse_media_range()` | Media-ranges are mime-types with wild-cards and a 'q' quality parameter. |
| `quality()` | Determines the quality ('`q`') of a mime-type when compared against a list of media-ranges. |
| `quality_parsed()` | Just like `quality()` except the second parameter must be pre-parsed. |
| `fitness_and_quality_parsed()` | Just like `quality_parsed()` but also returns the fitness score. |
| `best_match()` | Choose the mime-type with the highest fitness score and quality ('`q`') from a list of candidates. |

## Usage

### In Erlang

```
1> mimeparse:best_match(["application/xbel+xml", "text/xml"], "text/*;q=0.5,*/*; q=0.1").
"text/xml"
```

Note that neither `quality_parsed()` nor `fitness_and_quality_parsed()` are exported from the Erlang version.

### In JavaScript

```
Rhino 1.7 release 1 2008 03 06
js> load('mimeparse.js');
js> Mimeparse.bestMatch(['application/xbel+xml', 'text/xml'], 'text/*;q=0.5,*/*; q=0.1');
text/xml
```

This example uses the [Rhino JavaScript shell](http://developer.mozilla.org/en/Rhino_Shell) but usage should be similar for other JavaScript environments.

### In Perl

```
use MIMEParse qw( best_match );
print best_match(['application/xbel+xml', 'text/xml'], 'text/*;q=0.5,*/*; q=0.1');
# text/xml
```

### In PHP

```
include_once 'mimeparse.php';

echo Mimeparse::best_match(array('application/xbel+xml', 'text/xml'),
  'text/*;q=0.5,*/*; q=0.1');
    ==>"text/xml"
```

### In Python

```
>>> import mimeparse
>>> mimeparse.best_match(['application/xbel+xml', 'text/xml'],
      'text/*;q=0.5,*/*; q=0.1')
'text/xml'
```

### In Ruby

```
require "mimeparse"
    ==>true
MIMEParse.best_match(['application/xbel+xml', 'text/xml'],
  'text/*;q=0.5,*/*; q=0.1')
    ==>"text/xml"
```

### In Java

```
List<String> mimeTypesSupported = Arrays.asList(StringUtils.split(
                "application/xbel+xml,text/xml", ','));
String bestMatch = MIMEParse.bestMatch(mimeTypesSupported, "text/*;q=0.5,*/*;q=0.1");
```

### In Go

```
import "mimeparse"

bestmatch := mimeparse.BestMatch(["application/xbel+xml", "text/xml"],
  "text/*;q=0.5,*/*; q=0.1");
```

## Testing

The format of the JSON test data file is as follows:

A top-level JSON object which has a key for each of the functions to be tested. The value corresponding to that key is a list of tests. Each test contains: the argument or arguments to the function being tested, the expected results and an optional description.

### Python

The Python tests require either Python 2.6 or the installation of the SimpleJSON library.

Installing SimpleJson can be done by:

    sudo easy_install simplejson

Run the tests by typing:

    python mimeparse_test.py
