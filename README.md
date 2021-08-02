# Demystifying Cookies and Tokens Security

* Labs and materials of my talk on Cookies and Tokens Security.
* The article is on <https://securityflow.io/demystifying-cookies-and-tokens-security>
* The presentation is on <...> in which you can find more about several exploits.
* Special thanks to [@voorivex](https://twitter.com/yshahinzadeh) for interactive dockerized labs.

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
