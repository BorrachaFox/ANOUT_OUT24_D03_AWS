# Criar uma instância EC2

- Acesse o console da AWS e busque por EC2

![image](https://github.com/user-attachments/assets/4f1530f7-96ef-487a-ac51-3592732f8523)

- Acesse a aba instancias e selecione a opção **Executar instancia**

![image 1](https://github.com/user-attachments/assets/d0e7a822-a28e-4ede-b6c7-a549a3ca0b3e)

- Agora no Launch de criação da instância siga os passos abaixo para configurar a instância
- Em Nome e tags selecione adicionar mais tags, e adicione 3 tags:
    - **Name** → compasscar-api (nesse exemplo vamos usar esse nome)
    - **CostCenter** → test (manter test)
    - **Project** → test (manter test)
    - Em **Tipos de recurso** adicionar **Instâncias** e **Volumes em** todas as tags.

![image 2](https://github.com/user-attachments/assets/be18f54b-d4c2-4c91-ba41-6613183eee23)

![image 3](https://github.com/user-attachments/assets/ecb2c9ca-d076-4427-88d8-2df1bbe61025)

- Na hora de escolher o sistema operacional manter **Amazon Linux** (recomendado) e manter as configurações pré-definidas.

![image 4](https://github.com/user-attachments/assets/08a6048c-25b2-4e3b-b1e5-05fa395f66eb)

- Em tipo de instância, manter o que está:

![image 5](https://github.com/user-attachments/assets/8b740583-d2fe-4e43-89aa-2122652bd9a5)

- Em Par de Chaves, vá em **Criar novo par de chaves**.
    - **Nome do par de chaves →** compasscar-api-key
    - **Tipo de par de chaves →** RSA
    - **Formato de arquivo de chave privada →** .pem

![image 6](https://github.com/user-attachments/assets/f84a2f8d-ea22-483e-a792-6541d481a74c)

![image 7](https://github.com/user-attachments/assets/8cc0ff35-92f4-4ffd-bfa9-80bca1e21f1f)

- Após clicar em salvar o seu navegador vai fazer o download do arquivo .pem, nesse exemplo criei uma pasta chamada aws para facilitar na hora de acessar a instância.

![image 8](https://github.com/user-attachments/assets/9632f4df-0ebc-475d-8779-25a507104365)

- Após criação a chave já deve estar selecionada, se não tiver selecione, esse par de chaves também poderá ser usado em nova instâncias.

![image 9](https://github.com/user-attachments/assets/b674b7b7-897a-434e-b0eb-fec42d8260ac)

- Em **Configurações de Redes** marque as opções **Permitir tráfego HTTPS da Internet** e **Permitir** **Tráfego HTTP da Internet** depois clique em **Editar.**

![image 10](https://github.com/user-attachments/assets/fd0812de-39ff-48a3-b434-e3fefc92b158)

- Na tela de edição mude o **Nome do grupo de segurança** para **compasscar-api-security.**

![image 11](https://github.com/user-attachments/assets/4a800b34-6e64-4eaa-9107-c4dd0df6efe1)

- Na tela de edição em **Regras do grupo de segurança de entrada** clique em **Adicionar regra de grupo de segurança.**

![image 12](https://github.com/user-attachments/assets/01e84f57-0a2e-4299-8fc5-2cf7a649c927)

- Preencha os campos conforme abaixo:
    - **Tipo** → TCP personalizado
    - **Tipo de origem** → Qualquer lugar
    - **Intervalo de portas** → 3000 (nesse exemplo liberamos a porta 3000 mas pode ser a porta da sua aplicação node)
    
    ![image 13](https://github.com/user-attachments/assets/c0144256-f7b3-4863-9ae9-117ca476bc5f)

- Em **Configurar armazenamento** e **Detalhes avançados** mantenha como foi pré-definido

![image 14](https://github.com/user-attachments/assets/4b1565e6-1380-4803-8478-83b661e1da41)

![image 15](https://github.com/user-attachments/assets/609d2743-025e-4edf-940d-91d569165124)

- Por ultimo clique em **executar instância**.

![image 16](https://github.com/user-attachments/assets/a45ac815-0e97-4437-840c-8b693d01b936)

- Pronto a instância foi executada com sucesso, vá em visualizar todas as instâncias e a sua já estará listada.

![image 17](https://github.com/user-attachments/assets/751d8fed-0afd-419a-83d8-7cbda3dda09c)
