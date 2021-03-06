# Reto para la Práctica p2-t1-testing

En el JSON generado, el valor de la entrada `authors` es un Array de Strings:


```json
{
  "id": 132,
  "title": "The Art of War",
  "authors": [
    "Sunzi, active 6th century B.C.",
    "Giles, Lionel"
  ],
  "subjects": [
    "Military art and science -- Early works to 1800",
    "War -- Early works to 1800"
  ]
}
```

En los ficheros RDF figura información adicional sobre los autores. Por ejemplo tienen atributos **alias**
y **webpage**s:

```xml
<pgterms:agent rdf:about="2009/agents/4349">
    <pgterms:name>Sunzi, active 6th century B.C.</pgterms:name>
    <pgterms:alias>孫子</pgterms:alias>
    <pgterms:alias>孙子</pgterms:alias>
    <pgterms:webpage rdf:resource="http://zh.wikipedia.org/wiki/%E5%AD%99%E6%AD%A6"/>
    <pgterms:alias>Sun Tzu</pgterms:alias>
    <pgterms:webpage`rdf:resource="http://en.wikipedia.org/wiki/Sun_Tzu"/>
</pgterms:agent>
```

Convierta el valor de la entrada `authors` en un Array
de objetos, cada uno de los cuales disponga de atributos `name` y `webpages`. 
El atributo `webpages` es el valor del atributo `rdf:resource` 
de los elementos `pgterms:webpage`:

```json
{
  "id": 132,
  "title": "The Art of War",
  "authors": [
    {
       "name": "Sunzi, active 6th century B.C.",
       "webpages": ["http://zh.wikipedia.org/wiki/%E5%AD%99%E6%AD%A6", "http://en.wikipedia.org/wiki/Sun_Tzu"]
    },
    {
        "name": "Giles, Lionel",
        "webpages": ["http://en.wikipedia.org/wiki/Lionel_Giles"]
    }
  ],
  "subjects": [
    "Military art and science -- Early works to 1800",
    "War -- Early works to 1800"
  ]
}
```

# Pruebas

Esta vez invierta el BDD: una vez escrita su solución, escriba las pruebas.

Quizá el módulo [chai-things](https://www.npmjs.com/package/chai-things) pueda serle de ayuda.
Por ejemplo, podemos usar el atributo `all` para comprobar si todos los elementos
cumplen una determinada afirmación:

```js
 expect(book.authors).to.all.have.property("name").and.all.have.a.property("webpages");
 ```

# Solución 

* [Una solución](https://github.com/ULL-ESIT-PL-1819/p2-t1-testing-crguezl) (privado)