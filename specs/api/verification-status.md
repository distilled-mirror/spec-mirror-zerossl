# REST API Verification Status



<div class="split-heading">
  <h2>Get Domain Verification Status</h2>
  <span class="method">HTTPS GET</span>
</div>




To retrieve information about the domain verification status for a specific certificate using the ZeroSSL API, simply make an HTTPS GET request to the API endpoint below, specifying your certificate using its ID (hash) inside the URL's `{id}` parameter, as shown below.



Only for Email Verification
Please note that the verification status endpoint is only useful if Email Verification is your selected domain verification method. Other verification methods (CNAME and File Upload) usually provide instant verification results using the [Verify Domains endpoint](/documentation/docs/api/verify-domains).



**API Request URL:**


```
api.zerossl.com/certificates/{id}/status
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify your certificate ID / hash. |



**API Response:**



If your API request has been successful, you will receive a JSON API response containing verification status information for each of the domains in your certificate.


```
{
    "validation_completed": 0,
    "details": {
        "domain.com": {
            "method": "postmaster@domain.com",
            "status": "Email Sent"
        },
        "www.domain.com": {
            "method": "postmaster@domain.com",
            "status": "Email Sent"
        }
    }
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `validation_completed` | `validation_completed`Returns `1` or `0` depending on whether domain verification has been completed. |
| `details` | `details`Returns a sub-object for each domain (or a pair of www and non-www domains) containing verification information. |
| `method` | `method`Returns the verification email selected for the given domain. |
| `status` | `status`Returns the current verification status of the given domain. |






                                  [Resend Verification](/documentation/api/resend-verification)
