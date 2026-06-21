# DevBrowser

**Navegador para desenvolvedores baseado no Kiwi Browser (Chromium)**

## 🎯 O que é?

Fork do [Kiwi Browser](https://github.com/kiwibrowser/src) com foco em **ferramentas de desenvolvimento**:

- ✅ DevTools nativos do Chromium
- ✅ Suporte a extensões Chrome
- ✅ Ferramentas de debug integradas
- ✅ UI otimizada para devs

## 🚀 Começando

### 1. Fork este repositório

```bash
# Via GitHub
gh repo fork kiwibrowser/src --clone --directory devbrowser
```

### 2. Configurar GitHub Actions

O workflow já está configurado em `.github/workflows/build-devbrowser-minimal.yml`

### 3. Build automático

A cada push para `main`:
1. GitHub Actions detecta mudanças
2. Faz sync das dependências
3. Compila o APK
4. Disponibiliza para download

### 4. Download do APK

```
GitHub > Actions > DevBrowser CI > artifacts
```

## 📁 Estrutura

```
devbrowser/
├── .github/workflows/
│   └── build-devbrowser-minimal.yml   # CI/CD
├── chrome/android/                     # Android app
├── android_webview/                   # WebView
├── build/                            # Scripts
└── out/                              # Builds (gitignored)
```

## 🔧 Workflows

### `build-devbrowser-minimal.yml`

| Feature | Descrição |
|---------|-----------|
| **Incremental** | Só rebuild o que mudou |
| **Cache** | ccache + build cache |
| **Fast** | ~30-60 min por build |
| **Multi-arch** | arm, arm64, x86, x64 |

### triggering:

```bash
# Via CLI
gh workflow run build-devbrowser-minimal.yml

# Via API
curl -X POST https://api.github.com/repos/{owner}/{repo}/actions/workflows/build-devbrowser-minimal.yml/dispatches \
  -H "Authorization: token $GITHUB_TOKEN" \
  -d '{"ref":"main"}'
```

## 📱 Releases

Releases automáticos são criados quando:
- Push para branch `main`
- Build completa com sucesso

APKs ficam disponíveis em:
```
Releases > v{run_number} > Assets
```

## 🛠️ Customizações

Para adicionar features:

1. Edite código em `chrome/android/java/`
2. Commit e push
3. GitHub Actions compila automaticamente
4. Download do APK

### Customizações planejadas:

- [ ] DevTools panel sempre visível
- [ ] Botão screenshot rápido
- [ ] Console integrado
- [ ] Network inspector melhorado
- [ ] Tema dark dev-friendly

## 📄 Licença

Baseado no Chromium/Kiwi Browser.
Licença BSD - see `LICENSE`.

## 🙏 Créditos

- [Kiwi Browser](https://kiwibrowser.com/) - Base
- [Chromium](https://www.chromium.org/) - Motor
