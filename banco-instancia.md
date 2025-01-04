# Configurar PostgreSQL em uma Instância EC2

### Criando uma instância EC2 com a distro Ubuntu
- Em configurações de Redes clique em **Editar**
- Na tela de edição em Regras do grupo de segurança de entrada clique em **Adicionar regra de grupo de segurança.**
- Preencha os campos conforme abaixo:
  - Tipo → PostgreSQL
  - Tipo de origem → Qualquer lugar

  ![image](https://github.com/user-attachments/assets/84edefe4-2d23-4fd2-b785-70ac5d7b41e8)

### Instalando e Configurando Postgres
- Acesse o terminal do Ubuntu e atualize com o seguinte comando
```
sudo apt update && sudo apt upgrade -y
```
- Instale o PostgreSQL
```
sudo apt install postgresql
```
- Altere a senha do usuario padrão para a senha que desejar.

![image](https://github.com/user-attachments/assets/91054795-bf1c-4e12-a60e-c56f318533d4)

- Edite o arquivo X

![image](https://github.com/user-attachments/assets/9d2d9691-f617-441a-8011-c9353911b2a5)
![image](https://github.com/user-attachments/assets/e45baa7e-3e22-447d-b863-8c42c5f50620)

- Edite o arquivo Y

![image](https://github.com/user-attachments/assets/8b90efeb-276d-4148-af0d-950940ea2368)
![image](https://github.com/user-attachments/assets/1536e188-9e86-485b-9330-e24d4524fe29)

- reinicie o postgresql
```
sudo systemctl restart postgresql
```

Você pode acessar o db usando

![image](https://github.com/user-attachments/assets/1d4561ae-c418-42a4-a16e-a670eab56034)
