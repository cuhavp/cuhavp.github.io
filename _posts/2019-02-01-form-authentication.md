---
layout: post
title:  "Working with form authentication"
author: ha
categories: [ selenium, tutorial ]
image: https://images.unsplash.com/photo-1600695268275-1a6468700bd5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2551&q=80
---

Form Authentication is basic page to login a site. So we are using selenium to create a test automated for this site.


## Test Case description

Steps: 
 - Open browser
 - Navigate to https://the-internet.herokuapp.com/login
 - Fill in username with `tomsmith`
 - Fill in the password with `SuperSecretPassword!`
 - Click on Login button
 - And the home page is appear



## Writing code 

We using two dependencies
```
<dependency>
    <groupId>org.seleniumhq.selenium</groupId>
    <artifactId>selenium-java</artifactId>
    <version>3.141.59</version>
</dependency>
<dependency>
    <groupId>org.testng</groupId>
    <artifactId>testng</artifactId>
    <version>7.3.0</version>
    <scope>test</scope>
</dependency>
```

Tạo Test class
{% highlight java %}
 @Test
    void validCredentials(){
        WebDriver driver = new ChromeDriver();
        driver.get("https://the-internet.herokuapp.com/login");

        driver.findElement(By.id("username")).sendKeys("tomsmith");
        driver.findElement(By.id("password")).sendKeys("SuperSecretPassword!");

        driver.findElement(By.xpath("//button[@type='submit']")).click();

        Assert.assertEquals(driver.getCurrentUrl(),"https://the-internet.herokuapp.com/secure");

    }
{% endhighlight %}