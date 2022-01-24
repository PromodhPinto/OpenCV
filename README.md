# SYNTHETIC DATA GENERATION

Synthetic data generation is the process of generating images and corresponding ground truths with different font family, font colour, font size, background color, space between words and many more.

## Prerequisites
- python 3.7
- ubuntu 16.04

You need to install some libraries. I have specified the names and versions of python libraries in requirements.txt
```bash
pip install -r requirements.txt
```

# Configuration

We have here config settings that may help generate synthetic data for each languages:

* lang_code : language code
* lang      : language
* num_lines : the number of lines to generate dataset from raw corpus
* bgs_path  : background images path
* real_imgs : real data path
* real_txt  : real data ground truth path
* font_ path: font files path
* noices    : noise filters to be applied
* font_colour: font color codes
* ...

# Directories

The folder structure consists of the following files/directories
* the `synthetic_data_generator` directory holds all services, each with their files
* the `BG_PAPER` directory holds useful background images, needed to genereate the synthetic images
* `real-data` directory holds real world data that is added along with the synthetic data
* `line_txt` directory holds list of files containing text corpus for each language
* `font_files` directory holds list of directories containing fonts for each language
* `output` directory holds the generated data

## APIs and Documentation
After successful installation of prerequisites, you will have to run run.py

```bash
python app.py
```
This service is used to tokenise sentences from a paragraph. After initiating this service,
hit: ```http://0.0.0.0:5001/api/v0/tokenisation```
### Request Format
```json
POST/tokenisation
Accept list of files

{
        "files": [
            {
                "locale": "en",
                "path": "text file which contains paragraphs",
                "type": "txt"
            },
            {....},
            {....}
        ]}
```
### Response
```
POST/tokenisation
Returns txt file which have tokenised sentences

{
    "files": [
        {
            "inputFile": "input txt file",
            "outputFile": "text file conaining tokenised sentences",
            "outputLocale": "en",
            "outputType": "txt"
        },
        {....},
        {....}
    ],
    "state": "SENTENCE-TOKENISED",
    "status": "SUCCESS"
}
```
For more information about api documentation, please check @ ```https://github.com/project-anuvaad/anuvaad/blob/dev-sentence/anuvaad-etl/anuvaad-extractor/sentence/docs/sentence-api-contarct.yml```
## License
[MIT](https://choosealicense.com/licenses/mit/)
