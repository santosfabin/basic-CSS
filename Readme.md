# HTML

- **CSS COMBINATOR SELECTORS**
    - element element
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | element element | div p | Seleciona TODOS os elementos <p> dentro do elemento <div> |
        | “ | " | Selects all <p> elements inside <div> elements |
        1. Ou seja, ele pega TODOS os elementos descendentes da <div> pai
            1. o elemento pai é a <div>
            2. o elemento descendente é o <p> que é descendente da <div>
        
        ```css
        div p{
        	background-color: yellow;
        }
        ```
        
        ```html
        <div>
        	<h2>texto1</h2>
        	<p>texto2</p>
        		<!-- ESTE SIM -->
        </div>
        
        <p>texto3</p>
        		<!-- ESTE NÃO -->
        ```
        
    - elemente > element
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | element > element | div > p | Seleciona TODOS os elementos <p> onde o elemento <div> é o pai |
        | " | " | Selects all <p> elements where the parent is a <div> element |
        1. Ou seja, ele pega TODOS os elementos filhos que tem a <div> como pai
            1. Diferente de element element o element > element pega apenas o <p> q é filho da <div>
            2. o elemento pai é a <div>
            3. o elemento <p> é filho da <div>
        
        ```css
        div > p {
        	background-color: yellow;
        }
        ```
        
        ```html
        <div>
          <h2>My name is Donald</h2>
          <p>I live in Duckburg.</p>
        		<!-- ESTE SIM -->
        </div>
        
        <div>
          <span>
        		<p>I will not be styled.</p>
        		<!-- ESTE NÃO -->
        	</span>
        </div>
        ```
        
    - element+element
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | element + element | div + p | Seleciona o PRIMEIRO elemento <p> que é colocado imediatamente APÓS os elementos <div> |
        | element + element | " | Selects the first <p> element that are placed immediately after <div> elements |
        1. Ou seja, seleciona o primeiro elemento <p> depois de cada elemento <div> colocado
            1. SE depois de <div> ... </div> o próximo elemento FOR <p> ele então SERÁ SELECIONADO
            2. SE depois de <div> ... </div> NÃO FOR <p> ele NÃO SERÁ SELECIONADO
            
            ```css
            div + p {
            	background-color: yellow;
            }
            ```
            
            > HTML FUNCIONAL
            > 
            
            ```html
            <div>
              <h2>texto1</h2>
              <p>texto2</p>
            		<!-- ESTE NÃO -->
            </div>
            
            <p>texto3</p>
            		<!-- ESTE SIM -->
            ```
            
            > HTML NÃO FUNCIONAL
            > 
            
            ```html
            <div>
              <p>texto1</p>
            		<!-- ESTE NÃO -->
            </div>
            
            <span>texto2</span>
            		<!-- ESTE NÃO -->
            <p>texto3</p>
            		<!-- ESTE NÃO -->
            ```
            
    - element1~elemente2
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | element1~element2 | p ~ ul | Seleciona todos os elementos <ul> que estão depois de por um elemento <p> |
        | “ | “ | Selects every <ul> element that are preceded by a <p> element |
        1. Ou seja, ele pega TODOS OS ELEMENTOS <ul> QUE ESTÃO DEPOIS DE UM <p>
            1. <div> ... </div> <ul> ... </ul> não está dentro do esperado
            2. <p> ... </p> <ul> ... </ul> está dentro do esperado
            
            ```css
            p ~ ul {
              background: #ff0000;
            }
            ```
            
            ```html
            <div>div</div>
            	<ul>
            	  <li>Coffee</li>
            	  <li>Tea</li>
            	  <li>Milk</li>
            	</ul>
            <!-- está não acontecerá nada -->
            
            <p>texto1</p>
            <ul>
              <li>1</li>
              <li>2</li>
              <li>3<li>
            </ul>
            <!-- essa está dentro
            do pedido pelo css -->
            
            <h2>Another list</h2>
            <ul>
              <li>Coffee</li>
              <li>Tea</li>
              <li>Milk</li>
            </ul>
            <!-- essa está dentro
            do pedido pelo css -->
            ```
            

