# Docker

## Conexão SSH

### Descobrindo o IP do servidor

```
ip addr show
```

### Conectando ao servidor

```
ssh <username>@<ip do servidor>
```

### Descobrindo a chave SSH do servidor

```
ssh-keygen -lf /etc/ssh/ssh_host_rsa_key.pub

or 

ssh-keygen -lf /etc/ssh/ssh_host_dsa_key.pub  # DSA key

or 

ssh-keygen -lf /etc/ssh/ssh_host_ecdsa_key.pub  # ECDSA key

or

ssh-keygen -lf /etc/ssh/ssh_host_ed25519_key.pub  # Ed25519 key
```

### Permitindo autenticação via password no servidor

```
sudo nano /etc/ssh/sshd_config
```

Então descomente #PasswordAuthentication yes. E reinicie o serviço:

```
sudo service ssh restart
```



