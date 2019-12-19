# ICOS Carbon Portal Use Case 


Claudio D’Onofrio ([claudio.donofrio@nateko.lu.se](mailto:claudio.donofrio@nateko.lu.se)), Maggie Hellström, Alex Vermeulen

ICOS Carbon Portal  
Lund University  
Geocentrum II, Sölvegatan 12  
22362 Lund, Sweden

# Introduction

The **I**ntegrated **C**arbon **O**bservation **S**ystem (ICOS [1]) is a “pan-European research infrastructure for quantifying and understanding the greenhouse gas balance of the European continent”. ICOS consists of roughly 150 stations across Europe. The stations are split in three domains (thematic centres) namely Atmosphere [2], Ecosystem [3], and Ocean [4] to collect observational data from the state of the carbon cycle in Europe. Additionally a Central Analytical Laboratory [5] is available to support the monitoring activities of the observational networks. 

ICOS has produced an overall framework of guidelines and requirements to provide quality controlled, standardised and harmonised data collections. Each domain has a dedicated team to assess the measurements to ensure consistent quality before  the data is released to the public. 

The data collections are available in parts through the thematic centres and as a one stop shop at the ICOS Carbon Portal [6].  The Carbon Portal offers access to research data, as well as easily accessible and understandable science and educational products. 

