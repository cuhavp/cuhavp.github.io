---
title:  "What is testing tool?"
layout: post
author: ha
categories: [ testing-tool, tutorial ]
image: https://images.unsplash.com/photo-1581783898377-1c85bf937427?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1258&q=80
tag: [feature]
---

Có rất nhiều tool được sử dụng trong quá trình làm kiểm thử tự động ví dụ như automation tool, build tool, CI tool, Editor tools. Bài này mình sẽ nói về `Testing tool`

### Công việc của một tester

Đâu tiên chúng ta thử xem lại những công việc chính của một người làm kiểm thử phần mềm. Sau khi nhân được *Requirements* thì tiếp theo các bạn tester sẽ dùng những kỹ thuật viết `test case` để tạo ra các bộ test case liên quan tới yêu cầu mới và có thể luư trữ trên jira, testlink, testrails hoặc thậm chí là excel.

Kế tiếp là dựa theo cái `Iteration` mà những bạn tester sẽ xác định `test plan`. Trong test plan thường phải có test trên môi trường nào, bộ test case sẽ được thực thi là gì, và như thế nào là pass.

Sau đó là đên giai đoạn mình run/execute những test case đó để có được `testing reports`.

![Testing]({{ site.baseurl }}/assets/images/18.png)

### Testing tool là gì?

Trong quá trình phát triển của nền công nghiệp phần mềm thì kiểm thử tự động như một xu thế tất yếu. Một trong những mảng được ứng dụng kiểm thử tự động sớm nhất đó là `unit test`.

Với động lực như vậy nên các developer mới phát triển ra một loại công cụ mới giúp chuyển đổi những công việc `manual` của một tester thành các thư viện có thể viết được bằng các đoạn mã code. Đó là  sự ra đời của `Testing as code`.

Cho nên testing tool sẽ cho chúng ta cách viết 1 test case, test case và test report.

Một điểm khác so với các bạn làm manual là kiểm thử tự động không cần con ngừoi thực thi các test case mà thông qua các testing tool và automation tool việc này sẽ làm hoàn toàn tự động.

Do đó chúng ta sẽ thấy kiểm thử tự động thường được dùng cho `regression test`. Và lúc này giá trị của kiểm thử tự động mới thấy được.

Ngoài ra chúng ta cũng sẽ thấy để viết được 1 test case tự động cũng sẽ tốn nhiều thời gian và kỹ năng hơn là một test case thực thi bằng tay. Ngoài kiến thức về hệ thống sản phẩm, kỹ năng thiết kế test case còn cần kỹ năng lập trình.

### Một số testing tools phổ biến

- Java
  - Junit4/Junit5
  - TestNG
  
- Python
  - pytest

- Scala
  - ScalaTest

- Ruby
  - RSpec