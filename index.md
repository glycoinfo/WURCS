## WURCS Working Group

The WURCS Working Group is the primary community focusing on the development of glycan representation guidelines, accumulating and reflecting recommendations from international communities.

![Sorbitol](https://github.com/glycoinfo/WURCS/blob/master/docs/logo/WURCS_logo.png?raw=true "WURCS")

## [About WURCS](about.md)

Web3 Unique Representation of Carbohydrate Structures (WURCS) is a representation of carbohydrate structure.

## [Documentation](/doc/WURCS2.md)

## [Tips](tips.md)

## [Tools and Databases](/tools/)


* Software tools supporting WURCS

### Software download

* [https://gitlab.com/GlycoTool/release](https://gitlab.com/GlycoTool/release)

| Tool | Description | Repository | Reference |
| ------ | ------ | ------ | ------ |
| WURCSFramework | WURCSFramework is a framework for WURCS input/output, WURCS string validation and standardization. | [gitlab](https://gitlab.com/glycoinfo/wurcsframework) | ... |
| GlycanFormatConverter | GlycanFormatConverter is core library of glycan text conversion tools. It is also used in [GlycoNAVI](https://glyconavi.org), [GlyTouCan](https://glytoucan.org) and [GlyCosmos](https://glycosmos.org).| [github](https://github.com/glycoinfo/GlycanFormatConverter) & [cli](https://gitlab.com/glycoinfo/GlycanFormatConverter-cli) | Bioinformatics. 2019 Jul 15;35(14):2434-2440. doi: [10.1093/bioinformatics/bty990](https://doi.org/10.1093/bioinformatics/bty990). |
| GlycanBuilder2 | GlycanBuilder2 is a glycan structure editing tool that supports a wide variety of glycans and can output images using [SNFG symbols](https://www.ncbi.nlm.nih.gov/glycans/snfg.html). It is also used in [GlycoNAVI](https://glyconavi.org), [GlyTouCan](https://glytoucan.org) and [GlyCosmos](https://glycosmos.org). | [github](https://github.com/glycoinfo/GlycanBuilder2) | Carbohydr Res. 2017 Jun 5;445:104-116. doi: [10.1016/j.carres.2017.04.015](https://doi.org/10.1016/j.carres.2017.04.015). Epub 2017 Apr 19. PMID: 28525772 |
| PDB2Glycan | It is a tool that analyzes the glycan related data of Protein Data Bank (PDB) and converts it into Resource Description Framework (RDF) data. It is possible to extract information such as the sugar chain structure and the distance between sugar chains. It is also used in [GlycoNAVI](https://glyconavi.org) and OneDep of [wwPDB](https://www.wwpdb.org/). | [gitlab](https://gitlab.com/glyconavi/pdb2glycan) | ... |
| WURCSRDF | WURCSRDF is a convert tool that can output from WURCS string to Resource Description Framework (RDF) and SPARQL Query.  It is also used in [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glycoinfo/wurcsrdf) | ... |
| subsumption | This tool generates relationships for glycans with the same mass and for glycans with the same composition. | ... | ... |
| GlycanFormatConverter-cli | This tool provides GlycanFormatConverter functionality from the CUI. | [gitlab](https://gitlab.com/glycoinfo/GlycanFormatConverter-cli) | ... |
| MolWURCS | MolWURCS is a tool to generate WURCS from chemical structure data such as Molfile. | [gitlab](https://gitlab.com/glycoinfo/molwurcs) | ... |
| GlycanCompositionConverter | This tool generates WURCS from glycan composition notations. It is used by [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glycosmos/glycompconverter) | ... |
| SugarDrawer | SugarDrawer is a web-based glycan structure tool, which supports the depiction of glycans, and a database search. This tool has a unique feature for selecting possible attachment sites, which is defined in the Symbol Nomenclature for Glycans ([SNFG](https://www.ncbi.nlm.nih.gov/glycans/snfg.html)). In addition, this tool can input and output glycans in WURCS and GlycoCT formats, which are the commonly-used text formats for glycan structures. It is also used in [GlycoNAVI](https://glyconavi.org) and [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glycoinfo/sugardrawer/sugardrawer) | Molecules. 2021 Nov 25;26(23):7149. PMID: 34885724 PMCID: PMC8659005 doi: [10.3390/molecules26237149](https://doi.org/10.3390/molecules26237149).  |
| GlycanBuilder2Web | GlycanBuilder2Web is a web-based glycan structure tool, which supports the depiction of glycans, and a database search. This tool support for glycan symbols defined in the Symbol Nomenclature for Glycans ([SNFG](https://www.ncbi.nlm.nih.gov/glycans/snfg.html)). In addition, this tool can input and output glycans in WURCS and GlycoCT formats, which are the commonly-used text formats for glycan structures. It is also used in [GlycoNAVI](https://glyconavi.org) and [GlyCosmos](https://glycosmos.org). | [gitlab](https://gitlab.com/glyconavi/glycanbuilder2web) | ... |
| Glycoworkbench | GlycoWorkbench is a software tool to assist the manual interpretation of MS data. The tool provides an easy to use graphical interface, a set of structural constituents, a collection of fragmentation types, and a broad list of annotation options. | [gitlab](https://gitlab.com/glycoinfo/glycoworkbench) | J Proteome Res. 2008 Apr;7(4):1650-9. doi: [10.1021/pr7008252](https://doi.org/10.1021/pr7008252). Epub 2008 Mar 1. |
| wurcs2pic | wurcs2pic is a command line tool that generates images of glycans from WURCS strings. It is also used in OneDep of [wwPDB](https://www.wwpdb.org/). | [gitlab](https://gitlab.com/glycoinfo/wurcs2pic) | Structure. 2021 Apr 1;29(4):393-400.e1. doi: [10.1016/j.str.2021.02.004](https://doi.org/10.1016/j.str.2021.02.004). Epub 2021 Mar 2. |
| compo2wurcsUI | compo2wurcsUI is a web application that utilizes the functionality of GlycanCompositionConverter. This Web tool translated into form monosaccharide compositions to WURCS. It is available at https://glycosmos.gitlab.io/compo2wurcsui/ . | [gitlab](https://gitlab.com/glycosmos/compo2wurcsui) | ... |
| TCarpRDF | TCarpRDF is a tool that converts PDB data into parsed RDF data in batches using the PDB2Glycan functionality. It is used in [GlycoNAVI](https://glyconavi.org). | [gitlab](https://gitlab.com/glyconavi/tcarprdf) | ... |

* Databases

| Database | Description | URL | Reference |
| ------ | ------ | ------ | ------ |
| GlyTouCan | [GlyTouCan](https://glytoucan.org) is international glycan  structure repository, allowing researchers to assign accession numbers to glycan structures. | [GlyTouCan](https://glytoucan.org) | Nucleic Acids Res. 2021 Jan 8;49(D1):D1529-D1533. doi: [10.1093/nar/gkaa947](https://doi.org/10.1093/nar/gkaa947). |
| GlyCosmos | THe [GlyCosmos Portal](https://glycosmos.org) is a Web portal aiming to integrate the glycosciences with the life sciences. It consists of Standards, Repositories and Data Resources, providing information about genes, proteins, lipids, pathways and diseases. (from GlyCosmos site: https://glycosmos.org/) | [GlyCosmos](https://glycosmos.org) | Nat Methods. 2020 Jul;17(7):649-650. doi: [10.1038/s41592-020-0879-8](https://doi.org/10.1038/s41592-020-0879-8). |
| GlycoNAVI | [GlycoNAVI](https://glyconavi.org) is a website designed to support glycoscience It provides databases and tools for glycans. | [GlycoNAVI](https://glyconavi.org) | ... |
| wwPDB | [wwPDB](https://www.wwpdb.org/) is the organization that handles the registration, data processing, and distribution of PDB data. | [wwPDB](https://www.wwpdb.org/) | Nucleic Acids Res 47: D520-D528 doi: [10.1093/nar/gky949](https://doi.org/10.1093/nar/gky949) |
| PubChem | [PubChem](https://pubchem.ncbi.nlm.nih.gov/) is the world's largest collection of freely accessible chemical information. Search chemicals by name, molecular formula, structure, and other identifiers. Find chemical and physical properties, biological activities, safety and toxicity information, patents, literature citations and more. (from PubChem site: https://pubchem.ncbi.nlm.nih.gov/) | [PubChem](https://pubchem.ncbi.nlm.nih.gov/) | Nucleic Acids Res. 2021;49(D1):D1388–D1395. doi:[10.1093/nar/gkaa971](https://doi.org/10.1093/nar/gkaa971) |
| GlyGen | [GlyGen](https://glygen.org/) is a data integration and dissemination project for carbohydrate and glycoconjugate related data. GlyGen retrieves information from multiple international data sources and integrates and harmonizes this data. This web portal allows exploring this data and performing unique searches that cannot be executed in any of the integrated databases alone. (from GlyGen site: https://glygen.org/) | [GlyGen](https://glygen.org/) | Glycobiology. 2020 Jan 28;30(2):72-73. doi: [10.1093/glycob/cwz080](https://doi.org/10.1093/glycob/cwz080). |
| CSDB | [CSDB](http://csdb.glycoscience.ru/) contains manually curated natural carbohydrate structures, taxonomy, bibliography, NMR, and other data from literature. | [CSDB](http://csdb.glycoscience.ru/) | Nucleic Acids Res. 2016 Jan 4;44(D1):D1229-36. doi: [10.1093/nar/gkv840](https://doi.org/10.1093/nar/gkv840). Epub 2015 Aug 18. |



## Related Links

 * [GlycoNAVI Tools](https://glyconavi.org/Tools/)
 
 * [GlycanFormatConverter Web](https://glyconavi.org/Tools/tool/gfc.php)
 
 * [GlyCosmos API Web](https://glyconavi.org/Tools/tool/cosmos.php)
 
 * [GlyTouCan Glycan Viewer](https://glyconavi.org/Tools/tool/idviewer.php)


## Publications

### WURCS

* WURCS: the Web3 unique representation of carbohydrate structures.
   * J Chem Inf Model. 2014 Jun 23;54(6):1558-66. doi: [10.1021/ci400571e](https://doi.org/10.1021/ci400571e). Epub 2014 Jun 4. PMID: 2826306

* WURCS 2.0 Update To Encapsulate Ambiguous Carbohydrate Structures.
   * J Chem Inf Model. 2017 Apr 24;57(4):632-637. doi: [10.1021/acs.jcim.6b00650](https://doi.org/10.1021/acs.jcim.6b00650). Epub 2017 Mar 22. PMID: 24897372

### Tools using WURCS

* SugarDrawer: A Web-Based Database Search Tool with Editing Glycan Structures.
   * Molecules. 2021 Nov 25;26(23):7149. PMID: 34885724 PMCID: PMC8659005 doi: [10.3390/molecules26237149](https://doi.org/10.3390/molecules26237149). 

* GlycanFormatConverter: a conversion tool for translating the complexities of glycans
   * Bioinformatics. 2019 Jul 15;35(14):2434-2440. doi: [10.1093/bioinformatics/bty990](https://doi.org/10.1093/bioinformatics/bty990).

* Implementation of GlycanBuilder to draw a wide variety of ambiguous glycans.
   * Carbohydr Res. 2017 Jun 5;445:104-116. doi: [10.1016/j.carres.2017.04.015](https://doi.org/10.1016/j.carres.2017.04.015). Epub 2017 Apr 19. PMID: 28525772


## Contact

* yamadaissaku@gmail.com

## Acknowledgements

This work has been supported by NBDC of Japan Science and Technology Agency (JST).
