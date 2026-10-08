# REST API Resend Verification




<div class="split-heading">
  <h2>Resend Verification Email</h2>
  <span class="method">HTTPS POST</span>
</div>



To resend all verification emails for a specific certificate using the ZeroSSL API, simply make an HTTPS GET request to the API endpoint below, specifying your certificate using its ID (hash) inside the URL's `{id}` parameter, as shown below.



Only for Email Verification
Please note that this API endpoint can only be used if Email Verification is your selected domain verification method.



**API Request URL:**


```
api.zerossl.com/certificates/{id}/challenges/email
```



**HTTPS GET Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify your certificate ID / hash. |



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






                                  [Revoke Certificate](/documentation/api/revoke-certificate)
