HTTP Client Library Implementation

There is implementation of the HTTP client using TCP Sockets. The programming library implements only a small subset of HTTP specifications. In other words, the HTTP library supports the following features:
1. GET operation
2. POST operation
3. Query parameters
4. Request headers
5. Body of the request

The following presents the options of the final command line.

httpc (get|post) [-v] (-h "k:v")* [-d inline-data] [-f file] URL
1. Option -v enables a verbose output from the command-line. Verbosity could be useful for testing and debugging stages 
2. URL determines the targeted HTTP server. It could contain parameters of the HTTP operation. For example, the URL 'https://www.google.ca/?q=hello+world' includes the parameter q with "hello world" value.
3. To pass the headers value to your HTTP operation, used -h option. The latter means setting the header of the request in the format "key: value." 
4. -d gives the user the possibility to associate the body of the HTTP Request with the inline data, meaning a set of characters for standard input.
5. Similarly to -d, -f associate the body of the HTTP Request with the data from a given file.
6. get/post options are used to execute GET/POST requests respectively. post should have either -d or -f but not both. However, get option should not used with the options -d or -f.
7. –o filename, which allow the HTTP client to write the body of the response to the specified file instead of the console.

Example:

Server Side:    httpfs -d directory
                httpfs -v -d directory
                httpfs -v -p 8080 -d directory


Client side     httpc get -v 'http://localhost/get?course=networking&assignment=1'
                httpc post -h Content-Type:application/json --d '{"Assignment": 1}' 'http://localhost/post'


                httpc post -v -h Content-Type:application/json --d '{"Assignment": 210}' 'http://localhost/inputBody.txt'
                httpc post -v -h Content-Type:application/json --d '{"Assignment": 210}' 'http://localhost/xx.txt'
                httpc get -v 'http://localhost'
                httpc get -v 'http://localhost/inputBody.txt'
                httpc get -v 'http://localhost/input.txt'
