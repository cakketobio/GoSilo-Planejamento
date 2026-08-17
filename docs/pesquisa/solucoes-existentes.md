# Análise de Concorrentes e Soluções Existentes (Visão do Usuário)

A tabela a seguir apresenta o mapeamento das soluções atuais utilizadas por produtores rurais para tentar resolver a falta ou sobra de espaço de armazenamento.

| Nome da Solução | Tipo (app/site/planilha/manual) | Pontos Fortes (como usuária) | Pontos Fracos (o que irrita) | Link (se houver) |
| :--- | :--- | :--- | :--- | :--- |
| **Grupos de WhatsApp e Telegram Regionais** | Manual / App | • Resposta rápida de contatos conhecidos.<br>• Uso muito fácil e popular no campo.<br>• Sem custo adicional. | • Mensagens se perdem no fluxo da conversa.<br>• Alcança poucas pessoas fora do círculo de amizades.<br>• Não mostra localização no mapa nem preço claro.<br>• Falta padronização de tamanho e condições do silo. |  |
| **Silo Bolsa / Embutidoras (Aluguel ou Compra)** | Manual | • Permite guardar a silagem na própria fazenda.<br>• Dá independência de outros produtores. | • Custo alto para comprar a máquina ou contratar o serviço na urgência.<br>• Lonas podem rasgar ou ser furadas por animais.<br>• Exige mão de obra rápida e qualificada. | https://pacifil.com.br/produtos/silo-bolsa-pacifil-para-armazenamento-de-graos-e-silagem/ |
| **Classificados Agrícolas (ex: MF Rural / OLX)** | Site / App | • Alcança produtores de várias regiões.<br>• Permite colocar fotos e descrições detalhadas. | • Focado em venda de fazendas e máquinas, não em aluguel temporário de espaço.<br>• Não tem mapa interativo para ver a distância exata.<br>• Não aceita lances ou negociação rápida em tempo real.<br>• Respostas demoradas. | https://www.mfrural.com.br

---

## Critério de Aceite / Análise Crítica
- **Status:** Aceito pelo time.
- **Análise Crítica:** Nenhuma das alternativas atuais resolve o problema do produtor de forma completa. Nenhuma oferece **geolocalização em mapa** para encontrar silos próximos rapidamente (economizando no frete e evitando que os grãos estraguem) associada a um **sistema de leilão/lances** para negociação ágil e justa.

# Análise Técnica de Soluções Existentes e Concorrentes

## Visão Geral da Análise

Esta análise avalia sob a ótica de Engenharia de Software as alternativas e concorrentes mapeados no mercado de armazenagem agrícola e logística (Grupos de WhatsApp/Telegram, Silo Bolsa, Classificados como MF Rural/OLX, Siloz e SpaceFill). A avaliação abrange aspectos de plataforma, conectividade, stack tecnológica provável, arquitetura de armazenamento, parâmetros técnicos críticos e conclusões para a arquitetura do sistema **GoSilo**.

---

## Tabela Comparativa Técnica de Soluções e Concorrentes

| Solução / Concorrente | Plataforma | Conectividade | Stack Tecnológica Provável | Tipo de Armazenamento | Parâmetros Técnicos Notáveis |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Grupos de WhatsApp / Telegram** | Multiplataforma (Android, iOS, Web, Desktop) | Online (dependente de conexão ativa) | Erlang/Elixir, C++, MTProto / Signal Protocol, RocksDB | Híbrido (Nuvem centralizada + Cache local) | Dados totalmente não estruturados (mensagens de texto/mídia); ausência de consultas por raio geográfico, mapas interativos ou transações ACID. |
| **Silo Bolsa / Embutidoras** | N/A (Solução Física / Maquinário) | Offline (Sem conectividade) | N/A (Equipamentos mecânicos e polímeros industriais) | Armazenamento Físico no Solo | Ausência total de dados digitais, métricas automatizadas ou integração com APIs de gestão/leilão. |
| **Classificados (MF Rural, OLX, etc.)** | Web Responsivo + Aplicativo Mobile | Online (requisita conexão contínua) | PHP/Node.js, MySQL/PostgreSQL, CDN (AWS S3) | Nuvem (Relacional + Armazenamento de Objetos) | Anúncios estáticos com requisições HTTP tradicionais; busca básica por texto/estado sem geofencing, raio exato em $km$ ou WebSockets. |
| **Siloz** | Web App (SaaS) + App Companion Mobile | Híbrida (Arquitetura *Offline-first*) | React / React Native, Node.js / Python, SQLite local | Nuvem + Sincronização Local (*Local Sync*) | Foco em ERP e gestão de estoque interno de armazéns; integração com telemetria de sensores de silos e balanças agrícolas. |
| **SpaceFill** | Web App (SaaS B2B) | Online (SaaS em nuvem) | React / Vue.js, Python (Django) / Node.js, PostgreSQL + ElasticSearch | Nuvem (*Multi-tenant Cloud*) | Matching logístico B2B de galpões e armazéns; cálculo de volume ($m^3$) e contratos complexos; sem leilão dinâmico em tempo real. |

