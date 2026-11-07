# Plano de evolução do fork Traccar — WMK

**Responsável:** Walney Moreira Klein — walneyk@hotmail.com

## Prioridade 1: Traccar

Este fork é um servidor Java/Gradle e inclui a interface React como **submódulo Git** `traccar-web`. A interface simples personalizada do laboratório está modificada localmente em `traccar-web/simple/index.html`, mas ainda não foi publicada em um fork próprio do frontend.

### Regra de segurança para publicação

Não publicar automaticamente `posicoes-simuladas.jsonl`, backups locais, credenciais, tokens ou arquivos temporários. O histórico de posições pode revelar trajetos. Não atualizar o ponteiro do submódulo sem garantir que o commit do frontend esteja disponível em repositório público apropriado.

### Fases

1. **Inventário e testes de regressão:** verificar Java, endpoints, protocolos, interface, quatro dispositivos de laboratório, autenticação, manuais e testes.
2. **Português brasileiro:** revisar textos de frontend, telas, mensagens, menus e ajuda, preservando as chaves de internacionalização e suporte multilíngue.
3. **Identidade visual:** personalização do fork sem remover licenças e créditos originais.
4. **Frontend versionado:** preparar fork separado de `traccar-web`, publicar suas alterações e atualizar o submódulo no fork Traccar.
5. **API e integração:** testar `/api/devices`, `/api/positions`, `/api/socket` e contrato com WMK Geo Bridge; adicionar documentação OpenAPI e exemplos.
6. **Testes e publicação:** testes automatizados e manuais; commits separados para backend, frontend e documentação; tag de versão somente após validação.

### Testes mínimos antes de publicar mudanças funcionais

| ID | Teste | Aprovação |
| --- | --- | --- |
| TR-001 | `GET /api/server` | HTTP 200 |
| TR-002 | Login com usuário de laboratório | Sessão autorizada |
| TR-003 | Listagem de dispositivos | Quatro dispositivos de teste, se cadastrados |
| TR-004 | Ingestão OsmAnd porta 5055 | Posições recebidas |
| TR-005 | Mapa, seleção e telemetria | Sem erros de execução |
| TR-006 | Interface pt-BR | Textos e acentos corretos |
| TR-007 | Conector Bridge autenticado | HTTP 200 e dados normalizados |
| TR-008 | Testes de build Java e frontend | Compilação sem falhas |

**Situação:** TR-001 confirmado nesta sessão; demais itens aguardam execução sistemática. Nenhum teste deve ser considerado aprovado por inferência.

## Prioridade 2: WMK Geo Bridge

Concluir autenticação real com Traccar, testes HTTP, documentação Swagger e contrato estável. Manter serviço independente e seguro.

## Prioridade 3: WMK Geo Intelligence

Preservar alterações locais, corrigir configuração do remoto GitHub e implementar camada GPS opcional no Cesium, sem alterar o trânsito existente.

## Regra de publicação

Todo commit precisa de escopo, testes e registro. A publicação do submódulo web depende de um repositório remoto apropriado, não do fork Java sozinho.
