# WURCS - Web3 Unique Representation of Carbohydrate Structures -

* Version 2.0

## Introduction

### Theoretical considerations

Figures

* A generic schema of a complex carbohydrate sequence. (A) Squares represent vertexes, arrows symbolize directed edges. Carbohydrate sequence may contain repeating units with non-stoichiometric modification (STA), multiple connections between vertexes, cyclic subgraphs, alternative residue declarations and fuzzily defined capping unit locations. (B) More detailed representation of (A) in WURCS. Squares are backbone of monosaccharides and circles are modifications connected backbones. In WURCS representation, an edge can link only between a backbone and a modification. So that the linkage between two backbones, such as glycosidic linkage, must be represented by one modification and at least two edges. (C) Legend of (B).


### WURCS: Introduction

* WURCS (Web3 Unique Representation of Carbohydrate Structures) is the notation scheme and algorithm for the wide-ranging and complex carbohydrate structure data on the databases to code a unique linear format based on atomic level information about monosaccharides and their linkages.


#### The WURCS format is follows:

`WURCS=<Version>/<Unit Count>/<UniqueRES List>/<RES Sequence>/<LIN List>`


* The format starts with “WURCS=” and is followed by the sections Version, Unit Count, UniqueRES List, RES Sequence, and LIN List, separated by forward slashes “/”. Version is the WURCS version (currently 2.0), Unit Count is the section which contains the number of UniqueRESs, RESs, and LINs, UniqueRES List is the section in which UniqueRESs are listed, RES Sequence is the section which uniquely lists the RESs in order, and LIN List is the section in which LINs are listed.  Here, UniqueRES is a string representing every unique monosaccharide contained in the glycan, RES is an index number of the UniqueRES in UniqueRES List representing each monosaccharide residue, and LIN is a string representing linkage information between two or more different RESs. Components of these sections are ordered according to a sorting algorithm (described in detail in Section 4).


#### Definitions of each section and component

* Each section in WURCS 2.0 is also composed there components.
The Version section describes the current WURCS version as follows:

`<Version>:   	2.0 (current version)`

* The Unit Count section is as composed of UniqueRES Count, RES Count and LIN Count, in order separated by commas “,” as follows:

`<Unit Count>:	<UniqueRES Count>,<RES Count>,<LIN Count>`

* They represent the number of UniqueRESs, RESs and LINs, respectively, in the representative glycan.  However, there may be the case when the number of linkages is uncertain.  Therefore, if the glycan potentially contains uncertain linkages, Uncertain LIN Count is used instead as follows:

`<Uncertain LIN Count>:	<LIN Count>+`

* For Uncertain LIN Count, plus “+” is added after the LIN Count, where LIN Count indicates the number of known linkages.  Here, plus “+” indicates that there may potentially be more than LIN Count linkages.
The UniqueRES List section is composed of one or more UniqueRESs with no separator as follws:

`<UniqueRES List>:	<UniqueRES #1><UniqueRES #2>...<UniqueRES #n>`

* A UniqueRES is the ResidueCode enclosed in square brackets “[” and “]” as follows:

`<UniqueRES>:		[<ResidueCode>]`

* ResidueCode represents a monosaccharide residue consisting of a backbone and its modifications and is composed of a BackboneCode and some MODs separated by underscore “_” as follows:

`<ResidueCode>:	<BackboneCode>_<MOD #1>_<MOD #2>_..._<MOD #n>`

* BackboneCode represents the backbone structure of the monosaccharide residue and is composed of SkeletonCode and Anomeric Information, described above, separated by a hyphen “-” as follows:

`<BackboneCode>:	<SkeletonCode>-<Anomeric Information>`

* SkeletonCode represents a backbone carbon chain structure and is a sequence of CarbonDescriptors, as described above.
MOD represents a substituent modifying a backbone and is composed of LIPs and a MAP, where each LIP is separated by a hyphen “-” followed by MAP as follows:

