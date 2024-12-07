# Parsing

Phase 2 of the interpreting process, it takes input data (tokens from the lexer) and produces a data structure (the abstract syntax tree)

This will be a "top down operator parser" a type of "recursive descent parser"

## Example I/O

```
// start

if (3 * 5 > 10) {
  return "hello";
} else {
  return  "goodbye";
}
```

```
// lexer out 

{Type:IF Literal:if}
{Type:( Literal:(}
{Type:INT Literal:3}
{Type:* Literal:*}
{Type:INT Literal:5}
{Type:> Literal:>}
{Type:INT Literal:10}
{Type:) Literal:)}
{Type:{ Literal:{}
{Type:RETURN Literal:return}
{Type:IDENT Literal:hello}
{Type:; Literal:;}
{Type:} Literal:}}
{Type:ELSE Literal:else}
{Type:{ Literal:{}
{Type:RETURN Literal:return}
{Type:IDENT Literal:goodbye}
{Type:; Literal:;}
{Type:} Literal:}}
```

```
// parser out 

{
    type: "if-statement",
    condition: {
        type: "operator-expr",
        operator: ">",
        left: {
            type: "operator-expr",
            operator: "*"
            left: { type: "integer-literal", value: 3 },
            right: { type: "integer-literal", value: 5 }
        }
        right: { type: "integer-literal", value: 10 }
    },
    consequence: {
        type: "return-statement",
        returnValue: { type: "string-literal", value: hello }
    },
    alternative: {
        type: "return-statement",
        returnValue: { type: "string-literal", value: goodbye }
    }
}
```

## Format

- let statements: `let <identifier> = <expression>;`

