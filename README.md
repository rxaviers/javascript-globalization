# JavaScript Globalization Overview

Overview page that shows what solutions exist for JavaScript globalization
(internationalization and localization). What is missing. What overlaps. Why
each library was created. What are their goals, strengths and weaknesses.

## Summary

### ECMA-402

The standard native implementation. It provides collation (string comparison),
number formatting, and date and time formatting. The API was developed by a
working group with members from Google, Microsoft, Mozilla (Norbert Lindenberg),
Amazon, and IBM.

Strengths
- Best performant on both speed and size. Speed, because it's native compiled
  code, which runs faster than interpreted JavaScript code from libraries. Size,
  because again it's native compiled code, which requires no extra JavaScript or
  resource loading (it relies on compiled i18n data) to be executed.

Weaknesses
- Limited browser support (it may NOT be supported by your target client).
- Lack of a resource loading mechanism (certain locale may NOT be available on
  your target client).

Links
- http://www.ecma-international.org/ecma-402/1.0/
- http://norbertlindenberg.com/2012/12/ecmascript-internationalization-api/index.html
- http://generatedcontent.org/post/59403168016/esintlapi (locale support)

### Cldrpluralruleparser

Standalone library created by Santhosh Thottingal that provides CLDR plural rule
parsing. Used by Wikimedia Foundation.

Strengths
- Based on CLDR data (largest and most extensive i18n repository).
- No bugs due to outdated i18n content (it has no hard coded i18n data).

Links:
- https://github.com/santhoshtr/CLDRPluralRuleParser/

### Globalize

A jQuery project, initially created to fullfil jQuery UI (datepicker and spinner
widgets). It provides number formatting and parsing, date and time formatting
and parsing, message formatting, and plural support.

The design goals are (a) to leverage the official CLDR JSON data, (b) allow
users to load as much or as little data as they need, (c) avoid duplicating data
if using multiple i18n libraries that leverage CLDR, and (d) run in browsers or
node.js.

Strengths
- Based on CLDR data (largest and most extensive i18n repository).
- No bugs due to outdated i18n content (it has no hard coded i18n data).
- Allow different locale instances running simultaneously.

Links:
- https://github.com/jquery/globalize/

### Google Closure i18n

Part of the larger Closure library, based on CLDR data. Provides number
formatting and parsing, date and time formatting and parsing, message
formatting (including plural and gender support), access to some of the CLDR
data (like currency symbols).

Strenghts
- Based on CLDR data (largest and most extensive i18n repository).

Weaknesses
- Supports only one locale at the time (default model, can be bypassed).

Links
- http://docs.closure-library.googlecode.com/git/namespace_goog_i18n.html

### Messageformat.js

Standalone library created by Alex Sexton that provides ICU MessageFormat
support, with built-in SelectFormat and pluggable PluralFormat.

Strengths
- Precompile formatter for faster/smaller runtime.

Links:
- https://github.com/SlexAxton/messageformat.js/

### FormatJS

FormatJS is a modular collection of JavaScript libraries for internationalization that are focused on formatting numbers, dates, and strings for displaying to people. It includes a set of core libraries that build on the JavaScript `Intl` built-ins and industry-wide i18n standards, _plus_ a set of integrations for common template and component libraries.

