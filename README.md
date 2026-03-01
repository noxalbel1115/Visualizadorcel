# Autos eproc — Visualizador Mobile

Visualizador de autos processuais do sistema eproc (TJ/SC) otimizado para dispositivos móveis. Permite navegar PDFs de processos judiciais com árvore de eventos, classificação automática por polo, anotações com screenshot, exportação seletiva de páginas e muito mais.

## Funcionalidades

### Navegação
- Swipe vertical para trocar páginas (estilo reels)
- Pinch-to-zoom com pan
- Double-tap para zoom in/out
- Rail lateral com preview de páginas
- Shake para voltar à página anterior

### Árvore Processual
- Extração automática de eventos a partir do outline ou separadores do eproc
- Badges coloridos por tipo de evento (estilo eproc)
- Classificação automática por polo (autor/réu) via cruzamento com dados da capa
- Filtros por tipo de evento
- Quick jump para eventos específicos
- Busca textual

### Análise Inteligente
- Detector de prazos com contagem de dias
- Mapa de citações legais (artigos, súmulas, leis)
- Alerta de peça processual faltante
- Contador de laudas por polo

### Anotações
- Modo anotação com seleção retangular (screenshot parcial da página)
- Comentários vinculados a evento/documento/página do eproc
- Exportação em DOCX com imagens inline

### Exportação Seletiva
- Checkboxes na árvore para selecionar eventos/documentos
- Exportação de PDF apenas com páginas selecionadas
- Capa automática com índice do conteúdo exportado
- Ideal para preparar arquivos menores para análise com IA

### Outras
- Tema claro/escuro
- Abas para múltiplos processos simultâneos
- Notas de voz vinculadas a páginas
- Compartilhamento de posição via código
- Modo comparação lado-a-lado
- Citação formatada (p. X dos autos do processo Y, Evento Z)
- Modo apresentação (fullscreen)
- PWA instalável (funciona offline após primeira carga)

## Cores dos Eventos

| Tipo | Cor | Exemplos |
|------|-----|----------|
| Sentença | 🟢 Verde escuro | Sentença, Julgado procedente/improcedente |
| Decisão | 🟢 Teal | Decisão interlocutória, Tutela |
| Petição (autor) | 🔵 Azul | Petição inicial, Réplica, Emenda |
| Petição (réu) | 🔴 Vermelho | Contestação, Impugnação, Embargos |
| Ato judicial | 🟢 Verde | Despacho, Certidão, Mandado, Audiência |
| Intimação | 🔵 Azul | Intimação, Ciência |
| Publicação | 🟡 Amarelo | Publicado/Disponibilizado no DJEN |
| Sistema | ⚪ Cinza | Conclusos, Decorrido prazo, Distribuído |

A classificação autor/réu é feita automaticamente cruzando o nome da parte no separador com os dados da capa do processo.

## Instalação

### GitHub Pages (recomendado)

1. Fork este repositório
2. Vá em Settings → Pages → Source: main → Save
3. Acesse `https://seu-usuario.github.io/autos-eproc/`
4. No celular, toque "Adicionar à tela inicial" para instalar como app

### Local (servidor HTTP)

```bash
# Opção 1: Python
python3 -m http.server 8080

# Opção 2: Node
npx serve .
```

Acesse `http://localhost:8080` no navegador do celular (mesma rede Wi-Fi).

### Direto no celular (Simple HTTP Server)

1. Copie os arquivos para o celular
2. Instale o app "Simple HTTP Server" da Play Store
3. Aponte para a pasta dos arquivos
4. Acesse o endereço mostrado no app

## Uso

1. Abra o app e toque no botão **+** ou **Abrir PDF**
2. Selecione o PDF dos autos baixado do eproc
3. Aguarde o carregamento (extração de texto e metadados)
4. Navegue por swipe ou pela árvore lateral (☰)

### Exportação seletiva para IA

1. Abra o drawer (☰) → aba Árvore
2. Marque os checkboxes dos eventos/documentos desejados
3. Toque "Exportar PDF" na barra inferior
4. O PDF gerado contém apenas as páginas selecionadas com capa indexada

## Requisitos

- Navegador moderno (Chrome 90+, Safari 14.3+, Edge 90+)
- Conexão internet na primeira carga (para CDNs)
- Funciona offline após instalação via PWA

## Dependências (CDN)

- [PDF.js 4.9.155](https://mozilla.github.io/pdf.js/) — renderização de PDF
- [JSZip 3.10.1](https://stuk.github.io/jszip/) — exportação DOCX
- [pdf-lib 1.17.1](https://pdf-lib.js.org/) — exportação PDF seletiva
- [Outfit](https://fonts.google.com/specimen/Outfit) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) — tipografia

## Estrutura

```
autos-eproc/
├── index.html      # Aplicação completa (single-file)
├── manifest.json   # PWA manifest
├── sw.js           # Service worker (cache offline)
├── icon-192.png    # Ícone PWA
├── icon-512.png    # Ícone PWA
└── README.md
```

## Licença

Uso pessoal e institucional. Desenvolvido para auxiliar magistrados e servidores na análise de processos judiciais eletrônicos.
