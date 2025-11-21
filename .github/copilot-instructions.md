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