Strengths:
- Integrates with template/component libraries: [Handlebars](http://formatjs.io/handlebars/), [React](http://formatjs.io/react/), and [Dust](http://formatjs.io/dust/).
- Modular, integration libs (above) are built on [core libraries](http://formatjs.io/github/#core): [intl-mesageformat](https://github.com/yahoo/intl-messageformat), [intl-relativetime](https://github.com/yahoo/intl-relativeformat).
- IE6+ support, automated testing in IE7+.
- Built on standards: ECMA-402, CLDR, and ICU Message syntax.

Weaknesses:
- No parsing beyond what the `Date` and `Number` build-ins provide.

Links:
- http://formatjs.io/
- http://formatjs.io/github/ (packages)

### iLib

iLib is a library of Javascript internationalization routines implemented in pure Javascript without many dependendencies on other libraries. It is the i18n library used in webOS, which is currently shipping on millions of LG SmartTVs.

Strengths:
- Completeness. Goal is to be the "ICU" of Javascript!
- Runs in rhino, nodejs, various browsers and webOS
- Based on CLDR
- Over 15,000 unit tests

Weaknesses:
- Code is large. Needs to be modularized and to support more of a jquery-style plugins.
- Needs some performance enhancements

Links:
- http://sourceforge.net/projects/i18nlib/
- http://demo.jedlsoft.com/
- http://docs.jedlsoft.com/ilib/jsdoc/

## Grid

| &nbsp; | ECMA-402<br><sub><sup>Native</sup></sub> | Cldrpluralruleparser<br><sub><sup>[santhoshtr/cldrpluralruleparser][]</sup></sub> | Globalize<br><sub><sup>[jquery/globalize][]</sup></sub> | Messageformat.js<br><sub><sup>[slexaxton/messageformat.js][]</sup></sub> | FormatJS<br><sub><sup>[formatjs.io][]</sup></sub> | iLib<br><sub><sup>[ilib][]</sup></sub> |
| --- | --- | --- | --- | --- | --- | --- |
| **Functionality** | | | | | | |
| &nbsp; | | | | | | |
| [Date Format][]<br><sub><sup>`new Date()` ⟹ Oct 23, 2014, 9:00:00 AM</sup></sub> | :heavy_check_mark: | | :heavy_check_mark: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| [Date Parse][]<br><sub><sup>Oct 23, 2014, 9:00:00 AM ⟹ `new Date()`</sup></sub> | | | :heavy_check_mark: | | |
| [Relative Time Format][]<br><sub><sup>`new Date()` ⟹ last month</sup></sub> | | | :soon: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;[intl-relativeformat](https://github.com/yahoo/intl-relativeformat)</sup></sub> | :heavy_check_mark: |
| [Duration Format][]<br><sub><sup>203:23:23</sup></sub> | | | | | | :heavy_check_mark: |
| [Date Range Format][]<br><sub><sup>Jan 11-13, 2015</sup></sub> | | | | | | :heavy_check_mark: |
| [Time Zone Support][]<br><sub><sup>Jan 13, 2015 KST</sup></sub> | | | | | | :heavy_check_mark: |
| [Multiple Calendar Support][]<br><sub><sup>Aban 1, 1393 (Persian)</sup></sub> | | | | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Number Format][]<br><sub><sup>`12734.89` ⟹ 12,734.89</sup></sub> | :heavy_check_mark: | | :heavy_check_mark: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| [Number Parse][]<br><sub><sup>12,734.89 ⟹ `12734.89`</sup></sub> | | | :heavy_check_mark: | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Currency Format][]<br><sub><sup>`{EUR: 1000.00}` ⟹ €1,000.00</sup></sub> | :heavy_check_mark: | | :soon: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> | :heavy_check_mark: |
| [Currency Parse][]<br><sub><sup>€1,000.00 ⟹ `{EUR: 1000.00}`</sup></sub> | | | :soon: | | | :heavy_check_mark: |
| [Percentage Format][]<br><sub><sup>% 23,4 (tr-TR)</sup></sub> | | | | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Unit Format][]<br><sub><sup>1,234.56 feet</sup></sub> | | | | | | :heavy_check_mark: |
| [Unit Conversion][]<br><sub><sup>1 mile -> 16.09 km</sup></sub> | | | | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Name Parse][]<br><sub><sup>John James Smith -> {givenName: "John", middleNames: "James", familyName: "Smith"}</sup></sub> | | | | | | :heavy_check_mark: |
| [Name Format][]<br><sub><sup>{givenName: "John", middleNames: "James", familyName: "Smith"} -> John James Smith</sup></sub> | | | | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Address Parse][]<br><sub><sup>123 any st.<br>Santa Clara, CA 94044<br>USA ⟹ `{streetAddress:"123 any st.",locality:"Santa Clara",region:"CA",country:"USA",postalCode:"94044"}`</sup></sub> | | | | | | :heavy_check_mark: |
| [Address Format][]<br><sub><sup></sup>`{streetAddress:"123 any st.",locality:"Santa Clara",region:"CA",country:"USA",postalCode:"94044"}` ⟹ 123 any st.<br>Santa Clara, CA 94044<br>USA</sub> | | | | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Phone Number Parse][]<br><sub><sup>1 (650) 555-1212 -> {trunkCode:"1",areaCode:"650",subscriberNumber:"5551212"}</sup></sub> | | | | | | :heavy_check_mark:<br><sub><sup>20 locales</sup></sub> |
| [Phone Number Format][]<br><sub><sup>{trunkCode:"1",areaCode:"650",subscriberNumber:"5551212"} -> 1 (650) 555-1212</sup></sub> | | | | | | :heavy_check_mark:<br><sub><sup>20 locales</sup></sub> |
| [Phone Number Normalization][]<br><sub><sup>{subscriberNumber:"5551212"} -> `{iddCode:"+",trunkCode:"1",areaCode:"650",subscriberNumber:"5551212"}` | | | | | | :heavy_check_mark: |
| [Phone Number Geolocation][]<br><sub><sup>{areaCode: "650",subscriberNumber:"5551212"} -> " | | | | | | :heavy_check_mark: |
| &nbsp; | | | | | |
| [Charset Mapping][]<br><sub><sup>Shift-JIS -> Unicode</sup></sub> | | | | | | :soon: |
| &nbsp; | | | | | |
| [Plural][]<br><sub><sup>`3` ⟹ `few`</sup></sub> | | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[santhoshtr/cldrpluralruleparser][]</sup></sub> | | :heavy_check_mark: | :heavy_check_mark: |
| [Resource Bundle][]<br><sub><sup>`getString(id)` ⟹ "resource string"</sup></sub> | | | | | | :heavy_check_mark: |
| [Message Format][]<br><sub><sup>`You have {count, plural,`<br>` one {1 item}`<br>` other {# items}}` ⟹ You have 5 items</sup></sub> | | | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[slexaxton/messageformat.js][]</sup></sub> | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Via&nbsp;[intl-messageformat](https://github.com/yahoo/intl-messageformat)</sup></sub> | :heavy_check_mark: |
| [Unicode Normalization Algorithm] | | | | | | :heavy_check_mark: |
| [Code Point Support] | | | | | | :heavy_check_mark: |
| [Glyph Support] | | | | | | :heavy_check_mark: |
| [Locale-sensitive Capitalization] | | | | | | :heavy_check_mark: |
| [Unicode Character Properties] | | | | | :heavy_check_mark:<br><sub><sup>(via the CType functions)</sup></sub> |
| &nbsp; | | | | | | |
| Template integration | | | | | Handlebars<br>React<br>Dust | |
| &nbsp; | | | | | | |
| [Collation] | :heavy_check_mark: | | | | | :heavy_check_mark:<br><sub><sup>limited locales so far</sup></sub> |
| &nbsp; | | | | | |
| **I18n data** | Compiled | | [CLDR][] >= 25 | | [CLDR][] | Compiled or Dynamic load.<br>CLDR 22.1 |
| &nbsp; | | | | | | |
| **Support** | | | | | |
| &nbsp; | | | | | | |
| Environments | Globals | AMD<br>CommonJS<br>Globals | AMD<br>CommonJS<br>Globals | AMD<br>CommonJS<br>Globals | ES6<br>CommonJS<br>Globals |
| Node.js | >= 0.12<br><sub><sup>`en` only by default</sup></sub> | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Browser | Chrome: 24<br>Firefox: 29<br>Safari: N/A<br>Opera: 15<br>IE: 11<br><sub><sup>Reference MDN.</sup></sub> | | Chrome: <sub><sup>(Current - 1) or Current</sup></sub><br>Firefox: <sub><sup>(Current - 1) or Current</sup></sub><br>Safari: 5.1+<br>Opera: 12.1x, <sub><sup>(Current - 1) or Current</sup></sub><br>IE: 8 <sub><sup>(needs ES5 polyfill)</sup></sub>, IE9+ | | All ES3+ including IE6 | Chrome: 20+<br>Firefox: 25<br>Safari: 5.1+<br>IE: 9+ |
| Mobile | | | iOS: 6.1+<br>Android: 2.3, 4.0+ | | :heavy_check_mark: | :heavy_check_mark: |

[andyearnshaw/intl.js]: https://github.com/andyearnshaw/Intl.js/
[CLDR]: http://cldr.unicode.org/index/cldr-spec/json
[ibm-js/ecma402]: https://github.com/ibm-js/ecma402
[jquery/globalize]: https://github.com/jquery/globalize/
[santhoshtr/cldrpluralruleparser]: https://github.com/santhoshtr/CLDRPluralRuleParser/
[slexaxton/messageformat.js]: https://github.com/SlexAxton/messageformat.js/
[formatjs.io]: http://formatjs.io/
[ilib]: http://sourceforge.net/projects/i18nlib/

[Date Format]: ./date-format.md
[Date Parse]: ./date-parse.md
[Duration Format]: ./duration-format.md
[Date Range Format]: ./date-range-format.md
[Relative Time Format]: ./relative-time-format.md
[Time Zone Support]: ./time-zone-support.md
[Multiple Calendar Support]: ./multiple-calendar-support.md
[Number Format]: ./number-format.md
[Number Parse]: ./number-parse.md
[Currency Format]: ./currency-format.md
[Currency Parse]: ./currency-parse.md
[Plural]: ./plural.md
[Message Format]: ./message-format.md
[Percentage Format]: ./percentage-format.md
[Unit Format]: ./unit-format.md
[Unit Conversion]: ./unit-conversion.md
[Name Parse]: ./name-parse.md
[Name Format]: ./name-format.md
[Address Parse]: ./address-parse.md
[Address Format]: ./address-format.md
[Phone Number Parse]: ./phone-number-parse.md
[Phone Number Format]: ./phone-number-format.md
[Phone Number Normalization]: ./phone-umber-format.md
[Charset Mapping]: ./charset-mapping.md
[Unicode Normalization Algorithm]: ./unicode-normalization-algorithm.md
[Code Point Support]: ./code-point-support.md
[Glyph Support]: ./glyph-support.md
[Locale-sensitive Capitalization]: ./locale-sensitive-capitalization.md
[Unicode Character Properties]: ./unicode-character-properties.md
[Phone Number Normalization]: ./phone-number-normalization.md
[Phone Number Geolocation]: ./phone-number-geolocation.md
[Collation]: ./collation.md
[Resource Bundle]: ./resource-bundle.md
