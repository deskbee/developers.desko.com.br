# Criando Aplicativo

Para realizar integração com API do Desko é necessaŕio criar um ClientApi no Painel Desko.

{% hint style="info" %}
Apenas usuários com Perfil **Admin** e **Master** possuem acesso ao menu integrações.
{% endhint %}

1. Acesso o Painel Desko, Integrações > ClientApi. e Clique em **Novo Cliente**

![](<../../.gitbook/assets/Desko-Painel (1) (2).png>)

2\. Informe um Nome para Identificar o Aplicativo e escolha os escopos que este aplicativo deve ter acesso.



![](<../../.gitbook/assets/Desko-Painel (2).png>)

{% hint style="warning" %}
Para um maior compliance, escolha apenas os escopos que o aplicativo precisa utilizar
{% endhint %}

4\. Após a criação clique no icone de visualização de dados

![](<../../.gitbook/assets/Desko-Painel (3).png>)

5\. Será exibido o **clientid**, **client_secret** e os **escopos**, estão são os 3 dados necessários para criar um Token de Autenticação (OAuth2).

![](<../../.gitbook/assets/Desko-Painel (4).png>)
