PREFIX ppm: <https://mestergruppen.no/ontologies/projectproductionmanagement#>
PREFIX dicp: <https://w3id.org/digitalconstruction/0.5/Processes#>
PREFIX dice: <https://w3id.org/digitalconstruction/0.5/Entities#>
PREFIX ex: <https://example.com/ppm/>
PREFIX dici: <https://w3id.org/digitalconstruction/0.5/Information#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT ?jobcard ((?plannedworkquantity / (?reportedworkhour * COUNT(DISTINCT ?worker))) AS ?reportedworkrate) ?defaultworkrate
WHERE { GRAPH ex:AsPlannedContext {  ?jobcard a ?jobcardtype .
?jobcardtype rdfs:subClassOf ppm:JobCard.
?jobcard ppm:hasWorkQuantity ?plannedworkquantity .
?jobcard ppm:hasCrew ?crew .
    ?crew dice:hasMember ?worker .}
GRAPH ex:DefaultContext {?jobcardtype ppm:hasJobCardSpecification ?jobcardspecification .
?jobcardspecification dici:includesEntry ?jobcardspecificationentry . }
GRAPH ?jobcardspecificationentry {?jobcardtype ppm:hasWorkRate ?defaultworkrate .}
GRAPH ex:ReportedContext {?jobcard ppm:hasWorkHour ?reportedworkhour. }
FILTER(?reportedworkhour > 0)}
GROUP BY ?jobcard ?plannedworkquantity ?reportedworkhour ?defaultworkrate
