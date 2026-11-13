# EasyList Germany

EasyList Germany is a supplementary filter list for German-language websites. It removes ads and ad leftovers that the main [EasyList](https://github.com/easylist/easylist) does not cover and is designed to be used **together with EasyList**, not as a replacement for it.

The list uses Adblock Plus filter syntax and works with Adblock Plus, AdBlock, uBlock Origin, AdGuard and other compatible content blockers.

## Subscribe

Most ad blockers already offer EasyList Germany as a built-in or recommended list for German-speaking users. To add it manually, use:

```
https://easylist.to/easylistgermany/easylistgermany.txt
```

More lists and subscription links are available at [easylist.to](https://easylist.to/).

## Reporting issues

Found an ad that isn't blocked or something that is blocked by mistake (a false positive)? Please let us know:

- **GitHub issues:** [open an issue](https://github.com/easylist/easylistgermany/issues) (preferred)
- **Email:** easylist.germany@gmail.com

> **Note:** EasyList Germany does not handle anti-adblock messages ("Please disable your ad blocker" walls or overlays). If a site detects or blocks your ad blocker, please report it to the developer of the ad blocking extension you use.

Reports in German or English are welcome. To help us reproduce the problem, please include:

1. The full URL of the affected page
2. A description of what's wrong (unblocked ad, broken page, missing content)
3. Your browser and ad blocker, including versions
4. Which filter lists you have enabled
5. A screenshot, if helpful

## How the list is built

Every push to `master` triggers the **Build and Deploy** workflow. It renders `easylistgermany.template` into a single `easylistgermany.txt` using `flrender` from [python-abp](https://github.com/adblockplus/python-abp), adds the source commit hash to the list header, and publishes the result to the `gh-pages` branch.

To build the list locally:

```bash
pip install git+https://github.com/adblockplus/python-abp.git
flrender -i easylistgermany=. easylistgermany.template easylistgermany.txt
```

A separate **Dead Domains Check** workflow runs every Monday. It uses [AdGuard's Dead Domains Linter](https://github.com/AdguardTeam/DeadDomainsLinter) to find rules that target domains that no longer exist then opens an issue and a pull request to remove them. Low-traffic sites are occasionally flagged by mistake, so these pull requests are reviewed before merging.

## Licence

EasyList Germany is dual-licensed under the GNU General Public License (version 3 or later) and the Creative Commons Attribution-ShareAlike 3.0 Unported licence. See the [EasyList licence page](https://easylist.to/pages/licence.html) for details.

`FOP.py` is licensed separately under the GNU General Public License v3 or later.
