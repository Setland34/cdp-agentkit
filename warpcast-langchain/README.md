# Warpcast Langchain Integration

This package provides integration between Warpcast and Langchain, enabling agentic workflows to interact with Warpcast.

## Installation

To install the package, use the following command:

```bash
pip install warpcast-langchain
```

## Usage

### Setting Up Environment Variables

To use the Warpcast API, you need to set up the following environment variables:

- `WARPCAST_API_KEY`: Your Warpcast API key.

You can create a `.env` file in your project directory and add the environment variables there:

```plaintext
WARPCAST_API_KEY=your_warpcast_api_key
```

### Example Usage

Here's an example of how to use the Warpcast Langchain integration:

```python
import os
from warpcast_langchain.warpcast_api_wrapper import WarpcastApiWrapper
from warpcast_langchain.warpcast_toolkit import WarpcastToolkit

# Load environment variables from .env file
from dotenv import load_dotenv
load_dotenv()

# Initialize Warpcast API Wrapper
api_key = os.getenv("WARPCAST_API_KEY")
warpcast_api = WarpcastApiWrapper(api_key)

# Create Warpcast Toolkit
warpcast_toolkit = WarpcastToolkit.from_warpcast_api_wrapper(warpcast_api)

# Get tools from the toolkit
tools = warpcast_toolkit.get_tools()

# Example: Post a cast
cast_tool = next(tool for tool in tools if tool.name == "cast")
result = cast_tool.func({"content": "Hello, Warpcast!"})
print(result)

# Example: Reply to a cast
reply_tool = next(tool for tool in tools if tool.name == "reply")
result = reply_tool.func({"cast_id": "12345", "content": "This is a reply"})
print(result)

# Example: Get user details
user_details_tool = next(tool for tool in tools if tool.name == "get_user_details")
result = user_details_tool.func({"user_id": "user123"})
print(result)

# Example: Get user's casts
user_casts_tool = next(tool for tool in tools if tool.name == "get_user_casts")
result = user_casts_tool.func({"user_id": "user123"})
print(result)
```

## Contributing

Contributions are welcome! Please refer to the [CONTRIBUTING.md](../CONTRIBUTING.md) file for guidelines on how to contribute to this project.

## License

This project is licensed under the Apache 2.0 License. See the [LICENSE](../LICENSE.md) file for more details.
