# R packages (RStudio)

## Packages required for R Notebooks (16)

- **base64enc**: Tools for base64 encoding

This package provides tools for handling base64 encoding. It is more flexible than the orphaned base64 package.

- **digest**: Create Compact Hash Digests of R Objects

Implementation of a function 'digest()' for the creation of hash digests of arbitrary R objects (using the 'md5', 'sha-1', 'sha-256', 'crc32', 'xxhash', 'murmurhash', 'spookyhash' and 'blake3' algorithms) permitting easy comparison of R language objects, as well as functions such as'hmac()' to create hash-based message authentication code. Please note that this package is not meant to be deployed for cryptographic purposes for which more comprehensive (and widely tested) libraries such as 'OpenSSL' should be used.

- **evaluate**: Parsing and Evaluation Tools that Provide More Details than the Default

Parsing and evaluation tools that make it easy to recreate the command line behaviour of R.

- **glue**: Interpreted String Literals

An implementation of interpreted string literals, inspired by Python's Literal String Interpolation <https://www.python.org/dev/peps/pep0498/> and Docstrings <https://www.python.org/dev/peps/pep-0257/> and Julia's Triple-Quoted String Literals <https://docs.julialang.org/en/v1.3/manual/strings/#Triple-Quoted-String-Literals-1>

- **highr**: Syntax Highlighting for R Source Code

Provides syntax highlighting for R source code. Currently it supports LaTeX and HTML output. Source code of other languages is supported via Andre Simon's highlight package (<http://www.andre-simon.de>).

- **htmltools**: Tools for HTML

Tools for HTML generation and output.

- **jsonlite**: A Simple and Robust JSON Parser and Generator for R

A reasonably fast JSON parser and generator, optimized for statistical data and the web. Offers simple, flexible tools for working with JSON in R, and is particularly powerful for building pipelines and interacting with a web API. The implementation is based on the mapping described in the vignette (Ooms, 2014). In addition to converting JSON data from/to R objects, 'jsonlite' contains functions to stream, validate, and prettify JSON data. The unit tests included with the package verify that all edge cases are encoded and decoded consistently for use with dynamic data in systems and applications.

- **knitr**: A General-Purpose Package for Dynamic Report Generation in R

Provides a general-purpose tool for dynamic report generation in R using Literate Programming techniques.

- **magrittr**: A Forward-Pipe Operator for R

Provides a mechanism for chaining commands with a new forward-pipe operator, %>%. This operator will forward a value, or the result of an expression, into the next function call/expression. There is flexible support for the type of right-hand side expressions. For more information, see package vignette. To quote Rene Magritte, "Ceci n'est pas un pipe."
 
- **mime**: Map Filenames to MIME Types

Guesses the MIME type from a filename extension using the data derived from /etc/mime.types in UNIX-type systems.

- **rmarkdown**: Dynamic Documents for R

Convert R Markdown documents into a variety of formats.

- **stringi**: Character String Processing Facilities

A collection of character string/text/natural language processing tools for pattern searching (e.g., with 'Java'-like regular expressions or the 'Unicode' collation algorithm), random string generation, case mapping, string transliteration, concatenation, sorting, padding, wrapping, Unicode normalisation, date-time formatting and parsing, and many more. They are fast, consistent, convenient, and - thanks to 'ICU' (International Components for Unicode) - portable across all locales and platforms.

- **stringr**: Simple, Consistent Wrappers for Common String Operations

A consistent, simple and easy to use set of wrappers around the fantastic 'stringi' package. All function and argument names (and positions) are consistent, all functions deal with "NA"'s and zero length vectors in the same way, and the output from one function is easy to feed into the input of another.

- **xfun**: Supporting Functions for Packages Maintained by 'Yihui Xie'

Miscellaneous functions commonly used in other packages maintained by 'Yihui Xie'.

- **yaml**: Methods to Convert R Data to YAML and Back

Implements the 'libyaml' 'YAML' 1.1 parser and emitter (<http://pyyaml.org/wiki/LibYAML>) for R.

- **tinytex**: Helper Functions to Install and Maintain TeX Live, and Compile LaTeX Documents

Helper functions to install and maintain the 'LaTeX' distribution named 'TinyTeX' (<https://yihui.org/tinytex/>), a lightweight, cross-platform, portable, and easy-to-maintain version of 'TeX Live'. This package also contains helper functions to compile 'LaTeX' documents, and install missing 'LaTeX' packages automatically.

## Packages required for other RStudio functionality

- **curl**: A Modern and Flexible Web Client for R

The curl() and curl_download() functions provide highly configurable drop-in replacements for base url() and download.file() with better performance, support for encryption (https, ftps), gzip compression, authentication, and other 'libcurl' goodies. The core of the package implements a framework for performing fully customized requests where data can be processed either in memory, on disk, or streaming via the callback or connection interfaces. Some knowledge of 'libcurl' is recommended; for a more-user-friendly web client see the 'httr' package which builds on this package with http specific tools and logic.

- **openssl**: Toolkit for Encryption, Signatures and Certificates Based on OpenSSL

Bindings to OpenSSL libssl and libcrypto, plus custom SSH key parsers. Supports RSA, DSA and EC curves P-256, P-384, P-521, and curve25519. Cryptographic signatures can either be created and verified manually or via x509 certificates. AES can be used in cbc, ctr or gcm mode for symmetric encryption; RSA for asymmetric (public key) encryption or EC for Diffie Hellman. High-level envelope functions combine RSA and AES for encrypting arbitrary sized data. Other utilities include key generators, hash functions (md5, sha1, sha256, etc), base64 encoder, a secure random number generator, and 'bignum' math methods for manually performing crypto calculations on large multibyte integers.

- **packrat**: A Dependency Management System for Projects and their R Package Dependencies

Manage the R packages your project depends on in an isolated, portable, and reproducible way.

- **rsconnect**: Deployment Interface for R Markdown Documents and Shiny Applications

Programmatic deployment interface for 'RPubs', 'shinyapps.io', and 'RStudio Connect'. Supported content types include R Markdown documents, Shiny applications, Plumber APIs, plots, and static web content
Note: imports: packrat

- **shiny**: Web Application Framework for R

Makes it incredibly easy to build interactive web applications with R. Automatic "reactive" binding between inputs and outputs and extensive prebuilt widgets make it possible to build beautiful, responsive, and powerful applications with minimal effort.

- **learnr**: Interactive Tutorials for R

Create interactive tutorials using R Markdown. Use a combination of narrative, figures, videos, exercises, and quizzes to create self-paced tutorials for learning about R and R packages.
