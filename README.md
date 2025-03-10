# Ambientes-Inteligentes-Atividade-N1-1B
Atividade Avaliativa para N1 do 1◦ Bimestre, a entrega ser´a individual. Cada estudante  dever´a realizar o in´ ıcio da an´alise explorat´oria para o conjunto de dados Movie Lens (small):  https://grouplens.org/datasets/movielens/.
Prazo de entrega 10/03/2025 até as 23:55 com desconto de 10 pontos por dia de atraso. Seguem os critérios a serem avaliados:
#Questão 1. Descrição da base de dados. 
##(a) (20 pontos) Descrição geral do dataset. 
O dataset MovieLens (ml-latest-small) conté, dados de interações de usuários com filmes no serviço de recomendação de filmes. A base de dados apresenta informações sobre avaliações(ratings) e tags(etiquetas) atribuídas pelos usuários aos filmes. O dataset inclui:
•	100.836 avaliações de 5 estrelas, feitas por 610 usuários.
•	3.683 aplicações de tags, em um total de 9.742 filmes.
•	Os dados cobrem um período de tempo de 29 de março de 1996 a 24 de setembro de 2018.
•	Usuários selecionados aleatoriamente que avaliaram pelo menos 20 filmes.
•	Não contém informações demográficas dos usuários.
Os dados estão distribuídos em quatro arquivos CSV principais, que são:
1.	ratings.csv: Contém as avaliações dos usuários sobre os filmes.
2.	tags.csv: Contém as tags atribuídas pelos usuários aos filmes.
3.	movies.csv: Contém informações sobre os filmes, incluindo título e gêneros.
4.	links.csv: Contém identificadores que podem ser usados para vincular os filmes a fontes externas (IMDb, TMDb).
O dataset pode ser utilizado para fins de pesquisa em sistemas de recomendação, no entanto, não é adequado para resultados de pesquisa compartilhados, já que pode sofrer alterações ao longo do tempo.
##(b) (10 pontos) O que significa cada linha de cada arquivo? 
Cada arquivo contém uma estrutura específica, que é explicada abaixo:
ratings.csv: Cada linha representa uma avaliação de um filme feita por um usuário. O formato da linha é: userId, movieId, rating, timestamp.
•	userId: Identificador único do usuário.
•	movieId: Identificador único do filme.
•	rating: A avaliação dada pelo usuário, em uma escala de 0.5 a 5.0 estrelas.
•	timestamp: O momento em que a avaliação foi feita, representado como o número de segundos desde 1 de janeiro de 1970 (UTC).
tags.csv: Cada linha representa uma tag aplicada a um filme por um usuário. O formato da linha é: userId, movieId, tag, timestamp.
•	userId: Identificador único do usuário.
•	movieId: Identificador único do filme.
•	tag: A tag atribuída ao filme pelo usuário (geralmente uma palavra ou uma curta frase).
•	timestamp: O momento em que a tag foi aplicada, representado como o número de segundos desde 1 de janeiro de 1970 (UTC).
movies.csv: Cada linha representa um filme no sistema MovieLens. O formato da linha é: movieId, title, genres.
•	movieId: Identificador único do filme.
•	title: Título do filme, incluindo o ano de lançamento entre parênteses.
•	genres: Lista de gêneros do filme, separados por "pipe" (|).
links.csv: Cada linha contém os identificadores do filme em diferentes fontes externas. O formato da linha é: movieId, imdbId, tmdbId
•	movieId: Identificador único do filme no MovieLens.
•	imdbId: Identificador do filme no IMDb.
•	tmdbId: Identificador do filme no The Movie Database.
##(c) (10 pontos) quais são os atributos (colunas) e seus tipos
Os principais atributos de cada arquivo, com os tipos de dados mencionados para facilitar o processamento e análise dos dados, são:
•	ratings.csv:
1.	userId: Inteiro (Identificador único do usuário).
2.	movieId: Inteiro (Identificador único do filme).
3.	rating: Float (Avaliação do filme, entre 0.5 e 5.0).
4.	timestamp: Inteiro (Timestamp em segundos desde 1 de janeiro de 1970).
•	tags.csv:
1.	userId: Inteiro (Identificador único do usuário).
2.	movieId: Inteiro (Identificador único do filme).
3.	tag: String (Tag atribuída pelo usuário ao filme).
4.	timestamp: Inteiro (Timestamp em segundos desde 1 de janeiro de 1970).
•	movies.csv:
1.	movieId: Inteiro (Identificador único do filme).
2.	title: String (Título do filme, incluindo o ano de lançamento).
3.	genres: String (Lista de gêneros separados por "|").
•	links.csv:
1.	movieId: Inteiro (Identificador único do filme).
2.	imdbId: String (Identificador do filme no IMDb).
3.	tmdbId: String (Identificador do filme no The Movie Database).
#Questão 2. Preparação da base de dados. 
##(a)	(25 pontos) Identificação de Problemas no Dataset
1. Faltando Dados em Coluna (tmdbId):
•	Dataset 1 (links.csv): A coluna tmdbId possui 9734 valores não nulos, enquanto as colunas filmeId e imdbId têm 9742 valores não nulos. Isso sugere que existem 8 valores faltantes para o tmdbId. A falta de dados em uma coluna importante pode impactar a análise e a capacidade de linkar corretamente filmes com o TMDB (The Movie Database).
2. Tipagem de Dados Inadequada (timestamp):
•	Dataset 3 (ratings.csv) e Dataset 4 (tags.csv): A coluna timestamp está como int64, mas representando um valor de data/hora (normalmente armazenado como um número de segundos desde uma data inicia). Essa coluna deveria ser convertida para o tipo datetime para facilitar o trabalho com datas.
3. Nomes das colunas em inglês
•	Como estamos trabalhando esses dados no Brasil cuja língua nativa é o português, idealmente as colunas deveriam seguir um padrão em português para facilitar a compreensão.
##(b) (25 pontos) Correções Aplicadas
Com base nos problemas identificados, aqui estão as possíveis correções:
1. Tratamento de Dados Faltantes (tmdbId):
•	Preencher os valores ausentes de tmdbId com um valor padrão (0). Usando o método fillna().
2. Conversão da Coluna timestamp para o Tipo datetime:
•	Como a coluna timestamp está como um tipo inteiro, podemos convertê-la para o tipo datetime para facilitar a análise temporal. Usando o to_datetime.
3. Renomeação das Colunas:
•	Podemos renomear as colunas para facilitar a análise. Usando o columns.

#Questão 3. Compartilhe o link do seu repositório Git com a resolução da sua atividade.


