---
title: Reference Information
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: IOOS SOS v1.0 Web Service Description
sidebar: mydoc_sidebar
#topnav: topnav
toc: false
#permalink: sos-wsdd-github-notoc.html
---

<!--
* TOC
{:toc}
  -->


# **Glossary**{: style="color: crimson"}
   
Term | Definition
:-----| :--------
Consumers| In this document, “Consumers” refer to any systems that need to obtain weather data from SOS and connect via a web service interface.
Service|The IT realization of some self-contained business functionality. An implementation – independent reusable operational function that may be discovered as self-describing interfaces, and invoked using open standard protocols across networks. 
Service Discovery | The processes through which a service consumer may search for and find services, (generally done by providing criteria to search for against a corpus of service metadata which service providers have provided to describe their services).
Service Oriented  Architecture (SOA) | A paradigm for organizing and utilizing distributed capabilities of services to clients that may be under the control of different ownership domains.  SOA provides a uniform means to offer, discover, interact with and use capabilities to produce desired effects consistent with measurable preconditions and expectations
Service Registration | The registering process for the agreed service.
Service Registry | An enabling infrastructure service that uses a formal registration process to store, catalog, and manage metadata relevant to the services. A registry supports the search, identification, and understanding of resources, as well as query capabilities.
Stateful Dialogues | Dialogues that have “state” information between participating server and consumer agents to invoke requests and responses.
Subscribe|To request data via the Broker from a publisher on a particular subject or topic.
Taxonomy | A collection of controlled vocabulary terms organized into a hierarchical structure or categorization. Each term in taxonomy is in one or more parent-child relationships to other terms in the taxonomy.
Observation | A value measured at given time instant (e.g. value: 0.2, time: 08-11-2012 12:12), and represented according to the O&M standard data model.
Procedure | A process that indicates who provide the observations. For SOS this is generally the sensor, but may also be a generic process that leads to some observations and is represented as SensorML standard data model.
Observed Property | A physical phenomenon that is observed (e.g. phenomenon: water temperature), and is represented with a Uniform Resource Identifier (URI) composed by colon separated text according to the `<om:observedProperty>` element of the O&M standard.
Feature of Interest | A feature that relates to the observations, and represented according to the `<om:featureOfInterest>` element of the O&M standard. For in-situ observation, the feature of interest is the instrument (sensor) location, while for remote observation it is the location of the target.
Offering | A collection of sensors used to conveniently group them up (e.g. network:all, network:all-temperature, sensor:watertemp, etc.) and is represented as `<sos:ObservationOffering>` element of the SOS standard.


# **Acronyms and Abbreviations**{: style="color: crimson"}

Acronym|Definition
 :----- |:-----
ADCP|Acoustic Doppler Current Profiler
ANSI|American National Standards Institute
ASCII|American Standard Code for Information Interchange
BBOX|Bounding Box
CF|Climate and Forecast
CO-OPS|Center for Operational Oceanographic Products and Services
CRS|Coordinate Reference System
CSV|Comma-Separated Values
DCP|Distributed Computing Platform
DMAC|Data Management and Communication
DQA|Data Quality Assurance or Data Quality Assessment
ENU|East, North, Up directions
EPSG|European Petroleum Survey Group
EQC|Equivalent Quality Control or Environmental Quality Commission 
GEOSS|Global Earth Observation System of Systems
GML|Geography Markup Language
GMT|Greenwich Mean Time
GPS|Global Positioning System
HTML|HyperText Markup Language
HTTP|HyperText Transfer Protocol
HTTPS|HyperText Transfer Protocol Secure
ID|Identifyer
IGLD|International Great Lakes Datum
INCITS|InterNational Committee for Information Technology Standards
IOOS|Integrated Ocean Observing System
IP|Internet Protocol
ISO|International Organization for Standardization
IT|Information Technology
JSON|JavaScript Object Notation
KVP|Key-Value Pair
LF|Line Feed
LST|Local Sidereal Time
MHHW|Mean Higher High Water
MMI|Marine Metadata Interoperability
MSL|Mean Sea Level
NAVD|North American Vertical Datum
NDBC|National Data Buoy Center
NetCDF|Network Common Data Format
NOAA|National Oceanic and Atmospheric Administration
NODC|National Oceanographic Data Center
NWS|National Weather Service
OASIS|Organization for the Advancement of Structured Information Standards
OGC|Open Geospatial Consortium
OM|Observations and Measurements
OMO|One-Minute Observation
PNW|Pacific Northwest
PSU|Pressure Switch Unit
QA|Quality Assurance
QARTOD|Quality Assurance of Real Time Ocean Data
QC|Quality Control
RA|Regional Assotiation
RDBMS|Relational Database Management System 
SOA|Service-Oriented Architecture
SOAP|Simple Object Access Protocol
SOS|Sensor Observation Service
SWE|Senesor Web Enablement
TBA|To be added
TBD|To be developed
TLS|Transport Layer Security
TR|Technical Report
TSV|Tab-Separated Values
UML|Unified Modeling Language
URI|Uniform Resource Identifyer
URL|Uniform Resource Locator
URN|Uniform Resource Name
US|United States
USA|United States of America
UTC|Coordinated Universal Time
WAN|Wide Access Network
WARP|Weather and Radar Processor
WCS|Web Coverage Service
WFS|Web Feature Service
WGS|World Geodetic System
WMO|World Meteorological Organization
WMS|Web Map Service
WSDD|Web Service Description Document
WSDL|Web Service Description Language
WSN|Web Services Notification
WSRD|Web Service Requirements Document
XML|eXtensible Markup Language



