# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default tseslint.config({
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- Replace `tseslint.configs.recommended` to `tseslint.configs.recommendedTypeChecked` or `tseslint.configs.strictTypeChecked`
- Optionally add `...tseslint.configs.stylisticTypeChecked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and update the config:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Set the react version
  settings: { react: { version: '18.3' } },
  plugins: {
    // Add the react plugin
    react,
  },
  rules: {
    // other rules...
    // Enable its recommended rules
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```


# Cấu trúc dự án

GUNDAMMARKET/
├── node_modules/
├── public/
│   └── assets/
├── src/
│   ├── application/           # Logic xử lý nghiệp vụ (Use Cases)
│   │   └── usecases/
│   │       └── GetProductUseCase.ts
│   ├── domain/                # Các đối tượng, logic nghiệp vụ thuần túy
│   │   ├── entities/
│   │   │   └── Product.ts
│   │   └── repositories/
│   │       └── ProductRepository.ts
│   ├── infrastructure/        # Xử lý tương tác với API, database, third-party services
│   │   ├── api/
│   │   │   └── ProductApi.ts
│   │   └── services/
│   │       └── ProductService.ts
│   ├── presentation/          # Thành phần giao diện và xử lý giao diện
│   │   ├── components/        # Các component nhỏ
│   │   │   ├── Button.tsx
│   │   │   ├── Icon.tsx
│   │   │   └── Favourite.tsx
|   |   |__ ui/
|   |   |   |__ Header.tsx
|   |   |   |__ Footer.tsx
│   │   ├── pages/             # Các trang chính của ứng dụng
│   │   │   ├── user
│   │   │   ├── admin
│   │   ├── routes/            # Định nghĩa routing
│   │   │   └── AppRouter.tsx
│   │   ├── styles/            # Styles của dự án
│   │   │   └── main.css
│   │   └── App.tsx
│   ├── shared/                # Các thành phần dùng chung trong dự án
│   │   └── constants.js
│   └── main.tsx               # Entry point của ứng dụng
├── .gitignore
├── index.html                 # File HTML gốc
├── package.json
├── vite.config.js             # Cấu hình Vite
└── README.md

