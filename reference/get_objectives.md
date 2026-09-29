# Retrieve Objectives set for waterbodies

Retrieves details of objectives set for waterbodies in terms of
predicted classification from EA Catchment Data Explorer site. Data can
be retrieved by specifying waterbody id (`WBID`), Management Catchment
(`MC`), Operational Catchment (`OC`) or River Basin District (`RBD`).
Start year (`startyr`) and end year (`endyr`) allow specific timeranges
to be downloaded. For Management Catchment (`MC`), Operational Catchment
(`OC`) or River Basin District (`RBD`) level downloads, waterbody `type`
can also be specified to allow extraction of specific waterbody types
(River, Lake etc).

## Usage

``` r
get_objectives(
  ea_name = NULL,
  column = NULL,
  level = "Overall Water Body",
  year = NULL,
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
  <https://environment.data.gov.uk/catchment-planning/help#help-classification-hierarchy>.

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

- year:

  The year that objectives are set for, either 2015, 2021, 2027, 2040
  or 2050. If not given then objectives for all years are returned. Note
  that objectives may not be set for all years.

- type:

  Type of waterbody to be extracted. For Operational/Management
  catchment level or RBD level queries, the data can also be subset by
  waterbody type. Possible values are `River`, `Lake`,
  `GroundWaterBody`, `TransitionalWater` or `CoastalWater`.

## Value

An object of class `cde_df` containing the details of the objectives set
for the specified set of waterbodies. For details of the meaning of the
the different columns returned, see
<https://docs.ropensci.org/cde/articles/cde-output-reference.html>.

## Examples

``` r
# get all objectives set for waterbody GB112071065700
get_objectives(ea_name="GB112071065700", column="WBID")
#>  river_basin_district management_catchment operational_catchment water_body
#>            North West               Ribble            Big Ribble Duddel Bro
#> With an additional 13 columns of data. 
#> Row values may be truncated to fit console. 

# get the objectives set for Lakes in the Humber RBD, for the year 2021
get_objectives(ea_name="Humber", column="RBD", year=2021, type="Lake")
#>  river_basin_district management_catchment operational_catchment water_body
#>                Humber       Idle and Torne            Idle River Welbeck Gr
#>                Humber Wharfe and Ouse Lowe Wharfe Middle and Was Swinsty Re
#>                Humber Trent Valley Staffor Penk Rivers and Lakes Belvide Re
#>                Humber Swale Ure Nidd and O            Nidd Upper Gouthwaite
#> With an additional 13 columns of data. 
#> Row values may be truncated to fit console. 

# get the objectives set for Rivers in the Avon Warwickshire
# Management Catchment in relation to Chemical status
get_objectives(ea_name="Avon Warwickshire", column="MC", level="Chemical", type="River")
#>  river_basin_district management_catchment operational_catchment water_body
#>                Severn    Avon Warwickshire  Avon - Midlands West Elmley Cas
#>                Severn    Avon Warwickshire  Avon - Midlands West Mary Bk - 
#>                Severn    Avon Warwickshire  Avon - Midlands West Harvington
#>                Severn    Avon Warwickshire  Avon - Midlands West Broadway-B
#>                Severn    Avon Warwickshire  Avon - Midlands West Swilgate -
#>                Severn    Avon Warwickshire  Avon - Midlands West Piddle Bk 
#>                Severn    Avon Warwickshire  Avon - Midlands West Bretforton
#>                Severn    Avon Warwickshire  Avon - Midlands West Littleton 
#>                Severn    Avon Warwickshire  Avon - Midlands West Whitsunn B
#>                Severn    Avon Warwickshire  Avon - Midlands West Bourne Bk 
#> With an additional 65 rows and 13 columns of data. 
#> Row values may be truncated to fit console. 
```
