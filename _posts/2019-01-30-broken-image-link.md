---
layout: post
title:  "Check broken image with selenium"
author: ha
categories: [ selenium, tutorial ]
image: https://images.unsplash.com/photo-1561997968-aa846c2bf255?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
---

Để kiểm tra 1 hình có được hiển thị trên 1 website hay không thông thường sẽ kiếm tra lỗi `404` khi gọi mọt request tới file đó
Với Selenium chúng có thêm 1 cách khác để làm việc đó. 
Thông qua việc kiểm tra attribute `naturalWidth` của một đối tượng có bằng `0` hay không?

> Định nghĩa về `naturalWidth` 
> 
>Definition and Usage
>The naturalWidth property returns the original width of an image.

>For example, if you have an image that is originally 100 pixels wide. Then, you style the image with CSS/or by using the HTML "width" attribute to make it 500 pixels wide. The naturalWidth property will return "100", the width property however, will return 500.

### Code
{% highlight java %}
@Test
    void checkBrokenImages(){
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.get("http://the-internet.herokuapp.com/broken_images");

        List<WebElement> images = driver.findElements(By.cssSelector("img"));
        for(WebElement image: images){
            if(image.getAttribute("naturalWidth").equals("0")){
                System.out.println(image.getAttribute("outerHTML") + " is broken.");
            }
        }

    }
{% endhighlight %}
