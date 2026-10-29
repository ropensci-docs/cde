# Search database of site names

Searches the listing of EA monitoring sites to find rows that contain
the string provided. Can search by WBID (`WBID`), name (`name`),
Management Catchment (`MC`), Operational Catchment (`OC`) or River Basin
District (`RBD`). There is a hierarchical relationship between these
levels as shown at
<https://environment.data.gov.uk/catchment-planning/help#help-catchment-hierarchy>.

The search is done on a local copy of the waterbody listing contained in
the [`ea_wbids`](https://docs.ropensci.org/cde/reference/ea_wbids.md)
object rather than connecting to the EA site.

## Usage

``` r
search_names(string = NULL, column = NULL)
```

## Arguments

- string:

  The search string to be matched (case-sensitive). Will match whole or
  partial strings in the column values.

- column:

  The column to be searched. Possible options are `WBID`, `name`, `OC`
  (Operational Catchment), `MC` (Management Catchment) and `RBD` (River
  Basin District)

## Value

A data frame containing the details of all the sites that match the
search string (full or partial matches) in the column specified. Columns
returned are defined in
[`ea_wbids`](https://docs.ropensci.org/cde/reference/ea_wbids.md).

## Examples

``` r
# search for sites containing "Tadnoll" in the name
search_names(string="Tadnoll", column="name")
#>                WBID                                    name  type
#> 3694 GB108044009660 Tadnoll Brook (including Empool Bottom) River
#>                        OC     MC        RBD
#> 3694 Poole Harbour Rivers Dorset South West

# search for Operational Catchments containing "Cornwall"
search_names(string="Cornwall", column="OC")
#>                WBID           name        type                     OC
#> 3544 GB610807680002 Cornwall North     Coastal Cornwall North Coastal
#> 3567 GB620806570000 Cornwall South     Coastal Cornwall South Coastal
#> 3763 GB40802G800300 North Cornwall Groundwater         North Cornwall
#> 3769 GB40802G800200 South Cornwall Groundwater         South Cornwall
#> 3772 GB40802G800100  West Cornwall Groundwater          West Cornwall
#>                   MC        RBD
#> 3544 South West TraC South West
#> 3567 South West TraC South West
#> 3763   South West GW South West
#> 3769   South West GW South West
#> 3772   South West GW South West
```
