# Keep it Simple 

> Hello, today we will be solving a CyberTalents challenge about meta-data: [Keep it Simple](https://cybertalents.com/learn/introduction-to-cybersecurity/17-meta-data/challenges/keep-it-simple)

So, upon visiting this page, all we can see is an image and one input and hint that directs us to an image: ![image](https://user-images.githubusercontent.com/111907811/231579268-7e606a31-81f1-4277-8987-356f946fd793.png)

Let's try to view the page source of the page: 

```
<!DOCTYPE html>
<html>
<head>

 <link rel="stylesheet" href="styles.css">

<title>Keep it Simple</title>

</head> 

<body>

<center>

	<h1>Restircted Area</h1>
	<h2>Provide the secret to enter the safe</h2>
	<img src="img/the_eye.jpeg"  id="lii" >
	<form action="action.php" method="get">
  		<div class="container">
    		<label for="psw"><b>Password</b></label>
    		<input type="password" placeholder="Enter Password" name="password" required>
    		<button type="submit" name="submit">Login</button>
  		</div> 
	</form>
	</center>
	<img src="the_eye.jpeg" id="li" >
	<center>
	<p>Forget Secret, Need 
		<a href="Hint.JPG">Hint
		</a>
	</p>
</center>
</body>

</html>

```

We can find there is a hint image, upon visiting it, I didn't find anything usefull in it: ![image](https://user-images.githubusercontent.com/111907811/231579943-14d7fe21-f57d-4bd6-a44a-4dce08a922ab.png)

I checked there was an image with the name "the_eye.jpeg", I downloaded it to kali linux and tried to view the meta-data information of it with **exif** tool:

`exif the_eye.jpeg`

![image](https://user-images.githubusercontent.com/111907811/231580919-efb04bd0-87c0-486a-ba6d-9f4f87db14ea.png)

We can see in the output there is a flag in the "Rights" field: 
![image](https://user-images.githubusercontent.com/111907811/231580982-ecc8b433-19f3-4ccd-a731-fc5a85771a75.png)

> {S1mpl3sty_i$_th_@nswer}


Stay tuned for more!
