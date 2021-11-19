--- 
wordpress_id: 159
layout: post
title: Neward's paper on the OR mismatch and LINQ
wordpress_url: https://www.robsanheim.com/?p=159
---
<a href="https://blogs.tedneward.com/">Ted Neward</a> recently posted an <a href="https://msdn.microsoft.com/netframework/default.aspx?pull=/library/en-us/dndotnet/html/linqcomparisons.asp">extensive paper</a> comparing various OR solutions from over the years, including <a href="https://java.sun.com/products/jdbc/">JDBC</a>, <a href="https://www.service-architecture.com/database/articles/sqlj.html">SQLJ</a>, and <a href="https://wiki.rubyonrails.com/rails/pages/ActiveRecord">ActiveRecord</a>.  Of course, the paper finished up by showing .NET's upcoming solution with <a href="https://msdn.microsoft.com/netframework/future/linq/">LINQ </a>and how it "hopes to take a large step forward in minimizing the object-relational mismatch."  It allows you to code something like this (this retrieves Order, OrderDetails and Product in the Northwind db in one request):

[csharp]var custs = (
  from c in db.Customers
  where c.City == "London"
  select c )
  .Including(c => c.Orders
    .Including(o => o.OrderDetails
      .Including(od => od.Product)));

foreach (var cust in custs) {
  foreach (var ord in cust.Orders) {
    foreach (var orderDetail in ord.OrderDetails) {
      Console.WriteLine("CustomerID {0} has an OrderID {1} " + 
                        "with ProductID {2} that has name {3}.",
                            cust.CustomerID, ord.OrderID,
                            orderDetail.ProductID,
                            orderDetail.Product.ProductName);
    }
  }
}[/csharp]

Even with a higher level of abstraction such as Spring's <a href="https://www.springframework.org/docs/api/org/springframework/jdbc/core/JdbcTemplate.html">JdbcTemplate</a>, I can imagine it would be quite a bit nastier.  I'd love to see something like this come to Java, either in the next JDBC but more likely via Hibernate or Spring.  Go read the paper and <a href="https://blogs.tedneward.com/2006/01/11/LINQ+Paper+Comments+And+Feedback.aspx">let Ted know what you think</a>.
