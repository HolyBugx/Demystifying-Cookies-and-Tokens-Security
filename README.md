<img width="1440" alt="Screen Shot 2021-08-01 at 23 04 53" src="https://user-images.githubusercontent.com/71842138/127934378-ff958fd0-8307-405a-9ed5-ff6c405d4e37.png">

* The full article is posted on my [blog](https://securityflow.io/demystifying-cookies-and-tokens-security).
* The video presentation is shared [here](https://youtu.be/FZ_7xWZ03cQ).
* The presentation slides are shared [here](https://github.com/HolyBugx/Demystifying-Cookies-and-Tokens-Security/blob/main/presentation/Demystifying%20Cookies%20and%20Tokens%20Security.pdf).
* The exploit codes are shared [here](https://github.com/HolyBugx/Demystifying-Cookies-and-Tokens-Security/tree/main/exploits).
* Special thanks to [@voorivex](https://twitter.com/yshahinzadeh) for interactive dockerized labs!

## Labs installation

```
git clone https://github.com/HolyBugx/Demystifying-Cookies-and-Tokens-Security.git
cd Demystifying-Cookies-and-Tokens-Security
docker build -t samesite . --rm
docker run --name samesite -p 80:80 -v $PWD/another-site-mainsite.lab/:/var/www/app/another -v $PWD/same-site-mainsite.lab/:/var/www/app/main -v $PWD/xyz.subdomain.same-site-mainsite.lab/:/var/www/app/sub --rm samesite
```
The session's attribute can be changed by modifying `index.php`:
```php
session_set_cookie_params([
    'samesite' => 'Lax'
]);
```
Then add the following lines into the `hosts` file:
```
127.0.0.1 same-site-mainsite.lab
127.0.0.1 xyz.subdomain.same-site-mainsite.lab
127.0.0.1 another-site-mainsite.lab
```
## Credentials

```
Username: security
Password: flow
```
