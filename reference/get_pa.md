# Retrieve Protected Area Information

Retrieves details of Protected Areas associated with waterbodies,
catchments or River Basin Districts from the EA Catchment Data Explorer
site. Data can be retrieved by specifying waterbody id (`WBID`),
Management Catchment (`MC`), Operational Catchment (`OC`) or River Basin
District (`RBD`).

## Usage

``` r
get_pa(ea_name = NULL, column = NULL)
```

## Arguments

- ea_name:

  A string representing the description (`name` for `OC`, `MC` or `RBD`
  level downloads or `WBID` for individual waterbodies) of the features
  to be extracted. For example to extract data for the whole of the
  Humber RBD, this would be "Humber"; also see examples. Must be an
  exact match to the values used in the EA database. Use the
  [`search_names`](https://docs.ropensci.org/cde/reference/search_names.md)
  function to search for specific values.

- column:

  The column to be searched. Possible options are `WBID` (waterbody id),
  `OC` (Operational Catchment), `MC` (Management Catchment) and `RBD`
  (River Basin District)

## Value

An object of class `cde_df` containing the details of the Protected
Areas associated with the waterbodies. For details of the meaning of the
the different columns returned, see
<https://docs.ropensci.org/cde/articles/cde-output-reference.html>.

## Examples

``` r
# get protected areas associated with waterbody GB112071065700
get_pa(ea_name="GB112071065700", column="WBID")
#>  river_basin_district management_catchment operational_catchment
#>            North West               Ribble            Big Ribble
#>            North West               Ribble            Big Ribble
#> With an additional 5 columns of data. 
#> Row values may be truncated to fit console. 

# get the protected areas associated with the Humber RBD
get_pa(ea_name="Humber", column="RBD")
#>  river_basin_district management_catchment operational_catchment
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#>                Humber            Humber GW Aire and Calder Carb 
#> With an additional 2279 rows and 5 columns of data. 
#> Row values may be truncated to fit console. 

# get the protected areas associated with the Avon Warwickshire
# Management Catchment
get_pa(ea_name="Avon Warwickshire", column="MC")
#>  river_basin_district management_catchment operational_catchment
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#>                Severn    Avon Warwickshire  Avon - Midlands West
#> With an additional 114 rows and 5 columns of data. 
#> Row values may be truncated to fit console. 
```
