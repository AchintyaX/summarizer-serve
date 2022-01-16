# Summarizer Serve 

An attempt to learn MLFlow, by inferencing T5 transformer architecture and using it for text summarization.
Here we are running the experiment using mlflow and then using mlflow for serving the model. 

## set up
1. clone the repo
2. run `poetry install`
3. run `poetry run python text_summarizer.py `

## ML Flow interface 

ML Flow lets you track your different experiments along with serving models as APIs.
you can check it out - 
1. run `mlflow ui`
2. open `localhost:5000` and checkout the run, and you can copy the `run_id`

## Serving the model 
You can serve any of your runs using MLFlow using the following command <br>-
```shell

mlflow models serve -m runs:/<RUN_ID>/model --port=1234 --no-conda

```
and you can make curl requests to test the model like <br>:

```shell
curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["text"],"data":[["H.P.Lovecraft wrote his best books in Masachusettes."]]}' localhost:1234/invocations

```
