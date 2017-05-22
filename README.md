<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
# Templated Open Information Extraction

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running](#running)
- [Output format](#output-format)
- [Examples:](#examples)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

Extracts templated Open Information Extraction: allowing for diverse, non-contiguous, multi-word predicates, while keeping argument short and useful for downstream applications.

For example, given the sentence:

_Under the agreement with the House and Senate leaders , the minimum wage would rise from the current $ 3.35 an hour to $ 4.25 an hour._

One of the extractions is:

* **Under** {A0} {A1} **would *rise* from** {A2} **to** {A3}

        A0:	the agreement
        A1:	the minimum wage
        A2:	$ 3.35 an hour
        A3:	$ 4.25 an hour

Note that that the head of the predicate (_rise_) is also identified.


## Prerequisites
1. python 2.7
2. pip 9.x

## Installation
1. Install required packages:<br>
```bash
pip install -r ./requirements.txt
```
2. Download spaCy English models:<br>
```bash
python -m spacy download en
```

## Running 
```
Usage:
    prop_extraction --in=INPUT_FILE --out=OUTPUT_FILE [--id]

Extract propositions from a given input file, output is produced in separate output file.
If both in and out paramaters are directories, the script will iterate over all *.txt files in the input directory and
output to *.prop files in output directory.

Options:
   --in=INPUT_FILE      The input file, each sentence in a separate line
   --out=OUTPUT_FILE    The output file, Each extraction in a tab separated line, each consisting of original sentence,
   predicate template, lemmatized predicate template,argument name, argument value, ...
   --id                 Indicate that the input file is composed of sentence-id \t sentence, and copy this id in the output.
```

## Output format

Each extraction is presented in a tab separated line, consisting of:
1. Original sentence <br>
Words are separated by a single space, chunks by double spaces
2. Index of the main predicate's chunk
3. Predicate template
4. Lemmatized predicate
6. Argument1 name
7. Argument1 value
8. ...

## Examples:
```bash
python ./prop_extraction.py --in=../examples/sentences.txt --out=../examples/sentences.prop
```
