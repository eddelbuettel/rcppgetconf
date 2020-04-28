## RcppGetconf: Rcpp Interface for Querying System Configuration Variables

[![Build Status](https://travis-ci.org/eddelbuettel/rcppgetconf.svg)](https://travis-ci.org/eddelbuettel/rcppgetconf) 
[![License](http://img.shields.io/badge/license-GPL%20%28%3E=%202%29-brightgreen.svg?style=flat)](http://www.gnu.org/licenses/gpl-2.0.html) 
[![CRAN](http://www.r-pkg.org/badges/version/RcppGetconf)](https://cran.r-project.org/package=RcppGetconf) 
[![Dependencies](https://tinyverse.netlify.com/badge/RcppGetconf)](https://cran.r-project.org/package=RcppGetconf) 
[![Downloads](https://cranlogs.r-pkg.org/badges/RcppGetconf?color=brightgreen)](https://www.r-pkg.org/pkg/RcppGetconf)
[![Last Commit](https://img.shields.io/github/last-commit/eddelbuettel/rcppgetconf)](https://github.com/eddelbuettel/rcppgetconf)

### What is this?

Modern POSIX systems have a binary `getconf` which can access the system
calls `sysconf`, `pathconf` and `confstr`.  This package brings the
values back to R.

### Requirements

This package requires access to these system calls, and definitions of its
data structures in the system header files. We have used it exclusively on
Linux and OS X so far.  It _should_ (or _could_) work on other POSIX-based
operating systems, and contributions to make it build more widely would be
very welcome.

### Quick Examples

The first function corresponds to `getconf -a` and provides all values which
can be retried -- currently 320 on my systems.

```{.r}
R> res <- getAll()
R> head(res)
               key value type
1         LINK_MAX 65000 path
2  _POSIX_LINK_MAX 65000 path
3        MAX_CANON   255 path
4 _POSIX_MAX_CANON   255 path
5        MAX_INPUT   255 path
6 _POSIX_MAX_INPUT   255 path
R> tail(res)
                      key  value type
315    LEVEL4_CACHE_ASSOC      0  sys
316 LEVEL4_CACHE_LINESIZE      0  sys
317                  IPV6 200809  sys
318           RAW_SOCKETS 200809  sys
319           _POSIX_IPV6 200809  sys
320    _POSIX_RAW_SOCKETS 200809  sys
R> 
```

The second example provides read access to individual settings:

```{.r}
R>  getConfig("_NPROCESSORS_CONF")
[1] 8
R>  getConfig("LEVEL1_ICACHE_SIZE")
[1] 32768
R> getConfig("GNU_LIBC_VERSION")
[1] "glibc 2.23"
R> 
```

### Installation

The package is on [CRAN](https://cran.r-project.org) and can be installed via
a standard

```r
R> install.packages("RcppGetconf")
```

command.

### Status

It contains two useful functions right now.  It currently builds cleanly on
Linux and OS X; reports from other builds would (and PRs where needed) would
be greatly appreciated.

### Author

Dirk Eddelbuettel

### License

GPL (>= 2)