- **CSS ATTRIBUTE SELECTORS**
    - [attribute]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute] | [target] | Seleciona todos os elementos com um atributo de destino |
        | “ | “ | Selects all elements with a target attribute |
        1. Seleciona todos os elementos que tem dentro de si o elemento target
            1. Exemplos:
                1. <span target> texto1 </a>
                    
                    exemplo sem nome para o target
                    
                2. <span target=”julionagaita”> texto2 </a>
                    
                    exemplo com nome no target
                    
            
            > EXEMPLO1:
            > 
            
            ```css
            [target] {
              background-color: yellow;
            }
            ```
            
            ```html
            <span target>Texto1</span>
            <span target="julio">Texto2</span>
            <span target="slamano">Texto3</span>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            span[target] {
              background-color: yellow;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <p target>Texto1</p>
            	<!-- ESTE NÃO -->
            
            <span target>Texto2</span>
            	<!-- ESTE SIM -->
            
            <span target="slamano">Texto3</span>
            	<!-- ESTE SIM -->
            ```
            
    - [attribute=value]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute=value] | [target=blank] | Seleciona todos os elementos com target="blank” |
        | “ | “ | Selects all elements with target="blank" |
        1. Seleciona APENAS os elementos que tenha dentro de si o elemento target com o valor de “blank”
            1. [target=blank]
                1. CORRETO
            2. span[target=blank]
                1. CORRETO
            3. span [target=blank]
                1. ERRADO não deve ter espaço entre eles
            
            > EXEMPLO1:
            > 
            
            ```css
            [target=blank] {
              background-color: yellow;
            }
            ```
            
            ```html
            <span target=blank>Texto1</span>
            <p target=blank>Texto2</p>
            <h1 target=blank>Texto2</h1>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            span[target=blank] {
              background-color: yellow;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <p target>Texto1</p>
            	<!-- ESTE NÃO -->
            
            <span target>Texto2</span>
            	<!-- ESTE NÃO -->
            
            <span target="blank">Texto3</span>
            	<!-- ESTE SIM -->
            ```
            
        
    - [attribute~=value]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute~=value] | [title~=word] | Seleciona todos os elementos com um atributo title contendo a palavra "flor” |
        | “ | “ | Selects all elements with a title attribute containing the word "flower" |
        1. Seleciona APENAS os elementos que contenha “word”  em seu atributo
            1. ou seja, deve ter “word” e mais alguma coisa
            2. ele sozinho não é considerado
            3. EXEMPLOS:
                1. title="master word"
                    
                    CORRETO
                    
                2. title="word master"
                    
                    CORRETO
                    
                3. title="wordmaster"
                    
                    ERRADO deve conter espaço entre a palavra requerida
                    
                4. title="word"
                    
                    ERRADO ela não pode estar sozinha
                    
            
            > EXEMPLO1:
            > 
            
            ```css
            [title~=word] {
              background-color: yellow;
            }
            ```
            
            ```html
            <p title="klematis word"> texto </p>
            <p title="klematis word asf"> texto </p>
            <p title="word asf"> texto </p>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            span[title~=word] {
              background-color: yellow;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <span title="klematis word"> texto </span>
            	<!-- ESTE SIM -->
            
            <span title="klematis word klematis"> texto </span>
            	<!-- ESTE SIM -->
            
            <span title="word asf"> texto </span>
            	<!-- ESTE SIM -->
            
            <span title="wordas"> texto </span>
            	<!-- ESTE NÃO -->
            
            <span title="klematis wordss"> texto </span>
            	<!-- ESTE NÃO -->
            
            <p target>Texto1</p>
            	<!-- ESTE NÃO -->
            
            <p title="klematis word">Texto1</p>
            	<!-- ESTE NÃO -->
            
            ```
            
    - [attribute|=value]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute|=value] | [lang|=en] | Seleciona todos os elementos com um valor de atributo lang começando com "en” |
        | “ | “ | Selects all elements with a lang attribute value starting with "en" |
        1. Seleciona APENAS os elementos que comece com “en” em seu atributo
            1. ou seja todos os atributos que comecem com “en” serão selecionados
            2. os elementos que SÓ tenha “en” TAMBÉM SERÃO selecionados
            3. EXEMPLOS:
                1. lang="en”
                    
                    CORRETO
                    
                2. lang="en-sla”
                    
                    CORRETO
                    
                3. lang="En”
                    
                    CORRETO
                    
                4. lang="fen”
                    
                    ERRADO ele deve COMEÇAR COM “en” NÃO conter em si “en”
                    
            
            > EXEMPLO1:
            > 
            
            ```css
            [lang|=en] {
              background-color: yellow;
            }
            ```
            
            ```html
            <span lang="en"> texto </span>
            <span lang="en-us"> texto </span>
            <span lang="En"> texto </span>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            span[lang|=en] {
              background-color: yellow;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <span lang="en"> texto </span>
            	<!-- ESTE SIM -->
            
            <span lang="en-us"> texto </span>
            	<!-- ESTE SIM -->
            
            <span lang="En"> texto </span>
            	<!-- ESTE SIM -->
            
            <span lang="uen">Hello!</span>
            	<!-- ESTE NÃO -->
            
            <span lang="uo">Hello!</span>
            	<!-- ESTE NÃO -->
            
            <p lang="eu">Hello!</p>
            	<!-- ESTE NÃO -->
            
            ```
            
    - [attribute^=value]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute^=value] | a[href^="https"] | Seleciona cada elemento <a> cujo valor de atributo a href começa com "https" |
        | “ | " | Selects every <a> element whose href attribute value begins with "https" |
        | “ | div[class^="test"] | Seleciona cada elemento <div> cujo valor de atributo a class começa com "test” |
        | “ | “ | Selects every <div> element whose class attribute value begins with "test" |
        1. Seleciona APENAS os elementos <div>  que tenha o valor class começando com “test”
            1. ou seja, apenas as <div> que tenha a classe com o valor começando com “test” serão selecionados
            2. caso não tenha uma classe começando com “test” não será selecionada
            3. ele sozinho É SIM considerado
            4. EXEMPLOS:
                1. class="test"
                    
                    CORRETO
                    
                2. class="test_ex"
                    
                    CORRETO
                    
                3. class="first test"
                    
                    ERRADO deve APENAS começar com “test”
                    
            
            > EXEMPLO1:
            > 
            
            ```css
            [class^="test"] {
              background: #ffff00;
            }
            ```
            
            ```html
            <div class="test">Texto1</div>
            <div class="test_ex">Texto2<div>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            div[class^="test"] {
              background: #ffff00;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <div class="test">Texto</div>
            	<!-- ESTE SIM -->
            
            <div class="test_ex">Texto</div>
            	<!-- ESTE SIM -->
            
            <div class="first_test">Texto</div>
            	<!-- ESTE NÃO -->
            
            <div class="second">Texto<div>
            	<!-- ESTE NÃO -->
            
            <p class="test_ex">Texto<p>
            	<!-- ESTE NÃO -->
            ```
            
    - [attribute$=value]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute$=value] | div[class$="test"] | Seleciona cada elemento <div> cujo valor de atributo href termina com ".test” |
        | “ | " | Selects every <div> element whose href attribute value ends with ".test” |
        1. Seleciona APENAS os elementos que TERMINE com “.text” em seu atributo
            1. ou seja, deve ter “.text” em seu fim
            2. ele sozinho É SIM considerado
                1. class="first_.test”
                    
                    CORRETO
                    
                2. class=".test”
                    
                    CORRETO
                    
                3. class="test”
                    
                    ERRADO o requerimento deve estar completo
                    
            
            > EXEMPLO1:
            > 
            
            ```css
            [class$=".test"] {
              background: #ffff00;
            }
            ```
            
            ```html
            <div class="first_.test">Texto</div>
            <div class=".test">Texto</div>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            div[class$=".test"] {
              background: #ffff00;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <div class="first_.test">Texto</div>
            	<!-- ESTE SIM -->
            
            <div class=".test">Texto</div>
            	<!-- ESTE SIM -->
            
            <div class="test">Texto</div>
            	<!-- ESTE NÃO -->
            
            <div class=".second">Texto</div>
            	<!-- ESTE NÃO -->
            
            <p class=".test">Texto</p>
            	<!-- ESTE NÃO -->
            
            ```
            
    - [attribute*=value]
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | [attribute*=value] | div[class*="test"] | Seleciona cada elemento <div> cujo valor de atributo href contém a substring "test” |
        | “ | " | Selects every <div> element whose href attribute value contains the substring "test” |
        1. Seleciona APENAS os elementos <div> que tenha “test” em seu atributo
            1. deve conter “test” em QUALQUER lugar do atributo
            2. “test” pode estar junto ou separado (na parte do nome)
                1. “first test”
                    
                    CORRETO
                    
                2. “firsttest”
                    
                    CORRETO
                    
            
            > EXEMPLO1:
            > 
            
            ```css
            [class*="test"] {
              background: #ffff00;
            }
            ```
            
            ```html
            <div class="firsttest">texto</div>
            <div class="first test">texto</div>
            <div class="test">texto</div>
            	<!-- TODOS ELES SERÃO SELECIONADO -->
            ```
            
            > EXEMPLO2:
            > 
            
            ```css
            div[class*="test"] {
              background: #ffff00;
            }
            /* NÃO deve ter espaço entre eles */
            ```
            
            ```html
            <div class="firsttest">texto</div>
            	<!-- ESTE SIM -->
            
            <div class="first test">texto</div>
            	<!-- ESTE SIM -->
            
            <div class="test">texto</div>
            	<!-- ESTE SIM -->
            
            <div class="second">texto</div>
            	<!-- ESTE NÃO -->
            
            <p class="test">texto</p>
            	<!-- ESTE NÃO -->
            ```
            
