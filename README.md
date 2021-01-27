## Les Fromages Français

### Présentation du jeu de données

Ce jeu de données réunit la liste de 338 spécialités fromagères françaises.

<iframe src="https://data.opendatasoft.com/explore/embed/dataset/fromagescsv-fromagescsv@public/table/?disjunctive.fromage&static=false&datasetcard=false" width="400" height="300" frameborder="0"></iframe>

### Les fromages selon le type de lait

<iframe src="https://data.opendatasoft.com/chart/embed/?dataChart=eyJ0aW1lc2NhbGUiOiIiLCJxdWVyaWVzIjpbeyJjaGFydHMiOlt7ImFsaWduTW9udGgiOnRydWUsInR5cGUiOiJwaWUiLCJmdW5jIjoiQ09VTlQiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiJyYW5nZS1jdXN0b20iLCJwb3NpdGlvbiI6ImNlbnRlciJ9XSwiY29uZmlnIjp7ImRhdGFzZXQiOiJmcm9tYWdlc2Nzdi1mcm9tYWdlc2NzdkBwdWJsaWMiLCJvcHRpb25zIjp7fX0sInhBeGlzIjoibGFpdCIsIm1heHBvaW50cyI6NTAsInNvcnQiOiIiLCJjYXRlZ29yeUNvbG9ycyI6eyJWYWNoZSI6IiNFODcyNzMiLCJDaFx1MDBFOHZyZSI6IiNFRTlBOUEiLCJCcmViaXMiOiIjRjdBRDg0IiwiVmFjaGVzIjoiI0M3OERCRCJ9LCJzZXJpZXNCcmVha2Rvd24iOiIiLCJzZXJpZXNCcmVha2Rvd25UaW1lc2NhbGUiOiIifV0sImFsaWduTW9udGgiOnRydWUsImRpc3BsYXlMZWdlbmQiOnRydWV9&static=false&datasetcard=false" width="400" height="300" frameborder="0"></iframe>

### Datavisualisation des fromages selon leur région de production


Voici une datavisualisation qui présente les fromages de France selon leur région de production. On remarque que la Savoie est la région qui produit le plus de fromage en France.


<iframe frameborder="0" width="800" height="600" src="https://data.opendatasoft.com/map/embed/liste_des_fromages_francais2/?&static=false&scrollWheelZoom=false"></iframe>

## Requête WikiData

### Les peintures de Monet

````sparql

select distinct ?peinture
where {
    ?peinture wdt:P31/wdt:P279* wd:Q3305213 .
    ?peinture wdt:P170 wd:Q296 .
}

````

### Résultat 

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#select%20distinct%20%3Fpeinture%0Awhere%20%7B%0A%20%20%20%20%3Fpeinture%20wdt%3AP31%2Fwdt%3AP279%2a%20wd%3AQ3305213%20.%0A%20%20%20%20%3Fpeinture%20wdt%3AP170%20wd%3AQ296%20.%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>


### Les peintures de Monet avec les labels (via le service wikibase:label) et les images associées 

````sparql

SELECT DISTINCT ?peinture ?peintureLabel ?image WHERE {
  ?peinture (wdt:P31/(wdt:P279*)) wd:Q3305213;
    wdt:P170 wd:Q296.
  OPTIONAL { ?peinture wdt:P18 ?image. }
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr". }
} 

````

### Résultat 

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%0ASELECT%20DISTINCT%20%3Fpeinture%20%3FpeintureLabel%20%3Fimage%20WHERE%20%7B%0A%20%20%3Fpeinture%20%28wdt%3AP31%2F%28wdt%3AP279%2a%29%29%20wd%3AQ3305213%3B%0A%20%20%20%20wdt%3AP170%20wd%3AQ296.%0A%20%20OPTIONAL%20%7B%20%3Fpeinture%20wdt%3AP18%20%3Fimage.%20%7D%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22fr%22.%20%7D%0A%7D%20" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>

### Les peintures de Monet avec en option (via OPTIONAL) les collections/lieux de conservation



````sparql

#defaultView:ImageGrid #def + ctrl espace pour l'auto-complétion 
select DISTINCT ?peinture ?peintureLabel ?image ?localisation ?localisationLabel
where {
 ?peinture wdt:P170 wd:Q296.
 ?peinture wdt:P18 ?image.
OPTIONAL {?peinture wdt:P195 ?localisation
}  
  
SERVICE wikibase:label {
bd:serviceParam wikibase:language "fr"}
}

````

### Résultat

<iframe style="width: 80vw; height: 50vh; border: none;" src="https://query.wikidata.org/embed.html#%23defaultView%3AImageGrid%0Aselect%20DISTINCT%20%3Fpeinture%20%3FpeintureLabel%20%3Fimage%20%3Flocalisation%20%3FlocalisationLabel%0Awhere%20%7B%0A%20%3Fpeinture%20wdt%3AP170%20wd%3AQ296.%0A%20%3Fpeinture%20wdt%3AP18%20%3Fimage.%0AOPTIONAL%20%7B%3Fpeinture%20wdt%3AP195%20%3Flocalisation%0A%7D%20%20%0A%20%20%0ASERVICE%20wikibase%3Alabel%20%7B%0Abd%3AserviceParam%20wikibase%3Alanguage%20%22fr%22%7D%0A%7D" referrerpolicy="origin" sandbox="allow-scripts allow-same-origin allow-popups" ></iframe>
