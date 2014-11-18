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

### ibm-js/ecma402

JavaScript implementation of some of the ECMA-402 APIs as developed by IBM.
It provides number formatting and date and time formatting, but not collation.
The package was primarily developed by John Emmons (IBM), who is the chairman of the
Unicode CLDR Technical Committee. Members of IBM's Dojo development team assisted with
many of the resource loading issues.

Strengths
- Should work on any browser, even those that don't have a native implementation
of ECMA-402.
- Supports a wide variety of locales and calendar systems, using standardized JSON
data as published by the Unicode CLDR project.
- Consistency - The package will produce the same results no matter which browser you
are running on. There are some inconsistencies in the results produced by the
native implementations in the various browsers.
- Provides a "shim" feature, which allows the application to use the native ECMA-402
implementation in the browser if it is available, or the Javascript implementation
if native is not available.
- Allows multiple locales to be available to the application via the locale preloading
mechanism.

Weaknesses
- Speed - JavaScript implementation of ECMA-402 requires code and data loading, which
will always be slower than a native implementation.
- Official version not yet released - still under development.

Links
- http://github.com/ibm-js/ecma402
- http://www.ecma-international.org/ecma-402/1.0/

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

Strengths
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

## Grid

| | ECMA-402<br><sub><sup>Native</sup></sub> | Cldrpluralruleparser<br><sub><sup>[santhoshtr/cldrpluralruleparser][]</sup></sub> | Globalize<br><sub><sup>[jquery/globalize][]</sup></sub> | Messageformat.js<br><sub><sup>[slexaxton/messageformat.js][]</sup></sub> | FormatJS<br><sub><sup>[formatjs.io][]</sup></sub> |
| --- | --- | --- | --- | --- | --- |
| **Functionality** | | | | | |
| &nbsp; | | | | | |
| [Date Format][]<br><sub><sup>`new Date()` ⟹ Oct 23, 2014, 9:00:00 AM</sup></sub> | :heavy_check_mark: | | :heavy_check_mark: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> |
| [Date Parse][]<br><sub><sup>Oct 23, 2014, 9:00:00 AM ⟹ `new Date()`</sup></sub> | | | :heavy_check_mark: | | |
| [Relative Time Format][]<br><sub><sup>`new Date()` ⟹ last month</sup></sub> | | | :soon: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;[intl-relativeformat](https://github.com/yahoo/intl-relativeformat)</sup></sub> |
| &nbsp; | | | | | |
| [Number Format][]<br><sub><sup>`12734.89` ⟹ 12,734.89</sup></sub> | :heavy_check_mark: | | :heavy_check_mark: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> |
| [Number Parse][]<br><sub><sup>12,734.89 ⟹ `12734.89`</sup></sub> | | | :heavy_check_mark: | | |
| &nbsp; | | | | | |
| [Currency Format][]<br><sub><sup>`{EUR: 1000.00}` ⟹ €1,000.00</sup></sub> | :heavy_check_mark: | | :soon: | | :heavy_check_mark:<br><sub><sup>Via&nbsp;ECMA-402 or its polyfil</sup></sub> |
| [Currency Parse][]<br><sub><sup>€1,000.00 ⟹ `{EUR: 1000.00}`</sup></sub> | | | :soon: | | |
| &nbsp; | | | | | |
| [Plural][]<br><sub><sup>`3` ⟹ `few`</sup></sub> | | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[santhoshtr/cldrpluralruleparser][]</sup></sub> | | :heavy_check_mark: |
| [Message Format][]<br><sub><sup>`You have {count, plural,`<br>` one {1 item}`<br>` other {# items}}` ⟹ You have 5 items</sup></sub> | | | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[slexaxton/messageformat.js][]</sup></sub> | :heavy_check_mark: | :heavy_check_mark:<br><sub><sup>Via&nbsp;[intl-messageformat](https://github.com/yahoo/intl-messageformat)</sup></sub> |
| &nbsp; | | | | | |
| Template integration | | | | | Handlebars<br>React<br>Dust |
| &nbsp; | | | | | |
| Collation | :heavy_check_mark: | | | | |
| &nbsp; | | | | | |
| **I18n data** | Compiled | | [CLDR][] >= 25 | | [CLDR][] |
| &nbsp; | | | | | |
| **Support** | | | | | |
| &nbsp; | | | | | |
| Environments | Globals | AMD<br>CommonJS<br>Globals | AMD<br>CommonJS<br>Globals | AMD<br>CommonJS<br>Globals | ES6<br>CommonJS<br>Globals |
| Node.js | >= 0.12<br><sub><sup>`en` only by default</sup></sub> | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Browser | Chrome: 24<br>Firefox: 29<br>Safari: N/A<br>Opera: 15<br>IE: 11<br><sub><sup>Reference MDN.</sup></sub> | | Chrome: <sub><sup>(Current - 1) or Current</sup></sub><br>Firefox: <sub><sup>(Current - 1) or Current</sup></sub><br>Safari: 5.1+<br>Opera: 12.1x, <sub><sup>(Current - 1) or Current</sup></sub><br>IE: 8 <sub><sup>(needs ES5 polyfill)</sup></sub>, IE9+ | | All ES3+ including IE6 |
| Mobile | | | iOS: 6.1+<br>Android: 2.3, 4.0+ | | :heavy_check_mark: |

[andyearnshaw/intl.js]: https://github.com/andyearnshaw/Intl.js/
[CLDR]: http://cldr.unicode.org/index/cldr-spec/json
[ibm-js/ecma402]: https://github.com/ibm-js/ecma402
[jquery/globalize]: https://github.com/jquery/globalize/
[santhoshtr/cldrpluralruleparser]: https://github.com/santhoshtr/CLDRPluralRuleParser/
[slexaxton/messageformat.js]: https://github.com/SlexAxton/messageformat.js/
[formatjs.io]: http://formatjs.io/

[Date Format]: ./date-format.md
[Date Parse]: ./date-parse.md
[Relative Time Format]: ./relative-time-format.md
[Number Format]: ./number-format.md
[Number Parse]: ./number-parse.md
[Currency Format]: ./currency-format.md
[Currency Parse]: ./currency-parse.md
[Plural]: ./plural.md
[Message Format]: ./message-format.md
