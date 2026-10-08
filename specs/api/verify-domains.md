
# REST API Verify Domains


<div class="split-heading">
  <h2>Verify Domains</h2>
  <span class="method">HTTPS POST</span>
</div>



In order for your certificate to be issued, all domains included in your certificate will need to be verified. There are four methods that can be used to verify domains: email verification, verification via DNS (CNAME), verification via HTTP file upload and verification via HTTPS file upload.



To initiate domain verification, you will need to make a request to the endpoint below carrying your API access key as well as some HTTPS POST request parameters. Please note that `{id}` must be replaced with your certificate ID (hash).



**API Request URL:**


```
api.zerossl.com/certificates/{id}/challenges
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify your certificate ID / hash. |



**HTTPS POST Request Parameters:**



| Parameter | Description |
| --- | --- |
| `validation_method` | `validation_method`**[Required]** Use this parameter to specify the verification method to use for this certificate. Possible values: `EMAIL` (email verification), `CNAME_CSR_HASH` (CNAME verification), `HTTP_CSR_HASH` (HTTP file upload), `HTTPS_CSR_HASH` (HTTPS file upload) |
| `validation_email` | `validation_email`If your selected verification method is **email verification**, use this parameter to specify one or multiple comma-seperated verification email addresses. You need to specify one verification email address per domain. |



::: warning Verification Methods

Please note that you can use the API endpoint above to re-initiate domain verification using the same or another verification method at any given time before the certificate is validated and issued.


IP Address certificates **can only be verified using the File Upload method**. Other domain validation methods, such as Email or CNAME, are not supported for IP-based certificates.
:::





Email Verification **API Response**



If you selected email verification and your API request was successful, you will receive a verification email to the selected verification email address for each of the domains in your certificate. In order for your certificate to be issued, you will need to follow the steps shown in these verification emails. If you are not sure about how to verify your domains via email, you can [learn more about email verification here](/help/verify-domains).



For as long as your domains remain unverified, the status of your certificate will be `pending_validation`. As soon as your domains have been verified and your certificate has been issued, the certificate status will be changed to `issued` automatically by our system.


::: warning Check Verification Status
To check the email verification status of the domains in your certificate, you can use the API's [Status endpoint](/documentation/docs/api/verification-status).
:::





CNAME **API Response**



If the verification of your CNAME-records was successful, the ZeroSSL API will return your entire certificate object with status `pending_validation`. From this moment it will take just a few seconds (in some cases, up to 5-10 minutes) for our system to validate and issue your certificate. As soon as your certificate has been issued, the certificate status will change to `issued` automatically.



CNAME **Possible Errors**



If the verification of some or all of your CNAME-records fails, the API will return an error object in JSON format outlining in detail which of the domains could be verified and which could not be verified.



You will find an example error response for CNAME verification below:


```
{
    "success": false,
    "error": {
        "code": 0,
        "type": "domain_control_validation_failed",
        "details": {
            "domain.com": {
                "domain.com": {
                    "cname_found": 0,
                    "record_correct": 0,
                    "target_host": "_2B449B729284AA7CB56014584F261FBF",
                    "target_record": "A1063BBA157D.686A709A3.4BAD7A.CA.COM",
                    "actual_record": ""
                },
                "www.domain.com": {
                    "cname_found": 0,
                    "record_correct": 0,
                    "target_host": "_2B449B729284AA7CB56014584F261FBF",
                    "target_record": "A1063BBA157D.686A709A3.4BAD7A.CA.COM",
                    "actual_record": ""
                }
            }
        }
    }
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `success` | `access_key`Returns `false` to indicate that an API error occurred. |
| `error` | `error`Returns a sub-object containing error details. |
| `code` | `code`Returns a numeric error code uniquely associated with the specific error. |
| `type` | `type`Returns a text-based error key uniquely associated with the specific error. |
| `details` | `details`Returns an object containing error details for each domain (or a pair of www and non-www domains). |
| `cname_found` | `cname_found`Returns `1` or `0` depending on whether your CNAME-record was found. |
| `record_correct` | `record_correct`Returns `1` or `0` depending on whether the CNAME-record found is correct. |
| `target_host` | `target_host`Returns the host-part (Name) of the required CNAME-record. |
| `target_record` | `target_record`Returns the value-part (Point To) of the required CNAME-record. |
| `actual_record` | `actual_record`Returns the value-part of the CNAME record found for the given domain. |






HTTP file validation **API Response**



If the verification of your uploaded files was successful, the ZeroSSL API will return your entire certificate object with status `pending_validation`. From this moment it will take just a few seconds (in some cases, up to 5-10 minutes) for our system to validate and issue your certificate. As soon as your certificate has been issued, the certificate status will change to `issued` automatically.



HTTP file validation **Possible Errors**



If the verification of some or all of your uploaded files fails, the API will return an error object in JSON format outlining in detail which of the domains could be verified and which could not be verified.



You will find an example error response for HTTP file upload verification below:



```
{
    "success": false,
    "error": {
        "code": 0,
        "type": "domain_control_validation_failed",
        "details": {
            "zero.example-zero.com": {
                "http://zero.example.com/.well-known/pki-validation/E437B2F258578249498AA2A3708D6951.txt": {
                    "file_found": 0,
                    "error": true,
                    "error_slug": "wrong_file_content",
                    "error_info": "The validation file was found, but the contents are wrong."
                }
            },
            "one.example-one.com": {
                "http://one.example.com/.well-known/pki-validation/E437B2F258578249498AA2A3708D6951.txt": {
                    "file_found": 0,
                    "error": true,
                    "error_slug": "bad_response_code",
                    "error_info": "Server responded with status code: 404"
                }
            },
            "example.com": {
                "validation_successful": true
            }
        }
    }
}
```





HTTP file validation **Explanation of error response**



Explanation of example:


* *example.com*: The file was found and successfully verified
* *zero.example-zero.com*: The file was found, but the content is wrong.
* *one.example-one.com*: The server responded with status code 404, which means the file was not yet uploaded.






Explanation of error slug:


Recently we have implemented more granular error reporting for the HTTP file validation. If validation fails, in many cases (except for server failures) you may want to work with validation error slugs:



| Error Slug | Description |
| --- | --- |
| `http_transport_failed` | Returned if there was a connection problem. Reasons can be that the host can not be resolved or your server is not reachable. Check if the file is publicly available. This might also occur as a temporary problem, in this case just retry the API call. |
| `bad_response_code` | The server responded not with HTTP code 200 (OK). Most probably the validation file was not placed correctly (404). Note that redirections (3xx) are not allowed for the HTTP file validation. |
| `timeout` | Request to the server had a timeout. Check if your server responds very slowly. If not, just retry. |
| `bad_file_content` | The validation file can not be read or is wrong. |
| `wrong_file_content` | Your file does not contain exactly the content required. |



                                  [Download Certificate](/documentation/api/download-certificate)
