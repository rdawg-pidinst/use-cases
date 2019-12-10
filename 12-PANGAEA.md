# PANGAEA Data Publisher User Case

Anusuriya Devaraju, Michael Diepenbroek, Uwe Schindler, Robert Huber  
{adevaraju, mdiepenbroek, uschindler, rhuber}@marum.de  
20<sup>th</sup> September 2018

 

## Introduction to PANGAEA

PANGAEA is a data infrastructure for archiving and publishing Earth and Environmental datasets. It is hosted by the Alfred Wegener Institute, Helmholtz Center for Polar and Marine Research (AWI) and the Center for Marine Environmental Sciences (MARUM) of University of Bremen. The infrastructure holds more than 370000 datasets from individual researchers, projects, data centers and research infrastructures. The datasets include quantitative, textual data and binary files such as audio and video. Datasets are archived with their metadata in a relational database. They are published and registered with Digital Object Identifiers (DOIs), and are accessible via the web portal [1]. For advanced interaction, related web services and APIs, e.g., OAI-PMH metadata provider and Elasticsearch API, and a data warehouse are also available.

## Use Case

The PANGAEA metadata primarily represents descriptions of datasets. At present, it only contains device types (e.g., pollen sampling device and barometer) and method types (e.g., X-ray fluorescence and continuous flow analysis (CFA)). These types are applied as part of the faceted search on the PANGAEA web portal. We may improve the discovery of PANGAEA datasets by capturing the persistent identifiers of devices and their relations to datasets as part of the metadata. For example, the web portal may display datasets with the relevant device persistent identifiers. These identifiers should be translated into actionable links on the portal. This association between a dataset and its source (device) is vital for reproducibility of science as it adds to a better understanding of the lineage and quality of the dataset through the device information.

In PANGAEA, data owners may publish datasets at different stages, e.g., raw, derived, and data products, depending on their applications. Consequently, in some cases users misused and misinterpreted the two fields ‘device’ and ‘method types’. We may avoid this ambiguity through device persistent identifiers, as their landing pages provide more comprehensive descriptions of the devices.

## Device Metadata

In the PANGAEA database, the ‘term’ table contains standard terminologies used to describe datasets including the definition of parameter (quantity and features), method and device types. Currently, there are 1364 device types defined in the table.

The metadata service only includes the device type as part of the metadata of a dataset, e.g., see the field ‘agg-device’ in the response returned by the request [http://ws.pangaea.de/es/pangaea/panmd/886115](http://ws.pangaea.de/es/pangaea/panmd/886115). More detailed information about the device type is available through the PANGAEA ElasticSearch Term Index [2]. For example, here is the metadata of the device type ‘Box corer’.

The following table summarizes the metadata related to the device type. The table excludes the common fields (e.g., _index,_score) originated from the ElasticSearch.

<table>
  <tr>
   <td><strong>Property</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td><strong>Definition</strong>
   </td>
   <td><strong>DataType</strong>
   </td>
  </tr>
  <tr>
   <td>_id
   </td>
   <td>1
   </td>
   <td>Id of the term
   </td>
   <td>Integer
   </td>
  </tr>
  <tr>
   <td>name
   </td>
   <td>1
   </td>
   <td>Name of the term
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td>abbreviation
   </td>
   <td>0..1
   </td>
   <td>Abbreviation of the term
   </td>
   <td>String 
   </td>
  </tr>
  <tr>
   <td>terminology_id
   </td>
   <td>1
   </td>
   <td>The id of the terminology/ontology that specifies the term
   </td>
   <td>Integer
   </td>
  </tr>
  <tr>
   <td>description_uri
   </td>
   <td>0..1
   </td>
   <td>The URI of the term
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td>status
   </td>
   <td>1
   </td>
   <td>The id of the status of the term (for internal editing purpose)
   </td>
   <td>Integer
   </td>
  </tr>
  <tr>
   <td>terminology
   </td>
   <td>1
   </td>
   <td>The name of the terminology/ontology that specifies the term; identifies by the terminology id.
   </td>
   <td>String
   </td>
  </tr>
</table>

The following are the required properties to support the PID Instrument use case in PANGAEA:

<table>
  <tr>
   <td><strong>Property</strong>
   </td>
   <td><strong>Occurrence</strong>
   </td>
   <td><strong>Definition</strong>
   </td>
   <td><strong>DataType</strong>
   </td>
  </tr>
  <tr>
   <td>Identifier
   </td>
   <td>1
   </td>
   <td>Unique and persistent identifier of a device
   </td>
   <td>URI
   </td>
  </tr>
  <tr>
   <td>Name
   </td>
   <td>1
   </td>
   <td>The name of the instrument, which will be used to support the full-text search.
   </td>
   <td>String
   </td>
  </tr>
  <tr>
   <td>Device Type
   </td>
   <td>0..1
   </td>
   <td>Controlled vocabularies of device types, which will be used to support the full-text search.
   </td>
   <td>String 
   </td>
  </tr>
</table>

---

[1] https://www.pangaea.de/

[2] http://ws.pangaea.de/es/pangaea-terms/term/_search


<!-- Docs to Markdown version 1.0β17 -->