`<MOD>:	<LIP #1>-<LIP #2>-...-<LIP #n><MAP>`

* Here, LIP represents the linkage information between a backbone and its modification, and is composed of Position, Direction and Star Index as follows:

`<LIP>:		<Position><Direction><Star Index>`

* Position is the carbon number of the backbone, which is represented either by a positive integer or a question mark “?” indicated as an unknown position.  Direction is an alphabetical symbol that represents the comparison of the modifications that are connected to the same backbone carbon. Star Index is the index number of backbone carbon indicated by an asterisk “*” in the MAP and is represented by a positive integer. Direction and Star Index are omittable.

* MAP represents the atomic path of the modification, including the connecting backbone carbon, sorted by the same algorithm as used in WURCS 1.0.  The backbone carbon in the MAP is represented by an asterisk “*”.  If the MAP has multiple asterisks and the asterisk positions in the MAP can be distinguished, Star Indices are added to the back of each asterisk “*” for indexing.

* The RES Sequence section is composed of one or more RESs separated by a hyphen “-” as follows:

`<RES Sequence>:	<RES #1>-<RES #2>-...-<RES #n>`

* A RES is represented by the numerical index number in the UniqueRES List of the UniqueRES to which it corresponds. Each of RESs in this section is ordered by a sorting algorithms. 

* The LIN List section is composed of a list of LINs separated by an underscore “_” as follows:

`<LIN List>:	<LIN #1>_<LIN #2>_..._<LIN #n>`

* If there is no LIN, e.g. in the case of a single monosaccharide, LIN List is left blank. A LIN is composed of one or more GLIPs and a MAP as follows:

`<LIN>:        	<GLIP #1>-<GLIP #2>-...-<GLIP #n><MAP>`

* A GLIP is the same as a LIP, except that the connecting modification bridges two or more backbones. Therefore, GLIP requires the specification of a RES Index as follows:

`<GLIP>:	<RES Index><Position><Direction><Star Index>`

* RES Index is the alphabetical index of the corresponding RES #, where a = 1, b = 2, etc.  Thus, the components of LIP and GLIP can be parsed by alternating alphabet and number, greatly reducing the length of the whole string. This notation is a major change from WURCS 1.0.

* To handle ambiguous linkages, several sections are defined in both WURCS 1.0 and 2.0. If the linkage information is represented statistically, Statistic LIP is used instead of LIP. For Statistic LIP, the Probability Range is enclosed by two percent sign symbols “%”, alongside the LIP section as follows:

`<Statistic LIP>:	%<Probability Range>%<LIP> or <LIP>%<Probability Range>%`

* If the Probability Range precedes LIP, the probability indicates that the LIP on the backbone side is indefinite, and if it follows LIP, the opposite holds.  Within the Probability Range, the upper and lower probability values are separated by a hyphen “-”, but these are represented as a single value if they are the same, as follows:

`<Probability Range>:	<Upper Probability>-<Lower Probability> or <Probability>`

* The probability value is represented as a decimal fraction, with no zero in the whole number position, e.g. “0.333” is represented as “.333”.  A question mark “?” is used for an unknown probability value.
If alternative linkage positions are possible, Alternative LIP is used instead of LIP.  For Alternative LIP, each candidate LIP is separated by a vertical bar “|” as follows:

`<Alternative GLIP>:	<GLIP #1>|<GLIP #2>|...|<GLIP #n>`

* Statistic LIP and Alternative LIP cannot be used together.
Statistic GLIP and Alternative GLIP can also be used in the same way as Statistic LIP and Alternative LIP, respectively. These are represented as follows:

`<Statistic GLIP>:	%<Probability Range>%<GLIP> or <GLIP>%<Probability Range>%`

`<Alternative GLIP>: 	<GLIP #1>|<GLIP #2>|...|<GLIP #n>`

