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
    String usernameTxt = "username";
    String passwordTxt = "password";
    String loginBtn = "//button[contains(.,'Login')]";

    public LoginPage(WebDriver driver) {
       this.driver = driver;
    }

    public void open() {
        driver.get("https://the-internet.herokuapp.com/login");
    }

    public void login(String username, String password) {
        driver.findElement(By.id(usernameTxt)).sendKeys(username);
        driver.findElement(By.id(passwordTxt)).sendKeys(password);
        driver.findElement(By.xpath(loginBtn)).click();
    }
```

Trên trang login có 3 đối tượng:
```
    String usernameTxt = "username";
    String passwordTxt = "password";
    String loginBtn = "//button[contains(.,'Login')]";
```
Ở đây đều được khai báo là kiểu `String`. Ưu điểm của cách này là đơn giản với những bạn mới bắt đầu làm quen với Selenium bằng Page Object model.
Vấn đều ở đây là `String usernameTxt = "username"` có khả năng là id, name, text, class name nên việc tái sử dụng lại có thể mất thêm thời gian để hiều đây là thuộc tính nào của đối tượng. Mặt khác nếu trên front-end có thay đổi cũng sẽ mất thời gian để cập nhât hoặc hiểu được đó là đối tượng nào trên UI.

Để tránh được rủi ro này thì có thể đưa ra 1 chuẩn là lấy theo css hoặc xpath cho cả team làm theo.
