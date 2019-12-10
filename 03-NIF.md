# Use Case Description National Imaging Facility 

Veah Tapat  
December 2017

# Introduction

The National Imaging Facility ([NIF](http://anif.org.au/)) is a national research infrastructure in Australia established through the National Collaborative Research Infrastructure Strategy ([NCRIS](https://www.education.gov.au/national-collaborative-research-infrastructure-strategy-ncris)). NIF provides a national network of state-of-the-art imaging capabilities and expertise, enabling research within three themes – Molecular Imaging & Radiochemistry, Human Imaging, and Plants, Animals, Materials Imaging distributed among 10 nodes throughout Australia. NIF delivers a nationally coordinated imaging capability which provides open access to more than 50 imaging modalities, informatics expertise, and curated data repositories.

# Persistent Identifiers in a Trusted Data Repository 

Recognizing that data acquisition and management differed across the 10 nodes, NIF engaged with the Australian National Data Services ([ANDS](www.ands.org.au)) and Research Data Services ([RDS](www.rds.org.au)) to develop a solution that ensured interoperability while recognizing the differences in practice. The resulting Trusted Data Repository (TDR) project aims to enhance the quality, durability and reliability of data that is generated at NIF facilities and to establish TDRs to ensure accessibility of the data, including metadata that documents the data quality and quality process, for a minimum of ten years.

The project produced a set of requirements to be satisfied in order for data to be “NIF Certified,” including acquisition from a “NIF-compliant instrument [1].”  Essential to the latter requirement is the need for an instrument to be assigned a unique identifier, referred to as the Instrument Unique Identifier (IUID), and registered with Research Data Australia (RDA). An example record can be seen here: [http://hdl.handle.net/102.100.100/50043](http://hdl.handle.net/102.100.100/50043). Further requirements of a NIF-compliant instrument include: 

* Documented quality control [2] (QC) process specific to the instrument, including definitions of quality assurance (QA) measures.
* Defined QC Project with an assigned Project Unique Identifier (PUID). The QC data for the instrument must be collected and the analysis uploaded to a NIF TDR service under the PUID. All QC documentation and associated QA measures are to be included under the same PUID. 

Under the definitions of this project, an instrument with a hardware upgrade is deemed to be a new instrument. Thus, it must be given a new IUID and be registered in the RDA.

NIF-certified data must also include NIF-minimal metadata, which is defined as: 

* Date and time of data acquisition
* PUID of the project to which the data belongs
* PUID of the QC Project for the instrument
* Description of the conversion tools used to generate the open data formats 
* Indication of whether or not the data is NIF-certified. 

# Persistent Identifiers for Research Infrastructure 

The Australian Government National Research Infrastructure Roadmap, released in 2016, emphasized the need for eResearch infrastructure to “take advantage of new and emerging technologies and digital methods [to] support the seamless retention, use, and reuse of research relevant data. [3]” 

As the status and identification of the instrumentation on which the data was acquired is critical to ensuring the value of data, a persistent identifier for research infrastructure offers the following:

* Reinforces that data can be TRUSTED by providing a record of quality control assurance
* Provides a framework that enables multi-centre imaging research projects
* Addresses requirements for quality management systems certification 
* Integrates and links to other persistent IDs - see RAiD [4], ORCID [5], DOI etc.
* Supports international collaborations, through transparency regarding quality of instrumentation  

While the TDR project was completed in December 2017, NIF and its partners remain committed to the extension of the project. Additional instruments will be integrated, including microscopy instruments from other clinical research facilities.

# Essential metadata

<table>
  <tr>
   <td><strong>Property</strong>
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
string that identifies the instrument. Currently this is a Handle ID
   </td>
   <td>PID
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
   <td>Description
   </td>
   <td>0..1
   </td>
   <td>Text Description of Instrument State.  \
 \
This allows to define the status of sub-components of an instrument (gradients, coils, acquisitions software version)
   </td>
   <td>String
   </td>
   <td>
   </td>
  </tr>
</table>

## Notes

[1] NAP - [preclinical Imaging](https://docs.google.com/document/d/171sWgML7ujurvAfkPJS0nFUjmRVorkaMnFOoqtpTtKE/edit?usp=sharing) 

[2] Where possible, QC processes should be standardized across NIF nodes with same or similar instruments

[3] https://www.education.gov.au/2016-national-research-infrastructure-roadmap

[4] RAiD - www.raid.org.au

[5] ORCiD - www.orcid.org


<!-- Docs to Markdown version 1.0β17 -->
