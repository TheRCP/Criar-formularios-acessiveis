## Criar formulários acessíveis

### Introdução

Os formulários são utilizados para os mais variados propósitos interativos na web. Os formulários permitem aos utilizadores selecionar e adquirir mercadorias, responder a questionários, efetuar a inscrição em cursos, procurar por informação na web, preencher formulários de impostos, entre uma infindável lista de tarefas.

Muitos são os utilizadores que necessitam de usar o teclado para navegar e interagir com um formulário. São disso exemplo: pessoas cegas mas também pessoas que fazem uso de softwares de varrimento de ecrã como é o caso das pessoas com deficiências neuromotoras graves. Existem poucas coisas que poderão tornar os formulários totalmente inacessíveis a quem usa apenas o teclado como forma de interação com um computador. Uma delas é o uso de javascript. É necessário ter alguns cuidados adicionais quando se faz uso de javascript para manipular dados de um formulário, para definir o focus num dado controlo, para alterar elementos, ou mesmo para submeter um formulário para processamento pelo servidor. Cada um destes aspetos pode tornar o formulário difícil ou mesmo impossível de preencher caso não seja possível usar o teclado.

> Teste sempre os seus formulários verificando nomeadamente que aquilo que consegue fazer com o rato também o consegue fazer usando apenas o teclado.

Os formulários devem também ser organizados de uma forma lógica, na qual a sequência de preenchimento faça sentido e em que seja explícita a agregação dos diversos campos que o compõem.

Como regra geral todos os controlos ativos de um formulário devem ter as respetivas etiquetas **explicitamente** e **implicitamente** associadas (elemento `<label>`). Na linguagem do **W3C** isso significa:

![Figura 1: Modelo de caixas CSS do campo de edição e da respetiva legenda num formulário](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_1.jpg)
![Associação não implícita: é visível na imagem que a label não envolve o campo de edição.](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_1b.jpg)

