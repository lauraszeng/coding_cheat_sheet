# Fetch API

Fetch is a built in function in javascript that you can use to make HTTP requests to fetch resources (like data in JSON format, images, files, etc). It simplifies asynchronous dta fetching in JavaScript and is used for interacting with APIs to retrieve and send data asynchronously over the web.

## Basic Format
fetch() takes 2 arguments:
- a url
- an object (of options, including method properties like GET/POST/PUT/DELETE... if you don't specify one, then the default is GET)

it's promise-based, which means that it sends in a request that either resolves or rejects

the typical format is:
``` javascript
fetch("url_string")
    .then(response => console.log(response))
    .then(data => console.log(data))
    .catch(error => console.error(error));
```
once a promise resolves, it returns a response object. the response object will have a status code that lets you know how the request went, and also has a list of methods that you can use to convert it to different readable formats (like JSON)

note that if you pass through a request where the site can't locate the resource, the promise is still going to resolve, meaning that it won't return an error message. you can check if the response isn't ok tho by console.logging the response object.

data is the data that gets returned to us after passing the response object through a method

.catch catches errors

here's a typical code block
``` javascript
fetch("https://pokeapi.co/api/v2/pokemon/pikachu")
    .then(response => {
        // if the response isn't ok, throw a new error to be caught using .catch
        if(!response.ok {
            throw new Error("wow that's not there");
        })
        // if the resposne is ok tho, return the response in a JSON format
        return response.json();
    })
    .then(data => console.log(data.weight))
    .catch(error => console.error(error));
```

response.json converts the response into a json format. this is also promise based.

## Asynchronous Fetch

``` javascript
async function fetchData() {
    try {
        const response = await fetch();
    }
    catch(error) {
        console.error(error);
    }
}
```
