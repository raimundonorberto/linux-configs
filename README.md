# Lembrete das configurações

### Configuração do Proxy:
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


