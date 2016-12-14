## Provenance
GA uses many methods to record provenance - the lineage of data - with some systems using external dedicated provenance storage systems to record the work that they do, others storing provenance within themselves.  Regardless of where it is recorded, it is always compatible with the [W3C's PROV standard](http://www.w3.org/TR/prov-overview/). 

GA's public Datasets within eCat Public, GA's main public dataset catalogue, provenance relationship have previously been indicated in plain text in the ISO19115 Lineage field, however this is not machine-readable, so we now represent provenance with specific object-to-object links in other ISO19115 fields. Where one Dataset derives from another, such a generic relationship - unqualified derivation - is represented conceptually as DatasetY prov:wasDerivedFrom DatasetX. In the standard XML for DatasetY we would see something like:

```
...
<mri:associatedResource>
  <mri:MD_AssociatedResource>
    <mri:associationType>
      <DS_AssociationTypeCode 
          codeList="http://www.isotc211.org/2005/resources/Codelist/gmxCodelists.xml#DS_AssociationTypeCode" 
          codeListValue="source">
        source
      </DS_AssociationTypeCode>
    </mri:associationType>
    <mri:metadataReference uuidref="DatasetX_UUID"/>
  </mri:MD_AssociatedResource>
</mri:associatedResource>
...
```
This indicates that DatasetY's *source* was DatasetX. DatasetY could have many sources and DatasetX could have many datasets that refer to is as their source.

This equates to the GAPD OWL model, serialised in [Turtle](https://www.w3.org/TR/turtle/), as:

```
<http://pid.geoscience.gov.au/dataset/DatasetY_eCat_ID> 
	a gapd:Dataset;
	prov:wasDerivedFrom <http://pid.geoscience.gov.au/dataset/DatasetX_eCat_ID>
.

<http://pid.geoscience.gov.au/dataset/DatasetX_eCat_ID> 
	a gapd:Dataset
.
```

#### Namespaces
Prefix | URI
------ | ---
prov | http://www.w3.org/ns/prov#