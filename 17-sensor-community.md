# PIDs for Instruments Use-Case

Following: http://dtr-test.pidconsortium.eu/#objects/21.T11148/17ce618137e697852ea6


## Gesellschaft für wissenschaftliche Datenverarbeitung Göttingen, Community Use-Case

Sven Bingert (sven.bingert@gwdg.de ORCID [0000-0001-9547-1582](https://orcid.org/0000-0001-9547-1582))
Jakob Hördt (j.hoerdt@stud.uni-goettingen.de ORCID [0000-0001-5559-0368](https://orcid.org/0000-0001-5559-0368))


July 2020

### Introduction

Sensor.Community (https://sensor.community/en/) is a contributors driven global sensor network that creates Open Environmental Data.
The network consists of over 12.000 sensors each measuring several different values, e.g. air pollution, noise or climate information such as temperatures.
In this citizen science project any of us can purchase a sensor, mount it at a place of interest and share the data with the community.
The typical sensor setup is very cheap (about 50,-euros).

The goal is to include citizen science projects, collect environmental data on a large scale and provide them as open data.

### Motivation for PIDINST implementation

By implementing PIDINST we aim for higher visibility of the project and the data.
Standardized sensor meta data will allow a better understanding of available measurement data and therefore support a more targeted search for measurements, which can be used in different analysis workflows.
By including the citizen scientists (the owners of the sensors) in the meta data collection process (e.g. contact details), a higher 
identification with the community can be achieved.


### Measurements standardization
The current standardization is driven by the development of the sensor firmware and
the central data collection end point.


### Implementation PIDINST schema


PIDINST property ID | PIDINST property<br>     | equivalent sensor.community property                                                                              | Potential improvements
--------------------|--------------------------|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
1                   | Identifier               | sensor_id                                                                                                         | PIDINST
2                   | LandingPage              | https://sensor.community                                                                                          | https://sensor.community/devices/{Identifier} or similar template uri
3                   | Name                     | sensor_type                                                                                                       |
4                   | Owners                   |                                                                                                                   | Simple form allows citizen scientists to identify with the sensor, increasing visibility and identification with the project. If not provided by the owner, the sensor.community can be used instead or in addition to citizen scientis contact.
4.1                 | Owner                    | sensor.community                                                                                                  |
4.1.1               | ownerName                | sensor.community                                                                                                  |
4.1.2               | ownerContact             | contact@sensor.community                                                                                          |
4.1.3               | ownerIdentifier          |                                                                                                                   |
4.2                 | Owner                    | Currently private                                                                                                 |
4.2.1               | ownerName                | Name of the citizen scientist                                                                                     | Can be declared using form.
4.2.2               | ownerContact             |                                                                                                                   | Email address of citizen scientist who owns the sensor. Obtained through form.
5                   | Manufacturers            |                                                                                                                   |
5.1                 | Manufacturer             | Currently private                                                                                                 | Manufacturer information also acquired through form that citizen scientists fill out.
5.1.1               | manufacturerName         |                                                                                                                   |
5.1.2               | manufacturerIdentifier   |                                                                                                                   |
5.1.3               | modelName                | Only a few types of boards are distributed, but this is still private like the rest of the Manufacturer property. |
6                   | Description              | Technical description shared by all sensors of the same sensor_type                                               |
7                   | InstrumentType           | Sensor class, eg. Weather sensor, or fine dust sensor. Derived from sensor_type.                                  |
8                   | MeasuredVariables        | Derived from sensor_type, a dht22 sensor for example measures the values temperature and humidity.                |
8.1                 | MeasuredVariable         | eg. temperature                                                                                                   |
9                   | Dates                    | Commissioned and Decommissioned are known.                                                                        | BuyDate, Commissioned, Decommissioned. BuyDate can be declared by citizen scientists through form
9.1                 | Date                     | first_msg                                                                                                         |
9.2                 | Date                     | last_msg                                                                                                          |
9.3                 | Date                     |                                                                                                                   |
10                  | RelatedIdentifiers       |                                                                                                                   |
10.1                | RelatedIdentifier        | A station id called location is known for every sensor that is attached to it.                                    | The id of the station this sensor belongs to.
10.1.1              | relatedIdentifierValue   | location                                                                                                          | location
10.1.2              | relatedIdentifierType    |                                                                                                                   | other-Identifier
10.1.3              | relationType             | BELONGS_TO                                                                                                        | isComponentOf
10.2                | RelatedIdentifier        |                                                                                                                   | PIDINST of the sensors (multiple possible), that share a station with this sensor
10.2.1              | relatedIdentifierValue   | sensor_id (of sibling sensor)                                                                                     | PIDINST
10.2.2              | relatedIdentifierType    |                                                                                                                   | "PIDINST"
10.2.3              | relationType             |                                                                                                                   | isSibling
11                  | AlternateIdentifiers     |                                                                                                                   |
11.1                | AlternateIdentifier      |                                                                                                                   |
11.1.1              | alternateIdentifierValue | sensor_id                                                                                                         |
11.1.2              | alternateIdentifierType  |                                                                                                                   | other-Identifier
