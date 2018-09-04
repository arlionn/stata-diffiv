diffiv
======

Fast implementation of Gandhi and Houde (2016) style instruments.
Currently this package is only available in Stata for Unix (Linux).

`version 0.2.0 04Sep2018`

Installation
------------

I only have access to Stata 13.1, so I impose that to be the minimum.
```stata
local github "https://raw.githubusercontent.com"
net install diffiv, from(`github'/mcaceresb/stata-diffiv/master/build/)
* adoupdate, update
* ado uninstall diffiv
```

Usage
-----

```stata
sysuse auto
egen j = group(make)
expand 3, gen(t)
replace price = price + 10 * rnormal()
diffiv priceIV = price, market(t) good(j)
diffiv priceIV mpgIV = price mpg if foreign, market(t) good(j) replace
```

Compiling
---------

To compile, you will need

- The GNU compiler collection (gcc)
- git

Then you can run
```sh
cd ../stata-diffiv
make
```

License
-------

stata-diffiv is [MIT-licensed](https://github.com/mcaceresb/stata-diffiv/blob/master/LICENSE)