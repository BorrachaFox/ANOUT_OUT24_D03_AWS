# Criando e Publicando Documentação Swagger no S3 da AWS
### 1. Gerando arquivo html do swagger.

- Acesse a api no na rota **/api-json** e salve o conteudo em um arquivo **.json**.
  - use o comando **ctrl + s** para salvar o arquivo

  ![image](https://github.com/user-attachments/assets/33ecc19f-7160-413b-bd79-99e2554d4249)

- Salve o arquivo para que possamos acesssa-lo depois.

![image](https://github.com/user-attachments/assets/b31007a2-e478-4134-82cd-38241b38504e)

### convertendo o arquivo .json para .html
- Abra o terminal na pasta em que o arquivo foi salvo.
  - Instale a biblioteca redoc-cli: ```npm install -g redoc-cli```
  - Converta o arquivo .json para .html: ```redoc-cli bundle -o index.html swagger.json```

  ![image](https://github.com/user-attachments/assets/3c534963-3fc1-40f2-8083-7ff1a99c7da1)

## 2. Publicando no S3 da AWS
- Acesse o console da AWS e busque por S3.

![image](https://github.com/user-attachments/assets/ed0c302d-1b92-48b8-a554-964fc2d98e11)

- Vá em **buckets de uso geral** -> **Criar bucket**

![image](https://github.com/user-attachments/assets/9af3d7bf-c83f-4dd6-b98b-a4d5e5c39624)

- Agora na criação do bucket siga os passos abaixo para configurar a instância
  - Crie um nome para o bucket (o nome deve ser unico globalmente)

  ![image](https://github.com/user-attachments/assets/2db6bff1-fef1-438b-8850-2507161dca95)

  - Em propiedade de objeto selecione a opção **ACLs habilitadas** e deixe **Proprietário do bucket preferido** selecionado

  ![image](https://github.com/user-attachments/assets/cac6bc83-292c-4d4c-be3f-4e61946356b9)

  - Em Configurações de bloqueio do acesso público deste bucket, libere o acesso publico:
 
  ![image](https://github.com/user-attachments/assets/54fcf2c7-a3f6-495c-a72e-281533c3e459)

  - Por ultimo clique em criar bucket.

  ![image](https://github.com/user-attachments/assets/aeb9429b-bffb-41f1-af2a-96a694fa5fb2)

Pronto seu bucket foi criado, agora vamos adicionar o arquivo index.html que geramos anteriormente.

- Volte para a pagina de buckets de uso geral e acesse o bucket que foi criado.

![image](https://github.com/user-attachments/assets/7727d4c6-4f92-4fce-acd9-3cb4607f0ba4)

- Clique em carregar

![image](https://github.com/user-attachments/assets/f4c01d10-b42d-4671-aad8-068d7507cc18)

- Clique em adicionar arquivos, adicione o arquivo index.html que geramos anteriormente.

![image](https://github.com/user-attachments/assets/41586c07-2074-402f-8c1b-28b1b2c791e9)
![image](https://github.com/user-attachments/assets/77eac163-ef5a-4d3c-8e7b-be5e357fdef1)

- Após adicionar o arquivo index.html, clique em carregar.

![image](https://github.com/user-attachments/assets/bf0b7bff-641d-4d99-bcfd-b7de1c0c93ec)

- Acesse o bucket novamente e deixe o arquivo publico.
  - selecione o arquivo -> Ações -> Tornar publico usando ACL

  ![image](https://github.com/user-attachments/assets/d0783ead-3581-4236-bfba-abcafbe4efe6)

  - clique em **tornar publico**
  
  ![image](https://github.com/user-attachments/assets/ee2a0af0-821c-472a-8972-4bc6c569f1a9)

- Pronto, agora seu arquivo index.html já esta disponivel para ser acessado publicamente.
  - Selecione o arquivo e clique em copiar URL
  
  ![msedge_Ay2MbOrheO](https://github.com/user-attachments/assets/ac1a2e4d-dcba-4e45-a4da-5fa62d397e19)

  - Esta sera a URL de acesso publico do seu arquivo
 
  ![image](https://github.com/user-attachments/assets/6cfc20f5-9d17-4c6b-9ff7-7b43fac3747b)

  


  
