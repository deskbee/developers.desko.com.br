---
description: >-
  Este documento apresenta o passo-a-passo para configuração do método de
  autenticação Single sign on para contas Google Suite.
---

# Google Suite

1.Acesse Admin Console [https://admin.google.com/ac/home?hl=en-US](https://admin.google.com/ac/home?hl=en-US)

2\. Esta documentação foi escrita utilizando Google Admin com a linguagem Inglês, caso ache necessário e sua linguagem esteja configurada diferente no Google Admin, altere a linguagem do seu Google para o inglês, para facilitar a compreensão dos passos.

## Criando Aplicativo Desko no Admin do Google

3\. Clique em **Apps**

![](<../.gitbook/assets/2 (1).png>)

4\. Clique em **Web and Mobile Apps**

![](<../.gitbook/assets/3 (1).png>)

5\. Clique em **Add App**, após em **Add custom SAML app**

![](<../.gitbook/assets/4 (1).png>)

6\. Informe o Nome do seu App e Clique em **Continue**

![](<../.gitbook/assets/5 (1).png>)

7\. Nesta etapa será exibido os dados de acesso por parte do Google, você deverá acessar o Painel Desko ([https://painel.desko.com.br](https://painel.desko.com.br)), utilizando um usuário e senha que lhe foi fornecido, pois será necessário realizar a troca de URLs e certificados entre o Provedor de Identidade (Google) e o Provedor de Serviço (Desko)

8\. Dados de Acesso do SSO do Google

![](https://lh5.googleusercontent.com/PcF489Uc5W-m6OsoqEeVdtlO2S6UkqhFxbuJw4PE-SbI2O3BL9TvfbBHfwWUC8gQOTeTGA-T5MZ6xHM4Cm0i5R0M8VqQLq37pm09OsSBdwLs6yv_YWKGwAtZ2u9Jx7S3p-nl7QSY=s0)

9\. Acesse o Painel Desko ([https://painel.desko.com.br](https://painel.desko.com.br))

![](https://lh3.googleusercontent.com/cr4ctdoS5wjPz2tMiH5WeEOwj8c1UH5aXep9J9bPFkTIGiT_wlor24miw5ABSbFNbQ8XIzBLJ_kxRdr8b3j1vPmRqEt163elsxm5xzZoJj3v27ElG266VrMTQ8c8kp20GGJsR5Qt=s0)

10\. Acesse o Menu **Integrações** / **Autenticações**.

O Acesso de Integrações / Autenticação é restrito aos Perfis TI e Super Usuários, verifique com o administrador se sua conta faz parte de um destes perfis.

![](<../.gitbook/assets/8 (1).png>)

11\. Habilite a **Autenticação SAML SSO**\
****

![](https://lh3.googleusercontent.com/Zd9W0T-LSMpEv74dA3MVxkFaQeciXubIdAjJXxRV7ZnUP5kUL40-j\_4x6u-07paevMBRpaFJhNXGH5oOKmW6elZ13hfRwJyys4sA_HuTgR5NVEgLZEx6k0xPHFPrNWwywoyhn6ax=s0)

\


12\. Informe um nome para a sua conexão\


![](https://lh4.googleusercontent.com/CfHBnt_ssS_zlBcmoABpXRU4CsGU5\_dONxzPKyBc8lPIRZWRsy1krW4wu9Tih493v7TGzEdxr8JhduUAEXUobUvXQPX6vyQlXykvESMXRzvO0i8OP9OZTnA1PCOAZi3zj5vusw_x=s0)

\


13\. Volte ao Google e copie as Urls fornecidas pelo Google no Painel Desko conforme demonstrado abaixo.



![](<../.gitbook/assets/11 (1).png>)

Campos do Google Equivalentes ao Campo no Painel Desko

| **Campo do Google** | **Campo do Painel Desko**               |
| ------------------- | --------------------------------------- |
| Entity ID           | ID da Identidade (Url do Identificador) |
| SSO URL             | URL de Login                            |

14\. No Google Admin baixe o certificado, clicando no ícone de Download\


![](<../.gitbook/assets/12 (1).png>)

15\. Volte ao Painel Desko, clique em **Atualizar certificado** no campo, **Certificado de Autenticação SAML (Base64)**, e faça o upload do certificado que você baixou\


![](<../.gitbook/assets/13 (1).png>)

16\. Após inserir as urls do google no Desko e fazer o upload do Certificado, Volte ao Google e clique em **CONTINUE**\


![](<../.gitbook/assets/14 (1).png>)

17\. Volte ao Painel Desko e Copie as URL de Configuração do Desko

No Painel do Desko em Configuração Básica de SAML, copie as urls existentes no seu Painel, as mesmas deverão ser informadas no Google\
**Esta imagem abaixo é apenas ilustrativa, verifique no PAINEL Desko as urls referentes a sua conta. Cada conta possui a sua URL específica** 

![](https://lh6.googleusercontent.com/NWRXQxYCijdlRonWMFyi8C2HLAc6RgRSAz5pzeS2gokMolwH1vZLCTQWgfV5G24eF-1HjdeeRTUnoocMJRXPnUEeztgXINHVBG3eSuKDFYKsIxq6BplbnJV2xM_Sr7j3K4X51rNO=s0)

****

18\. As urls disponíveis em **Configuração Básica de SAML** no Painel Desko devem ser adicionadas nos campos correspondentes do Google, conforme abaixo.

![](<../.gitbook/assets/16 (1).png>)

Urls do Painel Desko que correspondem as urls do Google\


| **Painel Desko**                                                           | **Google** |
| -------------------------------------------------------------------------- | ---------- |
| <p>Identificador<br>(ID da Entidade)</p>                                   | Entity ID  |
| <p>URL de Resposta ACS<br>(URL do Serviço do Consumidor de Declaração)</p> | ACS URL    |

19\. No Campo Name ID Format selecione a opção **PERSISTENT**\


![](<../.gitbook/assets/17 (1).png>)

20\. Campo Name ID, deve estar selecionada a **Opção Basic Information > Primary email,** e clique em **CONTINUE**\


21\. Clique em **ADD MAPPING** 3 vezes para inserir os 3 atributos de usuários (Claims)\


![](<../.gitbook/assets/19 (1).png>)

22\. Selecione no Google os 3 campos como **First Name**, **Last Name** e **Primary email,** e insira os atributos conforme demonstrado abaixo\


![](<../.gitbook/assets/20 (1).png>)

23\. Dados que devem ser inseridos\


| **Google Directory attributes** | **App Attributes**                                                 |
| ------------------------------- | ------------------------------------------------------------------ |
| First Name                      | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name         |
| Last Name                       | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/lastname     |
| Primary Email                   | http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress |

\
Para Integração com Google outros atributos/claims podem ser ignorados\


24\. Clique em **FINISH**\


25\. No Google lembre de Incluir usuários na aplicação do Google\
\


![](<../.gitbook/assets/21 (1).png>)

26\. Pronto basta acessar seu app do Desko **\<nomedaempresa>.desko.com.br** e clicar no Botao que você nomeou para login\


**27. Seja Feliz :)**

**Versionamento**

| **Versão** | **Author**                     | **Data**   |
| ---------- | ------------------------------ | ---------- |
| v1.5       | Cleber Rodrigues               | 12/07/2021 |
| v1.4       | Cleber Rodrigues               | 19/02/2021 |
| v1.3       | Cleber Rodrigues e Mário Verdi | 03/02/2021 |
| v1.2       | Cleber Rodrigues               | 08/10/2020 |
| v1.1       | Cleber Rodrigues               | 15/09/2020 |
| v1.0       | Mário Verdi                    | 13/09/2020 |
