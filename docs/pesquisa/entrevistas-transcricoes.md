# Transcrições das Entrevistas com Produtores Rurais

**Entrevistador(a):** Ana Vitória Oliveira Ribeiro  
**Objetivo:** Entender a visão de produtores rurais sobre a falta de espaço para armazenar grãos na colheita e a existência de silos com capacidade ociosa na região.

---

### Entrevista 1: Vicente Almeida
- **Idade / Perfil:** 90 anos | Proprietário Rural

**Pergunta:** O senhor já passou por situações em que a colheita de grãos foi maior que o espaço disponível para guardar?

**Resposta:** 
"Já passei por isso muitas vezes. O silo da fazenda enchia e o resto ficava pra fora ou dependia de conseguir espaço com algum vizinho. Naquela época, a gente só resolvia se conhecesse donos de outras fazendas pessoalmente. Quem não tinha esse contato passava aperto e corria o risco de perder umas partes ou perder tudo."

---

### Entrevista 2: Vilma Almeida
- **Idade / Perfil:** 62 anos | Criada na Fazenda

**Pergunta:** Na sua rotina na fazenda, você já acompanhou a dificuldade de encontrar espaço para guardar os grãos colhidos?

**Resposta:**
"Sim, acompanhar o período da colheita sempre foi estressante, principalmente para quem não tem conhecidos que também são da roça. Várias vezes vi meu pai e meu irmão ligando para vários conhecidos tentando achar algum silo ou armazenamentos com espaço. O ruim é saber que às vezes tinha um espaço livre em uma fazenda próxima, mas a gente não tinha como saber."

---

### Entrevista 3: Vicente Almeida Filho
- **Idade / Perfil:** 58 anos | Produtor Rural

**Pergunta:** Como produtor, como você lida com a capacidade dos silos quando a produção de grãos supera o esperado?

**Resposta:**
"O que a gente espera nem sempre bate com a vida real aqui na roça. Quando a colheita vem acima do esperado, o meu silo que é pequeno enche rápido e aí preciso encontrar um jeito para não deixar o grão perder. Hoje em dia o processo ainda é manual mas já ajuda bastante, dependendo de ligações e mensagens de WhatsApp."

---

### Entrevista 4: Sandra Almeida
- **Idade / Perfil:** 60 anos | Gestora da Fazenda

**Pergunta:** Do ponto de vista de gestão, ter um silo ocioso ou não ter onde armazenar os grãos afeta o lado financeiro?

**Resposta:**
"Muito, por que construir e manter um silo custa caro, então deixar o silo vazio ou só com metade é um custo que não tem retorno. E por outro lado, quem precisa armazenar os grãos rápido acaba pagando fretes mais longos ou aceitando condições ruins, o que já aconteceu comigo."

---

### Entrevista 5: Rodolfo Oliveira
- **Idade / Perfil:** 61 anos | Produtor Rural

**Pergunta:** Você percebe se existe muita capacidade ociosa em silos na sua região durante a safra?

**Resposta:**
"Sim, já vi bastante e é muito comum ver um produtor sem saber onde descarregar  ou guardar os grãos enquanto outros, a poucos quilômetros de distância, estão com armazenamentos sobrando e nem avisam ou as vezes nem ficam sabendo que tem gente precisando."

---

## Critério de Aceite
- **Status:** Concluído.
- **Validação:** As 5 transcrições confirmam que a falta de visibilidade sobre a capacidade ociosa de silos de grãos gera gargalos logísticos e financeiros para produtores da região.

# Análise de Viabilidade Técnica dos Desejos do Usuário

**Responsável:** Breno Daniel Santos Silva <br>
**Objetivo:** Avaliar de forma realista cada desejo extraído das entrevistas, com foco na viabilidade técnica e nível de dificuldade para cada implementação.

| Desejo Extraído das Entrevistas | Viabilidade | Notas Técnicas e Abordagem Arquitetural |
| :--- | :--- | :--- |
| **1. Descoberta Geográfica de Espaços Ociosos**<br>*(Evitar a dor de não saber que há espaço sobrando a poucos quilômetros - citado por Vilma e Rodolfo)* | **Média** | Requer a implementação de buscas espaciais. O uso do **PostGIS** com queries de geofencing (raio em $km$) resolve o problema do back-end. No front-end, exige a integração com APIs de mapas (Mapbox/Google Maps) para plotagem visual, o que demanda cuidado com o consumo de memória do dispositivo móvel. |
| **2. Descentralização e Automação da Comunicação**<br>*(Eliminar a dependência de ligações e mensagens manuais via WhatsApp para conhecidos - citado por Vicente, Vilma e Vicente Filho)* | **Simples** | A criação de uma plataforma de classificados/ofertas estruturada resolve essa dor. Do ponto de vista técnico, é um clássico modelo de operações **CRUD** (Create, Read, Update, Delete) em um banco de dados relacional (PostgreSQL), cruzando a oferta do Dono do Silo com a demanda do Produtor Rural. |
| **3. Acessibilidade e Usabilidade para Público Sênior**<br>*(A faixa etária dos entrevistados varia de 58 a 90 anos, o que impõe um desafio de interface)* | **Média** | O desenvolvimento no **React Native** precisará de um rigoroso padrão de UX/UI voltado para acessibilidade. Isso inclui fontes com tamanho dinâmico, alto contraste, botões grandes (touch targets generosos) e fluxos lineares, evitando menus complexos ou informações sobrecarregadas na mesma tela. |
| **4. Rentabilização e Segurança Financeira**<br>*(Evitar o prejuízo de manter o silo vazio e evitar que o produtor pague fretes abusivos por urgência - citado por Sandra)* | **Difícil** | Envolve transações financeiras e retenção de comissão. A viabilidade é mais complexa pois exige integração segura com um **Gateway de Pagamento** (Mercado Pago/Stripe), implementação de Webhooks para confirmação de pagamento e propriedades ACID no banco de dados para garantir que não haja cobranças duplicadas ou falhas de concorrência. |
| **5. Agilidade na Negociação (Senso de Urgência)**<br>*(Evitar a perda da colheita por lentidão em fechar negócio - citado por Vicente)* | **Difícil** | Para que a transação seja rápida e justa, o sistema utilizará o motor de leilão em tempo real. A dificuldade técnica reside na implementação de **WebSockets**. É necessário garantir baixa latência na transmissão dos lances, gerenciar o estado da conexão caso o usuário passe por uma área sem cobertura de internet (reconexão automática) e lidar com regras dinâmicas de cronômetro no back-end (FastAPI). |

---

## Resumo

A análise confirma que o GoSilo é **tecnicamente viável**, mas possui níveis de complexidade distintos. 

As funcionalidades básicas de cadastro e oferta de silos (Desejo 2) são de implementação **Simples**. A inteligência geográfica (Desejo 1) e a adaptação de interface (Desejo 3) representam uma complexidade **Média**, exigindo boas práticas de design de software e banco de dados espacial. O verdadeiro desafio de engenharia — de nível **Difícil** — concentra-se no núcleo transacional: garantir um leilão em tempo real sem falhas de sincronia (Desejo 5) e processar o acordo financeiro com segurança (Desejo 4).
