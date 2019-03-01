---
title: Introduction to Guidelines for IOOS SOS 1.0
keywords: sample homepage
tags: [getting_started]
toc: false
#permalink: index.html
summary: This brief description summarizes the content of the Guidelines. The other topics on this site provide additional information and detail about working with all aspects of the IOOS SOS 1.0.
---

## **IOOS SOS Application Profile**

U.S. IOOS distributes ocean observations using the OGC Sensor Observation Service. To support this effort U.S. IOOS has developed a profile of SOS v1.0 (henceforth IOOS SOS v1.0) that includes specific behaviors for the SOS interface and for the output formats delivered in response to the three operations of the SOS Core Profile.
The GitHub repository contains documentation of the IOOS SOS v1.0 profile, example templates for the responses, and information on two reference implementations developed to support the IOOS SOS v1.0 profile. To facilitate the practical implementation of the SOS, IOOS has developed the IOOS Application Profile (AP) for SOS, which includes a series of operation templates, controlled vocabularies, IOOS Conventions for SOS Implementation, and a set of tests for IOOS SOS implementations.

### [**IOOS SOS 1.0 WSDD**{: style="color: crimson"}](./sos-wsdd-1-0.html)

The Web Service Description Document (WSDD) provides a description of a Sensor Observation Service (SOS) that has been developed by U.S. IOOS for deployment by NOAA data providers and IOOS Regional Associations (RAs). This service provides a service consumer with the capability to access ocean observations data products, such as time series and profiles, which have XML-based encodings and included in the SWE Common Data Model.

### **IOOS SOS 1.0 Templates**

 * [**GetCapabilities**{: style="color: black"}](./sos-getcapabilities.html): A template for generic (independent of feature type) GetCapabilities response.
 * [**DescribeSensor-Network**{: style="color: black"}](./sml-describesensor-network.html): A template for generic (independent of feature type) SensorML DescribeSensor response (network of stations)
 * [**DescribeSensor-Station**{: style="color: black"}](./sml-describesensor-station.html): A template for generic (independent of feature type) SensorML DescribeSensor response (single station)
 * [**OM GetObservation**{: style="color: black"}](./om-getobservation.html): A template for a generic (independent of feature type) GetObservation response (the result block in this template is empty; see SWE templates for guidance on the result block)
* [**SWE Data Record - Single Station / TimeSeries**{: style="color: black"}](./swe-singlestation-singleproperty-timeseries.html): A template for SWE Data Record’s static and dynamic fields (single station with a single sensor)
 * [**SWE Data Record - Single Station / TimeSeriesProfile**{: style="color: black"}](./swe-singlestation-timeseriesprofile.html): A template for SWE Data Record’s static and dynamic fields (a station with profiling sensors)
 * [**SWE Data Record Template - Single Station / TimeSeriesProfile with QC**{: style="color: black"}](./swe-singlestation-timeseriesprofile-qc.html): A template for SWE Data Record’s static and dynamic fields (a station with profiling sensors including quality elements for some quantities)
 * [**SWE Data Record Template - Multiple Stations / TimeSeries**{: style="color: black"}](./swe-multistation-timeseries.html): A template for SWE Data Record’s static and dynamic fields (multiple stations with a variety of sensors)
 * [**SWE Data Record Template - Multiple Stations / TimeSeries with QC**{: style="color: black"}](./swe-multistation-timeseries-qc.html): A template for SWE Data Record’s static and dynamic fields (multiple stations with a variety of sensors including quality elements for some quantities)

### [**IOOS SOS 1.0 Compliance and Interoperability Tests**{: style="color: crimson"}](./sos-test-list-summary.html)

This document describes a collection of tests that have to be run in order to ensure a required level of compliance with IOOS SOS Profile 1.0 (IOOS Convention), and official OGC SOS 1.0.0 specification.
