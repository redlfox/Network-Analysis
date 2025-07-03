# Network-Analysis

## HTTP/2

### FOSS
A great tool to inspect HTTP/2 frames of real-world connections is
[Wireshark](https://www.wireshark.org).

https://github.com/ProxymanApp/proxyman-windows-linux https://proxyman.com/download

### Paid

#### Fiddler
- [官方文档](https://www.telerik.com/fiddler)

#### Charles
- [官方文档](https://www.charlesproxy.com)

### HTTPS

To see the traffic in Wireshark, some clients can be configured to dump an
`SSLKEYLOGFILE` that Wireshark
[can use](https://wiki.wireshark.org/TLS#Using_the_.28Pre.29-Master-Secret)
to decrypt the traffic.

* [neykov/extract-tls-secrets - Decrypt HTTPS/TLS connections on the fly with Wireshark - 支持TLSv1.3](https://github.com/neykov/extract-tls-secrets/)

[mitmproxy](https://mitmproxy.org) is a nice tool to inspect HTTPS traffic,
and supports dumping the SSLKEYLOGFILE. However, since it 'understands' HTTP,
it might not be 'transparent' enough: especially when diagnosing protocol
errors, adding this proxy might interfere with reproducing the problem.

[sslsplit](https://www.roe.ch/SSLsplit) should be able to dump an intercepted
stream to a pcap file directly, but currently its `https` proxy mode does not
bridge the ALPN negotiation, so connections will downgrade to HTTP/1.1. This
might be fixed when they [add HTTP/2 support](https://github.com/droe/sslsplit/issues/218)

[alpnpass](https://github.com/VerSprite/alpnpass) can be used to intercept
the plaintext traffic in Wireshark: you can set its `InterceptorPort` to
the same value as the `ReturnPort` and then sniff the loopback interface and
filter on that port.

tcpdump

https://github.com/kasketis/netfox
