# Stack proposta 
Sugestão tecnológica inicial para o projeto.

---

## Frontend Mobile (Aplicativo Móvel)

Para o aplicativo móvel, o grupo precisa de uma ferramenta multiplataforma (iOS e Android) para não precisar programar o app duas vezes.

|Tecnologia Sugerida|Prós|Contras|
|----------------|-----------------------|-----------------------|
|**React Native (com Expo)**|**Facilidade de Início**: Com o aplicativo Expo Go instalado no celular, a equipe consegue testar o app em tempo real no próprio smartphone apenas lendo um QR Code no computador.<br>**Ecossistema Amplo**: Possui bibliotecas prontas e fáceis de usar para mapas (react-native-maps), geolocalização (expo-location), câmera e notificações push.<br>**Comunidade Gigante**: É a tecnologia com mais tutoriais e soluções de dúvidas na internet para iniciantes. Gerenciamento de estados (ex: Context API ou Redux) exige um pouco de estudo prático.|Gerenciamento de estados (ex: Context API ou Redux) exige um pouco de estudo prático.|
|**Flutter (Linguagem Dart)**|Linguagem Dart é fortemente tipada e orientada a objetos, lembrando a estrutura lógica do C/C++/Java.<br>Interface rica em widgets prontos com excelente desempenho.|Exige a instalação e configuração completa do Android SDK/Emuladores no computador desde o primeiro dia, o que pode gerar dificuldades de ambiente de desenvolvimento em computadores mais fracos.|

## Backend (Servidor e Regras de Negócio)

<p align="center">O backend será responsável por intermediar os leilões, validar as regras de negócio (como o cálculo da comissão de 5% e a regra de prorrogação de tempo anti-sniping), gerenciar acessos e expor as APIs.</p>

|Tecnologia Sugerida|Prós|Contras|
|----------------|-----------------------|-----------------------|
|**Python com FastAPI**|**Sintaxe Amigável**: O Python é conhecido como uma das linguagens mais fáceis e legíveis de aprender.<br>**Documentação Automática**: O FastAPI gera automaticamente uma página interativa (Swagger UI) com todos os pontos de acesso (endpoints) da API, o que ajuda muito na apresentação para a banca do projeto e nos testes da equipe.<br>**Suporte a WebSockets**: Possui suporte nativo e simples para conexões em tempo real (essencial para o leilão).|Exige aprender uma linguagem diferente do frontend (Python no backend e JavaScript/TypeScript no mobile).|
|**Node.js (com Express ou Fastify em JavaScript/TypeScript)**|Unificação de linguagem: usa JavaScript/TypeScript no backend e no frontend mobile.|Sem uma estrutura bem definida (como NestJS), o código do Express pode ficar desorganizado para desenvolvedores iniciantes.|

## Banco de Dados e Geolocalização

<p align="center">O GoSilo possui requisitos fortes de busca por raio geográfico (ex: silos a até 50km do produtor), agrupamento de pontos (clusters) e consistência de dados para evitar lances simultâneos conflitantes.</p>

|Tecnologia Sugerida|Prós|Contras|
|----------------|-----------------------|-----------------------|
|**PostgreSQL com extensão PostGIS**|**Poder Geográfico (PostGIS)**: Permite calcular distâncias exatas (ST_DWithin), agrupar marcadores e aplicar múltiplos filtros espaciais e de atributos simultaneamente (WHERE distancia < X AND grao = 'Milho').<br>**Garantia de Integridade (Transações ACID)**: Garante que se dois produtores derem um lance na mesma fração de segundo, apenas um seja processado e o outro seja avisado (requisito RF-025).<br>**Gratuito e Hospedagem Fácil**: Pode ser hospedado gratuitamente ou por baixo custo em plataformas como Supabase, Render ou Railway.|Exige aprender a linguagem SQL para consultas e modelagem de tabelas.|

### Por que NÃO usar SQLite ou Firebase Firestore isoladamente?
``` bash
SQLite: É um banco de dados local (armazenado apenas dentro do aplicativo do celular).
Não serve para ser o banco central do leilão onde todos os usuários se conectam.

Firebase Firestore (NoSQL): Embora seja fácil de configurar, realizar consultas complexas
combinando raio de distância + tipo de grão + faixa de preço é extremamente difícil
e ineficiente em bancos NoSQL orientados a documentos.
```

## Comunicação em Tempo Real (Leilão e Chat)

<p align="center">Para o cronômetro do leilão, a atualização de lances instantânea e o chat entre o vencedor e o dono do silo, é necessária comunicação bidirecional sem necessidade de recarregar a tela (RF-024).</p>

