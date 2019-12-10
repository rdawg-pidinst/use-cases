# Use Case Description at IREA - CNR 


Alessandro Oggioni, Cristiano Fugazza, and Paolo Tagliolato  
January 2018


# Introduction

The Spatial Data Infrastructures (SDI) development team at the Institute for Electromagnetic Sensing of the Environment of the Italian National Research Council (IREA - CNR) has been active in the implementation of Sensor Web Enablement (SWE) practices since 2012. The main output of this research thread, the Geoinformation Enabling ToolkIT starterkit [1] (GET-IT) is currently deployed in the context of a broad range of initiatives. Persistent identification of sensor instances that are registered in the SOS server included in this software suite is among the desiderata that are envisaged for future releases.

Since SWE is the reference framework of our research, we focus on features that can be exposed via PID metadata and are missing in the representation of sensor instances that are ingested by SOS servers, namely SensorML descriptions, and in the SWE ecosystem at large. Example of such features include … In fact, beside the primary usage of PIDs as unique, persistent references to resources, PID metadata can enable further features of both the Registration Agency and the specific Registrant.


# UC1: Extensibility of PID metadata

The first use case addresses a shortcoming of SensorML sensor descriptions. In fact, in SensorML it is not possible to indicate which SOS service a given sensor instance is registered in (though, by interrogating an SOS service it is possible to know which sensor instances are registered in). This shortcoming hampers effective usage of the sensor instance, by the sensor owner as well as by third parties.

For instance, a third party who wants to access the observations collected by a given sensor instance needs to know in which SOS service the sensor instance is registered. In the SWE ecosystem this information can be provided by interrogating individual SOS services or by sensor catalogs that harvest multiple SOS services. Sensor catalogs are not widely implemented. For third parties it is cumbersome to look up multiple SOS services for the sensor instance they already identified. Instead, by associating the sensor instance with a PID and providing this information as PID metadata, it would be possible for third parties to directly access SOS service information.

Moreover, sensor owners require this information to enact semi-automated workflows that execute operations on the sensor instance (such as updating calibration information or accessing the observations collected by a given sensor). Currently, the sensor owner has to keep track of which SOS service the sensor is registered in. By associating the sensor instance with a PID, it would be possible to store this information in PID metadata and subsequently refer to sensor instances in workflows via their PID (thus providing this additional information to the workflows accessing the sensor instance).

Finally, as other use cases suggest,  the range of possible metadata formats PIDs shall be associated with is heterogeneous as well as the possible features that PID metadata should support (e.g., specification of the schema governing sensor metadata, specifying versioning information, etc.). 

A possible requirement that emerges from this use case is:

R1: In order to be applicable to our scenario, PIDs shall feature a metadata schema that is arbitrarily extensible.


# UC2: Actionability of PIDs

This use case addresses PID _actionability_, i.e. metadata that is intelligible to automated agents. An essential element is _content negotiation_, i.e. the capability of either the PID resolution system or that by the Registrant to serve different content according to the type specified in the HTTP request. The main providers of DOI for research (Crossref, DataCite, mEDRA) already provide this feature [2] (albeit not for the purpose of actionability of DOIs). It works as follows:



*   If the request specifies text/html as the intended format, DOI resolution operates as usual (redirecting the agent to the landing page specified in the metadata);
*   Otherwise, if one of the alternative formats is specified (such as application/x-bibtex) the DOI metadata is translated into the specified format and returned to the agent (with no redirection to the landing page).

On the Registration Agency-side, content negotiation could be more customizable by the Registrant: As an example, it may be useful for redirection to return a human-intelligible HTML page if text/html is requested and return the SensorML description if text/xml is specified (both these contents, of course, shall be managed directly by the Registrant). Then, metadata shall specify which content types shall be managed by the PID resolution system set up by the Registration Agency (e.g., featuring a behavior such as that of DOIs, as explained above) and which content types can be handled by the Registrant itself. Also, the PID resolution system may feature (and thus expose as part of the API) features that are currently missing in the SWE ecosystem, such as those described in the previous section.

On the other hand, PID actionability on the Registrant-side may enable features such as those described below. For sensor owners, PID actionability may enable full automation of the workflows mentioned in the previous use case. As an example, PID metadata may allow for automatic update of  SensorML metadata by the SOS services the sensor instance is registered in as soon as the “canonical” SensorML stored by the PID Registrant is modified (e.g., for updating calibration information). 

