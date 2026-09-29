# Plot method for `cde_df` output

Default plots of the output main `get_` functions. Details of the plots
for different data are given below.

For `status` and `objectives` produces a (stacked) percentage barplot of
waterbody observed or predicted (objective) status information for a
given set of data.

For `rnag`, `measures` or `pa` produces a frequency histogram. The
columns plotted for each data type are given below:

- rnag (pressure_tier_3)

- measures (measure_category_1)

- pa (protected_area_type)

The full detail of the different data being plotted can be found in the
EA Catchment Data Explorer API reference:
<https://environment.data.gov.uk/catchment-planning/ui/reference>

Plotting is only possible for MC, OC or RBD downloads.

## Usage

``` r
# S3 method for class 'cde_df'
plot(x, ...)
```

## Arguments

- x:

  An object of class `cde_df` to be plotted.

- ...:

  Other arguments passed on to individual methods. The only other
  argument implemented at present is `scheme`. For `status` and
  `objectives` data this defines which colour scheme to use with plots.
  It defaults to a viridis-based scheme (`scheme="vir"`). Alternatively,
  the colours specified in the WFD document can be used by specifying
  `scheme="wfd"`.
