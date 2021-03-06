# censei-backend

> Flask Server to process text and return censored versions with emojis

## Getting Started

```sh

# Setting up virtual environment for local development
virtualenv -p python3 venv

# Activate the virtual environment
source venv/bin/activate

# Install dependencies
pip3 install -r requirements.txt

# Set flask environment variables
export FLASK_APP=main.py
export FLASK_ENV=development
export FLASK_DEBUG=1 # optional

# Run flask server locally
flask run

```

## Endpoints 

- ### `POST /censorText`
    - Request Parameters
        - text : The text to be censored
        - censor_list: list of words to be added to the list of bad words (MUST all be lowercase)
        - white_list: list of bad words to be allowed for use (MUST all be lowercase)
    - Sample Request
        ```HTTP
        POST /censorText HTTP/1.1
        Host: localhost:5000
        Content-Type: application/json

        {
            "text": "You suck so much stupid!",
            "censor_list": ["much"],
            "white_list": ["suck"]
        }
        ```
    - Response
        - censored_text: The censored versions of the text corpus sent in the request
    - Sample Response
        ```json
        {
            "censored_text": " You suck so 🌽🌽🌽🌽 🍵🍵🍵🍵!"
        }
        ```
