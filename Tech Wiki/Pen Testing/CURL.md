Tags:  [[Cybersecurity]] [[Cyber Tool]] [[Penetration Testing]] [[Command Line Tool]] #Curl 

cURL (short for “client URL” and pronounced “curl”) is an open-source command line tool for exchanging data with a server. With cURL, you specify an endpoint (a URL where you want to send data to or retrieve data from) and, if necessary, the data you want to send — all this through a command line interface (CLI).

CURL Syntax

The basic syntax of the curl command looks like this:

CURL [options] [URL]

Let's unpack each part of this command:

- command: All cURL commands begin with cURL to specify that you are making a cURL command.

- options: Options (also called flags) customize the behavior of the command. They are, you guessed it, optional.

- URL: This is the location where you want to access data from or send data to.

#### Get Webpage content
```Bash
curl https://google.com
```


#### Send a POST Request

Post Data

Using the POST method, you can transfer data to a server through an API. The API processes the data, then takes steps such as saving it to a database, and returns a response indicating the status of your request.

To use POST and other HTTP methods besides GET, we need to add options to our command. For specifying the HTTP method, we use the -X flag combined with the method. The -X flag is an alias for --request.

For example, to post a new resource through the JSONPlaceholder API, we’ll construct a command with the following:

    -X POST to specify that we’re making a POST request.
    -H “Content-Type: application/json” which sets the header of the request and tells the API that the data is in JSON format. -H is an alias for --header.
    -d '{"title": "My New Post", "body": "This is the body of the post.", "userId": 1}' which is the new resource to be posted. -d is an alias for --data.
    https://jsonplaceholder.typicode.com/posts which is the endpoint of the request.

Together, the command looks like this:

```Bash
curl -X POST -H “Content-Type: application/json” -d '{"title": "My New Post", "body": "This is the body of the post.", "userId": 1}' https://jsonplaceholder.typicode.com/posts
```

After sending this request, the API gives us a response confirming the post was made.

#### Get Header information
```Bash
curl http://10.0.100.1 -v
```

The headers can show information like webserver software and possibly the programming/scripting language in use. 

```Bash
           
user@machine$ curl http://10.10.53.76 -v
*   Trying 10.10.53.76:80...
* TCP_NODELAY set
* Connected to 10.10.53.76 (10.10.53.76) port 80 (#0)
> GET / HTTP/1.1
> Host: 10.10.53.76
> User-Agent: curl/7.68.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< X-Powered-By: PHP/7.4.3
< Date: Mon, 19 Jul 2021 14:39:09 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive

        
```