---

## Análise Aprofundada dos Parâmetros Técnicos Críticos

### Geolocalização, Mapeamento e Spatial Indexing
* **Cenário Atual:** Soluções tradicionais (como MF Rural e OLX) filtram anúncios apenas por municípios ou estados através de consultas `WHERE estado = 'GO'`.
* **Exigência GoSilo:** O GoSilo requer geofencing e consultas por raio de distância em quilômetros (ex: `distancia <= 50km`) combinadas com agrupamento visual de marcadores (*clusters*).
* **Solução Técnica:** Uso do **PostgreSQL com a extensão PostGIS** e indexação espacial GiST/SP-GiST para cálculos eficientes de distância Geodésica (`ST_DWithin`).

### Gestão de Estado e Conectividade no Meio Rural
* **Cenário Atual:** O Siloz utiliza abordagem *offline-first* para permitir que operadores registrem entradas de grãos mesmo sem sinal 4G/Wi-Fi na fazenda.
* **Exigência GoSilo:** O aplicativo do GoSilo será utilizado no campo, onde a conectividade é oscilante, mas a dinâmica de leilões exige sincronia rápida quando online.
* **Solução Técnica:** Adoção de armazenamento temporário local no app (via SQLite ou AsyncStorage no React Native) para cache de navegação e formulários offline, com sincronização em background ao restabelecer a conexão.

### Estruturação de Dados e Lances em Tempo Real
* **Cenário Atual:** Negociações em grupos de WhatsApp/Telegram ocorrem em texto livre, gerando inconsistências, falta de histórico auditável e risco de duplicidade.
* **Exigência GoSilo:** Controle rigoroso de estados de leilão, prevenção de lances simultâneos conflitantes (*race conditions*) e prorrogação automática anti-sniping.
* **Solução Técnica:** Transações com propriedades ACID no banco de dados e comunicação bidirecional via **WebSockets** (FastAPI) para propagação instantânea de lances com baixa latência.

---

## Conclusão Técnica: Recomendações para a Arquitetura GoSilo

### O que Replicar / Adotar
1. **Arquitetura Nuvem Centralizada com Suporte Espacial (SpaceFill / Siloz):** Utilizar banco de dados relacional robusto (PostgreSQL + PostGIS) hospedado em nuvem para garantir a consistência transacional dos leilões e consultas espaciais eficientes.
2. **Resiliência e Cache Local (*Offline-first* Parcial - Siloz):** Implementar armazenamento local temporário no aplicativo móvel para permitir o preenchimento de cadastros de silos e consulta de informações em cache sem depender de sinal ininterrupto.
3. **Modelagem Parametrizada de Espaço e Capacidade (SpaceFill):** Estruturar os dados de capacidade ociosa em métricas padronizadas (volume em $m^3$ ou sacas), tipo de grão aceito e período de disponibilidade.

### O que Evitar / Descartar
1. **Negociação Desestruturada e Informal (WhatsApp / Telegram):** Evitar fluxos de negociação por chat sem validação de estado e regras de negócio automatizadas.
2. **Atualização de Interface por *Polling* / Requisição Convencional (Classificados):** Evitar recarregamentos de página (HTTP REST Polling) para acompanhamento de lances. O leilão do GoSilo exige arquitetura orientada a eventos via WebSockets.
3. **Dependência Exclusiva de Conexão Online Ininterrupta:** Não bloquear a navegação do aplicativo caso o produtor rural perca temporariamente a conexão com a internet.

---
