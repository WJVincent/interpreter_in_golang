# Lexing

Phase 1 of the interpreting process, tokenizing the plain text of the code.

## Example I/O

```
// input
let x = 5 + 5;
```

```
// output

[
  LET,
  IDENTIFIER("x"),
  EQUAL_SIGN,
  INTEGER(5),
  PLUS_SIGN,
  INTEGER(5),
  SEMICOLON
]
```