- **CSS PSEUDO-CLASSE**
    - :active
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :active | a:active | Seleciona o link ativo |
        | “ | “ | Selects the active link |
        1. Vai alterar APENAS quando é ativo
            1. ou seja quando ta segurando no mouse1
            2. isso serve pra qualquer elemento clicável
        
        > **EXEMPLO1:**
        > 
        
        ```css
        :active {
          background-color: yellow;
        }
        /* serve para todos os elementos
        que serão ativados */
        /*como não está sendo sendo
        específicado para qual :active
        ele irá mudar o background-color do body*/
        *:active {
          background-color: yellow;
        }
        /* serve para todos os elementos
        que serão ativados */
        /*ele irá mudar o background-color do TUDO
        então se vc clicar em qualquer coisa ele
        irá mudar o background-color*/
        ```
        
        > **EXEMPLO2:**
        > 
        
        ```css
        input:active {
          background-color: yellow;
        }
        /*como é um input que esta sendo
        requerido, ele vai mudar o backgroun-color
        apenas do próprio input*/
        ```
        
        ```html
        <!-- Será ativado -->
        <input>
        <input type="button">
        <!-- Será ativado -->
        
        <!-- NÃO será ativado -->
        <a href="#">texto</a>
        <!-- NÃO será ativado -->
        ```
        
    - :checked
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :checked | input:checked | Seleciona cada elemento <input> marcado |
        | “ | “ | Selects every checked <input> element |
        
        > **EXEMPLO1:**
        > 
        
        ```css
        :checked {
          height: 50px;
          width: 50px;
        }
        /* serve para todos os elementos
        que serão ativados */
        /*como não está sendo sendo
        específicado para qual :active
        ele irá mudar o background-color do body*/
        *:checked {
          height: 50px;
          width: 50px;
        }
        /* serve para todos os elementos
        que serão ativados */
        /*ele irá mudar o background-color do TUDO
        então se vc clicar em qualquer coisa ele
        irá mudar o background-color*/
        ```
        
        > **EXEMPLO2:**
        > 
        
        ```css
        input:checked {
          height: 50px;
          width: 50px;
        }
        /*como é um input que esta sendo
        requerido, ele vai mudar
        apenas do próprio input*/
        ```
        
        ```html
        <!-- CATEGORIA 1 -->
        <input type="radio" checked="checked" value="male" name="gender"> Male<br>
        	<!-- aqui ele já esta com o checked ligado -->
        <input type="radio" value="female" name="gender"> Female<br>
        <!-- CATEGORIA 1 -->
        
        <!-- CATEGORIA 2 -->
        <input type="checkbox" checked="checked" value="Bike"> bike<br>
        	<!-- aqui ele já esta com o checked ligado -->
        <input type="checkbox" value="Car"> car
        <!-- CATEGORIA 2 -->
        
        <!-- também pode ser assim para algumas situações: checked="active" -->
        
        ```
        
    - :disabled
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :disabled | input:disabled | Seleciona cada elemento <input> desabilitado |
        | “ | “ | Selects every disabled <input> element |
        
        ```css
        input[type=text]:disabled {
          background: #000;
          color: white;
        }
        /*como é um input que esta sendo
        requerido, ele vai mudar o backgroun-color
        apenas do próprio input*/
        ```
        
        ```html
        <!-- será alterados -->
        Country: <input type="text" disabled="disabled" value="Disneyland"><br>
        <!-- será alterados -->
        
        <!-- NÃO serão alterados -->
        First name: <input type="text" value="Mickey"><br>
        Last name: <input type="text" enable="enable" value="Mouse"><br>
        Name: <input disabled="disabled" value="Pedro">
        <!-- NÃO será alterados -->
        ```
        
    - :empty
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :empty | p:empty | Seleciona cada elemento <p> que não tem filhos |
        | “ | “ | Selects every <p> element that has no children |
        
        ```css
        p:empty {
          width: 100px;
          height: 20px;
          background: #ff0000;
        }
        ```
        
        ```html
        <!-- SERÁ ATIVADO -->
        <p></p>
        <!-- SERÁ ATIVADO -->
        
        <!-- NÃO SERÁ ATIVADO -->
        <p>texto</p>
        <p> </p>
        <p>texto</p>
        <!-- NÃO SERÁ ATIVADO -->
        ```
        
    - :enabled
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :enabled | input:enabled | Seleciona cada elemento <input> habilitado |
        | “ | “ | Selects every enabled <input> element |
        
        ```css
        input[type=text]:enabled {
          background: #ffff00;
        }
        ```
        
        ```html
        First name: <input type="text" value="Mickey"><br>
        Last name: <input type="text" value="Mouse"><br>
        ```
        
    - :first-child
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :first-child | p:first-child | Seleciona todos os elementos <p> que são o primeiro filho de seu pai |
        | “ | “ | Selects every <p> elements that is the first child of its parent |
        
        ```css
        p:first-child {
          background-color: yellow;
        }
        ```
        
        ```html
        <p>texto</p>
        	<!-- SERÁ ATIVADO -->
        
        <div>
        	<p>texto</p>
        	<!-- SERÁ ATIVADO -->
        		<!-- pois é o primeiro dentro da <div> -->
        	<p>texto.</p>
        	<p>texto</p>
        </div>
        ```
        
    - :first-of-type
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :first-of-type | p:first-of-type | Seleciona cada elemento <p> que é o primeiro elemento <p> de seu pai |
        | “ | “ | Selects every <p> element that is the first <p> element of its parent |
        
        ```css
        p:first-of-type {
          background-color: red;
        }
        ```
        
        ```html
        <p>The first paragraph.</p>
        	<!-- será ativo -->
        		<!-- pois é o primeiro (pai) -->
        <p>The second paragraph.</p>
        	<!-- NÃO será ativo -->
        <p>The third paragraph.</p>
        	<!-- NÃO será ativo -->
        
        <div>
        	<p>The tt paragraph.</p>
        		<!-- será ativo -->
        			<!-- pois é o primeiro (pai)
        				dentro da div-->
        </div>
        ```
        
    - :focus
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :focus | input:focus | Seleciona o elemento <input> que tem foco |
        | “ | “ | Selects the <input> element that has focus |
        
        ```css
        input:focus {
          background-color: yellow;
        }
        ```
        
        ```html
        First name: <input type="text" name="firstname">
        ```
        
    - :hover
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :hover | a:hover | Seleciona links ao passar o mouse |
        | “ | “ | Selects links on mouse over |
        
        > **EXEMPLO1:**
        > 
        
        ```css
        a:hover {
          background-color: yellow;
        }
        ```
        
        ```html
        <a href="#">texto</a>
        ```
        
        > **EXEMPLO2:**
        > 
        
        ```css
        p:hover {
          background-color: yellow;
        }
        ```
        
        ```html
        <p>Texto</p>
        ```
        
    - :in-range
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :in-range | input:in-range | Seleciona elementos <input> com um valor dentro de um intervalo especificado |
        | “ | “ | Selects <input> elements with a value within a specified range |
        
        ```css
        input:in-range {
          border: 2px solid yellow;
        }
        /*então se for menor que 5
        	ou maior que 10
        	ele sairá do foco
        	e perderá a cor*/
        ```
        
        ```html
        <input type="number" min="5" max="10" value="7">
        ```
        
    - :invalid
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :invalid | input:invalid | Seleciona todos os elementos <input> com um valor inválido |
        | “ | “ | Selects all <input> elements with an invalid value |
        1. Ou seja, ele pega todos os valores que não atendem o requirido
            1. <input type="email" value="supportEmail">
                1. aqui ele espera um valor “email”, então qualquer palavra que NÃO tenha gmail ELE SELECIONARÁ
        
        ```css
        input:invalid {
          border: 2px solid red;
        }
        ```
        
        ```html
        <input type="email" value="supportEmail">
        	<!-- SERÁ selecionado -->
        		<!-- pois está INVALIDO -->
        
        <input value="supportEmail">
        	<!-- NÃO será selecionado -->
        		<!-- pois está dentro do esperado -->
        ```
        
    - :lang(language)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :lang(language) | p:lang(it) | Seleciona cada elemento <p> com um valor EXATO atributo a lang sendo ele “it” |
        | “ | “ | Selects every <p> element with a lang attribute value starting with "it" |
        1. Ele selecionará APENAS o <p> que tenha atribuído “it” em lang
            1. ele deve ser EXATAMENTE it
        
        ```css
        p:lang(it) { 
          background: yellow;
        }
        ```
        
        ```html
        <p lang="it">Texto</p>
        	<!-- será selecionado -->
        
        <!-- NÃO serão selecionados -->
        <p lang="ita">Ciao bella!</p>
        <p>texto</p>
        <!-- NÃO serão selecionados -->
        ```
        
    - [:last-child](https://www.w3schools.com/cssref/sel_last-child.asp)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :last-child | p:last-child | Seleciona todos os elementos <p> que são o último filho de seu pai |
        | “ | “ | Selects every <p> elements that is the last child of its parent |
        1. Selecionará todos o <p> que estão no fim
            1. tanto em alguma <div>
            2. tanto a ultima do body
        
        ```css
        input:in-range {
          border: 2px solid yellow;
        }
        /*então se for menor que 5
        	ou maior que 10
        	ele sairá do foco
        	e perderá a cor*/
        ```
        
        ```html
        <div>
        <!-- NÃO serão selecionados -->
        	<p>Texto</p>
        	<p>Texto</p>
        <!-- NÃO serão selecionados -->
        
        	<p>Texto</p>
        <!-- será selecionado -->
        </div>
        
        <p>Texto</p>
        <!-- será selecionado -->
        ```
        
    - :last-of-type
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :last-of-type | p:last-of-type | Seleciona cada elemento <p> que é o último elemento <p> de seu pai |
        | “ | “ | Selects every <p> element that is the last <p> element of its parent |
        1. Seleciona o ultimo <p> de qualquer elemento pai
        
        ```css
        p:last-of-type {
          background: #ff0000;
        }
        ```
        
        ```html
        <p>texto</p>
        <p>texto</p>
        <p>texto</p>
        <!-- NÃO É O ULTIMO DE UM ELEMENTO PAI -->
        
        <div>texto
        	<div>texto</div>
        	<p>texto</p>
        	<p>texto</p>
        <!-- NÃO É O ULTIMO DE UM ELEMENTO PAI -->
        		<p>texto</p>     <!-- SIM -->
        </div>
        <p>texto</p>     <!-- SIM -->
        ```
        
    - :link
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :link | a:link | Seleciona todos os links não visitados |
        | “ | “ | Selects all unvisited links |
        1. O estilo do seletor :link estiliza links para páginas que você ainda não visitou
        
        ```css
        a:link {
          background-color: yellow;
        }
        ```
        
        ```html
        <a href="#">texto</a>
        <a href="#">texto</a>
        ```
        
    - :not(selector)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :not(selector) | :not(p) | Seleciona todos os elementos que não são um elemento <p> |
        | “ | “ | Selects every element that is not a <p> element |
        1. Selecionará APENAS elementos NÃO <p>
        
        > EXEMPLO1:
        > 
        
        ```css
        :not(p) {
          color: red;
        }
        p{
        color: blue;
        }
        ```
        
        ```html
        <!-- SERÃO SELECIONADOS -->
        <h1>Texto</h1>
        <div>Texto</div>
        <a href="#" target="_blank">Texto</a>
        <!-- SERÃO SELECIONADOS -->
        
        <!-- NÃO SERÃO SELECIONADOS -->
        <p>Texto</p>
        <p>Texto</p>
        <!-- NÃO SERÃO SELECIONADOS -->
        ```
        
        > EXEMPLO2:
        > 
        
        ```css
        :not(p) {
          color: red;
        }
        ```
        
        ```html
        <h1>Texto</h1>
        <div>Texto</div>
        <a href="#" target="_blank">Texto</a>
        
        <p>Texto</p>
        <p>Texto</p>
        
        <!-- TODOS SERÃO SELECIONADOS -->
        <!-- pois não há formatação
        própria para o <p> -->
        ```
        
    - :nth-child(n)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :nth-child(n) | p:nth-child(2) | Seleciona cada elemento <p> que é o segundo filho de seu pai |
        | “ | “ | Selects every <p> element that is the second child of its parent |
        1. Dentro do () deverá ser escrito o número que desejar
            1. sendo o número correspondente a posição que queira
        
        ```css
        li:nth-child(2) {
          background: lightgreen;
        }
        ```
        
        ```html
        <ul>
          <li>1</li>
          <li>2</li>   <!-- ESSE -->
          <li>3</li>
          <li>4</li>
          <li>5</li>
        </ul>
        ```
        
    - :nth-last-child(n)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :nth-last-child(n) | p:nth-last-child(2) | Seleciona cada elemento <p> que é o segundo filho de seu pai, contando a partir do último filho |
        | “ | “ | Selects every <p> element that is the second child of its parent, counting from the last child |
        1. É a mesma coisa do [:nth-child(n)](https://www.notion.so/nth-child-n-cde89d48b7fe405c82df507bdb8758c5) só que a contagem é de baixo pra cima, em vez de cima pra baixo
            1. então deve ser escrito a posição que deseja dentro do () so que a contagem será feito da ultimo para o primeiro
        
        > EXEMPLO1:
        > 
        
        ```css
        p:nth-last-child(2) {
          background: red;
        }
        ```
        
        ```html
        	
        <p>Texto</p>
        <p>Texto</p>
        <p>Texto</p>     <!-- ESSE -->
        <p>Texto</p>
        ```
        
        > EXEMPLO2:
        > 
        
        ```css
        p:nth-last-child(2) {
          background: red;
        }
        ```
        
        ```html
        <div>
        	<p>Texto</p>
        	<p>Texto</p>
        	<p>Texto</p>     <!-- ESSE -->
        	<p>Texto</p>
        </div>
        
        <p>Texto</p>
        <p>Texto</p>
        <p>Texto</p>
        <p>Texto</p>     <!-- ESSE -->
        <!-- eles está contando a ultima
        div q tem o <p> como +1 -->
        
        <div>
        	<p>Texto</p>
        	<p>Texto</p>
        	<p>Texto</p>     <!-- ESSE -->
        	<p>Texto</p>
        </div>
        ```
        
    - :nth-last-of-type(n)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :nth-last-of-type(n) | p:nth-last-of-type(2) | Seleciona cada elemento <p> que é o segundo elemento <p> de seu pai, contando a partir do último filho |
        | “ | “ | Selects every <p> element that is the second <p> element of its parent, counting from the last child |
        
        ```css
        p:nth-last-of-type(2) {
          background: red;
        }
        ```
        
        ```html
        <div>
          <p>Texto</p>
          <p>Texto</p>
          <p>Texto</p>     <!-- ESSE -->
          <p>Texto</p>
        </div>
        ```
        
    - :nth-of-type(n)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :nth-of-type(n) | p:nth-of-type(2) | Seleciona cada elemento <p> que é o segundo elemento <p> de seu pai |
        | “ | “ | Selects every <p> element that is the second <p> element of its parent |
        
        ```css
        li:nth-of-type(2) {
          background: lightgreen;
        }
        ```
        
        ```html
        <ul>
          <li>First list item</li>
          <li>Second list item</li>     <!-- ESSE -->
          <li>Third list item</li>
          <li>Fourth list item</li>
          <li>Fifth list item</li>
        </ul>
        ```
        
    - :only-of-type
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :only-of-type | p:only-of-type | Seleciona cada elemento <p> que é o único elemento <p> de seu pai |
        | “ | “ | Selects every <p> element that is the only <p> element of its parent |
        1. Deve APENAS contar UM elemento PAI
        
        ```css
        p:only-of-type {
          background: red;
        }
        ```
        
        ```html
        <div>
        	<p>Texto</p>  <!-- SIM -->
        </div>
        
        <div>
        	<p>Texto</p>  <!-- NÃO -->
        	<p>Texto</p>  <!-- NÃO -->
        </div>
        ```
        
    - :only-child
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :only-child | p:only-child | Seleciona cada elemento <p> que é o único filho de seu pai |
        | “ | “ | Selects every <p> element that is the only child of its parent |
        
        ```css
        p:only-child {
          background: red;
        }
        ```
        
        ```html
        <div>
          <p>This is a paragraph.</p>  <!-- SIM -->
        </div>
        
        <div>
          <p>This is a span.</p>  <!-- NÃO -->
          <p>This is a paragraph.</p>  <!-- NÃO -->
        </div>
        ```
        
    - :optional
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :optional | input:optional | Seleciona elementos <input> sem atributo "obrigatório” |
        | “ | “ | Selects <input> elements with no "required" attribute |
        1. O seletor :opcional seleciona elementos de formulário sem atributo "obrigatório"
        
        ```css
        input:optional {
          background-color: yellow;
        }
        ```
        
        ```html
        <p>An optional input element:<br><input></p>  <!-- SIM -->
        
        <p>A required input element:<br><input required></p>  <!-- NÃO -->
        
        ```
        
    - :out-of-range
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :out-of-range | input:out-of-range | Seleciona elementos <input> com um valor fora de um intervalo especificado |
        | “ | “ | Selects <input> elements with a value outside a specified range |
        1. Tente digitar um número dentro do intervalo determinado (entre 5 e 10), para ver o estilo desaparecer
        
        ```css
        input:out-of-range {
          border: 2px solid red;
        }
        ```
        
        ```html
        <input type="number" min="5" max="10" value="17">
        ```
        
    - :read-only
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :read-only | input:read-only | Seleciona elementos <input> com um atributo "readonly" especificado |
        | “ | “ | Selects <input> elements with a "readonly" attribute specified |
        
        ```css
        input:read-only {
          background-color: yellow;
        }
        ```
        
        ```html
        <input readonly value="hello">
        ```
        
    - [:read-write](https://www.w3schools.com/cssref/sel_read-write.asp)
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :read-write | input:read-write | Seleciona elementos <input> sem atributo "readonly” |
        | “ | “ | Selects <input> elements with no "readonly" attribute |
        
        ```css
        input:read-write {
          background-color: yellow;
        }
        ```
        
        ```html
        <input value="hello">  <!-- SIM -->
        
        <input readonly value="hello">  <!-- NÃO -->
        ```
        
    - :required
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :required | input:required | Seleciona elementos <input> com um atributo "obrigatório" especificado |
        | “ | “ | Selects <input> elements with a "required" attribute specified |
        1. O seletor :required seleciona elementos de formulário com um atributo "required"
        
        ```css
        input:required {
          background-color: yellow;
        }
        ```
        
        ```html
        <input required>  <!-- SIM -->
        <input>  <!-- NÃO -->
        ```
        
    - :root
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :root | root | Seleciona o elemento raiz do documento |
        | “ | “ | Selects the document's root element |
        1. O CSS não precisa ser aplicado necessariamente ao HTML
        2. Ele é uma forma de estilizar documentos. Como se referencia ao elemento que dá origem a todos os outros? Ou seja, o que é em termo genéricos o elemento que contém todos ou outros? Esse é elemento é conhecido como `:root`. 
            1. Se estiver usando uma página HTML é é o equivalente ao `<HTML>`. 
            2. Se for um SVG, então ele é o `<SVG>`.
        
        ```css
        :root {
          background: #ff0000;
        }
        /*como é um html ele vai usar o background para o html*/
        ```
        
    - :target
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :target | #news:target | Seleciona o elemento #news ativo atual (clicado em um URL que contém esse nome de âncora) |
        | “ | “ | Selects the current active #news element (clicked on a URL containing that anchor name) |
        1. Clique nos links acima e o seletor :target destaca a âncora HTML ativa atual
            1. aplica estilo no alvo de um link, esse alvo seria um elemente intern não externo
            2. o algo q foi direcionadk será selecionado pelo css
                1. (PÓS)
        
        ```css
        :target {
          border: 2px solid #D4D4D4;
          background-color: red;
        }
        ```
        
        ```html
        <p><a href="#news1">1</a></p>
        <p><a href="#news2">2</a></p>
        
        <p id="news1"><b>1</b></p>
        <p id="news2"><b>2</b></p>
        ```
        
    - :valid
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :valid | input:valid | Seleciona todos os elementos <input> com um valor válido |
        | “ | “ | Selects all <input> elements with a valid value |
        1. Caso digite algo que não seja um email ele não selecionará
        
        ```css
        input:valid {
          background-color: yellow;
        }
        ```
        
        ```html
        <input type="email">
        ```
        
    - :visited
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | :visited | a:visited | Seleciona todos os links visitados |
        | “ | “ | Selects all visited links |
        1. Se o link já foi visitado/clicado, ele aceitará e irá usa-lo
        
        ```css
        a:visited {
          color: pink;
        }
        ```
        
        ```html
        <a href="https://www.w3schools.com">W3Schools Home</a>
        ```
        
- **CSS PSEUDO ELEMENTS**
    - ::after
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | ::after | p::after | Insert content after every <p> element |
        | ~ | ~ | Inserir conteúdo após cada elemento <p> |
        
        ```css
        ::selection {
          color: red;
          background: yellow;
        }
        ```
        
        ```html
        <p>My name is Donald</p>
        <p>I live in Ducksburg</p>
        ```
        
        1. Então sempre depois do <p> terá " - Remember this"
    - ::before
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | ::before | p::before | Inserir conteúdo antes de cada elemento <p> |
        | “ | “ | Insert content before every <p> element |
        
        ```css
        p::before {
          content: "Read this -";
        }
        ```
        
        ```html
        <p>My name is Donald</p>
        <p>I live in Ducksburg</p>
        ```
        
        1. Então sempre antes do <p> terá " - Remember this"
    - ::first-letter
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | ::first-letter | p::first-letter | Seleciona a primeira letra de cada elemento <p> |
        | “ | “ | Selects the first letter of every <p> element |
        
        ```css
        p::first-letter {
          font-size: 200%;
          color: #8A2BE2;
        }
        ```
        
        ```html
        <p>My name is Donald.</p>
        <p>I live in Duckburg.</p>
        <p>My best friend is Mickey.</p>
        ```
        
    - ::first-line
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | ::first-line | p::first-line | Seleciona a primeira linha de cada elemento <p> |
        | “ | “ | Selects the first line of every <p> element |
        
        ```css
        p::after { 
          content: " - Remember this";
        }
        ```
        
        ```html
        <h2>WWF's Mission Statement</h2>
        <p>To stop the degradation of the planet's natural environment and to build a future in which humans live in harmony with nature, by; conserving the world's biological diversity, ensuring that the use of renewable natural resources is sustainable, and promoting the reduction of pollution and wasteful consumption.</p>
        ```
        
    - ::selection
        
        
        | Selector | Example | Example description |
        | --- | --- | --- |
        | ::selection | p::selection | Seleciona a parte de um elemento que é selecionado por um usuário |
        | “ | “ | Selects the portion of an element that is selected by a user |
        
        ```css
        p::first-line {
          background-color: yellow;
        }
        ```
        
        ```html
        <h1>Select some text on this page:</h1>
        
        <p>This is a paragraph.</p>
        <div>This is some text in a div element.</div>
        ```
        
    - ::marker