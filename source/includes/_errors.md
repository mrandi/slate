# Errors

<aside class="notice">The Fullstop API uses the following error codes</aside>


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is bad
401 | Unauthorized -- Your token is not valid or wrong
403 | Forbidden -- The resource requested is hidden for administrators only
404 | Not Found -- The specified violation could not be found
405 | Method Not Allowed -- You tried to access a resource with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The resource requested has been removed from our servers
418 | I'm a teapot
429 | Too Many Requests -- You're requesting too many violations! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
