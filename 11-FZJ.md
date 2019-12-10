# Use Case Description Central Library of Forschungszentrum Jülich

Claudia Frick  
31 July 2018
 
This document describes how persistent identification of instruments may be used in the Central Library of Forschungszentrum Jülich [1]. There are currently two useful purposes which will be described individually before a combined set of meta data is presented that would be required for both purposes.

## Journal of large-scale research facilities (JLSRF)

The Journal of large-scale research facilities (JLSRF) [2] publishes articles describing large-scale scientific equipment. This covers large-scale equipment from all scientific disciplines that is intended to be used by scientists who are not affiliated to the institution operating the facilities (dedicated user operation). The articles in JLSRF provide scientists with a simple means to reference large-scale facilities in their publications. In their terms of use, operators of large-scale equipment can refer to the respective article in JLSRF. All articles are published in the name of the operating institution (corporate author) and not by an individual author. If appropriate, individual subunits of a large-scale research facility, such as the different detectors at a particle accelerator, can also be described separately.

If an instrument would have a PID, it could be stated in the description published in JLSRF. Additionally, the DOI of the published description should be deposited in the PID metadata. Ideally, this should be a one-to-one link. To ensure this, an appropriate workflow should be set up.

## Bibliometrics

The Central Library tailors bibliometric analyses to suit the specific needs of every request. Among other things, the team Data & Metrics of the Central Library offers bibliometric analyses of research institutions, citation analyses of institutes and working groups, and network analyses [3].

There is a large need to identify all publications related to an instrument. Even though the identification of these articles is completely addressed by citing the JLSRF article of the instrument, a linked instrument PID could provide further machine readable input information to improve these kind of analyses. The PID could be linked via the DOI, be part of the citation or mentioned in the acknowledgement which is indexed by Web of Science.

## Risks

Besides the benefits, there might also be some risks related to setting up complementary systems for machine-readable (instrument PIDs) and human-readable (JLSRF) information on one instrument. For example, asking scientists to cite the description of the instrument in JLSRF and to include the instrument PID might lead to a random selection of doing both, only cite the JLSRF description, only include the instrument PID or neither of them.

## Meta data

<table>
  <tr>
   <td><strong>Property</strong>
   </td>
   <td><strong>Occurence</strong>
   </td>
   <td><strong>Definition</strong>
   </td>
   <td><strong>Subfields</strong>
   </td>
   <td><strong>Datatypes</strong>
   </td>
  </tr>
  <tr>
   <td>Instrument identification
   </td>
   <td>1
   </td>
   <td>Information directly identifying the instrument
   </td>
   <td>Name, PID, DOI of instrument description in JLSRF, URL, date of installation, date of shutdown, version number (see Related instruments), type of the instrument (classification needed)
   </td>
   <td>Text, URL, ID, ISO 8601, numeric
   </td>
  </tr>
  <tr>
   <td>Ownership
   </td>
   <td>1-n
   </td>
   <td>Information about the ownership including history of ownership, i.e. one entry for each past or current owner
   </td>
   <td>Name, ID of the owner (e.g. GRID, ISNI or Ringgold ID), Country, beginning of ownership, end of ownership
   </td>
   <td>Text, ID, ISO 3166, ISO 8601
   </td>
  </tr>
  <tr>
   <td>Contact
   </td>
   <td>1-n
   </td>
   <td>Contact information, might be people or generic contact addresses
   </td>
   <td>Name, e-mail, phone, institution, ID of the institution (see ID of owner)
   </td>
   <td>Text, ID
   </td>
  </tr>
  <tr>
   <td>Related instruments
   </td>
   <td>1-n
   </td>
   <td>Links to predecessors to successors, but also to parents and childs for subunits
   </td>
   <td>Name, PID
   </td>
   <td>Text, ID
   </td>
  </tr>
</table>


## References


[1] Central Library of Forschungszentrum Jülich. [http://fz-juelich.de/zb/EN/Home/home_node.html](http://fz-juelich.de/zb/EN/Home/home_node.html)  

[2] Journal of large-scale research facilities (JLSRF). [https://jlsrf.org](https://jlsrf.org)

[3] Bibliometrics in the Central Library of Forschungszentrum Jülich. [https://fz-juelich.de/zb/EN/Expertise/bibliometrics/bibliometrics_node.html](https://fz-juelich.de/zb/EN/Expertise/bibliometrics/bibliometrics_node.html)

 


<!-- Docs to Markdown version 1.0β17 -->
