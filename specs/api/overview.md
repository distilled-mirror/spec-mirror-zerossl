# Documentation REST API



## Getting Started


                        ZeroSSL makes it easy to create, install and manage SSL certificates of any kind by offering
                            an easy-to-use user interface with calear instructions and plenty of automation in the
                            background. To better serve customers who are looking to put SSL management on autopilot
                            completely, we are offering a full-fledged SSL REST API that will allow you to automate all
                            the actions our UI supports and perform them using a secure, fast and straightforward API
                            interface.


## Base URL


                        API requests are made using a simple API base URL, variable endpoints and requests using **HTTPS**
                            GET and POST. No matter which API endpoint you are using, the value below will your base
                            URL: 


```
api.zerossl.com
```



## HTTPS redirection



The ZeroSSL API redirects HTTP to HTTPS for security reasons. We recommend using HTTPS directly for your requests in order to avoid any redirection issues.



## Access Key


                        Each user account is assigned a unique API access key, which must be passed to the API using
                            a simple HTTPS GET request parameter called `access_key`. You will find your API
                            access key in the [Developer section]({{ $page->appBaseUrl }}/developer)
                            of your ZeroSSL management console. 


You can find an example URL carrying an API access key below:



```
api.zerossl.com/example_endpoint?access_key=EXAMPLE_KEY
```



Please note that the values `example_endpoint` and `EXAMPLE_KEY` will
need to be replaced in order to work.



## Methods


                        The ZeroSSL API currently supports around 10 methods you can use to create, verify, download
                            and otherwise existing or new SSL certificates. Some methods are making use of HTTPS GET
                            parameters, others require HTTPS POST parameters in order to work.


To get started right away, please find a list of available API methods below:



* [Download Certificate (.zip)](/documentation/docs/api/download-certificate)
* [Get Verification Status](/documentation/docs/api/verification-status)
* [Resend Verification Email](/documentation/docs/api/resend-verification)



## Alternative: Send JSON requests


                        Instead of using HTTP GET or POST parameters, you can submit JSON in every API request. The parameters
                        are exactly the same as described in the API documentation, the JSON has to be in the request body.


Allowed request content
In certain endpoints we require you to send lists as comma-seperated strings. Currently, this also applies to JSON requests, you can **not send arrays** instead (yet).



Header required

If you are submitting a JSON request it is mandatory to set the `Content-Type: application/json` header.



                            **JSON request body sample for [Create Certificate](https://zerossl.com/documentation/api/create-certificate/):**




```
{
    "certificate_domains": "zerossl.dev",
    "certificate_validity_days": 90,
    "certificate_csr": "CSR",
    "strict_domains": 1
}
```




New feature, added Q2, 2023.



## API integrator information


                        Read this section carefully if you are going to automate processes using our API for instance by
                            writing your own scripts ([Sample API integration](https://github.com/zerossl/cli-client)).

                        API changes

                        Sometimes new functionality is added to the ZeroSSL API, and in rare cases the functionality
                            of endpoints may change a little.
                            The ZeroSSL API basically follows the rules of the **tolerant reader pattern**.
                            If you implement the ZeroSSL API in your web application your web application should be *tolerant*
                            in the following regards:


* **Endpoints: ** New endpoints might be published over time
* **Enumerations: ** Additional options might be added over time


                        In general the current API is treated as conservative as possible, and we try to do as few
                            changes as possible. Endpoints as well as attributes shall never be removed. Anyway try to
                            be tolerant in your implementations.

                        Proper use of the API

                        The ZeroSSL API is protected against misuse. Write appropriate integrations which use the
                            ZeroSSL API in a reasonable way.
                            In case of heavy misuse - which endangers our systems' functionality and therefore other
                            users - you might get blocked (temporarily or even permanently).

                        


                        
                            [Create Certificate](/documentation/api/create-certificate)
