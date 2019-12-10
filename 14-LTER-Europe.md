# Use Case Description “LTER-Europe” metadata of instruments


Alessandro Oggioni (LTER-Italy) et al.  
[oggioni.a@irea.cnr.it](mailto:oggioni.a@irea.cnr.it)  
24<sup>th</sup> October 2018


## Introduction to LTER-Europe

Long-Term Ecosystem Research (LTER) is an essential component of world-wide efforts to better understand ecosystems. Through research and monitoring, LTER seeks to improve our knowledge of the structure and functions of ecosystems and their long-term response to environmental, societal and economic drivers.

LTER contributes to the knowledge base informing policy and to the development of management options in response to the Grand Challenges under Global Change.

[LTER-Europe](http://www.lter-europe.net/lter-europe/about) was launched in 2003 as the umbrella network for Long-Term Ecosystem Research (LTER) in Europe. It's members are [national networks](http://www.lter-europe.net/lter-europe/infrastructure) operating a wide range of research and monitoring [sites](http://www.lter-europe.net/lter-europe/infrastructure/sites-platforms) as well as larger [platforms](http://www.lter-europe.net/lter-europe/infrastructure/sites-platforms) for socio-ecological research.


## Use Case

European Long-Term Ecosystem Research (LTER-Europe) network adopted [EMF](http://inspire-regadmin.jrc.ec.europa.eu/dataspecification/ScopeObjectDetail.action?objectDetailId=9768) for describe sites. A site is a location where the observation and/or experimentation takes place. Most of the sites are characterised by a design which is setup to study and analyse ecosystem processes in the field. Sites are described by their biotic and abiotic characteristics as well as by the administrative setup. This includes the infrastructure (e.g. measurement towers or experimental design) as well as the research topics studies.

An example of EMF sites from DEIMS-SDR: [LTER Zöbelboden](https://deims.org/8eda49e9-1f4e-4f3e-b58e-e0bb25dc32a6)

For describe instruments present or used for collect observations during the field work on the site, 2 solutions are adopted:


* SensorML template within Geoinformation Enabling ToolkIT starterkit [1] (GET-IT) 
* DEIMS-SDR template

SensorML specific profile (see paragraph 2.2) adopted in order to describe instruments used in the LTER sites. An example of SensorML landing pages from GET-IT: [LTER Zöbelboden Austria precipitation WW deployed at site LTER Zöbelboden - Austria](http://cdn.lter-europe.net/sensors/sensor/ds/?format=text/html&sensor_id=https%3A//deims.org/sensor/fb583610-fe71-4793-b1a9-43097ed5c3e3)


### Software adopted


#### DEIMS-SDR

In order to manage and register the site and the related dataset, DEIMS-SDR (Dynamic Ecological Information Management System – Site and dataset registry, [https://deims.org/](https://deims.org)) was developed starting with a basic outline during the EnvEurope project. DEIMS-SDR is the central catalogue for long term observation and experimentation facilities and is used by LTER Europe and ILTER to manage their site network. 

As at March 2019, a total of 1089 of long term observation and experimentation sites are registered on DEIMS-SDR, including both LTER and non-LTER sites. This includes LTSER platforms covering a wide range of socio-ecological research topics and a large spatial scale to point-based research plots with very particular research topics. 

The goal of DEIMS-SDR is to be the most globally comprehensive catalogue of environmental research facilities, featuring foremost but not exclusively information about all LTER sites worldwide and providing that information to science, politics and the public in general. 


#### GET-IT and EDI for sensors management

GET-IT [2] is a software suite that aims to enable domain expert researchers to become leaders in the creation of an interoperable SDI. By using some relevant standards from the OGC (WMS, WFS, WCS, CSW, SensorML, and SOS), it enables the interoperable distribution of data collected by researchers, both geospatial and observations, through web services, creating their own spatial data repositories and facilitating the entry and maintenance of data and metadata of data and sensors. Created services, with entered data and metadata, are hosted by virtual machines that can be installed in server or in hosting sites. Developed by a joint research group of CNR IREA - CNR ISMAR under the flagship project RITMARE, GET-IT is completely free and open-source and has among its objectives the creation of a federated interoperable infrastructure for the observational network of geographic data, allowing researchers and research organizations to share their data and metadata. The system, as a whole, adopts a service-oriented architecture dedicated to geographic and observational services. 

The architecture is divided into three different layers (Fig. 3.2): 

* Resource layer - which corresponds to the physical storage, in databases or files, of appropriately structured data and metadata (data description); 
* Access layer (services) - tools for accessing and managing resources through interoperable services; 
* Graphic user interface (GUI) - client-side component of the platform, the GUI is delegated to the display of resources and includes the tools to aggregate (mashup) and reorganize the same, and to facilitate user interaction.

GET-IT consists of a different docker containers one of each software (Fig. 3.2); the basic software used is GeoNode [3], an open source software widely known geographic content management system. GeoNode already contains: PyCWS [4] a OGC catalogue service of metadata server written in Python and GeoServer [5] an open source server for sharing geospatial data. Within GeoNode some aspect is missing, in particular are not present Sensor Web Enablement (SWE) and semantic enablement, has been edited and have been added new software implementations, both client and server side, for the creation and management of observations, sensors and metadata, semantically enabled.

In particular, the new software implementations include:

* A metadata editor client, named EDI, which allows the creation and validation of metadata in accordance with different profiles or templates. EDI allows plugging in external data sources that are made available as SPARQL endpoints;
* A SOS manager (52°North SOS [6]) that allows the registration of new sensors edited in Sensor Metadata Language (SensorML) metadata profile by EDI metadata editor;
* An insert observation interface allows to upload observations, by copy and paste action, for GET-IT registered sensor;
* A geographic data manager (GeoServer [7]) that allows to share geographic data;
* A SOS client that allows viewing the information of registered sensors and data recording in a web map.

The documentation of GET-IT is available on a dedicated website [8] also providing information on installation routines [9]. 

### Sensor Web Enablement Lightweight SOS Profile adopted by LTER-Europe community [10]

SensorML is the recommended sensor metadata for SOS 2.0 [11].

SensorML is used within SOS for encoding sensor metadata documents that are returned in case of DescribeSensor requests. This lightweight profile [12] defines a minimum set of mandatory metadata that need to be provided in a SensorML document. Complex elements of SensorML are not considered here.

        **gml:description** (mandatory): Short textual description of the sensor or sensor system.


        **gml:identifier **(mandatory): Unique identifier of the sensor system. 


        **sml:keywords** (mandatory): Terms which help to describe the sensor system and serve for discovery purposes. For example, the phenomena observed by the system or the types of contained sensors can be mentioned. 


        **sml:identification** (mandatory): This element contains identifiers of the sensor system. Each "identifier/Term" element contained in the "IdentifierList" must have a "definition" attribute which links to the semantics of the sensor system. One identifier has to be present which contains the definition "urn:ogc:def:identifier:OGC:shortname". The value of its contained "Term" element represents a human understandable name for the instance. One identifier has to be present which contains the definition "urn:ogc:def:identifier:OGC:longname". The value of its contained "Term" element represents a human understandable name for the sensor system. 


        **sml:classification** (mandatory): This element contains classifiers for the sensor system. 11-169r1 Copyright © 2014 Open Geospatial Consortium 11 Each "classifier/Term" element contained in the "ClassifierList" must have a "definition" attribute. This attribute links to the semantics of the identifier. One classifier has to be present which contains the definition “http://www.opengis.net/def/property/OGC/0/SensorType”. The value of its contained “Term” element states the type of the sensor system (e.g., “weather station”). 


        **sml:contacts **(mandatory): This element contains contact information about the operator of the sensor. The element "contacts/ContactList/member/gmd:CI_ResponsibleParty" has to be present to define the responsible party of the sensor system [13]. 


        **sml:featuresOfInterest** (mandatory): This element contains the real world entity, the feature of interest, which is observed by the sensor system. In case of this profile, the feature of interest is a station and modelled as a SamplingPoint. 


        **sml:outputs** (mandatory): The outputs of the sensors attached to the sensor system. Each child-element of an "output" has to use the "definition"-attribute to specify the URI of the observed property. If the child-element of the output is a "swe:Quantity" it has to contain the "swe:uom" element which specifies the "code" attribute stating the UCUM code. Depending on the observation types the outputs have to be described as one of the following elements o swe:Quantity (in case of Measurement) o swe:Count (in case of CountObservation) o swe:Boolean (in case of TruthObservation) o swe:Category (in case of CategoryObservation) o swe:Text (in case of TextObservation)


### EMF SensorML- XML example


```
<sml:PhysicalSystem gml:id="Lake_Jyvasjarvi_Meteorological_Station">
            <gml:description>On lake meteorological station providing year-round data @ 1 min
                interval. Campbell weather station: Wind speed and direction (gust), air temperature,
                solar radiation, rain, air pressure.</gml:description>
            <gml:identifier codeSpace="uniqueID">https://deims.org/sensor/a5119301-bd84-4b07-9e92-b41375d4c99d</gml:identifier>
            <gml:name>Lake Jyväsjärvi Meteorological Station deployed at site Lake
                Päijänne LTER - Finland</gml:name>
            <sml:keywords>
                <sml:KeywordList>
                    <sml:keyword>lakes</sml:keyword>
                    <sml:keyword>snow and meteorological data</sml:keyword>
                    <sml:keyword>year-round</sml:keyword>
                    <sml:keyword>online</sml:keyword>
                </sml:KeywordList>
            </sml:keywords>
            <sml:identification>
                <sml:IdentifierList>
                    <sml:identifier>
                        <sml:Term definition="urn:ogc:def:identifier:OGC:1.0:shortName">
                            <sml:label>short name</sml:label>
                            <sml:value>Lake Jyväsjärvi Meteorological Station</sml:value>
                        </sml:Term>
                    </sml:identifier>
                    <sml:identifier>
                        <sml:Term definition="http://mmisw.org/ont/ioos/definition/longName">
                            <sml:label>long name</sml:label>
                            <sml:value>Lake Jyväsjärvi Meteorological Station deployed at site Lake
                                Päijänne LTER - Finland</sml:value>
                        </sml:Term>
                    </sml:identifier>
                </sml:IdentifierList>
            </sml:identification>
            <sml:classification>
                <sml:ClassifierList>
                    <sml:classifier>
                        <sml:Term definition="http://www.opengis.net/def/property/OGC/0/SensorType">
                            <sml:label>sensorType</sml:label>
                            <sml:value>Meteorological Station</sml:value>
                        </sml:Term>
                    </sml:classifier>
                </sml:ClassifierList>
            </sml:classification>
            <sml:capabilities name="offerings">
                <sml:CapabilityList>
                    <sml:capability name="offeringID">
                        <swe:Text definition="urn:ogc:def:identifier:OGC:offeringID">
                            <swe:label>Main Offering</swe:label>
                            <swe:value>a5119301-bd84-4b07-9e92-b41375d4c99d/offering/1</swe:value>
                        </swe:Text>
                    </sml:capability>
                </sml:CapabilityList>
            </sml:capabilities>
            <sml:contacts>
                <sml:ContactList>
                    <sml:contact xlink:arcrole="http://inspire.ec.europa.eu/metadata-codelist/ResponsiblePartyRole/pointOfContact" xlink:href="http:// orcid.org/0000-0001-9302-1174">
                        <gmd:CI_ResponsibleParty>
                            <gmd:individualName>
                                <gco:CharacterString>Juha Karjalainen</gco:CharacterString>
                            </gmd:individualName>
                            <gmd:organisationName>
                                <gco:CharacterString>University of Jyväskylä</gco:CharacterString>
                            </gmd:organisationName>
                            <gmd:positionName>
                                <gco:CharacterString>Sensor Contact person</gco:CharacterString>
                            </gmd:positionName>
                            <gmd:contactInfo>
                                <gmd:CI_Contact>
                                    <gmd:address>
                                        <gmd:CI_Address>
                                            <gmd:deliveryPoint>
                                                <gco:CharacterString>Survontie 9</gco:CharacterString>
                                            </gmd:deliveryPoint>
                                            <gmd:city>
                                                <gco:CharacterString>Jyväskylä</gco:CharacterString>
                                            </gmd:city>
                                            <gmd:postalCode>
                                                <gco:CharacterString>40500</gco:CharacterString>
                                            </gmd:postalCode>
                                            <gmd:country>
                                                <gco:CharacterString>FI</gco:CharacterString>
                                            </gmd:country>
                                            <gmd:electronicMailAddress>
                                                <gco:CharacterString>juha.karjalainen@jyu.fi</gco:CharacterString>
                                            </gmd:electronicMailAddress>
                                        </gmd:CI_Address>
                                    </gmd:address>
                                </gmd:CI_Contact>
                            </gmd:contactInfo>
                            <gmd:role>
                                <gmd:CI_RoleCode codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#CI_RoleCode" codeListValue="pointOfContact"/>
                            </gmd:role>
                        </gmd:CI_ResponsibleParty>
                    </sml:contact>
                </sml:ContactList>
            </sml:contacts>
            <sml:featuresOfInterest>
                <sml:FeatureList definition="http://www.opengis.net/def/featureOfInterest/identifier">
                    <swe:label>Lake Jyväsjärvi</swe:label>
                        <sml:feature
                            xlink:href="http://cdn.lter-europe.net/"/>
                </sml:FeatureList>
            </sml:featuresOfInterest>
            <sml:outputs>
                <sml:OutputList>
                    <sml:output name="atmospheric_parameter">
                        <swe:Quantity definition="http://vocabs.lter-europe.net/EnvThes/20937">
                            <swe:uom code="filler_code"/>
                        </swe:Quantity>
                    </sml:output>
                    <sml:output name="solar_radiation">
                        <swe:Quantity definition="http://vocabs.lter-europe.net/EnvThes/22284">
                            <swe:uom code="filler_code"/>
                        </swe:Quantity>
                    </sml:output>
                    <sml:output name="air_temperature">
                        <swe:Quantity definition="http://vocabs.lter-europe.net/EnvThes/22035">
                            <swe:uom code="filler_code"/>
                        </swe:Quantity>
                    </sml:output>
                    <sml:output name="precipitation_intensity">
                        <swe:Quantity definition="http://vocabs.lter-europe.net/EnvThes/22204">
                            <swe:uom code="filler_code"/>
                        </swe:Quantity>
                    </sml:output>
                    <sml:output name="wind_direction">
                        <swe:Quantity definition="http://vocabs.lter-europe.net/EnvThes/22317">
                            <swe:uom code="filler_code"/>
                        </swe:Quantity>
                    </sml:output>
                    <sml:output name="wind_speed">
                        <swe:Quantity definition="http://vocabs.lter-europe.net/EnvThes/22319">
                            <swe:uom code="filler_code"/>
                        </swe:Quantity>
                    </sml:output>
                </sml:OutputList>
            </sml:outputs>
            <sml:position>
                <swe:Vector id="SYSTEM_LOCATION" referenceFrame="urn:ogc:def:crs:EPSG::4326">
                    <swe:coordinate name="easting">
                        <swe:Quantity axisID="Lon" definition="longitude">
                            <swe:uom code="degree"
                                xlink:href="http://vocab.nerc.ac.uk/collection/P06/current/UAAA/"/>
                            <swe:value>62.235716000000</swe:value>
                        </swe:Quantity>
                    </swe:coordinate>
                    <swe:coordinate name="northing">
                        <swe:Quantity axisID="Lat" definition="latitude">
                            <swe:uom code="degree"
                                xlink:href="http://vocab.nerc.ac.uk/collection/P06/current/UAAA/"/>
                            <swe:value>25.781366000000</swe:value>
                        </swe:Quantity>
                    </swe:coordinate>
                </swe:Vector>
            </sml:position>
        </sml:PhysicalSystem>
```



## 2.3 SensorML and INSPIRE EMF

INSPIRE Data Specification on EMF (Environmental Monitoring Facilities) currently has limited means to describe sensors, therefore sensor metadata expressed in SensorML can be linked to EMF files.


### EMF Sensor fields

inspireId = _XXXXXXX_

name = _Hydrometric sensor : O12525100101_

geometry = GM_Point (_X/Y/Spatial Reference System of the sensor_)

responsibleParty = _DREAL Midi-Pyrénées_

mediaMonitored [14] = http://inspire.ec.europa.eu/codeList/MediaValue/water

measurementRegime [15] = _http://inspire.ec.europa.eu/codeList/MeasurementRegimeValue/continuousDataCollection_

mobile = False

resultAcquisitionSource [16] = _http://inspire.ec.europa.eu/codeList/ResultAcquisitionSourceValue/inSitu_

specialisedEMFType = _http://sandre.eaufrance.fr/?urn=urn:sandre:dictionnaire:HYD::entite:Capteur:ressource:2.1:::html_


### EMF Sensor fields - XML example [17]


```
<complexType name="EnvironmentalMonitoringFacilityType">
    <complexContent>
    <extension base="ef:AbstractMonitoringFeatureType">
    <sequence>
        <element minOccurs="0" name="representativePoint" nillable="true" type="gml:PointPropertyType">
        <annotation>
        <documentation>
        -- Definition -- Representative location for the EnvironmentalMonitoringFacility. -- Description --
        </documentation>
        </annotation>
        </element>
        <element name="measurementRegime" nillable="true" type="gml:ReferenceType">
        <annotation>
        <documentation>-- Definition -- Regime of the measurement</documentation>
        </annotation>
        </element>
        <element name="mobile" nillable="true">
        <annotation>
        <documentation>
        -- Definition -- Indicate whether the EnvironmentalMonitoringFacility is mobile (repositionable) during the acquisition of the observation.
        </documentation>
        </annotation>
        <complexType>
        <simpleContent>
        <extension base="boolean">
            <attribute name="nilReason" type="gml:NilReasonType"/>
        </extension>
        </simpleContent>
        </complexType>
        </element>
        <element maxOccurs="unbounded" minOccurs="0" name="resultAcquisitionSource" nillable="true" type="gml:ReferenceType">
        <annotation>
        <documentation>-- Definition -- Source of result acquisition</documentation>
        </annotation>
        </element>
        <element minOccurs="0" name="specialisedEMFType" nillable="true" type="gml:ReferenceType">
        <annotation>
        <documentation>
        -- Definition -- Categorisation of EnvironmentalMonitoringFacilities generally used by domain and in national settings. -- Description -- EXAMPLE: platform, site, station, sensor, ...
        </documentation>
        </annotation>
        </element>
        <element maxOccurs="unbounded" name="operationalActivityPeriod" nillable="true">
        <annotation>
        <documentation>
        -- Definition -- Lifespan of the physical object (facility).
        </documentation>
        </annotation>
        <complexType>
        <complexContent>
        <extension base="gml:AbstractMemberType">
            <sequence minOccurs="0">
            <element ref="ef:OperationalActivityPeriod"/>
            </sequence>
            <attributeGroup ref="gml:AssociationAttributeGroup"/>
        </extension>
        </complexContent>
        </complexType>
        </element>
        <element maxOccurs="unbounded" minOccurs="0" name="relatedTo" nillable="true">
        <annotation>
        <documentation>
        -- Definition -- Any Thematic Link to an Environmental Monitoring Facility. The association has additional properties as defined in the association class AnyDomainLink.
        </documentation>
        </annotation>
        <complexType>
        <sequence minOccurs="0">
        <element ref="ef:AnyDomainLink"/>
        </sequence>
        <attributeGroup ref="gml:AssociationAttributeGroup"/>
        <attributeGroup ref="gml:OwnershipAttributeGroup"/>
        </complexType>
        </element>
        <element maxOccurs="unbounded" minOccurs="0" name="belongsTo" nillable="true">
        <annotation>
        <documentation>
        -- Definition -- A link pointing to the EnvironmentalMonitoringNetwork(s) this EnvironmentalMonitoringFacility pertains to. The association has additional properties as defined in the association class NetworkFacility.
        </documentation>
        <appinfo>
        <reversePropertyName xmlns="http://www.opengis.net/gml/3.2">ef:contains</reversePropertyName>
        </appinfo>
        </annotation>
        <complexType>
        <sequence minOccurs="0">
        <element ref="ef:NetworkFacility"/>
        </sequence>
        <attributeGroup ref="gml:AssociationAttributeGroup"/>
        <attributeGroup ref="gml:OwnershipAttributeGroup"/>
        </complexType>
        </element>
    </sequence>
    </extension>
    </complexContent>
</complexType>
```

<!-- Footnotes themselves at the bottom. -->
## Notes

[1] Geoinformation Enabling ToolkIT starterkit (GET-IT): [http://www.get-it.it/](http://www.get-it.it/)

[2] http://www.get-it.it

[3] http://geonode.org

[4] http://pycsw.org

[5] http://www.geoserver.com

[6] http://52north.org

 [7] http://geoserver.org

 [8] http://getit.readthedocs.io/en/latest/

 [9] http:// getit.readthedocs.io/en/latest/tutorial/admin/scratch.html#scratch

 [10] [OGC® Best Practice for Sensor Web Enablement Lightweight SOS ...https://portal.opengeospatial.org/files/?artifact_id=52803](https://portal.opengeospatial.org/files/?artifact_id=52803)

 [11] http://www.ogcnetwork.net/sos_2_0/tutorial/sensorml

 [12] https://portal.opengeospatial.org/files/?artifact_id=52675

 [13] https://portal.opengeospatial.org/files/?artifact_id=52803

 [14] http://inspire.ec.europa.eu/codelist/MediaValue

 [15] http://inspire.ec.europa.eu/codelist/MeasurementRegimeValue

 [16] http://inspire.ec.europa.eu/codelist/ResultAcquisitionSourceValue

 [17] http://inspire.ec.europa.eu/schemas/ef/4.0/EnvironmentalMonitoringFacilities.xsd


<!-- Docs to Markdown version 1.0β17 -->