For third parties, exploiting PID actionability may be more tricky because PID metadata should unambiguously specify the semantics of the API that is exposed (e.g., specify that the REST call http://.../list-sos/123 returns the list of SOS services the sensor whose PID is “123” is registered in). However, the opportunities for third parties are manifold: As an example, PID metadata could expose an API call allowing catalogs to notify that a given sensor has been indexed (because it has been found in the SOS services that were harvested). 

The two requirements that emerge from this use case are:

R2: The PID system shall support content negotiation.

R3: PID resolution shall return to the automated agent a fine-grained description of the API through which it is possible to interact with the registered resource/registration agency.


# Metadata

From 20180606 call notes: Work in progress, no exhaustive list of metadata idea is to support a heterogeneous set of metadata items that could come up from various use cases. Looking at how heterogeneous metadata can be captured by ePIC.

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



# Appendix A: Mockup metadata

This section contains mockup metadata that may address some of the requirements defined in the PIDINST use cases as well as in the case statement. The metadata is provided as JSON-LD [3] data structures in order to be either easily intelligible to programmers and arbitrarily extensible via the many existing ontologies and schemata.

NOTE: For many of the metadata fields, it could be argued that their place is in sensor metadata, not in PID metadata. Exploiting PID metadata to complement sensor metadata can make sense but such practice can make the definition of a common baseline for PID metadata more difficult to accomplish.


```
{
  "@context": {
	"priorVersion": {
  	"@id": "http://www.w3.org/2002/07/owl#priorVersion",
  	"@type": "@id"
	},
	"hasSubSystem": {
  	"@id": "http://www.w3.org/ns/ssn/hasSubSystem",
  	"@container": "@list"
	},
	"metadataDocument": {
  	"@id": "http://purl.org/spar/cito/citesAsMetadataDocument",
  	"@type": "@id"
	},
	"metadataScheme": {
  	"@id": "http://purl.org/spar/datacite/MetadataScheme",
  	"@type": "@id"
	},
	"generated": {
  	"@reverse": "http://www.w3.org/ns/prov#wasGeneratedBy",
  	"@type": "@id"
	},
	"associatedWith": {
  	"@id": "http://www.w3.org/ns/prov#wasAssociatedWith",
  	"@type": "@id"
	},
	"isCitedBy": {
  	"@id": "http://purl.org/spar/cito/isCitedBy",
  	"@type": "@id"
	}
  },
  "@id": "http://example.org/20.123/abc",
  "@type": "http://www.w3.org/ns/sosa/Sensor",
  "priorVersion": "https://example.org/20.123/def",
  "hasSubSystem": [
	{
  	"@id": "http://example.org/20.123/ghi",
  	"@type": "http://www.w3.org/ns/sosa/Sensor"
	},
	{
  	"@id": "http://example.org/20.123/jkl",
  	"@type": "http://www.w3.org/ns/sosa/Sensor"
	}
  ],
  "metadataDocument": {
	"metadataScheme": "http://some.other.site.org/some/schema",
	"@id": "http://some.site.org/some/document",
	"@type": "http://purl.org/spar/fabio/MetadataDocument"


  },
  "generated": "http://example.org/20.123/mno",
  "associatedWith": "http://example.org/20.123/pqr",
  "isCitedBy": "http://example.org/20.123/stu"
}
```



# Appendix B: Possible improvements

In this section, we provide possible improvements over metadata items that may already annotate instruments.

B1: Defining  the "author" (that is, the principal investigator):


```
{
  "@context": {
	"foaf": "http://xmlns.com/foaf/0.1/",
	"name": "foaf:name",
	"givenName": "foaf:givenName",
	"familyName": "foaf:familyName",
	"datacite": "http://purl.org/spar/datacite/",
	"author" : "datacite:hasCreatorList"
  }

  "@id": "https://example.org/20.1234/abc",
  "author": [
	{
  	"name": "Cristiano Fugazza",
  	"givenName": "Cristiano",
  	"familyName": "Fugazza"
	},
	...
  ]
}
```


doing it better:


```
{
  "@context": {
	"datacite": "http://purl.org/spar/datacite/",
	"author": "datacite:hasCreatorList",
	}
  }

  "@id": "https://example.org/20.1234/abc",
  "author": [
	{
  	"@id": "https://orcid.org/0000-0003-2679-4868",
  	"@type": "@id"
	},
	...
  ]
}
```


doing it even better:


```
{
  "@context": {
	"datacite": "http://purl.org/spar/datacite/",
	"author": "datacite:hasCreatorList",
	}
  }

  "@id": "https://example.org/20.1234/abc",
  "author": [
	{
  	"@id": "https://example.org/people/CristianoFugazza",
  	"@type": "@id"
	},
	...
  ]
}
```


where resolving https://example.org/people/CristianoFugazza returns:


```
{
  "@context": {
	"foaf": "http://xmlns.com/foaf/0.1/",
	"name": "foaf:name",
	"givenName": "foaf:givenName",
	"familyName": "foaf:familyName",
	"account": "foaf:account",
	"uid": "foaf:accountName",
	"service": "foaf:accountServiceHomepage",
	"knows": "foaf:knows"
	}
  }

  "@id": "https://example.org/people/CristianoFugazza",
  "name": "Cristiano Fugazza",
  "givenName": "Cristiano",
  "familyName": "Fugazza"
  "account": [
	{
  	"uid": "0000-0003-2679-4868",
  	"service": "https://orcid.org/"
	}
  ]
  "knows": {
	"@id": "https://example.org/people/AlessandroOggioni",
	"@type": "@id"
  }
  ...
}
```

## Notes

[1] Geoinformation Enabling ToolkIT starterkit (GET-IT): [http://www.get-it.it/](http://www.get-it.it/)

[2] DOI content negotiation: https://citation.crosscite.org/docs.html

[3] JSON-LD: https://json-ld.org/


<!-- Docs to Markdown version 1.0β17 -->
