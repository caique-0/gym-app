# 🏋️ Meu Treino

PWA de academia com progressão de carga, histórico na nuvem e suporte a smartwatch.

🔗 **[Acessar o app](https://caique-0.github.io/gym-app)**

---

## Funcionalidades

- **Login com Google** — histórico salvo na nuvem por usuário
- **Progressão de carga** — compara a carga atual com a sessão anterior
- **Timer de descanso** — conta regressiva com vibração ao terminar
- **Histórico visual** — gráfico de barras com evolução das últimas sessões
- **Modo Galaxy Watch** — UI adaptada para telas ≤ 320px
- **Funciona offline** — Service Worker faz cache dos arquivos
- **Modo claro/escuro** — segue a preferência do sistema

---

## Tecnologias

| Camada | Tecnologia |
|---|---|
| Frontend | HTML, CSS, JavaScript (vanilla) |
| Autenticação | Firebase Authentication (Google) |
| Banco de dados | Firebase Firestore |
| Hospedagem | GitHub Pages |
| Offline | Service Worker (Cache API) |

---

## Instalação no celular

1. Acesse **https://caique-0.github.io/gym-app** no Chrome
2. Toque nos 3 pontinhos → **"Adicionar à tela inicial"**
3. O app abre em tela cheia como um app nativo

## Instalação no Galaxy Watch

1. Abra o app **Internet** no relógio
2. Acesse **https://caique-0.github.io/gym-app/?watch**
3. O app entra no modo relógio automaticamente (sem tela de login)
4. Toque em ★ para fixar nos favoritos

> O parâmetro `?watch` garante compatibilidade com todos os modelos de Galaxy Watch.

---

## Estrutura do projeto

```
gym-app/
├── index.html          # App completo (phone + watch)
├── manifest.json       # Configuração do PWA
├── service-worker.js   # Cache offline
├── icon-192.png        # Ícone PWA 192x192
└── icon-512.png        # Ícone PWA 512x512
```

---

## Segurança

As regras do Firestore garantem que cada usuário acessa apenas seus próprios dados:

```js
match /users/{userId} {
  allow read, write: if request.auth != null && request.auth.uid == userId;
}
```

---

## Desenvolvimento local

```bash
git clone https://github.com/caique-0/gym-app.git
cd gym-app
npx serve .
```

Acesse `http://localhost:3000` no navegador.
