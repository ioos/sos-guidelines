---
title: GetCapabilities Response Template
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: Deprecation Notice - This guidance was deprecated by IOOS on 2020-01-10 and is superceded by the IOOS Metadata Profile 1.2.  Please read the Deprecation Notice below for more information.  Original Summary - Template for a generic (independent of feature type) GetCapabilities response.
toc: false
#permalink: sos-wsdd-github-notoc.html
---

# **Deprecation Notice** 

**Notice:** This convention has been deprecated due to IOOS' transition from the OGC SOS/SWE suite of standards to [ERDDAP](https://coastwatch.pfeg.noaa.gov/erddap) for in situ data dissemination.  

All relevant guidance in this standard has been superceded as of the **2020-01-10** publication date of the [IOOS Metadata Profile 1.2](https://ioos.github.io/ioos-metadata/).  Please refer to the IOOS Metadata Profile for current guidance.

The information below is retained for historical reference purposes only.

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!-- Template Document for a generic (independant of feature type) Get Capabilites -->
<!--  -->
<!-- Template includes the following required metadata elements: -->
<!--    ServiceIdentification -->
<!--    ServiceProvider -->
<!--    OperationMetadata -->
<!--    Contents - specifically the network offerings-->
<!--  -->
<sos:Capabilities
  xmlns:sos="http://www.opengis.net/sos/1.0"
  xmlns:ows="http://www.opengis.net/ows/1.1"
  xmlns:gml="http://www.opengis.net/gml"
  xmlns:om="http://www.opengis.net/om/1.0"
  xmlns:xlink="http://www.w3.org/1999/xlink"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://www.opengis.net/sos/1.0
    http://schemas.opengis.net/sos/1.0.0/sosAll.xsd" version="1.0.0">
  <ows:ServiceIdentification>
    <ows:Title>TITLE</ows:Title>
    <!-- Note to implementer: if any metadata value is missing for a data source use "UNKNOWN" -->
    <!-- Missing values should be logged and reported so that the provider fix it. -->
    <ows:Abstract>ABSTRACT</ows:Abstract>
    <ows:Keywords>
      <ows:Keyword>KEYWORD 1</ows:Keyword>
      <ows:Keyword>KEYWORD 2</ows:Keyword>
    </ows:Keywords>
    <ows:ServiceType codeSpace="http://opengeospatial.net">OGC:SOS</ows:ServiceType>
    <ows:ServiceTypeVersion>1.0.0</ows:ServiceTypeVersion>
    <ows:Fees>NONE</ows:Fees>
    <ows:AccessConstraints>NONE</ows:AccessConstraints>
  </ows:ServiceIdentification>
  <ows:ServiceProvider>
    <ows:ProviderName>PROVIDER</ows:ProviderName>
    <ows:ProviderSite xlink:href="PROVIDER_LINK"/>
    <ows:ServiceContact>
      <ows:IndividualName>CONTACT NAME</ows:IndividualName>
      <ows:ContactInfo>
        <ows:Phone>
          <ows:Voice>PHONE</ows:Voice>
        </ows:Phone>
        <ows:Address>
          <ows:DeliveryPoint>foo</ows:DeliveryPoint>
          <ows:City>foo</ows:City>
          <ows:AdministrativeArea>foo</ows:AdministrativeArea>
          <ows:PostalCode>foo</ows:PostalCode>
          <ows:Country>foo</ows:Country>
          <ows:ElectronicMailAddress>foo@bar</ows:ElectronicMailAddress>
        </ows:Address>
      </ows:ContactInfo>
    </ows:ServiceContact>
  </ows:ServiceProvider>
  <ows:OperationsMetadata>
    <ows:Operation name="GetCapabilities">
      <ows:DCP>
        <ows:HTTP>
          <ows:Get xlink:href="SOS_SERVER"/>
          <ows:Post xlink:href="SOS_SERVER"/>
        </ows:HTTP>
      </ows:DCP>
      <ows:Parameter name="Sections">
        <ows:AllowedValues>
          <ows:Value>ServiceIdentification</ows:Value>
          <ows:Value>ServiceProvider</ows:Value>
          <ows:Value>OperationsMetadata</ows:Value>
          <ows:Value>Contents</ows:Value>
          <ows:Value>All</ows:Value>
        </ows:AllowedValues>
      </ows:Parameter>
    </ows:Operation>
    <ows:Operation name="GetObservation">
      <ows:DCP>
        <ows:HTTP>
          <ows:Get xlink:href="SOS_SERVER"/>
          <ows:Post xlink:href="SOS_SERVER"/>
        </ows:HTTP>
      </ows:DCP>
      <ows:Parameter name="observedProperty">
        <ows:AllowedValues>
          <ows:Value>VALUE</ows:Value>
          <ows:Value>COMPOSITE_VALUE</ows:Value>
        </ows:AllowedValues>
      </ows:Parameter>
    </ows:Operation>
    <ows:Operation name="DescribeSensor">
      <ows:DCP>
        <ows:HTTP>
          <ows:Get xlink:href="SOS_SERVER"/>
          <ows:Post xlink:href="SOS_SERVER"/>
        </ows:HTTP>
      </ows:DCP>
      <ows:Parameter name="outputFormat">
        <ows:AllowedValues>
          <!-- Specify the flavor of SML described by these templates -->
          <ows:Value>text/xml;subtype="sensorML/1.0.1/profiles/ioos_sos/1.0"</ows:Value>
        </ows:AllowedValues>
      </ows:Parameter>
    </ows:Operation>
    <ows:Parameter name="service">
      <ows:AllowedValues>
        <ows:Value>SOS</ows:Value>
      </ows:AllowedValues>
    </ows:Parameter>
    <ows:Parameter name="version">
      <ows:AllowedValues>
        <ows:Value>1.0.0</ows:Value>
      </ows:AllowedValues>
    </ows:Parameter>
    <ows:ExtendedCapabilities>
      <gml:metaDataProperty xlink:title="ioosTemplateVersion"
        xlink:href="http://code.google.com/p/ioostech/source/browse/#svn%2Ftrunk%2Ftemplates%2FMilestone1.0">
        <gml:version>1.0</gml:version>
      </gml:metaDataProperty>
          <ows:ExtendedCapabilities>
      <gml:metaDataProperty xlink:title="softwareVersion"
          xlink:href="http://someURI">
          <gml:version>0.9.4.5</gml:version>
      </gml:metaDataProperty>
    </ows:ExtendedCapabilities>    
  </ows:OperationsMetadata>
  <sos:Contents>
    <!-- IoosTech Convention: -->
    <!-- NetworkAll is a required grouping of stations. -->
    <!-- Individual stations and other networks may be offered as well. -->
    <!-- It is recomended to use DescribeSensor-Network to get a listing -->
    <!-- of the platforms in a network rather than list them as offerings -->
    <!-- in the GetCaps. -->
    <sos:ObservationOfferingList>

      <!-- NETWORK_ALL -->
      <sos:ObservationOffering gml:id="network_all">
        <gml:description>All stations</gml:description>
        <gml:name>urn:ioos:network:AUTHORITY:all</gml:name>
        <gml:srsName>EPSG:4326</gml:srsName>
        <!-- Always use EPSG:4326 as CRS for 2D coordinates -->
        <gml:boundedBy>
          <gml:Envelope srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
            <gml:lowerCorner>-90 -180</gml:lowerCorner>
            <gml:upperCorner>90 180</gml:upperCorner>
          </gml:Envelope>
        </gml:boundedBy>
        <sos:time>
          <gml:TimePeriod>
            <!-- Time period allows a variety of fixed (ISO 8601) and evaluated (now) expressions -->
            <gml:beginPosition>2008-04-28T08:00:00.000Z</gml:beginPosition>
            <gml:endPosition indeterminatePosition="now"/>
          </gml:TimePeriod>
        </sos:time>
        <!-- SOS 2.0 only allows one procedure list only one for future compatibility -->
        <sos:procedure xlink:href="urn:ioos:network:AUTHORITY:all"/>
        <sos:observedProperty xlink:href="http://mmisw.org/ont/cf/parameter/VALUE"/>
        <sos:observedProperty xlink:href="http://mmisw.org/ont/cf/parameter/COMPOSITE_VALUE"/>
        <sos:featureOfInterest xlink:href="FEATURE"/>
        <sos:responseFormat>text/xml;subtype="om/1.0.0/profiles/ioos_sos/1.0"</sos:responseFormat>
        <sos:resultModel>om:ObservationCollection</sos:resultModel>
        <sos:responseMode>inline</sos:responseMode>
      </sos:ObservationOffering>

      <!-- NETWORK_FAVORITES -->
      <!-- It is not scalable to list individual platforms or sensors here however -->
      <!-- listing additional logical groupings by provide, region, measurement type etc -->
      <!-- is encouraged! -->
      <sos:ObservationOffering gml:id="network_favorites">
        <gml:description>All stations</gml:description>
        <gml:name>urn:ioos:network:AUTHORITY:favorites</gml:name>
        <gml:srsName>EPSG:4326</gml:srsName>
        <!-- Always use EPSG:4326 as CRS for 2D coordinates -->
        <gml:boundedBy>
          <gml:Envelope srsName="http://www.opengis.net/def/crs/EPSG/0/4326">
            <gml:lowerCorner>30 -130</gml:lowerCorner>
            <gml:upperCorner>45 -110</gml:upperCorner>
          </gml:Envelope>
        </gml:boundedBy>
        <sos:time>
          <gml:TimePeriod>
            <!-- Time period allows a variety of fixed (ISO 8601) and evaluated (now) expressions -->
            <gml:beginPosition>2008-04-28T08:00:00.000Z</gml:beginPosition>
            <gml:endPosition indeterminatePosition="now"/>
          </gml:TimePeriod>
        </sos:time>
        <!-- SOS 2.0 only allows one procedure list only one for future compatibility -->
        <sos:procedure xlink:href="urn:ioos:network:AUTHORITY:favorites"/>
        <sos:observedProperty xlink:href="http://mmisw.org/ont/cf/parameter/VALUE"/>
        <sos:observedProperty xlink:href="http://mmisw.org/ont/cf/parameter/COMPOSITE_VALUE"/>
        <sos:featureOfInterest xlink:href="FEATURE"/>
        <sos:responseFormat>text/xml;subtype="om/1.0.0/profiles/ioos_sos/1.0"</sos:responseFormat>
        <sos:resultModel>om:ObservationCollection</sos:resultModel>
        <sos:responseMode>inline</sos:responseMode>
      </sos:ObservationOffering>

    </sos:ObservationOfferingList>
  </sos:Contents>
</sos:Capabilities>
```
