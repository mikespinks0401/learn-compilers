# How Compiles Work

1. The file input is turned into a string
2. The string Goes through a tokenizer("lexical Analysis")
    - An Array is created to keep track of the tokens
        token ex. {type: "paren", value: "("},
        token ex. {type: "number", value: 422},
        token ex. {type: "string", value:  "stringContent" }
    - token types = "name", | "paren" | "number" | "string"
    - value = ""
    - createPerson ("Michael", 34)
    - Iterate through input
    - Tokens = []
    - Tokenized = [
      - {type: 'name',value: "createPerson"},
      - {type: 'paren', value : "("},
      - {type: 'string', value: "Michael" }
      - {type: 'number', value: 34}
      - {type: 'paren', value: ")"}
      - ]
    a
3. The Tokens Array Goes Pass Through A Parser to create a Abstract Syntax Tree(AST)
    - Reformats the tokens into a representation that describes each part of the syntax and relationships to one anouther. 
    - A deeply nested Object
    - Represents the code in a way that is easy to work with and give use tons of information
    - The Parser walks through the array("recursion")

      **AST** OF THE SAMPLE ABOVE WOULD LOOK LIKE THIS

            {
            type: 'Program',
            body: [{
                type: 'CallExpression',
                name: 'createPerson',
                params: [{
                    type: "StringLIteral",
                    value: "Michael",
                    },{
                    type: "NumberLiteral",
                    value: 34
                    }]
                }]
            }
        