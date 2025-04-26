PREFIX ppm: <https://mestergruppen.no/ontologies/projectproductionmanagement#>
PREFIX dicp: <https://w3id.org/digitalconstruction/0.5/Processes#>
PREFIX dice: <https://w3id.org/digitalconstruction/0.5/Entities#>
PREFIX ex:  <https://example.com/ppm/>
PREFIX dici: <https://w3id.org/digitalconstruction/0.5/Information#>
PREFIX dicv: <https://w3id.org/digitalconstruction/0.5/Variables#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT (CONCAT(?materialname, " ", STR(?quantity), " ", ?unit) AS ?materialinformation)
WHERE{
GRAPH ex:AsPlannedContext { ex:Worker1 ppm:participates ?jobcard  .
?jobcard a ?jobcardtype .}
GRAPH ex:DefaultContext {?jobcardtype rdfs:subClassOf ppm:JobCard.
?jobcardtype ppm:hasJobCardSpecification ?jobcardspecification .
?jobcardspecification dici:includesEntry ?jobcardspecificationentry .}
GRAPH ?jobcardspecificationentry {?jobcardtype ppm:includesTemplateMaterialList ?materiallist .}
GRAPH ?materiallist {?materialset a ppm:MaterialSet .
        ?materialset rdfs:label ?materialname.
        ?materialset dicv:hasUnit ?unit .
        ?materialset ppm:hasMaterialQuantity ?quantity}}
