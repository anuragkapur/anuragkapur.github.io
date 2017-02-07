
---
layout: post
title:  "Spring and Mockito in Junits"
date:   2017-02-07 16:30:00 +0000   
categories: highlight programming
tags: spring mockito junit java programming
teaser: Getting Spring and Mockito to work happily together in JUnits
---  

# Problem statement
Given a Test class using sprint Junit runner
```java
@RunWith(SpringJUnit4ClassRunner.class)
public class MyTest {

  //...
  
}
```

And you want to use Mockito, you can't use the MockitoJunitRunner annotation. So what do you do?

# Solution
```java
@Before
public void setup() {
    MockitoAnnotations.initMocks(this);
}
```

