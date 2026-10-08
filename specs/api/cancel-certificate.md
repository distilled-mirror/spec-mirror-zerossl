# REST API Cancel Certificate



<div class="split-heading">
  <h2>Cancel Certificate</h2>
  <span class="method">HTTPS POST</span>
</div>



To cancel an existing certificate using the ZeroSSL API you will need to make an HTTPS POST request to the API endpoint below and specify your certificate using its ID (hash) inside the URL's `{id}` parameter, as shown below.



::: warning Limitations
Please note that only certificates with status `draft` or `pending_validation` can be cancelled.
:::


**API Request URL:**


```
api.zerossl.com/certificates/{id}/cancel
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify your certificate ID (hash). |



**API Response:**



If your API request has been successful, you will receive a simple JSON response indicating that your API request was successful.


```
{
    "success": 1
}
```



**Response Objects:**



| Parameter | Description |
| --- | --- |
| `success` | `success`Returns `1` to indicate that your API request was successful. |






                                  [Validate CSR](/documentation/api/validate-csr)
