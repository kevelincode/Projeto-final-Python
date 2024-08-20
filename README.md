
 


Documentação do Código: Integração de APIs e Geração de Banco de Dados













Kevelin Suellen de Souza Oliveira
Turma: 58875
Data de criação: 22/07/2024
Última modificação: 17/08/2024



Sumário
Objetivo	3
Público alvo	3
Saída	3
Nível de privacidade	3
Pré requisitos	3
Ambientes	3
Bibliotecas	3
Arquivos	4
API’s utilizadas	4
Funções criadas	4
Tratamentos aplicados	4
•	Tratamento de datas	4
•	Tratamento de Valores Ausentes	4
•	Conversão de Tipos	5
•	Agregação	5
Método de saída	5
Exemplo de consulta	6
Versionamento	6
Referências	6












Objetivo
Este projeto tem por finalidade extrair dados da API do YouTube para analisar e comparar canais na plataforma. O objetivo é reunir informações relevantes sobre o desempenho dos canais e dos vídeos, possibilitando uma análise detalhada e comparativa. Foi necessário a instalação das bibliotecas Pandas, google-api-python-client.

Público alvo
Este código é voltado para analistas de dados e profissionais de marketing digital que desejam fornecer insights valiosos para criadores de conteúdo. Ele permite coletar métricas importantes para acompanhar o crescimento de canais e identificar tópicos que possam aumentar o engajamento do público.
Saída
O código gerado nos fornece um arquivo chamado 'Análise_Youtube.xlsx' e 4 abas sendo elas:
'Estatísticas dos Canais' – com as colunas channel_id, channel_name, published_date, published_tim, country, subscribers, view, total_videos e playlist_id;
'Detalhes dos Vídeos' - channel_name, vídeo_id, title, published_date, published_time, duration, category_id, views, likes e comments;
'Uploads Mensais' - channel_name, month e uploads;
'Média de Engajamento' – metric, avarege e channel_name.

Nível de privacidade
Os dados coletados são públicos, pois podem ser acessados por qualquer usuário que navegue pelo Youtube.
Entretando, para conseguir acesso a API, é necessário solicitar uma chave. O acesso a chave é feito através do google clound. 

Pré requisitos
Ambientes
O código foi executado em Python 3.7 utilizando o Visual Code como editor.
Bibliotecas
As bibliotecas utilizadas são: 
•	googleapiclient.discovery: v Interação com APIs do Google
•	Pandas: Manipulação e análise de dados.
•	Requests: Realização de requisições HTTP.
•	Isodate: Manipulação de datas e horários em formato ISO 8601.
•	Sqlite3: Interação com bancos de dados SQLite.

Arquivos
Chave da API: O código requer que a chave da API do YouTube seja inserida diretamente no código, substituindo 'YOUR_API_KEY' pela chave válida que você obtém no Google Cloud Console.

API’s utilizadas
A API utilizada foi a YouTube Data API v3. Ela permite o acesso e interação com os dados do YouTube, como informações sobre vídeos, canais, playlists, comentários, etc.
Para acessar a API, é necessário criar um projeto no Google Cloud Console, habilitar a YouTube Data API v3 e gerar credenciais de API. 

Funções criadas
•	get_channel_id(youtube, custom_url):
Busca o ID do canal usando a API e retorna o ID encontrado.
•	get_channel_stats(youtube, channel_ids):
Obtém estatísticas dos canais, como número de inscritos, visualizações e vídeos publicados.
•	get_video_ids(youtube, playlist_id):
Retorna uma lista contendo os IDs dos vídeos encontrados.
•	get_video_details(youtube, video_ids, channel_name):
Obéem detalhes dos vídeos, como título, data de publicação, visualizações, curtidas e comentários.
•	get_channel_activity(youtube, playlist_id):
Calcula a frequência mensal de uploads e o engajamento médio (visualizações, curtidas e comentários) dos vídeos do canal.

Tratamentos aplicados
•	Tratamento de datas
Formatação: A parte da A data é convertida para um objeto datetime do Pandas e formatada para o padrão dia/mês/ano. E como as datas são separadas usando o separador 'T' elas são tratadas para que venham separadas por barras (/).

•	Tratamento de Valores Ausentes
Uso de get: O método get é usado para obter um valor de um dicionário, se a chave 'publishedAt' não existir no dicionário, o valor 'N/A' será atribuído.

•	Conversão de Tipos
O número de inscritos, que é uma string no JSON, é convertido para um número inteiro usando a função int(). Se a chave 'subscriberCount' não existir, o valor padrão será 0.

•	Agregação
Os dados são agrupados por canal e mês usando o método groupby.

•	Erro de conexão
Verificação de falhas na comunicação com a API.


Método de saída
Os dados extraídos da API, irão gerar um arquivo .XLSX com 4 abas.
Primeira aba - Estatísticas dos Canais
channel_id - object
channel_name - object
published_date - object
published_time - object
country - object
subscribers - int64
views - int64
total_videos - int64
playlist_id – object

Segunda aba – Destalhes dos vídeos
channel_name - object
video_id - object
title - object
published_date - object
published_time - object
duration - object
category_id - object
views - int64
likes - int64
comments - int64

Terceira aba – Uploads mensais
channel_name - object
month - object
uploads - int64

Quarta aba – Média de enganjamento
Metric - object
average - float64
channel_name – object

Exemplo de consulta
Para executar uma consulta as tabelas, foi usado o método head() para visualizar as primeiras linhas do código a fim de verificar como estão sendo extraídos os dados.
Exemplo: avg_engagement_df.head(3) – Nos traz as primeiras 3 linhas da tabela Média de enganjamento.

Versionamento
Um arquivo requiriment.txt foi gerado e será fornecido juntamente com a documentação deste projeto.

Referências
Foi utilizado como referência o tutorial do canal Programação dinâmica do Youtube
https://www.youtube.com/watch?v=olDCJ1w3FLM&t=538s

