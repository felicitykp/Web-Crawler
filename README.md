# **Project 5**: Web-Crawler
### By Ella Isgar and City Keyzer-Pollard

## High-Level Project Description


The 3700crawler program is a simple web crawler that gathers data from a fake social networking website provided to us. 

We define a Crawler class that supports one socket, server, port, username, password, middle_token, csrf_token, and session_id at a time. Throughout execution, a list of secret flags discovered, URLs visited, and URLs to_visit is maintained.

The get_request method crafts an HTTP GET request using the provided path and sets the necessary headers. Similarly, the post_request method crafts an HTTP POST request with headers and data. The initial_get_request method crafts an HTTP GET request that doesn't require the csrf_token and session_id.

The parse_response method searches the HTTP response for specific content and updates the corresponding instance variables in the class.

The goto method implements our recursive URL searching algorithm that determines its current action based on the status code of the HTTP response it receives. If the status is 2, it calls the search_page method to search the given HTTP response for any secret flags and all URLs to the to_visit list if they are not already visited or to be visited.

The setup method creates a socket, wraps it in SSL, and connects to the provided server and port.

The receive_data method receives data and looks for the Content-Length header to receive the full response body. If the received data is less than the expected length, it keeps receiving until it gets the full response body.

## Challenges Faced

Logging in! Understanding the elements needed in the GET requests was essential to us being able to make it past the login in page and subsequent rerouted login page that would not stop being the response until we realized that we needed to update the tokens and session id continuously. Once we were able to implement a dependable log-in flow, the breakdown of our algorithm to search for the URLs simply relied on us using algorithms to search recursively through each page.

## Testing the Code
We broke down the progress of our Web-Crawler by setting goals for our program.

The first goal was actually logging in. We Sent an initial GET request, comparing our own GET request to the captured packet that was generated when actually visiting fakebook.com. After ensuring our request and response contained the pieces we needed to continue onto our POST message, we counted this goal of reaching the site as complete.

The success of logging in to fakebook.com was determined by reading the raw HTML in the response to our POST request. When we were not rerouted immediately to another log-in attempt and could see the first layer of linked friends, we knew we were in.

Testing our recursive searching algorithm came down to simple print statements and patience. We began basic, with one list, simply gathering as many URLs as possible. Then implementing no repeating URLs. Once we confirmed our lists printed with no repeats, we searched for our flags.

Upon submission, our flags printed cleanly and handled changed username / password without failure, passing all tests it was given on Gradescope.