# Twitter Account Details

This directory contains the `account_details` function, which retrieves the authenticated Twitter (X) user account details.

## Overview

The `account_details` function is a tool that returns account details for the currently authenticated Twitter (X) user context. It uses the `tweepy` library to interact with the Twitter API.

## Usage

### Setup

1. Install the required dependencies:
    ```bash
    pip install tweepy
    ```

2. Obtain Twitter API credentials by creating a Twitter Developer account and creating an app. You will need the following credentials:
    - API Key
    - API Secret Key
    - Access Token
    - Access Token Secret
    - Bearer Token

3. Set up the credentials as environment variables:
    ```bash
    export TWITTER_API_KEY="your_api_key"
    export TWITTER_API_SECRET="your_api_secret"
    export TWITTER_ACCESS_TOKEN="your_access_token"
    export TWITTER_ACCESS_TOKEN_SECRET="your_access_token_secret"
    export TWITTER_BEARER_TOKEN="your_bearer_token"
    ```

### Functionality

The `account_details` function retrieves the authenticated Twitter (X) user account details and returns a message containing the account details in JSON format.

### Example

Here is an example of how to use the `account_details` function:

```python
import tweepy
from cdp_agentkit_core.actions.social.twitter.account_details import account_details

# Set up the Twitter client
client = tweepy.Client(
    consumer_key="your_api_key",
    consumer_secret="your_api_secret",
    access_token="your_access_token",
    access_token_secret="your_access_token_secret",
    bearer_token="your_bearer_token",
    return_type=dict,
)

# Get account details
response = account_details(client)
print(response)
```

### Expected Input and Output

#### Input

- `client` (tweepy.Client): The Twitter (X) client used to authenticate with.

#### Output

- A message containing account details for the authenticated user context in JSON format.

#### Example Output

```json
{
    "data": {
        "id": "1853889445319331840",
        "name": "CDP AgentKit",
        "username": "CDPAgentKit",
        "url": "https://x.com/CDPAgentKit"
    }
}
```
