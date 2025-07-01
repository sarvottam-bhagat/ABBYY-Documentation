Python
Documentation for the Document AI Python SDK

​
SDK Installation
[!NOTE] Python version upgrade policy

Once a Python version reaches its official end of life date, a 3-month grace period is provided for users to upgrade. Following this grace period, the minimum python version supported in the SDK will be updated.

The SDK can be installed with either pip or poetry package managers.

​
PIP
PIP is the default package installer for Python, enabling easy installation and management of packages from PyPI via the command line.

```
pip install abbyy-document-ai
```

​
Poetry
Poetry is a modern tool that simplifies dependency management and package publishing by using a single pyproject.toml file to handle project metadata and dependencies.

```
poetry add abbyy-document-ai
```

​
Shell and script usage with uv
You can use this SDK in a Python shell with uv and the uvx command that comes with it like so:

```
uvx --from abbyy-document-ai python
```
It’s also possible to write a standalone Python script without needing to set up a whole project like so:

```
#!/usr/bin/env -S uv run --script
# /// script
# requires-python = ">=3.9"
# dependencies = [
#     "abbyy-document-ai",
# ]
# ///

from abbyy_document_ai import DocumentAi

sdk = DocumentAi(
    # SDK arguments
)

# Rest of script here...
```
Once that is saved to a file, you can run it with uv run script.py where script.py can be replaced with the actual file name.

​
IDE Support
​
PyCharm
Generally, the SDK will work well with most IDEs out of the box. However, when using PyCharm, you can enjoy much better integration with Pydantic by installing an additional plugin.

PyCharm Pydantic Plugin
​
SDK Example Usage
​
Example

# Synchronous Example
```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

        res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>")

        while res is not None:
                # Handle items

                res = res.next()
```
The same SDK client can also be used to make asychronous requests by importing asyncio.

# Asynchronous Example
```python
from abbyy_document_ai import DocumentAi
import asyncio
import os

async def main():

        async with DocumentAi(
                api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
        ) as document_ai:

                res = await document_ai.documents.list_async(cursor="<optional_pagination_cursor_goes_here>")

                while res is not None:
                        # Handle items

                        res = res.next()

asyncio.run(main())
```
​
Authentication
​
Per-Client Security Schemes
This SDK supports the following security scheme globally:

| Name           | Type | Scheme       | Environment Variable         |
|----------------|------|--------------|-----------------------------|
| api_key_auth   | http | HTTP Bearer  | DOCUMENTAI_API_KEY_AUTH     |

To authenticate with the API the api_key_auth parameter must be set when initializing the SDK client instance. For example:

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

        res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>")

        while res is not None:
                # Handle items

                res = res.next()
```

​
Available Resources and Operations
The available API operations and SDK implementation examples can be found within our API Reference documentation

​
Pagination
Some of the endpoints in this SDK support pagination. To use pagination, you make your SDK calls as usual, but the returned response object will have a Next method that can be called to pull down the next group of results. If the return value of Next is None, then there are no more pages to be fetched.

Here’s an example of one such pagination call:

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

        res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>")

        while res is not None:
                # Handle items

                res = res.next()
```

​
Retries
Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a RetryConfig object to the call:

```python
from abbyy_document_ai import DocumentAi
from abbyy_document_ai.utils import BackoffStrategy, RetryConfig
import os

with DocumentAi(
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

        res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>",
                RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False))

        while res is not None:
                # Handle items

                res = res.next()
```
If you’d like to override the default retry strategy for all operations that support retries, you can use the retry_config optional parameter when initializing the SDK:

```python
from abbyy_document_ai import DocumentAi
from abbyy_document_ai.utils import BackoffStrategy, RetryConfig
import os

with DocumentAi(
        retry_config=RetryConfig("backoff", BackoffStrategy(1, 50, 1.1, 100), False),
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

        res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>")

        while res is not None:
                # Handle items

                res = res.next()
```

​
Error Handling
Handling errors in this SDK should largely match your expectations. All operations return a response object or raise an exception.

By default, an API error will raise a models.APIError exception, which has the following properties:

| Property      | Type           | Description            |
|---------------|----------------|------------------------|
| .status_code  | int            | The HTTP status code   |
| .message      | str            | The error message      |
| .raw_response | httpx.Response | The raw HTTP response  |
| .body         | str            | The response content   |

When custom error responses are specified for an operation, the SDK may also raise their associated exceptions. You can refer to respective Errors tables in SDK docs for more details on possible exception types for each operation. For example, the list_async method may raise the following exceptions:

