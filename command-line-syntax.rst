.. _section-top_cmd-syntax:

Command-Line Syntax
===================

All client applications as well as all of the Monitor Application's
built-in commands share the same command line parser for lexical
analysis (i.e. tokenizing) and parsing command line arguments.  While
for most usual cases, the syntax is straight-forward, there are some
corner cases and features to be aware of, especially if it comes to
arguments with special characters, such as filenames that contain
spaces.

Characters With Special Semantics
---------------------------------

For the command-line parser, the following characters have special
meaning:

* A white space character ("``⠀``", ASCII #32 / 0x20) is interpreted
  as delimiter between two adjacent arguments, unless the white space
  character is escaped or appears within a string enclosed in
  double-quotes.  Multiple adjacent white space delimiters are
  squashed into a single white space delimiter.  White space character
  delimiters that are prefixed at the start of the command line or
  appended at the end of the line are ignored.
* The double-quote character (“``"``”, ASCII #34 / 0x22) is used to
  quote a sequence of characters by enclosing it with quotes.  For
  example, imagine a filename arguments that contains a white space
  character.  Without quoting, the white space in the filename would
  be interpreted as arguments delimiter, such that the tail of the
  filename would be cut off.
* Alternatively, a single white space character can also be quoted by
  escaping.  A white space character is escaped by prefixing it with a
  backslash character ("``\``", ASCII #92 / 0x5c).
* The backslash character itself can also be quoted by prefixing it
  with a backslash character.  Escaping a backslash character is
  necessary e.g. when a backslash is to appear literally in a
  filepath.
* If the double-quote character is to literally appear as part of an
  enclosed string (rather than terminating it by being interpreted as
  closing quote), the double-quote character must be escaped by
  prefixing it with a backslash character.
* The hash character ("``#``", ASCII #35 / 0x23) is interpreted as
  comment lead-in character for single-line comments, unless it
  appears within a quoted string or it is quoted with a backslash.
  Any characters on a command line, that appear after the comment
  lead-in, are ignored.  Comments can be useful especially when
  authoring scripts for the monitor application.

Example
-------

Suppose, in the monitor application, you want to pass the following
filename as argument to the ``script`` command::

  filename with spaces and "quotes".mon

Since this filename contains white spaces and quote characters, these
characters would be treated specially rather than interpreted
literally, as supposed.  To avoid special treatment, but force literal
interpretation, you could write: ::

  script --file "filename with spaces and \"quotes\".mon"

Or: ::

  script --file filename\ with\ spaces\ and\ \"quotes\".mon

Or even: ::

  script --file filename\ wi"th spaces and \"qu"otes\".mon
