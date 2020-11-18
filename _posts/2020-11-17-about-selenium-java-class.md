---
layout: post
title:  "About Selenium Java class"
author: ha
categories: [ selenium ]
image: https://images.unsplash.com/photo-1472162072942-cd5147eb3902?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80
---
Selenium Java basic class, khoá học cung câp kiến thức cơ bản để làm việc với Selenium bằng Java language.
Khoá học giúp mọi ngừoi có cách để lấy các đối tượng, viết các test case với các ví dụ từ đơn giản đến phức tạp.




Các kỹ năng yêu cầu trước khi tham gia khoá học này:

#### 1. Thiết lập môi trường làm việc với Java ☕ 

- Cài đặt [Java JDK](https://www.oracle.com/java/technologies/javase-jdk13-downloads.html)
- Thiết lập biến môi trường JAVA_HOME
  * Cho [Windows 7](https://medium.com/@tushar0618/setting-java-home-variable-on-windows-7-bab344b6f3c4)
  * Cho [Windows 10](https://mkyong.com/java/how-to-set-java_home-on-windows-10/)
  * Cho [Linux](https://www.baeldung.com/linux/path-variable)
  * Cho MAC OS

From OS X 10.5, Apple introduced a command line tool (/usr/libexec/java_home) which dynamically finds the top Java version specified in Java Preferences for the current user.

Open ~/.bash_profile in any text editor and add:

{% highlight bash %}
    export JAVA_HOME=$(/usr/libexec/java_home)
{% endhighlight %}


Save and close the file.

Open a Terminal and run the source command to apply the changes:

{% highlight bash %}
   source ~/.bash_profile
{% endhighlight %}


Now we can check the value of the JAVA_HOME variable:

{% highlight bash %}
  echo $JAVA_HOME
{% endhighlight %}

The result should be the path to the JDK installation:
{% highlight bash %}
  /Library/Java/JavaVirtualMachines/jdk1.8.0_111.jdk/Contents/Home
{% endhighlight %}



#### 2. Download [apache-maven-3.6.3](https://mirror.downloadvn.com/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).

- Sau đó giải nén file zip.

- Thêm đường dẫn **your-dir/apache-maven-3.6.3/bin** vào biến **PATH**


#### 3. Java Project:

- ⭐  [Khỏi tạo 1 dự án Java bằng IntelliJ](https://www.jetbrains.com/help/idea/delegate-build-and-run-actions-to-maven.html)

- ⭐  Khỏi tạo 1 package

- ⭐  Cách định nghĩa một class, method

- ⭐  biến

- ⭐  các câu điều kiện, câu lệnh lặp

- ⭐  Lập trình hướng đối tượng OOP


👉 Mình có làm sẵn một số câu hỏi về Java các bạn có thể tham khảo taị [Java for Tester](https://github.com/cuhavp/JavaForTester)


#### 4. Nội dung khoá học
1. Giới thiệu căn bản về Kiểm thử tự động
2. Giới thiệu căn bản về Selenium
3. Sử dụng Selenium để mở các trình duyệt
4. Sử dụng Selenium để tương tác với các đối tượng trên một trang web
* Text box
* Button
* Hyper link
* Drop down
* Check box
* Table
* JS Alert
* Frame/IFrame
* Mouse actions 
   - right click
   - hover
   - drag drop

5. Làm việc với TestNG
6. Sử dụng một framework có sẵn để viết test cases


![Selenium class content]({{ site.baseurl }}/assets/images/19.png)