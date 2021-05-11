# Output validation

Use structured mechanisms that automatically enforce the separation between data and code. These mechanisms may be able to provide the relevant quoting, encoding, and validation automatically, instead of relying on the developer to provide this capability at every point where output is generated. 

For mitigating the low-hanging fruit, the [Top 25 vulnerabilities](https://cwe.mitre.org/top25/archive/2020/2020_cwe_top25.html) can be used, except for any "Inclusion of functionality from untrusted control sphere" and "Missing authorisation". //Understand the context in which the data will be used and the encoding that will be expected. This is especially important when transmitting data between different components, or when generating outputs that can contain multiple encodings at the same time, such as web pages or multi-part mail messages. Study all expected communication protocols and data representations to determine the required encoding strategies.//

