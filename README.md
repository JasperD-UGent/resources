# resources
This repository contains the resources I (co-)created. If you want to use the resources, please carefully read the license agreement (``LICENSE``).

The first part of every directory refers to the language of the resources:
- ES = Spanish

Each filename consists of three parts, separated by an underscore:
1. Short description of the resource
2. Source of the resource
   1. ``custom`` = self-compiled
   2. ``SCAP`` = based on corpora that have been compiled within SCAP (Spanish Corpus Annotation Project), a project launched in 2020 at [Ghent University](https://www.ugent.be/), Belgium (see [project description page](https://research.flw.ugent.be/en/projects/scap-spanish-corpus-annotation-project) and [online environment](https://scap.ugent.be/))
3. Version of the resource, starting at ``v1``

## ES_anaphorLists

### Active resources
- ``adverbialAnaphorList_custom_v1.txt``: TXT file containing a self-compiled list of adverbial anaphors in Spanish.

### Deprecated resources
None

## ES_associationMeasureLists
Association measures used in the resources:
- **Delta P**: (uni)directional metric (i.e. its values will differ depending on which word functions as the "cue") that is considered one of the most suitable association measures because it (1) normalises conditional probabilities, (2) has a computationally straightforward calculation, and (3) is rooted in psychological/psycholinguistic theory (Ellis, 2006; Gries, 2013).
- **LMI** (Lexicographer's Mutual Information): bidirectional or symmetric measure that computes the probability of two words co-occurring together in a corpus and balances out the tendency of the regular mutual information measure (also called Pointwise Mutual Information or PMI) to assign very high scores to low-frequency words because it multiplies the PMI score by the absolute co-occurrence frequency. We employ the normalised variant of the PMI measure, which normalises PMI scores in the [-1, 1] range by dividing the PMI value by the negative logarithm of the co-occurrence probability *p*<sub>(word_1, word_2)</sub> (Bouma, 2009). The use of the normalised PMI metric should improve the interpretability of the values as well as reduce the impact of the sizes of the corpora used to calculate the LMI values.

### Active resources
- ``deltaP-NOUN-ADJ_SCAP_v1.json``: Python dictionary that presents delta P values for a series of Spanish noun-adjective bigrams in an adjectival modifier (``"amod"``) dependency relation. The values for each bigram are stored in a nested dictionary under the ``"delta_P"`` key, the SCAP corpora used to calculate the bigram frequencies are stored under the ``"corpora"`` key. Let us take the noun *comisión* and the adjective *rogatorio* as an example: the entry ``"comisión_NOUN|rogatorio_ADJ"`` should be interpreted as "given *rogatorio* in an *amod* dependency relation as the cue, how likely is it that we see *comisión* as the other member of the pair", whereas the entry ``"rogatorio_ADJ|comisión_NOUN"`` should be interpreted the other way around, as "how predictive is *comisión* of *rogatorio*".
- ``deltaP-VERB-NOUN_SCAP_v1.json``: Python dictionary that presents delta P values for a series of Spanish verb-noun bigrams in a subject (``"subj"``), indirect object (``"iobj"``), direct object (``"obj"``), or oblique (``"obl"``) dependency relation.
- ``LMI-NOUN-ADJ_SCAP_v1.json``: Python dictionary that presents LMI values for a series of Spanish noun-adjective bigrams in an adjectival modifier (``"amod"``) dependency relation. The values for each bigram are stored in a nested dictionary under the ``"LMI"`` key, the SCAP corpora used to calculate the bigram frequencies are stored under the ``"corpora"`` key. Let us take the noun *comisión* and the adjective *rogatorio* as an example: the entry ``"comisión|NOUN_rogatorio|ADJ"`` (the words appear in alphabetical order) should be interpreted as how probable it is these two words co-occur in an *amod* dependency relation (regardless of co-occurrence data with other words). The values are provided in a nested dictionary, consisting of ``"MI"`` (PMI score), ``"MI_normalised"`` (normalised PMI score, see above), and ``"LMI"`` (LMI score) as its keys.
- ``LMI-VERB-ADJ_SCAP_v1.json``: Python dictionary that presents LMI values for a series of Spanish verb-noun bigrams in a subject (``"subj"``), indirect object (``"iobj"``), direct object (``"obj"``), or oblique (``"obl"``) dependency relation.

### Deprecated resources
None

## ES_frequencyDictionaries

### Active resources
- ``frequencyDictionary-percentiles_SCAP_v1.json``: Python dictionary that presents frequency data for the content words occurring in a targeted selection of SCAP corpora. The frequency data for each word are stored under the ``"frequency_dictionary"`` key, the corpora used to calculate the frequency data are stored under the ``"corpora"`` key. Words are grouped in a nested dictionary per part-of-speech tag (``"PROPN"`` for proper nouns, ``"X"`` for other, ``"ADV"`` for adverbs, ``"NOUN"`` for nouns, ``"VERB"`` for verbs, and ``"ADJ"`` for adjectives) and frequencies are calculated at lemma level. The frequency data are stored in the form of a nested dictionary as well and always include information on the absolute frequency (``"freq"``) and frequency percentile (``"percentile"``). If the part-of-speech tag contains more than 10,000 lemmas, the percentile within the top 10,000 most frequent lemmas is added to the dictionary (``"percentile_top_10K"``; lemmas that are not among the top 10,000 are assinged ``"NA"`` as their value). For nouns, verbs, and adjectives the dictionary also contains the key ``"percentile_top_10K_NOUN|VERB|ADJ"``, which corresponds to the frequency percentile within the top 10,000 most frequent nouns, verbs, and adjectives combined.
- ``lemma-n-grams_SCAP_v1``: Python dictionary that presents absolute frequency data for the *n*-grams (with lemmas as the lexical unit) occurring in a targeted selection of SCAP corpora. The frequency data for each *n*-gram are stored under the ``"lemma_n_grams"`` key, the corpora used to calculate the frequency data are stored under the ``"corpora"`` key. *N*-grams are grouped in a nested dictionary per value of *n* (for now, only the results for *n*=5 are included) and the members of the lemma *n*-gram are separated by a pipe (e.g., ``"creer|que|ser|hora|de"``).

### Deprecated resources
None

## ES_lexica

### Active resources
- ``lemmaList_SCAP_v1.json``: Python dictionary that links Spanish word pairs consisting of a token and a part of speech (POS) to a list of possible lemmas for that token-POS combination. The word pairs are stored in a nested dictionary under the ``"frequency_dictionary"`` key, the SCAP corpora taken into account to determine the lemmas are stored under the ``"corpora"`` key.
- ``tokenList_SCAP_v1.json``: Python dictionary containing the list of tokens that occur in a targeted selection of SCAP corpora. The list of tokens is stored under the ``"token_list"`` key, the SCAP corpora taken into account to determine the token list are stored under the  ``"corpora"`` key.

### Deprecated resources
None

## ES_specificVocabularyLists

### Active resources
- ``sensitiveVocabularyList_custom_v1.txt``: TXT file containing a self-compiled list of sensitive vocabulary in Spanish, categorised based on the PARSNIP approach (Gray, 2010) plus swear words as an additional category.
- ``speakingVerbList_custom_v1.text``: TXT file containing a self-compiled list of Spanish speaking verbs (i.e. verbs that can introduce direct speech).

### Deprecated resources
None

## References
- Bouma, G. (2009). Normalized (pointwise) mutual information in collocation extraction. *Proceedings of GSCL*, *30*, 31–40.
- Ellis, N. C. (2006). Language Acquisition as Rational Contingency Learning. *Applied Linguistics*, *27*(1), 1–24. https://doi.org/10.1093/applin/ami038
- Gray, J. (2010). *The Construction of English*. Palgrave Macmillan UK. https://doi.org/10.1057/9780230283084
- Gries, S. T. (2013). 50-something years of work on collocations: What is or should be next ... *International Journal of Corpus Linguistics*, *18*(1), 137–166. https://doi.org/10.1075/ijcl.18.1.09gri
