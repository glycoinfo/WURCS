# WURCS Tools and DBs

* Software tools supporting WURCS

| Tool | Dependencies | Description | Repository | Reference |
| ------ | ------ | ------ | ------ | ------ |
| WURCSFramework |  | WURCSFramework is a framework for WURCS input/output, WURCS string validation and standardization. | [gitlab](https://gitlab.com/glycoinfo/wurcsframework) | ... |
| GlycanFormatConverter | WURCSFramework | GlycanFormatConverter is core library of glycan text conversion tools. It is also used in [GlycoNAVI](https://glyconavi.org), [GlyTouCan](https://glytoucan.org) and [GlyCosmos](https://glycosmos.org).| [github](https://github.com/glycoinfo/GlycanFormatConverter) & [cli](https://gitlab.com/glycoinfo/GlycanFormatConverter-cli) | ... |
| GlycanBuilder2 | WURCSFramework | GlycanBuilder2 is a glycan structure editing tool that supports a wide variety of glycans and can output images using [SNFG symbols](https://www.ncbi.nlm.nih.gov/glycans/snfg.html). It is also used in [GlycoNAVI](https://glyconavi.org), [GlyTouCan](https://glytoucan.org) and [GlyCosmos](https://glycosmos.org). | [github](https://github.com/glycoinfo/GlycanBuilder2) | ... |
| PDB2Glycan | WURCSFramework | It is a tool that analyzes the glycan related data of Protein Data Bank (PDB) and converts it into Resource Description Framework (RDF) data. It is possible to extract information such as the sugar chain structure and the distance between sugar chains. It is also used in [GlycoNAVI](https://glyconavi.org) and OneDep of [wwPDB](https://www.wwpdb.org/). | [gitlab](https://gitlab.com/glyconavi/pdb2glycan) | ... |
| WURCSRDF | WURCSFramework | WURCSRDF is a convert tool that can output from WURCS string to Resource Description Framework (RDF) and SPARQL Query.  It is also used in [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glycoinfo/wurcsrdf) | ... |
| subsumption | WURCSFramework | This tool generates relationships for glycans with the same mass and for glycans with the same composition. | ... | ... |
| GlycanFormatConverter-cli | GlycanFormatConverter | This tool provides GlycanFormatConverter functionality from the CUI. | [gitlab](https://gitlab.com/glycoinfo/GlycanFormatConverter-cli) | ... |
| MolWURCS | WURCSFramework | ... | [gitlab](https://gitlab.com/glycoinfo/molwurcs) | ... |
| GlycanCompositionConverter | GlycanFormatConverter | ... | [gitlab](https://gitlab.com/glycosmos/glycompconverter) | ... |
| SugarDrawer | GlycanFormatConverter | ... | [gitlab](https://gitlab.com/glycoinfo/sugardrawer/sugardrawer) | ... |
| GlycanBuilder2Web | GlycanBuilder2 | ... | [gitlab](https://gitlab.com/glyconavi/glycanbuilder2web) | ... |
| Glycoworkbench | GlycanBuilder2 | ... | [gitlab](https://gitlab.com/glycoinfo/glycoworkbench) | ... |
| wurcs2pic | GlycanBuilder2 | ... | [gitlab](https://gitlab.com/glycoinfo/wurcs2pic) | ... |
| compo2wurcsUI | GlycanCompositionConverter | ... | [gitlab](https://gitlab.com/glycosmos/compo2wurcsui) | ... |
| TCarpRDF | PDB2Glycan | ... | [gitlab](https://gitlab.com/glyconavi/tcarprdf) | ... |

* DBs

| DB | Dependencies | Description | URL | Reference |
| ------ | ------ | ------ | ------ | ------ |
| GlyTouCan | WURCSFramework & GlycanFormatConverter & GlycanBuilder2 | ... | [GlyTouCan](https://glytoucan.org) | ... |
| GlyCosmos | WURCSFramework & GlycanFormatConverter & GlycanBuilder2 & compo2wurcsUI & SugarDrawer | ... | [GlyCosmos](https://glycosmos.org) | ... |
| GlycoNAVI | WURCSFramework & GlycanFormatConverter & GlycanBuilder2 & PDB2Glycan & SugarDrawer | ... | [GlycoNAVI](https://glyconavi.org) | ... |
| wwPDB | PDB2Glycan & wurcs2pic | ... | [wwPDB](https://www.wwpdb.org/) | ... |
| PubChem | MolWURCS | ... | [PubChem](https://pubchem.ncbi.nlm.nih.gov/) | ... |
| GlyGen | WURCS | ... | [GlyGen](https://glygen.org/) | ... |
| CSDB | WURCS | ... | [CSDB](http://csdb.glycoscience.ru/) | ... |




