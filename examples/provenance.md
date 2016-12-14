## Provenance
GA uses many methods to record provenance - the lineage of data - with some systems using external dedicated provenance storage systems to record the work that they do, others storing provenance within themselves.  Regardless of where it is recorded, it is always compatible with the [W3C's PROV standard](http://www.w3.org/TR/prov-overview/). 

GA's public Datasets within eCat Public, GA's main public dataset catalogue, provenance relationship have previously been indicated in plain text in the ISO19115 Lineage field, however this is not machine-readable, so we now represent provenance with specific object-to-object links in other ISO19115 fields. Where one Dataset derives from another, such a relationship - unqualified derivation - is represented conceptually as DatasetY prov:wasDerivedFrom DatasetX. In the standard XML for Dataset Y we would see something like:

``
NOT WORKING YET

MD_AssociatedResource DS_AssociationTypeCode source

 <mri:associatedResource>
	<mri:MD_AssociatedResource>
	   <mri:associationType />
	   <mri:metadataReference uuidref=""/>
	</mri:MD_AssociatedResource>
 </mri:associatedResource>
 
<associationType>
	<DS_AssociationTypeCode codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#DS_AssociationTypeCode" codeListValue="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#DS_AssociationTypeCode_largerWorkCitation">largerWorkCitation</DS_AssociationTypeCode>
</associationType>
``

An example of this in GA's eCat catalogue is:

``
NOT WORKING YET

blah blah blah
``

which equates to the GAPD model in OWL as:

``
<http://pid.geoscience.gov.au/dataset/456> 
	a gapd:Dataset;
	prov:wasDerivedFrom <http://pid.geoscience.gov.au/dataset/123>
.

<http://pid.geoscience.gov.au/dataset/123> 
	a gapd:Dataset
.
``


#### Namespaces
Prefix | URI
------ | ---
prov | http://www.w3.org/ns/prov#