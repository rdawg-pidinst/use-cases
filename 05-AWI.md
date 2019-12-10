# Use Case Description SENSOR.awi.de

Roland Koppe [1] and Ana Macario [2]  
April 6, 2018 


# Introduction


Over the last 2 decades, the Alfred Wegener Institute (AWI) Helmholtz Center for Polar and Marine Research has been continuously committed to develop and sustain an eResearch infrastructure for coherent discovery, view, dissemination, and archival of scientific data and related information in polar and marine regions. Most of the data collected by scientists originates from research activities carried out on a wide variety of research platforms operated by AWI (vessels, aircraft, stations, buoys, moorings, in-situ ocean floor stations, drones, and ocean floor crawling systems). Archival and publishing in the information system PANGAEA along with DOI assignment to individual datasets is a typical end-of-line for most data producers.

In order to address the increasing heterogeneity of research platforms and respective devices and sensors along with varying project-driven requirements, we built a generic and cost-effective framework, hereafter named O2A [3], intended to support the flow of sensor observation to archives. The modular and extensible components developed within this framework are in compliance with OGC standards, ensuring interoperability at international level.

In the context of this RDA Working Group, the main goal of SENSOR (Fig. 1) is to enhance the quality of published and archived data in PANGAEA by providing complete metadata and PIDs on sensors used in the data acquisition process.  SENSOR has been publicly available since 2015 as institutional repository and bi-annual release packages are being systematically implemented.  In the context of the upcoming MOSAiC project,  SENSOR will be used as a mandatory component  by all international partners.

Additional issues addressed in SENSOR are:

* Support to specific requirements from scientists meant to facilitate the scientific pipelines. Examples:
  * Integration of station lists from expeditions to action/event component (as part of the sensor provenance metadata)
  * Harmonization of various vocabularies with existing data acquisition systems on board of our vessels and stations (device names, types, parameters, units; adoption of SeaVox vocabularies)
* In-house inventory and management of platforms/devices/sensors
* Traceability of sensors in particular in regard to varying payloads for small vehicles (e.g. ROVs)
* Support for OGC interoperability standards, specifically SensorML and SOS

# Challenges

Given that platforms and sensors evolve in time (sensors are being calibrated, mounted/unmounted, etc), it is clearly important to trace changes applied to these over time. Having successfully integrated AWI Handle Server services with SENSOR, we are currently able to support:

* Sensor versioning, i.e. audit trail of changes
* Minting of persistent identifiers, generating UUIDs in the handle syntax.  
* Automated generation of a sensor citation

While tracking changes to platforms/devices/sensors is technically feasible, it became clear to us early on that in practice one has to decide which type of action/event (e.g. sensor calibration) warrants the creation of an individual version of a sensor (= a new PID).  We have intensively discussed the usability scenarios with AWI scientists in particular in regard to which types of actions/events associated with a sensor are relevant in the long run from data use perspective. Pragmatically, we have opted to (a) narrow down the scenarios in which metadata versioning takes place (including minting PIDs/handles), and, (b) „force“ certain changes to sensors to trigger the creation of a new version.  

To date the action/events which automatically lead to the creation of a PID are:  commission, mount, deployment and calibration.   In figure 2, we illustrate an example for PID  [https://hdl.handle.net/10013/sensor.664525cf-45b9-4969-bb88-91a1c5e97a5b](https://hdl.handle.net/10013/sensor.664525cf-45b9-4969-bb88-91a1c5e97a5b) related to a deployment event along with respective payload at that point in time (in this case a dive of the AUV “Paul” during an expedition from RV Merian in 2013 in the Arctic Ocean).  In this figure we also show how this PID has been linked in PANGAEA.de (as reference to the respective event (individual dive).  

We are in particular interested in working out together recommendations towards answering the following questions:

* When a PUID should/must be minted, recognizing that not all „hardware“ changes should necessarily lead to a new PUID (e.g. contrasting a simple battery change with a calibration procedure)?
* How would an „evolving“ citation for a sensor look like? Examples in the community, in particular for ARGO (dynamic) datasets could be considered.


# Metadata

ID = Numbering, 1, 2, 3 and sub properties with 1.1, 1.2 (akin to DataCite schema)

Property = Name of the property

Occurrence = 1 (mandatory) or 0-1 (optional at most once) or 0-n (optional multiple) or 1-n (at least one)

In metadata of = IP (Infrastructure Provider) or LP (Landing Page)


<table>
  <tr>
   <td><strong>ID</strong>
   </td>
   <td><strong>Property</strong>
   </td>
   <td><strong>Occ.</strong>
   </td>
   <td><strong>Definition</strong>
   </td>
   <td><strong>Datatype</strong>
   </td>
   <td><strong>In metadata of</strong>
   </td>
  </tr>
  <tr>
   <td>1
   </td>
   <td>Identifier
<p>
Additional identifiers:  serial number, asset number (from SAP),...
<p>
Also includes short and long names for instruments
   </td>
   <td>1
   </td>
   <td>
   </td>
   <td>PID, type hdl
<p>
Integer
   </td>
   <td>IP, LP
   </td>
  </tr>
  <tr>
   <td>2
   </td>
   <td>Manufacturer
<p>
+
<p>
Related model
   </td>
   <td>1
   </td>
   <td>
   </td>
   <td>String;  ideally PID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>3
   </td>
   <td>Description
   </td>
   <td>1
   </td>
   <td>
   </td>
   <td>String
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>4
   </td>
   <td>Instrument category
   </td>
   <td>1
   </td>
   <td>SDN Vocabulary, if applicable 
   </td>
   <td>PID, type URL
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>5
   </td>
   <td>Measurement properties (e.g. accuracy, resolution, min/max values, operation temperature,....); type and value
   </td>
   <td>0-n
   </td>
   <td>
   </td>
   <td>String, integer, real
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>6
   </td>
   <td>Contact (incl. Roles like owner)
   </td>
   <td>1-n
   </td>
   <td>
   </td>
   <td>Strong, ORCID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>7
   </td>
   <td>RelatedResources
   </td>
   <td>0-n
   </td>
   <td>Documents, user manuals, web pages
   </td>
   <td>PID, type DOI, hdl, URL,...
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>8
   </td>
   <td>Measured parameters
   </td>
   <td>1-n
   </td>
   <td>SDN Vocabulary, if applicable
   </td>
   <td>PID, type URL
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>9
   </td>
   <td>Actions (type, begin/end date, lat/lon/elevation/depth
<p>
Intern type vocaularies: comissioned, mounted, deployment, calibration, ...
   </td>
   <td>1-n
   </td>
   <td>
   </td>
   <td>String, real, integer
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>10
   </td>
   <td>Landing page (incl. citation)
   </td>
   <td>1
   </td>
   <td>
   </td>
   <td>PID, type hdl
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>11
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
</table>



<!-- Footnotes themselves at the bottom. -->
## Notes

[1] [Roland.Koppe@awi.de](mailto:Roland.Koppe@awi.de), ORCID: 0000-0002-2826-3932

[2] [Ana.Macario@awi.de](mailto:Ana.Macario@awi.de) , ORCID: 0000-0003-3747-793X

[3] O2A:  doi:[10.1109/OCEANS-Genova.2015.7271657](http://doi.org/10.1109/OCEANS-Genova.2015.7271657) 


<!-- Docs to Markdown version 1.0β17 -->
