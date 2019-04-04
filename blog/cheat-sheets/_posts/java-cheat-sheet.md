# JSON processing
## Jackson ignore unknown field annotation
```java
@JsonIgnoreProperties(ignoreUnknown = true)
```

# Spring
## Testing - Setup Environment for a single Controller, doesn't start server
```java
@RunWith(SpringRunner.class)
@WebFluxTest(WorkoutController.class)
@Import({InMemoryRepository.class, AuthorisationFilter.class})
```

## Testing - Setup Environment with an embedded server
```java
@AutoConfigureWebTestClient
@RunWith(SpringRunner.class)
@SpringBootTest
```

## Rest Template

https://docs.spring.io/spring/docs/4.3.14.RELEASE/spring-framework-reference/htmlsingle/#rest-resttemplate

## Get request with request headers
```java
HttpHeaders headers = new HttpHeaders();
headers.setContentType(MediaType.APPLICATION_JSON);
HttpEntity<?> requestEntity = new HttpEntity<>(headers);
ResponseEntity<String> responseEntity = restTemplate.exchange("http://localhost:4200/abc", HttpMethod.GET, requestEntity, String.class);
```

# IO
## Write to File

## Read from File