| Error Type                  | Status Code | Content Type         |
|-----------------------------|-------------|----------------------|
| models.BadRequestError      | 400         | application/json     |
| models.UnauthorizedError    | 401         | application/json     |
| models.TooManyRequestsError | 429         | application/json     |
| models.InternalServerError  | 500         | application/json     |
| models.APIError             | 4XX, 5XX    | */*                  |

​
Example

```python
from abbyy_document_ai import DocumentAi, models
import os

with DocumentAi(
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:
        res = None
        try:

                res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>")

                while res is not None:
                        # Handle items

                        res = res.next()

        except models.BadRequestError as e:
                # handle e.data: models.BadRequestErrorData
                raise(e)
        except models.UnauthorizedError as e:
                # handle e.data: models.UnauthorizedErrorData
                raise(e)
        except models.TooManyRequestsError as e:
                # handle e.data: models.TooManyRequestsErrorData
                raise(e)
        except models.InternalServerError as e:
                # handle e.data: models.InternalServerErrorData
                raise(e)
        except models.APIError as e:
                # handle exception
                raise(e)
```

​
Server Selection
​
Override Server URL Per-Client
The default server can be overridden globally by passing a URL to the server_url: str optional parameter when initializing the SDK client instance. For example:

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
        server_url="https://api.abbyy.com/document-ai",
        api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

        res = document_ai.documents.list(cursor="<optional_pagination_cursor_goes_here>")

        while res is not None:
                # Handle items

                res = res.next()
```

​
Custom HTTP Client
The Python SDK makes API calls using the httpx HTTP library. In order to provide a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration, you can initialize the SDK client with your own HTTP client instance. Depending on whether you are using the sync or async version of the SDK, you can pass an instance of HttpClient or AsyncHttpClient respectively, which are Protocol’s ensuring that the client has the necessary methods to make API calls. This allows you to wrap the client with your own custom logic, such as adding custom headers, logging, or error handling, or you can just pass an instance of httpx.Client or httpx.AsyncClient directly.

For example, you could specify a header for every request that this sdk makes as follows:

```python
from abbyy_document_ai import DocumentAi
import httpx

http_client = httpx.Client(headers={"x-custom-header": "someValue"})
s = DocumentAi(client=http_client)
```
or you could wrap the client with your own custom logic:

```python
from abbyy_document_ai import DocumentAi
from abbyy_document_ai.httpclient import AsyncHttpClient
import httpx

class CustomClient(AsyncHttpClient):
        client: AsyncHttpClient

        def __init__(self, client: AsyncHttpClient):
                self.client = client

        async def send(
                self,
                request: httpx.Request,
                *,
                stream: bool = False,
                auth: Union[
                        httpx._types.AuthTypes, httpx._client.UseClientDefault, None
                ] = httpx.USE_CLIENT_DEFAULT,
                follow_redirects: Union[
                        bool, httpx._client.UseClientDefault
                ] = httpx.USE_CLIENT_DEFAULT,
        ) -> httpx.Response:
                request.headers["Client-Level-Header"] = "added by client"

                return await self.client.send(
                        request, stream=stream, auth=auth, follow_redirects=follow_redirects
                )

        def build_request(
                self,
                method: str,
                url: httpx._types.URLTypes,
                *,
                content: Optional[httpx._types.RequestContent] = None,
                data: Optional[httpx._types.RequestData] = None,
                files: Optional[httpx._types.RequestFiles] = None,
                json: Optional[Any] = None,
                params: Optional[httpx._types.QueryParamTypes] = None,
                headers: Optional[httpx._types.HeaderTypes] = None,
                cookies: Optional[httpx._types.CookieTypes] = None,
                timeout: Union[
                        httpx._types.TimeoutTypes, httpx._client.UseClientDefault
                ] = httpx.USE_CLIENT_DEFAULT,
                extensions: Optional[httpx._types.RequestExtensions] = None,
        ) -> httpx.Request:
                return self.client.build_request(
                        method,
                        url,
                        content=content,
                        data=data,
                        files=files,
                        json=json,
                        params=params,
                        headers=headers,
                        cookies=cookies,
                        timeout=timeout,
                        extensions=extensions,
                )

s = DocumentAi(async_client=CustomClient(httpx.AsyncClient()))
```

​
Resource Management
The DocumentAi class implements the context manager protocol and registers a finalizer function to close the underlying sync and async HTTPX clients it uses under the hood. This will close HTTP connections, release memory and free up other resources held by the SDK. In short-lived Python programs and notebooks that make a few SDK method calls, resource management may not be a concern. However, in longer-lived programs, it is beneficial to create a single SDK instance via a context manager and reuse it across the application.

```python
from abbyy_document_ai import DocumentAi
import os
def main():

        with DocumentAi(
                api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
        ) as document_ai:
                # Rest of application here...


# Or when using async:
async def amain():

        async with DocumentAi(
                api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
        ) as document_ai:
                # Rest of application here...
```

​
Debugging
You can setup your SDK to emit debug logs for SDK requests and responses.

You can pass your own logger class directly into your SDK.

```python
from abbyy_document_ai import DocumentAi
import logging

logging.basicConfig(level=logging.DEBUG)
s = DocumentAi(debug_logger=logging.getLogger("abbyy_document_ai"))
```
You can also enable a default debug logger by setting an environment variable DOCUMENTAI_DEBUG to true.
