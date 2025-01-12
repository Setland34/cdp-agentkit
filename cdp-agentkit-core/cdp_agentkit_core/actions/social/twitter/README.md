# Twitter Account Details Action

This directory contains the `account_details` action for retrieving account details of the authenticated Twitter (X) user.

## Overview

The `account_details` action retrieves the account details of the authenticated Twitter (X) user. It returns a JSON payload containing the user's account information, such as the user ID, name, username, and profile URL.

## Usage

To use the `account_details` action, follow these steps:

1. Ensure you have the necessary dependencies installed. You can install them using `pip`:

   ```bash
   pip install tweepy pydantic
   ```

2. Import the required modules and create a `tweepy.Client` instance with your Twitter API credentials:

   ```python
   import tweepy
   from cdp_agentkit_core.actions.social.twitter.account_details import account_details

   client = tweepy.Client(
       consumer_key="YOUR_CONSUMER_KEY",
       consumer_secret="YOUR_CONSUMER_SECRET",
       access_token="YOUR_ACCESS_TOKEN",
       access_token_secret="YOUR_ACCESS_TOKEN_SECRET",
       bearer_token="YOUR_BEARER_TOKEN",
       return_type=dict,
   )
   ```

3. Call the `account_details` function with the `tweepy.Client` instance:

   ```python
   response = account_details(client)
   print(response)
   ```

## Examples

### Example 1: Successful Retrieval

```python
import tweepy
from cdp_agentkit_core.actions.social.twitter.account_details import account_details

client = tweepy.Client(
    consumer_key="YOUR_CONSUMER_KEY",
    consumer_secret="YOUR_CONSUMER_SECRET",
    access_token="YOUR_ACCESS_TOKEN",
    access_token_secret="YOUR_ACCESS_TOKEN_SECRET",
    bearer_token="YOUR_BEARER_TOKEN",
    return_type=dict,
)

response = account_details(client)
print(response)
```

Expected output:

```
Successfully retrieved authenticated user account details:
{"data": {"id": "1853889445319331840", "name": "CDP AgentKit", "username": "CDPAgentKit", "url": "https://x.com/CDPAgentKit"}}
```

### Example 2: Failure due to API Error

```python
import tweepy
from cdp_agentkit_core.actions.social.twitter.account_details import account_details

client = tweepy.Client(
    consumer_key="YOUR_CONSUMER_KEY",
    consumer_secret="YOUR_CONSUMER_SECRET",
    access_token="YOUR_ACCESS_TOKEN",
    access_token_secret="YOUR_ACCESS_TOKEN_SECRET",
    bearer_token="YOUR_BEARER_TOKEN",
    return_type=dict,
)

# Simulate an API error by providing invalid credentials
client = tweepy.Client(
    consumer_key="INVALID_CONSUMER_KEY",
    consumer_secret="INVALID_CONSUMER_SECRET",
    access_token="INVALID_ACCESS_TOKEN",
    access_token_secret="INVALID_ACCESS_TOKEN_SECRET",
    bearer_token="INVALID_BEARER_TOKEN",
    return_type=dict,
)

response = account_details(client)
print(response)
```

Expected output:

```
Error retrieving authenticated user account details:
TweepyException: Invalid or expired token.
```
