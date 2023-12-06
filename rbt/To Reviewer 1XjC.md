Thank you for your useful comments and suggestions on our manuscript. They are very valuable and helpful for revising and improving the paper. We have studied the comments carefully and made revision accordingly. The detailed responds are listed as follows:

**【Q1】** Does generating fingerprint information for mobile devices pose potential security and privacy issues?

**【A1】** Generating fingerprints for mobile devices using Magnifier does not inherently pose security and privacy issues, particularly in terms of user privacy disclosure. This assertion is supported by the following reasons:

1. Magnifier exclusively focuses on domain features within network traffic during fingerprint construction. Device-specific details, including serial numbers, MAC addresses, or IP addresses, are intentionally excluded from the fingerprint generation process. This deliberate omission of sensitive information ensures that even if the fingerprints were to be made publicly available, there would be no risk of exposing personally identifiable data or any device-specific identifiers.
2. On the other hand, the publicly available dataset (NetCess2023) will not lead to privacy disclosure neither. Because most of the communication traffic is encrypted by TLS/SSL or private encryption protocol over HTTP. That means the payload between devices and servers is encrypted and invisible. The domain features Magnifier extracted are mainly from the headers of the encrypted traffic, which will not lead to the exposure of the communication detail.

​	We appreciate the guidance provided regarding the discourse on potential security and privacy concerns. Subsequently, we have incorporated this discussion into our paper.

