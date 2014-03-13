# EXEMPLAR
----------

EXEMPLAR is an open relation extraction system originating from a research project at the University of Alberta. Relation extraction is the task of, given a text corpus, identifying relations (e.g., acquisition, spouse, employment) among named entities (e.g., people, organizations). Open relation extraction systems like EXEMPLAR are able to identify an open set of relations (as long as they are described in the text) rather than a finite set provided as input.

EXEMPLAR takes text files as input and extracts relations with two or more arguments. For instance, consider the following sentence:

    NFL approves Falcons' new stadium in Atlanta. 
    
Given this sentence, EXEMPLAR extracts an instance of the relation `approve new stadium` whose arguments are "NFL", "Falcons" and "Atlanta".

	Relation: approve new stadium
	    SUBJ: NFL
	    POBJ-OF: Falcons
		POBJ-IN: Atlanta

The role of an argument can be one of the following: SUBJ (subject), DOBJ (direct object) and POBJ (prepositional object). We often append the preposition of a POBJ argument to its role (e.g., "POBJ-IN" for preposition "in"). EXEMPLAR makes an educated guess when the preposition of a POBJ argument is implicit. This is the case for "Falcons" in this example.

## People

* Filipe Mesquita (<mesquita@ualberta.ca>)
* Jordan Schmidek (<schmidek@ualberta.ca>)
* Denilson Barbosa (<denilson@ualberta.ca>)


## Running

    $ ./exemplar parser input output

* parser: the parser to be used. Valid options are: stanford and malt.

* input: path to the document file or directory containing the 
document files. The tool will recursively look for .txt files in subdirectories.

* output: path to the file where the triples will be stored. 

## Sample Output

The output file contains one relation per line. Fields are separted by tab in the following order: Subjects, Relation, Objects, Normalized Relation and Sentence. This is the output for our example:

    SUBJ:NFL#ORG <tab> approves new stadium <tab> POBJ-OF:Falcons#ORG,,POBJ-IN:Atlanta <tab> approve new stadium <tab> NFL approves Falcons ' new stadium in Atlanta .

The suffix in each argument corresponds to its type. Possible types are person (PER), organization (ORG), location (LOC) and miscellaneous (MISC). Subjects and objects are 
separated by double comma (",,"), if more than one exists.


## Libraries

The main libraries used in this tool are:

* Stanford Parser: tokenization, lemmatization, part-of-speech tagging, named entity recognition and dependency parsing.
* Malt Parser: dependency parsing.

## Citing
If you use this code in your research, please acknowledge that by citing:

    @INPROCEEDINGS { mesquita-schmidek-barbosa:2013:EMNLP, 
		AUTHOR = { Filipe Mesquita and Jordan Schmidek and Denilson Barbosa }, 
		BOOKTITLE = { Proceedings of the 2013 Conference on Empirical Methods in Natural Language Processing }, 
		MONTH = { October }, PAGES = { 447--457 }, 
		PUBLISHER = { Association for Computational Linguistics }, 
		TITLE = { Effectiveness and Efficiency of Open Relation Extraction }, 
		PDF = { http://www.aclweb.org/anthology/D13-1043 }, 
		YEAR = { 2013 }
	} 

## Acknowledgements
This work was primarily funded by the NSERC Business Intelligence Network (BIN). 