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

settings.setCommentCollectionEnabled(true);
CsvParser parser = new CsvParser(settings);
parser.beginParsing(getReader("/examples/example.csv"));
String[] row;
while ((row = parser.parserNext()) != null) {
  String comment = parser.getContext().lastComment();
  if (comment == null || comment.trim().isEmpty()) {
    comment = "No relevant comments yet";
  }
  println("Comment: " + comment + ". Parsed: " + Arrays.toString(row));
}

println("\nAll comments found:\n---------------");

Map<Long, String> comments = parser.getContext().comments();
for (Entry<Long, String> e : comments.entrySet()) {
  long line = e.getKey();
  String commentAtLine = e.getValue();
  println("Line: " + line + ": '" + commentAtLine + "'");
}

settings.setProcessorErrorHandler(new RetryableErrorHandler<ParsingContext>() {
  @Override
  public void handleError(DataProcessingException error, Object[] inputRow, ParsingContext context) {
    println(out, "Error processing row: " + Arrays.toString(inputRow));
    println(out, "Error details: column '" + error.getColumnName() + "' (index" + error.getColumnIndex() + ") has value '" + inputRow[error.getColumnIndex()] + "'. Setting it to null");
    
    if(error.getColumnIndex() == 0) {
      setDefaultValue(null);
    } else {
      keepRecord();
    }
  }
});

BeanListProcessor<AnotherTestBean> beanProcessor = new BeanProcessor<AnotherTestBean>(AnotherTestBean.class);
settings.setProcessor(beanProcessor);

settings.setProcessorErrorHandler(new RowProcessorErrorHandler() {
  @Override
  public void handleError(DataProcessingException error, Object[] inputRow, ParsingContext context) {
    println(out, "Error processing row: " + Arrays.toString(inputRow));
    println(out, "Error details: column '" + error.getColumnName() + "' (index" + error.getColumnIndex() + ") has value '" + 
  }
});
CsvParser parser = new CsvParser(settings);
parser.parse(getReader("/example/bean_test.csv"));

println(out);
println(out, "Printing beans that could be parsed");
println(out);
for (AnotherTestBean bean : beanProcessor.getBeans()){
  println(out, bean);
}





```

```
```

```
```

