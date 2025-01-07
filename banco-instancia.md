# Configurar PostgreSQL em uma Instância EC2

### 1. Crie uma instância EC2 utilizando a distro do Ubuntu
- No Launch de criação da instância siga os passos abaixo para configurar a instância
- Em Nome e tags selecione adicionar mais tags, e adicione 3 tags:
    - **Name** → compasscar-postgresql (nesse exemplo vamos usar esse nome)
    - **CostCenter** → test (manter test)
    - **Project** → test (manter test)
    - Em **Tipos de recurso** adicionar **Instâncias** e **Volumes em** todas as tags
![image](https://github.com/user-attachments/assets/fbf7a6b2-4de4-415b-b49e-32ae97bea849)

- Na hora de escolher o sistema operacional manter **Ubuntu** (recomendado) e manter as configurações pré-definidas.

![image](https://github.com/user-attachments/assets/7bb570fb-45ef-4cd9-89a4-ab16104386b9)

- Em tipo de instância, manter o que está:

![image 5](https://github.com/user-attachments/assets/8b740583-d2fe-4e43-89aa-2122652bd9a5)

- Em Par de Chaves, vá em **Criar novo par de chaves**.
    - **Nome do par de chaves →** compasscar-postgresql-key
    - **Tipo de par de chaves →** RSA
    - **Formato de arquivo de chave privada →** .pem

![image](https://github.com/user-attachments/assets/4e409903-fc38-4c41-b273-f19cc6cadb66)

- Após clicar em salvar o seu navegador vai fazer o download do arquivo .pem, nesse exemplo criei uma pasta chamada aws para facilitar na hora de acessar a instância.

![image](https://github.com/user-attachments/assets/56114171-bfa0-40c1-b13c-aed7538b89ad)

- Após criação a chave já deve estar selecionada, se não tiver selecione, esse par de chaves também poderá ser usado em nova instâncias.

![image](https://github.com/user-attachments/assets/f3dc2dcb-6b49-437b-8546-ffef4bdf70d0)

- Em configurações de Redes clique em **Editar**
- Na tela de edição em Regras do grupo de segurança de entrada clique em **Adicionar regra de grupo de segurança. Preencha os campos conforme abaixo:
  - Tipo → PostgreSQL
  - Tipo de origem → Qualquer lugar

  ![image](https://github.com/user-attachments/assets/84edefe4-2d23-4fd2-b785-70ac5d7b41e8)

- Por ultimo clique em executar instância.

![image](https://github.com/user-attachments/assets/ee3e86ed-5440-4ee8-ace5-a1081d6f9c2d)

### 2. Acessando nossa instancia
- Selecione a instancia que deseja a qual deseja conectar na aba de **Instancias** e clique em conectar

![image](https://github.com/user-attachments/assets/407c0395-1de7-41a2-8961-57c30f5f098e)

- Vá para a aba cliente SSH e copie o exemplo de conexão

![image](https://github.com/user-attachments/assets/7a8707a3-8afa-45b6-9ca5-d9a6678e08d1)

- Abra o terminal na pasta em que salvamos o arquivo "compasscar-postgresql-key.pem" e execute o comando do exemplo de conexão

![image](https://github.com/user-attachments/assets/35e47ba8-fa43-4ed6-bfee-8aa3ca87df4a)

- Pronto estamos conectados !

### 3. Instalando e Configurando Postgres
- No terminal Ubuntu da nossa instancia EC2 rode o seguinte comando para atualizar nosso sistema:
```
sudo apt update && sudo apt upgrade -y
```
- Instale o PostgreSQL
```
sudo apt install postgresql
```
- Altere a senha do usuario padrão para a senha que desejar.

![image](https://github.com/user-attachments/assets/91054795-bf1c-4e12-a60e-c56f318533d4)

- Modifique o arquivo **postgresql.conf**
  - use ```sudo find / -name "postgresql.conf"``` para obter o caminho do arquivo.
  - use ```sudo nano <caminho_do_arquivo>``` para modificar o arquivo.

  ![image](https://github.com/user-attachments/assets/9d2d9691-f617-441a-8011-c9353911b2a5)

  - Tire o comentario de ```listen_addresses = 'localhost'``` e subtitua por ```listen_addresses = '*'```

  ![image](https://github.com/user-attachments/assets/e45baa7e-3e22-447d-b863-8c42c5f50620)

  - Use ```Ctrl + X``` para sair do arquivo.
  - Pressione ```Y``` para salvar as alterações e, em seguida, ```Enter``` para confirmar.

- Modifique o arquivo **pg_hba.conf**
  - use ```sudo find / -name "pg_hba.conf"``` para obter o caminho do arquivo.
  - use ```sudo nano <caminho_do_arquivo>``` para modificar o arquivo.

  ![image](https://github.com/user-attachments/assets/8b90efeb-276d-4148-af0d-950940ea2368)

  - Adicione o seguinte texto ao final do arquivo
  ```
  host    all             all              0.0.0.0/0                       md5
  host    all             all              ::/0                            md5
  ```

  ![image](https://github.com/user-attachments/assets/1536e188-9e86-485b-9330-e24d4524fe29)

  - Use ```Ctrl + X``` para sair do arquivo.
  - Pressione ```Y``` para salvar as alterações e, em seguida, ```Enter``` para confirmar.

- Após as configurações reinicie o postgresql
```
sudo systemctl restart postgresql
```

- Pronto, agora voce pode acessar o Bando de Dados a partir de qualquer maquina.
  - Vá no console da aws na lista de instâncias e clique para ver o detalhe dessa instância.
  - Copie o Endereço IPV4 Publico.
  ![image](https://github.com/user-attachments/assets/659ee1c1-1d0e-4a15-a21c-8e46aa15e7f4)

  - Acesse o banco de dados usando o seguinte comando
  ![image](https://github.com/user-attachments/assets/777c9e65-012c-47e2-9b5c-302d32b96159)

