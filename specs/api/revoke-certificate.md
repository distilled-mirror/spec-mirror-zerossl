# REST API Revoke Certificate


<div class="split-heading">
  <h2>Revoke Certificate</h2>
  <span class="method">HTTPS POST</span>
</div>



To revoke an issued certificate using the ZeroSSL API you will need to make an HTTPS POST request to the API endpoint below and specify your certificate using its ID (hash) inside the URL's `{id}` parameter, as shown below.



Possible reasons why you might want to revoke an issued certificate:



* There is any risk that its private key might have been compromised (urgent)
* The domain it was issued for is no longer operational
* The contents of the certificate are wrong



Warning
Make sure to use this endpoint with care and do only revoke certificates you really want to revoke. Only certificates with status `issued` can be revoked.
If a certificate has already been successfully revoked you will get a success response nevertheless.



**API Request URL:**



```
api.zerossl.com/certificates/{id}/revoke
```



**HTTPS POST Request Parameters:**



| Parameter | Description |
| --- | --- |
| `access_key` | `access_key`**[Required]** Use this parameter to specify your API access key. |
| `{id}` | `{id}`**[Required]** Use this parameter to specify the certificate ID (hash) of the certificate to be revoked. |
| `reason` | `reason`  One of:                                           * `Unspecified`: Default * `keyCompromise`: Compromised private key * `affiliationChanged`: Subjects' name or identity information has changed * `Superseded`: Certificate has been replaced * `cessationOfOperation`: Authorized domain names are no longer owned |



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






                            [Cancel Certificate](/documentation/api/cancel-certificate)
