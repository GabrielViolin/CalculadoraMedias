# Calculadora de Médias

## Descrição

Aplicativo mobile desenvolvido com React Native e Expo para calcular a média aritmética simples de três avaliações de uma disciplina. O usuário informa o nome da matéria, as três notas e a média mínima desejada; o aplicativo atualiza o resultado automaticamente e indica se a média foi atingida. Também permite consultar um histórico das médias cadastradas enquanto o aplicativo permanece aberto.

## Aluno

- **Nome:** Gabriel Violin Ramos
- **RGM:**  43617832

## Telas

- **Início (`screens/HomeScreen.js`):** apresenta o resumo das disciplinas cadastradas, a média geral, o histórico de médias e o botão para iniciar um novo cálculo. Ao selecionar uma disciplina do histórico, abre a tela de detalhes.
- **Calculadora (`screens/CalculatorScreen.js`):** recebe o nome da disciplina, três notas de 0 a 10 e a média mínima para aprovação. Mostra uma prévia da média enquanto as notas são preenchidas e permite salvar o resultado.
- **Detalhes (`screens/DetailsScreen.js`):** apresenta a média calculada, o status em relação à média mínima, as notas informadas e o método de cálculo utilizado. Oferece opções para voltar ao início ou fazer outro cálculo.

## Fonte de dados

O aplicativo utiliza **dados locais informados pelo usuário**, armazenados em memória por meio do estado do React (`useState`). Não consome API pública nem API própria.

As três avaliações possuem o mesmo peso. O cálculo utilizado é:

`Média = (Avaliação 1 + Avaliação 2 + Avaliação 3) / 3`

A média mínima começa em **6,0**, mas pode ser alterada no formulário. O histórico é mantido apenas enquanto o aplicativo está aberto; ao recarregar ou reiniciar o app, os registros são perdidos.

## Onde estão os requisitos

- **Componentes:**
  - `components/AppButton.js` — botão reutilizável que recebe título, estilo e função de ação por props.
  - `components/GradeInput.js` — campo reutilizável para entrada de texto e notas.
  - `components/StatusPill.js` — indicador visual de média atingida ou abaixo da média mínima.
  - `components/SubjectCard.js` — cartão reutilizável para exibir uma disciplina no histórico.
- **Props com callback:** `components/SubjectCard.js` recebe `subject` e `onPress`; ao ser pressionado, envia a disciplina selecionada para a tela pai. `AppButton.js` também recebe a função `onPress` por props.
- **useState:** `App.js` mantém a lista de disciplinas cadastradas (`subjects`). `screens/CalculatorScreen.js` utiliza estados para o nome da disciplina, as três notas, a média mínima, a média calculada e mensagens de validação.
- **useEffect:** `screens/CalculatorScreen.js` recalcula a prévia da média sempre que uma das três notas é alterada. O efeito possui as três notas no array de dependências.
- **Navegação com parâmetros:** `App.js` configura o `NavigationContainer` e o `createNativeStackNavigator` com três telas. Em `CalculatorScreen.js`, o resultado é enviado com `navigation.navigate('Detalhes', { materia: subject })`. Em `DetailsScreen.js`, os dados são recebidos por `route.params.materia`. A tela inicial também envia uma disciplina selecionada para a tela de detalhes.
- **Estilos:** os estilos das telas e dos componentes são definidos com `StyleSheet.create`.

## Vídeo de demonstração

/demo/demo.mp4

## Como executar

## Localmente

O projeto deve estar dentro de um projeto criado com o template blank do Expo. Na pasta raiz do projeto, execute:

npm install
npx expo start

## Pelo Expo Snack

Abra o projeto no Expo Snack.

Mantenha a estrutura de pastas e os nomes dos arquivos indicados neste README.

Utilize o Expo SDK 54, com versões das dependências compatíveis com esse SDK.
