## Message Format

```
You have {count, plural,
  one {1 item}
  other {# items}}
```
⟹ You have 5 items

| | Globalize<br><sub><sup>[jquery/globalize][]</sup></sub> | iLib | Messageformat.js<br><sub><sup>[slexaxton/messageformat.js][]</sup></sub> |
| --- | --- | --- | --- |
| Variable substitution | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[slexaxton/messageformat.js][]</sup></sub> | :heavy_check_mark:<br><sub><sup>but with different syntax</sup></sub> |
| Select | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[slexaxton/messageformat.js][]</sup></sub> | |
| Plural | :heavy_check_mark:<br><sub><sup>Powered&nbsp;by&nbsp;[santhoshtr/cldrpluralruleparser][]</sup></sub> | :heavy_check_mark: |

**Variable substitution**

Simple variable replacement.

**Select**

It supports the creation of internationalized messages by selecting phrases
based on keywords. It's often used to select gender.

**Plural**

It supports the creation of internationalized messages with plural inflection by
returning the appropriate message based on value's plural group: zero, one, two,
few, many, or other.

[jquery/globalize]: https://github.com/jquery/globalize/
[santhoshtr/cldrpluralruleparser]: https://github.com/santhoshtr/CLDRPluralRuleParser/
[slexaxton/messageformat.js]: https://github.com/SlexAxton/messageformat.js/
