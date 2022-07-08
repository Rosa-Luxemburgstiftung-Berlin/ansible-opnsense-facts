[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)
[![lint](https://github.com/Rosa-Luxemburgstiftung-Berlin/ansible-opnsense-facts/actions/workflows/lint.yml/badge.svg)](https://github.com/Rosa-Luxemburgstiftung-Berlin/ansible-opnsense-facts/actions?query=workflow%3Aansible-lint)


# ansible-opnsense-facts
gather ansible facts for opnsense

will provide you with some local facts per package and a firmware changelog list:

```json
"ansible_local": {
            "opnsense": {
                "ansible_opnsense_facts_version": "0.1",
                "core": {
                    "product_abi": "21.7",
                    "product_arch": "amd64",
                    "product_copyright_owner": "Deciso B.V.",
                    "product_copyright_url": "https://www.deciso.com/",
                    "product_copyright_years": "2014-2021",
                    "product_email": "project@opnsense.org",
                    "product_flavour": "OpenSSL",
                    "product_hash": "98e6d76d6",
                    "product_id": "opnsense",
                    "product_name": "OPNsense",
                    "product_nickname": "Noble Nightingale",
                    "product_series": "21.7",
                    "product_version": "21.7.3_1",
                    "product_website": "https://opnsense.org/"
                },
                "dyndns": {
                    "product_abi": "21.7",
                    "product_arch": "amd64",
                    "product_email": "franco@opnsense.org",
                    "product_flavour": "OpenSSL",
                    "product_hash": "19131fc6b",
                    "product_id": "os-dyndns",
                    "product_name": "dyndns",
                    "product_version": "1.24_2",
                    "product_website": "https://opnsense.org/"
                },
                "hw-probe": {
                    "product_abi": "21.7",
                    "product_arch": "amd64",
                    "product_email": "m.muenz@gmail.com",
                    "product_flavour": "OpenSSL",
                    "product_hash": "728fbcde4",
                    "product_id": "os-hw-probe",
                    "product_name": "hw-probe",
                    "product_version": "1.0_1",
                    "product_website": "https://opnsense.org/"
                },
                "lldpd": {
                    "product_abi": "21.7",
                    "product_arch": "amd64",
                    "product_email": "m.muenz@gmail.com",
                    "product_flavour": "OpenSSL",
                    "product_hash": "728fbcde4",
                    "product_id": "os-lldpd",
                    "product_name": "lldpd",
                    "product_version": "1.1_1",
                    "product_website": "https://opnsense.org/"
                },
		# ...
		"firmware_changelog": [
                    {
                        "date": "January 02, 2015",
                        "series": "15.1",
                        "version": "15.1"
                    },
                    {
                        "date": "January 12, 2015",
                        "series": "15.1",
                        "version": "15.1.1"
                    },
		    # ...
		    {
                        "date": "June 23, 2022",
                        "series": "22.1",
                        "version": "22.1.9"
                    },
                    {
                        "date": "July 07, 2022",
                        "series": "22.1",
                        "version": "22.1.10"
                    }
                ],
...
```
So for example you can use `ansible_local.opnsense.core.product_series` to detect the opnsense release version.
