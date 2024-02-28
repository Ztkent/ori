# Ori
Manage notifications and reminders with [BlinkStick](https://www.blinkstick.com).  

## Setup
To connect, you'll need to authenticate with each service you want to use:  
#### 
- Microsoft
    - Azure AD requires a connection to the [Microsoft Graph API](https://developer.microsoft.com/en-us/graph).
        - This is done with the wrapper [MSGraph-Python](https://github.com/Ztkent/msgraph-python).
        - Follow the instructions [here](https://github.com/Ztkent/msgraph-python) to register a new app with Azure AD.
- Google
    - Google requires a connection to the [Google API](https://developers.google.com/gmail/api).
        - This is done with the SDK [google-api-python-client](https://github.com/googleapis/google-api-python-client)
        - You will need to generate a `credentials.json` file from the [Google Developer Console](https://console.developers.google.com/).
            - "APIs & Services" > "Credentials"
            - "Create credentials" > "OAuth client ID"
            - "Desktop app" > "Create"
- BlinkStick
    - On Mac, it might require 'sudo' to detect connected BlinkSticks.

## Supported Services
- Microsoft: 
    - Teams
    - Outlook
    - Calendar
- Google:
    - Gmail
    - Calendar

## Usage

#### Setup your environment
```bash
pip install -r requirements.txt
# Microsoft Required ENVs
export CLIENT_ID=YOUR_CLIENT_ID
export TENANT_ID=YOUR_TENANT_ID
# Google Required ENVs
export GCREDS_PATH=YOUR_PATH_TO_CREDENTIALS_JSON
```
#### Run the app
```bash
# Connect to all services
python3 -m ori
# Connect to specific services
python3 -m ori -service "google" -scopes "gmail"
python3 -m ori -service "google,microsoft" -scopes "gmail,calendar,teams-chat,teams-channel"
```