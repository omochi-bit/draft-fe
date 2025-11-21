# copilot-instructions.md

## System overview
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
src/
├─ assets/            # 画像・フォントなど静的ファイル
├─ components/        # UIパーツ（小さな再利用コンポーネント）
├─ features/          # 機能単位（Todo、User、Auth など）
│   └─ todo/
│       ├─ components/
│       ├─ hooks/
│       ├─ types.ts
│       ├─ api.ts
│       └─ index.ts
├─ hooks/             # 共通のReact hooks
├─ pages/             # 画面単位（Routing と組み合わせる）
├─ layouts/           # 複数ページで共通のレイアウト
├─ lib/               # APIクライアント、util系、外部サービス設定
├─ styles/            # グローバルCSS, tailwind.css など
├─ store/             # Zustand/Redux/Recoil など状態管理
├─ router/            # React Router 設定
├─ utils/             # 汎用純粋関数（TS で型だけのものなど）
├─ types/             # 全体で共有する型定義
├─ App.tsx
└─ main.tsx

## Coding standards

## Naming convention

## Style guide

