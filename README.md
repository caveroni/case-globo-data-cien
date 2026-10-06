# Case Data Analyst – Globo

Fiz o case em duas partes: três queries SQL com pandasql e uma análise exploratória do Cartola Pro. O enunciado está na pasta docs.

## Estrutura

```
Case_Globo/
├── data/        base_desafio_cartola.csv, videos_metadata.csv, titles_genres.csv (não versionados)
├── notebooks/   sql_analysis.ipynb, cartola_eda.ipynb (já executados, com saídas)
├── outputs/
│   └── figures/ gráficos PNG gerados pela EDA
├── docs/        PDFs do enunciado
├── requirements.txt
└── README.md
```

## Como rodar

Crie um ambiente virtual, instale o requirements.txt (mais o ipykernel, para abrir os notebooks no VS Code) e rode os notebooks de dentro da pasta notebooks, porque os caminhos são relativos. Os CSVs não estão no repositório; para rodar de novo, coloque-os em data. Os notebooks já estão salvos com as saídas, então dá para só abrir e ler.

## SQL

O join entre vídeos e gêneros dá 1.501 linhas, e muita gente fica sem gênero porque o título não tem um cadastrado. Por categoria, Entretenimento tem 1.205 vídeos distintos, Sem Categoria 204, Notícias 49 e Esportes 43. A duração média dos títulos de Drama é de 1,72 hora.

## EDA

Quis entender o que diferencia quem assina o Cartola Pro, então olhei só quem já joga Cartola: 30.096 usuários, dos quais 1.077 são Pro.

O que mais separa os grupos é a frequência. A taxa de Pro vai de 1,4% para quem acessou de 1 a 3 dias até 7,0% para quem acessou 22 dias ou mais. O dispositivo também pesa: quem usa computador e celular tem 6,5% de Pro, contra 3,2% só no computador e 1,7% só no celular, e a diferença continua quando comparo usuários com a mesma frequência.

Quem lê 3 ou mais modalidades olímpicas tem 6,2% de Pro, contra 2,1% de quem não lê nenhuma. Em parte isso é só volume de uso, já que o efeito some entre os usuários mais frequentes, mas entre os ocasionais ainda fica em torno de 2x. Também há diferença por perfil (homens 5,3%, mulheres 2,7%, e São Paulo e Paraná acima do Rio de Janeiro), mas isso vale só para quem tem cadastro, cerca de metade dos jogadores.

Juntando frequência e dispositivo, o grupo que mais chama atenção é o "Fiel multi-device" (15 dias ou mais, nos dois dispositivos). Ele é 13,9% dos jogadores, mas tem 32,7% dos Pro, com taxa de 8,4%. Os gráficos estão em outputs/figures.

## Limitações

É uma análise exploratória, então mostra associação e não causa: o Pro pode acessar mais justamente por ser assinante. Uns 36% dos usuários não têm cartola_status e ficaram de fora. A base cobre só um mês, e um mês atípico por causa das Olimpíadas, e não dá para saber quando cada usuário virou Pro.
