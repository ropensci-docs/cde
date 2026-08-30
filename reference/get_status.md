# Retrieve WFD Status Classification Data

Retrieves WFD Status classification data from EA Catchment Data Explorer
site. Data can be retrieved by specifying waterbody id (`WBID`),
Management Catchment (`MC`), Operational Catchment (`OC`) or River Basin
District (`RBD`). Start year (`startyr`) and end year (`endyr`) allow
specific timeranges to be downloaded. For Management Catchment (`MC`),
Operational Catchment (`OC`) or River Basin District (`RBD`) level
downloads, waterbody `type` can also be specified to allow extraction of
specific waterbody types (River, Lake etc).

## Usage

``` r
get_status(
  ea_name = NULL,
  column = NULL,
  level = "Overall Water Body",
  startyr = NULL,
  endyr = NULL,
  type = NULL
)
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

- level:

  The level within the WFD quality classification elements that
  objectives have been set at. For full details of the hierarchy of
  elements within the classification used, see
  <https://environment.data.gov.uk/catchment-planning/help/usage#catchment-hierarchy>.

  Defaults to 'Overall Water Body'. Possible values for the different
  levels retrieved by the function are shown below.

  |              |                                        |                    |
  |--------------|----------------------------------------|--------------------|
  | **Level 1**  | **Level 2**                            | **Level 4**        |
  | Ecological   | Biological quality elements            | Overall Water Body |
  | Chemical     | Chemical Status element                | \-                 |
  | Quantitative | Hydromorphological Supporting Elements | \-                 |
  | \-           | Other Substances                       | \-                 |
  | \-           | Physico-chemical quality elements      | \-                 |
  | \-           | Priority hazardous substances          | \-                 |
  | \-           | Priority substances                    | \-                 |
  | \-           | Quantitative Status element            | \-                 |
  | \-           | Specific pollutants                    | \-                 |
  | \-           | Supporting elements                    | \-                 |

- startyr:

  The data can be extracted for specific years using the `startyr` and
  `endyr` arguments. If only `startyr` is specified this extracts for a
  particular year. If no years are specified all years are returned.

- endyr:

  The data can be extracted for specific years using the `startyr` and
  `endyr` arguments. The `endyr` should only be specified if `startyr`
  is also included, otherwise an error is returned.

- type:

  Type of waterbody to be extracted. For Operational/Management
  catchment level or RBD level queries, the data can also be subset by
  waterbody type. Possible values are `River`, `Lake`,
  `GroundWaterBody`, `TransitionalWater` or `CoastalWater`.

## Value

An object of class `cde_df` containing the classification details for
the specified combination of criteria. For details of the meaning of the
the different columns returned, see
<https://docs.ropensci.org/cde/articles/cde-output-reference.html>.

## Examples

``` r
# get Overall Water Body status classification for waterbody GB520804714300
get_status(ea_name="GB520804714300", column="WBID")
#>  river_basin_district management_catchment operational_catchment
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#> With an additional 17 columns of data. 
#> Row values may be truncated to fit console. 

# get status class based on Priority substances for waterbody GB520804714300
get_status(ea_name="GB520804714300", column="WBID", level="Priority substances")
#>  river_basin_district management_catchment operational_catchment
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#>            South West      South West TraC         Tamar Estuary
#> With an additional 1 rows and 17 columns of data. 
#> Row values may be truncated to fit console. 

# get the Overall Water Body status of Lakes in the Humber RBD, between
# 2012 and 2014
get_status(ea_name="Humber", column="RBD", startyr=2012, endyr=2014, type="Lake")
#>  river_basin_district management_catchment operational_catchment
#>                Humber Louth Grimsby and An              Ancholme
#>                Humber Louth Grimsby and An              Ancholme
#>                Humber Louth Grimsby and An              Ancholme
#>                Humber Hull and East Riding    Barmston Sea Drain
#>                Humber Hull and East Riding    Barmston Sea Drain
#>                Humber Hull and East Riding    Barmston Sea Drain
#>                Humber Trent Valley Staffor Blithe Rivers and Lak
#>                Humber Trent Valley Staffor Blithe Rivers and Lak
#>                Humber Trent Valley Staffor Blithe Rivers and Lak
#>                Humber                 Dove Churnet Rivers and La
#> With an additional 380 rows and 17 columns of data. 
#> Row values may be truncated to fit console. 

# get the Overall Water Body status for Rivers in the Avon Warwickshire
# Operational Catchment in 2011
get_status(ea_name="Avon Warwickshire", column="MC", startyr=2011, type="River")
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
#> With an additional 59 rows and 17 columns of data. 
#> Row values may be truncated to fit console. 
```
