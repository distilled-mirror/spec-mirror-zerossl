# REST API Download Certificate (inline)



<div class="split-heading">
  <h2>Download Certificate (inline)</h2>
  <span class="method">HTTPS GET</span>
</div>



To download a certificate inline as JSON objects using the ZeroSSL API, you can use the `download` endpoint below and pass the given certificate ID (hash) to the API to the URL inside the `{id}` parameter, as shown below.



**API Request URL:**


```
api.zerossl.com/certificates/{id}/download/return
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify your certificate ID / hash. |
| `include_cross_signed` | `include_cross_signed`                                             Set this parameter to `1` to include the cross signed certificate in the response                                             [(further information)](https://help.zerossl.com/hc/en-us/articles/360060198034-Legacy-Client-Compatibility-Cross-Signed-Root-Certificates). |



Please Note
Please note that only issued certificates can be downloaded.



**API Response:**



If your API request is successful, the ZeroSSL API will return your certificate files in JSON format. You will find an example API response carrying an example certificate below:


```
{
    "certificate.crt": "---BEGIN CERTIFICATE---{primary_certificate}---END CERTIFICATE---",
    "ca_bundle.crt": "---BEGIN CERTIFICATE---{certificate_bundle}---END CERTIFICATE---"
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `certificate.crt` | `certificate.crt`Returns your primary certificate file. |
| `ca_bundle.crt` | `ca_bundle.crt`Returns your certificate bundle file. |






                                  [Get Certificate](/documentation/api/get-certificate)
