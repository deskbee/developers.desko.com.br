# Códigos Erros

Erros retornados pela API do Desko

| Código  | Mensagem              | ID                   | Mensagem                                                     |
| ------- | --------------------- | -------------------- | ------------------------------------------------------------ |
| 400     | Bad Request           | unexpected_value     | Dados enviados são inválidos ou inexistentes                 |
| 400     | Bad Request           | oauth_escope         | Scope Autenticação OAuth inválido                            |
| 401     | Unauthorized          | unauthenticated      | Não autorizado a acessar este métiodo                        |
| 401     | Unauthorized          | oauth_server         | Erro nas credenciais de acesso para gerar token JWT          |
| 401     | Unauthorized          | oauth_unauthorized   | Erro autorização na autenticação OAuth                       |
| 404     | Not Found             | not_found            | Endpoint não encontrado ou inexistente                       |
| 422     | Unprocessable Entity  | unprocessable_entity | Sua requisição contém parâmetros inválidos                   |
| 507     | Insufficient Storage  | query_error          | Não foi possível armzenar seus dados                         |
| 429     | Too Many Requests     | request_limit        | Você superou o limite de consumo, tente novamente mais tarde |
| 500     | Internal Server Error | internal_error       | Algo deu errado com o Servidor, notifique o problema         |

