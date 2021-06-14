<h1>🔥 Ignite - Trilha NodeJS</h1>
<h3 align="center">Desafio 03 - Corrigindo o código</h3>
<h2>🚀 Sobre o desafio</h2>
<p>Nesse desafio, temos uma aplicação Node.js que está em processo de desenvolvimento mas que já possui os testes necessários para fazer toda a validação dos requisitos (você não deve mexer nos testes).
Após algumas alterações no código da aplicação, parte dos testes deixaram de passar e agora só você pode resolver esse problema. Bora lá? 🚀
Essa aplicação realiza o CRUD (**C**reate, **R**ead, **U**pdate, **D**elete) de repositórios de projetos. Além disso, é possível dar likes em repositórios cadastrados, aumentando a quantidade de likes em 1 a cada vez que a rota é chamada.
A estrutura de um repositório ao ser criado é a seguinte:</p>
<pre>{
  id: uuid(),
  title,
  url,
  techs,
  likes: 0
}</pre>
<p>Descrição de cada propriedade:</p>
<ul>
<li>id deve ser um uuid válido;</li>
<li>title é o título do repositório (por exemplo "unform");</li>
<li>url é a URL que aponta para o repositório (por exemplo "https://github.com/unform/unform");</li>
<li>techs é um array onde cada elemento deve ser uma string com o nome de uma tecnologia relacionada ao repositório (por exemplo: ["react", "react-native", "form"]);</li>
<li>likes é a quantidade de likes que o repositório recebeu (e que vai ser incrementada de 1 em 1 a cada chamada na rota de likes).</li>
</ul>
<p>Note que a quantidade de likes deve sempre ser zero no momento de criação.</p>
<h3>Rotas da aplicação</h3>
<p>Com o template já clonado e o arquivo <strong>index.js</strong> aberto, você deve completar onde não possui código com o código para atingir os objetivos de cada teste.</p>
<h4>GET /repositories</h4>
<p>A rota deve retornar uma lista contendo todos os repositórios cadastrados.</p>
<h4>GET /repositories</h4>
<p>A rota deve receber title, url e techs pelo corpo da requisição e retornar um objeto com as informações do repositório criado e um status 201.</p>
<h4>PUT /repositories/:id</h4>
<p>A rota deve receber title, url e techs pelo corpo da requisição e o id do repositório que deve ser atualizado pelo parâmetro da rota. Deve alterar apenas as informações recebidas pelo corpo da requisição e retornar esse repositório atualizado.</p>
<h4>DELETE /repositories/:id</h4>
<p>A rota deve receber, pelo parâmetro da rota, o `id` do repositório que deve ser excluído e retornar um status `204` após a exclusão.</p>
<h4>DELETE /repositories/:id</h4>
<p>A rota deve receber, pelo parâmetro da rota, o id do repositório que deve receber o like e retornar o repositório com a quantidade de likes atualizada.</p>
<h4>Específicação dos testes</h4>
<h4>Testes de repositórios</h4>
<ul>
<li><h5>Should be able to create a new repository</h5>
<p>Para que esse teste passe, você deve permitir que um novo repositório seja cadastrado pela rota <strong>POST</strong> /repositories. Caso precise confirmar o formato do objeto. 
Também é necessário que você retorne a resposta com o código <strong>201</strong>.</p>
</li>
<li><h5>Should be able to list the projects</h5>
<p>Para que esse teste passe, é necessário que você conclua o teste anterior. Se tudo ocorreu bem, os repositórios cadastrados deverão aparecerem na listagem da rota <strong>GET</strong> /repositories e esse teste irá passar.</p>
</li>
<li><h5>Should be able to update repository</h5>
<p>Para que esse teste passe, você deve permitir que um repositório seja atualizado a partir de seu id pela rota <strong>PUT</strong> /repositories/:id usando as informações recebidas pelo corpo da requisição.
Para que esse teste passe, você deve permitir que um repositório seja atualizado a partir de seu id pela rota <strong>PUT</strong> /repositories/:id usando as informações recebidas pelo corpo da requisição. Lembre-se de manter as informações que não foram passadas pelo corpo, por exemplo:
Se o usuário quiser trocar apenas o `title`, mantenha `url` e `techs` que já estavam no repositório.
<li><h5>Should not be able to update a non existing repository</h5>
<p>Para que esse teste passe, você deve verificar se o repositório existe antes de atualizar as informações na rota <strong>PUT</strong> /repositories/:id. Caso não exista, retorne um status 404 (que é o status para Not Found) com uma mensagem de erro no formato { error: "Mensagem do erro" }.</p>
</li>
<li><h5>Should not be able to update repository likes manually</h5>
<p>Para que esse teste passe, você deve impedir que a quantidade de likes de um repositório seja alterada manualmente através da rota PUT /repositories/:id.
Por exemplo:</p>
</li>

<h4>Errado:</h4>
<pre>// Repositório recém criado:
{
	id: "c160a99b-9d3b-4669-8a35-8dce1e8196ec",
	title: "Umbriel",
	techs: ["React", "ReactNative", "TypeScript", "ContextApi"],
	url: "https://github.com/Rocketseat/umbriel",
	likes: 0
}

// Requisição para alterar informações: 
// Rota: "/repositories/c160a99b-9d3b-4669-8a35-8dce1e8196ec"
// Método: PUT
// Corpo: { title: "Novo título", likes: 10 }

// Retorno:

{
	id: "c160a99b-9d3b-4669-8a35-8dce1e8196ec",
	title: "Novo título",
	techs: ["React", "ReactNative", "TypeScript", "ContextApi"],
	url: "https://github.com/Rocketseat/umbriel",
	likes: 10
}</pre>
<h4>Certo:</h4>
<pre>// Repositório recém criado:
{
	id: "c160a99b-9d3b-4669-8a35-8dce1e8196ec",
	title: "Umbriel",
	techs: ["React", "ReactNative", "TypeScript", "ContextApi"],
	url: "https://github.com/Rocketseat/umbriel",
	likes: 0
}

// Requisição para alterar informações: 
// Rota: "/repositories/c160a99b-9d3b-4669-8a35-8dce1e8196ec"
// Método: PUT
// Corpo: { title: "Novo título", likes: 10 }

// Retorno:

{
	id: "c160a99b-9d3b-4669-8a35-8dce1e8196ec",
	title: "Novo título",
	techs: ["React", "ReactNative", "TypeScript", "ContextApi"],
	url: "https://github.com/Rocketseat/umbriel",
	likes: 0 // A quantidade de likes não mudou
}</pre>
<list><h5>Should be able to delete the repository</h5>
<p>Para que esse teste passe, você deve permitir que um repositório seja excluído através do id passado pela rota DELETE /repositories/:id.</p>
</list>
</list><h5>Should not be able to delete a non existing repository</h5>
<p>Para que esse teste passe, você deve validar se o repositório existe antes de excluí-lo. Caso o repositório não exista, retorne um status 404 com uma mensagem de erro no formato { error: "Mensagem do erro" }.</p>
</list>
<h5>Testes de likes</h5>
</list><h5>Testes de likes</h5>
<p>Para que esse teste passe, deve ser possível incrementar a quantidade de likes em 1 a cada chamada na rota POST /repositories/:id/like. Use o id passado por parâmetro na rota para realizar essa ação.</p>
</list>
</list><h5>Should not be able to give a like to a non existing repository</h5>
<p>Para que esse teste passe, você deve validar que um repositório existe antes de incrementar a quantidade de likes. Caso não exista, retorne um status 404 com uma mensagem de erro no formato { error: "Mensagem do erro" }.</p>
</list>
</ul>




