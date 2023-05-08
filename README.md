# Blog repository: Turn your code into a serverless API

The repository contains all the workflows and Python code which was used in the blog article:

https://blog.direktiv.io/turn-your-code-into-a-serverless-api-748490acd470

Blog repository: Turn your code into a serverless API

## Workflow overview

This is a simple workflow example to show how to run Python code from a GitHub repository as a serverless function in Direktiv. The workflow will run Python code which will connect to the Twitter API and retrieve the last 10 Tweets based ona keyword search. Once the Tweets have been collected, we will run this thourgh a secondary Python script to do langugage analysis on the Tweets using the Google Language detection API. The following notes regarding the workflow:

 - The Python code we run is `tweet-lang.yaml.get-tweets.py` and `tweet-lang.yaml.get-lang.py`. Note that the ACTUAL name of the scripts are `get-tweets.py` and `get-lang.py`, however, prepending the name of the orchestration policy (`tweet-lang.yaml`) forces Direktiv to create these Ptyhon scripts as variables which can be used in the workflow. This happens automatically when the GitHub repository is synchronised with the Direktiv namespace.
 - The `tweet-lang.yaml.requirements.txt` contains some Phthon module to import. Again, the import file is called `requirements.txt` and Direktiv will create this as a variable during the GitHub syncrhnonisation.
 - A Twitter bearer token needs to be created to access the Twitter API.
 - A google key is needed to send the request to the Google Language API. The GCP_KEY secret is created in the Direktiv namespace and looks something like this:

## Variables

 - get-tweets.py: automatically created as a worklfow variable in Direktiv during GitHub sync, contains the Python code for retrieving the Tweets
 - get-lang.py: automatically created as a worklfow variable in Direktiv during GitHub sync, contains the Python code for doing language analysis using Google Language API
 - requirements.txt: Python library requirements

## Secrets

 - GCP_KEY: Google Cloud credentials, needs access to the Google Language detection API

## Namespace Services

 - None

## Input examples

```json
{
    "bearer_token": "AAAAAAAAA...........jhYlNYLrhlZ6F",
    "twitter_searchstring": "direktiv",
    "max_search_returns": 10
}
```

## External links:

 - Blog article: https://blog.direktiv.io/turn-your-code-into-a-serverless-api-748490acd470ß