# Entre no MySQL como um usuário que tenha permissões administrativas (por exemplo, o usuário root) usando o comando:

```
mysql -h localhost -u root -pDEVOPS12345
```

- Após entrar com a senha do usuário root, execute o seguinte comando para conceder permissões ao usuário wpuser para todas as origens (wildcard %):

```
GRANT ALL PRIVILEGES ON wpdb.* TO 'wpuser'@'%' IDENTIFIED BY 'DEVOPS12345'; FLUSH PRIVILEGES;
```
- Saia do MySQL usando EXIT.

- Tente agora conectar-se novamente usando o comando:

```
mysql -h mysql-service -u wpuser -pDEVOPS12345
```

- Certifique-se de que a senha DEVOPS12345 corresponda à que você definiu no YAML.



# Para validar os usuários criados no MySQL e suas permissões, você pode executar comandos SQL diretamente no servidor MySQL.

- Listar todos os usuários, isso mostrará todos os usuários e os hosts associados.:

```
SELECT User, Host FROM mysql.user;
```

- Mostrar as concessões (permissões) de um usuário específico:

```
SHOW GRANTS FOR 'nome_do_usuário'@'host';
```

Substitua 'nome_do_usuário' pelo nome do usuário e 'host' pelo host correspondente (pode ser % para qualquer host ou um IP específico).


- Mostrar todas as concessões para todos os usuários:

```
SELECT User, Host, Grant_priv, Super_priv FROM mysql.user;
```

# Comando K8S

- Acessar o pod do MySQL diretamente usando o comando kubectl exec 

```
kubectl exec -it NOME_DO_POD_DO_MYSQL -n SEU_NAMESPACE -- /bin/bash
```
