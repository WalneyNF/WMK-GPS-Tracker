# Guia de integração: aplicativo de celular enviando GPS

**Público:** desenvolvedores Android/iOS e usuários que desejam entender a integração.  
**Créditos das contribuições WMK:** Walney Moreira Klein — walneyk@hotmail.com.

## 1. Objetivo

Um aplicativo próprio poderá enviar localização a um servidor WMK GPS Tracker **sem instalar** WMK Geo Bridge ou WMK Geo Intelligence. O núcleo Traccar recebe dados usando protocolos compatíveis; o dispositivo precisa estar cadastrado e autorizado.

## 2. Antes de programar

1. Instale e inicie o servidor seguindo a documentação oficial do Traccar e o manual WMK.
2. Confirme `GET http://127.0.0.1:8082/api/server` na máquina do servidor.
3. Cadastre um dispositivo de teste com um identificador único fictício.
4. Escolha um protocolo suportado, como OsmAnd, e confirme a porta configurada no servidor. **Não confunda 8082 (web/API) com a porta de entrada do protocolo GPS.**
5. Para um celular em outra rede, configure endereço público, HTTPS/TLS onde aplicável, autenticação e firewall. `127.0.0.1` aponta para o próprio celular, não para seu computador.

## 3. Exemplo de requisição para o protocolo OsmAnd

O protocolo OsmAnd do Traccar pode aceitar uma requisição HTTP com parâmetros de posição. **Exemplo apenas para laboratório, sem dados pessoais:**

```text
GET http://127.0.0.1:5055/?id=wmk-demo-001&lat=-22.281&lon=-42.531&timestamp=1762470000
```

O dispositivo `wmk-demo-001` precisa existir no cadastro do servidor. A porta 5055 é a configuração comum do OsmAnd no Traccar, mas deve ser confirmada na instalação. O timestamp é ilustrativo; para posições reais use horário UTC correto. Não execute esse exemplo contra um serviço público sem autorização.

## 4. Android e iOS

O aplicativo deve solicitar permissão de localização de forma transparente, informar a finalidade do rastreamento e respeitar as regras de localização em segundo plano do sistema operacional. Envie dados apenas com consentimento e segurança. Use fila local, retry com backoff e controle de bateria; não assuma que a rede estará sempre disponível.

## 5. Verificação de ponta a ponta

1. Confirmar HTTP 200 em `/api/server` (somente disponibilidade do backend).
2. Confirmar cadastro do identificador de teste.
3. Enviar uma posição fictícia ao protocolo configurado.
4. Consultar a última posição do dispositivo com conta autorizada pela API do Traccar.
5. Conferir latitude, longitude e horário; documentar o resultado.
6. Repetir com o Bridge desligado: o Tracker deve continuar recebendo dados.

**Situação em 06/11/2026:** a disponibilidade do backend foi confirmada; este fluxo completo de celular ainda não foi executado nesta revisão.

## 6. Segurança e licença

Não publique identificadores reais, rotas, senhas ou tokens. A documentação e as contribuições WMK são creditadas a Walney Moreira Klein — walneyk@hotmail.com; preserve também a licença Apache 2.0 e os avisos dos autores do Traccar. Obrigações legais de redistribuição dependem dos textos de licença aplicáveis.