* If Alternative GLIP contains linkages toward two or more backbones, RES Alternative GLIP is used instead. In the RES Alternative GLIP section, curly brackets “{” or “}” are added surrounding Alternative GLIP as follows:

`<RES Alternative GLIP>:	{<Alternative GLIP> or <Alternative GLIP>}`


* If the glycan has a repeating unit, Repeated LIN is used instead of LIN.  Repeated LIN contains the linkage LIN between the starting and ending monosaccharides in the repeating unit.  In Repeated LIN, the Repeat Count Range section is added following the LIN separated by a tilde “~” as follows:

`<Repeated LIN>:      	<LIN>~<Repeat Count Range>`

* In Repeat Count Range, the maximum and minimum count numbers are separated by a colon “:” or a single number is used if they are the same as follows:

`<Repeat Count Range>:	<Max Repeat Count>:<Min Repeat Count> or <Repeat Count>`

* The count number is represented as a positive integer.  “n” is used for an unknown count number.

### Omission rules

* MOD is omitted if the substituent is a hydrogen, hydroxyl or carbonyl group.
MAP is omitted if it is an ether linkage.

* Star Index is omitted if the number of Star Index is zero “0”.
Direction is omitted if it is obvious from CarbonDescriptor, but it cannot be omitted if Star Index is not omitted. In this case, “n” is used for the Direction to serve as a separator between Position and Star Index. CarbonDescriptors when Direction is not omitted are “M”, “C”, “c”, “N”, “n”.


## Definitions of WURCS component

### Glycan

* In WURCS definition, glycan strucuture consists following components;

| definition | description|
|---|---|
| Backbone | The carbon backbone of a monosaccharide (residue) in a glycan containing only carbons. The backbone has three carbon atoms at least.|
| Modification | Components of monosaccharides other than the backbone carbons. |
| Aglycone | The non-sugar component of a glycan. |
| Connection | The connection information between a backbone and a modification or an aglycone. |

* Based on the difinitions, monosaccharides and these linkage is defined anew as following;

| definition | description|
|---|---|
| Monosaccharide | A combination of a Backbone, Modification(s) on the Backbone and their Connection(s). |
| Linkage | A combination of a Modification bridging two or more Backbones and their Connections. |

* Each components are encoded to the string based on each rules.


### Backbone

#### Definition:

* A carbohydrate is a polyhydroxy aldehyde or -ketone. The substance class of alditols is treated as carbohydrates.

 - Aromatic or carbocyclic ring is not treated as carbohydrate.

* A backbone is the carbon backbone of a monosaccharide in a glycan containing only carbons.

 - Hydroxyl groups and hydrogens attached a backbone carbon are also treated as modification.

 - A ring information is not treated as backbone.


* Backbone structure is represented as SkeletonCode. If Backbone has anomeric center Anomeric Information is also contained.

### Modification

#### Definition:
* Components of glycans other than the carbon of monosaccharide backbones.
* Modification also include in the hydrogen and oxygen atoms attached to the carbons of the backbones in addition to other heteroatoms.
* Modification is represented as MAP.


### Aglycone

* The non-sugar component of a glycan, which is usually connected to the anomeric carbon position of backbone. In WURCS, aglycone is a Modification but not treated in standard. If you want to contain the aglycone to the WURCS, “@” is used instead of the MAP but it is not standard WURCS. GlyTouCan allow only standard WURCSs.

* For example, WURCS of a D-glucopyranoside which has aglycone is represented as following:

`WURCS=2.0/1,1,0/[a2122h-1x_1-5_1@]/1/`

* For the MAP of aglycone, you can contain only “@”. Another information must not be contained in WURCS. If you also want to contain two or more different aglycones, these numbers distinguished aglycones is added to “@” such as “@1” and “@2”.


### Connection

* The connection information between a backbone and a modification. That have linkage position information, direction of the connection and connected atom position of the modification.
These information are represented as LIP or GLIP.


