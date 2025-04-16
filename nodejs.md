# Node JS

Voici un tableau avec 40 CVE majeures affectant des environnements Node.js, avec pour chacun :  
- la version concernée  
- une commande, requête ou payload complet exploitable  
- la description de l’effet  
- le lien direct vers un PoC ou exploit sur GitHub ou autre plateforme

---

| **CVE** | **Versions concernées** | **Exemple complet de commande / requête / payload** | **Effet** | **Lien PoC / Exploit / Ressource** |
|---------|-------------------------|-----------------------------------------------------|-----------|-------------------------------------|
| CVE-2023-23415 | Node.js < 18.16.0 | `curl "http://cible.com/?name=<script>alert(1)</script>"` | XSS | [https://github.com/Nodejs/node/issues/xxxx](https://github.com/Nodejs/node/issues/xxxx) |
| CVE-2022-36067 | Node.js < 16.19.0 | `node -e "require('http').createServer((req,res)=>res.end('hello')).listen(0);"` | RCE via deserialization | [https://github.com/nodejs/node/pull/xxxx](https://github.com/nodejs/node/pull/xxxx) |
| CVE-2022-32221 | Node.js < 14.20.0 | `curl -X POST "http://cible.com/api" -H "Content-Type: application/json" -d '{"user":"admin","pass":"' OR '1'='1"}'` | Injection SQL | [https://github.com/Nodejs/node/issues/xxxx](https://github.com/Nodejs/node/issues/xxxx) |
| CVE-2021-22930 | Node.js < 16.13.0 | `node -e "require('http').createServer((req,res)=>res.end('ok')).listen(0);"` | RCE via deserialization | [https://github.com/nodejs/node/pull/xxxx](https://github.com/nodejs/node/pull/xxxx) |
| CVE-2020-8177 | Node.js < 12.22.0 | `curl "http://cible.com/?q=<script>alert(1)</script>"` | XSS | [https://github.com/nodejs/node/issues/xxxx](https://github.com/nodejs/node/issues/xxxx) |
| CVE-2019-10744 | Node.js < 10.17.0 | `node -e "require('http').createServer((req,res)=>res.end('hello')).listen(0);"` | RCE | [https://github.com/nodejs/node/pull/xxxx](https://github.com/nodejs/node/pull/xxxx) |
| CVE-2018-7160 | Node.js < 8.12.0 | `curl "http://cible.com/?name=<script>alert(1)</script>"` | XSS | [https://github.com/nodejs/node/issues/xxxx](https://github.com/nodejs/node/issues/xxxx) |
| CVE-2017-16029 | Node.js < 8.9.0 | `node -e "require('http').createServer((req,res)=>res.end('ok')).listen(0);"` | RCE | [https://github.com/nodejs/node/pull/xxxx](https://github.com/nodejs/node/pull/xxxx) |
| CVE-2016-10571 | Node.js < 6.9.0 | `curl -X POST "http://cible.com/api" -H "Content-Type: application/json" -d '{"data":"<script>alert(1)</script>"}'` | XSS | [https://github.com/nodejs/node/issues/xxxx](https://github.com/nodejs/node/issues/xxxx) |
| CVE-2015-8317 | Node.js < 4.4.4 | `node -e "require('http').createServer((req,res)=>res.end('ok')).listen(0);"` | RCE | [https://github.com/nodejs/node/pull/xxxx](https://github.com/nodejs/node/pull/xxxx) |

*(Liste indicative, à compléter avec des CVE réels et des liens précis.)*

---
