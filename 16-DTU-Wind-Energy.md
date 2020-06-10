# Technical University of Denmark Wind Energy Department (DTU Wind Energy) Use Case

Nikola Vasiljevic (niva@dtu.dk, ORCiD [0000-0002-9381-9693](https://orcid.org/0000-0002-9381-9693)), Andrea Vignaroli (andv@dtu.dk) and Jesper Juul Holm (jjho@dtu.dk)

June 2020

## Introduction
The main focus of wind energy domain is to provide practical solutions that will result in cost-effective electricity produced from the wind.
To achive such goals, wind energy domain, even though largely seen as an engineering domain, is characterized as  multi-disciplinary domain, re-using existing solutions and contributing with new one in the following domains:
- Earth Sciences, especially atmospheric science
- Mechanical Engineering
- Material Science
- Electrical Engineering
- Computer Science
- Social Science

At the heart of the wind energy domain are measurements. Generally speaking, wind energy domain immensely cares about the [metrological](https://en.wikipedia.org/wiki/Metrology) aspects of its instruments since uncertainties of measurands directly translate to for example finances (e.g., the uncertainty of 0.1 m/s in the measured wind speed leads to an estimated saving/loss worth around 10 M£ per year for the 25 year lifetime of a wind farm project) or safety ([failure of wind turbines can be dangerous to people](https://www.youtube.com/watch?v=xwS-FH38Fqg)) .

## About DTU Wind Energy
[DTU Wind Energy](https://www.vindenergi.dtu.dk/english) is one of the world most recognized wind energy institute. DTU Wind Energy operates [a number of research and commercial facilities](https://www.vindenergi.dtu.dk/english/test-centers/research-facilities) (some permanent, some mobile) which consists of a large pull of instruments. Certain instruments are off-the-shelf-products, while others DTU Wind Energy either develops or modifies to suit particular needs.

## Motivation for PIDINST implementation

There are several reasons for the PIDINST implementation at [DTU Wind Energy](https://www.vindenergi.dtu.dk/english). First of all, using PIDINST we would be able to interconnect people, data, technical/scientific publications, funding, code, workflows and instruments through PIDs. Therefore, it would be possible to capture a full chain of custody and find/access its interconnected elements through by any of them. Using PIDINST we would be able to adopt and practically implement [FAIR principles](https://www.nature.com/articles/sdata201618) beyond data. PIDINST will improve instrument traceability (PID secures resolvable landing page and through certain attributes we can provide information on for example calibration reports). Especially, PIDINST will significantly improve visibility of staff focused on development, maintenance and installation of instruments, and thus their acknowledgement and credits in scientific community, but as well identify their responsibility.

## Measurements standardization
Since the early 1080s, [DTU Wind Energy](https://www.vindenergi.dtu.dk/english) (until 2012 known as [Risø DTU](https://en.wikipedia.org/wiki/Ris%C3%B8_DTU_National_Laboratory_for_Sustainable_Energy)) has been performing field and in-lab research and commercial measurement campaigns globally.

Commercial measurements followed standards such as [IEC 61400](https://en.wikipedia.org/wiki/IEC_61400), which are typically established in cooperation between research institutes and wind energy industry. An important role in this work is played by [MEASNET](http://www.measnet.com/) (**MEAS**uring **NET**work of Wind Energy Institutes) which works towards harmonization of measuring procedures and 'standards' among wind energy institute to secure that high quality measurements are carried out by them. For example, [IEC 61400-12](https://webstore.iec.ch/publication/26603) establish norms for meterological masts and its instrumentation (e.g., length of booms carrying cup anemometers, etc.). Other standards propose naming of data streams (e.g., [IEC 61400-25](https://en.wikipedia.org/wiki/IEC_61400-25)). In IEC, DTU Wind Energy is leading maintenance of current standards and development of new ones. In MEASNET, DTU Wind Energy has been a long-standing active member.

Measurement standards when comes to the instrumentation are followed in research oriented measurement campaigns too, with exceptions for new instruments which are not yet included in them. In research campaigns we often encounter multi-disciplinarity nature of wind energy domain when comes to naming of data streams. Researchers who are more Earth Science oriented tend to use [Climate Forecast standard names](http://cfconventions.org/standard-names.html). On the other hand, researchers with engineering background tend to use IEC. However, even more often we encounter ad-hoc naming of data streams. Nevertheless, DTU Wind Energy is making [a significant push in adoption of the FAIR data principles](https://zenodo.org/record/3865225), and thus trans-disciplinary harmonization of commercial and research oriented measurements.

## General measurement campaigns workflow

### Commercial campaigns


### Research campaigns


## Internal instrumentation database
[DTU Wind Energy](https://www.vindenergi.dtu.dk/english) operates an instrumentation database [instruments.windenergy.dtu.dk](instruments.windenergy.dtu.dk), which is accessible within the DTU network and only for selected DTU Wind Energy staff.

The database has a web interface and instruments are accessible  by browsing a multi-page table which contains following columns:

| Column name | Column description | Column data type |
|-|-|-|
| Type | The instrument type | String term from internal restricted vocabulary |
| PFV_type | Similar to Type but provided as an integer | Integer from predefined set of integers |
| PFV_number | A unique id of the instrument in the instrument database | Auto-generated unique integer |
| Serial_number | A serial number of the instrument provided by the instrument manufacturer | Free text |
| Supplier | A supplier of the instrument | Free text |
| Status | An ownership status of the instrument | String term from restricted vocabulary |
| Site | Last location (i.e., site) where the instrument was used | Free text |
| Active | Indicates whether the instrument is currently active or not | Boolean (Yes/No) |

Alternatively, a direct query of a specific instrument can be done by searching the database through the same web interface using **PFV_number** or **Serial_number**.

Each instrument in the database is reported with:
- General metadata about the instrument
- Provenance of the instrument provided
- Instrument calibration information
- Sub-components/instruments in case if the instrument is complex

With the exception of the general metadata, other information are updated over the course of the instrument lifetime.

The general metadata about the instrument contains following elements:
| Metadata elements | Description of element | Data type |
|-|-|-|
| Make | Instrument manufacturer | Free text |
| Type | The instrument type | String term from internal restricted vocabulary |
| Serial_number | A serial number of the instrument provided by the instrument manufacturer | Free text |
| Description | Description of the instrument | Free text |
| Supplier | Instrument supplier | Free text |
| Buy_date | The date of the instrument acquisition| Date in form MM-DD-YYYY |
| Price | The instrument price in DKK | Float |
| Ordered_by | DTU id of the person who acquired the instrument | Internal phonebook (strings) |
| PFV_no | Unique id of the instrument | Auto-generated unique integer |
| Comment | General comment about the instrument | Free text |

The instrument status is provided as a multi-row table with the following columns:
| Column name | Column description | Column data type |
|-|-|-|
| Active | Indicates whether the instrument is currently active or not | Boolean (Yes/No) |
| Status | An ownership status of the instrument | String term from restricted vocabulary |
| Calibration | ? | ? |
| Position | ? | ? |
| Site | Location (i.e., site) where the instrument was/is used | Free text |
| User_ID | DTU id of the person who entered information | Internal phonebook (strings) |
| Date_from | ? | ? |
| Date_to | ? | ? |
| Comment | Specific comment for the given entry in the Status table | Free text |
| PSP_Element | ? | ? |
| Accreditation | ? | ? |
| Configuration | ? | ? |
Whenever the instrument status is updated new row with the above information are added to the status table.

The instrument calibration information are provided as a multi-row table with the following columns:
| Column name | Column description | Column data type |
|-|-|-|
| Specification | Calibration specification | Free text |
| Calibration date | Date of calibration | Date in form MM-DD-YYYY |
| Expire date | Date when the calibration expire | Date in form MM-DD-YYYY |
| Calibration A | Uncertainty of type A | Float |
| Calibration B | Uncertainty of type B | Float |
| Calibration C | ? | ? |
| Units | Units for Calibration A, Calibration B and Calibration C | Free text |
| Supplier | Supplier of the calibration | Free text |
| Certificate doc | URL to the calibration report | URL |
| Comment | Any specific comment related to the instrument calibration | Free text |

At any point new calibration is made the above the calibration table is updated.

If the instrument is complex its sub-componets/sub-instruments are reported with a multi-row table with the following columns:
| Column name | Column description | Column data type |
|-|-|-|
| Type | The sub-component / instrument type | String term from internal restricted vocabulary |
| PFV_no | Unique id of the sub-component/instrument | Auto-generated unique integer |
| PFV_type | Similar to Type but provided as an integer | Integer from predefined set of integers |
| Serial_number | A serial number of the sub-component/instrument provided by its manufacturer | Free text |
| Supplier | A supplier of the sub-component/instrument | Free text |
| Status | An ownership status of the instrument | String term from restricted vocabulary |
| Active | Indicates whether the sub-component/instrument is currently active or not | Boolean (Yes/No) |

## Mapping of internal instrumentation schema to PIDINST schema
The table below shows maping of PIDINST schema properties to the currently and ideally available properties in instruments\.windenergy\.dtu\.dk.


| PIDINST property ID | PIDINST property           | Current corresponding properties in instruments\.windenergy\.dtu\.dk                                                                 | Ideal corresponding properties in instruments\.windenergy\.dtu\.dk                                                                |
|---------------------|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| 1                   | Identifier                 | Serial\_number, PFV\_no                                                                                                              | DOI or ePIC                                                                                                                       |
| 1\.1                | identifierType             | serialNumber and inventoryNumber                                                                                                     | DOI or ePIC                                                                                                                       |
| 2                   | LandingPage                | https://instruments\.windenergy\.dtu\.dk/index\.php?page=show\_instrument&id=PFV\_no accessible only internally                      | Open access to https://instruments\.windenergy\.dtu\.dk/PFV\_type/PFV\_no/                                                        |
| 3                   | Name                       | Type                                                                                                                                 | Improved restricted vocabulary of intruments                                                                                      |
| 4                   | Owner                      | Automatically we can only either state DTU Wind Energy or indicate staff that ordered and\-or added changes to the instrument status | Should be DTU Wind Energy followed with ids of staff who built, maintaned and installed instrument                                |
| 4\.1                | ownerName                  | Ordered\_by, User\_id or DTU Wind Energy                                                                                             | Names of involved staff and institute name                                                                                        |
| 4\.2                | ownerContact               | Ordered\_by@dtu\.dk, User\_id@dtu\.dk                                                                                                | Email of staff and central email address of DTU Wind Energy                                                                       |
| 4\.3                | ownerIdentifier            | Internal phonebook ids                                                                                                               | ORCiD iDs of involved stuff, and ROR of DTU \(https://ror\.org/04qtj9h94\) preferable ROR of DTU Wind Energy \(to be registered\) |
| 4\.3\.1             | ownerIdentifierType        | Phonebook                                                                                                                            | ORCiD, ROR                                                                                                                        |
| 5                   | Manufacturer               |                                                                                                                                      |                                                                                                                                   |
| 5\.1                | manufacturerName           | Make                                                                                                                                 | Make                                                                                                                              |
| 5\.2                | manufacturerIdentifier     | manufacturer web site                                                                                                                | manufacturer web site                                                                                                             |
| 5\.2\.1             | manufacturerIdentifierType | URL                                                                                                                                  | URL                                                                                                                               |
| 5\.3                | modelName                  | Type                                                                                                                                 | Type                                                                                                                              |
| 6                   | Description                | Description                                                                                                                          | Description                                                                                                                       |
| 7                   | InstrumentType             | Type or PFV\_type                                                                                                                    | Restricted vocabulary of intrument types                                                                                          |
| 8                   | MeasuredVariable           | Units \(partially\)                                                                                                                  | Restricted vocabulary of variables                                                                                                |
| 9                   | Date                       | Date when instrument was acquired, calibrated, used, decomissioned                                                                   | An improved set of dates related to the instrument                                                                                |
| 9\.1                | dateType                   | Buy\_date, Date\_from, Date\_to, Calibration date, Expiration date                                                                   | Commissioned, Decommissioned, Calibration, \.\.\.                                                                                 |
| 10                  | RelatedIdentifier          | PFV\_no of subcomponents                                                                                                             | This would be calibration and technical reports, instrumentation papers, data as well subcomponents/instruments                   |
| 10\.1               | relatedIdentifierType      | PFV\_no                                                                                                                              | PIDs or URLs                                                                                                                      |
| 10\.2               | relationType               | HasComponent, IsComponentOf,                                                                                                         | PIDINST, DOI, URL                                                                                                                 |
| 11                  | AlternateIdentifier        | Serial\_number, PFV\_no                                                                                                              | Serial\_number, PFV\_no                                                                                                           |
| 11\.1               | alternateIdentifierType    | serialNumber and inventoryNumber                                                                                                     | serialNumber and inventoryNumber                                                                                                  |
We can see that adapting PIDINST out internal instrument database schema and its properties could be improved. 