|Tecnologia Sugerida|Como Funciona|Prós|Contras|
|----------------|-----------------------|-----------------------|-----------------------|
|**WebSockets nativos (FastAPI) ou Socket.IO**|Mantém um "tubo" de comunicação aberto entre o aplicativo e o servidor. Quando alguém dá um lance, o servidor envia esse valor imediatamente para todos os usuários que estão assistindo àquele leilão.|Baixa latência e atualizações instantâneas no celular.|Exige tratamento no servidor para reconexão em caso de oscilações de sinal no meio rural (4G/3G).|

## Criptografia e Segurança

<p align="center">Para atender à regra de privacidade RNE-012 (onde os dados sensíveis do produtor ficam ocultos e criptografados no banco de dados até a finalização do leilão) e às exigências da LGPD (RF-008):</p>

|Parâmetro Analisado|Tecnologia Sugerida|Funcionamento|
|----------------|----------------|-----------------------|
|**Criptografia de Dados Sensíveis (At-Rest)**|**Criptografia Simétrica AES-256**|Os dados do participante (CPF, nome) são criptografados antes de salvar na tabela do banco. O dono do silo vê apenas um ID anonimizado (ex: "Produtor #A12F"). Quando o leilão é finalizado, o servidor descriptografa os dados do vencedor para liberar o contato.|
|**Armazenamento de Senhas**|**BCrypt ou Argon2id**|Transforma a senha em um hash irreversível. Nunca se deve salvar a senha em texto puro no banco de dados.|
|**Autenticação de Sessão**|**JWT (JSON Web Tokens)**|Gera um token seguro e assinado após o login, enviado em cada requisição do aplicativo para validar o usuário.|
|**Segundo Fator de Autenticação (2FA - RF-006)**|**TOTP (Time-based One-Time Password)**|Uso de bibliotecas como pyotp (compatível com apps como Google Authenticator) ou envio de código por e-mail.|

## APIs Externas e Integradores

<p align="center">Para simplificar algumas partes, a equipe deve utilizar serviços e APIs consolidados:</p>

### Mapas e Interface Visual (RF-010):

|Tecnologia Sugerida|Funcionamento|
|----------------|-----------------------|
|**Mapbox API ou OpenStreetMap (Leaflet/React Native Maps)**|O Mapbox oferece mapas bonitos e uma quota gratuita mensal generosa para projetos acadêmicos.|

### Validação de CPF / CNPJ (RNE-002, RF-002):

|Tecnologia Sugerida|Funcionamento|
|----------------|-----------------------|
|**BrasilAPI (Gratuita e pública) ou ReceitaWS**|Permitem verificar o formato e a situação cadastral na Receita Federal de forma simples através de chamadas HTTP.|

### Notificações Push (RNE-021, RF-023):

|Tecnologia Sugerida|Funcionamento|
|----------------|-----------------------|
|**Firebase Cloud Messaging (FCM) ou OneSignal**|Serviços gratuitos para enviar alertas para o celular do usuário quando ele receber um lance ou vencer o leilão.|

### Simulação de Pagamentos / Comissão (RNE-024):

|Tecnologia Sugerida|Funcionamento|
|----------------|-----------------------|
|**Mercado Pago API (Sandbox) ou Stripe API (Test Mode)**|Permitem simular o pagamento e a geração de cobranças da comissão de 5% da plataforma em ambiente de testes sem gastar dinheiro real.|

## Tecnologias para IoT (Internet das Coisas - Opcional / Diferencial)

<p align="center">Embora não esteja explicitamente detalhado como requisito obrigatório de código no documento principal, monitorar o nível de preenchimento ou as condições do silo via IoT é um diferencial fortíssimo no agronegócio.</p>

### Hardware Recomendado:

|Tecnologia Sugerida|Funcionamento|
|----------------|-----------------------|
|**Placa ESP32**|Microcontrolador barato (custa em torno de R$ 35 - R$ 50), fácil de programar (utiliza linguagem baseada em C/C++, o que se alinha com o que a equipe está aprendendo na faculdade!) e já vem com Wi-Fi e Bluetooth embutidos.|
|**Sensor Ultrassônico (HC-SR04 ou JSN-SR04T impermeável)**|Instalado no teto do silo para medir a distância até a silagem acumulada, calculando automaticamente o volume ocioso em metros cúbicos (m^3).|
|**Sensor de Temperatura e Umidade (DHT22)**|Para monitorar a qualidade do ambiente de armazenamento.|

### Protocolo de Comunicação IoT:

|Tecnologia Sugerida|Funcionamento|
|----------------|-----------------------|
|**MQTT (Broker Mosquitto ou HiveMQ)**|Protocolo ultra-leve próprio para dispositivos com pouca internet, enviando as medições do ESP32 diretamente para o servidor FastAPI.|

---
