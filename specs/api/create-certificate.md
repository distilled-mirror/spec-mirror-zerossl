# REST API Create Certificate



<div class="split-heading">
  <h2>Create Certificate</h2>
  <span class="method">HTTPS POST</span>
</div>



To create a new SSL certificate using the ZeroSSL API you will need to make an HTTPS POST request to the API's `certificates` endpoint. Below you will find the API request URL you will need to make your request to as well as all required and optional request parameters.



**API Request URL:**


```
api.zerossl.com/certificates
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |



**HTTPS POST Request Parameters:**



| Parameter | Description |
| --- | --- |
| `certificate_domains` | `certificate_domains`**[Required]** Use this parameter to specify one or multiple comma-separated domains (or IP addresses) to be secured by your certificate. The first element of the list should be identical to the CN (common name) specified within your CSR. |
| `certificate_csr` | `certificate_csr`**[Required]** Use this parameter to specify a *certificate signing request (CSR)* for your certificate. The CSR has to be *2048-bit or 4096-bit encrypted*, otherwise it is rejected or might cause other issues.                                             The CSRs' CN (common name) should be identical to the first element in your `certificate_domains` parameter.                                               *It is highly recommended to use a fresh, unique and correct CSR for each and every certificate* (for security reasons and in order to avoid any problems with the certificate).                                               Valid examples for the CSRs' CN (common name): `example.com`, `127.0.0.1`. |
| `certificate_validity_days` | `certificate_validity_days` For creating 1-year certificates specify `365` here, the default is `90`. Other values are currently not supported. |
| `strict_domains` | `strict_domains` Set this parameter to `1` in order to create a certificate exactly for the domains passed in the `certificate_domains` parameter.                                             This means the certificates' *Subject Alternative Names (SAN)* will not include any alternative DNS entries.                                               In practice this mostly affects *www./non-www.* variants: While most users prefer to cover and validate both variants by default,                                             you might want to create a certificate which covers exactly one of those variants. |
| `replacement_for_certificate` | `replacement_for_certificate` Certificate hash of the certificate to be replaced.                                             The certificate to be replaced must be in status `issued` or `expiring_soon`. You can only create one replacement certificate for an existing certificate.                                             This parameter is entirely optional and not yet widely adapted. In the future it might be used in the UI. |



::: warning Breaking change (BC) for few user agents
The ZeroSSL REST API redirects HTTP requests to HTTPS with a 301 permanent redirect. According to the specification 301 redirects may not change the request method.
Some clients which are not sticking to the specification will change a POST into a GET request to the same URL and this can lead to unexpected results. Make sure to use the correct request method.
More information: [Mozilla HTTP Status Code 301](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/301).
:::


::: warning CSR is required
Please note that in order for your certificate to be created you will be required to specify an existing CSR using the `certificate_csr` parameter. [Here's a tool](https://csrgenerator.com/) you can use to generate a new CSR.
:::


::: info Validate your CSR
If you want to validate your CSR first you can use the [validate CSR endpoint](/documentation/docs/api/validate-csr) for the check.
:::



**API Response:**


If your API request has been successful, you will receive a JSON API response containing all the details of your newly created SSL certificate. For illustration purposes, you will find an example API response below.


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
    "signature_algorithm_properties": null,
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
| `type` | `type`Returns a numeric ID to identify the certificate type. Possible values: `1` (90-day), `2` (90-day wildcard), `3` (90-day multi-domain), `4` (1-year), `5` (1-year wilcard), `6` (1-year multi-domain) |
| `common_name` | `common_name`Returns the common name (e.g. `domain.com`) of your certificate. |
| `additional_domains` | `additional_domains`Returns any additional domains (SANs) in your certificate. |
| `created` | `created`Returns the exact time (UTC) your certificate was created. |
| `expires` | `expires`Returns the exact time (UTC) your certificate will expire. |
| `status` | `status`Returns the current certificate status. Possible values: `draft`, `pending_validation`, `issued`, `cancelled`, `revoked`, `expired` |
| `validation_type` | `validation_type`Returns `null` if domain verification has not been initiated, or the selected verification type. Possible values: `EMAIL` (email verification), `CNAME_CSR_HASH` (CNAME verification), `HTTP_CSR_HASH` (HTTP file upload), `HTTPS_CSR_HASH` (HTTPS file upload) |
| `validation_emails` | `validation_emails`Returns one or a comma-separated list of selected verification emails if email verification is chosen for this certificate. |
| `replacement_for` | `replacement_for`Returns the ID (certificate hash) of the existing certificate this certificate is replacing as part of a renewal. |
| `validation` | `validation`Returns a series of sub-objects related to domain verification. |
| `email_validation` | `email_validation`Returns an array of eligible domain verification emails. |
| `other_methods` | `other_methods`Returns a series of sub-objects (one for each domain in your certificate) containing alternative verification methods. |
| `file_validation_url_http` | `file_validation_url_http`Returns the URL (http format) your verification file must be uploaded to as part of domain verification. |
| `file_validation_url_https` | `file_validation_url_https`Returns the URL (https format) your verification file must be uploaded to as part of domain verification. |
| `file_validation_content` | `file_validation_content`Returns the content your verification file must contain, consisting of three lines of plain-text. |
| `cname_validation_p1` | `cname_validation_p1`Returns the host-part (Name) of the CNAME-record that must be created as part of domain verification. |
| `cname_validation_p2` | `cname_validation_p2`Returns the value-part (Point To) of the CNAME-record that must be created as part of domain verification. |



Certificate Issuance
In order for your certificate to be issued, please note that you will need to complete one of the 3 available domain verification methods: Email Verification, Verification via CNAME Record, Verification via HTTP File Upload or Verification via HTTPS File Upload.






                                  [Verify Domains](/documentation/api/verify-domains)
