# Use case description at HZB


## Rolf Krahl


## November 17, 2017

_A working group on Persistent Identification of Instruments [3] within the Research Data Alliance [4] is planned to be established. For the purpose of the discussion in this group, we describe how persistent identification of instruments may be used at HZB and for what purposes this might be useful._

The Helmholtz Zentrum Berlin für Materialien und Energie (HZB) [1] operates large scale scientific facilities, such as the synchrotron light source BESSY II. More than forty experiment stations offer a large variety of methods and experimental techniques. Most of these stations are fixedly attached to a respective beamline, some of them are flexible and can be moved between beamlines. Depending on the case, it might be required to identify a particular combination of a specific beamline and experiment station. 

Both, the beamlines and the experiment stations are unique instruments respectively. They are mostly designed and sometimes even manufactured in-house by HZB staff. The instruments are built off several components. Components range from simple, such as mirrors and slits, to complex custom built, such as monochromators (beamline) or sophisticated sample environment (experiment station), but may also be off-the-shelf products from third party manufacturers, such as detectors. It may also be required to identify individual components of an instrument in order to describe their characteristics. As the setup of instruments may change over time, the versioning of the persistent identification is a requirement. 

**The greatest value of the persistent identification of instruments would come from the ability to create references between instruments and other objects**. Relevant use cases for HZB include (text in _italics _give examples for statements that could be generated automatically out of these references):



1. Document the provenance of datasets created as a result of a measurement performed by an instrument: _This dataset has been created at instrument_ …
2. Track the scientific output of a given instrument: _This instrument has created the following datasets: ..., leading to the following publications: ..._
3. For a given dataset, search for other datasets created at the same instrument. This is particular relevant for the search of calibration data.
4. Each of HZB’s instruments has a web page providing documentation on the instrument, its design and capabilities, see [5] for an example. Registering this page as the landing page of the instrument’s PID would allow this documentation to be linked automatically to related data objects and make it easier to find in general.
5. Obtain an even richer documentation of the instruments by also attributing persistent identifiers to major components, such as detectors, and reference these from the PID of the instrument. This would require some sort of “has component” and “is component of” relations in the PID metadata.
6. The parameters of a measurement at a given instrument need to be documented. To this end, it would be helpful to link the metadata schema used at a given instrument to store these parameters in the resulting data: _Datasets created at this instrument store the metadata of the measurement using the ... schema_.

An earlier approach to address in particular use case 2 has been the creation of the Journal of Large-Scale Research Facilities (JLSRF) [2]. In general, each of HZB’s instruments has an article in JLSRF, describing the instrument. Users are asked to cite this article in publications that use data obtained from the instrument. These citations allow at least to track the publications coming out of the instrument. Nevertheless, JLSRF is not redundant to PID for instruments, both approaches are rather considered to be complementary: the textual instrument description in JLSRF gives more value to a human reader then an instrument PID, while the instrument PID provides much richer options to automatically aggregate information by following the references.


# Metadata Properties

The following table lists the properties to be stored in the metadata of the PID that this use case requires or that are at least considered to be useful in some situations.


<table>
  <tr>
   <td><strong>ID</strong>
   </td>
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
   <td>
   </td>
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
   <td>
   </td>
   <td>Name
   </td>
   <td>1-n
   </td>
   <td>The name identifying the instrument
   </td>
   <td>Text
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>URL
   </td>
   <td>1
   </td>
   <td>URL of a landing page providing more information
   </td>
   <td>URL
   </td>
   <td>IP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Owner
   </td>
   <td>1
   </td>
   <td>Organization or entity that operates the instrument
   </td>
   <td>Text
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>ownerIdentifier
   </td>
   <td>0-1
   </td>
   <td>Persistent identifier of the Owner, such as ISNI
   </td>
   <td>PID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Manufacturer
   </td>
   <td>0-1
   </td>
   <td>Name of the manufacturer that created the instrument
   </td>
   <td>Text
   </td>
   <td>LP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>modelName
   </td>
   <td>0-1
   </td>
   <td>Name of the device type, optional sub property of Manufacturer
   </td>
   <td>Text
   </td>
   <td>LP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>deviceURL
   </td>
   <td>0-1
   </td>
   <td>URL providing information on the device type, such as specifications, optional sub property of Manufacturer
   </td>
   <td>URL
   </td>
   <td>LP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Description
   </td>
   <td>0-1
   </td>
   <td>Description of the instrument
   </td>
   <td>Free text
   </td>
   <td>LP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>Date
   </td>
   <td>0-n
   </td>
   <td>Dates relevant for the instrument
   </td>
   <td>ISO 8601, may be a single date or an interval
   </td>
   <td>LP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>dateType
   </td>
   <td>1
   </td>
   <td>Mandatory sub property for each Date
   </td>
   <td>Controlled list of values: InOperation, Revised, …
   </td>
   <td>LP
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>RelatedIdentifier
   </td>
   <td>0-n
   </td>
   <td>Identifiers of related ressources
   </td>
   <td>PID
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>relatedIdentifierType
   </td>
   <td>1
   </td>
   <td>Type of the PID, mandatory sub property for each RelatedIdentifier
   </td>
   <td>Controlled list of values: Instrument-PID, DOI, Handle, URL, URN, …
   </td>
   <td>
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>relationType
   </td>
   <td>1
   </td>
   <td>Description of the relationship, mandatory sub property for each RelatedIdentifier
   </td>
   <td>Controlled list of values: IsDescribedBy, IsNewVersionOf, IsPreviousVersionOf, HasComponent, IsComponentOf, …
   </td>
   <td>
   </td>
  </tr>
</table>



# References

[1] Helmholtz-Zentrum Berlin für Materialien und Energie (HZB). [https://www.helmholtz-berlin.de/](https://www.helmholtz-berlin.de/)

[2] Journal of Large-Scale Research Facilities (JLSRF). [https://jlsrf.org/](https://jlsrf.org/) 

[3] Persistent Identification of Instruments Group. [https://www.rd-alliance.org/groups/persistent-identification-instruments](https://www.rd-alliance.org/groups/persistent-identification-instruments) 

[4] Research Data Alliance. [https://www.rd-alliance.org/](https://www.rd-alliance.org/) 

[5] mySpot: a versatile microfocussing station for scanning methods at BESSY II. [http://helmholtz-berlin.de/pubbin/igama_output?modus=einzel&sprache=en&gid=1697&typoid=50738](http://helmholtz-berlin.de/pubbin/igama_output?modus=einzel&sprache=en&gid=1697&typoid=50738)


<!-- Docs to Markdown version 1.0β17 -->