Escriba un método bexec para los objetos RegExpque funcione como exec pero sólo case en la posición lastIndex:
~~~JavaScript
        RegExp.prototype.bexec = function(str) {
          var i = this.lastIndex;
          var m = this.exec(str);
          if (m && n.index == i) return m;
          return null;
        };
~~~
Basándose en el método bexec del ejercicio anterior escriba las partes que faltan del método tokens que implementa un analizador léxico para un lenguaje de tipo JavaScript en el que if y then son palabras reservadas:
~~~JavaScript
  String.prototype.tokens = function() {
    var RESERVED_WORD, from, getTok, i, key, m, make, n, result, rw, tokens, value;
    from = 0;
    i = 0;
    n = 0;
    m = 0;
    result = [];
    tokens = {
      WHITES: /\s+/g,
      ID:/[a-zA-Z_]\w*/,
      NUM: /\b[+-]?\d+([.]\d*)?([eE][+-]?\d+)?\b/g,
      STRING: /"(\\.|[^"])*"|'(\\.|[^'])*'/g,
      ONELINECOMMENT:/\/\/.*/g,
      MULTIPLELINECOMMENT:/\/[*](.|\n)*?[*]\//g,
      COMPARISONOPERATOR:/[!=]?==?|[<>]=|[+][+=]|-[-=]/g,
      ONECHAROPERATORS: /([=()&|;:,{}[\]])/g,
      ADDOP: /[+-]/g,
      MULTOP: /[*\/]/g
    };
    RESERVED_WORD = {
      "if": "IF",
      then: "THEN"
    };
    ~~~
Explique como se usa en el análisis el objeto RESERVED_WORD y para que sirve. Observe su uso en el bucle

Siver para distingir las palabras reservadas del lenguaje if y them del resto de ids

~~~JavaScript
    make = function(type, value) {
      return {
        type: type,
        value: value,
        from: from,
        to: i
      };
    };
    getTok = function() {
      var str;
      str = m[0];
      i += str.length;
      return str;
    };
    if (!this) {
      return;
    }
    while (i < this.length) {
      for (key in tokens) {
        value = tokens[key];
        value.lastIndex = i;
      }
      from = i;
      if (m = tokens.WHITES.bexec(this) ||
         (m = tokens.ONELINECOMMENT.bexec(this)) ||
         (m = tokens.MULTIPLELINECOMMENT.bexec(this))) {
           getTok();
      } else if (m = tokens.ID.bexec(this)) {
        rw = RESERVED_WORD[m[0]];
        if (rw) {
          result.push(make(rw, getTok()));
        } else {
          result.push(make("name",getTok()));
        }
      } else if (m = tokens.NUM.bexec(this)) {
        n = +getTok();
        if (isFinite(n)) {
          result.push(make("number", n));
        } else {
          make("NUM", m[0]).error("Bad number");
        }
      } else if (m = tokens.STRING.bexec(this)) {
        result.push(make("STRING", getTok().replace(/(^["'])|(["']$)/g, "")));
      } else if (m = tokens.COMPARISONOPERATOR.bexec(this)) {
        result.push(make("COMPARISON", getTok()));
      } else if (m = tokens.ADDOP.bexec(this)) {
        result.push(make("ADDOP", getTok()));
      } else if (m = tokens.MULTOP.bexec(this)) {
        result.push(make("MULTOP", getTok()));
      } else if (m = tokens.ONECHAROPERATORS.bexec(this)) {
        result.push(make(m[0], getTok()));
      } else {
        throw "Syntax error near '" + (this.substr(i)) + "'";
      }
    }
    return result;
  };
~~~
