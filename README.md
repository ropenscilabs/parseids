parseids
========



[![Build Status](https://travis-ci.org/ropenscilabs/parseids.svg?branch=master)](https://travis-ci.org/ropenscilabs/parseids)


Parsers for Digital Object Identifiers (DOIs) and Other Identifiers

Uses the R pkg [piton](https://github.com/Ironholds/piton) which gives access to the C++ PEG implementation [PEGTL](https://github.com/taocpp/PEGTL).

## Example rules

Capture any letter

```
struct name
  : plus< alpha >
{};
```

Capture any digit

```
struct numbers
  : plus< digit >
{};
```

## Grammar

Rules are combined to form a grammar, 

e.g., string must match `name`, then have one comma, then one space, 
then match `numbers`.

```
struct grammar
  : must< name, one< ',' >, space, numbers, eof >
{};
```

Which is then applied to parsing user input strings

## Install


```r
devtools::install_github("ropenscilabs/parseids")
```


```r
library("parseids")
```


## Parse DOI


```r
pid_doi("Foo 10.1094/PHYTO-04-17-0144-R")
#> [1] "10.1094/PHYTO-04-17-0144-R"
```


```r
pid_doi(c("Foo 10.1094/PHYTO-04-17-0144-R", "adsfljadfa dflj fjas fljasf 10.1094/PHYTO-04-17-0144-R"))
#> [1] "10.1094/PHYTO-04-17-0144-R" "10.1094/PHYTO-04-17-0144-R"
```


## Meta

* Please [report any issues or bugs](https://github.com/ropenscilabs/parseids/issues).
* License: MIT
* Get citation information for `parseids`: `citation(package = 'parseids')`
* Please note that this project is released with a [Contributor Code of Conduct](CONDUCT.md). By participating in this project you agree to abide by its terms.

[![rofooter](https://ropensci.org/public_images/github_footer.png)](https://ropensci.org)

