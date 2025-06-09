# Task 1 — What is Content Discovery?
**What is the Content Discovery method that begins with M?** `Manually`<br>
**What is the Content Discovery method that begins with A?** `Automated`<br>
**What is the Content Discovery method that begins with O?** `OSINT`
# Task 2 — Manual Discovery - Robots.txt
**What is the directory in the robots.txt that isn't allowed to be viewed by web crawlers?** `/staff-portal`<br>
# Task 3 — Manual Discovery - Favicon
**What framework did the favicon belong to?**<br>
La risposta è `cgiirc`. Si ottiene confrontando l'hash md5 ottenuto dal `md5sum` della favicon con il database favicons di OWASP.
# Task 4 — Manual Discovery - Sitemap.xml
**What is the path of the secret area that can be found in the sitemap.xml file?** `/s3cr3t-area`
# Task 5 — Manual Discovery - HTTP Headers
**What is the flag value from the X-FLAG header?**<br>
La flag è `THM{HEADER_FLAG}` e si trova nell'header personalizzato `X-FLAG` ottenuto mediante `curl http://10.10.219.29/ -v`.<br>
**Nota**: la convenzione di `X-` come prefisso negli header personalizzati è stata deprecata a Giugno 2012 nel [RFC 6648](https://datatracker.ietf.org/doc/html/rfc6648).
```*   Trying 10.10.219.29:80...
* TCP_NODELAY set
* Connected to 10.10.219.29 (10.10.219.29) port 80 (#0)
> GET / HTTP/1.1
> Host: 10.10.219.29
> User-Agent: curl/7.68.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.18.0 (Ubuntu)
< Date: Mon, 09 Jun 2025 10:04:25 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< X-FLAG: THM{HEADER_FLAG}
< ...
```
# Task 6 — Manual Discovery - Framework Stack
**What is the flag from the framework's administration portal?**<br>
La flag è `THM{CHANGE_DEFAULT_CREDENTIALS}` e si ottiene accedendo a `/thm-framework-login` con le credenziali `admin:admin` che sono riportate nella documentazione del framework su `https://static-labs.tryhackme.cloud/sites/thm-web-framework/documentation.html`.
# Task 7 — OSINT - Google Hacking / Dorking
**What Google dork operator can be used to only show results from a particular site?** `site:`
# Task 8 — OSINT - Wappalyzer
**What online tool can be used to identify what technologies a website is running?** `Wappalyzer`
# Task 9 — OSINT - Wappalyzer
**What is the website address for the Wayback Machine?** `https://archive.org/web/`
# Task 10 — GitHub
**What is Git?** `Content Version System`
# Task 11 — OSINT - S3 Buckets
**What URL format do Amazon S3 buckets end in?** `.s3.amazonaws.com`
# Task 12 — Automated Discovery
**What is the name of the directory beginning "/mo...." that was discovered?** `/monthly`<br>
**What is the name of the log file that was discovered?** `/development.log`<br><br>
Entrambe le risposte si possono ottenere utilizzando Gobuster in modalità `dir` con una delle wordlists di SecLists.<br>
`gobuster dir --url http://10.10.105.119/ -w /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt`<br>
<br>
Output:
```
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.105.119/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/SecLists/Discovery/Web-Content/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/assets               (Status: 301) [Size: 178] [--> http://10.10.105.119/assets/]
/contact              (Status: 200) [Size: 3108]
/customers            (Status: 302) [Size: 0] [--> /customers/login]
/development.log      (Status: 200) [Size: 27]
/monthly              (Status: 200) [Size: 28]
/news                 (Status: 200) [Size: 2538]
/private              (Status: 301) [Size: 178] [--> http://10.10.105.119/private/]
/robots.txt           (Status: 200) [Size: 46]
/sitemap.xml          (Status: 200) [Size: 1391]
Progress: 4655 / 4656 (99.98%)
===============================================================
Finished
===============================================================```