## WURCS Format Components

### SkeletonCode

* SkeletonCode is a string representation of backbone carbons including the adjacent atoms in modification. Each character of a SkeletonCode is called a CarbonDescriptor. The SkeletonCode is similar to the Extended Stereocode used for representing monosaccharides in MonosaccharideDB. The length of a SkeletonCode is dependent upon the number of carbons in the backbone (e.g. six CarbonDesciptor represent that is a hexose). 


Fig

* For example, aldehydo-D-glucose is represented using SkeletonCode as “o2122h”. If the SkeletonCode contains an anomeric center (CarbonDescriptor “a”) such as α-D-glucopyranose shown in Figure 1, the relevant Anomeric Information section must be included (as described in the next section).

* In order to represent monosaccharide structures of unknown carbon chain length, we defined descriptors “<” and “>”.  Thus, CarbonDescriptors that are repeated (with unknown count) are enclosed by “<” and “>”.  For example, glycelaldehyde, tetrose, pentose, and hexose are aldoses, and these open-chain forms are represented using SkeletonCode as “oxh”, “oxxh”, “oxxxh”, “oxxxxh”, respectively. That is, the SkeletonCode of an open-chain aldose is terminated by “o” and “h” and contains a repeated “x”. Thus, such aldoses can be simply represented as “o<x>h” by using “<” and “>”.


### CarbonDescriptor

* A CarbonDescriptor represent the condition of connectivity and stereochemistry of neighboring atoms around a backbone carbon. In particular, we defined the classification method for CarbonDescriptor to represent the condition of (potential) carbonyl groups. This resulted definitions to the CarbonDescriptor list (described in detail in Appendix).

* Our classification was performed based on the following terms: (1) whether it is a backbone carbon of a monosaccharide, (2) the position of the backbone carbon, (3) whether the backbone carbon has hydrogen(s), (4) information between neighboring atoms on the backbone carbon, (5) stereochemistry and geometrical isomerism of any double bonds linked to any backbone carbon, (6) whether the backbone carbon is anomeric.

* Details regarding this classification is described in the Appendix.  Table 3.2-1 lists the common CarbonDescriptors defined in WURCS 2.0 as a result of this classification.



#### Table 3.2-1 CarbonDescriptors for the generic functional groups of monosaccharide. In Fischer projection, X and Y are atoms other than hydrogen and backbone carbons. A is a hetero atom in ether ring.



| Fischer projection | Typical functional group | CarbonDescriptor | Position in the backbone |
|---|---|---|---|



### Anomeric Information

* Anomeric Information represents position and stereochemistry of anomeric center. If one of the backbone carbons is anomeric center, Anomeric Information must be added to the SkeletonCode following a hyphen “-”. If no anomeric center exists, e.g. open chain form or alditols, the Anomeric Information is omitted. It is also omitted if it is not certain whether or not anomeric center exists.

* AnomericPosition represents position number of anomeric center. The position must be the same as the position of CarbonDescriptor “a” in SkeletonCode. Most aldoses have the number “1” and 2-ketoses have “2”. “?” is used for an unknown anomeric position.

* Anomeric Symbol represents stereochemistry of anomeric center. α anomer is represented as symbol “a” and β anomer is represented as symbol “b”. These two anomers are designated according to the configurational relationship between the anomeric center and the anomeric reference atom, hence “a” and “b” are relative stereodescriptors. In WURCS 2.0, new symbols “u” and “d” are defined to represent absolute stereodescriptors. When an exocyclic atom (not hydrogen) connected to the anomeric center is on the left side in cyclic Fischer projection, the Anomeric Symbol is “u” (“u”pside in the Haworth representation). When the exocyclic atom is on the right side, the Anomeric Symbol is “d” (“d”ownside in the Haworth representation). Table 3.3-1 shows these differences in detail. To ensure uniqueness in WURCS representation, these are used only when stereochemistry of anomeric center is specified and anomeric reference atom is not. When the stereochemistry of anomeric center is unknown, the Anomeric Symbol is “x”. “o” represents open chain form explicitly and is usually omitted. To ensure uniqueness in WURCS representation, “o” is used only if it is clearly an open chain form but the information can not be added to the SkeletonCode, e.g. any open chain monosaccharides “<Q>-?o”. These Anomeric Symbols are summarized below.


