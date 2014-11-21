## Number Format

`12734.89` ⟹ 12,734.89

| | ECMA-402<br><sub><sup>Native</sup></sub> | Globalize<br><sub><sup>[jquery/globalize][]</sup></sub> | FormatJS<br><sub><sup>[formatjs.io][]</sup></sub> | iLib |
| --- | --- | --- | --- | --- |
| Grouping separator<br><sub><sup>1,00,000.00</sup></sub>| :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Numeric numbering systems<br><sub><sup>latin (0123...), arabic (٠١٢٣...), thai (๐๑๒๓...)</sup></sub> | :heavy_check_mark: | :soon: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Algorithmic numbering systems / RBNF<br><sub><sup>roman, gregorian</sup></sub> | :heavy_check_mark: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Scientific Notation | :heavy_check_mark: | :soon: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Max and Min Fraction Digits | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Rounding Modes | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Percentage<br><sub><sup>%23,4 (tr-TR)</sup></sub> | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| Currency<br><sub><sup>`{EUR: 1000.00}` ⟹ €1,000.00</sup></sub> | :heavy_check_mark: | :soon: | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |

**Grouping separator**

TBD

**Numeric numbering systems**

TBD

**Algorithmic numbering systems / RBNF**

TBD

**Scientific Notation**

TBD

**Max and Min Fraction Digits**

TBD

**Rounding Modes**

TBD

### Currency Format

`{EUR: 1000.00}` ⟹ €1,000.00

| | ECMA-402<br><sub><sup>Native</sup></sub> | iLib |
| --- | --- | --- |
| Common format (uses currency symbols) | TBD | :heavy_check_mark: |
| ISO format (using ISO code) | TBD | :heavy_check_mark: |
| Automatic Fraction Digits | TBD | :heavy_check_mark: |
| Localized Number Format | TBD | :heavy_check_mark: |

**Common format (uses currency symbols)**

TBD

**ISO format (using ISO code)**

TBD

**Automatic Fraction Digits**

TBD

**Localized Number Format**

TBD

[formatjs.io]: http://formatjs.io/
[jquery/globalize]: https://github.com/jquery/globalize/
