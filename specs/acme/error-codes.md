# ACME API Error Codes


<div class="split-heading">
  <h2>Error Codes</h2>
  <span class="method"></span>
</div>


::: info
The errors listed here are relevant for the EAB credentials endpoint, the ACME API itself ([https://acme.zerossl.com/v2/DV90](https://acme.zerossl.com/v2/DV90)) has its own set of errors.
:::


**Errors are responded in JSON just as in the normal ZeroSSL API:**



```
{
    "success": false,
    "error": {
        "code": 2902,
        "type": "failed_creating_eab_account"
    }
}
```

| Error Code / Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| --- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `2902`   `failed_creating_eab_account` | `2902 / failed_creating_eab_account `Your EAB credentials can not be created currently. This is usually due to maintenance or temporary downtimes, please try again later.                                                                                                                                                                                                                                                                                                                             |
| `2903`   `failed_saving_eab_account` | `2903 / failed_saving_eab_account `Your EAB credentials could not be saved. This should occur very rarely, please try again.                                                                                                                                                                                                                                                                                                                                                                           |
| `2904`   `too_many_eab_credentials_created_today` | `2904 / too_many_eab_credentials_created_today `You have created too many EAB credentials today.                                         EAB credentials can be re-used, we do not know any meaningful scenario where you might need those amount of credentials.                                         Please check your implementation (in case of troubles please contact: [support@zerossl.com](mailto: support@zerossl.com)).                                                                   |
| `2905`   `too_many_eab_credentials_created_for_user` | `2905 / too_many_eab_credentials_created_for_user `You have created too many EAB credentials with this user.                                         EAB credentials can be re-used, we do not know any meaningful scenario where you might need those amount of credentials.                                         Please check your implementation (in case of troubles please contact: [support@zerossl.com](mailto: support@zerossl.com)).                                                       |
| `2977`   `caddy_legacy_user_removed` | `2977 / caddy_legacy_user_removed `The Caddyserver legacy user was removed. You can use the Caddyserver with ZeroSSL                                         in various other ways such as the API, with a ZeroSSL user account or by at least providing your email address. More information: [https://github.com/caddyserver/caddy/releases/tag/v2.8.0](https://github.com/caddyserver/caddy/releases/tag/v2.8.0). <br/> Be free to contact our support team in case you have any further questions. |
