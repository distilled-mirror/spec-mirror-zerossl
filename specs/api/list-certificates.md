# REST API List Certificates


<div class="split-heading">
  <h2>List Certificates</h2>
  <span class="method">HTTPS GET</span>
</div>



To retrieve information about an existing certificate using the ZeroSSL API you will need to make an HTTPS GET request to the API's `certificates`. You can use a series of GET parameters to specify certificate status, search and configure pagination.



::: info Note
In case you have more than 100 ACME certificates you need at least a ZeroSSL basic plan in order to work with those in Dashboard or API.
In case you have more than 100K ACME certificates you need at least a ZeroSSL premium plan in order to work with those in Dashboard or API.
:::


**API Request URL:**


```
api.zerossl.com/certificates
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `certificate_status` | `certificate_status`Use this parameter to specify one or multiple comma-separated certificate status values. Possible values: `draft`, `pending_validation`, `issued`, `cancelled`, `revoked`, `expired`.                                                                                            You can also send the special status `expiring_soon`. In this case all issued certificates are included, which expire within the next 30 days and should be renewed (in paid ZeroSSL accounts those are not credited anymore). |
| `certificate_type` |
| `single90Days`                                                              `1` | Single-Domain 90-Day certificates |
| `wildcard90Days`                                                              `2` | Wildcard 90-Day certificates |
| `multiDomain90Days`                                                              `3` | Multi-Domain 90-Day certificates |
| `single1Year`                                                              `4` | Single-Domain 1-Year certificates |
| `wildcard1Year`                                                              `5` | Wildcard 1-Year certificates |
| `multiDomain1Year`                                                              `6` | Multi-Domain 1-Year certificates |
| `acme90Days`                                                              `7` | ACME certificates |





                                        `search`
                                        `search`
                                            Use this parameter to search for certificates having the given common name or SAN.


High volume limitation
If you have more than 1000 certificates: You must provide the exact common name of the certificate. SAN can not be searched at the moment (we are going to provide a solution for this use case in the future).




                                        `limit`
                                        `limit`Use this parameter to specify a pagination limit (Default: `100`).

High volume limitation
You may retrieve a maximum of 1000 certificates with one API call. If you have more results, you have to use the pagination (please check the properties `total_count`, `result_count`, `page` and `limit` from the response).




                                        `page`
                                        `page`Use this parameter to specify a pagination page. If not specified the default `1` is returned, otherwise a numeric string containing the number of the page.






**API Response:**



If your API request has been successful, you will receive a JSON API response containing all the details of your SSL certificate. For illustration purposes, you will find an example API response below.


```
{
    "total_count": 11,
    "result_count": 10,
    "page": 1,
    "limit": 10,
    "acmeUsageLevel": "LOW",
    "isAcmeLocked": false,
    "results": [
        {
            "id": "a856a39a1c3ad0s8asa606g37667d221",
            "type": "1",
            "common_name": "domain.com",
            "additional_domains": "www.domain.com",
            "created": "2020-04-29 09:04:19",
            "expires": "2020-07-28 00:00:00",
            "status": "draft",
            "validation_type": null,
            "validation_emails": null,
            "replacement_for": "",
            "fingerprint_sha1": null,
            "brand_validation": null,
            "signature_algorithm_properties": "sha384WithRSAEncryption:2048",
            "validation": {
                "email_validation": {
                    "domain.com": [
                        "admin@domain.com",
                        "administrator@domain.com",
                        "hostmaster@domain.com",
                        "postmaster@domain.com",
                        "webmaster@domain.com"
                    ]
                },
                "other_methods": {
                    "domain.com": {
                        "file_validation_url_http": "http://domain.com/.well-known/pki-validation/2449B.txt",
                        "file_validation_url_https": "https://domain.com/.well-known/pki-validation/2449B.txt",
                        "file_validation_content": [
                            "2B449B722B449B729394793947",
                            "comodoca.com",
                            "4bad7360c7076ba"
                        ],
                        "cname_validation_p1": "2B449B7293947.domain.com",
                        "cname_validation_p2": "2B449B7293947.23DD7293947.11DD7293941.ca.com"
                    },
                    "www.domain.com": {
                        "file_validation_url_http": "http://www.domain.com/.well-known/pki-validation/2449B.txt",
                        "file_validation_url_https": "https://www.domain.com/.well-known/pki-validation/2449B.txt",   
                        "file_validation_content": [
                            "2B449B722B449B729394793947",
                            "comodoca.com",
                            "4bad7360c7076ba"
                        ],
                        "cname_validation_p1": "2B449B7293947.www.domain.com",
                        "cname_validation_p2": "2B449B7293947.23DD7293947.11DD7293941.ca.com"
                    }
                }
            }
        },
        {...}
    ]
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `total_count` | `total_count`Returns the total number of results found for your query. |
| `result_count` | `result_count`Returns the number of results shown on the current page. |
| `page` | `page`Returns the current page number. |
| `limit` | `limit`Returns the specified pagination page limit. |
| `results` | `results`Returns an array of certificates. For detailed information about certificate response objects, please refer to the [Get Certificate](/documentation/docs/api/get-certificate) section. |






                                  [Verification Status](/documentation/api/verification-status)
