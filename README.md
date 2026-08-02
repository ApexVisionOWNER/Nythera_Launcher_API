# Nythera_Launcher_API

Repositório estático que serve como "API" (somente leitura) para o Nythera Launcher.
O launcher lê os JSONs deste repo via `raw.githubusercontent.com` para descobrir
quais versões (Vanilla, Nythera modpacks) e imagens de fundo mostrar.

> ⚠️ **Este repo deve ser PÚBLICO e conter apenas dados públicos.**
> NÃO coloque aqui contas de usuário, tokens, e-mails, IDs de Discord ou
> Twitch de usuários finais. Esses dados devem ficar em um banco de dados
> privado com autenticação.

## Estrutura

```
Nythera_Launcher_API/
├── README.md
├── versions/
│   ├── index.json              # catálogo raiz — quais categorias existem
│   ├── vanilla.json            # lista de versões vanilla exibidas em destaque
│   ├── nythera.json             # lista de modpacks Nythera
│   └── nythera/
│       ├── 1.20.1/
│       │   ├── manifest.json   # info do modpack (loader, versão MC, mods URL)
│       │   ├── mods.zip        # zip com todos os .jar de mods (você faz upload)
│       │   ├── config.zip      # zip com a pasta config/ do modpack
│       │   └── background.png  # imagem de fundo desta versão (opcional)
│       └── 1.21.1/
│           ├── manifest.json
│           ├── mods.zip
│           ├── config.zip
│           └── background.png
└── backgrounds/
    ├── default.png             # fundo padrão da tela de versões
    ├── vanilla.png             # fundo da aba Vanilla
    └── nythera.png              # fundo da aba Nythera
```

## URLs base

Depois de subir para o GitHub (`https://github.com/SEU_USUARIO/Nythera_Launcher_API`),
os arquivos ficam disponíveis em:

```
https://raw.githubusercontent.com/SEU_USUARIO/Nythera_Launcher_API/main/versions/index.json
https://raw.githubusercontent.com/SEU_USUARIO/Nythera_Launcher_API/main/versions/nythera/1.20.1/mods.zip
```

Edite o arquivo `nythera_launcher/config.py` do launcher e defina:

```python
API_BASE_URL = "https://raw.githubusercontent.com/SEU_USUARIO/Nythera_Launcher_API/main"
```

## Como adicionar uma nova versão Nythera

1. Crie a pasta `versions/nythera/<mc_version>/` (ex: `versions/nythera/1.20.1/`).
2. Coloque um `manifest.json` (veja exemplo em `versions/nythera/1.20.1/manifest.json`).
3. Zipe a pasta `mods/` do modpack como `mods.zip` (contém os `.jar`).
4. Zipe a pasta `config/` como `config.zip`.
5. (Opcional) Coloque `background.png` (recomendado 1920x1080).
6. Adicione uma entrada no array `versions` de `versions/nythera.json`.
7. Commit + push. O launcher busca do repo automaticamente.

## Como adicionar uma imagem de fundo

Só jogar em `backgrounds/` como `.png` ou `.jpg`. O launcher deixa o usuário
escolher via `background_key` no manifest ou usa `default.png`.

## O que NÃO fazer

- ❌ NÃO commitar contas de usuários (nome, e-mail, Discord ID, Twitch nick).
- ❌ NÃO commitar tokens (bot token, client secret, API keys).
- ❌ NÃO deixar o launcher gravar aqui — não há autenticação num repo público.

Para persistir dados de usuários (login, vínculo com Twitch, estatísticas),
suba um backend privado com autenticação (Lovable Cloud, Supabase, etc.).
