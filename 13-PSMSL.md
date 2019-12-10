# PSMSL/GLOSS delayed mode data archive centre – Use of PIDs for tide gauge sensors and sea level stations

Louise Darroch  
October 2018

The Permanent Service for Mean Sea Level (PSMSL) is responsible for the collection, publication, analysis and interpretation of mean sea level data from a global network of tide gauges. The Global Sea Level Observing System (GLOSS) Delayed Mode Data Centre is operated by the British Oceanographic Data Centre (BODC) in collaboration with PSMSL. It has the responsibility for assembling, quality controlling and distributing the “final” version of GLOSS sea level data sets, as well as all supporting metadata information (including benchmark details). The Delayed Mode Centre handles hourly and sub-hourly values, together with ancillary variables (e.g. atmospheric pressure).

Sea level records are some of the longest ocean observations available, with the earliest continuous time series beginning in the 18th Century. The length of data available makes creating one complete findable, accessible, interoperable and reusable (FAIR) record a challenge.

The main issues facing the data centres, when making available a continuous time series are:

* Ensuring that data processing steps e.g. calibrations, quality control level and corrections are documented
* Tracking the movement of sensors around a site and also exchanging sensors between sites
* Giving proper accreditation to all involved in the creation and curation of the dataset e.g. funders, creators, suppliers and curators

We could solve these issues by assigning persistent identifiers (PIDs) to the sensors producing the data. This will help improve the description of a time series where the sensor and platform can change many times.

Data providers make their data available via ftp sites, webpages and satellite communications, which are open to being harvested and incorporated into data portals and systems that might not collect associated metadata and documentation. Sea level data have been distributed via international portals, claiming to be quality controlled, when no QC has been performed on the original data and the processes cannot be replicated. We need to link the quality control procedures and version information to data so that they cannot be separated. When a user downloads data from a portal, they need to know what modifications have been made to that series and if it is considered the best version available. Some portals provide composite series where data from multiple synchronous or neighbouring sensors have been merged to create a single dataset. This can have its uses, but the user needs to be made aware that this has occurred so they can make an informed decision about whether the series is suitable for their application.

Over time, a tide gauge can be relocated around a harbour, and providing the data can always be connected to consistent benchmarks, an unbroken time series can be produced. We need to know if the same sensors have been moved from one position to another, or whether new sensors have been installed when the gauge moves. Sensors are also moved between tide gauge locations. In the UK, the Digiquartz® sensors that are part of the bubbler gauges have been switched between various sites. This has also happened at some Spanish tide gauges, where the radar sensor at one site has been relocated to a new station. We need to keep track of the movements of sensors, as when calibration issues arise, we may need to apply corrections to the datasets at multiple locations.

We have identified an issue with data harvesting portals not supplying the proper accreditation with the data they distribute. If a site has obtained the data from third party, the data can be labelled as originating from that third party. This is frustrating for the actual funders of the dataset, as they are not properly able to track the impact of their data. Users of the data will also have difficulty tracing the correct people to contact if they have a query about the dataset. We need to improve the metadata available to ensure that the funders, creators, suppliers, curators etc. of the data are given proper credit and are traceable/contactable.

We need to make sure that we create comprehensive usage and lineage metadata, stored with a dataset, so that users can have confidence in the reuse of those data but also that those involved with the production of that dataset are given the proper credit. 

## Key Metadata

Here we describe a core set of metadata needed to describe and identify both a station and a sensor. We have attempted to use properties and sub-properties from the DataCite metadata schema.

**Station**

*NB. PID may include URL to a controlled vocabulary term

 


<table>
  <tr>
   <td><strong>Identifier</strong>
   </td>
   <td><strong>Occurrence (The number of times the identifier can be used)</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Format</strong>
   </td>
  </tr>
  <tr>
   <td>Creator
   </td>
   <td>0..n
   </td>
   <td>The organisation primarily responsible for operating the station. Multiple creators may be listed where responsibility is split between two or more organisation. For example, the station on Tarawa Atoll is operated by the Australian Bureau of Meteorology and the Kiribati Met Office
   </td>
   <td>Text or PID*
   </td>
  </tr>
  <tr>
   <td>Title
   </td>
   <td>1
   </td>
   <td>A descriptive name of the location, e.g. “Liverpool, Gladstone Dock”.
   </td>
   <td>Text
   </td>
  </tr>
  <tr>
   <td>Publisher
   </td>
   <td>1
   </td>
   <td>The organisation issuing the persistent identifier.
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>PublicationYear
   </td>
   <td>1
   </td>
   <td>The year the identifier was issued.
   </td>
   <td>date
   </td>
  </tr>
  <tr>
   <td>ResourceType
   </td>
   <td>1
   </td>
   <td>Other / Water Level Station
<p>
 
   </td>
   <td>Controlled list of values
   </td>
  </tr>
  <tr>
   <td>Contributor
   </td>
   <td>0..n
   </td>
   <td>Other people or organisations involved in the operation of the site: for example funding agencies, data distributors or site owners. The nature of the contribution will be defined by the sub-property “contributorType”.
<p>
 
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>ContributorType
   </td>
   <td>0..n
   </td>
   <td>Qualification of “Contributor”
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>GeoLocation
   </td>
   <td>1
   </td>
   <td>The geographic coordinates of the station.
   </td>
   <td>Text
   </td>
  </tr>
</table>

**Sensor**

<table>
  <tr>
   <td><strong>Identifier</strong>
   </td>
   <td><strong>Occurrence (The number of times the identifier can be used)</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Format</strong>
   </td>
  </tr>
  <tr>
   <td>Creator
   </td>
   <td>0..n
   </td>
   <td>The manufacturer of the instrument.
<p>
 
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>Title
   </td>
   <td>1
   </td>
   <td>A name identifying the instrument: e.g., “Digiquartz Sensor Model XYZ Serial Number 12345”
   </td>
   <td>Text
   </td>
  </tr>
  <tr>
   <td>Publisher
   </td>
   <td>1
   </td>
   <td>The organisation issuing the persistent identifier.
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>PublicationYear
   </td>
   <td>1
   </td>
   <td>The year the identifier was issued.
   </td>
   <td>date
   </td>
  </tr>
  <tr>
   <td>ResourceType
   </td>
   <td>1
   </td>
   <td>PhysicalObject / Water Level Sensor
   </td>
   <td>Controlled list of values
   </td>
  </tr>
  <tr>
   <td>Contributor
   </td>
   <td>0..n
   </td>
   <td>Other involved organisations, such as the owner. The nature of the contribution will be defined by the sub-property “contributorType”.
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>ContributorType
   </td>
   <td>0..n
   </td>
   <td>Qualification of “Contributor”
   </td>
   <td>Text or PID
   </td>
  </tr>
  <tr>
   <td>Description
   </td>
   <td>0..1
   </td>
   <td>Further information about the sensor. Ideally a link to a standardized description of the sensor (e.g. SensorML).
   </td>
   <td>Text, PID, URL
   </td>
  </tr>
</table>


 


<!-- Docs to Markdown version 1.0β17 -->
