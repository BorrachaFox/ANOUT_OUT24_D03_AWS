# Deploy da Aplicação Node

### 1. Criando um token de acesso pessoal no GitHub
- Como esse repositório é privado vamos precisar de um token de acesso para clonar o repositório futuramente na instancia EC2 da aws.
- No GitHub vá em:
    - Settings → Developer settings → Personal access tokens → Tokens (classic)
    - Configurações → Configurações do desenvolvedor → Tokens de acesso pessoal → Tokens (classico)
  
![image](https://github.com/user-attachments/assets/88bb1547-dbde-4159-b750-c6e08364ec25)
![image](https://github.com/user-attachments/assets/7795ebfa-a300-4e0c-8378-616267714629)
![image](https://github.com/user-attachments/assets/378a1720-b40e-43ea-9c8a-1c56da079287)
- Na tela de criação de token passe as seguintes informações
    - **Note (descrição)** → compasscar-api-aws
    - **Expiration (prazo de expiração)** → 30 days
    - **Select sopes (permissões)** → selecione a opção **repo**
    - Clique em **Generate Token** (Gerar token)
    - Depois de criado copie e guarde o token gerado, que será utilizado para clonar o repositório dentro da instancia ec2 na aws.
  
![image](https://github.com/user-attachments/assets/e89e61e2-1bac-494f-901c-2fff7b4c3d68)
![image](https://github.com/user-attachments/assets/bc54e509-a8f5-4a3d-abd3-6d7ef0610779)

### Acesse a maquina EC2
  
- Instale o git, node e pm2

- Agora vamos clonar o repositório seguindo os seguintes passos
    - vamos precisar do link do repositório e do token de acesso gerado no GitHub o link para clonar deve ter o seguinte formato:
        - [https://seu-user:token-de-acesso@github.com/seu-user/seu-repo.git](https://jailson273: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@github.com/jailson273/node-api-ec2.git)
        - git clone [https://seu-user:token-de-acesso@github.com/seu-user/seu-repo.git](https://jailson273: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@github.com/jailson273/node-api-ec2.git)

![image](https://github.com/user-attachments/assets/4f5d7eba-9b57-4339-a672-bcee341fc0d1)

### Navegue até a pasta do repositório que foi clonado e instale suas dependencias executando os comandos a seguir:
- ls
- cd node-api-ec2
- npm i
    ![image](https://github.com/user-attachments/assets/60c9db0a-ac8b-45c0-a623-e5a10c01ad00)

### Crie um arquivo.env com os dados nescessarios da aplicação:
- nano .env
- substitua <senha_do_banco_de_dados> pela senha que foi adicionada ao usuario **postgres** no banco de dados.
- substitua <ip_da_maquina_ecs> pelo ip da maquina ec2 em que o postgresql foi instalado
![image](https://github.com/user-attachments/assets/6584c2dd-79d0-40b6-9a38-96ffef82835c)

### Rode os comando nescessarios para configurar o prisma
- npx prisma generate
- npx prisma migrate dev

![image](https://github.com/user-attachments/assets/d037ff1b-55d7-423f-b23c-6f59511151f8)
![image](https://github.com/user-attachments/assets/906ccf94-e05c-4410-8121-97fbc9602487)

- Faça o build do projeto e inicie o servidor com **pm2**
    - npm run build
    - pm2 start dist/src/main.js --name compasscar-api
    - curl http://localhost:3000
 
![image](https://github.com/user-attachments/assets/f503a1bf-2e1e-46b2-adb3-534a3d4fa202)

- Pronto sua API está rodando na aws agora vamos testar o acesso de fora da instância.
    - Vá no console da aws na lista de instâncias e clique para ver o detalhe dessa instância.
        - Copie o DNS IPV4 Publico

          ![image](https://github.com/user-attachments/assets/35a9148a-0f3e-4c4a-8461-9f45a7a48a32)
        - No navegador cole o link substituindo https por http e passando a parta 3000

          ![image](https://github.com/user-attachments/assets/0dfe303d-4d6d-4aee-98cd-32173305d646)



