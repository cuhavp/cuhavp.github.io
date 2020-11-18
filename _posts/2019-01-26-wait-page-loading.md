---
layout: post
title:  "Using wait to handle page loading"
author: ha
categories: [ selenium, tutorial ]
image: https://images.unsplash.com/photo-1599689444589-133726281155?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80
---
Loading là một trong những sự kiện mà khi làm việc với các trang web mình phải tìm cách làm việc với nó, tránh việc này ảnh hưởng test flow.

Selenium có 3 cách waits:
- implicit wait hay là chờ cứng theo một mốc thời gian nhất định.
- explicit wait hay chờ mềm sử dụng trạng thái của một đối tượng hay một trang web để chở trong một khoảng thời gian nhất định. Việc sử dụng explcit giúp linh hoạt trong thì thực thi kiểm thử tự động trong các điều kiện mạng nhanh chậm khác nhau hoặc trạng thái của các đối tượng thay đổi liên tục
- fluent wait - đây là một cải tiến của explicit wait với nhiều điều kiện hơn

Đối với những ngừoi dùng selenium hiện nay thường dùng `explicit wait`. Thông qua test case dưới đây mình cho mọi ngừoi hiểu rõ hơn cách dùng `explicit wait`

### Test case
*Steps*
- Open browser
- Navigate to `https://the-internet.herokuapp.com/dynamic_loading/1`
- Click on Start button
- Wait process bar disappear
- Check fisnish message

### Test case as code

{% highlight java %}
@Test
    void dynamicLoadingPage() {
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.get("https://the-internet.herokuapp.com/dynamic_loading/1");

        driver.findElement(By.xpath("//button[.='Start']")).click();

        WebDriverWait wait = new WebDriverWait(driver, 30);
        String finishLbl = wait.until(
                ExpectedConditions
                        .visibilityOfElementLocated(
                                By.id("finish")))
                .getText();

        Assert.assertEquals(finishLbl,"Hello World!");
    }
{% endhighlight %}

### More ...
- Để có thể sử dụng explicit wait đầu tiên mình cần khởi tạo một biến `wait`:
```
WebDriverWait wait = new WebDriverWait(driver, 30);
```
- Ở đây mình đưa vào 2 biến là `driver` và `Maximum timeout in seconds  = 30`

- Class ```ExpectedConditions``` cho chúng ta nhiều phương thức khác để chờ đối tượng.
`visibilityOfElementLocated`: chờ đối tượng hiển thị trông DOM và trên UI.