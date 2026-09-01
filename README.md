# Insetos vivos do Paraná v2

Página estática com estimativa populacional modelada de insetos em cinco
municípios do Paraná: Telêmaco Borba, Curitiba, Londrina, Maringá e Foz do Iguaçu.

Tudo vive em `index.html` — sem build, sem dependências. É só abrir o arquivo.

## O modelo

As **mesmas seis espécies** são estimadas em todos os municípios, para que os
números sejam comparáveis entre cidades:

| Espécie | Nome científico | Densidade (ind/ha) | Afinidade urbana |
|---|---|---:|---:|
| Grilo-do-campo | *Gryllus assimilis* | 850 | 0,15 |
| Formiga-cortadeira | *Atta sexdens* | 42.000 | 0,10 |
| Abelha-jataí | *Tetragonisca angustula* | 1.600 | 0,30 |
| Besouro-rola-bosta | *Dichotomius anaglypticus* | 190 | 0,05 |
| Borboleta-do-maracujá | *Agraulis vanillae* | 55 | 0,25 |
| Pernilongo | *Culex quinquefasciatus* | 3.400 | 0,80 |

O cálculo é:

```
fator de habitat = verde × (1 − urbano) + (1 − verde) × urbano
habitat efetivo  = área do município (ha) × fator de habitat
população        = habitat efetivo × densidade
```

Área e população humana vêm do **IBGE (Censo 2022)**. As densidades por hectare
são valores de referência da literatura entomológica — ordens de grandeza, não
medições locais. As densidades resultantes ficam entre 0,003 ind/m² (borboletas)
e cerca de 3 ind/m² (formigas), faixa compatível com levantamentos de campo.

A afinidade urbana faz cada espécie responder à cidade de forma diferente: o
pernilongo tem mais habitat efetivo em Curitiba do que em Telêmaco Borba,
enquanto o besouro-rola-bosta segue o caminho inverso.

## Sobre o contador "em tempo real"

O número oscila porque o modelo simula o fluxo contínuo de nascimentos e mortes.
A variação é **proporcional ao tamanho da população** e fica limitada a ±2,5% da
estimativa base. **Não é uma contagem real nem um sensor em campo** — é uma
estimativa, e a página diz isso de forma explícita.
