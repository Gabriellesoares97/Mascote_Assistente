<p align="center">
  <img src="assets/icon-192.png" width="96" alt="Ícone do Mascote Assistente">
</p>

<h1 align="center">🦊 Mascote Assistente</h1>

<p align="center">
  <a href="#-português-brasil">🇧🇷 Português (Brasil)</a> ·
  <a href="#-português-portugal">🇵🇹 Português (Portugal)</a> ·
  <a href="#-english">🇺🇸 English</a> ·
  <a href="#-español">🇪🇸 Español</a>
</p>

<p align="center">
  <img src="assets/screenshot.png" width="320" alt="Captura de tela do app">
</p>

---

## 🇧🇷 Português (Brasil)

Um app de bem-estar acolhedor, feito para todos os tipos de pessoas organizarem a semana
sem se sobrecarregar — com um mascote fofo pra fazer companhia no caminho.

### ✨ O que o app faz

- **Semana sem sobrecarga** — cada dia tem um limite de tarefas de acordo com o seu nível de
  energia (🦊💤 baixa, 🦊🌿 média, 🦊⚡ alta), com micro-passos, arrastar-e-soltar entre dias e
  exportação para agenda (`.ics`).
- **Lixeira e Armazém de Ideias** — um lugar pra despejar pensamentos soltos sem compromisso, e
  outro pra guardar de verdade as ideias que valem a pena.
- **Hidratação e peso** — meta de água calculada com carinho, sem julgamento, com gráficos de
  evolução dos últimos meses.
- **Movimento** — registro rápido de exercício com trilha semanal de patinhas.
- **Ciclo menstrual** — acompanhamento de fase (menstrual, folicular, ovulatória, lútea) que
  ajusta automaticamente as metas de tarefas e água nos dias que pedem mais gentileza. Pode ser
  desligado nas configurações de gênero.
- **Cantinho da Calma** — respiração guiada, sons ambiente e uma fanfarra própria (composição
  original) tocada ao concluir tarefas.
- **Mascote personalizável** — 13 bichinhos à escolha, cada um com seu próprio desenho de
  patinha inspirado no animal real, e nome customizável.
- **Cores e clima do app** — paleta livre, além de um preset "fofo" (rosa) ou "arrojado" (azul)
  conforme a preferência de gênero, sempre em tons claros e acessíveis.
- **4 idiomas** — Português (Brasil e Portugal), English (US) e Español, com troca em tempo real.
- **Notificações locais** — lembretes de água e tarefas pendentes enquanto a aba estiver aberta.
- **Backup** — exporte e importe seus dados em `.json` a qualquer momento.
- **Conta Google (opcional)** — conecte sua conta pra guardar uma cópia dos dados na nuvem e enviar suas tarefas pro Google Agenda automaticamente. Exige que você crie seu próprio "Client ID" gratuito (veja a seção de configuração abaixo).

### 🧸 Filosofia

Nada aqui empurra produtividade a qualquer custo. Os limites de tarefas por energia, os avisos
gentis e as mensagens do mascote existem pra lembrar que ir devagar também é ir.

O acompanhamento de ciclo é uma ferramenta de bem-estar e autoconhecimento — **não é um método
contraceptivo nem um recurso de diagnóstico clínico.**

### 🛠️ Tecnologia

Um único arquivo HTML, sem dependências, sem build, sem servidor. HTML + CSS + JavaScript puro,
com dados salvos localmente no seu navegador (`localStorage`) — nada é enviado pra fora do seu
dispositivo.

### 🚀 Como usar

Baixe o [`index.html`](index.html) (e a pasta [`assets/`](assets)) e abra no navegador. Se os
dados não salvarem entre sessões (`localStorage` pode ser restrito em `file://`), sirva a pasta
com um servidor local simples:

```bash
python3 -m http.server 8000
```

**GitHub Pages:** suba o repositório, ative em *Settings → Pages* (branch principal, pasta raiz)
e o `index.html` vira a página inicial automaticamente.

### ⚠️ Limitações conhecidas

- Notificações só funcionam com a aba do app aberta (sem servidor/backend, não há push real).
- Nomes dos dias da semana, tags de tarefa e tipos de exercício ainda não foram traduzidos.

### 🔐 Configurando a integração com o Google (opcional) — passo a passo pra quem nunca fez isso

