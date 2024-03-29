---
title: SWE Data Record Template - Multiple Stations / TimeSeries with QC
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: Deprecation Notice - This guidance was deprecated by IOOS on 2020-01-10 and is superceded by the IOOS Metadata Profile 1.2.  Please read the Deprecation Notice below for more information.  Original Summary - Template for a SWE Data Record's static and dynamic fields for multiple stations with multiple sensors including quality elements for some quantities
toc: false
#permalink: sos-wsdd-github-notoc.html
---

# **Deprecation Notice** 

**Notice:** This convention has been deprecated due to IOOS' transition from the OGC SOS/SWE suite of standards to [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap) for in situ data dissemination.  

All relevant guidance in this standard has been superceded as of the **2020-01-10** publication date of the [IOOS Metadata Profile 1.2](https://ioos.github.io/ioos-metadata/).  Please refer to the IOOS Metadata Profile for current guidance.

The information below is retained for historical reference purposes only.


```XML
<?xml version="1.0" encoding="UTF-8"?>
<!-- This template is an example of a SWE Data Record composed of static and dynamic fields for -->
<!-- multiple stations with multiple sensors including quality elements for some quantities. -->
<!--  -->
<!-- This template is almost identical to the SWE-Multisation-TimeSeries with the addition of some -->
<!-- quality elements. Quality flags for static and dynamic data are included for station1 sensor 1.-->
<!-- An example of NilValue is also provided for wind speed in station 1 sensor 1 -->
<!--  -->
<!-- Most any element may be static or dynamic, but the static fields must be encoded inline, while -->
<!-- The dyamic elements must be block encoded in the data array. -->
<!--  -->
<!-- Description of data -->
<!-- SWE DataRecord containing 3 Stations: -->
<!-- Station 1 has 2 sensors -->
<!-- Station 2 has 2 sensors -->
<!-- Station 3 has 1 sensors -->
<swe2:DataRecord
  xmlns:swe2="http://www.opengis.net/swe/2.0"
  xmlns:xlink="http://www.w3.org/1999/xlink"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.opengis.net/swe/2.0 http://schemas.opengis.net/sweCommon/2.0/swe.xsd"
  definition="http://mmisw.org/ont/ioos/swe_element_type/observationRecord">

  <!-- STATIC DATA -->
  <!-- This field "stations" contains static data for all stations and sensors in the response -->
  <!-- Static data is linked to dynamic data (sensor observation values) via an abbreviated, -->
  <!-- underscored sensor URN. For example, urn:ioos:sensor:wmo:41001:sensor1 becomes -->
  <!-- wmo_41001_sensor1 -->
  <!-- This abbreviated URN is used as the sensor's DataRecord id in the static block and the -->
  <!-- DataChoice item name in the dynamic block. Consequently it also appears in the dynamic -->
  <!-- swe:values encoding. And may thus be used as a look up for the metadata of a given row -->
  <!-- of the data block -->
  <!-- All fields in the static block must include inline values. -->
  <!-- All fields in the dynamic block must not include inline values. -->
  <swe2:field name="stations">
    <!-- IoosTech Convention: -->
    <!-- The data record containing the static data for each station shall be defined -->
    <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/stations">
      <!-- Static data for the first station, urn:ioos:station:wmo:41001 -->
      <!-- Required elements include for each station: stationID, platformLocation, sensors -->
      <swe2:field name="wmo_41001">
        <!-- IoosTech Convention: -->
        <!-- The data record containing the static data for a station shall be defined -->
        <swe2:DataRecord id="wmo_41001"
          definition="http://mmisw.org/ont/ioos/swe_element_type/station">
          <swe2:field name="stationID">
            <!-- IoosTech Convention: -->
            <!-- The text element containing the station id shall be defined -->
            <swe2:Text definition="http://mmisw.org/ont/ioos/definition/stationID">

              <swe2:quality>
                <!-- Optional element can contain any valid static quality element for this station -->
              </swe2:quality>

              <swe2:value>urn:ioos:station:wmo:41001</swe2:value>
            </swe2:Text>
          </swe2:field>
          <!-- The platformLocation may be defined here, statically, or specified in the dynamic -->
          <!-- section. In either case, all coordinates must be specified inline or block encoded. -->
          <!-- They encoding can not be split to save bandwidth in the response. -->
          <swe2:field name="platformLocation">
            <!-- Field: platformLocation; -->
            <!-- The location of the platform relative to WGS 84 (Horizontal) and Instantaneous Water Level (Vertical). -->
            <!-- Each sensor will specify a height relative to the platform location. If complete orientation and -->
            <!-- relative position are available for a sensor, SWE 2.0 clearly defines how to record it. Generally, -->
            <!-- for IOOS buoy instruments we believe just specifying the height is the appropriate solution. -->
            <swe2:Vector definition="http://www.opengis.net/def/property/OGC/0/PlatformLocation"
              referenceFrame="http://www.opengis.net/def/crs-compound?1=http://www.opengis.net/def/crs/EPSG/0/4326&amp;2=http://www.opengis.net/def/crs/EPSG/0/5829"
              localFrame="#wmo_41001_frame">
              <!-- Vector: -->
              <!-- The coordinate vector defining the station location in the specified reference frame. -->
              <!--  -->
              <!-- For floating, surface buoys a new compound coordinate reference system has been developed -->
              <!-- which combines the WGS84 for horizontal (GPS) latitude and longitude CRS with a vertical CRS -->
              <!-- which uses height in above the Instantanious Water Level as a datum. -->
              <!--  -->
              <!-- For a tide gauge or a station at a fixed location relative to the Geoid (MSL), the CRS should be: -->
              <!-- EPSG::4979 referenceFrame="http://www.opengis.net/def/crs/EPSG/0/4979" -->
              <!--  -->
              <!-- Each stations localFrame must be unique.  -->
              <swe2:coordinate name="latitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/latitude" axisID="Lat">
                  <swe2:uom code="deg" />
                  <swe2:value>32.382</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="longitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/longitude" axisID="Lon">
                  <swe2:uom code="deg" />
                  <swe2:value>-75.415</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="height">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height" axisID="Z">
                  <swe2:uom code="m" />
                  <swe2:value>0.5</swe2:value>
                  <!-- Zero height is at water level in the IOOS Buoy CRS. All sensors locations should be a height -->
                  <!-- (vertical upward) relative to this reference frame -->
                </swe2:Quantity>
              </swe2:coordinate>
            </swe2:Vector>
          </swe2:field>

          <!-- Static data for all sensors on this station -->
          <swe2:field name="sensors">
            <!-- IoosTech Convention: -->
            <!-- The data record containing the static data for each sensor shall be defined -->
            <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensors">
              <swe2:field name="wmo_41001_sensor1">
                <!-- IoosTech Convention: -->
                <!-- The data record containing the static data for a sensor shall be defined -->
                <!-- Reminder: the DataRecord id of a sensor in the static block matches the DataChoice item -->
                <!-- name in the dynamic block -->
                <swe2:DataRecord id="wmo_41001_sensor1"
                  definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sensorID">
                    <!-- Field: sensorID -->
                    <!-- The sensorID urn may use a meaningful "component" name (eg, "sbe16"); or, -->
                    <!-- if not available, a simple, constant string followed by an integer counter -->
                    <!-- such as "sensor1", "sensor2", "salt1", etc. -->
                    <!-- IoosTech Convention: -->
                    <!-- The text element containing the sensor id shall be defined -->
                    <swe2:Text definition="http://mmisw.org/ont/ioos/definition/sensorID">

                      <swe2:quality>
                        <!-- Optional element can contain any valid static quality element for this sensor -->
                      </swe2:quality>

                      <swe2:value>urn:ioos:sensor:wmo:41001:sensor1</swe2:value>
                    </swe2:Text>
                  </swe2:field>
                  <!-- Height is generally a static field so we demonstrate its use here. It can be -->
                  <!-- defined statically or dynamically. -->
                  <swe2:field name="height">
                    <!-- The location of the sensor relative to the platform  -->
                    <!-- We don't currently have enough information about orientation and relative position -->
                    <!-- of sensors on a platform to define a sensor reference frame, but it is certainly -->
                    <!-- possible to do if and when that is needed. -->
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                      axisID="Z"
                      referenceFrame="#wmo_41001_frame">
                      <swe2:uom code="m" />
                      <swe2:value>5</swe2:value>
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:field>

              <swe2:field name="wmo_41001_sensor2">
                <!-- IoosTech Convention: -->
                <!-- The data record containing the static data for a sensor shall be defined -->
                <!-- Reminder: the DataRecord id of a sensor in the static block matches the DataChoice item -->
                <!-- name in the dynamic block -->
                <swe2:DataRecord id="wmo_41001_sensor2"
                  definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sensorID">
                    <!-- IoosTech Convention: -->
                    <!-- The text element containing the sensor id shall be defined -->
                    <swe2:Text definition="http://mmisw.org/ont/ioos/definition/sensorID">

                      <swe2:quality>
                        <!-- Optional element can contain any valid static quality element for this sensor -->
                      </swe2:quality>

                      <swe2:value>urn:ioos:sensor:wmo:41001:sensor2</swe2:value>
                    </swe2:Text>
                  </swe2:field>
                  <swe2:field name="height">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                      axisID="Z"
                      referenceFrame="#wmo_41001_frame">
                      <swe2:uom code="m" />
                      <swe2:value>-2</swe2:value>
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:field>
            </swe2:DataRecord>
          </swe2:field>
        </swe2:DataRecord>
      </swe2:field>

      <!-- Station 2 static data -->
      <swe2:field name="wmo_41002">
        <!-- IoosTech Convention: -->
        <!-- The data record containing the static data for a station shall be defined -->
        <swe2:DataRecord id="wmo_41002"
          definition="http://mmisw.org/ont/ioos/swe_element_type/station">
          <swe2:field name="stationID">
            <!-- IoosTech Convention: -->
            <!-- The text element containing the station id shall be defined -->
            <swe2:Text definition="http://mmisw.org/ont/ioos/definition/stationID">
              <swe2:value>urn:ioos:station:wmo:41002</swe2:value>
            </swe2:Text>
          </swe2:field>

          <swe2:field name="platformLocation">
            <swe2:Vector definition="http://www.opengis.net/def/property/OGC/0/PlatformLocation"
              referenceFrame="http://www.opengis.net/def/crs-compound?1=http://www.opengis.net/def/crs/EPSG/0/4326&amp;2=http://www.opengis.net/def/crs/EPSG/0/5829"
              localFrame="#wmo_41002_frame">
              <swe2:coordinate name="latitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/latitude" axisID="Lat">
                  <swe2:uom code="deg" />
                  <swe2:value>32.5</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="longitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/longitude" axisID="Lon">
                  <swe2:uom code="deg" />
                  <swe2:value>-78.5</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="height">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height" axisID="Z">
                  <swe2:uom code="m" />
                  <swe2:value>0</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
            </swe2:Vector>
          </swe2:field>

          <swe2:field name="sensors">
            <!-- IoosTech Convention: -->
            <!-- The data record containing the static data for each sensor shall be defined -->
            <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensors">
              <swe2:field name="wmo_41002_sensor1">
                <!-- IoosTech Convention: -->
                <!-- The data record containing the static data for a sensor shall be defined -->
                <!-- Reminder: the DataRecord id of a sensor in the static block matches the DataChoice item -->
                <!-- name in the dynamic block -->
                <swe2:DataRecord id="wmo_41002_sensor1"
                  definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sensorID">
                    <!-- IoosTech Convention: -->
                    <!-- The text element containing the sensor id shall be defined -->
                    <swe2:Text definition="http://mmisw.org/ont/ioos/definition/sensorID">
                      <swe2:value>urn:ioos:sensor:wmo:41002:sensor1</swe2:value>
                    </swe2:Text>
                  </swe2:field>
                  <swe2:field name="height">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                      axisID="Z"
                      referenceFrame="#wmo_41002_frame">
                      <swe2:uom code="m" />
                      <swe2:value>3</swe2:value>
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:field>

              <swe2:field name="wmo_41002_sensor2">
                <!-- IoosTech Convention: -->
                <!-- The data record containing the static data for a sensor shall be defined -->
                <swe2:DataRecord id="wmo_41002_sensor2"
                  definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sensorID">
                    <!-- IoosTech Convention: -->
                    <!-- The text element containing the sensor id shall be defined -->
                    <swe2:Text definition="http://mmisw.org/ont/ioos/definition/sensorID">
                      <swe2:value>urn:ioos:sensor:wmo:41002:sensor2</swe2:value>
                    </swe2:Text>
                  </swe2:field>
                  <swe2:field name="height">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                      axisID="Z"
                      referenceFrame="#wmo_41002_frame">
                      <swe2:uom code="m" />
                      <swe2:value>-5</swe2:value>
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:field>
            </swe2:DataRecord>
          </swe2:field>
        </swe2:DataRecord>
      </swe2:field>

      <!-- Station 3 static data -->
      <swe2:field name="wmo_41003">
        <!-- IoosTech Convention: -->
        <!-- The data record containing the static data for a station shall be defined -->
        <swe2:DataRecord id="wmo_41003"
          definition="http://mmisw.org/ont/ioos/swe_element_type/station">
          <swe2:field name="stationID">
            <!-- IoosTech Convention: -->
            <!-- The text element containing the station id shall be defined -->
            <swe2:Text definition="http://mmisw.org/ont/ioos/definition/stationID">
              <swe2:value>urn:ioos:station:wmo:41003</swe2:value>
            </swe2:Text>
          </swe2:field>

          <swe2:field name="platformLocation">
            <swe2:Vector definition="http://www.opengis.net/def/property/OGC/0/PlatformLocation"
              referenceFrame="http://www.opengis.net/def/crs-compound?1=http://www.opengis.net/def/crs/EPSG/0/4326&amp;2=http://www.opengis.net/def/crs/EPSG/0/5829"
              localFrame="#wmo_41003_frame">
              <swe2:coordinate name="latitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/latitude" axisID="Lat">
                  <swe2:uom code="deg" />
                  <swe2:value>33.5</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="longitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/longitude" axisID="Lon">
                  <swe2:uom code="deg" />
                  <swe2:value>-79.5</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="height">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height" axisID="Z">
                  <swe2:uom code="m" />
                  <swe2:value>0</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
            </swe2:Vector>
          </swe2:field>
          <swe2:field name="sensors">
            <!-- IoosTech Convention: -->
            <!-- The data record containing the static data for each sensor shall be defined -->
            <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensors">
              <swe2:field name="wmo_41003_sensor1">
                <!-- IoosTech Convention: -->
                <!-- The data record containing the static data for a sensor shall be defined -->
                <!-- Reminder: the DataRecord id of a sensor in the static block matches the DataChoice item -->
                <!-- name in the dynamic block -->
                <swe2:DataRecord id="wmo_41003_sensor1"
                  definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sensorID">
                    <!-- IoosTech Convention: -->
                    <!-- The text element containing the sensor id shall be defined -->
                    <swe2:Text definition="http://mmisw.org/ont/ioos/definition/sensorID">
                      <swe2:value>urn:ioos:sensor:wmo:41003:sensor1</swe2:value>
                    </swe2:Text>
                  </swe2:field>
                  <swe2:field name="height">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                      axisID="Z"
                      referenceFrame="#wmo_41003_frame">
                      <swe2:uom code="m" />
                      <swe2:value>3</swe2:value>
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:field>
            </swe2:DataRecord>
          </swe2:field>
        </swe2:DataRecord>
      </swe2:field>
    </swe2:DataRecord>
  </swe2:field>

  <!-- DYNAMIC DATA (SENSOR OBSERVATIONS) -->
  <!-- All measurements made by sensors and any other dynamic data (e.g. location for mobile sensors) -->
  <!-- are encoded in a DataArray. Again, sensor field name in the static DataRecord above corresponds to -->
  <!-- DataChoice item name in the dynamic DataArray -->
  <swe2:field name="observationData">
    <!-- IoosTech Convention: -->
    <!-- The field containing the dynamic data from each sensor shall contain a DataArray defined as such-->
    <swe2:DataArray definition="http://mmisw.org/ont/ioos/swe_element_type/sensorObservationCollection">
      <!-- Count of records in swe:values -->
      <swe2:elementCount>
        <swe2:Count>
          <swe2:value>13</swe2:value>
        </swe2:Count>
      </swe2:elementCount>
      <!-- Definition of fields in the DataArray -->
      <swe2:elementType name="observations">
        <!-- IoosTech Convention: -->
        <!-- The data record containing the dynamic observation descriptors for each sensor shall be defined -->
        <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensorObservations">
          <!-- Time is included for all sensor so it is listed first and is outside of DataChoice. -->
          <!-- If time is defined differently for some sensors it could be moved inside the data -->
          <!-- but this is uncommon. -->
          <swe2:field name="time">
            <swe2:Time definition="http://www.opengis.net/def/property/OGC/0/SamplingTime">

              <!-- IoosTech Convention: -->
              <!-- This is an optional quality element used to express QC data that applies to an -->
              <!-- entire record. The definition of the Category element spcifies that it applies -->
              <!-- to the entire record, not to the time element. -->
              <swe2:quality>
                <swe2:Category definition="http://mmisw.org/ont/ioos/swe_element_type/recordQuality">
                  <swe2:constraint>
                    <swe2:AllowedTokens>
                      <swe2:value>a</swe2:value>
                      <swe2:value>b</swe2:value>
                      <swe2:value>c</swe2:value>
                    </swe2:AllowedTokens>
                  </swe2:constraint>
                </swe2:Category>
              </swe2:quality>

              <swe2:uom xlink:href="http://www.opengis.net/def/uom/ISO-8601/0/Gregorian" />
            </swe2:Time>
          </swe2:field>

          <!-- Since different observations are made by each sensor, DataChoice is used to select -->
          <!-- a sensor and the set of observation fields for each record from that sensor in the -->
          <!-- block encoded values of the data array. -->
          <swe2:field name="sensor">
            <!-- IoosTech Convention: -->
            <!-- The data array shall contain one field with a DataChoice defined as sensor records -->
            <swe2:DataChoice definition="http://mmisw.org/ont/ioos/swe_element_type/sensors">
              <!-- DataChoice for wmo 41001's sensor1 -->
              <!-- Dynamic sensor observations are linked to static data using the DataChoice -->
              <!-- item name: wmo_41001_sensor1 -->
              <swe2:item name="wmo_41001_sensor1">
                <!-- IoosTech Convention: -->
                <!-- The data record containing the dynamic observation descriptors for a sensor shall be defined -->
                <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <!-- wmo_41001_sensor1's observed properties -->
                  <swe2:field name="air_temperature">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/air_temperature">

                      <!-- The next 3 elements specify the quality of the Air Temperature field -->
                      <!-- using ndbc qc flags as an example.  -->
                      <swe2:quality>
                        <!-- NDBC EQC Quality -->
                        <!-- Data Descriptor only - value must be block encoded -->
                        <swe2:Category
                          definition="http://sdftest.ndbc.noaa.gov/sos/qcflags.shtml">
                          <swe2:label>EQC Flag</swe2:label>
                          <swe2:codeSpace
                            xlink:href="http://sdftest.ndbc.noaa.gov/sos/qcflags.shtml"/>
                          <!-- This is not a formal code space. Use it till something better is created.-->
                          <swe2:constraint>
                            <swe2:AllowedTokens id="ndbcEqcFlags">
                              <swe2:value>T</swe2:value>
                              <swe2:value>M</swe2:value>
                              <swe2:value>W</swe2:value>
                              <swe2:value>D</swe2:value>
                              <swe2:value>S</swe2:value>
                              <swe2:value>V</swe2:value>
                              <swe2:value>L</swe2:value>
                              <swe2:value>H</swe2:value>
                              <swe2:value>R</swe2:value>
                            </swe2:AllowedTokens>
                          </swe2:constraint>
                        </swe2:Category>
                      </swe2:quality>

                      <swe2:quality>
                        <!-- NDBC DQA Quality -->
                        <!-- Unfortuantly there is no way to specify an array quality elements inside the -->
                        <!-- quantity. To allow for upto 2 values, two quality fields must be defined. -->
                        <swe2:Category
                          definition="http://sdftest.ndbc.noaa.gov/sos/qcflags.shtml">
                          <swe2:label>DQA Flag 1</swe2:label>
                          <swe2:codeSpace
                            xlink:href="http://sdftest.ndbc.noaa.gov/sos/qcflags.shtml"/>
                          <!-- This is not a formal code space. Use it till something better is created.-->
                          <swe2:constraint>
                            <swe2:AllowedTokens id="ndbcDqaFlags">
                              <swe2:value>a</swe2:value>
                              <swe2:value>b</swe2:value>
                              <swe2:value>d</swe2:value>
                              <swe2:value>f</swe2:value>
                              <swe2:value>g</swe2:value>
                              <swe2:value>i</swe2:value>
                              <swe2:value>j</swe2:value>
                              <swe2:value>k</swe2:value>
                              <swe2:value>m</swe2:value>
                              <swe2:value>n</swe2:value>
                              <swe2:value>p</swe2:value>
                              <swe2:value>q</swe2:value>
                              <swe2:value>r</swe2:value>
                              <swe2:value>s</swe2:value>
                              <swe2:value>t</swe2:value>
                              <swe2:value>v</swe2:value>
                              <swe2:value>w</swe2:value>
                              <swe2:value>x</swe2:value>
                              <swe2:value>y</swe2:value>
                              <swe2:value>z</swe2:value>
                            </swe2:AllowedTokens>
                          </swe2:constraint>
                        </swe2:Category>
                      </swe2:quality>

                      <swe2:quality>
                        <!-- Second DQA element -->
                        <swe2:Category
                          definition="http://sdftest.ndbc.noaa.gov/sos/qcflags.shtml">
                          <swe2:label>DQA Flag 2</swe2:label>
                          <swe2:codeSpace
                            xlink:href="http://sdftest.ndbc.noaa.gov/sos/qcflags.shtml"/>
                          <!-- This is not a formal code space. Use it till something better is created.-->
                          <swe2:constraint xlink:href="#ndbcDqaFlags"/>
                          <!-- The second DQA element can reference the constraints defined in the first -->
                        </swe2:Category>
                      </swe2:quality>
                      <!-- End quality elements -->
                      <swe2:uom code="Celsius" />
                    </swe2:Quantity>
                  </swe2:field>

                  <swe2:field name="wind_speed">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/wind_speed">
                      <!-- Each field and quantity can reference the constraints defined above to  -->
                      <!-- define quality elements. -->
                      <swe2:quality>
                        <swe2:Category>
                          <swe2:label> DQA Flag 1</swe2:label>
                          <!-- Example of constraint by reference -->
                          <swe2:constraint xlink:href="#ndbcDqaFlags"/>
                        </swe2:Category>
                      </swe2:quality>

                      <swe2:nilValues>
                        <swe2:NilValues>
                          <swe2:nilValue reason="http://www.opengis.net/def/nil/OGC/0/BelowDetectionRange"> INF </swe2:nilValue>
                          <!-- nilValue for a quntity may be one of INF, -INF, NaN or any value (such as 5.28) -->
                          <!-- See SWE Common Data Moel OGC 08-094r1 section 8.1.14 NilValues Element for details -->
                          <!-- Use a defined reason where possible -->
                        </swe2:NilValues>
                      </swe2:nilValues>
                      <swe2:uom code="m/s" />
                    </swe2:Quantity>
                  </swe2:field>

                  <swe2:field name="wind_to_direction">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/wind_to_direction">
                      <swe2:uom code="degrees" />
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:item>

              <swe2:item name="wmo_41001_sensor2">
                <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sea_water_temperature">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature">
                      <swe2:uom code="Celsius" />
                    </swe2:Quantity>
                  </swe2:field>

                  <swe2:field name="dissolved_oxygen">
                    <swe2:Quantity definition="http://mmisw.org/ont/ioos/parameter/dissolved_oxygen">
                      <swe2:uom code="mg/L" />
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:item>

              <swe2:item name="wmo_41002_sensor1">
                <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="air_temperature">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/air_temperature">
                      <swe2:uom code="Celsius" />
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:item>

              <swe2:item name="wmo_41002_sensor2">
                <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="sea_water_temperature">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature">
                      <swe2:uom code="Celsius" />
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:item>

              <swe2:item name="wmo_41003_sensor1">
                <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="air_temperature">
                    <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/air_temperature">
                      <swe2:uom code="Celsius" />
                    </swe2:Quantity>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:item>

            </swe2:DataChoice>
          </swe2:field>
        </swe2:DataRecord>
      </swe2:elementType>

      <swe2:encoding>
        <!-- SWE encoding and data values -->
        <!-- IoosTech Convention: -->
        <!-- swe:encoding *must* be always specified exactly as described below, -->
        <!-- to avoid the need to have fully general parsers that interpret -->
        <!-- swe:TextEncoding. That is, parsers may hard-code this particular -->
        <!-- swe:TextEncoding specification. -->
        <!--  -->
        <!-- About DataChoice from SWE Common 2.0: -->
        <!-- 9.2.5	Rules for DataChoice -->
        <!-- A тАЬDataChoiceтАЭ is encoded with the text method by providing the name of the selected item -->
        <!-- before the item values themselves. The name used shall correspond to the тАЬnameтАЭ attribute -->
        <!-- of the тАЬitemтАЭ property element that describes the structure of the selected item. -->
        <!--  -->
        <!-- IoosTech Convention: -->
        <!-- The name encoded for by data choice must match both the static sensor field name -->
        <!-- as well as the name attribute of the data choice item in the dynamic data. -->
        <!--  -->
        <!-- This data stream interleaves different types of messages separated by the block separator -->
        <!-- character. The element type is a тАЬDataChoiceтАЭ which means that each block is composed of -->
        <!-- the item name, followed by values of the item. This example also demonstrates that items -->
        <!-- of a choice can be of different types and length. -->
        <swe2:TextEncoding
          decimalSeparator="."
          tokenSeparator=","
          blockSeparator="&#10;" />
      </swe2:encoding>
      <swe2:values>
        <!-- The first three records are from wmo_41001_sensor1 and contain quality values -->
        2009-05-23T00:00:00Z,a,wmo_41001_sensor1,15.4,T,a,r,2.0,m,280
        2009-05-23T01:00:00Z,b,wmo_41001_sensor1,15.8,M,j,j,1.8,m,121
        2009-05-23T02:00:00Z,c,wmo_41001_sensor1,15.6,M,,,1.0,m,142
        2009-05-23T00:00:00Z,a,wmo_41001_sensor2,5.6,8.0
        2009-05-23T01:00:00Z,b,wmo_41001_sensor2,5.8,8.2
        2009-05-23T02:00:00Z,c,wmo_41001_sensor2,5.7,8.5
        2009-05-23T00:00:00Z,a,wmo_41002_sensor1,16.2
        2009-05-23T01:00:00Z,b,wmo_41002_sensor1,16.4
        2009-05-23T02:00:00Z,c,wmo_41002_sensor1,16.5
        2009-05-23T00:00:00Z,a,wmo_41002_sensor2,6.1
        2009-05-23T01:00:00Z,b,wmo_41002_sensor2,6.3
        2009-05-23T02:00:00Z,c,wmo_41002_sensor2,6.5
        2009-05-23T01:00:00Z,a,wmo_41003_sensor1,15.8
      </swe2:values>
    </swe2:DataArray>
  </swe2:field>
</swe2:DataRecord>
```
