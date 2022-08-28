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
| MolWURCS | WURCSFramework | MolWURCS is a tool to generate WURCS from chemical structure data such as Molfile. | [gitlab](https://gitlab.com/glycoinfo/molwurcs) | ... |
| GlycanCompositionConverter | GlycanFormatConverter | This tool generates WURCS from glycan composition notations. It is used by [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glycosmos/glycompconverter) | ... |
| SugarDrawer | GlycanFormatConverter | SugarDrawer is a web-based glycan structure tool, which supports the depiction of glycans, and a database search. This tool has a unique feature for selecting possible attachment sites, which is defined in the Symbol Nomenclature for Glycans ([SNFG](https://www.ncbi.nlm.nih.gov/glycans/snfg.html)). In addition, this tool can input and output glycans in WURCS and GlycoCT formats, which are the commonly-used text formats for glycan structures. It is also used in [GlycoNAVI](https://glyconavi.org) and [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glycoinfo/sugardrawer/sugardrawer) | ... |
| GlycanBuilder2Web | GlycanBuilder2 | GlycanBuilder2Web is a web-based glycan structure tool, which supports the depiction of glycans, and a database search. This tool support for glycan symbols defined in the Symbol Nomenclature for Glycans ([SNFG](https://www.ncbi.nlm.nih.gov/glycans/snfg.html)). In addition, this tool can input and output glycans in WURCS and GlycoCT formats, which are the commonly-used text formats for glycan structures. It is also used in [GlycoNAVI](https://glyconavi.org) and [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glyconavi/glycanbuilder2web) | ... |
| Glycoworkbench | GlycanBuilder2 | GlycoWorkbench is a software tool to assist the manual interpretation of MS data. The tool provides an easy to use graphical interface, a set of structural constituents, a collection of fragmentation types, and a broad list of annotation options. | [gitlab](https://gitlab.com/glycoinfo/glycoworkbench) | ... |
| wurcs2pic | GlycanBuilder2 | wurcs2pic is a command line tool that generates images of glycans from WURCS strings. It is also used in OneDep of [wwPDB](https://www.wwpdb.org/). | [gitlab](https://gitlab.com/glycoinfo/wurcs2pic) | ... |
| compo2wurcsUI | GlycanCompositionConverter | compo2wurcsUI is a web application that utilizes the functionality of GlycanCompositionConverter. This Web tool translated into form monosaccharide compositions to WURCS. It is available at https://glycosmos.gitlab.io/compo2wurcsui/ . | [gitlab](https://gitlab.com/glycosmos/compo2wurcsui) | ... |
| TCarpRDF | PDB2Glycan | TCarpRDF is a tool that converts PDB data into parsed RDF data in batches using the PDB2Glycan functionality. It is used in [GlycoNAVI](https://glyconavi.org). | [gitlab](https://gitlab.com/glyconavi/tcarprdf) | ... |

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




