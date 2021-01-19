# The regexperiment
making a safe cross language regular expression library

this work originated from the [Biscuit authorization tokens](https://github.com/CleverCloud/biscuit/issues/50) where regular expressions can be used inside authorization policies. Those authorization policies can be specified on the server side, but can also come from users as part of their token, and so we needed a way to execute regular expressions safely (avoiding [ReDoS issues](https://owasp.org/www-community/attacks/Regular_expression_Denial_of_Service_-_ReDoS)).
The conversation [started on Twitter](https://twitter.com/gcouprie/status/1351246572210835459).

## Requirements

- regular expressions must be executed the same way, with the same syntax, in multiple languages
- the implementation should work in an adversarial setup, where the attacker feeds us pathological expressions
- must be usable at runtime (regexps can come from a network request)
- the expressions will not run on a large string at once (at most 1 kilobyte in most environments), but could be executed on lots of small inputs
