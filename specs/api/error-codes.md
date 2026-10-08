# REST API Error Codes



<div class="split-heading">
  <h2>Error Codes</h2>
  <span class="method"></span>
</div>




Whenever there is an error processing your API request, the API will return a straightforward JSON error message carrying a `success` response object set to `false`, an error code as well as a text-based error type.



You will find an example error as well as a list of all possible error codes and messages below.



**Example Error:**



```
{
    "success": false,
    "error": {
        "code": 2803,
        "type": "certificate_not_found"
    }
}
```



**Errors - General:**



| Error Code / Type | Description |
| --- | --- |
| `101`   `invalid_access_key` | `101 / invalid_access_key `User has provided an invalid API access key. |
| `102`   `inactive_user` | `101 / inactive_user `You can not authenticate because your account is not active. |
| `103`   `invalid_api_function` | `103 / invalid_api_function `User has provided an invalid API function. |
| `104`   `route_not_found` | `104 / route_not_found `This route does not exist. Check the spelling in your request URL and also the HTTP method you are using (some endpoints can only be called using a POST request for instance). |
| `110`   `invalid_request_body` | `110 / invalid_request_body `The body of your request was wrong. Please check your request arguments. |
| `111`   `internal_server_error` | `111 / internal_server_error `Something went wrong. If the problem persists, please contact our support team ([support@zerossl.com](mailto:support@zerossl.com)). |
| `112`   `conflict` | `112 / conflict `The target resource can not be modified. |
| `113`   `unprocessable_entity` | `113 / unprocessable_entity `The syntax of your request was correct, but your request can not be processed. |
| `114`   `conflict` | `114 / conflict `The target resource can not be modified. |
| `115`   `invalid_json_request` | `115 / invalid_json_request `You have sent a JSON request, but it can not be decoded as JSON. Please check your input. |
| `116`   `invalid_json_request_param` | `116 / invalid_json_request_param `You have sent an illegal parameter in your JSON request. Multidimensional arrays, objects and resources are not allowed. |
| `2800`   `incorrect_request_type` | `2800 / incorrect_request_type `User has made a non-supported API request. |
| `2801`   `permission_denied` | `2801 / permission_denied `User does not have the permissions to access this resource. |
| `2802`   `missing_certificate_hash` | `2802 / missing_certificate_hash `User has not provided a certificate ID (hash). |
| `2803`   `certificate_not_found` | `2803 / certificate_not_found `The given certificate ID (hash) could not be found. |



**Errors - Create Certificate:**



| Error Code / Type | Description |
| --- | --- |
| `2804`   `cannot_issue_certificate_unpaid_upgrade_invoices` | `2804 / cannot_issue_certificate_unpaid_upgrade_invoices `The current certificate cannot be issued due to unpaid invoices on a user account. |
| `2805`   `invalid_certificate_type` | `2805 / invalid_certificate_type `User has provided an invalid certificate type. |
| `2806`   `missing_certificate_type` | `2806 / missing_certificate_type `User has not provided a valid certificate type. |
| `2807`   `invalid_certificate_validity` | `2807 / invalid_certificate_validity `User has not provided a valid certificate validity. |
| `2808`   `invalid_certificate_domain` | `2808 / invalid_certificate_domain `User has not provided one or more invalid certificate domains. |
| `2809`   `wildcard_domains_not_allowed_in_multidomain_certificate` | `2809 / wildcard_domains_not_allowed_in_multidomain_certificate `Wildcards cannot be included in multi-domain certificates. |
| `2810`   `invalid_domains_in_multidomain_request` | `2810 / invalid_domains_in_multidomain_request `User has not provided one or more invalid domains in multi-domain request. |
| `2811`   `duplicate_domains_in_array` | `2811 / duplicate_domains_in_array `User has not provided one or more duplicate domains. |
| `2812`   `missing_certificate_domains` | `2812 / missing_certificate_domains `User has not provided any certificate domains. |
| `2813`   `cannot_replace_certificate_other_replacement_in_draft` | `2813 / cannot_replace_certificate_other_replacement_in_draft `Only issued certificates can be renewed or replaced by a new certificate. |
| `2814`   `permission_denied_on_original_certificate` | `2814 / permission_denied_on_original_certificate `User does not have the permissions to access certificate to renew. |
| `2815`   `original_certificate_not_active` | `2815 / original_certificate_not_active `Only issued certificates can be renewed or replaced by a new certificate. |
| `2816`   `cannot_find_original_certificate` | `2816 / cannot_find_original_certificate `Certificate to renew was not found. |
| `2817`   `certificate_limit_reached` | `2817 / certificate_limit_reached `Limit of certificates on user account was reached. |
| `2818`   `invalid_certificate_csr` | `2818 / invalid_certificate_csr `User has not provided a valid CSR value. |
| `28181`   `invalid_certificate_csr_for_non_wildcard` | `28181 / invalid_certificate_csr_for_non_wildcard `You provided a CSR where the common name is a wildcard, but your certificate is not a wildcard. This will not work. It is recommended to leave the CSR common name completely empty, it is deprecated anyway. |
| `28182`   `invalid_certificate_csr_for_wildcard` | `28182 / invalid_certificate_csr_for_wildcard `You provided a CSR where the common name is not a wildcard, but your certificate is a wildcard. This will not work. It is recommended to leave the CSR common name completely empty, it is deprecated anyway. |
| `2819`   `missing_certificate_csr` | `2819 / missing_certificate_csr `User has not provided a CSR value. |
| `2820`   `internal_error_failed_processing_csr` | `2820 / internal_error_failed_processing_csr `Internal error processing CSR. Please contact support if this error occurs. |
| `2821`   `internal_error_failed_creating_certificate` | `2821 / internal_error_failed_creating_certificate `Internal error generating certificate. Please contact support if this error occurs. |
| `2836`   `csr_cn_is_invalid` | `2836 / csr_cn_is_invalid ` The CN (= common name) in the CSR has an invalid value. Most probably it is not a valid internet address (domain or IP without protocol). Valid examples: `example.com`, `127.0.0.1`.                                           Please note that the CSRs' CN (common name) should be exactly the first of your `certificate_domains` parameter. It is recommended to use a fresh, unique and correct CSR for all certificates. |
| `2839`   `duplicate_certificates_found` | `2839 / duplicate_certificates_found `Domain can no longer be protected using Free Plan, upgrade to Basic Plan required. |
| `2841`   `certificate_creation_locked_unpaid_invoices` | `2841 / certificate_creation_locked_unpaid_invoices `Your account has been temporarily suspended due to unpaid invoices. Please pay your open invoices in order to unlock this endpoint. |
| `2880`   `invalid_san` | `2880 / invalid_san `Your SAN is being rejected. Most probably you have too many subject alternative names for your certificate or they have too many characters overall. |



