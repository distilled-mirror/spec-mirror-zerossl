# Documentation ACME

<div class="split-heading">
  <h2>Explore ACME Documentation</h2>
  <span class="method"></span>
</div>

- [Generate EAB credentials](/acme/generate-eab-credentials)
- [Error Codes](/acme/error-codes)

ACME stands for Automatic Certificate Management Environment and provides an easy-to-use method of automating interactions between a certificate authority (like ZeroSSL) and a web server. There are many ACME clients out there, all free to use and created to simplify use of the ACME protocol.



While ZeroSSL works with any type of ACME client that supports EAB authorization, there is a number of ACME clients that we formed explicit partnerships with in order to enhance your user experience even more. For example, choosing one of our partner ACME clients will allow you to keep track of any automatically created SSL certificates right from your ZeroSSL dashboard.



**Unlimited Certificates, Free of Charge:**



By using ZeroSSL's ACME feature, you will be able to generate an unlimited amount of 90-day SSL certificates at no charge, also supporting multi-domain certificates and wildcards. Each certificate you create will be stored in your ZeroSSL account.



To see a list of ZeroSSL partner ACME clients, follow this link: [ZeroSSL Partner ACME Clients](https://zerossl.com/features/acme#clients)


::: info Please Note

Configure your scripts and clients to use our free of charge ACME API in a meaningful way. We want to provide a reliable and stable service to all our customers, malicious users can be limited or even blocked. Also, the **maximum number of labels in subdomains is six**, excluding the public suffix (more information: [https://publicsuffix.org/](https://publicsuffix.org/), but including e.g. a wildcard asterisk character). If you need a certificate with more labels, which is very rarely required in healthy setups, you have to use the ZeroSSL API.
:::

## ACME Server URL



In order to use the ACME protocol with ZeroSSL, this is the server URL to connect to:


```
https://acme.zerossl.com/v2/DV90
```



## EAB Credentials



Unlike for the ZeroSSL API for which you are using a ZeroSSL access key, for using our ACME service you have to create and use EAB (External Account Binding) credentials within your ZeroSSL dashboard.
To generate EAB credentials click "Generate" at the bottom of the Developer section of your ZeroSSL management console or use the ACME REST API.(/documentation/docs/acme/generate-eab-credentials).



::: warning Please Note
EAB credentials are not stored in your account, please make sure to note them somewhere. Each click on "Generate" will create a new set of credentials. Even if you create multiple credentials, all of them will remain functional.
:::


::: warning Please Note
Since March 2022 all EAB credentials are **reusable**. One set of EAB credentials should be enough for most use cases. EAB credentials are limited to a maximum per user/per day.
:::
