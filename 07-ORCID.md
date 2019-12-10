# ORCID Use case for PIDINST


Tom Demeranville  
May 2018


## Summary {#summary}

ORCID is developing the ability to recognise access and use of large scale facilities and infrastructure within the ORCID record.  This document describes our proposed implementation and rationale.

At launch ORCID expects users of this new functionality to use existing identifier infrastructure such as RRIDs (Research Resource Identifiers [1]), Handles, DOIs and even plain URIs to reference infrastructure and facilities, but will incorporate the outputs of the PIDINST WG as they are released.


## 1.0 Background {#1-0-background}

At present, the ORCID record contains sections for listing Affiliations, Works, Funding, and Peer Review.  A recent ORCID-supported working group [2] charged with developing workflows for acknowledging User Facilities (see Report [3]) found that facilities are distinct from both affiliations and funding.  In that work, a draft JATS xml schema for publishers created a distinct section to capture facilities, collections, and research resources (see Table 1, below). 


## 2.0 Proposal for a new ORCID record section {#2-0-proposal-for-a-new-orcid-record-section}

ORCID will create a new section, called “Research Resources” in the ORCID record to hold information about “things that researchers use for their research”.  The section will contain connections to resources that are not generally cited by researchers within article reference lists, which will vary by domain. **These connections require that the resource be associated with a persistent identifier** [4]**, preferably one that is resolvable to a landing page with more information about the resource.**  In addition, updating an ORCID record requires explicit record holder permission, so there must be an API-mediated process during which the researcher’s ORCID iD can be authenticated and read/write permissions collected.  This scopes the resources included in this section to those_ that require a specific proposal process or credential to access_. With this caveat, this section would hold information about the resources listed in the following table:

 


<table>
  <tr>
   <td><strong>Resource Type</strong> [5]
   </td>
   <td><strong>Definition</strong>
   </td>
   <td><strong>Examples</strong>
   </td>
  </tr>
  <tr>
   <td>Infrastructure
   </td>
   <td>A facility, building, or other physical space used to perform research. 
   </td>
   <td>Neutron spallation source, animal facility, data enclave, archaeological site, telescope array. ships, planes, farms, laboratories
   </td>
  </tr>
  <tr>
   <td>Collection [6]
   </td>
   <td>An object or group of objects used for research purposes; can be tangible or digital. 
   </td>
   <td>Ocean mission, field campaign, collaborative data sets or resources, rare book collection; museum collection, biological specimen collection
   </td>
  </tr>
  <tr>
   <td>Equipment [7]
   </td>
   <td>Hardware used for research purposes
   </td>
   <td>Microscope, computers, glassware, samples, materials
   </td>
  </tr>
  <tr>
   <td>Service
   </td>
   <td>Services used for research purposes
   </td>
   <td>Proteomics analysis, computing services, data analysis, logistical support, legal services, copyediting, expert or staff advisement. 
   </td>
  </tr>
</table>


** Table 1.  Resource types**


## 3.0 Data fields {#3-0-data-fields}

ORCID strives to make connections between identifiers using the minimal amount of metadata.  Our goal is to enable the creation, storage, and sharing of iD-ID connections with trusted provenance.  Ideally, creation of iD-resource connections would occur as a researcher shares their ORCID iD in a research workflow, such as a permit or credentialing process to request access to a resource. Information about the resource would be posted into the ORCID record by the resource host when access is granted.  And, the metadata record would be shared as a researcher creates an output based on their use of the resource.


### 3.1 Proposal/Project Metadata {#3-1-proposal-project-metadata}

These are the data fields collected and stored by Resource and/or Proposal Host, detailed in the User Facilities and Publications Working Group Report. 


#### 3.1.1 Required {#3-1-1-required}

