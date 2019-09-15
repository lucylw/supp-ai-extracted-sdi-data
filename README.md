# SDI/SSI dataset

This dataset consists of evidence sentences for supplement-drug interactions and supplement-supplement interactions extracted from PubMed abstracts. These data were automatically extracted and classified, and have not been verified by domain experts or medical professionals.

Supplement and drug entities are identified by a linked UMLS CUI (2018AB). Source papers are identified using Semantic Scholar paper identifiers.

There are two files in this repository:
* `sentence_dict.json`
* `paper_metadata.json`

## Sentences

Evidence sentences are located in `sentence_dict.json`. This is a json dict where keys are interaction identifiers between two CUIs (CUI1-CUI2) and values are lists of evidence sentences extracted from text. Each evidence sentence contains the source paper id, sentence, and two arguments (arg1 and arg2) which correspond to the two CUIs and linked spans within the sentence, e.g.:

```json
"C0004057-C0031610": [{
	"paper_id": "0000c4d7c1904b389cc65c1efdb5e3da94037126", 
	"sentence": "This appears to be dependent upon phospholipase A2 activation, since it is well preserved in the presence of aspirin, which completely blocked both intracellular Ca2+ elevation and phosphatidic acid formation which would indicate phospholipase C activation.", 
	"arg1": {
		"id": "C0004057", 
		"span": [109, 116]
	}, 
	"arg2": {
		"id": "C0031610", 
		"span": [181, 208]
	}
}]
```

In rare cases, the full sentence may not be provided due to publisher restrictions. In those cases, we show the first 50 word tokens in the sentence.

## Paper metadata

Paper metadata is provided in `paper_metadata.json`. This is a json dict where keys are paper ids (corresponding to papers in `sentence_dict.json`) and values are dicts of metadata fields, e.g.:

```json
"0028faac71374d078f40133ffb9f8b6f33146766": {
	"title": "Insulin-induced formation of ruffling membranes of KB cells and its correlation with enhancement of amino acid transport", 
	"authors": [{
		"first": "Kiyota", 
		"middle": null, 
		"last": "Goshima", 
		"suffix": null
	}, {
		"first": "Akiko", 
		"middle": null, 
		"last": "Masuda", 
		"suffix": null
	}, {
		"first": "Katsushi", 
		"middle": null, 
		"last": "Owaribe", 
		"suffix": null
	}], 
	"year": 1984, 
	"pmid": 6321519
}
```