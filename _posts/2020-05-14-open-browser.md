---
layout: post
title:  "Open browser"
author: ha
categories: [ selenium, java ]
image: https://images.unsplash.com/photo-1446582186851-3fe172f6acb9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80
tags: [browser]
---
Việc đầu tiên khi tìm hiểu selenium đó là selenium mở browser lên như thế nào.


## Chrome
Viết đoạn code như dưới đây rồi run nó :

{% highlight java %}
   public static void main(String[] args) {
        new ChromeDriver();
    }
{% endhighlight %}

và bạn thấy lỗi văng ra ở đoạn code ở mở :
{% highlight bash %}
  Exception in thread "main" java.lang.IllegalStateException: The path to the driver executable must be set by the webdriver.chrome.driver system property; for more information, see https://github.com/SeleniumHQ/selenium/wiki/ChromeDriver. The latest version can be downloaded from http://chromedriver.storage.googleapis.com/index.html
{% endhighlight %}

vấn để là message này chỉ đến đó là hệ thống không biết được đường dẫn tới driver mà được gán cho biến môi trường *webdriver.chrome.driver* là ở đâu?

Các bước để có giúp hệ thống hiểu được:
1. kiểm version hiện tại của Chrome trên máy tính của bạn.
2. Lên trang http://chromedriver.storage.googleapis.com/index.html kiếm đúng version *chromedirver*
đúng với version ở bước 1
3. giải nén file vừa donwload xuống, lấy đường dẫn của file này
4. Thêm đoạn code để máy bạn hiểu được *webdriver.chrome.driver*
{% highlight java %}
     public static void main(String[] args) {
        System.setProperty("webdriver.chrome.driver","<chrome-driver-path>");
        new ChromeDriver();
    }
{% endhighlight %}

Chạy lại đoạn code ở trên và xem kết quả nào!!!!