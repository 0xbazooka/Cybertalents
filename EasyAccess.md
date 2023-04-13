## hello , today we're going to solve a very interesting challenge from cybertalents
 it's about SQL injection! [Easy Access](https://cybertalents.com/learn/introduction-to-cybersecurity/sql-injection/challenges/easy-access)


###  description 
> Only superpower makes you see unlimited view.


you will find a login form

![sqli](https://user-images.githubusercontent.com/130427754/231786251-2869af6e-be5f-4628-8c75-755c486ee6ab.png)

>Error-Based SQLi

 the first try is to inject a wrong payload to see if the error message returned by the database can reveal any sensitive information

![sqli(1)](https://user-images.githubusercontent.com/130427754/231788000-1e964092-a1f2-4526-a5c3-eab7a0e0febd.png)

the error message returned by the database shows the name of the database server which is `MariaDB` !

![sqli(2)](https://user-images.githubusercontent.com/130427754/231789116-6ad6dfe8-078d-4b62-a332-f80bd8fa6b6b.png)

the second try is to inject this payload
>` ' or 1=1; # `

![sqli(3)](https://user-images.githubusercontent.com/130427754/231793583-e6c0bd9f-c469-445d-9b03-4c22b4e7dbcc.png)

And VOILA ! we succeeded to inject 

 ![admin](https://user-images.githubusercontent.com/130427754/231812336-d2575905-34e8-4f96-8bad-e9d63034f8c6.png)

```
 
 flag{!njection_3v3ry_wh3r3}
 
```
