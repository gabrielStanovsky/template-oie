# template-oie
Extract templated Open Information Extraction

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
