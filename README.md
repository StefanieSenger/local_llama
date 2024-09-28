### local llama

Experiment to run a llama model locally and make annotations as a basis for fine-tuning the model.
Made at Feminist AI LAN Party, Berlin September 2024.

1. download llamafile from https://github.com/Mozilla-Ocho/llamafile?tab=readme-ov-file and follow instructions to make it executable and run
	- will start local llama with interactive prompting session on local host 8080
    - now we can play with prompts and possibly try to break it and whatever we do there remains private

2. make new repo and environment
    `pip install prodigy --extra-index-url PRODIGY_KEY`

3. start prodigy annotation tool: 
`PRODIGY_PORT=8081 prodigy ner.manual ner_example_data blank:en ./example_data.jsonl --label PERSON,ORG,PRODUCT,LOCATION`
    - will start prodigy on local host 8081

4. check the docs on how to annotate: https://prodi.gy/docs

	`prodigy db-out ner_example_data > ./annotations.jsonl`

5. save annotations with disc symbol on local host

6. retrain spacy model and export to `output_dir`
    `prodigy train ./output_dir --ner ner_example_data`