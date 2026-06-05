# Roupa Solidária

Aplicativo mobile que conecta instituições que doam roupas com pessoas que precisam delas.

## Sobre o projeto

**Disciplina:** Programação para Dispositivos Móveis em Android
**Professor:** Julio Cartier

**Integrantes:**
-ANA LUCIA DE SOUSA — 202402435914
- HUGO LEONARDO LIMA MARTINS — 2023309722038
- MATHEUS MUNIZ GOMES— 202302292054
- PHILIPPE VILLENEUVE DE FRANÇA MARTINS — 202403755221

## Problema social

Muitas famílias em situação de vulnerabilidade precisam de roupas — principalmente peças para frio, roupas infantis e uniformes escolares — mas não sabem onde encontrar instituições que estão distribuindo. Por outro lado, ONGs, igrejas e instituições beneficentes nem sempre conseguem divulgar de forma eficiente o que têm disponível.

O Roupa Solidária resolve esse problema com dois fluxos diferentes:

- **Doadores** (qualquer pessoa, sem precisar de cadastro) podem ver a lista pública de doações e entrar em contato direto pelo WhatsApp, telefone ou e-mail.
- **Instituições** (com login e senha) podem cadastrar, editar e excluir suas próprias doações.

## Funcionalidades
### CRUD
 **CREATE** — Cadastrar uma nova doação disponível
- **READ** — Listar todas as doações ordenadas pela mais recente
- **UPDATE** — Editar uma doação existente
- **DELETE** — Excluir uma doação
- Acionar contato direto (telefone ou e-mail) via `Linking`

### Para o público em geral

- Lista de doações ordenadas da mais recente pra mais antiga
- Detalhes completos: tipo de peça, tamanho, quantidade, endereço
- Botões de contato direto:
  - WhatsApp com mensagem pré-pronta
  - Telefone (abre o discador)
  - E-mail
- Endereço clicável que abre no Google Maps

### Para instituições

- Cadastro de conta com nome, e-mail e senha
- Login persistente (continua logado mesmo fechando o app)
- Painel próprio com apenas as doações da instituição
- CRUD completo: criar, ler, atualizar e deletar
- Botões de editar e excluir só aparecem pra quem cadastrou a doação

## Tecnologias usadas

- **Expo SDK 52** (framework React Native)
- **React Navigation 7** (navegação entre telas)
- **Firebase Firestore** (banco de dados em nuvem)
- **Firebase Authentication** (login por e-mail e senha)
- **AsyncStorage** (persistência de sessão)
- JavaScript

## Estrutura de pastas

```
RoupaSolidaria/
├── App.js
├── index.js
├── app.json              (configuração Expo)
├── package.json
└── src/
    ├── firebaseConfig.js
    ├── assets/           (ícones e splash)
    ├── navigation/
    │   └── AppNavigator.js
    ├── services/
    │   ├── authService.js
    │   └── donationService.js
    ├── screens/
    │   ├── WelcomeScreen.js
    │   ├── HomeScreen.js
    │   ├── LoginScreen.js
    │   ├── RegisterScreen.js
    │   ├── MyDonationsScreen.js
    │   ├── AddDonationScreen.js
    │   └── DetailScreen.js
    └── components/
        └── DonationCard.js
```

## Como rodar o projeto

### Pré-requisitos

1. Node.js LTS (https://nodejs.org)
2. App Expo Go no celular Android (baixa na Play Store)
3. Conta no Firebase (https://console.firebase.google.com) com:
   - Firestore Database criado em modo de teste
   - Authentication com método E-mail/senha ativado

### Passo a passo

1. Extraia o projeto numa pasta sem espaços/acentos.

2. Abra um terminal na pasta do projeto e instale as dependências:

```
npm install
```

3. Atualize as credenciais do Firebase no arquivo `src/firebaseConfig.js`.

4. Inicie o servidor Expo:

```
npx expo start
```

5. Vai aparecer um QR code no terminal. Abra o app Expo Go no celular e escaneie esse QR code. O app vai abrir no celular conectado ao computador.

Pra rodar no navegador (visualização limitada):

```
npx expo start --web
```

## Como gerar APK

Pra gerar APK pronto pra instalar no celular, use o EAS Build (serviço gratuito do Expo):

1. Instale o EAS CLI:
```
npm install -g eas-cli
```

2. Faça login na sua conta Expo:
```
eas login
```

3. Configure o build:
```
eas build:configure
```

4. Gere o APK:
```
eas build --platform android --profile preview
```

Após alguns minutos, o link de download do APK fica disponível na sua conta Expo.
