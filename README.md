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
    prop_extraction --in=INPUT_FILE --out=OUTPUT_FILE [--include-id]

Extract propositions from a given input file, output is produced in separate output file.
If both in and out paramaters are directories, the script will iterate over all *.txt files in the input directory and
output to *.prop files in output directory.

Options:
   --in=INPUT_FILE    The input file, each sentence in a separate line
   --out=OUTPUT_FILE  The output file, Each extraction in a tab separated line, each consisting of original sentence,
   predicate template, lemmatized predicate template,argument name, argument value, ...
```

## Output format

Each extraction is presented in a tab separated line, consisting of:
1. Original sentence
2. Predicate template
3. Lemmatized predicate
4. Template
5. Argument1 name
6. Argument1 value
7. ...

## Examples:
```bash
python ./prop_extraction.py --in=../examples/sentences.txt --out=../examples/sentences.prop
```



