# Learn WaterML 2 / WaterML 2 Syntax #

WaterML 2 XML syntax conforms to the [WaterML 2.0 schema](http://www.opengeospatial.org/standards/waterml),
which defines the names of elements and attributes,
indicates whether elements are required/optional, and whether multiple elements are allowed.
Because the WaterML 2.0 schema relies on other schemas that have been designed over time and by multiple entities,
there is inconsistency in naming conventions (case, plural, etc.).

This page contains the following sections, which walk through important schema elements and provides
context relevant to typical time series data handling.
The [WaterML 2.0 - Getting Started](http://external.opengeospatial.org/twiki_public/WaterML/WaterML2GettingStarted)
documentation is also helpful to understand the hierarchy of elements.

* [Root Element](#root-element)
	+ [Collection (Standard)](#collection-Standard)
	+ [FeatureCollection (USGS)](#featurecollection-usgs)

## Root Element ##

XML files are a hierarchy and require as single root element as the entry point.
The root element for WaterML 2.0 according to the standard is `Collection`.
However, different implementations may provide additional data, such as the USGS, which wraps the `Collection` element with `FeatureCollection`,
as discussed below.

### Collection (Standard) ###

The WaterML 2.0 standard uses `Colletion` as the root element, for example (this example was created by slightly rearranging data
from the USGS NWIS example in the next section).
Note that the first element contains information such as the schemas used in the file.

```xml
<wml2:Collection gml:id="C.USGS.09071750" xsi:schemaLocation="http://www.opengis.net/waterml/2.0 http://schemas.opengis.net/waterml/2.0/waterml2.xsd" xmlns:gml="http://www.opengis.net/gml/3.2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:wml2="http://www.opengis.net/waterml/2.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:om="http://www.opengis.net/om/2.0" xmlns:sa="http://www.opengis.net/sampling/2.0" xmlns:sams="http://www.opengis.net/samplingSpatial/2.0" xmlns:swe="http://www.opengis.net/swe/2.0">
      <gml:identifier codeSpace="http://waterservices.usgs.gov/nwis/dv">USGS.09071750</gml:identifier>
      <gml:name codeSpace="http://waterservices.usgs.gov/nwis/dv">Timeseries collected at COLORADO RIVER ABOVE GLENWOOD SPRINGS, CO</gml:name>
      <wml2:metadata>
        <wml2:DocumentMetadata gml:id="doc.USGS.MP.USGS.09071750">
          <gml:metaDataProperty about="contact" xlink:href="http://waterservices.usgs.gov"/>
          <wml2:generationDate>2017-06-29T04:34:37.787-04:00</wml2:generationDate>
          <wml2:version xlink:href="http://www.opengis.net/waterml/2.0" xlink:title="WaterML 2.0"/>
        </wml2:DocumentMetadata>
      </wml2:metadata>
      <wml2:observationMember>
```

### FeatureCollection (USGS) ###

USGS NWIS web services use `FeatureCollection` as the root element, for example:

```xml
<gml:FeatureCollection gml:id="USGS.waterservices" xsi:schemaLocation="http://www.opengis.net/waterml/2.0 http://schemas.opengis.net/waterml/2.0/waterml2.xsd" xmlns:gml="http://www.opengis.net/gml/3.2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:wml2="http://www.opengis.net/waterml/2.0" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:om="http://www.opengis.net/om/2.0" xmlns:sa="http://www.opengis.net/sampling/2.0" xmlns:sams="http://www.opengis.net/samplingSpatial/2.0" xmlns:swe="http://www.opengis.net/swe/2.0">
  <gml:featureMember>
    <wml2:Collection gml:id="C.USGS.09070500">
      <gml:identifier codeSpace="http://waterservices.usgs.gov/nwis/dv">USGS.09070500</gml:identifier>
      <gml:name codeSpace="http://waterservices.usgs.gov/nwis/dv">Timeseries collected at COLORADO RIVER NEAR DOTSERO, CO</gml:name>

```

Note that the `FeatureCollection` provides minimal additional data in this example.
Once the `Collection` element is encountered, the remainder of the elements follow the WaterML 2.0 standard.

### More Data ###

***TODO smalers 2017-07-15 need to transfer content from the "WaterML 2.0 Open Data Implementation Guidance Project".***`
