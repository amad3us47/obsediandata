

## API RECON 

API requests about specific resource on its server. For example, consider the following GET requests:
`GET /api/books HTTP/1.1 
`Host: example.com`
The API endpoint for this requests is /api/books.
Once you have identified the endpoints, you need to determine how to interact with them. This enables you to construct valid HTTP requests to test the API. For example, you should find out information about the following:

- The input data the API processes, including both <span style="color:rgb(192, 0, 0)">compulsory and optional parameters.</span>
- The <span style="color:rgb(192, 0, 0)">types of requests the API accepts</span>, including supported HTTP methods and media formats.
- <span style="color:rgb(192, 0, 0)">Rate limits</span> and <span style="color:rgb(192, 0, 0)">authentication</span> mechanisms.

<span style="color:rgb(192, 0, 0)">API documentation</span> is often publicly available, particularly if the API is intended for use by external developers. If this is the case, always start your recon by reviewing the documentation. It's written in structured formats like JSON or XML.


## Discovering API documentation

Find the API documentation endpoints by crawling the website.

 `/api`
 `/swagger/index.html`
`/openapi.json`
`/api/swagger/v1`
`/api/swagger`
`/api`

<span style="color:rgb(192, 0, 0)">Lab Solution:</span> 
visit /api found using ffuf using api docs wordlist.
You will get some /OPTIONS there like 
GET    /api/user/{username : string}
DELETE  /api/user/{username : string}
PATCH /api/user/{username : string}

Now to delete the user carlos 
Visit /api/user/carlos  but with DELETE not GET
It will delete the user carlos


## IDENTIFYING API ENDPOINTS

You can also gather a lot of information by browsing applications that use the API. This is often worth doing even if you have access to API documentation, as sometimes documentation may be inaccurate or out of date. While browsing the application, look for patterns that suggest API endpoints in the URL structure, such as `/api/`.


## INTERACTING WITH API ENDPOINTS

Once you've identified API endpoints, interact with them using Burp Repeater and Burp Intruder. This enables you to observe the API's behavior and discover additional attack surface. For example, you could investigate how the API responds to changing the HTTP method and media type.
As you interact with the API endpoints, review error messages and other responses closely. Sometimes these include information that you can use to construct a valid HTTP request.\


## IDENTIFYING SUPPORTED HTTP METHODS

- GET - Retrieves data from a resource.
- PATCH - Applies partial changes to a resource.
- OPTIONS - Retrieves information on the types of request methods that can be used on a resource.
- An API endpoint may support different HTTP methods. It's therefore important to test all potential methods when you're investigating API endpoints. This may enable you to identify additional endpoint functionality, opening up more attack surface.

For example, the endpoint `/api/tasks` may support the following methods:

- `GET /api/tasks` - Retrieves a list of tasks.
- `POST /api/tasks` - Creates a new task.
- `DELETE /api/tasks/1` - Deletes a task.


## IDENTIFYING SUPPORTED CONTENT TYPES

API endpoints often expect data in a specific format. They may therefore behave differently depending on the content type of the data provided in a request. Changing the content type may enable you to:

- Trigger errors that disclose useful information.
- Bypass flawed defenses.
- Take advantage of differences in processing logic. For example, an API may be secure when handling JSON data but susceptible to injection attacks when dealing with XML.

To change the content type, modify the `Content-Type` header, then reformat the request body accordingly. You can use the Content type converter BApp to automatically convert data submitted within requests between XML and JSON.


## Finding and exploiting an unused API endpoint

<span style="color:rgb(255, 0, 0)">Lab solution :</span>
Login in the the given username and password
Visit the the leather jacket page
/product?productId=1

You will find /api/products/1/price which give the price of the jacket
You will find something like Content-type: application/json when GET
change the mode to PATCH
and add 
Content-type: application/json
{
}

It will give error of price not given 
so the fill 
{
 "price":0
}
This will make the value of jacket to $0.0

## Using intruder to find hidden endpoints

Once you have identified some initial API endpoints, you can use Intruder to uncover hidden endpoints. For example, consider a scenario where you have identified the following API endpoint for updating user information:

`PUT /api/user/update`

To identify hidden endpoints, you could use Burp Intruder to find other resources with the same structure. For example, you could add a payload to the `/update` position of the path with a list of other common functions, such as `delete` and `add`.

When looking for hidden endpoints, use wordlists based on common API naming conventions and industry terms. Make sure you also include terms that are relevant to the application, based on your initial recon.

## Finding hidden parameters

When you're doing API recon, you may find undocumented parameters that the API supports. You can attempt to use these to change the application's behavior. Burp includes numerous tools that can help you identify hidden parameters:

- Burp Intruder enables you to automatically discover hidden parameters, using a wordlist of common parameter names to replace existing parameters or add new parameters. Make sure you also include names that are relevant to the application, based on your initial recon.
- The Param miner BApp enables you to automatically guess up to 65,536 param names per request. Param miner automatically guesses names that are relevant to the application, based on information taken from the scope.
- The Content discovery tool enables you to discover content that isn't linked from visible content that you can browse to, including parameters.

## Mass assignment vulnerabilities

Mass assignment (also known as auto-binding) can inadvertently create hidden parameters. It occurs when software frameworks automatically bind request parameters to fields on an internal object. Mass assignment may therefore result in the application supporting parameters that were never intended to be processed by the developer.

## Identifying hidden parameters

Since mass assignment creates parameters from object fields, you can often identify these hidden parameters by manually examining objects returned by the API.

For example, consider a `PATCH /api/users/` request, which enables users to update their username and email, and includes the following JSON:

`{ 
`"username": "wiener",
`"email": "wiener@example.com",
`}`

A concurrent `GET /api/users/123` request returns the following JSON:

`{ 
`"id": 123, 
`"name": "John Doe", 
`"email": "john@example.com", 
`"isAdmin": "false" 
`}`

This may indicate that the hidden `id` and `isAdmin` parameters are bound to the internal user object, alongside the updated username and email parameters.

## Testing mass assignment vulnerabilities


To test whether you can modify the enumerated `isAdmin` parameter value, add it to the `PATCH` request:

`{ 
`"username": "wiener", 
`"email": "wiener@example.com", 
`"isAdmin": false, 
`}`

In addition, send a `PATCH` request with an invalid `isAdmin` parameter value:

`{ 
"username": "wiener",
`"email": "wiener@example.com", 
`"isAdmin": "foo", 
`}`

If the application behaves differently, this may suggest that the invalid value impacts the query logic, but the valid value doesn't. This may indicate that the parameter can be successfully updated by the user.

You can then send a `PATCH` request with the `isAdmin` parameter value set to `true`, to try and exploit the vulnerability:

`{ 
`"username": "wiener", 
`"email": "wiener@example.com", 
`"isAdmin": true, 
`}`

If the `isAdmin` value in the request is bound to the user object without adequate validation and sanitization, the user `wiener` may be incorrectly granted admin privileges. To determine whether this is the case, browse the application as `wiener` to see whether you can access admin functionality.

## Lab: Exploiting a mass assignment vulnerability

<span style="color:rgb(255, 0, 0)">Lab Solution :</span>
GET  /api/checkout HTTP/2
to 
POST /api/checkout HTTP/2
Add this on post request 
Content-Type: application/json; charset=utf-8

Get this from GET  /api/checkout HTTP/2 response 
{"chosen_products":[{"product_id":"1","name":"Lightweight \"l33t\" Leather Jacket","quantity":1,"item_price":1337}]}

and past it into 
POST /api/checkout HTTP/2
Modifying "item_price":1337

## Preventing vulnerabilities in APIs

When designing APIs, make sure that security is a consideration from the beginning. In particular, make sure that you:

- Secure your documentation if you don't intend your API to be publicly accessible.
- Ensure your documentation is kept up to date so that legitimate testers have full visibility of the API's attack surface.
- Apply an allowlist of permitted HTTP methods.
- Validate that the content type is expected for each request or response.
- Use generic error messages to avoid giving away information that may be useful for an attacker.
- Use protective measures on all versions of your API, not just the current production version.

To prevent mass assignment vulnerabilities, allowlist the properties that can be updated by the user, and blocklist sensitive properties that shouldn't be updated by the user.

## Server-side parameter pollution

Some systems contain internal APIs that aren't directly accessible from the internet. Server-side parameter pollution occurs when a website embeds user input in a server-side request to an internal API without adequate encoding. This means that an attacker may be able to manipulate or inject parameters, which may enable them to, for example:

- Override existing parameters.
- Modify the application behavior.
- Access unauthorized data.

You can test any user input for any kind of parameter pollution. For example, query parameters, form fields, headers, and URL path parameters may all be vulnerable.

## Testing for server-side parameter pollution in the query string

To test for server-side parameter pollution in the query string, place query syntax characters like `#`, `&`, and `=` in your input and observe how the application responds.

Consider a vulnerable application that enables you to search for other users based on their username. When you search for a user, your browser makes the following request:

`GET /userSearch?name=peter&back=/home`

To retrieve user information, the server queries an internal API with the following request:

`GET /users/search?name=peter&publicProfile=true`

## Truncating query strings

You can use a URL-encoded `#` character to attempt to truncate the server-side request. To help you interpret the response, you could also add a string after the `#` character.
For example, you could modify the query string to the following:

`GET /userSearch?name=peter%23foo&back=/home`

The front-end will try to access the following URL:

`GET /users/search?name=peter#foo&publicProfile=true`

Review the response for clues about whether the query has been truncated. For example, if the response returns the user `peter`, the server-side query may have been truncated. If an `Invalid name` error message is returned, the application may have treated `foo` as part of the username. This suggests that the server-side request may not have been truncated.

If you're able to truncate the server-side request, this removes the requirement for the `publicProfile` field to be set to true. You may be able to exploit this to return non-public user profiles.

## Injecting invalid parameters

You can use an URL-encoded `&` character to attempt to add a second parameter to the server-side request.

For example, you could modify the query string to the following:

`GET /userSearch?name=peter%26foo=xyz&back=/home`

This results in the following server-side request to the internal API:

`GET /users/search?name=peter&foo=xyz&publicProfile=true`

Review the response for clues about how the additional parameter is parsed. For example, if the response is unchanged this may indicate that the parameter was successfully injected but ignored by the application.

To build up a more complete picture, you'll need to test further.

## Injecting valid parameters

If you're able to modify the query string, you can then attempt to add a second valid parameter to the server-side request.
For example, if you've identified the `email` parameter, you could add it to the query string as follows:

`GET /userSearch?name=peter%26email=foo&back=/home`

This results in the following server-side request to the internal API:

`GET /users/search?name=peter&email=foo&publicProfile=true`

Review the response for clues about how the additional parameter is parsed.

## Overriding existing parameters

To confirm whether the application is vulnerable to server-side parameter pollution, you could try to override the original parameter. Do this by injecting a second parameter with the same name.

For example, you could modify the query string to the following:

`GET /userSearch?name=peter%26name=carlos&back=/home`

This results in the following server-side request to the internal API:

`GET /users/search?name=peter&name=carlos&publicProfile=true`

The internal API interprets two `name` parameters. The impact of this depends on how the application processes the second parameter. This varies across different web technologies. For example:

- PHP parses the last parameter only. This would result in a user search for `carlos`.
- ASP.NET combines both parameters. This would result in a user search for `peter,carlos`, which might result in an `Invalid username` error message.
- Node.js / express parses the first parameter only. This would result in a user search for `peter`, giving an unchanged result.

If you're able to override the original parameter, you may be able to conduct an exploit. For example, you could add `name=administrator` to the request. This may enable you to log in as the administrator user.

