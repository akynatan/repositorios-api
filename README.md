Praticando conceitos de Node Js

<img alt="GitHub language count" src="https://img.shields.io/github/languages/count/rocketseat/bootcamp-gostack-desafios?color=%2304D361">

<img alt="License" src="https://img.shields.io/badge/license-MIT-%2304D361">

Essa será uma aplicação para armazenar repositórios do seu portfólio, que irá permitir a criação, listagem, atualização e
remoção dos repositórios, e além disso permitir que os repositórios possam receber "likes".

Rotas:
- **`POST /repositories`**:
  A rota deve recebe `title`, `url` e `techs` dentro do corpo da requisição, sendo a URL o link para o github desse repositório.
  Ao cadastrar um novo projeto, ele deve ser armazenado dentro de um objeto no seguinte formato:
  `{ id: "uuid", title: 'Desafio Node.js', url: 'http://github.com/...', techs: ["Node.js", "..."], likes: 0 }`;
  Certifique-se que o ID seja um UUID, e de sempre iniciar os likes como 0.

- **`GET /repositories`**:
  Lista todos os repositórios;

- **`PUT /repositories/:id`**:
  Altera o `title`, a `url` e as `techs` do repositório que possua o `id` igual ao `id` presente nos parâmetros da rota;

- **`DELETE /repositories/:id`**:
  Deleta o repositório com o `id` presente nos parâmetros da rota;

- **`POST /repositories/:id/like`**:
  Aumenta o número de likes do repositório específico escolhido através do `id` presente nos parâmetros da rota.
  A cada chamada dessa rota, o número de likes deve ser aumentado em 1;
  
  Se dividirmos semânticamente as responsabilidades da nossa aplicação em entidades, o `like` seria uma entidade, e `repository` seria outra entidade.

Com essa separação, temos diferentes regras de negócio para cada entidade, assim, ao chamar a rota de `like` e adicionamos apenas um like, podemos interpretar que estamos criando um novo like, e não atualizando os likes.

Então por que não usar `PUT` no lugar de `POST`? Justamente por estarmos "criando" UM novo like, e não atualizando o número de likes para qualquer outro valor.

Talvez fique difícil enxergar por ser apenas um número, mas pense que cada like seja salvo em uma tabela no banco junto do usuário que realizou esse like. Agora fica mais claro que você está criando um novo like, certo?
