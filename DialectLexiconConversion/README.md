CLARIAH Amsterdam Time Machine Dialect Lexicon Conversion
========

This directory contains the data and scripts to convert the Amsterdam dialects database to RDF. 

* Amsterdamsedata21-2-2019_copy.xlsx: dump of the dialect database compiled by Kristel Dorelijers, Nicoline van der Sijs and Brenda Assendelft 
* taalkaartZijdeman.csv: polygons for dialect neighbourhoods in rdf. The 19th different dialect neighbourhoods were first described by Johan Winkeler in 1874 in "Algemeen Nederduitsch en Friesch Dialecticon". A map was drawn from this description and published in Jan Berns (1948) Hij Zeit Wat. We use a revised reprint from 1993. The polygons were created by Richard Zijdeman. 
* bibliografischeGegevens.xlsx: the field 'bibliografische gegevens' from the dialect source file was expanded to separate title, author, year and publisher 
* lexdb_conversion.ipnb: Jupyter notebook that contains data cleanup and conversion. See documentation in the notebook for steps followed. 
* atm\_lexgraph26Feb2019.ttl and atm\_lexgraph26Feb2019.xml for resulting RDF files in turtle and xml format respectively. 
* datamodel.png: visual representation of the data model 


To do: 
 
* connect wijk/straat field to base map 
* (isocat?) registers for sociolect? (now it's modelled as a Literal)
* DBpedia links to etymological sources?
* model authors as entities instead of literals? 
* entry type (e.g. woordenschat) to entity type instead of literals? 
* shortcuts? 
* Licence? 

Creator: Marieke.van.Erp@dh.huc.knaw.nl  
Date: 26 February 2019
