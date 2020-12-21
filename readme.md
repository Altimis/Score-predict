#  TP SparQL
## AIT JEDDI Yassine
## Dataset : nobelprize

## Client et endpoint :
-   Client SPARQL  http://yasgui.triply.cc/
-   Endpoint : http://data.nobelprize.org/sparql

### Requete 1

Cette requete renvoit les 5 premieres femmes d'origine francaise et ayant pris un Prix Nobel de chimie avant la deuxieme guerre mondiale :

```
PREFIX dbpedia: <http://dbpedia.org/resource/>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX dbpprop: <http://dbpedia.org/property/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dbpedia-owl: <http://dbpedia.org/ontology/>
PREFIX nobel: <http://data.nobelprize.org/terms/>
PREFIX country: <http://data.nobelprize.org/resource/country/>
PREFIX category: <http://data.nobelprize.org/resource/category/>
SELECT DISTINCT ?label ?dateprize
WHERE { 
  ?laur rdfs:label ?label .
  ?laur dbpedia-owl:birthPlace country:France . 
  ?laur foaf:gender "female" .
  ?laur nobel:laureateAward ?award . 
  ?award nobel:category category:Chemistry.
  ?award nobel:year ?dateprize.
  FILTER (?dateprize <= "1939"^^xsd:integer ).
}ORDER BY ASC(?dateprize) Limit 5
  
```
### Resultat : 
comme prévu on trouve Irène Joliot-Curie.
![enter code here](q1.PNG).

#### RDF de query

Voici le RDF de la premiere query : 

![enter code here](RDF1.PNG).

### Requete 2 

L'objectif de cette deuxieme requete est de filtrer les personnes nées en Allemagne et ayant pris un Prix Nobel de la paix avant la deuxieme guerre mondiale. 


```
PREFIX dbpedia: <http://dbpedia.org/resource/>
PREFIX dbpprop: <http://dbpedia.org/property/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dbpedia-owl: <http://dbpedia.org/ontology/>
PREFIX nobel: <http://data.nobelprize.org/terms/>
PREFIX country: <http://data.nobelprize.org/resource/country/>
PREFIX category: <http://data.nobelprize.org/resource/category/>
SELECT DISTINCT ?label ?dateprize
WHERE { 
  ?laur rdfs:label ?label .
  ?laur dbpedia-owl:birthPlace country:Germany . 
  ?laur nobel:laureateAward ?award . 
  ?award nobel:category category:Peace.
  ?award nobel:year ?dateprize.
  FILTER (?dateprize <= "1939"^^xsd:integer ).
}ORDER BY ASC(?dateprize) Limit 5
```
#### Le résultat de query
On obtient comme resultat 3 personnes, ce qui montre que, malgré la brutalité et l'inhumanité du Führer à cette époque, le peuple allemand a toujours été l'un des peuples les plus pacifiques de la terre.
![enter code here](q2.PNG)

#### RDF de query

Le Rdf de cette requete : 

![enter code here](RDF2.PNG).
