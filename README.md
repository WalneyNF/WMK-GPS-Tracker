# WMK GPS Tracker

**Plataforma de rastreamento GPS baseada no Traccar — fork mantido por Walney Moreira Klein**

[![Documentação](https://img.shields.io/badge/documentação-pt--BR-16803c)](manuais/index.html)
[![API](https://img.shields.io/badge/API-OpenAPI-blue)](openapi.yaml)
[![Licença](https://img.shields.io/badge/licença-Apache--2.0-lightgrey)](LICENSE.txt)

> **Situação do projeto:** fork em evolução. O núcleo GPS permanece baseado no **Traccar 6.17.0** (versão identificada no servidor local em 06/11/2026). A personalização WMK ainda está em desenvolvimento. Não confunda a versão do produto original com as versões da documentação WMK.

## Para que serve?

O WMK GPS Tracker é uma plataforma de rastreamento para veículos e outros ativos. Seu núcleo Traccar recebe posições de dispositivos compatíveis, armazena dados, disponibiliza mapa, eventos e relatórios e oferece uma API para integração com outros sistemas.

É destinado a usuários individuais, administradores de frotas e desenvolvedores que desejam estudar, hospedar e ampliar uma solução de rastreamento de código aberto.

### Recursos existentes no núcleo Traccar

- Cadastro e gerenciamento de dispositivos e usuários.
- Recebimento de posições GPS por protocolos compatíveis.
- Mapas, histórico, relatórios, eventos e geocercas (dependem de configuração e permissões).
- API HTTP e comunicação em tempo real do Traccar.
- Servidor Java com banco de dados configurável.

**Não são recursos concluídos do fork WMK:** tradução integral da interface, API pública WMK independente, painel próprio definitivo e integração ponta a ponta com WMK Geo Intelligence.

## Comece aqui

**Usuários comuns:** leia [Manual do usuário](manuais/15-manual-usuario-wmk.html). Ele explica os conceitos, o primeiro acesso, como cadastrar um dispositivo, entender as posições e resolver problemas frequentes.

**Desenvolvedores:** leia [Manual do desenvolvedor](manuais/16-manual-desenvolvedor-wmk.html). Ele cobre arquitetura, submódulo frontend, API, autenticação, exemplos e testes.

**Todos os manuais:** [Central de documentação em português](manuais/index.html).

**Regra permanente:** [Padrão de documentação WMK](manuais/PADRAO-DOCUMENTACAO-WMK.md) — guias para leigos, desenvolvedores e administradores, integração móvel, testes e atribuições.

### Execução local

A instalação depende do ambiente e da configuração de banco de dados. Para o laboratório Windows já configurado, a interface é acessada em `http://127.0.0.1:8082/` **enquanto o servidor estiver ativo**.

Não assuma que esse endereço funciona fora da máquina em que o Traccar foi instalado. Não publique a porta 8082 na internet sem TLS, autenticação e configuração de segurança.

A resposta `GET /api/server` pode ser utilizada como diagnóstico básico do servidor; ela **não comprova** que um dispositivo está enviando posições ou que o usuário está autenticado.

## API e integrações

A especificação original está em [openapi.yaml](openapi.yaml). A documentação oficial do Traccar também está disponível em [traccar.org/traccar-api](https://www.traccar.org/traccar-api/).

O WMK GPS Tracker poderá trabalhar de forma independente ou ser conectado ao [WMK Geo Bridge](https://github.com/WalneyNF/WMK-Geo-Bridge) e ao [WMK Geo Intelligence](https://github.com/WalneyNF/WMK-Geo-Intelligence). Essas integrações são opcionais e estão em desenvolvimento; a existência dos repositórios não significa que o fluxo completo já tenha sido testado.

## Desenvolvendo este fork

O código do servidor está neste repositório. A interface web React está no **submódulo Git** `traccar-web`, atualmente vinculado ao projeto upstream. Modificações locais nesse submódulo **não são publicadas automaticamente** quando se faz push do servidor.

Para estudar a estrutura e a compilação, consulte o manual de desenvolvedor e a [documentação de build do Traccar](https://www.traccar.org/build/). Não faça `git submodule update --force` em uma cópia com modificações locais sem backup e revisão.

## Versões e testes

- **Núcleo identificado:** Traccar 6.17.0, pela resposta do servidor local.
- **Documentação WMK:** revisão 0.2.0 — guias iniciais de usuário e desenvolvedor.
- **Teste local confirmado nesta revisão:** `GET http://127.0.0.1:8082/api/server` → HTTP 200.
- **Pendente:** validação integral do frontend React, autenticação, ingestão de posições, integração com Bridge e build completo nesta revisão. Consulte [relatório de testes](manuais/TESTES-WMK.md).

As versões do núcleo, da documentação e das integrações são registradas separadamente para evitar anúncios de funcionalidades ainda não validadas.

## Créditos e licença

**Personalização, documentação e integração WMK:** Walney Moreira Klein — walneyk@hotmail.com.

**Projeto original:** [Traccar](https://github.com/traccar/traccar), seus autores e colaboradores. O código original permanece sujeito à **Apache License 2.0**, conforme [LICENSE.txt](LICENSE.txt). O fork preserva os créditos e avisos de licença do projeto de origem.

**Uso responsável:** dados de localização podem ser sensíveis. Rastreie somente dispositivos e pessoas com autorização adequada, respeitando a legislação aplicável e as políticas de privacidade.

**Aplicativos moveis:** [Guia de envio de GPS do celular sem Bridge ou Geo Intelligence](manuais/17-integracao-celular-gps.md).


## Funcionamento independente e integrado — suíte WMK

**Este projeto funciona de maneira independente:** não é obrigatório instalar os outros dois projetos WMK para usar suas funções principais.

**Modo independente — WMK GPS Tracker:** Recebe e armazena posições GPS e oferece API e interface sem precisar dos outros dois produtos.

**Modo integrado (opcional):** Pode fornecer dispositivos e posições ao Bridge e, futuramente, ao mapa 3D. A integração ponta a ponta ainda precisa ser validada.

**Projetos relacionados:** [WMK GPS Tracker](https://github.com/WalneyNF/WMK-GPS-Tracker) · [WMK Geo Bridge](https://github.com/WalneyNF/WMK-Geo-Bridge) · [WMK Geo Intelligence](https://github.com/WalneyNF/WMK-Geo-Intelligence).

**Situação dos testes:** os serviços responderam individualmente no laboratório, mas a integração ponta a ponta ainda não está aprovada. Consulte os manuais e os testes antes de disponibilizar dados privados.

**Documentação:** [padrão WMK](manuais/PADRAO-DOCUMENTACAO-WMK.md). Créditos das contribuições WMK: **Walney Moreira Klein — walneyk@hotmail.com**. Preserve também as licenças e os avisos dos autores originais.
