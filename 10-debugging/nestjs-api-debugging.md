# NestJS API Debugging - Reflection

## How can logging request payloads help with debugging?

Logging request payloads helps track what data is being sent to the server. If something goes wrong, you can check the logs to see if the request is missing information or has incorrect data. It’s useful for identifying issues like wrong request formats or missing parameters.

## What tools can you use to inspect API requests and responses?

You can use tools like Postman, Bruno, or curl to inspect API requests and responses. Postman and Bruno are great for manual testing with a GUI, while curl is quick and works directly from the terminal. All of these tools help you test the API, check headers, payloads, and responses.

## How would you debug an issue where an API returns the wrong status code?

To debug this, start by checking the controller or service handling the request. Look at the conditions where the status code is set. If it’s wrong, check if the logic is incorrect or if you’re using the wrong status code. Logs can also help verify the flow and spot where things go wrong.

## What are some security concerns when logging request data?

When logging request data, be careful with sensitive information like passwords, tokens, or personal data. Logging these can expose security risks. Always sanitize the logs to exclude sensitive data and avoid logging sensitive headers or body content.

![Image](https://github.com/user-attachments/assets/98d5f001-1a25-4b92-95bd-b496d197e63f)
