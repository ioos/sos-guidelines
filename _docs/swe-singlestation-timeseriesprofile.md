---
title: SWE Data Record Template - Single Station / TimeSeriesProfile
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: Deprecation Notice - This guidance was deprecated by IOOS on 2020-01-10 and is superceded by the IOOS Metadata Profile 1.2.  Please read the Deprecation Notice below for more information.  Original Summary - Template for a SWE Data Record's static and dynamic fields for a station with profiling sensors
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
<!-- multiple stations with multiple profiling sensors -->
<!--  -->
<!-- Most any element may be static or dynamic, but the static fields must be encoded inline, while -->
<!-- The dyamic elements must be block encoded in the data array. -->
<!--  -->
<!-- Description of data -->
<!-- SWE DataRecord containing 1 Station: -->
<!-- Station 1 has 2 sensors -->
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
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/latitude"
                  axisID="Lat">
                  <swe2:uom code="deg" />
                  <swe2:value>32.382</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="longitude">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/longitude"
                  axisID="Lon">
                  <swe2:uom code="deg" />
                  <swe2:value>-75.415</swe2:value>
                </swe2:Quantity>
              </swe2:coordinate>
              <swe2:coordinate name="height">
                <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                  axisID="Z">
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
                  <!-- An example of an acoustic doppler current profiler -->
                  <swe2:field name="sensorID">
                    <!-- Field: sensorID -->
                    <!-- The sensorID urn may use a meaningful "component" name (eg, "sbe16"); or, -->
                    <!-- if not available, a simple, constant string followed by an integer counter -->
                    <!-- such as "sensor1", "sensor2", "salt1", etc. -->
                    <!-- IoosTech Convention: -->
                    <!-- The text element containing the sensor id shall be defined -->
                    <swe2:Text definition="http://mmisw.org/ont/ioos/definition/sensorID">
                      <swe2:value>urn:ioos:sensor:wmo:41001:sensor1</swe2:value>
                    </swe2:Text>
                  </swe2:field>

                  <swe2:field name="sensorOrientation">
                    <!-- If available for an profiling sensor such as an ADCP, record the sensor -->
                    <!-- orientation as part of the static (or dyanmic) data. -->
                    <!-- Orientation could be for the profile or for each observation in the profile. -->
                    <swe2:Vector definition="http://www.opengis.net/def/property/OGC/0/SensorOrientation"
                      referenceFrame="http://www.opengis.net/def/crs/OGC/0/ENU">
                      <swe2:coordinate name="platform_orientation">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/platform_orientation"
                          axisID="Z">
                          <swe2:uom code="deg" />
                          <swe2:value>0</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                      <swe2:coordinate name="platform_pitch_angle">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/platform_pitch_angle"
                          axisID="X">
                          <swe2:uom code="deg" />
                          <swe2:value>90</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                      <swe2:coordinate name="platform_roll_angle">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/platform_roll_angle"
                          axisID="Y">
                          <swe2:uom code="deg" />
                          <swe2:value>0</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                    </swe2:Vector>
                  </swe2:field>

                  <swe2:field name="sensorLocation">
                    <!-- For a profiling sensor such as an ADCP it is best to specify its location relative -->
                    <!-- to a CRS rather than relative to the platform or buoy unless this relationship is -->
                    <!-- actually measured. It is likely that the relative measured location would be dynamic -->
                    <!-- changing with each observation. Where as an absolute lat,lon,Z may be -->
                    <!-- approximated as static. -->
                    <!-- Local frames should always be specified as #{short_asset_id}_frame, regardless of feature type -->
                    <swe2:Vector definition="http://www.opengis.net/def/property/OGC/0/SensorLocation"
                      referenceFrame="http://www.opengis.net/def/crs-compound?1=http://www.opengis.net/def/crs/EPSG/0/4326&amp;2=http://www.opengis.net/def/crs/EPSG/0/5829"
                      localFrame="#wmo_41001_sensor1_frame">
                      <swe2:coordinate name="latitude">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/latitude"
                          axisID="Lat">
                          <swe2:uom code="deg" />
                          <swe2:value>32.382</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                      <swe2:coordinate name="longitude">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/longitude"
                          axisID="Lon">
                          <swe2:uom code="deg" />
                          <swe2:value>-75.415</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                      <swe2:coordinate name="height">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                          axisID="Z">
                          <swe2:uom code="m" />
                          <swe2:value>0.0</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                    </swe2:Vector>
                  </swe2:field>

                  <swe2:field name="profileBins">
                    <!-- IoosTech Convention: -->
                    <!-- Static profile bins and depths shall be encoded as an defined array -->
                    <swe2:DataArray definition="http://mmisw.org/ont/ioos/swe_element_type/profileBins">
                      <swe2:description>Array of synchronous observation locations in a profile</swe2:description>
                      <swe2:elementCount>
                        <swe2:Count>
                          <swe2:value>5</swe2:value>
                          <!-- The number of bins defined should be greater than or equal to the -->
                          <!-- number of binned observations in the dynamic data for this sensor. -->
                          <!-- This would allow for ragged arrays of data from upward looking adcps. -->
                        </swe2:Count>
                      </swe2:elementCount>
                      <swe2:elementType name="profileBinDescription">
                        <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/profileBin">
                          <swe2:field name="binCenter">
                            <!-- IoosTech Convention: -->
                            <!-- binCenters shall be represented by a defined quantity -->
                            <!-- NOTE: sufficient to use height definition for bin center, since it's in a -->
                            <!--       profile_bin? Would be more consistent with normal profiles -->
                            <swe2:Quantity axisID="Z"
                              definition="http://mmisw.org/ont/cf/parameter/height"
                              referenceFrame="#wmo_41001_sensor1_frame">
                              <swe2:uom code="m" />
                            </swe2:Quantity>
                          </swe2:field>
                          <swe2:field name="binEdges">
                            <!-- IoosTech Convention: -->
                            <!-- binEdges shall be represented by a defined quantity -->
                            <swe2:QuantityRange axisID="Z"
                              definition="http://mmisw.org/ont/ioos/swe_element_type/profileBinEdges"
                              referenceFrame="#wmo_41001_sensor1_frame">
                              <swe2:uom code="m" />
                            </swe2:QuantityRange>
                          </swe2:field>
                        </swe2:DataRecord>
                      </swe2:elementType>
                      <swe2:encoding>
                        <swe2:TextEncoding
                          decimalSeparator="."
                          tokenSeparator=","
                          blockSeparator="&#10;" />
                      </swe2:encoding>
                      <swe2:values>
                        -10.0,-5.0 -15.0
                        -20.0,-15.0 -25.0
                        -30.0,-25.0 -35.0
                        -40.0,-35.0 -45.0
                        -50.0,-45.0 -55.0
                      </swe2:values>
                    </swe2:DataArray>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:field>


              <!-- An example of a thermister chain -->
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
                      <swe2:value>urn:ioos:sensor:wmo:41001:sensor2</swe2:value>
                    </swe2:Text>
                  </swe2:field>

                  <swe2:field name="sensorLocation">
                    <!-- For a profiling sensor such as an thermister chain it is best to specify its location relative -->
                    <!-- to a CRS rather than relative to the platform or buoy unless this relationship is -->
                    <!-- actually measured. It is likely that the relative measured location would be dynamic -->
                    <!-- changing with each observation. Where as an absolute lat,lon,Z may be -->
                    <!-- approximated as static. -->
                    <!-- Local frames should always be specified as #{short_asset_id}_frame, regardless of feature type -->
                    <swe2:Vector definition="http://www.opengis.net/def/property/OGC/0/SensorLocation"
                      referenceFrame="http://www.opengis.net/def/crs-compound?1=http://www.opengis.net/def/crs/EPSG/0/4326&amp;2=http://www.opengis.net/def/crs/EPSG/0/5829"
                      localFrame="#wmo_41001_sensor2_frame">
                      <swe2:coordinate name="latitude">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/latitude"
                          axisID="Lat">
                          <swe2:uom code="deg" />
                          <swe2:value>32.382</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                      <swe2:coordinate name="longitude">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/longitude"
                          axisID="Lon">
                          <swe2:uom code="deg" />
                          <swe2:value>-75.415</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                      <swe2:coordinate name="height">
                        <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/height"
                          axisID="Z">
                          <swe2:uom code="m" />
                          <swe2:value>0.0</swe2:value>
                        </swe2:Quantity>
                      </swe2:coordinate>
                    </swe2:Vector>
                  </swe2:field>

                  <swe2:field name="profileHeights">
                    <!-- IoosTech Convention: -->
                    <!-- Static profile bins and heights shall be encoded as an defined array -->
                    <swe2:DataArray
                      definition="http://mmisw.org/ont/ioos/swe_element_type/profileHeights">
                      <swe2:elementCount>
                        <swe2:Count>
                          <swe2:value>3</swe2:value>
                          <!-- The number of bins defined should be greater than or equal to the -->
                          <!-- number of binned observations in the dynamic data for this sensor. -->
                        </swe2:Count>
                      </swe2:elementCount>
                      <swe2:elementType name="profileDefinition">
                        <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/profileHeight">
                          <swe2:field name="height">
                            <!-- IoosTech Convention: -->
                            <!-- Profile depth shall be represented by a defined quantity -->
                            <swe2:Quantity axisID="Z"
                              definition="http://mmisw.org/ont/cf/parameter/height"
                              referenceFrame="#wmo_41001_sensor2_frame">
                              <swe2:uom code="m" />
                            </swe2:Quantity>
                          </swe2:field>
                        </swe2:DataRecord>
                      </swe2:elementType>
                      <swe2:encoding>
                        <swe2:TextEncoding
                          decimalSeparator="."
                          tokenSeparator=","
                          blockSeparator="&#10;" />
                      </swe2:encoding>
                      <swe2:values>
                        -5.0
                        -10.0
                        -20.0
                      </swe2:values>
                    </swe2:DataArray>
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
          <swe2:value>6</swe2:value>
        </swe2:Count>
      </swe2:elementCount>
      <!-- Definition of fields in the DataArray -->
      <swe2:elementType name="observations">
        <!-- IoosTech Convention: -->
        <!-- The data record containing the dynamic observation descriptors for each sensor shall be defined -->
        <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensorObservations">
          <!-- Time is included for all sensors so it is listed first and is outside of DataChoice. -->
          <!-- If time is defined differently for some sensors it could be moved inside the data -->
          <!-- but this is uncommon. -->
          <swe2:field name="time">
            <swe2:Time definition="http://www.opengis.net/def/property/OGC/0/SamplingTime">
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

                  <swe2:field name="adcpProfile">
                    <swe2:DataArray definition="http://mmisw.org/ont/ioos/swe_element_type/profile">
                      <swe2:description>Array of synchronous observations in a Profile</swe2:description>
                      <swe2:elementCount>
                        <!-- IoosTech Convention: -->
                        <!-- Count value is always omitted here and included inline with the encoded -->
                        <!-- data array to allow ragged inner array for trajectories and adcps. -->
                        <swe2:Count />
                      </swe2:elementCount>
                      <swe2:elementType name="profileObservation">
                        <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/profileObservation">

                          <swe2:field name="profileIndex">
                            <!-- IoosTech Convention: -->
                            <!-- A count element, constrained by the maximum dimension of the array -->
                            <!-- shall specify which zero-based bin index the data applies to, -->
                            <!-- allowing ragged arrays -->
                            <!-- NOTE: http://www.opengis.net/def/property/OGC/0/ArrayIndex is mentioned -->
                            <!--       in the SWE 2.0 spec but doesn't resolve... -->
                            <swe2:Count definition="http://mmisw.org/ont/ioos/swe_element_type/profileIndex">
                              <swe2:constraint>
                                <swe2:AllowedValues>
                                  <swe2:interval>0 4</swe2:interval>
                                </swe2:AllowedValues>
                              </swe2:constraint>
                            </swe2:Count>
                          </swe2:field>

                          <swe2:field name="direction_of_sea_water_velocity">
                            <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/direction_of_sea_water_velocity">
                              <swe2:uom code="deg" />
                            </swe2:Quantity>
                          </swe2:field>

                          <swe2:field name="sea_water_speed">
                            <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_speed">
                              <swe2:uom code="cm/s" />
                            </swe2:Quantity>
                          </swe2:field>

                        </swe2:DataRecord>
                      </swe2:elementType>
                    </swe2:DataArray>
                  </swe2:field>
                </swe2:DataRecord>
              </swe2:item>

              <swe2:item name="wmo_41001_sensor2">
                <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/sensor">
                  <swe2:field name="thermisterProfile">
                    <swe2:DataArray definition="http://mmisw.org/ont/ioos/swe_element_type/profile">
                      <swe2:elementCount>
                        <!-- IoosTech Convention: -->
                        <!-- Count value is always omitted here and included inline with the encoded -->
                        <!-- data array to allow ragged inner array for trajectories and adcps -->
                        <swe2:Count />
                      </swe2:elementCount>
                      <swe2:elementType name="profileObservation">
                        <swe2:DataRecord definition="http://mmisw.org/ont/ioos/swe_element_type/profileObservation">

                          <swe2:field name="binIndex">
                            <!-- IoosTech Convention: -->
                            <!-- A count element, constrained by the maximum dimension of the array -->
                            <!-- shall specify which zero-based bin index the data applies to, -->
                            <!-- allowing ragged arrays -->
                            <swe2:Count definition="http://mmisw.org/ont/ioos/swe_element_type/profileIndex">
                              <swe2:constraint>
                                <swe2:AllowedValues>
                                  <swe2:interval>0 2</swe2:interval>
                                </swe2:AllowedValues>
                              </swe2:constraint>
                            </swe2:Count>
                          </swe2:field>

                          <swe2:field name="sea_water_temperature">
                            <swe2:Quantity definition="http://mmisw.org/ont/cf/parameter/sea_water_temperature">
                              <swe2:uom code="Cel" />
                            </swe2:Quantity>
                          </swe2:field>

                        </swe2:DataRecord>
                      </swe2:elementType>
                    </swe2:DataArray>
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
        <!-- 9.2.5  Rules for DataChoice -->
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
        2009-05-23T00:00:00Z,wmo_41001_sensor1,2,0,359.0,10.0,3,352.0,9.6
        2009-05-23T01:00:00Z,wmo_41001_sensor1,1,2,345.0,10.4
        2009-05-23T02:00:00Z,wmo_41001_sensor1,4,0,332.0,10.5,1,334.0,10.3,2,336.0,10.1,3,335.0,9.9
        2009-05-23T00:00:00Z,wmo_41001_sensor2,3,0,13.7,1,16.8,2,19.2
        2009-05-23T01:00:00Z,wmo_41001_sensor2,3,0,13.5,1,16.4,2,19.3
        2009-05-23T02:00:00Z,wmo_41001_sensor2,3,0,13.4,1,16.5,2,18.8
      </swe2:values>
    </swe2:DataArray>
  </swe2:field>
</swe2:DataRecord>
```