**Errors - Verify Domains:**



| Error Code / Type | Description |
| --- | --- |
| `2822`   `failed_showing_certificate` | `2822 / failed_showing_certificate `The requested certificate could not be retrieved. |
| `2823`   `failed_validating_certificate` | `2823 / failed_validating_certificate `Domain verification failed and must be retried.   Possible reasons for this are:                                          * You are using a [restricted TLD](https://help.zerossl.com/hc/en-us/articles/360060119833-Restricted-Countries) * Your domain name is too long (~ 62 characters maximum) * Your custom CSR is using a key which is believed to be compromised Please also make sure you know about [common verification problems](https://help.zerossl.com/hc/en-us/articles/360058294194--I-have-troubles-during-certificate-verification). |
| `2824`   `missing_validation_emails` | `2824 / missing_validation_emails `User has not provided a validation email for each domain in certificate. |
| `2825`   `missing_validation_email` | `2825 / missing_validation_email `User has not provided a validation email for each domain in certificate. |
| `2826`   `internal_error_while_valdating_domain_control` | `2826 / internal_error_while_valdating_domain_control `Internal error verifying domains. Please contact support if this error occurs. |
| `2827`   `invalid_validation_method` | `2827 / invalid_validation_method `User has provided an in invalid domain verification method. |
| `2828`   `missing_validation_method` | `2828 / missing_validation_method `User has not provided a domain verification method. |
| `2829`   `incorrect_certificate_validation_type` | `2829 / incorrect_certificate_validation_type `User has provided an in invalid domain verification method or value. |
| `2830`   `certificate_not_eligible` | `2830 / certificate_not_eligible `The given certificate is not eligible for domain verification. |
| `2831`   `certificate_not_ready_to_validate` | `2831 / certificate_not_ready_to_validate `The given certificate is not ready for domain verification. |
| `2840`   `invalid_caa_records_detected` | `2840 / invalid_caa_records_detected `Invalid CAA records detected for some domains. Array of affected domains can be found in `details` object. [Learn more](/hc/en-us) about CAA records. |
| `2841`   `caa_record_check_failed` | `2841 / caa_record_check_failed`An internal error occurred checking your CAA records. If the problem persists please contact our support team ([support@zerossl.com](mailto:support@zerossl.com)). |
| `2842`   `replacement_needs_same_common_name` | `2842 / replacement_needs_same_common_name`A replacement certificate needs the same common name as its replacement. |
| `2843`   `ipv6_is_not_yet_supported` | `2843 / ipv6_is_not_yet_supported`We are working on providing IPv6 certificates. The feature is not yet available. |
| `2874`   `certificate_restricted_top_level_domain` | `2874 / certificate_restricted_top_level_domain `We are not able to issue certificates for this Top-Level-Domain at the moment. [Learn more](https://help.zerossl.com/hc/en-us/articles/360060119833-Restricted-Countries). |
| `2875`   `certificate_premium_not_allowed` | `2875 /certificate_premium_not_allowed `You are not allowed to issue premium certificates, most probably due to unpaid invoices or upgrades / downgrades. In case you think this is a mistake, please contact the ZeroSSL support team. |
| `2877`   `certificate_unsupported_top_level_domain` | `2877 /certificate_unsupported_top_level_domain`Certain TLDs are reserved for special purposes and we are not allowed to issue certificates for those. Those TLDs include `.local`, `.localhost`, `.example`, `.invalid` and `.test` as well as some others. You think there is a mistake on our side and issuing certs for this top level domain should be allowed? Please contact our support team and describe the issue! |



**Errors - Download Certificate:**



| Error Code / Type | Description |
| --- | --- |
| `2832`   `certificate_not_issued` | `2832 / certificate_not_issued `The given certificate has not been issued yet. |
| `2860`   `certificate_not_downloadable` | `2860 / certificate_not_downloadable `The certificate can currently not be downloaded. |



**Errors - Revoke Certificate:**



| Error Code / Type | Description |
| --- | --- |
| `2906`   `revocation_failed` | `2906 / revocation_failed `The certificate can not be revoked currently, please try again later.                                         If the problem persists - especially in urgent cases like key compromise - please contact our support team ([support@zerossl.com](mailto:support@zerossl.com)). |
| `2907`   `certificate_not_in_revocable_state` | `2907 / certificate_not_in_revocable_state `The certificate is not in a revocable state. Either the state has transitioned in the background,                                         you are trying to revoke a certificate which can not be revoked due to its status or some process is going on in the background.                                         If you think this is a mistake at our side please contact our support team ([support@zerossl.com](mailto:support@zerossl.com)). |
| `2908`   `certificate_revocation_temporarily_blocked` | `2908 / certificate_revocation_temporarily_blocked` Due customer protection mechanisms, your certificate can not be revoked at the moment. **Try again some hours later**.                                         We temporarily disable revocation functionality, if high numbers of certificates are revoked. This was implemented as a preventive measure                                         to limit possible loss in case of whatever related incident. Help and further information: ([support@zerossl.com](mailto:support@zerossl.com)). |
| `2909`   `certificate_not_revocable_being_issued` | `2909 / certificate_not_revocable_being_issued` The certificate can not be revoked / cancelled because it is currently                                     being issued. If this was a mistake, you may revoke it after issuance (most probably in 1-2 minutes). |
| `2910`   `certificate_not_revocable_already_replaced` | `2910 / certificate_not_revocable_already_replaced` The certificate has already been replaced by a new one. Does not apply for certificates                                     where you have used the standard "renew" functionality of ZeroSSL, can only happen for special cases. |



**Errors - Cancel Certificate:**



| Error Code / Type | Description |
| --- | --- |
| `2833`   `certificate_cannot_be_cancelled` | `2833 / certificate_cannot_be_cancelled `The given certificate cannot be cancelled due to its status. |
| `2834`   `failed_cancelling_certificate` | `2834 / failed_cancelling_certificate `Internal error cancelling certificate. Try again or contact support. |



**Errors - Resend Verification:**



| Error Code / Type | Description |
| --- | --- |
| `2837`   `failed_resending_email` | `2837 / failed_resending_email `Internal error resending verification email. Try again or contact support. |



**Errors - Get Verification Status:**



| Error Code / Type | Description |
| --- | --- |
| `2838`   `failed_getting_validation_status` | `2838 / failed_getting_validation_status `Error retrieving domain verification status. Try again and make sure Email Verification is selected. |



**Errors - Email verification:**



| Error Code / Type | Description |
| --- | --- |
| `2950`   `user_email_already_verified` | `2950 / user_email_already_verified `This email has already been verified. If this is your email, and you think this is a mistake, please contact our support team. |
| `2951`   `user_email_verify_try_later` | `2951 / user_email_verify_try_later `There are too many email verification requests at the moment and a maximum limit has been hit. Please try again later. |
| `2952`   `verification_email_missing` | `2952 / verification_email_missing `The email you want to verify is missing in the request. |
| `2953`   `verification_email_missmatch` | `2953 / verification_email_missmatch `The verification emails do not match. |
| `2954`   `verification_token_missing` | `2954 / verification_token_missing `The verification token is missing in your email verification attempt. |
| `2955`   `verification_token_invalid` | `2955 / verification_token_invalid `The email verification token is invalid. |
| `2956`   `verification_token_expired` | `2956 / verification_token_expired `The verification token is expired. Create a new token and finish the verification in time in order to resolve the issue. |
| `2957`   `missing_email_in_email_change_request` | `2955 / missing_email_in_email_change_request `The email is missing in the email change request. |
| `2958`   `invalid_email_in_email_change_request` | `2958 / invalid_email_in_email_change_request `The email you have submitted in the email change request is invalid. |
| `2987`   `email_already_exists` | `2958 / email_already_exists `That email is already registered in our system. An email must be unique in our system. The email must be unused also in our ACME service. If you think there is an issue in that regard, please contact our support team ([support@zerossl.com](mailto:support@zerossl.com)). |
| `2988`   `new_email_matches_old_email` | `2988 / new_email_matches_old_email `Your new email seems to match or old email. If you want to verify your email you are calling the wrong endpoint. |
| `2993`   `failed_to_send_verification_email` | `2993 / failed_to_send_verification_email `Due to an internal error we have not been able to send the verification email. Please try again later or contact us if you need further assistance. |
