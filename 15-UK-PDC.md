# UK Polar Data Centre (UK PDC) Use Case


Alex Tate (ajtate@bas.ac.uk)  
Feb 2019

# Introduction

The UK Polar Data Centre is located at the British Antarctic Survey in Cambridge and is responsible for managing and distributing environmental data collected within the polar regions primarily by NERC funded researchers. As a data centre constrained by spatial extent rather than scientific domain, we deal with a very wide range of data produced by an equally wide range of instruments and sensors. The UK PDC works closely with other UK-based environmental data centres, especially the British Oceanographic Data Centre and utilises the vocabularies made available in the NERC Vocabulary Server. While the UK PDC is a long-term archive for polar datasets, data centre staff are very much involved in operational data management, working with engineers and scientists in the early stages of sensor design and often being deployed in the field (mainly ships and bases) to ensure data are acquired in a manner that reduces issues with their long-term management. 

From the UK PDC perspective there are two main use cases for having persistent identifiers for instruments, as a creator and documenter of instruments and a repository/curator of datasets collected by others.


# Use case 1 – instrument creator/documenter

In this use case data centre staff are either working directly with hardware and software engineers to create new instruments or are present during data acquisition and are recording instrument configurations. This could be compound instruments (e.g. recording the setup of a ‘CTD’) or the creation of a single component such as a daylight sensor for bird tracking. 

The ability to assign a global identifier to instruments and to describe them using internationally accepted metadata elements would facilitate interoperability in a number of different areas including:

**Operational processes** – This mainly refers to integration of PIDs within asset management systems used for instrument maintenance and stock management. Engineers and technicians typically populate and manage these data but this has often happened in isolation from data management processed. PIDs won’t entirely solve this disconnect but will help the two groups work more closely when creating instrument metadata.

**UK PDC data management** – Instrument PIDs and metadata form a key part of the provenance of any resulting dataset and many received requests are based on searches for data collected by particular instrument configurations.  A consistent way of identifying instruments and onward linkages to information around calibrations etc. will allow consumers of the data (humans and machines) to better understand provenance and data quality. 

**Other data centres or data aggregators (e.g. BODC)** – In many cases NERC data collected in the polar regions are aggregated regionally or within scientific domains, often at a very early stage in the data management lifecycle (e.g. streamed in near-real time from the platform). As an operational data centre we would like to reduce the effort expended by data aggregators in assimilating data collected in the polar regions, especially through the ships, planes and bases that we directly support. If by adopting an internationally agreed set of instrument metadata we can significantly reduce effort elsewhere, then we will certainly do so.


# Use case 2 – data curator

The UK PDC also acts in a more familiar data centre role, providing advice to a range of data collecting projects and integrating resulting datasets into a long-term archive for onward dissemination to various user communities. In this use case we are typically not involved in the data acquisition phase, nor have any involvement in the design, maintenance or ongoing documentation of the data collecting instruments. However, we are in a position to champion instrument PIDs and metadata in dialogue with external organisations and these recommendations are always easier to sell if they form part of an internationally agreed standard. As in the use case 1, implementation of PIDs (by third party data collectors) will reduce data centre effort when ingesting data.


# Implementation issues of concern

**Granularity** - Already noted by the RDA working group but critical in the uptake of any instrument PID schema, especially when we rely on non-data management staff for the creation of PIDs and instrument metadata. Possibly require domain best practice examples, rather than strict across-the-board rules.

**Responsibility** – Who should be responsible for minting and maintaining instrument PIDs? What do you do about the inevitable ‘duplication’ of PIDs when multiple organisations (especially data aggregators) describe the self-same instrument is slightly different ways.

**Lineage** – When does an instrument entity morph into a new entity rather than a new version? When a sensor is added/removed/upgraded? When an instrument stays the same but moves group/organisation/funding body? When hardware stays the same but software changes? In the same vein, when does an instrument entity cease to be? 

**Bespoke instruments** – A large proportion (volume and size) of datasets are produced by off-the-shelf sensors and instruments where much of the metadata can be found directly from manufacturer datasheets (possibly in the future manufacturers could provide PIDs and metadata upfront). However many bespoke instrument configurations exist and these require the most effort to document and need additional thought to facilitate any possible interoperability. This is especially true of many mechanical devices such as marine trawling nets, sediment corers, ecological quadrats etc. which cannot be described simply as a series of (well documented) electronic sensor sub-components. Similarly, compound instruments are difficult to describe where sub-component details are not provided or known.

**Humans as sensors** – Despite their very wide variability, human observations are often all lumped together in sensor/instrument controlled vocabularies. Possibly outside the scope of the RDA working group but many datasets exist as they do because human ‘a’ made the observation rather than human ‘b’. 

**Similar regional/global efforts**

Linkages (or at least acknowledgement) should be made with similar exercises currently being undertaken outside of the RDA. This is especially true for efforts that fall mostly outside the scientific research domain e.g. Identifiers in Internet of Things ([https://aioti.eu/wp-content/uploads/2018/03/AIOTI-Identifiers_in_IoT-1_0.pdf.pdf](https://aioti.eu/wp-content/uploads/2018/03/AIOTI-Identifiers_in_IoT-1_0.pdf.pdf)).


# Primary metadata elements (from BODC use case submission) 

Rather than reinvent the wheel we have taken the list provided by BODC and annotated it with extra comments to show agreement with our use cases. Given that one of our use cases is making BODC’s life easier it stands to reason that we would wish to support their requirements.


<table>
  <tr>
   <td><strong>Identifier</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td><strong>BODC Comment</strong>
   </td>
   <td><strong>UK PDC Comment</strong>
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
   <td>Agreed
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
   <td>Agreed but possibly 0..n
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed but often not easy to work out especially in tiered governmental organisations
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed. A PID specific DOI in this case
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
   <td>Agreed
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
   <td>Agreed
   </td>
  </tr>
</table>



# Secondary metadata elements (from BODC use case submission) 


<table>
  <tr>
   <td><strong>Identifier</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td><strong>BODC Comment</strong>
   </td>
   <td><strong>UK PDC Comment</strong>
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed but care needed with the overloaded term, ‘event’ 
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed
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
   <td>Agreed 
   </td>
  </tr>
</table>



<!-- Docs to Markdown version 1.0β17 -->
