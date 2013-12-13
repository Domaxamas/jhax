hjax
====

Very thin wrapper around XMLHttpRequest.

Usage: hjax(url[, options][, callback]);

url can be relative or absolute

options is a key/value object containing the following settable properties:
        log: boolean or a custom function to log with. Default false.
        headers: object. Request headers. Default {"X-Requested-With": "XMLHttpRequest"}
        method: string. Default "GET"
        username: string. For http basic auth. Default ""
        password: string. For http basic auth. Default ""
        data: string. post body data. Default ""
        parseJSON: boolean. Whether to try to JSON.parse the response. Default true.

callback takes the following arguments: (error, data, xhr)
        error will be set if options.parseJSON is true and the data does not parse.
        data is either the parsed or raw data from the server
        xhr is the xhr object, allowing access to .status, .getAllResponseHeaders, etc.

hjax will automatically set content-length and encoding if options.data is set
and you have not aleady set them in options.headers

hjax will set method to POST if you specify options.data and not options.method
or if options.method === "GET"

hjax returns the native xhr object immediately so you can abort etc if need be.
