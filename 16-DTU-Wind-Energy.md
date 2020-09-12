# Technical University of Denmark Wind Energy Department (DTU Wind Energy) Use Case

Nikola Vasiljevic (niva@dtu.dk, ORCiD [0000-0002-9381-9693](https://orcid.org/0000-0002-9381-9693)), Andrea Vignaroli (andv@dtu.dk, ORCiD [0000-0001-8007-7291](https://orcid.org/0000-0001-8007-7291)) and Jesper Juul Holm (jjho@dtu.dk)

June 2020

## Introduction
The main focus of the wind energy domain is to provide practical solutions that will result in cost-effective electricity produced from the wind.
To achieve such goals, wind energy domain, even though largely seen as an engineering domain, is characterized as  multi-disciplinary domain, re-using existing solutions and contributing with a new one in the following domains:
- Earth Sciences, especially atmospheric science
- Mechanical Engineering
- Material Science
- Electrical Engineering
- Computer Science
- Social Science

At the heart of the wind energy domain are measurements. Generally speaking, wind energy domain immensely cares about the [metrological](https://en.wikipedia.org/wiki/Metrology) aspects of its instruments since uncertainties of measurands directly translate to for example finances (e.g., the uncertainty of 0.1 m/s in the measured wind speed leads to an estimated saving/loss worth around 10 M£ per year for the 25 year lifetime of a wind farm project) or safety ([failure of wind turbines can be dangerous to people](https://www.youtube.com/watch?v=xwS-FH38Fqg)).

## About DTU Wind Energy
[DTU Wind Energy](https://www.vindenergi.dtu.dk/english) is one of the world's most recognized wind energy institute. DTU Wind Energy operates [several research and commercial facilities](https://www.vindenergi.dtu.dk/english/test-centers/research-facilities) (some permanent, some mobile) which consists of a large pull of instruments. Certain instruments are off-the-shelf-products, while others DTU Wind Energy either develops or modifies to suit particular needs.

## Motivation for PIDINST implementation

There are several reasons for the PIDINST implementation at [DTU Wind Energy](https://www.vindenergi.dtu.dk/english). First of all, using PIDINST we would be able to interconnect people, data, technical/scientific publications, funding, code, workflows, and instruments through PIDs. Therefore, it would be possible to capture a full chain of custody and find/access its interconnected objects (from a single object to any other object). Using PIDINST we would be able to adopt and practically implement [FAIR principles](https://www.nature.com/articles/sdata201618) beyond data. PIDINST will improve instrument traceability (PID secures resolvable landing page and through certain attributes, we can provide information on for example calibration reports). Especially, PIDINST will significantly improve the visibility of staff focused on the development, maintenance, and installation of instruments, and thus their acknowledgment and credits in the scientific community, but as well make them accountable.

## Measurements standardization
Since the early 1980s, [DTU Wind Energy](https://www.vindenergi.dtu.dk/english) (until 2012 known as [Risø DTU](https://en.wikipedia.org/wiki/Ris%C3%B8_DTU_National_Laboratory_for_Sustainable_Energy)) has been performing field and in-lab research and commercial measurement campaigns globally.

Commercial measurements followed standards such as [IEC 61400](https://en.wikipedia.org/wiki/IEC_61400), which are typically established in cooperation between research institutes and wind energy industry. An important role in this work is played by [MEASNET](http://www.measnet.com/) (**MEAS**uring **NET**work of Wind Energy Institutes) which works towards harmonization of measuring procedures and 'standards' among wind energy institute to secure that high-quality measurements are carried out by them. For example, [IEC 61400-12](https://webstore.iec.ch/publication/26603) establishes norms for meteorological masts and its instrumentation (e.g., length of booms carrying cup anemometers, etc.). Other standards propose the naming of data streams (e.g., [IEC 61400-25](https://en.wikipedia.org/wiki/IEC_61400-25)). In IEC, DTU Wind Energy is leading maintenance of current standards and development of new ones. In MEASNET, DTU Wind Energy has been a long-standing active member.

Measurement standards when it comes to the instrumentation are followed in research-oriented measurement campaigns too, with exceptions for new instruments that are not yet included in them. In research campaigns, we often encounter the multi-disciplinarity nature of the wind energy domain when it comes to the naming of data streams. Researchers who are more Earth Science oriented tend to use [Climate Forecast standard names](http://cfconventions.org/standard-names.html). On the other hand, researchers with engineering backgrounds tend to use IEC. However, even more often we encounter ad-hoc naming of data streams. Nevertheless, DTU Wind Energy is making [a significant push in adoption of the FAIR data principles](https://zenodo.org/record/3865225), and thus trans-disciplinary harmonization of commercial and research-oriented measurements.

## General measurement campaign workflow
Every measurement campaign at DTU Wind Energy starts with a sensor list. This is just a list of all the parameters to be measured. The sensor list usually contains also information regarding heights and positions, brand and model of the sensors to be used. The sensor list is the basis for the preparation of CAD drawings where the layout of the measurements system is defined in more detail like cable length junction boxes and adapter required. For certain applications, such as noise and wind mapping, more distributed measurements are required. In those cases, CAD drawings are supplemented with GIS maps.
The CAD drawings initiate the manufacturing of the measurements system which is assembled and tested before sent at the site for installation. At the same time, the sensors are ordered and sent to calibration, if they are not already on the stock. The instrument database is updated to show that certain sensors are being used in a certain site for a certain project.
Once the measurement system is at the site the installation can start. This phase can take several days depending on the complexity of the system and weather conditions. Usually, a line calibration is also performed after installation by injecting a known frequency/voltage instead of the sensor and check plausibility and linearity of the readings are from the data acquisition software.
All the documentation is stored in a project folder sitting in a network drive behind the DTU firewall. Visibility and access to such a folder are controlled by the IT administrator. The project folder will contain also the data files when the measurement starts.
To get the data acquisition up and running, a configuration file has to be created. This file contains crucial information like the naming of the parameter, sampling frequency, calibration factors, the drivers that the data acquisition software has to use to interpret certain signals, or create new parameters on basis of others.
The data acquisition software runs on an industrial PC. the computer time is synchronized every 15 minutes by a local network time server.
Every ten minutes, the data files (both the file with the high-frequency data, and the file with the 10min statistics) are:
-   Packed, together with a copy of the setup file, into a zip file.
-   This compressed file is copied into a local archive, in the measurement PC.
-   The compressed file is transferred by secure FTP to DTU.
At DTU’s database and file server computer, a schedule runs every ten minutes and performs the following operations:
-   Downloads the compressed data files from the FTP and stores them in the project folder.
-   Uploads the 10-minute data into a database. The database consists of several tables, including a setup version list, which is updated every time a measurement channel is modified, removed, or added in the data acquisition software.

No further corrections are applied to the databases.  If an additional correction is to be applied on a channel, it is done in the post-processing performed during the data analysis.

In parallel, every ten minutes text files with 10-minute statistical data (optionally, Flex4 binary files too) are generated from the high-frequency data files. The conversion software can apply gain and offset to the certain signals to account for some effects like line calibration. The post-processed data can be sent to the client via FTP. Automatic conversion from text and binary files to the [NetCDF](https://www.unidata.ucar.edu/software/netcdf/) format is also possible.
The data acquisition software can also stream the logged high-frequency data in UDP packages if logging of the signals from another data acquisition software is required.

It is possible that in a very large measurement campaign some parameters are measured by instruments equipped with their own data acquisition system. In that case, the data files are merged after they reach DTU servers. This can create some time synchronization problems. Some measurement devices have UDP streaming capabilities to avoid such risk.

The measurement campaign is monitored daily by accessing remotely to each device and checking that the data acquisition software is up and running. Quality check of the measurement data is performed on a 3-5 days basis by using a web interface that plots stored data in the database. Alarms for missing data or data out of range can be defined in such a web interface. Relevant events and actions are recorded in a WebLog.

This workflow is applicable for both research and commercial measurement campaign. But confidentiality, especially in commercial campaigns, regulates how much information, such as used instruments and recorded data, can be made publicly available. 

## Internal instrumentation database
[DTU Wind Energy](https://www.vindenergi.dtu.dk/english) operates an instrumentation database [instruments.windenergy.dtu.dk](instruments.windenergy.dtu.dk) (initially developed 20 years ago), which is accessible within the DTU network and only for selected DTU Wind Energy staff. The database contains metadata on actual instruments and related components (e.g., data acquisition systems, batteries, UPS, etc.) An instrument/component can have subcomponents (e.g. an enclosure), and is thus referred to as a "complex instrument".

The database has a web interface and instruments and related components are accessible  by browsing a multi-page table which contains following columns:

| Column name | Column description | Column data type |
|-|-|-|
| Type | The instrument/component type | String term from user-maintained list of instrument types |
| PFV_type | Unique ID of Type | Manually, sequentially numbered unique integer |
| PFV_number | Unique ID of the instrument in the instrument database | Manually, sequentially numbered unique integer |
| Serial_number | A serial number of the instrument provided by the instrument manufacturer | Free text, optional |
| Supplier | The supplier of the instrument | String term from user-maintained list of suppliers |
| Status | An inventory status of the instrument | String term from restricted vocabulary |
| Site | Current or last location (site/parent component) where the instrument was used | String term from user-maintained list of sites |
| Active | Indicates whether the instrument is currently active or not | Boolean (Yes/No) |

Alternatively, a direct query of a specific instrument can be done by searching the database through the same web interface using **PFV_number**.

Each instrument in the database is reported with:
- General metadata about the instrument
- Provenance of the instrument provided
- Instrument calibration information
- Information about errors and repairs
- Subcomponents/-instruments in case the instrument is complex.

Except for the general metadata, other information is updated throughout the instrument lifetime.

The general metadata about the instrument contains the following elements:
| Metadata elements | Description of element | Data type |
|-|-|-|
| Make | Instrument manufacturer | String term from user-maintained list of instrument types |
| Type | The instrument type | String term from user-maintained list of instrument types |
| Serial_number | A serial number of the instrument provided by the instrument manufacturer | Free text, optional |
| Description | Description of the instrument | Free text |
| Supplier | Instrument supplier | String term from user-maintained list of suppliers |
| Buy_date | The date of the instrument acquisition| Date |
| Price | The instrument price in DKK | Float |
| Ordered_by | DTU id of the person who acquired the instrument | Internal phonebook (string) |
| PFV_no | Unique id of the instrument | Manually, sequentially numbered unique integer |
| Comment | General comment about the instrument | Free text |

The instrument status is provided as a multi-row table with the following columns:
| Column name | Column description | Column data type |
|-|-|-|
| Active | Indicates whether the instrument is active or not at the time of the status update | Boolean (Yes/No) |
| Status | An inventory status of the instrument | String term from restricted vocabulary |
| Calibration | Indicates if the instrument has been calibrated at the time of the status update | Boolean (Yes/No) |
| Position | Remark about placement of the instrument (e.g. altitude, direction, shelf etc.) | Free text |
| Site | Location (i.e. site or stock ) where the instrument was/is used | Free text |
| User_ID | DTU id of the person who entered the information | Internal phonebook (string) |
| Date_from | The start date of the status update | Date |
| Date_to | The ending date of the status update (e.g. an instrument should be taken down). Not heavily used. | Date |
| Comment | Specific comment for the given entry in the status table | Free text |
| PSP_Element | Internally used project number | Free text |
| Accreditation | If the accomplishment has been accreditated | Boolean (Yes/No) |
| Configuration | Relevant information about new/changed configuration of the equipment | Free text |

Whenever the instrument status is updated new row with the above information are added to the status table.

The instrument calibration information are provided as a multi-row table with the following columns:
| Column name | Column description | Column data type |
|-|-|-|
| Specification | Calibration specification | Free text |
| Calibration date | Date of calibration | Date in form MM-DD-YYYY |
| Expire date | Date when the calibration expire | Date in form MM-DD-YYYY |
| Calibration A | Uncertainty of type A | Float |
| Calibration B | Uncertainty of type B | Float |
| Units | Units for Calibration A and Calibration B | Free text |
| Supplier | Supplier of the calibration | String term from user-maintained list of suppliers |
| Certificate doc | URL to the calibration report | URL |
| Comment | Any specific comment related to the instrument calibration | Free text |

At any point new calibration is made the above calibration table is updated.

If the instrument is complex its subcomponents/subinstruments are reported with a multi-row table with the following columns:

| Column name | Column description | Column data type |
|-|-|-|
| Type | The subcomponent / instrument type | String term from user-maintained list of instrument types |
| PFV_no | Unique id of the instrument | Manually, sequentially numbered unique integer |
| PFV_type | Unique ID of Type | Manually, sequentially numbered unique integer |
| Serial_number | A serial number of the instrument provided by the instrument manufacturer | Free text, optional |
| Supplier | Instrument supplier | String term from user-maintained list of suppliers |
| Status | An ownership status of the instrument | String term from restricted vocabulary |
| Active | Indicates whether the subcomponent/-instrument is active or not at the time of the status update | Boolean (Yes/No) |

## Implementation PIDINST schema
The table below shows mapping between PIDINST schema and instruments properties available in [instruments.windenergy.dtu.dk](instruments.windenergy.dtu.dk). Also, the last table column highlights potential improvements that could be introduced to the existing version of [instruments.windenergy.dtu.dk](instruments.windenergy.dtu.dk) or that can be used to develop next version of this database having PIDINST minting in its core.

| PIDINST property ID<br> | PIDINST property<br>           | instruments.windenergy.dtu.dk<br> property <br>  | Potential improvements |
|---------------------|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| 1                   | Identifier                 | Serial\_number, PFV\_no                                                                                                              | DOI or ePIC                                                                                                                       |
| 1\.1                | identifierType             | serialNumber and inventoryNumber                                                                                                     | DOI or ePIC                                                                                                                       |
| 2                   | LandingPage                | https://instruments.windenergy.dtu.dk/index.php?page=show_instrument&id=PFV_no accessible only internally                      | Open access to https://instruments.windenergy.dtu.dk/PFV_type/PFV_no/                                                        |
| 3                   | Name                       | Type                                                                                                                                 | Improved controlled vocabulary of instruments                                                                                      |
| 4                   | Owner                      | Automatically we can only either state DTU Wind Energy or indicate staff that ordered and\-or added changes to the instrument status | Should be DTU Wind Energy followed with ids of staff who built, maintained and installed instrument                                |
| 4\.1                | ownerName                  | Ordered\_by, User\_id or DTU Wind Energy                                                                                             | Names of involved staff and institute name                                                                                        |
| 4\.2                | ownerContact               | Ordered\_by@dtu\.dk, User\_id@dtu\.dk                                                                                                | Email of staff and central email address of DTU Wind Energy                                                                       |
| 4\.3                | ownerIdentifier            | Internal phonebook ids                                                                                                               | ORCiD iDs of involved stuff, ROR of DTU (https://ror.org/04qtj9h94) and URL of DTU Wind Energy|
| 4\.3\.1             | ownerIdentifierType        | Phonebook                                                                                                                            | ORCiD, ROR                                                                                                                        |
| 5                   | Manufacturer               |                                                                                                                                      |                                                                                                                                   |
| 5\.1                | manufacturerName           | Make                                                                                                                                 | Make                                                                                                                              |
| 5\.2                | manufacturerIdentifier     | manufacturer web site                                                                                                                | manufacturer web site                                                                                                             |
| 5\.2\.1             | manufacturerIdentifierType | URL                                                                                                                                  | URL                                                                                                                               |
| 5\.3                | modelName                  | Type                                                                                                                                 | Type                                                                                                                              |
| 6                   | Description                | Description                                                                                                                          | Description                                                                                                                       |
| 7                   | InstrumentType             | Type or PFV\_type                                                                                                                    | Improved controlled vocabulary of instrument types                                                                                          |
| 8                   | MeasuredVariable           | Units \(partially\)                                                                                                                  | Direct link to controlled vocabulary of parameters                                               |
| 9                   | Date                       | Date when instrument was acquired, calibrated, used, decommissioned                                                                   | An improved set of dates related to the instrument                                                                                |
| 9\.1                | dateType                   | Buy\_date, Date\_from, Date\_to, Calibration date, Expiration date                                                                   | Commissioned, Decommissioned, Calibration, \.\.\.                                                                                 |
| 10                  | RelatedIdentifier          | PFV\_no of subcomponents                                                                                                             | This would be calibration and technical reports, instrumentation papers, data as well subcomponents/instruments                   |
| 10\.1               | relatedIdentifierType      | PFV\_no                                                                                                                              | PIDs or URLs                                                                                                                      |
| 10\.2               | relationType               | HasComponent, IsComponentOf,                                                                                                         | PIDINST, DOI, URL                                                                                                                 |
| 11                  | AlternateIdentifier        | Serial\_number, PFV\_no                                                                                                              | Serial\_number, PFV\_no                                                                                                           |
| 11\.1               | alternateIdentifierType    | serialNumber and inventoryNumber                                                                                                     | serialNumber and inventoryNumber                                                                                                  |





Since [DTU Wind Energy](https://www.vindenergi.dtu.dk/english) operates commercial measurement campaigns beside research campaigns the entire database of instruments cannot be made publicly available. Therefore, as a proof-of-concept of PIDISNT implementation, we will mirror parts of [instruments.windenergy.dtu.dk](instruments.windenergy.dtu.dk), which would not harm commercial competitive advantage of DTU Wind Energy neither harm its commercial customers. To start with this work we will make available access to information on instruments located at a meteorological mast that operates in front of the [research wind turbine V52](https://www.vindenergi.dtu.dk/english/Research/Research-Facilities/The-research-wind-turbine-V52) as well to several [WindScanners](https://www.vindenergi.dtu.dk/english/research/research-facilities/windscanner).
