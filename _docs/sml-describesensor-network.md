---
title: DescribeSensor Response Template - Network
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: Deprecation Notice - This guidance was deprecated by IOOS on 2020-01-10 and is superceded by the IOOS Metadata Profile 1.2.  Please read the Deprecation Notice below for more information.  Original Summary - Template for a generic (independent of feature type) SensorML DescribeSensor response for Network of Stations
toc: false
#permalink: sos-wsdd-github-notoc.html
---

# **Deprecation Notice** 

**Notice:** This convention has been deprecated due to IOOS' transition from the OGC SOS/SWE suite of standards to [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap) for in situ data dissemination.  

All relevant guidance in this standard has been superceded as of the **2020-01-10** publication date of the [IOOS Metadata Profile 1.2](https://ioos.github.io/ioos-metadata/).  Please refer to the IOOS Metadata Profile for current guidance.

The information below is retained for historical reference purposes only.


```XML
<?xml version="1.0" encoding="UTF-8"?>
<!-- Template document for a generic (independant of feature type) Describe Sensor Network -->
<!-- Each member system in the template includes: -->
<!--    Name & Description -->
<!--    Temporal & Spatial Bounds -->
<!--    Identifiers -->
<!--    Classifiers -->
<!--    Contacts -->
<!--    Components -->
<!--  -->
<!-- The SML document is designed to present useful metadata about the sensor network -->
<!-- sufficient to determine which additional descriptions or observations are needed. -->
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
      <gml:description>Collection of all station assets available via the NANOOS SOS service</gml:description>
      <gml:name>urn:ioos:network:nanoos:all</gml:name>

      <!-- Spatial bounds of the content described by this network -->
      <gml:boundedBy>
          <gml:Envelope srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
              <gml:lowerCorner>32.7 -75.0</gml:lowerCorner>
              <gml:upperCorner>34.7 -72.0</gml:upperCorner>
          </gml:Envelope>
      </gml:boundedBy>

      <!-- =============================================================== -->
      <!-- IDENTIFIERS                                                     -->
      <!-- The networkID, shortName and longName are manditory             -->
      <!-- list all that are appropriate                                   -->
      <!-- =============================================================== -->
      <sml:identification>
        <sml:IdentifierList>
          <sml:identifier name="networkID">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/networkID">
              <sml:value>urn:ioos:network:nanoos:all</sml:value>
            </sml:Term>
          </sml:identifier>
          <sml:identifier name="shortName">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/shortName">
              <sml:value>NANOOS SOS station assets collection</sml:value>
            </sml:Term>
          </sml:identifier>
          <sml:identifier name="longName">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/longName">
              <sml:value>Collection of all station assets available via the NANOOS SOS service</sml:value>
            </sml:Term>
          </sml:identifier>
        </sml:IdentifierList>
      </sml:identification>

      <!-- =============================================================== -->
      <!-- CLASSIFIERS                                                     -->
      <!-- List any classifiers that apply to this network offering        -->
      <!-- =============================================================== -->
      <sml:classification>
        <sml:ClassifierList>
          <!-- List as many as needed to describe the content of the network offering -->   
          <sml:classifier name="publisher">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/publisher">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/organization"/>
              <sml:value>NANOOS</sml:value>
            </sml:Term>
          </sml:classifier>
          <!-- At least one parent network must reference an IOOS codespace and list the RA Acronym -->
          <sml:classifier name="parentNetwork">
            <sml:Term definition="http://mmisw.org/ont/ioos/definition/parentNetwork">
              <sml:codeSpace xlink:href="http://mmisw.org/ont/ioos/organization"/>
              <sml:value>NANOOS</sml:value>
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
      <!-- CONTACTS                                                        -->
      <!-- List all publisher and operator contacts that apply to this     -->
      <!-- network offering.                                               -->
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
                  <!-- Required: country [Values: USA|<COUNTRY NAME>|NON-USA] -->
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
      <!-- COMPONENTS                                                      -->
      <!-- List all component platforms in the network offering            -->
      <!-- Manditory Elements:                                             -->
      <!--   identification - the names by with the platform is called     -->
      <!--   capabilities   - observation time range                       -->
      <!--   location*      - the location of the platform                 -->
      <!--   outputs        - the quantities observed by this platform     -->
      <!-- *location may be large but useful for platforms which move      -->
      <!-- =============================================================== -->
      <sml:components>
        <sml:ComponentList>          
          <sml:component name='wmo_41001'>
            <sml:System>
            <!-- Include name & description only if they have some useful human readable purpose -->

              <!-- ==================================================================== -->
              <!-- PLATFORM IDENTIFIERS                                                 -->
              <!-- Gives ability to platforms by name                                   -->
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
                </sml:IdentifierList>
              </sml:identification>

              <!-- Time range for this platform -->
              <sml:capabilities name="observationTimeRange">
                <swe:DataRecord>
                  <swe:field name="observationTimeRange">
                    <swe:TimeRange definition="http://mmisw.org/ont/ioos/swe_element_type/observationTimeRange">
                      <swe:value>2006-02-12T00:00:00.000Z 2013-04-21T00:00:00.000Z</swe:value>
                    </swe:TimeRange>
                  </swe:field>
                </swe:DataRecord>
              </sml:capabilities>


              <!-- =============================================================== -->
              <!-- LOCATION                                                        -->
              <!-- Station geographic location (lat & lon only, no z)              -->
              <!-- Always use epsg 4326.                                           -->
              <!-- For moving platforms use <gml:LineString>                       -->
              <!-- =============================================================== -->
              <sml:location>
                <gml:Point srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
                  <gml:pos>34.7 -72.73</gml:pos>
                </gml:Point>
              </sml:location>


              <!-- =============================================================== -->
              <!-- OUTPUTS                                                         -->
              <!-- A list of the quantities observed by this platform              -->
              <!-- =============================================================== -->
              <sml:outputs>
                <sml:OutputList>
                  <sml:output name="Sea Water Temperature">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature"/>
                  </sml:output>
                  <sml:output name="Dissolved Oxygen">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/dissolved_oxygen"/>
                  </sml:output>
                </sml:OutputList>
              </sml:outputs>

            </sml:System>
          </sml:component>

          <!-- Compact form -->
          <sml:component name='wmo_41002'>
            <sml:System>
              <sml:identification>
                <sml:IdentifierList>
                  <!-- The 2 identifiers listed below are MANDATORY -->
                  <sml:identifier name="stationID">
                    <sml:Term definition="http://mmisw.org/ont/ioos/definition/stationID">
                      <sml:value>urn:ioos:station:wmo:41002</sml:value>
                    </sml:Term>
                  </sml:identifier>
                  <sml:identifier name="shortName">
                    <sml:Term definition="http://mmisw.org/ont/ioos/definition/shortName">
                      <sml:value>WMO 41002 Buoy, Cape Hatteras</sml:value>
                    </sml:Term>
                  </sml:identifier>
                </sml:IdentifierList>
              </sml:identification>

              <sml:capabilities name="observationTimeRange">
                <swe:DataRecord>
                  <swe:field name="observationTimeRange">
                    <swe:TimeRange definition="http://mmisw.org/ont/ioos/swe_element_type/observationTimeRange">
                      <swe:value>2006-02-12T00:00:00.000Z 2013-04-21T00:00:00.000Z</swe:value>
                    </swe:TimeRange>
                  </swe:field>
                </swe:DataRecord>
              </sml:capabilities>

              <sml:location>
                <gml:Point srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
                  <gml:pos>34.7 -72.73</gml:pos>
                </gml:Point>
              </sml:location>

              <sml:outputs>
                <sml:OutputList>
                  <sml:output name="Sea Water Temperature">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature"/>
                  </sml:output>
                  <sml:output name="Dissolved Oxygen">
                    <swe:Quantity definition="http://mmisw.org/ont/cf/parameter/dissolved_oxygen"/>
                  </sml:output>
                </sml:OutputList>
              </sml:outputs>
            </sml:System>
          </sml:component>

        </sml:ComponentList>

      </sml:components>

    </sml:System>
  </sml:member>
  <!-- No additional members are expected because SOS DescribeSensor only allows a request for a single procedure-->
</sml:SensorML>
```
