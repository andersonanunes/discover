# Discover | Agregador de conteúdo
Este documento tem o objetivo construir um projeto de um agregador de conteúdo do zero, explorando de maneira prática a utilização de ferramentas como HTML, CSS, Javascript, Git e Github. O projeto conta ainda com protótipo do Figma utilizado como referência para a criação das páginas.

## ✒️ Autores
Seguem abaixo todos os responsáveis pela elaboração, criação e aplicação do projeto apresentado neste repositório.
**Anderson Nunes** - *Trabalho Inicial/Documentação*

## Documentação
**[Swagger](https://siteapihomolog.drconsulta.com/api-docs/swagger/)** - Documentação dos endpoints

## 🛠️ Tecnologias Envolvidas
* [HTML]
* [CSS]
* [Javascript]
* [Git]
* [Github]
* [Robot Framework versão 5.0](https://robotframework.org/)     - O framework usado
* [Python versão 3.10](https://www.python.org/)                 - Linguagem predominante
* [Github Actions](https://docs.github.com/pt/actions)          - Tecnologia CI/CD

## 🚀 Preparando o ambiente
Essas instruções permitirão que você obtenha uma cópia do projeto em operação na sua máquina local para fins de desenvolvimento e teste.

## 📋 Pré-requisitos
Quais ferramentas serão necessárias para poder executar os testes localmente?

**[Download do Python 3.10](https://www.python.org/downloads/)**

Após a instalação, execute o comando a seguir:

```bash
# Para verificar se a instalação do python foi feita com sucesso
$ python --version

# Para verificar se o pip foi instalado
$ pip --version
```

**[Download do VsCode](https://code.visualstudio.com/download)**

Extensões do **VSCode**

- **Material Icon Theme**
- **Python**
- **Robot Framework Language Server**

Ferramentas Opcionais

**[Download do CMDER](https://cmder.net/)**

**[Download do Postman](https://www.postman.com/downloads/)**


### Faça uma cópia do projeto clonando o repositório do GIT

```bash
# Clone o projeto para sua máquina
$ git clone https://github.com/andersonanunes/discover.git

# Acessar a branch
$ git checkout origin
```


## 🔧 Instalação do Robot Framework 5.0

Agora que temos o projeto disponível em nossa máquina e todas as ferramentas, vamos mostrar aqui como instalar alguns recursos que poderão nos ajudar no processo de automação. Para instalar o Robot Framework execute o comando a seguir:

```bash
# Comando para instalar o robot framework
$ pip install robotframework

# Para verificar se a instalação foi feita com sucesso
$ robot --version 
```


### Instalando as Libraries do nosso projeto.

Dentro do projeto de automação, temos um arquivo chamado **requirements.txt**. Este arquivo contêm todas as libraries (dependências) que serão necessárias para que possamos executar nossos testes sem problemas.

Quais as libraries necessárias?

-   **RequestsLibrary**
-   **Collections**
-   **OperatingSystem**
-   **JSONLibrary**
-   **JsonValidator**

### Onde encontrar as libs

-   **[robotframework.org](https://robotframework.org/#resources)**
-   **[pypi.org](pypi.org)**

```bash
# Para instalar uma nova library
$ pip install <nome_library>

# Para verificar as libraries instaladas
$ pip freeze

# Para gerar o arquivo requirements.txt a partir das libraries instaladas
$ pip freeze > requirements.txt

# Para reinstalar todas as libraries do projeto
$ pip install -r requirements.txt
```

Pronto! Agora é só começar a executar os testes...


## 📦 Arquitetura

Aqui iremos apresentar a arquitetura padrão do nosso projeto. A arquitetura de forma geral foi criada utilizando **Page Objects** pensando na fácil compreensão de todos que trabalharem com a automação. Focados em uma arquitetura limpa e que exigisse uma curva de aprendizado menor, chegamos a seguinte arquitetura:


Estrutura de Pastas que fazem parte do projeto:

<a href="https://imgbb.com/"><img src="https://i.ibb.co/HqJPfbP/estrutura-pastas.png" alt="estrutura-pastas" border="0"></a>

-   **api:**  Pasta responsável por armazenar todo o core do projeto como, configurações, massa e keywords do projeto como um todo.
-   **data:** Pasta que possui as massa de dados e mensageria dos testes como, credenciais de acesso ou validação de mensagens de erro ou sucesso.
-   **json:** Pasta contendo todos os payloads enviados nas requisições que precisam de um body, separadas por features.
-   **keywords:** Pasta com todas as keywords do projeto, separadas por features.
-   **reports:** Pasta responsável por armazenar todos os logs / reports pós execução e evidências.
-   **schemas:** Pasta contendo todos os schemas para validação da tipagem de dados de cada endpoint, separadas por features.
-   **tests:** Pasta responsável por armazenar os cenários BDD's de execução, separadas por features.


## ⚙️ Executando os testes

Para executarmos os testes, precisamos abrir o terminal integrado na pasta raiz do projeto.
Neste caso a raiz é a pasta qa-sitebff-robot.

#### Primeiro passo:

Vamos abrir o cmder (ou o terminal de sua preferência) e navegar até a pasta do projeto.

#### Segundo passo:

Para executarmos toda a suíte de testes existentes no projeto, devemos executar o seguinte comando:

```bash
# Comando para executar todos os testes do projeto
$ robot -d ./reports tests
```

Já para executarmos uma feature específica, devemos informar qual .robot queremos executar. Exemplo:

```bash
# Comando para executar features específicas
$ robot -d ./reports tests/site/Home.robot
```

Também podemos executar cenários específicos, desde que os mesmos possuam uma Tag única. 
Cada cenário possui uma ou mais tags, o que permite que sejam executados de maneira independente e agrupados de maneira específica.
Para isso, inserimos o comando -i e em seguida a tag que desejamos executar. Exemplo:

```bash
# Comando para executar um teste específico através de sua tag.
$ robot -d ./reports -i Smoke tests/site/Home.robot
```

Caso queira alterar o local onde os logs são salvos, basta ajustar o caminho após o -d.
Exemplo: Iremos passar no comando que os tests/logs serão salvos na pasta reports/home:

```bash
# Alterar o caminho após o -d
$ robot -d ./reports/home tests/site/Home.robot
```


## ℹ️ Boas Práticas

Pensando em boas práticas e padrões de desenvolvimento, levantamos alguns itens que devem ser seguidos a risca para que possamos ter êxito na questão de Design Patterns.

**Essas praticas consistem em:**

- **BDD:** Usar as features sempre em terceira pessoa [Advérbio + sujeito + verbo (Quando for ação)].
- **Variáveis:** Sempre criar dicionários e variáveis com letras maiusculas.
- **Keywords:** Todo texto validado não deve ser adicionado direto nas keywords. É esperado que o texto ou mensagem a serem validadas sejam armazenadas em variáveis.
- **Git:** É esperado que ao concluirmos o desenvolvimento, seja realizado um pull request para a branch develop. Após a aprovação do pull request, a branch de trabalho deverá ser excluída.



## 📌 Changelog

17.11.22 - Upload inicial do Projeto
10.07.23 - Inclusão do cenário de teste da rota /home
    - Validar endpoint GetHomeCms
Para executarmos a feature:
```bash
$ robot -N "Automação APIs BFF | Discover" -d ./reports -i GetHomeCms tests/site/Home.robot
```
11.07.23 - Inclusão dos cenários de teste rota /units:
    - Validar endpoint GetUnitsProducts
    - Validar endpoint GetUnitsProducts filtrando por unidade
    - Validar endpoint GetUnitsProducts filtrando por UF
    - Validar endpoint GetUnitsProducts filtrando por cidade
    - Validar endpoint GetUnitsProducts filtrando por grupo
Para executarmos a feature:
```bash
$ robot -N "Automação APIs BFF | Discover" -d ./reports -i Units tests/site/Units.robot
```




