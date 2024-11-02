---
title: Nginx An Error occurred 에러
date: 2024-10-11
categories:
- Nginx
tags:
- Nginx
---

```
listen.acl_users와 listen.acl_groups 설정 비활성화
listen.acl_users와 listen.acl_groups가 설정된 경우, listen.owner와 listen.group 설정이 무시되므로, 아래처럼 주석 처리하여 비활성화 해주세요.
```

```
;listen.acl_users = nginx
;listen.acl_groups = nginx
```
PHP-FPM과 Nginx 설정 변경 후, 아래와 같이 재시작하여 설정이 적용되었는지 확인 합니다.

```
service php-fpm restart
nginx -t
nginx -s reload
```
Nginx와 PHP-FPM을 재시작하여 페이지를 확인해보면 정상 작동한 것을 확인할 수 있습니다.