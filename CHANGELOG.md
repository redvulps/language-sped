# Change Log

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

## [0.3.0] - 2026-02-04

### Added

- Reconhecimento de CNPJ (14 dígitos) com highlighting específico
- Reconhecimento de CPF (11 dígitos) com highlighting específico
- Reconhecimento de datas no formato DDMMAAAA
- **Reconhecimento de Unidades de Medida Fiscais** (UNID, PC, CX, KG, TON, M, M2, M3, LITRO, e mais de 40 outras unidades)
- Reconhecimento de CST (Código de Situação Tributária) para ICMS, IPI, PIS/COFINS
- **Suporte aos novos impostos da Reforma Tributária (obrigatórios a partir de janeiro/2026):**
  - Reconhecimento de códigos IBS (Imposto sobre Bens e Serviços)
  - Reconhecimento de códigos CBS (Contribuição sobre Bens e Serviços)
  - Reconhecimento de códigos do Imposto Seletivo (IS)
- Scopes diferenciados para registros de abertura (|0000|) e encerramento (|9900|, |9990|, |9999|)
- Reconhecimento separado de números decimais (com vírgula) e inteiros
- Documentação expandida no README com descrição completa do projeto
- Arquivos de exemplo SPED para testes manuais:
  - `example-basic.txt` - Exemplo básico
  - `example-complete.txt` - Exemplo completo com todos os recursos
  - `example-efd-icms-ipi.txt` - Exemplo EFD ICMS/IPI Layout 019 (2025)
  - `example-tax-reform.txt` - Exemplo com IBS, CBS e IS (Reforma Tributária)

### Changed

- Lista de CFOPs atualizada e validada com especificações recentes
- Melhorado pattern de reconhecimento de registros para maior precisão
- Patterns regex reescritos usando lookahead/lookbehind para melhor precisão
- ScopeName alterado de `source.txt` para `source.sped` para melhor identificação
- Comentários agora reconhecem apenas linhas iniciadas com `*`
- **Scopes otimizados para melhor diferenciação visual:**
  - CNPJ usa `entity.name.type` (normalmente em cor de destaque)
  - CPF usa `variable.parameter` (cor diferenciada)
  - Datas usam `constant.language` (cor especial)
  - Unidades de medida usam `support.type` (cor distinta)

### Fixed

- Correções em patterns regex para melhor precisão no matching
- Ordem de precedência dos patterns ajustada para evitar conflitos
- Melhorada detecção de números para evitar falsos positivos

## [0.2.1]

- Melhorado início e fim dos matches

## [0.2.0]

- Corrigido RegEx dos números
- Adicionado highlight de chave de nota fiscal
- Adicionado highlight de CFOP
- Atualizada lista de CFOPs

## [0.1.0]

- Initial release
