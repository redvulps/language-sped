# Language SPED - Syntax Highlighting Extension

[![Version](https://img.shields.io/badge/version-0.3.0-blue.svg)](https://github.com/redvulps/language-sped)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/redvulps/language-sped/blob/master/LICENSE)

Extensão do Visual Studio Code que fornece syntax highlighting (realce de sintaxe) para arquivos SPED (Sistema Público de Escrituração Digital) da Receita Federal do Brasil.

## 📋 Sobre o SPED

O **SPED** (Sistema Público de Escrituração Digital) é um sistema da Receita Federal do Brasil que unifica e moderniza as atividades de recepção, validação, armazenamento e autenticação de livros e documentos que integram a escrituração contábil e fiscal dos empresários e das pessoas jurídicas.

Os principais módulos do SPED incluem:

- **EFD ICMS/IPI**: Escrituração Fiscal Digital do ICMS e IPI
- **EFD-Contribuições**: Escrituração Fiscal Digital das Contribuições (PIS/COFINS)
- **ECF**: Escrituração Contábil Fiscal
- **ECD**: Escrituração Contábil Digital

## ✨ Funcionalidades

Esta extensão fornece syntax highlighting para os seguintes elementos dos arquivos SPED:

### Identificadores de Registros

- **Registros de abertura** (`|0000|`) - Destacado de forma especial
- **Registros de encerramento** (`|9900|`, `|9990|`, `|9999|`) - Destacado de forma especial
- **Registros genéricos** (`|XXXX|`) - Identificador de 4 caracteres no início da linha

### Códigos Fiscais

- **CFOPs de Entrada** (séries 1000-3000) - Códigos de operações de entrada
- **CFOPs de Saída** (séries 5000-7000) - Códigos de operações de saída
- **CST** - Código de Situação Tributária (ICMS, IPI, PIS/COFINS)

### Identificadores e Documentos

- **CNPJ** - 14 dígitos (Cadastro Nacional de Pessoa Jurídica)
- **CPF** - 11 dígitos (Cadastro de Pessoa Física)
- **Chaves de Nota Fiscal** - 44 dígitos

### Dados Numéricos e Datas

- **Datas** - Formato DDMMAAAA (com destaque visual diferenciado)
- **Números decimais** - Formato brasileiro (com vírgula)
- **Números inteiros**

### Unidades de Medida Fiscais

- **Unidades padronizadas** - UNID, PC, CX, KG, TON, M, M2, M3, LITRO
- **Unidades específicas** - AMPOLA, BALDE, BANDEJ, BOBINA, CART, FARDO, FRASCO, GALAO, JOGO, KIT, LATA, PACOTE, PALETE, ROLO, SACO, e mais de 40 outras

### Estrutura e Comentários

- **Separadores de campo** (`|`) - Delimitadores de dados
- **Comentários** - Linhas iniciadas com `*`

### 🆕 Suporte à Reforma Tributária (2026)

**NOVIDADE!** A partir da versão 0.3.0, esta extensão está preparada para os novos impostos da Reforma Tributária Brasileira:

- **IBS** (Imposto sobre Bens e Serviços) - Substitui ICMS e ISS
- **CBS** (Contribuição sobre Bens e Serviços) - Substitui PIS e COFINS
- **IS** (Imposto Seletivo) - Novo tributo extrafiscal

> ⚠️ **Nota**: O destaque destes campos será obrigatório a partir de **Janeiro de 2026**, conforme Nota Técnica 2025.002

## 📦 Instalação

### Via Marketplace do VS Code

1. Abra o VS Code
2. Pressione `Ctrl+Shift+X` (ou `Cmd+Shift+X` no Mac) para abrir a aba de extensões
3. Procure por "language-sped"
4. Clique em "Install"

### Instalação Manual

1. Baixe a extensão do [repositório GitHub](https://github.com/redvulps/language-sped)
2. Copie a pasta para o diretório de extensões do VSCode:
   - **Windows**: `%USERPROFILE%\.vscode\extensions`
   - **macOS/Linux**: `~/.vscode/extensions`
3. Reinicie o VS Code

## 🚀 Uso

### Associação Automática

A extensão associa automaticamente arquivos `.txt` ao highlighting SPED. Se você precisar abrir um arquivo SPED com outra extensão:

1. Abra o arquivo no VS Code
2. Clique no indicador de linguagem no canto inferior direito (geralmente mostra "Plain Text")
3. Digite "Sped" na paleta de comandos
4. Selecione "Sped" da lista

### Exemplos

Confira os arquivos de exemplo no diretório [`examples/`](./examples/) do repositório:

- [`example-basic.txt`](./examples/example-basic.txt) - Exemplo básico com registros comuns
- [`example-complete.txt`](./examples/example-complete.txt) - Exemplo completo com todas as funcionalidades
- [`example-efd-icms-ipi.txt`](./examples/example-efd-icms-ipi.txt) - Exemplo específico do EFD ICMS/IPI Layout 019
- [`example-tax-reform.txt`](./examples/example-tax-reform.txt) - Exemplo com IBS, CBS e Imposto Seletivo (Reforma Tributária)

## 🛠️ Desenvolvimento

### Pré-requisitos

- [Node.js](https://nodejs.org/) instalado
- [Visual Studio Code](https://code.visualstudio.com/) instalado
- [vsce](https://github.com/microsoft/vscode-vsce) (Visual Studio Code Extension Manager)

### Testando Localmente

1. **Clone o repositório:**

   ```bash
   git clone https://github.com/redvulps/language-sped.git
   cd language-sped
   ```

2. **Abra o projeto no VS Code:**

   ```bash
   code .
   ```

3. **Execute a extensão em modo de desenvolvimento:**
   - Pressione `F5` ou vá em `Run > Start Debugging`
   - Isso abrirá uma nova janela do VS Code chamada **"Extension Development Host"**
   - A extensão estará carregada nesta janela

4. **Teste o syntax highlighting:**
   - Na janela Extension Development Host, abra um dos arquivos de exemplo:
     - `examples/example-basic.txt`
     - `examples/example-complete.txt`
     - `examples/example-efd-icms-ipi.txt`
     - `examples/example-tax-reform.txt`
   - Verifique se os elementos estão sendo destacados corretamente
   - Experimente diferentes temas do VS Code para ver a diferenciação de cores

5. **Fazer alterações:**
   - Edite `syntaxes/sped.tmLanguage.json` para modificar a sintaxe
   - Depois de salvar, pressione `Ctrl+R` (ou `Cmd+R` no Mac) na janela Extension Development Host para recarregar
   - As mudanças serão aplicadas imediatamente

### Buildando o VSIX

O VSIX é o formato de pacote de extensões do VS Code, usado para distribuição e instalação.

1. **Instale o vsce (se ainda não tiver):**

   ```bash
   npm install -g @vscode/vsce
   ```

2. **Build do pacote VSIX:**

   ```bash
   vsce package
   ```

   Isso criará um arquivo `language-sped-0.3.0.vsix` no diretório do projeto.

3. **Instalar o VSIX localmente:**

   **Opção 1 - Via linha de comando:**

   ```bash
   code --install-extension language-sped-0.3.0.vsix
   ```

   **Opção 2 - Via interface do VS Code:**
   - Abra o VS Code
   - Vá em Extensions (`Ctrl+Shift+X`)
   - Clique no menu `...` (três pontos) no topo
   - Selecione "Install from VSIX..."
   - Escolha o arquivo `language-sped-0.3.0.vsix`

4. **Publicar no Marketplace (apenas para mantenedores):**

   ```bash
   vsce publish
   ```

   > ⚠️ **Nota**: Você precisa de um Personal Access Token do Azure DevOps para publicar.

### Estrutura do Projeto

```
language-sped/
├── .vscode/              # Configurações do VS Code
├── examples/             # Arquivos de exemplo SPED
│   ├── example-basic.txt
│   ├── example-complete.txt
│   ├── example-efd-icms-ipi.txt
│   └── example-tax-reform.txt
├── syntaxes/             # Definições de sintaxe
│   └── sped.tmLanguage.json
├── CHANGELOG.md          # Histórico de mudanças
├── language-configuration.json  # Config de linguagem
├── package.json          # Manifesto da extensão
└── README.md            # Esta documentação
```

### Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:

1. **Reportar bugs ou sugerir melhorias:**
   - Abra uma [Issue](https://github.com/redvulps/language-sped/issues) descrevendo o problema ou sugestão
   - Inclua exemplos de arquivos SPED quando relevante

2. **Contribuir com código:**
   - Fork o repositório
   - Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
   - Faça suas mudanças e commits
   - Teste localmente (veja instruções acima)
   - Envie um Pull Request

3. **Adicionar novos CFOPs ou códigos:**
   - Verifique a documentação oficial da RFB
   - Atualize `syntaxes/sped.tmLanguage.json`
   - Adicione exemplos em `examples/`
   - Documente no CHANGELOG.md

## 📚 Referências

- [Portal SPED - Receita Federal](http://sped.rfb.gov.br/)
- [Guia Prático EFD-ICMS/IPI](http://sped.rfb.gov.br/pasta/show/1573)
- [Nota Técnica 2025.002 - NF-e/NFC-e (Reforma Tributária)](https://www.nfe.fazenda.gov.br/)
- [Lei Complementar nº 214/2025 - Reforma Tributária](http://www.planalto.gov.br/)

## 📝 Changelog

Veja o arquivo [CHANGELOG.md](./CHANGELOG.md) para detalhes sobre as mudanças em cada versão.

## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo LICENSE para mais detalhes.

## 👤 Autor

**redvulps**

- GitHub: [@redvulps](https://github.com/redvulps)

## ⭐ Apoie o Projeto

Se esta extensão foi útil para você, considere dar uma estrela ⭐ no [repositório GitHub](https://github.com/redvulps/language-sped)!
