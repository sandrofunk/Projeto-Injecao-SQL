# Projeto Injection SQL

## O que é SQL Injection

SQL Injection é um tipo de vulnerabilidade de segurança que ocorre quando um atacante é capaz de manipular um banco de dados inserindo ou "injetando" código SQL malicioso em uma consulta. Isso pode permitir que o atacante visualize, modifique ou exclua dados do banco de dados, levando potencialmente a acesso não autorizado a informações sensíveis. Os ataques de SQL Injection podem ter consequências graves e são uma preocupação significativa para qualquer organização que utilize bancos de dados para armazenar e gerenciar dados. É importante que os desenvolvedores empreguem medidas de segurança adequadas para prevenir vulnerabilidades de SQL Injection em suas aplicações.

Na página de login, um ataque de SQL Injection pode ocorrer quando os dados inseridos em campos de entrada, como nome de usuário e senha, não são adequadamente validados ou escapados antes de serem utilizados em consultas SQL para verificar as credenciais de login.

Um atacante pode aproveitar essa falha de segurança inserindo comandos SQL maliciosos nos campos de entrada. Por exemplo, em vez de inserir um nome de usuário e uma senha convencionais, o atacante pode inserir uma sequência de caracteres projetada para alterar o significado da consulta SQL original. Isso poderia permitir que o atacante contorne o processo de autenticação e faça login sem fornecer credenciais válidas.

Para mitigar esse tipo de ataque, é fundamental que as consultas SQL sejam parametrizadas e que a entrada do usuário seja devidamente validada e escapada para evitar a interpretação maliciosa como parte da consulta SQL. Além disso, a implementação de práticas de segurança, como o princípio do menor privilégio e o uso de listas de permissões (whitelists) em vez de listas negras (blacklists), pode ajudar a reduzir o risco de ataques de SQL Injection em páginas de login e em todo o sistema.

Por exemplo:

Suponha que a aplicação de login execute a seguinte consulta SQL para verificar as credenciais do usuário:

SELECT * FROM users WHERE username = 'input_username' AND password = 'input_password';

Se a aplicação não validar adequadamente e escapar os campos de entrada do usuário, um atacante mal-intencionado poderia inserir o seguinte no campo de nome de usuário:

  ' OR '1'='1 

Dessa forma, a consulta SQL resultante se tornaria:

  SELECT * FROM users WHERE username = '' OR '1'='1' AND password = 'input_password';

Neste caso, a condição '1'='1' sempre é verdadeira, o que significa que a consulta retornaria a primeira entrada da tabela de usuários, independentemente do nome de usuário e senha especificados. Com isso, o atacante poderia potencialmente contornar o processo de autenticação e obter acesso não autorizado ao sistema.

Para evitar esse tipo de ataque, é fundamental que as consultas SQL sejam parametrizadas e que a entrada do usuário seja devidamente validada e escapada para evitar a interpretação maliciosa como parte da consulta SQL.

## Os tipos comuns de SQL injection incluem:

1. **Injeção de SQL baseada em erro (Error-based SQL Injection)**: Neste tipo, o atacante insere dados que resultam em erros no banco de dados. Os dados de erro resultantes podem revelar informações sensíveis ou estrutura do banco de dados.

1. **Injeção de SQL baseada em tempo (Time-based SQL Injection)**: Neste tipo, o atacante introduz atrasos controlados nas consultas SQL para inferir informações do banco de dados com base no tempo de resposta.

1. **Injeção de SQL baseada em booleanos (Boolean-based SQL Injection)**: Aqui, o atacante explora a lógica booleana das consultas SQL para extrair informações do banco de dados.

1. **Injeção de SQL baseada em união (Union-based SQL Injection)**: Neste tipo, o atacante utiliza a cláusula UNION para combinar o resultado de uma consulta maliciosa com a consulta original, permitindo a recuperação de dados adicionais.

Esses são apenas alguns exemplos de como os atacantes podem explorar vulnerabilidades de SQL Injection para acessar informações não autorizadas em um banco de dados. É crucial entender e mitigar esses tipos de ataques implementando práticas de segurança apropriadas.
