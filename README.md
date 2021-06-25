## Fandemonium.pl

Stare strony internetowe nie słyną z dobrych zabezpieczeń, podobnie jest z fandemonium które wciąż cieszy się pewną popularnością,
do sprawdzenia jej skłonił mnie dość zabawny błąd, który można zobrazować tym "krótkim" url [fandemonium.pl/ifgprtl123456789u3h423...](), jest on najdłuższym bzdurnym adresem, na jaki odpowiada fandemonium i co ciekawe prowadzi on do tego mema:
<img align="left"
  src="https://github.com/prkx/fandemonium/blob/main/incydent.png">
</img>

Tylko dlaczego? Na fandemonium id nowego obrazka nie jest losowo generowane tylko inkrementowane i taką iteracją dochodzimy do obrazka fandemonium.pl/upload/file/404.png, pod który przekierowuje nas serwer, otrzymując kod 404, analogicznie dla innych kodów http.





**A teraz mała lista rzeczy do załatania.**


### Otwarte porty: 
```
  fandemonium.pl (79.96.24.117)
  PORT      STATE  SERVICE
  21/tcp    open   ftp       
  143/tcp   open   imap       
  465/tcp   open   smtps     
  1433/tcp  open   ms-sql-s
  3306/tcp  open   mysql
  5432/tcp  open   postgresql
```
![ftp](https://github.com/prkx/fandemonium/blob/main/ftp.png)

Rozwiązanie: ```Konfiguracja Firewalla ```
### Brak charsetu:
![charset](https://github.com/prkx/fandemonium/blob/main/charset.png)

Rozwiązanie: ```text/html;charset=utf-8 ```

### Wypisywanie błędów z php:
```
Deprecated: Function session_register() is deprecated in /inc/class.rejestracja.php on line 11
```
Rozwiązanie: ``` error_reporting(0); ini_set('display_errors', 0);```

### Brak flagi httponly
![httponly](https://github.com/prkx/fandemonium/blob/main/cookie.png)

Rozwiązanie:
```
setcookie(
    string $name,
    string $value = "",
    int $expires = 0,
    string $path = "",
    string $domain = "",
    bool $secure = false,
    bool $httponly = false  <---- ustawić na true
): bool
```
### Zły Content-Type przez co captcha przychodzi w takiej formie [captchatxt](https://github.com/prkx/fandemonium/blob/main/captcha.txt)
![Contentype](https://github.com/prkx/fandemonium/blob/main/ctype.png)

Rozwiązanie:
```
<?php
header('Content-Type: image/jpeg');
?>
```
### Brak captchy przy logowaniu + pole login_try które nieważne ile razy się loguje, zawsze jest ustawione na 1.
![login](https://github.com/prkx/fandemonium/blob/main/login.png)
### Http z logowaniem..
Rozwiązanie: [link](https://www.widzialni.pl/blog/jak-przeniesc-strone-na-https-instrukcja-krok-po-kroku)

Chyba już wystarczy 
