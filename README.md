# ReconHunter 🕵️‍♂️

ReconHunter is a comprehensive bash script designed for bug bounty hunters and penetration testers to automate reconnaissance of a target domain.

This tool aggregates subdomains, performs DNS resolution, probes for HTTP services, collects archived URLs, discovers URL parameters, performs optional directory fuzzing, and scans for known vulnerabilities using Nuclei.

---

## 📦 Features

- Subdomain enumeration using:
  - `assetfinder`
  - `subfinder`
  - `findomain`
  - `crt.sh` scraping
  - `amass` (passive & active)

- DNS resolution using `dnsx`

- HTTP probing using `httpx-toolkit`

- Archive data collection via `gau` and `waybackurls`

- Parameter fuzzing using `arjun`

- (Optional) Directory bruteforcing using `ffuf`

- Vulnerability scanning using `nuclei`

---

## 🛠 Requirements

Ensure the following tools are installed:

```bash
sudo apt install -y jq figlet
go install github.com/tomnomnom/assetfinder@latest
go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install github.com/OWASP/Amass/v3/...@latest
go install github.com/projectdiscovery/dnsx/cmd/dnsx@latest
go install github.com/projectdiscovery/httpx/cmd/httpx@latest
go install github.com/lc/gau@latest
go install github.com/tomnomnom/waybackurls@latest
go install github.com/s0md3v/Arjun@latest
go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest
go install github.com/ffuf/ffuf@latest
```

Also ensure `$GOPATH/bin` is added to your `$PATH`.

---

## 🚀 Usage

```bash
chmod +x recon.sh
recon example.com
```

- Replace `example.com` with the target domain.
- All output will be saved in a directory named `recon_example.com`.
- *Recommended* : Add the executable file in /usr/local/bin to make the file executable globally.
---

## 📂 Output Structure

```
recon_example.com/
├── subs_assetfinder.txt
├── subs_subfinder.txt
├── subs_findomain.txt
├── subs_crtsh.txt
├── subs_amasspassive.txt
├── subs_amassactive.txt
├── all_subdomains.txt
├── resolved.txt
├── alive_http.txt
├── urls_gau.txt
├── urls_wayback.txt
├── all_urls.txt
├── arjun_params.txt
├── ffuf_<subdomain>.json
├── nuclei_output.txt
├── nuclei_urls.txt
```

---

## ⚠️ Notes

- Ensure rate limits are respected to avoid blocking.
- Wordlist for ffuf should exist at:

```bash
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

- Directory bruteforcing is optional and can be commented/uncommented as needed.
- Use only on domains you have explicit permission to test.

---

## 📝 Authors

This tool is developed by the team of two people :-
- [Mansi Singh](https://github.com/mansi-1204)
- [Lakshay Bhatnagar](https://github.com/lakshay-bhatnagar)
---

## 📃 License

This tool is provided for educational purposes only. The authors take no responsibility for misuse. Always ensure you have permission before running this script on any domain.

---

Happy Hunting! 🕵️‍♀️