Esse recurso é opcional e exige que **você mesmo** crie uma credencial gratuita chamada "Client ID" — é como uma identidão do seu app, pra o Google saber quem está pedindo acesso. Ninguém pode criar isso por você, mas o passo a passo abaixo não exige nenhum conhecimento técnico, só ir clicando com calma.

**O que você vai precisar:** uma conta Google (a mesma do Gmail) e uns 10-15 minutos.

**Passo 1 — Crie um projeto no Google Cloud**
1. Acesse [console.cloud.google.com](https://console.cloud.google.com/) e faça login com sua conta Google.
2. No topo da página, clique no menu de projetos (ao lado do texto "Google Cloud") e depois em **"Novo projeto"**.
3. Dê um nome qualquer, tipo "Meu Mascote Assistente", e clique em **"Criar"**. É gratuito e não pede cartão de crédito.
4. Espere alguns segundos até o Google avisar que o projeto foi criado, e confirme que ele está selecionado no menu do topo.

**Passo 2 — Ative as duas APIs que o app usa**
1. Na barra de busca do topo da página, digite **"Google Calendar API"** e clique no resultado.
2. Clique no botão azul **"Ativar"**.
3. Volte pra busca do topo, digite **"Google Drive API"** e clique no resultado.
4. Clique em **"Ativar"** de novo.

**Passo 3 — Configure a "Tela de consentimento" (a telinha que aparece quando você faz login)**
1. No menu à esquerda, procure **"APIs e Serviços" → "Tela de consentimento OAuth"**.
2. Escolha **"Externo"** e clique em "Criar".
3. Preencha só os campos obrigatórios: nome do app (ex: "Mascote Assistente"), seu e-mail de suporte, e seu e-mail de contato do desenvolvedor lá embaixo. Clique em "Salvar e continuar" nas telas seguintes (pode pular os campos opcionais).
4. Quando chegar na etapa **"Usuários de teste"**, clique em "Adicionar usuários" e coloque o seu e-mail do Gmail (e o de qualquer outra pessoa que for usar o app). **Esse passo é importante** — enquanto o app não passar por uma verificação do Google (processo mais demorado, só necessário se quiser disponibilizar pra qualquer pessoa), só esses e-mails cadastrados aqui conseguem fazer login.

**Passo 4 — Publique o app num endereço da internet (se ainda não publicou)**
O login do Google não funciona abrindo o arquivo `index.html` direto do computador — precisa estar num site publicado com endereço `https://`. Se você já subiu esse repositório pro GitHub e ativou o GitHub Pages (veja a seção "Publicando com GitHub Pages" acima), você já tem esse endereço, algo como `https://seu-usuario.github.io/nome-do-repositorio`.

**Passo 5 — Crie o Client ID**
1. No menu à esquerda, vá em **"APIs e Serviços" → "Credenciais"**.
2. Clique em **"Criar credenciais"** (no topo) e escolha **"ID do cliente OAuth"**.
3. Em "Tipo de aplicativo", escolha **"Aplicativo da Web"**.
4. Em **"Origens JavaScript autorizadas"**, clique em "Adicionar URI" e cole o endereço do seu app (ex: `https://seu-usuario.github.io`) — sem barra no final.
5. Clique em **"Criar"**. Vai aparecer uma janela com o seu **Client ID** — é um texto longo terminado em `.apps.googleusercontent.com`.

**Passo 6 — Cole o Client ID no app**
1. Copie o Client ID gerado.
2. Abra o app, vá na aba **Config → Conta Google**.
3. Cole no campo de texto e clique em **"Salvar Client ID"**.
4. Um botão **"Conectar com Google"** vai aparecer — clique nele e faça login com a mesma conta que você cadastrou como "usuário de teste" no Passo 3.

Pronto! Depois disso é só usar os botões "Sincronizar agora" ou ligar o envio automático de tarefas pro Google Agenda, na mesma seção.

### 🤝 Contribuindo

Veja o [`CONTRIBUTING.md`](CONTRIBUTING.md).

### 📄 Licença

MIT — veja [`LICENSE`](LICENSE).

---

## 🇵🇹 Português (Portugal)

Uma app de bem-estar acolhedora, feita para todos os tipos de pessoas organizarem a semana
sem se sobrecarregarem — com uma mascote fofa para fazer companhia pelo caminho.

### ✨ O que a app faz

- **Semana sem sobrecarga** — cada dia tem um limite de tarefas de acordo com o teu nível de
  energia (🦊💤 baixa, 🦊🌿 média, 🦊⚡ alta), com micro-passos, arrastar e largar entre dias e
  exportação para agenda (`.ics`).
- **Caixote e Armazém de Ideias** — um sítio para despejar pensamentos soltos sem compromisso, e
  outro para guardar mesmo as ideias que valem a pena.
- **Hidratação e peso** — meta de água calculada com carinho, sem julgamentos, com gráficos de
  evolução dos últimos meses.
- **Movimento** — registo rápido de exercício com trilha semanal de patinhas.
- **Ciclo menstrual** — acompanhamento de fase (menstrual, folicular, ovulatória, lútea) que
  ajusta automaticamente as metas de tarefas e água nos dias que pedem mais delicadeza. Pode ser
  desligado nas definições de género.
- **Cantinho da Calma** — respiração guiada, sons ambiente e uma fanfarra própria (composição
  original) tocada ao concluíres tarefas.
- **Mascote personalizável** — 13 bichinhos à escolha, cada um com o seu próprio desenho de pata
  inspirado no animal real, e nome personalizável.
- **Cores e ambiente da app** — paleta livre, além de um preset "fofo" (rosa) ou "arrojado"
  (azul) conforme a preferência de género, sempre em tons claros e acessíveis.
- **4 idiomas** — Português (Brasil e Portugal), English (US) e Español, com troca em tempo real.
- **Notificações locais** — lembretes de água e tarefas pendentes enquanto o separador estiver
  aberto.
- **Cópia de segurança** — exporta e importa os teus dados em `.json` quando quiseres.
- **Conta Google (opcional)** — liga a tua conta para guardares uma cópia dos dados na nuvem e enviares as tuas tarefas para o Google Agenda automaticamente. Exige que crie o teu próprio "Client ID" gratuito (vê a secção de configuração abaixo).

### 🧸 Filosofia

Nada aqui empurra produtividade a qualquer custo. Os limites de tarefas por energia, os avisos
gentis e as mensagens da mascote existem para lembrar que ir devagar também é ir.

O acompanhamento de ciclo é uma ferramenta de bem-estar e autoconhecimento — **não é um método
contracetivo nem um recurso de diagnóstico clínico.**

### 🛠️ Tecnologia

Um único ficheiro HTML, sem dependências, sem build, sem servidor. HTML + CSS + JavaScript puro,
com dados guardados localmente no teu navegador (`localStorage`) — nada é enviado para fora do
teu dispositivo.

### 🚀 Como usar

Descarrega o [`index.html`](index.html) (e a pasta [`assets/`](assets)) e abre no navegador. Se
os dados não guardarem entre sessões, serve a pasta com um servidor local simples:

```bash
python3 -m http.server 8000
```

**GitHub Pages:** sobe o repositório, ativa em *Settings → Pages* (branch principal, pasta raiz)
e o `index.html` torna-se a página inicial automaticamente.

### ⚠️ Limitações conhecidas

- As notificações só funcionam com o separador da app aberto (sem servidor/backend).
- Nomes dos dias da semana, etiquetas de tarefa e tipos de exercício ainda não foram traduzidos.

### 🔐 A configurar a integração com o Google (opcional) — passo a passo para quem nunca fez isto

Este recurso é opcional e exige que **tu mesmo** cries uma credencial gratuita chamada "Client ID" — é como um bilhete de identidade da tua app, para o Google saber quem está a pedir acesso. Ninguém pode criar isto por ti, mas o passo a passo abaixo não exige nenhum conhecimento técnico, só ires clicando com calma.

**O que vais precisar:** uma conta Google (a mesma do Gmail) e uns 10-15 minutos.

**Passo 1 — Cria um projeto na Google Cloud**
1. Acede a [console.cloud.google.com](https://console.cloud.google.com/) e faz login com a tua conta Google.
2. No topo da página, clica no menu de projetos (ao lado do texto "Google Cloud") e depois em **"Novo projeto"**.
3. Dá um nome qualquer, tipo "O Meu Mascote Assistente", e clica em **"Criar"**. É gratuito e não pede cartão de crédito.
4. Espera alguns segundos até a Google avisar que o projeto foi criado, e confirma que está selecionado no menu do topo.

**Passo 2 — Ativa as duas APIs que a app usa**
1. Na barra de pesquisa do topo da página, escreve **"Google Calendar API"** e clica no resultado.
2. Clica no botão azul **"Ativar"**.
3. Volta à pesquisa do topo, escreve **"Google Drive API"** e clica no resultado.
4. Clica em **"Ativar"** outra vez.

**Passo 3 — Configura o "Ecrã de consentimento" (o ecrã que aparece quando fazes login)**
1. No menu à esquerda, procura **"APIs e Serviços" → "Ecrã de consentimento OAuth"**.
2. Escolhe **"Externo"** e clica em "Criar".
3. Preenche só os campos obrigatórios: nome da app (ex: "Mascote Assistente"), o teu e-mail de suporte, e o teu e-mail de contacto do developer lá em baixo. Clica em "Guardar e continuar" nos ecrãs seguintes (podes saltar os campos opcionais).
4. Quando chegares à etapa **"Utilizadores de teste"**, clica em "Adicionar utilizadores" e coloca o teu e-mail do Gmail (e o de qualquer outra pessoa que for usar a app). **Este passo é importante** — enquanto a app não passar por uma verificação da Google (processo mais demorado, só necessário se quiseres disponibilizá-la para qualquer pessoa), só estes e-mails registados aqui conseguem fazer login.

**Passo 4 — Publica a app num endereço da internet (se ainda não publicaste)**
O login da Google não funciona a abrir o ficheiro `index.html` diretamente do computador — precisa de estar num site publicado com endereço `https://`. Se já subiste este repositório para o GitHub e ativaste o GitHub Pages (vê a secção "Publicando com GitHub Pages" acima), já tens esse endereço, algo como `https://o-teu-utilizador.github.io/nome-do-repositorio`.

**Passo 5 — Cria o Client ID**
1. No menu à esquerda, vai a **"APIs e Serviços" → "Credenciais"**.
2. Clica em **"Criar credenciais"** (no topo) e escolhe **"ID de cliente OAuth"**.
3. Em "Tipo de aplicação", escolhe **"Aplicação Web"**.
4. Em **"Origens JavaScript autorizadas"**, clica em "Adicionar URI" e cola o endereço da tua app (ex: `https://o-teu-utilizador.github.io`) — sem barra no final.
5. Clica em **"Criar"**. Vai aparecer uma janela com o teu **Client ID** — é um texto comprido terminado em `.apps.googleusercontent.com`.

**Passo 6 — Cola o Client ID na app**
1. Copia o Client ID gerado.
2. Abre a app, vai ao separador **Config → Conta Google**.
3. Cola no campo de texto e clica em **"Guardar Client ID"**.
4. Vai aparecer um botão **"Ligar com Google"** — clica nele e faz login com a mesma conta que registaste como "utilizador de teste" no Passo 3.

Pronto! Depois disto é só usar os botões "Sincronizar agora" ou ligar o envio automático de tarefas para o Google Agenda, na mesma secção.

⚠️ Este login só funciona com a app publicada num endereço `https://` a sério (GitHub Pages funciona) — não funciona a abrir o `index.html` diretamente do computador.

### 🤝 Contribuir

Vê o [`CONTRIBUTING.md`](CONTRIBUTING.md).

### 📄 Licença

MIT — vê [`LICENSE`](LICENSE).

---

## 🇺🇸 English

A cozy wellness app built for all types of people to plan their week without burning out — with
a cute mascot to keep them company along the way.

### ✨ Features

- **A week without overload** — each day has a task limit based on your energy level (🦊💤 low,
  🦊🌿 medium, 🦊⚡ high), with micro-steps, drag-and-drop between days, and calendar export
  (`.ics`).
- **Idea Dump and Idea Storage** — a place to drop loose thoughts with no pressure, and another to
  actually keep the ideas worth holding onto.
- **Hydration and weight** — a water goal calculated with care, no judgment, plus charts of your
  progress over the past months.
- **Movement** — quick exercise logging with a weekly paw-print streak.
- **Menstrual cycle** — phase tracking (menstrual, follicular, ovulatory, luteal) that
  automatically softens task and water goals on days that call for extra gentleness. Can be
  turned off from the gender settings.
- **Calm Corner** — guided breathing, ambient sounds, and an original victory fanfare played when
  you complete a task.
- **Customizable mascot** — 13 animals to choose from, each with its own paw-print design
  inspired by the real animal's anatomy, plus a customizable name.
- **Colors and app mood** — a free color palette, plus a "cute" (pink) or "bold" (blue) preset
  based on gender preference, always in light, accessible tones.
- **4 languages** — Portuguese (Brazil and Portugal), English (US), and Spanish, switchable live.
- **Local notifications** — reminders about water and pending tasks while the tab is open.
- **Backup** — export and import your data as `.json` whenever you want.
- **Google Account (optional)** — connect your account to keep a cloud copy of your data and automatically send your tasks to Google Calendar. Requires you to create your own free "Client ID" (see the setup section below).

### 🧸 Philosophy

Nothing here pushes productivity at any cost. The energy-based task limits, the gentle nudges, and
the mascot's messages all exist to remind you that going slow still counts as going.

Cycle tracking is a wellness and self-knowledge tool — **it is not a contraceptive method or a
clinical diagnostic resource.**

### 🛠️ Tech stack

A single HTML file, no dependencies, no build step, no server. Plain HTML + CSS + JavaScript, with
data saved locally in your browser (`localStorage`) — nothing ever leaves your device.

### 🚀 Getting started

Download [`index.html`](index.html) (and the [`assets/`](assets) folder) and open it in your
browser. If data isn't saving between sessions (`localStorage` can be restricted for `file://`),
serve the folder with a simple local server instead:

```bash
python3 -m http.server 8000
```

**GitHub Pages:** push the repo, enable it under *Settings → Pages* (main branch, root folder),
and `index.html` becomes the homepage automatically.

### ⚠️ Known limitations

- Notifications only fire while the app's tab is open (serverless app, no real push support).
- Weekday names, task tags, and exercise types haven't been translated yet.

### 🔐 Setting up the Google integration (optional) — step by step for beginners

This feature is optional and requires **you** to create a free credential called a "Client ID" yourself — think of it as an ID card for your copy of the app, so Google knows who's asking for access. Nobody else can create this for you, but the steps below don't require any technical knowledge, just clicking around calmly.

**What you'll need:** a Google account (the same one as your Gmail) and about 10-15 minutes.

**Step 1 — Create a project in Google Cloud**
1. Go to [console.cloud.google.com](https://console.cloud.google.com/) and sign in with your Google account.
2. At the top of the page, click the project menu (next to the "Google Cloud" text) and then **"New Project"**.
3. Give it any name, like "My Mascote Assistente", and click **"Create"**. It's free and doesn't ask for a credit card.
4. Wait a few seconds until Google confirms the project was created, and make sure it's selected in the top menu.

**Step 2 — Enable the two APIs the app uses**
1. In the search bar at the top of the page, type **"Google Calendar API"** and click the result.
2. Click the blue **"Enable"** button.
3. Go back to the top search bar, type **"Google Drive API"** and click the result.
4. Click **"Enable"** again.

**Step 3 — Set up the "consent screen" (the screen that shows up when you sign in)**
1. In the left-side menu, find **"APIs & Services" → "OAuth consent screen"**.
2. Choose **"External"** and click "Create".
3. Fill in only the required fields: app name (e.g. "Mascote Assistente"), your support email, and your developer contact email at the bottom. Click "Save and continue" on the following screens (you can skip the optional fields).
4. When you reach the **"Test users"** step, click "Add users" and enter your Gmail address (and anyone else's who'll use the app). **This step matters** — until the app goes through a Google verification process (a longer process, only needed if you want to make it available to anyone), only these registered emails can sign in.

**Step 4 — Publish the app on the internet (if you haven't already)**
Google sign-in doesn't work by opening the `index.html` file directly from your computer — it needs to be on a published site with an `https://` address. If you've already pushed this repository to GitHub and enabled GitHub Pages (see the "Deploying with GitHub Pages" section above), you already have that address, something like `https://your-username.github.io/repo-name`.

**Step 5 — Create the Client ID**
1. In the left-side menu, go to **"APIs & Services" → "Credentials"**.
2. Click **"Create credentials"** (at the top) and choose **"OAuth client ID"**.
3. Under "Application type", choose **"Web application"**.
4. Under **"Authorized JavaScript origins"**, click "Add URI" and paste your app's address (e.g. `https://your-username.github.io`) — no trailing slash.
5. Click **"Create"**. A window will pop up with your **Client ID** — a long piece of text ending in `.apps.googleusercontent.com`.

**Step 6 — Paste the Client ID into the app**
1. Copy the generated Client ID.
2. Open the app, go to **Settings → Google Account**.
3. Paste it into the text field and click **"Save Client ID"**.
4. A **"Connect with Google"** button will appear — click it and sign in with the same account you registered as a "test user" in Step 3.

That's it! From there, just use the "Sync now" button or turn on automatic task syncing to Google Calendar, in the same section.

### 🤝 Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md).

### 📄 License

MIT — see [`LICENSE`](LICENSE).

---

## 🇪🇸 Español

Una app de bienestar acogedora, hecha para que todo tipo de personas organicen su semana sin
sobrecargarse — con una mascota adorable que las acompaña en el camino.

### ✨ Qué hace la app

- **Una semana sin sobrecarga** — cada día tiene un límite de tareas según tu nivel de energía
  (🦊💤 baja, 🦊🌿 media, 🦊⚡ alta), con micropasos, arrastrar y soltar entre días, y exportación
  a calendario (`.ics`).
- **Papelera y Almacén de Ideas** — un lugar para soltar pensamientos sueltos sin compromiso, y
  otro para guardar de verdad las ideas que valen la pena.
- **Hidratación y peso** — meta de agua calculada con cariño, sin juicios, con gráficos de
  evolución de los últimos meses.
- **Movimiento** — registro rápido de ejercicio con una racha semanal de huellitas.
- **Ciclo menstrual** — seguimiento de fase (menstrual, folicular, ovulatoria, lútea) que ajusta
  automáticamente las metas de tareas y agua en los días que piden más delicadeza. Se puede
  desactivar desde los ajustes de género.
- **Rincón de la Calma** — respiración guiada, sonidos ambientales y una fanfarria propia
  (composición original) al completar tareas.
- **Mascota personalizable** — 13 animales para elegir, cada uno con su propio diseño de huella
  inspirado en la anatomía real del animal, y nombre personalizable.
- **Colores y ambiente de la app** — paleta libre, además de un preset "adorable" (rosa) o
  "audaz" (azul) según la preferencia de género, siempre en tonos claros y accesibles.
- **4 idiomas** — Portugués (Brasil y Portugal), English (US) y Español, con cambio en tiempo
  real.
- **Notificaciones locales** — recordatorios de agua y tareas pendientes mientras la pestaña esté
  abierta.
- **Copia de seguridad** — exporta e importa tus datos en `.json` cuando quieras.
- **Cuenta de Google (opcional)** — conecta tu cuenta para guardar una copia de tus datos en la nube y enviar tus tareas a Google Calendar automáticamente. Requiere que crees tu propio "Client ID" gratuito (consulta la sección de configuración abajo).

### 🧸 Filosofía

Nada aquí empuja la productividad a cualquier costo. Los límites de tareas por energía, los avisos
amables y los mensajes de la mascota existen para recordar que ir despacio también es ir.

El seguimiento del ciclo es una herramienta de bienestar y autoconocimiento — **no es un método
anticonceptivo ni un recurso de diagnóstico clínico.**

### 🛠️ Tecnología

Un único archivo HTML, sin dependencias, sin compilación, sin servidor. HTML + CSS + JavaScript
puro, con datos guardados localmente en tu navegador (`localStorage`) — nada sale de tu
dispositivo.

### 🚀 Cómo usarlo

Descarga el [`index.html`](index.html) (y la carpeta [`assets/`](assets)) y ábrelo en tu
navegador. Si los datos no se guardan entre sesiones, sirve la carpeta con un servidor local
simple:

```bash
python3 -m http.server 8000
```

**GitHub Pages:** sube el repositorio, actívalo en *Settings → Pages* (rama principal, carpeta
raíz) y el `index.html` se convierte automáticamente en la página de inicio.

### ⚠️ Limitaciones conocidas

- Las notificaciones solo funcionan con la pestaña abierta (app sin servidor, sin push real).
- Los días de la semana, etiquetas de tareas y tipos de ejercicio aún no están traducidos.

### 🔐 Configurando la integración con Google (opcional) — paso a paso para principiantes

Esta función es opcional y requiere que **tú mismo** crees una credencial gratuita llamada "Client ID" — es como una identificación de tu app, para que Google sepa quién está pidiendo acceso. Nadie más puede crear esto por ti, pero los pasos de abajo no requieren ningún conocimiento técnico, solo ir haciendo clic con calma.

**Qué vas a necesitar:** una cuenta de Google (la misma de tu Gmail) y unos 10-15 minutos.

**Paso 1 — Crea un proyecto en Google Cloud**
1. Entra en [console.cloud.google.com](https://console.cloud.google.com/) e inicia sesión con tu cuenta de Google.
2. En la parte superior de la página, haz clic en el menú de proyectos (junto al texto "Google Cloud") y luego en **"Proyecto nuevo"**.
3. Ponle cualquier nombre, como "Mi Mascote Assistente", y haz clic en **"Crear"**. Es gratis y no pide tarjeta de crédito.
4. Espera unos segundos hasta que Google confirme que el proyecto fue creado, y verifica que esté seleccionado en el menú superior.

**Paso 2 — Activa las dos APIs que usa la app**
1. En la barra de búsqueda de arriba, escribe **"Google Calendar API"** y haz clic en el resultado.
2. Haz clic en el botón azul **"Habilitar"**.
3. Vuelve a la búsqueda de arriba, escribe **"Google Drive API"** y haz clic en el resultado.
4. Haz clic en **"Habilitar"** de nuevo.

**Paso 3 — Configura la "Pantalla de consentimiento" (la pantalla que aparece al iniciar sesión)**
1. En el menú de la izquierda, busca **"APIs y servicios" → "Pantalla de consentimiento de OAuth"**.
2. Elige **"Externo"** y haz clic en "Crear".
3. Completa solo los campos obligatorios: nombre de la app (ej: "Mascote Assistente"), tu correo de soporte, y tu correo de contacto de desarrollador más abajo. Haz clic en "Guardar y continuar" en las siguientes pantallas (puedes saltar los campos opcionales).
4. Cuando llegues al paso **"Usuarios de prueba"**, haz clic en "Añadir usuarios" y coloca tu correo de Gmail (y el de cualquier otra persona que vaya a usar la app). **Este paso es importante** — mientras la app no pase por un proceso de verificación de Google (más largo, solo necesario si quieres que esté disponible para cualquier persona), solo estos correos registrados aquí podrán iniciar sesión.

**Paso 4 — Publica la app en internet (si todavía no lo has hecho)**
El inicio de sesión de Google no funciona abriendo el archivo `index.html` directamente desde tu ordenador — necesita estar en un sitio publicado con dirección `https://`. Si ya subiste este repositorio a GitHub y activaste GitHub Pages (consulta la sección "Publicando con GitHub Pages" más arriba), ya tienes esa dirección, algo como `https://tu-usuario.github.io/nombre-del-repositorio`.

**Paso 5 — Crea el Client ID**
1. En el menú de la izquierda, ve a **"APIs y servicios" → "Credenciales"**.
2. Haz clic en **"Crear credenciales"** (arriba) y elige **"ID de cliente de OAuth"**.
3. En "Tipo de aplicación", elige **"Aplicación web"**.
4. En **"Orígenes de JavaScript autorizados"**, haz clic en "Añadir URI" y pega la dirección de tu app (ej: `https://tu-usuario.github.io`) — sin barra al final.
5. Haz clic en **"Crear"**. Aparecerá una ventana con tu **Client ID** — un texto largo que termina en `.apps.googleusercontent.com`.

**Paso 6 — Pega el Client ID en la app**
1. Copia el Client ID generado.
2. Abre la app, ve a **Ajustes → Cuenta de Google**.
3. Pégalo en el campo de texto y haz clic en **"Guardar Client ID"**.
4. Aparecerá un botón **"Conectar con Google"** — haz clic y inicia sesión con la misma cuenta que registraste como "usuario de prueba" en el Paso 3.

¡Listo! A partir de ahí, solo usa el botón "Sincronizar ahora" o activa el envío automático de tareas a Google Calendar, en la misma sección.

### 🤝 Contribuir

Consulta [`CONTRIBUTING.md`](CONTRIBUTING.md).

### 📄 Licencia

MIT — consulta [`LICENSE`](LICENSE).
