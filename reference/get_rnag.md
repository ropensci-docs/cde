# Retrieve Reasons for Not Achieving Good Status

Retrieves details of Reasons for Not Achieving Good (RNAG) status and
Reasons For Failure (RFF) from EA Catchment Data Explorer site. Data can
be retrieved by specifying waterbody id (`WBID`), Management Catchment
(`MC`), Operational Catchment (`OC`) or River Basin District (`RBD`).
Start year (`startyr`) and end year (`endyr`) allow specific timeranges
to be downloaded. For Management Catchment (`MC`), Operational Catchment
(`OC`) or River Basin District (`RBD`) level downloads, waterbody `type`
can also be specified to allow extraction of specific waterbody types
(River, Lake etc). Data are presented at the level of individual
elements that are the reasons for not achieving good status.

## Usage

``` r
get_rnag(ea_name = NULL, column = NULL, type = NULL)
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

- type:

  Type of waterbody to be extracted. For Operational/Management
  catchment level or RBD level queries, the data can also be subset by
  waterbody type. Possible values are `River`, `Lake`,
  `GroundWaterBody`, `TransitionalWater` or `CoastalWater`.

## Value

An object of class `cde_df` containing the details of the Reasons for
Not Achieving Good Status for the specified combination of criteria. For
details of the meaning of the the different columns returned, see
<https://docs.ropensci.org/cde/articles/cde-output-reference.html>.

## Examples

``` r
# get all RNAG issues identified for waterbody GB112071065700
get_rnag("GB112071065700", "WBID")
#>  river_basin_district management_catchment operational_catchment water_body
#>            North West               Ribble            Big Ribble Duddel Bro
#>            North West               Ribble            Big Ribble Duddel Bro
#>            North West               Ribble            Big Ribble Duddel Bro
#>            North West               Ribble            Big Ribble Duddel Bro
#> With an additional 24 columns of data. 
#> Row values may be truncated to fit console. 

# get the RNAG issues for Lakes in the Humber RBD, between
# 2013 and 2014
get_rnag(ea_name="Humber", column="RBD", type="Lake")
#>  river_basin_district management_catchment operational_catchment water_body
#>                Humber Louth Grimsby and An              Ancholme Cadney Res
#>                Humber Louth Grimsby and An              Ancholme Cadney Res
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#>                Humber Hull and East Riding    Barmston Sea Drain Hornsea Me
#> With an additional 544 rows and 24 columns of data. 
#> Row values may be truncated to fit console. 

# get the RNAG issues for Rivers in the Avon Warwickshire
# Management Catchment
get_rnag(ea_name="Avon Warwickshire", column="MC", type="River")
#>  river_basin_district management_catchment operational_catchment water_body
#>                Severn    Avon Warwickshire  Avon - Midlands West Isbourne -
#>                Severn    Avon Warwickshire  Avon - Midlands West Mary Bk - 
#>                Severn    Avon Warwickshire  Avon - Midlands West Bow Bk - L
#>                Severn    Avon Warwickshire  Avon - Midlands West Mary Bk - 
#>                Severn    Avon Warwickshire  Avon - Midlands West Bow Bk - L
#>                Severn    Avon Warwickshire  Avon - Midlands West Littleton 
#>                Severn    Avon Warwickshire  Avon - Midlands West Avon - Tol
#>                Severn    Avon Warwickshire  Avon - Midlands West Tirle Broo
#>                Severn    Avon Warwickshire  Avon - Midlands West Avon - Tol
#>                Severn    Avon Warwickshire  Avon - Midlands West Isbourne -
#> With an additional 593 rows and 24 columns of data. 
#> Row values may be truncated to fit console. 
```
