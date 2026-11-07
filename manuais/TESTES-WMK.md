# Relatório de testes — WMK GPS Tracker

**Revisão da documentação:** 0.2.0  
**Núcleo observado:** Traccar 6.17.0  
**Créditos:** Walney Moreira Klein — walneyk@hotmail.com

## Metodologia

Cada teste exige comando, resultado esperado, resultado observado e decisão. A documentação WMK é versionada independentemente do software original. Não anunciar nova versão funcional sem build e testes de regressão.

| ID | Objetivo | Resultado | Situação |
| --- | --- | --- | --- |
| TR-001 | Verificar servidor HTTP em 8082 | GET /api/server respondeu HTTP 200; JSON informou version=6.17.0 | APROVADO |
| TR-002 | Verificar ambiente Java | `java -version` falhou ao procurar `C:\Program Files\Java\jre-1.8\lib\amd64\jvm.cfg` | BLOQUEADO |
| TR-003 | Testar login e permissões | Não executado nesta revisão | PENDENTE |
| TR-004 | Testar ingestão e posições | Não executado nesta revisão | PENDENTE |
| TR-005 | Testar frontend React e mapas | Não executado nesta revisão | PENDENTE |
| TR-006 | Compilar e executar testes Gradle | Não executado nesta revisão; Java do PATH precisa ser corrigido | PENDENTE |
| TR-007 | Validar integração real com Geo Bridge | Não executado nesta revisão | PENDENTE |
| TR-008 | Conferir arquivos README e manuais | Arquivos obrigatórios presentes, links do índice confirmados e acentuação UTF-8 validada | APROVADO |

## Próxima ação

Corrigir a seleção do JDK sem instalar nada no disco C: e sem modificar os projetos. Depois executar Gradle e autenticação com credenciais de laboratório armazenadas fora do Git.

## Cuidados

A pasta `laboratorio-gps/` contém dados de simulação e não deve ser publicada automaticamente. O frontend `traccar-web` é um submódulo com alterações locais ainda não versionadas em fork próprio.
