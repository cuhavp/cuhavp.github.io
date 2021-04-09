---
layout: post
title:  "How to put parameters into xpath string with Java"
author: ha
categories: [ selenium ]
image: https://images.unsplash.com/photo-1518085250887-2f903c200fee?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80
tags: [featured]
---

Trong thực tế làm việc với Selenium, bạn sẽ thấy rất nhiều đối tượng chỉ khác nhau 1 giá trị trong xpath locator.

### Dưới đây là một số ví dụ:
```
".//*[@id='bankList']/p[.='ANZ']"
".//*[@id='bankList']/p[.='HSBC']"
".//*[@id='bankList']/p[.='Barclays']"
```

Trong các ngôn ngữ lập trình đều hỗ trợ `String Format` để mình có thể ghép các chuối lại với nhau.

Java cũng có `String.format()` để giúp chúng ta tạo ra một `pattern` chung cho các locator có dạng như ví dụ ở trên.

### Đầu tiên là định nghĩa locator string:
```
String bank = ".//*[@id='bankList']/p[.='%s']";
```

### Sử dụng để tạo ra các locator cụ thể
```
String.format(bank, "ANZ"); //--> output :  ".//*[@id='bankList']/p[.='ANZ']"
String.format(bank, "HSBC"); //--> output :   ".//*[@id='bankList']/p[.='HSBC']"
String.format(bank, "Barclays"); //--> output :   ".//*[@id='bankList']/p[.='Barclays']"
```