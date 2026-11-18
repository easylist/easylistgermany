## Repository Structure

The published list is built from the source files in the `easylistgermany` folder. Each file holds one type of rule:

| File | Contents |
|------|----------|
| `easylistgermany_general_block.txt` | Generic blocking rules |
| `easylistgermany_general_hide.txt` | Generic element hiding rules |
| `easylistgermany_adservers.txt` | Third-party ad servers |
| `easylistgermany_thirdparty.txt` | Third-party ad resources that aren't full ad servers |
| `easylistgermany_specific_block.txt` | Site-specific blocking rules |
| `easylistgermany_specific_hide.txt` | Site-specific element hiding rules |
| `easylistgermany_allowlist.txt` | Exception rules that fix site breakage |
| `easylistgermany_allowlist_general_hide.txt` | Exceptions to generic hiding rules |
| `easylistgermany_allowlist_dimensions.txt` | Exceptions for dimension-based rules |

Rules that only target popups go in the `_popup` version of the matching file. Popup files exist for `adservers`, `allowlist`, `general_block`, `specific_block` and `thirdparty`, for example `easylistgermany_specific_block_popup.txt`.

`easylistgermany.template` in the root directory defines the list header and the order in which the source files are combined into the published `easylistgermany.txt`.

## Commit Recommendations

After confirming that the rule you want to add works correctly and fits the scope described in the [README](README.md), make sure to do the following:

**Match the rule to the correct file:**
Choose the file that fits the rule's type, using the table above.
For example, an ad hidden by the rule `example.de##.ad-12345` belongs in `easylistgermany/easylistgermany_specific_hide.txt`.

**Order the rule in the file:**
Rules may be grouped using comments: `! <comment>`. If so, place the rule under the correct group.
Then insert the rule in the correct position following ASCII ascending sorting.

**Sort with FOP:**
We recommend [FOP.rs](https://github.com/ryanbr/fop-rs), a faster Rust port of FOP that works as a drop-in replacement for `FOP.py`:

```bash
npm install -g fop-cli
```

Run it from the repository root:

```bash
fop        # sort, then prompt for a commit message
fop -n     # sort only, no commit
```

`FOP.py` in the root directory still works (`python3 FOP.py`) if you'd rather not install anything.

## Commit Policy

EasyList Germany commit messages use three prefixes to indicate the type of a change:
- **A:** *Added* a new filter
- **M:** *Modified* the existing filter for a website, either to match a website's update or to clean up the list
- **P:** *Problem* fix for a website, such as removing existing filters or making them more specific

Follow the prefix with the URL of the affected page, for example `A: https://www.example.de/`. Both FOP versions check this format before committing.