Earth observations are ideally collected continuously over a very long time frame. A very famous long-term observation is located in Hawaii ([https://www.esrl.noaa.gov/gmd/obop/mlo/](https://www.esrl.noaa.gov/gmd/obop/mlo/)) continuously recording since 1950. This data was one of the first indicators for global increase in CO<sub>2</sub> in the atmosphere. The station is alive and still recording data. At ICOS, stations have a long-term view of at least 20 years. This leads naturally to time series datasets, from different time zones and different geographical locations as well as different sensors & instruments recording the same kind of data.  For a “European” view, the stations data needs to be harmonized and combined. Different infrastructure networks measuring the same parameters in other continents are then combined for an “Earth” view.


# Our Goal

The ICOS Carbon Portal aims to provide data collections of greenhouse gases and fluxes from the European continent. The data is free and openly available to everybody (humans and machines) and includes persistent identifiers for reliable long term access. Additionally we have adopted the FAIR data policy: **F**indable, **A**ccessible, **I**nteroperable, **R**eusable.

There are different levels of data offered through the Carbon Portal:



*   Quality controlled raw
*   Near real time data
*   Aggregated data
*   Advanced data products

As a long term European infrastructure project we need to ensure that the data is accessible in the long run, but more importantly to provide the necessary metadata about instruments, people, location, methods, etc., to future proof traceability and provenance.


# Challenges

To study the physical process,  for example CO<sub>2</sub> fluxes, data needs to be combined at station level (temperature, humidity, gas analyser, turbulent wind speed and direction).

Hence we need to:



*   keep track of Sensor / Instrument configuration, sampling rate, date 
*   harmonize raw data to make data sets comparable.
    *   geodetic system
    *   time in UTC
    *   SI Units
    *   …
*   get it right the first time because we observe & measure the environment. We can’t reproduce or repeat experiments.
*   handle data collections where an instrument changes within the time frame. We are mainly interested in data series, not so much in single values measurement. How do we handle a data collection over time, while within the collection timeframe an instrument/sensor was replaced or calibrated?
*   treat the data for gaps and outliers. Methods of data cleaning, gap filling, calculating hourly means, etc. need to be stored together with the results (harmonized raw data).


# ICOS Raw Data Entity

In the ICOS world we regard the “raw” data as smallest entity to store and provide a persistent identifier. The definition of raw data however is not straight forward and is often a data “object” which contains a time series of one or more variables. But regardless of the granularity, shape and form of data, we aim to:



*   Provide Governance and traceability
    *   Create new PID triggered by any change of the underlying information (metadata, sensor – instrument, etc.).
*   Make data comparable
    *   Harmonize raw data to consistent reference frames for time, location, orientation, physical units (SI).
*   Apply FAIR principles
    *   Keep metadata up to date, provide easy to use human and machine interactions.

The raw data with a [dataset?] PID consists of three parts and is elaborated in the following sections:


## 1 - Sensor & Instrument



*   Immutable information about the Sensor / Instrument / Hardware
    *   Manuals
    *   Hardware
    *   Manufacturer
    *   ...
*   Provides individual information (instance)
    *   Serial number
    *   Calibration
    *   …

Ideally a PID is provided by the manufacturer which is the bridge between the company and the internal inventory, purchase, warranty information system. This may contain a potential flag for regular maintenance, out of date or recalibration information. From the manufacturing view point, this would be the top of the supply chain management, representing the final product including bespoke customer requirements (-> Industry 4.0). As an example we can think of a laptop computer which links back to the manufacturers website through the service tag pointing not only to the model but bespoke information including purchase date, installed memory, keyboard layout, hard-disk size, firmware version etc.


## 2 - Installation & Configuration



*   Changes to default parameters and values  
    *   Unit
    *   Sensitivity
    *   Accuracy
    *   …
*   Specific information to the installation
    *   Principal investigator
    *   Last calibration
    *   Location
    *   …

The second part consist of adjustments of the hardware settings, configurable sensor settings and ICOS specific standards, bespoke installation reports, individual calibration data etc. 


## 3 - Conversion & Transformation

As explained above, what is considered as “raw” data and hence being the smallest entity or atomic data, may be differently defined by the thematic centres and the origin of the data. It is possible that the data has been treated to reach a usable data set for further calculations. The following list (not exhaustive) highlights common approaches and topics leading to raw but pre-processed data:

*   Cleaning in regards to outliers and known invalid data points (warming up of a sensor for example and disregarding that time period).
*   Replace invalid data points with a specific symbol (-99999, NaN, …).
*   Remove or flag invalid data. For example on a wind sonic senor the ICOS protocol states: “**Note on the flow distortion**: the Gill HS has a horizontal geometry: this means that all the supporting structures (sonic arm etc.) are placed on the same side and at the same level of the sonic head, i.e. on the opposite of the alignment direction. For that reason the wind coming from “behind” in the sonic reference system is severely disturbed by flow distortion, and must be discarded. By default, considering only the sonic structure, this  sector is 20° wide, 10° on each side of the direction of the sonic arm.” 
*   Adjust orientation, for example wind sonic sensor is normally mounted in the direction of prevailing wind. Hence the data may be transformed to true geographic north.
*   Synchronize data collection timestamps if it’s not possible to collect the data stream on the same datalogger.
*   Conversion to physical units (engineering units, SI)
*   Conversion to UTC 
*   Conversion to the same geodetic system
*   Convert from binary machine level data with proprietary software to standard format/unit

For these reasons, it is paramount to store the methods, approaches, scripts, conversion, algorithms, software,  etc together with the “raw” data to provide full provenance and traceability. 

## Atomic Data View

At his stage, combining all three steps explained above , we reach the level of “harmonized raw data” which includes in an ideal world a PID for the Hardware, how the hardware has been installed and configured, and how the data collected has been treated (if at all).

This state of data will be minted with a PID and contains all information necessary to recreate the data object. Any change in the underlying data will trigger the generation of a new PID or at least document the change in time.

This infographic as a general overview is valid to explain where the “ICOS PID” comes into place, however ICOS stations measure a great variety of variables using many sensors, instruments and data loggers. So in an ideal world we do have one instrument with a PID from the manufacturer, but the real world installations are more complex. Following are a few scenarios of hardware implementations found in ICOS, which needs to be addressed in a “bespoke” manner.



*   A simple sensor like a thermocouple. Can’t exist on its own to provide data because it needs excitation (power) and a datalogger to record the measurement. But the specification for the thermocouple (linearity, hysteresis, sensitivity etc) may provide a reason for a separate PID.
*   We have an instrument (like a gas analyser) with multiple inlets. Each inlet ( a tube with a filter for this example) may have a PID to keep record of location (installation height on tower) and when the filter is changed (maybe the “filter” in itself has a PID).
*   To avoid problems in time synchronisation, especially in high frequency data collection (up to 50Hz), multiple instruments and sensors are connected to the same datalogger.
*   Sensors / instruments on the same data logger are not necessarily sampled at the same frequency.
*   Sensors / Instruments need a geo referenced location. However the instrument can be reused at different location or is portable. Hence location, ownership, configuration etc. may change.
*   We have instruments on research vessels, moving across oceans. So the location of instrument is fixed in the reference frame of the Vessel, but not in the “earth” frame. 


# Conclusion

For ICOS measurements we don’t have a straightforward definition for a PID on the “atomic” level for the hardware. For each Thematic Centre or even each measurement type, a specific way of implementation and how to measure is defined to standardise the data collection.  Depending on what is measured, the atomic PID may consist of many hardware components which may have their own PID’s. Hence, we have opted for a solution where the data object regarded as raw data is a compound of PID’s consisting of hardware, software and meta-data links providing traceability and provenance for that specific time frame.


# Open Questions

As already stated in the “Challenge” section, raw data objects may contain a time series of data. Hence, if any of the parameters of atomic data view does change within the time frame of the data series, we create a new PID, which consequently leads to more than one PID for the same data series. But with more than one PID new difficulties arise such as:



*   If the time series is an aggregate, for example half hour means for a full year, the means are calculated “after” that year. With more than one PID assigned to that data set the calculation of mean, stddev, etc. becomes non-trivial
*   Calculating uncertainty for the data is difficult due to change or recalibration of a sensor / instrument.
*   Methods and scripts to tackle this more complex calculations needs to be stored as well with the data to provide governance.

Which means we need a new PID to include theses scripts and methods? Should we change the granularity of raw data PID, such that raw data by definition is a compound of PID’s representing all the single components?


# Metadata

ID = Numbering, 1, 2, 3 and sub properties with 1.1, 1.2 (akin to DataCite schema)

Property = Name of the property

Occurrence = 1 (mandatory) or 0-1 (optional at most once) or 0-n (optional multiple) or 1-n (at least one)

In metadata of = IP (Infrastructure Provider) or LP (Landing Page)

There are four different levels of classification for the metadata properties:

**M** - Mandatory properties must be provided,

**R** - Recommended properties are optional, but strongly recommended for interoperability

**O** - Optional properties are optional and provide richer description

**C** - Conditional information. For example if it is desired to have an exact geo-location for an Instrument. Otherwiese the hosting infrastructure geolocation is used. Of . Conditional can be combined with M, R, and O to indicate a specific information is needed. 

For certain entries a  fixed and predefined “code” list is provided to ensure a unique and uniform entry of values. For example the country code is specified as ISO 3166-1 alpha 2 entry. A code list (or for this example a link to find the code list) is provided for each specification. Entries M, R, O, C are marked with a star M*****, R*****, O*****, C*** **to indicate the existence and mandatory use of code list.


<table>
  <tr>
   <td>ID
   </td>
   <td>Name
   </td>
   <td>Definition
   </td>
   <td>Notes, Examples
   </td>
   <td>Class
   </td>
   <td>Occ
   </td>
   <td>Const.
   </td>
  </tr>
  <tr>
   <td>1
   </td>
   <td>Instrument Identification
   </td>
   <td>An ID as unique as possible.
   </td>
   <td>Ideally this is a serial number, uniquely identifying the instrument.
   </td>
   <td>M
   </td>
   <td>1
   </td>
   <td>String
<p>
PID
   </td>
  </tr>
  <tr>
   <td>2
   </td>
   <td>Manufacturer
   </td>
   <td>Company, Person, Organization who built the instrument
   </td>
   <td>In case of a bespoke unique build of instrument, this may be the same as the owner.
   </td>
   <td>M
   </td>
   <td>1
   </td>
   <td>String
<p>
PID
   </td>
  </tr>
  <tr>
   <td>3
   </td>
   <td>Model
   </td>
   <td>Model description, specification sheet from manufacturer.
   </td>
   <td>In case of a bespoke unique build of instrument model might not be available.
   </td>
   <td>R
   </td>
   <td>1
   </td>
   <td>String
<p>
PID
   </td>
  </tr>
  <tr>
   <td>4
   </td>
   <td>Owner
   </td>
   <td>Ownership in terms of responsibility to carry out measurements.
   </td>
   <td>This is the owner of the instrument, likely to be responsible for the maintenance, calibration, replacements etc. In the ICOS world this should be a PID to the observation station. Codelist on page 18.
   </td>
   <td>M*
   </td>
   <td>1
   </td>
   <td>String
<p>
PID
   </td>
  </tr>
  <tr>
   <td>5
   </td>
   <td>Infrastructure
   </td>
   <td>Specify which infrastructure is hosting the instrument.
   </td>
   <td>Please link to the infrastructure defined through the station. For example a tower.
   </td>
   <td>O
   </td>
   <td>0-1
   </td>
   <td>String
<p>
PID
   </td>
  </tr>
  <tr>
   <td>6
   </td>
   <td>Orientation
   </td>
   <td>This is an offset to geographic north
   </td>
   <td>For instruments with a “north” orientation, wind sonic for example, the offset to geographical north is required
   </td>
   <td>MC
   </td>
   <td>1
   </td>
   <td>double
<p>
([0-360] degree)
   </td>
  </tr>
  <tr>
   <td>7
   </td>
   <td>Latitude
   </td>
   <td>Latitude
   </td>
   <td>This can be the same as “infrastructure” for example in the case of one tower at station.
   </td>
   <td>MC
   </td>
   <td>1
   </td>
   <td>GeoLatitude (double)
   </td>
  </tr>
  <tr>
   <td>8
   </td>
   <td>Longitude
   </td>
   <td>Longitude
   </td>
   <td>This can be the same as “infrastructure” for example in the case of one tower at station.
   </td>
   <td>MC
   </td>
   <td>1
   </td>
   <td>GeoLongitude (double)
   </td>
  </tr>
  <tr>
   <td>9
   </td>
   <td>Height
   </td>
   <td>Height above ground in meters
   </td>
   <td>Define the exact height of measurement.
   </td>
   <td>R
   </td>
   <td>1
   </td>
   <td>double
   </td>
  </tr>
  <tr>
   <td>10
   </td>
   <td>StartDate
   </td>
   <td>Installation date of the instrument
   </td>
   <td>When was the instrument installed / used?
   </td>
   <td>M
   </td>
   <td> 
   </td>
   <td>DateTime
   </td>
  </tr>
  <tr>
   <td>11
   </td>
   <td>EndDate
   </td>
   <td>Decommission date of Instrument.
   </td>
   <td>Until when was the instrument in use?
   </td>
   <td>M
   </td>
   <td> 
   </td>
   <td>DateTime
   </td>
  </tr>
  <tr>
   <td>12
   </td>
   <td>Related Instruments
   </td>
   <td>Cross identification ID
   </td>
   <td>In case it is an assembly of Sensors, datalogger, instruments etc, the parent – child cross relations should be listed.
   </td>
   <td>O
   </td>
   <td>0-n
   </td>
   <td>String
<p>
 PID
   </td>
  </tr>
</table>



# Links

ICOS and Thematic Centres


<table>
  <tr>
   <td>Integrated Carbon Observation System 
<p>
Research Infrastructure
   </td>
   <td><a href="https://www.icos-ri.eu/">https://www.icos-ri.eu/</a>
   </td>
  </tr>
  <tr>
   <td>Carbon Portal
   </td>
   <td><a href="https://www.icos-cp.eu/">https://www.icos-cp.eu/</a>
   </td>
  </tr>
  <tr>
   <td>Atmosphere
   </td>
   <td><a href="https://icos-atc.lsce.ipsl.fr/">https://icos-atc.lsce.ipsl.fr/</a>
   </td>
  </tr>
  <tr>
   <td>Ecosystem
   </td>
   <td><a href="http://www.europe-fluxdata.eu/icos/home">http://www.europe-fluxdata.eu/icos/home</a>
   </td>
  </tr>
  <tr>
   <td>Ocean
   </td>
   <td><a href="https://otc.icos-cp.eu/">https://otc.icos-cp.eu/</a>
   </td>
  </tr>
  <tr>
   <td>Central Analytical Laboratories
   </td>
   <td><a href="https://www.icos-cal.eu/">https://www.icos-cal.eu/</a>
   </td>
  </tr>
</table>


 \
DOI minted documentation of ICOS Framework on how to install and collect data for the Ecosystem Thematic Centre: \
[https://search.datacite.org/works?query=icos+ecosystem](https://search.datacite.org/works?query=icos+ecosystem)

ICOS Carbon Portal data search and an example landing page for raw data \
[https://data.icos-cp.eu/portal/#search](https://data.icos-cp.eu/portal/#search) \
[https://doi.org/11676/5Uw4Cb6X_3ReH8pU2HusB6q1](https://doi.org/11676/5Uw4Cb6X_3ReH8pU2HusB6q1)

FAIR data principles \
[https://www.force11.org/group/fairgroup/fairprinciples](https://www.force11.org/group/fairgroup/fairprinciples) \
[https://www.nature.com/articles/sdata201618](https://www.nature.com/articles/sdata201618)

Don’t confuse:  

**Meteorology** ( [https://en.wiktionary.org/wiki/meteorology](https://en.wiktionary.org/wiki/meteorology) ), the science that deals with the study of the atmosphere and its phenomena, especially with weather and weather forecasting.   
and **Metrology** ( [https://en.wiktionary.org/wiki/metrology](https://en.wiktionary.org/wiki/metrology) ), the science of weights and measures or of measurement.



*   GUM: Guide to the Expression of Uncertainty in Measurement \
[https://www.bipm.org/utils/common/documents/jcgm/JCGM_100_2008_E.pdf](https://www.bipm.org/utils/common/documents/jcgm/JCGM_100_2008_E.pdf) 
*   VIM3: International Vocabulary of Metrology \
[https://www.bipm.org/en/publications/guides/vim.html](https://www.bipm.org/en/publications/guides/vim.html)
*   The International System of Units (SI) \
[https://www.bipm.org/utils/common/pdf/si_brochure_8_en.pdf](https://www.bipm.org/utils/common/pdf/si_brochure_8_en.pdf) 

<!-- Footnotes themselves at the bottom. -->
## Notes

[1] [https://www.icos-ri.eu/](https://www.icos-ri.eu/) 

[2] [https://icos-atc.lsce.ipsl.fr/](https://icos-atc.lsce.ipsl.fr/) 

[3] [http://www.europe-fluxdata.eu/icos/home](http://www.europe-fluxdata.eu/icos/home) 

[4] [https://otc.icos-cp.eu/](https://otc.icos-cp.eu/) 

[5] [https://www.icos-cal.eu/](https://www.icos-cal.eu/) 

[6] [https://www.icos-cp.eu/](https://www.icos-cp.eu/)


<!-- Docs to Markdown version 1.0β17 -->
