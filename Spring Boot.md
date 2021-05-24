***Criando o projeto Spring Boot***

- Faço o download e instalação do STS pelo site https://spring.io/tools
- Para instalar o STS basta dar um duplo clique no arquivo que foi feito download
- Para criar um novo projeto selecione a opção Create new Spring Starter Project
- No campo Service URL não mude o conteúdo
- No campo Name você pode colocar o nome da sua API
- Use default location deve continuar selecionado
- Type será utilizado o Maven que é uma ferramenta de gerenciamento de dependências e automação de builds de projetos Java, mas poderia ser utilizado o Gradle
- Package será utilizado Jar
- Versão do Java será utilizada a versão 11 que é a LTS (última versão estavél)
- Linguagem Java - existem outras linguagens que podem ser utilizadas como o Kotlin
- Em Group você coloca o caminho dos seus packages, exemplo com.tortora. Group é o identificador do projeto no maven
- Dentro de um projeto podem existir vários artefatos. O nome do Artifact pode ser o mesmo do name
- Version pode continuar com a versão sugerida
- Description é uma descrição do projeto. Pode ser colocado qualquer coisa
- Package é o pacote básico. Pode ser utilizado o mesmo que foi colocado em Group. Será o caminho onde será colocado as classes da aplicação
- Clique em Next
- Na próxima tela será requisitado as dependências que serão utilizadas no projeto
- Primeiro devemos escolher qual a versão do Spring que vamos utilizar
- Selecione a dependência Spring Web, essa dependência vai configurar o que é necessário para desenvolver um projeto spring web com a ajuda do spring
- Clique em Next
- Na última tela será mostrado como será gerado o projeto
- O projeto é gerado não localmente mas por um serviço na web que está na base URL passando as configurações que estão na Full URL
- Esse comando vai baixar um arquivo .zip que será descompactado e adicionado no workspace
- Clique em Finish
- O Spring vai baixar as dependências que você ainda não tem no seu repositório local

***Estrutura projeto Spring Boot***

**Pom.xml**
- Project Object Model é o coração do projeto maven. É um arquivo que contém informações e configurações do projeto usadas pelo maven para fazer build
- Pom.xml não é um arquivo do Spring Boot é um arquivo do maven
- No começo do arquivo existe o <parent> com o link das configurações do Spring Boot
- Na verdade estamos herdando as configurações do Spring Boot dentro do arquivo do maven
- O projeto não fica pesado pois é baixado somente o que será utilizado
- Uma das configurações que podemos especificar no projeto são as dependênias que ficam dentro de dependencies
- A dependência spring-boot-starter-test não é adicionada no projeto final quando publicamos o serviço

**Maven Dependencies**
- É uma pasta lógica onde temos todos os arquivos .jar que foram adiconados ao nosso projeto
- Esses arquivos não ficam dentro do projeto, são uma referência do caminho onde estão armazenados

**Gerando um arquivo .jar**
- Chamado de FatJar que seria um Jar Gordo porque dentro dele estará tudo que a nossa aplicação precisa para ser executada
- Incluindo um servletContainer por exemplo o TomCat que é o padrão como se fosse um servidor web
- Vai ter todas as dependências utilizadas no projeto
- Para gerar o FatJar clique com o botão direito no projeto -> Run as -> Maven Build... -> será aberta uma janela de configuração
- Na janela que for aberta o que estiver dentro de Profile pode ser apagado
- Em Goals digite clean package ou seja limpar tudo depois empacote o projeto
- Clique em Run
- Depois que o Build for feito com sucesso a pasta target será preenchida
- O nome do FatJar nesse caso seria tortora-api-0.0.1-SNAPSHOOT.jar
- O arquivo pode ser executado pelo terminal com o comando java -jar tortora-api-0.0.1-SNAPSHOT.jar. Troque tortora-api-0.0.1-SNAPSHOT.jar pelo nome do seu arquivo .jar
- 


















