# HTTP Service Stubs

Node service for stubbing responses to GET requests

## Creating Stubs

Create stubs by sending a PUT request to the path you want stubbed with a triple representing the response you want the next GET request to responed with:

    PUT http://example.org/example_path/ HTTP/1.1
    Host: localhost:5000
    Content-Type: application/json
    
    [200, {"Content-Type": "application/json"}, "{ \"foo\": \"bar\" }"]

The triple consists of:
1. HTTP response code
2. HTTP headers
3. The body of the response

Multiple PUT requests will generate additional stubs that will be returned by additional GET requests 

## Requests 

A GET request for a stubbed resource will return the stubbed response if one exists or a 404 if one isn't available.
If multiple stubs have been created for an endpoint each GET requests will respond with the next stub until all stubs have been deleted.
The most recent stub created is the last one to be returned.




