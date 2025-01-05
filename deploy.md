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

## Acesse a maquina EC2
  
- Instale o git, node e pm2

- Agora vamos clonar o repositório seguindo os seguintes passos
    - vamos precisar do link do repositório e do token de acesso gerado no GitHub o link para clonar deve ter o seguinte formato:
        - [https://seu-user:token-de-acesso@github.com/seu-user/seu-repo.git](https://jailson273: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@github.com/jailson273/node-api-ec2.git)
        - git clone [https://seu-user:token-de-acesso@github.com/seu-user/seu-repo.git](https://jailson273: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@github.com/jailson273/node-api-ec2.git)

  
