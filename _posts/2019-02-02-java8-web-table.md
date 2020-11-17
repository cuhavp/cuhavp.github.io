---
layout: post
title:  "Using Java8 to test web table"
author: ha
categories: [ java, selenium ]
image: https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80
tags: [featured]
---
Web table là một trong nhưng dạng đối tượng thường gặp trên các trang web hiện nay. Đối tượng này dùng để hiển thị các dạng thông tin dữ liệu ở dạng lưới gồm cột và hàng tương tự như một ma trận 2 chiều.

- Java8 là phiên bản có rất nhiều cải tiến đáng đồng tiền bát gạo. Một trong nhưng feature mới đó là là `Stream` giúp làm việc với các danh sách `List`

- `Comparator` class giúp lấy giá trị lớn nhất và bé nhất từ một danh sách.

- Kết hợp hàm `findElements() -> List<WebElement>` và `Stream` giúp chúng ta có thể dễ dàng làm việc với WebTable.


Trong ví dụ này mình có sử dụng thêm 1 thư viện đó là `Lombok`. Giúp viết các hàm `Getter & Setter` cũng nhưng các `Constructor` của một đối tượng đơn giản hơn.

### Với 1 table có dạng dưới đây

<table id="table1" class="tablesorter">
<thead>
    <tr>
    <th class="header"><span>Last Name</span></th>
    <th class="header"><span>First Name</span></th>
    <th class="header"><span>Email</span></th>
    <th class="header"><span>Due</span></th>
    <th class="header"><span>Web Site</span></th>
    <th class="header"><span>Action</span></th>
    </tr>
</thead>
<tbody>
    <tr>
    <td>Smith</td>
    <td>John</td>
    <td>jsmith@gmail.com</td>
    <td>$50.00</td>
    <td>http://www.jsmith.com</td>
    <td>
        <a href="#edit">edit</a>
        <a href="#delete">delete</a>
    </td>
    </tr>
    <tr>
    <td>Bach</td>
    <td>Frank</td>
    <td>fbach@yahoo.com</td>
    <td>$51.00</td>
    <td>http://www.frank.com</td>
    <td>
        <a href="#edit">edit</a>
        <a href="#delete">delete</a>
    </td>
    </tr>
    <tr>
    <td>Doe</td>
    <td>Jason</td>
    <td>jdoe@hotmail.com</td>
    <td>$100.00</td>
    <td>http://www.jdoe.com</td>
    <td>
        <a href="#edit">edit</a>
        <a href="#delete">delete</a>
    </td>
    </tr>
    <tr>
    <td>Conway</td>
    <td>Tim</td>
    <td>tconway@earthlink.net</td>
    <td>$50.00</td>
    <td>http://www.timconway.com</td>
    <td>
        <a href="#edit">edit</a>
        <a href="#delete">delete</a>
    </td>
    </tr>
</tbody>
</table>
  
### Test case : 
 - Kiểm tra ngừoi có có `Due` lớn nhất là `Doe Jason`

### Thực hiện

- Tạo  class `Person`
{% highlight java %}
@Data
public class Person {
    private final String lastName;
    private final String firstName;
    private final String email;
    private final float due;
    private final String website;

/**
Constructors and Getters Setters
**/
}
{% endhighlight %}    

- Tạo class `TableTest` :
{% highlight java %}
public class TableTest {

    @Test
    void getPersonWhoHasMaxOfDue() {
        WebDriver driver = new ChromeDriver();
        driver.get("https://the-internet.herokuapp.com/tables");
        List<WebElement> rows = driver.findElements(By.xpath("//table[@id='table1']/tbody/tr"));

        List<Person> persons = rows.stream()
                .map(this::toPerson).collect(Collectors.toList());

        Person largestDuePerson = persons
                .stream()
                .max(Comparator.comparing(Person::getDue))
                .orElseThrow(NoSuchElementException::new);

        Assert.assertEquals(String.format("%s %s", largestDuePerson.getLastName(), largestDuePerson.getFirstName()), "Doe Jason");

    }

    /**
     * element is a row in table
     *
     * @param element
     * @return
     */
    private Person toPerson(WebElement element) {
        String lastName = element.findElements(By.tagName("td")).get(0).getText();
        String firstname = element.findElements(By.tagName("td")).get(1).getText();
        String email = element.findElements(By.tagName("td")).get(2).getText();
        Float due = Float.valueOf(element.findElements(By.tagName("td")).get(3).getText().trim().replace("$", ""));
        String website = element.findElements(By.tagName("td")).get(4).getText();
        return new Person(firstname, lastName, email, website, due);
    }
}
{% endhighlight %}   
