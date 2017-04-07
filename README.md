# Lembrete das configurações

### Configuração do Proxy:

###### Nas variáveis de ambiente
 - Adicione as seguintes linhas no arquivo /etc/environment
```
MY_PROXY_URL="http://myproxy.com:3128/"
HTTP_PROXY=$MY_PROXY_URL
HTTPS_PROXY=$MY_PROXY_URL
FTP_PROXY=$MY_PROXY_URL
http_proxy=$MY_PROXY_URL
https_proxy=$MY_PROXY_URL
ftp_proxy=$MY_PROXY_URL
export HTTP_PROXY HTTPS_PROXY FTP_PROXY http_proxy https_proxy ftp_proxy
```

###### Apt-get
 - Adicione as seguintes linhas no arquivo /etc/apt/apt.conf
```
Acquire::http::proxy "http://<USUÁRIO>:<SENHA>@<ENDEREÇO DO PROXY>:<PORTA DO PROXY>/";
Acquire::https::proxy "https://<USUÁRIO>:<SENHA>@<ENDEREÇO DO PROXY>:<PORTA DO PROXY>/";
Acquire::ftp::proxy "ftp://<USUÁRIO>:<SENHA>@<ENDEREÇO DO PROXY>:<PORTA DO PROXY>/";
Acquire::socks::proxy "socks://<USUÁRIO>:<SENHA>@<ENDEREÇO DO PROXY>:<PORTA DO PROXY>/";
```

### Adicionando os Certificados:
###### Linux (Ubuntu, Debian)
 - Copie seu CA para o diretório /usr/local/share/ca-certificates/
  - **sudo cp foo.crt /usr/local/share/ca-certificates/foo.crt**
 - Atualize o CA store:
  - **sudo update-ca-certificates**

###### Linux (Fedora)
 - Se for o caso, converta o formato do arquivo CA de CRT para PEM:
  - **openssl x509 -in foo.crt -out foo.pem -outform PEM**
 - Copie seu CA para o diretório /etc/pki/ca-trust/source/anchors/:
  - **sudo cp foo.pem /etc/pki/ca-trust/source/anchors/**
 - Atualize o CA store:
  - **sudo update-ca-trust**


