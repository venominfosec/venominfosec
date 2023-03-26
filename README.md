# Alex Poorman
Penetration Tester at NetSPI

- 🔭 I’m working on automating the penetration testing process for web application, external network, and AWS cloud tests
- 🌱 I’m learning how to be a more efficient penetration tester and advanced Python development

# Open Source Tools I've Created
## NetblockTool
Find netblocks owned by a company

https://github.com/NetSPI/NetblockTool

```
  _   _      _   _     _            _    _____           _
 | \ | | ___| |_| |__ | | ___   ___| | _|_   _|__   ___ | |
 |  \| |/ _ \ __| '_ \| |/ _ \ / __| |/ / | |/ _ \ / _ \| |
 | |\  |  __/ |_| |_) | | (_) | (__|   <  | | (_) | (_) | |
 |_| \_|\___|\__|_.__/|_|\___/ \___|_|\_\ |_|\___/ \___/|_|
```
**Overview:**
* Use NetblockTool to easily dump a unique list of IP addresses belonging to a company and its subsidiaries.
* All data gathering is passive. No traffic is ever sent to the target company.
* Sources include ARIN API, ARIN GUI search functionality, and Google dorking. Company subsidiaries are retrieved from SEC's public database.

**How it works:**
* A target company is provided
* Google dorking is used to find netblocks
* Traffic is sent that simulates a user searching ARIN's database for the company name
* All ARIN links are found, visited, and processed from the previous database query
* Duplicate networks are removed
* Each netblock is given a confidence score
* Netblocks are sorted by confidence score and written to a CSV

## AutoDirbuster
Automatically run and save Dirbuster scans for multiple IPs

https://github.com/NetSPI/AutoDirbuster

```
     ___         __        ____  _      __               __
    /   | __  __/ /_____  / __ \(_)____/ /_  __  _______/ /____  _____
   / /| |/ / / / __/ __ \/ / / / / ___/ __ \/ / / / ___/ __/ _ \/ ___/
  / ___ / /_/ / /_/ /_/ / /_/ / / /  / /_/ / /_/ (__  ) /_/  __/ /
 /_/  |_\__,_/\__/\____/_____/_/_/  /_.___/\__,_/____/\__/\___/_/
 ```
**Why?**

Ffuf is a great directory buster but running it against multiple IPs and ports is a very manual process with a lot of downtime between scans. This script attempts to automate that process and eliminates downtime between scans.

**How it works:**
* A list of targets is provided
* A TCP connect scan is done on the target port to test if it's open
* If the port open, HTTP and HTTPS requests are sent to determine if the service is HTTP-based and whether it requires TLS
* If the service is HTTP, a check is done to determine if a previous report file is in the same directory
  * Report files follow the format: `ffuf-report-{proto}_{target}_{port}'`
* ffuf is run using Python's `subprocess.Popen()`
* The next IP:port goes through the same process (TCP connect, HTTP service query, dirbust)

## SecretsChecker
Automatically check for secrets in files

https://github.com/venominfosec/SecretsChecker

![SecretsChecker](https://i.imgur.com/qXXqpXV.png)

**Overview:**
* Use SecretsChecker to files for hardcoded secrets
* Secrets are identified using regular expressions
* 45 different secret types currently supported
