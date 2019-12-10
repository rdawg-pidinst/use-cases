# Use Case Description “marine SWE group”


Robert Huber et al.  
May 2018


# Introduction

Over the last years, marine organisations, projects and communities have been working towards standardisation of sensor data and metadata by implementing OGC Sensor Web Enablement (SWE) standards. To avoid interoperability issues in OGC SWE implementations within the marine community, an agreement was needed on how to apply SWE concepts and how to use vocabularies in a common way that would be shared by different projects, implementations, and users.

The SWE Marine Profiles group was created as a solution to the above mentioned need. The group involves partners from several projects and initiatives (AODN, BRIDGES, EMSO, ENVRIplus, EUROFLEETS/EUROFLEETS2, FixO3, FRAM, IOOS, Jerico/Jerico-Next, NeXOS, ODIP/ODIP II, RITMARE, SeaDataNet, SenseOcean, X-DOMES) who joined forces to develop common marine profiles of OGC SWE standards that can be used in multiple projects and organizations.


# Use Case

The group has identified some key areas in sensor descriptions of platform models, their instances, sensor models and sensor instances. One of the main foci was the provision of key vocabularies that cover six SensorML sections, namely the History, Capabilities, Characteristics, Classification, Identification and Contacts.

Identification of sensors is of key importance for the marine SWE group. A dedicated vocabulary has been agreed on and published at [http://vocab.nerc.ac.uk/collection/W07/current/](http://vocab.nerc.ac.uk/collection/W07/current/) in order to allow to distinguish between the different levels of identifications for sensors, platforms and their instances such as ‘Model number’, ‘Serial number’ and ‘Unique ID’. The latter illustrates the interest of this WG. 

The particular challenge we identify is to agree on and introduce a common persistent identifier system for marine sensors and platforms within the marine community and at the same time agree on a core set of metadata elements which allow full compatibility with other communities.


# Essential metadata

<table>
  <tr>
   <td>
<strong>Property</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td><strong>Definition</strong>
   </td>
   <td><strong>Datatype</strong>
   </td>
   <td><strong>In metadata of</strong>
   </td>
  </tr>
  <tr>
   <td>Identifier
   </td>
   <td>1
   </td>
   <td>The Identifier is a unique
<p>
string that identifies the instrument instance
   </td>
   <td>PID
   </td>
   <td>IP
   </td>
  </tr>
  <tr>
   <td>Inventory Number
   </td>
   <td>0..1
   </td>
   <td>The identifier registered in the owner institution’s device or asset catalogs or management systems
   </td>
   <td>String or PID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Local Name
   </td>
   <td>0..1
   </td>
   <td>The title of the instrument instance used within the institution e.g. ‘John’s CTD’’
   </td>
   <td>String
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Manufacturer
   </td>
   <td>1
   </td>
   <td>The manufacturer name
   </td>
   <td>String or PID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Manufacturer Identifier
   </td>
   <td>0..1
   </td>
   <td>The number/id given to the sensor product by the manufacturer.
<p>
Aka: manufacturer part number
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Model Name
   </td>
   <td>1
   </td>
   <td>The model name given by the instrument’s manufacturer
   </td>
   <td>String
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Serial Number
   </td>
   <td>1
   </td>
   <td>Serial number issued to the instrument instance by the manufacturer
   </td>
   <td>String
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Instrument Category
   </td>
   <td>0..n
   </td>
   <td>A category for the instrument such as ‘CTD’. Preferred PID is from the SDN vocabulary for instruments
   </td>
   <td>PID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Observable Property
   </td>
   <td>0..n
   </td>
   <td>Aka: Measurable Property
   </td>
   <td>String
   </td>
   <td>
   </td>
  </tr>
</table>



<!-- Docs to Markdown version 1.0β17 -->
