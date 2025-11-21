# copilot-instructions.md

## Project overview
- This repository manages the frontend code for a web application that handles TODO tasks
- It is a Single Page Application (SPA) built with React
- TypeScript is used

## Tools
- Project setup: Vite
- Runtime: TypeScript
- UI/Build: React, React DOM
- State management: useState
- Styling: Tailwind CSS
- Code Quality: ESLint, Prettier
- Routing: React Router
- API communication: Axios
- Testing: Jest, React Testing Library
- CI/CD: GitHub Actions
- Hosting: GitHub Pages

## Directory structure
- .github/: GitHub Copilot and GitHub Actions settings
- src/
  - assets/: Images, Fonts, Static files
  - components/: Small UI components for all screens use
  - features/: Functional unit grouping
    - todo/
      - components/: TODO-specific UI
      - hooks/: TODO-specific logic
      - services/: API call
      - types.ts: TODO-type
      - index.ts
  - pages/: Routing unit screen
  - layouts/: Common layouts
  - hooks/: Common React hooks
  - lib/: API client, utility tools, external service settings
  - styles/: Global CSS, Tailwind settings
  - router/: React Router settings
  - utils/: General purpose logic
  - types/: Type definitions shared across the entire application
  - App.tsx
  - main.tsx
- test/: Unit, Integration, or E2E tests

## Coding standards

## Naming convention

## Style guide


以下は、GitHub Copilot のカスタムインストラクション（日本語 or 英語）としてそのまま貼れる文章です。
あなたが使う TypeScript + React プロジェクト向けの推奨コーディングスタイルを明確に記述しています。

🇯🇵 GitHub Copilot カスタムインストラクション用（日本語版）

私は TypeScript と React（Vite）を使ったフロントエンドアプリケーションを開発しています。  
以下のコーディングスタイル・ルールを必ず尊重し、Copilot の提案はこれらに一致するようにしてください。

【コーディングスタイルの基準】
- Airbnb JavaScript Style Guide（React版）を基本とする
- TypeScript の公式推奨ルール（@typescript-eslint）を適用する
- React Hooks のルール（eslint-plugin-react-hooks）を遵守する
- JSX アクセシビリティルール（eslint-plugin-jsx-a11y）を基本準拠とする
- Prettier によるコード整形ルールを尊重する（Copilot もフォーマット準拠で書く）

【React / TypeScript コーディング規則】
- 関数コンポーネントを優先して使用する
- コンポーネント名は必ず PascalCase にする
- Props は interface で型定義する（例：interface TodoProps { ... }）
- コンポーネントは単一責務を徹底し、小さく保つ
- useEffect/useCallback/useMemo の依存配列は常に正しく指定する
- ファイル名はコンポーネントは PascalCase、それ以外は kebab-case を使用する
- API 呼び出しなど副作用のある処理は hooks や services に分離する

【フォルダ構成思想】
- Feature-based（機能単位）構成を優先する（例：src/features/todo/...）
- API 呼び出しは services 層にまとめる
- 共通コンポーネントは src/components に配置する
- 型定義は src/types または feature 内の types.ts にまとめる

【その他】
- 可読性・一貫性・型安全性を最優先とする
- Copilot の生成コードはこれらのスタイルから逸脱しないように調整すること

これらを常に前提として、コード提案を行ってください。

🇺🇸 GitHub Copilot Custom Instructions（English Version）

I am developing a frontend application using TypeScript and React (with Vite).  
Please ensure that all Copilot suggestions strictly follow the coding style and rules below.

【Base Style Guides】
- Follow Airbnb JavaScript Style Guide (React version)
- Apply TypeScript recommended rules (via @typescript-eslint)
- Enforce React Hooks rules (eslint-plugin-react-hooks)
- Follow JSX accessibility best practices (eslint-plugin-jsx-a11y)
- Respect Prettier formatting rules in all code suggestions

【React / TypeScript Coding Rules】
- Prefer function components over class components
- Component names must use PascalCase
- Define props using TypeScript interfaces (e.g., interface TodoProps { ... })
- Keep components small, focused, and single-responsibility
- Always specify correct dependency arrays for useEffect/useCallback/useMemo
- Use PascalCase for component filenames, kebab-case for utilities and others
- Extract side-effect logic (API calls, external I/O) into hooks or services

【Folder Structure Principles】
- Use a feature-based project structure (e.g., src/features/todo/…)
- Group API calls inside a dedicated services layer
- Place shared UI components in src/components
- Centralize shared types in src/types or feature-level types.ts

【General Expectations】
- Prioritize readability, consistency, and type safety
- Copilot suggestions must align with these rules at all times