# **Applicable Documents**{: style="color: crimson"}

| #  | Name and Location  |
| :---: | :--- |
| 1 | OpenGIS Geography Markup Language (GML) Encoding Standard Version 3.1, Open Geospatial Consortium (OGC), February 2004. [http://www.opengeospatial.org/standards/gml](http://www.opengeospatial.org/standards/gml) |
| 2 | OpenGIS Sensor Model Language (SensorML) Implementation Specification Version 1.0.0, Open Geospatial Consortium (OGC), July 2007 [http://www.opengeospatial.org/standards/sensorml](http://www.opengeospatial.org/standards/sensorml) |
| 3 | OpenGIS Filter Encoding 2.0 Encoding Standard Version 2.0.0, Open Geospatial Consortium, International Organization for Standards (ISO) 19143:2010, November 2010. [http://www.opengeospatial.org/standards/filter](http://www.opengeospatial.org/standards/filter)|
| 4 | OpenGIS Geography Markup Language (GML) Encoding Standard Version 3.2.1, Open Geospatial Consortium (OGC), August 2007. [http://www.opengeospatial.org/standards/gml](http://www.opengeospatial.org/standards/gml) |
| 5 | OpenGIS Sensor Observation Service (SOS) Implementation Standard Version 1.0.0, Open Geospatial Consortium, October 2007, OGC 06-009r6. [http://www.opengeospatial.org/standards/sos](http://www.opengeospatial.org/standards/sos) |
| 6 | OpenGIS Sensor Observation Service (SOS) Implementation Standard Version 2.0, Open Geospatial Consortium, April 2012, OGC 12-006. [http://www.opengeospatial.org/standards/sos](http://www.opengeospatial.org/standards/sos) |
| 7 | OpenGIS Network Common Data Form (NetCDF) Core Encoding Standard Version 1.0, Open Geospatial Consortium, April 2011. [http://www.opengeospatial.org/standards/netcdf](http://www.opengeospatial.org/standards/netcdf) |
| 8 | OpenGIS Web Services Common Standard Version 2.0, Open Geospatial Consortium, April 2010. [http://www.opengeospatial.org/standards/common](http://www.opengeospatial.org/standards/common) |
| 9 | Web Services Description Language (WSDL) Version 1.1, W3C Note, March 2001 [http://www.w3.org/TR/wsdl](http://www.w3.org/TR/wsdl) |
| 10 | NetCDF Climate and Forecast (CF) Metadata Conventions Version 1.6, December 2011,  [http://cf-pcmdi.llnl.gov/documents](http://cf-pcmdi.llnl.gov/documents) |
| 11 | CF Conventions Standard Name Table, Version 25, July 2013,  [http://cf-pcmdi.llnl.gov/documents/cf-standard-names/standard-name-table/25/cf-standard-name-table.html](http://cf-pcmdi.llnl.gov/documents/cf-standard-names/standard-name-table/25/cf-standard-name-table.html) |
| 12 | NetCDF Feature Type Templates, National Oceanographic Data Center (NODC) [http://www.nodc.noaa.gov/data/formats/netcdf/#templatesexamples](http://www.nodc.noaa.gov/data/formats/netcdf/#templatesexamples) |
| 13 | OpenGIS SWE Common Data Model Encoding Standard Version 2.0.0, Open Geospatial Consortium (OGC), January 2011 [http://www.opengeospatial.org/standards/swecommon](http://www.opengeospatial.org/standards/swecommon) |

* * * * *