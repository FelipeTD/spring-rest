# Spring-Rest
Repositorio para estudo do spring rest de acordo com mergulho Spring Rest da AlgaWorks

# Fundamentos de Rest
  - Principal evento de Java do mundo "Java One" agora conhecido como "Oracle Code One"
  - Principal evento de Spring do mundo "Spring One"

**O que é uma API (Application Programming Interface)?**
  - Interface de programação de uma aplicação
  - É um componente de software que possui um conjunto de funções que faz a intermediação do acesso as funcionalidades de alguns sistemas
  - Para fazer sentido uma API é necessário existir dois papéis:

**Software Consumidor <- API -> Software Provedor**
  - Basicamente é um software conversando com outro graças a uma API que o provedor disponibilizou
  - Web Services vs APIs. Web Services e APIs são a mesma coisa?
  - Web Services são um tipo de API. É uma API que fornece sua interface de comunicação pela internet. Quando falamos em Web Services estamos falando sobre Web API.
  - Por que devo aprender implementar web services? Por que toda comunicação que existe atualmente é feita a partir de web services.

**Exemplo**

**Software Restaurante <- API do IFood -> iFood**
  - Você pode utilizar a API do IFood no software do seu restaurante para conseguir utilizar os serviços do IFood.
  - Isso faz com que vários restaurantes possam automatizar seus processos de delivery

**REST**
  - REpresentational State Transfer
  - É uma estilo arquitetural para desenvolver web API
  - Não é uma tecnologia, não é uma ferramenta, não é uma biblioteca
  - É uma especificação que define a forma de comunicação entre componentes de software na web independente da linguagem de programação usada
  - Surgiu no inicio dos anos 2000 a partir da tese de PHD de um cientista chamado Roy Fielding
  - O intuito era a formalização de um conjunto de melhores práticas e regras para desenvolvimento de web services
  - Uma REST API é uma API que segue as regras especificadas pelo Roy Fielding

**Porque REST?**
  - Separação entre cliente e servidor. O cliente pode crescer independente do servidor
  - Escalabilidade. Se um servidor não é o suficiente podemos adicionar mais um sem ter que ficar replicando a sessão de uma máquina para outra. Qualquer máquina servidora pode atender qualquer requisição
  - Independência de linguagem. Podemos fazer o serviço com qualquer linguagem
  - Mercado. É mais fácil fazer a integração entre sistemas que utilizam REST.

**Constraints - Regras para ser considerado REST**
  - Deve ser cliente-servidor. Precisa de um cliente para consumir as chamadas feitas para o servidor. As aplicações devem poder evoluir sem qualquer dependência
  - Stateless. A aplicação não deve possuir estado. O servidor não pode manter uma sessão por exemplo
  - Cache. A API pode fazer cache das respostas das requisições. Por exemplo uma chamada de uma lista de cidades que não precisar ser feita a requisição toda vez
  - Interface Uniforme. Conjunto de operações bem definidas no sistema. Uma vez definida deve seguir religiosamente. Isso simplifica e desacopla a arquitetura. Isso permite que cada parte evolua de forma independente. Utilização dos verbos GET, POST, DELETE. A resposta de uma requisição também deve ser padronizada
  - Sistema em camadas. Diz que pode existir outros servidores entre o cliente e o servidor. Esses servidores podem fornecer uma camada de segurança, cache, balanceamento de carga. O cliente não deve conhecer quantas camadas existem no meio
  - Código sobre demanda. O servidor pode enviar como resposta de alguma requisição algum código que pode ser executado no cliente. Por exemplo, o servidor poderia retornar um código javascript responsável por montar um gráfico para o cliente executar em uma aplicação web e mostrar para o usuário

**Protocolo HTTP**

**Cliente -> Requisição -> Servidor**

**Servidor -> Resposta -> Cliente**

  - É um protocolo requisição-resposta. Ajuda a entender a constraint cliente-servidor
  - Composição de uma requisição. 

**[Método] [URI] HTTP/[Versão]**

**[Cabeçalhos]**

**[Corpo/Payload]**

  - Exemplo

**POST /produtos HTTP/1.1**

**Content-Type: application/json**

**Accept: application/json**

**{**

**"nome": "Notebook i7",**

**"preco: 2100.0**

**}**

**Métodos**

  - Existe uma especificação com um conjunto de métodos que podemos utilizar em requisições HTTP
  - GET. Método que indica que queremos um conjunto de dados do servidor
  - POST. Método que indica que vamos submeter para o servidor

**URI**

  - É um caminho que identifica o que queremos dentro de um servidor HTTP

**Cabeçalhos**

  - São informações sobre a requisição
  - São definidos por chaves e valores que podem ser utilizados pelo servidor para interpretar as requisições e executar as operações

**Corpo/Payload**

  - Não é obrigatório. Depende do método HTTP utilizado
  - É no corpo da requisição que enviamos os dados para o servidor API

**Composição da resposta**

**HTTP/[Versão] [STATUS]**

**[Cabeçalhos]**

**[CORPO]**

  - Exemplo

**HTTP/1.1 201 Created**

**Location: /produtos/331**

**Content-Type: application/json**

**{**

**"codigo": 331,**

**"nome": "Notebook i7",**

**"preco": 2100.0**

**}**

**Status**

  - Serve para dizer qual foi o resultado do processamento
  - O servidor deve retornar um status adequado para cada requisição para o cliente ficar sabendo o que aconteceu

**Cabeçalho**

  - Informações que o servidor envia junto com a resposta para o consumidor
  - Essas informações podem ser utilizadas pelo software consumidor para interpretar a resposta

**Corpo**

  - É onde fica o conteúdo da resposta
  - É opcional, pode ter ou não a resposta. Depende do caso

**Recursos REST (REST Resources)**

  - É qualquer coisa exposta na web como um documento, uma página, um vídeo, uma imagem e até mesmo um processo de negócio
  - É algo que tem importância suficiente para ser referenciado como uma coisa no software
  - Por exemplo em um e-commerce em um catalogo de produtos. Um único produto, uma nota fiscal, um pagamento. Tudo isso pode ser considerado como um resource
  - Um recurso único é conhecido como Singleton Resource
  - Uma coleção de recursos é conhecido como Collection Resource. Possui zero ou muitos recursos de um mesmo tipo

**Identificando Recursos**

  - URI. Uniform Resource Identifier. É um conjunto de caracteres que tem como objetivo dar uma especie de endereço para os recursos de forma não ambigua
  - URI vs URL. Uma URL é um tipo de URI. URL é Uniform Resource Locator. URI e URL são a mesma coisa dentro do contexto de recursos REST
  - Não é uma boa prática identificar um recurso utilizando verbos. O correto é utilizar substantivos. Exemplo listarProdutos pode ser escrito de forma correta como produtos
  - Deixa a API mais fácil e intuitiva para usar porque existe uma consistência na construção dela.
  - A diferenciação de o que será feito vai ser definida com a utilização do HTTP. Por exemplo, se eu quiser um retorno de produtos eu utilizo o GET
  - Para identificar um produto único podemos utilizar o código no final da requisição. Por exemplo /produtos/{codigo}
  - O ideal para o mercado é utilizar o substantivo sempre no plural
