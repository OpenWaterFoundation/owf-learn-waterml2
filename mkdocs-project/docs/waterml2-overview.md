# Learn WaterML 2 / WaterML 2 Overview

WaterML 2 files adhere to the WaterML 2.0 XML schema standard (version 2.0 is the latest version as of this writing).
See the [Open Geospatial Consortium (OGC) WaterML specification](http://www.opengeospatial.org/standards/waterml).
The standard has been developed to facilitate hydrologic time series data exchange,
in particular between entities that share data as part of large "enterprise" operations.
A strict XML standard ensures that time series data can be encoded and decoded by software tools.
Other data standards already exist or are under development for related data, such as stream rating data,
water quality data, and groundwater data.
WaterML 2 is typically used for data transfer and not a persistent format.
However, WaterML 2 files can be saved and read later,
although some supporting data may need to be provided to fully understand how to read the file.

In addition to representing time series data, WaterML 2 includes other data types such as spatial data for the
station at which data were collected.  These representations leverage other XML schemas as building blocks.
On the negative side, the hierarchy of objects from different schema can be difficult to follow.
Developing standard tools to read and write WaterML 2 can hide such complexities and simplify use of WaterML 2.

One way to understand WaterML 2 is to view examples and compare to the specification.
Ultimately, implementing software to read or write WaterML 2 requires a good understanding of XML technologies for the language being used.
This documentation was prepared by focusing on Java tools but will be expanded in greater detail for other languages as resources allow.
The following provides and overview of elements, and examples:

* [WaterML 2.0 - Getting Started](http://external.opengeospatial.org/twiki_public/WaterML/WaterML2GettingStarted)
* [Query of WaterML 2.0 from USGS NWIS daily data web services](https://waterservices.usgs.gov/nwis/dv/?format=waterml,2.0&indent=on&sites=09071750,09070500&startDT=2000-01-01&endDT=2000-03-15&siteStatus=all)
* [Query of WaterML 2.0 from USGS NWIS instantaneous data web services](https://waterservices.usgs.gov/nwis/iv/?format=waterml,2.0&indent=on&sites=09071750,09070500&startDT=2010-03-14&endDT=2010-03-17&siteStatus=all)

Note that the examples above include an additional `FeatureCollection` root element around the standard WaterML 2.0 `Collection` root element.

The [WaterML 2 Syntax documentation](waterml2-syntax) describes WaterML 2 syntax in more detail
and includes concepts relevant to implementation of tools.

## WaterML 2 Benefits ##

* The detailed representation of hydrologic time series data covers many data concepts that are encountered in practice
and therefore handles a wide range of situations
* XML schema supports using standard XML software tools
* WaterML 2 is an open specification

## WaterML 2 Limitations ##

* The schema is complex and can be difficult to understand, in particular if more detailed elements are used
* The schema allows for flexibility, such as "id" attribute conventions and open-ended metadata,
which results in different implementation dialects, which requires specific software features and complicates
development of universal tools
* Mapping data for an organization to WaterML 2 can take some effort
* Significant automated software tests are necessary to ensure that all aspects of a WaterML 2 implementation are correct
* Until generally-accessible tools can be developed, only larger organizations are likely to attempt publishing WaterML 2
and deal with its intricacies
