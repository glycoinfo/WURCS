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
