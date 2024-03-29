---
title: DescribeSensor Response Template - Station
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: Deprecation Notice - This guidance was deprecated by IOOS on 2020-01-10 and is superceded by the IOOS Metadata Profile 1.2.  Please read the Deprecation Notice below for more information.  Original Summary - Template for a generic (independent of feature type) SensorML DescribeSensor response for a single station
toc: false
#permalink: sos-wsdd-github-notoc.html
---

# **Deprecation Notice** 

**Notice:** This convention has been deprecated due to IOOS' transition from the OGC SOS/SWE suite of standards to [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap) for in situ data dissemination.  

All relevant guidance in this standard has been superceded as of the **2020-01-10** publication date of the [IOOS Metadata Profile 1.2](https://ioos.github.io/ioos-metadata/).  Please refer to the IOOS Metadata Profile for current guidance.

The information below is retained for historical reference purposes only.


```XML
<?xml version="1.0" encoding="UTF-8"?>
<!-- Template document for a generic (independant of feature type) Describe Sensor Station -->
<!--  -->
<!-- Since Milestone 1.0 really only addresses timeSeries and timeSeriesProfile, only station -->
<!-- is addressed here. -->
<!--  -->
<sml:SensorML
  xmlns:sml="http://www.opengis.net/sensorML/1.0.1"
  xmlns:gml="http://www.opengis.net/gml"
  xmlns:swe="http://www.opengis.net/swe/1.0.1"
  xmlns:xlink="http://www.w3.org/1999/xlink"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.opengis.net/sensorML/1.0.1 http://schemas.opengis.net/sensorML/1.0.1/sensorML.xsd"
  version="1.0.1">

  <!-- SERVICE VERSION METADATA -->
  <sml:capabilities name="ioosServiceMetadata">
    <swe:SimpleDataRecord>
      <swe:field name="ioosTemplateVersion">
        <swe:Text definition="http://code.google.com/p/ioostech/source/browse/#svn%2Ftrunk%2Ftemplates%2FMilestone1.0">
          <swe:value>1.0</swe:value>
        </swe:Text>
      </swe:field>
    </swe:SimpleDataRecord>
  </sml:capabilities>

  <sml:member>
    <sml:System>
      <gml:description>Observations at urn:ioos:station:wmo:41001 buoy station,
        150 NM East of Cape HATTERAS</gml:description>
      <gml:name>urn:ioos:station:wmo:41001</gml:name>

      <!-- ==================================================================== -->
      <!-- PLATFORM IDENTIFIERS                                                 -->
      <!-- ==================================================================== -->
      <sml:identification>
        <sml:IdentifierList>
          <!-- The 3 identifiers listed below are MANDATORY -->
          <sml:identifier name="stationID">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/stationID">
              <sml:value>urn:ioos:station:wmo:41001</sml:value>
            </sml:Term>
          </sml:identifier>
          <sml:identifier name="shortName">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/shortName">
              <sml:value>WMO 41001 Buoy, Cape Hatteras</sml:value>
            </sml:Term>
          </sml:identifier>
          <sml:identifier name="longName">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/longName">
              <sml:value>urn:ioos:station:wmo:41001 buoy station, 150 NM East of Cape HATTERAS</sml:value>
            </sml:Term>
          </sml:identifier>
          <!-- Optional WMO and/or NDBC/CMAN? ID -->
          <sml:identifier name="wmoID">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/wmoID">
              <sml:value>41001</sml:value>
            </sml:Term>
          </sml:identifier>
        </sml:IdentifierList>
      </sml:identification>

      <!-- ==================================================================== -->
      <!-- PLATFORM CLASSIFIERS                                                 -->
      <!-- Manditory classifiers for all platforms:                             -->
      <!--   platformType                                                       -->
      <!--   operatorSector                                                     -->
      <!--   publisher                                                          -->
      <!--   parentNetwork                                                      -->
      <!-- List as many as needed for the platform                              -->
      <!-- ==================================================================== -->
      <sml:classification>
        <sml:ClassifierList>
          <!-- At least one parent network must reference an IOOS codespace and list the RA Acronym -->
          <sml:classifier name="parentNetwork">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/parentNetwork">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/organization"/>
              <sml:value>NANOOS</sml:value>
            </sml:Term>
          </sml:classifier>
          <sml:classifier name="platformType">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/platformType">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/platform"/>
              <sml:value>buoy</sml:value>
            </sml:Term>
          </sml:classifier>
          <sml:classifier name="operatorSector">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/operatorSector">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/sector"/>
              <sml:value>academic</sml:value>
            </sml:Term>
          </sml:classifier>          
          <sml:classifier name="publisher">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/publisher">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/organization"/>
              <sml:value>NANOOS</sml:value>
            </sml:Term>
          </sml:classifier>
          <sml:classifier name="sponsor">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/sponsor">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/organization"/>
              <sml:value>ACE</sml:value>
            </sml:Term>
          </sml:classifier>
        </sml:ClassifierList>
      </sml:classification>

      <!-- sml:validTime represents the date range of the validity of this document -->
      <sml:capabilities name="observationTimeRange">
        <swe:DataRecord>
          <swe:field name="observationTimeRange">
            <swe:TimeRange definition="http://mmisw.org/ont/ioos/swe_element_type/observationTimeRange">
              <swe:value>2008-04-28T08:00:00.000Z 2012-12-27T19:00:00.000Z</swe:value>
            </swe:TimeRange>
          </swe:field>
        </swe:DataRecord>
      </sml:capabilities>     


      <!-- =============================================================== -->
      <!-- CAPABILITIES                                                    -->
      <!-- It is mandatory to list the networks to with this station       -->
      <!-- belongs. DescribeSensor Sensor will list the parent station.    -->
      <!-- =============================================================== -->
      <sml:capabilities name="networkProcedures">
        <swe:SimpleDataRecord>
          <swe:field name="network1">
            <swe:Text definition="http://mmsiw.org/ont/ioos/definition/networkID">
              <swe:value>urn:ioos:network:nanoos:all</swe:value>
            </swe:Text>
          </swe:field>
          <swe:field name="network2">
            <swe:Text definition="http://mmsiw.org/ont/ioos/definition/networkID">
              <swe:value>urn:ioos:network:nanoos:network1</swe:value>
            </swe:Text>
          </swe:field>
          <swe:field name="network3">
            <swe:Text definition="http://mmsiw.org/ont/ioos/definition/networkID">
              <swe:value>urn:ioos:network:nanoos:network2</swe:value>
            </swe:Text>
          </swe:field>
        </swe:SimpleDataRecord>
      </sml:capabilities>

      <!-- =============================================================== -->
      <!-- CONTACTS                                                        -->
      <!-- List all publisher and operator contacts that apply to this     -->
      <!-- platform                                                        -->
      <!-- Mandatory contacts for all platforms:                           -->
      <!--   operator                                                      -->
      <!--   publisher                                                     -->
      <!-- Consider using xlink:href to external document for concision    -->
      <!-- =============================================================== -->
      <sml:contact>
        <sml:ContactList>
          <sml:member xlink:role="http://mmisw.org/ont/ioos/definition/operator">
            <sml:ResponsibleParty>
              <sml:organizationName>PNW Buoys</sml:organizationName>
              <sml:contactInfo>
                <sml:address>
                  <sml:deliveryPoint>1007 Balch Blvd.</sml:deliveryPoint>
                  <!-- Optional: City; but strongly encouraged  -->
                  <sml:city>Fremont</sml:city>
                  <sml:administrativeArea>WA</sml:administrativeArea>
                  <sml:postalCode>98195</sml:postalCode>
                  <!-- Required: country [Values: USA|(COUNTRY NAME)|NON-USA] -->
                  <sml:country>USA</sml:country>
                  <!-- Required: electronicMailAddress -->
                  <sml:electronicMailAddress>contact@buoys.com</sml:electronicMailAddress>
                </sml:address>
                <!-- Optional: onlineResource; but strongly encouraged for operator -->
                <sml:onlineResource xlink:href="http://pnw.buoyoperator.org"/>
              </sml:contactInfo>
            </sml:ResponsibleParty>
          </sml:member>
          <sml:member xlink:role="http://mmisw.org/ont/ioos/definition/publisher">
            <sml:ResponsibleParty>
              <sml:organizationName>NANOOS</sml:organizationName>
              <sml:contactInfo>
                <sml:address>
                  <sml:country>USA</sml:country>
                  <sml:electronicMailAddress>mayorga@apl.washington.edu</sml:electronicMailAddress>
                </sml:address>
                <sml:onlineResource xlink:href="http://nanoos.org"/>
              </sml:contactInfo>
            </sml:ResponsibleParty>
          </sml:member>
        </sml:ContactList>
      </sml:contact>

      <!-- =============================================================== -->
      <!-- DOCUMENTATION (Optional: experimental in Milestone1.0)          -->
      <!-- External resources for human consumption about this platform    -->
      <!-- and the observation data it produces                            -->
      <!-- =============================================================== -->
      <sml:documentation>
        <sml:DocumentList>
          <sml:member name="qc" xlink:arcrole="qualityControlDocument">
            <sml:Document>
              <gml:description>Handbook of Automated Data Quality Control Checks and Procedures, National Data Buoy Center, August 2009</gml:description>
              <sml:format>pdf</sml:format>
              <sml:onlineResource xlink:href="http://www.ndbc.noaa.gov/NDBCHandbookofAutomatedDataQualityControl2009.pdf"/>
            </sml:Document>
          </sml:member>
          <sml:member name="wp1" xlink:arcrole="urn:ogc:def:role:webPage">
            <sml:Document>
              <gml:description>Station web page from provider</gml:description>
              <sml:format>text/html</sml:format>
              <sml:onlineResource xlink:href="STATION_WEBPAGE"/>
            </sml:Document>
          </sml:member>
          <sml:member name="wp2" xlink:arcrole="urn:ogc:def:role:webPage">
            <sml:Document>
              <gml:description>Station web page from operator</gml:description>
              <sml:format>text/html</sml:format>
              <sml:onlineResource xlink:href="STATION_WEBPAGE"/>
            </sml:Document>            
          </sml:member>
        </sml:DocumentList>
      </sml:documentation>

      <!-- =============================================================== -->
      <!-- HISTORY (Optional: experimental in Milestone1.0)                -->
      <!-- Events and status changes of the platform such as deployment    -->
      <!-- and recovery                                                    -->
      <!-- =============================================================== -->
      <sml:history>
        <sml:EventList>
          <sml:member name="deployment_start">
            <sml:Event>
              <sml:date>2010-01-12</sml:date>
              <gml:description>Deployment start event</gml:description>
              <sml:documentation xlink:href="http://sdftest.ndbc.noaa.gov/sos/server.php?service=SOS&amp;request=DescribeSensor&amp;version=1.0.0&amp;outputformat=text/xml;subtype=&quot;sensorML/1.0.1&quot;&amp;procedure=urn:ioos:station:wmo:41001:20100112"/>
            </sml:Event>
          </sml:member>
          <sml:member name="deployment_stop">
            <sml:Event>
              <sml:date>2011-02-06</sml:date>
              <gml:description>Deployment stop event</gml:description>
              <sml:documentation xlink:href="http://sdftest.ndbc.noaa.gov/sos/server.php?service=SOS&amp;request=DescribeSensor&amp;version=1.0.0&amp;outputformat=text/xml;subtype=&quot;sensorML/1.0.1&quot;&amp;procedure=urn:ioos:station:wmo:41001:20100112"/>
            </sml:Event>
          </sml:member>
          <sml:member name="deployment_start">
            <sml:Event>
              <sml:date>2011-02-07</sml:date>
              <gml:description>Deployment start event</gml:description>
              <sml:documentation xlink:href="http://sdftest.ndbc.noaa.gov/sos/server.php?service=SOS&amp;request=DescribeSensor&amp;version=1.0.0&amp;outputformat=text/xml;subtype=&quot;sensorML/1.0.1&quot;&amp;procedure=urn:ioos:station:wmo:41001:20110207"/>
            </sml:Event>
          </sml:member>
        </sml:EventList>
      </sml:history>

      <!-- =============================================================== -->
      <!-- LOCATION                                                        -->
      <!-- Station geographic location (lat & lon only, no z)              -->
      <!-- Always use epsg 4326.                                           -->
      <!-- For moving platforms use gml:LineString                         -->
      <!-- =============================================================== -->
      <sml:location>
        <gml:Point srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
        <gml:pos>34.7 -72.73</gml:pos>
        </gml:Point>
      </sml:location>

      <!-- =============================================================== -->
      <!-- COMPONENTS                                                      -->
      <!-- List all component platforms in the network offering            -->
      <!-- Manditory Elements:                                             -->
      <!--   description    - describe the instrument/sensor               -->
      <!--   identification - the names by with the platform is called     -->
      <!--   documentation  - reference to docuemtation about the sensor   -->
      <!--   outputs        - the quantities observed by this platform     -->
      <!-- *location may be large but useful for platforms which move      -->
      <!-- =============================================================== -->
      <sml:components>
        <sml:ComponentList>
          <!-- name should be a human readable label -->
          <sml:component name="WatertempSensor1">
            <sml:System >
              <!-- Description is strongly suggested, but if it will not be useful omit it. -->
              <gml:description>Surface water temperature sensor on WMO platform 41001</gml:description>
              <sml:identification xlink:href="urn:ioos:sensor:wmo:41001:watertemp1"/>
              <sml:documentation xlink:href="http://sdftest.ndbc.noaa.gov/sos/server.php?service=SOS&amp;request=DescribeSensor&amp;version=1.0.0&amp;outputformat=text/xml;subtype=&quot;sensorML/1.0.1&quot;&amp;procedure=urn:ioos:sensor:wmo:41001:watertemp1"/>
              <sml:outputs>
                <sml:OutputList>
                  <sml:output name="Water Temperature">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature">
                      <swe:uom code="degC" />
                    </swe:Quantity>
                  </sml:output>
                </sml:OutputList>
              </sml:outputs>
            </sml:System>
          </sml:component>
          <sml:component name="Sensor ct1">
            <sml:System gml:id="sensor-ct1">
              <gml:description/>
              <sml:identification xlink:href="urn:ioos:sensor:wmo:41001:ct1"/>
              <sml:documentation xlink:href="http://sdftest.ndbc.noaa.gov/sos/server.php?service=SOS&amp;request=DescribeSensor&amp;version=1.0.0&amp;outputformat=text/xml;subtype=&quot;sensorML/1.0.1&quot;&amp;procedure=urn:ioos:sensor:wmo:41001:ct1"/>
              <sml:outputs>
                <sml:OutputList>
                  <sml:output name="Water Temperature">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature">
                      <swe:uom code="degC" />
                    </swe:Quantity>
                  </sml:output>
                  <sml:output name="Salinity">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_salinity">
                      <swe:uom code="PSU" />
                    </swe:Quantity>
                  </sml:output>
                </sml:OutputList>
              </sml:outputs>
            </sml:System>
          </sml:component>
          <sml:component name="Sensor baro1">
            <sml:System>
              <gml:description/>
              <sml:identification xlink:href="urn:ioos:sensor:wmo:41001:baro1"/>
              <sml:documentation xlink:href="http://sdftest.ndbc.noaa.gov/sos/server.php?service=SOS&amp;request=DescribeSensor&amp;version=1.0.0&amp;outputformat=text/xml;subtype=&quot;sensorML/1.0.1&quot;&amp;procedure=urn:ioos:sensor:wmo:41001:baro1"/>
              <sml:outputs>
                <sml:OutputList>
                  <sml:output name="Barometric Pressure">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/air_pressure">
                      <swe:uom code="mb" />
                    </swe:Quantity>
                  </sml:output>
                </sml:OutputList>
              </sml:outputs>
            </sml:System>
          </sml:component>
          <sml:component name="Sensor airtemp1">
            <sml:System gml:id="sensor-airtemp1">
              <gml:description/>
              <sml:identification xlink:href="urn:ioos:sensor:wmo:41001:airtemp1"/>
              <sml:outputs>
                <sml:OutputList>
                  <sml:output name="Air Temperature">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/air_temperature">
                      <swe:uom code="degC" />
                    </swe:Quantity>
                  </sml:output>
                </sml:OutputList>
              </sml:outputs>
            </sml:System>
          </sml:component>
        </sml:ComponentList>
      </sml:components>
      <!-- ============================================================================= -->

    </sml:System>
  </sml:member>
</sml:SensorML>
```
