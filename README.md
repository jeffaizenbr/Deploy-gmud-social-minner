# Deploy-gmud-social-minner


#Criar QA Page

## 1 - Acessar o confluence pela url abaixo 
```bash
https://socialminer.atlassian.net/wiki/spaces/SIS/overview
```
## 2 - Acessar a ALLIN e clicar em Create Child, apos isso 
Preencher os campos conforme exemplo abaixo, e clicar em publish
```bash
cas | cas | client| app
```

## 3 - Copiar a rash e inserir na tabela, 
```bash
https://socialminer.atlassian.net/wiki/spaces/SIS/pages/2741862401/nave-mae+nave-mae+api+admin
```

## 4 - utilizar a query abaixo substituindo os respectivos items na query

```bash
SELECT * FROM service_gmud.Systems;

INSERT INTO service_gmud.Systems
(Id, Name, Namespace, `Type`, Description, QaPageId, Solution, Platform)
VALUES (null, 'client', 'cas', 'app', '...', '2741862401', 'cas', 'allin');
```

## 5 - Preencher planilha no banco, acessos abaixo: 
```bash
Conexão: localhost:30105
User: admin
Pass: G1tiPLr7Fd2M
```
## 6 - Acessar o caminho abaixo:
```bash
Databases>Service_gmud>Tables>Systems 
botao direito em systems e view data
```
## 7 - Utilizando o Dbeaver inserir a query do item "4" e seguir o caminho abaixo para isso.
```bash
SQL editor > newsql script
```

## 8 - Preencher como no modelo abaixo:
```bash
cas | cas | client| app
```

## 9 - Acessar o jenkins e criar o Pipe abaixo, modelo a ser utilizado para deploy de GMUD:
```bash
Dashboard>navemae>NEWnaveMaeAdminAPIJob
```
## 10 - campos a serem preenchidos abaixo:
```bash
X Este Build é parametrizado
Nome=Branch
Escolhas=none
		 homol
		 master
	```	 
>>>>>>>>>>>>>>Parâmetro String
```bash
Nome=GMUD_ID
```
>>>>>>>>>>>>>>Escolha
```bash
nome=SYSTEM_ID
escolhas=226
```
>>>>>>>>>>>>>>Escolha
```bash
nome=QA_PAGE
escolhas=2741862401XXXX
```
>>>>>>>>>>>>>>Pipeline
```bash
Definition=Pipeline Script from SCM
SCM=Git
Repository URL=git@code.allin.com.br:devops/devops-deploy.git
Branch Specifier (blank for 'any')= */master
```

## 11 - Baixar pipe para a maquina e modificar

#utilizar comandos do git para baixar para a maquina. 
```bash
git add .
git commit -m 'adding admin-api GMUD'
git push origin homol
```

## 12 - Acessar pasta da GMUD no jenkins, pela URL abaixo:
```bash
http://ci.allin.com.br/view/infra/job/GMUD/

## 13 - Clicar em create apos isso, configuração: 

## 14 - CLicar em configuração e selecionar extended choice
```
>>Name
```bash
SIS_ALLIN_CAS
```
>>value
```bash
226 | cas | client | app
```

## 13 - Acessar a opção GMUD no jenkins:

ir para o caminho Infra > GMUD > GMud create
