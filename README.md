# Configuração da API OpenWeatherMap

Para utilizar este projeto, você precisa de uma chave de API do OpenWeatherMap. Siga os passos abaixo:

---

## 1. Crie uma conta

Acesse o link de cadastro:  
🔗 [https://home.openweathermap.org/users/sign_up](https://home.openweathermap.org/users/sign_up)

---

## 2. Complete o registro

- Preencha seu nome, e-mail e senha  
- Aceite os Termos de Serviço  
- Clique em **Create Account**

---

## 3. Obtenha sua chave API

Após fazer login:  
1. Acesse o [Painel de API Keys](https://home.openweathermap.org/api_keys)  
2. Clique em **Generate** para criar uma nova chave  
3. Aguarde alguns minutos para a chave ativar

---

## 4. Configure no projeto

Adicione sua chave no arquivo `.env` do projeto:


## Desafio Técnico
## 1. ETL - Extração de Dados da OpenWeatherMap
Cidades:
CITIES = [
    ("São Paulo", "BR"),
    ("Rio de Janeiro", "BR"),
    ("New York", "US"),
    ("Tokyo", "JP"),
    ("London", "GB")
]
Campos obrigatórios na saída:

Campo	Descrição	Exemplo
coord	Coordenadas geográficas	lon, lat
weather	Condições climáticas	description, icon
base	Fonte dos dados	"stations"
main	Dados principais	temp, humidity
visibility	Visibilidade (metros)	10000
wind	Dados de vento	speed, deg
clouds	Nuvens (cobertura %)	all
rain	Dados de chuva (se disponível)	1h, 3h
snow	Dados de neve (se disponível)	1h, 3h
dt	Horário da medição (UTC)	2023-10-05 18:00:00
sys	Dados do sistema	country, sunrise
timezone	Fuso horário (segundos UTC)	-10800
id	ID da cidade	3448439
name	Nome da cidade	São Paulo
cod	Código de status HTTP	200
## 2. Armazenamento em Camada RAW
Formato: Parquet
Local: data/raw/openweather/
## 3. Persistência em PostgreSQL
Criar tabela weather_data com estrutura correspondente aos campos extraídos
## 4. Acesso ao MongoDB - Credenciais fornecidas pelo Cristiano Cloud Atlas
Database: desafio_dataengenieer
Collection: reviews

## 5. Exportação MongoDB para Parquet datalake(Minio)
Salvar dados da collection reviews em:
minio://bucket-name/raw/mongodb/reviews.parquet
## 6. Geração de Nuvem de Palavras
Processar coluna "Review" dos dados do MongoDB
Utilizar algoritmo Python para contagem de palavras

## 7. Armazenamento da Nuvem de Palavras
Collection: desenvolvedor_nuvem_palavras
Estrutura:
json
{
  "word": "exemplo",
  "count": 15
}
## 8. Processamento de Arquivo CSV
Arquivo: social_media_engagement.csv
Ações:
Ler arquivo CSV usando Pandas
Imprimir conteúdo no console
Salvar em formato Parquet no MinIO:
minio://bucket-name/raw/social_media.parquet