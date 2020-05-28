# reuseDeVries

This project is reusing De Vries' dataset on social mobility in Amsterdam (https://doi.org/10.17026/dans-xez-eqdv) in order to experiment with reusing data as Linked Data. We hook up the data to other data available on the Web of Data.

## data
Data that is needed for transformation:
* /org: the original data by De Vries from DANS-EASY, including the conversion into csv.
* /addresses: addresses created in de ATM/CLARIAH pilot
* /districts: data on old districts in Amsterdam, collected from AdamLink.
* /hisco: mapping of functiontitles in De Vries' data in HISCO.

Addtional data:
* /saa-beeldbank: pictures in the City Archives collection, linked to addresses
* /volkstellingen: census-data on Amsterdam district-level

## dataHarvesting
Scripts and SPARQL-queries for collecting necessary data from other sources online.

## dataTransformation
Scripts for dataTransformation. In Python3.

### Result 1: p1223a.ttl/p1223b.ttl
These files contain the original De Vries data in LOD format.

#### Steps
- In: 		data/org/p1223a.por
- Tool:		SPSS - save as csv with labels
- Out:		data/org/p1223a.csv

- In:		data/org/p1223a.csv, data/org/p1223a.csv-metadata.json
- Tool:		http://cattle.datalegend.net/
- Out:		data/p1123a.ttl

#### Steps
- In: 		data/org/p1223b.por
- Tool:		SPSS - save as csv with labels
- Out:		data/org/p1223b.csv

- In:		data/org/p1223b.csv, data/org/p1223b.csv-metadata.json
- Tool:		http://cattle.datalegend.net/
- Out:		data/p1123b.ttl

With cow and rapper installed you can do:
from /reuseDeVries

'''
$ cow_tool convert data/org/p1223a.csv
$ rapper data/org/p1223a.csv.nq -i nquads -o turtle > data/p1223a.ttl
'''

### Result 2: p1123a_standardization.ttl/p1123b_standardization.ttl
These files contain additional triples with URI's for some of the values in the original files ('links for strings'), refering to observations in p1223a.ttl and p1223b.ttl.

Preconditions (available in /data):
- mapping of functionnames for occupations in the dataset onto HISCO in file data/hisco/bdv_occupations_hisco.csv
- districts/neighbourhoods by AdamLink in file data/districts/wijkindeling1853.csv
- addresses created in de ATM/CLARIAH pilot.

#### Steps
- In:		data/org/p1223a.csv, 
		data/hisco/p1223a_occupations_hisco.csv,
		data/districts/wijkindeling1853.csv,
		data/addresses/adressenconcordans.csv
- Tool:	dataTransformation/combineData1223a.py
- Out:	data/p1223a_standardization.ttl

#### Steps
- In:		data/org/p1223b.csv, 
		data/hisco/p1223b_occupations_hisco.csv,
		data/districts/wijkindeling1853.csv
- Tool:	dataTransformation/combineData1223b.py
- Out:	data/p1223b_standardization.ttl

## dataAnalysis
SPARQL-queries that create data in csv to be analysed or visualised in other tools, eg. R or QGIS.


