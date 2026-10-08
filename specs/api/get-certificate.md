# REST API Get Certificate



<div class="split-heading">
  <h2>Get Certificate</h2>
  <span class="method">HTTPS GET</span>
</div>



To retrieve information about an existing certificate using the ZeroSSL API you will need to make an HTTPS GET request to the API's `certificates` and pass the given certificate ID (hash) to the URL inside the `{id}` parameter, as shown below.



**API Request URL:**


```
api.zerossl.com/certificates/{id}
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify your certificate ID / hash. |



**API Response:**



If your API request has been successful, you will receive a JSON API response containing all the details of your SSL certificate. For illustration purposes, you will find an example API response below.


```
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
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `id` | `id`Returns the internal certificate ID, also referred to as certificate hash. |
| `type` | `type`Returns a numeric ID to identify the certificate type. Possible values: `1` (90-day), `2` (90-day wildcard), `3` (90-day multi-domain), `4` (1-year), `5` (1-year wildcard), `6` (1-year multi-domain) |
| `common_name` | `common_name`Returns the common name (e.g. `domain.com`) of your certificate. |
| `additional_domains` | `additional_domains`Returns any additional domains (SANs) in your certificate. |
| `created` | `created`Returns the exact time (UTC) your certificate was created. |
| `expires` | `expires`Returns the exact time (UTC) your certificate will expire. |
| `status` | `status`Returns the current certificate status. Possible values: `draft`, `pending_validation`, `issued`, `revoked`, `cancelled`, `expired` |
| `validation_type` | `validation_type`Returns `null` if domain verification has not been initiated, or the selected verification type. Possible values: `EMAIL` (email verification), `CNAME_CSR_HASH` (CNAME verification), `HTTP_CSR_HASH` (HTTP file upload), `HTTPS_CSR_HASH` (HTTPS file upload) |
| `validation_emails` | `validation_emails`Returns one or a comma-separated list of selected verification emails if email verification is chosen for this certificate. |
| `replacement_for` | `replacement_for`Returns the ID (certificate hash) of the existing certificate this certificate is replacing as part of a renewal. |
| `fingerprint_sha1` | `fingerprint_sha1`The SHA-1 fingerprint of the certificate (if issued). [Note: Added in autumn 2022, is `null` for older certificates.] |
| `brand_validation` | `brand_validation`Usually `null` or `false` - only true for very few certificates where the domain has to be manually reviewed. |
| `signature_algorithm_properties` | `signature_algorithm_properties`Signature algorithm and key size for your certificate.   Syntax: `[OpenSSL parsed signature algorithm]:[key size]`.                                               Examples: `sha384WithRSAEncryption:2048`, `ecdsa-with-SHA384:256`.                                               We get that information by best effort: It is `null` until a certificate has been issued and its signature algorithm properties have been determined. It can also be `null` for certificates being issued before December 2025, although we try to catch up. Furthermore, it can be `null` in case we are unable to retrieve the required information (can also be `unknown` or similar). |
| `validation` | `validation`Returns a series of sub-objects related to domain verification. |
| `email_validation` | `email_validation`Returns an array of eligible domain verification emails. |
| `other_methods` | `other_methods`Returns a series of sub-objects (one for each domain in your certificate) containing alternative verification methods. |
| `file_validation_url_http` | `file_validation_url_http`Returns the URL (http format) your verification file must be uploaded to as part of domain verification. |
| `file_validation_url_https` | `file_validation_url_https`Returns the URL (https format) your verification file must be uploaded to as part of domain verification. |
| `file_validation_content` | `file_validation_content`Returns the content your verification file must contain, consisting of three lines of plain-text. |
| `cname_validation_p1` | `cname_validation_p1`Returns the host-part (Name) of the CNAME-record that must be created as part of domain verification. |
| `cname_validation_p2` | `cname_validation_p2`Returns the value-part (Point To) of the CNAME-record that must be created as part of domain verification. |






                                  [List Certificates](/documentation/api/list-certificates)
