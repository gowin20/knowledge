ISO EBNF|grep -E regular expression|description
-|-|-|
[optional stuff]|O?,
(grouped stuff)|(G),
{repeated stuff}|R*,
,E+|one or more instances of the symbol. Not present in ISO EBNF
A*|A*,
"A, B"|AB,
A | B|A | B,
A - B|,A except B (set difference) - not present in grep
a b c|,single identifiers -  not present in grep
(* comment *)|," not present in grep"
lhs = rhs;|,grammar rule -  not present in grep