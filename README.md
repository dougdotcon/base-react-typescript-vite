# React + TypeScript + Vite

Bem-vindo ao template **React + TypeScript + Vite**! Este template oferece uma configuração minimalista para iniciar rapidamente projetos React utilizando TypeScript e Vite, aproveitando Hot Module Replacement (HMR) e regras básicas do ESLint.

## Índice

- [Visão Geral](#visão-geral)
- [Recursos](#recursos)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Scripts Disponíveis](#scripts-disponíveis)
- [Configuração do ESLint](#configuração-do-eslint)
- [Plugins Oficiais Disponíveis](#plugins-oficiais-disponíveis)
- [Expansão da Configuração do ESLint](#expansão-da-configuração-do-eslint)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Construção para Produção](#construção-para-produção)
- [Deploy](#deploy)
- [Contribuição](#contribuição)
- [Licença](#licença)

## Visão Geral

Este template utiliza **Vite** como bundler para proporcionar um ambiente de desenvolvimento rápido e eficiente. Combinado com **React** e **TypeScript**, oferece uma base robusta para desenvolver aplicações web modernas, escaláveis e tipadas.

## Recursos

- **Vite**: Ferramenta de build rápida com suporte a Hot Module Replacement (HMR).
- **React**: Biblioteca JavaScript para construção de interfaces de usuário.
- **TypeScript**: Superset de JavaScript que adiciona tipagem estática.
- **ESLint**: Ferramenta de linting para garantir a qualidade do código.
- **Plugins Oficiais do Vite**: Integração com Babel ou SWC para Fast Refresh.

## Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [Node.js](https://nodejs.org/) (versão 14 ou superior)
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/)

## Instalação

Clone este repositório e instale as dependências:

```bash
git clone https://github.com/seu-usuario/seu-repo.git
cd seu-repo
npm install
# ou
yarn install
```

## Scripts Disponíveis

No diretório do projeto, você pode executar:

- **`npm run dev`** ou **`yarn dev`**: Inicia o servidor de desenvolvimento com HMR.
- **`npm run build`** ou **`yarn build`**: Compila a aplicação para produção.
- **`npm run preview`** ou **`yarn preview`**: Serve a versão compilada para pré-visualização.
- **`npm run lint`** ou **`yarn lint`**: Executa o linting do código com ESLint.

## Configuração do ESLint

Este template inclui uma configuração básica do ESLint para garantir a consistência e qualidade do código. Para personalizar ou expandir as regras do ESLint, siga as instruções abaixo.

### Configuração Básica

O arquivo de configuração do ESLint está localizado em `eslint.config.js`. Ele utiliza as configurações recomendadas para TypeScript e React.

```javascript
// eslint.config.js
import { defineConfig } from 'eslint-define-config'

export default defineConfig({
  parser: '@typescript-eslint/parser',
  extends: [
    'eslint:recommended',
    'plugin:react/recommended',
    'plugin:@typescript-eslint/recommended',
  ],
  plugins: ['react', '@typescript-eslint'],
  env: {
    browser: true,
    es2021: true,
  },
  settings: {
    react: {
      version: 'detect',
    },
  },
  rules: {
    // Adicione ou modifique regras conforme necessário
  },
})
```

## Plugins Oficiais Disponíveis

Atualmente, dois plugins oficiais estão disponíveis para integrar React com Vite:

1. **[@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md)**
   - Utiliza [Babel](https://babeljs.io/) para Fast Refresh.
   - Ideal para projetos que já utilizam Babel ou que necessitam de funcionalidades específicas do Babel.

2. **[@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc)**
   - Utiliza [SWC](https://swc.rs/) para Fast Refresh.
   - Oferece tempos de build mais rápidos devido ao desempenho otimizado do SWC.

### Como Usar um Plugin

No arquivo `vite.config.ts`, você pode configurar o plugin de sua preferência:

```typescript
// vite.config.ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
// ou
// import react from '@vitejs/plugin-react-swc'

export default defineConfig({
  plugins: [react()],
})
```

## Expansão da Configuração do ESLint

Se você está desenvolvendo uma aplicação em produção, é recomendável aprimorar a configuração do ESLint para incluir regras mais rigorosas e baseadas em tipos.

### Passo a Passo

1. **Atualize as opções do parser no ESLint:**

   Edite o `eslint.config.js` para incluir `parserOptions` com os caminhos para seus arquivos `tsconfig.json`.

   ```javascript
   // eslint.config.js
   import { defineConfig } from 'eslint-define-config'

   export default defineConfig({
     parser: '@typescript-eslint/parser',
     parserOptions: {
       project: ['./tsconfig.node.json', './tsconfig.app.json'],
       tsconfigRootDir: __dirname,
       ecmaVersion: 'latest',
       sourceType: 'module',
     },
     extends: [
       'eslint:recommended',
       'plugin:react/recommended',
       'plugin:@typescript-eslint/recommended',
       'plugin:@typescript-eslint/recommended-requiring-type-checking',
     ],
     plugins: ['react', '@typescript-eslint'],
     env: {
       browser: true,
       es2021: true,
     },
     settings: {
       react: {
         version: 'detect',
       },
     },
     rules: {
       // Regras adicionais ou modificadas
     },
   })
   ```

2. **Substitua as configurações recomendadas:**

   - Substitua `eslint:recommended` por `plugin:@typescript-eslint/recommendedTypeChecked` ou `plugin:@typescript-eslint/recommendedStrict`.

3. **Opcional: Adicione regras estilísticas:**

   - Você pode incluir `plugin:@typescript-eslint/stylisticTypeChecked` para regras de estilo baseadas em tipos.

4. **Instale o plugin do React para ESLint:**

   ```bash
   npm install eslint-plugin-react --save-dev
   # ou
   yarn add eslint-plugin-react --dev
   ```

5. **Atualize a configuração do ESLint para incluir o plugin do React:**

   ```javascript
   // eslint.config.js
   import { defineConfig } from 'eslint-define-config'
   import react from 'eslint-plugin-react'

   export default defineConfig({
     parser: '@typescript-eslint/parser',
     parserOptions: {
       project: ['./tsconfig.node.json', './tsconfig.app.json'],
       tsconfigRootDir: __dirname,
       ecmaVersion: 'latest',
       sourceType: 'module',
     },
     extends: [
       'eslint:recommended',
       'plugin:react/recommended',
       'plugin:@typescript-eslint/recommended',
       'plugin:@typescript-eslint/recommended-requiring-type-checking',
     ],
     plugins: ['react', '@typescript-eslint'],
     env: {
       browser: true,
       es2021: true,
     },
     settings: {
       react: {
         version: 'detect',
       },
     },
     rules: {
       // Regras adicionais ou modificadas
       ...react.configs.recommended.rules,
       ...react.configs['jsx-runtime'].rules,
     },
   })
   ```

## Estrutura do Projeto

A estrutura do projeto segue uma organização padrão, facilitando a manutenção e escalabilidade:

```
seu-projeto/
├── node_modules/
├── public/
│   └── index.html
├── src/
│   ├── assets/
│   ├── components/
│   ├── hooks/
│   ├── pages/
│   ├── styles/
│   ├── App.tsx
│   ├── main.tsx
│   └── vite-env.d.ts
├── .eslintrc.js
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.node.json
├── vite.config.ts
├── package.json
└── README.md
```

- **public/**: Contém arquivos estáticos como `index.html`.
- **src/**: Código-fonte da aplicação.
  - **assets/**: Imagens, fontes e outros recursos estáticos.
  - **components/**: Componentes reutilizáveis do React.
  - **hooks/**: Hooks personalizados.
  - **pages/**: Componentes de páginas.
  - **styles/**: Arquivos de estilo (CSS, SCSS, etc.).
  - **App.tsx**: Componente raiz da aplicação.
  - **main.tsx**: Ponto de entrada da aplicação.
  - **vite-env.d.ts**: Declarações de tipos para Vite.
- **tsconfig.json**: Configuração principal do TypeScript.
- **vite.config.ts**: Configuração do Vite.
- **package.json**: Dependências e scripts do projeto.

## Construção para Produção

Para compilar sua aplicação para produção, execute:

```bash
npm run build
# ou
yarn build
```

Isso gerará uma pasta `dist/` com os arquivos otimizados prontos para serem servidos em um servidor web.

## Deploy

Após a construção, você pode fazer o deploy da pasta `dist/` em diversos serviços de hospedagem, como:

- **Vercel**
- **Netlify**
- **GitHub Pages**
- **Firebase Hosting**
- **Surge**

Cada serviço possui seu próprio processo de deploy, geralmente envolvendo a conexão do repositório e a configuração do diretório de saída (`dist`).

### Exemplo: Deploy no Vercel

1. Instale a [Vercel CLI](https://vercel.com/docs/cli).
2. Faça login na Vercel:

   ```bash
   vercel login
   ```

3. Execute o deploy:

   ```bash
   vercel
   ```

4. Siga as instruções no terminal para concluir o processo.

## Contribuição

Contribuições são bem-vindas! Siga os passos abaixo para contribuir:

1. **Fork** este repositório.
2. **Crie uma branch** para sua feature ou correção:
   
   ```bash
   git checkout -b minha-feature
   ```

3. **Commit** suas alterações:

   ```bash
   git commit -m "Adiciona minha feature"
   ```

4. **Push** para a branch:

   ```bash
   git push origin minha-feature
   ```

5. **Abra um Pull Request** descrevendo suas alterações.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---

Desfrute do desenvolvimento com **React**, **TypeScript** e **Vite**! Se tiver dúvidas ou sugestões, sinta-se à vontade para abrir uma issue ou contribuir com o projeto.