### univocity-parsers
---
https://github.com/uniVocity/univocity-parsers

```java
public Reader getReader(String relativePath) {
  return new InputStreamReader(this.getClass().getResourceAsStream(relativePath, "UTF-8"));
}

CsvParserSettings settings = new CsvParserSettings();
settings.getFormat().setLineSeparator("\n");
CsvParser parser = new CsvParser(settsings);
List<String[]> allRows = parser.parseAll(getReader("/example/example.csv"));

// https://www.univocity.com/pages/univocity_parsers_tutorial




```

```
```

```
```

