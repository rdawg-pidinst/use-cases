# British Oceanographic Data Centre (BODC) Use Case


Louise Darroch (lorr@bodc.ac.uk), Justin Buck and James Ayliffe  
July 2018

# Rationalisation

The British Oceanographic Data Centre (BODC) is located in the UK and is a national facility responsible for looking after and distributing data concerning the marine environment. It primarily deals with biological, chemical, physical and geophysical data and holds over 118,000 data series in their databases which are discoverable via web interfaces and web services (e.g. Sensor Web Enablement Sensor Observation Services). BODC hosts the NERC Vocabulary Server (NVS), which publishes over 240 vocabulary collections (list of standardised terms) represented in the Simple Knowledge Organisation System (SKOS) and Linked Data Resource Description Framework (RDF). They are responsible for hosting and maintaining vocabulary collections of instrument models (static entities), L22 (SeaVoX Device Catalogue) and categories, L05 (SeaDataNet device categories).

A persistent identifier for instrument instances would be of benefit to BODC for the following reasons:


## Enhance data ingestion efficiency

Compiling metadata about datasets can be time-consuming, especially when we often receive only sub-sets of information. Identifiers which can unambiguously identify instruments used and their associated will help in this process.


## Semantic interoperability

Much of BODC’s metadata is standardised to allow for semantic interoperability, maximise discovery and allow machines to assess if data is fit for purpose. A globally unique identifier with standardised metadata element sets will enhance semantic interoperability and improve discoverability through our search portals or web services. It will also allow BODC to easily link data to instances and their associated metadata (in machine readable form), allowing end-users to assess if data is fit for purpose. We will also be able to link instances to instrument model entities in L22 completing the semantic chain.


## Automated workflows

Globally unique identifiers and associated metadata that are machine readable will facilitate their integration into automated workflows, such as the transfer of data from source formats into bodc formats (e.g. glider data in APDS) or applying calibrations during QA/QC of a ship’s underway dataset (ships underway workflow is in development at BODC).


## Sensor Web Enablement (SWE)/Linked Data Semantic Sensor Network (SSN) ontology

As part of the EU’s SenseOCEAN project, BODC developed a system to make sensors and their data discoverable and accessible in the web through standardised APIs (sensor nodes) using OGC SWE and W3C’s Linked Data/SSN (Marine Linked Systems). The system currently relies on Universally Unique Identifiers (UUIDs) to identify sensor instances, match an instance’s metadata to its data and publish the information on the web. A globally unique identifier will help harmonise our sensor nodes with the rest of the world, a key aspect of the semantic sensor web. Sensor catalogues are actively being developed by different groups (EMSO, BODC, AWI, Ifremer, NOC-OBE for the PAP stie, etc) and OGC SWE enabled sensors will also output standardised metadata descriptions, semantic interoperability of these repository outputs will enable the use and ingestion of the metadata regardless of which group hosts it.


## PID publication

BODC has the capability to mint and publish Digital Object Identifiers (DOI) that are registered at DataCite. Expanding the service to the publication of instrument instances will offer our users a wider service and extend our reputation in the community. Publishing the PID makes BODC hosted instances of sensors globally unique which is a fundamental requirement of the PID for sensors concept.


## FAIR findability

Integrating persistent identifiers into BODC will contribute to FAIR findability and the provenance criteria of reusability.


# Requirements



*   Must allow tools to leverage the content for the semantic web by:
    *   enhancing semantic interoperability by accommodating community specific identifiers such as controlled vocabularies which are used extensively in the marine community. These may be in URI form.
    *   allowing for relationships so users can organise information in discovery catalogues or machine-readable ontologies e.g. instance belongs to instrument class; LongName has manufacturer etc.
*   Metadata elements must allow the identification of the instance to be unambiguous
*   The identifier must be web resolvable
*   URI needs to resolve to a landing page that includes content negotiation to resolve machine readable metadata (depending on the call made)


# Concerns/risks



*   Handling evolution and versions of instrument instances – who will be responsible? How will this be determined?
*   Handling deprecation of instrument instances – who will be responsible? How will this be determined?
*   The potential for different interpretations of an instrument – how do we constrain this?
*   The resource involved in implementing and handling legacy (i.e. linkages between instruments and legacy datasets will probably require funding)


# Primary metadata element set for BODC 

