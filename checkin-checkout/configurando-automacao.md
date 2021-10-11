# Configurando

No Painel Desko Acesse **Integrações** , **Automação** e Clique em **Automação Checkin / Checkout**

{% hint style="info" %}
Apenas usuários com Perfil **Admin** e **Master** possuem acesso ao menu integrações
{% endhint %}

![](<../.gitbook/assets/Desko-Painel (1) (1).png>)

Crie uma Automação informando dados que poderão ser enviados.

| Campo                | Descrição                                                                                                                                                                                                             |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Executar a ação de   | Checkin / Checkout: Define qual ação automatizada será realizada quando a API do Desko receber a requisição do endpoint: `/integration/checkin`                                                                       |
| Código Dispositivo   | Código da Catraca ou Dispositivo que o usuário passou                                                                                                                                                                 |
| Prédio               | <p>Prédio Mapeado no Desko, esta ação faz o vinculo Dispositivo X Prédio.</p><p></p><p>Com isso o Desko obterm todas as reservas realizadas no Prédio, quando receber a requisição com este código de dispositivo</p> |
| Identificando Pessoa | Além de saber onde, precisamos saber Quem: Este campo definr qual parâmetro será enviado no endpoint `/integration/checkin` na Api do desko ára que possamos identificar qual usuário passou pelo dispositivo         |

![](<../.gitbook/assets/Desko-Painel 2(1).png>)
