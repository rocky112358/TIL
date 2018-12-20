# Docker certbot/certbot으로 LetsEncrypt 인증서 갱신하는 방법
```
docker run -it --rm --name [container_name] \
-v /path/to/save/certs:/etc/letsencrypt certbot/certbot certonly --manual -d [domain]
```
인증서 만료일이 가까워지면 인증서 발급할때 쓴 메일로 당신의 인증서가 곧 만료된다고 알림이 온다.
그 때 certbot을 위와 같이 실행하면 재발급을 진행한다.

재발급시 해당 도메인과 연결된 서버에 http로 acme-challenge를 한다.

## nginx
```
location /.well-known/acme-challenge {
  alias /var/www/html;
}
```

을 추가하고 reload 한 뒤, certbot에서 요구하는 파일명과 내용을 가진 파일을 /var/www/html/ 아래에 두면 된다.

##### 사족
```
location /.well-known/acme-challenge {
  root /var/www/html;
}
```

위와 같이 하면 /var/www/html/.well-known/acme-challenge/ 디렉토리를 들여다보고 404를 뱉으니 주의.