| Anomeric Symbol | Descriptin |
|---|---|
|	a	| alpha |
|	b	| beta |
|	u	| up	(absolute representation) |
|	d	| down	(absolute representation) |
|	x	| unknown |
|	o	| no anomeric center	(only when it must be indicated that the anomeric center is not existed when the anomer is not represented in SkeletonCode) |


##### Table 3.3-1. Comparisons of Anomeric Symbols “a”, “b”, “u” and “d”, corresponding to monosaccharide structures represented by Haworth representation and Fischer projection, and the configurational relationships between the anomeric center and the anomeric reference atom in the Fischer projection.



| Symbol | Haworth representation*1 | Fischer projection*1 | Configurational relationship*2 |
|---|---|---|---|



Fig.

* For example, while the structure must be represented using multiple notations in the other notations, e.g. β-D-gluculonic acid or α-L-idulonic acid in IUPAC notation, WURCS can represent this as a single SkeletonCode “a212xA” since the anomeric reference atom C-5 can be represented as “x” which is CarbonDescriptor representing an unknown chiral center.
In this example, AnomericSymbol “u” is used to represent the absolute configuration of the anomer.
Thus the BackboneCode of this structure is represented as “a212xA-1u”.


### MAP (Modification Atom Path)

* MAP is string representation of a modification including adjacent carbon(s) in backbone(s). We simply note here that asterisks “*” are used in the MAP string to indicate the adjacent carbons. When the modification type of a MAP is implied in CarbonDescriptor of the connected backbone carbon, the MAP must be omitted. Usually, hydrogens, hydroxyl groups, and carbonyl groups are omitted because these can be distinguished by the CarbonDescriptors.

##### Table 3.4-1

|Abbreviation | Substituent group | MAP |
|---|---|---|
|-H | Hydrogen | *  (H is omitted) |
|-OH | Hydroxyl | *O |
|-O- | Ether | *O* |
|-N | Primary Amine | *N |
|-Me | C-linked Methyl | *C |
|-OMe | O-linked Methyl | *OC |
|-Ac | C-linked Acetyl | *CC/2=O |
|-OAc | O-linked Acetyl | *OCC/3=O |
|-NAc | N-Acetyl | *NCC/3=O |
|-NGc | N-Glycolyl | *NCCO/3=O |
|-P | Phosphate | *OPO/3O/3=O |
|-S | Sulfate | *OSO/3=O/3=O |
|-Pyr | Pyruvate | *OCCC/4=O/3=O |
|-PC | Phosphocholine | *OPOCCNC/7C/7C/3O/3=O |
|-PEtn | Phosphoethanolamine | *OPOCCN/3O/3=O |
|-PPEtn | Diphosphoethanolamine | *OPOPOCCN/5O/5=O/3O/3=O |

* Divalent (or more multi-valent ) substituent has multiple asterisks “*”. If these are not equivalent in the MAP, each “*” is numbered using the priority rule (described in details in Appendix). The number is called Star Index.

* In other words for “equivalent”, it is that the MAPs generated by the traverse of modification substructure started from the different asterisks become same string. Therefore, same Star Index is applied to these asterisks. Conversely, the not equivalent asterisks are distinguished by the Star Index.

* On the other hand, the MAP must be generated only from atoms in the modification substructure. Because the MAP string should be able to represent the modification substructure by itself. Moreover, the same modification substructures should have a same MAP to ensure uniqueness. Therefore, Star Index must be determined uniquely by only atoms of modification substructure. Thus, the priority rules for asterisks are also defined.

