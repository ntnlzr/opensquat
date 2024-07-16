
# openSquat
![openSquat Logo](https://raw.githubusercontent.com/atenreiro/opensquat/master/screenshots/openSquat_logo.png)

## Table of Contents
- [What is openSquat](#what-is-opensquat)
- [Screenshot / Video Demo](#screenshot--video-demo)
- [Demo / Forks](#demo--forks)
- [How to Install](#how-to-install)
- [How to Update](#how-to-update)
- [Usage Examples](#usage-examples)
- [Automations & Integrations](#automations--integrations)
- [To Do / Roadmap](#to-do--roadmap)
- [Changelog](#changelog)
- [How to Contribute](#how-to-contribute)
- [Authors](#authors)
- [How to Help](#how-to-help)

## What is openSquat
openSquat is an open-source Intelligence (OSINT) security tool designed to identify **cyber squatting** threats to specific companies or domains, including:

- Phishing campaigns
- Domain squatting
- Typo squatting
- Bitsquatting
- IDN homograph attacks
- Doppelgänger domains
- Other brand/domain-related scams

### Key Features
- Automatic daily updates of newly registered domains
- Levenshtein distance calculation for word similarity
- Fetches active and known phishing domains (Phishing Database project)
- IDN homograph attack detection
- Integration with VirusTotal and Quad9 DNS service
- Adjustable confidence thresholds
- Output in various formats (txt, JSON, CSV)
- Integration with other threat intelligence tools and DNS sinkholes

## Screenshot / Video Demo
![openSquat Screenshot](https://raw.githubusercontent.com/atenreiro/opensquat/master/screenshots/openSquat.PNG)

Check the [40-second Demo Video](https://asciinema.org/a/361931) (v1.95).

## Demo / Forks
- [Phishy Domains](https://phishydomains.com): Simple web version of openSquat
- [openSquat Bot](https://telegram.me/opensquat_bot): Telegram bot
- [RapidAPI](https://rapidapi.com/atenreiro/api/opensquat1): Integrate your application with openSquat using REST API

**Note:** The forks do not contain all the openSquat features.

## How to Install
\`\`\`bash
git clone https://github.com/atenreiro/opensquat
pip install -r requirements.txt
\`\`\`
Make sure you have **Python 3.6+** and **pip3** in your environment.

## How to Update
> :warning: **When updating**: especially for a major release, re-run \`pip install\` to check for new dependencies.

To update your current version, run the following commands inside the openSquat directory:
\`\`\`bash
git pull
pip install -r requirements.txt
\`\`\`

## Usage Examples
Edit the \`keywords.txt\` with your customized keywords to hunt.

\`\`\`bash
# Lazy run with default options
python opensquat.py

# For all the options
python opensquat.py -h

# Search for generic terms used in phishing campaigns (can lead to false-positives)
python opensquat.py -k generic.txt

# With DNS validation (quad9)
python opensquat.py --dns

# Subdomain search
python opensquat.py --subdomains

# Check for domains with open ports 80/443
python opensquat.py --portcheck

# With Phishing validation (Phishing Database)
python opensquat.py --phishing phish_results.txt

# Save output as JSON
python opensquat.py -o example.json -t json

# Save output as CSV
python opensquat.py -o example.csv -t csv

# Conduct a certificate transparency (ct) hunt
python opensquat.py --ct

# Period search - registrations from the last month (default: day)
python opensquat.py -p month

# Tweak confidence level (0: very high, 1: high (default), 2: medium, 3: low, 4: very low)
python opensquat.py -c 2

# All validations options
python opensquat.py --phishing phishing_domains.txt --dns --ct --subdomains --portcheck
\`\`\`

## Automations & Integrations
You can set up openSquat to run automatically using a task scheduler (such as crontab for Linux) to generate a new list of results daily.

We update our feeds with a fresh new list of domains every day around 7:30 AM (UTC+0 / GMT+0).

\`\`\`bash
# Crontab example - run openSquat every day at 8 AM
# In this example, the results are saved to a JSON file format
0 8 * * * /home/john/opensquat/opensquat.py -k keywords.txt -o results.json -t json
\`\`\`
You can use this output file to feed your SIEM, SOAR, or other tools that support importing from TXT/JSON/CSV formats.

Alternatively, currently in a **Beta preview**, you can integrate using REST APIs with [RapidAPI](https://rapidapi.com/atenreiro/api/opensquat1).

Do you have an integration idea or would like to share an integration you developed with our community? Open a GitHub issue or send me an email.

## To Do / Roadmap
- ~~Integration with VirusTotal (VT) for subdomains validation~~
- Integration with VirusTotal (VT) for malware detection
- ~~Use certificate transparency~~
- ~~Homograph detection~~
- ~~Improve code quality from B to A grade (codacy)~~
- ~~PEP8 compliance~~
- AND logical condition for keywords search (e.g., google+login) - Thanks to Steff T.
- Enhanced documentation

## Changelog
Check the [CHANGELOG](https://github.com/atenreiro/opensquat/blob/master/CHANGELOG) file.

## How to Contribute
We welcome and encourage contributions from the community! If you're interested in helping improve openSquat, here are a variety of ways you can contribute:

- **Reporting Bugs:** To report bugs, open an issue on our [GitHub issues page](https://github.com/atenreiro/opensquat/issues). You should include as much detail as possible to help us understand the problem and what the ideal solution would be.
- **Feature Requests:** To request a new feature, create a "new issue" and describe the feature and potential use cases. You can upvote the "issue" and contribute to the discussions if something similar already exists.
- **Code Contributions:** To help advance openSquat with coding, you can look at open issues or feature requests. Be sure to fork the repository, make your changes, and submit a pull request.
- **Documentation:** You can help improve documentation by fixing typos, clarifying instructions, or adding new, valuable sections.

Thank you for your interest in contributing to openSquat!

## Authors
Project founder:
- Andre Tenreiro [(LinkedIn)](https://www.linkedin.com/in/andretenreiro/)
- andre+nospam@opensquat.com - remove the "nospam" - [PGP Key](https://mail-api.proton.me/pks/lookup?op=get&search=andre@opensquat.com)

Contributors:
- Please check the contributors page on GitHub.

## How to Help
You can help this project in many ways:
- Providing your time and coding skills to enhance the project
- Building a decent but simple [project webpage](https://opensquat.com)
- Providing access to OSINT feeds
- Opening new issues with suggestions, ideas, bug reports, or feature requests
- Spreading this project within your network
- Sharing your story about how you have been using openSquat and its impact
