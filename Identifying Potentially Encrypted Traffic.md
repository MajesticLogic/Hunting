 **# Identifying Potentially Encrypted Traffic Using Wireshark**

**While Wireshark can't directly decrypt non-standard encryption, here are methods to identify it:**

**## 1. Analyze Packet Size and Patterns:**

- **Examine packet sizes:** Encrypted traffic often has consistent, equal-sized packets due to padding and encryption headers. Look for patterns in packet lengths.
- **Check for randomness:** Encrypted data often appears random or unintelligible. Use Wireshark's "Follow TCP Stream" or "Follow UDP Stream" to examine payloads.

**## 2. Inspect Port Numbers:**

- **Identify unusual ports:** Non-standard encryption might use ports not typically associated with encrypted protocols. Check for traffic on ports not used for common services like HTTPS (443) or SSH (22).

**## 3. Examine Protocol Distribution:**

- **Look for unknown protocols:** Wireshark might label traffic as "TCP" or "UDP" without a specific protocol name. This could indicate non-standard encryption.

**## 4. Filter for Potential Indicators:**

- **Apply filters:** Use Wireshark's filters to focus on specific traffic patterns or characteristics that might suggest encryption:
    - `tcp.port != 443 and tcp.port != 22` (exclude common encrypted protocols)
    - `tcp.len == 1400` (find packets with fixed size)

**## 5. Investigate Protocol Behavior:**

- **Analyze protocol handshakes:** Encrypted protocols often have distinctive handshake patterns. Learn to recognize common handshakes and look for anomalies.
- **Examine payload patterns:** Even without decryption, patterns in payloads might reveal encryption usage.

**## 6. Employ Heuristic Analysis:**

- **Apply statistical analysis:** Tools like Wireshark's "Statistics" menu can help identify patterns in packet sizes, frequencies, and intervals that might suggest encryption.

**## 7. Use External Tools and Resources:**

- **Seek expert knowledge:** Consult online resources or security professionals to identify non-standard encryption methods and their characteristics.

**## Remember:**

- **Limits of Wireshark:** It cannot definitively identify all non-standard encryption.
- **Contextual analysis:** Combine these techniques with network knowledge and context for better identification.
- **Ethical considerations:** Respect privacy and legal restrictions when capturing and analyzing traffic.
