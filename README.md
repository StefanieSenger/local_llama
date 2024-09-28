### local llama

Made at Feminist AI LAN Party, Berlin September 2024.

Run a llama model locally and make annotations as a basis for fine-tuning the model.
</br>
</br>

My notes on all the steps:

1. download llamafile from https://github.com/Mozilla-Ocho/llamafile?tab=readme-ov-file and follow instructions to make it executable and run it
	- will start local llama with interactive prompting session on local host 8080
	- now we can play with prompts and possibly try to attack it to check for biases and privacy (whatever we do here remains private)

2. make new repo and environment

    `pip install prodigy --extra-index-url PRODIGY_KEY`

3. have a .jsonl file with data or for testing purpose download the file provided at https://prodi.gy/docs

4. start prodigy annotation tool:

	`PRODIGY_PORT=8081 prodigy ner.manual ner_example_data blank:en ./example_data.jsonl --label PERSON,ORG,PRODUCT,LOCATION`

    - will start prodigy on local host 8081
    - we can annotate on more interesting items than on `PERSON,ORG,PRODUCT,LOCATION`

5. annotate; check the docs on how to do that: https://prodi.gy/docs

6. save annotations with disc symbol on local host

7. export the annotated data

	`prodigy db-out ner_example_data > ./annotations.jsonl`

9. retrain spacy model and export to `output_dir`

    `prodigy train ./output_dir --ner ner_example_data`
