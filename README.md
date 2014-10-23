| | ECMA-402<br><sub><sup>Native</sup></sub> | Globalize<br><sub><sup>[jquery/globalize][]</sup></sub> |
| --- | --- | --- |
| **Functionality** | | |
| &nbsp; | | |
| Date Format<br><sub><sup>`new Date()` ⟹ Oct 23, 2014, 9:00:00 AM</sup></sub> | :heavy_check_mark: | :heavy_check_mark: |
| Date Parse<br><sub><sup>Oct 23, 2014, 9:00:00 AM ⟹ `new Date()`</sup></sub> | | :heavy_check_mark: |
| Relative Time Format<br><sub><sup>`new Date()` ⟺ last month</sup></sub> | | |
| &nbsp; | | |
| Number Format<br><sub><sup>`12734.89` ⟹ 12,734.89</sup></sub> | :heavy_check_mark: | :heavy_check_mark: |
| Number Parse<br><sub><sup>12,734.89 ⟹ `12734.89`</sup></sub> | | :heavy_check_mark: |
| &nbsp; | | |
| Currency Format<br><sub><sup>`{EUR: 1000.00}` ⟹ €1,000.00</sup></sub> | :heavy_check_mark: | |
| Currency Parse<br><sub><sup>€1,000.00 ⟹ `{EUR: 1000.00}`</sup></sub> | | |
| &nbsp; | | |
| Plural<br><sub><sup>`3` ⟹ `few`</sup></sub> | | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[santhoshtr/cldrpluralruleparser][]</sup></sub> |
| Format Message<br><sub><sup>`You have {count, plural, one {1 item} other {# items}}` ⟹ You have 5 items</sup></sub> | | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[slexaxton/messageformat.js][]</sup></sub> |
| &nbsp; | | |
| Collation | | |
| &nbsp; | | |
| Postal Codes | | |
| Phone Codes | | |
| &nbsp; | | |
| **I18n data** | Compiled | [CLDR][] >= 25 |
| &nbsp; | | |
| **Template integration** | | |
| &nbsp; | | |
| Dust | | |
| Handlebars | | |
| React | | |
| &nbsp; | | |
| **Support** | | |
| &nbsp; | | |
| Environments | :heavy_minus_sign: | AMD<br>CommonJS |
| Node.js | >= 0.12<br><sub><sup>`en` only by default</sup></sub> | :heavy_check_mark: |
| Browser | Chrome: 24<br>Firefox: 29<br>Safari: N/A<br>Opera: 15<br>IE: 11<br><sub><sup>Reference MDN.</sup></sub> | Chrome: <sub><sup>(Current - 1) or Current</sup></sub><br>Firefox: <sub><sup>(Current - 1) or Current</sup></sub><br>Safari: 5.1+<br>Opera: 12.1x, <sub><sup>(Current - 1) or Current</sup></sub><br>IE: 8 <sub><sup>(needs ES5 polyfill)</sup></sub>, IE9+ |
| Mobile | | iOS: 6.1+<br>Android: 2.3, 4.0+ |

[andyearnshaw/intl.js]: https://github.com/andyearnshaw/Intl.js/
[CLDR]: http://cldr.unicode.org/index/cldr-spec/json
[ibm-js/ecma402]: https://github.com/ibm-js/ecma402
[jquery/globalize]: https://github.com/jquery/globalize/
[santhoshtr/cldrpluralruleparser]: https://github.com/santhoshtr/CLDRPluralRuleParser/
[slexaxton/messageformat.js]: https://github.com/SlexAxton/messageformat.js/
