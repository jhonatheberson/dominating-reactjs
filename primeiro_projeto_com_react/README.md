# Criando projeto do zero

Não precisamos ficar criando projeto react de forma manual como fizemos antes.

podemos  usar o script react que já cria tudo para nos da seguinte forma:

~~~bash
yarn create react-app <nome do projeto>
~~~

com [typescript](https://create-react-app.dev/):

~~~bash
yarn create react-app <nome do projeto> --template typescript
~~~

com [next](https://nextjs.org/):

~~~bash
yarn create next-app <nome do projeto> --typescript
~~~

neste tutorial vamos usar a primeira opção, apenas com javascript:


~~~bash
yarn create react-app modulo05
~~~

com isso nã precisamo criar nosso projeto do zero, ele ja instala varias biblitecas necessarias para o desenvolvimento inicial como:

- [react-scripts](https://www.npmjs.com/package/react-scripts) ->  babel, webpack

- [react-dom](https://pt-br.reactjs.org/docs/react-dom.html) -> O pacote react-dom provê métodos específicos para o DOM que podem ser usados no nível superior de sua aplicação como uma válvula de escape para sair do modelo do React se você precisar. A maioria de seus componentes não devem precisar deste módulo.


- [react](https://pt-br.reactjs.org/)

- [web-vitals](https://web.dev/vitals/) ->  Web Vitals é uma iniciativa do Google para fornecer orientação unificada para sinais de qualidade essenciais para proporcionar uma ótima experiência ao usuário na web.

- [testing-library/jest-dom](https://github.com/testing-library/jest-dom#readme) ->  A @testing-library/jest-dombiblioteca fornece um conjunto de combinadores de jest personalizados que você pode usar para estender o jest. Isso tornará seus testes mais declarativos, claros para ler e manter.

- [testing-library/react](https://github.com/testing-library/react-testing-library) -> O React Testing Libraryé uma solução muito leve para testar os componentes do React. Ele fornece funções utilitárias leves em cima react-dome react-dom/test-utils, de uma forma que incentiva melhores práticas de teste. Seu principal princípio orientador é:


- [testing-library/user-event](https://www.npmjs.com/package/react-scripts) -> user-eventtenta simular os eventos reais que aconteceriam no navegador à medida que o usuário interage com ele. Por exemplo userEvent.click(checkbox), mudaria o estado da caixa de seleção.


foi incluido alguns scripts padrão:

- yarn *start* -> executar a,biente de desenvolvimento webpack
- yarn *build* -> executar ambiente de produção webpack leve
- yarn *test* -> executar os testes implementados
- yarn *eject* -> ele vai ejetar as configurações padrões para raiz do projeto assim podemos reconfigura-lo de forma mais funda, ou mudar algo que queremos


agora vamos linpar um pouco o prjeto retirando algumas coisas que não queremos:

## [eslint](https://eslint.org/)

  Aqui vamos retirar a configuração padrão do eslint porque vamos fazer a nossa, como preferimos.

## [public](https://github.com/jhonatheberson/dominating-reactjs/tree/master/primeiro_projeto_com_react/modulo05/public)

  Agora vou na pasta **public** e abrir arquivo inde.html e vou retirar os comentarios deixando de forma mais clean caso queira **opcional**

  também podemos excluir o [PWA](https://web.dev/add-manifest/) que é manifesto do aplicativo da web é um arquivo JSON que informa ao navegador sobre o seu Progressive Web App e como ele deve se comportar quando instalado na área de trabalho ou dispositivo móvel do usuário. Um arquivo de manifesto típico inclui o nome do aplicativo, os ícones que o aplicativo deve usar e a URL que deve ser aberta quando o aplicativo é iniciado. se não formos sar o PWA.


  para exluir vamos deletar a seguinte linha de comando:

  ~~~javascript
  <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
  ~~~

  e deletar o arquivo **public/manifest.json**

  ## [src](https://github.com/jhonatheberson/dominating-reactjs/tree/master/primeiro_projeto_com_react/modulo05/src)

  para editar nosso react precisamos ir no arquivo **App.js**

  vamos retirrar tudo que está dentro da div:

  ~~~javascript
  div className="App"
  ~~~

  colocando o:

  ~~~javascript
  <p>
    Hello World
  </p>
  ~~~

  aqui também temos alguns arquivos de estilização (App.css, index.css, logo.svg), testes (App.test.js, setupTests.js), e desempenho (reportWebVitals.js)

  caso não queremos usar podemos deletar esses arquivos ou substituir suas configurações.

  nesse caso vamos em deletar porque não vamos aproveitar esses estilos e nem os testes inicialmente

  assim ficando dentro da pasta **src/** apenas esses arquivos

  - App.js
  - index.js
  - reportWebVitals.js

  para isso funcinar precisamos retirar as importações dentro de [index.js](https://github.com/jhonatheberson/dominating-reactjs/blob/master/primeiro_projeto_com_react/modulo05/src/index.js) vou retirar a importação do css

  ~~~javascript
  import './index.css';
  ~~~

  ficando dessa forma:

  ~~~javascript
  import React from 'react';
  import ReactDOM from 'react-dom';
  import App from './App';
  import reportWebVitals from './reportWebVitals';

  ReactDOM.render(
    <React.StrictMode>
      <App />
    </React.StrictMode>,
    document.getElementById('root')
  );

  reportWebVitals();
  ~~~

  agora no **App.js** vou retirar as importanções

  ~~~javascript
  import logo from './logo.svg';
  import './App.css';
  ~~~

  no final meu arquivo [App.js](https://github.com/jhonatheberson/dominating-reactjs/blob/master/primeiro_projeto_com_react/modulo05/src/App.js) ficou assim:


  ~~~javascript

  function App() {
    return (
      <div className="App">
          <h1>
            Hello World
          </h1>
      </div>
    );
  }

  export default App;

  ~~~

  ### **OBS**: quando temos muitas configurações especificas não é muito legal usar **create react-app**, mas 99,9% é possivel utilizar sim **create react-app**.




# ESlint, Prettier & EditorConfig

  ## EditorConfig

  Iremos criar um padrão de escrita para isso, vamos utilizar a extenssão no VSCode [Editorconfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig) e [aqui](https://github.com/editorconfig/editorconfig-vscode) está o repositorio.

  ao clicar no botão direito no mause no raiz do projeto tem opção criar **Generate .editorconfig** em seguida ele irá criar o arquivo **./.editorconfig** que ja vem com algumas configurações, vamos alterar as seguinte coisas:

  - trim_trailing_whitespace = true
  - insert_final_newline = true


  ficando o arquivo dessa forma:

  ~~~json
  # EditorConfig is awesome: https://EditorConfig.org

  # top-most EditorConfig file
  root = true

  [*]
  indent_style = space
  indent_size = 2
  end_of_line = lf
  charset = utf-8
  trim_trailing_whitespace = true
  insert_final_newline = true
  ~~~

  pronto o editorconfig está configurado.

  ## ESlint

  Primerio coisa é adicionar o ESlint como dependenca de desenvolvimento:

  ~~~bash
  yarn add eslint -D
  ~~~

  agora vamos iniciar as configurações fazendo assim:


  ~~~bash
  yarn eslint --init
  ~~~

  vamos selecionar a opção **To check syntax, find problems, and enforce code style** em seguida **JavaScript modules (import/export)**, depois **React**, se tiver usando typescript, mark como **Yes**, em nosso caso não estamos usando então será **No**,como estamos utilizando o react no **Browser** iremos marcar essa opção.
  Vamos utilizar **Use a popular style guide** e seguida  **Airbnb: https://github.com/airbnb/javascript**, vamos marcar **JavaScript**, depois vamos autorizar as instalações apertando **Yes** enter

  por padrão o eslint instala usando [npm](https://www.npmjs.com/), como estamo usando o **yarn** vamos deletar o arquivo **package-lock.json** em seguida roda **yarn** na raiz do projeto.

  ~~~bash
  yarn
  ~~~

  ### OBS: certifique-se que npm está instalado em sua maquina



  ## Prettier

  para finalizamos o ***eslint** vamos instalar o prettier

  ~~~bash
  yarn add prettier eslint-config-prettier eslint-plugin-prettier babel-eslint -D
  ~~~


  agora vamos no arquivo **./.eslintrc.js** e vamos adiconar alguns **extends**:

  ~~~javascript
  extends: [
    'plugin:react/recommended',
    'airbnb',
    'prettier',
    'prettier/react'
  ],
  ~~~

  vamos adicionar um **parser**:

  ~~~javascript
  parser: 'babel-eslint',
  ~~~

  e vamos adicionar **glugins**

  ~~~javascript
  plugins: [
    'react',
    'prettier'
  ],
  ~~~

  agora vamos adicionar alguma **rules** de **Airbnb**:

  ~~~javascript
  rules: {
    'prettier/prettier': 'error', //aponta qualquer regra que ele não encontrar como erro
    'react/jsx-filename-extension': [
      'warn',
      { extensions : ['.jsx','js'] } //isso faz que ele não reclame de de codigo jsx(html) em arquivos js
    ],
    'import/prefer-default-export': 'off' //desativa a regra que export não seja default ele não reclame
  },
  ~~~

  vamos criar o seguinte arquivo na raiz do projeto **.prettierrc**

  com seguinte conteudo

  ~~~json
  {
  "singleQuote": true,
  "trailingComma": "es5"
  }
  ~~~

  ### OBS: prettier deixa codigo mais bonito e eslint procura por erros dentro do codigo.

# Roteamento no React
  simgle page application para usar isso vamos utilizar biblioteca **react-route-dom**
  ,ou seja uma aplicação de uma unica pagina, nunca irá recarregar ao não ser que apertamos *F5*

  para instalado baixa executar o comando abaixo:

  ~~~bash
  yarn add react-router-dom
  ~~~

  que é para fazer routeamento do front-end

  primeiramente vamos criar o arquivo de rotas **/src/routes.js**

  agora vamos criar uma pasta **src/pages**

  dentro de **pages** vai ter inicialmente uma pasta **pages/Main** com arquivo *index.js* **/src/pages/Main/index.js**

  também vou criar um pasta **/pages/Rpository** dentro dela também dera um arquivo **index.js**

  ficando assim nossa estrura de diretorios no **pages**:

  - pages
    - Main
      - index.js
    - Repository
      - index.js


Vamos criar um roteamento mais simplex inicialmente:

primerio de tudo vamos criar o que sra exibido na **/pages/Main/index.js**

essa será nossa roda default **localhost:3000/**, dessa forma o conteudo da do arquivo ****/pages/Main/index.js**** está assim:

~~~javascript
import React from 'react';

// import { Container } from './styles';

function Main() {
  return <h1>Main</h1>;
}

export default Main;
~~~

para criar essa estrutura default podemos utilizar o snippets da rockseat digitando **rfc** que significa r - react, f - function, c - component.

da mesma forma o arquivo **/pages/Repository/index.js**

essa roda será **localhost:3000/repository**, dessa forma o conteudo da do arquivo ****/pages/Main/index.js**** está assim:

~~~javascript
import React from 'react'

export default function index() {
  return (
    <h1>Repository</h1>
  )
}
~~~

agora vamos adicionar nossas rotas no arquivo **routes.js** assim:

~~~javascript
import React from 'react';
import { BrowserRouter, Switch, Route } from 'react-router-dom'

import Main from './pages/Main';
import Repository from './pages/Repository';

    
// o BrowserRouter faz que as rotas possa ser criadas ex: http://localhost:3000/repository
//o Swith garente que seja chamado apenas um unico componente por vez 
export default function Routes() {
  return (
    <BrowserRouter>
      <Switch> 
        <Route path="/" exact component={Main} />
        <Route path="/repository" component={Repository} />
      </Switch>
    </BrowserRouter>
  );
}

~~~

### OBS: perceba que tem **exact**, porque para comparar com igualdade precisamos adicionar *exact* no componente para ele poder diferencia realmente, porque sem o *exact* vai ser verdade porque ele não vai olhar toda a roda, apenas o primeiro caractere e já retorna verdadeiro.

agora para finalizar precisamos colocar as rotas para funcionar, indo no arquivo **src/App.js**

e vamos importar o componente **Routes**

~~~javascript
import Routes from "./routes";

function App() {
  return (
    <Routes />
  );
}

export default App;
~~~

## Lembrando sempre que tudo em react são components

# Styled components

  essa biblioteca muda a forma como adicionamos e increvemos **CSS** em aplicações react e react-native

  vamos adicionar uma biblioteca chamada **styled-component**


  ~~~bash
  yarn add styled-components
  ~~~

  agora vamos adicionar essa nova estilização no **Main/index.js**,
  para utilizar estilização CSS default, precisamos colocar uma estilização em cada componente do HTML, tipo:

  ~~~javascript
  import CSS from fileCSS;

  function Main() {
    return <h1 className='stily'>Main</h1>;
  }

  export default Main;
  ~~~

  porém isso é problema quando a plicação é grande, está estilizando todo o h1, logo ele não está **escopado**, logo o **styled-component** resolve é todo CSS desse componente não será compartilhado, a não ser que o que queiramos.

  para isso vamos criar uma arquivo **/src/pages/Main/styles.js**


  vamos criar um component estilizado:


  ~~~javascript
    import styled from 'styled-components'

    export const Title = styled.h1`
      font-size: 24px;
      color: #7159c1;
      font-family: Arial, Helvetica, sans-serif;
    `;
  ~~~

  agora para adicionar a estilização na main precisamo importa **styles.js** e adicionar o componente **Title**:




  ~~~javascript
    import React from 'react';

    import { Title } from './styles';

    function Main() {
      return <Title>Main</Title>;
    }

    export default Main;
  ~~~


  ## Encadeamento de estilos

  isso é para quando eu tenho por exemplo um estilização do componente **Title** que é **h1** e dentro dessa componente quero fazer outra estilização por exemplo do **small** para isso basta modificar um pouco fazendo as seguintes mudanças:

  ~~~javascript
    import styled from 'styled-components'

    export const Title = styled.h1`
      font-size: 24px;
      color: #7159c1;
      font-family: Arial, Helvetica, sans-serif;

      small{
        font-size: 14px; 
        color: #333;
      }
    `;
  ~~~

  e mofiicando o **index.js**

  ~~~javascript
  import React from 'react';

  import { Title } from './styles';

  function Main() {
    return (
        <Title>
          Main
          <small>menor</small>
        </Title>
      );
  }

  export default Main;
  ~~~

  ## Utilizando funções para modificar estilizaçãoes

  controlar propriedades do CSS com funções.
  acessando propriedades dos elementos tipo assim:



  ~~~javascript
  import React from 'react';

  import { Title } from './styles';

  function Main() {
  return (
      <Title error={true}>
        Main
        <small>menor</small>
      </Title>
    );
  }

  export default Main;
  ~~~

  perceba o que mudou foi agora estou passando um valor chamado **error** como true.

  e agora vou acessar esse alementos dentro do **styles.js**

  ~~~javascript
  import styled from 'styled-components'

  export const Title = styled.h1`
    font-size: 24px;
    color: ${props => props.error ? 'red' : '#7159c1'};
    font-family: Arial, Helvetica, sans-serif;

    small{
      font-size: 14px; 
      color: #333;
    }
  `;
  ~~~

  perceb que aqui estou usando uma função poderia ser uma mais complexa

  ~~~javascript
  color: ${props => props.error ? 'red' : '#7159c1'};
  ~~~

  estou acessando a propriedade **error** do component

  # Estilos globais

  definindo estilos globais, esses estilos compartilhados, estylos de bory da aplicação.


  para isso vamos criar pasta **/src/styles/**

  em seguida vamos criar um arquivo **global.js**


  ~~~javascrip
  import { createGlobalStyle } from 'styled-components'

  export default createGlobalStyle`
    * {
      margin: 0; /* removendo margin */
      padding: 0; /* removendo padding */
      outline: 0; /* removendo outline */
      box-sizing: border-box; /* evita quebra de leyaout, os elementos fica somando, o conteudo é exprimido */
    }

    html, body, #root {
      min-height: 100%; /* ocupando 100% da pagina */
    }

    body {
      background: #7159c1;
      -webkit-font-smoothing: antialiased ! important
    }

    body, input, button {
      color: #222;
      font-size: 14px;
      font-family: Arial, Helvetica, sans-serif;
    }

    button {
      cursor: pointer;
    }
  `;


  ~~~

  agora para aplicar essa estilização global precisamos colocar no arquivo **App.js** importando e adiconado o componente.

  ~~~javascript
  import Routes from "./routes";
  import GlobalStyle from './styles/global';

  function App() {
    return (
      <>
        <Routes />
        <GlobalStyle />
      </>
    );
  }

  export default App;
  ~~~
  

  # Estilizando página Main

  nossa aplicação vai consumir a API do github para isso vamos estilizar a pagina principal.


  vamos adicionar icons, para isso vamos adicionar o pacote:

  ~~~bash
  yarn add react-icons
  ~~~

  vamos importar e CTRL + SPACE, ele mostra todo o que tem.



  se quero estilizar o compotanmento do alguma coisa, preciso criar um componente para fazer a estilização.


  nosso arquivo de stilização ficou assim:

  ~~~javascript
  import styled from 'styled-components'

  export const Title = styled.h1`
    color: #fff;
    /* font-size: 24px;
    color: ${props => props.error ? 'red' : '#7159c1'};
    font-family: Arial, Helvetica, sans-serif;

    small{
      font-size: 14px; 
      color: #333;
    } */
  `;
  
  export const Container = styled.div`
    max-width: 700px; /*definindo largura maxima para conteiner */
    background: #fff; /* cor de fundo branco*/
    border-radius: 4px; /* a o radio de borda de 4px*/
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    padding: 30px; /*espaçamento interno de 30px */
    margin: 80px auto; /* margem em cima de 80 px, e nas latereais como auto, assim ficando centralizado*/
    
    h1{
      font-size: 20px;
      display: flex;
      flex-direction: row;
      align-items: center; /* ficar alinhado o texto e icons */
    }
    svg {
      margin-right: 10px; /*espaçamento do icons com texto */
    }
  `;
  export const Form = styled.form`
    margin-top: 30px; /*margin de cima, para ficar com espaçamento do h1 para form */
    display: flex; 
    flex-direction: row; /*garente que o buton mais, e form fica um ao lado do outro */

    input {  export const Title = styled.h1`
    color: #fff;
    /* font-size: 24px;
    color: ${props => props.error ? 'red' : '#7159c1'};
    font-family: Arial, Helvetica, sans-serif;

    small{
      font-size: 14px; 
      color: #333;
    } */
  `;
  
  export const Container = styled.div`
    max-width: 700px; /*definindo largura maxima para conteiner */
    background: #fff; /* cor de fundo branco*/
    border-radius: 4px; /* a o radio de borda de 4px*/
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    padding: 30px; /*espaçamento interno de 30px */
    margin: 80px auto; /* margem em cima de 80 px, e nas latereais como auto, assim ficando centralizado*/
    
    h1{
      font-size: 20px;
      display: flex;
      flex-direction: row;
      align-items: center; /* ficar alinhado o texto e icons */
    }
    svg {
      margin-right: 10px; /*espaçamento do icons com texto */
    }
  `;
  export const Form = styled.form`
    margin-top: 30px; /*margin de cima, para ficar com espaçamento do h1 para form */
    display: flex; 
    flex-direction: row; /*garente que o buton mais, e form fica um ao lado do outro */

    input {
      flex: 1; /*isso faz com que o form ocupe todo espaço possivel */
      border: 1px solid #eee;
      padding: 10px 15px; /* altura e largura de 10px e 15px */
      border-radius: 4px; /*aredonda a borda do input */
      font-size: 16px; /*tamanho da fonte */
    }
  `;
  export const SubmitButton = styled.button.attrs({
    type:'submit'
  })`
    background: #7159c1;
    border: 0;
    padding: 0 15px;
    margin-left: 10px;
    border-radius: 4px;

    display: flex;
    justify-content: center;
    align-items: center;

  `;
      flex: 1; /*isso faz com que o form ocupe todo espaço possivel */
      border: 1px solid #eee;
      padding: 10px 15px; /* altura e largura de 10px e 15px */
      border-radius: 4px; /*aredonda a borda do input */
      font-size: 16px; /*tamanho da fonte */
    }
  `;
  export const SubmitButton = styled.button.attrs({
    type:'submit'
  })`
    background: #7159c1;
    border: 0;
    padding: 0 15px;
    margin-left: 10px;
    border-radius: 4px;

    display: flex;
    justify-content: center;
    align-items: center;

  `;
  ~~~

  e o arquivo **index.js** com seus componentes:


  ~~~javascript
  import React from 'react';

  import { Container, Form, SubmitButton } from './styles';

  import { FaGithubAlt, FaPlus } from 'react-icons/fa'

  function Main() {
    return (
        <Container>
          <h1>
            <FaGithubAlt />
            Repositórios
          </h1>

          <Form onSubmit={() => {}}>
            <input 
              type="text"
              placeholder='Adicionar repositório'
            />

            <SubmitButton>
              <FaPlus color='#FFF' size={14} />
            </SubmitButton>
          </Form>
        </Container>
        // <Title>
        //   Hello World
        // </Title>
        // <Title error={false}>
        //   Main
        //   <small>menor</small>
        // </Title>
      );
  }

  export default Main;

  ~~~

  # Adicionando repositorios

  Vamos no **MAin/index.js**, fazer mundança de function para class, e colocar o **states**, para assim poder fazer os metodos que irá manipular o states.

  ficou assim, o codigo.

  ~~~
  import React, { Component } from 'react';

  import { Container, Form, SubmitButton } from './styles';

  import { FaGithubAlt, FaPlus } from 'react-icons/fa'

  export default class Main extends Component {
    state = {
      newRepo: '',
    };

    handleInputChange = (e) => {
      this.setState({ newRepo: e.target.value });
    };

    handleSubmit = (e) => {
      e.preventDefault();

      console.log(this.state.newRepo);
    }

    render() {
      const { newRepo } = this.state;

      return (
        <Container>
          <h1>
            <FaGithubAlt />
            Repositórios
          </h1>

          <Form onSubmit={this.handleSubmit}>
            <input
              type="text"
              placeholder="Adicionar repositório"
              value={newRepo}
              onChange={this.handleInputChange}
            />

            <SubmitButton>
              <FaPlus color="#FFF" size={14} />
            </SubmitButton>
          </Form>
        </Container>
      );
    }
  }
  ~~~  

  agora vamos consumir a **API do Github**
  para isso não vamos utlizar o *fatch*, porque ele nãao suportar uma *base_url*.


  vamos utlizar uma biblioteca chamada de **axios** que vai consumir a API no react.

  ~~~bash
  yarn add axios  
  ~~~  

  agora vamos criar um pasta **services**,
  dentro de src. ficando assim **/src/services/api.js**

  o arquivo API, ficou assim:

  ~~~javascript
  import axios from 'axios'

  const api = axios.create({
    baseURL: 'https://api.github.com',
  })

  export default api;
  ~~~


  agora em **Main/index.js**, vamos importar **api**
  e utilizar dessa forma:

  ~~~javascript
  const response = await api.get(`/repos/${newRepo}`)
  ~~~

  além disso, realizamos a animação de loading, usando **{keyframes, css}**
  do *styled-components*, aplicamos condicionais, entre outras técnicas coomo pegar **props*
  de compoenentes na estilização, nosso arquivo final ficou assim:


  ~~~javascript
  import styled, {keyframes, css} from 'styled-components'

  export const Title = styled.h1`
    color: #fff;
    /* font-size: 24px;
    color: ${props => props.error ? 'red' : '#7159c1'};
    font-family: Arial, Helvetica, sans-serif;

    small{
      font-size: 14px; 
      color: #333;
    } */
  `;
  
  export const Container = styled.div`
    max-width: 700px; /*definindo largura maxima para conteiner */
    background: #fff; /* cor de fundo branco*/
    border-radius: 4px; /* a o radio de borda de 4px*/
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    padding: 30px; /*espaçamento interno de 30px */
    margin: 80px auto; /* margem em cima de 80 px, e nas latereais como auto, assim ficando centralizado*/
    
    h1{
      font-size: 20px;
      display: flex;
      flex-direction: row;
      align-items: center; /* ficar alinhado o texto e icons */
    }
    svg {
      margin-right: 10px; /*espaçamento do icons com texto */
    }
  `;
  export const Form = styled.form`
    margin-top: 30px; /*margin de cima, para ficar com espaçamento do h1 para form */
    display: flex; 
    flex-direction: row; /*garente que o buton mais, e form fica um ao lado do outro */

    input {
      flex: 1; /*isso faz com que o form ocupe todo espaço possivel */
      border: 1px solid #eee;
      padding: 10px 15px; /* altura e largura de 10px e 15px */
      border-radius: 4px; /*aredonda a borda do input */
      font-size: 16px; /*tamanho da fonte */
    }
  `;

  const rotate = keyframes`
    from {
      transform: rotate(0deg);
    } to {
      transform: rotate(360deg);
    }
  `;

  // possopegar propriedades dos componentes também
  export const SubmitButton = styled.button.attrs((props) => ({
    type: 'submit',
    disabled: props.loading,
  }))`
    background: #7159c1;
    border: 0;
    padding: 0 15px;
    margin-left: 10px;
    border-radius: 4px;

    display: flex;
    justify-content: center;
    align-items: center;

    /*aqui a estilização vai ocorrer apenas quando estiver desabilitado*/
    &[disabled] {
      cursor: not-allowed;
      opacity: 0.6;
    }

    ${(props) =>
      props.loading &&
      css`
        svg {
          animation: ${rotate} 2s linear infinite;
        }
      `}
  `;
  ~~~

  utilizei  icons **FaSpinner** para fazer o loading, index.js ficou assim:

  ~~~javascript
  import React, { Component } from 'react';
  import { FaGithubAlt, FaPlus, FaSpinner } from 'react-icons/fa'

  import api from '../../services/api'

  import { Container, Form, SubmitButton } from './styles';


  export default class Main extends Component {
    state = {
      newRepo: '',
      repositories: [],
    };

    handleInputChange = (e) => {
      this.setState({ newRepo: e.target.value });
    };

    handleSubmit = async (e) => {
      e.preventDefault();

      this.setState({ loading:true });

      const { newRepo, repositories } = this.state;

      const response = await api.get(`/repos/${newRepo}`)
      console.log(response.data);

      const data = {
        name: response.data.full_name,
      }

      this.setState({ 
        repositories: [...repositories, data],
        newRepo:'',
        loading:false,
      });
    }

    render() {
      const { newRepo, loading } = this.state;

      return (
        <Container>
          <h1>
            <FaGithubAlt />
            Repositórios
          </h1>

          <Form onSubmit={this.handleSubmit}>
            <input
              type="text"
              placeholder="Adicionar repositório"
              value={newRepo}
              onChange={this.handleInputChange}
            />

            <SubmitButton loading={loading}>
              { loading ? (<FaSpinner color="#FFF" size={14} />
              ) : (
                <FaPlus color='#FFF' sizee={14} />
              )}
            </SubmitButton>
          </Form>
        </Container>
      );
    }
  }
  ~~~