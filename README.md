* The full article is posted on my [blog](https://securityflow.io/demystifying-cookies-and-tokens-security).
* The video presentation is shared on youtube.
* The presentation slides are shared [here](https://github.com/HolyBugx/Demystifying-Cookies-and-Tokens-Security/blob/main/presentation/Demystifying%20Cookies%20and%20Tokens%20Security.pdf).
* The exploit codes are shared [here](https://github.com/HolyBugx/Demystifying-Cookies-and-Tokens-Security/tree/main/exploits). I recommend you to watch the presentation video as I shared several exploits in detail.
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
