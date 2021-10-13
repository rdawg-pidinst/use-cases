# PIDs for Instruments Sensor Community Use-Case
## Gesellschaft für wissenschaftliche Datenverarbeitung Göttingen, Sensor Community Use-Case

Sven Bingert (sven.bingert@gwdg.de ORCID [0000-0001-9547-1582](https://orcid.org/0000-0001-9547-1582))
Jakob Hördt (j.hoerdt@stud.uni-goettingen.de ORCID [0000-0001-5559-0368](https://orcid.org/0000-0001-5559-0368))


October 2021

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
Following: https://dtr-test.pidconsortium.eu/#objects/21.T11148/17ce618137e697852ea6

Example pids:
- https://hdl.handle.net/21.11138/7b58b582-096a-4fd8-a966-8d01e589a95b?noredirect
- https://hdl.handle.net/21.11138/a6442237-381e-4e97-92f7-74b7749350da?noredirect

PIDINST property ID|PIDINST property|current implementation|Potential improvements
----------|----------|----------|----------
1|Identifier|PIDINST|
2|LandingPage|https://sensor.community|https://sensordata.open-forecast.eu/devices/{Identifier} or similar template uri
3|Name|sensor_id|
4|Owners||Simple form could allow citizen scientists to identify with the sensor, increasing visibility and identification with the project.
4.1|Owner||
4.1.1|ownerName|SensorCommunity|
4.1.2|ownerContact|contact@open-forecast.eu|
4.1.3|ownerIdentifier||
4.2|Owner||
4.2.1|ownerName||Can be declared using form.
4.2.2|ownerContact||Email address of citizen scientist who owns the sensor. Obtained through form.
5|Manufacturers|Manufacturer of the sensor component derived from the known sensor_type|
5.1|Manufacturer||
5.1.1|manufacturerName||
5.1.2|manufacturerIdentifier|not present|determine Identifiers for the small number of possible Manufacturers
6|Model||
6.1|modelIdentifier|sensor_type eg. SDS011|find out an Identifier for the sensor_type
6.2|modelName|sensor_type|
7|Description|Technical description shared by all sensors of the same sensor_type and a Datasheet URL if available|
8|InstrumentType|Sensor classification, eg. Weather sensor, fine dust sensor. Derived from sensor_type.|
8|MeasuredVariables|list of measured variables, derived from sensor_type. Currently a subset of [pressure, altitude, pressure_sealevel, temperature, humidity, PM10, PM2.5, noise_LAeq, noise_LA_min, noise_LA_max, noise_LA01, noise_LA95, P0, durP1, ratioP1, durP2, ratioP2, counts_per_minute, hv_pulses, tube, counts, sample_time_ms, P4, N10, N4, N25, N1, N05, TS, co2_ppm]|a description for each variable could be helpful
9|Dates|Only the earliest and latest measurement dates are known. first_msg is taken as Commissioned, last_msg is given as another date without a dateType|BuyDate, Commissioned, Decommissioned. BuyDate could be declared by citizen scientists through form
10|RelatedIdentifiers|not implemented|A station id called location is known for every sensor that is attached to it. Could also put sibling sensors here.
11|AlternateIdentifiers|no use|
