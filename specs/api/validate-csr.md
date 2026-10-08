
# REST API Validate CSR



<div class="split-heading">
  <h2>Validate certificate signing request (CSR)</h2>
  <span class="method">HTTPS POST</span>
</div>



You might want to validate a certificate signing request (CSR) e.g. before using it in a certificate creation request.



**API Request URL:**



```
api.zerossl.com/validation/csr
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |



**HTTPS POST Request Parameters:**



| Parameter | Description |
| --- | --- |
| `csr` | `csr`**[Required]** The CSR you want to validate. |



**API Response:**



If your CSR is valid, you will receive the following JSON:


```
{
    "valid": true,
    "error": null,
    "csrResponse": [
        "2048",
        "sigalg=sha256WithRSAEncryption"
    ]
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `valid` | `valid`Returns `true` to indicate your CSR is valid, false otherwise. |
| `error` | `error`Returns `null` in case the CSR was successfully validated, error code and description otherwise. |
| `csrResponse` | `csrResponse`Returns an array containing the key size and signature algorithm in case the CSR was successfully validated, `null` otherwise. |






                            [Error codes](/documentation/api/error-codes)
