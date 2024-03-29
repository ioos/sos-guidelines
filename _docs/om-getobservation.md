---
title: GetObservation Response Template
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: Deprecation Notice - This guidance was deprecated by IOOS on 2020-01-10 and is superceded by the IOOS Metadata Profile 1.2.  Please read the Deprecation Notice below for more information.  Original Summary - Template for a generic (independent of feature type) GetObservation response.
toc: false
#permalink: sos-wsdd-github-notoc.html
---

# **Deprecation Notice** 

**Notice:** This convention has been deprecated due to IOOS' transition from the OGC SOS/SWE suite of standards to [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap) for in situ data dissemination.  

All relevant guidance in this standard has been superceded as of the **2020-01-10** publication date of the [IOOS Metadata Profile 1.2](https://ioos.github.io/ioos-metadata/).  Please refer to the IOOS Metadata Profile for current guidance.

The information below is retained for historical reference purposes only.

> **NOTE: This is a generic template with empty result block; for details, see specific Result Block templates.**


```XML
<?xml version="1.0" encoding="UTF-8"?>
<!-- Template Document for a generic (independent of feature type) Get Observation. -->
<!-- Specific feature types are referenced for example only. -->
<!--  -->
<!-- The GO contains one member observation per feature type in the response.  -->
<!-- The result block in the template is empty. Examples of the result block are in the SWE -->
<!-- templates defined seperately for each strucutre and concept. Any of these SWE results could -->
<!-- be expressed in the result block of this document with the appropriate matching metadata. -->
<!--  -->
<om:ObservationCollection
  xmlns:om="http://www.opengis.net/om/1.0"
  xmlns:gml="http://www.opengis.net/gml"
  xmlns:swe="http://www.opengis.net/swe/1.0.1"
  xmlns:swe2="http://www.opengis.net/swe/2.0"
  xmlns:xlink="http://www.w3.org/1999/xlink"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.opengis.net/om/1.0 http://schemas.opengis.net/om/1.0.0/om.xsd">

  <!-- DISCLAIMER (optional) -->
  <gml:metaDataProperty xlink:title="disclaimer">
    <gml:GenericMetaData>
      <gml:description>DISCLAIMER</gml:description>
    </gml:GenericMetaData>
  </gml:metaDataProperty>

  <!-- IOOS SOS VERSION (optional) -->
  <gml:metaDataProperty
    xlink:title="ioosTemplateVersion"
    xlink:href="http://code.google.com/p/ioostech/source/browse/#svn%2Ftrunk%2Ftemplates%2FMilestone1.0">
    <gml:version>1.0</gml:version>
  </gml:metaDataProperty>

  <!-- =========================================================== -->
  <!-- A GO response will contain at least one member observation. -->
  <!-- Multiple stations and multiple sensors of the same feature  -->
  <!-- type may be expressed in a single observation result block. -->
  <!--  -->
  <!-- Separate member observations are used when the response     -->
  <!-- contains more than one feature type. Each feature type is   -->
  <!-- returned in a separate member observation.                  -->
  <!-- =========================================================== -->
  <om:member>
    <om:Observation>

      <!-- =========================================================== -->
      <!-- gml:description                                             -->
      <!-- Intended as fairly free-form text for human eyeballs.       -->
      <!-- Should include station(s) name and location as well as      -->
      <!-- sensor or procedure information if possible                 -->
      <!-- =========================================================== -->
      <gml:description>
        Observations at point station urn:ioos:station:wmo:41001, 150 NM East of Cape
        HATTERAS. Observations at point station urn:ioos:station:wmo:41002, S HATTERAS
        - 250 NM East of Charleston, SC
      </gml:description>

      <!-- =========================================================== -->
      <!-- samplingTime                                                -->
      <!-- Time bounds of response data, encoded as an iso8601 string  -->
      <!-- or using a GML attribute expressions (e.g. 'now').          -->
      <!-- Currently only UTC (Z) is supported/advocated.              -->
      <!-- =========================================================== -->
      <om:samplingTime>
        <gml:TimePeriod>
          <gml:beginPosition>2009-05-23T00:00:00Z</gml:beginPosition>
          <gml:endPosition>2009-05-23T02:00:00Z</gml:endPosition>
        </gml:TimePeriod>
      </om:samplingTime>

      <!-- =========================================================== -->
      <!-- procedure                                                   -->
      <!-- Each station is listed as a process member                  -->
      <!-- =========================================================== -->
      <om:procedure>
        <om:Process>
          <gml:member xlink:href="urn:ioos:station:wmo:41001" />
          <gml:member xlink:href="urn:ioos:station:wmo:41002" />
        </om:Process>
      </om:procedure>

      <!-- =========================================================== -->
      <!-- observedProperty                                            -->
      <!-- This block contains a list of *scalar* properties only,     -->
      <!-- referencing the MMI CF or IOOS parameter vocabularies; see  -->
      <!-- the wiki documentation on the topic for the choice of       -->
      <!-- vocabularies. Requests constructed using composite (vector) -->
      <!-- phenomena such as "winds" will return the scalar components -->
      <!-- only.This scheme accommodates both true composite phenomena -->
      <!-- like winds, and ad-hoc requests for multiple properties     -->
      <!-- (eg, water and air temperature). The general                -->
      <!-- swe:CompositePhenomenon element is used even when the       -->
      <!-- response returns a single observed property.                -->
      <!-- =========================================================== -->
      <om:observedProperty>
        <swe:CompositePhenomenon dimension="5"
          gml:id="observedproperties1">
          <gml:name>Response Observed Properties</gml:name>
          <swe:component xlink:href="http://mmisw.org/ont/cf/parameter/air_temperature" />
          <swe:component xlink:href="http://mmisw.org/ont/cf/parameter/wind_speed" />
          <swe:component xlink:href="http://mmisw.org/ont/cf/parameter/wind_direction" />
          <swe:component xlink:href="http://mmisw.org/ont/cf/parameter/sea_water_temperature" />
          <swe:component xlink:href="http://mmisw.org/ont/ioos/parameter/dissolved_oxygen" />
        </swe:CompositePhenomenon>
      </om:observedProperty>

      <!-- =========================================================== -->
      <!-- featureOfInterest                                           -->
      <!-- Encompasses all spatial and feature-type response metadata. -->
      <!-- =========================================================== -->
      <om:featureOfInterest>
        <gml:FeatureCollection>

          <!-- CF Feature Type (discrete-sampling-geometry). -->
          <gml:metaDataProperty>
            <gml:name codeSpace="http://cf-pcmdi.llnl.gov/documents/cf-conventions/1.6/cf-conventions.html#discrete-sampling-geometries">timeSeries</gml:name>
          </gml:metaDataProperty>

          <!-- Geographic (lat lon) Bounding Box of this feature -->
          <gml:boundedBy>
            <gml:Envelope srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
              <gml:lowerCorner>32.38 -75.42</gml:lowerCorner>
              <gml:upperCorner>34.7 -72.73</gml:upperCorner>
            </gml:Envelope>
          </gml:boundedBy>



          <!-- =========================================================== -->
          <!-- location                                                    -->
          <!-- Feature geographic location (lat & lon only, no z)          -->
          <!-- Always use epsg 4326.                                       -->
          <!-- This example includes one point for one station.            -->
          <!-- Several gml feature types are available to describe the     -->
          <!-- location of the data in the response. See the IoosTech wiki -->
          <!-- for documentation on what GML type to use for each IoosTech -->
          <!-- feature type.                                               -->
          <!-- =========================================================== -->
          <gml:location>
            <!-- For a station with timeSeries or timeSeriesProfile data   -->
            <!-- use gml:MultiPoint -->
            <gml:MultiPoint
              srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
              <gml:pointMembers>
                <!-- For each station in the result add an additional point -->
                <gml:Point>
                  <gml:name>urn:ioos:station:wmo:41001</gml:name>
                  <gml:pos>34.7 -72.73</gml:pos>
                </gml:Point>
                <gml:Point>
                <gml:name>urn:ioos:station:wmo:41002</gml:name>
                  <gml:pos>32.382 -75.415</gml:pos>
                </gml:Point>
              </gml:pointMembers>
            </gml:MultiPoint>
          </gml:location>
        </gml:FeatureCollection>
      </om:featureOfInterest>

      <!-- =========================================================== -->
      <!-- result                                                      -->
      <!-- (THE "DATA" BLOCK)                                          -->
      <!-- =========================================================== -->
      <om:result>
        <!-- This block contains a SWE Data Record conforming to the   -->
        <!-- appropriate result block template in Milestone 1.0.       -->
      </om:result>

    </om:Observation>
  </om:member>

  <om:member>
    <!-- A different feature type may be returned in this member -->
  </om:member>

</om:ObservationCollection>
```