This is a list of metadata that are specific to BODC (essentially our metadata requirements). They are also what we think are important to be included in a DOI metadata schema in order to locate instrument instances with little ambiguity. They are also metadata that we think could be easily consumed by end-users in local applications. In order to keep things simple we have not attempted to map them to DataCITE properties and sub-properties


<table>
  <tr>
   <td><strong>Identifier</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td><strong>Comment</strong>
   </td>
  </tr>
  <tr>
   <td>Persistent Identifier
   </td>
   <td>Globally unique identifier
   </td>
   <td>1
   </td>
   <td>PID
   </td>
  </tr>
  <tr>
   <td>Alt Instance Identifier
   </td>
   <td>An alternative identifier such as a local identifier e.g. an inventory number
   </td>
   <td>0..1
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Long Name
   </td>
   <td>The full instrument instance name
   </td>
   <td>1
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Manufacturer Serial No.
   </td>
   <td>The part number of the design
   </td>
   <td>0..1
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Model Name
   </td>
   <td>The model design (e.g. 4135) that the instance is based on.
   </td>
   <td>0..1
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Manufacturer Name
   </td>
   <td>The device manufacturer or developer (e.g. Chelsea, University of Washington etc.)
<p>
http://vocab.nerc.ac.uk/collection/L35/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Device Type
   </td>
   <td>A community-specific identification of the system/model (e.g. L22). Allows for broader relationships
<p>
http://vocab.nerc.ac.uk/collection/L22/current/
   </td>
   <td>0..1
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Device Category
   </td>
   <td>A community-specific identifier for the classification of the instrument instance.
<p>
http://vocab.nerc.ac.uk/collection/L05/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Owner Organisation
   </td>
   <td>Organisation name (we need to think about compliance with GDPR)
<p>
http://vocab.nerc.ac.uk/collection/B75/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Valid From
   </td>
   <td>from when this instance is true
   </td>
   <td>0..1
   </td>
   <td>date
   </td>
  </tr>
  <tr>
   <td>Valid To
   </td>
   <td>To when this instance is true
   </td>
   <td>0..1
   </td>
   <td>date
   </td>
  </tr>
  <tr>
   <td>Description
   </td>
   <td>General description of the instance to help in identification
   </td>
   <td>0..1
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Output
   </td>
   <td>Outputs will help with machine semantic interoperability
<p>
http://vocab.nerc.ac.uk/collection/P01/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Publisher
   </td>
   <td>The centre responsible for creating the DOI
   </td>
   <td>1
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Publication Year
   </td>
   <td>The year published
   </td>
   <td>1
   </td>
   <td>date
   </td>
  </tr>
  <tr>
   <td>Resource Type
   </td>
   <td>Indicates this is an instrument PID (Specified by RDA group or PID provider)
   </td>
   <td>1..n
   </td>
   <td>Controlled list of values:
<p>
Physical object,
<p>
Instrument PID
   </td>
  </tr>
</table>



# Secondary metadata element set for BODC


<table>
  <tr>
   <td><strong>Identifier</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Characteristic
   </td>
   <td>An instrument’s characteristic. Requires sub-properties (e.g. weight)
<p>
http://vocab.nerc.ac.uk/collection/W05/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Capability
   </td>
   <td>An instrument’s capability. Requires sub-properties (e.g. accuracy)
<p>
http://vocab.nerc.ac.uk/collection/W04/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Event
   </td>
   <td>An event in an instrument’s lifecycle. Requires sub-properties (e.g. Calibration, Calibration Valid From etc.)
<p>
http://vocab.nerc.ac.uk/collection/W03/current/
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>Sub Model Name
   </td>
   <td>The sub-model or version of the design.
   </td>
   <td>0..1
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Device Type
   </td>
   <td>The type of instrument (e.g. oxygen optode). This is more granular than the DeviceCategory.
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
  <tr>
   <td>Instance Reference
   </td>
   <td>A model design reference (e.g. Turner et al. 1994). Can apply to older instances that were not mass produced.
   </td>
   <td>0..n
   </td>
   <td>free text
   </td>
  </tr>
  <tr>
   <td>Funding reference
   </td>
   <td>Name of the funding body. Our instruments are owned by the National Capability Centre which is funded by the Natural Environment Research Council
   </td>
   <td>0..n
   </td>
   <td>standardised term or free text
   </td>
  </tr>
</table>



<!-- Docs to Markdown version 1.0β17 -->
