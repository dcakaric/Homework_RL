# Homework_RL

## Z1000 changelog
The changelog contains references to our internal ticketing system. We use the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format.

### v7.3.0
March 2025

#### New features
* Added new API endpoint allowing users to download the original analyzed samples: [[ZON-5769](https://example.com.)]
    * `/api/v1/download_samples/`
* Added a new graphical dashboard showing statistical information about analyzed emails. [[ZON-5770](https://example.com.)]


#### Bug fixes
* **Security fix**: Fixed a security issue where analyzing PHP files would execute them, potentially leading to remote code execution (RCE) and unauthorized access. ([CVE-2024-4577](https://nvd.nist.gov/vuln/detail/CVE-2024-4577)) [
[ZON-5771](https://example.com.)]
* **Stability fix**: Resolved an issue where the system crashed when analyzing files larger than 13.37 GB. [[ZON-5772](https://example.com.)]#