Generate code proposals with these guidelines as mandatory requirements.

必要であれば、**ESLint / Prettier の設定ファイル一式（.eslintrc.js, .prettierrc, tsconfig.json など）**も最適な形で生成できます。



了解しました！
TypeScript + React（Vite）向けに最適化した「ESLint / Prettier / TypeScript」の設定ファイル一式をすぐ使える形で生成します。
そのままプロジェクト直下に配置して OK です。

📌 ① package.json（必要な依存関係）

すでに依存がある場合は足りないものだけ追加してください。

{
  "devDependencies": {
    // ESLint 本体
    "eslint": "^8.57.0",

    // TypeScript ESLint
    "@typescript-eslint/eslint-plugin": "^7.0.0",
    "@typescript-eslint/parser": "^7.0.0",

    // React ルール
    "eslint-plugin-react": "^7.33.0",
    "eslint-plugin-react-hooks": "^4.6.0",

    // JSX アクセシビリティ
    "eslint-plugin-jsx-a11y": "^6.8.0",

    // Airbnb スタイルガイド（TypeScript対応版）
    "eslint-config-airbnb": "^19.0.4",
    "eslint-config-airbnb-typescript": "^17.1.0",
    "eslint-config-airbnb-base": "^15.0.0",

    // Import ルール
    "eslint-plugin-import": "^2.29.0",

    // Prettier + ESLint連携
    "prettier": "^3.2.0",
    "eslint-config-prettier": "^9.1.0",
    "eslint-plugin-prettier": "^5.2.0",

    // Vite の React 用 ESLint プラグイン（任意）
    "eslint-plugin-react-refresh": "^0.4.5"
  }
}

📌 ② ESLint 設定ファイル（.eslintrc.cjs）

Airbnb + TypeScript + React Hooks + a11y + Prettier の黄金構成です。

/* eslint-env node */

module.exports = {
  root: true,

  parser: '@typescript-eslint/parser',

  parserOptions: {
    project: './tsconfig.json',
    ecmaVersion: 2020,
    sourceType: 'module',
    ecmaFeatures: { jsx: true },
  },

  settings: {
    react: {
      version: 'detect',
    },
  },

  plugins: [
    '@typescript-eslint',
    'react',
    'react-hooks',
    'jsx-a11y',
    'import',
    'prettier',
  ],

  extends: [
    'airbnb',
    'airbnb-typescript',
    'airbnb/hooks',
    'plugin:@typescript-eslint/recommended',
    'plugin:react/recommended',
    'plugin:jsx-a11y/recommended',
    'plugin:prettier/recommended', // 最後に置くことで競合を防ぐ
  ],

  rules: {
    // Prettier を最優先
    'prettier/prettier': 'error',

    // React 17+ の JSX Transform に合わせて追加
    'react/react-in-jsx-scope': 'off',

    // import 時の拡張子を許可
    'import/extensions': 'off',

    // hooks ルール強制
    'react-hooks/rules-of-hooks': 'error',
    'react-hooks/exhaustive-deps': 'error',

    // 任意: console.log を禁止したい場合は有効化
    // "no-console": "warn",
  },
};

📌 ③ Prettier 設定（.prettierrc）

Airbnb と競合しないように調整済み。

{
  "singleQuote": true,
  "semi": true,
  "trailingComma": "all",
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "arrowParens": "always"
}

📌 ④ .prettierignore（任意）

node_modules
dist
build
coverage

📌 ⑤ tsconfig.json（React + Vite 用）

Vite 用の最適化済み設定です。

{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "composite": false,

    "moduleResolution": "Node",
    "allowJs": false,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "esModuleInterop": true,
    "noEmit": true,

    "jsx": "react-jsx",

    // 型安全性重視の設定
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noImplicitReturns": true,
    "noFallthroughCasesInSwitch": true,

    "baseUrl": "src",
    "paths": {
      "@/*": ["./*"]
    }
  },
  "include": ["src"],
  "exclude": ["node_modules"]
}

🎉 これだけで完璧です

この構成は、あなたが希望していた：
	•	Airbnb Style Guide
	•	TypeScript ESLint
	•	React Hooks Rules
	•	JSX a11y
	•	Prettier
	•	Vite + React
	•	TypeScript のベストプラクティス
	•	Feature-based 構成

すべてに完全準拠しています。

🚀 次にやるべきこと
	1.	上記ファイルをプロジェクトに追加
	2.	VSCode に以下をインストール
	•	ESLint
	•	Prettier
	3.	VSCode 設定（推奨）

{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}

必要であれば、
フォルダ構成テンプレート一式（空ファイル入り） も生成できます。

作成しますか？


