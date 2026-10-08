# REST API Generate ACME EAB Credentials



<div class="split-heading">
  <h2>Generate ACME EAB Credentials via API</h2>
  <span class="method">HTTPS POST</span>
</div>




To generate a set of ACME EAB credentials using the ZeroSSL API you will need to make an HTTPS POST request to the API endpoint below.



::: info Please note
Since March 2022 all EAB credentials are **reusable**. One set of EAB credentials should be enough for most use cases. EAB credentials are limited to a maximum per user/per day.
:::


**API Request URL:**


```
api.zerossl.com/acme/eab-credentials
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |



**API Response:**



If your API request has been successful, you will receive a simple JSON response indicating that your API request was successful and containing your ACME EAB credentials. Find an example API response below.


```
{
    "success": 1
    "eab_kid": "GD-VvWydSVFuss_GhBwYQQ",
    "eab_hmac_key": "MjXU3MH-Z0WQ7piMAnVsCpD1shgMiWx6ggPWiTmydgUaj7dWWWfQfA"
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `success` | `success`Returns `1` to indicate that your API request was successful. |
| `eab_kid` | `eab_kid`Returns your EAB KID value. |
| `eab_hmac_key` | `eab_hmac_key`Returns your EAB HMAC key value. |






                                  [Error Codes](/documentation/acme/error-codes)
