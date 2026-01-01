# nFKs Authentication Server 


## 📁 Backend folder structure (exact)
```
nfks-auth-server/
├── src/
│   ├── auth/
│   │   ├── authorize.controller.ts   ← /authorize
│   │   ├── token.controller.ts       ← /token
│   │   ├── pkce.ts                   ← PKCE verify
│   │   ├── jwks.ts                   ← /.well-known/jwks.json
│   │   └── store.ts                  ← auth codes (dev)
│   │
│   ├── routes.ts
│   ├── server.ts
│   └── main.ts
│
├── .env
├── package.json
└── tsconfig.json
```

## 🔗 How frontend talks to backend

Your existing frontend code stays almost the same.

Example:

```
Consent → Redirect
window.location.href =
  `http://localhost:4000/authorize?` +
  new URLSearchParams({
    client_id: state.clientApp.clientId,
    redirect_uri: state.clientApp.redirectUri,
    code_challenge: state.codeChallenge!,
    code_challenge_method: "S256",
    scope: state.scopes.join(" "),
  });

Callback → Token exchange
POST http://localhost:4000/token
```