* For example, 2-aminoethanol (ethanolamine) having two linkages to backbone(s) on the oxygen and nitrogen atoms has two asterisks but there are two possible MAPs as illustrated in Figure 3.4-1. Here, the start atom of the MAP is always “*1” because it has most higher priority of all asterisks and it is selected to the start node of the traverse for modification substructure. In this case, “*1OCCN*2” is correct due to “O” is prior than “N” in the priority rule.


##### Figure 3.4-1 2-aminoethanol (ethanolamine) having two linkages to monosaccharide backbones.



* For example, the MAP of phytosphingosine (2S,3R,4R-2-amino-octadecane-1,3,4-triol) having four linkages to backbone(s) on the oxygen and nitrogen atoms has four asterisks and these are numbered by Star Index as illustrated in Figure 3.4-2.



##### Figure 3.4-2 phytosphingosine (2S,3R,4R-2-amino-octadecane-1,3,4-triol) having four linkages to monosaccharide(s) on the oxygen and nitrogen atoms and its MAP string.


*  If some “*” are equivalent in the MAP, these are numbered by the same Star Index.


### Definition of symbols in MAP

* In MAP string, several symbols are used to represent atom information in the chemical graph. These indicate element of atoms, backbone carbons, branch, cyclic, type of bond, stereochemical information of atoms or bonds and aromatic atoms.

##### Table 3.4.1-1. Description for the MAP symbols.


| Symbol | Description |
|---|---|
|H, C, O, ... | Atom symbol. An atom cannot be represented as abbreviation such as “Me” and “Et”. |
|*[n] | Backbone carbon in MAP. If multiple backbone carbons are contained in MAP and these carbons are not equivalent, StarIndex is added after “*”. |
|/n | Branching atom appeared in MAP already. n is an index number of atom at branching point in MAP atoms. |
|$n | Cyclic. n is an index number of atom at cyclic point in MAP atoms. |
|=, # | Double and triple bond, respectively. |
|^R, ^S, ^X | Chiral information to the previous atom. R and S are based on CIP rule. X indicate unknown chirality.  |
|^E, ^Z, ^X | Geometrical isormerism to the previous bond. E and Z are based on CIP rule. X indicate unknown E/Z. |
|(, ) | Start and end of aromatic atom group. In this group, double bond “=” is omitted.

##### Figure 3.4.1-1. Example of numbering for index numbers of atoms in large MAP.


### Ambiguous MAP string



### Generation of MAP string

* In contrast to the backbone, modifications are represented as a general graph structure that contains branches and loops in their chemical structure. The modifications are also represented as linear strings. At this time, to represent stereochemistry of modification atoms which are directly attached to the backbone, the backbone atoms which have directly attached modifications are included in the MAP.
* In the following explanation of MAP string generation, the word “modification” refers to the substructure of the modification including the directly attached atoms of the backbone. A MAP is generated as follows. First, select the starting node in the modification using determineStartingNode. Next, depth-first search is conducted on all the modifications starting from the selected starting node using traverseModification, and the traversed results are represented as a traversed list. The traversed list has five parameters: traverseNo, startingNo, endingNo, atom and bond. Information about the start and end node of a bond which are passed in the traverse are converted to the traverseNo of the record which stores the corresponding atom to atom. Then the corresponding traverseNo is stored in startingNo and endingNo. The starting node of a traverse is set to the following: (traverseNo, startingNo, endingNo, atom, bond) = (1, null, 1, starting node, null).
* In the following steps of traverse, all start atoms of bonds are considered to be pre-traversed atoms. Thus we can set the traverseNo of pre-traversed atoms to the corresponding startingNo. On the other hand, the ending atom of bonds can be either a pre-traversed atom or a non-traversed atom. If the ending atom of a bond is a pre-traversed atom, we set traverseNo of the pre-traversed atom to endingNo and set atom to null, otherwise we set the current traverseNo to endingNo and set the end node of the bond to atom. bond is set to bond. Finally the traverse list is converted to an MAP string using outputMAP. For example, the following illustrates that atoms 2-3-5-7-9 forms the backbone. The modification which contains atoms 9, 10, 11, 12, 13 and 14 is converted to the MAP string “*OPO/3O/3=O”.


































