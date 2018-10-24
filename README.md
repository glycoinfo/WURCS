# WURCS is a representation of carbohydrate structure.

## Usage 1: cat [File] | java -jar mol2wurcs2std_v1.2.jar -stdin
## Usage 2: cat [File] | java -jar mol2wurcs2std_v1.2.jar -stdin -out
## Usage 3: java -jar mol2wurcs2std_v1.2.jar -f [File] -out
## Usage 4: java -jar mol2wurcs2std_v1.2.jar -f [File]

## Usage 5: $ cat [File] | java -jar count2noc2mol2wurcs2_v1.2.jar -ID [tag ID] -stdin -out
* $ cat Compound_000425001_000450000.sdf | java -jar count2noc2mol2wurcs2_v1.2.jar -ID PUBCHEM_COMPOUND_CID -stdin -out
	
