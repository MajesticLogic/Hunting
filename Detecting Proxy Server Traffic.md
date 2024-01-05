
# Detecting Proxy Server Traffic in Wireshark

## 1. Apply Filters

### Search for HTTP Traffic:

Filter: http
### Known Proxy IP Address:

Filter: ip.addr == <proxy_ip_address>
(Replace <proxy_ip_address> with the actual IP address)

### Proxy Headers Present:

Filter: (http.proxy_connect_port || http.proxy_connect_host || http.proxy_authentication || http.proxy_authorization)

If traffic is present, include the following to determine the proxy server:

&& tls.handshake.type == 2
(http2.headers.proxy_authentication || http2.headers.proxy_authorization)

## 2. Examine Packet Details

Double-click individual packets to inspect their contents.

Inspect fields:
HTTP headers: Look for Via, Proxy-Connection, X-Forwarded-For, or other proxy-related headers.
Source IP address: Likely the proxy server.
Source port: Configured port for HTTP traffic to be sent to within the network.
Verify traffic routing: Determine which traffic is routed through the proxy server and which is not.
