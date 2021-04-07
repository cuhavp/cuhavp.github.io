---
layout: post
title:  "Page Object Model: Using string to define locator"
author: ha
categories: [ selenium,tutorial ]
image: https://images.unsplash.com/photo-1544020385-7919c818744e?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=1934&q=80
tags: featured
---

`Page Object Model` là một cách tổ chức code(design pattern) giúp việc sử dụng hoặc khả năng đọc hiểu tốt hơn khi làm việc với Selenium. 

Page Object Model làm 2 việc dưới đây:
 - Định nghĩa các "Operator" hay hành vi người dùng trên 1 trang cụ thể
 - Định nghĩa các "Object" hay các đối tượng trên 1 trang cụ thể

Có một điểm lưu ý khi làm việc với POM đó là chỉ tập trung trên 1 trang cụ thể để làm cho các class page đơn giản và tập trung hơn.

Trong bài này mình sẽ lấy một ví dụ để mô ta việc mình sử dụng kiểu String để mô ta đối tượng.

```
    WebDriver driver;
    By usernameTxt = By.id("username");
    By passwordTxt = By.id("password");
    By loginBtn = By.xpath("//button[contains(.,'Login')]");

    public LoginPage(WebDriver driver) {
       this.driver = driver;
    }

    public void open() {
        driver.get("https://the-internet.herokuapp.com/login");
    }

    public void login(String username, String password) {
        driver.findElement(usernameTxt).sendKeys(username);
        driver.findElement(passwordTxt).sendKeys(password);
        driver.findElement(loginBtn).click();
    }
```