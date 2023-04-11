### hello hackers, today we're going to solve an easy web challenge from cybertalents
## Description 
> Come back home Mr. Bean.

pay attention to the description as it will help us ahead

![image](https://user-images.githubusercontent.com/99322823/231008050-f08a7606-d6e3-4eee-902d-dcf25683c021.png)

first we'll see the source code
```

<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8">
  <title></title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
</head>
<body>
	<img style="width: 80%; height: auto; margin-left: 20%;" src="./bean.jpg">
</body>
</html>
```
nothing of interest

next checked the `robots.txt` of the site, but found nothing

## Directory Enumerating
using `gobuster` I bruteforced the directories

```
gobuster dir -u http://wlemyw93xjyc7zr8r4gvmkxal3dmp6v4pjjefx3g-web.cybertalentslabs.com/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o gobuster.txt
===============================================================
Gobuster v3.5
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://wlemyw93xjyc7zr8r4gvmkxal3dmp6v4pjjefx3g-web.cybertalentslabs.com/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.5
[+] Timeout:                 10s
===============================================================
2023/04/10 16:41:20 Starting gobuster in directory enumeration mode
===============================================================
/files                (Status: 301) [Size: 185] [--> http://wlemyw93xjyc7zr8r4gvmkxal3dmp6v4pjjefx3g-web.cybertalentslabs.com/files/]

```

going to the `/files/` directory

![image](https://user-images.githubusercontent.com/99322823/231015632-8a1c5015-6996-44b6-872b-34df367870e9.png)

## Directory Traversal
Checked if it's vulnerable to path traverse `http://wlemyw93xjyc7zr8r4gvmkxal3dmp6v4pjjefx3g-web.cybertalentslabs.com/../../../../../`

but it just took me back to the mr. bean page

I scrolled through and found a `shadow` directory but its access was denied 

![image](https://user-images.githubusercontent.com/99322823/231015807-f37e6361-690f-4f9e-bfbb-628b67670f01.png)

but it gave us some valuable info: it's run on nginx, AND there was a directory named `nginx` so I went back and searched through it a bit and found something interesting 

## Nginx Alias

navigating to:
`/files/nginx/conf.d/default.conf `

```
server {
	listen 80;

	root /usr/share/nginx/html;

	index index.html;

	server_name _;

    autoindex on;

	location /files../ {
        alias /etc/;
    }
}
```
 the last two lines indicate it's vulnerable to alias path traversal
 
 for reading more about this vulnerability check this article [here](https://www.acunetix.com/vulnerabilities/web/path-traversal-via-misconfigured-nginx-alias/) 
 
 basically, that means if we write `/files../` it will go back one directory, and voila 

![image](https://user-images.githubusercontent.com/99322823/231026577-cc1c725e-3d61-4be4-bd4f-01872ab7e997.png)
 
 now the description comes in use "Come back home Mr. Bean."
 
 going to the `home/` directory we find the flag 
 
 ![image](https://user-images.githubusercontent.com/99322823/231026886-013ce3e9-6863-4132-b0b6-b6c0f8e02dbb.png)
![image](https://user-images.githubusercontent.com/99322823/231027047-7f16da22-1681-42c6-a8d8-4221309ee955.png)
