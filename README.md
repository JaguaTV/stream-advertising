# Slideshow de Patrocinadores (Browser Source)

Site estático com duas páginas:

- **index.html** — o slideshow em si. É essa URL que você coloca como Browser Source no LiveNow (ou OBS).
- **admin.html** — o painel que você abre no celular para adicionar/remover patrocinadores. Edita o arquivo `sponsors.json` direto no seu repositório do GitHub, sem precisar mexer em código.

Tudo é gratuito, hospedado no GitHub Pages.

---

## 1. Criar o repositório

1. Crie uma conta no [github.com](https://github.com) se ainda não tiver.
2. Clique em **New repository**.
3. Dê um nome, ex: `patrocinadores-live`. Deixe **Public** (o GitHub Pages grátis exige repositório público, a menos que você tenha GitHub Pro).
4. Crie o repositório vazio (sem README).

## 2. Subir os arquivos

Envie estes arquivos para a raiz do repositório (você pode arrastar e soltar direto na interface do GitHub, em **Add file → Upload files**):

```
index.html
admin.html
sponsors.json
.nojekyll
sponsors/.gitkeep
```

Confirme o commit direto na branch `main`.

## 3. Ativar o GitHub Pages

1. No repositório, vá em **Settings → Pages**.
2. Em **Build and deployment → Source**, escolha **Deploy from a branch**.
3. Branch: **main**, pasta: **/(root)**. Salve.
4. Espere ~1 minuto. Sua URL vai ser algo como:
   `https://SEU-USUARIO.github.io/patrocinadores-live/`

## 4. Criar o token de acesso (pra editar pelo celular)

1. No GitHub, vá no seu avatar → **Settings → Developer settings → Personal access tokens → Fine-grained tokens**.
2. **Generate new token**.
3. Em **Repository access**, escolha **Only select repositories** e selecione o seu repositório.
4. Em **Permissions → Repository permissions**, defina **Contents: Read and write**.
5. Gere o token e **copie agora** — ele só aparece uma vez.

> Esse token dá acesso só a esse repositório, então mesmo que ele vaze, o risco é limitado. Ainda assim, não compartilhe ele com ninguém.

## 5. Configurar o painel no celular

1. No celular, abra: `https://SEU-USUARIO.github.io/patrocinadores-live/admin.html`
2. Preencha usuário, nome do repositório, branch (`main`) e cole o token.
3. Toque em **Salvar conexão**.
4. Pronto — dá pra adicionar/ativar/desativar/reordenar/excluir patrocinadores por ali. Cada ação já salva direto no repositório.

Dica: adicione essa página à tela inicial do celular (menu do navegador → "Adicionar à tela de início") pra abrir como um app.

## 6. Usar no LiveNow

1. No LiveNow, adicione uma fonte do tipo **Browser Source** (ou "Navegador").
2. Cole a URL: `https://SEU-USUARIO.github.io/patrocinadores-live/index.html`
3. Ajuste a largura/altura da fonte conforme o espaço no seu layout.

O slideshow já busca sozinho o `sponsors.json` a cada ~20 segundos, então qualquer alteração feita no celular aparece na live automaticamente — **não precisa remover e recolocar a fonte**.

### Parâmetros opcionais na URL do index.html

- `?bg=transparent` — fundo transparente (funciona se o LiveNow suportar alpha na fonte de navegador).
- `?bg=green` — fundo verde para chroma key.
- `?bg=1a1a2e` — qualquer cor hexadecimal como fundo.
- `?interval=8` — força 8 segundos por slide, ignorando o valor salvo no painel.
- `?labels=1` — mostra o nome do patrocinador embaixo da logo.

Exemplo combinando tudo:
`https://SEU-USUARIO.github.io/patrocinadores-live/index.html?bg=green&interval=6&labels=1`

---

## Estrutura dos arquivos

```
/index.html       → tela do slideshow (Browser Source)
/admin.html        → painel de controle (celular)
/sponsors.json      → dados: lista de patrocinadores e tempo de exibição
/sponsors/          → logos enviadas pelo painel
```

## Observações

- Ao excluir um patrocinador, a imagem correspondente continua no repositório (dentro de `/sponsors/`), só é removida a referência no `sponsors.json`. Isso é intencional, pra manter o painel simples — se quiser, pode apagar imagens não usadas manualmente pelo GitHub de vez em quando.
- Como o repositório é público, qualquer pessoa pode ver as imagens e o `sponsors.json`, mas só quem tiver o token consegue editar.
- Se quiser trocar o nome do repositório depois, lembre de atualizar a URL usada no LiveNow e reconfigurar o `admin.html`.
