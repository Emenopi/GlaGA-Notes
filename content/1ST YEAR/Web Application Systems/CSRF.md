---
tags:
  - Web_Application_Systems
---
Cross Site Request Forgeries, also known as XSRF or Sea Surf - a type of web security vulnerability that tricks an authenticated user into unknowingly performing an action on a website they're logged into

Since the user is already logged into the website, their browser automatically sends their cookies and other auth info along with the attacker's forged request

In Django, adding the csrf_token tag takes care of the vulnerability