*   **Researcher(s) **This is the name of the person(s) submitting or associated with the proposal and the associated unique identifier for the researcher, expressed as a URI with the format [https://orcid.org/####-####-####-####](https://orcid.org/####-####-####-####).
    *   **Researcher(s) Name**
    *   **ORCID iD**
    *   **Researcher Host **
        *   **Institution Name**
        *   **Organization ID**. This is the home organization(s) of the Researcher(s) performing work at the Resource.  For intramural researchers, this will be the same as the Resource Host institution.  The ID uniquely identifies the organization and should resolve to a to a public description (landing page) of the organization.
*   **Proposal / Registration**
    *   **Proposal Title/Registration**. This is the public title of the proposal or registration the researcher submitted to access a resource. 
    *   **Proposal/Registration Unique Identifier.**  This is an external persistent identifier assigned by the Proposal or Resource Host to a proposal/project or registration.  Should resolve to a public view (landing page) of the project.
    *   **Proposal/Registration Host(s).  **This is the organization(s) that hosts the proposal process.** **This can be the same as the resource host organization. 
        *   **Name**
        *   **Organization ID**
*   **Resource(s) **This is the resource (e.g., facility, field station, collection, etc.) and its unique identifier.  
    *   **Resource ID.  **The ID can be an organization ID or specific resource ID.
    *   **Research Resource Name.**
    *   **Host (s) **This is the organization that administers or operates the Resource, typically a national laboratory, government agency, or research university. 
        *   **Name**
        *   **Organization ID**


#### 3.1.2 Optional {#3-1-2-optional}

*   **Reviewer. **The name and ORCID iD for the person(s) reviewing the resource proposal or request. 
    *   **Name**
    *   **ORCID iD** 
*   **Data management plan. **This describes how data will be collected, curated, stored, and accessed. 
    *   **Name**
    *   **ID**  
*   **Dataset(s). **This is a (public) data record created as researchers use a Resource.
    *   **Name**
    *   **ID**


### 3.2 ORCID Record Metadata {#3-2-orcid-record-metadata}

These are the data fields collected through the ORCID Member API and stored (with permission) in a researcher’s ORCID record.  This is our mapping of the data described in section 3.1.


#### 3.2.1 Required {#3-2-1-required}

*   **Proposal/Registration Title. ** This is the main display field for research resources e.g., “Neutron Beam Award” or “Beam time and computing resources”.
*   **Proposal/Registration ID.**  This is the public identifier (DOI, PURL, etc.) for the proposal or request (ID type tbc) to use the resource, e.g., 2017-A: CNCS.  Ideally, this identifier should be persistent and resolve to a public landing page with information about the proposal or request, such as an awards database or resource user log. 
*   **Proposal Host(s).** This is the organization that receives and processes resource proposals or requests. Proposal Host may be the same as Resource Host.  XSEDE [8] is an example of a Proposal Host that is different from the Resource Host. Oak RIdge National Laboratory is an example of a Proposal Host that is the same as the Resource Host. 
    *   **Proposal Host Name**.
    *   **Proposal Host Organization iD**.  This is the public identifier (one of GRID, Ringgold ID, Open Funder ID, LEI) for the organization managing the proposal or request process.
*   **Resource(s) **(granularity capped at 100 per ORCID record item). 
    *   **Resource Name** - e.g., Neutron Spallation Source
    *   **Resource ID(s) **- from an extensible list of acceptable PID types (RRID, DOI, URI). Subsets with a unique ID are accommodated in this model.
    *   **Resource Type **- one of ‘Infrastructures’, ‘Collections’, ‘Equipment’, or ‘Services’.
    *   **Resource Host(s) **This is the organization that administers or operates the Resource, typically a national laboratory, government agency, or research university. 
        *   **Resource Host Name**
        *   **Resource Host Organization ID**


#### 3.2.2 Optional {#3-2-2-optional}



*   **Proposal URL** for general information about the resource use. 
*   **Proposal Start Date**
*   **Proposal End Date**


#### 3.2.3 ORCID Record UI and xml examples.   {#3-2-3-orcid-record-ui-and-xml-examples}

Information about resource use is put into a researcher’s record by the resource or proposal host, using the ORCID member API.  Researchers must provide the host with read/write permissions, which can be requested by the host during the proposal or request process.  For more on how this works, see the Working Group report or ORCID’s API documentation [9].


### 3.3 Publisher Metadata {#3-3-publisher-metadata}

These are the data fields collected and stored by a publisher, as the researcher is filing a research report, detailed in the User Facilities and Publications Working Group Report.  


#### 3.3.1 Required Fields {#3-3-1-required-fields}



*   **Researcher **and **ORCID iD: **this is the author (and co-author) of a research report (article) describing work done (in part) using a Resource (as described above) and their unique identifier. The ORCID iD should be collected using an authenticated process, as detailed in best practice documentation, to ensure the iD and researcher belong to each other and that the researcher can grant permissions to read/write their ORCID record data.  iD collection can occur at the time of manuscript submission (preferred) or acceptance for the author and co-authors. 
*   **Proposal/Request ID.**  This is the public identifier (DOI, PURL, RRID, URI etc.) for the proposal or request (ID type tbc) to use the resource, e.g., 2017-A: CNCS.  It should resolve to a public landing page with information about the proposal or request, such as an awards database or resource user log. 
*   **Proposal Host Organization Name(s)**.  This is the organization that receives and processes resource proposals or requests. Proposal Host may be the same as Resource Host.  
*   **Proposal Host Organization iD**.  This is the public identifier (one of GRID, Ringgold ID, Open Funder ID, LEI) for the organization managing the proposal or request process.


#### 3.3.2 Optional Fields {#3-3-2-optional-fields}



*   **Resource(s) **(granularity capped at 100 per ORCID record item)
    *   **Resource Name** - e.g., Neutron Spallation Source
    *   **Resource ID(s) **- from an extensible list of acceptable types (RRID, DOI, URI)
    *   **Resource Type**- one of ‘Infrastructure’, ‘Collection’, ‘Equipment’  and ‘Service’.
    *   **Resource Host Name** - e.g., Oak Ridge National Laboratory
    *   **Resource Host Organization ID **- one of GRID ID, Ringgold ID, Open Funder ID, LEI.


## Metadata

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
   <td>
   </td>
   <td>Resource Name
   </td>
   <td>1
   </td>
   <td>The common name of the resource/instrument
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Resource ID(s)
   </td>
   <td>1-n
   </td>
   <td>An ID/PID that references the resource/instrument
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Resource Type
   </td>
   <td>1
   </td>
   <td>One of ‘Infrastructures’, ‘Collections’, ‘Equipment’, or ‘Services’
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Resource Host Name
   </td>
   <td>1-n
   </td>
   <td>The name of the host organisation
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Resource Host ID
   </td>
   <td>1-n
   </td>
   <td>A PID for the host organisations
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Proposal/Registration Title
   </td>
   <td>1
   </td>
   <td>The public title of the proposal or registration the researcher submitted to access a resource.   Possibly a grant title.
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Proposal/Registration PID
   </td>
   <td>1
   </td>
   <td>PID assigned by the Proposal or Resource Host to a proposal/project or registration.  Should resolve to a public view (landing page) of the project. (A url is fine)
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Proposal/Registration Host Name
   </td>
   <td>1-n
   </td>
   <td>The name of the proposal host organisation (may be the same as the resource/instrument owner)
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Proposal/Registration Host ID
   </td>
   <td>1-n
   </td>
   <td>A PID for the host organisations (may be the same as the resource/instrument owner)
   </td>
   <td>String
   </td>
   <td>?
   </td>
  </tr>
</table>



<!-- Footnotes themselves at the bottom. -->
## Notes

[1] https://www.force11.org/group/resource-identification-initiative

[2] https://orcid.org/content/user-facilities-and-publications-working-group

[3] https://doi.org/10.23640/07243.5623750.v1

[4] To accommodate research domain practices, resource PIDs should have domain specific ontologies within each of these resource types.  Some of this work is being undertaken by the PID Types Working Group of the Research Data Alliance.  See [https://rd-alliance.org/groups/pid-information-types-wg.html](https://rd-alliance.org/groups/pid-information-types-wg.html). 

[5] MERIL have developed an infrastructure type list that could be used as a basis for the resource type field. See <a href="https://portal.meril.eu/meril/static/static_about">https://portal.meril.eu/meril/static/static_about</a>. 

[6] See the recent RDA Research Data Collections recommendations for more information on this topic. https://github.com/RDACollectionsWG/specification/blob/master/Recommendation%20package/rda-collections-recommendation.pdf

[7] A newly formed RDA working group is tackling the problem of equipment identifiers, which will also cover larger facilities/infrastructures.  See <a href="https://www.rd-alliance.org/groups/persistent-identification-instruments">https://www.rd-alliance.org/groups/persistent-identification-instruments</a> 

[8] https://portal.xsede.org/#/guest

[9] https://members.orcid.org/api


<!-- Docs to Markdown version 1.0β17 -->
