# 자바란 무엇일까?

### resources 경로의 파일 접근

```java
// java.lang
// public URL getResource(String name)
ClassLoader.getSystemResource("csv_s3_test.csv")

// org.springframework.util
// public static File getFile(String resourceLocation) throws FileNotFoundException
final File file = ResourceUtils.getFile("classpath:csv_s3_test.csv");
```