# Learn WaterML 2 / Tools for Java #

This page describes Java tools that are available for WaterML 2.

The Java language ecosystem includes technologies to facilitate writing and reading XML files.
These technologies can be used, for example, to create a Java Application Programming Interface (API) library.
The API can then be be used to read WaterML XML files into "plain old Java object" POJO objects and to
create WaterML XML files from POJOs.  The API Java classes adhere to the WaterML 2 specification.

A typical approach is to use the [Java Architecture for XML Binding (JAXB)](https://en.wikipedia.org/wiki/Java_Architecture_for_XML_Binding)
specification and the [`xfc` compiler](https://docs.oracle.com/javase/8/docs/technotes/tools/unix/xjc.html) to process the XML schema into Java code library.
However, in the case of WaterML 2, a number of XML schema conflicts occur, which requires use of an
external "bindings" file to guide the `xjc` program.
The following GitHub repository provides useful bindings files for Open Geospatial Consortium (OGC) standards:  [Highsource OGC Schemas](https://github.com/highsource/ogc-schemas).
The Open Water Foundation used this information to create a workable API
(see: [Open Water Foundation owf-lib-waterml2-java on GitHub](https://github.com/OpenWaterFoundation/owf-lib-waterml2-java)), which was then
incorporated into the TSTool software listed below.
Unfortunately, these API solutions are not as clean or simple as desired due to the complex naming convention of auto-generated APIS.
Consequently, many programmers may find it easier to parse the DOM using XML tools.
Parsing the DOM is appropriate and workable, especially if only a subset of data in the file is read.
OWF implemented the API and DOM approach in the TSTool `ReadWaterML2()` and `WriteWaterML2()` commands in order to evaluate level of effort to code and performance.

Although an auto-generated API is useful, its implementation is limited by a number of factors:

* There is enough flexibility in the WaterML 2 specification that different implementations of WaterML 2 software
must be written to handle the different "dialects", for example:
	+ Implementors of WaterML 2 may choose to use "id" attributes for elements to encode key
	data, such as site identifier, data type, and statistic. USGS NWIS web services take this approach.
	+ WaterML 2 metadata elements provide means to encode generic property lists,
	which must be mapped to software objects by convention (rather than specific API).
	Again, this may be used for site identifier, data type, interval etc.
	+ Some API code resorts to using more generic `JAXBElement` objects,
	and therefore must be parsed similar to parsing the DOM.
* An organization's data management solution (typically a database) and software applications typically do not exactly match
the WaterML 2 data model.  Consequently, it is necessary to write code to map the specific data representation
to the WaterML 2 specification and API.  Due to the complexity of the specification, the mapping
exercise may not be simple.

A number of organizations have developed Java code to utilize WaterML 2 and are useful as a reference to
implement WaterML 2 features in a specific software solution:

* [52 North Sensor Observation Service](https://github.com/52North/sos) - European effort, integrates WaterML 2.0 with data collection system
* [Deltares FEWS WaterML 2 Data Import](https://publicwiki.deltares.nl/display/FEWSDOC/WaterML2Import) - used in FEWS product
* [Open Water Foundation Java WaterML 2 API Library](https://github.com/OpenWaterFoundation/owf-lib-waterml2-java) - auto-generated API using Highsource bindings as core

It would be possible with more resources to create a generic Java API library.
However, variations in dialects need to be understood in order to implement a general solution.
