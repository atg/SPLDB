# SPLDB: Semantic Programming Language Database

**SPLDB** is a project to build a database of programming language metadata (info, conventions, syntax, semantics, etc) in a form that computers can consume.

## Why?

In [Chocolat](http://chocolatapp.com) (a text editor for Mac), we have a class which stores information about various programming languages. But hardcoded objects in source aren't ideal. If we want to update the data, we have to change the source and ship a new update. And others can't easily contribute new languages.

**SPLDB** is intended for anyone who needs to analyze, modify or edit source code.

## Setup

**SPLDB** is developed as a series of json files, one file per language. The `compile.py` script takes these json files then assembles and minifies them into one big file called `data.json`.

To get started:

    git clone https://github.com/fileability/SPLDB.git
    python compile.py
    cat data.json

Then use one of the many [JSON implementations](http://www.json.org/).

## Contributing

Please submit any changes as a pull request.

### Extending Languages

The following keys are used in language definitions

    name (string): A display name for the language, complete with spaces and correct capitalization. This should be the *most common* rendering of the name.
    
    tab-width: Consensus on tab size, in spaces, if it exists (eg 4 for python).
    
    comment.line (string|array): A string that starts a line comment
    comment.block.start (string|array): A string that starts a block comment. If array, must have same length as comment.block.end.
    comment.block.end (string|array): A string that ends a block comment. If array, must have same length as comment.block.start.
     

### New Languages

If you want to contribute a *new* language, create a file `languagename.json`. The file's name should be all lowercase, and contain no spaces (use hyphens instead). The file's name shouldn't be abbreviated unless the language's name is almost always abbreviated that way (`objective-c.json` but `ocaml.json`).

Then put in a bit of boilerplate:

    {
        "name": "Ocaml",
    }

The `name` attribute is used to give a display name to the language, complete with spaces and correct capitalization. This should be the *most common* rendering of the name.

