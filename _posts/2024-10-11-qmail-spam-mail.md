---
title: 큐메일(Qmail) 스팸 메일 차단하기
date: 2024-10-11
categories:
- Qmail
tags:
- Qmail
---

이번에 내부 플랫폼 개발을 하면서 메일 서버가 필요해 우여곡절 설치 . 설정은 완료해서 끝났구나 싶었는데, <br/>
아니나 다를까 스팸 메일 공격을 받았다. 😫

원인을 확인해보니 직접적으로 우리 서버에 접속해서 한 것이 아닌, 외부에서 SMTP 서버에 접속하여 <br/>
메일을 무단으로 보내는 부분이 확인되었다.

Qmail에는 tcp.smtp 파일에서 특정 주소로부터 메일을 막아버릴 수가 있다. (예를 들어 스팸 메일) <br/>
다음과 같은 방식으로 내용을 추가하여 tcp.smtp에 추가해준 후 cdb 파일로 만들어 줍니다.

```
[root@ip-xxx-xx-x-xx control]# find / -name tcp.smtp
/etc/tcprules.d/tcp.smtp
[root@ip-xxx-xx-x-xx control] vi /etc/tcprules.d/tcp.smtp
```

tcp.smtp 파일에서 다음과 같이 수정을 합니다.
```
127.0.0.1:allow,RELAYCLIENT="",CHKUSER_RCPTLIMIT="50",CHKUSER_WRONGRCPTLIMIT="10"
{통신이 필요한 허용 IP}:allow,CHKUSER_RCPTLIMIT="50",CHKUSER_WRONGRCPTLIMIT="10",TLS="1"
:deny --> 그 외, IP는 모두 허용하지 않기
```

tcp.smtp.cdb 파일을 생성합니다.
```
tcprules /etc/tcprules.d/tcp.smtp.cdb /etc/tcprules.d/tcp.smtp.tmp < /etc/tcprules.d/tcp.smtp
```

추가적으로 보안을 더 꼼꼼하게 설정을 해야하지만, <br/>
기본적으로 다음과 같이 진행하면 SMTP 접속 부분에 대해서는 만족한다고 생각한다.