## Generation of MAP
### MAP vs substituent name

Table 6.2-1. Monovalent substituents

|Abbreviation | Substituent group | Substituent name in MonosaccharideDB*1 | MAP string|
|---|---|---|---|
|-Ac | C-linked acetyl | (nd:1)acetyl | *CC/2=O|
|-OAc | O-acetyl | (no:1)acetyl | *OCC/3=O|
|-NAc | N-acetyl | (nd:1)n-acetyl | *NCC/3=O|
|-Br | C-linked bromo | (nd:1)bromo | *Br|
|-Cl | C-linked chloro | (nd:1)chloro | *Cl|
|-Et | C-linked ethyl | (nd:1)ethyl | *CC|
|-OEt | O-linked ethyl | (no:1)ethyl | *OCC|
|-F | Fluoro  | (nd:1)fluoro | *F|
|-CHO | C-linked formyl | (nd:1)formyl | *C=O|
|-OCHO | O-formyl | (no:1)formyl | *OC=O|
|-NCHO | N-formyl | (nd:1)n-formyl | *NC=O|
|-Gc | C-linked glycolyl | (nd:1)glycolyl | *CCO/2=O|
|-OGc | O-glycolyl | (no:1)glycolyl | *OCCO/3=O|
|-NGc | N-glycolyl | (nd:1)n-glycolyl | *NCCO/3=O|
|-CO | Hydroxymethyl | (nd:1)hydroxymethyl | *CO|
|-I | Iodo | (nd:1)iodo | *I|
|-Me | C-linked Methyl | (nd:1)methyl | *C|
|-OMe | O-methyl | (no:1)methyl | *OC|
|-NMe | N-methyl | (nd:1)n-methyl | *NC|
|-NAra | N-alanine | (nd:1)n-alanine | *NCC^XC/4N/3=O|
|0 | N-dimetyl | (nd:1)n-dimethyl | *NC/2C|
|-OC(=O)–(CH2)2–COOH | O-succinate | (no:1)succinate | *OCCCCO/6=O/3=O|
|-NHC(=O)–(CH2)2–COOH | N-succinate | (nd:1)n-succinate | *NCCCCO/6=O/3=O|
|-NC(=O)CF3 | N-trifluoroacetyl | (nd:1)n-trifluoroacetyl | *NCCF/4F/4F/3=O|
|-C(=O)=O | Nitrate | (nd:1)nitrate | *C=O/2=O|
| | C-linked (R)-lactate | (nd:1)(r)-lactate | *CC^RC/3O/2=O|
| | C-linked (S)-lactate | (nd:1)(s)-lactate | *CC^SC/3O/2=O|
| | O-linked (R)-lactate | (no:1)(r)-lactate | *OCC^RC/4O/3=O|
| | O-linked (S)-lactate | (no:1)(s)-lactate | *OCC^SC/4O/3=O|
|-SH | Thio | (no:1)thio | *S|
|-C(=NH)NH2 | C-linked amidino | amidino | *CN/2=N|
|-NHC(=NH)N | N-amidino | n-amidino | *NCN/3=N|
|-CCOOH | C-linked carboxymethyl | carboxymethyl | *CCO/3=O|
| |  | (r)-carboxyethyl | *C^RCO/3=O/2C|
| |  | (s)-carboxyethyl | *C^SCO/3=O/2C|
| |  | (no:1)phospho-choline | *OPOCCNC/7C/7C/3O/3=O|
| |  | phosphate | *OPO/3O/3=O|

*1 n is number of linkage position.
