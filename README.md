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
So for example you can use `ansible_local.opnsense.core.product_series` to detect the opnsense release.
In order to get the full version without the revision, use `ansible_local.opnsense.core.product_version.split('_')[0].strip()`

Another interesting part of the facts is the `pkg_upgrade`part. See realted issues and PRs:
  * Rosa-Luxemburgstiftung-Berlin/ansible-opnsense-facts#3
  * Rosa-Luxemburgstiftung-Berlin/ansible-opnsense-update#6
  * Rosa-Luxemburgstiftung-Berlin/ansible-opnsense-update#17

```json
"pkg_upgrade": [
    {
      "api_version": "2",
      "connection": "ok",
      "downgrade_packages": [],
      "download_size": "",
      "last_check": "Wed Dec 11 08:59:54 UTC 2024",
      "needs_reboot": "0",
      "new_packages": [],
      "os_version": "FreeBSD 13.2-RELEASE-p7",
      "product_id": "opnsense",
      "product_target": "opnsense",
      "product_version": "23.7.12_5",
      "product_abi": "23.7",
      "reinstall_packages": [],
      "remove_packages": [],
      "repository": "ok",
      "upgrade_major_message": "<p>OPNsense 23.7 \"<em>Restless Roadrunner</em>\" has reached its end of life. As such it will not receive any more updates, but the upgrade to the new 24.1 series is seamless and can be performed right here from the web GUI.</p> <p> Another method is to import and reinstall using a new installation image, which will retain your settings using \"Import Configuration\", then reformat the disk and apply a clean system using either \"Install (UFS)\" or \"Install (ZFS)\".</p> <p>You can also upgrade via console / SSH by using option 12 from the menu by typing \"24.1\" when prompted.</p> <p>Make sure to read the migration notes and account for possible breaking changes.</p> <p>Please backup your configuration, preview the new version via live image or in a virtual machine. Create snapshots. If all else fails, report back <a href=\"https://forum.opnsense.org/\" target=\"_blank\">in the forums</a> for assistance.</p> ",
      "upgrade_major_version": "24.1",
      "upgrade_needs_reboot": "1",
      "upgrade_packages": [],
      "upgrade_sets": [
        {
          "name": "packages",
          "size": "754585088",
          "current_version": "",
          "new_version": "24.1",
          "repository": "OPNsense"
        },
        {
          "name": "kernel",
          "size": "32841852",
          "current_version": "23.7.10",
          "new_version": "24.1",
          "repository": "OPNsense"
        },
        {
          "name": "base",
          "size": "116680004",
          "current_version": "23.7.10",
          "new_version": "24.1",
          "repository": "OPNsense"
        }
      ]
    }
]
```
