---
layout: base
title:  'Telugu UD'
udver: '2'
---

# UD for Telugu

## Tokenization and Word Segmentation

* In general, words are delimited by whitespace characters. Description of exceptions follows.
* According to typographical rules, many punctuation marks are attached to a neighboring word. These are normally tokenized as separate tokens (words);
  exceptions include abbreviations (the abbreviation-marking period is part of the main token) and hyphenated compounds (the hyphen does not split
  the token).
* There are no multiword tokens.

## Morphology

### Tags

* The Telugu treebank currently uses only 14 of the 17 universal POS categories, including particles ([PART]()).
  There are no auxiliary verbs, symbols and unknown words.
* The pronoun ([PRON]()) vs. determiner ([DET]()) distinction is based on word lists because the traditional grammar does not define determiners.

### Features

Telugu has a very rich morphology, being the highest among all literary Dravidian languages ([source](https://en.wikipedia.org/wiki/Telugu_grammar#Nouns)). Therefore, I have tried my best to account for almost all of them.

- **Converb** is used heavily in telugu.
	- [Explanation](https://en.wikipedia.org/wiki/Telugu_grammar#Converbs)
	- Past:  **-i** suffix
	- Present: **-tu** suffix

#### Cases

Cases are marked on nouns with the following suffixes:

- **-kosam**: Benefactive
- **-ni/-nu** : Accusative
- -ki/-ku: Dative
- -lo/lopala: Locative
- -loki/-lopalaki: illative Case
- -lonchi, -nunci: Ablative Case
- -ki : Allative (towards something)
- -valla : Causative
- -nunci : Ablative
- -kanna / -kante : Comparative
- -to: Instrumental, or Sociative (Associative/Comitative)
- Equative **-లాగా/ -లా/ -నట్టు**
	- not a standard case, but i am marking it as one here as it fits the function.
	- verb only suffix -నట్టు means "as if", "in the manner of", which is pretty much the same as "being like (something)"
	- example sentence: p2__11, p2__16
		- వెళ్ళి**నట్లు**లేదే

Note: Telugu prefers using the dative case much more than nominative. Therefore, the existing UD documentation marks the subject of such sentences as `nsubj:nc` (non-canonical), but I have opted to leave this out and mark it simply as `nsubj`

#### Participles

- "egirina" -na (Past) perfective
- "egiree" -e (non-past) imperfective

#### Mood

- Interrogative: Int -ఆ? (-ā)
- Admirative: doubting/guessing suffix -ఓ (-o)
	- e.g. వరికి తెలుసు**నో** "who knows?"
- suffix **-e** `PronType=Emp` Emphatic Determiner (He himself did it) అనుకోవలసిందే
- suffix **-ali** `Mood=Nec` Necessitative (MUST) అనుకోవలీ 

#### Genders 

Literary/formal telugu has three genders: male humans, female humans, and everything else.

### Other Features

- Demonstrative **Pronouns** can have two crucial features:
	- **Deixis: relative location from speaker**
		- Proximal: prefix **i-**
		- Remote/Distal: prefix **a-**
	- Formality: Polite, Informal
	- **తన** could mean his or her

- **Particles:**
	- **అని** (ani):
		- connecting particle:
			- marker of quotation/indirect report ("that")
			- to subordinate a claud expressing thinking or knowledge, opinion
			- "that's why"
	- అంటే (ante)
		- Contraction of అనినట్టయితే (if, / say,)

## Syntax

### Core Arguments, Oblique Arguments and Adjuncts

* Nominal subject ([nsubj]()) is a bare noun phrase (without adposition) in the nominative case.
  * A subordinate clause may serve as the subject and is labeled [csubj]().
* Direct object ([obj]()) is a bare noun phrase in accusative.
  * Accusative objects of some verbs alternate with finite clausal complements, which are labeled [ccomp]().

### Non-verbal Clauses

* Non-verbal clauses do not use a copula.

### Relations Overview

* The following relation subtypes are used in Telugu:
  * [nsubj:nc]() for non-canonical subject, such as a nominal in the dative case
  * [acl:relcl]() for relative clauses
  * [advcl:cond]() for conditional adverbial clauses
  * [compound:lvc]() for light verb constructions
  * [compound:svc]() for serial verb constructions
  * [compound:redup]() for reduplications
  * [nmod:poss]() for possessive/genitive modifiers
  * [nmod:tmod]() for temporal modifiers (a nominal modifies another nominal)
  * [obl:tmod]() for temporal modifiers (a nominal modifies a clause)
  * [obl:cau]() for oblique participants in the causative case (the causees)
  * [obl:cmp]() for standards of comparison
* The following relation types are not used in Telugu at all:
  [expl](), [aux](), [cop](), [fixed]()

## Treebanks

There is 2 Telugu UD treebanks:

  * [Telugu-MTG](../treebanks/te_mtg/index.html)
  * Telugu-UD-Treebank (Harsha's): https://github.com/harshamarsha/Telugu-Treebank
