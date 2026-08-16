# Proposta de Stack Tecnológica

---

# 1.  Frontend Mobile (Aplicativo Móvel)
Para o aplicativo móvel, o grupo precisa de uma ferramenta **multiplataforma** (iOS e Android) para não precisar programar o aplicativo duas vezes.  


**Recomendação Principal:**
- React Native com Expo. O Expo é uma camada sobre o React Native que elimina a complexidade inicial de configurar o Android Studio ou o Xcode. 

| Prós | Contras |
|------|---------|
|**Facilidade de Início:** Com o aplicativo Expo Go instalado no celular, a equipe consegue testar o app em tempo real no próprio smartphone apenas lendo um QR Code no computador.| Gerenciamento de estados (ex: Context API ou Redux) exige um pouco de estudo prático. |
|**Ecossistema Amplo:** Possui bibliotecas prontas e fáceis de usar para mapas (react-native-maps), geolocalização (expo-location), câmera e notificações push. |
|**Comunidade Gigante:** É a tecnologia com mais tutoriais e soluções de dúvidas na internet para iniciantes. |



**Alternativa:**
- Flutter (Linguagem Dart)
  
| Prós | Contras |
|------|---------|
|Linguagem Dart é fortemente tipada e orientada a objetos, lembrando a estrutura lógica do C/C++/Java.| Exige a instalação e configuração completa do Android SDK/Emuladores no computador desde o primeiro dia, o que pode gerar dificuldades de ambiente de desenvolvimento em computadores mais fracos. |
|Interface rica em widgets prontos com excelente desempenho.|


---
# 2. Backend (Servidor e Regras de Negócio)
O backend será responsável por intermediar os leilões, validar as regras de negócio (como o cálculo da comissão de 5% e a regra de prorrogação de tempo anti-sniping), gerenciar acessos e expor as APIs.  

**Recomendação Principal:**
- Python com FastAPI. O FastAPI é um framework moderno para construção de APIs em Python. 
 
| Prós | Contras |
|------|---------|
|**Sintaxe Amigável:** O Python é conhecido como uma das linguagens mais fáceis e legíveis de aprender. | Exige aprender uma linguagem diferente do frontend (Python no backend e JavaScript/TypeScript no mobile). |
|**Documentação Automática:** O FastAPI gera automaticamente uma página interativa (Swagger UI) com todos os pontos de acesso (endpoints) da API, o que ajuda muito na apresentação para a banca do projeto e nos testes da equipe. |
|**Suporte a WebSockets:** Possui suporte nativo e simples para conexões em tempo real (essencial para o leilão).|

**Alternativa:**
- Node.js (com Express ou Fastify em JavaScript/TypeScript)

| Prós | Contras |
|------|---------|
|Unificação de linguagem: usa JavaScript/TypeScript no backend e no frontend mobile. |Sem uma estrutura bem definida (como NestJS), o código do Express pode ficar desorganizado para desenvolvedores iniciantes. |

---
# 3. Banco de Dados e Geolocalização
O GoSilo possui requisitos fortes de busca por raio geográfico (ex: silos a até 50km do produtor), agrupamento de pontos (clusters) e consistência de dados para evitar lances simultâneos conflitantes.  

**Recomendação Principal:**
- PostgreSQL com extensão PostGIS  O PostgreSQL é um banco relacional robusto (ACID), e o PostGIS é a extensão padrão da indústria para dados geográficos.

| Prós | Contras |
|------|---------|
|**Poder Geográfico (PostGIS):** Permite calcular distâncias exatas (ST_DWithin), agrupar marcadores e aplicar múltiplos filtros espaciais e de atributos simultaneamente (WHERE distancia < X AND grao = 'Milho').|  Exige aprender a linguagem SQL para consultas e modelagem de tabelas. |
|**Garantia de Integridade (Transações ACID):** Garante que se dois produtores derem um lance na mesma fração de segundo, apenas um seja processado e o outro seja avisado (requisito RF-025).| 
|**Gratuito e Hospedagem Fácil:** Pode ser hospedado gratuitamente ou por baixo custo em plataformas como Supabase, Render ou Railway.| 

- Por que NÃO usar SQLite ou Firebase Firestore isoladamente?
  
| SQLite | Firebase Firestore (noSQL) |
|--------|----------------------------|
|É um banco de dados local (armazenado apenas dentro do aplicativo do celular). Não serve para ser o banco central do leilão onde todos os usuários se conectam. | Embora seja fácil de configurar, realizar consultas complexas combinando raio de distância + tipo de grão + faixa de preço é extremamente difícil e ineficiente em bancos NoSQL orientados a documentos.|

---
# Documento original
Ver documento [`GoSilo-Planejamento/docs/seu-arquivo.docx`](linkdouploadodoword).

