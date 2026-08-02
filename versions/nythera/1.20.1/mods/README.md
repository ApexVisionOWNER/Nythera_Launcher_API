# Pasta mods/ — Nythera 1.20.1

Coloque aqui os `.jar` dos mods deste modpack.

Depois de copiar todos os `.jar`, **zipe o CONTEÚDO desta pasta** (não a pasta em si) como `mods.zip` no diretório pai:

```
versions/nythera/1.20.1/
├── manifest.json
├── mods.zip        ← este arquivo (você gera)
├── config.zip
└── background.png
```

Exemplo (Linux/Mac):
```
cd versions/nythera/1.20.1/mods
zip -r ../mods.zip .
```

Exemplo (Windows PowerShell):
```
Compress-Archive -Path .\mods\* -DestinationPath .\mods.zip
```
