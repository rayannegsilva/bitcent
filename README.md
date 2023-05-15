<h2>
  <img src=".github/cover.svg" alt="Bitcent"/>
</h2>

# BitCent

Bitcent é uma aplicação web para controle de finanças pessoais com landing page e dashboard. O projeto utiliza o Firebase para autenticação e armazenamento de dados.

O projeto foi desenvolvido durante a **[Semana Tranformação.DEV](https://transformacao.dev/)** realizada pelo 
**[Cod3r](https://www.cod3r.com.br/)**!

Você pode encontrar acessar o projeto rodando clicando nesse link: **[Bitcent](bitcent-chi.vercel.app )**


## 🛠 Tecnologias

As tecnologias utilizadas nesse projeto, foram: 

- [React](https://reactjs.org)
- [Next.js](https://nextjs.org/)
- [Mantine](https://mantine.dev/)
- [Firebase](https://firebase.google.com/)
- [TypeScript](https://www.typescriptlang.org/)
- [TailwindCSS](https://tailwindcss.com/)

## 🚗 Como rodar

Antes de tudo é necessário clonar o repositório e baixar suas dependências:

```bash
git clone https://github.com/rayannegsilva/bitcent.git
cd bitcent
npm i
```

Crie um projeto no Firebase e ative a autenticação com o Google. Nas regras do Database, copie e cole:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
    	allow read, write: if false;
    }

    match /financas/{email}/transacoes/{id} {
  		allow read: if (request.auth != null && request.auth.token.email == email);
      allow write: if (request.auth != null && request.auth.token.email == email);
    }
    
    match /usuarios/{email} {
  		allow read: if (request.auth != null && request.auth.token.email == email);
      allow write: if (request.auth != null && request.auth.token.email == email);
    }
  }
}

```

Mude o arquivo `.env.local.example` para `env.local` e adicione as credenciais que o projeto pede:

```
NEXT_PUBLIC_FIREBASE_PROJECT_ID=
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=
NEXT_PUBLIC_FIREBASE_API_KEY=
```
