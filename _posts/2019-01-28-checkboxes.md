---
layout: post
title:  "Working with checkboxes"
author: ha
categories: [ selenium, tutorial ]
image: https://images.unsplash.com/photo-1597276144232-6f56f1a7f2e3?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1275&q=80
tags: [featured]
---

Đây cũng là một trong nhưng đối tượng thường xuyên xuất hiện trên các trang web.

Bài này mình giới thiệu cách làm việc với checkbox bằng selenium thông qua ví dụ sau check


### Test case
**Steps:**
- Open browser
- Navigate to `https://the-internet.herokuapp.com/checkboxes`
- Check on `checkbox1`
- Verify `checkbox1` is *checked*
- Check on `checkbox2`
- Verify `checkbox2` is *checked*

### Test case as code

{% highlight java %}
 @Test
    void checkboxes(){
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.get("https://the-internet.herokuapp.com/checkboxes");

       WebElement checkbox1 = driver.findElement(By.xpath("//form[@id='checkboxes']/input[1]"));
       WebElement checkbox2 = driver.findElement(By.xpath("//form[@id='checkboxes']/input[2]"));

       if (!checkbox1.isSelected()){
           checkbox1.click();
       }
       Assert.assertTrue(checkbox1.isSelected());

        if (!checkbox2.isSelected()){
            checkbox2.click();
        }
        Assert.assertTrue(checkbox2.isSelected());

    }

{% endhighlight %}



### More ...
Đối với hành động `check` thì tương tự như `click` vào một đối tượng, nhưng ở đây phải kiểm tra trạng thái của đối tượng đó trước khi `check`. Selenium cho chúng ta một method `.isSelected()` để kiếm tra xem đối tượng đã được chọn (``selected) hay chưa.

Do vậy chúng ta có thể viết thêm 2 hàm `check`  và `uncheck` để sau này có thể tái sử dụng lại như sau:
{% highlight java %}

public static void check (WebElement checkbox){
        if (!checkbox.isSelected()){
            checkbox.click();
        }
    }

public static void uncheck (WebElement checkbox){
    if (checkbox.isSelected()){
        checkbox.click();
    }
}
{% endhighlight %}

Và ta có thể sữa lại test case ở trên như sau :

{% highlight java %}
 @Test
    void checkboxes(){
        WebDriverManager.chromedriver().setup();
        WebDriver driver = new ChromeDriver();
        driver.get("https://the-internet.herokuapp.com/checkboxes");

        WebElement checkbox1 = driver.findElement(By.xpath("//form[@id='checkboxes']/input[1]"));
        WebElement checkbox2 = driver.findElement(By.xpath("//form[@id='checkboxes']/input[2]"));

        check(checkbox1);
        Assert.assertTrue(checkbox1.isSelected());

        check(checkbox2);
        Assert.assertTrue(checkbox2.isSelected());
    }
{% endhighlight %}