Nota à Figura: pintámos a vermelho a caixa `<form>` e a amarelo a caixa do elemento `<label>`. É visível, na primeira imagem, que o `<label>`, onde se encontra definida a legenda do campo de edição, envolve o próprio campo de edição. É a isto que o **W3C** chama de associação implícita (ver: [http://www.w3.org/TR/html401/interact/forms.html#h-17.9](http://www.w3.org/TR/html401/interact/forms.html#h-17.9)). A associação explícita é feita explicitamente no código com os atributos `for` e `id` respetivamente posicionados no elemento `<label>` e `<input>`, como se pode ver no código abaixo. Na segunda imagem acima é visível a legenda em que a `<label>` não envolve o campo de edição. De acordo com a versão 2.0 das **WCAG** é natural que a associação implícita deixe de ser utilizada, dada a capacidade dos agentes de utilizador em descodificar, hoje em dia, a associação explícita.

```html
<label for="nome">
  <input type id="nome" />
</label>
```

Deve-se igualmente adotar como regra geral a agregação de elementos de formulário relacionados (usando para o efeito o elemento `<fieldset>` e `<legend>`).

![Figura 2: Modelo de Caixas CSS para um formulário com `<fieldset>` e `<legend>`](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_2.jpg)

Nota à Figura: é visível no modelo de caixas CSS a associação entre os diversos elementos num formulário. Note que para além da riqueza estrutural, e clareza de associação entre os elementos, é ainda possível um cem número de formas de dar estilo a cada elemento individual do formulário.

```html
<fieldset>
  <legend>Dados pessoais:</legend><br />
  <label for="nome">Nome
    <input id="nome" type="text" name="vnome">
  </label><br />
  <label for="dtnasc">Data de Nascimento
    <input id="dtnasc" type="text" name="vdtnasc">
  </label><br />
</fieldset>
<fieldset>
  <legend>Dados académicos:</legend><br />
  <label for="gr_acad">Grau académico:
    <input id="gr_acad" type="text" name="vgr_acad">
  </label><br />
  <label for="curso">Curso:
    <input id="curso" type="text" name="vcurso">
  </label>
</fieldset>
```

## Tipos de controlos existentes num formulário.
### Controlo: `<input type="text"...`
**Função**: introduzir um campo de edição.

![Figura 3: Estrutura de um controlo input text corretamente codificado](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_3.jpg)

Nota à figura: Chama-se a atenção para o caráter "_" definido por defeito no campo de edição. Este caráter é útil para algumas tecnologias de apoio localizarem corretamente o início do campo de edição.

```html
<label for="name">Nome
  <input id="name" type="text" name="campoedicao" value="_" />
</label>
```

### Controlo: textarea
**Função**: Introduzir uma área de texto

![Figura 4: Estrutura de um controlo text area](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_4.jpg)

```html
<label for="motives">Explicite os seus motivos:<br />
  <textarea id="motives" name="areatexto">_</textarea>
</label>
```

### Controlo: `<input type="checkbox"`
**Função**: Caixas de verificação. Usadas para situações de resposta de escolha múltipla.

![Figura 5: Estrutura de um controlo check box](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_5.jpg)

```html
<fieldset>
  <legend>Escolha uma cor:</legend><br>
  <label for="blue"><input id="blue" type="checkbox" name="checkbox1" value="checkbox"> Blue</label><br>
  <label for="green"><input id="green" type="checkbox" name="checkbox2" value="checkbox"> Green</label><br>
  <label for="yellow"><input id="yellow" type="checkbox" name="checkbox3" value="checkbox"> Yellow</label>
</fieldset>
```

### Controlo: `<input type="radio"...`
Função: Botões de rádio. Usados para situações de resposta de escolha única.

![Figura 6: Estrutura de um controlo de radio](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_6.jpg)

```html
<fieldset>
  <legend>Escolha um meio de transporte:</legend><br>
  <label for="carro">
    <input id="carro" type="radio" name="radio" value="carro"> Carro
  </label><br>
  <label for="barco">
    <input id="barco" type="radio" name="radio" value="barco"> Barco
  </label><br>
  <label for="comboio">
    <input id="comboio" type="radio" name="radio" value="comboio"> Comboio
  </label>
</fieldset>
```

### Controlo: select
**Função**: Selecionar um elemento de uma lista.

![Figura 7: Estrutura de um controlo select/option](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_7-1.jpg)

```html
<label for="citydigi">Escolha uma Cidade Digital?
  <select id="citydigi" name="citydigi">
    <option value="1">Beja</option>
    <option value="3">Aveiro</option>
    <option value="4">Vila Real</option>
    <option value="5">Lisboa</option>
    <option value="2">Porto</option>
    <option value="6">Bragança</option>
    <option value="7">Faro</option>
    <option value="8">Portalegre</option>
    <option value="9">Coimbra</option>
    <option value="10">Guarda</option>
    <option value="11">Braga</option>
    <option value="12">Viseu</option>
  </select>
</label>
```

### Controlo: `<input type="submit" ... / <input type="reset"`
Função: o botão do tipo submit permite enviar os valores das variáveis recolhidas nos campos do formulário para processamento. O botão do tipo reset permite apagar os valores introduzidos pelo utilizador, deixando o formulário no seu estado inicial.

![Figura 8: Estrutura de um controlo submit/reset](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_8.jpg)

```html
<input type="submit" name="submit" value="Enviar formulário" />
<input type="reset" name="submit2" value="Apagar formulário" />
```

Controlo: `<input type="image"`
Função: permite construir botões gráficos.

![Figura 9: Estrutura de um botão gráfico num formulário](https://www.acessibilidade.gov.pt/wp-content/uploads/2020/04/2_form_9.jpg)

```html
<input type="image" alt="Enviar!" border="0" name="campoimagem" src="enviar.gif" width="109" height="41" />
```

Tutorial Original WebAIM com o título: [Creating Accessible Forms](https://webaim.org/techniques/css/invisiblecontent/).
Tradução e adaptação portuguesa: Jorge Fernandes