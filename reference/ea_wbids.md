# Details of name and index of all sites/catchments.

Dataframe used by \`cde\` to construct API calls. The data included are
made available under the Open Government Licence v3.0
<https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/>.
Use of the data accessed by and contained within this package implies
acceptance of these licence conditions.

## Usage

``` r
ea_wbids
```

## Format

A data frame with 5237 rows and 9 variables:

- WBID:

  identifier for individual waterbodies

- name:

  detailed name of the site/catchment

- type:

  type of waterbody (River, Lake etc.)

- OC:

  Operational Catchment name

- OC_num:

  Index number of the Operational Catchment

- MC:

  Management Catchment name

- MC_num:

  Index number of the Management Catchment

- RBD:

  River Basin District name

- RBD_num:

  Index number of the River Basin District

For details of the hierarchy of the different catchment types, see
<https://environment.data.gov.uk/catchment-planning/help#help-catchment-hierarchy>

## Source

<https://environment.data.gov.uk/catchment-planning/>
